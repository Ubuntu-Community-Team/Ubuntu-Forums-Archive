---
title: "Yet ANOTHER Samba Sharing to Windows Question!"
date: 2019-12-13
forum: Ubuntu/Debian BASED
---

### Post by soundesigner on 2019-12-13
My teeth hurt and my eyes are crossing!

I've read tutorials, posts, and recipes, watched YouTube tutorials, Googled for days, and all but held a seance.  I want to share files on a Linux-based box with a network of Windows PCs.  Currently I'm testing with an Atomic Pi (Intel Atom x5-Z8350 quad core) running Peppermint and I can get just far enough to be tantalized, but frustrated.  At first I could browse, open, and modify files in the Public directory (labeled "Publica") from my Win 10 PC.  Then I added a second share, a USB drive and now I can browse and read the Public directory, but can no longer write to it, and I can't get into the USB drive at all.

I have checked and rechecked the smb.conf file and have tried both the Samba GUI and using a text editor for set up, and "chmod 777'd" the heck out of the directories in question.  I will gladly post that configuration for someone more knowledgeable than I am to spot the issue.  Thanks!


[IMG]http://dolphinradio.org/wp-content/uploads/2019/12/samba3.jpg[/IMG]

---

### Post by Morbius1 on 2019-12-13
No one here knows how you set up the server and its shares. Posting the output of the following commands will tell them that:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by soundesigner on 2019-12-13
Morbius,

***Somebody*** knows! (You maybe?)  That which will be self-evident to a seasoned pro is mere hieroglyphics to a two-steps-past-noob like myself.  The kindness of strangers!
Anyway...

atomicpi@atomicpi-MF-001 ~ $ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Publica]"
Processing section "[usb-1]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    dns proxy = No
    log file = /var/log/samba/log.%m
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    security = USER
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    syslog = 0
    unix password sync = Yes
    username map = /etc/samba/smbusers
    usershare allow guests = Yes
    wins support = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[Publica]
    guest ok = Yes
    path = /home/atomicpi/Public
    read only = No


[usb-1]
    guest ok = Yes
    path = /media/atomicpi/62FD-20C1
    read only = No
atomicpi@atomicpi-MF-001 ~ $ net usershare info --long
atomicpi@atomicpi-MF-001 ~ $

---

### Post by Morbius1 on 2019-12-13
This ain't gonna work:
> [usb-1]
    guest ok = Yes
    path = /media/atomicpi/62FD-20C1
    read only = No
Change it to this:
> [usb-1]
    guest ok = Yes
    path = /media/atomicpi/62FD-20C1
    read only = No
[COLOR=#0000cd]**force user = atomicpi**[/COLOR]
Then restart smbd:
```
sudo service smbd restart
```
Reason: THe system places an access control on /media/$USER ( /media/atomicpi in this case ) such that it only allows that user access to what's under it. A guest user is not atomicpi so it will never get to the 62FD-20C1 folder. [highlight]force user = atomicpi[/highlight] will make the guest user appear to be atomicpi - at least for this share.

---

### Post by soundesigner on 2019-12-13
Morbius1,

Your solution was excellent in its result and your explanation was elegant.  The very thing I've been looking for!  Now, help me understand why the same thing doesn't apply to the Public directory; as is, I can browse and read it from the Win 10 machine, but cannot edit.  If I add the same line for [Publica] as outlined, I'm locked out altogether.  Is there more magic?  Oh, and buy yourself a refreshing beverage!

---

### Post by Morbius1 on 2019-12-13
You mean your [Publica] share now looks like this:
> [Publica]
    guest ok = Yes
    path = /home/atomicpi/Public
    read only = No
force user = atomicpi

And the guest user has no access?

What are the permissions on the folder:
```
ls -dl /home/atomicpi/Public 
```

---

### Post by soundesigner on 2019-12-13
1.  Yes

2.

ls -dl /home/atomicpi/Public
drwxr-xr-x 2 atomicpi atomicpi 4096 Dec 13 12:53

---

### Post by soundesigner on 2019-12-13
What a pain in the butt!  Now, I can no longer open the USB drive from the Windows machine!  I messed around with SMB file support settings in Windows (turned MB1.0/CIFS File Sharing Support ON, rebooted, didn't work, turned it off, rebooted)and now I've gone backwards!  Sheesh!

---

### Post by Morbius1 on 2019-12-14
This is going to be a flat out guess because I cannot come up with a scenario that results in your symptoms.

Did you at some point in your travels add the windows user name to the Linux samba password database? Run this command to find out:
```
sudo pdbedit -L
```
If you did and it shows up in the output remove it:
```
sudo smbpasswd -x winusername
```

---

### Post by soundesigner on 2019-12-14
There was, indeed, such.  I removed the winusername, but still no luck.  I'm thinking of nuking everything and starting over from scratch.  I know a lot of things...including that I don't know much!  Thanks again.

---

### Post by Morbius1 on 2019-12-14
Before you redo everything give this a shot:

Instead of accessing the share by it's ip address access it by it's mDNS ( .local ) host name in explorer:
```
\\atomicpi-MF-001.local
```
Win10 will think it's a different server.

---

### Post by soundesigner on 2019-12-14
```
\\atomicpi-MF-001.local
```

Back to being able to read (not write to) /Publica; still can't open USB (was "usb-1", now renamed, path adjusted in smb.conf).  For some reason, IP address works again as well (or as well as it does). 

[COLOR=#ff0000]**WAIT A MINUTE...JUST TRIED AGAIN... and it *WORKS*!**[/COLOR]

I don't know what wizardry you're using, but whether via MF-001.local or IP address, I can read/write to the USB, even if I can't write to the Public directory.  That's fine, though.

Meanwhile, can I assume correctly that swapping to a different USB drive will require some re-configuring?

I'm going to run this thing through a few cycles of file transfers, booting/rebooting and see if I can break it; if it remains stable, I'm going to "box it up" with my deep appreciation to you and your mad skills.

---

### Post by Morbius1 on 2019-12-14
> I don't know what wizardry you're using, but whether via MF-001.local or  IP address, I can read/write to the USB, [COLOR=#0000cd]**even if I can't write to the  Public directory**[/COLOR].  That's fine, though.
I wish I knew what was going on with the Public folder. At first I thought it was maybe an encrypted home issue but I would think the force user thingy would take care of it. There doesn't seem to be anything wrong with it's permissions and it's not a symlink so ... I just don't know why this is happening.

---

### Post by soundesigner on 2019-12-14
Well, in the scheme of things, it doesn't really matter since the other computers on the LAN will only need access to the audio files stored in the USB drive.  I've swapped out two others, changed info in the smb.conf and everything percolates like it should.  For some reason the Atomic Pi also now takes a long time to shut down or boot, but I'm not losing sleep.  Again, I'm in your debt!

---

