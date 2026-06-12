---
title: "DansGuardian not working as I expected"
date: 2008-11-18
forum: Ubuntu Christian Edition
---

### Post by eppu on 2008-11-18
I installed Ubuntu CE 4.0 on a computer that I planned to use as a gateway for Internet access. I installed Firestarter so I could share internet connection and everything works fine, all computers in the network have internet access through the gateway computer.
However, my intention was to prohibit access to certain websites. That was the main reason for installing Ubuntu CE 4.0. 

So current situation is as follows: DansGuardian enabled, filtering level Strict, Banned URLs list updated with URLs I would like to prohibit access to.

However, all users in the network still have access to prohibited (banned) URLs; those URLs are even accessible from the gateway computer. 

What else do I need to do in order to make it work as it should? What steps did I miss?
Any help would be greatly appreciated.

---

### Post by tak1150 on 2008-11-18
I wanted to do the same thing and I chronicled the process of achieving it in the form of a how-to article [here]("http://taksuyama.com/?p=16#more-16"). Hope this helps.

---

### Post by eppu on 2008-11-19
> **tak1150 said:**
> I wanted to do the same thing and I chronicled the process of achieving it in the form of a how-to article [here]("http://taksuyama.com/?p=16#more-16"). Hope this helps.

Thank you very much for this useful link. I will try to follow this guide to achieve my goal.

Still, I'd appreciate if someone else could help me out with my problem regarding Ubuntu CE 4.0 and DansGuardian (I'm perhaps too superstitious, but I'd LOVE to have CE at the gateway).

---

### Post by tak1150 on 2008-11-19
The Dansguardian package shipped with CE is intended filter only the browsing that happens on that local machine. You would have to change the settings for the firewall program (firehol) that controls things like what information gets passed through, etc.

So you can either customize the config files for firehol or follow the instructions above (it uses shorewalls instead of firehol).

As for using a "Christian" edition being a "better" choice for protecting your family, yes, it's superstition and the Bible doesn't agree with superstition (nothing wrong with CE). Having the CE wallpaper and other small gadgets won't protect your family any better. You should focus on praying and such. My 2 cents.

tak

---

