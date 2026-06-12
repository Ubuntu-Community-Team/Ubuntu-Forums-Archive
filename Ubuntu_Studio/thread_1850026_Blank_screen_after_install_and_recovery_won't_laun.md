---
title: "Blank screen after install and recovery won't launch"
date: 2011-09-25
forum: Ubuntu Studio
---

### Post by wilfite on 2011-09-25
Greetings all,

I am a new linux user.  I have been looking for a good excuse to invest the time necessary to learn linux for a while.  I have years of computer experience, but it has primarily been in windows.

Recently I decided to get back into music creation and have decided that was a good excuse, so I am attempting to convert an extra nettop I have into a DAW of sorts.  I downloaded the Ubuntu Studio ISO and burned it to a DVD with Img burn.  Installation seemed to go ok, with all installation options responding appropriately.  Unfortunately, after rebooting and choosing Ubuntu generic in grub, all I get is a blank screen.  I did some google searches that were not all that helpful, but many suggested going into recovery and loading a different set of graphic drivers, so I tried.  Recovery will not load completely, it hangs with a message similar to Eth0: No IPV6 something or other found.  (Sorry, I typed a really detailed message last night at 2AM and I guess I forgot to submit in the preview window.)

I am dual-booting on this machine with windows 7 professional.  The machine is an Acer Aspire Revo R1600 with upgraded ram and a wifi card from an Aspire One netbook.  The machine has an ION chipset and I have two monitors, one on HDMI and one on VGA.  The machine works fine with windows, thought a bit draggy.

Any assistance y'all could provide would be very welcome.  I expected to run into some issues, but being unable to boot at all wasn't quite what I had in mind :-)

Also, please remember I am very new to linux so I would appreciate complete explanations if you can take the time.  I did some google searches, however many of the suggestions I found were along the lines of "Oh, just do "this"...." when "this" might as well be swahili or something.

Thanks!

---

### Post by jejeman on 2011-09-25
First, did you check dvd for errors?
When you boot dvd choose: Test disk...

---

### Post by wilfite on 2011-09-25
Yes, I did.  No errors.

---

### Post by sgx on 2011-09-25
Hi. The iso should have perfect 'md5 checksum', which is usually
included at the iso download link. I get about 95% good checksums
downloading iso files at 3g speeds, but have had exactly your experience on a few occasions. How2:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I would also recommend testing
multiple linux versions, as newer hardware is not always equally
supported by different linux kernels. Lightweight distros, such as
macpup 528, or pclinuxos minime, may be a good bet for a netbook. AVLinux gets good reviews for people who found ubuntu did not like their hardware. I installed ubuntu variant Mint 11, on my wifes
laptop last night, and added the audio apps using synaptic, and the
dpkg -i command. It's one of the most popular alternatives to windows.
Very polished, but I added E17 for the main gui, as I am not familiar
with gnome, compared to other interfaces.

Hardware is the key to linux success, all the googling a night can hold will be fruitless, without supported hardware. So jot down your
computer chipsets, video and audio devices, and include them in posts
so people who have used them before, can share the experience.

Most linux distros can be run for testing as live dvd/cd, or installed
on usb sticks, or external drives, so you can find the compatible ones, and ones you like best, quite easily. Macpup is designed for
portability, and saves a configuration file if desired, at the first shutdown, which reloads in subsequent sessions. This file can be placed on your computers, or a usbstick, resized, and is searched for at boot time by the macpup cd media. It's fast, and gorgeous, by default!

You will love the freedom linux provides. You look back a year from now, like a an escaped convict cruising by the old prison in a shiny new sports car ;)  But like any escape, we must dig and claw and fight our way through. Defeat is not an option.

This has some discussion that may help, but you need a command prompt
to run the suggested commands. You may be able to access boot options,
during a new install attempt, to load the slower vesa graphics, and get the prompt. Watch the install screen for keypresses to halt the install, and look at the boot options, which you type in at the prompt   how2:

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

(look in the Common Kernel Options, scroll down a bit)

[http://kirichkov.com/707/getting-audio-through-hdmi-with-ubuntu-11-04-and-nvidia-ion-chipset/](http://kirichkov.com/707/getting-audio-through-hdmi-with-ubuntu-11-04-and-nvidia-ion-chipset/)

:guitar:

Cheers

---

### Post by wilfite on 2011-09-25
Thanks for the links.  I took a look and it appears my checksum is ok.  I've run Ubuntu standard on this machine in the past (for a short period of time) so I don't think it's an incompatibility issue.  My suspicion is that Ubuntu Studio doesn't have the right driver for the ION chipset.  I downloaded the driver from Nvidia's website to a DVD, is there some way to load the driver from command line in grub?

---

### Post by sgx on 2011-09-26
as I recall, download the linux nvidia driver from their website, place it in  /   restart your computer, and go to runlevel 3 by

telinit 3

at the root prompt, you type

sh name-of-nvidia-driver

You might need the kernel source installed, depending on the distro.
This is old info, possibly obsolete, but worked a few years ago.
There was/is an instruction link near the driver download link,
which you can choose by model/chipset etc, ION is listed

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

when it's installed

telinit 5

Definitely prefer the latest instruction from their site ;)

Also, most audio apps will work with the older ununtu, I still
think 8.04 was the best, and may set it up again, if I can find
a cheap P4 system

---

