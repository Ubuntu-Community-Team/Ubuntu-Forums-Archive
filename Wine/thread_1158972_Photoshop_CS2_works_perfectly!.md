---
title: "Photoshop CS2 works perfectly!"
date: 2009-05-14
forum: Wine
---

### Post by fanis on 2009-05-14
Ubuntu 9.04 x86_64, Wine 1.0.1(the one from the repos)

Well, one less reason to boot windows even once in a while! 

Installed through wine, didn't need to import anything from a windows installation! 

first you need to download winetricks by typing
```
wget http://www.kegel.com/wine/winetricks

```

I copied winetricks to ~/.wine, but it doesn't matter whatsoever. The next step is to install the fonts that photoshop uses, through winetricks. cd to to folder that you downloaded and do

```

chmod +x winetricks
sh winetricks corefonts vcrun6 fontfix tahoma liberation

```

At this point all you have to do is mount the photoshop cd (or iso) and voila! Install it exactly as you would on windows. After somewhat extensive testing, the only thing that doesn't seem to work is the adobe updater!

---

### Post by alex.rayu on 2009-05-14
Photoshop CS2 has been working perfectly under Wine for more than a year now. If it weren't I would never use Ubuntu =)

---

### Post by fanis on 2009-05-14
> **alex.rayu said:**
> Photoshop CS2 has been working perfectly under Wine for more than a year now. If it weren't I would never use Ubuntu =)

Yeah, I know, worked for me as well in 8.04 and 8.1, but I had to import windows registy keys (and thus have a local windows installation) among others. Also, the fonts were not nearly as good, plus I encountered a lot of bugs. What excites me is that I made the installation through wine and that's it!

---

### Post by AndThenWhat on 2009-05-14
It works perfectly for me out of the box on Wine 1.1.21, of course I am using the 32-bit architecture Ubuntu.

---

### Post by lightstream on 2009-05-14
Getting CS2 working as good as possible was one of Wine's priorities before they went to version 1.0.

if you have the money/resourcefulness to get a copy of CS2, you'd surely not have a problem acquiring Windows in a similar fashion.

So what I don't understand is why someone who uses CS2 regularly would want to use Linux?

---

### Post by fanis on 2009-05-14
> **lightstream said:**
> Getting CS2 working as good as possible was one of Wine's priorities before they went to version 1.0.

if you have the money/resourcefulness to get a copy of CS2, you'd surely not have a problem acquiring Windows in a similar fashion.

So what I don't understand is why someone who uses CS2 regularly would want to use Linux?

I'd choose ubuntu linux over any version of windows without a second thought.

Linux is faster, more secure, easier to maintain, GDM beats the windows interface by far, has so many great compilers and development tools, has great user management, file/directory permission, and has a shell that is powerful and not stupid. 

I mostly work on django and rails web apps, and belive me, it's totally annoying having to reboot to windows to make some changes to a couple of images you use in your css. But even if I was a digital photographer, I'd rather not have to worry about viruses trojans etc. I can see why someone would use a OSX over linux(I'm surely not that someone), but not windows. Windows is only for gaming. I got a PS3 for that, so windows can burn. ;)

---

### Post by lightstream on 2009-05-14
Ah Ok. Where I work there are a several Apple lovers, and at least one is very enamoured with Windows 7. If that turned out to be any good would you consider switching to it? I'm just curious! :mrgreen:

Personally it's Microsoft themselves which I have a disliking for - I think they are a rotten business. Their business model is based on disempowering their customers, rather than empowering them. There are plenty of businesses which empower their customers, but Microsoft is certainly not one! I don't really think Apple are much better either.

So from my point of view, how crap or insecure windows is is almost irrelevant, it's about freedom and sharing knowledge, man :guitar:

---

### Post by fanis on 2009-05-15
> **lightstream said:**
> Ah Ok. Where I work there are a several Apple lovers, and at least one is very enamoured with Windows 7. If that turned out to be any good would you consider switching to it? I'm just curious! :mrgreen:

Personally it's Microsoft themselves which I have a disliking for - I think they are a rotten business. Their business model is based on disempowering their customers, rather than empowering them. There are plenty of businesses which empower their customers, but Microsoft is certainly not one! I don't really think Apple are much better either.

So from my point of view, how crap or insecure windows is is almost irrelevant, it's about freedom and sharing knowledge, man :guitar:

I can understand that for some people windows is the only way to go(especially old people :D). Windows 7 seem decent, but I really don't care. I wouldn't consider switching to MS windows, unless they considered switching to a unix based system! I can do everything I need with linux, and with the improvements we see every day to wine and virtual box, vmware etc I see even less use for them(windows).

---

### Post by alex.rayu on 2009-05-15
I love apple. But an not sure if I would use it for real. I like Windows XP. I hate Vista for it's glass and complexity, and I hate win 7 a little less then Vista because they still have the effects I dislike but is less complex. My general impression is that win 7 will break give MS a new good start.

---

