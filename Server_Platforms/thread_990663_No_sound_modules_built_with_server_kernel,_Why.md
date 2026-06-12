---
title: "No sound modules built with server kernel, Why?"
date: 2008-11-22
forum: Server Platforms
---

### Post by pksings on 2008-11-22
Can somebody give me a logical reason why the sound modules are not even supplied with the server kernel?  I have a 32bit system that has been upgraded a few times and now has 4GB RAM. Works fine, but no sound. It's also my workstation as well as a web, file and print server. So to utilize the RAM I have to do without sound, or build a kernel from scratch. Not acceptable.

---

### Post by Thirtysixway on 2008-11-23
Well most servers don't have a need for speakers or soundcards...

You need to get the Desktop version, there's really no reason to be running Server version as a standard workstation.

---

### Post by pksings on 2008-11-23
No, what I need is kernel sound modules for the server kernel. 

Four problems with your post, First, either you didn't really read my post or you didn't understand it. Second, your post is NOT an answer to the question posed. 

Third, I have to ask, who are you to tell me what I "need" and that I don't have a perfectly good reason when I have already plainly stated my perfectly good and understandable reason? Are you my judge? Or maybe godlike or something? You are not in any position of authority to me that I'm aware of so, that post took either a lot of nerve or a complete lack of good sense, or maybe both. Please, if you can't help in the future, don't participate, that was totally un-helpful and rude. 

Fourth; just a little bit of thinking on my post makes it obvious that I already have a 32bit kernel, why else would I even be asking about the server kernel, it's only for 32bit, the 64bit automatically includes the functionality I'm asking about. By stating that it's been upgraded a few times I am showing that re-installing it as a 64bit system is not viable option, so I am trying to find a way to use the 32bit kernel with the "bigmem" patch. The system was originally installed with 6.06, Dapper, and has been upgraded from there. The hardware has been upgraded twice to get to this state, without the need for re-installing. (Take that Windows)

To the point,  I have a perfectly good reason for running the server kernel. I have 2.8GB of RAM without it when I really have 4GB installed. With the server kernel all 4GB get's used, without it it doesn't, wasted resources. Yes most servers don't have sound, obviously this one does. As I stated before, it's also a workstation. I don't want another machine in my home office wasting electricity and cooling to be my web, print and file server when I don't need to. This is much more energy efficient. I have 4 cores in this thing, it's got more than sufficient horsepower to do all the things I ask of it. What it doesn't have is enough memory available to not swap when I load a Windows VM. It has enough installed, just not available because I have to run a kernel that can't use the extra memory to get sound, and that doesn't seem right to me.

Hopefully someone from Canonical will read this and recognize that this is a really good selling point, your server can be your workstation. Ideal in today's small offices and smaller companies or today's energy conscious environment.

My apologies to everyone else that reads this, I shouldn't rail on this person like this but that post got to me....My parents taught me not to say anything if you haven't got anything nice to say. I think either he (or she, though I suspect a he) somehow didn't get, missed that lesson or forgot it's value. I am ruining the peaceful, helpful nature of this wonderful forum and I do apologize.

---

### Post by gombadi on 2008-11-23
> **pksings said:**
> Can somebody give me a logical reason why the sound modules are not even supplied with the server kernel? 

I believe that this is the question you asked and I also believe that Thirtysixway answered it with -

> 
Well most servers don't have a need for speakers or soundcards...


I agree with Thirtysixway. As most servers do not have sound cards or speakers there is little need for sound modules in the supplied kernel.

From what I can see you are using a non-standard configuration. You are using a workstation and wanting workstation features (sound) but have chosen to use a server kernel. That is your choice but having made that choice you have to live with the restrictions that choice will bring.

> 
Hopefully someone from Canonical will read this and recognize that this is a really good selling point, your server can be your workstation.


If someone from Canonical is reading, then as someone who is running many servers, please do not add unnecessary modules to the kernel. Clean and simple is best. But that is just my opinion.

Also may I add that after reading you original post I also asked myself why are you running a server kernel and expecting sound to work. 

Instead of expecting others to stop and think about your post it may be better to provide others all the things you have tried and the reasons why you have decided to configure your system the way you have. The reat of the community may not have the time to ponder all the things you expect them too.

Bottom line as I see it is that you have a system that can only use some of the RAM if using the desktop kernel or no sound if you use the server kernel. I also understand that you find building a kernel that suits your requirements as "Not acceptable". 
I also believe that you original question has been answered.

May I suggest that you now ask another question -

