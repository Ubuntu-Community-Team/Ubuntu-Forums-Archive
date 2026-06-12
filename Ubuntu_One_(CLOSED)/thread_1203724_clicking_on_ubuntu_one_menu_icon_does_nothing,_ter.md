---
title: "clicking on ubuntu one menu icon does nothing, terminal way as well"
date: 2009-07-03
forum: Ubuntu One (CLOSED)
---

### Post by chriskin on 2009-07-03
i got the invitation so i installed it as the site said, but when i get to open it from the menu or the terminal , well nothing happens :)

in the system monitor i can see it running but that's all :O
no window appears, no tray icon, nothing :S

---

### Post by Sub101 on 2009-07-03
Have you tried running it as root from the terminal?

 I wouldnt enter any accounts etc but it may be helpful to determine if the installation works at all.

In system monitor what is the program called?

---

### Post by chriskin on 2009-07-03
sudo doesn't work either
it just hangs on the terminal , neither getting me an error, nor stopping.

as for the name it is ubuntuone-client-applet,

---

### Post by Sub101 on 2009-07-03
OK. I wasnt sure if maybe it was a server version you have downloaded. 

I would do a complete remove and try again, see if that solves the issue. 

Having looked on the website it looks like there is a facility for reporting issues, it may be worth asking them what they think on this one.

---

### Post by insertnewsn on 2009-07-03
I'm having this same problem.

The only thing I can see is from my sys.log..

Jul  3 23:10:08 insertnewsn-laptop kernel: [ 1654.079070] nautilus[3264]: segfault at 4 ip b5701e24 sp bfe454d0 error 4 in libnautilus-ubuntuone.so (deleted)[b56ff000+5000].

Not sure if this is the problem, but segfaults usually aren't good, right? :-)...

I can't find any info anywhere on systems having problems running Ubuntu One..so I really don't know where else to turn.

---

### Post by rwabel on 2009-07-04
same issue here. I've already tried to completely remove and reinstall...but nothing happens :-(

---

### Post by rwabel on 2009-07-04
please refer to the following bug report and you should be able to get it to work
[https://bugs.launchpad.net/ubuntuone-client/+bug/369038](https://bugs.launchpad.net/ubuntuone-client/+bug/369038)

---

### Post by thebear78 on 2009-07-04
I also created a Launchpad Answer for this issue.
[https://answers.launchpad.net/ubunet/+question/76131](https://answers.launchpad.net/ubunet/+question/76131)

---

### Post by brujoquizz on 2009-07-05
I think it's been after the last update...

---

### Post by par129 on 2009-07-05
I installed Ubuntu One with no problems that I can tell during installation. Once installed the app doesn't run/start when clicking on the icon in the Internet menu. Logged off and resarted but neither helped. Would like to completely remove and try again but don't know the exact names of the packages to remove from the package manager.

---

### Post by mevets on 2009-07-05
I installed ubuntone today and when  I launch it from the gnome menu it never shows up as an applet. I tried running 'ubuntuone-client-applet' from the terminal but it does the same thing and doesnt give me any output. I even tried killing gnome-panel, watching it regenerate, and crossing my fingers in hopes that it would fix things but it didnt.

Can anyone give me advice?

---

### Post by chriskin on 2009-07-06
for my problem, let's say that it solved itself

i tried it today and it works

ubuntu one is not good enough yet, not compared to dropbox etc, but i sure hope it will become better

---

### Post by thebear78 on 2009-07-06
The issue will be resolved very soon but read this in the meantime for the resolution.
[https://answers.launchpad.net/ubunet/+question/76131](https://answers.launchpad.net/ubunet/+question/76131)

---

### Post by mevets on 2009-07-06
thank you, that solved my problem it seemed that the tools package wasnt being installed.

---

