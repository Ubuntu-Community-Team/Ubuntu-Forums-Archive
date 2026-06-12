---
title: "System time behind hardware clock."
date: 2011-10-06
forum: Server Platforms
---

### Post by TheDodd on 2011-10-06
I've got a number of Ubuntu servers, and several of them have system times that are about 100 seconds behind their hardware clocks:

ipg@TPHADOOP06:~$ sudo hwclock;date
Thu 06 Oct 2011 11:06:02 PM UTC  -0.547487 seconds
Thu Oct  6 23:04:22 UTC 2011

If I reset the system time using any variety of methods, such as hwclock --hctosys ot ntpdate, it will hold the correct time for a minute or two, and it will drop back roughly 100 seconds.

Now, if I do hwclock --systohc, setting the hardware clock to the incorrect time, the two times stay in sync.  

This condition exists regardless of whether ntp is on or off.  I've been doing the troubleshooting above with ntp turned off.  The /var/lib/ntp/ntp.drift and /etc/adjtime files have been deleted.   

This is happening on 6 out of 24 systems.  

Thanks in advance.

---

### Post by cconstantine on 2011-10-07
Is there anything interesting in your syslog files? (/var/log/kern.log or maybe /var/log/messages )

Are you sure the times are the same right after you set them (does your hwclock;date match, then they are unmatched some time later.)

I'm fishing around for some way that the ~100sec difference is actually just your localtime presentation of the system clock . . .

---

### Post by TheDodd on 2011-10-07
There are a number of ways the problem became apparent to me, but this is how I'm testing:

```
ipg@TPHADOOP05:~$ sudo hwclock;date
Fri 07 Oct 2011 04:39:29 PM CEST  -0.625852 seconds
Fri Oct  7 18:39:29 CEST 2011
```And on one of the unafflicted systems:

```
ipg@TPHADOOP16:~$ sudo hwclock;date
Fri 07 Oct 2011 04:40:41 PM UTC  -0.875684 seconds
Fri Oct  7 16:40:41 UTC 2011
```

Before I turned off ntp, there was a lot of these:

```
Oct  6 19:51:23 TPHADOOP06 ntpd[17271]: time reset +99.339460 s
Oct  6 19:54:45 TPHADOOP06 ntpd[17271]: synchronized to 91.189.94.4, stratum 2
Oct  6 20:07:03 TPHADOOP06 ntpd[17271]: time reset +98.787690 s
Oct  6 20:14:31 TPHADOOP06 ntpd[17271]: synchronized to 91.189.94.4, stratum 2
Oct  6 20:22:36 TPHADOOP06 ntpd[17271]: time reset +99.237959 s
Oct  6 20:32:46 TPHADOOP06 ntpd[17271]: synchronized to 91.189.94.4, stratum 2
Oct  6 20:37:39 TPHADOOP06 ntpd[17271]: time reset +98.670331 s
```

Which looked like ntp trying to keep time against whatever was causing the problem

---

### Post by Jonathan L on 2011-10-07
> **TheDodd said:**
> I've got a number of Ubuntu servers, and several of them have system times that are about 100 seconds behind their hardware clocks:

ipg@TPHADOOP06:~$ sudo hwclock;date
Thu 06 Oct 2011 11:06:02 PM UTC  -0.547487 seconds
Thu Oct  6 23:04:22 UTC 2011

If I reset the system time using any variety of methods, such as hwclock --hctosys ot ntpdate, it will hold the correct time for a minute or two, and it will drop back roughly 100 seconds.

Now, if I do hwclock --systohc, setting the hardware clock to the incorrect time, the two times stay in sync.  

This condition exists regardless of whether ntp is on or off.  I've been doing the troubleshooting above with ntp turned off.  The /var/lib/ntp/ntp.drift and /etc/adjtime files have been deleted.   

This is happening on 6 out of 24 systems.  

Thanks in advance.

Hi Dodd

Curious problem!  Can you tell us if your hwclocks are right?  Are they all in sync with each other?

