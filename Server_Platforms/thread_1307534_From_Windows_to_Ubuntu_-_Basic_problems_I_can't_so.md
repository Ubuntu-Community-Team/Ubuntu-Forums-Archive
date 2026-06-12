---
title: "From Windows to Ubuntu - Basic problems I can't solve"
date: 2009-10-31
forum: Server Platforms
---

### Post by MrQuan on 2009-10-31
Hi all,

I've taken the plunge to linux and I now have a headache :(  Let me first paint the picture for you...

I ran a home server on **Windows Server 2003** that was predominantly for file sharing for both work and play (dev stuff and streaming media to PS3), and also served as a webserver for testing web apps and demo-ing these to clients externally with my dot-com linked through. This means it had IIS, PHP, and MySQL for web stuff, and a Java based PS3 Media Server - I assumed this would be ok in Linux.  My server was running nicely for years humming in the corner, I haven't really touched it, it just works.  It's an old P4 with 512MB RAM, a 40GB IDE OS drive, and 2 x 1TB SATA drives.  Most other PCs on my network are Windows, but I also have an Ubuntu laptop.

So I've jumped in the deep end and installed **Ubuntu Server 9.10** x86 and selected lamp, SSH, and samba.  All good.  Rebooted and came to command line.  Funnily enough this is the first time I realised it was command line only... a bit scarey for me, but ok, I'm ready to roll up my sleeves and learn...

I have no screen or keyboard for this server so the first thing I did was find a remote management solution.  I installed Webmin and it works just fine. :)  This also confirms my Apachi is running well.

Next I set the IP static by editing a text file with the help of Google. All good.

Next I tried finding where my 2 x 1TB HDD are.  Can't find them anywhere? I did find reference to them in **/dev/disk/by-label** where is has them named as they were in Windows.  These are NTFS by-the-way.  I've googled 'ubuntu hard drive' etc for the past hour and found all sorts of results saying "go to PLACES" etc... well I have no GUI. :(

I'd like to get these drives on the system so I can them share them to my network (with Samba??).  Can someone please help me, I'm really frustrated with how insanely complex the linux filesystem is and could do with guidance.

Eventually I want it to serve videos to my PS3 again, but I'll leave that for another day... a day I'm not looking forward to :?

---

### Post by unmole on 2009-10-31
If you want a lightweight GUI you can install LXDE. This will greatly improve usability. Do a
```
 sudo apt-get install lxde 
```

---

### Post by unmole on 2009-10-31
You can make the interface even more user friendly by installing ubuntu-desktop. Simply do a 
```
 sudo apt-get install ubuntu-desktop 
```But keep in mind this will be a little heavier on the system resources.

---

### Post by MrQuan on 2009-10-31
Thanks for the suggestion. :)

A GUI is really only going to help me if it will allow me to VPN into it.  On my previous Windows install I would use remote desktop, does LXDE have a similar functionality?

I wouldn't mind being GUI-less, as I said, I won't be touching the server much after it's set up and running.

---

### Post by MrQuan on 2009-10-31
Figured out how to get my NTFS hard drives to connect :D:D


[LIST]
[*]Webmin > System > Disk and Network Filesystems
[*]Clicked 'Add Mount' for 'Windows NT Fliesystem (ntfs)'
[*]I set my first drive to mount at '/dev/my_hdd_01' and the other at '/dev/my_hdd_02'.
[*]Set it to 'Save and mount at boot'.
[/LIST]
Now I just need to get them shared to the Windows PCs on my network, so I'll start tinkering around with Samba.  I'll report back with any problems/success.

---

### Post by MrQuan on 2009-10-31
Samba Question...

I'm having real issues with permissions.  I have my HDDs file sharing in my Windows PCs, but everything is read-only.

I want to add a Samba user with write access to some directories.  Do I first need to create a new Ubuntu user, and then a Samba user of the same name?  I can't see how to do this in Samba alone.

---

### Post by Iowan on 2009-10-31
> **MrQuan said:**
>   Do I first need to create a new Ubuntu user, and then a Samba user of the same name?  Correct! The Ubuntu user will need to exist first, then a Samba user (of the same name) can be created with **smbpasswd**.

---

### Post by MrQuan on 2009-11-01
I've tried a couple of different things and can't seem to get my permissions to work.  Please note I'm using the standard 'Samba Windows File Sharing' module in Webmin.

