---
title: "jack realtime issue"
date: 2009-10-25
forum: Ubuntu Studio
---

### Post by jgrealish on 2009-10-25
Hello All.

I've upgraded to 9.04 64 bit (works great---except) not able to set Jack in real time mode. I've read about nightmares doing a RT kernel patch. Has anyone here experienced these problems, found fixes, or can suggest a workaround?

---

### Post by kayosiii on 2009-10-25
for me at least the rt kernel for Jaunty caused more problems than it solved. The stock kernel though is really quite excellent for a non realtime patched kernel.

The realtime kernel in Karmic 9.10 due out very soon now is working very well for me.

---

### Post by AutoStatic on 2009-10-26
Hello jgrealish, I use the 2.6.31-9 rt kernel from this PPA: [https://launchpad.net/~dnjl/+archive/kernel](https://launchpad.net/~dnjl/+archive/kernel)
Works well for me. The 9.10 rt kernel is also 2.6.31-9 isn't it?

---

### Post by raboofje on 2009-10-26
> **jgrealish said:**
> I've upgraded to 9.04 64 bit (works great---except) not able to set Jack in real time mode. I've read about nightmares doing a RT kernel patch. Has anyone here experienced these problems, found fixes, or can suggest a workaround?

If I'm not mistaken (pasting the exact error might be helpful), problems starting jack in realtime mode aren't caused by using a non-rt kernel, but by failing to configure your limits.conf to give jack elevated 'real-time' thread priority.

[http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf)

---

### Post by AutoStatic on 2009-10-26
You're right. You could also try to create a group 'audio' (System - Administration - Users and Groups) and modify your /etc/security/limits.conf file according to the settings in the Linuxmusicians Wiki or the settings mentioned in the Real-Time Support paragraph of the UbuntuStudioPreparation help page: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by jgrealish on 2009-10-26
Thanks everyone for the help! I had jack working well in 7.04 32bit but took the dive and bought an AMD X4 and upgraded ubuntu as well. Its been so long since I set up Jack that, yes, I could have my configuration wrong. Possibly, could one of you point me to a thread with a working setup file. I've already created an Audio group and made myself a member.

---

### Post by AutoStatic on 2009-10-27
You're welcome!
What are your current JACK settings? And what kind of soundcard are you using?

---

