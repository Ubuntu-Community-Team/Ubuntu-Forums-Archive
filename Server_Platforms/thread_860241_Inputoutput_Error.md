---
title: "Input/output Error"
date: 2008-07-15
forum: Server Platforms
---

### Post by umate on 2008-07-15
Hi my server has become unusable, i keep getting an input/output error for most commands i run. i cant even use sudo, i get the following error:
[HTML]
-bash: /usr/bin/sudo: Input/output error
[/HTML]

i can't view any sites on my apache server, i get the following error:

[HTML]
Forbidden

You don't have permission to access / on this server.
[/HTML]

---

### Post by cdenley on 2008-07-15
Sounds like your hard drive died. Try booting to a livecd. Once you shutdown the system, it might not boot successfully to the hard drive anymore.

---

### Post by alexander.forster on 2008-07-15
hi im getting this error on my external harddrive, well the input output error part,
any ideas? or can you point my in the right direction? thanks a bunch

---

### Post by umate on 2008-07-16
Thanks for your reply, i'm not sure what it is maybe something to do with the hard drive.

It's a new hp proliant server not even a month old. i can't even shut the system down from the terminal because the shutdown command also shows the input/output error message.

I have to shut it down from the power and restart it. It works fine for a few hours but then the same again.

I can't even access my sites, it gives a permission denied error. When i run the 'ls -l' command in /var/www directory i see ?'s in the output for the sites i cant access.

Cheers

---

### Post by windependence on 2008-07-16
I doubt his hard drive is bad. Are you using 2 cdrom/dvdrom drives? Are you mixing SATA drives with ATA drives? Have you done an upgrade or reinstall by any chance? Any of these could have done this. Was there anything you have changed just prior to this happening.

-Tim

---

