---
title: "Way to scan for Rootkits on linux?"
date: 2011-07-24
forum: Security
---

### Post by nrundy on 2011-07-24
I've read that there are a lot of rootkits that exist for linux. MS Windows has tools where you can boot a "portable" scanner from a CD and scan your whole Windows installation for rootkits. This way you can even scan boot sectors because you are never actually starting your installed Windows.

Is there anything available like this for Ubuntu? Is there a scanner I can run off the LIVE CD for example to scan my ubuntu installation for rootkits?

---

### Post by CandidMan on 2011-07-24
Not sure where you got the figures aying there are more rootkits for Linux. I'm guessing they seem more prominent because they're more effective and commonly used against Linux boxes. Considering the likely avenues of infection you ought to just as worried about viruses as a problem...
Having said that, back-track 5 and maybe knoppix have chkrootkit and rkhunter. But as I said, unless someone can physcially access your computer, you're about as likely to pick up a rootkit as a virus.
Just my £0.04

---

### Post by haqking on 2011-07-24
+1

---

### Post by e79 on 2011-07-24
+1 indeed for

Rkhunter:
```
sudo apt-get install rkhunter
```
then
```
sudo rkhunter -c
```

Chkrootkit:
```
sudo apt-get install chkrootkit
```
then
```
sudo chkrootkit

```

---

### Post by nrundy on 2011-07-24
Using Windows its common to see rootkits installed from browsing the internet, clicking links. I just read about one that exploits a JAVA vulnerability and all the user has to do is literally VIEW a forum webpage and the rootkit can install itself on a Win7 x64 box.

I don't have to worry about this kind of infection route using Ubuntu? That is, if my box is physically secured and I only install from MAIN and UNIVERSE repos, I have very low chance of picking up a rootkit from browsing the internet with Ubuntu?

---

### Post by unspawn on 2011-07-24
> **nrundy said:**
> I've read that there are a lot of rootkits that exist for linux.
Different times, different practices: in the previous millennium a lot of rootkits were created and used. Early this millennium only a few new kits were created and to find those (at least for me) In the Wild is rare (there's a wee bit of SHv5 toolkit resurgence though). The past years breaches more often happened due to running VNC-like services or SSH or by exploiting vulnerabilities in applications running in the web stack. Most of these point to lack of knowledge, hardening and regular auditing.


> **nrundy said:**
> Is there a scanner I can run off the LIVE CD for example to scan my ubuntu installation for rootkits?
Chkrootkit and Rootkit Hunter have been included in quite a few Live CDs including KNOPPIX, KNOPPIX-STD and Helix.


> **nrundy said:**
> if my box is physically secured and I only install from MAIN and UNIVERSE repos, I have very low chance of picking up a rootkit from browsing the internet with Ubuntu?
Using common sense like not blithely clicking any link you encounter, not taunting users in chat channels and not providing services to 'net users is a good start but do realize running post-incident tools is no substitute for proper system hardening. So best first give thought to *preventing* anything untoward from happening: see the distributions security documentation and this forums security notes.

---

### Post by bodhi.zazen on 2011-07-24
rootkits are something that are installed after you have already been cracked in order for the intruder to maintain root access.

They are complex and sophisticated and require you, the end user, to know what you are doing.

If you want to run these tools you need to start with a known good system and run and update the tools, and read the warnings, in order to understand what is normal on your system and how these tools work.

The problem is these tools are extremely generic, and most everyone has customized their installs, and so what one might find on a server is not the same as a desktop. So you need to first understand what is normal on your system ;)

With that in mind, I have never seen a root kit detected by either of these tools.

This is not windows and Linux security is not about running a bunch of scanners on your system.

I think you are much better off spending some time reading the security sticky and learning to use apparmor then you are learning to run these tools.

If you want to learn to use these tools, again start with the HIDS sticky (there is a reason it is a sticky), start reading the documentation, and start running scans on known good systems and learn the ropes. The documentation is quiet good and there is no reason for us to re-type the rkhunter or ckrootkit man pages here.

---

### Post by a2j on 2011-07-26
I scan my server daily with rkhunter and chkrootkit. and then just  read an email with scanning report.

---

