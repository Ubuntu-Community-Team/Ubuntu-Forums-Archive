---
title: "Benefits of prioritising better compatibility for Chromebooks"
date: 2020-04-28
forum: Ubuntu, Linux and OS Chat
---

### Post by mrjohnc on 2020-04-28
Hi all

I recently bought a Chromebook with the idea of installing Ubuntu and have had a issues with drivers etc, it got me thinking about what would be the advantages of Ubuntu having better support for Chromebooks.

I think there are some real benefits for users being able to use Ubuntu on their Chromebooks: 

[LIST]
[*] There a huge number of Chromebooks being sold but there are a relatively small number of models of Chromebook meaning any additional compatibility would impact a lot of machines.
[*] Chromebooks are bought in large quantities by school and other organisations, (60% of computers purchased by schools in the United States in 2018), being able to install Ubuntu on them would give them extra functionality and also give them a second life to Chromebooks being sold on after the institution has upgraded or support has finished for that model.
[*] Chromebooks are relatively cheap, it seems likely that many Chromebooks are being purchased by people who cannot afford more expensive machines.
[*] Expands functionality especially for people with limited or intermittent access to internet connections. 
[*] Allows users to increase their privacy on the devices they have [https://appleinsider.com/articles/17/04/19/eff-google-chromebook-is-still-spying-on-grade-school-students](https://appleinsider.com/articles/17/04/19/eff-google-chromebook-is-still-spying-on-grade-school-students)
[*] A large percentage of Chromebooks are being bought for children and it would be an opportunity to expose them to open source.
[/LIST]

I'm sure there would be other benefits, please do list others :) 


Currently there are a few ways to install Ubuntu on a Chromebook:

[LIST]
[*]Have it running on top of the same kernel as ChromeOS and be able to switch between them [https://ubuntu.com/tutorials/install-ubuntu-on-chromebook#1-overview](https://ubuntu.com/tutorials/install-ubuntu-on-chromebook#1-overview)
[*]A dual boot option [https://chrx.org/](https://chrx.org/) you can install different flavours of Ubuntu and also Gallium OS which is a distro based on Ubuntu specifically for Chromebooks
[/LIST]


The main issues for better compatibility appear to be:
[LIST]
[*] Installing alongside ChromeOS on the same kernel uses 16.04 and also has issues with being unable to access hardware acceleration
[*] Dual boot provides access to hardware acceleration but has a lot of compatibility issues, missing drivers etc [https://wiki.galliumos.org/Hardware_Compatibility](https://wiki.galliumos.org/Hardware_Compatibility) and is a bit fiddly (you have to press ctrl+l every time you boot up and if you just press enter it wipes your machine). 
[/LIST]

Thanks

---

### Post by TheFu on 2020-04-28
As Canonical moves more and more towards the snap package model, chromebooks will be less and less useful due to the limited storage and RAM.  When non-trivial snaps require 1GB each and the entire available storage is 16G or less, the added functionality just isn't there for most users.  i have 2 chromebooks, both purchased with the sole intent to wipe chromeOS and load Ubuntu-something.  The ChromeOS kernel was pretty limiting for my need since we use NFS extensively and that isn't available.

When schools buy chromebooks one of the main reasons for that is to have the same platform, managed by google, for all students.  1-off setups will cause too many problems for most school system people to handle.  The ability to "power wash" a device is probably the most important for the schools, students, and google.   it trains the students to login to gmail accounts, put stuff on google servers which is terrible for their privacy, and get used to working only when the internet is available.

Canonical is more interested in supporting 12 core, 32G of RAM, 2+TB SSD, 4K screen, systems with $250 GPUs.  They want to be full of cheese to make the competition jealous.  The "wow" is the goal.  The less capable systems aren't really interesting.  For example, they have dropped support for 32-bit CPUs, so very soon we won't be able to run any legacy software that wasn't built 64-bit.

---

### Post by mrjohnc on 2020-04-29
Thanks very much for your thoughts, I'm sorry you've had issues with installing Ubuntu, I'd suggest checking out Gallium OS, which is based on Ubuntu but is tailored to Chromebooks, there's a hardware compatibility list here [https://wiki.galliumos.org/Hardware_Compatibility](https://wiki.galliumos.org/Hardware_Compatibility) . For what its worth I cannot find a new model Chromebook available in the UK which has less than 32GB RAM but I do understand that older Chromebooks very often have less.

Question; Where is driver support for a machine added? Is it inside the main Linux kernel or in the distribution itself? If Debian were to add support would this mean Ubuntu, Xubuntu etc would also be compatible? Would it be possible to just copy drivers over from Chromium OS into the mainline Linux Kernel? 

Thanks again

---

### Post by TheFu on 2020-04-29
The purpose for chromebooks is to run chromeOS. Forcing any other OS onto those machines is not the purpose designed?  
> I cannot find a new model Chromebook available in the UK which has less than 32GB RAM
That is incorrect.  No chromebook has that much RAM.  Perhaps you mean local storage?

Drivers are often part of the kernel distribution, but odd devices aren't always included to keep the total distro size down.  Sometimes there are legal considerations for the drivers as well.  if the company behind the HW/driver doesn't allow redistribution or  doesn't provide the source, it is requires reverse engineering which takes time by a fanatical person.  
Drivers need to be compiled for the specific kernel to get the expected support.  Often, closely related kernels can load shared objects, provided the api between the kernel and provided object code don't change too much.  Generally, a kernel version 4.4.x would be compatible with any driver compiled for the 4.4.x version.  Often, that same driver can be loaded by 4.x.x kernels.  Going from a 4.4.x driver and kernel to a 5.x kernel is much less likely to work.
Of course, drivers have to be compiled for the specific CPU type.  Copying an AMD64 driver onto an ARM chromebook will not work.

---

