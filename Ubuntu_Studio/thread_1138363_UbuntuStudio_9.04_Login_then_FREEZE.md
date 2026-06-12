---
title: "UbuntuStudio 9.04 Login then FREEZE"
date: 2009-04-26
forum: Ubuntu Studio
---

### Post by nesnfsn on 2009-04-26
Anyone else experiencing a freeze after installing and logging into UbuntuStudio 9.04 i386 version?

I have installed i386 version several times. Alternated selection of relatime and noatime (believe those were the options amongst others available). No matter, I log in, and then, US 9.04 freezes. Have to hard reboot.

Also, can anyone advise as to what these options really do, and whether one would be better than the other (or the other options) for my hardware, and if so, why???

Am downloading amd64 version currently, and will try that one and see if it works.

Here are my specs, in case it helps:
Intel E8400 3.0Ghz Core2Duo CPU
EVGA 780i Motherboard
8Gb DDR-2 800 Mhz RAM
XFXForce 8600GT 1Gb DDR-2 Video Adapter
Maxtor 500Gb SATA-II Hard Drive

---

### Post by volter on 2009-04-26
You have nice comp. When you were installing your current system (windows/mac) / trying rearrang partitions did your comp gave you eny worring/arror while was loading drivers if not it's ubuntu problem.

---

### Post by Stochastic on 2009-04-26
In your initial install are you selecting the audio meta package?  This selects the realtime kernel by default (which looks to have some freezing issues still hanging around).

You may want to try not selecting the audio meta, then after you boot install the audio meta - this will give you both kernels rather than just the RT kernel.

---

### Post by nesnfsn on 2009-04-26
> **Stochastic said:**
> In your initial install are you selecting the audio meta package?  This selects the realtime kernel by default (which looks to have some freezing issues still hanging around).

You may want to try not selecting the audio meta, then after you boot install the audio meta - this will give you both kernels rather than just the RT kernel.

Thanks, I will give that a try sometime this week, when I get some free time. And, just so you know, I had chosen all application packages and selected none. Either way, boots, goes to log in, log in, go to update manager, and then FREEZE.

Btw, just in case I am not being clear, I had indeed tried the amd64 version this morning after my original post, and I had experienced the exact same freezing problem with amd64 version. 

Hope this is fixed soon, as I would love to see how this distribution runs with MythTV and/or XMBC, rather than just plain ubuntu (or TheeMann's Ultimate Edition which i have used for the past year or so).

---

### Post by WyleECoyote on 2009-04-26
I have the same problem both with studio 64 and 32, the problem as I have seen it is that you have hyperthreading enabled in your bios, the -rt kernel as far as I have seen only supports 1 CPU. you have 3 options I know work, at least they do for me.

   1) disable hyperthreading in your system bios - works, but I also want it enabled for my other OS's. So, not the option for me.

   2) you can disable acpi on boot, assuming you have grub, when grub loads highlight kernel you are booting, hit 'e' to edit boot options, at the end of the kernel line type "acpi=off" then ctrl-c to boot, that is a temp change, if it works and you are ok with it then fire up your favorite editor as root and change your grub configuration file:

For grub it is ```
sudo nano /boot/grub/menu.lst
``` For grub2 it is ```
sudo nano /boot/grub/grub.cfg
``` I use grub2 so I am not exactly sure the above is the same way to edit in grub at logon boot options, but should at least be close. this option is too slow for me.

   3) install generic kernel that will support HT. which is what I am going to do. because the -rt kernel is not worth the slow-down and problems.

   I have also read that you can downgrade to version 7, but I have not and will not try that.

   The easiest way I have found to test this was to boot single user mode with no modifications, select boot to command line with networking or whatever, install htop
```
sudo aptitude install htop gkrellm
```
gkrellm is optional, but my favorite when I actually make it into Gnome so I can keep and eye on my temps, HDD access, CPU usage etc..

after htop is installed run it with "htop" you will see that CPU2 is running at %100 with nothing loaded. F10 to exit reboot and fix whatever needs fixing.

