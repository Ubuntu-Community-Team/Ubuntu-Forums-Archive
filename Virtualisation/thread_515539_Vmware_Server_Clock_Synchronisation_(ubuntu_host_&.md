---
title: "Vmware Server Clock Synchronisation (ubuntu host &amp; guest)"
date: 2007-08-02
forum: Virtualisation
---

### Post by feeling367 on 2007-08-02
Hello, i've installed VmwareServer under a ubuntu host :

C2D E4200 + 1Gig memory

then I've installed ubuntu server 7.04 as guest.

I've a big clock drift ( about 10 minutes per hour faster than the host clock ).

I've set tools.syncTime = "TRUE" in the vmx file, 
I've installed vmware tools in the guest and it's running !
  
```
root      3770  0.1  0.2   2040   656 ?        Ss   10:20   0:02 /usr/sbin/vmware-guestd --background /var/run/vmware-guestd.pid
```

```

$ sudo ntpdate ntp.ubuntu.com
 2 Aug 10:35:09 ntpdate[3960]: step time server 82.211.81.145 offset -673.188035 sec

```

and 1 minute later :
```

$ sudo ntpdate ntp.ubuntu.com
 2 Aug 10:35:34 ntpdate[3961]: step time server 82.211.81.145 offset -8.511885 sec

```

... ok i've added the following lines to grub :
append="clock=pit nosmp noapic nolapic"

and the clock always drift :-(

somebody have an idea ?

---

### Post by scxtt on 2007-08-02
so you have a dual core HOST, are your VMs set up as single core or using both? ... i have a similar issue myself and even tho it's kinda working itself out (the longer the host is up, then i reboot the VMs - the better the time is) i used to have a cron job that would set the system time based off the hwclock (which was generally correct) ...

and my VMs were essentially ignoring the "syncTime" setting ...

i have a dual core AMD as the HOST and single core VMs ... if i use both CPUs for the VMs, networking doesn't work - odd!

---

### Post by midspot on 2008-01-18
would you mind sharing the cron script you used to sync the system time to the hwclock?

thanks

---

### Post by dcstar on 2008-01-18
> **feeling367 said:**
> Hello, i've installed VmwareServer under a ubuntu host :

C2D E4200 + 1Gig memory

then I've installed ubuntu server 7.04 as guest.

I've a big clock drift ( about 10 minutes per hour faster than the host clock ).
........
somebody have an idea ?

Is this any help (it seems to work for me)?:

[http://blog.autoedification.com/2006/11/vmware-guest-clock-runs-fast.html](http://blog.autoedification.com/2006/11/vmware-guest-clock-runs-fast.html)

---

### Post by scxtt on 2008-01-18
> **midspot said:**
> would you mind sharing the cron script you used to sync the system time to the hwclock?

thanksfor me, the clock drift ended up being the result of AMD's CnQ / frequency scaling -- so i turned that off and my clocks have been fine ever since ...

---

### Post by sufehmi on 2008-03-11
> **scxtt said:**
> for me, the clock drift ended up being the result of AMD's CnQ / frequency scaling -- so i turned that off and my clocks have been fine ever since ...

Nice hint, thanks. 

A bit more info on this; to find out your CPU's current speed settings, type **cpufreq-info**

If it's not installed, type **aptitude install cpufrequtils**

You can set the CPU's speed setting as well. An example :

**cpufreq-set -c 1 -g performance**

This will set "max performance" for the second CPU core.

Hope it helps.

---

