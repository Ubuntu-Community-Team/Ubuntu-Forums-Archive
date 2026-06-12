---
title: "Wine to install windows drivers?"
date: 2010-02-25
forum: Wine
---

### Post by spunkybd on 2010-02-25
I have a D-link 130, I searched on here and found people installing them using all sorts of cammand prompts and what not.. Im very new, virgin like, to the whole ubuntu OS.


So iwas wondering if i could use wine to install my windows drivers for the D-link DWA130

---

### Post by gsmanners on 2010-02-25
Wine isn't suitable for drivers. You'll want to use Ndiswrapper instead.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by kozhi on 2010-02-26
Hi! My issue is about using windows application supplied with my USB connected HP scanner (Scanjet G3010). The application has one of the best OCRs I have come across (I can't seem to get something better in Ubuntu). When I try to install the application under WINE, the installation window starts fine, but then stops at the point where presumably it is supposed to detect the USB where the scanner is connected (please see the screenshot). I understand that there is some issue with WINE not configured or mapped to detect USB connected devices. I also can't seem to located any similar issue in any of the forums. Any suggestions? Thanks a lot.

---

### Post by pbpersson on 2010-02-26
Have you looked at [this article]("http://wiki.winehq.org/USB") about getting USB devices to work with Wine?

---

### Post by kozhi on 2010-02-26
Yes, I had already visited that link before posting here. Couldn't make much sense out of it, being quite new to Linux...I mean I am using Ubuntu for close to a year & half now, but so many things work of of the box that I don't really need to go into complicated things.

Anyway, after seeing pbpersson's post, I revisited the wine link, and then following it, another page ([http://wiki.winehq.org/GitWine](http://wiki.winehq.org/GitWine)). At the terminal, I entered:
git clone git://source.winehq.org/git/wine.git ~/wine-git

The last line after a long series of lines at the terminal was:
Checking out files: 100% (6264/6264), done

Then:
cd ~/wine-git

So I am now into the wine-git directory??

Now I am stuck at ([http://wiki.winehq.org/USB):](http://wiki.winehq.org/USB):)

git am *.txt

 What is this '*'? I understand that its supposed to be a patch, and when I click on the first patch in the link ([http://wiki.winehq.org/USB](http://wiki.winehq.org/USB)), its a long long txt file.

Then, I am supposed to "For using native USB driver should copy HKLM\System\CurrentControlSet\Enum\USB\Vid_<vid>&Pid_<pid> and HKLM\System\CurrentControlSet\Services\<driver_name> from Windows registry, for example....." ([http://wiki.winehq.org/USB](http://wiki.winehq.org/USB))

What do I do with this?:confused:

---

### Post by dino99 on 2010-02-26
don't understand why you used wine (latest 1.1.39)

[http://sourceforge.net/projects/hp3900-series/](http://sourceforge.net/projects/hp3900-series/)

[http://www.linuxforums.org/forum/wine/94500-serial-ports-wine.html](http://www.linuxforums.org/forum/wine/94500-serial-ports-wine.html)

if you can't with wine, try virtualbox if xsane is not enough for your needs

---

### Post by pbpersson on 2010-02-26
> **dino99 said:**
> 

if you can't with wine, try virtualbox if xsane is not enough for your needs

The OP is trying to use OCR software for Windows - so no, they cannot use XSane.

I think the solution I provided is a hack to allow the program in Wine to find the device in the Linux kernel....but having not tried the solution I would not know the exact steps to follow.  Right now I cannot look at this as I am leaving on a weekend trip.

---

### Post by pbpersson on 2010-02-26
> **kozhi said:**
> Yes, I had already visited that link before posting here. Couldn't make much sense out of it, being quite new to Linux...I mean I am using Ubuntu for close to a year & half now, but so many things work of of the box that I don't really need to go into complicated things.

Anyway, after seeing pbpersson's post, I revisited the wine link, and then following it, another page ([http://wiki.winehq.org/GitWine](http://wiki.winehq.org/GitWine)). At the terminal, I entered:
git clone git://source.winehq.org/git/wine.git ~/wine-git

The last line after a long series of lines at the terminal was:
Checking out files: 100% (6264/6264), done

Then:
cd ~/wine-git

So I am now into the wine-git directory??

Now I am stuck at ([http://wiki.winehq.org/USB):](http://wiki.winehq.org/USB):)

git am *.txt

 What is this '*'? I understand that its supposed to be a patch, and when I click on the first patch in the link ([http://wiki.winehq.org/USB](http://wiki.winehq.org/USB)), its a long long txt file.

Then, I am supposed to "For using native USB driver should copy HKLM\System\CurrentControlSet\Enum\USB\Vid_<vid>&Pid_<pid> and HKLM\System\CurrentControlSet\Services\<driver_name> from Windows registry, for example....." ([http://wiki.winehq.org/USB](http://wiki.winehq.org/USB))

What do I do with this?:confused:

That article does not provide much detail.  Have you Googled to find other articles where people have actually done this?

The ```
git am *.txt
``` seems to indicate that git is an application, you are providing the am as a parameter, and the *.txt is the list of files it is going to act upon.

The article gets increasingly vague towards the end, I am not certain what you are supposed to do with the registry stuff.  I would assume you are grabbing registry entries from a genuine Windows machine where you have installed this device, inserting these registry entries into Wine, and then modifying them to somehow point to Linux kernel entries to establish a link but there are details missing from the instructions

---

