---
title: "Bionic Beaver can not discover samba hosts - netbios."
date: 2018-02-14
forum: Ubuntu Development Version
---

### Post by Morbius1 on 2018-02-14
Samba on the Linux desktop never gets a break. 

Ubuntu 18.04 contains version 4.7.4 of the samba client libraries which brings with it a lot of improvements but it changes one parameter that will cause this forum nothing but grief. It changes the upper default smb dialect that the samba client uses to SMBv3.11 from the earlier default of NT1 ( Samba speak for SMBv1 ).

Conceptually it should not make any difference to host browsing but what that does is disable host browsing ( netbios host discovery ). If you go to Files > Other Locations > Windows Network this will be the result: [ATTACH=CONFIG]278524[/ATTACH]

The only way out of this is to edit /etc/samba/smb.conf and override the default by adding a line in the [global] section  setting it back to the old default:

**First**: Ubuntu does not install a smb.conf in 18.04 so I suggest you install the samba client package:
```
sudo apt install smbclient
```
**Second**: Then edit /etc/samba/smb.conf and right unser the workgroup = WORKGROUP line add this line to change the default:
```
client max protocol = NT1
```
**Last**: Reboot

[COLOR=#0000cd]**But**[/COLOR] ... there is a reason why Samba set the client max to SMBv3.11. Windows 10 and many other SMB / Samba servers have disabled SMBv1 for security purposes. If the Linux client can only use SMBv1 no connection is possible to these servers.

So we as desktop users are [COLOR=#0000cd]**between a Rock:**[/COLOR]

If you set "clent max protocol" back to NT1 the Linux client will be able to find all the servers but will not be able to connect to any that disabled SMBv1.

[COLOR=#0000cd]**And a Hard Place:**[/COLOR]

If you allow the default of SMBv3.11 it will not be able to discover the servers but it will be able to connect to them.

[COLOR=#0000cd]_**NOTE**: This is not a host name resolution problem - it's a host browsing ( discovery ) problem._
[/COLOR]
** You can still connect to the server by name but you have to know it's name and you must connect to to it explicitly by that name .. as in ... smb://hostname or use Connect to Server in Nautilus.

** Any server that uses the more modern multicast DNS service announcement provided by Avahi in Linux and also available in macOS are unaffected. These servers will display correctly in "Other Locations" in Nautilus.

** And  a CIFS mount is unaffected by all this since it runs with it's own defaults.

** There is also one other odd peculiarity about all this and that's smbtree. The smbtree command which is a samba client command has no problem finding these servers and listing their shares. It appears that smbtree is using the client min / max protocol correctly starting with SMB1 first then moving up to SMB3. It appears to me that this is either a gvfsd-smb-browse problem or a libsmbclient problem.

---

### Post by #&amp;thj^% on 2018-02-14
Thanks Morbius1 for the very detailed heads-up.
Much Appreciated! :)

---

### Post by sdowney717 on 2018-02-15
I noticed clicking in the windows network brings up nothing at all, even though I have many shares from windows PC. One windows 7, the other windows 10.

---

### Post by Morbius1 on 2018-02-17
There's a certain irony here that compels me to post my personal thoughts on the status of Samba on the desktop. What triggered it is yet another silly post stating that Samba is just for Windows.

When asked about Samba in an all Linux network my response was follow these 3 steps:

[1] Right click a folder you own > Local Network Share > select some boxes
[COLOR=#0000cd]That will automatically install the correct samba for you automatically.[/COLOR]

[2] Create a file at /etc/avahi/services/samba.service with this content on all your Linux boxes:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">SMB %h</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```
[COLOR=#0000cd]This will "publish" your samba server to the rest of the network - but it's only discoverable to other Linux boxes or MacBooks. The whole Windows specific netbios mechanism and the source for this bug topic as well as the vast majority of support questions about Samba is eliminated.[/COLOR]

[3] To increase speed and reduce if not eliminate disconnects set the smb client to SMB3 by editing smb.conf and adding this parameter:
```
client max protocol = SMB3
```

Ubuntu 17.10 does step [2] for you automatically and seamlessly - using a different approach but still using avahi.

Ubuntu 18.04 does steps [2] and [3] for you automatically. 

So what we end up with in 18.04 is a file sharing system that if you didn&#8217;t know any better appears to be specifically designed for and works best with an all Linux network.

---

### Post by ubname on 2018-03-03
Excellent explanation Morbius1, this post should be stuck in network session of the forum (sticky ?)

---

### Post by Morbius1 on 2018-04-21
This is getting better and better folks. I just installed today's daily  build of Xubuntu 18.04 and ... um ... there is no smb.conf file to edit.

So  I will update my first post to include installing smbclient first, then  making the change, and - this is the best part - rebooting.

---

### Post by s-byczkowski on 2018-05-31
Upstream discussion is just worthless. libgnomevfs2-extra.deb is missing libsmb.so in the /usr/lib/x86_64-linux-gnu/gnome-vfs-2.0/modules/ that's why browsing smb does not work.  Ehh.

---

### Post by cariboo on 2018-05-31
Thread closer. Bionic has been released.

---

