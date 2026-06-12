---
title: "intermittent RT status in qjackctl"
date: 2009-06-20
forum: Ubuntu Studio
---

### Post by duffrecords on 2009-06-20
I have a brand-new installation of UbuntuStudio 9.04 (64-bit) and I built JACK2 from svn.  When I start jackd the yellow RT indicator in qjackctl turns on and off intermittently.  I'm a member of the audio group and limits.conf has been set as follows:
```
@audio		-	rtprio		99
@audio		-	nice		-10
@audio		-	memlock		unlimited
```I'm not sure what's wrong, as I had these same JACK parameters working in Hardy Heron and Debian Lenny:```
/usr/bin/jackd -v -R -P89 -dalsa -dhw:1,0 -r48000 -p128 -n2
```Is it just trouble with the new kernel?

---

### Post by thorgal on 2009-06-21
same here, it's just a normal behavior :)

To know if jackd runs some of its threads in RT, just type this in the terminal:

```

ps -Leo class,comm,rtprio | grep jack

```

if you see stuff like this
```

RR  jackd               70
RR  jackd               65

```
you should be good.

old article but you can read this:
[http://www.informit.com/articles/article.aspx?p=101760&seqNum=4](http://www.informit.com/articles/article.aspx?p=101760&seqNum=4)

SCHED_RR and SCHED_FF are both RT scheduling prio. SCHED_RR is like SCHED_FF with time slices.

---

### Post by raboofje on 2009-06-21
> **thorgal said:**
> same here, it's just a normal behavior :)

This got me confused in the past, too :).

---

### Post by duffrecords on 2009-06-21
This is the thread info:```
TS  jackd                -
TS  jackd                -
TS  jackd                -
FF  jackd               99
FF  jackd               89
```Does that look normal?

---

### Post by duffrecords on 2009-06-21
Interesting.  If I start qjackctl with the priority set to (default) rather than 89 as it was in the previous example, I get this:```
TS  jackd                -
TS  jackd                -
TS  jackd                -
FF  jackd               20
FF  jackd               10
```Those look like nice values.

---

### Post by thorgal on 2009-06-21
I set my jackd prio to 70 (look in the qjackctl setup window, a field called "priority")

99 seems wway too much and should be reserved to the softirq-timer's (not even sure about that one)

try:
```

ps -Leo comm,class,rtprio | grep timer

```

and to check that your audio card interrupt is also SCHED_FF, check this"
```

sudo /etc/init.d/rtirq status

```

that is, if you have the rtirq script. I am not sure whether ubuntu studio comes with it. I know 64 Studio ships it. There's a deb available in the 64 studio repos that you can always try to install:

[http://www.mirrorservice.org/sites/64studio.com/apt/pool/main/r/rtirq/rtirq_20070101-1_all.deb](http://www.mirrorservice.org/sites/64studio.com/apt/pool/main/r/rtirq/rtirq_20070101-1_all.deb)

```

sudo dpkg -i rtirq_blabla.deb

```

Your system services will start rtirq at boot time. You can also do it manually with

sudo /etc/init.d/rtirq start

You can tweak it in /etc/default/rtirq (text file with options that are relevant for your system)

---

### Post by duffrecords on 2009-06-21
Looks like the audio card interrupt is SCHED_FF.  It's a Roland SI-24 (the one in my profile avatar) with an RPC-1 card (using the ICE1712 chip).```
  PID CLS RTPRIO  NI PRI %CPU STAT COMMAND	
  120 FF      90   - 130  0.0 S<   IRQ-8	rtc0
 2130 FF      85   - 125  0.0 S<   IRQ-17	ICE1712
  117 FF      84   - 124  0.0 S<   IRQ-20	ohci_hcd:usb3, HDA Intel
  116 FF      80   - 120  0.0 S<   IRQ-21	ehci_hcd:usb2, nvidia
  115 FF      79   - 119  0.0 S<   IRQ-22	ehci_hcd:usb1
  118 FF      79   - 119  0.0 S<   IRQ-23	ohci_hcd:usb4
  119 FF      75   - 115  0.0 S<   IRQ-1	i8042
   76 FF      50   -  90  0.0 S<   IRQ-9	acpi
  104 FF      50   -  90  0.0 S<   IRQ-2299	PCI-MSI-edge      ahci
  111 FF      50   -  90  0.0 S<   IRQ-14	pata_amd
  112 FF      50   -  90  0.0 S<   IRQ-15	pata_amd
  431 FF      50   -  90  0.0 S<   IRQ-6	floppy
  547 FF      50   -  90  0.0 S<   IRQ-19	ohci1394
 2091 FF      50   -  90  0.0 S<   IRQ-18	cx18-0
 2988 FF      50   -  90  0.0 S<   IRQ-2298	PCI-MSI-edge      eth0
 3228 FF      50   -  90  0.0 S<   IRQ-4	
 4441 FF      50   -  90  0.0 S<   IRQ-16
```

---

### Post by duffrecords on 2009-06-21
```
ps -Leo comm,class,rtprio | grep timer
sirq-timer/0    FF      50
sirq-hrtimer/0  FF      50
posix_cpu_timer FF      99
posix_cpu_timer FF      99
sirq-timer/1    FF      50
sirq-hrtimer/1  FF      50
posix_cpu_timer FF      99
sirq-timer/2    FF      50
sirq-hrtimer/2  FF      50
posix_cpu_timer FF      99
sirq-timer/3    FF      50
sirq-hrtimer/3  FF      50
```

---

