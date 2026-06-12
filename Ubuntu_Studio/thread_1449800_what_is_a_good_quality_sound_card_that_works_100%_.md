---
title: "what is a good quality sound card that works 100% with linux?"
date: 2010-04-08
forum: Ubuntu Studio
---

### Post by urlwolf on 2010-04-08
Hi,

I gave up trying to get my tascam US122L to work (usb 2.0 and linux seems not to get along).

what is a good quality sound card that works 100% with linux? I have excellent amp and speakers ( dali IKON 6), onboard sound on my dell pc doesn't cut it...

I don't mind something older off ebay, as I have to discount the tascam brick that bought from the total price I spend on plain sound quality...

---

### Post by AutoStatic on 2010-04-08
Edirol UA-25EX. USB1 though but a very decent card if you ask me.

Dali Ikon's, those must sound awesome! I've just set up my hifi stack, got myself some Dali's also.

Best,

Jeremy

---

### Post by cchhrriiss121212 on 2010-04-08
Are you limited to using USB? There are some good pci/firewire cards out there too.

---

### Post by cascade9 on 2010-04-08
The ALSA page has a huge list of supported cards (by manufacturer), so if you are wondering about a specific card is a good place to go- 

[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

---

### Post by usndmac on 2010-04-08
I would second the firewire option. Though, I'd have to say that getting my Audiofire12's and FP10's working wasn't without effort. Once it worked, though, it was great.

Has all the new/old firewire stack stuff worked out yet?

My US122 always worked great in windoze, never actually attempted it in Ubuntu.

---

### Post by urlwolf on 2010-04-08
> **cchhrriiss121212 said:**
> Are you limited to using USB? There are some good pci/firewire cards out there too.

pci/firewire is an option. this is a dell dimension 755:
[http://reviews.cnet.com/desktops/dell-optiplex-755-small/4505-3118_7-32601594.html](http://reviews.cnet.com/desktops/dell-optiplex-755-small/4505-3118_7-32601594.html)

maybe mini-pci?
I'm looking at asus cards right now. they seem to have drivers for linux (!).

Ideally, I'd like to pay for good DA converters, and nothing accessory (inputs, compressors, etc)

---

### Post by urlwolf on 2010-04-08
> **cascade9 said:**
> The ALSA page has a huge list of supported cards (by manufacturer), so if you are wondering about a specific card is a good place to go- 

[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
hmm, but it's still hard to know if the info is up-to-date... the US122L looks like it could work, but the page was last changed in 2007 :)

---

### Post by cascade9 on 2010-04-08
The ASUS cards tend to have problems wth the front input jacks, and some of the cards need reallly new really kernels or ALSA versions to work.

Apart from that, they are nice cards. 

MAudio is prety good as well, but I've seen some 'professional' audio people say they suck.

Edit-
> **urlwolf said:**
> hmm, but it's still hard to know if the info is up-to-date... the US122L looks like it could work, but the page was last changed in 2007 :)

As far as I know, once the kernel or ALSA supports something, its fine from then on.

---

### Post by cchhrriiss121212 on 2010-04-08
> I'm looking at asus cards right now. they seem to have drivers for linux (!).
As you are in the studio forum, I'm guessing you want to use the card to record audio as well as send it to those fancy speakers?
In which case the asus cards might not be a good choice as the inputs don't seem to work so good:
[http://alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://alsa-project.org/main/index.php/Matrix:Vendor-Asus)

I'm using an m-audio card which work nicely with alsa, the 24/96 might be what you are looking for.

---

### Post by urlwolf on 2010-04-08
[http://forums.techgage.com/showthread.php?t=5672](http://forums.techgage.com/showthread.php?t=5672)
[http://www.guru3d.com/article/asus-xonar-essence-stx-review/](http://www.guru3d.com/article/asus-xonar-essence-stx-review/)
this looks killer!

---

### Post by markbuntu on 2010-04-10
If you have a Tascam US122 you need a firmware loader:

[http://ubuntuforums.org/showpost.php?p=6272809](http://ubuntuforums.org/showpost.php?p=6272809)

This is an old link but you might be able to get something out of it yet.

---

### Post by urlwolf on 2010-04-10
Thanks, I wonder if the US122L needs the firmware loader? Never heard of it before...

---

### Post by AutoStatic on 2010-04-11
If you want a good quality sound card that works 100% with Linux than forget about the Tascam US122L.

---

### Post by JC Cheloven on 2010-04-12
[http://ubuntuforums.org/showthread.php?t=1324473&page=2](http://ubuntuforums.org/showthread.php?t=1324473&page=2)
see last post (of mine)

---

### Post by cub on 2010-04-13
> **AutoStatic said:**
> Edirol UA-25EX. USB1 though but a very decent card if you ask me.
After reading up on the forums here I bought an Edirol UA-25EX for my first Ubuntu Studio installation. Worked like a charm. My only "issue" is that the output volume to the headphones is a bit low when recording louder instruments.

---

### Post by AutoStatic on 2010-04-13
> **cub said:**
> After reading up on the forums here I bought an Edirol UA-25EX for my first Ubuntu Studio installation. Worked like a charm. My only "issue" is that the output volume to the headphones is a bit low when recording louder instruments.That's true, I use a headphone amp when it gets loud.

---

