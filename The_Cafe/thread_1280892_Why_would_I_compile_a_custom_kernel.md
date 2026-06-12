---
title: "Why would I compile a custom kernel?"
date: 2009-10-02
forum: The Cafe
---

### Post by Shibblet on 2009-10-02
I just purchased a new PC.  My main Hardware is...
AMD Phenom x4, 8G Ram, Nvidia GeForce GTX260

I have a friend who keeps nagging me to compile a custom kernel.  He keeps telling me that a custom kernel will squeeze more performance out of my PC, and that I am losing 15% - 25% of my processing power by not running a custom kernel.

Now, I am sure that's an exaggeration, but I still would like to know the benefits of a custom kernel?

---

### Post by scragar on 2009-10-02
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

> 
Reasons for compiling a custom kernel
[list]
    [*] You are a kernel developer.
    [*] You need the kernel compiled in a special way, that the official kernel is not compiled in (for example, with some experimental feature enabled).
    [*] You are attempting to debug a problem in the stock Ubuntu kernel for which you have filed or will file a bug report.
    [*] You have hardware the stock Ubuntu kernel does not support. 
[/list]
Reasons for NOT compiling a custom kernel
[list]
    [*] You merely need to compile a special driver. For this, you only need to install the linux-headers packages.
    [*] You have no idea what you are doing, and if you break something, you'll need help fixing it. Depending on what you do wrong, you might end up having to reinstall your system from scratch.
    [*] You got to this page by mistake, and checked it out because it looked interesting, but you don't really want to learn a lot about kernels. 
Compiling your own kernel can give different levels of performance boost by disabling and enabling specific features, for the most part though it's not recommended because of the flaws it introduces, for starters you have to manually update your kernel from now on, some stability issues may occur and there's the ever popular time and effort spend deciding just what you want in your kernel.

If the 2-3% you will likely gain by compiling your kernel specific to your architecture is worth the time to you, go for it, if the 5% or so you'll get by disabling a few parts of it is worth it, go for it.
Otherwise leave your kernel alone, it's the very core of your OS, break it and you'll need to do a lot of work to repair it.

---

### Post by starcannon on 2009-10-02
A custom kernel can allow quite a bit of optimization; however, for most users this is not necessary. If you would like to experiment, you can compile your own kernels, and try them out, you can always boot from the ubuntu generic kernel if something does not work correctly in your custom kernel. If you decide to experiment with your own kernels just press "ESC" when prompted at boot time, and choose the kernel you'd like to boot, from the grub menu.

GL and HF

---

