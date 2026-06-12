---
title: "Bacula-Help with which files to back up"
date: 2009-12-30
forum: Server Platforms
---

### Post by Lori700698 on 2009-12-30
I got my 1T storage unit for Christmas and I got Bacula all connected up and talking to the new unit and the desktops that I am planning on backing up.  I'm assuming I only need to grab the home folders on those (if I should save something else there please mention it.)  What I'm more confused on and way more concerned with is my server.  I've worked my butt off the past year learning the modules and getting it the way I want it and I don't want to loose anything really important or some of the settings I spent weeks figuring out.  So here's my file list, I know I have made changes in the ones tagged back-up...would there be anything in the ones I don't have tagged that could have settings in I would need?

I have SQL, Bind9, Apachae,Squid Proxy, Citadel,Linux Firewall,users/passwords, and Webmin are the servers/programs I have made the most modifications to and have user settings/emails/files.  I have some cron jobs and boot scripts that I modified too.
Thank you so much!
Lori

bin
boot
command
dev
etc = Back-Up
home =  Back-Up
include = Empty
lib
lost+found = Empty
media
mnt = Empty
opt = Back-Up
proc
root = Back-Up
sbin
service = Empty
snort = Back-Up
srv = Empty
sys
tmp =Not-Needed
usr = Back-Up (not sure what's in this that I may need)
var = Back-Up

---

### Post by mhanson on 2009-12-30
For the server, if you have the space... back it all up (I exclude /dev and /proc). At least once a month and then in daily or weekly incraments.  You should be able to configure bacula to do it that way. If the monthlys get to big then archive them off onto DVD or another hard drive.

Also, I like to keep fairly recent disk image of all my servers handy. This way i can rebuild a server from the image and then apply whatever incramentals I need since the image was made. I use "clonezilla" for the imaging. It has been great so far.

Cheers.

---

### Post by Lori700698 on 2009-12-30
Oh my gosh, I need to clone too?  This thought never even crossed my mind.  Can Clonezilla get a whole server on a CD/DVD?

---

### Post by mhanson on 2009-12-31
Depends on how large your server install is. You can tell colnezilla to use compression and to split the image into sizes of your choice. 

Cheers

---

### Post by HermanAB on 2010-01-01
On not so critical systems, I just make a tar ball of /etc and back up the data.  If the whole server goes south, I would want to install the latest version of Linux anyway.

Critical systems, I install as virtual machines and then I keep the data outside the VM on a disk array (which could simply be some USB disks!).  I then tar and burn the whole VM to a DVD.  This way I can restore a server super fast on any hardware.

---

### Post by steven.jones on 2010-01-01
I backup /etc and /home I also do /var/www as I have a web site.

Lastly dump/export an output from your database and back that up? I dont see you doing that.

I would also suggest a "spare" disk and do tar.gz's to once a month of the above....I get away with an old 36gb scsi for that....it really depends on how big /home is.

---

