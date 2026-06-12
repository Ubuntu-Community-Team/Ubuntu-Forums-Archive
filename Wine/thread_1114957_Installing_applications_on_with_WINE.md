---
title: "Installing applications on with WINE"
date: 2009-04-03
forum: Wine
---

### Post by dE_logics on 2009-04-03
Can you install fully fledged applications (I mean proper setups) with WINE?...or MSI packages.

If yes can I install it on a non Microsoft file system?

---

### Post by cogadh on 2009-04-03
That is the whole purpose of Wine, so yes. File system type doesn't matter, everything the application "sees" is translated by Wine into "Windows lanuguage" so that app isn't even aware of what kind of file system it is running on.

---

### Post by dE_logics on 2009-04-03
Thanks player.


But where does the registry modifications and files that were originally meant to be sent to appdata folder etc... go?

Are they installed within that installed place which I designated while installing through WINE?

---

### Post by cogadh on 2009-04-03
When you first run Wine, it creates a "fake Windows" directory within your home directory. Inside that directory is a replicated version of the normal Windows file structure (Program Files directory, Windows directory, etc.) as well as Wine's version of the Windows registry. Anything you install with Wine is installed in this directory and all registry entries are written to the Wine registry. You can specify other locations to install things, but it is usually best to just use Wine's defaults.

---

### Post by dE_logics on 2009-04-04
Humm...thanks!

---

### Post by jhoeijao on 2009-05-30
If you want to install MS Office 2007 give this a try [http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft](http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft). Enjoy!

---

