---
title: "Updates on Mir display server, Ubuntu Edge fails to gain funding"
date: 2013-09-05
forum: Ubuntu, Linux and OS Chat
---

### Post by QDR06VV9 on 2013-09-05
Mods please move this thread if you want.
found this interesting.. from here-[http://distrowatch.com/weekly.php?issue=20130826#news]("http://distrowatch.com/weekly.php?issue=20130826#news")
> Jono Bacon, the Ubuntu community manager at Canonical, has posted some updates regarding Canonical's plans for the Mir display server technology. The new display server, which Canonical hopes to deploy on desktops, laptops, phones and tablets, has generated a lot of interest over the past few months. Some Ubuntu-based projects are moving to adopt the new technology, others are avoiding it in favour of the competing Wayland display protocol. Mr Bacon writes: "Our goal has been clear that in Ubuntu 13.10 we will include Mir by default for cards that support it and fall back to X for cards that don't (primarily those that require proprietary graphics drivers). In 14.04 we will deploy Mir but not provide the X fallback mode, and we are in active discussions with GPU manufacturers for them to support Mir in their drivers." While Mir is still under heavily development and therefore not yet ready for day-to-day usage, people interested in trying Mir can find packages for the display server in the Ubuntu 13.10 software repositories.

Kevin Gunn, who leads the Display Server team at Canonical, has some further updates which dig more into the technical nature of Mir. Gunn's status update covers Mir/Unity support, driver support, multi-monitor successes & problems and fallback support using X. Gunn also lays out some details as to what features and bug fixes are in the works and should be complete before Mir lands in the next Ubuntu long term support release.

Canonical is always experimenting, whether it is with display servers, desktop environments or phones. A month ago Canonical launched an Indiegogo fund raising project in an attempt to fund development of an Ubuntu-powered phone. While the funds came in fast at first, they eventually trickled to a halt. The Ubuntu Edge project managed to pull in approximately $12.8 million dollars of the required $32 million, which means backers will be refunded and Ubuntu fans will have to wait for mobile carriers to ship devices powered by Ubuntu. Not all experiments yield positive results, but it looks as thought Canonical has successfully tested the waters and are now aware just how much of the mobile market is interested in running Ubuntu on hand held devices.

* * * * *
[Linux] Do you have USB devices which regularly disconnect when they are plugged into your Linux-powered computer? If so it may not be a fault of the device as some people have long thought. Sarah Sharp, who has been working on USB drivers in the Linux kernel for eight years and who was at the forefront of bringing USB 3.0 support to the kernel, has made an interesting discovery. Namely, it seems that the core USB system does not give USB devices long enough to wake up which can cause disconnects. "If the USB core attempts to access those ports while the device is still coming out of resume, such as issuing transfers to the device, or resetting the port, the device will disconnect, or transfer errors will occur. This causes the USB core to mark the device as disconnected." No doubt we will soon see a fix for this issue arriving in future kernel updates.

---

### Post by Yougo on 2013-09-05
a bit of a bold statement, axing the x fallback mode in 14.04. if mir drivers haven't landed by then (quite probably) people will not only have to install the proprietary drivers, but set up the entire X stack as well? :-?

also, what about those apps that will take after Wayland? through what will they run on a mir machine?

that USB issue, i've noticed lately. it was a USB printer, and i just re-plugged it, but i found it odd indeed. *shrug* though i think it could get nasty if you're doing more vital things.

---

### Post by grahammechanical on 2013-09-05
This is not news. Did anyone listen/watch the 4 mir sessions at vUDS? I will tell you something that may or may not shock you, by 14.10 the xserver code will not be in the ubuntu distribution. It makes sense. Mir is to replace Xserver so there is no point in maintaining a code base that is no longer required. But that also is old news.

And there is more. Compiz will not be in 14.04 if everything goes according to plan. I specifically asked a question to confirm that. Please note this quotation from the MIR wiki specification.

> However, Wayland support could be added either by providing a  Wayland-specific frontend implementation for our display server or by  providing a client-side implementation of libwayland that ultimately  talks to Mir.

[https://wiki.ubuntu.com/Mir/Spec](https://wiki.ubuntu.com/Mir/Spec)

libwayland is in Saucy Salamander and I have seen updates to it. So, it is not a dead library. Wayland is after all just a protocol. Are there any Wayland apps? Is there a distro using Wayland/Weston?

Please move this to the section on Ubuntu, Linux and other OS chat.

---

### Post by Toz on 2013-09-05
> **grahammechanical said:**
> Please move this to the section on Ubuntu, Linux and other OS chat.

Moved.

---

### Post by QDR06VV9 on 2013-09-06
> **grahammechanical said:**
> This is not news. Did anyone listen/watch the 4 mir sessions at vUDS? I will tell you something that may or may not shock you, by 14.10 the xserver code will not be in the ubuntu distribution. It makes sense. Mir is to replace Xserver so there is no point in maintaining a code base that is no longer required. But that also is old news.

And there is more. Compiz will not be in 14.04 if everything goes according to plan. I specifically asked a question to confirm that. Please note this quotation from the MIR wiki specification.



[https://wiki.ubuntu.com/Mir/Spec](https://wiki.ubuntu.com/Mir/Spec)

libwayland is in Saucy Salamander and I have seen updates to it. So, it is not a dead library. Wayland is after all just a protocol. Are there any Wayland apps? Is there a distro using Wayland/Weston?

Please move this to the section on Ubuntu, Linux and other OS chat.

Thanks  grahammechanical
and also howefield for fixing Quote

---

