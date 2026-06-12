---
title: "Root compromised"
date: 2011-03-14
forum: Security
---

### Post by TonyField on 2011-03-14
I was running a older version of Ubuntu (from about 2.5 years ago, cannot remember the exact aversion) as my general web server.  This was a workstation configured with samba and apache2.  A few weeks ago, it seems my system was taken over and a large number of messages were sent from my system, to the point that the ISP sent me a rather strong email about my "misuse" of the internet.

The only thing I noticed was that, last week, if I attempted to do a sudo operation, I could not gain control.  A message "could not resolve <myhost>" was issued and the password could not be changed.  I assume that one of the functionalities of sudo has been replaced with a trojan.

I tried AVG and Avira - nothing was discovered.  As well, Microsoft Windows Security found nothing.

The only option was to install Ubuntu 10.10 as a clean install.

Any suggestions about how to avoid such an invasion of my system again??

tony

---

### Post by Kinstonian on 2011-03-14
1.  Follow the usual best practices such as keeping your system patched.

2.  Monitor your system for incidents, and investigate problems (like sudo not working) because being notified by a third party for misuse is not how you want to detect an incident.

3.  There is a lot more to intrusion analysis and recovery than running AV scans.

4.  Don't reinstall your OS after a compromise without trying to answer the questions you have, because you will never have those answers now.

---

### Post by The Cog on 2011-03-14
A message "could not resolve <myhost>" was issued

This is normally because of a mismatch between the hostname defined in /etc/hostname and the name->IP lookup in /etc/hosts. The name in hostname is normally mapped to 127.0.1.1 in hosts. You can fix this by using a live CD and editing the two files by hand.

That might make using the system easier, but the question of how it got that way remains. If you really have been compromised, I think you should reinstall with new and improved passwords, after your investigation. Don't trust anything on a compromised system.

---

### Post by TonyField on 2011-03-14
I check /etc/hostname and everything looked fine.  Any attempt to use sudo resulted in the non-acceptance of the password.  If I tried to change my personal password, the operation was disabled.

I could not find anything on the ubuntu forum about intrusion analysis - the only items found were boilerplate about the lack of virus and trojan intrusion.  Can you point me to some good references for intrusion analysis??

---

### Post by bodhi.zazen on 2011-03-14
Intrusion analysis is a complex task.

The general advise is to make an image of your installation, using dd or any tool you wish, and re-install.

You then analyze the image.

I disagree with the advice Kinstonian gave you, more so on an older version of Ubuntu. You may never know the cracking technique used to compromise the system.

After you install, read the security sticky. Use tools such as OSSEC and snort to monitor of intrusion attempts.

---

### Post by Kinstonian on 2011-03-14
> **TonyField said:**
> I check /etc/hostname and everything looked fine.  Any attempt to use sudo resulted in the non-acceptance of the password.  If I tried to change my personal password, the operation was disabled.

I could not find anything on the ubuntu forum about intrusion analysis - the only items found were boilerplate about the lack of virus and trojan intrusion.  Can you point me to some good references for intrusion analysis??

Intrusion analysis is just a term for describing doing computer forensics on hosts that have been compromised.  It involves analyzing Network Based Evidence (NBE) which includes network traffic and logs from network devices.  As well as analyzing Host Based Evidence (HBE) which includes memory and the file system; system and application logs, timelines, anti-malware scans and reverse engineering,  recovering deleted files, etc.

