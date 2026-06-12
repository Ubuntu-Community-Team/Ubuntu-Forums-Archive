---
title: "Emulating z/OS Hercules, under ubuntu ISSUE zlib."
date: 2013-04-18
forum: Server Platforms
---

### Post by GoshoDaskalov on 2013-04-18
[COLOR=#000000]Hello everyone,[/COLOR]

[COLOR=#000000]So several friend and I decided to get to know a little bit more in mainframes and since IBM is getting everything payed(we will not pay for an entire mainframe so we can educate) we learned a little bit more about hercules and the hole emulation of it, ok we managed to get the whole architecture emulated but when have to 'install' or 'initialize' (which suits you more) the z/OS OS on the 'mainframe' from an emulated DASD I get this issue:[/COLOR]

[COLOR=#000000]HHCCP002I CPU0000 thread started: tid=7F8389EE5700, pid=6028, priority=0 [/COLOR]
[COLOR=#000000]HHCTT002I Timer thread started: tid=7F8389DE4700, pid=6028, priority=-20 [/COLOR]
[COLOR=#000000]HHCCP003I CPU0000 architecture mode z/Arch [/COLOR]
[COLOR=#000000]HHCCP002I CPU0001 thread started: tid=7F82FBFFC700, pid=6028, priority=0 [/COLOR]
[COLOR=#000000]HHCCP003I CPU0001 architecture mode z/Arch [/COLOR]
[COLOR=#000000]HHCPN001I Control panel thread started: tid=7F838C2E9700, pid=6028 [/COLOR]
[COLOR=#000000]HHCAO001I Hercules Automatic Operator thread started; [/COLOR]
[COLOR=#000000]tid=7F8389AE1700, pri=0, pid=6028 [/COLOR]
[COLOR=#000000]IPL 0A81 [/COLOR]
[COLOR=#ff0000]**HHCCD124E 0A81 file[0] invalid trk hdr trk 0: zlib compression unsupported **[/COLOR]
[COLOR=#000000]HHCCP029E z/Arch mode IPL failed: CSW status=0D00 [/COLOR]
[COLOR=#000000]Sense=10000000 00000010 00000000 00000000 00000000 00000000 00000080[/COLOR]

[COLOR=#000000]this error occurs when I type IPL 0A81 - the IPL stands for initial program load which if you know mainframe you will understand if not -> considered it like loading the OS from a device/drive and the 0A81 is the drive/device. [/COLOR]

[COLOR=#000000]Since we do not have a whole high-tech library with multiple devices, hercules emulate some for the users.[/COLOR]

[COLOR=#000000]Here is the emulation 'type' or extension or .. I dunno how to call it in linux language [/COLOR]:grin:

[COLOR=#000000]# DASD Devices[/COLOR]


[COLOR=#000000]0A81 3390 "/media/BE5A83225A82D715/zOS/cckd/zares1.cckd" sf=shadow/zares1_*[/COLOR]
[COLOR=#000000]0A82 3390 "/media/BE5A83225A82D715/zOS/cckd/zares2.cckd" sf=shadow/zares2_*[/COLOR]

[COLOR=#000000]So I've read and understood that zlib is actually working with this cckd type of files which is kind of archived files or such/so. BUT! I when to Ubuntu Software Centre and i typed in the search bar 'zlib' and downloaded EVERYTHING from there (believe me one by one click is a terrible thing). Anyways, the problem persists, I read about this somewhere in the IBM forum and I gave a shot to: sudo apt-get install zlib* and it started to install around 780 MB packages or so. Even then this thing is not working and continue to spits out this error.[/COLOR]

[COLOR=#000000]Funny thing is that one of our colleagues managed to run the whole hercules z/os ect emulated system on SUSE and centOS, since I've started with the ubuntu I'd like to run the whole thing under ubuntu.[/COLOR]

[COLOR=#000000]Please assist. It is important and I need your guidance here [/COLOR]:smile:

[COLOR=#000000]Thanks in advance.

This theme was posted in beginners session since i've installed ubuntu less than a month ago. But I did not receive an answer for 10 hours [/COLOR]

---

### Post by matt_symes on 2013-04-18
Hi

Does this help ?

[http://hercules390.996247.n3.nabble.com/VM370sixpack-1-1-and-Linux-td37118.html](http://hercules390.996247.n3.nabble.com/VM370sixpack-1-1-and-Linux-td37118.html)

Did you build it yourself ?

It seems to suggest that zlib needs to be compiled in at build time.

I think you'll need to install this package when building it.

```
sudo apt-get install zlib1g-dev
```

Kind regards

---

