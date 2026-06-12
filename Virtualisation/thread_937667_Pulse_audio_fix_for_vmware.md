---
title: "Pulse audio fix for vmware?"
date: 2008-10-04
forum: Virtualisation
---

### Post by binbash on 2008-10-04
Whenever i open vmware beta it always says sound device is busy.How can i fix it?

---

### Post by xunil utnubu on 2008-10-05
This worked for me (sort of):
[VMWare PulseAudio HOWTO]("http://communities.vmware.com/thread/163605")

You can skip #2 and #3.

Also you need to install padevchooser and open "System/Preferences/PulseAudio Preferences":
In the "Network Access" tab, check "Enable Network access..." and "Don't require authentication"

I said "sort of" because sound from the vm's stutters, crackles, and pops. You need to fiddle with the settings for default-fragments and default-fragment-size-msec until it's bearable - it won't be perfect (4/5 worked ok for me)

Oh, and you need a correct PulseAudio setup to begin with, so follow this [HOWTO: PulseAudio Fixes & System-Wide Equalizer Support (Hardy Heron)]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")

---

### Post by shannon.jacobs on 2009-11-07
How to report the problem and how long until it is fixed? Good thing I'm not in any rush, but this is an example of the sort of niggling little problems that keep me from relying on Ubuntu for serious work...

---

### Post by blwegrzyn on 2011-06-07
I installed basic ubuntu 11.04 server install with ssh and kvm and added below packages for basic gui support:
xserver-xorg xserver-xorg-core
openbox
obconf
virt-manager
lxterminal
xinit
virt-goodies
vlan
firefox
mc
pulse*
paman

and then i installed vmware server 2.0.2 and followed the guide for the audio and nothing.  Vmware server starts with error:
msg.noautodetectbackingquestion:cannot connect virtual device sound. No corresponding device is available on the host

any ideas? 

thx

---

