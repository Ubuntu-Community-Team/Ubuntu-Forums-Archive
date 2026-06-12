---
title: "I can't login"
date: 2023-10-22
forum: Virtualisation
---

### Post by threeoaks on 2023-10-22
I fixed my password on the Ubuntu site but on the vm machine it won't login, 

said that password had been reset

---

### Post by ActionParsnip on 2023-10-23
Log in to what?

---

### Post by ajgreeny on 2023-10-23
There is no possible way to help you with this as we know absolutely nothing  about the computer or software you are using!

Please give us all the details of the OS being used and which hypervisor the VM is running in; virtualbox, VMware, KVM/QEMU?

---

### Post by threeoaks on 2023-10-23
my Ubuntu on the vm ware

---

### Post by threeoaks on 2023-10-23
vm ware on windows 10 pro. The virtual machine has Ubuntu on it but won't recognize the password that I set in the automated Ubuntu password system. Still won't open my session

---

### Post by ian-weisser on 2023-10-24
What is "the automated Ubuntu password system?" Maybe you mean Ubuntu One? Maybe you mean some Kerberos server. Maybe you mean the Automatic Login setting on Ubuntu Desktop. Maybe you mean something else.

We are not clairvoyant, so please help us to help you. We cannot help you with the limited information so far.
Please try to use actual names when possible.
Please try to describe the problem as if we have never seen your problem before. Tell us all the steps.

---

### Post by ajgreeny on 2023-10-24
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by MAFoElffen on 2023-10-24
I saw this when you first posted this and didn't answer because I thought you were talking about that your were having problems logging into the Forum itself. I waited until your posted more information to try to figure out what you were talking about. 

So let me get the layout of things... Correct me if I am assuming wrong, I am just guessing from trying to decipher what you have said:

You have a Window Host running VMware Player or Workstation.

One of your VMware VM Guests is Ubuntu Desktop...

You installed it as autologin (instead of requirig a login at boot), and it has problems where (somehow) it will not allow you to login...

Do you mean that it will not go to a Desktop? Meaning that something is wrong with the graphics?

I can't read your mind. I have tried. Not very good at that... I can not see through your eyes.

Please describe in detail what it does and does do, by a path of events, painting me a picture that I can visualize...

Does it boot to a Grub2 boot menu? From the boot menu, do you see a splash screen with the Ubunt Logo and a status loading kind of graphics? From that, does it get to a desktop or a black screen?

---

