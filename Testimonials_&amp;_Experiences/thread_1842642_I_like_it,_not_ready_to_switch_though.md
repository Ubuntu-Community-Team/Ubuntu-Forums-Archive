---
title: "I like it, not ready to switch though"
date: 2011-09-11
forum: Testimonials &amp; Experiences
---

### Post by jedispork on 2011-09-11
Sometimes when I get bored I will install the latest ubuntu and test it out for a while.  I am very impressed and could see using it as a primary os however I still have some issues with it. 

I have samba shares setup on a ntfs drive.  Nautilus does not setup ntfs shares properly so I had to do some digging on forums. I found instructions on editing the samba config file to set it up as a user share and that solved the issue.  Later when I'm accessing the shares things stop working. So I go over to see what happened and the computer went into (s3) sleep mode.  I make my way back here and do some searching and apparently there isn't a feature in ubuntu to keep it awake when samba is in use.  I found some complicated instructions for installing a script but didn't think it was worth the trouble or if it would keep working with future releases. All the focus is on unity but what I would really want is for the computer not to sleep when using a share. 

I also didn't like having to enter a password or press the power button to wake it up from sleep. I was able to do more digging and find instructions to disable the password when coming out of sleep but that is a option that should be more easily accessible. Not sure if there is a solution to wake on keyboard press but its silly this isn't a easily accessible option as well. Brasero also messed up and wouldn't eject a disc. IMG burn in windows is a much more finished product and I've heard it works well with wine so I might try that next time. 

I can get by on windows 7 only but not ubuntu by itself unfortunately. I don't hate windows but I think ubuntu is better for everyone. I don't plan to buy anymore windows upgrades but 7 should be good enough until ubuntu improves even more.

---

### Post by horned0wl on 2011-09-11
Hm. Haven't had that problem since Ubuntu 8.04. Didscovered that if I went into Synaptic and simply installed everything that said either Samba or smb, it usually came out right, and I could comfortably network windows, mac and linux machines all on the same network, wired or wireless, and share whatever files I'd given the permissions for.  My whole home network is Ubuntu, but I have guest winderz machines on my net all the time...

---

### Post by jedispork on 2011-09-12
after adding a line to the samba config so the permissions work properly for ntfs that part is fine now. My complaint is that there is no easy way to keep it from going into sleep mode while samba is in use. 

I've also been looking around for some help to wake on keyboard and found several unanswered posts and or info that doesnt work with current ubuntu. Seriously waking from the keyboard is a most basic feature and I'm surprised there isn't more posts about it. A few simple missing features is what keeps me on windows. For instance I won't use google chrome because there is no way to disable history without going incognito which also disables your cookies.  So I stay with firefox.

---

### Post by jasonrisenburg on 2011-09-13
This should make it perfect for you, or at least till you find another reason why Ubuntu isn't good enough to use...lol.
use.[http://www.liberiangeek.net/2011/03/disable-screensaver-lock-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/03/disable-screensaver-lock-ubuntu-11-04-natty-narwhal/)

---

### Post by Tamlynmac on 2011-09-13
> jasonrisenburg
This should make it perfect for you, or at least till you find another reason why Ubuntu isn't good enough to use

Great statement. I hope you don't mind if I quote you periodically.:lolflag:

---

### Post by jedispork on 2011-09-13
> **jasonrisenburg said:**
> This should make it perfect for you, or at least till you find another reason why Ubuntu isn't good enough to use...lol.
use.[http://www.liberiangeek.net/2011/03/disable-screensaver-lock-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/03/disable-screensaver-lock-ubuntu-11-04-natty-narwhal/)

Not quite, as I mentioned before this doesn't work when coming out of s3 sleep. You have to change a few more settings in gconf editor. Thats what I meant about this option not being easy to find.

---

