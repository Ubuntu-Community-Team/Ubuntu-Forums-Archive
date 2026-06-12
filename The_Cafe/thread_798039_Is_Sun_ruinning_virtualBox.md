---
title: "Is Sun ruinning virtualBox?"
date: 2008-05-17
forum: The Cafe
---

### Post by vexorian on 2008-05-17
All right, sorry for this post, but I need opinions to verify I am not going insane.

Before Hardy, I stayed with a pre Sun version of virtualbox (since I really need USB support in order to use scanner and my palm z22 and windows is already proprietary, I  use the evil version)  I upgraded to Hardy and needed a Hardy compliant virtualBox, which was made after Sun, later I updated it again with the most recent one.

First of all, "Sun xvm VirtualBox"? What is their problem? "Innotec virtualBox" at least sounded less random.

On a more serious basis: 
- VirtualBox's seamless mode used to respect gnome panel and adapt quite nicely to the limitation caused by it, so gnome-panel would never be placed on top of parts of the task bar or windows apps, apparently Sun thought that was a silly idea, so they now make the virtual machine take all the space during seamless mode, greatly reducing usability.

- VirtualBox used to remember that you had seamless mode enabled... not anymore.

- Now Sun is placing its adverts everywhere, try booting the machine, I just don't get why they push it is a Sun product so much, if I remember correctly, this product was innotec's innovation, Sun just bought it, I just wish Sun stopped bragging about buying other people's products...

---

### Post by FuturePilot on 2008-05-17
> **vexorian said:**
> 

- Now Sun is placing its adverts everywhere, try booting the machine, I just don't get why they push it is a Sun product so much, if I remember correctly, this product was innotec's innovation, Sun just bought it, I just wish Sun stopped bragging about buying other people's products...

Before it had a splash screen that said Innotec. I don't see what the difference is. Sun bought Innotec, for all intents and purposes, it's Sun's product now. They have a right to do what they want to the splash screen. It really wouldn't make any sense to leave it as Innotec...

---

### Post by vexorian on 2008-05-17
> **FuturePilot said:**
> Before it had a splash screen that said Innotec. I don't see what the difference is. Sun bought Innotec, for all intents and purposes, it's Sun's product now. They have a right to do what they want to the splash screen. It really wouldn't make any sense to leave it as Innotec...
It used to say "Innotec VirtualBox" now it says "Sun **xvm VirtualBox**" (emphasis reproduces the logo in use) Why do they try to sell it with "xvm" in the name? Are they just trying to use virtualbox as a ramp for some random technology?

---

### Post by hanzomon4 on 2008-05-17
> **vexorian said:**
> It used to say "Innotec VirtualBox" now it says "Sun **xvm VirtualBox**" (emphasis reproduces the logo in use) Why do they try to sell it with "xvm" in the name? Are they just trying to use virtualbox as a ramp for some random technology?

I guess two x's are better the one, lol

---

### Post by DeadSuperHero on 2008-05-17
Perhaps the packaging was poor?
I mean, heck, Hardy's got quite a few problems going for it right now.

---

### Post by Xanatos Craven on 2008-05-17
> - VirtualBox's seamless mode used to respect gnome panel and adapt quite nicely to the limitation caused by it, so gnome-panel would never be placed on top of parts of the task bar or windows apps, apparently Sun thought that was a silly idea, so they now make the virtual machine take all the space during seamless mode, greatly reducing usability.
I call bull on this one. VB always overlapped my bottom panel and took up all my space, well before it became Sun's product.

---

### Post by swoll1980 on 2008-05-17
> **Xanatos Craven said:**
> I call bull on this one. VB always overlapped my bottom panel and took up all my space, well before it became Sun's product.

+1 the only difference I notice is the splash screen. I never use seamless mode anyways now I just put the host on one monitor and the guest on the other it's like having 2 computers but with one mouse and keyboard

---

### Post by vexorian on 2008-05-17
> **Xanatos Craven said:**
> I call bull on this one. VB always overlapped my bottom panel and took up all my space, well before it became Sun's product.
Yeah, I made this thread with the intention to catch up a reply like this, does anybody have a clue on why this is happening? It could be a problem with a recent gnome version as well. When seamless mode was... seamless, I was using feisty, were you using gutsy?

> +1 the only difference I notice is the splash screen. I never use seamless mode anyways now I just put the host on one monitor and the guest on the other it's like having 2 computers but with one mouse and keyboard
you could actually have two computers then, you would be able to have 3d acceleration in windows, and you wouldn't be halving your resources in the *n*x* one.

---

### Post by Kingsley on 2008-05-17
> **vexorian said:**
> 
First of all, "Sun xvm VirtualBox"? What is their problem? "Innotec virtualBox" at least sounded less random.

It's not random. The following is what I gathered from Wikipedia.

> 
Sun xVM is a family of technologies from Sun Microsystems that addresses desktop and server virtualization, and datacenter automation. Sun announced the product family in October 2007.

They have at least 3 other products in the xVM family.

---

### Post by Frak on 2008-05-17
The Innotek version and the Sun version is very slightly different. Sun added some hardware functions and the splash screen and cleaned up code. That's about all they did.

---

### Post by Xanatos Craven on 2008-05-17
> 
Yeah, I made this thread with the intention to catch up a reply like this, does anybody have a clue on why this is happening? It could be a problem with a recent gnome version as well. When seamless mode was... seamless, I was using feisty, were you using gutsy?
I was using gutsy.

That bug alone was bearable, as I could always just consolidate everything into one panel, but I hated it when seamless mode got super-glitchy under compiz. Now I'm doing the same thing that swoll does, aside from using virtual desktops instead of dual monitors.

---

### Post by vexorian on 2008-05-17
> **Xanatos Craven said:**
> I was using gutsy.

That bug alone was bearable, as I could always just consolidate everything into one panel, but I hated it when seamless mode got super-glitchy under compiz. Now I'm doing the same thing that swoll does, aside from using virtual desktops instead of dual monitors.
Well, I just disabled metacity compositing when that happened, my priority was seamless windows, though I still use virtual desktops, I guess with compiz you can go from one virtual desktop to another without closing the VM's full screen, that's interesting.

What I did to deal with the panel, was to move the windows taskbar so it is placed vertically, I still need to take care when using the windows apps since instead of maximizing I got to manually change the size.

I miss the times this used to work, I will look if there's a bug report or something.

---

