---
title: "Upgrade Obsolete package in 13.04. How?"
date: 2013-03-28
forum: Ubuntu Development Version
---

### Post by Lur G on 2013-03-28
Hello eveybody. I have ubuntu 13.04 and now I have problem with the package...Appears a large message in the desktop:
 "Problem in gvfs-backends" and follow with: You have some obsolete package versions installed. Please upgrade........
Well, How? Where? :confused:
Please guys, answers for beginers but fast learners!!
Thanks in advance: :)
LuR

---

### Post by Lur G on 2013-03-28
Hello eveybody. I have ubuntu 13.04 and now I have problem with the package...Appears a large message in the desktop:
 "Problem in gvfs-backends" and follow with: You have some obsolete package versions installed. Please upgrade........
Well, How? Where? :confused:
Please guys, answers for beginers but fast learners!!
Thanks in advance: :smile:
LuR

---

### Post by ManamiVixen on 2013-03-28
Why are you using 13.04? It is beta software and is intended for testers and enthusiasts. Unless you know exactly what you are doing, use 12.04 or 12.10 instead.

But to answer your question in case of ignoring my advice. In a terminal run "sudo apt-get update && sudo apt-get dist-upgrade"

---

### Post by mörgæs on 2013-03-28
Please don't double-post.
Merged.

Agree with Vixen: If you are new to this you should wait with 13.04 until, say end of May.

---

### Post by Lur G on 2013-03-28
Hello Manami Vixen....Well, I'm using that version because I don't know  why a friend of mine put in my laptop. I mean: I said him to install  12.04 or 12.10 and he installed this version because he said it was the  lastest.....I haven't idea about this....Well, do you recomended me to  change the version? 
Now I don't have sound in  my laptop.
And?

---

### Post by Lur G on 2013-03-28
Sorry for post double. It's my first time posting and I'm lost....Then, I must change the version?

---

### Post by ManamiVixen on 2013-03-28
Well, first, what laptop do you have? It's make and model please? Still yes, 12.04 or 12.10 is better for you.

---

### Post by Lur G on 2013-03-28
the terminal ask me for password? Which password? Any idea?
Thanks again great helpers!!
finally I will do it..

---

### Post by Lur G on 2013-03-28
compaq presario CQ-50. 32 bits

---

### Post by ManamiVixen on 2013-03-28
The password in terminal is your User Account Password, what you use to login to Ubuntu.
Also according to the Specs, the Compaq you have is 64Bit. 2.00GHz Dual-Core Pentium T3200. So you can use Ubuntu 64bit if you want.

---

### Post by ManamiVixen on 2013-03-28
Also, the sound issue is a bug in ALSA. Thats the sofware that controls the audio on a computer in linux.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/945957](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/945957)

You will have to wait for a fix. BUT the report say the Headphone jack works. Try plugging in external speakers or use headphones.

---

### Post by cariboo on 2013-03-28
Moved to U+1

---

### Post by Lur G on 2013-03-29
Guys, I have already upgrade the obsolete packaged and my laptop still without sound (with or without headphones) 
Any recomendation, please?

---

### Post by dino99 on 2013-03-29
Go & check the menu: System Settings -> Sound icon , then glance at the tabs to know about the detected sound hardware, which one is selected, and into the profile, which output is selected. And of course the Sound switch need to be "on", otherwise its muted.

---

