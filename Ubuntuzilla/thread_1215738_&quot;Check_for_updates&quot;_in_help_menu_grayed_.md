---
title: "&quot;Check for updates&quot; in help menu grayed out"
date: 2009-07-17
forum: Ubuntuzilla
---

### Post by propan0 on 2009-07-17
I'm runing Ubuntu 8.10 - the Intrepid Ibex, and have the latest ubuntuzilla.

Recently, the new version of firefox 3.5.1 came out, and I was notified correctly by the script, however, I could not update firefox due to the fact that the "Check for updates" menu item in the help menu is grayed out (not active).

I worked around it by runing the remove action on ubuntuzilla, and installing firefox again with it, but I was wondering if I am missing a step for the "Check for updates" to be active, or if this is something that everyone is suffering from...

Any pointers?

---

### Post by PhilGil on 2009-07-17
I upgraded to 3.5.1 yesterday evening.  The trick is that you need to run Firefox as root in order to use "check for updates."

The instructions are on the Ubuntuzilla site: [http://ubuntuzilla.wiki.sourceforge.net/#tochome10](http://ubuntuzilla.wiki.sourceforge.net/#tochome10)

I had to do the update a couple of times before it "took," so don't make the same mistakes I did...

1. Be sure to close all open instances of Firefox before performing the actions described on the Ubuntuzilla site.

2. In order for the update to install, I had to close and re-open Firefox as root.  I then closed the root instance and opened Firefox by my usual method (clicking on the Firefox icon)

---

### Post by propan0 on 2009-07-18
> **PhilGil said:**
> I upgraded to 3.5.1 yesterday evening.  The trick is that you need to run Firefox as root in order to use "check for updates."

The instructions are on the Ubuntuzilla site: [http://ubuntuzilla.wiki.sourceforge.net/#tochome10](http://ubuntuzilla.wiki.sourceforge.net/#tochome10)

I had to do the update a couple of times before it "took," so don't make the same mistakes I did...

1. Be sure to close all open instances of Firefox before performing the actions described on the Ubuntuzilla site.

2. In order for the update to install, I had to close and re-open Firefox as root.  I then closed the root instance and opened Firefox by my usual method (clicking on the Firefox icon)

Ah that makes sense, thanks a lot PhilGil -- will keep it in mind for next time. Glad this isn't a bug =))

---

### Post by nanotube on 2009-07-21
> **PhilGil said:**
> 
2. In order for the update to install, I had to close and re-open Firefox as root.  I then closed the root instance and opened Firefox by my usual method (clicking on the Firefox icon)

hmm, that's strange - if you run firefox with 'gksudo firefox' and then download the update, you should be able to just click "restart firefox", and things will install, without having to manually restart as root. did that not work for you?

---

### Post by PhilGil on 2009-07-21
> **nanotube said:**
> hmm, that's strange - if you run firefox with 'gksudo firefox' and then download the update, you should be able to just click "restart firefox", and things will install, without having to manually restart as root. did that not work for you?
I would have worked fine if I had followed the instructions correctly.  Instead, I closed the root instance of Firefox without restarting and opened a user instance.  When I saw the update hadn't taken yet I had to re-open Firefox as root.

---

### Post by nanotube on 2009-07-21
> **PhilGil said:**
> I would have worked fine if I had followed the instructions correctly.  Instead, I closed the root instance of Firefox without restarting and opened a user instance.  When I saw the update hadn't taken yet I had to re-open Firefox as root.

ah ok, that explains it. :)

---

