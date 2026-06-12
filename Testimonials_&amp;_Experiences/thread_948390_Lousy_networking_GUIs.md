---
title: "Lousy networking GUIs"
date: 2008-10-15
forum: Testimonials &amp; Experiences
---

### Post by realn on 2008-10-15
Hi,

One of the things I don't know (too much) to do in command line is network configuration. After a couple of years of using Ubuntu, I saw that network configuration through the GUIs is LOUSY:
1) KDE network settings - obvious bugs: the gateway IP is not stored; network profiles simply doesn't work ( I saw there is a bug about it - in LOW priority for years now - let's get serious, guys, I sometimes take my laptop to work, then back home - what about if I do it every day??); try to enable a network device - it gets disabled without giving a reason;
2) NetworkManager and Knetworkmanager module - is not self-contained = very unclear interaction with the previous module : manual mode is not taken into account by NetworkManager and automatic mode doesn't work;
- WiFi support - no possibility of scanning networks; poor WPA support; 
- others - I plug a cable in my eth0 - sometimes nothing happens.

I think I'll have to go back to if* and ipw* commands and just drop these two pieces of S..T.

A very  ](*,) Ubuntu user.

---

### Post by realn on 2008-10-15
"no comment" ?

---

### Post by jimv on 2008-10-15
You, my friend, need WICD.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Iowan on 2008-10-15
Never mind...

---

### Post by Rocket2DMn on 2008-10-15
Not a support request, so I moved this thread to Ubuntu Testimonials & Experiences.

---

### Post by Sef on 2008-10-15
Wireless is much better supported in later versions.

---

### Post by realn on 2008-10-16
Where is the ESSID scanning? What about hidden ones? Where are the network profiles? When will I be able to re-connect automatically to a WPA network without having to enter passwords? That's why I am saying that "much better supported" should be more like "you can make it work. Eventually.Not all the time".

jimv - you made my day. And maybe a lot more, if i don't have to periodically fiddle with all these network settings. And if I can make it work with no X, than that would become one of my favorite apps. I am so glad I could remove Networkmanager from my computer. That piece of ...software used to be the only app which completely froze my computer. Now it's gone.
I still don't understand why ubuntu project managers don't look around for newr/better apps, especially for more sensitive parts, and keep on delivering old stuff which is rotten from inside.

---

### Post by ukripper on 2008-10-16
If you start another thread in support forums you may get your answers there.

---

### Post by hyper_ch on 2008-10-16
as suggested, use WICD

---

### Post by jimv on 2008-10-16
> **realn said:**
> 
jimv - you made my day. And maybe a lot more, if i don't have to periodically fiddle with all these network settings. And if I can make it work with no X, than that would become one of my favorite apps. I am so glad I could remove Networkmanager from my computer. That piece of ...software used to be the only app which completely froze my computer. Now it's gone.
I still don't understand why ubuntu project managers don't look around for newr/better apps, especially for more sensitive parts, and keep on delivering old stuff which is rotten from inside.

One of the first things I do when I install Ubuntu is install WICD.  The fact that it has profiles, the ability to run scripts upon connecting/disconnecting, and EASY configuring of static network settings just makes it infinitely better than Network Manager.

---

### Post by realn on 2008-10-16
Yes,

It seems so simple & user-friendly. In addition, I see that the daemon connects to the network without having an X server running. That's so nice.
I will do the same thing from now on - install wicd as my first app.

 Thanks again.

---

### Post by realn on 2010-07-20
Even in Lucid Lynx the network manager and its obnoxious kwallet are getting on my nerves. still using wicd. Marked as solved.

---

### Post by cariboo on 2010-07-20
If the op marked the thread as solved, I'll close it.

---

