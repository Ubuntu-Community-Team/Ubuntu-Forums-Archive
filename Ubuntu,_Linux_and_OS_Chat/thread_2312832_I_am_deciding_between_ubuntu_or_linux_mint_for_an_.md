---
title: "I am deciding between ubuntu or linux mint for an old laptop"
date: 2016-02-07
forum: Ubuntu, Linux and OS Chat
---

### Post by patrick112 on 2016-02-07
Hi All!

I have a core 2 duo 2.0 GHZ - 2GB Ram Laptop.

I have a few questions.

Will ubuntu or Linux Mint improve overall speed? Will it improve battery life?

I want to improve the performance, and life of battery. Will linux do this?

---

### Post by ajgreeny on 2016-02-07
Speed it up compared to what; Windows?

That will depend on the hardware specs in more detail that we have, particularly the graphic card, but either way, I think you may do better with a version of *Ubuntu or Mint that uses a lower resource hungry DE, eg, Xubuntu (uses xfce) or Mint with mate DE.

Both unity in the default Ubuntu and cinnamon in Mint need good resources to run fast but xfcfe and mate need lower specs to run well.

I doubt that battery life will be improved; that has never been an advantage of Linux in my opinion, though others may disagree.

---

### Post by monkeybrain20122 on 2016-02-07
Unity doesn't require a super computer to run. When people say it is resource demanding it is like based on maybe 10 year old hardware with <= 1 G of ram. The reason why people get somewhat sluggish performance in Unity sometimes  IMO more often has to do with graphic card incompatibility than resource consumption per se. 2G is pretty enough to run Unity with decent performance in my experience. I haven't used Mint but my bet would be that 2G would be sufficient as well. All Linux DE are light basically comparing to Windows. When they say such and such is "bloated" it is just a matter of comparison, anything modern looking would be 'bloated" next to LXDE or Openbox.

---

### Post by montag dp on 2016-02-07
For improving battery life, I always recommend TLP:
[URL="http://linrunner.de/en/tlp/tlp.html"]
http://linrunner.de/en/tlp/tlp.html[/URL]

It makes a big difference on my laptop.  Battery life is on par with Windows 7/10 on the same machine, and the idle wattage is actually lower.

As far as speed goes, I wouldn't be surprised if Ubuntu/Mint is faster than Windows 7/10.  That's been my experience, anyway.  If you use something lightweight like Xfce, I'm pretty confident you will see an improvement.

---

### Post by kansasnoob on 2016-02-07
Ubuntu' s default Unity DE and Kubuntu's KDE DE are IMHO the most resource hungry of the pack. Both GNOME Shell and Cinnamon are also a bit resource hungry although less so than KDE or Unity.

Lubuntu (LXDE), Xubuntu (Xfce), GNOME Flashback w/Metacity, and MATE w/Marco are all good lighter weight alternatives. I've never run any actual benchmark tests but in real world use I find the four almost indistinguishable in overall performance.

I think Mint offers MATE, LXDE and Xfce spins, and Peppermint has a rather hybrid mix of their own.

---

### Post by stalkingwolf on 2016-02-08
i have a couple different computers with these specs  i run mint 13 mate on all of them.  mate 17 seems to work as well

---

### Post by vasa1 on 2016-02-08
> **monkeybrain20122 said:**
> Unity doesn't require a super computer to run. When people say it is resource demanding it is like based on maybe 10 year old hardware with <= 1 G of ram. The reason why people get somewhat sluggish performance in Unity sometimes  IMO more often has to do with graphic card incompatibility than resource consumption per se. 2G is pretty enough to run Unity with decent performance in my experience. I haven't used Mint but my bet would be that 2G would be sufficient as well. All Linux DE are light basically comparing to Windows. When they say such and such is "bloated" it is just a matter of comparison, anything modern looking would be 'bloated" next to LXDE or Openbox.
Nobody alleges that Unity needs a super computer ;)

OTOH, it isn't a crime to develop a DE that takes advantage of modern technology.

But I think Unity does benefit if a GPU is present; without a GPU, the CPU has to do the heavy lifting to accommodate the eye candy. IIRC, Cinnamon is similarly placed.

---

### Post by buzzingrobot on 2016-02-08
For typical use, impressions of speed are determined by display responsiveness.  We don't know the OP's video card, though.

If the video is old/weak, it may not be able to run Cinnamon or Unity correctly.  Cinnamon, in that case, will use software rendering, which looks pretty poor, is slow, and comes with an oversized notice that you are using software rendering and you really ought to do something about it.  I'm not sure if Unity will fall back to software rendering. (To the OP:  "software rendering" means rendering of the graphic elements on screen is pushed off to the CPU because the GPU is inadequate. Besides gobbling up CPU cycles, it will never look very good.)

