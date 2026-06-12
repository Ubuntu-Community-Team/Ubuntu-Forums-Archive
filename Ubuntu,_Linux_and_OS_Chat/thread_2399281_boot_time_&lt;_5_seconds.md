---
title: "boot time &lt; 5 seconds"
date: 2018-08-23
forum: Ubuntu, Linux and OS Chat
---

### Post by ranchu-panchu on 2018-08-23
Hello,

We need to boot in 5 seconds with ubuntu.
Is it possible or ever done with ubuntu ?

Thank you,
ranran

---

### Post by TheFu on 2018-08-23
Maybe.
```
$ systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @8.340s
&#9492;&#9472;multi-user.target @8.339s
  &#9492;&#9472;postfix.service @7.779s +559ms
    &#9492;&#9472;network-online.target @7.778s
      &#9492;&#9472;network.target @7.775s
        &#9492;&#9472;networking.service @1.589s +6.186s
          &#9492;&#9472;apparmor.service @1.381s +131ms
            &#9492;&#9472;local-fs.target @1.377s
              &#9492;&#9472;run-cgmanager-fs.mount @1.592s
                &#9492;&#9472;local-fs-pre.target @595ms
                  &#9492;&#9472;lvm2-monitor.service @202ms +384ms
                    &#9492;&#9472;lvm2-lvmetad.service @243ms
                      &#9492;&#9472;lvm2-lvmetad.socket @188ms
                        &#9492;&#9472;-.slice @174ms
```
But it depends on your startup tasks.  Mine is trimmed fairly small on that machine.

Other systems here take 50sec and 20sec.  So it depends.  Both of those slower systems are virtual machine hosts. The 50sec one has many, many TB of storage which eats 38sec.

---

### Post by monkeybrain20122 on 2018-08-23
Possible, my toshiba netbook boots in about 2 sec (to the login screen) and takes total of 5 to the desktop. But I have tweked a bit and disabled some startup services, edited grub to lower wait time to 0 and get rid of all snap packages (Ubuntu 18.04, for 16.04 there were none installed by default). Without doing these it was still fast, about 10 secs for 16.04 and double that for 18.04 because of snap.

---

### Post by QIII on 2018-08-23
From BIOS load complete to Kubuntu desktop, my primary machine takes about 7 seconds.  There's not much you can do about the BIOS load unless you disable some of the POST checks, which I wouldn't recommend.

But that is with an AMD Threadripper 1950x, 32GB of DDR4 and NVMe storage devices.

If you are comparing this to Windows 10 "startup", don't be fooled.  Win10 does not boot back up from full shutdown.  I boots from a hybrid hibernation mode and a lot of the POST tasks skipped.  It's a bit of trickery.

---

### Post by poorguy on 2018-08-23
I never will understand why everyone is so concerned with boot time.

I turn my computer on when I wake up and go make coffee and when I come back to work on it everything is ready to go.  

This is my boot time on my 11 year old junk desktop computer and I'm happy with it under a minute if I'm figuring right. 

***32.029+26.466 = 58.495***


```
:~$ systemd-analyze
Startup finished in 5.551s (kernel) + 26.478s (userspace) = 32.029s
graphical.target reached after 26.466s in userspace
:~$ 

```

Intel model: DG33BU motherboard (07/15/2007)
Intel Pentium Dual E2220 processor 2.40 GHz @ 800 MHz FSB
Intel 82G33/G31 Express Integrated Graphics Controller
DDR2 Memory 6.0 GB @ 677 MHz FSB

---

### Post by TheFu on 2018-08-24
In a home or typical business, boot time shouldn't matter much.

But in a 911 emergency call center or a power generation or satellite command center or for certain hospital computing, 5 seconds is an eternity.

Plus, if you are coming from some other popular OS, perhaps there is an expectation that rebooting during critical times could be necessary due to poor uptime and no control over patch reboots?
```
$ uptime
 06:45:35 up 40 days, 22:41,  1 user,  load average: 6.00, 1.74, 0.60

```
is fairly common around here. That is a busy machine 8hrs a day.

A few decades ago, I worked on a knowledge system that was required to do what it did in under 2 seconds, every time, because providing the information to the controllers in a timely manner was deemed critical to mission success.  Life or death.

We don't know the OPs reasons.

---

### Post by poorguy on 2018-08-24
OK that makes sense and I understand I was just curious why so many non critical users are so into boot times.

Most users I know that are into boot up times are mainly laptop users running Windows 10 and boot up times seems to be an eternity for them.

I would think in hospitals and emergency type call centres computers would be left up and running in the ready mode.

When I was working as a field engineer the state department one of the first things to do upon arrival anywhere was to power up the laptop.


Thanks  :smile:

---

### Post by ranchu-panchu on 2018-08-26
Hi,

I need the boot time for embedded system which runs ubuntu on tegra jetson.
I am not sure if the ubuntu which comes with jetson is already customized somehow for that specific cpu.
Yet, I see that both **MONKEYBRAIN** and **QIII** achieved a very good boot time.
[B]
Can you please share your ubuntu image or solution concepts for the short boot time ?
[/B]
Thank you,
ranran

---

### Post by cariboo on 2018-08-26
Here's my boot time:

```
systemd-analyze
Startup finished in 205us (firmware) + 54us (loader) + 3.460s (kernel) + 7.465s (userspace) = 10.926s
graphical.target reached after 7.450s in userspace
```

I'm running a standard 18.10 install using kernel:

```
Linux skynet 4.17.0-8-generic #9-Ubuntu SMP Thu Aug 16 02:47:18 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by monkeybrain20122 on 2018-08-26
> **ranchu-panchu said:**
> Hi,

I need the boot time for embedded system which runs ubuntu on tegra jetson.
I am not sure if the ubuntu which comes with jetson is already customized somehow for that specific cpu.
Yet, I see that both **MONKEYBRAIN** and **QIII** achieved a very good boot time.
[B]
Can you please share your ubuntu image or solution concepts for the short boot time ?
[/B]
Thank you,
ranran

```
systemd-analyze time
Startup finished in 2.885s (kernel) + 1.919s (userspace) = 4.805s
graphical.target reached after 1.681s in userspace
```

I just  use systemd-analyze blame identify some services that take more time and  disable them (after checking that it is harmless), edit grub to change  wait time to 0 and uninstall all the snap, Other than that didn't do  anything special. This is Ubuntu 18.04 and 16.04 was about same with similar tweaking (without any tweaking would take about 10s for 16.04 and around 20s for 18.04 because of the snaps)

---

