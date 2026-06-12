---
title: "File permission issue on Samba share"
date: 2014-01-09
forum: Server Platforms
---

### Post by Tony_Lillie on 2014-01-09
I'm running Ubuntu 12.04 Server with a single basic Samba share, set up to allow access without passwords. I can read and write files from all of my several Windows clients without issue, but I can't read or write to the Samba share folder or sub-folders when I am on the server locally. I'm sure it's some kind of file permissions thing, but after 2 hours searching and reading I still can't get it nailed down.

The share folders all have "nobody" as the user, and "no group" as the group. I used the guide at this URL to do the initial set-up:  [https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)   Apparently the nobody/nogroup thing was necessary so I could access the share from all the clients without a password. When I successfully changed the user to "myusername" using this command ```
**sudo chown myusername.nogroup /srv/samba/share/**
```

it gave me local control of the folder but I lost access from the Windows clients.

I need both local and client read/write access to the Samba share folder. How do I achieve this?

---

### Post by bab1 on 2014-01-10
> **Tony_Lillie said:**
> I'm running Ubuntu 12.04 Server with a single basic Samba share, set up to allow access without passwords. I can read and write files from all of my several Windows clients without issue, but I can't read or write to the Samba share folder or sub-folders when I am on the server locally. I'm sure it's some kind of file permissions thing, but after 2 hours searching and reading I still can't get it nailed down.

The share folders all have "nobody" as the user, and "no group" as the group. I used the guide at this URL to do the initial set-up:  [https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)   Apparently the nobody/nogroup thing was necessary so I could access the share from all the clients without a password. When I successfully changed the user to "myusername" using this command ```
**sudo chown myusername.nogroup /srv/samba/share/**
```

it gave me local control of the folder but I lost access from the Windows clients.

I need both local and client read/write access to the Samba share folder. How do I achieve this?

That tutorial is incorrect.  You*** do not need to set the ownership to nobody:nogroup*** to provide non-authenticated access.

What you do need is a common group that all users can belong to.  Then you need to set the sgid bit  on the root directory of the share to provide the group inheritance for all files and folders below the root.  In your case that would be /srv/samba/share.  The last thing is to add the users to the common group.  There is a group that is already set up for just that.  It's called *users*.  You can see it with this command```
getent group users
```...it should be group 100.

There are a million ways to achieve this and quite a few to get around this, but in the end you need a consistent user group ID (e.g. 100) with all the users in it.

Linux file system ownership and permissions always trump any Samba setting.  Acting on the files directly (if I understand you correctly) has nothing to do with Samba at all.

I recommend that you create a new share at /srv/samba/share2.  Set the ownership to root:users.  Set the sgid bit (sudo chmod g+s).  Add yourself to the *users* group.  Now create a file in the directory /srv/samba/share2 (touch /srv/samba/share2/test.file.  What do the permissions look like?  Post the output of these 2 commands```
ls -ld /srv/samba/share2

ls -l /srv/samba/share2
```

If all is working you can now create the share and add all the other users to the *users* group.  It should all just work.  I'm assuming that you are familiar with Linux and Samba.  If you need a more detailed description just ask.

---

### Post by Tony_Lillie on 2014-01-21
**I apologize for not responding.** Apparently my account is not set up to get automatic email alerts for replies. I'll fix that in a minute!

Thank you for your helpful counsel. I will try the things you have instructed and report back later today.

---

### Post by tfrue on 2014-01-21
If you aren't worried about security, just edit the share for:
[code]
[YourShare]
guest ok= yes (This is the security problem as it will be open)
browseable= yes
read only= no
writeable= yes[/code
Save, restart the Samba deamons, and you should be set! I set the owner:user to my samba users I created and that worked for me.

Good luck,
Chris

---

### Post by bab1 on 2014-01-21
> **tfrue said:**
> If you aren't worried about security, just edit the share for:
```

