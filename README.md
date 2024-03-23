# 2024GraphicsTeam10
2024년 그래픽스 수업 팀과제 1
## 마크다운 언어
------------------------------
## 소감
## 김현욱
d;safd
## 김재형
과제를 하면서 triangle(), rect(), ellipse() 등등의 도형들을 써보면서 곡선 표현이 어렵다고 느껴져서 bezier()를 써봤는데 나름대로 생각한 표정이 나와서 좋았던 기억이 납니다 캐릭터를 만들기 위해서 여러 도형들을 실험해보면서 p5.js의 2D 도형들을 하나씩 다 사용해보는 경험이 되었고 캐릭터 디자인이라는 것이 센스가 필요하구나 하는 생각을 하게 만든 과제인 것 같습니다. 
## 우상범
p5.js로 캐릭터 만들기라는 라는 과제를 하며 지금까지 배운 함수를 다시 복습하는 시간이었던겄 갔습니다. 그리고 과제를 하면서 나만의 캐릭터를 만들어보는 것이 더욱 재미있고 좋았습니다.
## 최우진
ddd
## 코드
-------------------
function setup() {
  createCanvas(1500, 1500,WEBGL);
}
//최우진
let spinZ = 0;// Z축 회전
let spinZadd = 0.02;
let dogsize = 0;//scale 변수
let dogY = -350; //변화하는 Y축
let dogadd = 2; //Y축에 더하는 값
let spinZ2 = 0; //강아지 팔 움직이기
let spinZ2add = 0.01;

//우상벙
let mvpig = 0;
let pigsize = 0;

//김재형
let t1 = 0; // sin 함수에 들어갈 변수

//김현욱
let angle = 0;
let rotationSpeed = 0.01;
let scaleFactor1 = 0.5; // 첫 번째 별의 크기 비율
let scaleFactor2 = 1.5; // 두 번째 별의 크기 비율
let sizeChangeSpeed = 0.01; // 크기 변화 속도

function draw(){
  background(80);
  draw우진();
  draw상범();
  draw재형();
  draw현욱();
}

