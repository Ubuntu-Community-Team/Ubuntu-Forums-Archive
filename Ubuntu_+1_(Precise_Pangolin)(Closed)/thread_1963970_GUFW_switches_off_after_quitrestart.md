---
title: "GUFW switches off after quit/restart"
date: 2012-04-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Download Descendent on 2012-04-23
I don't really know if this an issue as I've never quite understood firewalls in Ubuntu and don't even know if I need one.

Anyway, using the daily build downloaded on Saturday evening.

Installed GUFW and unlocked it (needed password) switched it on - and when quitting the program, start the program again and it appears to have been turned off and need to unlock it and start again. I have tried altering a couple of preferences and it makes no difference.

Is anyone else having this problem.

---

### Post by dino99 on 2012-04-23
after giving the password to unlock it, the first setting is : status , and to activate it you need to see the "orange" switch.  "Incoming" is set to "Deny" & "Outgoing" is set to "Allow". Then you will see the rules into the screen below (no need to change them, except for special needs)

---

### Post by -Robert- on 2012-04-23
> **Download Descendent said:**
> 
Installed GUFW and unlocked it (needed password) switched it on - and when quitting the program, start the program again and it appears to have been turned off and need to unlock it and start again.
Same issue over here. But it is active, if you unlock gufw you can see it is still running. You just need superuser rights to see the true status.

What is the output of *sudo ufw status* ?

---

### Post by kansasnoob on 2012-04-23
I honestly don't think you need GUFW, nor do you need to change any settings in 'ufw' unless you need to allow something not allowed by the defaults, but this question would best be asked here:

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

In fact you may find your answer in the stickies there :)

---

### Post by Download Descendent on 2012-04-23
> **dino99 said:**
> after giving the password to unlock it, the first setting is : status , and to activate it you need to see the "orange" switch.  "Incoming" is set to "Deny" & "Outgoing" is set to "Allow". Then you will see the rules into the screen below (no need to change them, except for special needs)

Yes, I saw the orange switch - it was all fine.  It's just when I quit the program and restart it, it's as if it was never activated in the first place, eg I have to unlock it again and turn the switch to on and then see the 'orange'.  It does this every time.

---

### Post by Download Descendent on 2012-04-23
> **-Robert- said:**
> Some issue over here. But it is active, if you unlock gufw you can see it is still running. You just need superuser rights to see the true status.

What is the output of *sudo ufw status* ?

It says it's 'active' so it must be OK then.

Thanks for that.

---

### Post by Download Descendent on 2012-04-23
> **kansasnoob said:**
> I honestly don't think you need GUFW, nor do you need to change any settings in 'ufw' unless you need to allow something not allowed by the defaults, but this question would best be asked here:

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

In fact you may find your answer in the stickies there :)

Thanks, I will look through it.

I suspect I probably don't as I've not been prevented from doing anything either with it on or off.

---

### Post by Download Descendent on 2012-04-23
> **Download Descendent said:**
> Yes, I saw the orange switch - it was all fine.  It's just when I quit the program and restart it, it's as if it was never activated in the first place, eg I have to unlock it again and turn the switch to on and then see the 'orange'.  It does this every time.

OK - that's weird - having run the sudo etc when I go to the GUFW interface and unlock it it is already ON and orange.

Thanks

---

### Post by meborc on 2012-04-23
> **Download Descendent said:**
> OK - that's weird - having run the sudo etc when I go to the GUFW interface and unlock it it is already ON and orange.

Thanks

I guess it is security through obscurity :) people with no sudo rights should also not see what the firewall options are set.

seeing which ports are kept open could give the person possibility to plan his attack, although port scanners are quite common

---

### Post by jbicha on 2012-04-24
Right, gufw hides the firewall status until you authenticate.

Not sure whether that's the best idea or not, but ufw status works the same way.

---

