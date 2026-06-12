---
title: "My machine got cracked (Ubuntu 11.04)"
date: 2011-10-12
forum: Security
---

### Post by Graham17655 on 2011-10-12
Ok, so it was my fault.
I had port forwarding switched on for SSH and had a weak user name and the same password, but I stupidly thought that won't happen to me.
 
What happened to make me think this:
SSH from a my netbook to my desktop on the same internal network I was greated with the fact that I had logged on from <IP address>. Normally it mentions the computer name. I did a reverse IP lookup on the address to find it is in Madrid, Spain. I am in the UK.
 
Type history and loads of commands appear which not only do I not understand but I certainly don't recognise.
 
I then look at /var/log/auth to find that there have been loads of attempts at logging in. There were loads of usernames attempted and they seemed to be in alphabetical order. It is unfortunate that my username also began with an 'a' and then the unfortunate login from Spain.
 
My password had also been changed. Was the first thing on the history which I did not recognise, so when I attempted sudo poweroff' I couldn't do it.
 
I think I have some sort of bot net / eggdrop installed in /var/tmp by the person from Spain.
 
So where do I go from here?
There was nothing of great use to the hacker / cracker as this machine was used for recording satellite telly and streaming it to the rest of the house. Is it best to start again from scratch and re-install or try to unpick whatever has been messed around with. Is there any way of making sure that it was the only machine in the house that was effected. There is a windows machine and a NAS drive on the same network along with my netbook Linux machine?
 
Any advice greatfully accepted. I know that I need a new username / password policy! I have already changed all my other passwords on various internet sites.
 
To the hacker,
Thanks, but you won't get in next time. SSH forwarding is switched off and so is the machine.

---

### Post by Dangertux on 2011-10-12
> **Graham17655 said:**
> Ok, so it was my fault.
I had port forwarding switched on for SSH and had a weak user name and the same password, but I stupidly thought that won't happen to me.
 
What happened to make me think this:
SSH from a my netbook to my desktop on the same internal network I was greated with the fact that I had logged on from <IP address>. Normally it mentions the computer name. I did a reverse IP lookup on the address to find it is in Madrid, Spain. I am in the UK.
 
Type history and loads of commands appear which not only do I not understand but I certainly don't recognise.
 
I then look at /var/log/auth to find that there have been loads of attempts at logging in. There were loads of usernames attempted and they seemed to be in alphabetical order. It is unfortunate that my username also began with an 'a' and then the unfortunate login from Spain.
 
My password had also been changed. Was the first thing on the history which I did not recognise, so when I attempted sudo poweroff' I couldn't do it.
 
I think I have some sort of bot net / eggdrop installed in /var/tmp by the person from Spain.
 
So where do I go from here?
There was nothing of great use to the hacker / cracker as this machine was used for recording satellite telly and streaming it to the rest of the house. Is it best to start again from scratch and re-install or try to unpick whatever has been messed around with. Is there any way of making sure that it was the only machine in the house that was effected. There is a windows machine and a NAS drive on the same network along with my netbook Linux machine?
 
Any advice greatfully accepted. I know that I need a new username / password policy! I have already changed all my other passwords on various internet sites.
 
To the hacker,
Thanks, but you won't get in next time. SSH forwarding is switched off and so is the machine.

Sorry to hear your system got owned :-/ 

What I would suggest since you said there was no critical data is backing up any data you may wish to keep, then just doing a reinstall. If you want to disect logs just grab your entire /var/log directory, as well as your bash_history and profiles also a capture of environment. You can post them up if you want (note there may be sensitive information in some of your logs). Of particular interest will be syslog and auth.log Or just look at them yourself.

Ultimately there is a good chance the attacker did something to maintain their access, at least in the form of adding a user, potentially something more subversive. However, it's easiest just to wipe it and start from scratch.

Instead of passwords I would recommend public key authentication, and something like denyhosts or fail2ban next time just to be safe. 

Hope that helps.

---

### Post by Jonathan L on 2011-10-12
> **Graham17655 said:**
> Ok, so it was my fault.
I had port forwarding switched on for SSH and had a weak user name and the same password, but I stupidly thought that won't happen to me.
 
What happened to make me think this:
SSH from a my netbook to my desktop on the same internal network I was greated with the fact that I had logged on from <IP address>. Normally it mentions the computer name. I did a reverse IP lookup on the address to find it is in Madrid, Spain. I am in the UK.
 
Type history and loads of commands appear which not only do I not understand but I certainly don't recognise.
 
I then look at /var/log/auth to find that there have been loads of attempts at logging in. There were loads of usernames attempted and they seemed to be in alphabetical order. It is unfortunate that my username also began with an 'a' and then the unfortunate login from Spain.
 
My password had also been changed. Was the first thing on the history which I did not recognise, so when I attempted sudo poweroff' I couldn't do it.
 
I think I have some sort of bot net / eggdrop installed in /var/tmp by the person from Spain.
 
So where do I go from here?
There was nothing of great use to the hacker / cracker as this machine was used for recording satellite telly and streaming it to the rest of the house. Is it best to start again from scratch and re-install or try to unpick whatever has been messed around with. Is there any way of making sure that it was the only machine in the house that was effected. There is a windows machine and a NAS drive on the same network along with my netbook Linux machine?
 