[YourShare]
guest ok= yes (This is the security problem as it will be open)
browseable= yes
read only= no
writeable= yes
```
Save, restart the Samba deamons, and you should be set! I set the owner:user to my samba users I created and that worked for me.

Good luck,
Chris

Samba only authenticates you to the share.  The underlying Linux file permissions ultimately permits access (authorization).  [COLOR="#0000FF"]Authentication[/COLOR] (who are you?) is different than [COLOR="#FF0000"]authorization[/COLOR] (are you permitted read, write or eXecute permissions?).

---

### Post by Tony_Lillie on 2014-01-21
Ok, I've got it set up and here are the results for the commands you instructed me to run.

```
drwxr-sr-x 2 root users 4096 Jan 21 16:07 /srv/samba/share

total 0

```

Does that look right.

I'm going to test local and client access and report back.

---

### Post by Tony_Lillie on 2014-01-21
Well, this didn't work at all. I can see the share from a windows client, but it requires a username and password for access. When I enter the user and pass from my user account on the server I can map the share, but I can't write to it.

At the local server I can obviously open the share, but I can't write to it.

I'm sure it's possible I did something wrong, but maybe I wasn't clear. I need FULL read and write access WITHOUT passwords or logins of any kind both locally (at the server) and from several windows clients.

Can somebody please help me?? I had this set up and working from the windows clients but couldn't write to the share folder locally (at the server terminal).

---

### Post by bab1 on 2014-01-21
> **Tony_Lillie said:**
> Well, this didn't work at all. I can see the share from a windows client, but it requires a username and password for access. When I enter the user and pass from my user account on the server I can map the share, but I can't write to it.

At the local server I can obviously open the share, but I can't write to it.

I'm sure it's possible I did something wrong, but maybe I wasn't clear. I need FULL read and write access WITHOUT passwords or logins of any kind both locally (at the server) and from several windows clients.

Can somebody please help me?? I had this set up and working from the windows clients but couldn't write to the share folder locally (at the server terminal).

Is your user in the ***users** * group?  What does the share configuration look like?

---

### Post by Tony_Lillie on 2014-01-21
Yes, running the following command I see that my username is definitely in the users group.```
getent group users
```

Here is the configuration from /etc/samba/smb.conf

```
[share]
    comment = MediaServer Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0075


```

---

### Post by bab1 on 2014-01-21
> **Tony_Lillie said:**
> Yes, running the following command I see that my username is definitely in the users group.```
getent group users
```

Here is the configuration from /etc/samba/smb.conf

```
[share]
    comment = MediaServer Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0075  [COLOR="#FF0000"]<-- This should be 0664 -- it's for files only[/COLOR]


```

See my comment in red above.

Here is my share config for one of my public shares
```
[public]
        comment = Shared Data
        path = /srv/public
        browseable = yes
        guest ok = yes
        force group = users
        writeable = yes
        create mask = 0664
        force directory mode = 2775

```

---

### Post by bab1 on 2014-01-21
I just noticed this is WRONG also```
drwxr-sr-x 2 root users 4096 Jan 21 16:07 /srv/samba/share
```

It should be```
drwxrwsr-x 
```..that's rwx for the owner and rwx for the group and r-x for others (2775 not 2755).

---

### Post by Tony_Lillie on 2014-01-21
Changed my config file according to your counsel and no change. Still cannot write to the share folder from the local server, and still cannot write to the share folder from a windows client.

This doesn't seem to be getting me anywhere.

Any other ideas??

If not, I'm going to re-install and go back to my previous configuration. At least then i could read and write from all of my windows clients.

---

### Post by bab1 on 2014-01-21
> **Tony_Lillie said:**
> Changed my config file according to your counsel and no change. Still cannot write to the share folder from the local server, and still cannot write to the share folder from a windows client.

This doesn't seem to be getting me anywhere.

Any other ideas??

If not, I'm going to re-install and go back to my previous configuration. At least then i could read and write from all of my windows clients.

I can't see all that you see.  I'm not going to twist your arm to do something you don't want to do.  I don't "have ideas" I diagnose problems.  At this point I would guess you should just "re-install and go back to my previous configuration".

---

### Post by Tony_Lillie on 2014-01-21
Sorry, I didn't intend to come across snotty. I'm just frustrated that EVERYTHING in Ubuntu requires me to be a computer scientist. I have never yet done anything "ordinary" that doesn't turn out to be 8 hours in a forum and me wishing I had just spent the money for Windows.

So, what information can I give you to help you diagnose this situation more thoroughly?

---

### Post by bab1 on 2014-01-21
> **Tony_Lillie said:**
> Sorry, I didn't intend to come across snotty. I'm just frustrated that EVERYTHING in Ubuntu requires me to be a computer scientist. I have never yet done anything "ordinary" that doesn't turn out to be 8 hours in a forum and me wishing I had just spent the money for Windows.

As it should be.  In life it's always time or money. 
> 
So, what information can I give you to help you diagnose this situation more thoroughly?

Lets start at the beginning. Is the user name the same on all the client machines?  Is that user name also a Linux user (passwd) and in the Samba data base (smbpasswd -a)?  This is important if the client machines are Windows.

This is confusing:  "At the local server I can obviously open the share, but I can't write to it."  Does this meant you are mounting the Samba share (//server/share) to the Samba server hosts file system?  Can you create a file directly in the directory using either Nautilus or the command line (touch /srv/samba/share/test.file)?

Post the output of these CLI commands```

