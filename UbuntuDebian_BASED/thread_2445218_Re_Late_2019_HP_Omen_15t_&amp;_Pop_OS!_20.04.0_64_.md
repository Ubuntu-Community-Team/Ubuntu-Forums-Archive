---
title: "Re: Late 2019 HP Omen 15t &amp; Pop_OS! 20.04.0 64 bit LTS: ALC285 and Digital Microphone"
date: 2020-06-10
forum: Ubuntu/Debian BASED
---

### Post by Welly Wu on 2020-06-10
This is a shot in the dark and I understand that here at the Ubuntu Forums, but please forgive me for posting this thread here and bear with me.

I have done a few Google searches, but I would like to know how to upgrade my Linux kernel using Pop_OS! 20.04.0 64 bit LTS GNU/Linux. I own a late 2019 Hewlett Packard Omen 15t gaming notebook PC. I understand that it has the Intel Cannon Lake PCH cAVS for audio and it uses the ALC285 to be specific and I might need to download the go.sh script to download and install the SOF firmware and custom built Linux kernel 5.6.x 64 bit, but for first steps I would like to know how to upgrade my Linux kernel version using systemd-boot to choose the newer one by default for testing purposes in the first place. Can anyone help me?

Here is a bit more technical information about the SOF firmware: [https://bugzilla.redhat.com/show_bug.cgi?id=1772498](https://bugzilla.redhat.com/show_bug.cgi?id=1772498)

Here is yet more information about the digital microphone issues: [https://bugzilla.kernel.org/show_bug.cgi?id=201251](https://bugzilla.kernel.org/show_bug.cgi?id=201251)

I am assuming that Linux kernel 5.6 might be a better fit to fix the SOF firmware and digital microphone issues on my PC, but I understand that the bug fixes might be backported to Linux kernel 5.4.x 64 bit in the future, but I do not know if and when that will happen yet

This Ubuntu Forums thread is distantly related: [https://ubuntuforums.org/showthread.php?t=2437362](https://ubuntuforums.org/showthread.php?t=2437362)

---

### Post by wildmanne39 on 2020-06-10
*Thread moved to **Ubuntu/Debian BASED for a more appropriate fit**.*

---

### Post by Welly Wu on 2020-06-10
This is what I did to fix the internal audio: 1. sudo kernelstub -a snd_hda_intel.dmic_detect=0

This is what I did to fix the internal audio in /etc/modprobe.d/alsa-base.conf by adding this line: options snd-hda-intel index=1 model=laptop-dmic and saving. I restarted my PC after using kernelstub and modifying the alsa-base.conf file

So, the internal audio and speakers do output audio and sound and it is  found in GNOME 3.36 Settings under Sound. The microphone is listed in  Settings -> Sound as Rear Microphone, but it does not pick up the  sound of my voice when I speak at my PC. Only when I play audio from  Google YouTube does the rear microphone pick up audio

This Launchpad Bug report and comment #45 seems to fix it: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1840725](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1840725)

This is what I did to fix the internal audio in /etc/modprobe.d/alsa-base.conf by adding this line: options snd-hda-intel index=1 model=laptop-dmic and saving. I restarted my PC after using kernelstub and modifying the alsa-base.conf file

So, the internal audio and speakers do output audio and sound and it is found in GNOME 3.36 Settings under Sound. The microphone is listed in Settings -> Sound as Rear Microphone, but it does not pick up the sound of my voice when I speak at my PC. Only when I play audio from Google YouTube does the rear microphone pick up audio

This Launchpad Bug report and comment #45 seems to fix it: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1840725](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1840725)

wellywu

Comment #66 also helped and I modified my /etc/default/default.pa to add these two lines: load-module module-alsa-sink device=hw:0,0 channels=2 load-module module-alsa-source device=hw:0,6 channels=2

However, it still shows rear microphone and the built-in microphone does not work when I speak to my PC; only the rear microphone picks up audio

I installed alsa-tools-gui and I selected my ALC285 sound card, but how  do I determine which one is for my main internal microphone so I can  modify the /etc/default/default.pa to correct it so it uses the main  internal microphone and not the rear microphone?

This is from the Manjaro forum, but it lists my HP Omen 15t and the microphone issue: [https://forum.manjaro.org/t/laptop-microphone-not-working-hp-omen-15/121819](https://forum.manjaro.org/t/laptop-microphone-not-working-hp-omen-15/121819)

This is from the Arch forum, but it is similar to my last post: [https://bbs.archlinux.org/viewtopic.php?id=230890](https://bbs.archlinux.org/viewtopic.php?id=230890)

I think that there is a third-party script called go.sh to automate the build and installation of Sound Open Firmware and topology, ALSA version and Linux kernel 5.6 on the web, but I need to find it.

Anyway, this is the official build guide from the SOF website: [https://thesofproject.github.io/latest/getting_started/build-guide/build-from-scratch.html](https://thesofproject.github.io/latest/getting_started/build-guide/build-from-scratch.html)

---

### Post by Welly Wu on 2020-06-11
Based on ongoing and in depth research, I am going to need the Sound Open Firmware including its topology for my ALC285 sound card and digital microphone array, an updated ALSA version and at least Linux kernel version 5.6.3 64 bit or newer to fix the audio problems on my late 2019 CUK HP Omen 15t gaming notebook PC in the future. It may take until Ubuntu 20.04.2 64 bit LTS is released hopefully in February 2021 for that to happen. Pop_OS! uses systemd-boot and it does not use GRUB2 so there is no automated and safe way to download, build and install a highly custom Linux kernel version with these necessary SOF firmware, topology and updated ALSA version until both Canonical, Ltd. and System76 package it for me in a future software update. This is as far as I can safely go today without breaking my Pop instance from failing to boot up properly at the time of this writing. I am going to keep this thread open and watch it until I receive software updates to correct this bug in the future. Sorry for the extensive posting, but this is my train of thought.

---

### Post by Welly Wu on 2020-06-12
Sorry if this was duplicated because I did not check my previous posts yet.

Here is the official Ubuntu Launchpad bug report that affects me: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1874698](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1874698)

I am affected and it seems that I am on their list of people that are affected by this bug and I should be notified if future replies are made. I may contribute to this bug by asking questions in the near future. I might learn something applicable to Pop_OS!

---

### Post by Welly Wu on 2020-06-13
I  installed Pop_OS! 20.04.0 64 bit LTS GNU/Linux bare metal on my late  2019 CUK HP Omen 15t gaming notebook PC this past Monday, June 8th, 2020  at around 2:15 PM EDT. For the past several days, I have done my best  to do in depth research into the root cause of why my sound card and  microphone do not work properly and I learned a lot of technical  information. I also spent a lot of time to download, install, configure  and optimize my software packages and products and I discovered that  some of the third-party software vendors only officially support Ubuntu  up to version 18.04.x 64 bit LTS, but they are in the process of  patching and updating their software products for 20.04.0 64 bit LTS at  this time. In short, my choice of Pop_OS! in of itself may preclude me  from receiving official technical support in order to troubleshoot some  third-party software products that I am currently using and with which I  have relatively minor bugs with some apps. The more serious issue with  Pop_OS! is getting the Sound Open Firmware, device drivers and topology  along with updated versions of the required software packages an newer  Linux kernel version not to mention hardware specific hacks to configure  the sound card and digital microphone are not yet available for Ubuntu  20.04.0 64 bit LTS and my HP Omen 15t PC; future step by step  documentation that provides a working solution will almost certainly  require Ubuntu 20.04.x 64 bit LTS especially with regards to the  standard GRUB2 boot loader.
 At this point, I decided to mark this Ubuntu Launchpad bug as it does  not affect me to stop receiving notifications in the future. I have  decided to use my Easeus To-Do Home software product which I paid for  and licensed on my late 2019 CUK HP Omen 15t gaming notebook PC and to  plug in my Transcend StoreJet H3 2 TB portable hard disk drive to  restore my disk image and return back to a Microsoft Windows 10 64 bit  Pro edition version 1909 as of May 2020 Windows Update environment if  for no other reason that 100% compatibility and to receive official help  and technical support from Computer Upgrade King for the next three  years.
 This was an eye opening learning experience that yielded a valuable  lesson and one of my former friends told me not to **** with my Windows  desktop operating system when I received my product a few weeks ago. His  common sense advice should have been heeded by myself and I am going to  take it and restore Windows on my HP PC this weekend.

---

### Post by cluadio on 2020-08-08
Hi Welly,

I've managed to get both microphone and speaker working on the same laptop as you. All it took was being on the right Linux kernel version (5.7.9), having the sof-firmware package installed, and building PulseAudio from the source code and installing it on my system. 

I wrote a guide to get it working - it's for Manjaro, not Pop_OS!, but it might be useful if you decide to give Linux another go on your laptop. Don't give up! :)

[I wrote a tutorial to get everything, including sound, working smoothly on the Omen 15.]("I wrote a tutorial to get everything, including sound, working smoothly on the Omen 15. It's for Manjaro KDE, but you might find it useful for your sound issues on Ubuntu too.  https://medium.com/@claudio.cambra/troubleshooting-manjaro-linux-on-your-2019-hp-omen-15-gaming-laptop-august-2020-c570ced15ca8") It's for Manjaro KDE, but you might find it useful for your sound issues on Ubuntu too.

---

