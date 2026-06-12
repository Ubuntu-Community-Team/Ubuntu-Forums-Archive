---
title: "kvm xp virtual machine crappy sound"
date: 2009-11-07
forum: Virtualisation
---

### Post by blwegrzyn on 2009-11-07
I have a problem with the sound on the kvm vm in ubuntu 9.10
The xp starts and when the sounds play it is very distorted.
The pulse audio properties says:
alsa-plug-in(qemu-system-x86-64)

Any ideas why?
Is there a bug in the kvm module?

thx

---

### Post by sllih on 2009-11-08
I have the same issue. I changed audio driver to pulse audio:
```
$ export QEMU_AUDIO_DRV=pa
```
and then, **in the same terminal window**, please run your kvm command:
```
$ kvm ...your options here...
```

This workaround work for me.

---

### Post by blwegrzyn on 2009-11-09
hmm tried that and from both command line and through virtual manager i still same problem. I noticed that the pulse audio managers says: alsa-plug-in(qemu-system-x86-64)

So i am not sure if I am using pulse audio?
What drive did you use for audio?

---

### Post by sllih on 2009-11-09
Try to create text file with this content:
```

#!/bin/sh
export QEMU_AUDIO_DRV=pa
kvm ...your options here...   

```

Make it executable and run. After that my sound preferences says: "qemu", not "ALSA plug-in".

This work for me on Ubuntu 9.10. You can also try different audio driver (pa = pulse audio), for more information type in terminal:
```

kvm --audio-help

```

---

### Post by blwegrzyn on 2009-11-09
It show up as qemu, but no sound silence while playing media file.
Any special switches you use?
I just did:
-hda image -soundhw es1370 -m 512
and i tried -soundhw all

also i tried to check the xml file config but i dont see an option to change the settings to pulse audio there.
My system was not installed clean, I always was upgrading so maybe there is some problem with pulse audio?

root@blwegrzyn-laptop:/etc/libvirt/qemu# cat xp.xml 
<domain type='kvm'>
  <name>xp</name>
  <uuid>96dbea2f-c95a-c992-3afb-134fe5b870b3</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='i686' machine='pc-0.11'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <pae/>
  </features>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/home/blwegrzyn/VMS/xp.img'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='cdrom'>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='network'>
      <mac address='54:52:00:70:47:f1'/>
      <source network='default'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' keymap='en-us'/>
    <sound model='es1370'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
</domain>

---

### Post by sllih on 2009-11-10
I'm using "-soundhw all" option, nothing special. If this don't work for you, it's hard to tell what's wrong.

You can try all available drivers listed by $ kvm --audio-help
or even something like this file:
```

#!/bin/sh
export QEMU_AUDIO_DRV=sdl
export SDL_AUDIODRIVER=pulse
kvm ...your options here...

```

Maybe some bug report will help you, for example:
[https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/304649](https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/304649)

You can search launchpad for more bugs:
1. [http://www.google.pl/search?q=site%3Alaunchpad.net+kvm+OR+qemu+sound+OR+audio](http://www.google.pl/search?q=site%3Alaunchpad.net+kvm+OR+qemu+sound+OR+audio)
2. [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by blwegrzyn on 2009-11-11
After reinstalling ubuntu sound works with pulse!!!
thx

---

### Post by Tomy on 2009-12-01
> **sllih said:**
> Try to create text file with this content:
```

#!/bin/sh
export QEMU_AUDIO_DRV=pa
kvm ...your options here...   

```Make it executable and run. After that my sound preferences says: "qemu", not "ALSA plug-in".

This work for me on Ubuntu 9.10. You can also try different audio driver (pa = pulse audio), for more information type in terminal:
```

kvm --audio-help

```

Thanks, this worked for me. Now I can play music from the guest winXP and Ubuntu 9.10 at the same time.

---

