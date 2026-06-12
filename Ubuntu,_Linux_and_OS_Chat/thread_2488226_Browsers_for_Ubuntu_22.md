---
title: "Browsers for Ubuntu 22"
date: 2023-06-27
forum: Ubuntu, Linux and OS Chat
---

### Post by tinman456 on 2023-06-27
Hi folks, I decided that I would start this thread because of the problems I myself have experienced as a new Ubuntu 22 user with various browsers. None, and I mean none, of them were satisfactory. I came from a Windows environment and there also I had browser problems, specifically with Google Chrome, so much so that I ended up using Opera which performed a lot better.

So when I switched to Ubuntu I was under the impression my browser problems would go away - not so! I had so much problems with Chromium I ended up scrapping it altogether and moved to Opera. Lots of problems still, so I switched over to Firefox. This one was the most acceptable but it still kept hanging up and very often simply would stop working altogether and shut itself down.

As I continued to research this very annoying issue lo and behold I came up with an open source browser called Brave. I had never heard of it before but I was frustrated enough to give it a try - and Voila! All my browser issues went away immediately! I still can't believe it. Brave works far, far better than any of the others I have ever used in both Windows and Ubuntu and it has given me a new lease on life, so to speak.

So for any Ubuntu users like me who are experiencing browser problems - I strongly recommend - GO Brave! I'm so thankful for the folks who came up with it and did such outstanding work for our community. Hats off to them all.

---

### Post by TheFu on 2023-06-27
Exactly what are "browser problems?"  Be specific.  I don't have those ... except that Brave does something odd and doesn't allow my to log into some VPS control panels, so I'm using Firefox on those pages instead.  Brave has many other issues too, but that could just be the learning curve, since I've been using Mozilla browsers since the mid-1990s back when they had the browser AND email in the same product.

I've never understood why anyone would choose to run software from the largest internet marketing and tracking company in the world on-their-computer.  That doesn't make any sense to me.

As for 22.04 and chromium/firefox, both of those get installed as snap packages, which is often a huge problem for people who don't understand what a snap package is.  Of course, many people appreciate snaps and the mandatory constraints they inflict on users.  Takes all sorts in this world.  

Firefox can be installed without getting a snap package version, but you'll need to go out of your way to do that.  I use the Firefox ESR version from a mozilla PPA.  I suppose there are other methods, but I prefer to have my weekly patching address all patches on the system.  I truly dislike snap package updates being send whenever they are available.  I want to control when a patch is applied and I cannot do that with snaps.  I consider it a design flaw.

Running any high-risk program, like a browser without any added protection from the OS is asking for problems, IMHO.  I run firefox and brave inside firejail sandboxes.  Sometimes the sandbox is completely cut off from the file system and sometimes it is allowed to see specific portions. Which mode I choose depends on my risk mitigation needs at the time. Sometimes I'll be running 4 instances of Brave - 3 in "private" sandboxes and 1 that has limited access to the file system.  Firejail is very flexible.

Since you are new, you bring a view to Ubuntu that many of us are too far removed to consider ourselves.  Keep posting, but please provide facts.  Feelings are fine, but it is hard to help subjective problems get solved.

I do hope that brave works better for you than it does for me. It isn't bad, but I don't feel like I have the same level of control with any chromium-based browser. That's probably just my ignorance.

---

### Post by tinman456 on 2023-06-28
Hi Fu, yes your are right, of course. I did think abut including more specifics but I found the post was long enough and didn't know how much interest there would be in the topic. The problems I have always had with browsers, Windows and Linux, was hanging up the machine. They work fine when I start up but after a while they all slow to a crawl and I basically have to stop whatever it is I'm doing while the HDD starts working like a rabid dog. Until that resolves itself I'm stuck.

A fair amount of the time it never resolves and the laptop either freezes completely or reboots itself. I have noticed this behavior on other PCs/laptops that I have access too as well and it is beyond annoying. I have researched and tried all sorts of things to no avail. The comps I am referring to, although old, are quite well specked out with good Intel CPUs and 8GBs of RAM, 7200 rpm HDDs running Win10. So I had no other choice but to put up with it.

As I mentioned above, Opera was the one that worked best for me in Windows and now Brave, in Ubuntu, is the one that actually works as I always thought a browser was supposed to work. It's fast, never crashes, and basically apparently blends in perfectly with the OS. I hope this will be of more help to anyone experiencing the same problems I did.

PS I believe there is a Brave for Windows as well and I am ready to switch my wife over to that if she keeps complaining.

