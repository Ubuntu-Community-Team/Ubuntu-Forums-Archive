---
title: "How do I install the .NET fix so I can run modern windows programs?"
date: 2010-10-12
forum: Wine
---

### Post by Captain_Glen on 2010-10-12
When I try to install the .Net fix from the Microsoft site, it just comes up with an error saying the installation failed.  I have the service pack two version of the .NET fix.

I have whatever version of wine that comes with Ubuntu 10.10.

Any help would be appreciated.

Thanks,
Glen.

---

### Post by gintovan on 2010-10-12
What programs is it that you want to work with Wine?

Microsoft .Net framework doesn't really run well on Wine [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586)

Though as far as I know, Wine already supports some .Net libraries. But you are most likely not in luck if you need a newer .net app.

As with all apps on Wine will be very case to case based. 
It is not recommended to install .Net just to have it ;)
So depending on what app you want to run it might be possible.

---

### Post by Captain_Glen on 2010-10-13
Hi,

Thanks for the reply.  I want to use SciLor's Grooveshark Downloader ([http://www.scilor.com/index.html]("http://www.scilor.com/index.html"))

When I try and run it, it comes up with an error.  It use to say I needed the .NET fix.  But now it just says it has encountered a problem...

---

### Post by JustinR on 2010-10-13
> **Captain_Glen said:**
> Hi,

Thanks for the reply.  I want to use SciLor's Grooveshark Downloader ([http://www.scilor.com/index.html]("http://www.scilor.com/index.html"))

When I try and run it, it comes up with an error.  It use to say I needed the .NET fix.  But now it just says it has encountered a problem...

Try to find it using WineTricks:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by Captain_Glen on 2010-10-14
Thanks for the tip.

I installed winetricks and now I can run the program.  But when I try to search grooveshark for a song I get the following error.

It looks like I am missing "System.Xml.Linq".  Can I install it as a DLL or something?

Any help would be appreciated.

Thanks,
Glen.

Debug Log
[14/10/2010 10:34:04 PM] Searching...
[14/10/2010 10:34:04 PM] Error: System.IO.FileLoadException - Could not load file or assembly 'System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=969db8053d3322ac, Retargetable=Yes' or one of its dependencies. The given assembly name or codebase was invalid. (Exception from HRESULT: 0x80131047)
[14/10/2010 10:42:58 PM] Searching popular songs...
[14/10/2010 10:42:58 PM] Error: System.IO.FileLoadException - Could not load file or assembly 'System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=969db8053d3322ac, Retargetable=Yes' or one of its dependencies. The given assembly name or codebase was invalid. (Exception from HRESULT: 0x80131047)

---

### Post by Quadunit404 on 2010-10-15
This is why setting up Windows in a VM can be useful... sure, it'll be slower, but it won't require you to wait for the Wine Devs to fix .NET under Wine. Or you could always have another PC or two (or three) in your home that has Windows on it (like I do)

I'm not aware if there's a DLL for System.Xml.Linq but you can always try searching for one. Otherwise, back up the important stuff in your Wine directory (e.g. games, hard-to-find software, the AppData/Application Data folder(s)) and create a new Wine directory, as you _may_ have broken something somewhere.

---