My immediate guess would be that the hwclock is wrong, and that you've got something doing ntp against something correct.  But I'm sure you've ruled that out.  And you're quite certain it's the system time that's changing not the hwclock time?  (I'm looking at the "11-minute mode" section of hwclock(8).

Do you know how exactly close to 100 seconds it is?  It's such a suspicious but strange number.  I'm struggling to find something which would change clocks by non-multiple of 60 in the printout, and the best I can imagine is a typo (yes, but where!) where "1:00" was typed as "100".

I'm speculating, as you can tell.

Regards,
Jonathan.

---

### Post by TheDodd on 2011-10-07
> **Jonathan L said:**
> Hi Dodd

Curious problem!  Can you tell us if your hwclocks are right?  Are they all in sync with each other?

I've tested the hardware clock against a known-good node and it looks like it's the correct time.

> **Jonathan L said:**
> 
My immediate guess would be that the hwclock is wrong, and that you've got something doing ntp against something correct.  But I'm sure you've ruled that out.  And you're quite certain it's the system time that's changing not the hwclock time?  (I'm looking at the "11-minute mode" section of hwclock(8).
Well, I've been doing all this with NTP turned off so I can remove that as a variable.  I'm wondering if there isn't some sort of non-NTP software piece in ubuntu that's contributing to this.  I've run large clusters of CentOS and never had anything like this

> **Jonathan L said:**
> 
Do you know how exactly close to 100 seconds it is?  It's such a suspicious but strange number.  I'm struggling to find something which would change clocks by non-multiple of 60 in the printout, and the best I can imagine is a typo (yes, but where!) where "1:00" was typed as "100".
It's 100 seconds +- 5
I just took a look, and it looks like a couple of the nodes have lost about 30 seconds, so those nodes are around 130 seconds behind now.

> **Jonathan L said:**
> 
I'm speculating, as you can tell.

Regards,
Jonathan.
I'll take it, man.  Thanks :)

---

### Post by cconstantine on 2011-10-07
I was originally thinking something was kicking your system clock 100s, and ntpd was wrestling it back. Maybe you're system clock is just running way way off . . .  then you would get ntpd doing these massive time adjustments like you're seeing.

Perhaps your systems' /etc/adjtime parameters are horribly off? ...were these systems configured via automation/copying from a golden-master?

Maybe each system has a copy of the adjtime file from some master system. The adjtime values are chip-specific because they account for the particular oscillator frequency of the specific cpu chip in the system.

So each of your hardware clocks are right because they're in-built hardware timepieces, but your system clocks are off because your adjtime values aren't correct for each system.

Since your hardware clocks are probably good enough, you can install the "adjtimex" package on each system, which will spend a couple minutes watching the hardware and system clocks and will then tune your /etc/adjtime for you.

---

### Post by Jonathan L on 2011-10-07
Hi Again

Further speculations:

You could try bringing one of these naughty-clock servers up off a Live CD and see if it repeats?  Or single user and start NTPD by hand?

What I'm thinking is see if you can convert a naughty-clock machine into a well-behaved one.  Then you've got a gap to conquer.

> **TheDodd said:**
> I've run large clusters of CentOS and never had anything like this

I've run large clusters of lots of things and never seen it. :)

Hope ideas of some use.

Kind regards,
Jonathan.

---

### Post by Vegan on 2011-10-07
In all the times I have setup Ubuntu, it always seems to be on the right time after setting the time zone.

I always thought it was automatic

---

### Post by Jonathan L on 2011-10-11
> **Jonathan L said:**
> 
You could try bringing one of these naughty-clock servers up off a Live CD and see if it repeats?  Or single user and start NTPD by hand?

Hi

In hindsight was realising that suggestion was a bit silly -- if you boot off a Live CD it will work fine, but it's worth checking.

If your servers are all supposed to be the same, I'd diff -R the whole file system.  Somewhere, something is different: in /etc /boot or /usr.  It's brute force but you'll find things.

Any good?

Regards,
Jonathan

---