Gnome 2 was never positioned as an undemanding environment, and MATE, its fork, on my systems has always paired up against Unity/Cinnamon/Gnome-Shell in resource use. 

Lubuntu seems a likely candidate for that hardware if the OP is interested in performance.

I see lots of complaints about battery life on Linux, and don't recall seeing anyone praising it.

---

### Post by pfeiffep on 2016-02-08
> **patrick112 said:**
> Hi All!

I have a core 2 duo 2.0 GHZ - 2GB Ram Laptop.

I have a few questions.

Will ubuntu or Linux Mint improve overall speed? Will it improve battery life?

I want to improve the performance, and life of battery. Will linux do this?Without benefit of your specs here's my situation:
 I've found that using Ubuntu with gnome flashback installed provides a really good experience on my Dell laptop which seemed a bit sluggish using 3d unity. 
Concerning battery life - I found that installing the [Intel driver support]("http://www.omgubuntu.co.uk/2014/05/intel-linux-graphics-driver-installer-1-0-5") provides the ability to automatically set screen brightness which has a direct impact on battery life.

---

### Post by grahammechanical on 2016-02-08
Software cannot make up for the deficiencies of hardware. Over-clock a CPU and it will be like you have a more powerful computer but the CPU will use more power and on a laptop that will reduce battery life. There may also be issues with over heating. I give this as an example to show that the really best way to get a more powerful computer is to upgrade the hardware.

As regards comparing Ubuntu with Linux Mint, they both use a Linux kernel. And it is the Linux kernel that works with the hardware. If the CPU is designed to go faster or slower depending on the operational load, then it would be the kernel that needs to engage with that functionality. So, when it comes to the functioning of the kernel there is a kind of equality between Linux distributions.

And then there is the matter of the video adapter. Is it able to increase or decrease its speed of operation according to load? The faster the GPU goes the more power is used up. If the GPU is not designed to decrease speed according to load, then there is nothing that software can do to change that. Especially as the manufacturers of video adapters are very secretive about their hardware. They reveal very little to Linux developers.

Regards.

---

### Post by poorguy on 2016-02-08
Here is a Dell Desktop from 2006 that is running Ubuntu Mate and it is fast as lighting.
People tell me all of the time that it won't work and here is my proof that it does.
Either one Ubuntu Mate 14.04 / Linux Mint 17.x Mate or Xfce will run like lighting and I use both and no complaints with either.

