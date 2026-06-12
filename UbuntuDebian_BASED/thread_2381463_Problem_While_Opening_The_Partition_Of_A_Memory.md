---
title: "Problem While Opening The Partition Of A Memory"
date: 2018-01-01
forum: Ubuntu/Debian BASED
---

### Post by sehranshafi on 2018-01-01
I Have A 240 GB SSD And 30GB Is Used For Debian And 20 For Kali . WHEN I Use Kali The 182GB For My Data Is Not Getting Used Means It Shows That There Is A Partition But When I Click On That The Screen Git Blink And Went To Desktop. and In Debian I Get Some Files For Usage Whole Many Have Some Kind Of LockBy Which I Am Unable To Use Them . can Anybody Help Me Out

---

### Post by QIII on 2018-01-01
Moved to Ubuntu/Debian BASED.  Chat areas are not for technical support.

It seems that English may not be your native language.  We want you to get support, but your post is very difficult to decipher.  You might see if one of the [LoCo Team]("https://ubuntuforums.org/forumdisplay.php?f=183") sub-forums is better suited for you.

Otherwise, we'll have to hope someone is able to help.

---

### Post by The Cog on 2018-01-01
This may be because the two different systems number their users with different user IDs It is the user ID, not the user name that is stored in the file permissions/ownership on disk. The user ID -> name lookup is stored in the system files (/etc/passwd) and when using two systems, the same ID might have different names, or the same name might have different IDs. I know that in Ubuntu, the first user is given ID 1000. Kali may be different. 

If this is the reason for your problem then you could try creating a user in one system to have the same ID as the user in the other system. But I don't think it is a good idea for them to use the same disk location for their home folders because application settings are stored in the home folder, and different versions of applications in the two systems might not have compatible settings.

---

