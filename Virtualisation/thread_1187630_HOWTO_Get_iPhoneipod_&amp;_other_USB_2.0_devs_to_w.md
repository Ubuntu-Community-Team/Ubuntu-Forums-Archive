---
title: "HOWTO: Get iPhone/ipod &amp; other USB 2.0 devs to work with VirtualBox under Ubuntu"
date: 2009-06-14
forum: Virtualisation
---

### Post by jerone on 2009-06-14
Figured I would write this up as it has been a major pain for myself for a long time. I love open source and all. But I'm addicted to ipod/iphone like a crack addict. So I have for sometime been wanted to let go of the windows box in favor of doing everything in a virtual environment. I have finally gotten what I want. Here is how to get things going with Virtual Box.

1) Install latest proprietary Virtual Box (2.2.4 or greater)
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

2) Once installed ensure that your user is in group "vboxusers"

3) Turn off Nautilus Automount for user
As the user, run comman "gconf-editor"
apps->nautilus->prefrences
Uncheck box labeled "media_automount"

4) Disable gvfs-gphoto2-volume-monitor
* I don't know a better way to do this
Run " sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor"


So what your doing is disabling the automounting in Nautilus. So when you plug in a USB stick you will have to go into Nautilus and click on it for it to mount. Also the "gvfs-gphoto2-volume-monitor" is basically the auto mounter for cameras. The problem is if these apps are running then they will try to take control of the ipod/iphone and Virtualbox will fail to get the USB device correctly. The guest OS will see it as a problem with the device.


Now if you want your device to mount everytime your running your VirtualBox instance. You want to go into the setting for the Virtual machine and under "USB" you will see "USB Device Filters". Plug in your ipod/iphone and add it to the filter. Otherwise if you don't you can just choose it from the list of USB device to connect while the Virutal Machine is running.

* You will want to have your iphone added to the filter list if you are doing firmware updates to your iphone, as it will connect and disconnect often during the process.

I can say that I am now running my Windows XP virutal machine with Itunes 8.2 under Ubuntu Juanty 9.04 64-bit. It works great with my Iphone 3G, Ipod Gen 4, Ipod Nano Gen 2,& Apple TV. I told you I'm an addict.

If anyone knows a better way to disable gvfs-gphoto2-volume-monitor please tell.

---

### Post by PaganImmolator on 2009-06-15
I think this method works in ideal situations. I know from experience that syncing an Itouch and Iphone can be frustrating. 

For example my Iphone syncs just fine, albeit slowly, on VirtualBox running a XP guest. I am not doing anything that you suggested. I simply unmount the iphone before I launch VB and Itunes. 

My wifes Iphone and Itouch WILL NOT syncing right. They often hang during the syncing process.  A typical sync (if it works) takes 30-45 minutes. This is on a fast computer. 

Things I notice:
The amount of data per device seems to matter. Her Iphone syncs faster than her touch. Her Itouch is 32gigs while her Iphone is only 8. 

CPU overhead is extremely high. 100% or close to it during the sync process.  

If I momentarily bump the priority under XP of itunes.exe when it hangs, it often will make the sync process continue and things will finish just fine. 

I think the amount of apple encoded AAC files matters too. Her music is almost exclusively bought off Itunes. Mine is the opposite and almost all MP3 format. 

Your instructions are good and but I think that simply unmounting the device when it pops up will do pretty much the same effect

---

