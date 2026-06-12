---
title: "increased RAM"
date: 2011-09-24
forum: The Cafe
---

### Post by Linux_junkie on 2011-09-24
On Thursday I ordered 1GB of RAM for my Dell OptiPlex 170L desktop computer and by Friday morning it dropped through my letterbox.  Did not expect it to arrive so early!

Anyway, I installed it in  to my Dell and switched on.   I'm currently running Xubuntu 10.10 with both the XFCE and LXDE desktops installed. For the first time since using this computer it has felt a joy to use it with no slow down of system when running applications.

Just to try it out, I booted the computer from a live CD of Fedora 15 (Gnome); openSUSE 11.4 (KDE); Ubuntu 11.04 (Gnome / Unity); Kubuntu 10.10 (KDE).

With Fedora 15 all went well during its boot up sequence but it was only until it displayed the GUI that a problem arrose in that my on-board graphics chip was unable to handle the code for Gnome-shell and so it went in  to fall-back mode.  Overall I was happy that this machine is able to run Gnome 3.

With openSUSE  11.4 once again the boot up sequence went ok, however, when it loaded up the GUI there was problems displaying it.

The same problem with the display occurred with Ubuntu 11.04 but with Kubuntu 10.10 it was able to display the GUI only it did not display the translucent effect of KDE4.

Overall, apart from the display problems suffered in openSUSE and Ubuntu 11.04 I am quite pleased that when I come to upgrade from Next April I should be able to run Gnome 3 and KDE4 on this machine for the first time.

---

### Post by Gremlinzzz on 2011-09-24
Adding ram is a plus.:popcorn:

---

### Post by Ceiber Boy on 2011-09-25
I don't know of a specific answer to your enquiry, but my experience is that Linux is sensitive to RAM problems (I trust it was well packaged when it was 'dropped' through you letterbox!).

If you wanted to do an investigation you could reinstall your original RAM and boot your live CD gain, but if your installed OS works fine It might be worth just doing a memory test from the GRUB screen.

---

### Post by rjbl on 2011-09-25
> **Ceiber Boy said:**
> I don't know of a specific answer to your enquiry, but my experience is that Linux is sensitive to RAM problems (I trust it was well packaged when it was 'dropped' through you letterbox!).

If you wanted to do an investigation you could reinstall your original RAM and boot your live CD gain, but if your installed OS works fine It might be worth just doing a memory test from the GRUB screen.

We'd be interested to hear your experiences of GNU/Linux's 'sensitivities to RAM problems' Never noticed any myself, been in Linux since '95/96. 

Sure any 'puter will have issues if its RAM has problems, but 'in my experience' RAM module failures are extremely rare ( I've, personally, had one instance since 1984 and know of very, very few in all my many years working in very, very large corporate systems). The most usual cause of RAM issues on memory upgrade is mis-specifying memory type and/or mis-fitting the cards - easy to do on an older mobo, particularly where one fails to RTFM

rjbl

---

### Post by rjbl on 2011-09-25
> **Linux_junkie said:**
> On Thursday I ordered 1GB of RAM for my Dell OptiPlex 170L desktop computer and by Friday morning it dropped through my letterbox.  Did not expect it to arrive so early!

Anyway, I installed it in  to my Dell and switched on.   I'm currently running Xubuntu 10.10 with both the XFCE and LXDE desktops installed. For the first time since using this computer it has felt a joy to use it with no slow down of system when running applications.

Just to try it out, I booted the computer from a live CD of Fedora 15 (Gnome); openSUSE 11.4 (KDE); Ubuntu 11.04 (Gnome / Unity); Kubuntu 10.10 (KDE).

With Fedora 15 all went well during its boot up sequence but it was only until it displayed the GUI that a problem arrose in that my on-board graphics chip was unable to handle the code for Gnome-shell and so it went in  to fall-back mode.  Overall I was happy that this machine is able to run Gnome 3.

With openSUSE  11.4 once again the boot up sequence went ok, however, when it loaded up the GUI there was problems displaying it.

The same problem with the display occurred with Ubuntu 11.04 but with Kubuntu 10.10 it was able to display the GUI only it did not display the translucent effect of KDE4.

Overall, apart from the display problems suffered in openSUSE and Ubuntu 11.04 I am quite pleased that when I come to upgrade from Next April I should be able to run Gnome 3 and KDE4 on this machine for the first time.

Have you checked that you are using the right graphics driver? I am guessing that LiveCD's run on the distro's defaults and that when you get to do a full install you can blow the issue away just by loading up the current proprietary driver, which is easy to do with modern distro's

rjbl

---

### Post by mips on 2011-09-25
> **Linux_junkie said:**
> 
Overall, apart from the display problems suffered in openSUSE and Ubuntu 11.04 I am quite pleased that when I come to upgrade from Next April I should be able to run Gnome 3 and KDE4 on this machine for the first time.

You can always hunt around for a cheap second hand PCI GPU which should sort the graphics problems out as the Intel Extreme 2 chipset on that computer is kinda old and under powered.

The Dell Optiplex 170L only has PCI slots- no AGP, no PCI-Express.

Most powerful PCI cards will be ATI based but I dunno about driver support.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007853&IsNodeId=1&name=PCI](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007853&IsNodeId=1&name=PCI)

---

### Post by BrokenKingpin on 2011-09-26
> **Linux_junkie said:**
> I am quite pleased that when I come to upgrade from Next April I should be able to run Gnome 3 and KDE4 on this machine for the first time.
I am glad to hear that. That being said Xfce is better than KDE4 or Gnome3, but at least you can try them now to find out for yourself :P.

I have issues with the live CDs as well, mostly because the proprietary NVidia drivers will not be available on the Live CD. Once installed and I get the Nvidia driver installed everything is fine. Not sure why the open source Nvidia drivers do not play nice with Gnome3 or Unity.

---

