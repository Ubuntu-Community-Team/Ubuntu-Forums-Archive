---
title: "Adding Users to Groups"
date: 2009-10-09
forum: Security
---

### Post by burtzacarach on 2009-10-09
Hello everyone.
I am a newer user of Ubuntu and I just today installed it onto my home desktop. I've been running it on my laptop for a few months now and I'm really enjoying it.
I am the only user of my laptop so when I installed it there I wasn't concerned about multiple users and grouping, so I never needed to adjust any of those settings, but on my desktop it's a different story.
My entire family uses it, and I wanted to try to set up an environment on the computer where my younger ones couldn't adjust any settings that could damage the system. I read somewhere that linux-based operating systems excel in multi-user setups, which sounded perfect.
Through using Windows for years I felt I had a general understanding of user groups, so after adding all the appropriate users, I placed them all into fitting groups.
After perhaps putting a little too much thought into this, I decided to take myself out of the "admin" group. My rational was that sometimes I just don't log off and my kids are so eager to hop on right away that I still wanted a final safeguard against system threat, and the root password would check as the administrator's.
This didn't quite work out like I'd thought it would, and now I can't unlock my Users and Groups menu to change my group back.

TL;DR: What steps do I take to adjust user groups through the terminal?
Thanks for the help!

---

### Post by rippin on 2009-10-09
> **burtzacarach said:**
> 
<snip>

TL;DR: What steps do I take to adjust user groups through the terminal?
Thanks for the help!

Boot to single mode, use root password, change your user's rights via 'adduser' command:

NAME
       adduser, addgroup - add a user or group to the system

---

### Post by burtzacarach on 2009-10-09
Thanks.
I'm not sure if this worked yet, tho...
I don't know what booting into single mode is haha.

---

### Post by rippin on 2009-10-09
> **burtzacarach said:**
> Thanks.
I'm not sure if this worked yet, tho...
I don't know what booting into single mode is haha.

Read about the command before using or you can run into problems. Like, be certain to put ALL the groups your user will need. If you use one group, your user will have one **only**. One 'cheat' I use is to edit /etc/group (note no 's') and add user to each item as needed.

Re: booting to 'single' is A.K.A. 'rescue mode'.

---

### Post by Lars Noodén on 2009-10-09
It's good practice to not run with an admin account, you can use fast user switching to quickly log in-out of your admin account when you do need it.  If there are some specific tasks that you find yourself needing admin access for, then you can add a line specific to that task in sudoers.

If you have the installation disc, you can boot into rescue mode
use df to see which partitions you have and their mount points.  (e.g. /dev/sda1 as /, /dev/sda5 as /home) and jot them down.

Then boot using the installation cd and go into rescue mode and then choose to execute the shell in the root device.  Then you can add your admin user.

```

# create administrative user
adduser burtadmin;

# add default admin groups
usermod -G adm,dialout,cdrom,plugdev,lpadmin,admin,sambashare burtadmin;

```

---