ls -l /srv

ls -l /srv/samba

ls -l /srv/samba/share

sudo pdbedit -l   # this is a lowercase ell)

cat /etc/samba/smb.conf

smbtree -d3

```

---

### Post by Tony_Lillie on 2014-01-21
Sorry, I already started over. I've re-installed, but I haven't done any of the samba configuration yet, so perhaps you can help me from the start.

The Windows clients each have a unique username, and none of them are in the Samba database.

What I was trying to communicate is that I can sit at the server console and open the file system and see the share folder, but am not able to create a new folder inside that folder. I can't make changes. I can't write to the file when I'm sitting in front of the server using its keyboard and mouse.

If I follow the guide at this URL (as I did before): [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)  I will be able to map the share as a network drive on any of my Windows clients (without logging in) and read/write to the share, but I can't write to the file on the physical server console.

I want to be able to access the share with full read and write privileges BOTH from Windows clients and locally on the server.  For example, I want to be able to put a flash drive in the server and copy files from the flash drive to the share folder. After following the previously mentioned guide I cannot do that. But I can create a folder inside the share folder from a Windows client and send files to that folder over the network. The guide gets me half way.

So, starting from scratch, what should I do?

---

### Post by bab1 on 2014-01-21
> **Tony_Lillie said:**
> Sorry, I already started over. I've re-installed, but I haven't done any of the samba configuration yet, so perhaps you can help me from the start.

The new install is good.  DO NOT USE THE GUIDE YOU REFERRED TO BELOW!  It's really easy to set this up without doing all of that.
> 

The Windows clients each have a unique username, and none of them are in the Samba database.

This is part of the problem -- But it is not a deal breaker.
> 

What I was trying to communicate is that I can sit at the server console and open the file system and see the share folder, but am not able to create a new folder inside that folder. I can't make changes. I can't write to the file when I'm sitting in front of the server using its keyboard and mouse.

Where **you** are is irrelevant.  Local in this context means you are using the kernel mounted file system.  Remote means you are using the userland virtual file system (VFS (cifs mounted i.e. //server/share).  These are 2 different things.  For our use we can call them FS (for kernel mounted) and VFS for cifs mounted (mounted).  An example of the FS is /etc or /home.  An example of VFS is anything you mount via cifs. 
> 

If I follow the guide at this URL (as I did before): [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)  I will be able to map the share as a network drive on any of my Windows clients (without logging in) and read/write to the share, but I can't write to the file on the physical server console.

I'll ignore this.
> 

I want to be able to access the share with full read and write privileges BOTH from Windows clients and locally on the server.  For example, I want to be able to put a flash drive in the server and copy files from the flash drive to the share folder. After following the previously mentioned guide I cannot do that. But I can create a folder inside the share folder from a Windows client and send files to that folder over the network. The guide gets me half way.

So, starting from scratch, what should I do?

The first thing to do is add all usernames of your users (the real humans) of the Samba shares to the group users.  Under normal conditions you would have the same username on all clients (such as tony).  Since you don't you can map those names to your Samba server user login.  I've never done this.  My usernames for users are the same on all machines in the network.  There is no "guest user on Samba as you would think"  When Samba encounters a userame it doesn't recognize it creates files using the username *nobody*.  This is part of your problem.  it is oonly partially addressed in the tutorial that you have tried before.

Do you want to create consistent usernames across the various computers?  Or you can add all those names to the Ubuntu server and then we will add them to the Samba database.

[COLOR="#0000FF"]**Edit:** I'm going to backup a bit here.  I think you can just add the user *nobody *to the group _users_ and achive the same effect.  All users will be able to read and write to the share.  This is just the first step in the process.[/COLOR]

---

### Post by Tony_Lillie on 2014-01-21
For simplicity sake, let's just work with my primary Windows client and I'll add the others later after I learn how to do it with this one.

So, I will start by adding the username from my Windows client to the "users" group. How do I do that?

---

### Post by bab1 on 2014-01-21
> **Tony_Lillie said:**
> For simplicity sake, let's just work with my primary Windows client and I'll add the others later after I learn how to do it with this one.

So, I will start by adding the username from my Windows client to the "users" group. How do I do that?

See my update.  Lets just add the user "nobody" to the group *users*.  The user nobody is a system user so nobody can login as that user.  Samba uses it as an anonymous user.

---

### Post by Tony_Lillie on 2014-01-21
Ok, managed to do that with the following```
# sudo adduser <username> <groupname>
```

Seems to have worked.

Next?

---

### Post by bab1 on 2014-01-21
> **Tony_Lillie said:**
> Ok, managed to do that with the following```
# sudo adduser <username> <groupname>
```

Seems to have worked.

Next?
Post the complete output of ```
getent group
```

Did you see my edited post and the post after that?

---

### Post by Tony_Lillie on 2014-01-21
Yes, I am watching this thread very closely now and greatly appreciate your help.

Here is the output you requested ```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:lillie
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:lillie
floppy:x:25:
tape:x:26:
sudo:x:27:lillie
audio:x:29:pulse
dip:x:30:lillie
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:lillie
staff:x:50:
games:x:60:
users:x:100:nobody
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
messagebus:x:105:
whoopsie:x:106:
mlocate:x:107:
ssh:x:108:
landscape:x:109:
winbindd_priv:x:110:
sambashare:x:111:lillie
netdev:x:112:
lillie:x:1000:
lpadmin:x:113:lillie
bluetooth:x:114:
scanner:x:115:
colord:x:116:
ssl-cert:x:117:
lightdm:x:118:
nopasswdlogin:x:119:
avahi-autoipd:x:120:
avahi:x:121:
pulse:x:122:
pulse-access:x:123:
utempter:x:124:
rtkit:x:125:
saned:x:126:


