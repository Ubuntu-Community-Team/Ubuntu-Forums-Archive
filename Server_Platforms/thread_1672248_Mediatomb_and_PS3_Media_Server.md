---
title: "Mediatomb and PS3 Media Server"
date: 2011-01-20
forum: Server Platforms
---

### Post by p2ranger on 2011-01-20
(Sorry for the multiple posts. I was getting DB errors when I hit submit)

Been trying to setup media streaming from my Ubuntu 10.04 server to my PS3. Photos, music, video.

I had miniDLNA installed earlier. It partially worked with PS3, but I changed the location of some media and I couldn't figure out how to get that to pickup the change. I liked that Media Tomb has a webfront I can use to manage my media.

MediaTomb I can only figure out how to get it to run by entering it in by command line. I don't understand how to get it to run automatically. The other thing, is that the /etc/mediatomb directory is completely empty. I can only get the config  file to show up in my home directory from when I ran it the first time. The PS3 could see it then. The only information I've been able to find about how to get Mediatomb to start automatically is if you are using Ubuntu Desktop, which I'm not. Mediatomb also doesn't show up in the /etc/init.d/ directory either. From what the Ubuntu community documentation states "MediaTomb will by default run as a service at boot". Well, it doesn't on my computer.

So, I thought I'd give PS3 Media Server a whirl, but I can't figure out how to start or configure it after I installed it. The only directions I've seen show using a desktop.

I've spent most of the day reading up and looking for solutions, and couldn't find anything useful. I'd appreciate some help. Especially with Mediatomb starting automatically. If anyone has a better solution for me to use for media streaming, I'm willing to listen.

Thanks for any help

Jason

---

### Post by arrrghhh on 2011-01-20
I prefer PS3MediaServer myself.

Getting it to run at boot is a little tricky, but there's a great thread in their forums where a kind gent made a repo for it.  See that thread [here.](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589)  With that repo, you'll get a init.d script to start it at boot, works great.

You can also configure PS3MediaServer with a GUI - even if your server is headless, you can forward X over SSH using -X in the ssh login statement.  Much easier for initial configuration, but there is of course a config file - PMS.conf.

As for mediatomb, I stopped using it - webui was nice, but I couldn't get it to play nice with my PS3.  Some files would play, others wouldn't.

For the most part, everything I throw at my PS3 thru PS3MediaServer has been flawless.

---

### Post by arrrghhh on 2011-01-20
Ugh, yet another doublepost to apologize for... Sorry!

---

