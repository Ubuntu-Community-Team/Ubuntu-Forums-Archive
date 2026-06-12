---
title: "how do you use Jack rack?"
date: 2009-04-19
forum: Ubuntu Studio
---

### Post by chkneater on 2009-04-19
How do you use Jack rack?  I have jack running fine, but cannot get any of the jack rack effects to work, even if I hit enable.

---

### Post by markbuntu on 2009-04-23
You have to connect jack rack to some input and output in the connections box before it can do anything.

---

### Post by chkneater on 2009-05-02
Yes yes.  As I stated I have Jack running fine.  I can record and everything.  The problem is actually using the effects.  I know what most of them are but some sound odd.  How do I actually apply the effects to the sound chain?

---

### Post by chkneater on 2009-05-02
Wait a minute, after analyzing your answer I realized that there is no connections box anywhere?  Could that be the problem?

---

### Post by bobince on 2009-05-02
Yeah, you'll need to connect up jack-rack's inputs and outputs. The easy manual way is to run qjackctl and hit the ‘Connect’ button.

---

### Post by B4RR13N705 on 2009-05-02
You have to connect inputs and outputs.
You'll see 2 columns. Like this ones:
> 
Jack Rack <----------|----------> System
System <------------|----------> Jack Rack

Connect the left "jack rack" to the right "System", and the left "System" to the right "Jack rack", and you should listen the effects.

---

