---
title: "Paranoia about non-Nvidia graphic cards?"
date: 2009-10-24
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-10-24
I have a GeForce2 MX 400 graphics card currently and a continual problem I've had with using Linux is that I'll set a resolution (usually 1600x1200) and when I restart the computer sometimes I'll have a very low default resolution that can't be reset just by going to the display settings. It's been awhile since I've had to reset it but if I can remember it either involved resetting something from the command line or hitting a refresh button or something on the login page.

The way I've gotten around this problem is by installing Nvidia's official Linux package called "nvidia-settings" which writes your settings directly to the xorg.conf file and unlike the standard display settings that Ubuntu gives me the settings I set with Nvidia's proprietary app actually stay they way that I want them to and don't revert back.

Hopefully that all made sense.

What I want to know is: If I was going to buy/build a new computer and use Ubuntu on it should I be worried about using a non-Nvidia graphics card because the nvidia-settings app won't work with non-Nvidia graphics cards? This is a very irritating problem and I don't want to buy a graphics card only to find out that it won't even keep my default settings.

---

### Post by Xbehave on 2009-10-24
nvidia-settings sounds like a workaround for the prop drivers, I use ATI (with opensource drivers so no3D, yet (apparently its coming soon though)) and used to use intel drivers and never had such a problem. I also don't have the problem on my nvidia desktop so maybe its just me.

