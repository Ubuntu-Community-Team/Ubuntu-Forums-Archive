---
title: "Debian users- some tips?"
date: 2010-12-04
forum: The Cafe
---

### Post by Dustin2128 on 2010-12-04
I've been looking into debian for the past few days and I've decided to replace my mint partition with a debian one. I've heard that an improperly setup debian can be a nightmare- so, any tips? I want semi up to date packages, a system as stable as possible, plus nvidia legacy drivers, occupying as little space as possible (I'm going to start playing warcraft again soon- 25GB!)

---

### Post by madjr on 2010-12-04
why didnt you go with mint-debian?

---

### Post by Dustin2128 on 2010-12-04
> **madjr said:**
> why didnt you go with mint-debian?
Read above; minimizing on occupied space. Mint is rather bloated, since I'm installing it on a 35GB partition.

---

### Post by Pogeymanz on 2010-12-04
Debian is not that big of a deal. Whoever warned you that a misconfigured debian is difficult must have assumed than Ubuntu/Mint users are truly helpless.

Just dive in to Debian Testing (Debian Stable is only for production machines and servers with ancient packages).

---

### Post by kaldor on 2010-12-04
> **Dustin2128 said:**
> Read above; minimizing on occupied space. Mint is rather bloated, since I'm installing it on a 35GB partition.

You can just strip out Mint's extras altogether; it's not that bloated.

I'd recommend using the Testing or Sid branch as opposed to Stable (Stable is too outdated, and the new Stable comes out shortly). I set up Debian Stable at one point and it was pretty frustrating since the outdatedness led to me having to configure some drivers/settings on my hardware that had been fixed on newer kernels. 

I don't see how you could manage to mess up a Debian installation, though I might be missing something.

---

### Post by juancarlospaco on 2010-12-04
Debian what?, i got Debian BSD.

---

### Post by kaldor on 2010-12-04
> **juancarlospaco said:**
> Debian what?, i got Debian BSD.

No need to be smart ;)

---

### Post by madjr on 2010-12-04
am teaching my kid warcraft3, hes learning fast RTS (well after getting killed like 50 times) and loving it :)

---

### Post by Spice Weasel on 2010-12-04
Tip:

Don't install the xorg package.

Install the xserver-xorg package, then the drivers you need etc. (Install the vesa drivers as a failsafe if you feel like it)

That way the system doesn't install such useless things as the Radeon drivers alongside xorg.

Oh, and replace stable with squeeze in /etc/apt/sources.list for stable, more up to date packages.

---

### Post by kaldor on 2010-12-04
> **madjr said:**
> am teaching my kid warcraft3, hes learning fast rts (well after getting killed like 50 times) and loving it :)

?? :)

---

### Post by Dustin2128 on 2010-12-04
> **madjr said:**
> am teaching my kid warcraft3, hes learning fast RTS (well after getting killed like 50 times) and loving it :)
I meant world of warcraft; RTS's aren't exactly my forte. TBS's, though....
Anyway, which one, sid or testing?

---

### Post by odiseo77 on 2010-12-04
> **Dustin2128 said:**
> Anyway, which one, sid or testing?

Although I use Sid myself, I would say testing. It's rock solid, and has up to date packages. Besides, a clean install doesn't take too much space, if you're worried for space.

---

### Post by sidzen on 2010-12-05
antiX is Debian-based, uses the IceWM, istalls easily on most anything.  Check out the forum and talk to the moderators look at antix-M8.5  [http://antix.freeforums.org](http://antix.freeforums.org)

---

