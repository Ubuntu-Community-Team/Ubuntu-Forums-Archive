---
title: "Reload this Page Accidentally damaged my freshly installed Ubuntu desktop: remove Ubu"
date: 2014-09-04
forum: Ubuntu Studio
---

### Post by Cocolate on 2014-09-04
ok, Iv reinstalled my whole OS today, took me 5 hrs to back up, reinstall, unpack the backups, install all my programs, remake my playlists, etcetcetc

I then installed this

[http://www.javacodegeeks.com/2014/02/5-most-awesome-desktop-environments-for-ubuntu.html](http://www.javacodegeeks.com/2014/02/5-most-awesome-desktop-environments-for-ubuntu.html)

That what I did was add UbuntuStudio-Desktop flavor to my computer, but my system is now faulty.

Getting error, etc, when I restart, volume control is not displaying correctly, and  there is a BIG RED circle at the top with a white line across the middle.

```

An error occured, please run Package Manager from the right-click menu or apt-get in the terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0'. This usually means that your installed packages have unmet dependencies
```

Ugh, is there ANYWAY, I can fix this without having to reinstall my whole OS again?

Im running Ubuntu 13.10. I believe the link I used was for UbuntuStudio 14.04.

My MoBo is UEFI no secure boot, so I am forced to use Ubuntu 13.10 as of now. Making GPT is too advanced for me I have to do it manually.

This is the best info Ive found to remove UbuntuStudio

[http://askubuntu.com/questions/186425/how-do-i-uninstall-the-ubuntu-studio-desktop-package](http://askubuntu.com/questions/186425/how-do-i-uninstall-the-ubuntu-studio-desktop-package)

But it did not work for me. It tells me it is not installed but as soon as I installed many of the packages there was an error, and now my computer is getting errors as the one I posted above says.

...

When I post "apt-get" there is literally no useful information, and I do not see Package Manager right-clicking the desktop.

Please please please can anyone save me from another marathon reinstalling EVERYTHING that Ive just installed please?

---

### Post by Bjelleklang on 2014-09-04
Take a look in /var/log/apt/history.log. It shows everything you've installed via apt lately, that might help you figure out what to remove. I'm also guessing that you have to reinstall some ubuntu packages to get the default settings back.

---

### Post by jejeman on 2014-09-05
> Im running Ubuntu 13.10. 
13.10 is dead.
Why didn't you installed 14.04 anyway?

---

### Post by christopher9 on 2014-09-05
14.04 should install on your current hardware...secure boot is not necessary...and you might want to make sure you have a stable install with the recommended updates before trying customization with third-party gizmos...

---

