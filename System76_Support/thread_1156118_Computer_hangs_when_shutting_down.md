---
title: "Computer hangs when shutting down"
date: 2009-05-11
forum: System76 Support
---

### Post by elusivespoon on 2009-05-11
I recently upgraded to 9.04, and frequently, though not every time, when I shutdown my Daru2 my computer never powers down. When I look at the virtual console for the shut down info, the last message is "Will now halt." So it appears every step of the shutdown is fine, save for powering off. Any help will be appreciated.

---

### Post by thomasaaron on 2009-05-11
Did you do a fresh install of 9.04 or did you upgrade directly from 8.10?

---

### Post by elusivespoon on 2009-05-11
I did an upgrade.

---

### Post by thomasaaron on 2009-05-12
Then it probably is a hosed upgrade. We can hack at it if you like. 

To do so, try to shut it down.  When it hangs, restart the machine and then immediately****** go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

If it were me, though, I'd consider a fresh install. From a technical support perspective, this has been the most difficult upgrade I've seen yet. There have been an amazing number of hosed upgrades and glitches. Far more than dapper to edgy; edgy to feisty, feisty to gutsy, gutsy to hardy, or hardy to intrepid.

I hope they do a better job on intrepid to karmic.

---

### Post by elusivespoon on 2009-05-13
Fortunately it hasn't been happening much lately, so I haven't sent any log files. Though considering what you've saying about the upgrade, I'll probably do a fresh install as soon as I have time.

---

### Post by betrunkenaffe on 2009-05-14
I've ran into the same problem, I did a fresh install and format of /, only /home was left alone so that my preferences would remain.

I don't always have it fail to shutdown, only sometimes but every time I shut down it takes longer because I get a black screen with a bunch of flashing prompts. I can force the shutdown by hitting ctrl-alt-del but it actually does a restart so then I need to kill the power before it restarts.

I checked the log files and I don't see anything pertaining to the shutdown in it, which file(s) would I be looking in?

---

### Post by thomasaaron on 2009-05-14
betrunkenaffe, if you are using an nvidia machine, along with the 180 driver, you can run...

sudo apt-get install linux-backports-modules-jaunty

---

### Post by betrunkenaffe on 2009-05-16
Done,we'll see if it still hangs, I still get the black screen with all the prompts, doesn't happen on my desktop.

---

### Post by betrunkenaffe on 2009-05-24
Ok, so I haven't had it hang but the black screen with multiple cursors still shows up at the end of shutdown sequence. Pretty sure this isn't an nvidia driver issue since it has happened with all drivers I've tried (173,180.44 and beta 185). It didn't happen in 8.10 (obviously :P) and I used 173,177 and 180.23 in 8.10.

Any suggestions on how to get rid of this annoying screen? My desktop shutdown is around 10-15 seconds, my laptop is closer to 30-35 seconds. Both are 9.04, both are clean installs. I just don't know what else to do. I tried looking through logs and there didn't seem to be any problems or steps out of the ordinary.

---

### Post by thomasaaron on 2009-05-26
Not sure what you mean... black screen with multiple cursors... but it sounds like a variation of the nVidia discoloration bug.

Didn't see anything in your logs, and I haven't had any other reports of this one.

Do you get it with visual effects disabled?

My shop laptops shut down in 20-30 seconds.

---

### Post by elusivespoon on 2009-05-29
> **elusivespoon said:**
> Fortunately it hasn't been happening much lately, so I haven't sent any log files. Though considering what you've saying about the upgrade, I'll probably do a fresh install as soon as I have time.

I did a fresh install of 9.04, and it hadn't hung on a shutdown for a while. Today it finally did. I've attached the logs.tar file.

Also, though it hasn't been hanging on shutdowns much, it has been hanging on hibernate a lot.

---

### Post by thomasaaron on 2009-05-29
The logs definitely look like it is shutting down fine. Maybe, for some reason, the final hardware kill signal isn't getting sent to the BIOS.

Here is an interesting bug report...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/71004](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/71004)

...not exactly the same, but pertains to your intel chipset.

Try running this...

sudo mv /sbin/usplash_down /sbin/usplash_down.backup

Does that fix it? If not, you can re-enable usplash by running...

sudo mv /sbin/usplash_down.backup /sbin/usplash_down

---

### Post by betrunkenaffe on 2009-06-01
> **thomasaaron said:**
> 
Try running this...

sudo mv /sbin/usplash_down /sbin/usplash_down.backup

Does that fix it?

This actually fixed the problem I was having, I did notice an error on shutdown "Response null in XXXX". I'll write it down and provide it in full later.

---

### Post by elusivespoon on 2009-06-08
Having disabled the splash screen I was able to catch some errors when my computer hung again on shutdown. The first was:

> Killing all remaining processes . . . [FAIL]

The second was something to the effect that the / partition was busy, though I didn't notice it until I was doing a hard power down. If it comes up again, I'll write down the full message.

---

### Post by thomasaaron on 2009-06-08
...and after restarting, please go to the System76 Driver, create logs and post them. That's interesting. I wonder what's not shutting down.

---

### Post by elusivespoon on 2009-06-14
Ok happened again, and I was able to grab the logs (attached).

And the last messages on the screen were:
```
*Killing all remaining processes...    [fail]
. . .
*Unmounting local filesystems...    [OK]
mount: / is busy
Will now halt
```

Thanks for the help.

---

### Post by elusivespoon on 2009-06-14
Just hung again, but while stopping mysqld. I recently created a cron job to run mysqldump, so this might be unrelated. I've attached a New logs.tar from this crash as well.

---

### Post by thomasaaron on 2009-06-15
Looks to me like this bug...
[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/374397](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/374397)
...and the fix has been committed, but hasn't made it downstream yet.

---

