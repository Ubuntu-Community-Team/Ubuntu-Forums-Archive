---
title: "ISS Attack/Defend advice"
date: 2009-11-13
forum: Security
---

### Post by technicallygeek on 2009-11-13
As an Information Security student as part of our final labs we split into two teams both were to setup servers the opposing team was tasked with finding vulnerabilities within the others server and exploit. I was part of the attacking team, and will be on the defending team this coming week.

My team will be using Ubuntu for our server, I was reading the sticky on IDS and that seems to be fitting for our needs. One of the things the team will need to setup is a simple web page that we must defend. 

I read in the IDS sticky that using snort will enable apache. Is there a way to harden the apache that will be installed along with snort? 

Im not looking for someone to hold my hand or do my work. If I can get pointed in the right direction that would be great...

---

### Post by XCan on 2009-11-13
I don't know much about hardening apache, but I just think your project is very cool. Would indeed be interesting to hear about the do's and don't do's once you're finished. :)

---

### Post by technicallygeek on 2009-11-13
The other team was running a Windows 2003 server with IIS, DHCP. As I was on the attacking team I was the only one using a linux system to probe and attack. I did manage to get THC Hydra installed with a gui which didn't really help much. 

We did manage to find a hole in the FTP with annon login and write files to the system. Our main objective as to bring their web page down.

---

### Post by Velnias on 2009-11-14
Well, for defense you can install OpenBSD with  Apache ( it's bundled with OS and hardened, so you need just enable it ) and easy win!

---

### Post by rookcifer on 2009-11-15
Use hardened-gentoo with PaX enabled.  Then be sure to write some anal SELinux rules.  Let's see if anyone in your class can crack that.

---

### Post by mihalisla on 2009-11-16
You should definitely use apparmor to easily secure you apache server!!!
You can also find profiles from zazen in the apparmor thread from this forum.
Then there is no way they can exploit your server through apache.
Apparor is installed by default in ubuntu and you should install apparmor-profiles.I think there is one profile ready for apache that it should do!

Good luck!!!

PS. Do not forget to put your profile after installing apache to enforce mode "sudo aa-enforce .....apache (I don't remember the exact path it should be sth in /etc/apparmor.d/usr.sbin.apache or like)

---

### Post by mihalisla on 2009-11-16
Also post how the battle went!!!
It is very interesting

---

