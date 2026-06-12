---
title: "Hacked?"
date: 2010-02-22
forum: Security
---

### Post by illy123 on 2010-02-22
This evening I was installing boxee and xbmc on my unbuntu computer via vnc as I am away from home. When I opened firefox my home page was changed from google.co.uk to gay.com.  I have no idea how this happened; given that I have got ftp,vnc,apache, ssh servers running on it should I shut it down completely?  Thanks

---

### Post by jrusso2 on 2010-02-22
Suspects a vnc easily hacked.

---

### Post by cariboo on 2010-02-22
+1 probably a weak VNC password.

---

### Post by hackertarget on 2010-02-22
Maybe your flat mate was visiting that site....   :)

If you are using vnc externally I suggest tunnelling vnc over ssh and only having ssh open to the world, on a high port with strong passwords.

If your vnc session has been hijacked, they may have added back doors / new accounts or root kits.

Best option is a full rebuild unfortunately.

---

### Post by illy123 on 2010-02-23
I usually tunnel it over SSH but I got a bit lazy this one time.  The first time I connected today was at a uni library, and the second time in my halls - this is a social science institution so there are very few lurking computer geeks. I turned the PC off yesterday so that I can decide what to do.     Would changing all the passwords on the machine and terminating vnc port forward so that I am forced to use ssh not be enough?

---

### Post by HermanAB on 2010-02-23
Howdy,

There are two problems with using VNC:
1. Ubuntu does not enforce the use of secure passwords in PAM.  This is a serious oversight on the part of the Ubuntu developers.
2. VNC is an insecure system and automatic exploit scripts for it are widely available and deployed on the net.

So the bottom line is pretty much this:
Use VNC on Ubuntu == get your box hacked

There are many a tale of woe on these forums from people with the same unfortunate experience.

Soooo, you got to re-install.  Sorry...

---

### Post by illy123 on 2010-02-23
Thanks very much for all the replies.  What are the chances that the one time I'm too lazy to use an ssh tunnel this happens?  

Retracing my steps the times I connected without the ssh tunnel - once in my university library (I didn't think anyone would be sniffing there), once in my halls, once on my android via 3g. 

If the attacker changed my firefox homepage then I guess the chances are he was just mucking around - if he were to install a backdoor then surely he would rather make his presence invisible. Also I maybe have entered my account password on one occasion but I'm not sure what the chances of him getting it were (and so install any software).  Reinstalling would be a big pain: given that installing moodle took me a long time - however if necessary then I will.  

Do you think that if I change all my passwords (I've already removed vnc portforwarding; sticking with just ftp, apache, ssh) and run rootkit hunter along with clam antivirus I will get away with not having to reformat?  Thanks again.

---

### Post by cdenley on 2010-02-23
> **illy123 said:**
> Thanks very much for all the replies.  What are the chances that the one time I'm too lazy to use an ssh tunnel this happens?  

Retracing my steps the times I connected without the ssh tunnel - once in my university library (I didn't think anyone would be sniffing there), once in my halls, once on my android via 3g. 

If the attacker changed my firefox homepage then I guess the chances are he was just mucking around - if he were to install a backdoor then surely he would rather make his presence invisible. Also I maybe have entered my account password on one occasion but I'm not sure what the chances of him getting it were (and so install any software).  Reinstalling would be a big pain: given that installing moodle took me a long time - however if necessary then I will.  

Do you think that if I change all my passwords (I've already removed vnc portforwarding; sticking with just ftp, apache, ssh) and run rootkit hunter along with clam antivirus I will get away with not having to reformat?  Thanks again.

What is more relevant is whether your VNC server was directly accessible from the internet, not whether or not you tunneled your connection through SSH. Your VNC session probably wasn't compromised, but your VNC server probably was. There is no definitive way to determine how many people connected via VNC or what they may have done to your system. You can check logs, but attackers sometimes modify logs to cover their tracks. The only way to be 100% safe is to reinstall.

---

### Post by illy123 on 2010-02-23
> **cdenley said:**
> What is more relevant is whether your VNC server was directly accessible from the internet, not whether or not you tunneled your connection through SSH. Your VNC session probably wasn't compromised, but your VNC server probably was. There is no definitive way to determine how many people connected via VNC or what they may have done to your system. You can check logs, but attackers sometimes modify logs to cover their tracks. The only way to be 100% safe is to reinstall.

Yes, I had ported 4900 forwarded on my router (embarrassing I know :D)

I've done a bit of sniffing on my network (wpa handshakes, mitm) and I was only able to get my VNC passwords - would I be correct in thinking that this is the only password the intruder sniffed out? If so, he would not have gotten my account passwords and the only things he could do would not have required root privileges.

What is weird is that I checked my router's log (I have very secure passwords for the router and my wifi network so I would be surprised if he could have bruteforced with hydra or something) and I couldn't find a reference to a VNC connection.

Out of interest when I was installing boxee and XBMC I had to add 3rd party repositories - is it possible that one of them was slightly 'dodgy'?

---

### Post by cdenley on 2010-02-23
> **illy123 said:**
> 
Out of interest when I was installing boxee and XBMC I had to add 3rd party repositories - is it possible that one of them was slightly 'dodgy'?

Installing 3rd party software is always a security risk. You basically entrust your system to the third party. The safest approach is to trust only the ubuntu repos.

It is possible somebody intercepted your password, but probably more likely is somebody guessed your password. If the VNC password is different than the user password, then they probably didn't gain root access. However, there are all sorts of malicious things they could have done to your home directory, and they very well may have managed to escalate to root privileges somehow.

---

### Post by illy123 on 2010-02-23
> **cdenley said:**
> Installing 3rd party software is always a security risk. You basically entrust your system to the third party. The safest approach is to trust only the ubuntu repos.

It is possible somebody intercepted your password, but probably more likely is somebody guessed your password. If the VNC password is different than the user password, then they probably didn't gain root access. However, there are all sorts of malicious things they could have done to your home directory, and they very well may have managed to escalate to root privileges somehow.

I see. Thanks for your input once again.

Would running chkrootkit and rkhunter not be safe then? If it is highly recommended that I reinstall then I guess I probably could (one of the reasons I had vnc was because this was running as an ftp, ssh, apache server without a monitor), will be an inconvenience but at least I learnt a lesson.

I have different passwords for everything; most are 15 chars with symbols, upper, numbers and yet my server had it's VNC port forwarded for the whole internet with a dictionary password. Lol, how stupid is that?

---

### Post by cdenley on 2010-02-23
> **illy123 said:**
> 
Would running chkrootkit and rkhunter not be safe then?

It would be safe to run either one, but running it does not guarantee it is safe to continue using the server. You have to decide how important absolute certainty that your server is clean is to you.

---

