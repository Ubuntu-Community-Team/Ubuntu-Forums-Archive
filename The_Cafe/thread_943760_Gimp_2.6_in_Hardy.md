---
title: "Gimp 2.6 in Hardy?"
date: 2008-10-10
forum: The Cafe
---

### Post by Giant Speck on 2008-10-10
Hello.

This may be a stupid question, but is Gimp 2.6 installable in Hardy?

Because for some reason when I tried to run the .deb from getdeb, it told me I needed to install gimp-data for Gimp 2.6, and when I went to do that, it broke.

I had to reinstall Gimp 2.4.6, and now it runs really slowly.  When I go to uninstall it, it uninstalls ubuntu-desktop.

If it's possible to install 2.6 in Hardy, can someone give me solid instructions to do so, please?

Thanks,
Giant Speck

---

### Post by SunnyRabbiera on 2008-10-10
you need to download all the packages on getdeb listed for the gimp.
There isnt just 1, there are 6.
Also it might help to remove your current gimp first.

---

### Post by shadylookin on 2008-10-10
> **Giant Speck said:**
> Hello.

This may be a stupid question, but is Gimp 2.6 installable in Hardy?

Because for some reason when I tried to run the .deb from getdeb, it told me I needed to install gimp-data for Gimp 2.6, and when I went to do that, it broke.

I had to reinstall Gimp 2.4.6, and now it runs really slowly.  When I go to uninstall it, it uninstalls ubuntu-desktop.

If it's possible to install 2.6 in Hardy, can someone give me solid instructions to do so, please?

Thanks,
Giant Speck

I think 2.4 is in the repositories. 2.6 doesn't seem to be. 

You can compile 2.6 from source, but I'll warn you ahead of time that doing so is a royal pain.

---

### Post by Giant Speck on 2008-10-10
> **SunnyRabbiera said:**
> you need to download all the packages on getdeb listed for the gimp.
There isnt just 1, there are 6.
Also it might help to remove your current gimp first.

Yes, I know I should remove Gimp 2.4 first, but how do I resolve the issue where uninstalling Gimp 2.4 also uninstalls ubuntu-desktop?

Or would this repository issue be fixed by installing Gimp 2.6?

---

### Post by ajgreeny on 2008-10-10
I have already installed gimp 2.6 in Mint 5 without any problem.  On the getdeb page right click on all 6 packages and download them all to a new temporary folder (call it, for example, gimp26).  Now navigate to that folder in terminal cd /path/to/gimp26 and then simply use sudo dpkg -i *.deb  All the packages will be installed and should run with no problem.

I don't know if it is necessary to uninstall gimp 2.4.5 first, but it is easy enough to do with synaptic, and if you do so, I don't think it will remove ubuntu-desktop any more, as it used to.

---

### Post by ilrudie on 2008-10-10
I did not uninstall gimp 2.4 before installing gimp 2.6.  I followed the instructions [here]("http://phorolinux.com/how-to-install-gimp-26-on-linux.html#more-147") [phorolinux.com] and it works like a champ on 32-bit Hardy.  I had one issue with a broken dependency but synaptic cleared it up and I have not noticed any issues so far.

---

### Post by niccholaspage on 2008-10-10
> **Giant Speck said:**
> Yes, I know I should remove Gimp 2.4 first, but how do I resolve the issue where uninstalling Gimp 2.4 also uninstalls ubuntu-desktop?

Or would this repository issue be fixed by installing Gimp 2.6?
Removing Ubuntu-desktop should be fine. It is just a package which installs other packages. Is it uninstalling something else?

---

### Post by Giant Speck on 2008-10-10
I got it installed.  :)

The mistake I was making is that I was trying to install gimp-data before installing any of the libraries.

---

### Post by niccholaspage on 2008-10-10
Cool. Gimp 2.6 is awesome.

---

### Post by Giant Speck on 2008-10-10
> **niccholaspage said:**
> Cool. Gimp 2.6 is awesome.

Yeah, but what I thought was weird is that I had to set the Toolbox and Layers windows on "Always on Top" so that they'd stay on the screen while editing.

I figured with this new interface, they'd stay on top anyway.

---

### Post by niccholaspage on 2008-10-10
I don't really like the two windows. I liked it with only 1.

---

### Post by ajgreeny on 2008-10-11
> **niccholaspage said:**
> I don't really like the two windows. I liked it with only 1.
Which two windows?  In my old version of gimp there were 3 windows not one.  I prefer the new 2.6 layout personally and think it is a great move forwards.  As I said, so far I only have it on my Mint 5 installation, which I use to test things out, but not yet put it onto my Hardy Heron install.  That will come soon, if I don't upgrade to 8.10 first.

---