function draw우진() {
  push();
  noStroke();
  translate(-250,dogY);
  dogY += dogadd;
  if (dogY < -450 || dogY > 0){
    dogadd *= -1 ;
  }
  scale(2*sin(dogsize=dogsize+0.03)+2); //커졌다 작아졌다를 표현
  push();//몸통을 그리기 위해 선언
  fill(199,135,73);//시바견 색깔
  rotate(40.45);//몸통으로 쓰일 원 위치 설정
  arc(10, -25, 50, 50, 0,  PI +QUARTER_PI, OPEN);//몸통
  fill(215,195,165);//몸통안 색깔
  arc(12, -30, 21, 21, 0,  PI +QUARTER_PI, OPEN);//몸통안
  fill(199,135,73);//시바견 색깔
  rotateZ(spinZ2);//왼발이 움직이는 값
  ellipse(30,-8,22,10);//왼발
  rotate(32.10);//오른발의 각도를 돌려줌
  rotateZ(-2*spinZ2);//오른발이 같은 방향으로 움직이기위하여 -2를 곱하여줌
  translate(-38,-37)//오른발 위치설정
  ellipse(9,27,22,10);//오른발 
  spinZ2 += spinZ2add;//양발이 움직이도록 변수를 주고 점점 증가시킴
  if (spinZ2 < -0.05|| spinZ2 > 0.05){
    spinZ2add *= -1 ;//특정값에 도달하면 반대방향으로 돌아가도 설정
  }
  pop();//몸통
  
  rotateZ(spinZ);//얼굴 전체를 움직이기위해 설정
  fill(199,135,73);//시바견 색깔
  ellipse(0,0,40,40);//얼굴
  triangle(-13, 6, 16, 10, 20, -31);//왼쪽 귀
  fill(215,195,165);
  triangle(10, -17, 18.5, -27, 16, -12);//왼쪽귀 안
  fill(199,135,73);
  triangle(13, 6, -16, 10, -20, -31);//오른쪽 귀
  fill(215,195,165);
  triangle(-10, -17, -18.5, -27, -16, -12);//오른쪽 귀 안
  ellipse(-7,-9,8,3);//왼쪽 눈썹
  ellipse(7,-9,8,3);//오른쪽 눈썹
  fill(0,0,0);
  ellipse(7,-3,4,4);//왼쪽 눈
  ellipse(-7,-3,4,4);//오른쪽 눈
  fill(215,195,165);
  arc(0, 3, 35, 30, -QUARTER_PI/3, PI + QUARTER_PI/3, PIE);//얼굴 안 부분
  ellipse(0,2,12,8);//얼굴 안 중간
  fill(0,0,0);
  ellipse(0,1,8,4);//코
  ellipse(0,5,0.5,11);//noSteoke를 사용하여 line을 쓸 수 없기에 얇은 원으로 대채
  fill(255,0,0);
  arc(4, 11, 5, 8, 0, PI , PIE); //혀
  fill(0,0,0);
  arc(0, 10, 20, 5, -QUARTER_PI/5, PI + QUARTER_PI/5, PIE);//입
  spinZ += spinZadd;//머리가 움직이도록 변수를 주고 값을 더해줌
  if (spinZ > 0.3 || spinZ < -0.3){
    spinZadd *= -1;//특정값에 도달하면 반대방향으로 돌아가도록 설정
  }
  pop();
}
function draw상범() {
  push();
  translate(200,-150);
  fill(255, 230, 230);
  rotateZ(mvpig+=0.02);
  scale(sin(pigsize=pigsize+0.01));

  // 돼지의 머리
  ellipse(200, 150, 150, 150);

  // 눈
  fill(255);
  ellipse(170, 130, 30, 30);
  ellipse(230, 130, 30, 30);

  // 눈동자
  fill(0);
  ellipse(170, 130, 10, 10);
  ellipse(230, 130, 10, 10);

  // 코
  fill(255, 200, 200);
  ellipse(200, 170, 50, 30);

  // 코 구멍
  fill(0);
  ellipse(190, 170, 10, 10);
  ellipse(210, 170, 10, 10);

  // 귀
  fill(255, 230, 230);
  triangle(130, 100, 160, 60, 160, 120);
  triangle(270, 100, 240, 60, 240, 120);
  pop();
}
function draw재형() {
  let a = sin(t1 = t1+0.01)+1; // 주기적 크기 변화를 위해서 sin 함수 사용
  translate(-200, 300);
  push();   
  fill(255, 255, 0); 
  rotate(4*a);
  translate(130, 130);
  scale(a); 
  ellipse(0, 0, 100, 100); 
  fill(255, 0, 0); 
  strokeWeight(5); 
  line(-30, -15, -15, -15); 
  line(30, -15, 15, -15);
  bezier(-15, 25, -5, 10, 5, 10, 15, 25); 
  pop(); 
  
}
function draw현욱() {
  strokeWeight(3);
  translate(400, -100);
  // 크기가 커졌다가 줄어드는 효과를 위해 사인 함수를 사용하여 scaleFactor 조절
  scaleFactor1 = sin(angle) * 0.3 + 1;
  scaleFactor2 = sin(angle + PI) * 0.3 + 0.8;

  push ();
  rotate (radians(-50))
  drawEllipse (-70, 165, 100, 170); // 오른쪽 팔
  pop ();
  
  push ();
  rotate (radians(-35))
  drawEllipse (150, 365, 100, 170); // 오른쪽 팔
  pop ();
  
  push ();
  fill (249, 39, 104);
  rotate (radians(50))
  drawEllipse (350, 120, 100,150); // 왼쪽 발
  pop();
  
  push ();
  fill (249, 39, 104);
  rotate (-radians(50))
  drawEllipse (-70, 440, 100,150); // 오른쪽 발
  pop ();
  
  fill (254, 195, 217);
  ellipse (200, 200, 300, 300);
  
  push();
  noStroke();
  fill (1, 0, 0);
  drawEllipse (150, 150, 30,60); // 왼쪽 눈
  drawEllipse (250, 150, 30, 60); // 오른쪽 눈
  pop();
  
  push ();
  noStroke();
  fill (0, 137, 199);
  drawEllipse (150, 160, 17, 33); // 왼쪽 아래 파란 눈동자
  drawEllipse (250, 160, 17, 33); // 오른쪽 아래 파란 눈동자
  pop ();
  
  push ();
  noStroke();
  fill(1, 0, 0)
  drawEllipse (150, 155, 18, 26); // 왼쪽 아래 검은 반달
  drawEllipse (250, 155, 18, 26); // 오른쪽 아래 검은 반달
  pop ();
  
  
  push ();
  noStroke();
  fill(255);
  drawEllipse (150, 139, 15, 27.5); // 왼쪽 눈 동공
  drawEllipse (250, 139, 15, 27.5); // 오른쪽 눈 동공
  pop ();
  
  push ();
  noStroke();
  fill (255, 136, 168);
  drawEllipse (120, 220, 55, 50); // 왼쪽 볼 터치
  drawEllipse (280, 220, 55, 50); // 오른쪽 볼 터치
  pop();
  
  push ();
  drawSmile(200, 195, 30, 20); // 입 모양
  pop();
  
  push();
// 타원형 함수
function drawEllipse(x, y, w, h) {
  ellipse(x, y, w, h);
}


//웃는 입수함수
function drawSmile(x, y, w, h) {
  noFill();
  stroke(0);
  strokeWeight(5); 
  beginShape();
  for (let angle = PI; angle <= 2*PI; angle += 0.01) {
    let sx = x + w/2 * -cos(angle);
    let sy = y + h/2 * -sin(angle);
    vertex(sx, sy);
  }
  endShape();
  
}

function drawScaledRotatedRoundedStar(x, y, radius1, radius2, roundedness, rotationAngle, scaleFactor) {
  let angle = TWO_PI / 5;
  let halfAngle = angle / 2.0;
  beginShape();
  for (let a = -PI/2 + rotationAngle; a < TWO_PI-PI/2 + rotationAngle; a += angle) {
    let sx = x + cos(a) * radius2 * scaleFactor;
    let sy = y + sin(a) * radius2 * scaleFactor;
    vertex(sx, sy);
    let rx = x + cos(a + halfAngle) * radius1 * scaleFactor;
    let ry = y + sin(a + halfAngle) * radius1 * scaleFactor;
    let tx = x + cos(a + angle) * radius2 * scaleFactor;
    let ty = y + sin(a + angle) * radius2 * scaleFactor;
    quadraticVertex(rx, ry, tx, ty);
  }
  endShape(CLOSE);
}
  stroke (0);
  fill (255, 214, 114);
  strokeWeight(3); //선의 굵기 설정
  drawScaledRotatedRoundedStar(290, 30, 45, 15, 2, angle, scaleFactor1); // 첫 번째 별
  strokeWeight(3); //선의 굵기 설정
  drawScaledRotatedRoundedStar(400, 100, 100, 30, 3, angle, scaleFactor2); // 두 번째 별
  pop();
  
  angle += rotationSpeed; // 각도 업데이트

}
