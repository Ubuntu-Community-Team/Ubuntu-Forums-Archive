---
title: "Compiz uses less resources than Metacity?"
date: 2008-01-25
forum: The Cafe
---

### Post by tom66 on 2008-01-25
I heard this a while back and I decided to test it. Turns out it's true: Compiz, with Wobbly Windows and the Cube (the two plugins I tested) vs. normal moving of windows in Metacity and switching between workspaces (with no animation; seeming very bland and boring). It seems Metacity uses more resources.

I think the reason is because the graphics load is handled by the GPU, rather than the CPU. Are there any other reasons it uses less resources - is it very conservative? What are your thoughts? 

Just curious about this awesome piece of software.

---

### Post by ingvildr on 2008-01-25
So i'm guessing you are just talking about CPU, when you look at them in terms of memory usage metacity is a lot lighter. On my system compiz uses around 15-20mb of memory while metacity sits at around 3.3 mb.

---

### Post by tom66 on 2008-01-25
I don't really worry about that too much though - it's the CPU that worries me. I believe - although I might be wrong - higher CPU usage means less battery life (I use a laptop).

---

### Post by kripkenstein on 2008-01-25
> **tom66 said:**
> I don't really worry about that too much though - it's the CPU that worries me. I believe - although I might be wrong - higher CPU usage means less battery life (I use a laptop).
It does. But higher **G**PU usage also means less battery life :)

Overall, I would guess Compiz takes more power. But I'm not sure. Perhaps someone could do an experiment.

---

### Post by tom66 on 2008-01-25
Yes, but which uses more power? I thought the CPU drives in at about third, with the screen and hard disk/CD drive taking first and second place. 

(And it looks way better than Metacity because it doesn't leave that 'gunk' behind when you move a window rapidly off another window)

---

### Post by phrostbyte on 2008-01-25
This is a bit deceptive because Compiz uses features in X.org metacity does not use. So check the memory X.org uses as well, I bet it would jump when using Compiz.

---

### Post by phrostbyte on 2008-01-25
> **tom66 said:**
> Yes, but which uses more power? I thought the CPU drives in at about third, with the screen and hard disk/CD drive taking first and second place. 

(And it looks way better than Metacity because it doesn't leave that 'gunk' behind when you move a window rapidly off another window)

A very active GPU sucks power like nothing. My 3hour battery life laptop drops to 1hour when playing a game like HL2.

---

### Post by maniacmusician on 2008-01-25
> **phrostbyte said:**
> This is a bit deceptive because Compiz uses features in X.org metacity does not use. So check the memory X.org uses as well, I bet it would jump when using Compiz.

> **phrostbyte said:**
> A very active GPU sucks power like nothing. My 3hour battery life laptop drops to 1hour when playing a game like HL2.

correct on both accounts

---

