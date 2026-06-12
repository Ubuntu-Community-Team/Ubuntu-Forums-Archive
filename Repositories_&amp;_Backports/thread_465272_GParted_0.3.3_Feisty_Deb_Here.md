---
title: "GParted 0.3.3 Feisty Deb Here"
date: 2007-06-05
forum: Repositories &amp; Backports
---

### Post by mrfuzzemz on 2007-06-05
I've created a deb package for the latest version of GParted as of June 5, 2007. (0.3.3) I created it using Feisty, but it may very well work with other x86 versions.

You may need to satisfy some dependencies. I needed to install libuuid libgtkmm-2.4 libparted1.7. You should also install the -dev files for the required packages.
Please let me know if you run into any problems and enjoy!

---

### Post by stchman on 2007-06-07
> **mrfuzzemz said:**
> I've created a deb package for the latest version of GParted as of June 5, 2007. (0.3.3) I created it using Feisty, but it may very well work with other x86 versions.

You may need to satisfy some dependencies. I needed to install libuuid libgtkmm-2.4 libparted1.7. You should also install the -dev files for the required packages.
Please let me know if you run into any problems and enjoy!

What more does the 0.3.3 version do than the version that comes with Feisty?

---

### Post by mrfuzzemz on 2007-06-07
Bug fixes and better support for NTFS.  There are other features, but I've been using .3.3 since it came out so I forget what all the other advantages over .2.5 are.

---

### Post by Jellyffs on 2007-06-17
Hi,

Perfectly installed on my Feisty. Thanks for your work! 
Unfortunately, I was hoping this version would be able to format my external hard disk in NTFS. It's not that it doesn't work, it's just that I cannot select it at all, it doesn't make it available.

Do you have any idea why? Do I need to boot on a live-cd to be able to do this?

Thanks,

Alex.

ps: sorry I know it's not the subject.

**EDIT: After installing this version (I had 0.2.5 before), the entry in "System - Administration" for Gparted disappeared.**

---

### Post by Jellyffs on 2007-06-17
Sorry my mistake, I needed ntfs packages......:-\"

And Gparted is in "System tools" menu....... ](*,)

Conclusion:

You did your job perfeclty :)

---

### Post by mrfuzzemz on 2007-06-18
Thanks.  Glad to hear it worked for you!

---

### Post by Guil-T on 2007-06-22
I have no entry for GParted (it is not in system tools)

---

### Post by mrfuzzemz on 2007-06-22
> **Guil-T said:**
> I have no entry for GParted (it is not in system tools)

You'll have to put that in yourself:

Go to System > Preferences > Main Menu

and in 'System Tools' add a new item.  Click the box on the left to find the icon and then have this as your command:

```
gksudo gparted
```

The 'gksudo' is because you need root permissions to get the appropriate level of access. Let me know if you have any questions!

---

### Post by logos34 on 2007-06-22
any feedback on how well 3.3 works on edgy?  And should I uninstall the previous version first?

---

### Post by mrfuzzemz on 2007-06-22
I would uninstall the previous version.  If you don't like .3.3 then you can always easily uninstall and reinstall the old version.  It's run extremely well for me on at least 3 separate Feisty systems.

---

