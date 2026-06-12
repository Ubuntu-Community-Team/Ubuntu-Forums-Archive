---
title: "gazv5, 8.04, suspend and hibernate not working"
date: 2008-07-08
forum: System76 Support
---

### Post by akfrancis on 2008-07-08
I did a clean install of heron last month, ran the system 76 driver, and have installed all updates.  Neither suspend nor hibernate work; machine does not wake no matter what button is pushed, including power.  I end up shutting down, restarting.

Ideas on getting suspend and hibernate to work?

Edit:  64-bit

---

### Post by thomasaaron on 2008-07-08
I just tried suspend on my GazV5 with a fresh install of Hardy 64-bit, and it worked perfectly.

Please give a little more information about what is happening when you try to resume from suspend.

Also, please post the output of...

```
cat /etc/fstab
```

---

### Post by akfrancis on 2008-07-23
> **thomasaaron said:**
> I just tried suspend on my GazV5 with a fresh install of Hardy 64-bit, and it worked perfectly.

Please give a little more information about what is happening when you try to resume from suspend.

Also, please post the output of...

```
cat /etc/fstab
```


Sorry so long in replying--been too busy to get back to this until now.  (At bottom is the requested output.)  

The machine will not wake from suspend or hibernate.  If I go to the log-off options and click the suspend button, for example, it will suspend but not wake up at all (no screen activity) no matter what button I push (power, keyboard, cursor controls/onboard mouse, close and open lid)--same story if I have the power use preferences set to make the machine suspend from inactivity.  Eventually I give up, hold the power button to shut-down, and then power back up and do an intentional restart to make myself feel better.  

When hibernating (whether from power use preference settings or my clicking the hibernate button in log-off options), I can push the power button once and (unlike from suspend) the machine starts behaving as if it is waking-up; the screen lights up as at startup, gets as far as the ubuntu identification screen with the horizontal orange flashing activity bar, but then the orange activity bar freezes and the identification screen changes to the "ubuntu" being reoriented to the bottom of the screen with the letters stretched vertically and no activity bar present below them.  This distorted screen remains as-is indefinitely; I can push whatever button I like, open and close the lid...no change and eventually I shut-down using the power button, then restart per above.

Glad to hear you have the same machine and it works--looking forward to mine doing the same.

Please advise, thanks, 
Chris

Requested output:      

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=d35ae1fd-acfa-47f9-ac5a-6e38768d48b0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=1a0887b7-3bca-44c1-bf21-9b603bdcd709 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
chris@chris-laptop:~$

---

### Post by thomasaaron on 2008-07-23
OK. Thanks.

One more question, which cpu do you have?

```
cat /proc/cpuinfo
```

I'll try to duplicate the problem on a shop Gazelle.

Also, **attach** the output of this command **immediately following** a failed resume and restart.
It will create a text file on your Desktop.

```
cat /var/log/messages > ~/Desktop/messages.txt
```

That might help us figure out where it is hanging up.

---

### Post by akfrancis on 2008-07-28
Intel Core 2 Duo T5250 1.5GHz

Output to:  "cat /var/log/messages > ~/Desktop/messages.txt" was 5x too big to upload to the forum as an attachment; where should I send it?

Thanks much,

Chris

---

### Post by thomasaaron on 2008-07-28
Please send it to support(at)system76(dot)com and reference this thread's URL. 

One last thing: What is the output of this command:

uname -r

If it ends with a *-20, try booting into your *previous* kernel and see if suspend/hibernate work.

---

