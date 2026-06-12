---
title: "What is encrypted in Lucid Lynx 10.04?"
date: 2010-05-16
forum: Security
---

### Post by cavedog on 2010-05-16
I'm pretty sure this question has been asked and answered, but I've spent an hour looking and I can't find it.

I've done a fresh install of Lucid Lynx, and checked the little box at the user setup that calls for log on and decrypt home folder.

As I understand it, this will encrypt my home folder.  
What I don't know is:

What program is used to do the encryption?

How secure is it (compared to Truecrypt)?. 

What is included in the encryption (swap file? additional folders I make and fill with data within my home folder? etc) 


I have been using Truecrypt in the past, but I have been having problems (complete system lockup after a few minutes) moving files from a Truecrypt container on a usb drive to a Truecrypt container on the Lucid Linx computer (setup with the options I stated in my first paragraph).  I figured there might be some kind of conflict between the two encryption programs.  I made this deduction after encountering the same problem with Xubuntu and Ubuntu (both 10.04).  It's either that, or I'm holding my mouse wrong.....

---

### Post by friv_livs on 2010-05-16
As far as that option in the setup,

I don't know the details, but found chmod 700 /home/user to work better than the home folder encryption method.

---

### Post by cariboo on 2010-05-16
If you are using Trucrypt on other systems, to maintain compatability I woud use Truecrypt on Lucid. 

You can get Trucrypt for Linux [here]("http://www.truecrypt.org/downloads")

---

### Post by FuturePilot on 2010-05-16
> **cavedog said:**
> I'm pretty sure this question has been asked and answered, but I've spent an hour looking and I can't find it.

I've done a fresh install of Lucid Lynx, and checked the little box at the user setup that calls for log on and decrypt home folder.

As I understand it, this will encrypt my home folder.  
What I don't know is:

What program is used to do the encryption?

How secure is it (compared to Truecrypt)?. 

What is included in the encryption (swap file? additional folders I make and fill with data within my home folder? etc) 


I have been using Truecrypt in the past, but I have been having problems (complete system lockup after a few minutes) moving files from a Truecrypt container on a usb drive to a Truecrypt container on the Lucid Linx computer (setup with the options I stated in my first paragraph).  I figured there might be some kind of conflict between the two encryption programs.  I made this deduction after encountering the same problem with Xubuntu and Ubuntu (both 10.04).  It's either that, or I'm holding my mouse wrong.....

It encrypts your /home/$USER directory using [Ecryptfs]("https://launchpad.net/ecryptfs")
Some more info on how that works [http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html]("http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html")
It also sets up an encrypted swap partition using dm-crypt/LUKS. The rest of the system is unencrypted.

> **friv_livs said:**
> As far as that option in the setup,

I don't know the details, but found chmod 700 /home/user to work better than the home folder encryption method.

That won't stop someone from using a live CD or sudo from accessing your files.

---

### Post by cavedog on 2010-05-16
> **cariboo907 said:**
> If you are using Trucrypt on other systems, to maintain compatability I woud use Truecrypt on Lucid. 

You can get Trucrypt for Linux [here]("http://www.truecrypt.org/downloads")

Thanks, but I have Truecrypt for Linux installed. I'm experiencing lockups when I attempt to transfer files from a Truecrypt container on a usb hard drive to the Truecrypt container *(using Truecrypt)* on the Linux machine that also has been encrypted using the install option.

Unless the whole system, including the swap drive is encrypted, there is the potential for leaks.  And as I understand it, Truecrypt does not support OS encryption for Linux.

---

### Post by cavedog on 2010-05-16
> **FuturePilot said:**
> It encrypts your /home/$USER directory using [Ecryptfs]("https://launchpad.net/ecryptfs")
Some more info on how that works [http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html]("http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html")
It also sets up an encrypted swap partition using dm-crypt/LUKS. The rest of the system is unencrypted.

Thank you.  I think this will fit my needs.  I have a netbook I want to use when traveling on business, and if it is stolen or lost, I don't want the data compromised (sensitive work product). While losing a three hundred dollar netbook would suck large, as long as nobody can get to the fruit of my labors, I can replace the hardware easily enough.
It sounds like the only thing I need to be concerned about is a strong enough password.

---

### Post by Jive Turkey on 2010-05-17
If you install from the alternate cd you can encrypt the entire filesystem except for /boot and you will have to enter a password just to load the OS, even for single user mode.  It uses 256 bit aes.

---

### Post by Soul-Sing on 2010-05-17
I should use the alternate cd as earlier suggested. Truecrypt is great software with a poor license. (Fedora has refused it because of this poor license)
So LUKS and Ecryptfs would I prefer to use.

---

### Post by cavedog on 2010-05-17
> **Jive Turkey said:**
> If you install from the alternate cd you can encrypt the entire filesystem except for /boot and you will have to enter a password just to load the OS, even for single user mode.  It uses 256 bit aes.

I was wondering if there are any leaks from the encrypted home folder to the rest of the system, like MRU's, thumbnails, filename lists, etc.  The option you are proposing would wrap the whole sandwich up, not just the sliced ham.  The only thing left unencrypted would be the label on the paper bag that says "Sandwich".

I'm going to have to experiment with this.  Is this a visible option, or is it hidden?

One more question, and I will take a breath:  Is the total file encryption scheme available with Xubuntu?

---