edit: I suspect if its needed there will be similar workarounds for other graphics cards (i'd guess most will be editing hal configs)

---

### Post by Skripka on 2009-10-24
> **blueshiftoverwatch said:**
> I have a GeForce2 MX 400 graphics card currently and a continual problem I've had with using Linux is that I'll set a resolution (usually 1600x1200) and when I restart the computer sometimes I'll have a very low default resolution that can't be reset just by going to the display settings. It's been awhile since I've had to reset it but if I can remember it either involved resetting something from the command line or hitting a refresh button or something on the login page.

The way I've gotten around this problem is by installing Nvidia's official Linux package called "nvidia-settings" which writes your settings directly to the xorg.conf file and unlike the standard display settings that Ubuntu gives me the settings I set with Nvidia's proprietary app actually stay they way that I want them to and don't revert back.

Hopefully that all made sense.

What I want to know is: If I was going to buy/build a new computer and use Ubuntu on it should I be worried about using a non-Nvidia graphics card because the nvidia-settings app won't work with non-Nvidia graphics cards? This is a very irritating problem and I don't want to buy a graphics card only to find out that it won't even keep my default settings.

If you're worried about it, just write the settings to xorg.conf yourself.  You don't need nvidia-settings to do that, only a text editor, nano, or vi.

---

### Post by Xbehave on 2009-10-24
> **Skripka said:**
> If you're worried about it, just write the settings to xorg.conf yourself.  You don't need nvidia-settings to do that, only a text editor, nano, or vi.
Ubuntu moved to HAL so your xorg.conf is generated every reboot, for customisation you have to edit your HAL settings*

*I'd guess nvidia-settings cheats and writes xorg.conf after HAL writes it but before xorg reads it.

---

### Post by Skripka on 2009-10-24
> **Xbehave said:**
> Ubuntu moved to HAL so your xorg.conf is generated every reboot, for customisation you have to edit your HAL settings*

*I'd guess nvidia-settings cheats and writes xorg.conf after HAL writes it but before xorg reads it.

Really?

What a dumb thing for Ubuntu to do.

---

### Post by Xbehave on 2009-10-24
> **Skripka said:**
> Really?

What a dumb thing for Ubuntu to do.
Yeah i mean who likes auto-configuration? Oh right Ubuntu users, that's why they use Ubuntu NOT arch. There are no end of situations where auto-configuration is useful, but yeah helping users not having to manual edit config files is dumb because it doesn't work everywhere.

---

### Post by Skripka on 2009-10-24
> **Xbehave said:**
> Yeah i mean who likes auto-configuration? Oh right Ubuntu users, that's why they use Ubuntu NOT arch. There are no end of situations where auto-configuration is useful, but yeah helping users not having to manual edit config files is dumb because it doesn't work everywhere.

"Autoconfiguration" and regenerating config files every reboot are two COMPLETELY different things.  It is funny how y'all love to turn threads into being about Arch, with absolutely no help from anyone else.

---

### Post by Sylslay on 2009-10-24
Stuck to nvida, just chose very popular midle model, 

In my opinion Intsl is second worst, after ATI:

My list of graphic card:

1.Nvidia
2.ATI
3.Intel
4. Other - dont acount :KS

---

### Post by NCLI on 2009-10-24
> **Skripka said:**
> "Autoconfiguration" and regenerating config files every reboot are two COMPLETELY different things.  It is funny how y'all love to turn threads into being about Arch, with absolutely no help from anyone else.
I'd say they're exactly the same thing, actually. It checks what hardware you have in your PC everytime you reboot, to make sure nothing has been changed while the computer was off, and writes a new xorg.conf file to make sure nothing bad happens if you have.

What's wrong with that?

---

### Post by blueshiftoverwatch on 2009-10-24
> **Skripka said:**
> If you're worried about it, just write the settings to xorg.conf yourself.  You don't need nvidia-settings to do that, only a text editor, nano, or vi.
The nvidia-settings app writes it's own special section to the xorg.conf file that's different from where the default Linux display settings app writes the information such as the monitor's resolution.

---

### Post by Skripka on 2009-10-24
> **NCLI said:**
> I'd say they're exactly the same thing, actually. It checks what hardware you have in your PC everytime you reboot, to make sure nothing has been changed while the computer was off, and writes a new xorg.conf file to make sure nothing bad happens if you have.

What's wrong with that?

Umm, read your own post.


Because there is virtually NO reason for your computer to go altering xorg.conf on every reboot by itself w/o user input, in real life.  I qualify it as "virtually", as I have a bad bout of flu right now and am not in a state of mind right now to think thrings through enough to say "never".

If the hardware and the xorg.conf haven't changed--why should a new xorg.conf be written or processed at all (let alone on every reboot)?  Just for &^%$s and giggles?  Just to keep users on their toes?  As I said-it is dumb.

---

### Post by Xbehave on 2009-10-24
> **Skripka said:**
> If the hardware and the xorg.conf haven't changed--why should a new xorg.conf be written or processed at all (let alone on every reboot)?  Just for &^%$s and giggles?  Just to keep users on their toes?  As I said-it is dumb.

Because xorg.conf doesn't really matter its a file that is that's used for legacy reasons, xorg gets it's config data straight from HAL, if you want to change settings, change them in HAL configs that way they still apply when hw changes. It makes more sense for your configuration to be interms of hardware found that static hardware. 
If i have a mouse, give me a pointer and make it behave as ...
If i have an Nvidia card, give me a display of size...
If i have a 2nd Nvidia card, give me a 2nd dislay...

Static configurations don't make sense for anything that **can** change, using them just because most of the time something doesn't change is no excuse.

---

### Post by blueshiftoverwatch on 2009-10-24
Apparently [this guy]("http://forum.notebookreview.com/showthread.php?t=223017") was having the same problem.

Is this a problem that only happens with Nvidia graphics cards? I think I remember trying to manually edit the xorg.conf file with my desired resolution and having it not work until I used the nvidia-settings app to change my resolution.

---

### Post by Xbehave on 2009-10-25
> **blueshiftoverwatch said:**
> Apparently [this guy]("http://forum.notebookreview.com/showthread.php?t=223017") was having the same problem.

Is this a problem that only happens with Nvidia graphics cards? I think I remember trying to manually edit the xorg.conf file with my desired resolution and having it not work until I used the nvidia-settings app to change my resolution.
It may also affect flgrx but opensource drivers get their settings straight from HAL. There are probably a fair few ways to fix this that aren't nvida dependent. In order of goodness
[LIST=1]
[*]Put the settings into hal (example files are in /usr/share/hal/fdi/policy/ and ones in use are in /usr/share/hal/fdi/policy/ )
[*]make the xorg.conf file read only (maybe even [immutable]("http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html"))
[*]Script the xorg.conf creation yourself (something like:
[LIST=1]
[*]save an xorg.conf somewhere (e.g /etc/X11/xorg.conf.saved)
[*]write a script and put it in /etc/init.d/ (e.g /etc/init.d/restoreXorg)
```
#!/bin/sh
cp /etc/X11/xorg.conf.saved /etc/xorg.conf
```
(you may want to use ln -s instead of cp)
[*]make it an executable (chmod 755 /etc/init.d/restoreXorg)
[*]link to it in your startup (ln -s /etc/rc5.d/S27restoreXorg /etc/init.d/restoreXorg)
but not exactly like that and double check all my commands as this is all theory i have an xorg less system so this may not work.)
[/LIST]
[/LIST]

---

