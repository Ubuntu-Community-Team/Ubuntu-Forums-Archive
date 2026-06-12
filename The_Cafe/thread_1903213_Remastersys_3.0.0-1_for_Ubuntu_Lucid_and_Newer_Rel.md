---
title: "Remastersys 3.0.0-1 for Ubuntu Lucid and Newer Released"
date: 2012-01-01
forum: The Cafe
---

### Post by Fragadelic on 2012-01-01
There are many changes from the 2.0 series to 3.0.0-1.

From the changelog:

      * 3.0.0-1
      * Added remastersys-gtk gui into the main remastersys package - changes and fixes as well
      * Added plymouth theme generation
      * Added grub background changing option
      * Added live system menu background changing option
      * Added option for Backup mode Install Icon
      * Optimized stage 1 procedure
      * Fixed vesamenu.32 call
      * Removed ubiquity-frontend* from desktop manifest so it is removed after install and off original system so it doesn't have a bad menu item
      * Added /etc/shadow and /etc/gshadow to fix the rescue boot mode issue with root access
      * Added remastersys-skelcopy script
      * Prevent unimportant failures from showing to the user
      * Added more information to the remastersys.log
      * Properly spaced the script out to make it easier to read for scripters
      * Added check for working folder filesystem type as it has to be a valid linux filesystem

Most notable changes are as follows:

Brand New GUI based on remastersys-gtk gui created by Krasimir S. Stefanov <lokiisyourmaster@gmail.com> and some tweaks and ideas from me Tony Brijeski <tb6517@yahoo.com> but most of the credit needs to go to Krasimir for it.

The gui has translations in Bulgarian and Traditional Chinese as well.
Bulgarian - Krasimir S. Stefanov <lokiisyourmaster@gmail.com>
English - Krasimir S. Stefanov <lokiisyourmaster@gmail.com>
Traditional Chinese - Kent Chang <kentxchang@gmail.com>

Incorporated in the gui are tools I created to help those creating a distro to customize the live boot background, the system grub background, creating a new plymouth theme and selecting which plymouth theme will be the default as well as copying the relevant settings from your user to /etc/skel making it the default for the live system.

The remastersys.log will also show a lot more detail and I also added in more checks to try and help make sure the remaster is a good one but I can't account for every situation so if you have issues I will try to help you out.

Thanks very much to all the folks that tested this out and provided feedback and tweaks.

This is the best version of remastersys yet and I hope you all like it.

A direct download can be found here:

[http://www.remastersys.com/repository/lucid/](http://www.remastersys.com/repository/lucid/)

If you want to add it to your sources.list, here are the lines you need to add.

# Remastersys for Lucid and newer
deb [http://www.remastersys.com/repository](http://www.remastersys.com/repository) lucid/

Wishing everyone a Happy and Prosperous New Year!

If you had previously downloaded the test version of 3.0.0-1 you should upgrade to this final version as there are some final tweaks and fixes included.

---

### Post by Megaptera on 2012-01-02
Many thanks for this!!

---

### Post by labinnsw on 2012-01-02
Any idea what's happening here?
[ATTACH]210108[/ATTACH]

---

### Post by BrokenKingpin on 2012-01-02
Awesome, I will be giving this a try over the next couple weeks for sure. Keep up the good work!

---

### Post by Fragadelic on 2012-01-02
> **labinnsw said:**
> Any idea what's happening here?
[ATTACH]210108[/ATTACH]

Yes.  The newer Ubuntu's don't use Packages.gz anymore and use Packages so I changed this repo as well.

You can get it with direct download for now and I will put up the Packages.gz in an hour or so.

---

### Post by bluexrider on 2012-01-02
> **labinnsw said:**
> Any idea what's happening here?
[ATTACH]210108[/ATTACH]

[www.remastersys.com/repository/lucid/remastersys_3.0.0-1_all.deb](www.remastersys.com/repository/lucid/remastersys_3.0.0-1_all.deb)

---

### Post by Fragadelic on 2012-01-02
I added Packages.gz and will include both files so those using Lucid can apt-get it as well.

Try again and it should work.  Let me know either way.

---

### Post by labinnsw on 2012-01-03
> **Fragadelic said:**
> I added Packages.gz and will include both files so those using Lucid can apt-get it as well.

Try again and it should work.  Let me know either way.

Thanks

---

