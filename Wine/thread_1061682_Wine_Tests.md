---
title: "Wine Tests?"
date: 2009-02-06
forum: Wine
---

### Post by BoneSmash on 2009-02-06
I would just like some clarification on what exactly Wine Tests are, there seems to have been a lot of work being done in regards to fixing them.  From my understanding they show how closely Wine's behavior/implementation matches Windows.  Is this correct?

---

### Post by Ferrat on 2009-02-06
in a way yes, in a way no, as I understand it, it's also a diagnostics for how well wine does some things, like a benchmark. 
A simple way to see it over all there is regression, measuring the FPS for ex. on one standard and not 15 different games but also taking in to account the skipped stuff etc like the errors and fixme's. 

So in a way you get a idea of how closely stuff work to the "windows way" but it's more like making sure that there is as little regression as possible, because for a game a change can make the FPS go up but it might also skip something, maybe it's not vital but it still skips it = no good for other games that need it. 
wine tests helps the devs see where there is a true gain/loss.

Atleast that's what I think it does, I might have understood it wrong?

---

