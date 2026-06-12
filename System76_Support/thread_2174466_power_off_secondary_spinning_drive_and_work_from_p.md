---
title: "power off secondary spinning drive and work from primary SSD?"
date: 2013-09-14
forum: System76 Support
---

### Post by David_Sloboda on 2013-09-14
I am looking at getting one of the system76 laptops.   
I like the idea of getting one with two hard drives: a primary SSD for the OS and /home, and a second larger spinning drive for data storage.

Is it possible with a dual drive configuration to shut off the spinning drive and work only from the SSD once in a while?
I expect that this would conserve battery life.
What command(s) would halt this secondary drive?

I have searched this forum (and a few others), but I have not yet found any details  on how to do this.

Thank you for your time and response.
David Sloboda

---

### Post by David_Sloboda on 2013-09-14
I've continued searching.  I found a post from January 2012
  [http://ubuntuforums.org/showthread.php?t=1913501](http://ubuntuforums.org/showthread.php?t=1913501)
which implies that hdparm and some guesswork are required.
This other post
   [http://askubuntu.com/questions/194102/reducing-power-consumption-of-second-hdd](http://askubuntu.com/questions/194102/reducing-power-consumption-of-second-hdd)
has some examples.

If anyone else has any suggestions or experience here, I would be glad to hear of it.
Thank you,
David Sloboda

---

### Post by tgalati4 on 2013-09-14
Search on setting up Firefox to use a RAMdisk.  You can generalize that technique to work out of RAM and allow your hard disk to spin down.  An alternative is to create a home directory on your SSD and write a script to back it up to your spinner once a day.

---

### Post by David_Sloboda on 2013-09-24
Thanks.   
That led me to this post titled "Setting up a ramdisk"
[http://ubuntuforums.org/showthread.php?t=182764](http://ubuntuforums.org/showthread.php?t=182764) 
which led me to commands I understand, 
and to the reference to /dev/shm

David Sloboda

---

### Post by tgalati4 on 2013-09-24
Yes, that's it.  There is a script that backs up the firefox profile (cache and stuff) every 10 minutes to a mirror on a hard disk.  You could modify it to mirror your home directory every hour or so to your spinner.

[http://www.verot.net/firefox_tmpfs.htm](http://www.verot.net/firefox_tmpfs.htm)

---

### Post by Newbunto on 2013-09-30
> **David_Sloboda said:**
> I like the idea of getting one with two hard drives: a primary SSD for the OS and /home, and a second larger spinning drive for data storage.

That's basically what I have - except that the spinning drive doesn't have anything on it at all right now i.e. is completely unused.

> Is it possible with a dual drive configuration to shut off the spinning drive and work only from the SSD once in a while?

I expect so but I would go further and have that as your normal configuration unless you know that you are actively using the HDD.

> What command(s) would halt this secondary drive?

**WARNING:** It is **very** important that you type an uppercase **S** for the option in the following.

```
hdparm -S60 /dev/sdb
```

(or whatever is the correct device name for the HDD). Check the correct device name first!

That will put the drive into standby mode if not used for 5 minutes.

You can use

```
hdparm -C /dev/sdb
```

to see when the drive goes into standby.

If you want to make the change permanent then edit /etc/hdparm.conf for something like

```
[FONT=monospace]/dev/sdb {[/FONT]
 [FONT=monospace]        spindown_time = 60[/FONT]
 [FONT=monospace]}[/FONT]
```

In my experience on another computer (Edit: i.e. not running Ubuntu), it is very difficult to keep the drive in standby mode if the drive is being used for much. For example, some annoying software may poll a directory on the drive and thereby keep the drive awake.

---

