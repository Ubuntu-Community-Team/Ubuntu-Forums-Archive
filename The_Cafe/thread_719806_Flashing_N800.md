---
title: "Flashing N800"
date: 2008-03-09
forum: The Cafe
---

### Post by helliewm on 2008-03-09
I am having problems flashing my N800 with OS2008. I have downloaded the Flasher and OS2008 to my Desktop and I am following these instructions:

Flashing the Nokia N800

If you want to reflash your Nokia N800, follow the steps below:

    * PC: Download the Linux flasher-3.0
    * PC: In the same directory download the firmware image:
          o IT OS Software Edition 2008 (version 2.2007.51-3) from tablets-dev.nokia.com
          o IT OS -- List of firmware images, in case the above is not the latest Image.
    * Make sure the battery of your N800 is fully charged.
    * N800: Unplug charger and switch off the Nokia N800. Connect the tablet to your computer via USB
    * PC: Execute as root (or as a normal user with rights to use the USB port):

  ./flasher-3.0 -F RX-34_2008SE_2.2007.51-3_PR_COMBINED_MR0_ARM.bin -f -R

    * PC: "Suitable USB device not found, waiting" is displayed on the console
    * N800: Now plug in the charger to switch on the N800 or switch it on using the power button WHILE holding the Home-button
    * PC: Watch the messages as the image loads to the N800 after which it reboots automatically -- you're done now!
    

However I think I have not put the OS 2008 and Flasher in a Directory?

See screenhot from my terminal

Anyone any ideas what I am doing wrong?

---

### Post by handband2 on 2008-09-14
Check out this site:  [http://www.itcamefromtheinternet.com/tech/categories/6-Nokia-N800](http://www.itcamefromtheinternet.com/tech/categories/6-Nokia-N800)

> 01.) PC: Create a folder on your Ubuntu desktop and name it Nokia.

02.) PC: Download the Linux flasher-3.0 and save it to the Nokia folder you created.

03.) PC: Download the firmware image at the link below and also save it to the Nokia folder:
Software Edition 2008 version 4.2008.23-14 for Nokia N800

note: you will need your product id number to get the firmware image, remove the battery cover on your N800 to find it.

04.) PC: Open the Nokia folder, you need to individually right click each item you downloaded and select Properties, then select the Permissions tab, then check the box to "Allow executing file as program".

05.) N800: Unplug charger (if you had it plugged in) and make sure the N800 is turned OFF. Connect the N800 to your computer via USB (not through a USB hub)

06.) PC: Go to: Applications > System Tools > Root Terminal - you'll be asked for your password. If you don't see System Tools or Root Terminal, then right click on Applications and select Edit Menus, there you can make System Tools and Root Terminal show up in your Applications menu.

07.) PC: In the Root Terminal enter in this command then hit enter on your keyboard:

    cd /home/username/Desktop/Nokia




note: replace username with your actual username in the command above ;-)

08.) PC: In the Root Terminal enter in this command (as one single line) then hit enter on your keyboard:

    ./flasher-3.0 -F RX-34_DIABLO_4.2008.23-14_PR_COMBINED_MR0_ARM.bin -f -R




09.) PC: "Suitable USB device not found, waiting" is displayed in the console (root terminal). It's supposed to say this, so don't worry.

10.) N800: Now turn on the N800 using the power button WHILE holding the Home button.

11.) PC: Watch the messages in the root terminal as the new OS2008 Diablo firmware image loads to the N800, after which, the N800 reboots automatically - you're done!

If all went well then you can close the root terminal, unplug the USB cable from your computer and the N800, and delete the Nokia folder on your desktop. Your N800 will want to to proceed through a few steps to configure OS2008 Diablo on it. During this process it will detect your backup and ask if you want to restore it.

OS2008 Diablo is great, it's faster, easier to use, and I love that it can upgrade over-the-air.


IF YOUR MAEMO REPOSITORY DOESN'T WORK PROPERLY DO THE FOLLOWING:

Go to: Settings > Application Manager

Once the Application Manager opens, click where it actually says "Application Manager" then select:

Go to: Tools > Application Catalog

Look to see if the maemo repository listed there has a red "x" next to it and an error message, if so, select it and delete it.

Then click on the "New" button and add the following information:

    Catalog name: maemo
    Web address: [http://repository.maemo.org](http://repository.maemo.org)
    Distribution: chinook diablo
    Components: free non-free



Then hit the "OK" button.

Now click on the "New" button again and add this:

    Catalog name: maemo Extras For Diablo
    Web address: [http://repository.maemo.org](http://repository.maemo.org)
    Distribution: chinook diablo
    Components: free non-free



Then click the "OK" button.

Now click the "Close" button.

The Application Catalog should refresh and now you should have all the apps to choose from to install.

Enjoy Diablo!


---

