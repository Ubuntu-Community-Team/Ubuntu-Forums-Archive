---
title: "What is the easiest way to install ubuntu on tablet"
date: 2016-11-07
forum: Ubuntu Phone and Tablet
---

### Post by irraref on 2016-11-07
Hello,
I have an old samsung galaxy tab 2 and I would like to install ubuntu. I must say I am really unexperienced with this issue.

Is there an easy way as for desktop? I mean with a GUI?

Thanks

---

### Post by wlbi on 2016-11-08
> **irraref said:**
> Hello,
I have an old samsung galaxy tab 2 and I would like to install ubuntu. I must say I am really unexperienced with this issue.

Is there an easy way as for desktop? I mean with a GUI?

Thanks
Just a simple answer: You can't just do this.
[B]why?
[/B]Most of the smartphones and tabs are **not** i368 or amd64 CPU, they are using an ARM CPU.
ARM CPU don't have a [COLOR=#242729][FONT=Arial]PCI bus for [/FONT][/COLOR]hardware detection. This means each device needs his own special build operating-system, fitting exactly to this specific hardware.
There is not only one Galaxy Tab 2, there are many different kind of hardware.
p3110, p3100, p5110
Here you can see, that already somebody startet to do that work: [https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)
But is was discontinued 2013. Because it is a huuuge work...
Here a demo from 2013 on Tab 2 [https://www.youtube.com/watch?v=KQH2rlEgnJE](https://www.youtube.com/watch?v=KQH2rlEgnJE)

Here [COLOR=#000000][FONT=arial]Marius [/FONT][/COLOR]Gripsgard is developing Ubuntu Touch for different devices: [https://devices.ubports.com/#/](https://devices.ubports.com/#/)

---