I've created a few shares, set them as **writeable **and **allowed guest access**.  This is to test my new ubuntu server and samba are all good.  As expected the windows machines on my network can browse, read, and write these shares without any login or password.  All good so far, shares are working. :)

Now I want to implement some user permissions so one user has access to everything (me), and the other user has read only access to the media folders (so users can play videos and music, but can't accidentally delete them).

These are the steps I've taken in Webmin to try and accomplish this (unsuccessfully):

[LIST=1]
[*][COLOR=Red]System > Users and Groups[/COLOR]:  Create a new linux user called '**Test**' with standard password '**test**' and put them in a new group called '**win_users**'.
[*][COLOR=Red]Servers > Samba Windows File Sharing > Convert Unix users to Samba users[/COLOR]:  Here the Test user is added and I set the password to 'Account locked'.
[*][COLOR=Red]Servers > Samba Windows File Sharing > Edit Samba usera and Passwords[/COLOR]:  'Test' user now shows up here, so I click that and set the password to 'test'.  Note the '**Account disabled**' is left **unchecked**, everything else is left as is.
[*][COLOR=Red]Servers > Samba Windows File Sharing > Create a new file share[/COLOR]: Fill in the share path and name, leave everything else as default (permission: 755, available: yes, browseable: yes).
[*][COLOR=Red]Servers > Samba Windows File Sharing > Edit File Share > Security and Access Control[/COLOR]:  Here I set **Writable **to **Yes **and add '**Test**' user to '**Valid users**', I leave everything else as is (**Guest Access **is set to '**None**').
[*]The share is visible on my windows machine, when I click it I get a username password prompt, so I type in 'Test', 'test', and windows says '**The specified network password is not correct.**'
[/LIST]
I have tried this a few times now.  Tried once with a username and password that matched my windows PC, tried in a different order, still no luck.   The only way I've got sharing to work is with the insecure guest access.  Can someone please offer some guidance? I have no idea now :-k

Many thanks,
MrQuan

---

### Post by MrQuan on 2009-11-01
Ok, I've got a major set back.  After rebooting the server, my 2 sata hdd don't mount.  so I'm back at square one.  I've wasted a weekend on this, I don't know if I have the required patience for linux :(:(

[COLOR=Red]**Edit:**[/COLOR]
Ok ok ok *phew* what a saga. :|   I was playing around with my sata hdd mounts and discovered something strange.  It seams the auto-mounting at start up is working, however, the '**/dev/my_hdd_01**' folder is gone!!??  So if I go and create the '**/dev/my_hdd_01**' folder then, voilà! All my hdd stuff is magically in there and Webmin magically shows the drive as now being mounted. :-)  Is there a reason why those folders are missing when I reboot?

[COLOR=Red]**Edit:**[/COLOR]
Instead of using the Webmin file manager I tried '**mkdir my_hdd_01**' from the Webmin command shell, but after reboot it was gone as before.  Anyone know how to make these folder stick?

---

### Post by TwiceOver on 2009-11-01
Are you using the /dev folder for your mounts?  That might be the entire problem right there.  Webmin is great and all but you might have to dive into the command line to get the drives to mount properly each time.

With the drives look up how to edit fstab.  This is the file that tells the system where to mount your drives.  I usually mount my drives in /media.  Do a google search for ubuntu mount ntfs drive fstab and you'll probably find a good tutorial.

I am betting this will solve your user issues also as /dev is reserved for root I think.

EDIT:  Just an FYI, I previously ran a Windows Server as my home server.  I made the switch to ubuntu server and actually found a lot more I could do with my home server.  Keep with it, it will be a fun learning experience.  Also if you run into performance issues you might want to move the data off and change the drives from NTFS to EXT3 or some other file system.

---

### Post by MrQuan on 2009-11-01
Ah, ok, thank's for the advice.  I read somewhere online that /dev was for 'devices' so I assumed this would be a logical place to mount the hard drives.   I'll try moving my mount paths to /media and see how I go.

Yeah, I'm going to stick with it... Despite my initial pain and complaints I'll admit the server is already much more responsive than it's ever been and resource usage is very low.  Linux definatly is the smarter choice if you've got plenty of asprin for the learning curve :-P

[COLOR=Red]**Edit:**[/COLOR]
Thank you!! That got my HDD mounts to stick after rebooting :D  I'm going to grab another coffee and have another go at Samba.  Many thanks!

---

