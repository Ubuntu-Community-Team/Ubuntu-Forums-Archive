---
title: "Pop_OS Dropbox"
date: 2021-04-03
forum: Ubuntu/Debian BASED
---

### Post by MadMonkey1966 on 2021-04-03
I have just installed Pop_OS on an old machine of mine after watching various Youtube vids on how good it is.
I have to say, it seems great so far except for one thing....installing Dropbox
I followed the instructions for Ubuntu as that seemed logical.

sudo apt-get update
sudo apt-get install wget
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
~/.dropbox-dist/dropboxd

It then opened a browser for me to login in. All my files were synced etc....and all looked ok except the terminal was stuck doing nothing.
I tried to close it, but it warned me the app was still running.
Left it for 2 hours, no change, so i closed it, re-booted machine, and now the dropbox icon has gone.

I tried running:

~/.dropbox-dist/dropboxd

again, but it just does a few lines of stuff, then nothing (except the dropbox icon re-appears)

At a loss, any help would be greatly appreciated.
Thanks

---

### Post by CelticWarrior on 2021-04-03
Once installed you can run it like any other app, searching for an clicking in the icon.
Then adjust settings and whatnot.

BTW, it's already in the repositories, no need for the method you used.

---

