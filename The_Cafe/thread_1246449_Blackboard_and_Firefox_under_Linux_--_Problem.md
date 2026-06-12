---
title: "Blackboard and Firefox under Linux -- Problem"
date: 2009-08-21
forum: The Cafe
---

### Post by samalex on 2009-08-21
Hi,

I'm using Firefox 3.0.13 under Ubuntu 9.04 and today I tried to access the discussion boards on Blackboard for my upcoming online class (starts on Monday) to find I can't reply or post new messages.  It's like the first time I go in and click Thread or Reply it loads fine, but after that it won't do it again.  I pretty much have to close out of Firefox and go back in.  What it's doing is just not showing the body WYSIWIG interface, only the subject textbox and Cancel/Save/Submit buttons.

I noticed under about:plugins it's using this:
File name: IcedTeaPlugin.so
The IcedTea Java Web Browser Plugin 1.4.1 (6b14-1.4.1-0ubuntu11) executes Java applets.

... instead of the Java runtime.  Could this be incompatible?  And would it be possible for me to install the java runtime and remove this?  I tried installing the Java JRE through Synaptic, but it wanted to upgrade to Firefox 3.5 which I tested with and Bb crashes with that.

So any suggestions?  Thanks -

Sam

---

### Post by SunnyRabbiera on 2009-08-21
Just install java, as for firefox 3.5 it might work better with the official java.

---

### Post by matthewbpt on 2009-08-21
Install the following:
```
sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin
```
What you are using is the open source Java plugin called IcedTea, and while it works for most things it doesn't always work, the official one is more reliable.

---

### Post by DeadSuperHero on 2009-08-21
I hope it works, I start school next week and would hate to have Blackboard crap out on me.

---

### Post by running_rabbit07 on 2009-08-21
I am so glad my school broke the contract with Blackboard and got the Angel Learning system.

---

