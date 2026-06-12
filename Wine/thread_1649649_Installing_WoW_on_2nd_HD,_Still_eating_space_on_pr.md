---
title: "Installing WoW on 2nd HD, Still eating space on primary"
date: 2010-12-20
forum: Wine
---

### Post by torsoboy on 2010-12-20
Using wine 1.2
Ubuntu 10.04
most recent stable ATI driver
both HD's are IDE

So I set WoW to install on Z:/media/Storage/World of Warcraft which points to my second internal HD, but as I'm downloading the data, my primary HD fills up. My primary is now completely full, but WoW is still downloading like it doesn't even notice.

Now, WoW appears on the second HD as it should, along with 20+ GB of data.

I cant even FIND the data on my primary.

Any idea what's happening here? Any help is greatly appreciated, thanks.

Edit: specs

SOLVED: found the data at .wine/profiles/me/Local Settings/Temporary Internet Files/Content.IE5

---

### Post by torsoboy on 2010-12-20
OK- I should add that WoW is now fully updated and working fine with no errors, but I still have 20 GB of ghost data sitting on my HD

---

### Post by cwwilson721 on 2010-12-20
Seems to me you're still using the default wine install location, just added the additional drive.

Would have been better to have the new drive as it's own wine install, i.e:
```
env WINEPREFIX="<Wherever you want new install to be>" wine "C:\Program Files\World of Warcraft\Launcher.exe <Or wherever your WoW install is>" -opengl
```
And to to the preliminary work for setting up the new wine place:
```
env WINEPREFIX="<Wherever new install is>" winecfg
```

Note that it's not in '~/.wine' anymore, thus it is not going to add more files to your current main drive.

---

