---
title: "jackd - adjusting priority"
date: 2009-11-22
forum: Ubuntu Studio
---

### Post by bluesscream on 2009-11-22
Found a lot about optimizing jackd's samplerate and buffers but nothing actual about priority setting in qjackctl (-p in jackd commandline)
My background: When I set priority to high, i.e. 89 as recommended somewhere, I run into freezes and zombifying applications. First I found this when running hungry-for-ressources wine/wineasio/reaper/vsti, but it happened too with ardour, Zynadd...  My limit is ~ 60. Could it be that this is interacting with rtirq?
It's not the crackling, xruns and early app-crashes i get when I'm setting latencies to low or use sluggish ondemand cpu frequency scaling. The point here are system wide freezes for ~ 1/2 minute and persisting zombifyed apps to be killed on system level.

---

### Post by trulan on 2009-11-22
If I understand rt priority correctly, jack's priority setting would coincide with the IRQ priorities set by rtirq.  So if Jack gets a higher priority than something that it depends on, then it could cause issues.

The rtirq script in the Karmic repositories is not fully compatible with Karmic's RT kernel.  The issue has been fixed by the developer, but as of yet the fix hasn't made it into Ubuntu.

If you haven't updated your rtirq script, I would do that first and see if it helps.  Here's how:
> **trulan said:**
> I asked about the problem with rtc vs. rtc0 here:
[http://www.rncbc.org/drupal/node/107](http://www.rncbc.org/drupal/node/107)
and he said I should update my script, this has been fixed some time ago.  So I filed a bug about it here:
[https://bugs.launchpad.net/ubuntu/+source/rtirq/+bug/485262](https://bugs.launchpad.net/ubuntu/+source/rtirq/+bug/485262)

Until the rtirq package is updated, you can get the latest version of rtirq here:
[http://www.rncbc.org/jack/](http://www.rncbc.org/jack/)
There's no 'building' involved - it's just a file or two to copy, since we already have the script installed.

To update your script, download the tar.gz and extract it.  In a terminal, from the newly extracted directory, run:
```
sudo cp rtirq.sh /etc/init.d/rtirq
```The settings file hasn't changed, but you can copy the new one into place as well if you like:
```
sudo cp rtirq.conf /etc/default/rtirq
```

I think, even with this updated script, that there may be a problem with the priorities of the timer, hrtimer, and tasklet soft-irq's being too low for proper real time operation.  I'm still trying to sort it all out.

---

### Post by bluesscream on 2009-11-23
Trulan, you saved my day :D. My problem is solved. After replacing rtirq script I can set jackd priority to 89, no more freezing and zombifying, even frame/periode can be set one step lower. 

```
bluesscream@wormhole:~$ sudo /etc/init.d/rtirq status
[sudo] password for bluesscream: 

  PID CLS RTPRIO  NI PRI %CPU STAT COMMAND	
  670 FF      90   - 130  0.0 S<   irq/8-rtc0	
  962 FF      88   - 128  0.4 S<   irq/18-ohci1394	
  637 FF      84   - 124  0.0 S<   irq/21-ehci_hcd	
  643 FF      84   - 124  0.0 S<   irq/20-ohci_hcd	
  648 FF      83   - 123  0.0 S<   irq/22-ohci_hcd	
  659 FF      82   - 122  0.0 S<   irq/1-i8042	
  658 FF      81   - 121  0.0 S<   irq/12-i8042	
  190 FF      50   -  90  0.0 S<   irq/9-acpi	
  537 FF      50   -  90  0.0 S<   irq/22-sata_nv	
  551 FF      50   -  90  0.0 S<   irq/14-pata_amd	
  552 FF      50   -  90  0.0 S<   irq/15-pata_amd	
 1492 FF      50   -  90  0.0 S<   irq/7-parport0	
 2517 FF      50   -  90  0.1 S<   irq/19-nvidia	
 3685 FF      50   -  90  0.0 S<   irq/19-b43	
 3696 FF      50   -  90  0.0 S<   irq/21-eth0	
    4 FF      49   -  89  0.0 S<   sirq-high/0	
    5 FF      49   -  89  0.0 S<   sirq-timer/0	
    6 FF      49   -  89  0.0 S<   sirq-net-tx/0	
    7 FF      49   -  89  0.0 S<   sirq-net-rx/0	
    8 FF      49   -  89  0.0 S<   sirq-block/0	
    9 FF      49   -  89  0.2 S<   sirq-tasklet/0	
   10 FF      49   -  89  0.0 S<   sirq-sched/0	
   11 FF      49   -  89  0.0 S<   sirq-hrtimer/0	
   12 FF      49   -  89  0.0 S<   sirq-rcu/0	
   18 FF      49   -  89  0.0 S<   sirq-high/1	
   19 FF      49   -  89  0.0 S<   sirq-timer/1	
   20 FF      49   -  89  0.0 S<   sirq-net-tx/1	
   21 FF      49   -  89  0.0 S<   sirq-net-rx/1	
   22 FF      49   -  89  0.0 S<   sirq-block/1	
   23 FF      49   -  89  0.2 S<   sirq-tasklet/1	
   24 FF      49   -  89  0.0 S<   sirq-sched/1	
   25 FF      49   -  89  0.0 S<   sirq-hrtimer/1	
   26 FF      49   -  89  0.0 S<   sirq-rcu/1	

bluesscream@wormhole:~$ 
```


Thank you very much for your in-deepth analysis. Please let us take part with your future findings too.
You are on the way to wiki optimizing ubuntustudio performance.
Best regards

---

### Post by trulan on 2009-11-23
Great!  Thanks for posting your rtirq output too.  The main thing that gets missed by the version of rtirq in the repository is the real time clock (rtc, on irq 8 ), and I believe that was your problem.  The tasklet , timer, and hrtimer threads are all at 49 on your system.  I have seen various references to upping the priorities of these, but I haven't been able to prove that there is a benefit.

But you've proved that the priority of rtc is indeed important.  Once again, here is the bug about this issue:
[https://bugs.launchpad.net/ubuntu/+source/rtirq/+bug/485262](https://bugs.launchpad.net/ubuntu/+source/rtirq/+bug/485262)

---

### Post by bluesscream on 2009-11-23
:) The other thing that's really important especially for ubuntustudio audio beginners is fixing cpu frequency at highest available level. By minimizing ondemand up_threshold as default I had a little improvement, but no real benefit. This might be theme of an extra thread...

---

