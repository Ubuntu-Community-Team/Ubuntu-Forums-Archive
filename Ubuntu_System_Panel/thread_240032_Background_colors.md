---
title: "Background colors"
date: 2006-08-20
forum: Ubuntu System Panel
---

### Post by giuliastro on 2006-08-20
I haven't found a key for this, and don't know if it is a bug. But my "Applications" and "Places" plugin background colors seem wrong. Is there a way to fix this?

---

### Post by chanders on 2006-08-20
> **giuliastro said:**
> I haven't found a key for this, and don't know if it is a bug. But my "Applications" and "Places" plugin background colors seem wrong. Is there a way to fix this?

Check /apps/usp/use_custom_color, and set custom_color to one that you like ;)

---

### Post by Uncle Spellbinder on 2006-08-20
I had the same problem after applying "custom color". Looked just like the attatchment in post #1. To solve this, I right-clicked USP and clicked remove from panel. Then right clicked the panel to bring up "sdd to panel" and added USP again. All was fine. It seems that some things require removing and re-adding USP to take full effect.

---

### Post by giuliastro on 2006-08-20
> **Uncle Spellbinder said:**
> I had the same problem after applying "custom color". Looked just like the attatchment in post #1. To solve this, I right-clicked USP and clicked remove from panel. Then right clicked the panel to bring up "sdd to panel" and added USP again. All was fine. It seems that some things require removing and re-adding USP to take full effect.

I tried this but the situation got worse. See my screenshot. Did it many times but it isn't working.
I tried using custom colors but nothing seems to happen. I guess I found a bug. :-k

---

### Post by giuliastro on 2006-08-20
Ok, I noticed I had to restart USP to correctly see custom colors. Anyway latest version doesn't seem to correctly handle default colors. Also, when adding USP to ubuntu's panel it seems it gets colored with custom colors even if the checkbox is disabled.

---