Any advice greatfully accepted. I know that I need a new username / password policy! I have already changed all my other passwords on various internet sites.
 
To the hacker,
Thanks, but you won't get in next time. SSH forwarding is switched off and so is the machine.

Hi Graham

Sorry to hear of your problems.  It's shocking but educational.  Even a small web site can get people trying the car doors at several hertz.

CALM / COLLECTED / QUARANTINED / CHECKED / CANCELLED

1.  CALM.  Unplug the compromised machine from your networks and switch it off until you have a plan.

2.  COLLECTED.  Think of what the person would be able to do from the compromised machine, and what kind of trail that might leave.  Find the logs on the other machines for the corroborration.

3. QUARANTINED.  Boot your compromised machine single-user, ideally from a Live CD, and look for your evidence in log files etc.  History files showing ssh or port scans on your other machines?

4.  CHECKED.  If you want more help from the forums, copy bits of log files to a USB key and post them.  Corroborate anything you can from one log to another.  (This is when you're grateful for NTP!)  Don't bring your system up multi user and don't plug it in to the network.

5.  CANCELLED.  Reinstall from scratch on the compromised machine.  There's no point wasting your time trying to find every single thing a person did, unless you want the education. 

A good thing to think about for your new, improved, stable doors is how to do your logging.  For systems I've really cared about, I've set up two syslog receivers, in different buildings, one of which had no network access except syslog inwards (ie, no way to log in).  When we had trouble we could compare the logs of the locked one to the normal accessible one.  I think we only really used it twice, but it caught the bad guys both times.

Hope those are of some help.

Kind regards,
Jonathan.

---

### Post by Dangertux on 2011-10-12
Just another thing, I wouldn't work too hard at scrutinizing your log files they are likely sanitized. If they aren't, the odds are against you that your machine was cracked from an already compromised machine. So IMO I would just move on with daily life, reconstruct the system with a better set of credentials and not sweat it too much. That's just me though.

---

### Post by dFlyer on 2011-10-12
Reinstall and secure the system better.

---

### Post by CharlesA on 2011-10-12
> **Dangertux said:**
> Just another thing, I wouldn't work too hard at scrutinizing your log files they are likely sanitized. If they aren't, the odds are against you that your machine was cracked from an already compromised machine. So IMO I would just move on with daily life, reconstruct the system with a better set of credentials and not sweat it too much. That's just me though.

+1. If you really wanted to see what all they did, you can clone the box and install it into a VM with no network access and poke around.

---

### Post by Soul-Sing on 2011-10-12
> **CharlesA said:**
> +1. If you really wanted to see what all they did, you can clone the box and install it into a VM with no network access and poke around.


please don't. do not mess around with cracked things.
You do not know in what scene you're in.
Stay away from it, don't get involved, reinstall your op system.

---

### Post by Dangertux on 2011-10-12
> **leoquant said:**
> please don't. do not mess around with cracked things.
You do not know in what scene you're in.
Stay away from it, don't get involved, reinstall your op system.

It's a valid point, but I think that may be a little bit doom and gloom :-)

I don't see any reason why sticking it on a VM and taking a closer look would hurt anything, so long as you confine the VM safely. Judging from the nature of the attack I would speculate there won't be anything amazingly advanced found.

---

### Post by CharlesA on 2011-10-12
> **Dangertux said:**
> I don't see any reason why sticking it on a VM and taking a closer look would hurt anything, so long as you confine the VM safely. Judging from the nature of the attack I would speculate there won't be anything amazingly advanced found.

Yep. The most important thing to do is to make sure the VM doesn't have network access so it isn't doing "bad stuff" while you are poking around. The VM shouldn't have access to the host drives either.

---

### Post by Graham17655 on 2011-10-13
Thanks for all the help and support.  I'll reinstall this weekend with the new version of Ubuntu.  I am interested and somewhat worried with what was done with my machine on my internet connection.  What if it was my machine that brought down the blackberry service? Am I liable?  I did phone BT to explain that my machine had been hacked.  I didn't expect any linux support but I did get a call back saying that they would find out if my machine had done any damage anywhere on the internet and put it right for me.  I didn't expect that and I'm not sure if it was all talk.
 
The first thing I'll do is pull the LAN cable out the back before I look at anything.  If I find anything I'll post it here via a live disc, but to be honest I feel much happier reinstalling from scratch.  
 
Thanks again
Graham./

---

### Post by CharlesA on 2011-10-13
Reinstalling would be way easier then trying to figure out what they did and how to fix it, so +1 to that. :)

---

### Post by bodhi.zazen on 2011-10-13
It sort of depends on what, if anything you wish to do.

IMO the time to learn forensics is not now, I would simply re-install. If you use ssh, use keys and disable passwords.

[http://bodhizazen.net/Tutorials/SSH_keys](http://bodhizazen.net/Tutorials/SSH_keys)

I would not be afraid of forensics, but it will require a lot of time and reading.

Here is a general overview of the types of steps you would do. Note, often you start by pulling the network card, not powering down.

[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1)

[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2)

---