------------------------------
I have a combined workstation/file/web server system that will not use all 4GB of RAM if I use the desktop kernel and does not support sound if I use the server kernel. I do not want to/am unable to build a kernel myself.
Can someone suggest a way I can use all my RAM and enjoy sound.
------------------------------


> 
I am ruining the peaceful, helpful nature of this wonderful forum and I do apologize.


Others may disagree with your peaceful and helpful nature towards those that are trying to provide you with assistance. It may be better to reply with a "thanks but your suggestions do not suit because ..." than have to apologize.

---

### Post by pksings on 2008-11-23
Gombadi;

Thank you, your post makes sense, my configuration is definitely different from the server-farm type servers and I totally understand why those who have many servers might not want sound modules sitting on their drives. And the few MB of space that they would take up on the hard-drives would definitely be wasted space. All 5.21 MB of it.

On the other side of that same idea, the only drawback for servers is that the modules would exist on their hard-drives as they wouldn't be loaded as there is no hardware for them to support. 5.21MB is how much space they occupy. (2.6.24-generic kernel). All the physical servers that I have built at my day job in this last year were using 146GB drives, so this would be negligible. 
I don't think it would really add to anyone's "complexity". And the growth rate of the kernel is so fast that it really begins to be inconsequential in view of it. So much other stuff has and will continue to be added that those same big servers don't use, all the USB stuff, firewire, cameras, TV cards, multifunction printers, scanners, video cards, and lot's of other stuff, it's all on those drives already. I had to backup, delete and re-partition my system last year because my /boot was now too small, it could only hold two kernels. When I originally installed it, it held five. And that's just the kernels, init images and related files, not the modules. 
5.2 MB is totally inconsequential, and I don't believe you or anyone else would notice or care.

The versatility and the power savings that this configuration gives me however, are huge, in a SOHO or small business office this means one less computer is running. This also means one less computer has to be purchased, which is why I chose this configuration. That is a significant impact to a small business. As a selling point to me that is huge, versus having to buy a "server" and a separate workstation. That plus the built in backups of my files, no brainer.

No sound is a major irritant. For me personally it's a deal-breaker as I do have the need to edit sound files occasionally for my DJ business.

None of the supplied kernels in the repositories except the server kernel seem to have the bigmem patch. So, it does seem that the only way that I can solve this is re-installing as a 64 bit system, which unfortunately will clobber all of my custom changes accumulated over the past few years, and require many hours of redo time. Along with removal of functionality that I use daily, a reasonably un-buggy flash player for example. As far as I can tell 64bit workstation is not quite ready yet, still plenty of stuff that works funny or not quite right. A very, very unattractive alternative, especially in light of the 32bit system I have that works fine, just doesn't have enough memory.

As a side point, I came over to Ubuntu from Gentoo, I have built plenty of kernels before. I no longer wish to spend the time and experience the frustration of that process trying to get everything that this machine needs selected so that it will build one that makes everything work, and then have to repeat it when there is a patch. That is why I am using Ubuntu, the kernel builders do a great job, everything just works, kernel after kernel. Everything except sound with the server kernel, which is different than every other kernel, sound works fine with every other one I've tried.

Canonical, 5.2MB of space, versus no functionality for SOHO users like me. To me it's an easy choice, I would like to change your decision. Please consider it. As a compromise, how about providing the modules as a separate installable so the server-farm people can do without it if they want and us SOHO people can still have them? 4GB or RAM now costs $30 on sale here in the USA. This will become more and more common.

---

### Post by Thirtysixway on 2008-11-23
It doesn't matter how much space it takes up.  It's not needed by most users.

You've really come at us with a bad attitude about all of this.  It's not our fault you installed server version.  Perhaps you should look at the 64bit desktop version.

---

### Post by Philio on 2008-11-23
So you have Ubuntu server edition installed, but you've obviously installed the desktop components on top of this anyway... How exactly is this any different from installing the desktop edition of the OS, except that your running a kernel with less hardware and driver support as it is intended for headless machines with far less hardware?

All packages that are available in the desktop edition are available to the server edition and vise versa. The desktop edition does not restict you from running server components, there are many many users running the desktop edition with server software running such as LAMP, Samba, etc.

The same applies for 64 bit versions of Ubuntu, same packages, plus you can install the 32 bit libraries to run 32 bit applications. I have 9 servers and 2 desktops running 64 bit Ubuntu without any issues.

I may well be wrong but your posts sound like they are based more on assumption rather than good research. You mention buggy flash player, however I can't say I've ever come across any flash content that doesn't play on Ubuntu with 18 months of usage.

