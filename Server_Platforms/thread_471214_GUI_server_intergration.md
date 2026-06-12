---
title: "GUI server intergration"
date: 2007-06-11
forum: Server Platforms
---

### Post by Cazilla on 2007-06-11
Greeting fellow Linheads 8)
I pose this question to you.  Are there ANY  GUI not web interface, GUI server integration apps that can be installed on Ubuntu server? As an example, Cent OS does have this feature and it has been compared to Apple's X serve OS server admin.
Any constructive help would be appreciated and please keep all references to Ubuntu server OR to  Debian if has something like this that can be used on Ubuntu.
 Thank you for your eye balls 8)

---

### Post by dfreer on 2007-06-11
Linheads? lol

As for your question, I guess it depends on what exactly it is you want to administer. Like what is it you want to view through the GUI? I haven't used apple's server admin so any details on what it is you want to do could help.

---

### Post by az on 2007-06-11
> **Cazilla said:**
> Greeting fellow Linheads 8)
Cent OS does have this feature and it has been compared to Apple's X serve OS server admin.
Any constructive help would be appreciated and please keep all references to Ubuntu server OR to  Debian if has something like this that can be used on Ubuntu.
 Thank you for your eye balls 8)

What exactly is it called?  If it's GPLed, then it can go into Ubuntu and there would be no reason to keep it out of the Universe repo.

---

### Post by Cazilla on 2007-06-11
Well Apples X server OS  has a Server admim gui interface. Which quite literally make setting up a complete server  (web, dns, ldap, smba, domain controller, Et all) A matter of input name here and bam! server is configured ( Well, not quite that simple, but pretty damn close). It is also integrated which means that  if something new gets added the software updates ALL the applicable software and services. 

Does this help?

---

### Post by Cazilla on 2007-06-11
> **az said:**
> What exactly is it called?  If it's GPLed, then it can go into Ubuntu and there would be no reason to keep it out of the Universe repo.

I'm not sure exactly, still looking for more information on it. I do know however that railsmachine.com uses Cent OS with  Xen cluster and manages their services with it. Also I dont think that its a Rails or ruby app.

---

### Post by netlogic on 2007-06-11
You can always install a simple window manager like Fluxbox and Firestarter for a firewall (very simple firewall) and only allow ssh in from the admin's desktop using the private and public key. You can tunnel your gui applications, vnc, and x session from the admin's desktop station. a combination of ssh, restricted connection from ip for ssh will increase security and able to configure things using GUI. More interface layers you create, more managements you will create down the line. If you are in a rush to setup a Linux server, using the GUI only with ssh tunneling isn't a bad idea.

---

### Post by dfreer on 2007-06-11
> **Cazilla said:**
> Well Apples X server OS  has a Server admim gui interface. Which quite literally make setting up a complete server  (web, dns, ldap, smba, domain controller, Et all) A matter of input name here and bam! server is configured ( Well, not quite that simple, but pretty damn close). It is also integrated which means that  if something new gets added the software updates ALL the applicable software and services. 

Does this help?

Basically what you are describing there is the basic Synaptic package manager, although it doesn't really have a dedicated server interface (I'm pretty sure there is a Server/Security Tab though). And it does exactly that, when new software updates are available it will notify you and install them, if it needs to update another piece of software to do so it will.

If you want the simply ways to install/configure software, ubuntuguide is great but it almost exclusively uses the CLI, which isn't bad for installing things initially.

---

### Post by Cazilla on 2007-06-11
> **dfreer said:**
> Basically what you are describing there is the basic Synaptic package manager, although it doesn't really have a dedicated server interface (I'm pretty sure there is a Server/Security Tab though). And it does exactly that, when new software updates are available it will notify you and install them, if it needs to update another piece of software to do so it will.

If you want the simply ways to install/configure software, ubuntuguide is great but it almost exclusively uses the CLI, which isn't bad for installing things initially.

Well yes and no. I'm looking to be able to configure a server literally point and click and a few keystrokes with package management. Synaptic grabs every single package that might apply and leaves you to figure out what u want. which is fine if your familiar with what your installing. Also sometimes synaptic will tell you that A. Package is needed for Z. application when really its not the case. its almost better to simply use apt-get at that point. What I'm talking about integration is you alter file 1 here and in turn files 44, 62, bac. dev  etc get updated with the appropriate information to make services ZZ, BB, KK all work as they should.  example : DNS  you type in the NS  name and the application finishes it with the ip you want to use and the rest of the configurations and accompanying  files with the correct information AE in-addr-arpa, db.some address, rootcert etc.

---

### Post by Cazilla on 2007-06-11
BTW looking at your Ubuntu guide. When i have a bit more time ill have to go through it more thoroughly . It looks to have good info on it.

---

