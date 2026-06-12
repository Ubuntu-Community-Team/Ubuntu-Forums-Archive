---
title: "UbuntuOne on Natty password and encryption help"
date: 2011-05-07
forum: Ubuntu One (CLOSED)
---

### Post by Voluntaryist on 2011-05-07
I have a fresh Kubuntu 11.04 Natty install. I've had an UbuntuOne account for a long time. I installed UbuntuOne version 1.6.2-0ubuntu1 via KPackageKit. I can see my UbuntuOne folder in my /home/username directory. 

My problem is with connecting my computer to my account online. The instructions on the one.ubuntu.com site say > 10.10 (Maverick) and newer releases

Open System->Preferences->Passwords and Encryption Keys*

Under "Passwords", right-click on Ubuntu One and select Delete

Open Applications->Accessories->Terminal and run:

     u1sdtool -q; u1sdtool -c 

But I don't have the equivalent "System->Preferences->Passwords and Encryption Keys" in Kubuntu. I go to system settings and search for "password" and "encryption" and I cannot find them. 

How do I delete the Ubuntu One password/encryption key in Kubuntu? It seems I cannot connect my computer to my account without doing this step first.

---

### Post by Voluntaryist on 2011-05-08
Does anyone have UbuntuOne connected and synching in Kubuntu 11.04?

---

### Post by asv1988 on 2011-06-05
Hey, 

I have kinda the same problem. I desperately need Ubuntu One client for Kde. Unfortunately, according to quick google search, there is no solution to that so far, let's hope and wait.

P.S If anybody found any solution please post it here.

Thanks

---

### Post by asv1988 on 2011-06-05
You may try this one though:

[https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIInstallTheGNOMEUbuntuOneClientOnKubuntu](https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIInstallTheGNOMEUbuntuOneClientOnKubuntu)

Hope that helps

---

### Post by mrhhug on 2011-06-15
what your looking for is called seahorse.

if its installed you should be able to just ```
seahorse
``` and it'll open for you

---

### Post by schmandr on 2011-07-10
> **asv1988 said:**
> You may try this one though:

[https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIInstallTheGNOMEUbuntuOneClientOnKubuntu](https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIInstallTheGNOMEUbuntuOneClientOnKubuntu)

Hope that helps


Thank you, these instruction made it work for me on Kubuntu Natty!

If you want to sync a folder other than ~/Ubuntu One, run the following command:
```
u1sdtool --create-folder=/home/yourusername/yourfoldername/
```
If you have configured your mobile device to upload pictures taken automatically and want them to be synced to your computer, run the following command:
```
u1sdtool --list-folders
``` This will show you the name of the folder where the pictures are stored along with an id and "subscribed=False". Now subscribe to this folder with:
```
u1sdtool --subscribe-folder=ID-FROM-COMMAND-ABOVE
```
Replace ID-FROM-COMMAND-ABOVE with the id determined from the folder list. (Source: [Ubuntu One FAQ]("https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIStopSyncingAFolderOutsideMyUbuntuOneFolder"), adapted)

---

