---
title: "Howto: Kernel Compilation 2.6.27.x"
date: 2009-01-05
forum: Slackware and derivatives
---

### Post by Vince4Amy on 2009-01-05
[FONT="Arial Black"][SIZE="6"]Due To The Closure Of Other OS Talk, This Guide Is No Longer Maintained. For An Up To Date Version [Click Here](http://grubbn.org/otheros/showthread.php?tid=51)[/SIZE][/FONT]

I've made this guide to give a bit of information on compiling a custom kernel for Slackware. This is just something to get you started in compiling a kernel and removing options. Please make sure that before you remove things from the kernel you know what hardware is in your system and what things you can and cannot remove.

**All Stages will require that you are logged in as root.**

**Which Kernel Version**

You can either install the kernel sources package when you install Slackware (On 12.2 it is 2.6.27.7) or you can download the latest version (At the time of writing 2.6.27.10)

To download the latest version of the kernel please do the following:

```
cd /usr/src && wget http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.10.tar.bz2
``` (When a new version is released you can change  the .10 for .11 or whatever version at the  time.

Once the file has downloaded enter the following command:

```
bunzip linux-2.6.27.10.tar.bz2 && tar xvf linux-2.6.27.10.tar
``` - This will extract the kernel. Make a link to this at usr/src/linux by using the following:

```
ln -s linux-2.6.27.10 /usr/src/linux
```

*If you installed the kernel source package and  you are using the latest version from kernel.org you will have to remove the link to the old kernel source:*

```
rm /usr/src/linux
```

You are now ready to compile the kernel.

-----------------------------------------------------------------

You should already have a working Slackware system running with a kernel which has a variety of hardware support out of the box. 

The easiest way to compile your own kernel is to start by using what already worked with Slackware and building up and removing modules from there. To copy the current config file of the version of Slackware you are running you can run this command:

```
zcat /proc/config.gz > /usr/src/linux/.config
```

If you're using a newer version of the kernel you must run oldconfig because of added/removed features:

```
make oldconfig
```

Now you can begin compiling your own Kernel:

```
make menuconfig
``` - Select options using the command line.

```
make xconfig
``` - If you are using a working KDE you can use this to choose options with a GUI.

You will want to change the name of your kernel so that you know that you are running the latest version. Go to *General Setup>Change the release name*

You can then go through all the subcategories of menuconfig and disable/enable what you need. Once you have done this you can save the .config before you exit.

-----------------------------------------------------------------

To actually compile the kernel use:

```
make
```

Then to install the modules:

```
make modules_install
```

Set up booting:

```
cp arch/i386/boot/bzImage /boot/vmlinuz-custom
``` (Adding -custom so that it is easy to configure lilo.

Configure lilo:

```
nano /etc/lilo.conf
```

Add the following to the end of your lilo.conf file:

```

# Linux bootable partition config begins
image = vmlinuz-custom
label = linux-custom
root = /dev/(Whatever your primary hard drive is)
read-only
# Linux bootable partition config ends

```

To update lilo run:

```
lilo
```

Hopefully this will work for a basic kernel compilation. Please feel free to contribute any changes or error fixes you may find.

---

### Post by Bachstelze on 2009-01-05
For the sake of conciseness and simplicity, the first two steps can be done this way (I'm using [font="monospace"]sudo[/font] because old habits die hard, but feel free to do that while logged in as root instead, if you prefer):

After changing to a directory of your choice :

```
wget http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.10.tar.bz2
sudo tar xjf linux-2.6.27.10.tar.bz2 -C /usr/src
```

Also, in case [font="monospace"]/usr/src/linux[/font] is already there, a new symlink to another version of the kernel can be created in one step :

```
sudo ln -snf linux-2.6.27.10 linux
```

Another **very important step**, especially now that the version of the kernel has changed, is to run [font="monospace"]make oldconfig[/font] after copying over the config of your current kernel, so that any options that have been added/removed in the kernel will also be added/removed in your configuration.

---

### Post by Vince4Amy on 2009-01-05
> Another very important step, especially now that the version of the kernel has changed, is to run make oldconfig after copying over the config of your current kernel, so that any options that have been added/removed in the kernel will also be added/removed in your configuration.

Yes you're right, I forgot to include that one. I've added it. I'm using su in this guide and not sudo because I don't like sudo and it's not used by default on Slackware.

---

### Post by RedSquirrel on 2009-01-05
> **Vince4Amy said:**
> 
Set up booting:

```
cp arch/i386/bzImage /boot/vmlinuz-custom
```

Should be:

```
cp arch/i386[COLOR=Blue]**/boot**[/COLOR]/bzImage /boot/vmlinuz-custom
```;)

---

### Post by Vince4Amy on 2009-01-05
Yes you're right, I was typing this at school without access to Slackware at the time so I was working from memory.

---

### Post by Vince4Amy on 2009-01-30
Has anyone tried 2.6.28 on Slackware yet?

---

### Post by RedSquirrel on 2009-01-30
> **Vince4Amy said:**
> Has anyone tried 2.6.28 on Slackware yet?
I did, right after 2.6.28 came out. A couple of days later, I switched back to Gentoo. I use the vanilla kernel sources on Gentoo as well, currently 2.6.28.2.

---

### Post by yabbadabbadont on 2009-01-30
> **RedSquirrel said:**
> I did, right after 2.6.28 came out. A couple of days later, I switched back to Gentoo. I use the vanilla kernel sources on Gentoo as well, currently 2.6.28.2.

Interesting.  Any big differences from gentoo-sources?

---

### Post by RedSquirrel on 2009-01-30
> **yabbadabbadont said:**
> Interesting.  Any big differences from gentoo-sources?
Nothing that I've noticed, but then I haven't used gentoo-sources for a while (months, I guess), so it's difficult for me to compare them.

Someday when I'm bored, I'll have to look through the patches the Gentoo devs apply to the kernel sources. I know they add a little functionality and address some bugs, but I don't know much about the specifics.

---

### Post by yabbadabbadont on 2009-01-30
> **RedSquirrel said:**
> Nothing that I've noticed, but then I haven't used gentoo-sources for a while (months, I guess), so it's difficult for me to compare them.

Someday when I'm bored, I'll have to look through the patches the Gentoo devs apply to the kernel sources. I know they add a little functionality and address some bugs, but I don't know much about the specifics.

I should probably install the latest vanilla-sources and see if the shutdown issue with libata and sata_promise have been fixed.  I would have to have them installed anyway if I were to try to file a bug upstream.  Currently I just reboot and use the halt command in grub.  It's a pain to go through all the hoops required to file a kernel bug that will be accepted.  :)

---

