---
title: "Spurious &quot;Out of Space&quot;"
date: 2010-10-15
forum: Ubuntu One (CLOSED)
---

### Post by rickbeton on 2010-10-15
When I log in, I get a pop up saying I'm out of space and asking would I like to upgrade. I thought I get 2Gb for free - only 12Mb used so far.

What's wrong? Any ideas?

Rick

---

### Post by rickbeton on 2010-12-01
Ubuntu One has stopped doing it now. Presumably the bug has been fixed.

Rick

---

### Post by Pifilatakanemu on 2010-12-01
Just in case you want more space: with Dropbox you can reach up to 18GB of free space. Plus it works on other platforms. 

Check out the link in my signature and use the edu-optiobn to double the free space you get per referral.

---

### Post by grahammechanical on 2010-12-02
Did you perhaps do a complete re-installation? I did the other week and I got the same message. It went away like for you. And Ubuntu One is working as it should.

Regards.

---

### Post by glendavee on 2010-12-03
I had same problem, contacted ubuntu one help. This is their reply (the fix works) :

[COLOR="Red"]Sorry for the hassles with the pop up message. This is a bug affecting
some people on Ubuntu 10.10. We're working on fixing it. In the mean
time, you can get rid of this pop up by doing the following:

1. Open Applications > Accessories > Terminal and run:
sudo rm /usr/lib/gnome-settings-daemon-2.0/libubuntuone.so

2. Log out and login in to Ubuntu (or just reboot)[/COLOR]

---

