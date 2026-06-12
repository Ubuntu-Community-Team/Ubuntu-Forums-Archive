---
title: "Breezy update on laptop went great"
date: 2005-10-18
forum: Testimonials &amp; Experiences
---

### Post by moephan on 2005-10-18
I saw that a few people were sharing their experiences with upgrading to Breezy on laptops. Here's mine.

I have a refurbished Dell Latitude that I picked for $470 at a neighborhood computer service and sales place. They threw in a D-Link DWL G630 wireless card with it. It came without an OS, and I installed Hoary on it from CDs. It worked fine with ndswrapper, and some tweaks to etc/esound/esd.conf. I am pretty new to Linux. I ran Fedora for a while, and then warty and hoary on my previous laptop, and now hoary and breezy on this laptop. I use the web, play games, do office apps, and do some hobbyist c++ development and javascript web development.

I upgraded by changing all the references in the Synaptic repository dialog to point to Breezy instead of Hoary. The update went well, and Breezy seems to work even better on this laptop then Hoary did. A couple of notes:

1.The first time through the install, I clicked on the &#8220;terminal&#8221; disclosure triangle. This was a huge mistake, as it turned the update into an interactive process. I somehow aborted the update and the installer had to download a bunch of stuff again.
2.The installer noticed that I had updated esd.conf, and wanted to know if I wanted to let it put it's own version on. I didn't really know what to do, so I let it. Later I realized that I had to tweak the file to get sound working properly again. I had done this a couple of months ago in hoary, and had to redo it.
3.The installer put down the madwifi drivers for my wireless card, so I don't have to use ndiswrapper anymore. My wireless works much better now. It connects every time I boot with no intervention, and it doesn't seem to drop the connection. I used synaptic to remove ndiswrapper. I was very impressed that it just worked like that.
4.Every app seems to work great after the upgrade. Gnome seems more responsive. It installed OpenOffice 2, which seems to be working very well, but it left the old version of Open Office.
5.The new boot screen is a little nicer. All of my desktop customizations were maintained just fine.
6.Firefox turned on ipv6 after the install. To use the web I had to go through &#8220;about:config&#8221; and set network.dns.disableIPv6 to true.
7.Hibernate works now. I'm not sure that it didn't work before, but I remember trying it once and being very confused by the behavior. In any case, if I choose &#8220;Hibernate&#8221; from the logout window it seems to work fine.

Cheers, Rick

---

### Post by aysiu on 2005-10-19
I'm putting this in the testimonial archive.

---

