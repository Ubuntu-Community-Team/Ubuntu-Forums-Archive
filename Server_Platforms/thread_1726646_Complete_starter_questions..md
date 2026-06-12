---
title: "Complete starter questions."
date: 2011-04-11
forum: Server Platforms
---

### Post by Sulcalibur on 2011-04-11
I have just setup an old PC into a home server using Ubuntu Server Edition 10.

I got it all up and running - Awesome! Now the questions :P Sorry

I am a web designer by trade and work for a company and also do private work at home with me wife. So a server that we can both access is important. So that bit is fine. I also have four sons, and would like to use the server as a home hub for files, media, audio, video, photos, etc This will accessed by wireless Macs and Windows laptops.

Also, not sure if this can be done, but can it be set up to work with external hard drives plugged into it and get the MacBooks to use TimeMachine through it wirelessly?

Another question (sorry) is there anyway the Xbox 360 can pick up content from it also?
With these questions, is the Ubuntu server the right choice? 

Sincere thanks for any time and answers regarding all of these n00bie questions.

Thank you

---

### Post by rubylaser on 2011-04-11
To start, congratulations and welcome the world of Linux servers :)

Sharing files is very simple, you'll just have to decide what protocol(s) you want to share with. Samba (SMB) will be the easiest with the Windows machines and really the Macs too, but you could choose NFS, or AFP as well.

You can do TimeMachine wirelessly, but the easiest way to do that would be to use Netatalk so you could use AFP to share a TimeMachine share out for your Macs.  You'll want to make this be on a volume that you set the size (either a partition or LVM), otherwise if you give it access to the whole drive, it will eventually soak up the whole drive.  Or, just dedicate a drive to Timemachine (a better practice).

In regards to your 360, I don't have one, and other people may have better suggestions, but it seems that ushare works okay.

[http://www.themanfromdelmonte.co.uk/2010/02/09/stream-video-to-xbox-360-from-ubuntu-with-ushare/]("http://www.themanfromdelmonte.co.uk/2010/02/09/stream-video-to-xbox-360-from-ubuntu-with-ushare/")

---

### Post by Sulcalibur on 2011-04-11
> **rubylaser said:**
> To start, congratulations and welcome the world of Linux servers :)

Sharing files is very simple, you'll just have to decide what protocol(s) you want to share with. Samba (SMB) will be the easiest with the Windows machines and really the Macs too, but you could choose NFS, or AFP as well.

You can do TimeMachine wirelessly, but the easiest way to do that would be to use Netatalk so you could use AFP to share a TimeMachine share out for your Macs.  You'll want to make this be on a volume that you set the size (either a partition or LVM), otherwise if you give it access to the whole drive, it will eventually soak up the whole drive.  Or, just dedicate a drive to Timemachine (a better practice).

In regards to your 360, I don't have one, and other people may have better suggestions, but it seems that ushare works okay.

[http://www.themanfromdelmonte.co.uk/2010/02/09/stream-video-to-xbox-360-from-ubuntu-with-ushare/]("http://www.themanfromdelmonte.co.uk/2010/02/09/stream-video-to-xbox-360-from-ubuntu-with-ushare/")

Thank you for the kind welcome.

Samba is the plan after reading about it. I'm pleased that the TimeMachine backup will work also :) Thanks for the guidance although I have no idea what LVM or AFP mean :P

---

### Post by rubylaser on 2011-04-11
AFP is Apple Filing Protocol, and it's the best way to do a Timemachine share.  Here's a good walkthrough to set it up...
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/")

And LVM is Logical Volume Manager.  You can do alot of things with this, but in your case, you'd just want to carve out a volume to house your Timemachine backups (in GB or TB).  Here's a basic intro to LVM...
[http://www.howtoforge.com/linux_lvm]("http://www.howtoforge.com/linux_lvm")

---

### Post by Sulcalibur on 2011-04-11
> **rubylaser said:**
> AFP is Apple Filing Protocol, and it's the best way to do a Timemachine share.  Here's a good walkthrough to set it up...
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/")

And LVM is Logical Volume Manager.  You can do alot of things with this, but in your case, you'd just want to carve out a volume to house your Timemachine backups (in GB or TB).  Here's a basic intro to LVM...
[http://www.howtoforge.com/linux_lvm]("http://www.howtoforge.com/linux_lvm")

Thank you!!!!

---

