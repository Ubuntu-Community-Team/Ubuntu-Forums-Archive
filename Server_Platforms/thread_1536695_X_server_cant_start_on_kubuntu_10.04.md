---
title: "X server cant start on kubuntu 10.04"
date: 2010-07-22
forum: Server Platforms
---

### Post by ymann on 2010-07-22
pls, I am a new user of linux. 
I just installed Kubuntu (10.04), did some upgrades and updates then upon booting the computer wont go beyond the login page. at first it posted a message (Xsession:warning: unabele to write to /tmp; X session may exit with an error).
I followed some instructions from the net which asked that I do the following:
ctr+alt+f
aptitude clean of apt-get clean
cd /var/log
rm *.gz
rm *.0
rm *.1
rm  (all big files)
rm kern.log
rm syslog
reboot

after this, when I login it no more goes off, but the desktop wont still come on, instead a terminal (konsole) window is open but when I try start x it refuses.

(the only method I use to start my computer succesfully is though the recovery mode)

could some one help me out??????

---

### Post by arrrghhh on 2010-07-22
Perhaps if this was in the desktop support section, or the "Absolute Beginner" section it would get more attention.

You posted in the Server section of the forum, which by default doesn't include X :D

---

