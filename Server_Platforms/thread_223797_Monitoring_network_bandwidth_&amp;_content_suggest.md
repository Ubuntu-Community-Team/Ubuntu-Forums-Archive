---
title: "Monitoring network bandwidth &amp; content suggestions?"
date: 2006-07-26
forum: Server Platforms
---

### Post by Linus Torvalds on 2006-07-26
I live in a large household / home office with many internet users, pcs, wifi router/APs, laptops etc.  I want to implement a SOHO solution to monitor network health and content, i.e. I want to spot bottlenecks, or p2p bandwidth hogs and avoid RIAA C&D letters since ISP bill is in my name.

I am thinking of using Nagios for network health and bandwidth dashboard, and Snort for identifying what the traffic is.  What if any other free/opensource solutions do you guys use / recommend?

---

### Post by encompass on 2006-07-27
Snort should do just fine for monitoring... there arm many programs that have some very neat features that you may like.  for instance... I remember using one that saw all the traffic and picked out the images for you to see on the screen.  Good for busting someone with porn.
Another couple programs would be ethereal and ettercap... but those can be a little intrusive if you know what I mean.
And if this really is linus, moikka, if not, don't you think it would be disrespectful to use his name here, it could give him a bad rap.

---

### Post by LordMerlin on 2006-07-28
Come on, do you really think Linus would post on this forum, under his own name, asking for something as simple as this?

To the Linus impostor, please change your name. Give Linus the credit he deserves. If it wasn't for him, you'd still be stuck with Windows os MAC, or even AIX of Xenix

---

### Post by Linus Torvalds on 2006-07-29
Thanks Encompass I think I'll go ahead as planned with the Nagios / Snort combo.  I've used ettercap /etherpeek and the like for diagnostics while troubleshooting network issues in the past, but for "always on" active or passive tools to gather performance analytics trends and the like, I think Nagios/Snort should work out well.  I was hoping for some feeback from others who've been here and done this.  There may be some other tools that can do the same if not better.  I've been looking into the Cacti/Nagios combo also.  But thats probably more a subject better suited for the cacti forums.
Thanks

---

### Post by encompass on 2006-07-30
I am not sure... but there is this up and coming ubuntucenter or something to the effect.  It does all kinds of things.  And if your wanting to restrict certain traffik, consider squid.

---

