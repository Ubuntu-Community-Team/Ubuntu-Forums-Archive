---
title: "xmrig - Docker / Snap / Firetools - which to use"
date: 2022-01-22
forum: Security
---

### Post by stevenjrees on 2022-01-22
I want to run xmrig on my pc when I am not using it. 
Because it is my main desktop, I am paranoid about security.  

My mining is on a separate vlan to the desktop lan, so i need to be able to isolate the application and support a different vlan 

My question is, what is the most (system) efficient tool to using isolating xmrig 
i.e. should i run a docker or snap version, or should i just use firetools, bearing in mind the need to isolate the lan traffic.

---

### Post by DuckHook on 2022-01-22
Okay, providing you with more of a meta picture in the course of answering your question:

[list=1]
[*]Do you really want to do this? Though not exactly malware, the benefits are nonexistent and the payoff is actually negative. Unless you are located by a hydro facility with practically free electricity, you will pay more on your electrical bill than you mine.
[*]All such stuff is suspect in my eyes. Unless you are a guru who can parse the code and check it for hidden nasties, you don't know what traps or bugs are hidden inside. Yet, you want to install this on your main—I assume production—box. If you are simultaneously concerned enough about security to post on this forum, then you are sucking and blowing at the same time.
[*]Do you know that the XMRig binary does not support the GPU on Linux? According to [this]("https://linuxreviews.org/XMRig"), it is only able to mine using your CPU. This is just about the most inefficient way possible to mine, and you will pay even more in electricity.
[*]The vlan configuration is the least of your worries.
[/list]
Unless it's just for research, cryptomining only makes financial sense if you have limitless, almost free electricity and if you make use of GPUs, preferably tweaked and clustered. This does not even touch upon the huge attack surface that you've just opened up to the world's scumbags.

If you are still intent on doing this, then I've recently set up a tagged vlan for my home network. The learning curve is not trivial. I consider myself a power user and it took me three days.

Just as significantly, you will need to sandbox XMRig, which is also non-trivial. I wouldn't trust snap's sandboxing to be sufficient, but that's a personal opinion. Docker would be better. So would LXD. A VM adds way too much inefficiency, but this whole venture is already grossly financially negative, so I don't suppose that added inefficiency is that big a deal. VM, set up properly, would be your best sandbox. Firejail is another good option.

As for vlans, it's too complicated to address in a thread such as this. We have no idea of your topology and it's so involved that you will have no choice but to bake your own cake. A forum guru pointed me to an awesome YouTube resource: a series of videos by Lawrence Systems. A websearch on networking tutorials should also get you the basics. Tagging is not that hard once you understand networking basics, but OEMs all have their own quirks, so don't expect to just follow some recipe.

Good Luck.

---

