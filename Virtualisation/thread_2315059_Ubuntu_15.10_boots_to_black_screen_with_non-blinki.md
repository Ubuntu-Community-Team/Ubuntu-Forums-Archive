---
title: "Ubuntu 15.10 boots to black screen with non-blinking cursor in VMware Workstation 12"
date: 2016-02-25
forum: Virtualisation
---

### Post by agrippa3 on 2016-02-25
I recently created an Ubuntu 64-bit 15.10 VMware Workstation 12 Player image to create a software development environment. I am slightly familiar with using Ubuntu for Software development, but outside of knowing how to create some useful scripts to automate development, I know nothing about Ubuntu and Linux in general. 

I am running this VMware image on a laptop that has 64-bit Windows 10 with an Intel i7-6700HQ CPU, and Intel HD Graphics 530 GPU, and an Nvidia GeForce GTX 950M GPU (The laptop is a Toshiba Satellite S55-C). 

I was logged in to my Ubuntu VMware image, but put my laptop into sleep mode. I did not charge it soon enough, and the laptop was forced to shut down after running out of power. When I tried to boot the VMware image again, I ran into the black screen, and I am not able to advance past it. Before the black screen, I am prompted to login (not the Ubuntu GUI login screen), but before I can type anything, I am taken to the black screen. Before the login prompt, there is some diagnostic information shown. The diagnostic information, login prompt, and black screen are given below.

Diagnostics
[IMG]http://i.imgur.com/omYbPtD.png[/IMG]

Login Prompt
[IMG]http://i.imgur.com/XtvXhye.png[/IMG]

Black screen with non-blinking cursor
[IMG]http://i.imgur.com/bJ9rInm.png[/IMG]

I am able to enter the grub boot menu and can get into Ubuntu recovery mode. Running fsck and the check packages utilities did not seem to do anything. I am also able to enter the root command line. The command line is strange, since the ls command does not list files and directories like usual. It is only after using the cd command to change directories, such as into etc from the root directory, that the ls command works properly.

My original idea was to reinstall Ubuntu and use the option to keep my files and programs, however, I am not able to boot from a USB when powering on the VMware image. I tried enabling the firmware = "efi" option in the VM's configuration file, but I was still not able to boot from a USB.

I'm not sure where to go from here. When I as searching for answers, I thought I saw some solutions related to the video driver being used, but I can't seem to find them again. Additionally, I do not think that the Nvidia GTX 950M is being used to render VMware Workstation's display, and it is actually the Intel GPU doing that.

Thank you.

---

### Post by howefield on 2016-02-26
Thread moved to the "*Virtualisation*" forum.

---

### Post by agrippa3 on 2016-02-26
I was messing around creating new images in order to reproduce this behavior. It appears, to me at least, that the problem is tied somehow with installing updates from the update manager. I tried configuring the images the same way I did for my currently broken image, and nothing went wrong until I tried updating the packages. Looking around, Ubuntu booting to a black screen after updating seems to be a common problem, and it doesn't look like there is exactly a common fix for it either.

As per [these]("http://askubuntu.com/questions/690535/after-update-15-04-to-15-10-just-black-screen-on-boot") [questions]("http://askubuntu.com/questions/688709/ubuntu-15-10-upgrade-gives-blank-screen") and [this forum post]("http://ubuntuforums.org/showthread.php?t=1743535"), it seems that the problem revolves around video drivers.

I will try some of the solutions suggested in the forum thread and report back with results.

---

### Post by MAFoElffen on 2016-02-26
You linked to my sticky... and that should not be happening to you, with server edition (no XServer) and inside of VMWare Workstation.

What is the OS of your host? 
What is the graphics of your host?
In your VM environment, what is the virtualized graphics set to? (is it virtualized or passed through to the hosts GPU?)

When you boot your VM, press the left shift key. At the grub menu, press the <E> key > <ArrowDown> to the line that starts with "linux" > <RightArrow> to the end of that line, and append the text "text debug " (without the quotation marks) > Press <Cntrl><L> to boot. It will boot in text mode with no vga graphics...

