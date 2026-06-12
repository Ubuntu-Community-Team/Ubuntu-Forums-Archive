---
title: "completely remove wine"
date: 2011-03-13
forum: Wine
---

### Post by slashwannabe94 on 2011-03-13
Hello everyone, 

I am getting quite annoyed at wine today. 

I want to remove wine completely and have done so with the 

sudo apt-get remove --purge wine 

command, but the entries in the menu for wine are still there. 

i have re installed wine and all the programs i had previously still have entries in the menu. 

Can anyone help me with this error as it's rather annoying.

---

### Post by cogadh on 2011-03-13
After running that purge command, you need to delete the .wine directory from your home directory (its a hidden directory, so you will need show hidden files) and then manually remove any shortcuts left behind using the menu editor.

---

### Post by slashwannabe94 on 2011-03-13
I have done as you asked and deleted all wine related files. If there are any left over could you specify please? The following is the contents of my home directory using the ls -l command. 
..
.adobe
.amsn
amsn_received
.bash_history
.bash_logout
.bashrc
.cache
.compiz
.config
.dbus
Desktop
.dmrc
Documents
Downloads
.emacs.d
.esd_auth
.fontconfig
.gconf
.gconfd
.gksu.lock
.gnome2
.gnome2_private
.gstreamer-0.10
.gtk-bookmarks
.gvfs
hs_err_pid5588.log
.ICEauthority
.icedteaplugin
.icons
.local
.macromedia
.mission-control
.mozilla
Music
.nautilus
.netx
.openarena
Pictures
.profile
Public
.pulse
.pulse-cookie
.purple
.recently-used.xbel
.ssh
stty_-a_results.txt
.sudo_as_admin_successful
Templates
.themes
.thumbnails
Ubuntu One
.update-notifier
Videos
.xsession-errors
.xsession-errors.old


Thanks, 

SlashWannabe94

---

### Post by cogadh on 2011-03-13
Nope, you got them all.

---

### Post by slashwannabe94 on 2011-03-13
Strange man, the wine menu entry is still there. Damn this annoying...

---

### Post by cogadh on 2011-03-13
As I said, you need to use the menu editor to get rid of that... well, you don't NEED to use the menu editor (it can also be done by manually altering files), but it is the easiest way to get rid of the leftover menu entries. The menu editor is found under System > Preferences > Main Menu.

NOTE: If you ever intend to install Wine again, don't delete the leftover menu entries, just un-check them. When you delete them, they are permenently deleted and can only be restored by going in and manually editing the menu files. If you un-check them, they get hidden, but can easily be restored if needed via the menu editor.

---

### Post by Soulcage on 2011-03-15
Heres a list of files/folders to delete [http://wiki.winehq.org/FAQ#head-8a17a13a8a4cda9e12e24a1ad4e1b1aaf043d581]("http://wiki.winehq.org/FAQ#head-8a17a13a8a4cda9e12e24a1ad4e1b1aaf043d581")

---

### Post by 5149.5 on 2011-03-15
> **slashwannabe94 said:**
> Strange man, the wine menu entry is still there. Damn this annoying...
  In menu editor, after deleting wine-wine, you have to close the menu editor and then reopen it. Wine -wine will finally be gone when the editor is reopened.

---

### Post by silvama11 on 2012-02-16
I am trying to find the menu editor also. problem is that any system locations I see are not offering preference or  anything else. I have SYSTEM which is the drive that Ubuntu is on and system settings that show different icons (GUI) for different options (display,user accounts,back up ,etc.) so how do i get to the menu editor? I am using Ubuntu 11

---

### Post by vladmir on 2012-10-26
> **slashwannabe94 said:**
> Hello everyone, 

I am getting quite annoyed at wine today. 

I want to remove wine completely and have done so with the 

sudo apt-get remove --purge wine 

command, but the entries in the menu for wine are still there. 

i have re installed wine and all the programs i had previously still have entries in the menu. 

Can anyone help me with this error as it's rather annoying.



apt-get autoremove wine (this will unistall wine) 

apt-get autoremove (this will purge all wine files)

---

