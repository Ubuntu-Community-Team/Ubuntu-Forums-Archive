---
title: "Samba configuration issues"
date: 2015-09-01
forum: Server Platforms
---

### Post by ricardo35 on 2015-09-01
First of all, my apologies if I did something wrong. This is my first post here and also quite a newbie in the Ubuntu matter.
Secondly; I'm Dutch so my English isn't perfect but hey ;)

I've spent many houres in Google, reading forums etcetera and I've managed to create a clean install of Ubuntu Server LTS with webserver capabilities and mysql up and running with UFW, Fail2ban and so on. So I'm getting the hang of it.

Recently I've started a new project which involves creating my own file server. 

Did a clean install of ubuntu server. Installed samba. Created two shares ( Private and Guest ). The problem is that (after days) I can't seem to get the configuration right of the users.

The 'guest' folder is read / write for everyone
The 'prive' folder is read / write for only me ( ricardo, member of group prive ).

I've created screenshots of my config. I don't know what's going wrong?


[ATTACH=CONFIG]264153[/ATTACH][ATTACH=CONFIG]264154[/ATTACH][ATTACH=CONFIG]264155[/ATTACH][ATTACH=CONFIG]264156[/ATTACH]

---

### Post by Morbius1 on 2015-09-01
Are the clients to this server running Linux or Windows?

What you have will work for Linux clients but not for Windows clients - depending on which share is accessed first.

