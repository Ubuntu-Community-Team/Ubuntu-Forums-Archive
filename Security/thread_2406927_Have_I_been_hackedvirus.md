---
title: "Have I been hacked/virus?"
date: 2018-11-27
forum: Security
---

### Post by friskadbc on 2018-11-27
I had a worrying event happen to me today on my Kubuntu installation of Linux. I don't know if it was a glitch, error, or virus effect but I don't want to take my chances. 

I was playing a video on MPV media player and out of nowhere MPV suddenly froze. Then suddenly my firefox browser couldn't be closed because the bar at the top of the application with the minimize and X (close) button had suddenly completely vanished at the same time and I was left with a frozen unclosable MPV application displaying it's big black square taking up 70 percent of my monitor screen 

it left me with the only option of rebooting the computer because MPV would be at the forefront of any app I opened, making it extremely hard to view anything.

could this be the sign of a virus?

---

### Post by T.J. on 2018-11-28
It's very unlikely, Friskadbc.  I mean no disrespect to the community, but Ubuntu is based on Debian Unstable. From the sound of things, you hit a bug. When you lose the top bar - it means that the part of the KDE system called KWin crashed.  It's happened to me on Ubuntu before.  In the defense of all concerned, it could also be a crash caused by a bug somewhere in the graphics stack, completely upstream with nothing to do with Ubuntu.

As a fix if it happens again, you can type "ALT+F2".  A command box will appear at the top of the screen.  Type in "exec kwin &" and enter.  This should restart KWin without exiting the session.

---

### Post by mastablasta on 2018-11-30
in 90's and 2000's virus often caused crashes or similar behaviours as they were made by trolls to annoy users. these days they have a purpose to steal data, so they will do anything they can to stay "below the radar" and not get detected.

your kwin crashed. it happens sometimes.

if you are still worried check the logs with log viewer or manually using Kate or similar text editor. logs can be found in /var/log

---

### Post by mcyber4 on 2018-12-02
In my case my screen went completely black and I needed to reboot. Looking back, I'm sure this was when the rootkit activated the remote desktop. But at the time I thought to have never had such, but reboot was fine and I forgot about.
A good idea is to compare the modified date of files.

---

### Post by pending... on 2018-12-06
Even though Ubuntu is not malwares proof, it's even less bugs proof. It means that before worrying about malwares, you should think about internal errors. Normally, a "good" malware is supposed to hide itself in such a way that it doesn't trigger any warning. It could happen if it was badly designed and/or technically complicated, such as a kernel mode malware. 

My 2 cents.

---

### Post by nyeba on 2018-12-07
I supposed the duration before it crashed was like about 30 mins? This happened to me on old version couple of times it freezes I thought I was hit by some virus but digging around I found out was a bug conflicting on the libraries so what I do is update to latest version and until now I haven't encounter any issue.

---

### Post by JayKay3OOO on 2018-12-08
Not used kubuntu forever, but last time I used it, bits of it would crash all the time.

---

### Post by QIII on 2018-12-08
On the other hand, I've been using Kubuntu for years with only the very rare odd crash, which has pretty much only happened when I've fiddled around with something.

Please take care to avoid FUD.

---

