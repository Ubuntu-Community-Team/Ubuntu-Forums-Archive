---
title: "Ubuntu repair"
date: 2008-02-20
forum: Ubuntu Brainstorm
---

### Post by adi_das on 2008-02-20
there should be option repairing Ubuntu OS using live cd .

---

### Post by smartboyathome on 2008-02-20
How would you detect what needed to be repaired? Sometimes one portion is broken and sometimes another is.

---

### Post by amlucent23 on 2008-02-20
I agree with the OP. SuSE has had this for years. Yes, I know this is an unfair comparison as SuSE comes on many CDs or a DVD thus giving them much more room to integrate tools.

 I think it simply looks across common config files for errors and returns them to the default if an error is detected.

---

### Post by whitewizardcoder on 2008-02-21
+1

Additionally, and in some ways related, there should be the ability to reinstall Ubuntu over a previous install.  This could be used as some sort of "repair" feature as it would get the system up and running with a default setup while not erasing any of the users' files.

---

### Post by kool_kat_os on 2008-02-21
is there a restore program...like windows restore...except for ubuntu??

---

### Post by soulfly7x on 2008-02-21
> **whitewizardcoder said:**
> +1

Additionally, and in some ways related, there should be the ability to reinstall Ubuntu over a previous install.  This could be used as some sort of "repair" feature as it would get the system up and running with a default setup while not erasing any of the users' files.

If you're only concerned about the files you've saved, and not all the programs that will not be installed by default until you reinstall them, you can do this. 

During the partitioning phase of the install, choose to manually partition. Then, select the partition that Ubuntu is installed on , and tell it to install there again, also using the swap that is already there.

Now, when you select the partition for your install, it will be ext3 filesystem, but make sure the setting states to leave it unformatted. You can do this, and your home folder will remain unaffected. But, you may see some breakage of the system.

This is also one of the reasons it is recommended to have /home on it's own partition. By having /home on it's own partition, it is easy to install over an older installation without affecting your files, and without breaking the system, as the other directories CAN be reformatted with /home on it's own partition.

---

### Post by mrsteveman1 on 2008-02-25
Authenticating the installed files should be easy. Heres why:

All Ubuntu systems should have a deb package database of installed packages, it should be trivial for the livecd to crawl the database, checking to make sure that the packages the system says are installed, are actually installed, including any files that are part of those packages. If a users system is missing certain files for some reason, or those files are corrupted, it makes perfect sense to let the livecd check them and replace what is necessary instead of simply telling people to reinstall the system.

The Suse livecd does this for the minimal set of packages that come on the CD since those packages are all you need to check to ensure a functional system.

It would be similar to system restore on windows but only in the sense that packages might be rolled back (since older versions may be on the CD), but as long as all dependencies are resolved correctly the system should then be perfectly fine.

---

### Post by Dngrsone on 2008-02-26
So, if I were to copy my /home folder elsewhere, reinstall Ubuntu, then put the /home folder back in, things should work (except for the extra programs)?

---

### Post by smartboyathome on 2008-02-26
> **mrsteveman1 said:**
> Authenticating the installed files should be easy. Heres why:

All Ubuntu systems should have a deb package database of installed packages, it should be trivial for the livecd to crawl the database, checking to make sure that the packages the system says are installed, are actually installed, including any files that are part of those packages. If a users system is missing certain files for some reason, or those files are corrupted, it makes perfect sense to let the livecd check them and replace what is necessary instead of simply telling people to reinstall the system.

The Suse livecd does this for the minimal set of packages that come on the CD since those packages are all you need to check to ensure a functional system.

It would be similar to system restore on windows but only in the sense that packages might be rolled back (since older versions may be on the CD), but as long as all dependencies are resolved correctly the system should then be perfectly fine.

The problem is, though, that some packages in the repos rely on the newest packages, and older ones would break them, thus breaking the system further. And if you uninstall those programs, people would probably not be very happy that the "repair" function uninstalled them.

---

### Post by mrsteveman1 on 2008-02-26
smartboyathome: The alternative is sometimes to just reinstall the entire system, in which case you lost those programs anyway.

If the repair function simply keeps track of what was installed, fixes the system by removing things if needed and repairing files, then when the system boots it can update everything and put those programs back.

---