```

---

### Post by bab1 on 2014-01-21
Now add the username you use on Ubuntu to the group *users*.  If there are other users on the Ubuntu host (computer) and you want them to be able to wrote to the FS (what you call local) directory add them to the group *users *also.

---

### Post by Tony_Lillie on 2014-01-21
Ok, did it, same as before. It worked.

---

### Post by bab1 on 2014-01-21
> **Tony_Lillie said:**
> 
Here is the output you requested ```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:lillie
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:lillie
floppy:x:25:
tape:x:26:
sudo:x:27:lillie
audio:x:29:pulse
dip:x:30:lillie
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:lillie
staff:x:50:
games:x:60:
users:x:100:nobody
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
messagebus:x:105:
whoopsie:x:106:
mlocate:x:107:
ssh:x:108:
landscape:x:109:
winbindd_priv:x:110:
sambashare:x:111:lillie
netdev:x:112:
lillie:x:1000:
lpadmin:x:113:lillie
bluetooth:x:114:
scanner:x:115:
colord:x:116:
ssl-cert:x:117:
lightdm:x:118:
nopasswdlogin:x:119:
avahi-autoipd:x:120:
avahi:x:121:
pulse:x:122:
pulse-access:x:123:
utempter:x:124:
rtkit:x:125:
saned:x:126:


