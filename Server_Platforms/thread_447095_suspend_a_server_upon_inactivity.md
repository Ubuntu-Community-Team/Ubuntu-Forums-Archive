---
title: "suspend a server upon inactivity"
date: 2007-05-17
forum: Server Platforms
---

### Post by sulla on 2007-05-17
Hi all!

I have a feisty server, serving as a SAMBA and NFS server.

I want to suspend it after a certain time of inactivity of file - serving. Is this possible?

i.e. the server has to suspend itself if it does nothing for a while but it has to stay on if a samba-client is connected. In KDE and Gnome suspending upon inactivity is achieved by observing keyboard and mouse input, but for a server I guess defining "inactivity" is not possible easily, so I think powersaved and gnome-power-manager will not be of much use for me, or can I set it up somehow? Can I use acpid (e.g. define an "event" e.g. as "last SAMBA or NFS user logged out an hour ago" and the action "suspend"??)

Thanx for any help,
Sulla

---

### Post by craigp84 on 2007-05-18
Hi Sulla,

Current technology does not lend itself well to this usage.

While it would be possible to recognise a period of inactivity on SAMBA, then sleep / shutdown the computer, it would not be easily possible to awaken it again - unless you can just go along and hit the power button every time you wanted to access it which would quickly become irksome.

If you wish to use less power, consider investing in a smaller server, some external harddrive enclosures come with ethernet connectors and consume minimal amounts of power.

Otherwise, quit whining :-)

-c

---

### Post by sulla on 2007-05-19
OK, I will stop whining!

The wakeup would be done via Wake-On-Lan. I would install a command-line script to send the magic packt to the server on all clients. So if the server happens to be down, I'll just have to click an icon on the client and wait for 20 secs. That would be doable.

As it does not seem to be possible easily, on my server perhaps I'll have to write a script then (which I am - unfortunately - not good at) to evaluate /var/log/samba.log and /var/log/nfs.log to see when the last access to the box was. I'll create a cron job for it to run it every 10 mins. And if the last access was a long time ago, I'll just issue a "echo -n "disk" > /sys/power/state" to suspend the server.

Hm, doesn't sound too difficult to me after all, now that I talk to somebody about that...

What would be the right place to ask the devs for such a feature?

And my old PC precisely serves as a NAS storage. I want to recycle it, not buy a new server, which I know is possible, of course. But then, no NAS server I've ever looked at provides the functionality I need or want. It needs to serve as SAMBA (all of them do) and as NAS server (a feature very rare in commercial boxes, but it can be found). I also have a bunch of 5 old 80GB HDs that I want to use, so RAID-5-ing them is a feature I want (almost all of the commercial boxes pass out there). Finally, I would want to use encryption on the shares on the server. Commercial products: none ?!
So no, I'll not buy a minimum-power NAS server... Besides, my box uses 60W, not too bad for a server with 5 HDs... Still sleeping would be acustically and economically better, wouldn't it?

---

### Post by craigp84 on 2007-05-19
> The wakeup would be done via Wake-On-Lan. I would install a command-line script to send the magic packt to the server on all clients. So if the server happens to be down, I'll just have to click an icon on the client and wait for 20 secs. That would be doable.

This is fantasy land. 20 seconds? You're old box boots in 20 seconds? Try 2 mins. Waiting 2 mins to get a file? Why bother doing anything, you may as well go hit the power button every time.

What happens when you need to use the box for a few hours, adding files, deleting files, moving stuff around, and it keeps "sleeping" every 10 mins? Rather you than me!

> What would be the right place to ask the devs for such a feature?

This is not a good idea. Forget about it! You have concocted a problem in your head that does not really exist. Your 60w server must cost around £40 a year to run, if that. Burning your lights costs way more. Why do you use candles? Don't use your cooker either, that uses energy, resolve to eat only cold food.

> It needs to serve as SAMBA (all of them do) and as NAS server 

Samba, or CIFS / SMB more specifically, is a NAS technology, as is NFS etc. 
> 
Finally, I would want to use encryption on the shares on the server.

Pretty CPU intensive.

God i'm turning into a grumpy old bar-steward these days. Take no notice.

-c

---

### Post by sulla on 2007-05-19
> **craigp84 said:**
> This is fantasy land. 20 seconds? You're old box boots in 20 seconds?
Not boot, just resume from suspend to disk (around 10-20 secs) or from suspend to ram (<5 secs). No, booting would indeed be quite painful!

> **craigp84 said:**
> What happens when you need to use the box for a few hours, adding files, deleting files, moving stuff around, and it keeps "sleeping" every 10 mins? Rather you than me!
That's why the script should check to see if there are users connected to it. If there is nobody logged in (via Samba or NFS) for, say, 1 hour, then the script can just suspend the machine.

> **craigp84 said:**
> God i'm turning into a grumpy old bar-steward these days. Take no notice.
That sounds like the waiter in my favourite pub, the sort I like best...

> **craigp84 said:**
> Your 60w server must cost around £40 a year to run, if that.
That's about right. But, you know, I'm also a bit grumpy, so I hate waste.

Indeed, Cryptogaphy is CPU-intensive, but over my 100 Mbit link with its theoretical throughput of 12,5 MB/secs I still can push 9-10 using encryption, so its not a severe bottleneck. Plus, it is fun to set it up!

---

### Post by bbzbryce on 2007-07-13
Hi I'm curious to see if you got this to work as you wished? I run a media center machine that is always running even though it is only used a few times a week thus two minutes to boot up is not a problem; I prefer to shutdown then to suspend.

If you did manage to get it working could you provide a copy of your script which checks for smb and nfs inactivity? What about ssh?

Thanks

---

