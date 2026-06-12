---
title: "Problems after installing 12.04"
date: 2012-05-16
forum: Server Platforms
---

### Post by Frankincense93 on 2012-05-16
Hi guys,

I recently tried to upgrade from 11.10 to 12.04, but when it asked me to compare files I had no idea what to press when to exit the file and ended up accidentally ending the upgrade, rendering the install corrupted.

Anyway I ended up backing up all my files, clearing my hdd then installing 12.04 fresh. After installing I moved over all the config files to try and get everything back to normal etc.


But unfortunately almost everything I had working on 11.10, is not broken on 12.04.

List of things not working:
ssh
postfix
ssmtp
mysql/php is emailing me every half an hour with errors
openvpn
minecraft server


Is it worth just re-installing 11.10 to get everything working again? Or should I persist in trying to fix everything?

---

### Post by maverickaddicted on 2012-05-16
If you have accidently closed the upgrade process, you can try this 

```
sudo dpkg --configure -a
```

---

### Post by LHammonds on 2012-05-16
> **Frankincense93 said:**
> minecraft server
hahahaha...high five!

You might have goofed by trying to replace the 12.04 config files.  I'm new to Linux but I do have Ubuntu 10.04 servers and a new 12.04 server.   One big difference for me during the 12.04 install was that dns servers now reside in the interfaces file...not the resolve.conf file.

I have not upgraded any 10.04 server to 12.04 and I do not intend to.  When I do my upgrades, I will be installing fresh 12.04 server and make the software work on the new system.  Once I have a warm fuzzy, I will then migrate my data files.   So if anything acts stupid with the new server, I will have the old one on standby to turn back on.

If I were not so fortunate to have multiple servers (I love virtuals), I would have a full system backup along with a verification that it can be restored.  If anything got messy during an upgrade, I would use my backup to restore the system to the way it was before the upgrade.  Redo Backup and Recovery is nice for this.

LHammonds

---

### Post by Frankincense93 on 2012-05-17
So would you suggest trying to make everything work for 12.04? Or just re-installing 11.10?



Also, how do you create a full system backup?

---

### Post by LHammonds on 2012-05-17
> **Frankincense93 said:**
> So would you suggest trying to make everything work for 12.04? Or just re-installing 11.10?
I would never suggest to anyone to use a server that is not LTS (Long-Term Support).  Your options are 10.04 LTS and 12.04 LTS.  So in your case, I would recommend going to either of those and get off of 11.10.

> **Frankincense93 said:**
> Also, how do you create a full system backup?
AS I said, [Redo Backup and Recovery]("http://redobackup.org/")...visit that site, download the ISO image, burn it to CD.  Attach a USB hard drive to your server, insert the CD into the server you want backed up and reboot.  Once you load Redo, simply tell it to backup your server to the external USB HD.  To restore, do the exact same thing but tell it to restore and choose the image on the external USB HD.

**EDIT:** As for your current predicament, if you can get 11.10 back on your server and get everything working, I would suggest doing that 1st.   Next, I would recommend that you install a virtual environment on your desktop (e.g. VirtualBox) and install a 12.04 LTS server and go through the process of getting all your base software installed and working (do not migrate data at the point....you just want to get a 12.04 server running with everything you have running in 11.10).  Then figure out how to export the data from 11.10 to 12.04 and still have it work.  I recommend doing snapshots on the 12.04 server before doing anything so that if it does not work, simply revert the snapshot and try again....will save you MUCH time.

MySQL is quite easy to move from one server to another.  Use mysqldump to export all databases and data to text files...then import it to your new mysql server.

Minecraft is also dead simple.  All you have to do is copy the MC folder over.  The only thing extra you have to do is to install Java on the server 1st.

SSH can be installed during the initial setup of the 12.04 server by selecting it in the options box.

The other 3 I am not familiar with at all.

Once you have a virtual 12.04 server running with everything working, you now have an upgrade path you can follow.
1. Backup your 11.10 server
2. Blow out the 11.10 server and install a fresh copy of 12.04
3. Go through the same steps you did to setup your virtual 12.04 server.
4. Once you have everything working with the base 12.04 server, start migrating data over from your 12.04 virtual.
5. When done and you have a working 12.04 server, backup it up!
6. Have a beer and play MineCraft

---

### Post by Frankincense93 on 2012-05-22
Can't I just go straight to step 6? ;)

---

