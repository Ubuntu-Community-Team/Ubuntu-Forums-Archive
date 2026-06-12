---
title: "Experience with Karmic Beta Release on 3 laptops and 1 desktop."
date: 2009-10-11
forum: Testimonials &amp; Experiences
---

### Post by hari_home on 2009-10-11
I tried live CD Alpha 6 in IBM T60. All the hardware, wireless and graphics were perfectly recognized. Did not install.

I installed Beta in IBM T60 in virtual box under Windows XP. Tried Firefox
and Openoffice with wired network. Both worked. Performance was not acceptable even with dual CPU and 3GB RAM. Just an experiment. Not practical. Dual boot is way better.

In all the 3 cases below I just did
sudo update-manager-d
and let it do its thing.

I am typing this message from Beta installed in Toshiba laptop A215-S7416.
All drivers worked well including wired, wireless, graphics out of the box.

Power on to password was about 25 seconds. Password to system ready is about 8 seconds. Did not exactly time it with a stop watch. I believe this just a tad faster than Jaunty. Power down to fully off was an awesome 3-5 seconds. Way to go!

I had exactly same experience on a AMD64 desktop (Running in 32-bit x86 mode) using Asus A8N-VM CSM motherboard looks like the perfect workstation/HTPC motherboard with onboard graphics with analog and DVI-D monitor outputs, and nVidia PureVideo High Definition MPEG-2/WMV9 Playback acceleration. The A8N-VM CSM supports all Socket 939 AMD Athlon64/FX/X2 processors on the market, and is built around two recent nVidia chipsets, the NVIDIA GeForce 6150 & nForce 430.

Finally, I installed on Toshiba laptop A135-S4537. Problem was that wireless which was perfectly recognized by Jaunty was not even started.

I did some search in the forums. See
[https://bugs.launchpad.net/ubuntu/+bug/395565](https://bugs.launchpad.net/ubuntu/+bug/395565)

Finally the following commands made it work on kernel 2.6.31-11 (came with beta release)

sudo modprobe -r -f ath5k
sudo modprobe ath5k

So, I did the following to on startup.

Put the above 2 lines in file wireless.startup in directory
/etc/init.d
chmod +x /etc/init.d/wireless.startup
update-rc.d wireless.startup defaults

Bingo! It works on power up. I am sure that the developers are aware of this and it will be fixed be RC release.

Hope this helps some one.
:guitar:

---

