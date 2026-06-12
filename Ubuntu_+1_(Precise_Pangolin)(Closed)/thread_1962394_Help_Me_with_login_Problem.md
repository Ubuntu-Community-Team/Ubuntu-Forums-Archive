---
title: "Help Me with login Problem"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bverly on 2012-04-21
I need help, i can not login into my ubuntu..
I have the right password and username,
whenever i login the system show logging in...... but it never go through.
I can login through command line and Gnome classic...

---

### Post by masuch on 2012-04-23
I have the same problem. I am using xfce
And many many further problems - as usually within distro upgrade.
(It was working until I installed java oracle.)

---

### Post by masuch on 2012-04-23
> **masuch said:**
> I have the same problem. I am using xfce
And many many further problems - as usually within distro upgrade.
(It was working until I installed java oracle.)

My problem for unable to login was damaged file /etc/environment. I made copy of it from another ubuntu instance and I can login now.

---

### Post by gstvr on 2012-04-25
i found that you can install gdm (gnome desktop manager) as a workaround.


[LIST]
[*]boot to your login screen
[*]login in a console (ctrl+alt+F1)
[*]install gdm (sudo apt-get install gdm)
[*]select it as default in the settings screen showing up
[/LIST]

reboot. enjoy.

---

### Post by qaissi on 2012-04-25
Sadly I have the same issue.

Did the latest upgrades and rebooted and now I am stuck on the log in screen with it telling me it is logging in but nothing happens.

I can not log in to gnome either.

Kind of lost here.  I can do a Ctrl + Alt +F1 and log in there but don't hav any ideas what to do once I am there to rectify this problem.

I did try bverly's idea but nothing installed and of course I still can not log in.

Any hints would be appreciated

---

### Post by codingman on 2012-04-25
Does it give you any errors? Anything in particular? I always stay with the default login manager for beta releases, they are usually more stable :p

---

### Post by qaissi on 2012-04-26
No error messages at all.

When I type the password in and hit enter the password disappears and is replaced with the words "logging in ..." and then nothing.  I have left it for as long as a half hour and no change at all.

Now I can use shutdown option in the top right corner at this point.

I can hit the Escape key and the logging in message goes away and I get the password box back waiting for me to put a password in but it will not allow me to type into the box at that point.  Nor will it allow me to change which version of Ubuntu I can log into at this point.

It will let me choose to log in as a Guest but then it asks for a password and when I supply the guest password or even leave it blank it does exactly the same thing - "Logging in ..."

---

