---
title: "Issues with Samba"
date: 2017-01-04
forum: Server Platforms
---

### Post by MorneDJ on 2017-01-04
OK. I have been battling with this for more than a month now and it is just getting more problematic. I have installed a few ubuntu servers (3, so I am no expert) with samba without issues, but now I have screwed something up badly.

I setup a new Ubuntu 16.10 server and added Samba using apt-get. I then shared the drive and was able to connect via a Windows PC (same logon details). The idea however was to use security to allow only certain people access to the server and the files. I added two samba users. I used a few guidelines I found on the web, but I could not get it working.

So I decided, screw that, let me just give all access and will sort out security later and changed the settings back to what it was previously. Yet, now I could not connect. And I tried a few different solutions, yet nothing. Today, after spending hours, I suddenly could not even see the server. 

So, I decided to start again and remove/purge samba and reinstall. Did a purge and removed the config file and the /etc/default/samba files.

Did a apt-get update ... Then I tried to reinstall ... 

[IMG]https://www.flickr.com/photos/147496785@N08/31952898752/in/shares-8051fi/[/IMG]
[https://www.flickr.com/photos/147496785@N08/31952898752/in/shares-8051fi/](https://www.flickr.com/photos/147496785@N08/31952898752/in/shares-8051fi/)

Can some-one please tell me what I can do to fix this, I seriously do not wish to reinstall Ubuntu and the RAID system.

---

### Post by TheFu on 2017-01-04
Things I do to make samba stuff easy.

* Get all systems able to ping each other by hostname. That can be DNS or /etc/hosts. hostnames are lowercase.
* Only use linux file systems for the storage presented by samba. Not NTFS. Not *FAT*.
* Keep all userids lowercase.
* Keep all share names as 1 word. No funny characters or spaces or punctuation. I have used underscores and that works.
* There are 4 different "security models" for Samba.  Simple setups probably want "User" as the mode.
* Shares that will be for more than 1 user need to be from storage outside /home/
* For individual shares, just for each person, use the [Homes] section.
* Don't expect root to work over samba.
* If using symbolic links outside the share file system (to add more storage), additional options are needed. These added options impact overall security negatively.
* Setup samba passwords using **smbpasswd** for every account. No idea why normal userids can't be used and authenticated. Guess this requirement is more flexible?

When troubleshooting, use the **testparm** command to see the settings your config file pushes.

I've never used anything other than /etc/samba/smb.conf to configure samba. I've never used AD for authentication either. The normal settings needed to get samba working are pretty trivial, if those things are handled.

Can't read the image. Please copy/paste the text and use "*code tags*" here so things line up (Adv Reply). If you haven't setup ssh - do that first so access to the "server" can be conveniently, securely, made from any client system you like.

---

### Post by darkod on 2017-01-04
I would add to the above: Use only LTS releases. Which means 16.04 LTS instead of 16.10.

Yes, it's not "latest and greatest" but LTS releases have 5 years support and are meant to be most stable and reliable.

Standard releases have only 9 months support (by the time you have configured and tweaked it, it's out of support already) and I see them only as "steps in between" LTS releases. Linux servers are for stability and long running. Even for home I would never install a version that has such short support, unless it's only for a quick test.

---

### Post by Morbius1 on 2017-01-04
The only way you are ever going to get any help with your situation is for you to post the output of this command which will tell the good people here how you are set up:
```
testparm -s
```

I will tell you one thing I can and just did reproduce your error in less than 10 seconds:
[ATTACH=CONFIG]273042[/ATTACH]
I did it by changing the security mode to "share". All this and other fun things will be revealed when you post your testparm -s output.

If you can't run "testparm -s" just post the content of the entire file:
```
 cat /etc/samba/smb.conf
```

And please tell people what kind of network this is. Is this just a home network or is it some exotic enterprise / AD thingy. If it's the latter I will try to bow out gracefully from this topic ....

I will give you my own short list ( 1 item ) of things to do and not do: Stop purging samba.

There is a file located at /usr/share/samba/smb.conf that is a duplicate of the original default that is there for people like us that muck about so much that we need to reset ourselves.

            [TABLE]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by MorneDJ on 2017-01-05
Thanks for the reply guys. I will try and take it one for one.

* I can ping the host names and the various PCs using IP and host names.
* The ubuntu server only use linux file systems (think that the server is ext4, may be ext3)
* two users, morne and shaun. All lowercase. Not morné as per my correct name.
* Share name is NAS.
* Did a default install. Did not know that.
* The share is /storage/ mounted as NAS. Same as he share name.
* Not using individual space, this is to share work files.
* I got root working over samba on another server, but now I tried nobody
* Not using symbolic links
* Created the users with smbpasswd for each account.

Because I purged testprm does not work ... gives me;

> **> testparm -s**Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384) Error loading services.

Before I purged the smb.conf file contained:


> 

[NAS]
    comment = EARES files
    path = /storage
    public = yes
    force user = nobody
    valid users = morne shaun
    writable = yes
    browseable = yes 




I also tried root as the force user and valid user, i left that out and about 20 other iterations (seriously, tried for a few hours)

---

### Post by MorneDJ on 2017-01-05
After copying back my smb.conf file and reinstalling I have a working server. I changed the config manually by copying the contents of the other samba server 100%. Will test without changing anything for the next day on other PCs to check it is working. It seems that my smb.conf file was missing as I manually deleted it and samba do not reinstall the config file once it was installed.

Output from testprm -s is:

> **> testparm -s**Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[NAS]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = Yes
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    unix password sync = Yes
    dns proxy = No
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    browseable = No
    printable = Yes
    create mask = 0700


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[NAS]
    path = /storage
    force user = root
    guest ok = Yes  read only = No

Now to setup so that only two users can log in and get files on it. I do not want to share this with the other users on the network (7 people in total, basic network using unmanaged switch .. nothing fancy or strange).

I will again create two users but how do I manage that we need to log in ? Anything weird that I have to do on the windows PC's ?

---

### Post by darkod on 2017-01-05
I have open shares so the windows login doesn't matter in my case, but from reading here it is definitely best the windows login to match the linux/samba login. So if your two users always use same windows login, try to create the linux/samba users with identical username. That should help a lot.

If the passwords also match, the share will not even ask them for credentials. It should open directly and they should have the correct permissions according to what you allowed them in samba/linux.

---

### Post by Morbius1 on 2017-01-05
There's actually nothing wrong with this share definition:
> [NAS]
    comment = EARES files
    path = /storage
    public = yes
    force user = nobody
    valid users = morne shaun
    writable = yes
    browseable = yes 
Depending on how you are using the server and what you mean by this:
> * Not using individual space, this is to share work files.

It's a little odd that you are forcing the user to be "nobody" but it will only work if the "/storage" folder is owned by "nobody". To check:
```
ls -dl /storage
```

---

