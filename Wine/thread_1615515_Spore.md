---
title: "Spore"
date: 2010-11-07
forum: Wine
---

### Post by Kranix on 2010-11-07
Does anyone know if it works in wine?

I really like this game and would like to play it again, but on winehq it only has reviews from 9.10 and 10.04.

---

### Post by _outlawed_ on 2010-11-07
Why not just give it a try out? If it works, you can get the AppDB page for it updated. :popcorn:

---

### Post by Kranix on 2010-11-07
I tried, but when i right click the CD icon on my desktop and click "Open with Autorun Prompt" it just says:
```

Error starting autorun program: Permission denied
```

Any idea how to fix this?

---

### Post by Kranix on 2010-11-08
Bumping this since it's 24 hours past my last post.

---

### Post by VeeDubb on 2010-11-14
1. Open a terminal.
2. Browse to the CD folder.
3. wine nameofexecutable.exe
4. Get really pissed when you realize Spore doesn't work with wine unless you crack the DRM.
5. Re-up that Cedega subscription that you let lapse months and months ago, only to find out that even though it's "officially supported" it doesn't work with cedega anymore.
6. Try the demo of Crossover Games.
7. Get completely bummed out when you realize that even though it's listed as 'bronze,' it won't work there either.
8. Send nasty email to Cedega customer service. 
9. Get no response.
10. Install windows 7 in VMwarePlayer, and enjoy an "almost functional" game experience.


I know it sucks, but I've spent the last several days doing exactly that.  The only thing I've found that even helps a little is entering ```
echo 0 | sudo tee /proc/sys/kernel/yama/ptrace_scope
``` in the terminal, and using an older cedega engine.

---

