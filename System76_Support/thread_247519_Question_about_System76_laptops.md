---
title: "Question about System76 laptops"
date: 2006-08-30
forum: System76 Support
---

### Post by manzuk on 2006-08-30
I'm considering buying one of your laptops, but I've got some questions before taking the final decission:

1)Is there any way I can get them with Kubuntu installed instead of Ubuntu?
2) On which of them can I use XGL? al least with some effects disabled ( can't live without it now :D)
3)Where can I find high resolution pictures of the notebooks? (so as to check them better)

Thank you!

---

### Post by Omnios on 2006-08-30
Hi this is not what you asked about but the new Intel laptop chipset just came out so waiting a bit before buying might result in a better price or better hardware for the system you want to buy

---

### Post by crichell on 2006-08-30
Hello Manzuk

> 1)Is there any way I can get them with Kubuntu installed instead of Ubuntu?
We only provide Ubuntu out of the box.  You can install Kubuntu when you receive your laptop with the command:
```
sudo apt-get install kubuntu-desktop
```
> 2) On which of them can I use XGL? al least with some effects disabled
Testing XGL throughout our line is on our list of things to do.  XGL should run on all of our machines but I can't tell you for sure.  I know you can run XGL on the Serval and Bonobo laptops.
> 3)Where can I find high resolution pictures of the notebooks?
You can get a closer look by clicking on the images to enlarge.  The pictures on the website are what we have available.

---

### Post by user1397 on 2006-08-31
> **crichell said:**
> You can install Kubuntu when you receive your laptop with the command:```
sudo apt-get install kubuntu-desktop
```I would recommend giving the aptitude version of this command to your customers, crichell, as it can lead to happier customer satisfaction.  ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```installs the kubuntu desktop system, but with a simple ```
sudo aptitude remove kubuntu-desktop
``` kubuntu can be removed entirely, whereas with apt-get nothing would get removed.

---

### Post by crichell on 2006-09-01
Thanks for the suggestion.  Installation with the option to remove is a much better method.

---

### Post by manzuk on 2006-09-04
Omnios, when you say "*new Intel laptop chipset just came out*", which ones are you talking about?

---

### Post by kostkon on 2006-09-04
> **manzuk said:**
> Omnios, when you say "*new Intel laptop chipset just came out*", which ones are you talking about?

He/she means the [Core 2 Duo processors]("http://www.intel.com/products/processor/core2duo/").

---

