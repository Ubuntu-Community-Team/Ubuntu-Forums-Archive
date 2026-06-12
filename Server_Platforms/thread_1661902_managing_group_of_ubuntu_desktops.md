---
title: "managing group of ubuntu desktops"
date: 2011-01-07
forum: Server Platforms
---

### Post by logandzwon on 2011-01-07
This isn't really a server question per-se, I posted it in general first, but unsurprisingly, no one has responded, maybe this group will have some advice.

I'm trying to figure out the best way to maintain a group of about 60 Ubuntu workstations. I already have OpenLDAP running for permissions, and PXE boot netinstall for install and sets-up of new and recycled workstations. I want to be-able to maintain thing like what packages are installed on different groups, and control updates and upgrades. I know MS has group policy, and I know how to control policies, push packages, and control updates in OS X environments. Can someone recomend something similar for Ubuntu?

---

### Post by Skadork on 2011-01-07
Landscape is probably going to be your best bet, but Webmin is a free alternative.

---

### Post by logandzwon on 2011-03-02
Thanks, landscape is good, but non-free. Webmin really wont handle doing the work like in other ecosystems.

This project is for a middle school with no funding. I would be happy to volunteer the work to set-up all the systems, but I can't stay on full-time to maintain it. The full-time staff is non-technical teachers. If it was OS X or SBS2008 I could set-up a netboot to handle an fully automatic reinstall if any computer developed issues, and use the update manager to force updates to all workstations.

I was trying to figure out something similarly low maintenance I could do with free, as in beer, software.

---

### Post by headvampyre@hotmail.co.uk on 2011-03-02
You could always setup an environmen and create images for it. The youd need to configure DHCP and TFTP. Or look for FOG, its free (Ive never used it). This way you can boot the installers on clients via PXE and have everything prepared for the students.

---

### Post by HermanAB on 2011-03-02
Howdy,

Keep all machines exactly the same and use Parallel SSH to manage them all in one go. One command, 60 times all at once, done.

---

### Post by koenn on 2011-03-02
I'd go with what Herman says.

If you want it more complicated, you could have a look at ocsinventoy-ng
It's a network inventory tool first, but has a mechanism to push (config) files to and execute remote commands on the hosts it knows of (and you can group them etc). 
It feels to me that this is more geared towards Windows desktops where (in absence of a AD with GPO), remote configuration and command execution is less straightforward than "just run a command through ssh"

---

### Post by siddharthpuranik on 2011-04-06
Sorry to hack this thread,but I have similar issue.

Hi,

I am intermediate user in Linux area and not much familiar with command line etc.However,I am able to complete my work by reading blogs,docs from mint/ubuntu/debian forum.Now,I want to use Ubuntu desktops in one of the school with 35 desktops.Administrator should be able to do centralised administration as in directory server+Installations of some Open source apps

Problem / Scenario:
Step1: Need to create a domain abc.com in ubuntu desktop / server (Latest Version is preferred)
Step2: Need to join Ubuntu desktops to domain and users created in domain
Step3: Need to setup shares with quota=3 GB / user.
Step4:Some school related applications like MArklists/Attendance,kind of School Management system

Tried googling but not clear.

I checked for Calculate directory server and desktop but not went very well.(CDS works only if I use Calculate desktop,I don't want to get stuck to 'not so known' distro.)
So,again considering Ubuntu but searching for some distro which can offer this centralised administration capabilities.

Cent OS/Apache/OpenDS/389 directory server+Ubuntu??

Any suggestions?

---

