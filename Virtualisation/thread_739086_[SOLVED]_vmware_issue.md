---
title: "[SOLVED] vmware issue"
date: 2008-03-29
forum: Virtualisation
---

### Post by upthelum on 2008-03-29
I run some windows and linux virtual machines using vmware. Windows start up ok, a red hat image i use starts up fine, but a fedora image i need to use won't start up, it gives an x server error and gets really upset when trying to boot. The settings for both linux machines are the same. I have dual core but set them to just one cpu and it makes no difference. It seems like a graphical problem as when i login to the text interface it keeps throwing a wobbler and rebooting. 

Any suggestions?

---

### Post by dcstar on 2008-03-30
> **upthelum said:**
> I run some windows and linux virtual machines using vmware. Windows start up ok, a red hat image i use starts up fine, but a fedora image i need to use won't start up, it gives an x server error and gets really upset when trying to boot. The settings for both linux machines are the same. I have dual core but set them to just one cpu and it makes no difference. It seems like a graphical problem as when i login to the text interface it keeps throwing a wobbler and rebooting. 

Any suggestions?

One would imagine that asking a Fedora question in a Fedora forum (or even a specific VMware forum) would have a much greater chance of a useful answer than here.

---

### Post by mvan83 on 2008-03-30
> **upthelum said:**
> I run some windows and linux virtual machines using vmware. Windows start up ok, a red hat image i use starts up fine, but a fedora image i need to use won't start up, it gives an x server error and gets really upset when trying to boot. The settings for both linux machines are the same. I have dual core but set them to just one cpu and it makes no difference. It seems like a graphical problem as when i login to the text interface it keeps throwing a wobbler and rebooting. 

Any suggestions?

Check if the driver in the Fedora xorg.conf file is "vmware" and not something else. If it's not strictly an X problem, post the errors you're getting here.

---

### Post by upthelum on 2008-03-30
Ok i moved the images from the linux drive to windows partition to make space and when i copied it back over its up and running.

---

