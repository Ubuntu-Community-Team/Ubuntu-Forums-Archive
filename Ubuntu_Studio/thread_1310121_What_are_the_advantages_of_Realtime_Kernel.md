---
title: "What are the advantages of Realtime Kernel?"
date: 2009-11-01
forum: Ubuntu Studio
---

### Post by psidrum on 2009-11-01
how is it faster compared to a regular kernel?

why would i want a realtime kernel?

does this affect all apps? will they run faster?

---

### Post by bandgeek on 2009-11-01
As I understand a realtime kernel is simply designed to reduce Xruns. It isn't a faster kernel.

[https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")

Just started to read this
[http://wiki.linuxmusicians.com/doku.php]("http://wiki.linuxmusicians.com/doku.php")

---

### Post by mobilediesel on 2009-11-01
> **psidrum said:**
> how is it faster compared to a regular kernel?

why would i want a realtime kernel?

does this affect all apps? will they run faster?

For normal desktop use you probably wouldn't notice much difference.
Here's a few links with more info:
[http://rt.wiki.kernel.org/index.php/Frequently_Asked_Questions](http://rt.wiki.kernel.org/index.php/Frequently_Asked_Questions)
[https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)
[http://en.wikipedia.org/wiki/Real-time_operating_system](http://en.wikipedia.org/wiki/Real-time_operating_system)

---

### Post by AutoStatic on 2009-11-02
> **psidrum said:**
> how is it faster compared to a regular kernel?It's not faster at all. It enables lower latency settings for soundcards.

> **psidrum said:**
> why would i want a realtime kernel?You'd want a real-time kernel when you're using your machine for audio production. It allows you to use real-time effects and like I said above it allows for lower latency settings (ie. with my Firewire soundcard I achieve a latency below 3ms with a real-time kernel).

> **psidrum said:**
> does this affect all apps? will they run faster?No. It won't affect any application, only the way drivers like ffado or snd-usb-audio behave.

---

