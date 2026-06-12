---
title: "Is Server Edition Suitable For Me?"
date: 2008-03-31
forum: Server Platforms
---

### Post by masque7 on 2008-03-31
I have a friend that has many computers and notebooks which are all currently running Windows XP pro (yes, I know. He hasn't even used any variation of Linux yet :(), and they are on a wireless connection.

(Note: I'm extremely new to networking etc, so keep it simple if possible...)

My friend has a huge collection of files and media on his HDDs (which are spread out over 5 desktops - we're looking at maybe a couple TB here, and growing)... Which are all currently networked. Obviously having 5 PCs running all the time is a little strange (since he uses all 5 via a KVFM switch at the moment) when you could possibly move all the media and downloading/uploading (torrents, etc) over to a server? (We're also talking about quite a few external USB/firewire drives here too)

Remote desktop/SSH would be required, I guess. The only thing is I don't want to dump a server with no GUI on him straight away.

I think what he'd ideally like to do is move all of this over to a server that all the computers could access (Samba?). We're talking games, files, and media. He also has plans to make a website with a database.

Any ideas?

---

### Post by ryazkhan on 2008-03-31
samba is something you can consider of which you can use as domain controller as well. Do you have any Linux server running in your environment? if yes do these codes on you linux machine I am assuming that you have ubuntu Linux running. To become root do this
> sudo bash  
To install samba and winbind do this
> apt-get install samba winbind
Now you have samba and winbind running on you machine so stop both services by doing
> /etc/init.d/samba stop
> /etc/init.d/winbind stop
Since both services are stopped so remove some files 
> rm /var/lib/samba/*.tdb
> rm /var/run/samba/*.tdb
> rm /var/cache/samba/*.tdb
Now change your samba configs file by doing this command
> gedit /etc/sabma/smb.conf
And in that file add these lines
> 
[global]
workgroup = MYDOMAIN (your_domain_name)
netbios name = ubuntu (machine_hosting_samba_server)
logon drive = H: 
domain master = yes
preferred master = yes
domain logons = yes
wins support = yes
passdb backend = tdbsam
security = user

[homes]
comment = Home
path = %H
read only = no
browseable = no

[printers] 
comment = All Printers
path = /var/spool/samba
printable = yes
public = no
writable = no
create mode = 0700
browseable = no

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no
write list = root

[netlogon]
path = /netlogon
read only = yes
guest ok = yes
You can comment the rest of this file for now and later on umcomment whatever thing/s you want to do.
Now start samba and winbind
> /etc/init.d/samba start
/etc/init.d/winbind start
Edit host file and replace 127.0.1.1  with IP address of your machine (samba server)
> gedit /etc/hosts
Edit nsswitch.conf file 
> /etc/nsswitch.conf
and find   *hosts:*
add  *wins files *in front of hosts and leave the rest
Add root user in samba database
> smbpasswd -a root
Restart samba and winbind
> /etc/init.d/samba restart
/etc/init.d/winbind restart
If every thing went well you will be able to test your server so do this
> smbclient -L localhost
you might get error saying smbclient is not installed or some so intall it 
> apt-get install smbclient
Now restart samba and winbind again just to be safe and then test your server by running > smbclient -L localhost 
Provide root's samba password, if every thing went well we will see our new domain Good luck !
Now we have samba running and it is time to add some neccessary groups etc. Do these codes
> net groupmap add ntgroup="Domain Admins" unixgroup="root" type=domain
net groupmap add ntgroup="Domain Users" unixgroup="users" type=domain -U root
net groupmap add ntgroup="Domain Guests" unixgroup="nogroup" type=domain -U root
That is it you done now you should be able to join machines to this domain, but you have to add names of all machines you want to join in samba database 
> useradd xpmachine$ (replace winxp with the name of client machine)
smbpasswd -a -m xpmachine$ (replace winxp with the name of client machine) 

Now go to your xp machine and right click on my computer and select computer name then select change and click on domain radio and type your new domain. It will prompt you for samba password so enter root as user ID and root's samba password and hit enter you will see a message like welcome to domain. Restart the machine and try to logon to that domain.
you will be able to do that.
to add share in samba domain 
> [sharename]
path = /home/sharename
browseable = yes
read only = yes/no depanding on you requirements

[COLOR="Red"]Note: All stated above configuration will get you started and will make a very basic setup for you if you want some customization you are on your own![/COLOR]

---

### Post by masque7 on 2008-03-31
> **ryazkhan said:**
> samba is something you can consider of which you can use as domain controller as well. Do you have any Linux server running in your environment? if yes do these codes on you linux machine I am assuming that you have ubuntu Linux running. To become root do this
 
To install samba and winbind do this

Now you have samba and winbind running on you machine so stop both services by doing
I'm trying to help my friend with his network (and how he can condense power and gain ease etc with use of a server)..

All of his network is Windows-based. He wants a Linux or BSD server because of the benefits (ie. no rebooting, uptime, etc)

---

### Post by ryazkhan on 2008-03-31
I just put the whole procedure for samba. Look at it now
Yes I agree with Linux benefits over windows.

---

### Post by Poleh on 2008-03-31
definately consolidating him down onto a single server box running Ubuntu would be a good thing. You don't even have to run server edition initially; if you want to keep it simple why not pick the most powerful desktop he's not using and put Ubuntu desktop onto it? You can then install SAMBA and some other networking tools and you should be god to go.

---

### Post by masque7 on 2008-03-31
> **ryazkhan said:**
> I just put the whole procedure for samba. Look at it now
Yes I agree with Linux benefits over windows.
Yes, and I'm very grateful for that. However, what I'm trying to say is.. my friend (who I haven't even officially proposed this idea yet), has never, and isn't currently running any form of Linux. He has a number of desktops and notebooks. For example, he has 5 desktops hooked up to a KVM switch with many drives (external and internal) spread out amongst his machines.



> **Poleh said:**
> definately consolidating him down onto a single server box running Ubuntu would be a good thing. You don't even have to run server edition initially; if you want to keep it simple why not pick the most powerful desktop he's not using and put Ubuntu desktop onto it? You can then install SAMBA and some other networking tools and you should be god to go.
yes, this is what I was thinking. Which is why I asked, "Is server edition suitable?"

I believe most of his network is wireless. So what o/s would be best to run the router off of?

I may propose to him that he should buy a server case (with lots of room for his internal drives), and just use Ubuntu 7.10 as a server with SAMBA.

Not sure about other networking tools that would benefit his situation apart from remote assistance

---

### Post by PanzerMKZ on 2008-03-31
I would say prob not.  Get him a gui and let him learn on that.  With the server it is great but it is a big change from windows.  And yes there are cli torrent programs such as rtorrent that would be good.  But start with a gui.


Panzer

---

### Post by masque7 on 2008-04-01
> **PanzerMKZ said:**
> I would say prob not.  Get him a gui and let him learn on that.  With the server it is great but it is a big change from windows.  And yes there are cli torrent programs such as rtorrent that would be good.  But start with a gui.


Panzer
I heard it is possible to install a GUI on the server?

But anyway just giving him a filesharing 'server' with SAMBA and a torrent client on 7.10 will be fine. I'm thinking Xubuntu here. Meant to be much lighter - is it as easy to use as KDE and GNOME?

Deluge, rtorrent? I've never used rtorrent myself... Is the commandline hard to get used to?

---

### Post by ryazkhan on 2008-04-01
Yes I would agree with GUI. Try GUI (unbuntu desktop edition) first because it is very easy to use and configure and you can do all thing you can do in server and on top of that you have gui stuff too. I will do that if I am new to linux:)

---

### Post by masque7 on 2008-04-01
We've decided that I'm going to set up him a xubuntu server with LAMP, SAMBA, SSH/VNC, FTP, and webmin (I've been doing my research :).)

Obviously I'm going to use the wiki so it'll be a fun project. Maybe once i'm confortable I'll remove the GUI (no point having packages you don't need), and go all CLI.


Thanks for the help all

---

### Post by Deathrend on 2008-04-01
For a start, I will tell you have I've played with Linux off and on now for 10 years (Mostly Red Hat, and some older Debian).  I've also used Novell NetWare (PreLinux Novell).  But most, I go for windows networking and servers.  I spend enough time around command prompts and batch files that I could potentially build my own windows OS..

With that said, my home network consists of five physical servers, running running Ubuntu 7.10,  one with 8.04, and the last two with Windows Server 2003 Enterprise Edition.

I'm probably more die-hard wndows than your friend, (I currently own six licences to differnt Windows 2003 server OS's).  I recently started playing with Ubuntu however when I picked up a free ProLiant ML370 G2, sporting Dule Intell PIII 1.4Ghz processors and three gigs of ram.  This thing wasn't going to support any windows server OS /well/ so I decided on Ubuntu Server.  Since then, I've converted two more servers over to Ubuntu, and upgraded that one to 8.04.  

Durning all of this time, I've only killed it once, and thechnicly, I didn't kill it, it was a simple "sudo apt-get remove --purge packages".  I was really trying my hardest to brake it, playing with every software package that sounded like something I wanted to play with, until finally something took my LAMP server with it.

Tell your friend this, take one PC, turn it into an ubuntu server/desktop, and do whatever he can to it.  When he has a problem, go to google and I will almost bet within ten minutes of looking, his problem will be solved.

Now tell him to take his windows XP PC and do the same, I bet he will do a really fast about face on his ideals, I know I did.  Being in support/systems administration, I've spent WEEEKS looking for simple problems, that just can't be fixed.  I currently have a one hour policy at work, if it takes more than the time to reinstall the OS, I just swap the computer (All files are saved on a local file server, don't worry).

I have yet to have to reinstall Ubuntu (Well, atleast from it imbloding).  I have yet to have Ubuntu crash, and I have yet to have my Ubuntu server die after a lot of poking/proding/what's-that-thing-do?

Edit: Two things, Webmin is your friend, and Samba is more of a pain when running an active directory domain than you could ever immagine, however with a normal workgroup, your golden

Hope this helps, I'll stop babbling now ;)

---

### Post by masque7 on 2008-04-01
Yeah, I'm going down the road for the same career. :)

Would you recommend I connect the xubuntu server/desktop to the router directly, or would it be fine wirelessly? I don't exactly want to spend more time than I have configuring a wirless card/USB dongle.

Should I stick with 7.10 or 8.04? Also, since we're slowly going to transfer all of his slave and external drives over to the server, would this still work fine considering [I think] all his drives are NTFS? IIRC *ubuntu can now WRITE (as well as read) to/from NTFS.

Note on that - installed a new drive on Ubuntu: easy via CLI? I'm guessing it would either auto-detect it or I'd have to manually mount it.

Thanks again all

---

### Post by Deathrend on 2008-04-01
I have never had much luck with Linux Wireless, however I haven't played with it more than once or twice.  I'm guessing the GUI version however would be a lot simpler to use than the command line portion.

As for harddrives, your USB Thumb drives are more than likely a form a FAT, which is easily read by Linux, NTFS is readable, however you lose your fie permissions (Which isn't really a big deal unless you're working with a file server, thisalso depends on how it's managed, if it's a remote drive via networking, they will be intact, however mounting a drive with them will be ignored.)

As for version, I really can't see a diifferense, for production, you always go with the most stable (In tthis case 6.06) however for home users, you could go wih 8.04 and probably not see anything in the way of issues, more so with the full version coming out in 20(ish) days.

---

### Post by masque7 on 2008-04-02
> **Deathrend said:**
> I have never had much luck with Linux Wireless, however I haven't played with it more than once or twice.  I'm guessing the GUI version however would be a lot simpler to use than the command line portion.
yeah, we won't be running on acient hardware either (not *too* old anyway..

[quote=Death]As for harddrives, your USB Thumb drives are more than likely a form a FAT, which is easily read by Linux, NTFS is readable, however you lose your fie permissions (Which isn't really a big deal unless you're working with a file server, thisalso depends on how it's managed, if it's a remote drive via networking, they will be intact, however mounting a drive with them will be ignored.)[/quote]
not sure what you meant be the last bit - but i can tell you that you can now get NTFS write permissions (if that's what you did mean)

[quote=Death]As for version, I really can't see a diifferense, for production, you always go with the most stable (In tthis case 6.06) however for home users, you could go wih 8.04 and probably not see anything in the way of issues, more so with the full version coming out in 20(ish) days.[/QUOTE]
yeah, by the time i do get round to it 8.04 will most probably be the choice to make

Thanks

---

