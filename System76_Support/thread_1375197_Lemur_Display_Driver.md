---
title: "Lemur Display Driver"
date: 2010-01-07
forum: System76 Support
---

### Post by cheuschober on 2010-01-07
Hello System76.

We received a pair of lemurs that we're absolutely thrilled about but we're having issues with the display driver.

The short version of the story is that we're forced to use redhat or redhat variants like Fedora because the business mandates the use of Lotus Notes throughout and the only linux version of Lotus Notes we have access to is a RedHat x86 version that we just were not able to get working in Ubuntu.

In any case, we've tried Fedora 12 x86_64 (Fedora handles multi-arch for Notes, seamlessly) which we seemed to get to work with one exception -- the display driver.

From what I've read you use some custom patches on the Lemurs. Would it be possible for me to get a copy of those patches on the understanding that it's an 'unsupported configuration' ?

Regards,
cheuschober

---

### Post by thomasaaron on 2010-01-07
We don't patch the video driver for the Lemur. It has Intel GMA 4500MHD graphics, which is supported out of the box by Ubuntu.

Ubuntu uses the xserver-xorg-video-intel driver. Is there an equivalent in Fedora?

Did you try to use alien to convert the Notes .rpm to a .deb? I've never tried it with Lotus Notes, but I've had a few success stories with it.

Edit: The first two threads here...
[http://www.google.com/#hl=en&source=hp&q=how+to+lotus+notes+on+ubuntu&aq=f&aqi=&oq=&fp=e8d6ef47431c6a4a](http://www.google.com/#hl=en&source=hp&q=how+to+lotus+notes+on+ubuntu&aq=f&aqi=&oq=&fp=e8d6ef47431c6a4a)
...look interesting, but I can't tell if they are using the Red Hat version or not.

---

