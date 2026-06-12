---
title: "[SOLVED] How to start with a Linux-based Bible program?"
date: 2008-02-25
forum: Ubuntu Christian Edition
---

### Post by incen on 2008-02-25
I am new to Linux and so to e-Sword. I installed Xubuntu on my laptop two weeks ago and knew/installed e-Sword one week ago. Just now, I was so happy to see that there IS a bible-study program in Linux! However, I don't really know how to start. I read about Gnomesword. Is this the one I need? I also read about e-Sword. It seems it's kinda complicated to make it work.

Well... regardless to all this technical problem. I have sort of Christian's question. What's the Bible version installed by default with Gnomesword? I just installed it with
```
sudo aptitude install gnomesword
```

And then I opened it with (in Xubuntu)
Applications -> Accessories -> GnomeSword2 Bible Guide
It just gave me a lot of Arabic characters...
Is this AraSVC installed by default? Can I remove it?

---

### Post by themusicwave on 2008-02-25
I just re-installed gnome sword and I see what you mean.

It appears the Arabic package is tied to gonmoe sword and can;t be removed.

What you need is the English pack install it with:

sudo apt-get install sword-language-pack-en

There are lots of other languages, check out synaptic to see them all.

It's under System -> Administration -> Synaptic Package Manager

I was unable to remove the Arabic module.

The English versions are KJV and WEB.

I think there is a way to get lots of other versions.  Try googling about it.

Hope that helps,

Jon

---

### Post by incen on 2008-02-25
Hi, thanks for reply!
I sucessfully got the English package and installed ASV module in already. I downloaded it from Sword site: [http://www.crosswire.org/sword/index.jsp](http://www.crosswire.org/sword/index.jsp)

Unzip the file, and put the modules under /usr/share/sword. In case someone may need it. :p

---

