---
title: "Why should I instal an anti-virus in Ubuntu"
date: 2011-03-21
forum: Security
---

### Post by hijiz on 2011-03-21
Hi, Latley ive seen countless posts on the internet of antivirus software for ubuntu. I understand the main reason is not to infect other computers, but what other reasons are there for installing an anti virus in ubuntu?

---

### Post by nevius on 2011-03-21
> **hijiz said:**
> Hi, Latley ive seen countless posts on the internet of antivirus software for ubuntu. I understand the main reason is not to infect other computers, but what other reasons are there for installing an anti virus in ubuntu?

Not really. 

Think about it. What is it going to detect? The very limited amount of malware that has ever existed for Linux exploited vulnerabilities that have already been patched for a long time. 

The largest threat to a Linux user is social engineering / phishing.

Stick to the repositories, be careful of running server software (SSH, VNC, Apache, etc.), use firefox with no-script.

Check out the wikipedia article on Linux Malware: [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

Most importantly: READ THE SECURITY STICKY
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by HermanAB on 2011-03-22
Howdy,

On Linux, the policy is to fix the problem. On Windows, the policy is to fix the symptom.

So, on a Linux system, you do not need a malware scanner, just do your updates at least once a year.

---

### Post by bodhi.zazen on 2011-03-22
> **hijiz said:**
> Hi, Latley ive seen countless posts on the internet of antivirus software for ubuntu. I understand the main reason is not to infect other computers, but what other reasons are there for installing an anti virus in ubuntu?

The only reasons I would advise would be:

1. If you are running a file server (samba, nfs, ftp, etc) and shaing files with windows clients. You would then use antivirus to scan shared files.

2. You are running a mail server and wish to scan attachments.

3. You want to scan removable media (usb) you share with Windows.

There are no know active viruses for Linux and your system has been patched to the known Linux viruses long ago.

I have never been convinced the there is any "social responsibility" to scanning for viruses on a Linux server or desktop outside of the above 3 reasons. IMHO viruses are from windows, by windows, and for windows and if you ask me either Microsoft needs to step up and patch the vulnerabilities or windows uses need to learn to secure the OS.

---

### Post by SeijiSensei on 2011-03-23
> **hijiz said:**
> Hi, Latley ive seen countless posts on the internet of antivirus software for ubuntu.

I'm just curious who the sources of these "countless" posts might be.  I know a couple of antivirus vendors claim to offer their software for Linux; are they the source?  I find the AV vendors some of the most unreliable shills in the industry.  Since their industry is built on maintaining a climate of fear among computer users, they'll trumpet even the most implausible infection vectors as a rationale to buy their software.

Or are these just the usual rantings of uninformed users or critics of Linux?

---

