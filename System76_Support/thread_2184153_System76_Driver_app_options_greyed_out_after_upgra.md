---
title: "System76 Driver app options greyed out after upgrade"
date: 2013-10-27
forum: System76 Support
---

### Post by re1d on 2013-10-27
[COLOR=#333333][FONT=UbuntuRegular]Just upgraded to 13.10 via clean install. Notice after loading System76 drivers (which seem to have loaded up OK) that now, when I access the System76 Driver app, the options to **Install Drivers** and **Restore System** are greyed out. In past installations I haven't seen this - you could Restore at any time.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Are the options greyed out just because the correct drivers are loaded, and the app "knows" this - or is something wrong with the System76 Driver app? Otherwise, the system seems to run normally.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks for any info,[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Reid  [/FONT][/COLOR]

---

### Post by benhill70 on 2013-10-30
I'm seeing the same thing after a upgrade.

---

### Post by isantop on 2013-10-31
At the moment, the Install and Restore buttons both do the same thing. Instead, we now have a System76 Daemon that periodically checks that all required fixes are installed. There are some things it can't yet do (like installing color profiles for our ColorPro displays), but if a system doesn't require any of those, it will install the drivers automatically when you install the package, and clicking the button is not required.

(Alternatively, it may simply be that your system no longer requires any fixes in the driver)

---

### Post by re1d on 2013-11-01
Ian, Thanks! Good to know that it's OK - thanks for all the stellar work that goes to make this my favorite computer company!

---

