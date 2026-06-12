---
title: "Spin Down Hard Drives"
date: 2006-11-28
forum: Server Platforms
---

### Post by ericbarch on 2006-11-28
I've got an Ubuntu 6.10 Server setup and I'm trying to figure out how to spin down the hard drives automatically after something like 5 minutes of no use. They get pretty loud and can be annoying sitting in my room all day. Any idea how to do this through CLI? Any help would be appreciated. Thanks.

---

### Post by ericbarch on 2006-11-28
I see many GUI tools but I've yet to find a CLI program.

---

### Post by MJN on 2006-11-29
**hdparm** (run as root) is what you're after - it can control all aspects of your hard disk operation.

For the spindown, you want the **-S <value> /dev/hda** option however the <value> bit is somewhat non-intuitive so I'll copy verbatim from the man page:

```

-S           Set the standby (spindown) timeout for the drive.  This value is  used  by
              the  drive  to  determine  how long to wait (with no disk activity) before
              turning off the spindle motor to save power.   Under  such  circumstances,
              the  drive  may take as long as 30 seconds to respond to a subsequent disk
              access, though most drives are much quicker.  The encoding of the  timeout
              value  is  somewhat  peculiar.   A  value  of  zero  means  "timeouts  are
              disabled": the device will not automatically enter standby  mode.   Values
              from  1  to  240  specify multiples of 5 seconds, yielding timeouts from 5
              seconds to 20 minutes.  Values from 241 to 251 specify from 1 to 11  units
              of 30 minutes, yielding timeouts from 30 minutes to 5.5 hours.  A value of
              252 signifies a timeout of 21 minutes. A  value  of  253  sets  a  vendor-
              defined  timeout  period  between  8  and  12  hours, and the value 254 is
              reserved.  255 is interpreted as 21 minutes plus 15  seconds.   Note  that
              some older drives may have very different interpretations of these values.

```To check the current status of the drive (i.e. active/idle, standby etc) run **sudo hdparm -C /dev/hda** (for example).

Note that you might have difficulty spinning down your 'main' disk as it's regularly written to and, given its active state, kjournald will write to it every 5 seconds. 'Spare' discs will be fine.

Mathew

---

### Post by ericbarch on 2006-11-29
Thanks a bunch. I was trying to spin down 2 other hard drives that just store data, not the OS. They only get used now and then throughout the day and they're a bit loud so I wanted to spin them down when I could. This helps a lot. -Eric

---

### Post by Jose Catre-Vandis on 2007-01-04
Very useful thanks. for those that need the syntax:

to check current status (of 1st HD):
```
sudo hdparm -C /dev/hda
```

to set spin down time of 50 seconds (of 1st HD):
```
sudo hdparm -S 10 /dev/hda
```

to set spin down times of subsequent drives use hdc,hdd etc (hdb is probably your CDROM)

this seems to persist through drive accesses, have to check if it persists through reboots!

---

### Post by nrwilk on 2007-01-04
Thank you very much!

I have a laptop with two harddrives, and they get pretty hot after a couple hours of use.  One of the drives gets used very rarely, and I get the feeling that it never gets spun down.

The hdparm -C command is also very useful, because now I can actually see whether they are spun down or not.  Thanks for that, Jose. :) 

hdparm is definitely going into my list of useful programs.  I'm going to study the man page now.

Does anyone know a file which gets executed with root permissions that I can add these commands to so that my drives will sleep anytime they are idle, even after a reboot?

nrwilk

---

### Post by MJN on 2007-01-05
> **Jose Catre-Vandis said:**
> this seems to persist through drive accesses, have to check if it persists through reboots!

It doesn't. Configure /etc/hdparm.conf as required if you want this (or execute an hdparm command with a bootup script).

Mathew

---

### Post by Jose Catre-Vandis on 2007-01-05
> **MJN said:**
> It doesn't. Configure /etc/hdparm.conf as required if you want this (or execute an hdparm command with a bootup script).

Mathew

Based upon the above, I don't know what to put and couldn't see where to put it in the hdparm.conf file ? can you offer advice?

---

### Post by MJN on 2007-01-06
Sure, note the the default /etc/hdparm.conf file is effectively empty - everything in it is commented (and hence ignored) but included to illustrate defaults and examples.

So, to change the spindown time of hdb (second hard disk) to, say, 20 minutes add the following to the end of the file:

```

/dev/hdb {
     spindown_time = 240
 }

```This will effectively *add* the spinddown setting (set normally/manually with hdparm -S but the config file benefits from 'human-readable' setting labels) to the default  (safe) settings. Change any others at your peril - serious damage can occur with hdparm.

Apply/test the settings immediately with **sudo /etc/init.d/hdparm restart**

Any help?

Mathew

---

### Post by Jose Catre-Vandis on 2007-01-06
Thanks Matthew, it was just the different syntax (human readable - lol) that threw me :)

---

### Post by nrwilk on 2007-01-11
Hey guys, I just had to post here again to say how much the discovery of hdparm has helped me out.

Thanks so much!

Since adding a short spin-down time in the conf file, my laptop is _VERY_ much cooler.  At points before it would get so hot, right where the heels of my hands would touch under the keyboard that it was uncomfortable to type.  Now, it only gets slightly warm.

Thank you!

nrwilk

---