```

This is not a complete listing.  In the future please show all the output.  I won't ask questions that are security risks.

---

### Post by bab1 on 2014-01-21
> **Tony_Lillie said:**
> Ok, did it, same as before. It worked.

Show me.  ```
getent group 100
```

---

### Post by Tony_Lillie on 2014-01-21
Not sure what I missed, because that really is the entire unedited output.

Anyhow, here is the next ouput result ```
users:x:100:nobody,lillie


```

---

### Post by bab1 on 2014-01-21
> **Tony_Lillie said:**
> Not sure what I missed, because that really is the entire unedited output.

The user lillie should have a group named lillie also.  Post the output of ```
getent passwd lillie
```...this will show the user lillie and the group number (gid).  it will not show any password information.  Here is my entry on this machine```
bab:x:1000:1000:,,,:/home/bab:/bin/bash
```

---

### Post by Tony_Lillie on 2014-01-21
Here it is.```
lillie:x:1000:1000:Tony,,,:/home/lillie:/bin/bash


```

---

### Post by bab1 on 2014-01-21
> **Tony_Lillie said:**
> Here it is.```
lillie:x:1000:1000:Tony,,,:/home/lillie:/bin/bash


```
Now we can make the directory that will hold the Samba share, set the group ownership and permissions.  In this order use these commands```
sudo mkdir -p /srv/samba/share

sudo chown root:users /srv/samba/share

sudo chmod 2775 /srv/samba/share
```... This makes /srv/samba/share the root of this share.

Post the output of ```
ls -ld /srv/samba/share
```

---

### Post by Tony_Lillie on 2014-01-21
Here is the output: ```
drwxrwsr-x 2 root users 4096 Jan 21 22:54 /srv/samba/share
```

---

### Post by bab1 on 2014-01-21
> **Tony_Lillie said:**
> Here is the output: ```
drwxrwsr-x 2 root users 4096 Jan 21 22:54 /srv/samba/share
```

Now this command ```
touch /srv/samba/share/test.file
```

Show the output of this```
ls -l /srv/samba/share
```

---

### Post by Tony_Lillie on 2014-01-22
permission denied when I ran the first code.

Here is the output: ```
total 0


```

---

### Post by bab1 on 2014-01-22
> **Tony_Lillie said:**
> permission denied when I ran the first code.

Here is the output: ```
total 0


```
Log off and log back in (I assume as lillie).  The try the 2 commands again.

---

### Post by Tony_Lillie on 2014-01-22
That seems to have been the fix. Here is the output: ```
total 0
-rw-rw-r-- 1 lillie users 0 Jan 21 23:07 test.file
```

---

### Post by bab1 on 2014-01-22
> **Tony_Lillie said:**
> That seems to have been the fix. Here is the output: ```
total 0
-rw-rw-r-- 1 lillie users 0 Jan 21 23:07 test.file
```
So now you can write to the share directory from the local machine (the FS)

Is the Samba server installed and running?  Post the output of this```
pgrep -l mbd
```

---

### Post by Tony_Lillie on 2014-01-22
Yes, I installed it when i did the installation.

Here is the output: ```
729 smbd
808 smbd
1120 nmbd


```

---

### Post by bab1 on 2014-01-22
Let's create a share.  Add this to the bottom of your smb.conf file (note I used a different share name on purpose -- don't change it)```

[public]
        comment = Shared Data
        path = /srv/samba/share
        browseable = yes
        guest ok = yes
        force group = users
        writeable = yes
        create mask = 0664
        force directory mode = 0775


