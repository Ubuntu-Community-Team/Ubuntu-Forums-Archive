---
title: "Flash issue"
date: 2011-03-27
forum: System76 Support
---

### Post by smarmytime on 2011-03-27
A couple of days ago, my system (PanP7) let me know that there were some updates available, which I saw were mostly firefox updates. I rarely use firefox, but I thought it couldn't hurt to install the updated version, since I had heard that it was pretty nice. But ever since updating, flash doesn't work on either chromium or firefox. I typed about:plugins (<-- this should read about colon plugins) in chromium, and it wasn't even listed. I tried to install the latest version through software center, but it would start to install and then stop. 

Any suggestions? Does anybody know the file name I would have to use to install it directly from the command line?

---

### Post by mikewhatever on 2011-03-27
Try this:
```
sudo apt-get install flashplugin-installer
```

---

### Post by smarmytime on 2011-03-27
Hmmm...well this is odd:

```
roger@KarmaLaptop:~$ sudo apt-get install flashplugin-installer
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
roger@KarmaLaptop:~$ 

```

---

### Post by mikewhatever on 2011-03-27
You could also try reinstalling it:
```
sudo apt-get --reinstall install flashplugin-installer
```

I doubt a firefox update had something to do with it.

---

### Post by smarmytime on 2011-03-27
It does seem odd, but since Chromium stopped displaying flash immediately afterwards, and I did see that the update was installing flash for firefox, I think that it's more likely that it had something to do with it than it just spontaneously happened. Not saying that that means that it is the reason, just it's the very last thing I did before flash stopped working on my laptop.

Not quite sure what to make out of this.

```

roger@KarmaLaptop:~$ sudo apt-get --reinstall flashplugin-installer
E: Invalid operation flashplugin-installer
roger@KarmaLaptop:~$ 

```

---

### Post by isantop on 2011-03-28
I think you missed the install bit. For that, you need both "install" and "--reinstall".

---

### Post by smarmytime on 2011-03-28
Oh, right...I'll give that a try, thanks.

---

### Post by smarmytime on 2011-03-28
Success! Thank you both!

---

### Post by jalvarezv on 2012-03-31
I am having the same issue now with Firefox 11.0.  I tried the reinstall and that didn't work.  If I go to the plug-ins section of add-ons in firefox and check if my plugins are up to date, it says shockwave flash is outdated. I click to update, follow the instructions and it seems to go fine.  But when I open up firefox again, it still says the plug-in is outdated. Is there something else I can try?  I also have a panp7.

---

### Post by smarmytime on 2012-03-31
Is there actually any functional issue that you're running into on websites? Any information that isn't displaying, or anything like that? Or is it just firefox telling you this, and then it's not an issue?

---

### Post by jalvarezv on 2012-03-31
I can't see flash content.  In some cases the text "Adobe Flash Player" appears instead of the actual video, and in some cases nothing shows up, the screen is just blank.

---

### Post by haggus71 on 2012-03-31
If you install Chrome(NOT Chromium), there are no issues.  After Firefox froze my system, and Chromium wouldn't load flash(despite trying the multitude of techniques on this and other threads), it seems Google Chrome is the only one that was fine from the loading.  It's probably because all the updates and adjustments are done in the browser, without having to do the Linux gymnastics required with others.  This was fine back in 1995, when we had to compile our own drivers. Now, it's unacceptable.

And this ISN'T solved!

---

### Post by houseworkshy on 2012-03-31
May be worth taking a look at this

  [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

When uninstalling something broken with a view to re-installing it it can be a good idea to use "sudo apt-get purge" as this will clear settings.  Follow that with "sudo apt-get autoremove" to get rid of irrelevant stuff.  With firefox decide what to remove from the mozzilla folder ( maybe all of it ).  Also look at the .macromedia folder for the same reasons, its a hidden one so choose to make hidden files visable.  I had issues with other video apps which vanished when I followed the advise given in the thread pointed out above, apparantly this was irrelevant but it was one heck of a coincidence.  Flash does keep seem to keep doing strange things.  Good luck.

---

### Post by jalvarezv on 2012-03-31
I installed Chrome and the same issue occurs with it, so it seems like it's not a Firefox issue.  I tried the purge and autoremove with apt-get and it didn't work either.

---

### Post by jalvarezv on 2012-03-31
I finally found a fix.  I had Gnash SWF Viewer installed. I uninstalled it and now it seems like flash is working fine.  I don't know if there will be a time when I'll need the Shockwave flash for something and then I'll have to figure out what to do then.

Thanks for the suggestions though :-)

---

### Post by houseworkshy on 2012-04-01
Ah I should have asked if you had gnash installed, the two can conflict.  The lack of the player is not a problem though, just open whatever swf you need to play with firefox, if you have no-script  installed then you will have to allow the file and it will play fine.

---

### Post by jalvarezv on 2012-04-01
I did have both installed before it stopped working so I didn't think that was the problem. Maybe the newer version do have issues?

---

### Post by isantop on 2012-04-02
> **jalvarezv said:**
> I did have both installed before it stopped working so I didn't think that was the problem. Maybe the newer version do have issues?

Gnash is *known* to cause issues with flash, so if you have it installed, we recommend removing it.

EDIT: Also, be sure to use "apt-get purge" to remove gnash. This will remove it completely.

---

### Post by jalvarezv on 2012-04-03
Thanks.

---