### Post by TwiceOver on 2009-11-01
> **MrQuan said:**
> I read somewhere online that /dev was for 'devices' so I assumed this would be a logic place to mount the hdds.

I'm not 100% sure and people should correct me if I'm wrong, but /dev holds the devices that are attached to the system and is recreated every time you boot to show changes in devices.  This is why when you created the mount folders, they disappeared on boot.

I think anyway...

---

### Post by koenn on 2009-11-01
> **TwiceOver said:**
> I'm not 100% sure and people should correct me if I'm wrong, but /dev holds the devices that are attached to the system and is recreated every time you boot to show changes in devices.  This is why when you created the mount folders, they disappeared on boot.

I think anyway...
Almost.
/dev is where/how the kernel sees the devices. This can be anything from a hard disk to a serial port. 

With hard disks, you're (usually) not so much interested in the device itself, but in the filesystem on it. 
Mounting is the mechanism that includes the filesystem on the disk into your directory tree, and makes the files accessible. 
Windows doesn't know such a concept and doesn't distinguish between drives and filesystems, that's why people sometimes get confused.

You can make mounts permanent by adding the appropriate statements to /etc/fstab.
The usual mount point for external drives is /media. Fixed drives should get their dedicated mountpoint - possibly one you create first, say /data or /ntfs/disk1 or something. Keep out of /dev.

---

### Post by koenn on 2009-11-01
> **MrQuan said:**
> Thanks for the suggestion. :)

A GUI is really only going to help me if it will allow me to VPN into it.  On my previous Windows install I would use remote desktop, does LXDE have a similar functionality?

I wouldn't mind being GUI-less, as I said, I won't be touching the server much after it's set up and running.

You can use ssh.
It's not a GUI, it gives you a remote shell (command prompt).
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html)

---

### Post by MrQuan on 2009-11-01
> **koenn said:**
> Almost.
/dev is where/how the kernel sees the devices. This can be anything from a hard disk to a serial port. 

With hard disks, you're (usually) not so much interested in the device itself, but in the filesystem on it. 
Mounting is the mechanism that includes the filesystem on the disk into your directory tree, and makes the files accessible. 
Windows doesn't know such a concept and doesn't distinguish between drives and filesystems, that's why people sometimes get confused.

You can make mounts permanent by adding the appropriate statements to /etc/fstab.
The usual mount point for external drives is /media. Fixed drives should get their dedicated mountpoint - possibly one you create first, say /data or /ntfs/disk1 or something. Keep out of /dev.

Thanks for explaining this to me.  Mounting a file system is a new concept for me, like you said, Windows doesn't distinguish between a partition and a file system.

> **koenn said:**
> You can use ssh.
It's not a GUI, it gives you a remote shell (command prompt).
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html)

Awesome, I think having some decent command prompt is going to be very helpful.  I've been struggling with the Webmin command shell.  Thanks again for the advice. :)

I'm still having difficulty with Samba.  It seems straightforward enought to setup in Webmin, but I'm getting seemingly random results.  A user/password share will prompt my Windows PCs to ask for credentials, and then allows them in - however another share with the exact same Samba setup isn't allowing access.  Then some of my guest access shares screwed up so I had to re do them.  It's all very random and sparodic at the moment.  I think I'm going to have to clear all my Samba configuration and start from scratch. :(

---

### Post by koenn on 2009-11-02
> **MrQuan said:**
>  ...  from scratch. :(

you might ant to have a look at 
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba1.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba1.htm)

---

