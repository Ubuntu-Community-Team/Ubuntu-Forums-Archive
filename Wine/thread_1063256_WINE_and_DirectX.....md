---
title: "WINE and DirectX...."
date: 2009-02-07
forum: Wine
---

### Post by RaiCoss on 2009-02-07
I have noticed in the recent version's of WINE (1.0.1+), that DirectX functionality seems to have diminished considerably.

Just as an example, when I first used WINE on Hardy, I was curious about it's DirectX emulation capability. So I decided to experiment using   nVidia's tech demos. These demo's are used to show off what the cards can do ( new functionality etc...). I was highly surprised to see that all one ran flawlessly (Timbury), but after repeating the experiment on WINE 1.0.1 and 1.1.14, the only demo that works is the Adrianne demo.

No DirectX game I try will work under WINE anymore!!

Is it just me experiencing this kind of problem??

---

### Post by hikaricore on 2009-02-07
Regressions are common with WINE.  Your best bet is to stick to the version of WINE that works best for you and stop updating it.

The old if it ain't broke don't fix it scenario comes to mind.

Past this I've seen other users mentioning problems with "DirectX" lately... however some of these were the ones who ignored the general rule to NOT install DirectX under WINE and they're likely facing a different issue entirely.

---

### Post by RaiCoss on 2009-02-07
> **hikaricore said:**
> Regressions are common with WINE.  Your best bet is to stick to the version of WINE that works best for you and stop updating it.

The old if it ain't broke don't fix it scenario comes to mind.

Past this I've seen other users mentioning problems with "DirectX" lately... however some of these were the ones who ignored the general rule to NOT install DirectX under WINE and they're likely facing a different issue entirely.

Yeah but I've always installed DirectX under WINE and only recently has it decided to start break functioality, it's extremely annoying ¬¬

---

### Post by hikaricore on 2009-02-07
That may be but you're not supposed to... the only time you will ever need to do anything with DirectX will involve individual libraries.
Installing DirectX under WINE when you don't need to or don't know what you're doing is a sure fire way to break WINE.

Most DirectX libraries are already implemented under WINE anyway.

---

### Post by cogadh on 2009-02-07
> **RaiCoss said:**
> Yeah but I've always installed DirectX under WINE and only recently has it decided to start break functioality, it's extremely annoying ¬¬
That's most likely because Wine's own DirectX is much more robust than it used to be. By installing the "real" DirectX you are breaking the functionality that Wine is already expecting. Besides, pretty much the only libraries you might ever need from DirectX are the d3dx9_##.dll files, and you can get those without actually installing DirectX anyway.

---

