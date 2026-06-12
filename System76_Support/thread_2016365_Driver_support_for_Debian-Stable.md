---
title: "Driver support for Debian-Stable?"
date: 2012-07-04
forum: System76 Support
---

### Post by Mushroomheadbangers on 2012-07-04
No offence to the Ubuntu community but I simply could not stand Unity after a few months. Played around with a few other desktop interfaces and found myself still unsatisfied with some of the buggy behaviour in Ubuntu and a lot of the applications it supports.

I decided to revert back to a Debian-stable release called SolusOS. I was able to install the System76 deb package but am unable to launch the actual application to install the driver itself. Reviewing the change-log it appears this is developed specifically for Ubuntu so I'm wondering three things:
- Is there a known method of manually installing/unpacking the drivers?
- Will these drivers break a Debian-stable distro? 
- Will there be drivers released for standard functionality (IE: Keyboard) in other linux distros down the road?

Yes, I know Ubuntu is the officially supported distro of System76 and anything else is not.

---

### Post by jakobcreutzfeldt on 2012-07-04
Having recently gone through this with Arch Linux, I can say that the Ubuntu requirement runs pretty deep in the driver software. Your best bet is to browse the code and find out exactly what would be done for your model (or, rather, grep the code for your model short name, ie grep -r gazp7 *) and replicate it by hand. The code mostly in turn does system calls, so it should be straight-forward. For example, for my gazp7 I only needed to add something to my GRUB kernel line. I also saw some cases of modifying gconf entries and so on.

.deb files are just standard ar archives so you can unpack it with File Roller in Gnome, for example.

---

### Post by Mushroomheadbangers on 2012-07-04
Exactly what I was looking for :) Thanks jakobcreutzfeldt!

---

### Post by jakobcreutzfeldt on 2012-07-04
No problem :) 

And by "recently gone through this" I meant two days ago. So if you discover else that should be done please post it here. I'll do the same!

btw, I think the file you're most interested in is called driver.py (or something similar; I don't have my sys76 on hand at the moment)

---

### Post by Mushroomheadbangers on 2012-07-04
Spent sometime going through source files from the current and previous driver packages. If anything, there are more unrelated programs (IE: Webcam program, accounting program) installed than actual useful drivers...at least for my particular model (gazp6). 

**/usr/bin/system76-driver**

```
#import System76 specific files
import base_system
```

**/opt/system76/system76-driver/src/base_system.py**

```
# System76 Gazelle Pro (gazp6)
    elif modelname == ('gazp6'):
        if version == ('10.10'):
            sources.add()
            os.system('sudo apt-get --assume-yes install gnucash gnucash-docs system76-driver cheese')
```

**/opt/system76/system76-driver/src/driversdescribe.py** 

```
    elif modelname == ('gazp6'):
        if version == ('10.10'):
            fprint.fingerprintGUI().describe()
            acpi.xhcihcdModule().describe()
            misc.gnomeThemeRace().describe()
            acpi.pcie_aspm().describe()
        elif version == ('11.04'):
            acpi.pcie_aspm().describe()
        elif version == ('11.10'):
            nodrivers = "true"
            return nodrivers
        elif version == ('12.04'):
            fprint.fingerprintGUI().describe()
        else:
            nodrivers = "true"
            return nodrivers
```

It would appear, so far, that if I was using the current version of Ubuntu I may not even need any additional drivers. I may be wrong but so far I haven't found anything indicating otherwise.

---

### Post by jakobcreutzfeldt on 2012-07-05
That's not very surprising since these days most hardware is supported in Linux out of the box unless you have something exotic. So, that makes your life easier I guess, eh? :P

But, speaking of making lives easier, browsing that code makes me realize that the entire system is pretty brilliant. As System76's lineup grows and evolves, they can easily serve all of their customers with just one package that they have to maintain.

---

