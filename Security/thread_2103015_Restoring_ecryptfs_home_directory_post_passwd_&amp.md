---
title: "Restoring ecryptfs home directory post passwd &amp; system crash"
date: 2013-01-08
forum: Security
---

### Post by TomDHarray on 2013-01-08
Hi there,

I'm running kubuntu 12.01 LTS with the 3.2.0-35-generic kernel, 64 bit system, and have set up my home directory to be encrypted during the set-up of the system.

I have changed my login password using passwd from the command line, and I did not know then that I'd have to run ecryptfs-rewrap-passphrase ([[COLOR="Blue"]link[/COLOR]]("http://goshawknest.wordpress.com/2011/02/17/how-to-change-ecryptfs-home-cripted-filesystem-password-on-ubuntu-and-get-your-files-back/")). Unfortunately after changing the login password the system froze because of an other application, and I had to switch off the computer. The consequence is the usual that I cannot start my KDE desktop and the encrypted home folder is not mounted.

After looking for a solution ([[COLOR="blue"]link[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-1426960.html")) I figured out that the files
/home/.ecryptfs/$USER/.ecryptfs/wrapped-passphrase
  and
/home/$USER/.ecryptfs/wrapped-passphrase
are empty. Hence, the solution did not work.

By now, I am at least able to mount my home directory following [[COLOR="blue"]Recovering_Your_Data_Manually[/COLOR]]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Manually"). So I could start copying my files around, but I'm afraid of running into trouble by wrong file attributes despite using cp -dpr ...

So the question I have is: Is there a way to directly recover my home directory?

Thanks,

Tom

---

### Post by emiller12345 on 2013-01-09
You might want to invest in a backup harddrive, cp your data over and then verify that it is okay (check whatever you think might have been altered). This way, if its not right you can always go back to the original.

---