[COLOR=#000000]Results obtained using ( inxi -Fx ) . [/COLOR]

[COLOR=#000000]System: Host: DELL-PRECISION-380 Kernel: 3.16.0-59-generic i686 (32 bit, gcc: 4.8.2) [/COLOR]
[COLOR=#000000]Desktop: MATE 1.8.2 Distro: Ubuntu 14.04 trusty [/COLOR]
[COLOR=#000000]Machine: System: Dell product: Precision WorkStation 380 [/COLOR]
[COLOR=#000000]Mobo: Dell model: 0CJ774 Bios: Dell version: A07 date: 04/18/2006 [/COLOR]
[COLOR=#000000]CPU: Dual core Intel Pentium D CPU (-MCP-) cache: 1024 KB flags: (lm nx pae sse sse2 sse3) bmips: 11172.2 [/COLOR]
[COLOR=#000000]Clock Speeds: 1: 2793.062 MHz 2: 2793.062 MHz [/COLOR]
[COLOR=#000000]Graphics: Card: NVIDIA NV44 [Quadro NVS 285] bus-ID: 01:00.0 [/COLOR]
[COLOR=#000000]X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1024x768@60.0hz [/COLOR]
[COLOR=#000000]GLX Renderer: Quadro NVS 285/PCIe/SSE2 GLX Version: 2.1.2 NVIDIA 304.131 Direct Rendering: Yes [/COLOR]
[COLOR=#000000]Audio: Card-1: Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 [/COLOR]
[COLOR=#000000]Card-2: Creative Labs SB X-Fi driver: snd_ctxfi port: dce0 bus-ID: 05:02.0 [/COLOR]

---

### Post by yoshii on 2016-02-08
I think you can't go wrong with Xubuntu or something similar.  
If you wanted to compare, you could dual boot with WattOS, which is supposedly specifically designed to use low power.  
If you do install Lubuntu, the nice thing is that you can still install the Ubuntu Software Center to get access to conventional programs.  
Personally, I like Xubuntu a bit better than Lubuntu in terms of features.  My laptop has similar specs.  

Something you can also do to reduce battery usage is to disable file last access logging.  It's accomplished by editing fstab.  (noatime).  
With last access loggin enabled, every time I file is accessed, that time is written which makes file activities a lot busier than they need to be.  
Programs still function just fine with it turned off.  You still have the creation and modification times logged, so there's really no harm.

---

### Post by poorguy on 2016-02-08
Haven't heard of WattOS until now.
Looks as though it would run on anything that was super low power.

---

### Post by pfeiffep on 2016-02-09
> **patrick112 said:**
> Hi All!
I have a core 2 duo 2.0 GHZ - 2GB Ram Laptop.
I have a few questions.
Will ubuntu or Linux Mint improve overall speed? _**Will it improve battery life**_?
I want to improve the performance, and life of battery. Will linux do this?There are add ons that might help increase battery life ... I use [CPU Frequency Scaling Indicator]("http://askubuntu.com/questions/455687/how-to-run-cpufreqd-in-ubuntu-14-04") on my laptop and have it set for ondemand. 
Decreasing the brightness and processor speed will increase battery life.

---

### Post by monkeybrain20122 on 2016-02-09
> **vasa1 said:**
> 
But I think Unity does benefit if a GPU is present; without a GPU, the CPU has to do the heavy lifting to accommodate the eye candy. IIRC, Cinnamon is similarly placed.

I think most eye candies come from compiz rather than unity per se . I have run Ubuntu with full compiz on machines from XP era and it was very fast. My first experience with Ubuntu was on a handed me down small Dell with 2 G of ram with Ubuntu 10.04 and full compiz gory, it was as fast or faster than XP which it came with, there was no GPU.

---

### Post by night_sky2 on 2016-02-09
Linux Mint 17.3 Xfce would be a great fit for your laptop. This is my honest opinion. The Xfce desktop environment is quite light on ressources. There is also Xubuntu 14.04 but Mint OS I find more polished, beautully designed and it's packaged with media codecs, java and the most useful apps. It's **very** stable, as the Mint team choose not to update the Kernel and Xorg by default.

---

### Post by Nuno_Abreu on 2016-02-10
I'm pretty sure it'd run well on anything except KDE and/or Unity - even though I'm also sure it would not run so slow on these either.
Anyway, XFCE and LXDE are fast enough and full-featured (XFCE is my personal favourite and it runs well on a 9 year old computer with 1 GB of RAM).

If you're afraid of using a complete Desktop Environment, try a window manager with a panel or dock to suit your needs - in my experience, it's way faster and a lot more responsive: there's Openbox and Fluxbox as good examples.

I'd go for Mint, especially for XFCE - it's super customizable (a lot more than Unity for sure) and your RAM will not be bloated. If you like being kernel updated, go for Xubuntu!

[B]P.S.: Is it just me or I find Cinnamon heavy like a rock? It's a pure snail!
Also, did anyone experience any lag on MDM (default Mint Desktop Manager) image transitions?[/B]

---

### Post by night_sky2 on 2016-02-10
> **Nuno_Abreu said:**
> **P.S.: Is it just me or I find Cinnamon heavy like a rock? It's a pure snail!**
Not in my experience. Cinnamon has been greatly improved in the last 2 years. For instance, Cinnamon 2.4 has fixed about 30 memory leaks. It's much more smoother than it used to be. Of course it's meant as modern DE, and I would not necesserely recommend it for older hardware. It's still pretty good though and lighter than Unity or Gnome 3.

Xfce and MATE are the way to go if you are dealing with hardware more than 5 years old.

---

### Post by kurt18947 on 2016-02-10
If you have some 8 GB. flash drives and are not familiar with the various 'flavors' of Ubuntu, I'd recommend creating a few live USB drives and try them on your machine. See which one feels better. I have a similar machine only with 4 GB. of RAM and have LXLE 14.04.3 and XFCE 16.04 installed on it. They're both similar in speed and responsiveness on that hardware.

---

### Post by furtom on 2016-02-10
I have a similar laptop to you, though we don't know the particulars....

I find Both unity and cinnamon to be too much. They both run and I could live with them, but why should I when Xubuntu or Lubuntu are available? Lubuntu will snap like a new computer. So if you don't mind that DE, I'd go there. Xubuntu also runs well and is a bit more polished.

I've also had success with MATE, and still run it on occasion, but it's not as lean as the two above, esp. Lubuntu.

---

### Post by Nuno_Abreu on 2016-02-11
> **night_sky2 said:**
> Not in my experience. Cinnamon has been greatly improved in the last 2 years. For instance, Cinnamon 2.4 has fixed about 30 memory leaks. It's much more smoother than it used to be. Of course it's meant as modern DE, and I would not necesserely recommend it for older hardware. It's still pretty good though and lighter than Unity or Gnome 3.

Xfce and MATE are the way to go if you are dealing with hardware more than 5 years old.
I'll try the DE sometime - last time I got on my hands on it was like 1 year ago.
Those memory leaks make sense, since it took a lot of my short RAM away once I started it.

Thank you for your info!

---

