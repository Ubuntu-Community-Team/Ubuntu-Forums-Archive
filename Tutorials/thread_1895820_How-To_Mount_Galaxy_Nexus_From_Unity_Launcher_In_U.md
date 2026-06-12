---
title: "How-To: Mount Galaxy Nexus From Unity Launcher In Ubuntu 11.10 (New Guide)"
date: 2011-12-15
forum: Tutorials
---

### Post by nyteryder79 on 2011-12-15
I just got my Galaxy Nexus from Verizon and tackled this right away.  There was a post on [[COLOR="Purple"]**OMG! Ubuntu!**[/COLOR]]("http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access/") providing a rather lengthy guide on connecting your Galaxy Nexus to Ubuntu.  And when it's all said and done, you still have to type commands in terminal to mount the device.  I thought that there must be an easier way, and sure enough, there is.

Now, I'm no expert, but after getting this to work my way, I have no idea why there were so many steps in the post on omgubuntu's blog.  My method doesn't require nearly as many steps, and the best part, I have it all ready for you.

The install script included installs 2 scripts, one for mounting and one for unmounting the device, an icon to the /usr/share/pixmaps directory, and a launcher to the ~/.local/share/applications directory.  It then opens up Nautilus, showing you the new launcher with the Galaxy Nexus icon.  All you have to do is drag that puppy into your Unity launcher.  [COLOR="Blue"](You may need to restart before this works properly.  I didn't, but others reported that the MTPFS package needed a reboot.)[/COLOR]

To use it, connect your galaxy nexus, switch USB mode to MTP.  Then right-click your new icon in the Unity launcher and mount it.  To unmount, right-click the icon and unmount it.  Simple.

[**[COLOR="purple"]THIS PACKAGE[/COLOR]**]("http://dl.dropbox.com/u/25218780/mount_gnex.tar.bz2") provides everything you'll need, includes install and remove scripts as well as the icon for your Unity launcher and the launcher itself.

This is what you'll see when it's set up:
[IMG]http://i.imgur.com/ENGWt.png[/IMG]

And after getting my Galaxy Nexus, testing everything and doing some minor tweaks from the guide I posted yesterday, it's working properly for me.

Let me know if you experience any issues.

---

