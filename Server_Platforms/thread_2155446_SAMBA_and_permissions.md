---
title: "SAMBA and permissions"
date: 2013-06-18
forum: Server Platforms
---

### Post by twinpeaksr on 2013-06-18
**_Background:_**
My Ubuntu "Server" (Desktop install with Samba, moving to server install in December) motherboard crashed and burned last week.  Due to the age I decided to upgrade to a newer board/processor/memory.  The upgrade went fine, but the system was having issues with many missing/different drivers, and still being new to Linux I just re-installed 13.04 (Fresh install) and figured I needed practice setting things up anyway.

Everything loaded and worked great, until I got to Samba, that is where the saga started.  I come here after 2 days of searching forums (here and others) and being unable to solve my problem).

**_Setup:_**
- Trinity: Ubuntu 13.04 "Server" w/Samba on static IP address (192.168.0.5)
- Roadrunner: My workstation on Windows 7 using router DHCP
- Nelly: Wife's computer on Windows 7 using router DHCP

-Twinpeaksr: My user on all systems, same password on all systems (Also administrator on all systems)
-Mary: My wife's user on all systems, same password on all systems (Not administrator on any systems)
-twinpeaks: group on server that we are both member of, also listed as group that owns the folder being shared

_**Issue:**_
The problem is simple: I have the shares setup and can access them fine with my user on any system.  My wife's user can not access the shares, gets the "You do not have permissions" error when trying to access, it worked before I rebuilt the system.

**_What I tried:_**
I have tried many things to fix this and look to the intelligence of this forum to help me identify what I am missing.

[LIST=1]
[*]Have created both Samba (smbpasswd) and Unix user on server
[*]Have created a group (twinpeaks) with both users in it and added to samba valid users
[*]changed ownership of the folder to the "twinpeaks" group that we both are in
[*]Added her user to my group (twinpeaksr)
[*]Changed permissions to full permissions for everyone on the folder (chmod 0775 and 0777 tried)
[*]enabled guest account in Samba
[*]removed password on unix/samba user for her account
[*]added password back on to match windows machine
[*]verified that on the same computer, I can access shares if I login
[*]added her account to the valid users in samba directly
[*]made her an administrator on the server
[*]re-installed Samba
[*]set myself as the guest account
[/LIST]

I have also restarted SMBD and NMBD after every change.  I have restarted the Windows machine, I have restarted the server.  All of this has the same results: I can access the share without issue with my user, she has no access.  I am sure the issue is on the server/samba side, but I am running out of options.  I have tired a few diagnostic items as well:

[LIST=1]
[*]tried 'smbclient nellly -NL', could not access the samba client
[*]tried 'smbclient roadrunner - NL' (where I am logged in), get a response that says it is good
[*]Network connections are confirmed good, and I can see the shares at '//trinity/', but when I click on the shares they give the permission error only with her login
[*]verified that she was added to the twinpeaks user group using 'groups mary'
[/LIST]

**_smb.conf_**
```
[global]
    ; General server settings
    netbios name = trinity
    server string =
    workgroup = workgroup
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    unix password sync = yes
    ; null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    syslog = 1
    syslog only = yes

[Shared]
    path = /media/data500G/Shared
    browseable = yes
    read only = no
    guest ok = yes
    guest account = twinpeaksr
    valid users = @twinpeaks mary twinpeaksr
    create mask = 0644
    directory mask = 0755

```

I am running out of options, anyone have any other ideas I can try tonight?

Thanks!

---

### Post by matt_symes on 2013-06-18
Thread moved to **server platforms** with a redirect in the old sub-forum.

There may be more samba users here.

---

### Post by twinpeaksr on 2013-06-18
Thanks for the move, sorry, was not sure the best place to post.

---

### Post by CharlesA on 2013-06-18
Double check the permissions. If you have enabled guest sharing via smb.conf and they still cannot connect, it is more than likely a permissions issue. Also run this:

```
smbtree
```

It will ask your user password.

---

### Post by TheFu on 2013-06-18
Wow. Seems like you've done everything I could have suggested.  I can only suggest that you double-check for small errors - perhaps typing everything in backwards to ensure you do not make an unconscious mistake?

