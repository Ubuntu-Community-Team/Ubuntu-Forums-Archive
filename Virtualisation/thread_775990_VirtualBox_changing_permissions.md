---
title: "VirtualBox changing permissions?"
date: 2008-04-30
forum: Virtualisation
---

### Post by ArtPulse on 2008-04-30
Hey there! As I couldn't find any html/php editor I like as much as Dreamweaver CS 3, and GIMP far from being like Photoshop CS 3, I use VirtualBox to work with them both.

Right now I'm re-designing a site so I've setup my Apache2 + PHP + SQL server on my ubuntu 8.10 desktop edition. The root is at /home/artpulse/public_html/

Problem is... well, when I save my index.php with Dreamweaver (index.php or any other file), refreshing [http://localhost/](http://localhost/) looks like this:
[B]
Warning:[/B] Unknown: failed to open stream: Permission denied in **Unknown** on line **0**
[B]
Fatal error:[/B] Unknown: Failed opening required '/home/artpulse/public_html/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in **Unknown** on line **0**

So every time I save a file, I must chmod it, like...

$ chmod 0755 public_html/*.*
(could have been index.php instead of *.*, whatever xP)

also did same with sudo, but either way the permissions seem to change every time I save with Dreamweaver. It's quite annoying to do this on each file I modify every time I wanna take a look at it. If I chmod it, starts working fine again.
Btw: yes, I've chmoded my public_html as well.

I access my /home/artpulse/ folder from my VirtualBox's Windows XP SP2 as a shared folder (i.e: x:\public_html\).

I've said all the info that was needed I believe to make a diagnose xP... Anyone knows what's going on? Any way to say "QUIT IT, THE PERMISSIONS ARE **THIS** WAY!!! DO NOT CHANGE THEM!!", maybe more politely and computer language? >.< I keep screaming that but it doesn't seem to work ;P

Thanks everyone!! ^^

---

### Post by ArtPulse on 2008-04-30
dudes? >.<

forgot to mention, mayb, if it wasn't clear... the host os is Ubuntu, and the guest os is windoze...

---

### Post by bornakke on 2008-12-04
I have the same problem... have you found a solution?

---

### Post by jel3 on 2008-12-14
same problem for me as well. except with external drive shared. every few minutes lately i've been losing write access on my drive. I'm using 7.10, this just started to happen like 4 days ago.

---

