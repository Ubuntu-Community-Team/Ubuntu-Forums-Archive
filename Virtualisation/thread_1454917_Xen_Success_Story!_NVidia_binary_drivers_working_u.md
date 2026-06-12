---
title: "Xen Success Story! NVidia binary drivers working under xen in Ubuntu 9.10"
date: 2010-04-15
forum: Virtualisation
---

### Post by gypsyjiver on 2010-04-15
Greetings all,

I just thought I'd share a success story with you. Quite a good thing to have as my first post, eh?

Anyway, I have a new MSI CR500 laptop (the Japanese version) with an NVidia 8200M G graphics card. Almost everything was installed automagically, with the exceptions of the NVidia driver and the wifi card driver (RaLink rt3090). I managed to get those two working without too much hassle, and then I decided that it would be a great idea to install xen.

So I installed the ubuntu-xen-desktop package with Synaptic and let it do the rest. But when I rebooted into my new kernel, neither my NVidia card nor my wifi connection worked any more!

I looked on the internet to see if anyone had the same problem as me, and I saw a few solutions... unfortunately, they all talked about patching the kernel, compiling it yourself, manually editing makefiles... all far too much for a relative newbie like me. But after fiddling with my wifi drivers in synaptic for a bit, I found the solution. I just installed the kernel headers for my new kernel (plus the build-essential package), and Ubuntu did all the rest for me. I think it must have actually compiled the modules on the fly. Anyway, I just rebooted and everything was working perfectly. Marvellous. Thank you Ubuntu team!

So if you have the same problem as me, try this:
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```Let me know if it works for you too!

---

### Post by brendanqoki on 2011-01-08
> ** said:**
> It works for me, Many thanks to your [[COLOR=#000000]sharing[/COLOR]](http://www.purplers.net/sr/public-speaking/the-best-political-speech-of-the-last-century.html)!

---