---

### Post by TheFu on 2023-06-28
Machine lock ups tend to be due to other issues, not a specific single program, unless that program is eating all the resources of the system.  Tuning your setup may be all that is needed.  For example, if you don't have 4GB of swap, then an 8GB system may be limited for a modern browser. Ubuntu will kill a process that uses more RAM than is available.  This is a mix of real and virtual memory.  Not having enough swap would be the first place I checked.

**free -hm**

will show how memory is being used, including swap.

Of course, you can use lighter browsers, don't open as many tabs, and don't use them for watching videos as another way to reduce the resources a browser sucks.

I have systems with 2GB, 4GB, 8GB, 16GB and 32GB of RAM. On the systems with less than 16GB, having 4.1GB swap is important.  Having "some" swap matters for the kernel on systems with more RAM. It is due to the way the kernel works when there's some swap vs zero swap.

Also, using an SSD rather than a HDD would make a huge improvement in performance.

The easiest way to share system HW and configuration overview is with the **inxi -bz** command.  For example, my desktop:
```
$ inxi -bz
System:
  Kernel: 5.15.0-75-generic x86_64 bits: 64 Desktop: N/A
    Distro: Linux Mint 21.1 Vera
Machine:
  Type: Kvm System: QEMU product: Standard PC (i440FX + PIIX, 1996)
    v: pc-i440fx-focal serial: <superuser required>
  Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: 1.13.0-1ubuntu1.1
    date: 04/01/2014
CPU:
  Info: 2x 1-core AMD EPYC-Rome [SMP] speed (MHz): avg: 4200
Graphics:
  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel
  Display: server: X.Org v: 1.20.13 driver: X: loaded: N/A
    unloaded: fbdev,modesetting,vesa gpu: qxl note:  X driver n/a
    resolution: 1920x1200~60Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 22.2.5-0ubuntu0.1~22.04.3
Network:
  Device-1: Intel 82371AB/EB/MB PIIX4 ACPI type: network bridge
    driver: piix4_smbus
  Device-2: Red Hat Virtio network driver: virtio-pci
Drives:
  Local Storage: total: raw: 40 GiB usable: 76.16 GiB used: 17.66 GiB (23.2%)
Info:
  Processes: 240 **Uptime: 11d 1h 35m** **Memory: 5.74 GiB** used: 4.86 GiB (84.7%)
  Shell: Bash inxi: 3.3.13
```
As you can see, it has been running over 11 days. It is extremely stable with 2 cores and 6GB RAM.  I generally start desktops with 4GB of RAM, then add more if necessary.

---

### Post by tinman456 on 2023-06-28
Hi Fu, yes your are right, of course. I did think abut including more specifics but I found the post was long enough and didn't know how much interest there would be in the topic. The problems I have always had with browsers, Windows and Linux, was hanging up the machine. They work fine when I start up but after a while they all slow to a crawl and I basically have to stop whatever it is I'm doing while the HDD starts working like a rabid dog. Until that resolves itself I'm stuck.

A fair amount of the time it never resolves and the laptop either freezes completely or reboots itself. I have noticed this behavior on other PCs/laptops that I have access too as well and it is beyond annoying. I have researched and tried all sorts of things to no avail. The comps I am referring to, although old, are quite well specked out with good Intel CPUs and 8GBs of RAM, 7200 rpm HDDs running Win10. So I had no other choice but to put up with it.

As I mentioned above, Opera was the one that worked best for me in Windows and now Brave, in Ubuntu, is the one that actually works as I always thought a browser was supposed to work. It's fast, never crashes, and basically apparently blends in perfectly with the OS. I hope this will be of more help to anyone experiencing the same problems I did.

PS I believe there is a Brave for Windows as well and I am ready to switch my wife over to that if she keeps complaining.

---

### Post by tinman456 on 2023-06-28
Yes, I understand that Fu and yes I do think the OS management of the swap file had a lot to do with it. But I had played around enough with those settings until I got it working the best I think it was capable of. In spite of what you said though I really do believe that it was Chrome itself causing the problem because when I switched to Opera it became a lot better - although still not good. It was continuous esoteric problems like that which got me fed up with Windows and was the main reason why I decided to switch.

So far, and now with Brave as my browser, I am just about totally satisfied with the performance of my laptop. I have two small Windows utility programs that I always liked and they run just as good on Wine but I use native Linux programs for just about everything else - video editing, image manipulation, downloading torrents, etc. etc