```

Then restart the Samba server daemon (smbd) with this```
sudo service smbd restart
```

If you have not touched the smb.conf file other than adding this share we should be able to see and use the share from a Windows client.

---

### Post by Tony_Lillie on 2014-01-22
Is there a way for me to officially thank you on this forum? Because you have been amazing!!

It works perfectly!!! Just mapped the share as a network drive from my windows client, and was able to create a new folder which means (obviously) I have write privileges. AWESOME!!

First, your knowledge level is the best I've seen yet and second, you have gone the extra mile for me and been exceedingly patient.

I want you to know that I have learned a great deal from this interaction. THANK YOU!!

---

### Post by bab1 on 2014-01-22
> **Tony_Lillie said:**
> Is there a way for me to officially thank you on this forum? Because you have been amazing!!

It works perfectly!!! Just mapped the share as a network drive from my windows client, and was able to create a new folder which means (obviously) I have write privileges. AWESOME!!

First, your knowledge level is the best I've seen yet and second, you have gone the extra mile for me and been exceedingly patient.

I want you to know that I have learned a great deal from this interaction. THANK YOU!!

Wait, were not done yet.  If you are going to expand on this you should name the actual directory something more descriptive. Maybe something like /srv/samba/public.  The reason I named the share [public] was to show you that the share name does not have to be the same as the actual directory!  You can rename the directory and edit the path and it looks the same from the client's perspective.

Thank you for the kudos.  I've been do this for 25+ years.  If we are done here you can mark the thread solved.  If you need to, you can post to the thread after you mark it solved and I will see the new post.

In the future remember that not all tutorials are vetted and not all tutorials apply to your version Ubuntu.  Things change and users post without knowing what they are talking about. :-(

---

### Post by Tony_Lillie on 2014-01-22
> **bab1 said:**
> In the future remember that not all tutorials are vetted and not all tutorials apply to your version Ubuntu.  Things change and users post without knowing what they are talking about. :-(

You said a mouthful there! How true, and I have learned it the hard way repeatedly. The best and worst thing about Linux is that there is a ton of information available and often more than one way to get from point A to point B.

Yes, I will probably rename the directory now that I understand better what I'm doing. Your 25 years of experience REALLY shows. I'm grateful.

---

### Post by Tony_Lillie on 2014-01-22
One last thing. How do I make the folders created within the share inherit the same permissions? Just a minute ago I copied several folders into the share from a different partition, but when I tried to write to one of those sub-folders inside the share I couldn't.

---

### Post by bab1 on 2014-01-22
> **Tony_Lillie said:**
> One last thing. How do I make the folders created within the share inherit the same permissions? Just a minute ago I copied several folders into the share from a different partition, but when I tried to write to one of those sub-folders inside the share I couldn't.
Is this from a different partition on the Ubuntu machine?

---

### Post by blairnic on 2014-06-27
My goal was to read/write to a share that I mounted and was having privilege problems.  The solution that worked for me is a simplified version of what I found here:

[http://ubuntuforums.org/showthread.php?t=2198667&highlight=nogroup](http://ubuntuforums.org/showthread.php?t=2198667&highlight=nogroup)

In summary:

1. Set the owner of the root folder of the mount point so that you are the owner: 
sudo chown [your_user_name]:[your_group_name] [full_path_to_mount_point]
Example: sudo chown jsmith:jsmith /media/fileshare

2. Dynamically set the group ID of all subfolders and files to the same as the group of the root folder of the mount point (which you just set to be owned by you:
sudo chmod g+s [full_path_to_mount_point]
Example: sudo chmod g+s /media/fileshare

While ls -l still shows subfolders and files as belonging to others, e.g. root, nobody, I can add, edit, and delete everything in the share with no problems.

---

### Post by bjbwood on 2015-01-03
Thanks BAB1 this worked for me.

Runining 14.04LTS for LogitechMediaServer on HPMicroServer O/S on one drive, music on another. LMS would not "see" the mounted vis FSTAB file. Shame it can't be done through Samba Server Configuration Tool 1.2.63 so easily!

---

### Post by tachyon47 on 2015-06-10
Hello,
This thread was quite helpful for getting my smb.conf and user permissions setup but I still seem to be missing something. 
How should I set the fstab options? So far I am just running off whatever the system automounts. I am using Xubuntu 14.04 LTS

*UPDATE*
Actually, I have a different problem. My Windows 7 box can access shares fine. It's just my Mac that can't. I tell it to authenticate as guest and I can see my shares listed but then I can't actually browse shares.
From Windows I can do both without authenticating.
I did remove a user that had the same name as my mac user name from Ubuntu to force guest access.

---

