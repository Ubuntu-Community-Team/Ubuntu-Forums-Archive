---
title: "Trouble uninstalling vent from Wine"
date: 2010-06-14
forum: Wine
---

### Post by es305 on 2010-06-14
I tried using vent but for some reason which I think I've now figured out using mangler my Mic wouldn't get picked up through ventrilo. In any event I installed mangler got it to work and am now wanting to uninstall vent but am unable to, when I got to Applications>Wine>Uninstall Wine Software it still shows me the 32 and 64 bit versions both of which I installed I go through the removal process and nothing happens they remain on the list even after reboot and a ventrilo folder keeps reappearing in the c:drive file browser. sorry for the punctuation and grammer if it isn't worded too well. Thanks in advanced.

-eS

---

### Post by asdfoo on 2010-06-14
Uninstalling has been a low priority area for Wine developers since getting things installed and running is much more interesting to users.

If you really want to remove a program, you can delete your wine prefix which contains *ALL* your data for programs installed under Wine, then reinstall anything you do want.

---

### Post by cogadh on 2010-06-14
Have you tried using the uninstaller that comes with Vent? When Wine's uninstaller doesn't work, sometimes the "regular" uninstaller will work.

---

### Post by es305 on 2010-06-14
I've tried doing what both of you have suggested and I still have pokerstars and vent any other options perhaps? I also tried removing wine from the terminal    using sudo aptitude purge remove wine and they're both still there.

---

### Post by cogadh on 2010-06-14
Are you talking abut the Applications menu shortcuts? If so, thats all they are, leftover shortcuts; the application itself is not actually installed anymore. You can get rid of them using the menu editor.

---

### Post by es305 on 2010-06-15
I did what both of you told me. The folder is still there when I browse c: drive even after going into the folder deleting it and rebooting it just reappears, any ideas how to remove this through the terminal maybe?

---

### Post by es305 on 2010-06-15
> **asdfoo said:**
> Uninstalling has been a low priority area for Wine developers since getting things installed and running is much more interesting to users.

If you really want to remove a program, you can delete your wine prefix which contains *ALL* your data for programs installed under Wine, then reinstall anything you do want.

Ah sorry I just realized I didn't fully understand this what I did was just uninstall wine through synap pack manager and that really didn't do the trick. how would I delete my wineprefix containing all of this data?

---

### Post by cogadh on 2010-06-15
Just delete the .wine directory in your home directory. Its a hidden directory, so you will need to hit CTRL+H to see it in the file browser.

---

### Post by es305 on 2010-06-17
Thanks for both of your input and help. I ended up caving in and splitting my partition giving windows a small portion of my drive to run the few programs I was going to end up using with Wine. :tongue:

---

