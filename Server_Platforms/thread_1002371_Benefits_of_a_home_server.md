---
title: "Benefits of a home server?"
date: 2008-12-04
forum: Server Platforms
---

### Post by PhoenixMaster00 on 2008-12-04
Ok so I have an old computer knocking around at home which a friend suggesting using as a home file server but when he suggested using Windows there was a long silence (i think tumbleweed went by at one point) then i suggested Ubuntu since Linux seems to do good servers. Anyway what i want to no is mainly what are the benefits of a home file server? Is it easy for a first timer to set up. Is it easily accessible by OSX, Linux and Windows and how safe/secure is it?

Any links to other sites with guides would be good to if it helps speed the help process up.

Thanks

---

### Post by jpkotta on 2008-12-04
I have a file server at home, running Dapper currently.  I got it for free, I just had to buy some disks and a SATA card.  I put a RAID 5 array on LVM and a small drive for the OS.  I use it for movies, music, backups, and anything else that requires lots of disk space.  It is accessible to any computer on the LAN.

You can make your server accessible to most OSes with Samba.  I also use sshfs on Linux because it's really quick to set up for something temporary.  If you're familiar with Linux, it is not too hard to set up, depending on what all you want to do with it.  The best part of using Linux is once it's set up, you just throw it in a corner and forget about it.  If it is not open to the internet, in the sense of running internet-visible servers, it's no less safe/secure than a desktop.

---

### Post by nault31 on 2008-12-05
I've been running one for a few months and I never realized how powerful a simple file server can be.  Perfect for all your videos, tv shows, movies, pictures, or setting up a "storage bin" for those miscellaneous files.  I have 4 computers in my house (2 ubuntu, 2 windows) so having a central conputer for files helps greatly.  I show off pictures on one, watch a movie on the laptop in the backyard, stream music to my desktop connected to my stereo, there's so much to do.  And I've never had a problem so far, it runs very stable and the file transfers are seamless.  Also a 1TB OEM HD is $105 on newegg! :D  add a $5 cable and that's a steal of a hard drive

It took a while to get used to the terminal (I use ubuntu server edition, no gui), and I had to make sure that:
-I set up a static IP address
-That the hard drives automount
-Then set up samba to share those drives

Once you know what to do, it's pretty simple to set up if all you are doing is hosting files.  I typed up a basic "how to" (in case I had to start over) that if you would like I can post.

---

### Post by hyper_ch on 2008-12-05
> **PhoenixMaster00 said:**
> Anyway what i want to no is mainly what are the benefits of a home file server?
If you're not alone and multiple people use computers to exchange data at home (or from somewhere else) you can just keep the server running and everybody gets access to it....
You can even use it as firewall, proxy, run groupware on it, .........

> **PhoenixMaster00 said:**
> Is it easy for a first timer to set up.
Depends what you want to do...

> **PhoenixMaster00 said:**
> Is it easily accessible by OSX, Linux and Windows
Depends on how you set it up... samba should be quite easy and straight forward.

> **PhoenixMaster00 said:**
> and how safe/secure is it?
That again depends on how you set it up.

Here a howto for a samba server: [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

---

### Post by Traumadog on 2008-12-05
Just adding my "2 cents" to this discussion......

I had most of the same questions prior to setting up my home server a couple of years ago.  Now, I shudder when I imagine not having it up and running.  Like many of the folks in the above posts, I use my server to store and serve MP3 files, video files, pictures, and documents to the computers on my private LAN.  In addition to that, I access my home server via ssh over the internet to retrieve and store files when I'm away from home.  This has been invaluable to me at work as I'm constantly needing to access document files from multiple locations.  Further, as a public service, I'm using my server to host a website for one of our smaller local volunteer fire services.

In short, I think if you're interested, and have a little free time, you should give it a try.  I think you'll find that it's a really useful tool to have, and it's a lot of fun to play with.

Best wishes,  

Traumadog :)

---

### Post by lykwydchykyn on 2008-12-05
I look at setting up a server as an educational experience.  Mine at home does all kinds of stuff, from print serving to web filtering, running a wiki for taking notes, some custom web apps.  It's great.  It wasn't easy, but it wasn't impossible.  Just set yourself up for a learning experience, not an end-consumer sort of experience.

---

### Post by PhoenixMaster00 on 2008-12-05
Thanks for all the great advice guys/gals i think i have been convinced to start my server journey ;) may it be a good learning service and a bigger foothold into the wider world of Linux (in server terms anyway)

---

