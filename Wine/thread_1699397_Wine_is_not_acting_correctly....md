---
title: "Wine is not acting correctly..."
date: 2011-03-03
forum: Wine
---

### Post by projectbronco on 2011-03-03
I go to open up a program in wine and the attached image will pop up. Though only the first time.
I will then close it and in about three minutes the program will open. If I try to click on the program again, as many times as I click, the program will open in the interval of about three minutes apart.

It doesn't matter what program I am trying to open, it does it with every one.

I have Ubuntu 10.04 and Wine 1.2.2.

Any help would be greatly appreciated!

Thank you!

---

### Post by cogadh on 2011-03-04
Is it the same executable named in the error every time? If so, I would have to guess that you installed something that uses that sql manager as a service, so that every time you launch something in Wine, it tries to launch the service first. Your best solution would be to uninstall whatever it was that added that service or create a separate Wine prefix for it alone so that it doesn't interfere with anything else you might install.

---

### Post by projectbronco on 2011-03-10
Wow, sorry it took so long for me to reply, and thank you for answering!
Yes it is the same executable name every time that I have noticed, the w3dbsmgr.exe.
Is there a way to find out if something is conflicting? Like a command to put in a terminal or something?
It still takes about 3 minutes to open any program.

Sudo help? lol

---

### Post by cogadh on 2011-03-10
I don't think you understood what I was saying. Something you installed in Wine included that particular service. If it was installed on Windows, that service would run automatically at login and continue to run constantly. Since Wine doesn't run constantly but does try to replicate the working environment of Windows applications, that service will automatically start every time you launch something with Wine that is also installed in the same Wine prefix as the service. I don't think there is really any way to figure out what needs that service, since you haven't told us what you have installed in Wine.

Your best solution for the problem is to create a new Wine prefix that only has whatever application that uses that service installed, then use a different Wine prefix for your other apps that don't need that service. I actually have about a half dozen different Wine prefixes for different software, since some require specific configurations or additional file overrides that others do not. The default .wine prefix is just used for testing installs and configuring Wine for a particular app. Once an app is configured and working, I re-name the default prefix to something specific, then create a new default prefix for the next batch of testing.

To create a new Wine prefix, just run this:
```
WINEPREFIX=$PATH_TO_NEW_WINEPREFIX wineboot 
```
Obviously replace that "$PATH_TO_NEW_WINEPREFIX" with the actual directory path and name you want for your new prefix.

---

### Post by projectbronco on 2011-04-14
OK, I think I get what you are saying. I'll have to look into it a little more when I get some time. If you noticed, I haven't been here in 4 weeks, I have been a little swamped.
Thank you very much for the help though.

---

