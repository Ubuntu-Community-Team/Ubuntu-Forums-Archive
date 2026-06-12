---
title: "kdenlive: dvgrab missing ?"
date: 2008-08-10
forum: Ubuntu Studio
---

### Post by Thievrey Corporation on 2008-08-10
Hello,

kdenlive is installed and running with my ubuntu 8.04
But in the capture monitor, there is this red message:
"The programs dvgrab or ffplay are missing. Firewire capture will be disabled untill yo install them."

I got both programs (sudo apt-get install ec...): and it is still not working.

Is there any other specific command to really "install" dvgrab and ffplay ?

Thanks.

---

### Post by Ubuntiac on 2008-08-20
The one that throws a lot of people is that **there is no ffplay package**. To install ffplay in ubuntu you need to install **ffmpeg**.

Permisions problems are common, too. You can solve some of these by adding your user to the group "disk" and also by changing permissions on dv1394 and raw1394 to 777 (or read and write able for everyone). A quick search will tell you where they are. Be aware that this last suggestion **is a security risk**. If you're going to do it, I'd undo it after capturing.

Take a search on the forums at kdenlive.org. There's quite a bit of discussion there. If all else fails it's actually pretty easy to capture straight from the command line. Dvgrab --help will give you the options (though 99% of them you can ignore).

---

### Post by Thievrey Corporation on 2008-08-22
Thanks,

I'll try these options and will keep you informed

---

