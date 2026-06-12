---
title: "firewall &amp; Dan's Guardian do they clash?"
date: 2009-07-01
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2009-07-01
I already have UFW and GUFW installed and configured running on my system.  Last night I gave the Dan's Guardian gui a try.  Looks good and seems to work fine.  I think if I'm not mistaken that that pulls in a firewall doesn't it?  Do I then need ufw?  I'm not really good with this stuff, I like graphical firewall setups, that is why I use gufw (the graphical frontend to ufw).  

Shane

**EDIT:**  And how can I verify that DG is working?

---

### Post by david_kt on 2009-07-01
> **shane2peru said:**
> I already have UFW and GUFW installed and configured running on my system.  Last night I gave the Dan's Guardian gui a try.  Looks good and seems to work fine.  I think if I'm not mistaken that that pulls in a firewall doesn't it?  Do I then need ufw?  I'm not really good with this stuff, I like graphical firewall setups, that is why I use gufw (the graphical frontend to ufw).  

Shane

**EDIT:**  And how can I verify that DG is working?

Did you install from the repository I gave?
If yes, you could launch dansguardian gui, the dansguardian status is at the box title, and the filter and firefox proxy lock is on the text (below the box title).

But I think you should remove/disable ufw.

DK

---

### Post by shane2peru on 2009-07-01
> **david_kt said:**
> Did you install from the repository I gave?
If yes, you could launch dansguardian gui, the dansguardian status is at the box title, and the filter and firefox proxy lock is on the text (below the box title).

But I think you should remove/disable ufw.

DK

Yep, I wanted to test it out.  It is reporting that firefox proxy is locked, and that it is set for Young adult.  As a suggestion it may be nice to see what those settings mean, not so much the firefox proxy, but the settings for Dan's Guardian.  Just as a suggestion.  I still have ufw installed and enabled, I guess it isn't hurting anything.  With the DG-gui installation from your repo I assume that pulls in firehol, which if I'm not mistaken is also a firewall.  I think my LAN nfs stuff may be blocked if that is the case.  Whereas with gufw I had it setup to work.  Starts to get complex for me at this point. :)  Does firehol have a gui?

Shane

---

### Post by david_kt on 2009-07-01
> **shane2peru said:**
> Yep, I wanted to test it out.  It is reporting that firefox proxy is locked, and that it is set for Young adult.  As a suggestion it may be nice to see what those settings mean, not so much the firefox proxy, but the settings for Dan's Guardian.  Just as a suggestion.  I still have ufw installed and enabled, I guess it isn't hurting anything.  With the DG-gui installation from your repo I assume that pulls in firehol, which if I'm not mistaken is also a firewall.  I think my LAN nfs stuff may be blocked if that is the case.  Whereas with gufw I had it setup to work.  Starts to get complex for me at this point. :)  Does firehol have a gui?

Shane

Did you launch the script to lock the firefox proxy? Otherwise it would not be locked.

Filter for young adult means not very strict:

50 - 75 = Young children (very strict)
76 - 125 = old children (medium)
126 - 160 = young adult (less sctrict)

I do not know whether or not firehol has GUI.

DK

---

### Post by shane2peru on 2009-07-01
> **david_kt said:**
> Did you launch the script to lock the firefox proxy? Otherwise it would not be locked.

Filter for young adult means not very strict:

50 - 75 = Young children (very strict)
76 - 125 = old children (medium)
126 - 160 = young adult (less sctrict)

I do not know whether or not firehol has GUI.

DK

Yep, I did lock firefox proxy, I figure that wouldn't really matter.  Also I changed the setting to that, so it was a lesser setting.  Seems to work fine.  I like the interface, it isn't as pretty as the old one, but none the less it works.  And if it is more usable upon upgrades that will be worth the lack of beautification. :)  Functionality, and stability are worth it.  I will have to set it up on the kids computer too.  Thanks!

Shane

---

### Post by david_kt on 2009-07-02
> **shane2peru said:**
> Yep, I did lock firefox proxy, I figure that wouldn't really matter.  Also I changed the setting to that, so it was a lesser setting.  Seems to work fine.  I like the interface, it isn't as pretty as the old one, but none the less it works.  And if it is more usable upon upgrades that will be worth the lack of beautification. :)  Functionality, and stability are worth it.  I will have to set it up on the kids computer too.  Thanks!

Shane

The new gui should be stable (survive firefox upgrade or even distribution upgrade). So that if karmic koala released, I would be able to catch up quickly as there is nothing to do for most of the applications in ubuntu-ce. 

In addition to that, it is very small and very fast. It does not need any additional packages to pull for the gui. As I mentioned on other thread, websctrict would pull more than 100 MB to install it, and also it is quite resource hungry as based on java.

I check webcontentcontrol as well, it is developed based on previous CE dansguardian gui. But I do not know how to make it works and it also pull gambas2 for the gui.

That is why finally I decided to work from scratch for this gui. But so fat I am quite satisfied with the result:

Easy to use, small, stable, fast and fully functional.

As for the lack of explanation, I will try to add a help button to call manual (how to use this gui). Thanks for your feedback.

DK

---