Besides that, I'd suggest:
* do not set the guest account to a normal user.  use nobody.
* Check the UNIX file permissions for  /media/data500G/Shared - especially the user and group permissions. Be certain that both users are in the UNIX group specified.
* I've never used Samba groups, only UNIX groups.
* Verify that all user accounts are lowercase. Do not mix case in user accounts on any systems.
* R U running a WINS server?  If not, disable that.
* The create mask and directory masks are not good for folders shared by groups. You probably want to relook at that.
* Consider setting up a [Homes] stanza to give access to /home/{userid}/ folders for each individual.
* Review the /etc/log/samba/* log files for each connection.  Turn up the smbd verbosity until enough information is provided that you see the authentication error.

Sorry, don't think anything here will give her access, but perhaps.

---

### Post by CharlesA on 2013-06-18
> **TheFu said:**
> * Check the UNIX file permissions for  /media/data500G/Shared - especially the user and group permissions. Be certain that both users are in the UNIX group specified.
* I've never used Samba groups, only UNIX groups.

I've only used UNIX groups as well and did most of the permission stuff via UNIX permissions instead of dealing with Samba itself.

@OP: If you are still having issues, you might give this tutorial a shot:
[http://charlesa.net/tutorials/ubuntu/samba3-ubuntu.php](http://charlesa.net/tutorials/ubuntu/samba3-ubuntu.php)

/shamelessplug

---

### Post by twinpeaksr on 2013-06-18
> **CharlesA said:**
> I've only used UNIX groups as well and did most of the permission stuff via UNIX permissions instead of dealing with Samba itself.

@OP: If you are still having issues, you might give this tutorial a shot:
[http://charlesa.net/tutorials/ubuntu/samba3-ubuntu.php](http://charlesa.net/tutorials/ubuntu/samba3-ubuntu.php)

/shamelessplug

Thanks for the link, the shameless quote has got some good information that I could not find in the other tutorials, I will try out some of the things tonight and let you know how it works.

The groups I was referring to were Unix groups, not samba groups, just to clarify.

> **TheFu said:**
> Wow. Seems like you've done everything I could have suggested.  I can only suggest that you double-check for small errors - perhaps typing everything in backwards to ensure you do not make an unconscious mistake?

Besides that, I'd suggest:
* do not set the guest account to a normal user.  use nobody.
* Check the UNIX file permissions for  /media/data500G/Shared - especially the user and group permissions. Be certain that both users are in the UNIX group specified.
* I've never used Samba groups, only UNIX groups.
* Verify that all user accounts are lowercase. Do not mix case in user accounts on any systems.
* R U running a WINS server?  If not, disable that.
* The create mask and directory masks are not good for folders shared by groups. You probably want to relook at that.
* Consider setting up a [Homes] stanza to give access to /home/{userid}/ folders for each individual.
* Review the /etc/log/samba/* log files for each connection.  Turn up the smbd verbosity until enough information is provided that you see the authentication error.

Sorry, don't think anything here will give her access, but perhaps.

Glad to hear I at least gave a valiant effort!

- I will disable the guest account once things get working, that was one of my failed tests.
- permissions on Shared are I am the owner, group is twinpeaks (with both of us in it) and permissions are 0775.
- Did verify all users are in lower case on server, will check her machine, one thing I did not think of!
- I am not intentionally running WINS, so I guess I can disable?  I would hope I would know if I have that running!
- Any recommendations on masks?   Still new to all of this permission stuff, my goal is to get it up and running and then tune it up, since it is just my wife and I who have access right now.
- I have several shares of files that are used on several machines by several users (my wife, me, and some HTPC machines, soon my son), not sure the [Homes] will meet most of those needs, though it may be a good item for the personal directories (FYI, [Shared] is not the only share i have, one of 12, just trying to get one working first)
- will look a the logs, tried last night but still learning where all of them are.

Thanks, will let others know how tonight goes with this new information.

---

### Post by CharlesA on 2013-06-18
Good luck! I wrote that tutorial originally when I set up my 10.04 server and ran into a ton of conflicting information. so far it still works for 12.04 and Debian Wheezy. :)

Hope it works for you, too.

---

### Post by TheFu on 2013-06-18
I suggested the [Homes] as a way to validate each userid is working. If they can access their [Home], then the password/userid is configured and working. Sorry, I didn't explain that at all.

I have 3 different shares:
* [homes] (per-user files)
* Data (shared for different people)
* Backups (only way that I've found to actually backup Windows stuff)

---

### Post by twinpeaksr on 2013-06-18
Understand now!

Setup with the homes directories and was able to access with both users!  I assume that will get me closer to a solution???!?

One note, if I used 'valid users = %s' in the homes section, I could not access with either user (mine that works on all or hers that works on non) and got a login prompt when clicked on share.

So with this information what is my next step?  I can get it running, but there is still something seriously wrong since I now can only have her account see her home directory.

Thanks!

---

### Post by koenn on 2013-06-18
long shot: 

your explanation talks of a user "Mary".  your samba config akkiws a user 'mary'. You sure she (or her Windows machine) is supplying the correct username

failed attempts to approach a share are probably logged somewhere. Maybe they tell you what's going wrong (you may have to increase log level)

---

### Post by CharlesA on 2013-06-18
> **twinpeaksr said:**
> Understand now!

Setup with the homes directories and was able to access with both users!  I assume that will get me closer to a solution???!?

One note, if I used 'valid users = %s' in the homes section, I could not access with either user (mine that works on all or hers that works on non) and got a login prompt when clicked on share.

So with this information what is my next step?  I can get it running, but there is still something seriously wrong since I now can only have her account see her home directory.

Thanks!

Check out what koenn posted below:

> **koenn said:**
> long shot: 

your explanation talks of a user "Mary".  your samba config akkiws a user 'mary'. You sure she (or her Windows machine) is supplying the correct username

failed attempts to approach a share are probably logged somewhere. Maybe they tell you what's going wrong (you may have to increase log level)

I've always used lowercase for usernames, so that didn't occur to me.

If the homes share works for both, copy it and change the path and see what happens.

---

### Post by twinpeaksr on 2013-06-18
I tried copying the directory, and did not get it to work with that.

I also looked at the logs for her computer 'nelly' as well as her IP address, all logs for specific clients are empty.  checked the log.smbd and log.nmbd as well as log.samba, none show anything useful (mainly when I start and stop the service.

I also ran smbtree again, this time //NELLY showed up, where it did not before, probably because she can now access her home directory.

Seems like I am really close to getting this working but seem to be missing one piece!!  I hope to solve it tonight with the experts help here!

Thanks!

---

### Post by CharlesA on 2013-06-18
Can you post the results of this:

```
ls -ld /media/data500G/Shared
```

---

### Post by twinpeaksr on 2013-06-18
drwxrwxr-x 17 twinpeaksr twinpeaks 4096 Jun 17 17:20 /media/data500G/Shared

---

### Post by CharlesA on 2013-06-18
What file system is it using?

---

### Post by twinpeaksr on 2013-06-18
ext4

---

### Post by CharlesA on 2013-06-18
Ok. Run this then:

```
id mary
```
```
id twinpeaksr
```

---

### Post by twinpeaksr on 2013-06-18
Now it is getting wierd...

So if I create a directory, in this case /Data/tester, then chown and chgrp to mary, and share via samba, she can access it.
If I take /media/data500G/Shareed and chown and chgrp to mary, and share via samba the exact same way, she can not access it!

These were on two different hard drives, is there a possibility that this could be the clue needed to solve the mystery?  I checked the permissions she has and access external storage devices automatically is in there.  Also we are a member of the same groups.

I am not loving permissions right now...

---

### Post by twinpeaksr on 2013-06-18
> **CharlesA said:**
> Ok. Run this then:

```
id mary
```
```
id twinpeaksr
```

```
twinpeaksr@trinity:/media$ id mary
uid=1004(mary) gid=1004(mary) groups=1004(mary),27(sudo),46(plugdev),1000(twinpeaksr),124(sambashare),1005(twinpeaks)
twinpeaksr@trinity:/media$ id twinpeaksr
uid=1000(twinpeaksr) gid=1000(twinpeaksr) groups=1000(twinpeaksr),27(sudo),46(plugdev),124(sambashare),1005(twinpeaks)

```

---

### Post by twinpeaksr on 2013-06-18
Based on my last exiriment I think I can rule out the machine and samba, seems that I have a permissions issue:

- not machine, can access home directory without issue and access directory when created from scratch on boot drive
- not samba because can create shares that work

Is there something that I am overlooking with the diferent hard drives playing a part in this?  I changed the mapped drive group to twinpeaks and that did not have an effect.  Not sure what is going on, still learning about all the permissions stuff.

---

### Post by twinpeaksr on 2013-06-18
Figured it out!

It was the drives

before
```

drwx------   4 twinpeaksr twinpeaksr 4096 Jun 17 19:42 data1T
drwx------   4 twinpeaksr twinpeaksr 4096 Jun 17 19:42 data2T
drwx------  12 twinpeaksr twinpeaks  4096 Jun 17 19:42 data500G
drwx------   3 twinpeaksr twinpeaksr 4096 Jun 16 20:15 parity2T

```

after:
```

drwxrwxr-x   4 twinpeaksr twinpeaksr 4096 Jun 17 19:42 data1T
drwxrwxr-x   4 twinpeaksr twinpeaksr 4096 Jun 17 19:42 data2T
drwxrwxr-x  12 twinpeaksr twinpeaks  4096 Jun 17 19:42 data500G
drwx------   3 twinpeaksr twinpeaksr 4096 Jun 16 20:15 parity2T

```

Access works now, Thanks for the help!

---

### Post by CharlesA on 2013-06-18
chmod 777 all those and see what happens.

EDIT: Derp, need to read slower.

Glad you got it sorted. :)

---

### Post by twinpeaksr on 2013-06-18
works now with chmod 0775.

Now I can tune in the permissions.

Thanks!

---

### Post by CharlesA on 2013-06-18
Welcome! Enjoy your new shares. :)

---

### Post by twinpeaksr on 2013-06-18
Will do until I fill them up again!

Hope it goes easier in Dec when I build the new server.

Thanks again!

---

