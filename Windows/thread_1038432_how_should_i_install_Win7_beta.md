---
title: "how should i install Win7 beta?"
date: 2009-01-12
forum: Windows
---

### Post by Universal344 on 2009-01-12
I recently downloaded the windows 7 beta ISO and burnt it to dvd.  Currently I have Windows Vista Ultimate and Ubuntu 8.10 running.  I want to install the windows 7 beta but I know people have had issues with installing it correctly on multi-boot systems.  Is there a proper procedure for me to use when installing it?  My goal is to not have to reinstall GRUB, edit GRUB.lst or write a new MBR to my hard disk.  I realize this may be impossible and I appreciate any help you can provide.  Please note I do not know how to correctly add/remove an entry from GRUB.lst, so if I need to please explain how.  I know I should know how, I just haven't had the occasion to learn.  Again, thank you for any help.

---

### Post by whoop on 2009-01-12
I would would only install that inside a virtual machine.... try virtualbox. Windows 7 won't touch your system and you didn't even have to burn it onto a dvd

---

### Post by electrogeist on 2009-01-12
> **Universal344 said:**
> My goal is to not have to reinstall GRUB, edit GRUB.lst or write a new MBR to my hard disk.  I realize this may be impossible

Well are you more handy with the screwdriver or the keyboard?  

If you have another hard drive, you could just swap drives.

---

### Post by hikaricore on 2009-01-12
You don't wanna hear where I think you should install it... :guitar:

---

### Post by Universal344 on 2009-01-12
I've considered the drive swapping and I might do that if I need to but I want to try the multi-boot thing first.

---

### Post by Battie on 2009-01-12
I started with it in a virtual machine but was unhappy with the results, as it was slower (because of the expanding hard drive), and I could not enable Aero.  To get a real testing experience I resized the Vista partition on my work laptop to give me a spare 16 gb.  If you are using the new Windows bootloader there's almost no effort in getting it to dual-boot.  I'm not sure how it will go with GRUB though.

---

### Post by I-75 on 2009-01-12
Hard drive swapping is the way to go.

---

### Post by mgol on 2009-01-12
Be warned that it's beta, and it can destroy Your data. For example, Windows Media Player overwrites the beginning of opened mp3s (sic!) unless You download proper updates etc.

Nevertheless, I wouldn't risk installing it in my real HDD until it's finally released...

Not to mention that I use Ubuntu to work and XP for games & Skype and I don't really expect from Windows anything more that XP can give me... ;)

---

### Post by rickyjones on 2009-01-12
I've installed it on my laptop as the primary OS for testing and so far so good on a Dell Latitude D630.

If you wish to keep your current OS structure then you should be able to do a clean install to a free partition then re-install Grub after the fact. However I did not test this theory.

Thanks,
Richard

---

### Post by mamamia88 on 2009-01-13
i was wondering the same exact thing.  i am downloading it now and don't want to mess up grub or my existing dualboot.  i have 2gb ram and a 1.8ghz dual core amd processor should it run fine in virtualbox if i dedicate 1gb ram to it?

---

### Post by kahrytan on 2009-01-14
Separate hard drive is best. Windows 7 uses a boot partition it sets up for clean install.

---

### Post by rickyjones on 2009-01-14
> **mamamia88 said:**
> i was wondering the same exact thing.  i am downloading it now and don't want to mess up grub or my existing dualboot.  i have 2gb ram and a 1.8ghz dual core amd processor should it run fine in virtualbox if i dedicate 1gb ram to it?

That's what I did as an initial test. Worked great!

Thanks,
Richard

---

