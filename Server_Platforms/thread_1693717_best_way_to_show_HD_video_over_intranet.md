---
title: "best way to show HD video over intranet?"
date: 2011-02-23
forum: Server Platforms
---

### Post by gobbledigook on 2011-02-23
hi all!

i run ubuntu 10.10 on a 3.5ghz quad core, 4gb ram.

I had the idea to make an inranet for me and my housemates.... i have an extensive video collection mostly in .avi and .mkv. i would like to make a page which diplays this video and lets you select from a playlist/browse the directory, howeve i didn't really want to have to recode all the video to flv.

is there a way i can do with VLC? i have looked about and the vlcwebplayer just looks like another flash player... does it support VLC recoding on the fly? or am i missing *something*

any other ideas or options ?

Thanx!! :)

---

### Post by Joe of loath on 2011-02-23
You should be able to put all the data on a shared folder (samba/NFS depending on whether you have windows clients or not), and simply play it from there using VLC.

---

### Post by gobbledigook on 2011-02-23
yes i know that... and already have that set up.

but some users (even after i've mapped the drives to their windows PC's) are still unable to use it or worried they will mess something up... the girls mainly... its just not "familiar" to them. hence house intranet

---

### Post by Joe of loath on 2011-02-23
Then make it read only and tell them it's impossible to mess anything up ;)

---

### Post by gobbledigook on 2011-02-23
because then they won't be able to add their own content to the share... 

> is there a way i can do with VLC? i have looked about and the vlcwebplayer just looks like another flash player... does it support VLC recoding on the fly? or am i missing *something*

---

### Post by arrrghhh on 2011-02-23
> **gobbledigook said:**
> because then they won't be able to add their own content to the share...

Perhaps make a separate folder for uploads only?

There's several solutions I can think of, but if you have a mixed environment, SMB/NFS is going to be the way to go.

UPnP media streamer might fit the bill as well - have you looked at that?  I use PS3MediaServer, and despite the name it'll work with most UPnP DLNA-compliant devices.  Problem is for HD video, a lot of load will be placed on your server if anything has to be transcoded.  Multiple people watching... might not work out so well.  Hence the reason SMB/NFS is recommended if you're sharing to other PCs.

---

### Post by gobbledigook on 2011-02-23
wish i didn't live with such technophiles :lolflag:

---

### Post by arrrghhh on 2011-02-23
> **gobbledigook said:**
> wish i didn't live with such technophiles :lolflag:

You mean technophobes?  Technophiles would make me think of people molesting technology...

Wow, derailing this thread quickly.  Back to your topic, what doesn't work about what I suggested...?

---

### Post by Vegan on 2011-02-23
How much security do you need?

I could help design a system that can be reasonably safe.

---

### Post by joberly on 2011-02-23
[Subsonic]("http://www.subsonic.org") works great for this! You can stream movies and music with varying encoding options. Also allows for uploading content. Another nice benefit is a client for Android/iPhone. Forward the ports and access your collection from anywhere, too.

---

