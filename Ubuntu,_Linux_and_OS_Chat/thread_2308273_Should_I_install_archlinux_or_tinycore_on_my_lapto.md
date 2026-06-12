---
title: "Should I install archlinux or tinycore on my laptop?"
date: 2016-01-01
forum: Ubuntu, Linux and OS Chat
---

### Post by martin183 on 2016-01-01
I am very new to linux but don't mind a LINing curve as long as there is light at the end of the tunnel :).
  I have a new/old 256 meg laptop I want to install on.
  I was looking for the leanest command line only distros and arch and tinycore kept popping up as recommendations.
  I have been playing around a little with both but have yet to install either.
  By the way I only really need to rdp to my main windows computer from  other parts of my apartment so I don't require anything but the bare  bones. 
  I liked the bare bones philosophy initially of microcore however  there is alot less documentation than with the arch and almost non  existent vs huge community respectively. 
  I got stuck so far with microcore install trying to setup my usb  wireless device. Where arch layed all the info out in a wiki and the  tools were already there for me to use,  with micro I would try several  of the same commands only to find they weren't there.
  So I'm unsure whether it's worth proceeding with micro? I don't mind  the extra work but is it going to be easy enough to setup wlan on it? if  so how do I do it? and will it be more plain sailing then once I have  internet access on there and I can just wget what I need? or are there  many more hurdles to climb?

---

### Post by matt_symes on 2016-01-01
Hi

What chip does it have ?

Something that old may be missing the cmov cpu instruction.

BTW: I also have a laptop that old. A dell latitude c510/c610.

Kind regards

---

### Post by grahammechanical on 2016-01-01
> is it going to be easy enough to setup wlan on it?

You have answered that yourself. Do you not think so? You need an ethernet connection first. As you need to download a package to use to set up a WiFi connection

[http://wiki.tinycorelinux.net/wiki:setting_up_wifi](http://wiki.tinycorelinux.net/wiki:setting_up_wifi)

> If you want to set up wifi with minimum of fuss, just install wicd  package (and its dependencies) from the package repository. You will  then be able to setup your connection in a user-friendly GUI.

>  **TIP**: For a system that doesn't have wired access, you  may find it easier to download the wicd package files and its  dependencies first and store them some place convenient. You can then  load them into tinycore using the tce-load command 

   

Regards.

---

### Post by martin183 on 2016-01-02
I've installed the microcroe/tinycore OS fine now using a wired connection but for the wireless it is a USB wifi and it isn't seeing the device. I know it will work with linux though since I got it working on arch linux when I was trying that. 

But non of the default command utils are on this tinycore version. All the commands are not found. So how do I go about getting it to see my usb wifi? 

Its really a nuisance trying to search for relevant things because I keep getting the same 'install tinycore to usb stick' all the time rather than stuff related to setting up usb devices for the OS.

---

### Post by martin183 on 2016-01-02
I think I just need to install the driver for the usb wireless device.

---

### Post by martin183 on 2016-01-02
Sorted. I had to first find out how to access and then use a few of the package from the tinycore repos.

---

### Post by kevdog on 2016-01-02
What's wrong with installing arch base system?  It's pretty lean without all the extra crap. Arch very well supported and the wiki pages are very well documented.  I'm thankful a lot of people with knowledge have contributed to them. If planning to use a specific distro for awhile I think you need a community when you run into problems so you can troubleshoot and ask questions.  Arch linux forums aren't the nicest people -- however they are extremely knowledgeable.

---

### Post by QDR06VV9 on 2016-01-02
> [COLOR=#000000]Arch linux forums aren't the nicest people -- however they are extremely knowledgeable.[/COLOR]
:D So True...But there is one out there that has a handful of good(Helpful) posters there(Old Ubuntu users).[URL="https://forum.manjaro.org/"]
Manjaro Forum[/URL]
But I have yet to find a forum like this one.
Kind Regards

---

