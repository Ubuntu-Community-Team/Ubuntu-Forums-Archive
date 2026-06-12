---
title: "Pop OS problem"
date: 2021-07-25
forum: Ubuntu/Debian BASED
---

### Post by nightbird827 on 2021-07-25
Sorry if this is the wrong place. I feel pretty lost, but from what I understand Pop OS is built on Ubuntu so I assume this is correct. Anyways, I have an issue. Whenever I install ANYTHING from the Pop Shop, I get  the error "Error while installing package: installed postfix package  post-installation script subprocess returned error exit status 75" and  it says installation failed. However, the app still installs. It has  done this with Steam, Wine, WineTricks, and PlayOnLinux. Steam will  load, but it takes an excessively long time and I never receive the  email from SteamGuard (Not sure if it's related to the installation  error, but just including). Any idea how to fix this? From what I  googled, I seen a comment about removing the space in the computer ID  name if present, but mine does not have one (It's labeled as  JameyLaptop). Also in addition to that, I have an issue with the Fractional Scaling  option. !00% and 200% work perfectly fine, but anything else makes the  desktop stretch completely off screen, and the only way to resolve it is to swap back to 100% or 200%.

---

### Post by wildmanne39 on 2021-07-25
Moved to Ubuntu/Debian BASED.

---

### Post by guiverc on 2021-07-26
If this was a Ubuntu/Debian system and I had issues in a software/applications centre/center/store I'd explore it via terminal.

Firstly check there are no issues in your sources.

```
sudo apt update
```

read or scan the lines shown to ensure they look valid, and no warnings or errors are shown. If it's fine, I'd move to the next step, otherwise I'd fix them and repeat the `apt update` (*update software lists*) step.  This output should also reflect your *unstated* release (ie. I'm on *impish* so I'd expect only *impish* to appear on on lines; if you're on *focal* or 20.04 you'd expect to read only *focal*) so I'd look for potential *red-flags/*causes of problems where some lines contain a *codename* for a release you're not running.

```
sudo apt full-upgrade
```

ie. try and install all upgrades available for your system. Yes many users limit the upgrade, but given you have problems I'd let your system fully-upgrade.  Again I'd read the output and take note of any error messages or warnings that show.

Often errors here have clues; which may have you running fix commands such as --fix-broken  (`sudo apt -f install`) but messages will usually provide clues as to what to run, though usually the output is somewhat explicit in what to run to fix.

---

