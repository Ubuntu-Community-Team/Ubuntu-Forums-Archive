---
title: "Multi disk install in wine?"
date: 2009-05-05
forum: Wine
---

### Post by Gothamite on 2009-05-05
Hello, I have several games that have more than one disk, the problem is that while installing it asks me to insert the next CD, but I can't since it won't even let me open the CD drive, so obviously I can't complete the installation.

Any help on how to do this would be great :) thanks.

---

### Post by VinisLentoje on 2009-05-05
I had the same issue.

Try launching nautilus, right-click on the disk You want to eject and hit "unmount" or "eject" (I cant' tell exactly, since I don't use an English version of Ubuntu)

Or try finding the icon of that disk on Your desktop, assuming it is there, and do the same: right-click > unmount or eject

It should open the drive, or at least should let to open it. 

Hope this helps

---

### Post by Gothamite on 2009-05-05
Thanks very much for your reply, but how do you launch Nautilus, I'm a noob with ubuntu.

Thanks again

---

### Post by cogadh on 2009-05-05
Don't do it in Nautilus, use Wine to do it, otherwise you can break the install. Open a terminal and type "wine eject -a" and it will eject the disk without interrupting the install.

---

### Post by del_diablo on 2009-05-05
Or you could do it the easy way:

```
sudo mkdir /media/CD1 && sudo mkdir /media/CD2 && sudo mkdir /media/CD3
```

Creating the mounting points

```
sudo mount o -loop /file/path.iso /media/ /media/CD1 && sudo mount o -loop /file/path.iso /media/ /media/CD2 && sudo mount o -loop /file/path.iso /media/ /media/CD3
```

Mounting the .iso stuff

There is GUIs on this too, like gmountiso if you don't like to work in the command line.

For making .ISO files out of your CD and DVD there is always the DD command.
```
dd if=/dev/cdrom of=/where/you/want/it.iso
```
Sadly i don't remember how to list up list where you physical reader is <.< just the listed one might be correct also.
Guy for this? There should already be an installed one, i don't bother to look it up.

If you already got .iso files then enjoy :P

---

### Post by cogadh on 2009-05-05
Creating images from your disks then manually creating mount points and mounting each image individually is the easy way? Sorry, but typing one three word command in a terminal seems much easier to me.

---

### Post by Ninja duck on 2010-06-12
Another solution would be to configure wine (if you use PlayOnLinux this can be done by saying "yes" when it asks if you want to configure your prefix first, if not go to Applications/Wine/Configure Wine and add the setup.exe to the list of programs)

When you're in wine-config for the setup.exe file, go to the drives tab. Add a new drive for each disc, starting with /media/cdrom

When you're done you should have 3 wine drives, something like this:

E: /media/cdrom
F: /media/cdrom0
G: /media/cdrom1

(or more drives if needed)

When you install, mount each cd to the three different cdrom's and when installing the installer will recognize them when looking for the next disc.

I think i got a few names wrong, If anyone needs a screenshot i can provide one.

Edit: I added this because cogadh's solution didn't work for me

---

