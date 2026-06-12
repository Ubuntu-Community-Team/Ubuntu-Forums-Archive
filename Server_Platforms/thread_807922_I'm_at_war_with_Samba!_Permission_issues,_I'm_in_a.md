---
title: "I'm at war with Samba! Permission issues, I'm in a desperate situation, please help!"
date: 2008-05-26
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-05-26
Hello all this is really starting to get to me now!
All I want is to set up a home file server ( and learn something in the process )with 4 IDE drives (ext3 at the mo). 
I have an 80gb, 2x40gb and a 60gb. I would like each user to have their own directories on the 40gb, plus a shared directory on there. The 80gb will be used for torrent flux & amule. 1 40gb for business and work, and the other for backup.
I would like everyone to have an an account giving them access to their directories and the general shares. I would like only me and my father to have access to the business directory.

Here's what I've done so far - 

- Installed hardy
- Installed Ubuntu-Desktop & Cut out the fat
- Installed Webmin
- Using Webmin Changed workgroup to 'Simpsonnet'
- Using Webmin mounted all drives to media/ (general, torrents, backup & business)
- adduser gareth, + 3 other family members
- smbpasswd gareth, + same as above (this command may be incorrect, i found a command to add samba users from cli last time but think I forgot it)

From windows I can view the shares but can't write. The owner of the shares seems to be root and when I right click on the file to change permissions it wont let me, even if i use gksudo nautilius.
Last time I was able to write no problem. If I remember rightly I added users to samba and ubuntu and it just worked, I must be following a different process.
I wish I hadn't reinstalled! I was having problems with LAMP and messed up config files so I started again thinking it would be easier! I had torrentflux, amule, a website and filesharing working.
All the drives are backed up at the mo so I don't care about the data and I will probably do another reinstall as I think kde-core will be better than ubuntu-desktop. (will the server & kde-core fit on a 4gb drive?)
Someone please help me, this is all I've worked on since friday night. I'm well behind on my work cos I chose to fix ubuntu first, I wont be able to rest till, I sort it! 
I'm begging everyone here, to spare 10 mins of their time and you will make me extremely happy!

Thanks again every1!

Gareth

---

### Post by windependence on 2008-05-26
```
sudo chown -R /media/gareth
sudo chown -R /media/<each of the other users>
```

Do this in a terminal.

Restart samba both smb and nmb just to make sure.

also, the samba users and Windows users must have the same user ID and password, and it's case sensitive on Linux.

-Tim

---

### Post by garethsimpsonuk on 2008-05-26
thanx 4 the reply what does the -r mean? i tried chmod 777 * and this worked but this is unsafe? can i do this for each individual share to achieve the above?
i log in as administrator on my xp box (i know its bad!) and so does my brother on his laptop. this s gonna cause problems isn't it?

---

### Post by elbeano on 2008-05-26
The -R makes the command recursive... it applies on directories and files in the path.

I gave up trying to use XP with < admin access long ago. It will not be a problem from perspective of the samba box. The user permissions you set there will be the issue.

---

### Post by windependence on 2008-05-26
> **garethsimpsonuk said:**
> thanx 4 the reply what does the -r mean? i tried chmod 777 * and this worked but this is unsafe? can i do this for each individual share to achieve the above?
i log in as administrator on my xp box (i know its bad!) and so does my brother on his laptop. this s gonna cause problems isn't it?

Well as you know, neither of those options are secure. Did you change the OWNERSHIP of those directories like I wrote? I didn't say change any permissions. You might want to change the permissions back to 755 to make them a bit more secure, but make sure you change the OWNERSHIP too.

-Tim

---

