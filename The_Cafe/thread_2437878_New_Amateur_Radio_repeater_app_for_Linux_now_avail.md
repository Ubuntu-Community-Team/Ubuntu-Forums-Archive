---
title: "New Amateur Radio repeater app for Linux now available"
date: 2020-03-02
forum: The Cafe
---

### Post by NoBugs! on 2020-03-02
Greetings all,

Recently I was very surprised that there were zero ham radio repeater apps for Ubuntu/linux. Especially since there are going to be several Linux based phones, and there already are a couple repeaterbook-type apps for ios/Android. I have been writing howtos on some of the steps to build this at [https://howtotrainyourrobot.com/](https://howtotrainyourrobot.com/)

Just this weekend I uploaded the first version of [Repeater-START]("https://github.com/programmin1/Repeater-START"). 
This not only is open source software for Ubuntu/Linux, the repeater listing is freely usable without a recurring fee or restriction to redistribute.

Like Repeaterbook on Android, this new app shows nearby repeaters and distance. It also shows them on a map! Also, for certain rtlsdr devices that are set up to your computer, it should let you click play in the corner and listen in on the frequency to see how well used that repeater is.
Hope this is useful for any other Ham radio folks here.

Have a great week,
Luke

---

### Post by EuclideanCoffee on 2020-03-04
Would any of these applications be relevant to you?

[https://www.debian.org/blends/hamradio/get/metapackages](https://www.debian.org/blends/hamradio/get/metapackages)

---

### Post by NoBugs! on 2020-03-07
Not really, I don't have a radio that interfaces for HF radio and packet/winlink stuff. Mostly I thought there should be a repeater app for Linux and Librem phone and built this along with a repeater listing.

---

### Post by Skaperen on 2020-03-08
are SDR interfaces all alike to make this widely workable?  de KA9WGN

---

### Post by NoBugs! on 2021-01-02
I attempted to get it to play via rtlsdr device (the play button)
That portion of the code probably needs more work. It is all on Github if you want to take a look - [https://github.com/programmin1/Repeater-START](https://github.com/programmin1/Repeater-START)
I have published version 0.6 recently with maidenhead-grid-square-locator search and display btw: [https://sourceforge.net/projects/repeater-start/files/](https://sourceforge.net/projects/repeater-start/files/)

---

