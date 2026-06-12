---
title: "Clone Ubuntu Server"
date: 2016-03-04
forum: Server Platforms
---

### Post by Mark_Holland on 2016-03-04
Hi All,

I am completely new to Linux/Ubuntu so bear with me (about 3 weeks) i have decided to jump right in with Ububtu server to see if it will do what i need. I have everything installed and configure RDP setup, ftp setup, ubuntu desktop gui installed. I have also installed Virtualbox with windows 7 as the program i need to run will only build on windows 7 then it sends all files to a shared folder on Ubuntu so users can connect.

Hopefully that explains my setup. The issue i have is i need to clone this drive once a week in case anything were to happen to the original drive. I tried with clonezilla and it gave me a black screen with a grub error, i then used the live cd to try and repair but as a newbie I was a little out of my depth and had file permission errors when tring to follow a guide to repair.

Something i forgot mention is that i would like to do the clone in a working environment not from a live cd so not downtime.

What i need is a complete mirror image clone i can just swap whenever i need within a few minutes.

Thanks in advance - MH

---

### Post by houstonbofh on 2016-03-04
> **Mark_Holland said:**
> Something i forgot mention is that i would like to do the clone in a working environment not from a live cd so not downtime.
This is like changing a tire while driving...  Not really a viable option.  But...  You can make a copy and keep it current with rsync.  You have not said what the server is used for.  For things like user data and most ftp, simply making a copy of /home will keep all your data and can just be laid on top of a new install if needed.  If you have a lot of custom configuration, grab /etc as well.

Otherwise, it is an offline operation with a boot drive and something like dd.

---

