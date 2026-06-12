---
title: "Can't save network setting"
date: 2011-03-09
forum: Ubuntu Studio
---

### Post by Python42 on 2011-03-09
I'm running Ubuntu Studio 10.10. When I first installed it I was not able to connect to my wireless router (although my cable connection worked) because my router security was set to wpa personal (which was not an option in the drop-down list). I changed my router to wpa personal-2 (which was in the list) and I was able to connect after entering in my key. Of course, I had to change the network settings on the other four computers on the same router. Somehow, after applying the usual updates, my network connection stopped working. Ubuntu changed my settings back to wpa personal. The wireless connection was checked but inactive. When I attempted to change it back to wpa personal-2, I selected the correct setting and entered the security key but the connection reset itself back to wpa personal. I couldn't download any fixes even if they were available because my cable connection is now inactive. If I try to select it the same thing happens; after a few seconds any changes I make are discarded.

This is extremely frustrating so I would much appreciate any help.

additional info added 2011-03-10

I decided to start from scratch. I removed all internal drives leaving only the Ubuntu Studio 10.10 install DVD and the USB hard drive. I installed from scratch using the entire drive. I immediately noticed problems after the initial boot into the new system. The first minor problem was that even after disabling bluetooth (which worked) I was unable to successfully disable the "show bluetooth icon". I would deselect the box but the icon would remain. Going back into preferences showed it still selected.

Network setting were likewise unsaved. Setting the wireless connection to wpa-personal-2 and entering the key resulted in the setting being restored to wpa-personal with no wireless capability. I bit the bullet and set my router back to wpa-personal. I was still unable to establish a network connection. The cable connection, however, was functioning. Thinking it might not let me have two connections active at once, I unplugged the cable. I was still unable to get wireless working. Now, however, Ii was unable to select the cable connection (after reinserting the cable) and save the new status. I had to reboot to get the cable connection working.

I decided to install the recommended proprietary nvidia driver (recommended by the installed Ubuntu). It required a reboot which resulted in an error during the boot process even though the video seemed to be working.

Can someone remind me exactly why Ubuntu is said to be so much friendlier than Windows 7? I have installed hundreds of Windows systems over the last couple of decades and have never had these kinds of problems.

---

### Post by Python42 on 2011-03-10
OK. I don't know why this software was not included with Ubuntu Studio or why there was not a big, bold statement to the fact that WIRELESS CONNECTIONS MAY NOT WORK UNLESS YOU ALSO INSTALL WICD, but I was able to unearth this little gem and now my wireless is working.

---