---

### Post by Stochastic on 2009-04-26
> **WyleECoyote said:**
> I have the same problem both with studio 64 and 32, the problem as I have seen it is that you have hyperthreading enabled in your bios, the -rt kernel as far as I have seen only supports 1 CPU.

What?  The RT kernel supports dual-core processors.  There was a bug in the Intrepid version of RT that only used one core of dual-core processors, but the Jaunty one should be fine.
Furthermore, the chip that the OP has is not a hyperthreading chip.

I'd advise both of you to review the list of bugs here: [https://bugs.launchpad.net/ubuntu/+source/linux-rt](https://bugs.launchpad.net/ubuntu/+source/linux-rt) and add anything you feel is a legit issue.

---

### Post by nesnfsn on 2009-04-30
I did add a bug, and no response from US team. When will I learn if there is a fix???

---

### Post by andreika73 on 2009-05-04
[COLOR=black][FONT=Verdana]Hi there nesnfsn! I got exact same problem with my Acer Aspire 5610Z, Intel(R) CPU [EMAIL="T2080@1.73"][COLOR=#0000ff]T2080@1.73[/COLOR][/EMAIL] GHz, memory 2.00 GB, 32-bit OS (Vista Premium Home edition). It had worked just fine for a week, and now, as soon as I login and try to make a mouse move, it freezes forever. Did you find a fix yet? I'm about to install a different distribution. Thanks, Andrei[/FONT][/COLOR]

---

### Post by carlotheman on 2009-05-06
I have a similar problem; running a Samsung R41 Madea with ATI graphics, real time kernel. The freezes occur quite randomly and unpredictably, once it occurred right after loging. Interestingly, a sound server (supercollider) and JACK continue to play for a while after the freeze occurs before it dies too.

Carlo

---

### Post by Wistful on 2009-05-10
Same problem for me.

When I try to make some updates using the Update Manager.. after I selected my updates, I click to download and then FREEZE!

---

### Post by Stochastic on 2009-05-11
The best solution I've found is to IMMEDIATELY run ```
sudo apt-get install linux
``` after you've installed.

This gives you the regular Jaunty kernel along with the Realtime Patched kernel.  Then, whenever you're doing any non-audio work (particularly any system maintenance where programs are being installed) reboot into the more stable regular kernel to do that work.

This setup can also be achieved if during the install the Audio task is not selected (at the time when you're asked to install software packages), then install it after boot.

---

### Post by virgult on 2009-05-11
I know I'm not gonna do any kind of constructive criticism with this post, and I'm sorry for that, but I'll give you my opinion anyway.
Seems that the only way to fix this problem is to disable the SMP and the ACPI from Grub, when you boot the kernel; this is the workaround suggested by most people here, and by a friend of mine who knows linux very well. The fact is that the RT kernel doesn't behave as expected with dual-core machines, and all those CPUs with hyper-threading capabilities (P4 Northwood and Prescott, maybe the Atom but I'm not sure). This is the EXACT bug that occurred on the 8.10 release... and still, after six months, the issue is the same, even though the official site says that the "rt kernel is back".
I'm not a developer, and I don't have enough linux/programming skills to help the project as I'd like to do... but this lack of attention really bothers me. I mean, Ubuntu is meant to be the distro that boots up easily on almost all machines, and after some basic tweaks everybody can have his linux-box up and running (maybe with some issues, but not THAT serious). Though, the audio-oriented ubuntu is messed up in such a horrible way! Developers.... where are you?

For now, I installed a Debian Squeezy with Xfce and I'm gonna try building a rt kernel "from scratch". I'll see how this thing plays out, and if you are interested I can share my results.

---

### Post by StudioDave on 2009-05-12
> **virgult said:**
> I know I'm not gonna do any kind of constructive criticism with this post, and I'm sorry for that, but I'll give you my opinion anyway.

I'm going to say "Amen!" to your post and add my own screed.

> Seems that the only way to fix this problem is to disable the SMP and the ACPI from Grub, when you boot the kernel; this is the workaround suggested by most people here, and by a friend of mine who knows linux very well.

I will try those settings. I've added nosmp at boot but it didn't fix the problem.

Btw, I've had a lot of problems with Jaunty, and they are indeed almost all problems I had with 8.10. One new problem was the installation failure from either i386 or the amd64 DVD ISOs. Very exciting ! I got past the partitioning and then the installer failed at Select & Install Software. The entire process borked, I had to cancel the installation, and that left me with a hosed partition. I'm no newbie, I had kept my 64 Studio installation intact, and I could boot into it after Jaunty puked.

I took a cue from another user, re-installed 8.10 standard, and clicked the big Upgrade button in the update manager. Jaunty installed fine with its normal kernel, so I added the nVidia driver (180.xx, IIRC) from the Hardware Drivers panel. Things seemed to work fine, then I installed the Ubuntu Studio meta packages. After that I've had nothing but troubles with both the normal and the rt kernels. 

The mouse and keyboard freeze immediately after login. They work until the main display opens, then everything is gone and I have to do a hard reset, which really sucks IMO. Taking another cue from another user I took advantage of the pre-login condition and switched to a console. I logged in and set up the OpenSSH server, then I logged into that box from another machine. I used X forwarding and was able to run everything apparently just fine.

So where exactly is the problem ? Ah, that is the resolution-defying question, isn't it ? I thought it would be the rt kernel, but the freeze occurs with the normal kernel too. Maybe it's nVidia's fault ? I'll disable that driver and build it myself, perhaps I'll have better luck, but I don't believe it's the video driver's fault either. I use the same machine with 64 Studio 3 beta (based on Hardy, btw) and the latest nVidia driver (locally built), and everything works beautifully. So again I ask, where's the problem with Ubuntu Studio ? 

I've killed networkmanager and I've disabled unnecessary HAL polling, but that fixed nothing. Oh, and Jaunty, just like Intrepid, didn't recognize my Synaptics Touchpad, so there was no Touchpad panel to disable it. I thought I fixed the problem by editing a HAL fdi file but I got no joy from that either. Gsynaptics still tells me that SHM is unconfigured.

Y'know, X used to be comparatively easy to configure by hand. Not any more, and I don't agree that fdi files are an improvement.

Since I can ssh into the box I'll be happy to provide developers with reports up the wazoo. However, the wilderness that is the Ubuntu forums doesn't make me confident that I'm reaching the right devs, so a little acknowledgement and assurance wouldn't hurt. As some incentive, my experience is going to be written up for an article in the Linux Journal. It would be nicest if the experience has a happy ending.

> This is the EXACT bug that occurred on the 8.10 release... and still, after six months, the issue is the same, even though the official site says that the "rt kernel is back"... the audio-oriented ubuntu is messed up in such a horrible way! Developers.... where are you?

Good question, though I cut them a lot of slack just because Ubuntu is so popular. I figure they probably have their plates piled high with bug fixes to get to.

The audio situation is just pathetic. Ubuntu Studio still installs Pulseaudio as its sound server of choice, leaving pro-audio types to figure out how to dump the damned thing and just have JACK. Devs, Pulseaudio != pro audio. Please stop using desktop sound servers for audio production systems, it's like trying to race a stock Volkswagen in the Indy 500.

When I try to remove Pulseaudio I'm told that the Ubuntu and Ubuntu Studio desktops have to go too. Grrr.... what a PITA.

> For now, I installed a Debian Squeezy with Xfce and I'm gonna try building a rt kernel "from scratch". I'll see how this thing plays out, and if you are interested I can share my results.

Okay, I'm listening. :)

And yet again, lest anyone thinks I'm bashing Ubuntu: I LOVE the system's design and I think it's a wonderful distro. I just want it to work on my hardware. That would be nice, and I'd like it even better then.

[addendum] The hoops I jumped through in Intrepid to turn off my touchpad no longer worked with Jaunty. After mucking about with xorg.conf and the relevant HAL fdi file I still got no joy from gsynaptics, syndaemon, or synclient. However, 'modprobe rmmod psmouse' at last got rid of the touchpad. I don't know whether the shm stuff is still necessary, but the damned thing is turned off now and that's all I care about. Another PITA resolved.

Best regards,

Dave Phillips

[http://linux-sound.org](http://linux-sound.org)

[http://www.linuxjournal.com/user/800764/track](http://www.linuxjournal.com/user/800764/track)

---

### Post by thorgal on 2009-05-12
Ciao Dave,

After having read a few of your articles in the past, I sort of derived the idea that a DAW is a highly customized system. That's why I quickly got back to debian sid after a couple of weeks I put up together my DAW and installed U.S. That was during summer 2007. U.S didn't last very long on my HD before some weird behavior happened. So I thought: let's do like the wise guys out there, get your hands dirty, tweak your DAW, etc, because you will use it for production, so you'd better know what you are running on it and how. And I did, and I would not change it for anything else now. U.S ? that's too much of an utopia, like other pro-audio distros. They all have their pros and cons, no doubt. But in the end, there's no such thing as an automagic software installation that will transform any PC into a productive DAW system. 

I would say this: so long as you know how to configure, compile and install your own kernel with the RT patch, and add kernel modules against your custom kernel version, you can make up your own DAW. That's what a guy nicknamed GMaq (ardour forum) did with his AV Linux (version 2 as of now). He was tired of all these problems and decided to make up his own system. It is available for free. You have to look on the ardour forum though, I do not have the link readily available. 

As to my own system, well, it is way too customized to be released :)

ah, here it is: [http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)

---

### Post by StudioDave on 2009-05-12
> **thorgal said:**
> ... in the end, there's no such thing as an automagic software installation that will transform any PC into a productive DAW system. 

I would say this: so long as you know how to configure, compile and install your own kernel with the RT patch, and add kernel modules against your custom kernel version, you can make up your own DAW.

Hi thorgal,

Thanks for the link to AVLinux, I'll try it as soon as I can. Meanwhile I can report some progress with Ubuntu Studio. I've added these options to the kernel boot options :

nosmp
pnpbios=off
acpi=off

So far I've had no more freezes. Perhaps more importantly I kicked Pulseaudio off the stage, thanks to this fellow's fine advice :

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

I noted in /var/log/user.log that pulseaudio wasn't finding things, so I disabled it acccording to idyllictux's suggestions. Worked a charm, no more pulseaudio annoyances.

Anyone else's mileage will vary, of course, but for now I have an apparently stable system. I've rebooted a few times with no troubles, and I'm watching the system closely.

Re: rolling my own system: I did that for the first ten years I used Linux, and I'm just plain tired of it. I want to work on my music, not fart around with kernel patches and the rest. Yes, it was all very interesting at one point, but no longer. 64 Studio has proven to be the best fit for my hardware, though as you can see I still test other systems (hence the interest in US).

I must also mention the by-now ancient Jacklab distribution. JAD 1.0 is still running like a champion on my second production box. It's based on OpenSUSE 10.2 and is as steady as a rock. PlanetCCRMA is also a traditionally very stable system, but I'm not running it on any of my boxes at this time. Soon, I hope.

So with those systems working nicely, what's the problem with Ubuntu Studio ? The devels might want to consider how the 64 Studio and JAD devs succeeded and go from there. US is a lovely system in so many ways, but I'm jumping through too many hoops again just to get its audio up to my expectations.

Thanks for the note and advice, thorgal. It's always good to hear from you. :)

Best,

dp

---

### Post by thorgal on 2009-05-12
Dave,

re: rolling my own system. 
I did that for the first month :lol: and then I sticked to it, updating it has been a routine, nothing any debian user would not do regularly. Even compiling a new kernel is routine (and if I was more lazy - not less - I would write up a script to automate the whole procedure as every time, I do the exact same thing ;) )

---

### Post by mohanohi on 2009-05-17
followed every advice.. added acpi=off and others bla bla bla.. But still it freezes after booting up..

---

### Post by houseworkshy on 2009-05-18
I'm on a two drive machine and have found ubuntu 9.04 works but am having the same problem with studio 9.04 which I put on the other drive.  It freezes on updates.  From what I've read above it could be a duel core issue ( wasn't that true of the last release too? ). Until I read that it has been fixed I'll use the other drive for something else, which is a pity as I loved studio on my old single core machine.  Meanwhile for anyone who is finding that it is affecting their work don't worry, one can simply put all the audio, graphic and video goodies into the standard Ubuntu where they work fine.

---

### Post by Nab!!daN on 2009-05-18
Hi all,

I do have the same issue, all work fine on a regular kernel but freeze with kernel RT 9.04.

---

### Post by raboofje on 2009-05-18
> **StudioDave said:**
> I kicked Pulseaudio off the stage, thanks to this fellow's fine advice:

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

I simply removed pulseaudio (it was a while ago, but I don't remember it being much more complicated than 'apt-get remove pulseaudio') - doesn't seem to be causing me much trouble.

> Re: rolling my own system: I did that for the first ten years I used Linux, and I'm just plain tired of it. I want to work on my music, not fart around with kernel patches and the rest. Yes, it was all very interesting at one point, but no longer. 64 Studio has proven to be the best fit for my hardware

Hear, hear: regular users shouldn't have to bother too much with this kind of stuff, even if they can. Personally I'm not afraid of digging in a bit, and I still think it's worth the time if there's any chance my conclusions lead to fixes upstream that more people can take advantage of, but that somehow seems to be getting harder...

---

### Post by QwUo173Hy on 2009-05-20
Luke MacNiell packaged a custom rt-kernel which I am now using. I've been using it all day and I couldn't even get 10 minutes on the default rt-kernel so I'm happy with this.

You can find them here
[https://lists.ubuntu.com/archives/ubuntu-studio-users/2009-May/004780.html](https://lists.ubuntu.com/archives/ubuntu-studio-users/2009-May/004780.html)
but I'll be putting them up soon to spare his bandwitdh.

Jarlath

..okay, I've uploaded the same files to these locations:
[http://dl.getdropbox.com/u/464104/linux-headers-2.6.29.1-rt8-custom_2.6.29.1-rt8-custom-10.00.Custom_i386.deb](http://dl.getdropbox.com/u/464104/linux-headers-2.6.29.1-rt8-custom_2.6.29.1-rt8-custom-10.00.Custom_i386.deb)
[http://dl.getdropbox.com/u/464104/linux-image-2.6.29.1-rt8-custom_2.6.29.1-rt8-custom-10.00.Custom_i386.deb](http://dl.getdropbox.com/u/464104/linux-image-2.6.29.1-rt8-custom_2.6.29.1-rt8-custom-10.00.Custom_i386.deb)

---

### Post by StudioDave on 2009-05-22
> **mohanohi said:**
> followed every advice.. added acpi=off and others bla bla bla.. But still it freezes after booting up..

Did you remove the network manager ?

I resolved my problems with US by poring over the information in /var/log/* and comparing it with reports from other users. I discovered that Pulseaudio was causing some problems, the network manager was causing others, so both of them had to go. Other issues didn't seem to be the showstoppers.

Are you running an SMP or uniprocessor installation ? I've heard that SMP and rt kernels don't mix so well on US yet.

Is your system freezing at the login screen or can you get as far as the desktop ? My system froze upon reaching the desktop, specifically when it started the Update Manager. That's how I narrowed things down to the network manager.

What hardware are you using ?

---

### Post by mohanohi on 2009-05-23
it freezes randomly.. sometimes before boot. sometimes in login.. sometime after login working 2 mins mine is amddual core.. nvidia chipset asus motherboard

---

### Post by Totalchaos on 2009-05-24
Yeah i have had the same problems with 9.04. it freezes even when i use the audio production software and that sucks [-X So i made some experiments of my own and i found 3 ways to make the buggy software works with no vulnerabilities. the ways are:

1. Add the following in the menu.lst in the kernel options:  "nosmp  pnpbios=off  acpi=off" it works but it reduces the Productivity of my hardware and that's not the idea after all
2. Upgrade from Hardy 8.04and keep the hardy RT kernel "2.6.24.24". The Hardy RT kernel is stable and can be trusted. To prevent conflicts do not install any additional software during the upgrade. Well if you are feeling lucky it will work perfectly 4 U
3.Install the new testing 64studio kernel "2.6.29-1-mulimedia" available on both i386 and amd64 versions. i install the following 
  "linux-kbuild-2.6.29_2.6.29-1_amd64" 
  "linux-headers-2.6.29-1-common-multimedia_2.6.29-2_amd64"
  "linux-headers-2.6.29-1-multimedia-amd64_2.6.29-2_amd64"
  "linux-image-2.6.29-1-multimedia-amd64_2.6.29-2_amd64"
well if you want to do that, it will be nice to download the .deb files before reinstall the fresh US-9.04, because you can't use the internet with this buggy kernel ;) . So install the fresh US-9.04 add the new kernel and you are fine. The sympatic manager will give you error 128 (can't compile the new kernel), every time you install or upgrade some new software. BUT WHO CARES. it's better to work fine with some uninteresting tiny error, than no work at all but with no errors :lol:.
well if you like to try and share the experience here. Let's make this software works for us.
VIVA LINUX:guitar:

---

### Post by carlotheman on 2009-05-31
I'm trying the custom RT kernel, leave my system on for 30-40 hours, and report stability. (And feature regressions, if applicable)

[COLOR="Purple"]**Edit: The custom kernel crashed less frequently, but still did.**[/COLOR]

---

### Post by carlotheman on 2009-06-01
I am now trying the 64studio beta kernel. You can install it by installing a single package.

[64studio RT-Kernel 32bit]("http://apt.64studio.com/backports/pool/main/l/linux-2.6/linux-image-2.6.29-1-multimedia-686_2.6.29-9_i386.deb") [(headers)]("http://apt.64studio.com/backports/pool/main/l/linux-2.6/linux-headers-2.6.29-1-multimedia-686_2.6.29-9_i386.deb")

[64studio RT-Kernel 64bit]("http://apt.64studio.com/backports/pool/main/l/linux-2.6/linux-image-2.6.29-1-multimedia-amd64_2.6.29-2_amd64.deb") [(headers)]("http://apt.64studio.com/backports/pool/main/l/linux-2.6/linux-headers-2.6.29-1-multimedia-amd64_2.6.29-2_amd64.deb")

All Ubuntu functionality is working on my system (although I am not using any restricted drivers). Realtime performance is a definite improvement over the Jaunty RT-kernel.

I will report back with a stability report in about 48 hours.

Carlo

**[COLOR="Purple"]Edit: There have been no crashes since upgrading to this kernel. Real time performance has significantly improved. There have been no feature regressions for my system (Samsung R41 Madea notebook)[/COLOR]**

**[COLOR="Red"]Edit2: For some reason similar crashes have since returned, similarly frequent; however, now the computer can be restarted with ALT-PRNTSC-REISUB. I am now trying the following in addition to the new kernel.[/COLOR]**

```
cd /tmp
wget http://temp.minimum.se/mesa_with_fixed_ati_bug/libgl1-mesa-dri_7.4-0ubuntu3_i386.deb
wget http://temp.minimum.se/mesa_with_fixed_ati_bug/libgl1-mesa-glx_7.4-0ubuntu3_i386.deb
sudo dpkg -i libgl1-mesa-dri_7.4-0ubuntu3_i386.deb libgl1-mesa-glx_7.4-0ubuntu3_i386.deb
```

This approach found on a [post on the OSS Notebook blog]("http://ossnotebook.blogspot.com/2009/05/ubuntu-jaunty-unstable-with-video-ati.html").

[COLOR="DarkGreen"]**Edit3: The combined approach of aforementioned packages and the new kernel seem to render a stable Jaunty System. *Finally*, if I may add this! I also locked the two packages in synaptic to avoid upgrades that don't contain the fix.**[/COLOR]

[COLOR="DarkOrange"]Edit4: Apparently, there is *still*, even after all this trouble, the occasional hard freeze. It's rare enough to have a better-than-nothing usable system, but I am really thinking about getting myself a laptop that is somehow "officially supported" or something.[/COLOR]

---

### Post by Abanabanana on 2009-06-29
Hello! 

I have had the same problem.

I followed the instorcution form Totalchaos 
> 
2. Upgrade from Hardy 8.04and keep the hardy RT kernel "2.6.24.24". The Hardy RT kernel is stable and can be trusted. To prevent conflicts do not install any additional software during the upgrade. Well if you are feeling lucky it will work perfectly 4 U

So I did install 8.04 and updated everything to 9.04 but the rt-kernel. It works, but it is not really the solution on a long term. :-) 

So three questions: 
1) How can I install BETAS through Synaptic? (to try the third option of Totalchaos)
2) How do I known when a stable/corrected RT-kernel 9.04 is ready to be installed? Is there some RSS news list, or should I just wait for someone from this forum to post the news? :-)
3) I have an AMD64 system. Rexpectively, I installed the 64US. The problem now is that not all programs work, since they were writen for 32bit systems (e.g.Skype). Is there some major disadvantage  to go the 32bit US version? 

Cheers....
Patrick

PS: For years I have been trying to change my system to linux, but since I'm doing a lot of audio production, that was impossible. Now with US that is finally possible (I still did not check if all my audio hardware works, but it seems to work ESI ESP1010 soundcard). It is just a pitty, that problems, like the ones discussed in this forum (continue) to occur, because this invites me to go back to my Windows+Cubase system. So I hope that a STABLE 9.04+ US version will appear soon!!!!! :-) In this sence THANK YOU TO ALL working on this RT system. Cheers

---

### Post by Cthulhu_Dreams on 2009-07-11
FUUUUUUUUUUUUUUUUU

This is so friggin' ridiculous.  I hate how everytime I upgrade, I must deal with crap like this.

I've tried to install that 64studio kernel, but it gave me errors.  

It says:

User postinst hook script [update grub] exited with value 20
dpkg: error processing linux-image-2.6.29-1-multimedia-amd64 (--install):
subprocess post-installation script returned error exist status 20
Errors were encountered while processing"
linux image-2.6.29-1-multimedia-amd64

Help?

**edit: okay the kernel did apparently work....I've only been using it for a good twenty minutes but no issues so far.  What were those two packages you locked, and how can I lock them? (please :D)**

---

### Post by carlotheman on 2009-07-17
> **Cthulhu_Dreams said:**
> FUUUUUUUUUUUUUUUUU
**edit: okay the kernel did apparently work....I've only been using it for a good twenty minutes but no issues so far.  What were those two packages you locked, and how can I lock them? (please :D)**

Hey! Glad it worked for you... I share your frustrations... I know UbuntuStudio is a volunteer effort so I'm grateful for what they have accomplished and it amazes me... but that doesn't keep me from REALLY WISHING IT WOULD WORK OUT OF THE BOX!

I two packages I locked are: libgl1-mesa-dri and libgl1-mea-glx. I search for mesa in synaptic to find them, clicked each one to select it and chose Package -> Lock Version on it.

---

### Post by royleith on 2009-08-23
Whereas Kubuntu has been as steady as a rock for me in both 32 and 64 bit versions, Ubuntu Studio has been a problem since I started with 8.04. 

The machine in question is a laptop with an Athlon X2. So, no hyperthreading, but two cores. 9.04 (64bit) has been a dreadful pain with jack dying a death after around 8 seconds. I added a maxcpus=1 in the kernel line of Grub for Ubuntu Studio and the change is dramatic. The installation is now stable and supporting Firewire audio for the first time. i don't think the RT kernals have been really happy on multiple cores for a few versions now.

Regards
Roy Leith

---

