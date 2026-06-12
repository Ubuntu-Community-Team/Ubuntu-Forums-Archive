---
title: "Rant: Difficulty finding tutorials on installing drivers for the latest hardware"
date: 2009-03-12
forum: Testimonials &amp; Experiences
---

### Post by Ceza on 2009-03-12
Hello all,
   I don't mean to sound negative, but the fact is I just don't understand the community and in general the Linux mindset. Let me explain what I'm talking about. 

There are many versions of Ubuntu or Kubuntu or really any distro of Linux. Now one of the most common problems for someone that is moving from Windows is just getting drivers installed and updated. While there are TONS of little tidbits all over the internet, none of them are truly helpful to someone starting out. I know I can't be alone here...

I have a newer system and ALWAYS will. It has a 4870 ATI video card. I am installing Kubuntu 8.04. The proprietary driver is not in the repository yet for a 4800. Even if it was, I was a Windows user that always kept up with the newest drivers and if I'm going to run Kubuntu or any other Linux distro I will need to know how to do the same or I simply won't be happy. 

So.....   where are the tutorials that tell me how to do it?

Sounds like an easy question to me. But the fact is.. it isn't. If you take a couple DAYS to search it all you can gather enough information to pull it off... maybe. That is if you can get past the 50 million tutorials of "go to the repository" that are useless. So why is it so hard to do?

Why can I not bring up a google search for "Kubuntu 8.04 ATI 4800 Proprietary Driver Install" and find anything useful?

Why doesn't anyone knowledgeable just say, " You know, I'm going to do a tutorial that will help any nub out there. I will make the requirements be that someone has a known distro like Kubuntu/Ubuntu 8.04 and any ATI/Nvidia video card and I will step by step tell them how to install the proprietary driver and at each step I will explain what they are doing and why in easy terms."  

Lets face it, it really can't be THAT hard... How many of you know what to do? Take a fresh install of a distro like Kubuntu/Ubuntu 8.04.... and install the latest proprietary driver! Document the steps showing the command lines.. fill in some brief explanation of what you did on each step...  end with with some suggestions of other things to to make it perfect like perhaps a suggestion or 2 for people running dual monitors.

Well that is my rant/frustration. I know I'm not alone here. I realize it can be hard to document something with so many variables, but it seems like nobody is really trying. Take out the variables... make your tutorial start from a fresh install of a known distro. Maybe even just start it with a generic level explanation that doesn't depend on a distro.. like here is what needs to happen to install a proprietary driver from ATI/Nvidia's websites, and then suggest where they can go to get specific instructions.

 I can also tell you that once I do figure this out (oh.. and I will.. trust me) I will be VERY happy to help every person and their friends, and the guy they barely know to do it! I feel insulted by the Linux documentation and I'm on a mission now!

BTW, to add salt in the wound... I did find a tutorial on this that was VERY helpful. I LOST IT!!  No level of google searches seem to be able to find it again. One guy ( that I found ) did an excellent job and I LOST IT!!

Regards,
Ceza

P.S. Feel free to actually insult me if you like.. but know I will be grading them and will be even more disappointed if there isn't any creativity shown with the insults!

---

### Post by sgosnell on 2009-03-12
I agree. There is a need for a tutorial.  I'll expect yours to be posted very soon.

---

### Post by shazbut on 2009-03-12
Unfortunately this will always be a problem as long as the card is newer than the distro, unless the card makers decide to package their own deb installers for each distro.

For my 4670 I followed the guide here:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")
(you want method 2)

