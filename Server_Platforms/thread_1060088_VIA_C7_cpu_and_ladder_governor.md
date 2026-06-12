---
title: "VIA C7 cpu and ladder governor"
date: 2009-02-04
forum: Server Platforms
---

### Post by ambrosa on 2009-02-04
I've made a little home server based on a VIA LN10000EG motherboard (mini-ITX mobo , fanless) and Ubuntu 8.04 Server edition. No monitor (so no X Windows), no keyboard and no mouse. It's a "black box": only power supply and network connection. No magnetic disk: only a small 8 GB Compact Flash with an IDE/CF adapter as harddisk.
This mobo use VIA C7 cpu with clock 1Ghz. It run very fine with Ubuntu 8.04 Server.

For me it's the first time using Ubuntu Server. Till now I've used only Desktop edition and I know powernowd , governor concept and so on.

In Ubuntu Server things look different: no /etc/init.d/powernowd , /sys/device/system/cpu/ is different than Desktop.
Reading 'dmesg' I see that during kernel startup is loaded a "ladder governor" (?)

1) someone can explain me how it works ? I've searched but I've not found any useful infos

2) How I can see in which power state is the CPU ?

3) Because this small server is used only sometimes and it's FANLESS, I want minimized CPU load as "ondemand governor" do in Ubuntu Desktop (goal: to reduce temperature). Can I do this in Ubuntu Server ??


Thanks in advance for infos

---

