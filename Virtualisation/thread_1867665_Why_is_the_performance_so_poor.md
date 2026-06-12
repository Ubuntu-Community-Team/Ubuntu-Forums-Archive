---
title: "Why is the performance so poor?"
date: 2011-10-23
forum: Virtualisation
---

### Post by Tomination on 2011-10-23
Hi All,

Running 11.10 in Virtual Box as a guest using my Windows 7 Gaming Computer.

I have used previous versions in the past; really like 11.10 (once got Gnome Shell on :))

However, performance is terrible. like if i click "Activities" it takes 3-5 seconds to load, keyboard typing is a bit behind, just not what i was expected.

I am giving it the full ram it requires for 32bit (3.4mb) giving it 2 of my 4 processing cores; and 60 percent of my gaming graphics card for video.

In previous versions it was snappy as hell, this version is bordering on frustrating, has anybody got any ideas?

Thanks :) Tom

---

### Post by HermanAB on 2011-10-24
Howdy,

You are probably giving it too much RAM and you may also need to install guest additions.

---

### Post by jackdale on 2011-10-24
> **HermanAB said:**
> Howdy,

You are probably giving it too much RAM and you may also need to install guest additions.

I have never heard of too much RAM before...usually "more is more", but you are suggesting that "more might be less".  (can you direct us to a link that might help people calculate the optimal amount of RAM - assuming that there is a standardised bell curve equation to estimate this), or is this a bug in Ubuntu?

Also, I'm assuming this fellow has guest additions already installed because he can see the gnome-shell.  If there are not 3D resources, it goes to the fall-back mode on most virtualbox installations (not to mention he *has* done this before, according to his own post).

---

### Post by Phkillah on 2011-10-25
Virtualbox bugs'a'lot...

I'm hunting down the reason for the slowness of a XP guest inside Ubuntu for years now.

Yes VMWare is heavier.
Yes VBox only works temporarily.

very very sad.

---

### Post by CharlesA on 2011-10-25
Can I get a "works for me(tm)" ?

Been running XP and 7 on a *nix host using VBox for a while now with no slow down.

Same with *nix on a Windows host.

That being said, I only give them about a gig or two of RAM.

---

### Post by Phkillah on 2011-10-25
> **CharlesA said:**
> Can I get a "works for me(tm)" ?

Been running XP and 7 on a *nix host using VBox for a while now with no slow down.

Same with *nix on a Windows host.

That being said, I only give them about a gig or two of RAM.

Yup, it did "worked for me(tm)" while i had 4G and gave 1G to my guest.

Now that the RAM is close to depletion (i have 2G and 512m guest), there is a deadly lag in the CPU cores (i've checked, no IO stress, no swapping.. just wtf bugs..)

---

### Post by LinuxFan999 on 2011-10-29
> **Tomination said:**
> Hi All,
 
Running 11.10 in Virtual Box as a guest using my Windows 7 Gaming Computer.
 
I have used previous versions in the past; really like 11.10 (once got Gnome Shell on :))
 
However, performance is terrible. like if i click "Activities" it takes 3-5 seconds to load, keyboard typing is a bit behind, just not what i was expected.
 
I am giving it the full ram it requires for 32bit (3.4mb) giving it 2 of my 4 processing cores; and 60 percent of my gaming graphics card for video.
 
**In previous versions it was snappy as hell**, this version is bordering on frustrating, has anybody got any ideas?
 
Thanks :) Tom
For me, Ubuntu has never been snappy under virtualization. Instead, it has always been sluggish, and not just Ubuntu, but Linux in general. I always find it to be slower than other guests. I have a powerfull host machine (but no VT-X), and usually allocate 1.5-2 GB of RAM per virtual machine. I think that in my case, and maybe for others too, that it might be an issue with the kernel.
 
By the way, what are the specifiations of your host computer?

---

### Post by JockeF on 2011-11-30
Might be a bit off topic here (guest/host relationship reversed) but given the open headline I'll share my experience.
I have had massive problems with Windows 7 as a guest on Ubuntu 10.10 and XP on earlier versions of Ubuntu. It has been so bad that all my host applications tended to "gray out" and became unresponsive. The whole computer was close to useless if I opened VB with Windows while Linux guests worked fine.
Hunting the web for answers failed so I resorted to testing settings. It seems that in my case the problem was the SATA Controller setting Use host I/O cache. When I switched that off I was suddenly able to keep Windows running in the background while using Ubuntu, as one would expect. This might be a unusual problem perhaps related to hardware (Dell T1500) or how I have set things up as I found nothing about this online.
Nonetheless, I hope someone might find this info helpful, easy to try out anyway.

---

