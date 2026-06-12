---
title: "Fresh install pending - backup question"
date: 2017-02-03
forum: Virtualisation
---

### Post by oygle on 2017-02-03
I'm about to do a fresh install of Kubuntu; go up to 16.10

I usually backup everything, wipe the HDD, then install Kubuntu, then restore files. But I don't want to have to reinstall windows within the VM. Can I simply backup the .vdi file , then restore that after reinstalling the VM software ? It's about 9.6 Gb, and going through the whole Windows installation again would be very tedious and time consuming.

---

### Post by wildmanne39 on 2017-02-03
I have done it before in virtualbox, it has been a few years but I exported the vm's from the old OS then imported them into the new OS.

---

### Post by oygle on 2017-02-03
> **wildmanne39 said:**
> I have done it before in virtualbox, it has been a few years but I exported the vm's from the old OS then imported them into the new OS.

Thanks. I see there is a 'File  |  Export Appliance" function. I assume that will also export the settings, so they can be restored when the import is done.

---

### Post by wildmanne39 on 2017-02-03
Yes it kept all my settings.

---

### Post by oygle on 2017-02-03
Great , thanks  :)

---

### Post by &amp;KyT$0P# on 2017-02-03
If you're keeping all the same physical hardware, exporting is not necessary.  Just copy the entire VM folder.  Most likely the file paths will all be the same, but if not adjust as needed and you're good to go.

* Forgot to say, make sure the VM isn't running when you copy its folder.

** And to get the new VirtualBox to see the VM, go to Machine > Add, then select your VM's .vbox file.

---

### Post by oygle on 2017-02-03
> **halogen2 said:**
> If you're keeping all the same physical hardware, exporting is not necessary.  Just copy the entire VM folder.  Most likely the file paths will all be the same, but if not adjust as needed and you're good to go.

* Forgot to say, make sure the VM isn't running when you copy its folder.

** And to get the new VirtualBox to see the VM, go to Machine > Add, then select your VM's .vbox file.

Yes, it is the same hardware. These days I don't upgrade to Kubuntu releases, as I have found it is better to backup, wipe and do the fresh install, then restore files.

So, I will just make sure the VM is not running, then copy the entire VM folder, and after Kubuntu 16.10 is up and going, restore the VM folder.  Thanks  :)

---

