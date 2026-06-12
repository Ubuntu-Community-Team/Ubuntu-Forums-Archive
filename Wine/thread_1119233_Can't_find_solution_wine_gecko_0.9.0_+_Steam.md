---
title: "Can't find solution: wine gecko 0.9.0 + Steam"
date: 2009-04-07
forum: Wine
---

### Post by tpearson1 on 2009-04-07
I downloaded **SteamInstall.msi** from steampowered.com. After it was downloaded steam automatically began to run it's set-up. I went through the process (as i had multiple times on windows) and everything was going fine until the Updating Steam window came up and did ABSOLUTELY NOTHING. I left it there for a good 30 minutes before this error occurred:

**"Steam.exe (main exception): Unable to load library Steam.dll"**

I've also tried using the synaptic package manager to install Wine+**Wine gecko 0.9.0**. The problem with that was Gecko didn't want to install.

Also I've tried downloading **SteamInstall.exe** from various sites.

All have failed me and I just want to play CSS, TF2, and HL2.

Thanks for the help!

---

### Post by tpearson1 on 2009-04-08
No one can help me out? honestly? c'mon.

---

### Post by mrm48 on 2009-04-08
I did a fresh install of wine and steam today and it worked fine for me.

I installed wine by running:
```
sudo apt-get install wine
```

Instead of using steaminstall.msi, I searched google for steaminstall.exe and that worked without a hitch.

If that doesn't work, let me know.

---

### Post by asdfoo on 2009-04-08
> **tpearson1 said:**
> I downloaded **SteamInstall.msi** from steampowered.com. After it was downloaded steam automatically began to run it's set-up. I went through the process (as i had multiple times on windows) and everything was going fine until the Updating Steam window came up and did ABSOLUTELY NOTHING. I left it there for a good 30 minutes before this error occurred:

**"Steam.exe (main exception): Unable to load library Steam.dll"**

I've also tried using the synaptic package manager to install Wine+**Wine gecko 0.9.0**. The problem with that was Gecko didn't want to install.

Also I've tried downloading **SteamInstall.exe** from various sites.

All have failed me and I just want to play CSS, TF2, and HL2.

Thanks for the help!

You haven't specified which version of Wine you are using... for me it works fine with 1.1.18.

---

### Post by tpearson1 on 2009-04-08
I just updated from 1.0.1 to 1.1.18. 

I downloaded **SteamInstall.exe** and commenced to install. Then it froze up while installing with 0 seconds to go. I've attached a screen shot of the mess up.

I don't understand what's going on.

---

### Post by tpearson1 on 2009-04-08
also after clicking the Steam logo on my desktop... after about 20 minutes I had forgotten I had even clicked it... then this popped up. 

I hope this helps with your diagnosis

---

### Post by asdfoo on 2009-04-08
> **tpearson1 said:**
> also after clicking the Steam logo on my desktop... after about 20 minutes I had forgotten I had even clicked it... then this popped up. 

I hope this helps with your diagnosis


weird... are you out of disk space maybe?

I'd try installing under a clean wine prefix by moving or removing the old one.

mv ~/.wine ~/.wine-old

Then run msiexec /i steaminstall.msi

---

### Post by tpearson1 on 2009-04-08
I still have at least 120 gigs of disk space available. 

What do I do after I run those commands? Try installing the .msi again?

**EDIT** I tried installing the .msi through the command you listed. Still getting nothing. This is the window that doesn't show any activity of updating after installing the .msi...

**EDITx2** Along with the steam logo on my desktop a file appears titled "Steam.ink"? what is it?

---

### Post by asdfoo on 2009-04-09
strange... which version of Ubuntu are you using?

it's not an ink file, it's a lnk (windows shortcut)

---

### Post by NightMKoder on 2009-04-09
I suggest reading the Troubleshooting/howto @ [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554) .

Also, start with a fresh wine prefix:
```

mv ~/.wine ~/.wine_old
wine msiexec /i SteamInstall.msi

```

and also post output from the terminal (change the path to wherever steam.exe is)
```

cd "~/.wine/drive_c/Program Files/Steam/"
wine Steam.exe

```

---

### Post by tpearson1 on 2009-04-09
Unfortunately that didn't work either. I'm running Ubuntu 8.10... I've even tried installing it through playonlinux but with no avail. In after installing it on playonlinux when the steam update window comes up I couldn't exit out of it, then eventually it said it couldn't find the .dll library files. This is a tad bit frustrating.

---

### Post by tpearson1 on 2009-04-09
could this be some problem resulting from me installing Ubuntu 8.10 via usb drive?

---

### Post by sir_charles804 on 2011-03-08
I dont think that could have anything to do with it. I am having similar problems installing steam but I have had a good install of it before, and I am trying to return to that.

---

