---
title: "LMMS with VST from KX-Studio Repos on 64-bit UbuntuStudio"
date: 2015-01-11
forum: Ubuntu Studio
---

### Post by marseille2 on 2015-01-11
I want to install LMMS with VST support on 14.04 (64-bit), but I hesitated when I saw the KX-Studio repo provided a package for i386 machines. So my question is ... Will I get better performance by sticking with the 1.0 version in the UbuntuStudio package manager (and forego the VSTs), or is the newer version from KX-studio worth it for the VSTs?

---

### Post by jejeman on 2015-01-12
Why instal i386 package on 64-bit OS? Try to find 64-bit package.

---

### Post by marseille2 on 2015-01-12
In the package manager, I have two options. Stick with what I have installed (64-bit ubunstudio package), or choose the i386 version from the KX repo. The latter option made me worry that I'd break something. But now that a day has passed, and the DSSI-VST situation is looking grim ... I'm wondering if VSTs are worth the trouble. I have to say... Trusty is one of the best out-of-the-box UbuntuStudio LTS versions ever, so I don't want to break it:D

---

### Post by luctor on 2015-01-19
there's a 64 version in de kx repo ... 
[https://launchpad.net/~kxstudio-debian/+archive/ubuntu/apps/+files/lmms_1.1.0-1kxstudio1_amd64.deb](https://launchpad.net/~kxstudio-debian/+archive/ubuntu/apps/+files/lmms_1.1.0-1kxstudio1_amd64.deb)
maybe it has some 32 bit dependencies because of the vst plugins that actually run on wine
vst are working _ok_ in lmms, not perfect, still have some crashes now and then

---

### Post by marseille2 on 2015-01-20
Thanks Luctor! 

Do you happen to know which version of wine should be installed? I'm not so great with winehq anymore ... PlayLinux threw me off (when I started using it back in 12.04), and I don't know where to begin anymore.

---

### Post by luctor on 2015-02-02
just install lmms, the rest will be installed automatic.

---

### Post by marseille2 on 2015-02-02
Ok this is great news! Thank-you:):guitar:

---

### Post by marseille2 on 2015-02-27
I finally got this working, and installed LMMS 1.1.1 with VST from the KXSTudio (NOW) repo. Synaptic didn't show it via search results...  I *think* it turned up under "new in repository." So that's the good news.

The bad part is that there seems to be a known bug with the new package that affects VSTs... So far, I haven't got any to work. The vst's GUI will show up under the FX window in an LMMS instrument, but functionally ... they CRASH on load!

---

### Post by luctor on 2015-03-16
> **marseille2 said:**
> I finally got this working, and installed LMMS 1.1.1 with VST from the KXSTudio (NOW) repo. Synaptic didn't show it via search results...  I *think* it turned up under "new in repository." So that's the good news.

The bad part is that there seems to be a known bug with the new package that affects VSTs... So far, I haven't got any to work. The vst's GUI will show up under the FX window in an LMMS instrument, but functionally ... they CRASH on load!

Which are you trying to load?

---

### Post by marseille2 on 2015-03-16
I tried to load some of my favorites from my own stash, but I need to cross-reference that with the approved list on LMMS. I've been busy in Ardour, so I haven't gotten around to it yet. But it's on my to-do list:)

---

