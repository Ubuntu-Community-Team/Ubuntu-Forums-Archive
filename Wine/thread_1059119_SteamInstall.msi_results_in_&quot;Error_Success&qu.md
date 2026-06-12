---
title: "SteamInstall.msi results in &quot;Error: Success&quot;"
date: 2009-02-03
forum: Wine
---

### Post by GoofusGreen on 2009-02-03
```
$ wine start SteamInstall.msi
fixme:exec:SHELL_execute flags ignored: 0x00000100
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: Success

```

Or by running outside terminal, I get the wine error dialog "Success" with the red circle next to it and a little OK under it.

lol, "Error: Success"

Wine 1.1.4 64-bit (iexplore doesn't work either)
Ubuntu 8.10

Also, when I try steaminstall.exe, Steam installs properly up to the point that it must update. Then it gets stuck at "Steam is looking for updates." and does nothing.

Same issue with the 1.0.1 stable version. (At least iexplore works)

-----------------------------------------------------------------------

Solved: use Gecko 0.9.0 and use "msiexec /i SteamInstall.msi"

Problem: Steam crashes/freezes when attempting to install games.

---

### Post by elitenoobboy on 2009-11-15
> **GoofusGreen said:**
> ```
$ wine start SteamInstall.msi
fixme:exec:SHELL_execute flags ignored: 0x00000100
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: Success

```

Or by running outside terminal, I get the wine error dialog "Success" with the red circle next to it and a little OK under it.

lol, "Error: Success"

Wine 1.1.4 64-bit (iexplore doesn't work either)
Ubuntu 8.10

Also, when I try steaminstall.exe, Steam installs properly up to the point that it must update. Then it gets stuck at "Steam is looking for updates." and does nothing.

Same issue with the 1.0.1 stable version. (At least iexplore works)

-----------------------------------------------------------------------

Solved: use Gecko 0.9.0 and use "msiexec /i SteamInstall.msi"

Problem: Steam crashes/freezes when attempting to install games.
Thanks for that msiexec /i SteamInstall.msi command. Wine apparently still has this problem.

---

### Post by alienclone on 2009-11-15
Lol'd at "Error: Success"

---

