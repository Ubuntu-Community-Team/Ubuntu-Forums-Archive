---
title: "Touchpad Random Jumps"
date: 2019-12-10
forum: Ubuntu/Debian BASED
---

### Post by fatihmh on 2019-12-10
Hi,

I use Linux Mint with Lenovo Thinkpad E490 for 5 months.I have a problem these days with my touchpad.

Problem:Cursor jumps randomly.But this is strange because this promblem don't happen in login screen or desktop.it's happen when I open browser or a file.I updated drivers and system (I switch to libinput and nothing changed).I don't update bios (maybe problem is this,but I scared to hurt my laptop).No damage or drop.

```
xinput output:
&#9121; Virtual core pointer                    	    id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 Elan TrackPoint                  	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	    id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C         	id=
```13	[slave  keyboard (3)]

```
grep -i "Using input driver" /var/log/Xorg.0.log output:
[    35.269] (II) Using input driver 'libinput' for 'Power Button'
[    35.310] (II) Using input driver 'libinput' for 'Video Bus'
[    35.333] (II) Using input driver 'libinput' for 'Sleep Button'
[    35.356] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[    35.376] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    35.448] (II) Using input driver 'libinput' for 'TPPS/2 Elan TrackPoint'
[    35.498] (II) Using input driver 'libinput' for 'ThinkPad Extra Buttons'
[    39.379] (II) Using input driver 'libinput' for 'Integrated Camera: Integrated C'

```

```
uname -r output:
4.15.0-72-generic
```

Main question: is this a driver problem,bios problem or a hardware problem?

Thanks.

---

### Post by slickymaster on 2019-12-10
Thread moved to **Ubuntu/Debian BASED** for a better fit

---

### Post by mörgæs on 2019-12-15
Does this help?
[https://ubuntuforums.org/showthread.php?t=2432565](https://ubuntuforums.org/showthread.php?t=2432565)

---