Please post back with any error it shows you, in that mode.

After you get it going, are you looking to give it a job? Or just there to learn?

One more question... is your 3rd screen shot after "sitting idle" for about 3-5 minutes? For instance Server Edition has a console screen timeout, where it turns off the screen (like a screensaver) if sitting idle for a period of time. Pressing <Esc> what bring back the console...

---

### Post by agrippa3 on 2016-02-26
I am running the desktop version of Ubuntu, not the server version.

I am running VMware workstation on a laptop that has 64-bit Windows 10  with an Intel i7-6700HQ CPU, an Intel HD Graphics 530 GPU, and an  Nvidia GeForce GTX 950M GPU (The laptop is a Toshiba Satellite S55-C).

As far as I know, my VM environment is not setup for GPU pass through, so the graphics should be virtualized.

I made the text debug edit to the grub loader. There were no errors that I could see. Is there a place where the text debug information is dumped in a log that I could copy or a way to capture that text information directly? Also, interestingly, my grub menu told me to press <CNTRL><X> to boot.

I assume when you ask if I am going to give it a job, you want to know if I will put some long-running or persistent process on it, like a server. In that case, the answer is no. I am a student, and I am just setting up this environment so I can handle programs for my classes. I want to use the VM to keep my academic environment separate from my personal environment. I also thought it would be informative to learn the gcc + make toolchain, since I have been using Microsoft Visual Studio to create C/C++ programs so far.

As for the third screenshot, yes, that is after the computer has been left idle for some minutes. I have tried many key combinations at that screen, (e.g. <Esc>, <CTRL><ALT><F7>, etc.) and none of them seem to do anything.

---

### Post by MAFoElffen on 2016-02-26
The last kernel update seemed to break VMWare (14.04.03 and 15.10).

On boot, <Left-Shift> key. At grub boot menu, <ArrowDown> and select "Advanced". > Select an earlier kernel version and see if it boots.

---

### Post by agrippa3 on 2016-02-27
When I try to boot from the advanced option in the grub menu, I only have the option to boot from the Linux 4.2.0-30 kernel (the latest is 4.4, right?). Even when I do this, I still get the black screen. Before I made this thread, I seem to remember having another kernel version to boot from, but somehow it went away when I was trying different solutions. In any case, it seems my main black screen problem is related to the update.

I have since created a new image and configured it to my liking. I will just have to be careful about updating it until the issue is resolved.

Would it be appropriate to label my problem solved for now?

---

### Post by MAFoElffen on 2016-02-28
You got me curious-- so today I installed 15.10 in both vSphere ESXi and Vmware Player.. I applied updates to each ... and had no problems with either. But neither were Workstation Pro.

While I was filling out forms for a trial of NVidia Grid, while I was signed in on my VMWare account, I DL'ed a trial version of VMware Workstation Pro 12. I'll install that on one of my spare servers tomorrow night, then I'll install 15.10 in that and try to recreate it...

---

### Post by kaweka on 2016-03-02
> **MAFoElffen said:**
> You got me curious-- so today I installed 15.10 in both vSphere ESXi and Vmware Player.. I applied updates to each ... and had no problems with either. But neither were Workstation Pro.

I believe there was a short time span in Ubuntu 15.10 lifetime when buggy kernel updates were distributed.
The problem with graphic environment not starting cough me too immediately after security updates.
Then recovery session followed by security updates and the problem does not occur any more,
however the kernel update to version 4.2.0.30 which caused the problems that time 
is not offered any more, status today.

Several discussions can be found in web regarding Ubuntu 15.10 and kernel 4.2.0.30 and not starting graphic environment.

---

### Post by MAFoElffen on 2016-03-03
Then this is "Solved"?

If so, please select the Link to the upper right of the first post, that says "Thread Tools > Then select "Mark as Solved"". That way is helps other to find a solution the their similar problem.

---

