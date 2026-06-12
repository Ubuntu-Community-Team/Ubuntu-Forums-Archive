---
title: "Increasing the size of a WinXP Virtualbox harddisk"
date: 2010-09-08
forum: Virtualisation
---

### Post by notlistening on 2010-09-08
I have come up with a way to increase the basic size of a VirtualBox Guest Primary Disk. 

I had the problem with a WinXP disk that I made to be 10GB which by the end of the endless updates and configuration was full to the brim. 

So this is how i made it bigger. 

1. You need to download Drive Image XML for the windows machine. Install this application it is very a useful tool.

2. Shutdown the guest machine

3. In VirtualBox create a new virtual disk which is the size you want your disk to be.

4. Attach this to the guest machine by using the settings in virtualbox. The guest machine must be off to do this. 

5. Start the guest machines, navigate to control panel and then to Administrative Tools. Open computer management. From there go to Storage. It should ask if you want to install a new disk. Make sure you assign a drive letter to it and format it NTFS. All the default settings are fine. 

6. Find Drive Image XML under the start menu. It is hidden under Runtime Software. Load it up and click on copy disk to disk. Follow the on screen instructions. You can to copy from C: to E: (that is just an example) 

7. Do a full copy across then shutdown the guest machine. You will have to remove the old harddisk in the VirtualBox settings manager. Making sure that the new larger disk is the only one still listed.

8. Don't panic the machine will not boot now. The MBR is missing. You need to download the Gparted live cd iso (search Google)

9. Attach the new cd image to the guest and load into Gparted. You will notice that the new larger disk has issues and can not be modified. This is a bit of a fix. You have to set the flag for boot. Then if you click check on the drive and click apply it will try to run. This will fail do not worry as it has set the boot flag on the drive. 

10. Restart the machine and you should find the Windows boots again if all has worked. I recommend running chkdsk /F in a command prompt and restarting the machine to fix any file system issues. This requires another restart. 

11. Enjoy your new much bigger disk for your virtualbox guest system. 

Sorry the instructions are brief.

The same thing can be achieved using dd and mk2fs on Linux systems. Ask me for full instructions.

---

### Post by arak on 2011-04-12
I was running short of space for updating my Iphone and didn't want to trust Gparted etc.  So here is how I got enough space.  I created a second drive (E) with much space.  Then I went into the C drive (I'm using XP inside of Linux) and deleted the space for page files on C and put them on my new drive.  It gave me another gig on c.  You get to the page files through Systems in control panel.  Its all I need and when I install new programs I install them on the second drive.

---

