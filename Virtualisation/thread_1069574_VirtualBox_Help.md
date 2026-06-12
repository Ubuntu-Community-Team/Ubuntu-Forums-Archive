---
title: "VirtualBox Help"
date: 2009-02-14
forum: Virtualisation
---

### Post by Dal1980 on 2009-02-14
Hi everyone, I'm completely new to Ubuntu but I really like what they have done. I come from a windows background so please bare with me, I'm a complete noob when it comes to linux. :)

My problem;

I installed VirtualBox (Sun Microsystems) latest version and I went ahead and created a new virtual drive to install windows XP Pro onto. (I intent to use the VM while I slowly adjust to Ubuntu OS and find replacements for the programs I have used in windows). I popped my XP Pro install disc into the cd drive last night and managed to install windows successfully. I was playing around with it last night (windows I mean :p) and I had managed to close the virtualbox a few times between messing about but it worked when I went back to the console and typed "virtualbox", the app kicked back in and I was able to select to load WinXP pro again... cool

I turned the pc off last night (shut down both the virtualbox properly and ubuntu) but when I went back to the console this morning to load "virtualBox" back in, it said something about the program could not be found and suggested I used "sudo apt-get install virtualbox-ose" to start installing it again. I did that and the thing installed but I've now just got a message saying that it cannot be started;


failed to create VirtualBox COM object
The app will now terminate
------------------------------------------
Could not load the settings file '/home/trend/.VirtualBox/VirtualBox.xml'.
Cannot convert settings from version '1.6-linux'.
The source version is not supported.


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
VirtualBox
Interface: 
IVirtualBox {557a07bc-e6ae-4520-a361-4a8493199137}
-----------------------------------------------------

I've never used virtualBox at all other than last night so I dont recognise the problem.

I also couldnt find the virtual drive to copy stuff over so that XP could see the files.

Anyone know of any solution to either of these problems. Oh as a side note, when I did install VBox (downloaded it off the website) I noticed also that there was no way to start it other than going to the console window and typing it in there (no program icon existed anywhere within the ubuntu menu systems.:confused:

Thanks in advance
Dal1980

---

### Post by Dal1980 on 2009-02-14
Solved!

I followed this doc to the letter and everything is working again and I may even have solved my USB stick problem while I was at it.

Recommended read/bookmark;

[http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu-810-intrepid-ibex/](http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu-810-intrepid-ibex/)


:guitar:

Cheers
Dal

---