### Post by garethsimpsonuk on 2008-05-26
Well i was in the process of installing ebox (don't ask me why webmin is fine) and something went wrong so I'm reinstalling it again lol. 
When it's done I will take your advice and chown all my shares. so is this the right way guys?

- install ubuntu + webmin
- mount drives using webmin to /media/ (there is an option to 'mount shares as' and default is root. should i change it?) Would I be better using CLI for all this? how do i do it?
- share the mounts using webmin (what are commands for cli?)
- add users to ubuntu with adduser name
- add users to samba..how? (there is an option in webmin to convert unix user to samba, use that?)
- chown /media/backup, torrents, & media (do i do it each time for each user that i want to give read/write permissions, on each folder) i want everyone to have full rights on all shares but only me and dad on business.
- jump for joy if i get this far without another reinstall and install my bells & whistles (torrentflux, amule, rsync, sftp, vnc, media streaming etc.)

Is this the process I follow? i'm actually getting somewhere now so please put with me for a lil longer!
i think i might take the plunge and leave out the gui cos I always used the terminal anyway.

Thankyou so much you guys you've been great. I recognise Windependence from helping me before so thanks, without this forum I would've gave up on the first boot! I've learned loads and have believe it adds to my webdesign skillset (which I am also still learning.

Cheers

---

### Post by windependence on 2008-05-26
> **garethsimpsonuk said:**
> Well i was in the process of installing ebox (don't ask me why webmin is fine) and something went wrong so I'm reinstalling it again lol. 
When it's done I will take your advice and chown all my shares. so is this the right way guys?

- install ubuntu + webmin
- mount drives using webmin to /media/ (there is an option to 'mount shares as' and default is root. should i change it?) Would I be better using CLI for all this? how do i do it?

You don't have to mount them from Webmin, and you can mount them anywhere you want. Here is the CLI version. Remember mount what where.

```
mount -t /dev/hda /media/gareth
```

The above command mounts your first hard drive (hda) on /media/gareth. Your device may be different than hda depending on what kind of disks you use. You can try the commands:


```
sudo ls /dev/hd*
```

or

```
sudo ls /dev/sd*
```

to find out what drives are on your system.


> - share the mounts using webmin (what are commands for cli?)

I'd have to look in the SAMBA manual.


> - add users to ubuntu with adduser name
- add users to samba..how? (there is an option in webmin to convert unix user to samba, use that?)

You can set an option in SAMBA to automatically make all your Linux users SAMBA users, that way you only have to add them using the adduser command.

> - chown /media/backup, torrents, & media (do i do it each time for each user that i want to give read/write permissions, on each folder) i want everyone to have full rights on all shares but only me and dad on business.

You need each user to own his or her directory. You may want to create a group for files you want everybody to share and make them part of the group.

> - jump for joy if i get this far without another reinstall and install my bells & whistles (torrentflux, amule, rsync, sftp, vnc, media streaming etc.)

Is this the process I follow? i'm actually getting somewhere now so please put with me for a lil longer!
i think i might take the plunge and leave out the gui cos I always used the terminal anyway.

Thankyou so much you guys you've been great. I recognise Windependence from helping me before so thanks, without this forum I would've gave up on the first boot! I've learned loads and have believe it adds to my webdesign skillset (which I am also still learning.

Cheers


Just remember, those Linux guys don't say RTF for nothing, you really can learn from reading the manuals.

-Tim

---

### Post by garethsimpsonuk on 2008-05-26
Thanks a lot mate. Yea I do read manuals, a lot of them + ebooks & videos. but there's always a lot of different ways of doing things and different factors can affect the approaches. I just wanted some opinions and someone to verify that I was doing everything correct.
On forums where I'm not a noob and it's me giving the advice I find it very annoying when someone hasn't tried themselves. If they have tried and they're still stuck I will help them if I have the time & knowledge.
Admittedly I haven't read the samba manual so I will go and do it now while ubuntu's installing. Is it on the website? because I can't access my terminal to use the man command.

So can you confirm if this is correct?

mount -t /dev/sda /media/main
mount -t /dev/sdb /media/torrents
mount -t /dev/sdc /media/business

(i want them mounted in media)

adduser gareth
etc.
etc.

add same users to samba

sudo chown -R /media/main/gareth
sudo chown -R /media/main/dean
sudo chown -R /media/torrents/gareth
sudo chown -R /media/torrents/dean
sudo chown -R /media/business/gareth
sudo chown -R /media/business/dean

this will give read / write access to dean & gareth (i know I've got this bit wrong, if you correct anything plz correct this)

thanks for your help mate, appreciate it

-

---

### Post by garethsimpsonuk on 2008-05-26
Thanks a lot mate. Yea I do read manuals, a lot of them + ebooks & videos. but there's always a lot of different ways of doing things and different factors can affect the approaches. I just wanted some opinions and someone to verify that I was doing everything correct.
On forums where I'm not a noob and it's me giving the advice I find it very annoying when someone hasn't tried themselves. If they have tried and they're still stuck I will help them if I have the time & knowledge.
Admittedly I haven't read the samba manual so I will go and do it now while ubuntu's installing. Is it on the website? because I can't access my terminal to use the man command.

So can you confirm if this is correct?

mount -t /dev/sda /media/main
mount -t /dev/sdb /media/torrents
mount -t /dev/sdc /media/business

(i want them mounted in media)

adduser gareth
etc.
etc.

add same users to samba

sudo chown -R /media/main/gareth
sudo chown -R /media/main/dean
sudo chown -R /media/torrents/gareth
sudo chown -R /media/torrents/dean
sudo chown -R /media/business/gareth
sudo chown -R /media/business/dean

this will give read / write access to dean & gareth (i know I've got this bit wrong, if you correct anything plz correct this)

thanks for your help mate, appreciate it

-

---

### Post by windependence on 2008-05-26
You can't have two user own the directory at one time. The last chown command will be the person who owns it. There is also group ownership and in the case where you want two or more users to own the directory you should set up a new group (like main_users) and add gareth and dean to that group. Then make your directory owned by that group and set your permissions so only that group has rw access. Look up the addgroup command to see how to add the group and then use the usermod command to add the users to the group. Here is a good start:

[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)


-Tim

---

### Post by windependence on 2008-05-26
To automatically add a linux user to samba go into your /usr/sbin/adduser script and after the last line add:

```
smbpasswd -a "$LOGIN"
```

After the unix account had been created you will then asked for the samba password for the user. This only works if you add a user by the command line, not sure how to do this with a gui.

-Tim

---

### Post by garethsimpsonuk on 2008-05-26
ok brilliant thanx again. i appreciate it

---