The only 'problem' I still have to sort out is how to get my DVR connected cameras to work. And I can tell you, that's a biggie...but I'm hopeful.

Thanks for you input and advice, I much appreciate the time you took to reply to me.

---

### Post by TheFu on 2023-06-28
You might want to see who owns Opera browser. Be certain you understand the ramifications of that ownership.  [https://en.wikipedia.org/wiki/Opera_(company)](https://en.wikipedia.org/wiki/Opera_(company)) The founders where in Norway - great.  They sold the company to some others, however. Just something to consider. Please be certain you are comfortable.

---

### Post by tinman456 on 2023-06-28
Good advice but I'm happy with Brave for now. Thanks.

---

### Post by TheFu on 2023-06-28
> **tinman456 said:**
> Good advice but I'm happy with Brave for now. Thanks.

A quick look at Brave and my interaction with their support people seems like they are a company trying to do good.  

I use brave as my "high-risk" browser. I used Chromium for this need previously, but the change to snap packaging as the only way to get Chromium ran me off. Actually, it pushed me away from Ubuntu desktops.  Snaps shouldn't be mandated or even pre-installed. They need to be 100% optional.  

Lots of people I respect have been happy with Brave, so I felt trying it was necessary. All was great, until it wasn't and the issue wasn't huge, just a minor hassle when I was doing something on a new-to-me website.  OTOH, all websites have some issue with each browser. That's pretty common, especially if you are doing privacy + security things to the browser settings and the websites don't plan for those things to be blocked.

---

### Post by DuckHook on 2023-06-30
A bit late to this thread, but my tuppence for what it's worth:

Brave is one of my go&#8209;to browsers and I have been recommending it to most of my friends and family. Brave's non&#8209;tracking philosophy sits well with me and it's backed up by this:

[https://coveryourtracks.eff.org/](https://coveryourtracks.eff.org/)

Brave scored well. Frankly, it scored awesomely well compared to browsers like Chromium/Chrome, Edge, Safari, and the mainstream commercial ones. The only browsers that scored better were TOR&#8209;Browser and my specially hardened Firefox. TOR-Browser is no surprise, but Firefox probably scored so well only because I have it hardened ten ways to Sunday. Brave scored very well right out of the box.

I didn't test Vivaldi, Opera or other lesser known offerings. You (tinman456) may want to put them to the test for a comparison.

I don't want to hijack the thread by talking about _P_rivacy/_S_ecurity/_A_nonymity when you are concerned about basic functionality, but they are considerations.

BTW, like TheFu, I too have found that Brave chokes on some sites. I'm willing to live with that (and just use another browser for those sites) because Brave's PSA score is so good.

---

### Post by Bashing-om on 2023-06-30
2
> 
A bit late to this thread, but my tuppence for what it's worth:


Like many I too took exception to forced snap packages. As my preferred browser was chromium - in seeking an alternative I found slimjet.
[https://www.slimjet.com/](https://www.slimjet.com/)

Besides the fact that it is 3rd party, I find no fault with it - other than the maintenance of codecs. Works very well for my use case.

[INDENT]we do have choice
[/INDENT]

---

### Post by SeijiSensei on 2023-07-01
As far as I know, Brave is Chromium with some added features. I regularly use Firefox, Chrome, and Chromium on my Linux machines and never have problems. 

How many open tabs do you have? Each tab consumes memory even when you're not looking at it. If you have lots of open tabs, try limiting them to fewer than ten and see if that helps.

Try opening a console along side the Firefox browser and run the command "top". It will show your memory usage in real-time. If you have lots of "Isolated Web Content" entries, those are the tabs.

---

### Post by DuckHook on 2023-07-01
> **SeijiSensei said:**
> As far as I know, Brave is Chromium with some added features.

Very true. But it's those very added features that make all the difference in the world. A comparison of tracking risk and browser fingerprinting susceptibility between Brave and Chrome/Chromium is very instructive (and more than a little scary). The EFF site that I linked to above is a useful and eye&#8209;opening tool.

Caveat: I believe this has been mentioned, but it doesn't hurt to reiterate: the added hardening that Brave implements out of the box does come at a cost. I've visited several sites that don't display properly in Brave, but work seamlessly in another browser. I will also sometimes (not often) run into situations where Brave freezes on a download where other browsers have no problems. Despite these shortcomings, I still love Brave for its privacy/security/anonymity commitment. Not a lot of offerings out there these days whose primary goal aligns with my own needs rather than trying to monetize me.

---

