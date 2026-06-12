---
title: "Is it complusory to install all security updates?"
date: 2011-09-03
forum: Security
---

### Post by arroy_0209 on 2011-09-03
I am using Ubuntu 10.04 LTS and I receive "important security updates" and "recommended updates" notifications. My doubt is should I install all recommended updates or only those which are relevant for me? I confess I am not an expert but have some intuition telling me that some of these are irrelevant for my purpose. For example, latest notification telle me to install "samba-common" and "samba-common-bin". However I do not use samba at all and probably will never use this. On the other hand thers are some like "libsmbclient" whose purpose is not clear at all. So what should I do? Should I install all those which I feel are relevant and also those about which I am not so sure or should I install all recommended updates blindly? (It would be nice if ubuntu could provide details about each recommended updates, explaining importance in more details; short specifications are not helpful for people like me.)

---

### Post by ajgreeny on 2011-09-03
It is certainly not "compulsory" to update anything if you don't want to, and it is possible to use a setting that only update security packages, not recommended ones.  I have always used all updates, and even occasionally check the **backports** and **proposed** repos as well, just for peace of mind, but generally just go for the default of security and recommended

See screenshot, for Lucid, but I think it's the same for newer versions as well.

---

### Post by Rob_H on 2011-09-03
You'll only see updates for packages you have installed. Obviously, some packages may be installed as part of the base system even though you don't use them. It's a good idea to keep them updated anyway because you may be relying on a package now or in the future and not even know it.

I assume the reason you're asking is that you're worried about an updated package destabilizing your system. Rest assured, security updates are conservative and installing them is low-risk.

If you're really sure you don't need a package, you can try uninstalling it and then you won't be prompted for updates. But depending on what other packages depend on it, this may end up causing more problems than if you just leave well enough alone.

---

### Post by $uraj on 2011-09-03
"Important security updates" are released to provide patches for the software that are used in the system. Its better to install it to be at the safer side :)

On the other hand "Recommended updates" are NOT COMPULSORY as Ubuntu recommends it for smooth working(any bug fixes or anything like that).

U can disable "Recommended Updates" by clicking "Settings" in Update manager ->[Enter password for authentication]-> UNMARK the "Recommended updates" checkbox.

Software center DOES provide description about the update. Carefully note u can see a TRIANGLE somewhere below "Check" and "Install" button. Most probably above settings button. 

The description also provides wat are the changes that has been made in the application's update.


Ubuntu can be made customized to ur needs :)

---

### Post by Patsfriend on 2011-12-04
Thank you Thank You.
Your tip has helped me greatly!

> **$uraj said:**
> "Important security updates" are released to provide patches for the software that are used in the system. Its better to install it to be at the safer side :)

On the other hand "Recommended updates" are NOT COMPULSORY as Ubuntu recommends it for smooth working(any bug fixes or anything like that).

U can disable "Recommended Updates" by clicking "Settings" in Update manager ->[Enter password for authentication]-> UNMARK the "Recommended updates" checkbox.

Software center DOES provide description about the update. Carefully note u can see a TRIANGLE somewhere below "Check" and "Install" button. Most probably above settings button. 

The description also provides wat are the changes that has been made in the application's update.


Ubuntu can be made customized to ur needs :)

---