### Post by openfly on 2009-10-02
[http://www.nycresistor.com/2009/09/28/another-hack-from-the-past-kernel-hacking/](http://www.nycresistor.com/2009/09/28/another-hack-from-the-past-kernel-hacking/)

Some of my reasons for rolling custom kernels...

Back in the day for instance it was a long standing lol that the HZ var inside 2.4 kernels was set to 100.  It was actually slowing faster systems down considerably.  With customizations and removal of some modules it was certainly possible to pull 15-25% more in performance.  That's not untrue.

But obviously, the linux kernel is a big ever changing beast... and you need to be tracking lkml and some of the big developers blogs / release notes to know where the big improvements are.

I would recommend reading up on Alan Cox's -ac patch set for 2.6... just read the release notes on them.  It gives you an idea of just how quickly production kernel releases get patched and what they get patched for..  sometimes it's some pretty damned scary stuff.

Mind you I don't patch my kernel that often any more.  It's not like it was back in 98 when I was fighting with my slackware install to get my network card and sound card to work at the same time.

---

### Post by Shibblet on 2009-10-02
> **scragar said:**
> If the 2-3% you will likely gain by compiling your kernel specific to your architecture is worth the time to you, go for it, if the 5% or so you'll get by disabling a few parts of it is worth it, go for it.
Otherwise leave your kernel alone, it's the very core of your OS, break it and you'll need to do a lot of work to repair it.

5% at the most?  (Is that pretty accurate?)  I think I'll just hang with the Generic Ubuntu kernel and not bother recompiling.

One of the reasons I choose Ubuntu as my distro, is because of things that you have to do in other distros, like Sabayon or Gentoo.  I believe you have to compile a kernel in Arch also.

I don't care about all of that, and I just want my OS to work.  I'm don't like fiddling with the OS.

The last time I tried upgrading the kernel, it was to get the 2.6.30 kernel that worked better with Intel graphics drivers.  And that turned into a disaster.  First, it didn't support my wireless connection in my netbook.  Then synaptic couldn't download anything, half of my programs wouldn't work...  I foresaw things like that happening when I tried a recompile.

---

### Post by starcannon on 2009-10-02
> **Shibblet said:**
> 
I don't care about all of that, and I just want my OS to work.  I'm don't like fiddling with the OS.


Cheers to that; no OS is perfect, and they all require a certain type and amount of massage to get them just right for ones particular situation. But when there is work or fun to be had, no one wants to be waiting an hour for a compile, to then only find out they didn't get something essential and have to start over. I use Ubuntu as my Linux distro of choice because it recognizes that there are those who prefer to just turn it on and start computing. All that said, I do enjoy a good geek out once in awhile, I just like it to be on my terms, not on necessity.

GL and HF

---

### Post by scragar on 2009-10-02
> **Shibblet said:**
> 5% at the most?  (Is that pretty accurate?)  I think I'll just hang with the Generic Ubuntu kernel and not bother recompiling.

One of the reasons I choose Ubuntu as my distro, is because of things that you have to do in other distros, like Sabayon or Gentoo.  I believe you have to compile a kernel in Arch also.

I don't care about all of that, and I just want my OS to work.  I'm don't like fiddling with the OS.

The last time I tried upgrading the kernel, it was to get the 2.6.30 kernel that worked better with Intel graphics drivers.  And that turned into a disaster.  First, it didn't support my wireless connection in my netbook.  Then synaptic couldn't download anything, half of my programs wouldn't work...  I foresaw things like that happening when I tried a recompile.

Unless you really know what you're doing it would be foolish to try and get more than 5 or 10% extra performance, really you're not going to get much more than that out of it anyway(and at greater and greater risk for every bit more performance).

---

### Post by markharding557 on 2009-10-02
if you do it do it for you for the challenge not because someone says you should.

---

### Post by kevdog on 2009-10-02
If you are really interested in learning about Ubuntu or linux in general, I would suggest rolling your own kernel a few times.  You actually learn a lot about kernel modules, and the other modules that are contained.  If you play around with the options, you will probably screw it up a few times, however thats actually part of the learning process.  I would suggest this actually is a must activity for a serious Ubuntu users.  You might not actually end up using the kernel, however it will give you a far greater understanding when reading a lot of the tutorials.

---

### Post by cariboo on 2009-10-02
Back in the late nineties I compiled my own custom kernel, because most pre-compiled kernels didn't support smp. I had a server with dual PII 233Mhz processors, the only way to use both cpu's was to compile your own kernel.

I haven't had to compile a kernel since retiring that server, and I'm glad I don't have to now.

---

### Post by K.Mandla on 2009-10-02
I compile custom kernels regularly, but that's because I use a distro that requires you to build your own kernel at installation time. If I am using something like Ubuntu or Arch, I stick with the generic one.

I have built customized kernels in Ubuntu, and you can win back a lot of speed that way -- a lot more than just 5 percent, if you know what you're doing.

---

### Post by scragar on 2009-10-02
> **K.Mandla said:**
> I compile custom kernels regularly, but that's because I use a distro that requires you to build your own kernel at installation time. If I am using something like Ubuntu or Arch, I stick with the generic one.

I have built customized kernels in Ubuntu, and you can win back a lot of speed that way -- a lot more than just 5 percent, if you know what you're doing.

As I said, really depends on how much you know what you are doing, and the more you try to get out of it the greater the risk of breaking something, without a really good understand you're not going to get much more performance out of it at all.

---

### Post by fela on 2009-10-02
One month I rolled about 120 custom kernels and our electricity bill went crazy.

Must be the extra CPU usage.

I guess it could also have been the fact that we were running electric radiators because the central heating wasn't installed yet.

You weren't supposed to see the last paragraph.

---

### Post by Shibblet on 2009-10-02
> **fela said:**
> One month I rolled about 120 custom kernels and our electricity bill went crazy.

One night, I ate corn on the cob, and had kernels the next day...

But seriously folks...

I guess the general consensus is that custom building a kernel is not really worth the time.  Does anyone make Generic but Processor specific (Oxymoron: generic but custom) Ubuntu kernels for specific processors?  Kind of like the "Funtoo" guy?

---

### Post by The Real Dave on 2009-10-02
> **Shibblet said:**
> Why would I compile a custom kernel?

Funsies? :popcorn:

---

### Post by moe_syzlak on 2009-10-22
Does anyone has any hard numbers -- benchmark -- of the performance difference between stock kernel and vendor provided kernel? I'm Googlin' but I don't see anything yet.

---

### Post by hoppipolla on 2009-10-22
Back in the day when I compiled them I used to notice a pretty large improvement, but then at the time I may have actually switched from a 2.4 to 2.6 series kernel as well, so that probably contributed more to the leap!

It doesn't take too long to do... it really depends what you want to get out of your machine as it's also time consuming to have to adapt your kernel to new hardware or rebuild it if you want newer versions o.O

---

### Post by Shibblet on 2009-10-22
> **hoppipolla said:**
> It doesn't take too long to do... it really depends what you want to get out of your machine as it's also time consuming to have to adapt your kernel to new hardware or rebuild it if you want newer versions o.O

But compiling your own "custom" kernel requires you to have drivers that are compiled for your kernel.  At least that's how I understand it.  Which means any of the Ubuntu updates are irrelevant.  

It seems to me that compiling your own kernel is limiting, because any time a new kernel source is available, or any update that you might need is release, you're back to compiling your kernel again.

Then you're playing "Maintain the OS" instead of "Use my Computer."

---

### Post by ssam on 2009-10-22
if you are short on ram (you are not),then pulling unnecessary features out of the kernel may make a difference. though not as much as it used to because most drivers are now in modules that only get loaded if the are needed. if you are working with embeded systems, then this is very important.

there ubuntu devs have looked at providing different kernel flavours for differnt CPUs, but have never found a benchmark to show that it is worth it.

there are a few things you can tweak in the kernel to trade off interactivity with throughput, eg using different schedulers (see the recent BFS stuff). but the ubuntu devs have already done some tweaking.

it still might be worth doing just to understand how it is done, and to learn a bit about how it works. maybe you should read a bit of [http://kernelnewbies.org/](http://kernelnewbies.org/)

---

### Post by hoppipolla on 2009-10-22
> **Shibblet said:**
> But compiling your own "custom" kernel requires you to have drivers that are compiled for your kernel.  At least that's how I understand it.  Which means any of the Ubuntu updates are irrelevant.  

It seems to me that compiling your own kernel is limiting, because any time a new kernel source is available, or any update that you might need is release, you're back to compiling your kernel again.

Then you're playing "Maintain the OS" instead of "Use my Computer."

yeah totally, but like I say I used to do it for years, I used to love all that stuff lol

If the OP just wants to use his computer though and isn't doing anything too demanding with it then it may not be worth his time, but there is no rule saying he has to always update to all the latest version, so a kernel he compiles could last a little while.

---

### Post by Dharmachakra on 2009-10-22
It's something that's interesting to do a few times. But, with that kind of hardware, I'd be surprised if it made any difference.

---

### Post by kk0sse54 on 2009-10-22
> **moe_syzlak said:**
> Does anyone has any hard numbers -- benchmark -- of the performance difference between stock kernel and vendor provided kernel? I'm Googlin' but I don't see anything yet.

In reference to benchmarking a random custom kernel that would be pointless, each setup is different and a custom kernel is only as good as *you* configure it. In reference to the actual quote :oops:, interesting :)

---

### Post by BuffaloX on 2009-10-22
About two years ago, I played a bit with compiling my own kernel, and gained almost 10%. (GLXgears)
This was a lot more than most others claimed was possible.

The kernel was optimized by removing unneeded/unwanted modules for my system, and compiling for my specific processor.
I also fiddled a little with some settings like SMP, but don't remember exactly what I did.

I gave it up, because I got a ton of error messages on startup, because Ubuntu tried to start stuff which I had removed the modules for.

I don't properly understand the startup procedure for Ubuntu, and found it kind of stupid, and poorly documented, so I didn't care to look further into it.

Most people report less than 2% performance increase, and estimate it to be too little gain compared to the time and effort it takes to setup and compile your own kernel.

One thing that annoyed me was that I had to include SCSI, although I have absolutely nothing SCSI, and very much dislike it.

---

### Post by markbuntu on 2009-10-22
You can get a pretty good performance boost by just weeding out all the services you don't need with Boot Up Manager and Start Up Manager. Distros tend to boot up a lot of services many people do not use or need.

Plus it is far easier and faster than compiling a custom kernel but maybe not as much fun or such a learning experience.

---

### Post by PurposeOfReason on 2009-10-22
To disable ipv6 of course. :popcorn:

---

### Post by kevdog on 2009-10-22
Here is my answer to your question:  Just do it and then see if you can answer your own question.  You learn a ton by compiling your own kernel.  If you are thinking about it -- you should just go ahead and do it.

---

### Post by kbielefe on 2009-10-23
Back in the day you had to compile your own kernel a lot if you did anything even slightly out of the mainstream.  At one point I was using win4lin and a proprietary VPN driver to log in to my workplace, both of which required kernel patches that were sometimes months behind kernel security patches, and often conflicted with each other.  You also often used to need to roll your own if you wanted to boot from a filesystem other than ext, or for features like boot splash screens, or extra security like selinux.

Nowadays, the best reason is for bragging rights.  I built a [linuxfromscratch]("http://www.linuxfromscratch.org/") system when I was a newbie partly for my own education and partly because I would explain what open source was and people would keep asking if I had actually built from source.  Now, I use Ubuntu for convenience, but I don't get freaked out if I ever have to do anything manually, because I know I've successfully done it from scratch once.  I compile snort (intrusion detection) from source, for example, and can get pretty much anything done from the command line if I have to, including repairing a broken X configuration.

As far as doing it for the sake of performance, in my experience that requires some pretty in depth knowledge not only of how your system is used, but also how you define performance.  On a webserver that does nothing but crank out web pages all day it will be different than a workstation used for editing video, which will be different than a workstation for doing normal office work.  I don't think a normal desktop user would gain much performance benefit from a completely custom kernel, especially if one of your "performance" objectives is for it to be easy to maintain.

---

