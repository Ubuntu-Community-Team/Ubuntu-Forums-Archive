---
title: "ALSA, new OSS specification - what doeas it mean for me?"
date: 2007-03-16
forum: The Cafe
---

### Post by _tomcio on 2007-03-16
Hi!

I had read on [www.osnews.com](www.osnews.com), that new specification of OSS was released. I don't know much about sound support situation in Linux, but I thought, that is deprecated and it isn't developed any more. I was really surprised, when I read what new features were added to OSS ([http://www.opensound.com/press/2007/OSSv4.txt)](http://www.opensound.com/press/2007/OSSv4.txt)). The mos important thing for me is support for multichannel audio output.

I thought, that ALSA is recommended sound architecture for Linux and it want change. Generally it doesn't matter for me, if my sound works via ALSA or OSS, but I'm afraid, that OSS will back to game and become more popular (one big advantage of OSS is, that it's available on other *nix platforms). This may mean, that we will have problems with sound support, because some corporations, which will want to write drivers for their sound cards will support only wan standard. Moreover it isn't good when we have many standards....

---

### Post by hanzomon4 on 2007-07-18
I've been reading about oss v4.0 and everything I've read has it rated as superior to ALSA. It's now GPL'ed so what does that mean for Linux only ALSA. By the way I thought OSS was depreciated?

---

### Post by stmiller on 2007-07-18
ALSA is superior, esp with jack possibilities. Some older hardware only works with OSS, so that project is continuing. One of the biggest drawbacks of OSS is that it could only play sound from ONE application at a time. I see in those release notes that now up to 16 apps can share the sound device. So that is very cool.

Wow- and looking again looks like OSS finally opened the source of a lot of their code:

[http://www.opensound.com/press/2007/oss-gpl-cddl.txt](http://www.opensound.com/press/2007/oss-gpl-cddl.txt)

---

### Post by jrusso2 on 2007-07-18
I have had a lot more problems with alsa then I ever did with OSS.  I would be glad if we went back to OSS but I doubt that will happen they have too much invested in Alsa at this point.

---

### Post by PatrickMay16 on 2007-07-18
Hopefully the day will come when nobody ever has to see a "cannot open sound device" message again.

---

### Post by FuturePilot on 2007-07-18
> **PatrickMay16 said:**
> Hopefully the day will come when nobody ever has to see a "cannot open sound device" message again.

I hope so too. I hate when that happens:( 
I thought OSS was dead though.

---

### Post by hanzomon4 on 2007-07-18
No apparently OSS is very much alive, it was kicked out of the kernel after parts of it went closed source and was replaced with ALSA. It seems to have keep up and it works on every *nix platform.

---

### Post by Polygon on 2007-07-18
> **PatrickMay16 said:**
> Hopefully the day will come when nobody ever has to see a "cannot open sound device" message again.

quoted for truth.

---

### Post by Extreme Coder on 2007-07-18
IMO, I'd prefer if Linux would go back to OSS, but I don't know if that's possible.
For example, a no-name sound card works wonderfully with Mandrake Linux 8.2, but has all sorts of problems with Ubuntu and Mandriva today with ALSA :P

---

### Post by tomcheng76 on 2007-07-18
Hey, can anyone tell me how to check that i am using ALSA or OSS ?
and how to switch between them?

---

### Post by janfsd on 2007-08-25
Nice reading about oss/alsa:

[http://4front-tech.com/hannublog/?p=5](http://4front-tech.com/hannublog/?p=5)

I hope the new version gets into the kernel.

---