### Post by iMisspell on 2009-11-02
> **MrQuan said:**
> Awesome, I think having some decent command prompt is going to be very helpful.  I've been struggling with the Webmin command shell.  Thanks again for the advice. :)
A month or so ago i whent through the same as you are now.
You might find some info in this thread help full so you dont have to keep typing the same long commands.
[http://ubuntuforums.org/showthread.php?t=1301429](http://ubuntuforums.org/showthread.php?t=1301429)

Heres a snip from my servers .bash_aliases which you might find usefully ...

```


# edit .bash_aliases file
alias aledit='sudo $HOME/.bash_aliases'

# reload bash so edit are current
alias alre='echo "reloaded bash"; exec bash'

# Make a file executable (used when making scripts)
alias makeexe='sudo chmod +x'

# list files and folders when your in a dir
alias ll='ls -l $1' # you can pass extra parameters to this
alias la='ls -A $1' # you can pass extra parameters to this
alias l='ls -CF $1'# you can pass extra parameters to this

# open and edit file in root
alias sedit='sudo nano'

# apache2 stuff
alias phpconfig='sudo nano /etc/php5/apache2/php.ini'
alias wwwrestart='sudo /etc/init.d/apache2 restart'
alias wwwconfig='sudo nano /etc/apache2/apache2.conf'
alias wwwsites='sudo nano /etc/apache2/sites-available/default'
alias wwwlog='sudo nano /var/log/apache2/error.log'

# mysql stuff
alias mysqledit='sudo nano /etc/mysql/my.cnf'
alias mysqlrestart='sudo /etc/init.d/mysql restart'
alias mysqlstatus='sudo /etc/init.d/mysql status'

# mysql stuff
alias samba_edit='sudo nano /etc/samba/smb.conf'
alias samba_restart='sudo /etc/init.d/samba restart'

# aptitude
alias appin='$HOME/app_installer/install_remove_app.sh i 4'
alias inapp='sudo aptitude install'
alias appremove='sudo apt-get remove'
alias appremoveall='sudo aptitude purge'
alias appupdate='sudo aptitude update'
alias appupgrade='sudo aptitude update && sudo aptitude safe-upgrade'
alias appfullupgrade='sudo aptitude update && sudo aptitude full-upgrade'
alias appsearch='aptitude search'
alias appver='apt-cache policy'
alias appinfo='sudo aptitude show'
alias appwhere='dpkg-query --listfiles'
alias appkeepall='sudo aptitude keep-all'

```

---

### Post by MrQuan on 2009-11-04
> **koenn said:**
> You can use ssh.
It's not a GUI, it gives you a remote shell (command prompt).
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html)
I couldn't get the SSH to work through Webmin, and I assume this is an issue with Webmin/Java integration that I've seen others complaining about online also.  My work doesn't block ports though, so I'm not tied down to 80 (and therefore Webmin). So I went ahead and installed PuTTY at work and configured the port forwarding on my router at home.  Today I was able to connect to my server at home from work over port 22 successfully just using my linked dot com address in PuTTY!! :D   This is awesome, and something I'll be using on the home network.  Thanks again for the suggestion.

> **koenn said:**
> you might ant to have a look at 
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba1.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba1.htm)
I've had a read through this, and I'm feeling lucky, so I'll be attempting my Samba configuration again tonight. Cheers :)

> **iMisspell said:**
> A month or so ago i whent through the same as you are now.
You might find some info in this thread help full so you dont have to keep typing the same long commands.
[http://ubuntuforums.org/showthread.php?t=1301429](http://ubuntuforums.org/showthread.php?t=1301429)

Heres a snip from my servers .bash_aliases which you might find usefully...
That looks very handy, thanks :)

---

### Post by koenn on 2009-11-04
> **MrQuan said:**
> I couldn't get the SSH to work through Webmin, and I assume this is an issue with Webmin/Java integration that I've seen others complaining about online also.  My work doesn't block ports though, so I'm not tied down to 80 (and therefore Webmin). So I went ahead and installed PuTTY at work and configured the port forwarding on my router at home.  Today I was able to connect to my server at home from work over port 22 successfully just using my linked dot com address in PuTTY!! :D   This is awesome, and something I'll be using on the home network.  Thanks again for the suggestion.


hm, didn't think you were planning to do this over internet. 
Of course, it works, but you might want to keep in mind that everybody out there can do what you did : run putty or a linux ssh client and try to log on to your server. I hope you're using strong passwords.

better still, look into ssh with key authentication, or control what hosts/ip adresses ... are allowed to connect to your server. 

---
and have fun with samba

---

### Post by MrQuan on 2009-11-04
> **koenn said:**
> hm, didn't think you were planning to do this over internet. 
Of course, it works, but you might want to keep in mind that everybody out there can do what you did : run putty or a linux ssh client and try to log on to your server. I hope you're using strong passwords.

better still, look into ssh with key authentication, or control what hosts/ip adresses ... are allowed to connect to your server. 

---
and have fun with samba
Thanks, yes I also managed to set up my ufw so I've denied access to all but the essential ports I use, and it's accessable only from particular IPs (my home subnet, and work). I'm looking into the key thing though because in future I might want to log in from anywhere... no sure why I'd need to though :)  Thanks

Got distracted with some MySQL issues last night (I assume it's a Java issue because the server seems to run perfectly as far as I can see), so I still haven't hit Samba again.

---

