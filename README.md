# Basketball-game
// Name: Yoshiki Hoshinaga
// Date: June 9th 2022 - July 31th 2022
void setup()
{
size(600,800);
background(300,432,400);

}
float x =0;


// Drag (click and hold) your mouse across the 
// image to change the value of the rectangle

int value = 0;

int score=0;
int xb=303;
int yb=730;
int xp=303;
int yp=730;
float g=1;
float p=60;
float r=0;
float xl=0;
float yl=0;
float t=0;
boolean go=false;
boolean timeP=false;
boolean oneTime=true;
boolean oneTimel=true;
boolean goingdown=false;
boolean scored=false;
float tP=0;


void draw() {
  fill(value);
  
  color back = color(225, 225, 225);
fill(back);
rect(0,0,600,800);

color basketgoal= color(400,432,400);
fill(basketgoal);
rect(180,50,250,170);

//basketgoalSide
color basketgoalSide= color(0,0,100,100);
fill(basketgoalSide);
noStroke();
rect(180,50,250,10);
rect(180,210,250,10);
rect(420,60,10,150);
rect(180,60,10,150);
rect(258,175,90,8);
rect(258,122,90,8);
rect(258,130,8,45);
rect(340,130,8,45);
rect(275,220,70,8);
//basket ring
if((-yl/(2*g))<t){
  goingdown=true;
}
if(goingdown){
  color basketball = color(204, 102, 0);
fill(basketball);
ellipse(xb,yb,70,70);
color basketring = color(300,0,0);
fill(basketring);
rect(243,184,120,10);
}else{
color basketring = color(300,0,0);
fill(basketring);
rect(243,184,120,10);

//basketball
color basketball = color(204, 102, 0);
fill(basketball);
ellipse(xb,yb,70,70);
}

text("score = "+score,10,10);  

if(timeP){
  tP+=6.1;
  if(tP>100)
    tP=100;
  System.out.println(tP);
  
}
if(go){
  xb=(int)(t*xl+xp);
  yb=(int)(g*t*t+yl*t+yp);
  t+=0.5;
  if((goingdown  && (
  (sqrt(((float)(xb)-(243+5))*((float)(xb)-(243+5))+
  ((float)(yb)-(184+5))*((float)(yb)-(184+5))))<(5+35)))){
    if(oneTime){
      oneTime=false;
      xp=xb;
      yp=yb;
      yl=-20; //test change this later
      xl=1.5;
      t=0;
    }
  }else{
    if(!oneTime){
      oneTime=true;
    }
  }
  if((goingdown  && (
  (sqrt(((float)(xb)-(243+120-5))*((float)(xb)-(243+120-5))+
  ((float)(yb)-(184+5))*((float)(yb)-(184+5))))<(5+35)))){
    if(oneTimel){
      oneTimel=false;
      xp=xb;
      yp=yb;
      yl=-20; //test change this later
      xl=-1.5;
      t=0;
    }
  }else{
    if(!oneTimel){
      oneTimel=true;
    }
  }
  if(!scored && goingdown && xb>=243+10 && xb<=243+120-10 && yb>=184 && yb<=184+10 ){
    score++;
    scored=true;
  }
}
if(xb>=600 || yb>=800 || xb<=0){
  xb=(int)random(50,550);
  yb=730;
  xp=xb;
  yp=730;
  g=1;
  p=50;
  r=0;
  xl=0;
  yl=0;
  t=0;
  go=false;
  timeP=false;
  oneTime=true;
  oneTimel=true;
  goingdown=false;
  scored=false;
  tP=0;
}

}

void mousePressed() {
   timeP=true;
}

//void mouseDragged() {
//  yb=pmouseY;
//  xb=pmouseX;
//}
void mouseReleased(){
  timeP=false;
  p=50;//tP;
  if(!go){
  float x1 = mouseX-xp;
  float y1 = mouseY-yp;
  //r=(p*(mouseX-xp))/(mouseY-yp);
  yl=((sqrt(x1*x1+y1*y1)*p)/(x1*x1/y1+y1));
  xl=(yl*x1)/y1;
  }
  
  go=true;
  

  
}
