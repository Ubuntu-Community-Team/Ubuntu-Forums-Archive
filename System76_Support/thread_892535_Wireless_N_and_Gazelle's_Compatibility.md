---
title: "Wireless N and Gazelle's Compatibility"
date: 2008-08-17
forum: System76 Support
---

### Post by Beridel on 2008-08-17
Hey all,

Just recently we have had some issues with our old-ish linksys router so we decided to try out the new draft n stuff.  So we got a D-Link DIR-655 router and set it up and it all worked perfectly out of the box.  But the thing is we still have one laptop and one desktop (with a wireless adapter) that are only g capable, but we were interested in seeing how much of an improvement we would get with n to see if it be worth the money to buy some new n capable network adapters.  I decided to test it out with my gazelle since it has the intel 4965 card which I know does n.

Once I changed the router settings to only enable n broadcasting, my laptop would hang on Old device (wlan0) activating... while seeing what was happening with tail -f /var/log/daemon.log

I then switched it back to mixed broadcasting (n and g) and the gazelle connected just fine, so I'm wondering why its having issues connecting to an n network when it has a n capable NIC.

We have another laptop in the house that runs vista with a intel 4965 and just as a control, that laptop connects fine to the router with only n enabled.

Thanks for any help you can offer in advance.

---

### Post by thomasaaron on 2008-08-18
Hmmm... I'm not sure. I've connected to an n network with my Gazelle/4965 card.

Are you running Gutsy or Hardy? If memory serves, I was running Hardy at the time. Maybe it doesn't make any difference, but if I need to do any testing, it would be nice to duplicate your configuration.

---

### Post by Beridel on 2008-08-18
I'm currently running Hardy.  If you need any other information let me know, and I'll get it to you.

---

