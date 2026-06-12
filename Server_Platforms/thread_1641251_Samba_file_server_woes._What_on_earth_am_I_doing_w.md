---
title: "Samba file server woes. What on earth am I doing wrong?"
date: 2010-12-08
forum: Server Platforms
---

### Post by jupiterstorm on 2010-12-08
Hey guys! First post here.

I would be delighted if someone would offer their assistance troubleshooting a Samba server setup. I have read tons and tons, and been trying different things on and off for a month before coming for help - so please go easy on me if it turns out to be a simple solution :D

I am trying to set up a server box based on this guide: [http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html](http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html)

Basically, it's a Samba server that uses SWAP for management. For whatever reason, I CANNOT access shares from any other computers on my network! I have tried from Windows 7 (spending hours troubleshooting that so it will work with Samba/older sharing), Windows XP AND Windows 2000! ALL of them ask for the password when connecting over and over and over, never actually letting me connect! I know my password is correct, because I set it and added the user to the list of accepted users.

I have also tried disabling all firewalls on each computer and even using a hub in place of my router to see if it was the router screwing things up. 

As I said, the same thing occurs on every single computer that I try to access the shares from. Sometimes the shares are discoverable, other times not...it's crazy! I do not know what is wrong :( I seem to be able to ping the server and SSH into it no problem. It is just file sharing that does not function. I have tried setting up WINS and using a hostname, as well as using the IP directly. Nothing works! It can see the shares, and a password box pops up but it won't accept any credentials.

Does anyone have any idea as to what is wrong?

OH, almost forgot to add - I have installed Ubuntu Server OVER AND OVER trying different releases to see if that was the problem! I have tried 6.06, 6.1, 8.04, and the most recent. What could be doing this that is happening every time?

Thank you for any help!

---

### Post by jupiterstorm on 2010-12-08
Well, I fixed the problem. Thanks anyways :)

Solution? FreeNAS. I discovered that FreeNAS supports Transmission, so it was a no brainer. It worked fine from the get-go, so it definitely was Ubuntu specific. What was it exactly? I don't know...but I've screwed with it for too long these past weeks :P

Hope that helps anyone in my shoes experiencing the same thing.

Cheers!

---

### Post by tubaguy50035 on 2010-12-09
I doubt it is an Ubuntu issue.  If it was a problem we'd all be complaining about it already.  In the future, make sure you post your config files.  Seeing the Samba config would tell everyone on here what's going on.  There are several key things that must be setup in order to allow sharing.  Just remember that next time.

And when you're tired of a computer just being a NAS box and want it to be a server, definitely come back to Ubuntu.  It's fantastic.

---

### Post by jupiterstorm on 2010-12-09
> **tubaguy50035 said:**
> I doubt it is an Ubuntu issue.  If it was a problem we'd all be complaining about it already.  In the future, make sure you post your config files.  Seeing the Samba config would tell everyone on here what's going on.  There are several key things that must be setup in order to allow sharing.  Just remember that next time.

And when you're tired of a computer just being a NAS box and want it to be a server, definitely come back to Ubuntu.  It's fantastic.

Oops, rereading my post it sounds like I was knocking on Ubuntu - I wasn't trying to!

When I said "it's an Ubuntu issue", I meant as opposed to it being my network, or my client computers configurations.

Ubuntu is great :) I've ran servers on it before, but only in an Apple environment. That worked without a hitch the last time I did it - this time, not so much. I'm sure it was my configuration of it that wasn't working - I was just sick and tired of trying to figure it out. While I love learning about computers, it comes second to my real studies, so NAS it was!

I can't think of anything else that I would need at the moment besides File Sharing, Torrents, and Web Administration.

---

### Post by ingeva on 2010-12-11
One problem with SAMBA is that it's too simple, and people tend to complicate it. :)

First, run it straight out of the box. Don't worry about the shares. Change nothing
before you install.
From the other computers you can change the workgroup name to WORKGROUP,
but that's the default like in Samba, so if that's it, it's OK.
If you already have another workgroup name on several computers it's easier to
change it in Samba. In the file /etc/samba/smb.conf , change the line

   workgroup = WORKGROUP

to your workgroup name. Samba can't communicate with different workgroups.

Then there's the shares. They are described at the end of the file.
I have added a share like so, for the /Store directory (folder):

[Store]
   comment = User data
   path = /Store
   guest ok = yes
   read only = no
   browseable = yes
   create mask = 0666
   directory mask = 0777

and in /etc/fstab I added this line:
//Papa/Store  /mnt/SMB-Store cifs user=inge,pass=xxxxxx,iocharset=utf8 0 0

Papa is the other computer, which has the same setup so each one can reach the other.
Of course, the /mnt/SMB-Store directory must exist.... :)

If you have trouble with passwords when you try access from Windows, you can
remove the comment here:
#   encrypt passwords = true    ( file: /etc/samba/smb.conf)

and if that doesn't work, set it to false.
There used to be a problem with encrypted passwords in Windows. I think that's
history now, but if not you can tell Windows to NOT encrypt them by setting

EnablePlainTextPassword=1

Search for this word through the registry using the registry editor.
As it says, the value should be "1" for plain text password.

After changes in smb.conf, restart the samba server.

Hope you can use this. If not, someone else might. :)

The first time I set up Samba, it worked. Then I had to help the experts. :)

---

