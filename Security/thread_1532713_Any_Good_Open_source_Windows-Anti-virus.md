---
title: "Any Good Open source Windows-Anti-virus?"
date: 2010-07-16
forum: Security
---

### Post by pato wlmc on 2010-07-16
You'll see, I have to take my flash drive to my school's PC ( Running WinXp ) everyday, which, of course, is full of virus.

Not a big problem for me since I'm using Linux (Ubuntu Lucid). But today when I plugged it back to my PC i saw that f*cking autorun.inf on it, I just deleted it, but then i saw it was on my /home folder, again, I just deleted it, but it really bothers me to have Win viruses in my flash drive, because all my brothers, sisters ( uncles, and everyone in my family ) uses windows so..

I know i can actually use wine, but you have to pay for most of the good anti-virus software for windows.

So Any suggestion

---

### Post by UbuNoob001 on 2010-07-16
Hey there,
   My understanding is that the primary AVs, which you can get through apt-get/software sources, all scan for Win. viruses. In fact, because basically all viruses are windows viruses this is what they scan for. These are all GPL or Free/Open software. Check the repositories. 

    Check out Clam AV.

---

### Post by ST3ALTHPSYCH0 on 2010-07-16
1. Autorun is not a virus (although it can be infected by several)
2. ClamAV is in the repos (sudo apt-get install clamAV... sudo apt-get install clamTK if you want a GUI)
3. ClamAV is also available for Windows and Mac
4. I've been using Avast Free for at least 12 years, and have been virus free (It's even disallowed me to go to sites that have been redirected and hijacked).
5. Avast is also available for Linux.

---

### Post by bodhi.zazen on 2010-07-16
See [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

There is a HIDS thread

[Host-based Intrusion Detection Systems (HIDS)]("http://ubuntuforums.org/showthread.php?t=1477662")

And on that thread is information re: Antivirus.

There is also

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

In general, antivirus software for Windows does a better job.

---