Be sure you know how to backup/recover your xorg.conf file before you make any changes that could result in loss of the GUI.
Eg:
Backup
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Restore
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by DeMus on 2009-03-12
I fully agree with you. I have a nVidia card and also had problems installing the right driver. I did find a way and even posted it here so now for me things are running well.
After I posted it I got comments from others saying my method didn't work for them, others said it did work.
So it seems it is not that easy to make a tutorial for installing drivers, because what works for one does not work for another. It seems to depend on what you have done before installing the driver that way: which driver did you use until then, how did you install that one (from the repositories or from the manufacturer's website).
I also wrote a couple of times about doing things in Linux and doing the same things in Windows and although many have comments about Windows because of other reasons, people simply have to admit that doing several things the Windows way is easier. Still they won't admit it.
It's not only installing drivers, also installing programs. One program has to be installed using the deb way, another is a .bin file using sh **.bin, some others are still in the .tar.gz version and need yet another way of installing. Why?
Okay, downloading an .exe and installing it is dangerous, I admit that, but it works. Just as with the drivers. In Windows I never had problems installing a newer driver.
Also when Windows updates, the driver still works. Here when I update the kernel I also have to re-install the driver.
I do want to keep using Linux because I love it. I may sound differently, but i do love it. Now I only have legal stuff on my computer and I can do exactly the same as with many illegal programs in the Windows era, plus I did not have to pay tons of euro's for it.

I also wish Linux would mature (now I am in trouble for saying this) and with the benefits of having a secure system, because that may never change, would be as easy to use as a Windows system.

---

### Post by jerome1232 on 2009-03-12
> **DeMus said:**
> 
I also wrote a couple of times about doing things in Linux and doing the same things in Windows and although many have comments about Windows because of other reasons, people simply have to admit that doing several things the Windows way is easier. Still they won't admit it.
It's not only installing drivers, also installing programs. One program has to be installed using the deb way, another is a .bin file using sh **.bin, some others are still in the .tar.gz version and need yet another way of installing. Why?
Okay, downloading an .exe and installing it is dangerous, I admit that, but it works. Just as with the drivers. In Windows I never had problems installing a newer driver.


?? I really don't understand why everyone thinks installing things is hard...

debian packages are very easy you double click... 
.bin is the same thing as a .exe, it's an executable program, whether it's an installer or the program itself. Set it as executable then double click...
.tar.gz/tar.bz2, you honestly never downloaded a program that came as a .zip for windows? Same thing! Extract the contents and run the installer or it could be the program itself in there. If it's source code your trying to install yeah that can be harder.

Graphics drivers do tend to be behind the Windows ones but that's on nvidia/ati not the distro itself.

That's just my food for thought.

---

### Post by DeMus on 2009-03-13
> **jerome1232 said:**
> 

Graphics drivers do tend to be behind the Windows ones but that's on nvidia/ati not the distro itself.

That's just my food for thought.

So, when there is a new kernel and the video driver needs to be re-installed, this is a matter of nVidia/Ati, not of the Linux system? I do not agree with you here. I do believe this is a typical Linux matter.
I do fully agree with you installing the video drivers is a pain in the butt.
nVidia and Ati should put more effort in the installation process of their Linux drivers. But on the other hand Linux should also become more people-friendly and stop being a system for nerds only. Sorry guys.

---

### Post by sdennie on 2009-03-13
Actually the mechanisms for a "manually installed" driver to automatically update itself on new kernel installs have existed for years.  The vendors choose not to take advantage of those mechanisms so, yes, it is very much a driver problem and not a fundamental Linux problem.  There is also no reason why vendors can't setup software repositories and keep them up to date with the newest versions.  In which case, installing up to date drivers becomes incredibly trivial even for someone with only a few hours of Linux experience.

Almost all the problems with "driver installation" can be directly attributed to 3rd party driver writers thinking in Windows mode and not Linux mode.  If they would make their drivers more "Linuxy", many of the complaints/problems would go away.

---

### Post by dmizer on 2009-03-13
> **Ceza said:**
> I have a newer system and ALWAYS will. It has a 4870 ATI video card. I am installing Kubuntu 8.04. The proprietary driver is not in the repository yet for a 4800. Even if it was, I was a Windows user that always kept up with the newest drivers and if I'm going to run Kubuntu or any other Linux distro I will need to know how to do the same or I simply won't be happy.

If your biggest need is to have the latest and greatest, Ubuntu probably isn't your best choice. Something like Arch or Gentoo would be better suited. Ubuntu isn't designed for users who like to live on the bitter edge, it's designed with a wider userbase in mind. Distributions like Arch and Gentoo are designed to allow you to live on the bitter edge.

Moved this to Testimonials & Experiences as it seemed to be more of a rant than a specific request for help.

---

### Post by Vince4Amy on 2009-03-13
> I have a newer system and ALWAYS will. It has a 4870 ATI video card. I am installing Kubuntu 8.04. The proprietary driver is not in the repository yet for a 4800. Even if it was, I was a Windows user that always kept up with the newest drivers and if I'm going to run Kubuntu or any other Linux distro I will need to know how to do the same or I simply won't be happy.

Just download the driver from the ATi site like you would do on Windows. I'm not writing out the instructions again, but installing it is really simple, see my post on getting it working on OpenSuSE:

[http://grubbn.org/otheros/showthread.php?tid=53](http://grubbn.org/otheros/showthread.php?tid=53)

Just follow that guide apart from:

```
sax2 -r -m 0=fglrx
```

---

### Post by issih on 2009-03-13
I might be wrong, but I thought that making all this stuff as trivial as possible was the reason for the existence of envyng

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

EnvyNG is in the repositories, just install it and tell it to go download and install the latest ati or nvidia driver, then sit and wait for a bit. It has handled every video card I've ever tried it with (although admittedly none of those are particularly cutting edge hardware).

Hope that helps

---

### Post by Vince4Amy on 2009-03-13
EnvyNG provides a driver which is too old for the card that the OP is using.

---

### Post by 3rdalbum on 2009-03-13
Back when I had an ATI card, there was a tutorial that I followed on how to install the drivers from Ati.com. This was before the Restricted Drivers Manager, and the procedure was a bit involved.

As for Nvidia drivers, I guess it's pretty easy once you know how to work the system. Make sure you have kernel headers, kill the X server, switch to root, run the installer, start X again. It's basically this:

```
sudo apt-get install linux-headers-generic
sudo killall gdm
```

(make sure you're not logged into a desktop when you do the killall)

Press Control-Alt-F1 to go to a clean terminal, and log into it.

```
sudo su
chmod a+x NVIDIA \[tab\]
./NVIDIA \[tab\]
```

After typing the "NVIDIA" bit, you press Tab and it autocompletes to the full filename.

After the driver installs, just type this:

```
sudo gdm
```

And you're done.

---

### Post by Beastie Boy on 2009-03-13
Under Windows, to obtain and install the latest video card driver, I would go to the manufacturers web site, enter hardware and OS details and navigate to the driver download page. From there I then save the file to my computer and read the instructions on the site telling me how to install it.

Surprisingly, this also works with Linux!

Have a look [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36.3.1&lang=English&rev=9.2&ostype=Linux%20x86"). I doesn't look too difficult. But if you do run into problems, the Ubuntu community are uusually more than willing to help :)

Cheers, Beastie.

---

### Post by RaiCoss on 2009-03-13
Actually installing ATi drivers is actually really easy. This is how I used to do it:~

1)Download the driver to your DESKTOP.

2)Open ROOT terminal(you have to enable it by right clicking the menubar/menu, then click System Tools in the left hand menu pane, and then tick the Root Terminal in the right hand pane).

3)Now to to Applications>System Tools>Root Terminal. Enter your password if prompted. Then leave Root Terminal open, then click and drag the ATi driver into the Root Terminal window and let go. You should now see something like /home/whoeveryouare/Desktop/Ati(whateverdriverversion).run, and then just left click the mouse once inside the Root Terminal window and press enter. Then just follow the onscreen instructions and reboot. 

And unlike nVidia's drivers you dont need to worry about uninstalling the previous driver when installing the latest. Hope that helps somewhat.

P.S.I have to agree that Ubuntu needs far better documentation, I might actually try and help with this!

---

### Post by sisco311 on 2009-03-13
I don't own an ati card, so I made a little *experiment*.

[list=i]
[*]Goggle search: ati linux driver. 
The first result: [http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")
[*] Linux x86 -> Radeon -> ATI Radeon HD 4800 Series. Go
[*] I downloaded the driver and the Installation Instructions.
[*] In the Helpful Links section I've found the [Unofficial Wiki for the Ati Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page").
[*] There I've found the step-by-step instructions for installing the driver in [Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu").[/list]

Here is the guide for Intrepid Ibex: 
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

> **sdennie said:**
> Actually the mechanisms for a "manually installed" driver to automatically update itself on new kernel installs have existed for years.  The vendors choose not to take advantage of those mechanisms so, yes, it is very much a driver problem and not a fundamental Linux problem.  There is also no reason why vendors can't setup software repositories and keep them up to date with the newest versions.  In which case, installing up to date drivers becomes incredibly trivial even for someone with only a few hours of Linux experience.

Almost all the problems with "driver installation" can be directly attributed to 3rd party driver writers thinking in Windows mode and not Linux mode.  If they would make their drivers more "Linuxy", many of the complaints/problems would go away.
+1

---

### Post by stchman on 2009-03-13
I find that if you stay 6 months behind the latest hardware curve and check the Ubuntu Hardware Compatibility List you rarely run into problems.

I purchased my last three computers after checking the HCL and surprise, no problems.

---

### Post by wolfen69 on 2009-03-13
> **sisco311 said:**
> I don't own an ati card, so I made a little *experiment*.

[list=i]
[*]Goggle search: ati linux driver. 
The first result: [http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")
[*] Linux x86 -> Radeon -> ATI Radeon HD 4800 Series. Go
[*] I downloaded the driver and the Installation Instructions.
[*] In the Helpful Links section I've found the [Unofficial Wiki for the Ati Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page").
[*] There I've found the step-by-step instructions for installing the driver in [Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu").[/list]

Here is the guide for Intrepid Ibex: 
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")


+1

are me and sisco the only 2 people that know how to use google correctly?

i'm going to conduct my own *experiment*, and bang myself over the head and see if it makes me as dumb as the average person.

---

### Post by sgosnell on 2009-03-13
Wolfen69, [let me google that for you](http://www.lmgtfy.com/?q=how+to+use+google+correctly).   :D

---

### Post by wolfen69 on 2009-03-13
> **sgosnell said:**
> Wolfen69, [let me google that for you](http://www.lmgtfy.com/?q=how+to+use+google+correctly).   :D

thank you SOOOO much. how can i ever repay you?

---

### Post by betrunkenaffe on 2009-03-14
> **wolfen69 said:**
> are me and sisco the only 2 people that know how to use google correctly?

i'm going to conduct my own *experiment*, and bang myself over the head and see if it makes me as dumb as the average person.

No, and the fact that it seems this way sometimes (that no one knows how to google) annoys and saddens me greatly.

---

### Post by wolfen69 on 2009-03-14
> **betrunkenaffe said:**
> No, and the fact that it seems this way sometimes (that no one knows how to google) annoys and saddens me greatly.

yes, it is sad. but no matter what i try to do in life, if i don't know how to do something, i research and just get it done. obviously people in general don't follow this approach and expect everything to be handed to them.

---

