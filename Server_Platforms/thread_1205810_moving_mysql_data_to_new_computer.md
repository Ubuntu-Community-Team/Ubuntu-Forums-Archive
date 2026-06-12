---
title: "moving mysql data to new computer"
date: 2009-07-06
forum: Server Platforms
---

### Post by cacavolante on 2009-07-06
I had a server crashed due to ups failure. I can see the mysql data folder via usb box and I can copy the data folder to new machine. What does it takes to restore them to new machine?

PS. I have various exports from phpmyadmin but they were on the destroyed system partition - disk. I have no valid export or backup but the data folder.

Thanks in advanced

---

### Post by LepeKaname on 2009-07-06
Just copy those files inside the new data folder. It is recommended to have MySQL (the new one) turned off while copying. 

I have done that before several times, usually with no problems. If you don't care about the privileges, then I suggest not to copy the "mysql" database folder (as it will overwrite any users setup you have done in the new MySQL).

---

