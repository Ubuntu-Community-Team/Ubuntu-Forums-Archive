---
title: "Replacing the Ubuntu booting screen"
date: 2011-11-16
forum: Ubuntu Dev Link Forum
---

### Post by random_vamp on 2011-11-16
I'm working on a Ubuntu based virtual appliance and am currently trying to replace the boot progress screen.  In this text-only setup we're using this screen has a faintly-purple background, and text reading "Ubuntu 11.04" (ie the version we're currently using) and four progress dots (I attached a screen shot).  It looks to be straight text and I suspect its generated from some boot script, but I haven't been able to figure out where its coming from in order to replace it.  Any pointers?

---

### Post by random_vamp on 2011-11-17
Following some suggestions from a coworker I tried expanding the initrd.img that was included with the Ubuntu image we were using and tried changing the title field in these plymouth files:

/lib/plymouth/themes$ ls -R 
.:
details  text.plymouth  ubuntu-text

./details:
details.plymouth

./ubuntu-text:
ubuntu-text.plymouth  ubuntu-text.plymouth.in

But that didn't seem to do anything, and it appeared that "Ubuntu 11.04" didn't appear in any other files within initrd.

---

### Post by BlaineM on 2011-11-18
As far as installing custom Plymouth themes, I don't have that information, but how to change the theme to ones installed through Ubuntu Software Center or .deb, do the following:

$ sudo update-alternatives --config default.plymouth
-- this will bring up a menu in which you can enter the number of the installed Plymouth theme you want to use.  Type the number of the one you want, then press enter.  (I haven't tested what specifically this does, but it probably just changes the config files, which you might already be doing).

then

$ sudo update-initramfs -u
-- this will update your existing initrd.img like your co-worker was suggesting.

When you issue a reboot or shutdown, you'll see the new Plymouth theme being used.  It will stay persistent until you change it again.

---

### Post by BlaineM on 2011-11-19
Alright, so here's how to manually install a new Plymouth theme.

*note, my example commands shouldn't be directly copied, since the theme files are located and named differently than in my examples.  Please substitute the "$name" references with the proper locations and names on your system.

In my testing, I downloaded a theme from gnome-look created for a RHEL system.  The paths within the theme's *.plymouth file weren't accurate for the way Ubuntu has Plymouth installed, so I needed to update the file to point to the correct locations.


- First, copy your new theme directory into /lib/plymouth/themes.  You'll need to run the commands as root with sudo, since /lib/plymouth/themes is only writable by root.
```
$ sudo cp -R /home/$userdir/$directory/$new_theme_directory /lib/plymouth/themes
```

- Next, change directory to /lib/plymouth/themes
```
$ cd /lib/plymouth/themes
```

- Now, do a long directory listing to see the details and permissions of the files within the themes directory.  The default.plymouth file is the one we're looking for.
```
$ ls -lah
lrwxrwxrwx 1 root root   34 2011-11-18 17:29 default.plymouth -> /etc/alternatives/default.plymouth
```

(notice the default.plymouth file [which is what Plymouth reads to load the theme] is a symbolic link to another file)

- If we do a long listing on the file default.plymouth is point to, we'll see it's actually a symbolic link pointing back to a $theme.plymouth file located in /lib/plymouth/themes/$old_theme_directory
```
$ ls -lah /etc/alternatives/default.plymouth
lrwxrwxrwx 1 root root 37 2011-11-19 17:15 /etc/alternatives/default.plymouth -> /lib/plymouth/themes/$old_theme_directory/$theme.plymouth
```

- So, we'll want to change the symbolic link within /etc/alternatives to point to the *.plymouth file located in the new theme directory we copied earlier.
```
$ sudo ln -s /lib/plymouth/themes/$new_theme_directory/$theme.plymouth /etc/alternatives/default.plymouth
```

- Finally, we'll need to create a new init image with the new settings.
```
$ sudo update-initramfs -u
```

- Now when you shutdown or reboot, you'll see the new Plymouth theme installed.  Your changes will also stay persistent through reboots.

---

