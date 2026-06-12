---
title: "AV needed??"
date: 2008-12-05
forum: Security
---

### Post by magmon on 2008-12-05
I was reading up on linux security today, and saw that there are in fact a fair number of linux viruses. Should I get an AV or download scanner etc?

---

### Post by 2hot6ft2 on 2008-12-05
Not really since each linux distribution is a little different they would have to write it just for your system (and it would have to have root permissions) but if you duel boot it's nice to have since you can scan windows from linux and take them out when they have nowhere to run. clamav, AVG and a couple others are available for linux.

The exception would be if you use wine for windows apps. They can still get windows viruses but it can't spread to the linux OS.

Search for clamav in synaptic and you may find it's already installed. If you want a GUI for it you would install avscan and create a launcher in the menu for it. Or clamtk which will create the launcher itself.

---

### Post by Kinstonian on 2008-12-05
Well some things to keep in mind that suggest you don't need it are:

1.  There is still a relatively very small amount of malware for Linux compared with Windows.

2.  AV software is only one small part of the overall defense against malware.  If you take other measures to prevent malware than maybe you don't need AV software.

3.  It is also not uncommon for AV software such as ClamAV to have vulnerabilities that can actually leave you worse off.

Some reasons to have it are:

1.  Even if you are extremely careful about running code that might be malicious, you still have to worry about the code attackers will run on your computer that you know will be malicious.

2.  Quickly detecting and responding to incidents is vital.  As the saying goes, *prevention is ideal, detection is a must.*  Unfortunately AV software is often times peoples only form of detection.

However, if you utilize other methods of detecting incidents, then you won't have to worry about using AV software as a form of detection as much.

Those are some things you should consider, the choice is up to you.

---

### Post by 2hot6ft2 on 2008-12-06
Here this may help [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
Personally I like AVG it has helped me clean up a infected windows OS. While it doesn't remove them it showed me where they were and it was easy to go kill them.

---

### Post by cdtech on 2008-12-06
By using the repositories to install packages, md5 checksums and using root privileges only when necessary are just a few ways to to guard against an intrusion. SSH is often the first point of entry to a Linux machine. Using strong passwords and an antiviral software should ALWAYS be common practice for any OS and could potentially limit the risk of a system catastrophe.

There is a method to infect a system wide Linux OS without the need to become root, it's known as &#8220;Privilege escalation&#8221; --

> &#8220;Privilege escalation is the act of exploiting a bug or design fault in a software application to gain access to resources which normally would have been protected from an application or user. The result is that the application performs actions with more privileges than intended by the application developer or system administrator&#8221; (wiki,  Privilege escalation).

This is just my two cents and everyone has thier own methods to protect thier own systems......

---

### Post by hyper_ch on 2008-12-06
no antivirus in general needed

---

