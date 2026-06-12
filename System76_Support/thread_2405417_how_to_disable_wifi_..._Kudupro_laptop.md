---
title: "how to disable wifi ... Kudupro laptop"
date: 2018-11-05
forum: System76 Support
---

### Post by Skaperen on 2018-11-05
i want to do an install on my old Kudupro laptop (actually, i have two of them).  i will be doing this where i will not have access to shutdown the wifi access point router.  i want to be sure this install does not go out to the internet on its own before i have an opportunity to add a software on/off switch.  is there a hardware means to do this, other than to do the install inside a Faraday cage?

---

### Post by MoebusNet on 2018-12-01
Since no-one else has pitched in, during boot you should be able to access your BIOS which many times has an option to enable/disable WiFi. If not, booting from Live-DVD or Live-USB then the 'Try Ubuntu' option, you should be able to click on 'Network Manager' and deselect 'Enable WiFi' before you start installation. In addition, the installation process has an 'Update Operating System during Installation' option that can be deselected so that updates are not downloaded from the Internet. Network Manager has the built-in option to deselect WiFi aftere installation.

---

### Post by Skaperen on 2018-12-05
there was an option to go out to the network and update packages.  i did not select it.  installation worked fine each time ... i installed twice (to get a different first user) on each of 3 storage devices.  i wanted my first user to be "admin" be it rejected that despite not creating one.  the 2nd set of 3 installs was changing mind on that name.  i chose "admini" (a 6 letter abbreviation of "administrator".  i added "admin" later (and now have both).  after restoring many (but not all) files from my backups i now have my 20-some users working.  a few little issues and quirks remain.  one is that 2 user don't have pulseaudio working and it just now tried to automount one (of 2) partitions from the 3rd storage device.  i have turned automounting off for all uses.  and it also just turned the mouse pad back on even though i am using a wireless mouse.  i'll post about some of these issues elsewhere, later.

---

### Post by MoebusNet on 2018-12-06
I'm glad you got your installation issues sorted! You are absolutely correct about a separate thread for other issues. Please use the "Thread Tools' at the upper-right of the web page to mark this thread "SOLVED'.

---

### Post by Skaperen on 2018-12-06
no means was found to disable wi-fi but a workaround (in the installer) of my intention was discovered.  if you call that "solved" that's good enough for me.

---

