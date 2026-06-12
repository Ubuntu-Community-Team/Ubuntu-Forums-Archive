---
title: "Avidemux how to change permissions"
date: 2009-12-19
forum: Ubuntu Studio
---

### Post by ravengirl1960 on 2009-12-19
I have Linux Mint 8 (Helena) installed. I've tried in their forums but have no luck (same with googling) so I thought I'd try here.

Avidemux2 runs perfectly fine for me. However, there are times I'm doing housework or whatever and I don't need to use the computer for anything other than video converting. So I've tried to change the priority but it's grayed out. And searching on Google, a lot of people are getting the answer that you need root permissions to change the priority (why, I don't know).

I tried sudoing it from terminal (as well as just logging into su) and neither one worked; the option was still grayed out.

Any suggestions?

---

### Post by Tricity on 2009-12-19
I am not familiar with Avidemux, but let me try to understand - you run Avidemux with normal process priority. When the computer is not in use you want to increase the priority so that it runs faster?

I am not sure if this is a good idea. When the computer is not in use, there are hardly any active processes that would compete with Avidemux for CPU time. The speed gain would be marginal. On the other hand, if you elevate the priority to system level, you may get problems with stability. 

If you have a multi-CPU system (multi-core), it might be a better idea to distribute the work over the CPUs (whether this is possible - I don't know).

---

