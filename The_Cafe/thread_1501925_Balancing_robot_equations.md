---
title: "Balancing robot equations"
date: 2010-06-04
forum: The Cafe
---

### Post by cguy on 2010-06-04
There are a lot of smart, technical people around here, so I'm gonna try my chance.


I am building a balancing robot like the one here:
[http://www.geology.smu.edu/~dpa-www/robo/nbot/](http://www.geology.smu.edu/~dpa-www/robo/nbot/)

It's basically a body mounted on two wheels and its purpose is to control the motors as to keep the wheels under the center of mass and therefore keep the body in an upward position.

I wrote the mechanical equations for the body and for the wheels separately, but I am not 100% sure they are correct.

I need someone to check them, please.

---

### Post by cguy on 2010-06-05
No one? :(

---

### Post by Frogs Hair on 2010-06-05
May help if you could see them better.:)

---

### Post by cguy on 2010-06-05
Bigger size now:
[http://imagebin.org/99998](http://imagebin.org/99998)
[http://imagebin.org/99999](http://imagebin.org/99999)

---

### Post by Hyporeal on 2010-06-05
I'm not sure why you're adding torque in the first two equations. The units are wrong, and you've already considered the motion-causing components of torque: the traction and the normal. The motor torque ought to have nothing to do with the position of the robot, right?

---

### Post by McRat on 2010-06-05
You need a gyro and a stepper motors.

The bigger the gyro, the better.  The stepper motors move to a given rotational position, you don't worry about torque as long as you have enough.

When the axis sensor on the gyro sees a tip condition, you calculate out the angle of tip, dia of wheel, and rotate that much.  Voila.  The faster the reaction time is, the less it will "hunt".

---

### Post by cguy on 2010-06-05
I'm not sure either why I wrote those two.
At first I didn't write them, but then I had a look at this page:
[http://www.engin.umich.edu/group/ctm/examples/pend/invpen.html](http://www.engin.umich.edu/group/ctm/examples/pend/invpen.html)
and in the [second equation]("http://www.engin.umich.edu/group/ctm/examples/pend/inveq2.GIF") I saw the second term on the right side, which I thought was the moment of inertia times the angular acceleration.

(What is that second term anyway?)

I obviously didn't think, since the units are wrong, just as you said.

I'm scraping them right now. Aside from these is there anything else wrong?

---

### Post by red_Marvin on 2010-06-05
> **McRat said:**
> The stepper motors move to a given rotational position

That would be servos. Stepper motors move in discrete steps (if sent discrete pulses), but do not know their angular position.

---

### Post by cguy on 2010-06-06
BumPitY BuMp

---

