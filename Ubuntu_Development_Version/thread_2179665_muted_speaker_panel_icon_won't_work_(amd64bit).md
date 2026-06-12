---
title: "muted speaker panel icon won't work (amd64bit)"
date: 2013-10-09
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-10-09
The speaker icon is muted by default and when I go to "unmute" it , it shows a different pull down menu /Indicator Plugin/Move/Remove/Panel/ on the right click and this little white bar on the left click.

Regards..

Xubuntu - amd64 .. daily fully installed:

---

### Post by ventrical on 2013-10-09
Ok.. I went to Settings/Panel to customize the panel and I see now that the little speaker icon is called "Indicator Plugin" and thats what I get when I right click the icon on the panel. So somthing is wrong here..?

---

### Post by Elfy on 2013-10-09
Sounds like [https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204)

---

### Post by OrangeCrate on 2013-10-09
> **Elfy said:**
> Sounds like [https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204)

That's it.

Frankly, I didn't participate in that bug report, because, when I saw that the indicator-sound package didn't work, I just deleted it. My laptop buttons for sound work fine (Lenovo T400), and I have access to the Pulse Audio controls through the Applications Menu, so, I'm all good. I'm not a fan of clutter, so, I'll probably leave it like that, even if it is fixed.

Which brings up a concern/observation. There has always been a lot of leftover bugs that are never fixed on each new release. I don't hold out much hope for a better track record on fixes now that we're using a 9 month release cycle between LTS releases. Personally, like this conversation, if I can figure out a workaround that works for me, I'm beginning more and more to just forget about/ignore bugs. If they get fixed, fine. If not, whatever...

Edit:

LTS development cycles deserve a lot of attention and work by all community members. My comments above refer to the interim releases only, such as 13.10.

---

### Post by ventrical on 2013-10-09
> **OrangeCrate said:**
> That's it.

Frankly, I didn't participate in that bug report, because, when I saw that the indicator-sound package didn't work, I just deleted it. My laptop buttons for sound work fine (Lenovo T400), and I have access to the Pulse Audio controls through the Applications Menu, so, I'm all good. I'm not a fan of clutter, so, I'll probably leave it like that, even if it is fixed.

Which brings up a concern/observation. There has always been a lot of leftover bugs that are never fixed on each new release. I don't hold out much hope for a better track record on fixes now that we're using a 9 month release cycle between LTS releases. Personally, like this conversation, if I can figure out a workaround that works for me, I'm beginning more and more to just forget about/ignore bugs. If they get fixed, fine. If not, whatever...

Edit:

LTS development cycles deserve a lot of attention and work by all community members. My comments above refer to the interim releases only, such as 13.10.


 I just removed it , stuck in a audio CD and parole media player came on and just about blew me out of my chair ! :) <had volume at high on my amp. :) lol

Thanks elfin and orangecrate.

regards..

---

### Post by ventrical on 2013-10-09
Editing out duplicate entry.

btw .. as the parole media player was palying it affected the network .  I had problems getting staying on line and my sp even puked out one of those proprietary DSL screens at me :) lol

---

### Post by pqwoerituytrueiwoq on 2013-10-09
i posted a workaround for that in [comment 41](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204/comments/41), based on [comment 5](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204/comments/5)
my workaround should make a system with multiple DEs happy, also happy with multiple sessions with varying DEs

---

### Post by Elfy on 2013-10-10
There is work going on to get gtk3 indicators in, I've got them going on my machine.

---

### Post by pqwoerituytrueiwoq on 2013-10-10
well i really hope it makes it into the final ISO, a broken volume indicator on the live ISO will leave a bad impression

---

### Post by QDR06VV9 on 2013-10-10
```
elfy said There is work going on to get gtk3 indicators in, I've got them going on my machine.
```
Ya I'm going to wait for this one to geat fixed, I suffer like ventrical losing my net also!;)
Besides Gnome & KDE on 5 installs has kept me hoppin lately:p

---

### Post by ventrical on 2013-10-11
> **pqwoerituytrueiwoq said:**
> well i really hope it makes it into the final ISO, a broken volume indicator on the live ISO will leave a bad impression


Thats exactly it.!! I want Xubuntu to work . I really like it .  But when I go  and try to install it in a noobs machine and all this stuff happens , it's a really hard sell, even for free !!

---

### Post by ventrical on 2013-10-11
> **runrickus said:**
> ```
elfy said There is work going on to get gtk3 indicators in, I've got them going on my machine.
```
Ya I'm going to wait for this one to geat fixed, I suffer like ventrical losing my net also!;)
Besides Gnome & KDE on 5 installs has kept me hoppin lately:p


And I get that on stable too and tried to participate all in good faith .. and then menu items from the pull down menus just start disappearing out of nowhere (but thats off topic on this one )  :) lol

---

### Post by Elfy on 2013-10-11
> **ventrical said:**
> And I get that on stable too and tried to participate all in good faith .. and then menu items from the pull down menus just start disappearing out of nowhere (but thats off topic on this one )  :) lol

I've not seen a bug for that.

---

### Post by ventrical on 2013-10-11
> **Elfy said:**
> I've not seen a bug for that.


  I  believe (but am not 100% sure) that I put a bug up during 12.04 on that or during quantal and it would not let me file a bug .. so I just gave up.  I guess my comments are not fair comments because I use Unity DE  a greater percentage of the time. My bad.

---

