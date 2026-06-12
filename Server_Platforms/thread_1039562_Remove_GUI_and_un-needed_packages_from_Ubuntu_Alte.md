---
title: "Remove GUI and un-needed packages from Ubuntu Alternative install"
date: 2009-01-14
forum: Server Platforms
---

### Post by peeta123456 on 2009-01-14
Hello,

I used the alternative Ubuntu install as it seemed the only way to get a hardware RAID 1 working properly. Its working fine but I would like to remove most of the packages it installed. I did not get an option to select the software I would have liked during installation. I'd ideally like to be left with the same core packages as the server edition. Or can anyone suggest a way of choosing which packages are installed with the Alternative CD?

Any help much appreciated. :)
Regards,
Pete

---

### Post by RealPSL on 2009-01-16
Technically ```
sudo tasksel remove ubuntu-desktop
``` should remove the desktop/GUI environment.

---

### Post by peeta123456 on 2009-01-16
Hiya,

Thanks for your reply :). By removing the preseed line from the Alternative CD installer boot args I had control over which packages were installed.

Thanks anyway!

Regards,
Pete

---

