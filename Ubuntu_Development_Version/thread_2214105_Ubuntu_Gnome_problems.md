---
title: "Ubuntu Gnome problems"
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by drfox on 2014-03-30
I have been running Xubuntu for a long time, currently 14.04, and decided to try Gnome Shell.
I tried using the Beta2 installer to upgrade, and when I was finished, I was presented with choices to log into sessions of Default, Xubuntu, Xfce, Gnome and Gnome Classic. Oddly, logging into Gnome gave me a totally blank desktop, and the only way to get out was to hard reboot. Gnome Classic gave me the Gnome Shell. 
I decided to just try reinstalling without upgrading, so I wiped my / partition and kept /home and just did a fresh install. Now I am presented with Default, Gnome, and Gnome Classic. Gnome again gives me a blank desktop. Gnome Classic gives me shell. 
Is there a way to correct this behavior? Change some settings in Dconf editor? Can I safely delete some setting or hidden file in my /home directory and do a fresh install to fix it?
Thanks.

---

### Post by grahammechanical on 2014-03-30
In 14.04 what people call "Gnome classic" is actually a Gnome 3 shell extension. Its proper name is Gnome Shell Classic. It is part of the gnome-shell-extensions package. So, apart from the Gnome option giving you a blank screen the fact that Gnome Classic also gives you Gnome shell is exactly what we should expect.

By not formatting /home the re-install picked up the settings for Gnome shell. Try un-installing the Gnome Shell Extensions package and then Gnome Shell and then re-install.

Regards.

---

### Post by drfox on 2014-03-30
I tried uninstalling/purging shell extensions and shell; I then made the mistake of rebooting before reinstalling and could only log into Gnome, which gave me a blank screen. I reinstalled UbuntuGnome, and now I have the same options that I had before, but I can't do anything in plain Gnome. Is this "as designed" (aka a bug?); if so what is the purpose of "Gnome"? Is it supposed to look different than Gnome Classic/Shell?  
BTW, I also tried renaming .gconf and .conf, and that didn't seem to make a difference either.
I hate to do too much customization just in case I have to wipe and reinstall...any other suggestions to get the "Gnome" session either working or deleted?

---

### Post by kansasnoob on 2014-04-01
The standard GNOME session should look like this:

[ATTACH=CONFIG]251635[/ATTACH]

Then if you click on Activities like this:

[ATTACH=CONFIG]251636[/ATTACH]

And GNOME Classic should look like this:

[ATTACH=CONFIG]251637[/ATTACH]

Is that not what you see?

---

### Post by drfox on 2014-04-01
Thanks for the reply. 
My Gnome Classic desktop looks like your Gnome, and it has the same hot spot in the left upper corner which (even without clicking) opens the 2nd view.
My Gnome desktop now looks like a wallpaper with no menu, no hot corners, no way to interact with it.
I've gone back to XFCE/Xubuntu until I can figure out how to purge all of my Gnome settings and start all over again. Any idea how to do that?

---

### Post by kansasnoob on 2014-04-01
Since you have a mix of Ubuntu GNOME and Xubuntu I'd like you to see if there's any difference in booting with different display managers :)

Try these commands:

```
sudo dpkg-reconfigure gdm
```

```
sudo dpkg-reconfigure lightdm
```

Does it make any difference which display manager is used to boot the GNOME sessions?

---

### Post by drfox on 2014-04-02
Reconfiguring the login manager didn't make a difference. I have another laptop which seems to be working OK with both Xubuntu and the UbuntuGnome. I'm going to try copying the configuration settings from the working machine to the non-working machine to see what happens. I'll keep you posted.

---

