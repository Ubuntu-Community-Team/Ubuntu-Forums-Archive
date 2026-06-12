---
title: "How do I do Windows/Linux upgrade pushes"
date: 2011-08-06
forum: Server Platforms
---

### Post by frankie1234 on 2011-08-06
I am running Ubuntu 10.10 server edition with Samba file sharing on it. How do I push program installations or upgrades to windows or Linux machines when they connect? Is there a GUI interface for it? How do I differentiate between Linux and Windows and occasionally Macs? I looked around for a while on google but I didn't find anything...

---

### Post by omelette on 2011-08-06
Update Manager will automatically prompt you when upgrades are available, you just 'OK' the upgrade or 'Cancel' it.  You can do it manually via the Synaptic Package Manager app.

---

### Post by frankie1234 on 2011-08-07
That's not really what I am asking about. I want to be able to push things such as software installations.For example, I want to be able to install a broadcast receiving program automatically when a machine connects to my network so I can pass messages via broadcast. Not strictly upgrades. I also want to be able to push the upgrades instead of going around and manually upgrading each machine because some are not in use and some users are afraid to click the upgrade button:(.

Thanks in advance for any help

---

### Post by SeijiSensei on 2011-08-07
You can run a cron job each night that executes "apt-get upgrade".  Make sure it's run either in /etc/crontab or in root's crontab so the job runs with root privileges.

If you want to have control over which packages get upgraded, you can create your own repository on an internal web server and change the URL's in /etc/apt/sources.lists accordingly.  Have the server get the updates with apt-get but place them in a temporary storage location.  Then you can move the ones you want to distribute to the directory referenced in the sources.list URLs.

---

### Post by HermanAB on 2011-08-08
In a large Linux/Mac deployment, use Parallel SSH, or mount the /usr and /home directories over NFS, then you just update the servers.

Windows?  I don't do Windows anymore, but there something that can be deployed with Active Directory.  It used to be known as WUS - Windows Update Server - call a dog a bad name...

---

