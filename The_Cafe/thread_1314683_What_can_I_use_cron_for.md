---
title: "What can I use cron for?"
date: 2009-11-04
forum: The Cafe
---

### Post by rob86 on 2009-11-04
Cron/crontab is certainly a nifty little thing, but I haven't been able to think of things to run with it. What do people typically use crontabs for? Just looking for some usage ideas. 

I did find one use actually, I added @reboot wvdial which connects my dial-up on boot. It's handy..

Another use I found for it is to download weather radar images. Not a great use, since it only takes 30 seconds to download the image manually when I want an update, but oh well.

---

### Post by ZankerH on 2009-11-04
-As an alarm clock
-To turn off wifi when I'm not home
-To backup files from my laptops to the homeserver (using rsync)
-To backup the homeserver to external storage (rsync again)
-To periodically make my router send its IP to my DDNS provider (one of those cases where I actually resent having a dynamic IP)

---

### Post by amingv on 2009-11-04
-Configure updates to self-download and install (this is not always recommendable, though)
-Automate monotonous, but neccesary tasks (clearing the thumbnail folder and emptying the trash, making backups, etc)
-Waking you up in the morning (it's trustier than my cellphone, I can tell you that much)
-In short, pretty much anything that can be scheduled.

---

### Post by 3rdalbum on 2009-11-04
I used to use Cron on my server to turn the torrent client onto full speed during my ISP's "off-peak" period, and turn it back down to zero during the on-peak.

Now I don't bother; I had to switch from Transmission to Deluge (long story) and I can't figure out how to do it in Deluge.

I usually use "at"; it's much simpler for single-time tasks. I use it to reboot my machine and then suspend it; it's like a freshly-rebooted suspended computer.

```
sudo at now + 2 minutes
reboot
(control-d)

sudo at now + 5 minutes
pm-suspend
(control-d)

```

---

### Post by earthpigg on 2009-11-04
> **ZankerH said:**
> 
-To periodically make my router send its IP to my DDNS provider (one of those cases where I actually resent having a dynamic IP)

care to provide more details on how this is accomplished?

---

### Post by handy on 2009-11-05
> **3rdalbum said:**
> 
Now I don't bother; I had to switch from Transmission to Deluge (long story) and I can't figure out how to do it in Deluge. 

Transmission has the ability to set time periods for different speeds.

---

### Post by schauerlich on 2009-11-05
> **3rdalbum said:**
> I usually use "at"; it's much simpler for single-time tasks. I use it to reboot my machine and then suspend it; it's like a freshly-rebooted suspended computer.

shutdown supports delayed shutdown. On some systems, it defaults to waiting instead of shutting down immediately. 

```
sudo shutdown -r +2
```

---

### Post by Barriehie on 2009-11-05
I use it to:

1.  backup
2.  clean the firefox sqlite files
3.  clean the thumbnail dir.'s
4.  remove old session files
5.  minimize the size of the .sheep directory
6.  remove log files older than 1 month

Barrie

---

### Post by fatality_uk on 2009-11-05
> **earthpigg said:**
> care to provide more details on how this is accomplished?

+1 :d

---

### Post by 3rdalbum on 2009-11-05
> **handy said:**
> Transmission has the ability to set time periods for different speeds.

It does now, but it didn't in 8.10 which was the version I used on the server.

> shutdown supports delayed shutdown. On some systems, it defaults to waiting instead of shutting down immediately.

So it does, I forgot about that.

---

### Post by handy on 2009-11-06
> **3rdalbum said:**
> It does now, but it didn't in 8.10 which was the version I used on the server. 

Yeh! I thought that might be the case...

I like how they are perpetually improving Transmission.

---

