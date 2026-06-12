---
title: "Guest additions cannot compile kernel"
date: 2010-05-05
forum: Virtualisation
---

### Post by Euphorion on 2010-05-05
Hello

I am running Xubuntu in Virtual Box in order to gain experience with xubuntu prior to installing either xubuntu or lubuntu on an older laptop.

I have installed the VBoxGuestAddtions, during the installation (with admi rights) I received the message that I cannot compile kernel modules. Thereafter I can scale the window as I want, but I have no seamless mouse (mouse is trapped within VBox untill I release with right ctrl key).

I think that the problem will lie with the reduced features contained in Xubuntu as apposed to Ubuntu.

Can someone tell me what is missing and what I need to install in order to compile a kernel in order to install all the guest additions.

Thanks in advance

---

### Post by lmarmisa on 2010-05-05
Try to install this two packages: **build-essential** and **linux-headers-generic**.

```

**[FONT=Times New Roman][SIZE=2]sudo apt-get install build-essential  linux-headers-generic[/SIZE][/FONT]**

```I think that you will be able to compile the kernel modules after this update.

Best regards,

Luis

---

### Post by KevinP-Ott on 2010-05-05
I had the exact same problem as the original poster when trying to install the Guest Additions on Xubuntu 10.04.

The installation of the build-essential package and the generic headers allowed me to install the Guest Additions just fine.

My VirtualBox version is 3.1.6.r59338 - just in case its an issue related to version of Guest Additions.

-K

---

### Post by Euphorion on 2010-05-06
Have installed the headers and build essentials and now everything works a treat.

Thanks for your help.

---

