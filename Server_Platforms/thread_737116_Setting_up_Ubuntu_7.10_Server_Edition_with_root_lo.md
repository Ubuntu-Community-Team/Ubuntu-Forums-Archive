---
title: "Setting up Ubuntu 7.10 Server Edition with root login &amp; Gnome Desktop"
date: 2008-03-27
forum: Server Platforms
---

### Post by Yacaph on 2008-03-27
I was setting up an in-house file server and development “sandbox” and decided to try the Ubuntu 7.10 Server Edition. After installing Ubuntu 7.1 Server I was surprised to find that the user that was created during the install process did not have SU privileges; su and sudo did not work for this user; and there was no root login. Also, I wanted a GUI X-terminal desktop.

I found an excellent screen by screen install procedure at [http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html) for 6.1 and 7.1 seemed to be the same as far as the screens go. At the end of the process the author wrote:

“Enable root Account in Ubuntu server (Not Recommended for security Reasons this is just Optional)
After the reboot you can login with your previously created username (test). Now we will enable the root account using the following command
sudo passwd root
and give root a password.
Now onwards we become root by running the following command
Su”

This did not work on 7.1. After some extensive research I found information that finally got me up and going, and I want to share this and thank those who have contributed.

After installing Ubuntu 7.10 Server Edition, during the re-boot the system displays the message:
Grub loading…
Press <ESC> to enter the menu

Press <ESC> and select Ubuntu 7.10, kernel 2.6.22-server (recovery mode)
From there you will be logged as 'root' without asking for any root password. Now enter “passwd root” and you will be allowed to enter and verify a password for the root user. Next enter “visudo” to edit the super user file. In this file find the User privilege specification section and add the user name that you assigned during the install.

# User privilege specification
root ALL=(ALL) ALL
<username> ALL=(ALL) ALL

Re-boot and login with user name that you assigned during the install. You should now have super user privileges.

For more information on setting up user privileges see:
[http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/](http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/)


Ubuntu Server Has No GUI? How Do I Add A Gnome Desktop?

I like GUI’s and decided to install Gnome, and I wanted it to be a part of the primary installation rather than installed separately. Here are the commands for a few of the X-terminal installs.
sudo apt-get install ubuntu-desktop (for gnome)
-or-
sudo apt-get install kubuntu-desktop (kde)
-or-
sudo apt-get install xubuntu-desktop (xfce)

After the Gnome install I wanted to allow for root user login (more on why later). This can be accomplished by opening a terminal window via Applications > Accessories > Terminal.
Enter “sudo gdmsetup”. You will be ask for your user password (not the root password) and then the Login Window Preferences will be displayed. Select the security tab and check the “Allow local system administrator login” check box and close the window. You should now be able to login (with warnings) as root. Why a root login? Because is more “stuff” available to root than is available to the user such as the partition editor and the login windows preferences and I would rather access these from the menu rather than trying to remember the package name to type in from the terminal.

---

### Post by cdenley on 2008-03-27
Things like "partition editor" (gparted) are available to admin users (including the one created during installation) from the gnome menu, you just have to enter your password when prompted. You shouldn't run anything as root unless it needs root privileges to perform it's function. When you run gnome as root, you run all user applications and applets as root. The default user account should work with sudo, and did on the two gutsy server installs I'm currently running. I think "su" asks for the root password, so you shouldn't use it in ubuntu. You can use "sudo su", but that would be the same as "sudo -s" or "sudo bash". The server install does not include a gui since most server administrators would prefer a minimal system to reduce the disk usage and prevent unnecessary programs from running to improve security and performance. If you want gnome, you should start with a desktop install. Also, gnome is more of a heavy desktop environment, and not the first choice for a server. Xubuntu would probably be a better option for a server if a gui is absolutely necessary.

---