[COLOR=#0000cd]**Some friendly advice on future posts: **[/COLOR][B][COLOR=#000000]

[/COLOR][/B][COLOR=#0000cd]Don't attach screeshots of terminal output. That will annoy most folks so much they will not respond to your posts. Do a cut and paste to the forum instead so that the responder can copy and paste it with corrections or illustrations.

[/COLOR]

---

### Post by ricardo35 on 2015-09-01
Hi Morbius1,

Thank you for your reply.

About the screenshots, my appologies. Will keep that in mind for future references!

About the clients:
Clients are Windows PC's and Mac / OSx mostly. Also there's an Western Digital TV remote media player which will connect to it through SMB.

Why will this work on Linux but not on Windows clients?

---

### Post by Morbius1 on 2015-09-01
>  The 'guest' folder is read / write for everyone
No it is not. The samba share says it is but the Linux permissions says it's writeable only to "nobody"
> drwxr-xr-x 3 nobody nogroup 4096 Sep 1 13:06 guest

If all you had was the "Guest" share all of this would work. The Windows or Linux client would access the share since credentials are not required or given. The client is considered a "Bad User" and the "map to guest" operator in smb.conf would convert this "Bad User" to "nobody" The Linux permissions on the folder allow write to "nobody" ( and only "nobody" ) and everything works.

But then you created the "Prive" share and made it accessible only to members of the "prive" group.

When those users access the "Prive" share and their credentials are accepted by samba they are no longer "Bad User"s, they will no longer be converted to the user "nobody", and although they will be able to read the contents of the folder they will not be able to write. Once Windows successfully passes working credentials for a given share for a host it uses those same credentials to access all other shares on that host. It's a Windows thing.

There are literally dozens of ways around this problem. Here's just 2:

Change the shared folder to allow everyone to write:
```
sudo chmod 777 /shares/guest
```

OR, Add a line to the share definition for [Guest] so that all users become "nobody" for that share:
```
force user = nobody
```

It depends on how this server is being used. If you are populating the guest folder with things outside of samba then something more complicated needs to be done. If it's just a Public share that will be used only for other samba / smb clients this may be the only thing you need.

---

### Post by ricardo35 on 2015-09-01
Hi Morbius1, 

Wow, that was a very clear explanation. I now understand what is happening. Thanks a lot!

I went for the first suggestion because I liked that option more. Unfortunately, when accessing the share it directly pops up with the credentials box from Windows and thus not showing neither of both shares ( nor Guest, nor Prive ).
I did an ls- l which returned this:

ricardo@samba:/shares$ ls -l
total 8
drwxrwxrwx 3 nobody  nogroup 4096 Sep  1 13:50 guest
drwxrwxr-x 3 ricardo prive   4096 Sep  1 13:50 prive
ricardo@samba:/shares$

I would think that Guest is writable now for all users in the Linux permissions, right?

I did see one thing I forgot to say. In my SMB.conf ( see screenshot I added in my first post ) I put a # in front of security = user, just for testing reasons.
Obviously I removed the # again now. Don't know if it makes a difference.

---

### Post by Morbius1 on 2015-09-01
That symptom I cannot reproduce here. 

Did you add yourself to the samba password database:
```
sudo smbpasswd -a ricardo
```

---

### Post by ricardo35 on 2015-09-01
Yes I did. When navigating from Windows to \\192.168.1.89 ( ubuntu machine ) then it directly comes up with the login screen to provide my credentials. As soon as I log in with user 'ricardo' and it's password, it displays both shares ( guest and prive ) and I can write to both folders.

---

### Post by ricardo35 on 2015-09-01
I also did your option two, adding force user = nobody at the Guest section but that didn't help neither unfortunately.

Edit:

I came across this article:
[https://help.ubuntu.com/lts/serverguide/samba-fileprint-security.html](https://help.ubuntu.com/lts/serverguide/samba-fileprint-security.html) 
> [COLOR=#333333][FONT=Ubuntu]Now that Samba has been configured to limit which groups have access to the shared directory, the filesystem permissions need to be updated.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Traditional Linux file permissions do not map well to Windows NT Access Control Lists (ACLs). Fortunately POSIX ACLs are available on Ubuntu servers providing more fine grained control. For example, to enable ACLs on [FONT=monospace]/srv[/FONT] an EXT3 filesystem, edit [FONT=monospace]/etc/fstab[/FONT] adding the [FONT=inherit]*acl*[/FONT] option:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]UUID=66bcdd2e-8861-4fb0-b7e4-e61c569fe17d /srv  ext3    noatime,relatime,acl 0       1
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Then remount the partition:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=monospace]sudo mount -v -o remount /srv[/FONT]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit]The above example assumes [FONT=monospace]/srv[/FONT] on a separate partition. If [FONT=monospace]/srv[/FONT], or wherever you have configured your share path, is part of the [FONT=monospace]/[/FONT]partition a reboot may be required.[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]To match the Samba configuration above the [FONT=inherit]*sysadmin*[/FONT] group will be given read, write, and execute permissions to [FONT=monospace]/srv/samba/share[/FONT], the [FONT=inherit]*qa*[/FONT]group will be given read and execute permissions, and the files will be owned by the username [FONT=inherit]*melissa*[/FONT]. Enter the following in a terminal:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=monospace]sudo chown -R melissa /srv/samba/share/[/FONT]
[FONT=monospace]sudo chgrp -R sysadmin /srv/samba/share/[/FONT]
[FONT=monospace]sudo setfacl -R -m g:qa:rx /srv/samba/share/[/FONT]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit]The [FONT=inherit]*setfacl*[/FONT] command above gives [FONT=inherit]*execute*[/FONT] permissions to all files in the [FONT=monospace]/srv/samba/share[/FONT] directory, which you may or may not want.[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Now from a Windows client you should notice the new file permissions are implemented. See the [/FONT][/COLOR][COLOR=#333333][FONT=inherit]*acl*[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] and [/FONT][/COLOR][COLOR=#333333][FONT=inherit]*setfacl*[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] man pages for more information on POSIX ACLs.[/FONT][/COLOR]

Do you think it could have something to do with this?

---

### Post by Morbius1 on 2015-09-01
I've never once set an ACL on a folder to accommodate Samba so I can't help you with that, sorry.

> When navigating from Windows to \\192.168.1.89 ( ubuntu machine ) then  it directly comes up with the login screen to provide my credentials. As  soon as I log in with user 'ricardo' and it's password, it displays  both shares ( guest and prive ) and I can write to both folders.         
So what's the problem? The only odd thing is that it's asking for credentials at the host level not the share level. It could be because your user name on the Windows machine is also ricardo.

What I can tell you is that I took Ubuntu 14.04, removed the shares that I did have on that machine and replaced them with yours. I didn't go as far as you did in tossing out the whole smb.conf configuration I simply added your Guest and Private shares to the default smb.conf. Changed ownership of the guest folder to nobody/nogroup and applied 777 to the folder.

When I access this from Win10 I have free access to the Guest share and am asked for credentials for the Private share.

---

### Post by ricardo35 on 2015-09-01
Hmmm... that IS the case ideed, my username on Windows is also Ricardo. So that's the problem then that is shows the credential box on host level instead of share level?
Can you explain that a bit more? ( the why and how ).

Currently I'm starting ( again ) from scratch (reinstall ubuntu). This time I will not use Ricardo but another name to see how it acts.

---

### Post by Morbius1 on 2015-09-01
You don't need to reinstall Ubuntu to reset smb.conf if that's why you are doing it. There&#8217;s a backup copy of the default already present.

Here's a little secret: Linux doing samba / smb file sharing is a lot easier and more coherent that Windows doing smb. Windows has enough quirks in it to fill a small book.

When Windows accesses a samba/smb server it passes the current user's local login user name automatically. They must think that's feature.

This forces the Linux samba server to do something with it:

** If the user doesn't exist in Linux, "map to guest = Bad User" applies and the Windows user is converted to "nobody" and has access to guest shares.

** If the user does exist in Linux but the samba password for that user does not match exactly what is on the Windows machine for that user then you will be promoted for credentials. SInce Windows is doing this at the host level the prompt for credentials happens at the host level.

[COLOR=#0000cd]**EDIT**[/COLOR]: Boarding a plane to go to some place called Pitts ...um ... Pittsburgh. I don't know when I'll be able to get back to this but I suspect not until tomorrow.

---

### Post by ricardo35 on 2015-09-01
:D

Beginning to like Linux more than Windows. 

The Windows username was indeed the problem why the login box was showing directly on host level instead of share level. So everything is ALMOST perfect.
I created the user 'malissa' ( girlfriend ) and gave her a password ( smbpasswd ). Made her member of the group prive which is defined as valid users in SMB.conf.

[COLOR=#ff0000]1) When she accesses the share Guest, everything is ok. She can read and write. However when accessing Prive, the credentials are asked and she puts malissa and her password but it doesn't get accepted. -->[/COLOR][COLOR=#000000]Never mind, forgot to set a password for the Ubuntu system too. Then it worked. Oh and apparently Windows needs some refreshing ( closing explorer and opening it again ). [/COLOR]

2) Another question. Since nobody:nogroup is owner of the share guests, who should I put as owner of Prive ? Now I have malissa:prive  but what if later on I would like to give myself for example access ( user ricardo, which will be also member of prive ). I believe it should be set to groupowner only and not user specified. Hope you understand what I mean...

3) Can the users that I create also logon to my Linux machine? And if so, how do I prevent this since I don't want this of course. 

Thanks again for your help. You showed me more in the past houres then I was learning in the last week. Never would think that the Windows username was the cause of the problem.

---

### Post by CharlesA on 2015-09-01
> **ricardo35 said:**
> :D

Beginning to like Linux more than Windows. 

The Windows username was indeed the problem why the login box was showing directly on host level instead of share level. So everything is ALMOST perfect.
I created the user 'malissa' ( girlfriend ) and gave her a password ( smbpasswd ). Made her member of the group prive which is defined as valid users in SMB.conf.

[COLOR=#ff0000]1) When she accesses the share Guest, everything is ok. She can read and write. However when accessing Prive, the credentials are asked and she puts malissa and her password but it doesn't get accepted. -->[/COLOR][COLOR=#000000]Never mind, forgot to set a password for the Ubuntu system too. Then it worked. Oh and apparently Windows needs some refreshing ( closing explorer and opening it again ). [/COLOR]

2) Another question. Since nobody:nogroup is owner of the share guests, who should I put as owner of Prive ? Now I have malissa:prive  but what if later on I would like to give myself for example access ( user ricardo, which will be also member of prive ). I believe it should be set to groupowner only and not user specified. Hope you understand what I mean...

3) Can the users that I create also logon to my Linux machine? And if so, how do I prevent this since I don't want this of course. 

Thanks again for your help. You showed me more in the past houres then I was learning in the last week. Never would think that the Windows username was the cause of the problem.

2: It depends on the folder. I have a bunch of folders set to my user as the user and another group for the group so I can access them from my HTPC or other device without setting the file-level permissions to be readable by all.

3: If you created the users via smbpasswd, they only have a samba user and no actual shell user on the system.

This is a bit old, but it might help.. maybe..
[http://charlesauer.net/tutorials/ubuntu/samba3-ubuntu.php](http://charlesauer.net/tutorials/ubuntu/samba3-ubuntu.php)

---

### Post by ricardo35 on 2015-09-02
Hello CharlesA, Morbius1,

Just wanted to let you know that it works like a charm now. Thank you very much with your help.
I do still have some questions about the owner of the shared folder. I still don't understand who should be the owner of it. However, it works now. Time to 'CloneZilla' it to a live machine now :D

Next steps:
- How to mount USB drives
- How to set them in RAID
- Warn me when disks are getting full

Next projects:
- Asterisk server
- Fog server

Once again, I thank you for your help and... until we meet again!

---

### Post by CharlesA on 2015-09-02
> **ricardo35 said:**
> Hello CharlesA, Morbius1,

Just wanted to let you know that it works like a charm now. Thank you very much with your help.
I do still have some questions about the owner of the shared folder. I still don't understand who should be the owner of it. However, it works now. Time to 'CloneZilla' it to a live machine now :D

That all depends on how you want to file permissions to be set up or if you are just going to be using the share permissions within the smb.conf file. If you are just going to use the permissions you set in smb.conf, you can ignore who owns the folders and just leave it as is.

> Next steps:
- How to mount USB drives
- How to set them in RAID
- Warn me when disks are getting full

You can mount USB drives the same way you mount other drives - via the mount command.

As far as RAID goes, it depends, but you'll need some throughput if you want to use RAID, otherwise rebuilds or syncing will take ages over USB2.

Shell script can run to let you know when the disks are getting low on space.

---

### Post by Morbius1 on 2015-09-02
> I do still have some questions about the owner of the shared folder. I  still don't understand who should be the owner of it. However, it works  now. Time to 'CloneZilla' it to a live machine now :grin:

If all access to /shares/prive is done through samba it doesn't matter who owns the folder.

Originally it was owned by ricardo/prive Now it's owned by malissa/prive. Either one would work since your share definition allows access by anoyone who is a member of the prive group. 

> [Prive]
path = /shares/prive
[COLOR=#0000cd]**valid users = @prive**[/COLOR]
guest ok = no
writeable = yes
browseable = yes
And the Linux permissions of the folder being shared allows write by that group:
>  drwx[COLOR=#0000cd]**rwx**[/COLOR]r-x 3 ricardo prive   4096 Sep  1 13:50 prive

---

### Post by ricardo35 on 2015-09-02
Thanks for the clarification!

---

