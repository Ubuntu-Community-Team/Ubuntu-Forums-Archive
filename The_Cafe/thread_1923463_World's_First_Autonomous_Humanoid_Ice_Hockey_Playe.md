---
title: "World's First Autonomous Humanoid Ice Hockey Player"
date: 2012-02-10
forum: The Cafe
---

### Post by ve4cib on 2012-02-10
I thought I'd share this video with you: 

[http://youtu.be/D4xaaJNBhlk](http://youtu.be/D4xaaJNBhlk)

It is, to the best of my knowledge, the first autonomous humanoid robot ice hockey player in the world.  (We're Canadian, so I suppose ice hockey is only a natural thing for us to try to do, eh?)

The robot uses open-source software (it uses Xubuntu 11.10 for the OS, and all of the control code is written in C++ using open-source libraries like Espeak and OpenCV) and was created for the ICRA 2012 DARwIn-OP Humanoid Appliance Challenge.  The competition challenges teams to create a novel application for humanoid robots.  This video is our team's submission.

Finalists will be chosen sometime in March, with the final competition and presentations in May at ICRA 2012.

Obviously we've got a lot of room for improvement, but I'm pretty happy with the progress we've made so far.  Getting a robot to balance on skate blades at all is (unsurprisingly) a fairly difficult challenge.  But we're confident we can do it.

---

### Post by cgroza on 2012-02-10
Nice work.
Can it aim and shoot the puck at targets?

---

### Post by ve4cib on 2012-02-10
We're working on it.  It can already aim its kick to get a soccer ball in a goal, so we can re-use a lot of the same vision/logic systems for that.  The catch is that kicking a ball moves the ball in a straight line away from the robot.  Swinging a hockey stick moves the ball/puck left/right, so aiming is more difficult right now.  But we're working on it.

The big challenge I'm facing right now is improving the skating.  Right now it just kind of shuffles along.  I'm working on getting it to the point where it actually pushes and glides like a real skater.  We've got a pair of milled aluminium skate blades on-order that should come by next week or the week after.  That should make it easier to glide on the ice.

Once I've got the skating down (it can move forwards, backwards, and steer reliably) I'll work more on the aiming and stick-handling.  Those aspects are pretty rudimentary right now, I admit.

---

### Post by sanderella on 2012-02-11
It's left-handed. :popcorn:

---

### Post by mikodo on 2012-02-11
Double-post

---

### Post by mikodo on 2012-02-11
> **sanderella said:**
> It's left-handed. :popcorn:
Nope!

Most right-handed people shoot left, in hockey and cradle the puck with their left hand.

;)

---

### Post by ve4cib on 2012-02-12
Well, we in the lab consider the robot to be left-handed.  Once we get some extra motors installed in the arms so it can hold the stick two-handed it will be adopting a left-handed grip as well.  Technically the robot is ambidexterous though.  *shrug* Define robot handedness however you like.

---

