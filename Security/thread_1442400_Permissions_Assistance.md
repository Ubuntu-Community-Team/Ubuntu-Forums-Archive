---
title: "Permissions Assistance"
date: 2010-03-29
forum: Security
---

### Post by ImmortalZecred on 2010-03-29
Hello, everyone. I'm brand new to this great forum, but I've been with Ubuntu for about a year now. However, now that I'm starting to get into the more advanced Ubuntu features, there is just one thing standing in the way of some new ideas I had thought of for using Ubuntu.

Normally, with my user account (I am the only account on the Ubuntu installation), I am able to complete most tasks that I needed to perform. However, lately I have been confronted with the problem of permissions denial when writing to the "File System" drive. I have dual-installed Windows XP and Ubuntu on the same system, and the Ubuntu installation is on the slave drive. My first thought when I encountered the permissions denial was that I had mistyped. Alas, I had not! For some reason, it would not let me copy a "tar.gz" file to the /usr/local directory.

Thus, in an attempt to verify the problem, I looked at my account's permissions. Everything on the list was checked, including the option to "Administer the System". So, since I couldn't solve the problem using that process, I proceeded to manually copy my file to the directory of /usr/local and install the program contained therein (It was the newest version of the Seamonkey browser). I unpacked it and compiled it, then installed it. I was required to use the "sudo" command to do all of the steps for the installation, otherwise I would always be denied access to the filesystem.

If anyone can provide some assistance with this, it would be majorly appreciated.
Thanks a lot.
-Zecred

---

### Post by new_tolinux on 2010-03-29
It is normal that you have to use sudo or gksudo for this type of things.
Everything outside your ~/ (/home/yourusername/) requires sudo or gksudo. That includes installing programs or updates.

Basicly it's a security-measure, so no program can change the system on it's own.

---

### Post by Agent ME on 2010-03-29
The sudo command allows you to run another command as the root user of the system. You have to use sudo when administering your system through the command line. If you don't do this, you can only write to directories your user has permission to (mainly /home/<name>/ and /tmp/).

Also, you probably aren't supposed to put the .tar.gz file in /usr/local/. That's just where it installs to; you don't need to place the installer/source code there.

---

### Post by ImmortalZecred on 2010-03-29
> **Agent ME said:**
> The sudo command allows you to run another command as the root user of the system. You have to use sudo when administering your system through the command line. If you don't do this, you can only write to directories your user has permission to (mainly /home/<name>/ and /tmp/).

Also, you probably aren't supposed to put the .tar.gz file in /usr/local/. That's just where it installs to; you don't need to place the installer/source code there.

Well, I was just placing it there to unpack it, then I deleted it. Just made things easier on the command line, since I'm a coding newbie.

---

### Post by jhaskins75 on 2010-03-30
Master Geeks, I too am experiencing the same problem with being granted permission to open a certain folder or file. I finally got my xsane scanner program to function as designed, only when I enter sudo xsane, which the response to this is ' Dangerous ', but it is the only way it will recognize my scanner. If I do not do this, and click on the desktop icon, when it opens, it only will recognize my web cam as the imaging device. Anyway, my main question is, when I save the scanned image to file [ Documents or my picture folder ] there is either a ' X ' mark or a lock fiqure next to it, weather is it saved to Root or to my administrator folder ' john822 '. I right click onto the file and go to permissions, and everything is greyed out, and it says I am not the owner and I am denied the ability to change permission. Now mind you, this only happens with the sane scanner program. I too have dual operating setup with Windows 7 as well as Ubuntu 9.10. I am beginning to like the He*% out of LInux over my windows, as I have just begun to understand it as a open source program. I know most primary commands such as apt-get and sudo, etc. I just want to be in command by way of permission to all files, both root and administrator...HELP!/home/john822/Documents/xsane.png 2/home/john822/Pictures/Screenshot-6.png

---

### Post by jhaskins75 on 2010-03-30
[IMG]http://www.tinypic.com[/IMG]> **jhaskins75 said:**
> Master Geeks, I too am experiencing the same problem with being granted permission to open a certain folder or file. I finally got my xsane scanner program to function as designed, only when I enter sudo xsane, which the response to this is ' Dangerous ', but it is the only way it will recognize my scanner. If I do not do this, and click on the desktop icon, when it opens, it only will recognize my web cam as the imaging device. Anyway, my main question is, when I save the scanned image to file [ Documents or my picture folder ] there is either a ' X ' mark or a lock fiqure next to it, weather is it saved to Root or to my administrator folder ' john822 '. I right click onto the file and go to permissions, and everything is greyed out, and it says I am not the owner and I am denied the ability to change permission. Now mind you, this only happens with the sane scanner program. I too have dual operating setup with Windows 7 as well as Ubuntu 9.10. I am beginning to like the He*% out of LInux over my windows, as I have just begun to understand it as a open source program. I know most primary commands such as apt-get and sudo, etc. I just want to be in command by way of permission to all files, both root and administrator...HELP!/home/john822/Documents/xsane.png 2/home/john822/Pictures/Screenshot-6.png

---

### Post by OpSecShellshock on 2010-03-30
It probably happens because your scanner is owned by root, which would mean that the images that get scanned are also owned by root. You can either change permissions or ownership of the scanner, which would stop you having to sudo in order to use xsane (would be easier to do in terminal than graphically). As things are set up now, it appears that the scanner is owned by root but xsane is running as you, which is where the issues are coming from.

---

### Post by cariboo on 2010-03-30
Make sure you a member of the scanner group. You usually get added to the scanner group on first start up, or you should see a notification to do so. Just go to System->Administration->Users & Groups, and add yourself there.

---