You may find better results googling for some of those terms.  You can learn a lot from the [SANS Computer Forensic Blog](http://computer-forensics.sans.org/blog/) or the winning papers from [The Honeynet Project Challenges](https://honeynet.org/challenges)

There are also all kinds of books dealing with various elements of intrusion analysis, but I found [Real Digital Forensics](http://www.amazon.com/Real-Digital-Forensics-Computer-Security/dp/0321240693) to be a good book that puts it all together.  Or if you get hacked again, you could just find a security related forum and someone who can help you. =)

---

### Post by Kinstonian on 2011-03-14
> **bodhi.zazen said:**
> Intrusion analysis is a complex task.

The general advise is to make an image of your installation, using dd or any tool you wish, and re-install.

You then analyze the image.

I disagree with the advice Kinstonian gave you, more so on an older version of Ubuntu. You may never know the cracking technique used to compromise the system.

After you install, read the security sticky. Use tools such as OSSEC and snort to monitor of intrusion attempts.

I'm not sure what you disagree with or why...  Sometimes you can't figure out the root cause, but if you don't even investigate you will certainly never find out.

However, it would be a huge mistake to image the drive without collecting volatile data first, or reinstalling the OS before you've done the analysis since you'd probably get hacked again with the same vulnerability.  Furthermore,  in cases such as this, imaging the drive for analysis is probably neither appropriate or even necessary.  Often times a "sniper forensics" approach is all that is needed.

I agree with seeing the sticky threads though. :)

---

### Post by nec207 on 2011-03-14
Where did you get the old version from what web site? may be you got it from bad web site and was bad OS set up that way when you intall it.
 
Do you have firewall or packet sniffer that will look at all the packets going in and out ? Have you check for any running programs in the background.
 
Having malware or trojen will be eating up system RAM and CPU and running in the background monitoring you PC and sending it out.
 
For all you know a keylogger is on you computer.
 
On the up side your computer may be safe but your gmail or yahoo account may be hacked thus the ISP sent bad report or what ever.
 
If it was me do some detective work than format and reinstall new better  version from a good web site.

---

### Post by TonyField on 2011-03-14
The original version was picked up through the ubuntu site and ran beatuifully for 5 years (with only one update about 2.5 years ago).  The intrusion started in late Feb of this year.  None the less, the new ubuntu 10.10 has been installed and is now fully operational - about 4 elapsed hours work total.  I did not save the old installation for analysis - I simply had to get my server up and running (I am a photographer and need to have the images available).  If this happens again, I will certainly use some of the analysis packages as you suggested.

On another security note.... I have one filesystem on a second hard drive that contains essentially only images.  This is accessed by apache and by samba.  The permissions on all files are set to "nobody:nogroup".  This allows easy samba movement of image files from my Win7 work station to the server as well as allowing http access to the server.  (nominally, the Win7 system is logically disconnected from the network except for the needed file transfers).  In addition, I used the old filesystem (which was on the original contaminated system) with the images as a second drive - is this reasonable?

Is there anything simple I can do with file permissions to increase the general security?

---

### Post by bodhi.zazen on 2011-03-14
> **Kinstonian said:**
> I'm not sure what you disagree with or why...  

The OP is using an old, outdated, unsupported version of Ubuntu and I would not wait for forensic analysis before re-installing (an updated version of Ubuntu and associated applications).

Forensic analysis is challenging, to say the least, and the OP has no idea where to even start and, as I mentioned, forensic analysis my not yield any answers.

We could debate the various methods of Forenics until the cows come home, but, this late in the game, unless the intruder is very sloppy, Forensics are going to be very low yield.

---

### Post by bodhi.zazen on 2011-03-14
> **TonyField said:**
> Is there anything simple I can do with file permissions to increase the general security?

The only "simiple" things you can do are:

1. Use strong passwords.

2. Do not use Samba on the same server as apache, use ssh (use keys and disable password logins). From windows you can transfer files with winscp.

3. Keep your system up to date. Running updates every 18 months is simply inappropriate.

4. I keep all static files (pictures for example) owned by root with permissions of 444 (read only) or owned by root, group www-data, permissions 440 . The most important thing here is that the files are read only.

---

### Post by wacky_sung on 2011-03-15
I bet the best thing is isolation of your web server from any of your network.Using it with samba potential will lead any robotic attacks from script trojans which prone for any exploitable on your window application.My advise is to stay away from samba and recommendation as commented.

---

### Post by wacky_sung on 2011-03-15
> **bodhi.zazen said:**
> The only "simiple" things you can do are:

1. Use strong passwords.

2. Do not use Samba on the same server as apache, use ssh (use keys and disable password logins). From windows you can transfer files with winscp.

3. Keep your system up to date. Running updates every 18 months is simply inappropriate.

4. I keep all static files (pictures for example) owned by root with permissions of 444 (read only) or owned by root, group www-data, permissions 440 . The most important thing here is that the files are read only.

I bet some people may not know what is considered as strong password.

Below is a good example.
[http://strongpasswordgenerator.com/](http://strongpasswordgenerator.com/)

---

### Post by CharlesA on 2011-03-15
I know it's a bit extreme, but if I am going to have a server open to the internet, I'll be running it inside a Virtual Machine. That way if it gets compromised, I can take if offline for a little bit, restore a known good snapshot and restore backups.

---

### Post by wacky_sung on 2011-03-15
> **CharlesA said:**
> I know it's a bit extreme, but if I am going to have a server open to the internet, I'll be running it inside a Virtual Machine. That way if it gets compromised, I can take if offline for a little bit, restore a known good snapshot and restore backups.

Virtutal Machine server can easily run out of memory if the traffic are high or under the attack of DDOS.

---

### Post by CharlesA on 2011-03-15
> **wacky_sung said:**
> Virtutal Machine server can easily run out of memory if the traffic are high or under the attack of DDOS.

That's true. Same could be said for physical servers too.

---

### Post by theDaveTheRave on 2011-03-15
Please correct me if any of this is wrong, but my suggestion would be as follows.

I assume you are running your 'server' at home, and not using a virtual private server?

As others have mentioned separate your web server and you samba server onto separate machines.

Better still if you have an 'old' pc floating around you can put it in between your web server, samba server and the outside world. You then install various tools for tracking the communication between them Then you need to port forward to each of the other systems.

However will this be secure??

This depends. Strong password, and adjusting your user permisions (with regards to 'sudoers' and read / write access) will help. But the setup will only slow down a determined attack.

If you are mainly in need of the setup for 'personal access' to your files then you could do worse than to implement a SSH method whereby you can log in to make any required changes remotely.

Back quickly to the user access, it is also possible to have accounts only accessible from certain locations (ie IP addresses). I have this sort of setup on my 'server'. I can only log in as a very non privileged user from outside my network (ie at work or on the road) with read only access priveleges. And I can only log onto the server (via SSH) from a specific internal IP address that I have hard coded into the router.

For even better security you could get a second network card and enable remote logon to the server only through that card - which effectively ensures a local direct connection (unfortunately I only have the one network interface or I would set this up)

David

---

### Post by Kinstonian on 2011-03-15
> **bodhi.zazen said:**
> The OP is using an old, outdated, unsupported version of Ubuntu and I would not wait for forensic analysis before re-installing (an updated version of Ubuntu and associated applications).

Reinstalling and updating the OS/applications to fix **software** vulnerabilities would help, but probably wouldn't be enough if the original attack vector was a **configuration** vulnerability like the commonly seen weak password.  That's why a root cause analysis should always at least be attempted before simply reinstalling.

> Forensic analysis is challenging, to say the least, and the OP has no idea where to even start and, as I mentioned, forensic analysis my not yield any answers.

I certainly agree with that.  In my first reply to him I didn't mean for him to take it as he should be doing the analysis, which is why I later suggested he find someone online to help him.

> We could debate the various methods of Forenics until the cows come home, but, this late in the game, unless the intruder is very sloppy, Forensics are going to be very low yield.

Forensics now that the OP has effectively performed anti-forensics for the attacker by reinstalling the OS before analysis certainly would be low yield.  But as far as the future and the lessons learned in my first post, there are a number of variables that would either help or hinder an analyst in determining the root cause.  [Sourceforge](http://sourceforge.net/blog/sourceforge-attack-full-report/) and [Apache.org](https://blogs.apache.org/infra/search?q=incident+report) performed an intrusion analysis and found the root cause.

Other forums like LinuxQuestions often help members find the root cause of average attacks just by doing sniper forensics, and they do it for free.  [Google & Adobe](http://www.wired.com/threatlevel/2010/01/operation-aurora/) performed an intrusion analysis on **far** more sophisticated attacks and still were able to answer critical questions.  Companies like [Mandiant](http://www.mandiant.com/) even specialize in APT investigations.  Yes, sometimes there are important questions that can't be answered, but that certainly doesn't mean you don't try.

Detection and response is the only area in security I'm aware of where the odds are in the defender's favor, which is why I think it's important to utilize that one advantage we have to the fullest possibility.

---

