---
title: "Some Facts About The Ubuntu Betas"
date: 2018-04-10
forum: Ubuntu, Linux and OS Chat
---

### Post by lammert-nijhof on 2018-04-10
At the moment I run most of my work in Virtual Machines running from the zfs file system. My Host OS (using ext4) has been Ubuntu 16.04, I tried Ubuntu 18.04 and did finally choose Xubuntu 18.04, since it saves at least 500MB memory and it boots 30%-40% faster then the plain Ubuntu 18.04. I have some more detailed figures for the Virtual Machines. I have three groups of performance results; excellent, good and bad. Based on the next three parameters (initial boot time, reboot time, memory usage MB) and robustness.

 Excellent is:
[LIST]
[*]Xubuntu 18.04 (30, 7, 280)
[/LIST]
Good are:
[LIST]
[*]Ubuntu Mate 18.04 (30, 8, 397), excellent results, but Mate has a time travel annoyance, see explanation below.
[*]Ubuntu 16.04 (32, 12, 419), excellent results, but it has a slightly worse time travel annoyance. This has been my BANKING VM.
[*]Peppermint 8 (44, 25, 293), good results, but 40% longer boot times. This has been my MAIN VM.
[*]Linux Mint 18.3 (40, 21, 471), good results, but 40% longer boot times. Sometimes it does not like to power-off and has to be forced.
[*]Windows XP  (46, 28, 434), good results for the old chap. This has been my MUSIC VM.
[*]Windows 7 (76, 49, 874), not bad, but complexity has its price in boot time and memory usage.
[/LIST]
The time travel annoyance means that not all frames are displayed in sequence, sometimes the system steps back say ½ second in time. If you are typing, the letter appears, disappears and reappears again all in half to a full second. During typing it is a real annoyance. At the same time you also see the system monitor and conky graphs step back say 1 millimeter.

Bad for me are all distros that do crash using 3D acceleration in Virtualbox, they are measured with 3D acceleration disabled.. 
[LIST]
[*]Ubuntu Budgie 18.04 (43, 11, 690), login loop introduced at 20th of March
[*]Ubuntu 18.04 (56, 11, 910), login freeze introduced at 20th of March and before that time, maximizing a window did freeze the desktop.
[*]Kubuntu 18.04 (38, 8, 978), 3D desktop incomplete and complete disaster; without 3D the only distro with a black conky background.
[/LIST]
The example of Win 7, Budgie, Ubuntu and Kubuntu proves, that many sexy features have a real price through the added complexity. That price is paid in boot times, used memory and/or robustness.

I have and used the next two PCs,
[LIST]
[*]HP dc5850 from 2008, Phenom II X4 3.2GHz, 8GB, zfs file system with one 3.5" 500GB HDD and two 2.5" 320 and 160GB HDDs. The accumulated throughput is 240MB/s and I measured > 200MB/s.
[*]HP Elitebook from 2012, i5-2520M 2C/4T, 2.5/3.2Ghz, 8GB, zfs file system with one 2.5" 1TB SSHD at 110MB/s with built-in 32GB Solid State cache at only 200MB/s, but more importantly there are no disk head positioning delays.
[/LIST]
The figures are from my desktop, but the results of my laptop are comparable, but the initial boot times are in general 40% faster through the Solid State part of the SSHD. Once the VM is loaded, it work almost completely from the zfs ARC cache of 1.5GB, resulting in the same reboot times on both systems. The ARC cache of zfs also ensures mostly instantaneous reactions of the system to mouse and keyboard actions. 

For me 18.04 does not bring very much improvement. I will change my Host OS and MAIN VM to Xubuntu, basically a redetection of Xubuntu. I leave my MUSIC and BANKING VMs as they are to the oldies Win XP and Ubuntu 16.04. Maybe I will change my BANKING VM somewhere in the future from Ubuntu 16.04 to Ubuntu Mate 18.04. The improvement, that made me really happy in 18.04, is the compression of the zfs ARC cache. In my opinion Ubuntu 18.04 is a step backwards compared to Ubuntu 16.04, however Ubuntu Mate 18.04 and Xubuntu 18.04 did see some real improvements.

---

### Post by monkeybrain20122 on 2018-04-10
VM tests are not accurate in terms of performance, especially graphic related. So while there may be some truth in the qualitative sense but all those numbers are bunk. The only real test is on actual metal.

---

### Post by davidmohammed on 2018-04-10
Ubuntu Budgie and Ubuntu 18.04 are working just fine with 3D Acceleration + 128Mb virtual RAM on my virtualbox setup.  Intel Graphics Host.

So your observations are basically your setup that is the problem.

For a true analysis try on real hardware.

---

### Post by lammert-nijhof on 2018-04-10
@monkeybrain; I did not test graphics performance at all, with respect to graphics my only interest has been, did 3D-acceleration work yes or no. If you look, the test only depends on disks and CPU performance and maybe on the file system used. Comparisons on virtual machine are as good as  comparisons on real HW and an advantage is, that it omits many of the HW peculiarities, so that it is easier reproducible by others. In my case the only HW params of interest are CPU and HDD performances, so the whole comparison is done under exactly the same circumstances.

@davidmohammed; Well I use the same 3D acceleration with 128MB and it first worked, but after the update of 20th of March, it stopped working. As you can see I do not use Intel, I use an AMD processor and use the propriety NVidia driver for my 1 GB GeForce 8400GS old video card. Maybe you have a different Host OS too. A desktop, that avoids complexity has a better chance to work on any hardware or OS. At the moment you start to add many features and complexity, you will run into this type of 'configuration' issues. The old saying is still true: KISS. I don't think it is chance, that my problems occur with the more complex systems with longer boot times and higher memory usage. 

Like server centers, that only run VMs nowadays, I only run VMs on my desktop, because I get better performance and flexibility. For servers you do performance tests with VMs and not with real HW and I do the same. My Xubuntu host boots in 46 seconds on the real HW and my Xubuntu VM boots in 31 second on the same HW using zfs caching with striped HDDs. I see the same speed-up in loading programs initially. Looking at Betas with the frequent updates, Xubuntu reboots in 7 seconds and reloading programs also after reboots is instantaneous, try that on real HW, especially if it has 10 year. The only thing that is still worse, is the graphics performance. That generates approx. 20-30% higher CPU loads, even with 3D acceleration, but since I'm not a gamer, it is less important for me. However the huge CPU load penalty without 3D acceleration in e.g. displaying YouTube HD videos is unacceptable.  
You made me curious whether Budgie would work on my i5 laptop, I'll give it a try one of the next few days.

---

