---
title: "eXeLearning in Hardy AMD64"
date: 2008-05-04
forum: Tutorials
---

### Post by ugm6hr on 2008-05-04
I have written this How-to to illustrate how to use eXeLearning in Ubuntu AMD64 / 64-bit (Hardy / 8.04).

> 
The eXe project is developing a freely available Open Source authoring application to assist teachers and academics in the publishing of web content without the need to become proficient in HTML or XML markup. Resources authored in eXe can be exported in IMS Content Package, SCORM 1.2, or IMS Common Cartridge formats or as simple self-contained web pages.



I have tested this in Hardy 64-bit, but it should work in Feisty and Gutsy too (although the Firefox 2 vs 3 issue will not be a problem).

Using Synaptic Package Manager, search for and install the following package (with its dependencies):
> python-zopeinterface

A 32-bit (i386) Feisty .deb package is available to download from the eXe homepage here: [http://exelearning.org/](http://exelearning.org/)

Having downloaded the .deb to desktop, run the following commands in Terminal to install eXe:
```

cd ~/Desktop
sudo dpkg -i --force-all python2.5-exe_1.04.0.3532-ubuntu1_i386.deb

```

Since eXe runs in Firefox 2, but is not fully compatible with Firefox 3, I chose to get SwiftWeasel 2 32-bit in order to use Flash and Java, together with eXe.

This method allows you to keep Firefox 3 (64-bit) in addition to SwiftWeasel.

Thanks to Kilz for maintaining an easy script to install various 32-bit Firefox derivatives here: [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

Follow the instructions there, and download and run the 3in1 script (double-click, run in Terminal).

Follow the options - I chose Swiftweasel (choose your processor type), and then installed the Flash and Java options.  Make sure you enter your Ubuntu login correctly at the end.

Of course, you could opt for the traditional Firefox 2, and amend the following instructions by replacing *swiftweasel32* with *firefox32*.

Having done this, SwiftWeasel (or Firefox) will now be installed correctly.

Now to gete eXe to run in SwiftWeasel (or Firefox 2).

The script installs SwiftWeasel to /usr/local/bin.  Firefox is launched from /usr/bin.  The following instructions will redirect the firefox shortcut to launch swiftweasel32.

```

gksudo nautilus

```
> Browse to /usr/local/bin
Make Link to swifweasel32 (right-click -> Make Link)
This will create a new file "Link to swiftweasel32"
Rename this file to "firefox" (right-click -> Rename)
Copy this file (right-click -> Copy)
Browse to /usr/bin
Rename "firefox" to "firefox3" (right-click -> Rename)
Paste the new firefox shortcut (right-click -> Paste)

This could also be achieved via the Terminal, but I think this illustrates exactly what we are doing nicely.

Now eXe should work, and launch SwiftWeasel instead of Firefox 3 to open in.

Unfortunately, the Menu and Panel shortcuts also launch SwiftWeasel; hence we have to redirect those shortcuts to "firefox3":
> 
Panel launcher:
Right-click the Firefox icon in the top Panel and select Properties.
Replace the contents of the Command box with "firefox-3.0 %u"

> Menu:
System -> Preferences -> Main Menu
Select "Internet"
Right-click Firefox, and select Properties
Replace the contents of the Command box with "firefox-3.0 %u"

That has returned the Firefox menu links to Firefox 3.

All done!

For an illustration of what can be achieved with eXe (& dokeos), see my website: [http://epconsult.uni.cc/](http://epconsult.uni.cc/)
For further details and FAQ about eXe: [http://exelearning.org/Creating_a_new_Style](http://exelearning.org/Creating_a_new_Style) [http://exelearning.org/Support](http://exelearning.org/Support)

---

### Post by ugm6hr on 2009-07-09
A quick note to explain I am now trying to get this to work with FF3 and Jaunty (albeit i386 first).

Notes:
Styles stored in /usr/share/exe/style
Feisty .deb no longer works
Website links changed (uses sourceforge / trac)
Latest nightly build (MAY 2009) installs, but causes occasional javascript errors: error installing toolbar:TypeError: navBar.insertItem is not a function

---

### Post by bellera on 2012-05-10
OBSOLETE

New 32 & 64 bit packages supporting Firefox greater than 3 at:

[https://forja.cenatic.es/frs/?group_id=197&release_id=671#iteexe-debian-ubuntu-1-04-1-3605intef6-title-content](https://forja.cenatic.es/frs/?group_id=197&release_id=671#iteexe-debian-ubuntu-1-04-1-3605intef6-title-content)

Regards,

Josep Pujadas-Jubany

---

### Post by nothingspecial on 2012-05-10
Old thread, closed.

---

### Post by Elfy on 2012-05-10
Old thread closed.

---

