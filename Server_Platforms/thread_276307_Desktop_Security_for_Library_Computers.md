---
title: "Desktop Security for Library Computers"
date: 2006-10-12
forum: Server Platforms
---

### Post by nixios on 2006-10-12
Hi Gurus,

I'm helping my community public library for their 34 computers
to upgrade with EduUbuntu linux since their current XP pros 
installed are all pirated copy.

My Questions are:
1. Is it possible to lock down users not to change desktop
   background and default homepage?

2. Also can users cannot be alter the systems configurations?

3. Is is possible to lock down copying files from the hardrive
   to the USB drive? but they can be still use the USB drive.

4. Users should not be allowed to install any softwares.

Is there any simple way to do it?

Thanks in advance.
Nix

---

### Post by aysiu on 2006-10-12
KDE has *kiosktool*

Gnome has *sabayon* and *pessulus*

---

### Post by skymt on 2006-10-12
1. Yes, with a program called [Sabayon](http://www.gnome.org/projects/sabayon/). You can install it through Synaptic.

2. Sabayon again. It's really a great tool.

3. What files do you not want them to copy? They'll be able to copy anything to which they have read access, to anywhere that they have write access. There's no real way around that.

4. System-wide, or in the user account? Blocking system-wide software installation is easy. Just don't give the guest user admin powers. Blocking the user from bringing their own applications on a USB stick or from the Internet is much trickier. However, it is possible. You will want to have /home on a different partition. aysiu, of these forums, wrote a [good howto](http://psychocats.net/ubuntu/separatehome) for that. Next, edit the /etc/fstab entry for /home, and add the "noexec" option. Something like this (example modified from the howto):```
/dev/hda7 /home ext3 noexec,nodev,nosuid 0 2
```That will block custom compiled programs, but not interpreted (Ruby, Python, Perl, shell). For that, you need to remove execute permissions on the interpreters for the public user.

---

### Post by nixios on 2006-10-12
Thanks for replying.

3. Only selected folder.This folder contains files that
   for public views only but shouldn't be copy.
4. Only the selected public user.
5. Another thing,how can i create a username without 
   setting up a password?.

So,there is no settings on ubuntu system itself to
implement this kind of setup.I still need to install
3rd party software like sabayon?

Thanks again.

---

### Post by skymt on 2006-10-12
> **nixios said:**
> Thanks for replying.

3. Only selected folder.This folder contains files that
   for public views only but shouldn't be copy.
4. Only the selected public user.

So,there is no settings on ubuntu system itself to
implement this kind of setup.I still need to install
3rd party software like sabayon?

Thanks again.

I don't think 3 is possible. What's in the folder? Why would you want people to look at something but not copy it?

For 4, I meant whether you wanted to block the guest user from installing software system-wide or allow it to install software just for itself.

Sabayon isn't 3rd party. It's an official part of the Gnome desktop, it's just that Ubuntu doesn't install it by default. I don't think Edubuntu does either, which is kind of odd.

---

### Post by nixios on 2006-10-12
actually,its only a video files/mpeg,some sort of
educational tutorials.

thanks again.

---

### Post by Macchi on 2006-10-13
To be able to show documents or contents without the ability to copy them, the first idea that comes to my mind is to transform the documents into locked OpenOffice presentations available only on a hidden area, locally or on the intranet. To start the presentation you have to use a small program that starts a viewer but, importantly, hides the actual location of the files.

All these measures may evolve into something quite weird depending on the security level required. Often there is always a workaround to copy the contents if you are granting users the access to usb drives, webmail, printers, screen snapshots, and ultimately even video or voice recorders, paper and pencil, etc. There will be always a possibility for someone to spread the content they have accessed. Choose your solution accordingly. 

I understand that there are many situations when this is required, for instance in school examinations and tests, presenting confidential information or personal data.

Maybe a kiosk terminal is a better choice? It is awful but sometimes necessay to restrain freedom. Right now I have to stop myself from wasting workhours on this fantastic forum.

---

### Post by nixios on 2006-10-15
macci nice post..another question,what folder/directory 
should i install prgrams such as flash or adobe in a system
wide installation?

---

### Post by peanut butter on 2006-10-15
for flash, install flashplugin-nonfree from multiverse. There are many adobe alternatives. but i dont know how to install it.

---

### Post by nixios on 2006-10-16
I finally got it working, i just goto one website
that has autuomatic flash plugin installation.

---

### Post by nixios on 2006-10-16
skymt, i installed sabayon through synaptic 
successfuly but i got this error when i tried
to run it through terminal(#synaptic&).

Error: This desktop don't have an admin rights
to run this program?

but i login as admin. I even use the command sudo -i.

any thoughts about this, i have searched enough but 
i couldn't find any answers.

Thanks.

---

