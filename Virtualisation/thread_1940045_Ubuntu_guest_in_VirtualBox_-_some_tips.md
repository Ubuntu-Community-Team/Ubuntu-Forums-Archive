---
title: "Ubuntu guest in VirtualBox - some tips"
date: 2012-03-12
forum: Virtualisation
---

### Post by TE7 on 2012-03-12
1. Getting a high or fullscreen resolution for your Ubuntu guest:

If installing the Guest Additions doesn't give you a high enough resolution for a decent sized window, or nor a fullscreen resolution, try the following link:

[http://www.dreamincode.net/forums/topic/76340-ubuntu-in-virtualbox-set-a-high-screen-resolution/](http://www.dreamincode.net/forums/topic/76340-ubuntu-in-virtualbox-set-a-high-screen-resolution/)

I found I had to edit my xorg.conf (/etc/X11/xorg.conf) to give me fullscreen resolution. After you make the change, just reboot, and you will have your desired resolution (windowed or fullscreen). If fullscreen, just choose Fullscreen from the virtualbox view menu option.

2. Sharing a Windows folder with Ubuntu (for a Windows host and Ubuntu guest):

- In settings for the guest, choose your Windows folder to share.
- In your home folder in Ubuntu you can create a new folder (VBoxShared for example).
- Open the terminal in Ubuntu, and type the following command:

sudo mount -t vboxsf NameofYourWindowsFOlder ~/NameofYourFolderToShareInUbuntu

For example, if in the guest settings your choose a Windows folder called VirtualBoxShared, and created a folder called VBoxShared in Ubuntu in your home folder , you would use the following command:

sudo mount -t vboxsf VirtualBoxShared ~/VBoxShared

Just type in your password when prompted, and hit enter.

To make things quicker,

- You can open gedit, enter your command, and save it to the Desktop.
- Then right click on the saved file, choose Properties, then Permissions,
and check "Allow executing file as program"
- Then just double click, and choose Run In Terminal, and enter your password.

If you want to automatically access your Windows share every time you boot into your Ubuntu guest, you can do the following:

Add yourself (username) to the vboxsf group using the following command:

sudo usermod -a -G vboxsf username

Then logout and log back in, and your Windows shared folder should show up /media in the filesystem with read/write permissions.

Make sure that in the settings in VirtualBox for your Ubuntu guest, you select the Windows shared folder as auto-mount.

3. Create desktop launchers (for those who like desktop icons, in the Gnome Classic desktop, for example):

[http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html](http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html)

To make things quicker, open gedit, paste the command into it, save to desktop, and make executable, as in step 2 above. Most all of your program executables will be in /usr/bin when your browse for your command.

I hope these tips help.

Tom

---

### Post by speedwlk on 2012-03-13
Nice tips. I just would like to add the following comment regarding shared folders between the host os and the guest os[ubuntu].

After installing the guest additions in the guest[ubuntu], the user should add him/her-self to the group "vboxsf".

Then in the "Shared Folder" section of the properties of the guest os[ubuntu], selecting "auto-mount" option for shared folders will mount the folder automatically under /media with the required read and write permissions.

This avoids having to use the terminal to mount the shared folder.

Happy virtualization!

---

### Post by TE7 on 2012-03-13
Thanks. I'll add that.

---

### Post by niladrithedon on 2012-03-14
Thanks buddy. You saved my day. I could not connect my cdma usb modem in linux, so virtualbox seemed a very good option. Till this day I could not mount shared folders in ubuntu as I am not very good with commands. But I did it after reading your topic. Now I am surely free to expand my knowledge in ubuntu. Thanx.

---

### Post by TE7 on 2012-03-14
You are welcome.

---

