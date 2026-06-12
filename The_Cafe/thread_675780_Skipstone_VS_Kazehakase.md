---
title: "Skipstone VS Kazehakase"
date: 2008-01-23
forum: The Cafe
---

### Post by RAV TUX on 2008-01-23
[Skipstone 0.9.8]("http://www.muhri.net/skipstone/page.php3?node=home") was just released on 01/22/2008, I was wondering how Skipstone is, in contrast to [Kazehakase]("http://kazehakase.sourceforge.jp/")?

Has anybody here been using both Skipstone and Kazehakase for a while now and following the development of both?


What are your thoughts on the two?

---

### Post by orange2k on 2008-01-23
I tried Kazehakase, but it isn`t that much different from Epiphany or FF2, because it uses the Gecko 1.8 engine.

For this reason I installed FF3 beta. This way Im able to view some sites that wouldnt be rendered properly otherwise.

What engine does Skipstone use?

---

### Post by RAV TUX on 2008-01-23
> **orange2k said:**
> 

What engine does Skipstone use?

Same as Kazehakase.

---

### Post by RAV TUX on 2008-02-05
bump

---

### Post by koleoptero on 2008-02-05
I saw this at gnomefiles.org rss feed:
> 
Skipstone v1.0.0


About this version

Added Support for Apple WebKit through Gtk+ bindings and a few bugfixes.

Does this mean that skipstone uses the webkit or that you are able to make it use it?:confused:

---

### Post by muhri on 2008-02-05
Hello,

Yes, Apple WebKit support has been added to version 1.0.0 - Although, Gtk+ bindings for webkit are still a bit buggy. To compile SkipStone using webkit, install a nightly build of webkit from [http://www.webkit.org](http://www.webkit.org) and then cd skipstone-1.0.0/src and make -f Makefile.webkit.

Regards,

---

### Post by koleoptero on 2008-02-05
Thanks for the tip muhri. I'll give it a try. :)

---

### Post by SunnyRabbiera on 2008-02-05
Skipstone is kind of ancient compared to Kazehakase, I have used skipstone in the past but its really a dinosaur.

---

### Post by muhri on 2008-02-05
> **SunnyRabbiera said:**
> Skipstone is kind of ancient compared to Kazehakase, I have used skipstone in the past but its really a dinosaur.

Hi SunnyRabbiera,

Well, that depends on your definition of ancient and I try not to be biased here :)

Ancient: True, development began in August 2000 when I was a master's student and continues till today.

Ancient: Does not provide a lot of bells and whistles? Its intended this way so that it be light and with a few dependencies. However, its pluggable so you can write your own plugins if you like.

Ancient: In the sense that its not for everyone, Yes. It is intended for people who want practicality and lightness. I'm one of those :)

Dinosaur? Not at all, on the contrary, quite light.

Kaze is great and has lots of customizable features, plugins and uses lots of rendering engines as well - my guess would be try both of them (they do the same job at the end) and see which one you feel most at home with.

Regards,

---

