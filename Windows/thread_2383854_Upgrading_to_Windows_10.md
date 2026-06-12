---
title: "Upgrading to Windows 10"
date: 2018-01-30
forum: Windows
---

### Post by sheine on 2018-01-30
I am posting here to save others the agony that I went through. I am dual booting Ubuntu and Windows 7. I took advantage of the free upgrade to Windows 10 and then went back to Windows 7, thinking that I could go up and down as I pleased. But, when you upgrade to Windows10, a folder Windows.~BT is created which makes it nearly impossible to come back up again after you go down.  It is nearly impossible to get rid of this folder, there is a lot of discussion about it on the Internet with ways to get rid of it that never worked for me. What it does is to allow the Windows Upgrade Assistant to run almost to completion and then give you an error message. I finally found a way to neutralize it. Even though it doesn't allow you to delete it or rename it, it does allow you to rename subfolders and files and after that the folder itself.  Crippling this folder allows the upgrade to continue to the end.

Unfortunately when it reaches the install stage it doesn't.

Then I found a way to make a Windows 10 update disk starting with the free upgrade program that you downloaded on the Internet. You start the install process after crippling the folder above and when the installation phase reaches 82%, a folder "C:\$Get Current'" is created which contains the whole installation program. This folder is changed and becomes useless after the upgrade program runs its full course. However, while it is good you can copy it and store in a place like Documents. From wherever it is stored you can copy it to a DVD, which becomes an installation disk for Windows 10.

Unfortunately when I ran it, just as you would run any other OS installation, all the way it could not get past grub to update Windows7 to Windows10. I suppose if you are willing to give up your Linux partition and leave your whole disk open to the upgrade it will do so. After that you could repartition and install a linux OS.

---

