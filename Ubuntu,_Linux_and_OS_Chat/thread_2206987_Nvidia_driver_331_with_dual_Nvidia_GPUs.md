---
title: "Nvidia driver 331 with dual Nvidia GPUs"
date: 2014-02-19
forum: Ubuntu, Linux and OS Chat
---

### Post by markackerman8@gmail.com on 2014-02-19
I came up to this blog and see so much success.  

I will try this on my system:

HP Envy Touchsmart m7-j078ca Notebook
&#8226; Model # -            E0K99UA
&#8227; Intel® Core&#8482; i7-4700MQ (2.4 GHz, 6 MB cache, 4 cores)
&#8227; Graphics  
     &#8226; NVIDIA GeForce GT 740M (2 GB DDR3 dedicated)
          &#8226; and 
      Intel's Integrated Graphics Card from the  i7-4700MQ

"Please Help on my 2 1/2 year quest to get proprietary graphics working in Ubuntu Linux Mint or Just Ubuntu or Kubuntu, and all my posts over the past 1-2 weeks though it seems like years - all failed except at least some success with Lucas's procedure.

I can't give up now - not with so many friends who I have converted to linux - if not help me Help them

Linux MUST be able to work with The largest maker of Processors Intel , and the most ubiquitous Graphics Manager NVidia, with the latest (3 year old Technology) - being Optimus.  This is getting Silly."

I will definitely do a re-install on a second root partition and try this out (try 18 and over 30 hours just in the past month - wish me luck)

[email]MarkAckerman8@gmail.com[/email]  :o

sooo -- no luck - all nvidia drivers seemedto install without problems and when mdm loads I hear linux mint loading but just a completely black screen (no curser)

any help would be sure appreciated.

---

### Post by markackerman8@gmail.com on 2014-02-21
OK, for now I have logged into my root partition with Mint 16 freshly installed, and after these basic steps I got a black screen and removed /etc/X11/xorg.cong and it at least got me into low graphics mode yet again. I am happy to say that the Nvidia...331.sh driver installed without error which is relatively new. Here is what I did (from my terminal history) followed by some troubleshooting commands and their responses. Any nw troubleshooting tips would be GREATLY appreciated.

Week four with this computer and week 133 with this and my last Hp HYbrid.

sudo add-apt-repository ppaorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331
sudo add-apt-repository ppaorg-edgers/ppa (the previous one was mis-spelled)
sudo apt-get update
sudo apt-get install nvidia-331
(then installed all the suggeted packages)
sudo apt-get install nvidia-settings nvidia-prime libcuda1-331 nvidia-libopencl1-331 nvidia-opencl-icd-331 glibc-doc nvidia-331-uvm
sudo apt-get --purge remove bumblebee
sudo reboot
Black screen (though it seemd to be logged in with the normal beeps and computer activity)
in TTY1
sudo apt-get --purge remove bumblebee
sudo service mdm start (no help)
removed /etc/X11/xorg.cong
rebooted
now writing this from "fail Safe Mode" or Low Graphics Mode - I forget

So here are some troubleshooting facts from terminal

ack@Aarawn ~ $ lspci -vnn | grep '\''[030[02]\]'
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
01:00.0 3D controller [0302]: NVIDIA Corporation GK208M [GeForce GT 740M] [10de:1292] (rev a1)

ack@Aarawn ~ $ inxi -GSx
System: Host: Aarawn Kernel: 3.11.0-12-generic x86_64 (64 bit, gcc: 4.8.1) Desktop: Gnome Distro: Linux Mint 16 Petra
Graphics: Card: Intel 4th Gen Core Processor Integrated Graphics Controller bus-ID: 00:02.0
X.Org: 1.14.5 drivers: nouveau,intel (unloaded: nvidia,fbdev,vesa) Resolution: 1360x768@59.8hz
GLX Renderer: N/A GLX Version: N/A Direct Rendering: N/A

ack@Aarawn ~ $ dmesg | grep NVIDIA
[ 17.166582] nvidia: module license 'NVIDIA' taints kernel.
[ 17.172655] NVRM: loading NVIDIA UNIX x86_64 Kernel Module 331.38 Wed Jan 8 19:32:30 PST 2014

ack@Aarawn ~ $ sudo service mdm start
[sudo] password for ack:
start: Job is already running: mdm

ack@Aarawn ~ $ sudo insmod nvidia
Error: could not load module nvidia: No such file or directory

ack@Aarawn ~ $ sudo cat /var/log/syslog | grep NVI
ack@Aarawn ~ $ sudo cat /var/log/syslog | grep Nvi
ack@Aarawn ~ $ sudo cat /var/log/syslog | grep nvid
Nothing

Anything else to try?

Why can't I insert "insmod nvidia" ?
Why why Why? can't i get this to work? WOW !!

Thanks in advance Mark

---

### Post by howefield on 2014-02-21
Posts moved to own thread and "Ubuntu, Linux and OS Chat" forum.

---

### Post by markackerman8@gmail.com on 2014-02-21
Thanks I hope this gets some attention

---

