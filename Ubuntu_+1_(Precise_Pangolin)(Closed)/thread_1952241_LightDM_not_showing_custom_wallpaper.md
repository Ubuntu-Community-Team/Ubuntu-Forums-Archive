---
title: "LightDM not showing custom wallpaper"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by residualbit on 2012-04-03
I am using a custom desktop wallpaper. LightDM/login screen shows the default wallpaper.

If I use one of the built in wallpapers, LightDM correctly displays them as well, just not custom ones.

In 11.10 it was a matter of just editing 

```
/etc/lightdm/unity-greeter.conf
```

I have also checked

```
/var/lib/AccountsService/users/myusername
```

Both files correctly show the path to my custom background image. I even moved it to the default /usr/share/backgrounds directory, but that didn't make a difference.

Any ideas?

---

### Post by kaldor on 2012-04-04
Confirmed here. It works sometimes, but 99% of the time not.

---

### Post by mc4man on 2012-04-04
If you added to /usr/share/backgrounds then did you also add a new entry  to /usr/share/gnome-background-properties/ubuntu-wallpapers.xml using same format as others?

Otherwise, if custom image is elsewhere, (in $HOME) you may want to check the permissions
The folder it's in should be  drwxr-xr-x
The file should be  -rw-r--r--

---

### Post by Hylas de Niall on 2012-04-04
Greeter all works fine for me. My wallpaper is just in the 'pictures' folder too.

edit: my wp is the right size and doesn't need automatically scaling to screen size. Might scaling to size on-the-fly be an issue for the greeter I wonder?

---

### Post by ratcheer on 2012-04-04
A week or so ago, my system displayed my wallpaper selection for the lightdm login screen, but now it just shows the Ubuntu default. And my wallpaper is one of the standard Ubuntu choices.

Tim

---

### Post by odysseusjak on 2012-04-04
After playing with this, I found that the image has to be in the "Pictures" folder and not in a sub folder. I have a "Wallpapers" folder within my "Pictures" folder. If i selected an image in the "Wallpapers" folder, it would not show up on log in. If I copied or moved it to the root "Picture" folder, then it appeared.

---

### Post by ubuntu27 on 2012-04-05
Is it related to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/970634")?

---

### Post by ratcheer on 2012-04-05
I changed wallpapers yesterday, and now my system is again (correctly) showing my wallpaper on the login screen (after a few seconds of the purple with white dots screen). My old wallpaper was one of the Ubuntu selections, my new one was downloaded from the internet and is stored in mt Pictures folder.

Weird.

Tim

---

### Post by residualbit on 2012-04-05
I added an entry to

```
/usr/share/gnome-background-properties/ubuntu-wallpapers.xml
```

pointing to my custom wallpaper in the /usr/share/backgrounds directory. LightDM now correctly shows it.

I cam to 12.04 by upgrading from 11.10, not sure if that had anything to do with this. When 12.04 is final, I am going to wipe and install it fresh. I'll let you all know if this is still a bug then.

---

### Post by ubuntu27 on 2012-04-06
> **odysseusjak said:**
> After playing with this, I found that the image has to be in the "Pictures" folder and not in a sub folder. I have a "Wallpapers" folder within my "Pictures" folder. If i selected an image in the "Wallpapers" folder, it would not show up on log in. If I copied or moved it to the root "Picture" folder, then it appeared.

Everyone please comment and add yourselves to the "Does this bug affect you?" if you have the same problem as odysseusjak.


[[COLOR="Red"][SIZE="3"]BUG#970634[/SIZE][/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/970634")


It is cool to have a workaround, but it is still very important to fix the underlining issue. :)

---

### Post by grahammechanical on 2012-04-06
Were we aware that in 12.04 the Image Viewer, Eye of Gnome Image Viewer has an option to "Make the current picture your desktop background?"

I think that it also can create a background slide show for you. It puts the Images in the Pictures folder along with the XML script that Gnome Control Centre reads when setting a background image.

You see, we learn these things when we run the Checkbox Application Tests.

[http://www.theorangenotebook.com/](http://www.theorangenotebook.com/)

Regards.

---

