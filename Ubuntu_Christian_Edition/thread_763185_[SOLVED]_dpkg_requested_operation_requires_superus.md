---
title: "[SOLVED] dpkg: requested operation requires superuser privilege"
date: 2008-04-22
forum: Ubuntu Christian Edition
---

### Post by Pursuer on 2008-04-22
When I tried to follow the directions to manually configure > dpkg --configure -a, the header of my thread is the message I got.
Where/how can I show the system that I am a superuser to the computer, or is that not possible?
*Sigh* Sorry for the ignorance, and thank you so much for any help you can offer this pathetic momma.

---

### Post by Diabolis on 2008-04-22
```
sudo dpkg --configure -a
```
1.- **su** will log you in as root, you don't really need it
2.- **sudo** will log you in as root for a limited amount of time. I think it gives you 15 minutes, not sure.

---

### Post by Pursuer on 2008-04-23
Well, I tried the sudo superuser command, and then tried to install net responsibility. I received this message:

> E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)

Do you know what missing arch there may be?

---

### Post by Diabolis on 2008-04-23
The error is related to java. Try this:
```
sudo apt-get install sun-java6-bin
```

---

### Post by Pursuer on 2008-04-25
You are awesome for your help.

I did as you said, and got this message:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-00-2ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I tried doing what it said to do, and got this message:
> E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

And when I tried to enter yes, it gave a successive list of
y
y
y
etc.


Thank you.

---

### Post by Diabolis on 2008-04-25
Seems like you are getting used to the terminal and its error messages, cool.

Most of the times solutions are siting just in front of you, it's a matter of taking your time to read and understand what error messages say.

[Don't forget to mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by Pursuer on 2008-04-26
No, no... definitely not solved. the last post I made is where I left off. I even tried doing the sudo dpkg --configure -a again, to let it know I am the root, but it did nothing.
Totally not solved. Sorry about that.

---

### Post by Diabolis on 2008-04-26
Did you have to terminals running apt-get or Synaptic package manager open while trying to use apt-get in terminal? That will give you a similar error. Synaptic in the inside uses apt-get, apt-get uses dpkg and you are not allowed to run multiple instances of dpkg.

Go to: system / administration / synaptic package manager / edit / fix broken packages

---

### Post by Pursuer on 2008-05-07
Fantastic!!! You did it! Thank you, thank, you, thank you. :) I'd send you some of my handcrafted all natural laundry soap and some cookies, if I could!

---

### Post by msgtoram on 2008-08-23
Thanks a lot, I got the same problem and able to resolve with your help.

Thanks Again.

---

