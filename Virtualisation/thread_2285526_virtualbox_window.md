---
title: "virtualbox window"
date: 2015-07-06
forum: Virtualisation
---

### Post by huff2 on 2015-07-06
Hi all,

I recently installed virtualbox and running Ubuntu on it. I'm new to all this but the window is small and I can't seem to see the entire desktop. I hope I explained this correctly. 

Does anyone know of a solution?

Thanks

---

### Post by nerdtron on 2015-07-06
So your computer is windows, then you installed Virtualbox and then installed Ubuntu on virtualbox? (If you are having a hard time explaining your situation, you can always attach a screenshot of the problem)

Then try to install the "guest additions" which allows you to have mouse integration, clipboard support and better window adjustment, which I think is what you need.
On virtualbox Menu, click Devices>Install Guest additions. This will create a CD-rom on Ubuntu which holds an installer for the guest additions, Install the guest additions inside Ubuntu. 
See this: [http://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-a-virtualbox-vm](http://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-a-virtualbox-vm)
or this (old one but you know the concept): [http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/](http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/)

---

### Post by huff2 on 2015-07-06
Guest additions worked! Thank you!

---

### Post by bapoumba on 2015-07-06
*Thread moved to **Virtualisation**.*

---

