---
title: "Changing text and language files for re branding custom disros?"
date: 2008-11-18
forum: The Cafe
---

### Post by mikeuhlik on 2008-11-18
Hi everyone i was wondering how to change and edit text in a custom distro to re brand it a good example is ubuntu and linuxmint

[http://www.ubuntu.com/](http://www.ubuntu.com/)

[http://www.linuxmint.com/](http://www.linuxmint.com/)

They both have ubuntu stuff but the creator of linux mint has changed all the ubuntu text to linux mint including kernel and more i have seen so many distros out based off of ubuntu have look all over the net for months on how to do this i have even looked in the file by them selfs to see if i can just find the text ubuntu in any file the next step for me it to extract all the files from the linuxmint.iso and look in every file there for linuxmint were ubuntu would be to verify the change is correct and safe to make this is the only way i think this could be accomplished i know that the doc folders is a good start to re branding your linux distro also the item in the main ubuntu menu system i was wondering if any one new were it says about ubuntu were these file might be in the main drive were ubuntu is installed so i could change this. I am surprised with all the new distros no one has taken the time to explain this or help make a guide for the noobs like me to the Linux world with such great community support why has no one done it like the people at Linux mint they know were the file are to change this linuxmint it the best example of re branding Ubuntu ditros so i guess i will manually check every file to compare each file i can find to see what is safe and accurate to change i wish some community members would give some tip on were to find text or language file to change these text in Ubuntu when I am finished with my comparing which will be a while because I am also doing website project i will wright the best guide i can from my experience and post the pdf all over this is a big issue that know one want to tackle so ill try if any one can help of have tip and ideas i am open to hear them please let me know here i think this is the best place to start.

[color=#FF0000](Note)[/color] for re branding it to start with all document files in the doc folders. Also if some one could tell me were the language or text file extension are to make search and comparing easy i would appreciate it a lot.

P.S. Thank for your time and help everyone in the Linux community together well make better OS distros  :)

Mike

---

### Post by mikeuhlik on 2008-11-21
I am I all Alone ? :confused:

OK This is what i was trying to do i want to roll my own distro based off of Ubuntu.
I was wondering how do i change the text in the Linux operating system (Ubuntu) to the name i pick for my distro Example (MYOS). I made a PDF with Picture to explain in full detail of what i am trying to accomplish. There is a attachment to this post of the PDf to download.

After reading my PDF.
I want to Change any other text that is Ubuntu in the OS.

I was thinking dose any one know what the file Extension is for the files that hold the text for example i know when you make a translation for Ubuntu or linux Mint they are .mo and .po file but these are for Translation i need default text for the OS. Also i noticed that in the file system were Ubuntu is installed there was a file in this location 
/boot/grub it has a files called menu.lst, menu.lst.backup, & menu.lst_original which has this text

title		Linux Mint, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
boot

Changed the above to (MYOS) on all 3 file listed above it worked but cant find any other files.

title		MYOS, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
boot

I was wondering if the .lst file extension is a type of language file for the Linux OS and if it is were do I find the other ones for the default OS.

there has to be a language file format for the text to be called from by the Linux OS dose any one know what is is?
Kind like a website php script has language files to pull all the text from.

Thanks Mike

---

### Post by fatality_uk on 2008-11-21
Look for LinuxFromScratch. It's not easy, but will do what you want.

---

