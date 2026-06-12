---
title: "Ram upgrade."
date: 2010-04-14
forum: The Cafe
---

### Post by PhilMize on 2010-04-14
Quick question. I've never upgraded ram on an ubuntu machine before so I'm curious if this is good practice or not. If I currently have 2 gigs of ram installed and I'm moving too 4. Does this mean I should adjust the size of my swap partition to compensate for the ram increase?

---

### Post by Half-Left on 2010-04-14
I've never understood why people think they need to increase swap with more memory. It probably comes from Windows, since it uses such methods even when not out of ram.

I mean if you go into swap with 4Gb of ram and then need an extra 2Gb swap for usage, you need more ram, not more swap.

You should think of swap like an emergency memory fallback and only use it if really needed and not rely on a memory method that is so slow.

---

### Post by swoll1980 on 2010-04-14
> **PhilMize said:**
> Quick question. I've never upgraded ram on an ubuntu machine before so I'm curious if this is good practice or not. If I currently have 2 gigs of ram installed and I'm moving too 4. Does this mean I should adjust the size of my swap partition to compensate for the ram increase?

You didn't tell us how big your swap is now.

---

### Post by swoll1980 on 2010-04-14
> **Half-Left said:**
> I've never understood why people think they need to increase swap with more memory. It probably comes from Windows, since it uses such methods even when not out of ram.

I mean if you go into swap with 4Gb of ram and then need an extra 2Gb swap for usage, you need more ram, not more swap.

It's used for hibernation mostly.

---

### Post by Paqman on 2010-04-14
> **PhilMize said:**
> Does this mean I should adjust the size of my swap partition to compensate for the ram increase?

If you need to use hibernation you should expand your swap so that it's still bigger than your RAM. If you don't use hibernation you could leave it as is, or most likely reduce it, since you won't be using it as much.

---

### Post by PhilMize on 2010-04-14
I was always told your swap partition should be at least as big as your ram size. So I have 2gb of ram currently, my swap is 2gb. From your guys' remarks I'm thinking it's pretty irrelevant so thanks!:)

---

### Post by Lightstar on 2010-04-14
With more ram, your swap will actually be used less.  People are thinking in the opposite direction.

Swap is used when your ram memory is full.
With more ram memory, less swap should be needed.

I have 4gb.  I keep 1gb for swap, and so far my ubuntu/linux never had to use the swap.

---

### Post by K.Mandla on 2010-04-14
> **PhilMize said:**
> Quick question. I've never upgraded ram on an ubuntu machine before so I'm curious if this is good practice or not. If I currently have 2 gigs of ram installed and I'm moving too 4. Does this mean I should adjust the size of my swap partition to compensate for the ram increase?
Not to be obtuse, but what are you doing that you need 4Gb of RAM in Ubuntu anyway?

---

### Post by NovaAesa on 2010-04-14
> **K.Mandla said:**
> Not to be obtuse, but what are you doing that you need 4Gb of RAM in Ubuntu anyway?

Maybe he's a developer. I have 4GB of RAM at the moment and find that when I'm doing massive multitasking and running memory intensive code I'm swapping out alot. I could really do with 8GB :P

---

### Post by PhilMize on 2010-04-14
> **K.Mandla said:**
> Not to be obtuse, but what are you doing that you need 4Gb of RAM in Ubuntu anyway?

LOL! Got it free... So why not use it?

---

### Post by TheNessus on 2010-04-14
> **Half-Left said:**
> I've never understood why people think they need to increase swap with more memory. It probably comes from Windows, since it uses such methods even when not out of ram.

I mean if you go into swap with 4Gb of ram and then need an extra 2Gb swap for usage, you need more ram, not more swap.

You should think of swap like an emergency memory fallback and only use it if really needed and not rely on a memory method that is so slow.
But what about suspending to disk? (hibernation) where RAM is copied to the SWAP? think big, don't be so narrow...

---

### Post by K.Mandla on 2010-04-14
> **PhilMize said:**
> LOL! Got it free... So why not use it?
:D Then by all means ... ;)

---

### Post by Half-Left on 2010-04-14
> **TheNessus said:**
> But what about suspending to disk? (hibernation) where RAM is copied to the SWAP? think big, don't be so narrow...

Fine, if you have a laptop.

---

