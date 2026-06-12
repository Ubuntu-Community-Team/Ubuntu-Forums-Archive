---
title: "UFW/Iptables Firewall doubt"
date: 2010-12-04
forum: Security
---

### Post by ramujinius on 2010-12-04
Hi All

One quick question regarding firewall, since i didn't get any answer in my google search

In Ubuntu we open ports based on IP using iptables... But won't this be an issue if a malware or any program with malicious intention use that already opened port.

This could be avoided if the firewall is based on the App. 

Please let me know isn't a serious issue ?

---

### Post by Frogs Hair on 2010-12-04
Check out this thread. [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by QLee on 2010-12-04
[QUOTE=ramujinius]...
Please let me know isn't a serious issue ?[/QUOTE]
I don't know if you will be willing to take my assurance about this but it isn't a serious issue.
Even an open port is not a threat if nothing is listening for connection on that port and that is default for an Ubuntu install. You can have your firewall optioned to default "deny".

Do read carefully the documentation linked to by Frogs Hair.

---

### Post by The Cog on 2010-12-04
I think you are decieving yourself if you think you can make your system safer by trying to prevent the malware that has got into your system from making outgoing connections.

---

### Post by uRock on 2010-12-04
Moved to Security Discussions sub-forum.
> **The Cog said:**
> I think you are deceiving yourself if you think  you can make your system safer by trying to prevent the malware that has  got into your system from making outgoing connections.+1 If you get malware on your system, then it would have to have root permissions to run which means it will be able to shut off your firewall. You would have to enter your password to install the program containing the malware. That said be careful not to install something you are not sure of.

---

### Post by bodhi.zazen on 2010-12-05
This is not Windows, and security is different.

See:

[https://wiki.ubuntu.com/SecurityTeam/FAQ](https://wiki.ubuntu.com/SecurityTeam/FAQ)

[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)

[https://wiki.ubuntu.com/ZeroConfPolicySpec](https://wiki.ubuntu.com/ZeroConfPolicySpec)

So if there are no listing services, there is nothing to firewall.

The opposite is the case in Windows. In windows there are open ports, thus you need to add a firewall.

I also suggest you read the security stickies.

---

### Post by ramujinius on 2010-12-06
thanks all for the  links and advice
But still few things bothers me..

The malware which got installed without the awareness of the user, will not be affected by apparmor since it will not have any profile. And also the malware can communicate easily with the remote server since all the outgoing ports are open. Is it not easy for the program to read the local m/c confidential details (password, acc no) and pass it to remote m/c? 

I might be wrong at many places and so negative. Sorry for it :-)

---

### Post by bodhi.zazen on 2010-12-06
> **ramujinius said:**
> thanks all for the  links and advice
But still few things bothers me..

The malware which got installed without the awareness of the user, will not be affected by apparmor since it will not have any profile. And also the malware can communicate easily with the remote server since all the outgoing ports are open. Is it not easy for the program to read the local m/c confidential details (password, acc no) and pass it to remote m/c? 

I might be wrong at many places and so negative. Sorry for it :-)

A hypothetical application or in this case malware can do whatever it wants. This is because the application is run as root when you install it.

First there are no know malware applications that act the way you envision for Linux at this time.

Second, the real point here, do not install applications from untrusted sources. There really is not much, if anything, you can do to protect your system if you violate this second piece of advice.

---

