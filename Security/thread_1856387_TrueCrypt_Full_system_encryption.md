---
title: "TrueCrypt Full system encryption"
date: 2011-10-08
forum: Security
---

### Post by rwslippey on 2011-10-08
Hello all,

I am trying to do a full drive encryption on my laptop, currently a dual boot system.

Apparently trueccrypt will create it's own boot loader, require authentication then push everything out to the normal boot loader (grub in this case).

My question is (having never really messed with the boot loader or MBR) when truecrypt starts it's wizard it asks a series of questions, most are easy and I'm good to go, but this one stumped me and I can't seem to find an answer. 

"Is the currently running OS installed on the boot drive?"
I understand the question, just have no idea how I can find out of this is true or false(for clarity, I installed windows with my OEM factory CD and then installed ubuntu 10.10 (and let it do the repartitioning) 

A few questions later I get
"Is a non-windows boot-loader install in the MBR?" I obvisouly think this is true so thats a yes and I get the following:

Truecrypt currently doesn't support multi-boot configurations where a non-windows boot loader is installed in the master boot record.

Possible solution: If you use a boot manager to boot windows and linux , move the boot manager (GRUB?) from the MBR to a partition then start the wizard again and encrypt the system partition/drive.

Note that the truccyrpt boot loader will become your primary boot manager and it will allow you to launch the original boot manager as your secondary boot manager and thus you will be able to boot linux.  So by this should I go back and install ubuntu's own system encryption? and encrypt windows on it's own?

Sorry I know this is an extended post, thanks to anyone for any insight.

Also, if I can encrypt them both with truecrypt how can I move the boot load from the MBR without trashing my system?

Thanks again

---

### Post by stlsaint on 2011-10-08
Sorry i have never used truecrypt but i know the truecrypt site is well documented.

---

### Post by bodhi.zazen on 2011-10-08
With Linux you can not encrypt everything, even with truecrypt, /boot must be unencrypted.

I suggest you use LUKS, the default, from the alternate CD.

---

