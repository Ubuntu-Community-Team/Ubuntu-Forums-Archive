---
title: "Corecomp.ini fails install"
date: 2009-06-22
forum: Wine
---

### Post by Shobuz99 on 2009-06-22
Has anyone encountered this error while trying to install a windows app using Wine?:
[COLOR="Red"]"An installation support file '%systemDrive%\Program files\Common files\InstallShield\engine\6\Intel 32\corecomp.ini' could not be installed (0x8000ffff)"[/COLOR]

I get the error trying to install Dreamweaver MX 2004 (ver 6.0)
using Wine 1.1.24 beta on my 64 machine with Jaunty 9.04
Install does not happen. I've tried some workarounds with no progress. :frown:

Just wondered, if this is a common problem across Wine or Linux or the whole dang world...:confused:

thanks for any help..
Rick (shobuz99)

---

### Post by NightMKoder on 2009-06-22
What the case-sensitive crap? Try:

export systemDrive='C:'
wine ....exe

if that helps, should report this bug to wine. But if it doesn't you probably installed something evil on wine and it's being...evil. Delete your prefix (`rm -rf ~/.wine`, will delete all your programs) and try again.

---

### Post by Shobuz99 on 2009-06-22
> **NightMKoder said:**
> What the case-sensitive crap? Try:

export systemDrive='C:'
wine ....exe

If that helps, should report this bug to wine. But if it doesn't you probably installed something evil on wine and it's being...evil. Delete your prefix (`rm -rf ~/.wine`, will delete all your programs) and try again.

* what do you mean by "case-sensitive"?
* So I need to "Delete my prefix 'rm -rf ~/.wine'" 
Put wine beta back on, 
Go to Terminal and type $ export systemDrive='C:' 
and then try installing DWMX 2004 from CD all over again 
and run the install from Wine?
* I didn't install anything 'evil' on Wine.. where did that come from? 

Rick (shobuz99)

---

