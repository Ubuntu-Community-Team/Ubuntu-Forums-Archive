---
title: "ElementaryOS - cannot see updated version of website after DNS change."
date: 2015-09-24
forum: Ubuntu/Debian BASED
---

### Post by marc58 on 2015-09-24
So i created a new website, i tried creating a server on my computer and pointing the domain to my computer (didnt work out) - so i got some web hosting and pointed it there. When i get on my phone or other computer (using the same wifi connection), i can see the updated version of my site, but ive googled how to do fix this and ive mustve tried 10 different things, but i still cannot get the proper version of my site. Anyone have any suggestions? 

A few things that i remembered to have done (im using Chrome, but its the same regardless of browser).
1. Inspect -> Empty Cache and Hard Reload
2. Reset router
3. Reset computer.

---

### Post by Bucky Ball on 2015-09-25
*Thread moved to **Ubuntu/Debian BASED**.*

We officially support Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, Mythbuntu and Ubuntu Mate in the main forum areas here. You might consider posting in the Elementary forums, too, to increase you chances of support. :)

---

### Post by QIII on 2015-09-25
Hello!

When you were developing on your computer, before you moved everything to your web hosting provider, where were your content files?  Were they on your local machine, on another machine in your home, had you modified /etc/hosts to point the url to another IP on your home network?

Let me describe a scenario where I can see something like what you are describing happening:

When I work on my websites, I do so on a Raspberry Pi sitting on my desk.  To make sure I'm not getting out to the production websites on my VPS, I temporarily modify my hosts file and add something like

```
12.34.56.78  mytestsite.com
```

(where the IP is my R Pi) to be sure I don't mess with my production sites.  I move my work over when I'm satisfied.

But I often make minor changes on my live websites via SSH, say I want to use a different image somewhere.  If I were to open a browser on my computer with the modified hosts file, nothing would appear to have changed.  But I'd see the changes on my cell phone browser or another one of my machines.

---

