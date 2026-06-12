---
title: "A maths question"
date: 2007-07-24
forum: The Cafe
---

### Post by TheSqueak on 2007-07-24
*because hopefully there'll be some smart people here*


Given the co-ordinates of three points on an arc (the two endpoints and the midpoint if it makes a difference), how would I go about working out the equation which describes that arc?

---

### Post by KIAaze on 2007-07-24
1)First locate the center by using the fact that the perpendicular bisector of two points on the arc goes through the center.
=>center (xc,yc)

2)Then calculate the radius, by calculating the distance between the center and a point on the arc.
=>radius R=sqrt((xi-xc)^2+(yi-yc)^2) where (xi,yi) is one of the 3 points you have.

3)The equation is then simply (x-xc)^2+(y-yc)^2=R^2

More details on (1):maybe later... ^^

edit:
Ok, so here's how to get the equations of the perpendicular bisectors:
For two points A(x1,y1) and B(x2,y2):

[LIST]
[*]middle point=(xm,ym)
xm=(x1+x2)/2
ym=(y1+y2)/2

[*]equation of the perpendicular bisector:
If y1!=y2: y=-(x2-x1)/(y2-y1)*(x-xm)+ym
If y1=y2: x=(x1+x2)/2=xm
[/LIST]

To calculate the intersection:
Assuming the equation of the perpendicular bisector of [AB] is y=f(x)
and the one of [BC] is y=g(x),
just solve the system:
[LIST]
[*]y=f(x)
[*]y=g(x)
[/LIST]
If one of the equations is x=xm, then xc=xm and yc=f(xc)=f(xm).

---

### Post by lert on 2007-07-24
for an arc, the center (xc,yc) and the radius R can be solve by the following 3 equations
(xc-x1)^2+(yc-y1)^2=R^2  (1)
(xc-x2)^2+(yc-y2)^2=R^2  (2)
(xc-x3)^2+(yc-y3)^2=R^2  (3)
Eq(1)-Eq(2) and Eq(2)-Eq(3) can give you two linear equations about (xc,yc), then you can get it easily.

---

### Post by KIAaze on 2007-07-24
Yep, that's the analytical approach. :)
Seems more complicated to me than the geometrical approach in this case.

A system of three 2nd order equations with three variables... :/

---

