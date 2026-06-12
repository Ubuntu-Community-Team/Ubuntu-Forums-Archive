---
title: "Problem installing a digital copy of Windows 7 on VirtualBox"
date: 2011-10-18
forum: Virtualisation
---

### Post by tossman101 on 2011-10-18
So here's an interesting one.  I have an account with Microsoft's MSDN Academic Alliance through my school, which gives me free copies of Microsoft software as long as they are downloaded (physical copies cost money) so of course I'm trying to go for the poor college student route and not pay.  So I downloaded copies of Windows 7 and Server 2008 (both 64-bit) to run on VirtualBox.  The files that I've downloaded are saved on my computer as .exe files and the instructions on what to do next that MSDN gives are as follows

To download the selected file you must follow these directions:
1. Download a “Delivery Client” executable that will handle the actual file download, using the "Start Download” button below. Please make sure to save the file with an “.exe” file extension in order to launch the file. If the file is saved without an “.exe” extension and no icon appears, please rename the file and add the extension “.exe”.
2. Launch the Delivery Client 
3. The delivery client will walk you through the following four steps to download the file:
Authorization:*Your download must be authorized. If you do not have available downloads, please contact support to request additional downloads (see Help on the website).
Downloading:*The protected file will be downloaded to you local computer.
Unpacking:*The file needs to be unpacked as it is secured.
Launch Install:*This is the final step where you can choose to install or, in the case of ISO file downloads, to create a disk.
4. Your download is now complete. You can try your download again by retrieving this delivery client from the website or by simply launching it from your local computer at a later date.

You must now install the software; if you have difficulties please see the website for further instructions.
I launch the .exe file and I get a pop up reading: 

Blocked: wine start /unix
The file '/home/tossman/Downloads/Windows_7_with_Service_Pack_1_Debug_Checked_Build_64-bit_(English).exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

I tried just renaming the .exe file as a .iso file and mounting that on the VM to boot from, but the VM gives me a FATAL error message reading: Could not read from the boot medium!  System halted.  

I'm using Ubuntu 11.04, VirtualBox 4.1, Chrome as my browser, and  my system 
MSI 790GX-G65 AM3 AMD 790GX HDMI ATX AMD Motherboard
MSI R5670 CYCLONE 1G Radeon HD 5670
AMD Phenom II X6 1090T Black Edition Thuban 3.2GHz Socket AM3
4x G.SKILL Ripjaws Series 4GB 240-Pin DDR3 SDRAM DDR3 1066 (PC3 8500)
3x Western Digital Caviar Black 750GB 7200 RPM SATA 3.0Gb/s 3.5" Hard Drive -Bare Drive

I am still pretty new to Linux and Tech Support as a whole so if this is some easy fix sorry for being a newb.

---

### Post by Dr. C on 2011-10-18
One can try to right click on the .exe file on Ubuntu and select: ```
Open With Archive Manager
``` Many .exe archives can be opened in Ubuntu this way. If it opens then extract the .iso file.

---

### Post by tossman101 on 2011-10-18
Error occurred while loading the archive.  
Output:

Archive:  /home/tossman/Downloads/Windows_7_with_Service_Pack_1_Debug_Checked_Build_64-bit_(English).exe
[/home/tossman/Downloads/Windows_7_with_Service_Pack_1_Debug_Checked_Build_64-bit_(English).exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/tossman/Downloads/Windows_7_with_Service_Pack_1_Debug_Checked_Build_64-bit_(English).exe or
          /home/tossman/Downloads/Windows_7_with_Service_Pack_1_Debug_Checked_Build_64-bit_(English).exe.zip, and cannot find /home/tossman/Downloads/Windows_7_with_Service_Pack_1_Debug_Checked_Build_64-bit_(English).exe.ZIP, period.

---

### Post by Dr. C on 2011-10-18
It sounds like Microsoft has applied some sort of DRM to the archive, which is likely why it did not work in Wine. Can you try to run it on a Windows Machine?

---

### Post by tossman101 on 2011-10-18
Yeah I've got two options either in my XP VM or my girlfriends 7 laptop.  Let me play around and I'll update this thread with the results.

---

### Post by Dr. C on 2011-10-18
I suggest the laptop. Just a hunch.

---

### Post by tossman101 on 2011-10-18
Alright, I will try that first.

---

### Post by alexpotter on 2011-10-20
It is probably an application to download the ISO i think.

Try right clicking on the EXE, go to Properties, permissions and tick the box that says 'Allow executing file as program'

Then run in Wine and see what it says.

Hope I could help :)

---

### Post by clblanchard on 2011-10-24
> **alexpotter said:**
> It is probably an application to download the ISO i think.

Try right clicking on the EXE, go to Properties, permissions and tick the box that says 'Allow executing file as program'

Then run in Wine and see what it says.

Hope I could help :)

This is correct.  You only download a small file (.exe) that you have to run to download the actual file you wanted.  By default it will save the new file to Windows temp directory.  I had this same problem about 6 months ago.  GOOD LUCK!

---

