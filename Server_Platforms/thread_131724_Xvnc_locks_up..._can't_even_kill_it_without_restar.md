---
title: "Xvnc locks up... can't even kill it without restarting..."
date: 2006-02-17
forum: Server Platforms
---

### Post by encompass on 2006-02-17
Even after a free boot... it seems that if I try to log into my vnc server I get issues with it locking up.  I have to ssh in and reboot the server so that it will work again.  I think the pattern to error is that I use the server inperson first then try to login.  But my wife logs into the system all the time.  On the windows side using vncviewer it won't ask for the password to get in nor will it tell me an error.  it has not processer usage and seems to be just waiting.
If I reboot the computer... then vncveiwer on the windows side tells me I have been disconnected.
Veiw the process whill ssh'ed in show Xvnc using 99.9 percent of the CPU, but I am able to do everything with out problem.  It doesn't seem to be filling memory either.
Any ideas?  I am willing to provide you will any other test cases you may need.
Thanks,

---

### Post by tonkatruck on 2006-02-18
this is what happens when you use debian .....

---

### Post by encompass on 2006-02-19
Linux is Linux.... anyone else have any ideas?  Perhaps there is some log that I can find the information about the crash on... BTW it is a sefe shutdown and restart and the system doesn't seem to be slowed at all by Xvnc even though it says 99.9 percent or processor use.

---

### Post by motherofberyl on 2006-02-19
i have the same problem, if anyone has any wise words, please let me know...

---

### Post by encompass on 2006-03-05
Gosh, seems like no one knows the solution or we are left in the dark here.  Bummer.

---

### Post by xxMEL0Nxx on 2006-03-23
Hi, I have the same issue but I don't need to restart the server, I stop the gdm "sudo /etc/init.d/gdm stop" then i can kill Xvnc "killall xvnc" after that I can start gdm again "sudo /etc/init.d/gdm start" and after that I can use vnc again. I've been runing xvnc for 2 months and last week this started, this happen randomly and I'm looking for a solution.

---

### Post by kmi on 2006-03-24
Hello,
More/less the same problem here...
I have followed [this]("http://ubuntuforums.org/showthread.php?t=122402&highlight=resume+vnc") how-to and replaced vnc-common and vnc related packages with the vnc4-common and vnc4 related ones.
Now I can log in and log out BUT I also experiment 99,99% CPU usage after the first log out.
Now if I don't log out but just close the client application, there's no 99,99% CPU issue and I think (I will re-check....) no one else in my local network but me can log in whithout the password... that is my solution... don't know if it's good either...:-k
I know it is not a real solution - as a session is active and uses resources - and hope, like you, somebody has the beginning of a solution (and I'm not talking 'bout FreeNX which seems very good though ;) ).

---

### Post by rich on 2006-03-24
Does it make us more or less miserable knowing we are not alone ?

I've also had to walk away from xvnc - like you I've found it topping out, and again without really breaking anything else. 

I installed it via a howto here using xinetd, and while it can't be killed it can be stopped using xinetd.


Rich

---

### Post by encompass on 2006-03-24
> Does it make us more or less miserable knowing we are not alone ?
I do feel alone...in an answer! I wonder if we used the same howto, I can remember the one I used, but it was in such a way that I enter the pass with no username, it then takes me to the gdm login.  Sound like yours?  perhaps it is something with the howto and a bug that is brought out by it. shizzle :???:
but props to the guy with the work around. /me gives props..

---

