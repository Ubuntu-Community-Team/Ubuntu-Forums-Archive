---
title: "mount point for camera"
date: 2008-10-14
forum: The Cafe
---

### Post by Silvernail on 2008-10-14
I have Ubuntu 8.04 with all updates.
When I plug a flash drive in to a USB port I get an icon on the screen that I can right click on and find which drive it is mounted on. Then I can go to a command line and do whatever I want.

When   I  plug my USB camera into  a port I get a box telling me 'A camera has been detected' What to do?

How do I find where this camera is mounted?

Just as important, the media is 2 gigs and has a couple hundred pictures that i am now ready to clear. I don't want to have to delete each one individual when a move to trash or null would be quicker.

I have 'gwenview' and 'f-stop' installed and neither seems to have a media clear function.

Can anyone help?
TIA
Dave

---

### Post by brujoand on 2008-10-14
In terminal do: "df -h" to se all mounted filesystems, you'll be able to identify your camera here from the size, and also you will see the mount point. Ususally something like "/media/camera"

Then. either go graphical, or continue using the terminal, change direcory to the camera, something like "cd /media/camera" depending on the result from "df -h". Then to delete all files in the folder(which is everything on the camera) type "rm *". 
!! BUT!!! Beware, if there are eny needed files or folders other then the pictures, these will be deleted to. 
To delete only jpg's, type "rm *.jpg" * is a wildcard..

Hope that helps

---

### Post by patrickballeux on 2008-10-14
Some camera do not have a mount point because they use a PTP protocol (Not sure about the name of the protocol).


Normally, when something is mounted, you have a new folder in /media/.  If it is not the case, then you have to import your pictures using the tool that is showing you when you connect it.

It will work, but you have to deleted your files with the camera...

I think that the software used to import is F-Spot.  Take a look in "System - Preferences - Periphricals and removable media" (Hope it is named like this in english since my menu is in french...)

You will see what is called when you connect a camera...

Good luck!

---

### Post by Silvernail on 2008-10-16
Let me thank both of you for your feedback.

I finally got the problem resolved by going to my old Linspire distribution on another computer. I  had tried it several time and for some reason it refused to acknowledge the existence of a USB media card inserted in the card reader.

But this last attempt was successful and I got a 'Generis Storage Media' icon  on my Destop screen. Then I was able  to see that the camera was mounted on '/deb/sdc1'.  A  directory change and 'rm -Rf *' cleared the card.

Thanks again.
Dave

ps
PTP?  Photo Transfer Protocal??

---

### Post by earthpigg on 2008-10-16
> **Silvernail said:**
> 
ps
PTP?  Photo Transfer Protocal??

my noob understanding: some dumb thing that really accomplishes nothing and results in our digital cameras not being able to be read like simple USB storage devices. i had a similar problem.

and i STILL dont know how/why the .avi files off my camera end up all choppy when i play them.

---

### Post by chucky chuckaluck on 2008-10-16
this is what i put into my /etc/fstab file for my camera...

```
/dev/sdb1       /home/fuscia/camera        vfat        user,noauto,exec 0       0
```

all you need to do from there is to make a directory in you home folder for camera and do *mount camera* in the terminal and your pics will appear in you 'camera' folder. (you might have to mount as root... haven't used ubuntu in a while...)

---

### Post by Silvernail on 2008-10-17
> **chucky chuckaluck said:**
> this is what i put into my /etc/fstab file for my camera...

```
/dev/sdb1       /home/fuscia/camera        vfat        user,noauto,exec 0       0
```

all you need to do from there is to make a directory in you home folder for camera and do [i]ount camera[i] in the terminal and your pics will appear in you 'camera' folder. 9you might have to mount as root... haven't used ubuntu in a whole...)

How do you remove the pictures from your camera after you have imported them to your camera directory?

How did you determine that 'sdb1' was the correct device to mount? Or does this force the camera to be mounted to this device.

Thanks for the feedback.
Dave

---

### Post by chucky chuckaluck on 2008-10-17
> **Silvernail said:**
> How do you remove the pictures from your camera after you have imported them to your camera directory?

How did you determine that 'sdb1' was the correct device to mount? Or does this force the camera to be mounted to this device.

Thanks for the feedback.
Dave

i use the camera to delete pics. although, i do recall using my computer to delete some (i probably had to change the permissions to do so, but i don't recall).

i had some app automounting my camera, so i used the file manager to track down the device. i tried recently to do the same thing after changing to jfs on arch, but it didn't recognize sdb1. i doubt you'd have the same problem using ubuntu. 

be aware, it's out of shear luck i did this. i'm really just an end user with too much free time.

---

