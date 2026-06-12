---
title: "Complete Linux Home Server??"
date: 2009-02-02
forum: Server Platforms
---

### Post by Zaphrod on 2009-02-02
Hi all,

I have been messing around with the idea of using Ubuntu as a Complete Home Server. By Complete I mean the following.

File and Print Server
DHCP server
Domain Controller to allow roaming profiles
Media Server with Transcoding for PS3, XBOX and Mobile Devices 
PC Backup
Server Backup
Shadow Copy?
Easy Disk Expansion so all file and media space is always seen as one drive. 

I have left off web server as I am not sure how secure it would be to host a website on the same server as you have all your files etc. Unless someone can tell me different it seems unsafe. Possible one could be run from a virtual server on the same box?

I have had limited success getting this set up. I have tried SAMBA with both LDAP and TDB back ends as a domain controller both of which worked after a fashion but I could not get my Epson Photo Stylus Printer to work from a windows PC either time until I installed the ubuntu-desktop package which I don't mind but it installs a ton of stuff I don't need, there needs to be a desktop option with the utilities but no software. Ideally I would like no GUI but maybe a web interface like ebox or something would do the trick?

Until I get a Basic Domain Controller with File and Print sharing working there is no reason to go any further trying to get the media server going let alone PC and Server Backup etc.

It would be great if someone with the required knowledge could write a tutorial to get something like this working. I was documenting my efforts in case I managed to get the system running but have so far ran up against too many obstacles.

Is anyone up for the task? I think there might be quite a lot of desire for something like this.

---

### Post by cmnorton on 2009-02-02
You are considering a lot all at once, but a couple of things caught my eye. 

There is something to be said for having a single point of failure for web; that is have an inside-firewall/outside firewall server. As to protecting yourself, I would get the best firewall you can afford. I am not up on all the home equipment, which is best for security, ease of use, and so on.

You should be able to share out your Epson using samba, and print from Windows. I would
start out just running samba. Configuring it as a domain controller is another whole topic. I guess my basic advice here is start simple, and then build up complexity.

---

### Post by cariboo on 2009-02-02
You didn't need to install the desktop to share your Windows connected printer, use the cups web interface. If you are running a server with no gui you will need to install elinks, a text based web browser, to access the cups management interface. then at the prompt type:

```
elinks http://localhost:631
```

Doing it this way you don't need Samba.

Jim

---

### Post by tomwerner470 on 2009-02-02
I know that you are trying to get the printer working first, however, for later reference for yourself and others, the following links might be helpful...

> PC Backup
Server Backup

These can be handled by AMANDA ([http://amanda.zmanda.com/](http://amanda.zmanda.com/)), from their website it appears there are clients for Mac, Unix and Windows.

> 
Shadow Copy?
Easy Disk Expansion so all file and media space is always seen as one drive.

Shadow copy for windows is doable under samba, I havn't tried it myself, however there are a few tutorials out there on google. ([http://www.wlug.org.nz/SambaShadowCopyHowto](http://www.wlug.org.nz/SambaShadowCopyHowto))

A prerequisite of the shadow copy is that your volume (be-it plain or RAID) needs to be on a LVM to work, if you do go for an LVM, it should make it easier to add storage to the system at a later date.

One thing you havn't mentioned is your RAID config, if you are using software raid (which I am a great advocate of for low to mid end deployments) then adding storage to your arrays shouldn't be a problem, hardware controllers I havn't had much experience with and your mileage may vary.

Good luck with the printing, I am sure you are nearly there...

Regards,

Tom

---

### Post by Zaphrod on 2009-02-03
Thanks for all of the info all. It is a lot to digest. 

I did manage to get the cups web interface working and I did get the printer to show up and print from Ubuntu but for whatever reason when I set up the printer without using Gnome I could get windows to see the shared printer but could not get it to print to it. I cannot remember the error I got at this time.

The PC and Server Backup and the shadow copy functionality could actually wait as I have none of that now so would be missing nothing in the short term. and the disk expansion I guess could be taken care of by the on-board SATA raid controller but I am unsure whether I could use JBOD and add disks whenever required or not as I have not tried it before. Does anyone know?

Strangely enough the domain controller set up was fairly simple and worked as required.

I might have another go and see what happens.

---

### Post by cmnorton on 2009-02-03
The best thing I did was to put my admin user in the lpadmin group and use the cups web interface [http://localhost:631](http://localhost:631).. I have had very good luck configuring CUPS using that. Ubuntu's gnome configuration is good, though; I just prefer web in CUPS' case.

---

### Post by sraghav on 2009-02-03
Hi,

I've started down this path too. Got the machine connecting to the internet, sharing my external storage disk and printer using samba, so my Windows laptop can access both. Now got to address the backup, etc.

Fairly painless so far, thanks to all the help from these forums - hopefully it stays this way.

sraghav

---