If you want a response from Canonical on this you could always purchase their support package via [http://www.canonical.com/services/support](http://www.canonical.com/services/support) :)

Finally, this is a community forum, nobody has to help you, frankly your attitude towards Thirtysixway stinks.

---

### Post by cariboo on 2008-11-23
I don't know what kernel you ar using, but I'm running:

```
Linux willy 2.6.27-7-server #1 SMP Tue Nov 4 20:16:57 UTC 2008 x86_64 GNU/Linux

```

I have sound modules in /lib/modules/2.6.27-7-server

Even though I don't use the sound card there are modules loaded for it:

```
 lsmod | grep snd
snd_intel8x0           43688  0 
snd_ac97_codec        133080  1 snd_intel8x0
ac97_bus               10368  1 snd_ac97_codec
snd_pcm                99208  2 snd_intel8x0,snd_ac97_codec
snd_timer              34320  1 snd_pcm
snd                    79432  4 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore              16800  1 snd

```

Before complaining have a look. It may be that there isn't a module for your particular sound card.

Jim

---

### Post by kerry_s on 2008-11-23
you could have a sound card who's firmware is not distributable.
my firmware was dropped, i have to compile the firmware for any kernel over 2.6.20 for my yamaha card.

my card:
```
snd_pcm_oss            32800  0 
snd_mixer_oss          12320  2 snd_pcm_oss
snd_ymfpci             28224  1 
gameport               10700  1 snd_ymfpci
firmware_class          6816  2 pcmcia,snd_ymfpci
snd_ac97_codec         88484  1 snd_ymfpci
ac97_bus                1728  1 snd_ac97_codec
snd_pcm                62596  3 snd_pcm_oss,snd_ymfpci,snd_ac97_codec
snd_opl3_lib            9344  1 snd_ymfpci
snd_hwdep               6212  1 snd_opl3_lib
snd_page_alloc          7816  2 snd_ymfpci,snd_pcm
snd_mpu401_uart         6368  1 snd_ymfpci
snd_seq_midi            5728  0 
snd_seq_midi_event      6432  1 snd_seq_midi
snd_rawmidi            18496  2 snd_mpu401_uart,snd_seq_midi
snd_seq                41456  2 snd_seq_midi,snd_seq_midi_event
snd_timer              17800  4 snd_ymfpci,snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          6380  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd                    45604  12 snd_pcm_oss,snd_mixer_oss,snd_ymfpci,snd_ac97_codec,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6368  2 snd

```

---

### Post by pksings on 2008-11-24
All;

First, my apologies for my apparent bad attitude. I had just spent over an hour troubleshooting why I had no sound and was rather unhappy that it was because of no modules existing. To me that was rather mind-boggling. I definitely would like to apologize for that. I'm thinking I need to invoke a check system like Google that would prevent me from posting when irritated.

Second. I did not install the server version of the distro, I installed the desktop version as I wanted the GUI and sound and all of the related stuff. All of the other packages/services like MYSQL, Apache etc, were installed via synaptic. 

When I discovered that it would not use all of the installed memory I then did a bit of research, found that only the server kernel supports the bigmem patch in 32bit Ubuntu and installed that. 2.6.24-20-server and 2.6.24-21-server are the two that I tried. That's cool that a newer version does supply them. I don't see that version in Synaptic for Hardy at this time, but I'll enable additional available repositories for it, and it will solve my problem. Which also makes this whole discussion moot.  For grins and giggles I'll include just a bit more...

Third, 4GB of RAM is now very inexpensive. I think that we will see more and more people running into this issue and the bigmem patch may need to be more widely used. Most newer installs are using 64bit, but as I stated before, for me to do that would wipe a lot of accumulated changes and tweaks. And there are things that I use as a desktop user that as far as I can tell, aren't quite ready in 64bit, though it has been a while since I looked into it, I did see the post from the user who has been 64bit mode for while with no issues. About two months ago I couldn't get my wireless card to work with a 64bit install and it worked fine with 32bit, also the 3Ware RAID card GUI would only install in a i386 version kernel initially, I found a version that would install on i686 eventually, but that was after I got it installed initially.  I was thinking maybe another year or so before that became a viable option. In the meantime, being forced to use 64bit version just to get all of your memory available seems...limiting? Mostly because of the need to re-install.  

On the other hand what you state about this being rather unusual is probably true, and will be used by only a minority of people in all likelyhood. But with the modules being supplied in a more current kernel version apparently I'm not the only one who thinks this is a good idea.

Thanks for your time everyone, my apologies again for my attitude, I will endeavor to control it much better in the future. And thanks again.
 
I would like to extend an apology directly to thirtysixway, you were trying to help me and I totally took it wrong.  My error, and thanks for your help.

---

