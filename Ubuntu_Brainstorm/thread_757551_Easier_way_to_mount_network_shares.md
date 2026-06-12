---
title: "Easier way to mount network shares"
date: 2008-04-17
forum: Ubuntu Brainstorm
---

### Post by ionospheric on 2008-04-17
I dual-boot Windows and Ubuntu 7.10, and I have an NAS (network attached storage, basically a file server) on my network.

When I want to mount a share on the NAS under Windows, I can simply browse to that share, then right-click and use "Map Network Drive", and I have a network drive, for example Z:

Trying to do the same with Ubuntu turned out to be a major task, it took me weeks to figure it out.

First, I tried browsing to the share with the Go->Network command in Nautilus.I can find the share, but that doesn't help me if I want to use the "Save As" dialog in OpenOffice because the share with the prefix SMB: is not a valid volume. It would be nice if you could just right-click on the share and have something similar to the "Map Network Drive" command in Windows.

Next, I added an smbfs share entry to /etc/fstab and mounted the share manually, but this turned out to be unstable, with the computer freezing, and I have read many postings of other people reporting the same problem.
(I believe that I had to install smbfs with Synaptic, but I don't remember.)

Then I used the cifs option to mount the share. The entry in /etc/fstab is
```
//192.168.0.1/myshare    /mnt/myshare     cifs uid=1000,umask=000,nogroup,rw,credentials=/root/credentials/myshare,iocharset=utf8 0 0
```
This requires creating a folder /mnt/myshare and the credentials file, and a fixed IP for the NAS.

CIFS turned out to be stable, but I ran into permission problems. My uid on the Ubuntu system is 1000, and if the uid of the share is not 1000, I can't do anything on that share. The same thing happens with peer-to-peer networking, so it's not just the NAS.

After weeks of talking to the NAS manufacturer, we figured out the solution: Disable Linux extensions!

What you have to do is to issue the command
```
>echo 0 >  /proc/fs/cifs/LinuxExtensionsEnabled
```

but even that doesn't work right away!
On my system, the /proc/fs/cifs didn't exist, so I had to first mount something with cifs, then unmount, then disable the Linux extensions, then mount the share again.

At this point, everything works with the share the way it should.

However, as a final stumbling block, if you forget to manually unmount the cifs share, the system hangs when you shut down, giving this message:

```
CIFS VFS: Server not responding
CIFS VFS: no response for cmd 50 mid 30
```

How is a non-expert supposed to figure all of this out?#-o

I was really impressed with the control center in PCLinuxOS (Mandriva has the same, PCLinuxOS is derived from it).
The control center has a mount-point feature that does all the fstab work for you, at least for smbfs (not cifs and not the disabling Linux extensions).  I believe PCLinuxOS also unmounted the cifs share automatically at shutdown.

If Ubuntu had a GUI for creating mount points, it would make things a lot easier. Or add a "Map Network Share" option to the network browsing. And automatically unmount cifs shares at shutdown.

---

### Post by kaens on 2008-04-17
I use kubuntu, and konquorer tends to detect and handle samba shares perfectly fine. On the other hand, every time I've set up samba shares by hand, it's been a royal pain.

---

### Post by AdamWill on 2008-04-17
kaens: that's fine, but it's not enough for everyone. If you access the share via KDE or GNOME's VFS systems, you can only access it through KDE / GNOME applications (that support the VFS system in use, too). I always mount my network shares properly so they're available to *all* applications - I can manipulate them at a console, use them in some ancient application like nedit, or whatever. It is genuinely useful in some situations.

---

### Post by ionospheric on 2008-04-17
> **kaens said:**
> I use kubuntu, and konquorer tends to detect and handle samba shares perfectly fine. On the other hand, every time I've set up samba shares by hand, it's been a royal pain.

kaens,

when you start openoffice or kedit or any other editor and go to the File->Save As menu, are you able to navigate to the samba share that konqueror detects? Can you save the file on that share?
Also, can you open a terminal and issue the ls command on a folder in that share?

---

### Post by kaens on 2008-04-17
> **AdamWill said:**
> kaens: that's fine, but it's not enough for everyone. If you access the share via KDE or GNOME's VFS systems, you can only access it through KDE / GNOME applications (that support the VFS system in use, too). I always mount my network shares properly so they're available to *all* applications - I can manipulate them at a console, use them in some ancient application like nedit, or whatever. It is genuinely useful in some situations.

Yes, that's very true - it's not nearly enough for everyone. I was just commenting on my experience, which was one of getting really frustrated getting samba shares to work flawlessly.

[quote=ionospheric]when you start openoffice or kedit or any other editor and go to the File->Save As menu, are you able to navigate to the samba share that konqueror detects? Can you save the file on that share?
Also, can you open a terminal and issue the ls command on a folder in that share?[/quote]

It's been a while since I've actually used a samba share (I don't have any computers that aren't running linux, and use a fileserver setup in combination with ssh and sftp that meets my needs very well), but if I remember correctly you can save files on shares and so on, but if you're wanting to interact with the share from the terminal, it's worth it to actually set up samba correctly.

---

### Post by jwilentz on 2008-11-09
The entire Samba setup is so kludgy it's unbelievable!  Here are just a few of the problems I've encountered (other than the incredible saga of getting the thing installed and working in the first place).

1. Wireless -- I initially tried to run the fusesmb script in a startup mode (after a lot of research) but there was no way to have fusesmb wait until the wireless network was loaded and authenticated (got to type in that keyring password even though you've already signed on to your account -- oh I forgot, the national security is at stake here,  it's LINUX after all).  So I gave up on that and created a fusesmb script that can be run from an icon on the toolbar.  That works fine, but . . .

2. Polling the network for available shares -- doesn't happen, and I haven't been able to figure out how to do it.  On a Windows network, as available shares join the network, net neighborhood can see them and enabled programs can use them.  As these shares log off they are no longer seen or usable.  Why can't (or if I have missed it how can) Samba do the same?

I've looked for ways around these problems but have not found them, and I'm not a newb to computing but a bit newb to LINUX, so I would love a hand from those who may have solved this, but I expect many are in this boat.  It would be great for those of us who use Xubuntu as a way of (green) continuing to utilize older machines to be able to have a robust network interface.

Cheers,

Jim

---

### Post by Austin_Duffy on 2008-11-09
yes

---

