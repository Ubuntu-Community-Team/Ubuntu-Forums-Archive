---
title: "Truecrypt + TPM + Fingerprint reader... Possible?"
date: 2008-10-21
forum: Security
---

### Post by Tim T on 2008-10-21
I have a VAIO SR-190 (or I will when Sony replaces the motherboard on my month old notebook) and would like to install 8.10 when I get the notebook back in a few days. 
Firstly, I am trying to decide whether to use LUKS from the alternate Ubuntu boot disk or TrueCrypt for whole drive encryption. Speed is somewhat an issue, however overall security is paramount, so I am leaning towards Truecrypt. 
I also have an Infineon TPM chip in my notebook, and am wondering how Ubuntu would play ball with it... whether or not it would interfere with Truecrypt. 
And lastly, will the fingerprint reader work like it does in Vista? In Vista, When you unlock the drive with a finger swipe... it loads Vista, and automatically logs you into your username.

My ideal security setup would involve powering the notebook on, swiping my finger and entering a password. Then entering a different Truecrypt password. And finally entering a third (yet again different password) or perhaps have the BIOS auto-login to ubuntu ala Vista with TPM support.

PARANOID?! Yes, Yes I am. I have confidential information on my notebook, which I would like to keep confidential. Any information or links you folks can provide would be appreciated.

---

### Post by nubdora on 2008-10-21
> **Tim T said:**
> I have a VAIO SR-190 (or I will when Sony replaces the motherboard on my month old notebook) and would like to install 8.10 when I get the notebook back in a few days. 
Firstly, I am trying to decide whether to use LUKS from the alternate Ubuntu boot disk or TrueCrypt for whole drive encryption. Speed is somewhat an issue, however overall security is paramount, so I am leaning towards Truecrypt. 
I also have an Infineon TPM chip in my notebook, and am wondering how Ubuntu would play ball with it... whether or not it would interfere with Truecrypt. 
And lastly, will the fingerprint reader work like it does in Vista? In Vista, When you unlock the drive with a finger swipe... it loads Vista, and automatically logs you into your username.

My ideal security setup would involve powering the notebook on, swiping my finger and entering a password. Then entering a different Truecrypt password. And finally entering a third (yet again different password) or perhaps have the BIOS auto-login to ubuntu ala Vista with TPM support.

PARANOID?! Yes, Yes I am. I have confidential information on my notebook, which I would like to keep confidential. Any information or links you folks can provide would be appreciated.

If you're that paranoid about the information on the notebook, you're better off not lugging it around. You're better off using a clean notebook, booting from a live CD, and storing the information on a flash disk fitted with a string that you would tie to a back tooth and swallow, coughing it up when the information is needed. I'm not joking either.

---

### Post by Tim T on 2008-10-21
> **nubdora said:**
> If you're that paranoid about the information on the notebook, you're better off not lugging it around. You're better off using a clean notebook, booting from a live CD, and storing the information on a flash disk fitted with a string that you would tie to a back tooth and swallow, coughing it up when the information is needed. I'm not joking either.
I'd just be worried about my stomach acids burning my data up.... :P
I don't mind the passwords, I want a complete OS, and I'm not a fan of booting off of live discs, however I agree with you that it makes some sense.

---

### Post by Tim T on 2008-10-24
Bump... Any ideas on how the trio will work together?

---

### Post by nubdora on 2008-10-24
From what I've looked up, Bitlocker and WinMagic are the only names that support FDE with TPM integration.

---

### Post by Tim T on 2008-10-26
Hmm... well how about encrypting the drive with Truecrypt and using a fingerprint to login to ubuntu? Should be an acceptable amount of security I would think. Is there an app out there that for linux that will allow a fingerprint login?

---

### Post by hyper_ch on 2008-10-27
I don't think fingerprint readers are secure.

---

### Post by nubdora on 2008-10-27
> **Tim T said:**
> Hmm... well how about encrypting the drive with Truecrypt and using a fingerprint to login to ubuntu? Should be an acceptable amount of security I would think. Is there an app out there that for linux that will allow a fingerprint login?

One option:

[http://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html](http://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html)

Yes, that will work with Truecrypt.

---

### Post by nubdora on 2008-10-27
> **hyper_ch said:**
> I don't think fingerprint readers are secure.

I think it's ironic fingerprint readers are on devices users' use with their fingers.

---

### Post by hyper_ch on 2008-10-27
> **nubdora said:**
> i think it's ironic fingerprint readers are on devices users' use with their fingers.

+1

---

### Post by HunterThomson on 2009-09-28
> **nubdora said:**
> If you're that paranoid about the information on the notebook, you're better off not lugging it around. You're better off using a clean notebook, booting from a live CD, and storing the information on a flash disk fitted with a string that you would tie to a back tooth and swallow, coughing it up when the information is needed. I'm not joking either.


This is an Old thread.. Like all threads about TPM but Owe well.

That quote is like saying... "If your so paranoid about getting in a car accident that you would ware a Seat Belt.... You should just walk."



Your wrong. You can do one of three things....

No Encryption == No Physical Security

FD-Encryption == Stops all script kitty's and lazy cackers. Not Gov or real Crackers

FD-Encryption + SSD == Stops all script kitty's, All crackers, All Gov((At lest for a few months))


If you FD-Encrypt a HHD there is still all kinds of little tricks to "maybe" "Get around" your Encryption. Also, FD-Encryption Software sold with computers have back-doors built-in. Like if I use my HP elitebook FD-Encryption. The FBI could just call up HP and HP would tell them how or give them software to decrypt my drive in 5min's.

--------------------------------------------

I would like to try out the TPM though. I don't know a lot about it yet but the idea of a dedicated chip to handle encryption sounds like it will add a few things Truecrypt can't do. It also sounds like it could greatly speedup FD-Encryption as long as your not trying to protect your data form a Gov.

---

### Post by undecim on 2009-09-28
A required fingerprint would bring almost no more security to your suggested setup. The only thing the fingerprint reader will act as a soft password, which will be bypassed as easily as a password on an unencrypted setup (in other words, I boot a live cd, and your fingerprint requirement gone)

If I were you, I would use LUKS to encrypt the root partition, and create a GRUB CD to boot with (no boot partition on the machine; this way your boot partition is completely READ-ONLY, to prevent anyone with physical access to your machine from poisoning your boot partition then coming back later to retrieve the logged password). The caveat to this is that you will need to recreate the CD each time you upgrade your kernel (and if you have this machine connected to the internet at all, you will want to stay as secure as possible otherwise your encryption scheme will be worthless. Encryption protects against a stolen machine, not a hacked machine)

If you want another layer of encryption, you can set up ecryptfs on your ~/Private directory, and store all confidential information there, where it will be transparently encrypted (maybe after encrypting the REALLY sensitive files with another program if you are THAT paranoid...)

ecryptfs has two benefits: 1: it won't slow down your computer except when reading or writing to the files in your ~/Private directory (or, if you are like me, your entire home directory), and 2: If you unmount it, then your files cannot be retrieved without the password even if a running machine is compromised (though you will need to remember to unmount when you are not using it if you are worried about that).

Also, one final note: You should make sure that this machine will lock when you leave it anywhere. From your post it seems that you wouldn't leave it anywhere for any amount of time, but if you must, even in a trusted place (i.e. in the office of the company/organization whose secrets are on your laptop) make sure you lock your screen. It wouldn't be a bad idea to use that "blue proximity" app with your phone if you have a cell phone that will be on when you have this computer around, that way if you forget to lock it (or if someone runs off with it, etc.) it will lock itself. (You should probably also disable the unlock feature if you use that program...)

---

