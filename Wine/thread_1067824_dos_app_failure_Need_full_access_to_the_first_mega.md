---
title: "dos app failure: Need full access to the first megabyte for DOS mode"
date: 2009-02-12
forum: Wine
---

### Post by nullhility on 2009-02-12
I tried reporting the bug first: [http://bugs.winehq.org/show_bug.cgi?id=17341](http://bugs.winehq.org/show_bug.cgi?id=17341)

If anyone can make light of this; thanks in advance

> I'm trying to run an old dos app known only to me as "zodiac", now I tried
searching for the error and got the same post, tried getting some common
software with winetricks and upgrading to wine 1.1.4. I'm not at all adept with
wine so I decided to simply try posting a bug report, hope that's enough
information though, thanks for your time.

```

$ wine "C:\\program files\\zodiac\\ZODIAC.EXE"
err:service:validate_service_config Service L"Bscrom" has an unknown service type
err:service:scmdatabase_load_services Invalid configuration of service L"Bscrom" - skipping
err:dosmem:DOSMEM_MapDosLayout Need full access to the first megabyte for DOS mode
```

---

### Post by Dizzle7677 on 2009-02-12
Put this in your /etc/sysctl.conf file
vm.mmap_min_addr = 0 & run 'sudo sysctl -p' to apply the setting
or 
sudo echo 0 > /proc/sys/vm/mmap_min_addr
See if that works.

see explanation -> [Here]("http://marc.info/?l=linux-msdos&m=120802271919730&w=2")

---

### Post by nullhility on 2009-02-15
> Put this in your /etc/sysctl.conf file
vm.mmap_min_addr = 0 
& run 'sudo sysctl -p' to apply the setting
Thanks, looks like it worked.

However I'm getting a new error that repeats a lot of times with different values and registers. "Googling" hasn't yielded much either. Seeing as it's a "fixme" is there a windows dll or registry workaround for this?

```
fixme:ddraw:VGA_ioport_out Unsupported index, VGA graphics controller register - other 0x3ce: 0x01 (value 0x0f)
```

I've attached some of the last lines of output just in case.

---

### Post by Dizzle7677 on 2009-02-15
You might want to do some hunting over at [WineHq's Bugzilla]("http://bugs.winehq.org")

---

### Post by DOS4dinner on 2009-02-15
Have you already tried DOSBox? It runs 99% of DOS programs perfectly.

---

### Post by cogadh on 2009-02-15
> **DOS4dinner said:**
> Have you already tried DOSBox? It runs 99% of DOS programs perfectly.
+1 on this. Wine is for running Windows programs, DOSBox is for DOS programs. Wine can do some DOS, but DOSBox does it much better.

---

### Post by nullhility on 2009-02-15
> You might want to do some hunting over at WineHq's Bugzilla
There are some similar posts on the bug tracker but no real answer, I'm still looking into it though

> Have you already tried DOSBox? It runs 99% of DOS programs perfectly. 
Yeah, I've tried DOSbox and DOSemu, here's the output:
```
Initial Error 4: Icon File (.rsi) / Out of Memory [502]
```

Which to me looks like a fault in the program/files.

---

### Post by 7Lj3)(P38J on 2010-09-13
> **Dizzle7677 said:**
> Put this in your /etc/sysctl.conf file
vm.mmap_min_addr = 0 & run 'sudo sysctl -p' to apply the setting
or 
sudo echo 0 > /proc/sys/vm/mmap_min_addr
See if that works.

see explanation -> [Here]("http://marc.info/?l=linux-msdos&m=120802271919730&w=2")



This has not worked for me. I am trying to run JetPac on Wine 1.3.2. My errors log is as follows:

fixme:exec:SHELL_execute flags ignored: 0x00000100
err:dosmem:DOSMEM_MapDosLayout Need full access to the first megabyte for DOS mode

I have no workable solution for both erros, and the fixme seems the most difficult to solve.

---

### Post by vedavrata on 2010-10-13
> **Dizzle7677 said:**
> Put this in your /etc/sysctl.conf file
vm.mmap_min_addr = 0 
and run 'sudo sysctl -p' to apply the setting
See if that works.
see explanation -> [Here]("http://marc.info/?l=linux-msdos&m=120802271919730&w=2")

It works!!! Thank you very much!


$ uname -a
Linux station1 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux

$ wine --version
wine-1.3.4

---

### Post by gewone on 2010-11-17
> [I]Put this in your /etc/sysctl.conf file
vm.mmap_min_addr = 0
and run 'sudo sysctl -p' to apply the setting[/I]

Cheers mate! Works like a charm.

However, now WINE/CMD gives me this boring b-tch instead!

*```
fixme:int:DOSVM_Int10Handler Get Font Information - Not Supported
```*

This when I'm trying to execute PWORM.EXE :D
I'm aware that DOSBox fully covers [Pizza Worm]("http://en.wikipedia.org/wiki/Pizza_Worm"), I'm just curious on the nature of Wine here.


*Regards~*

---

