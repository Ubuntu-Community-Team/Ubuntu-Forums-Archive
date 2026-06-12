---
title: "World of Warcraft not working after latest Ubuntu upgrade!"
date: 2009-01-29
forum: Wine
---

### Post by Martin Wolflux on 2009-01-29
**SOLVED!**
[QUOTE="Wolflux"]Problem solved =) I found the solution. It was a driver error which had to be fixed manually as root, but WoW is running fine now.

What I did was to uninstall Wine using > sudo apt-get autoremove wine

And then I re-installed it. Then I did the following:

# apt-get remove --purge xserver-xorg-video-radeon

# apt-get remove --purge fglrx-kernel-source

# apt-get install fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev

After restarting X everything worked perfectly![/QUOTE]



-----------------------------


Hi, I've a small problem with World of Warcraft right not. I just updated my Ubuntu system with 44 upgrades (Jan. 29th, 09) and now Wine refuses to run World of Warcraft no matter what I do. I do not get any error messages - it tries to run the Wow.exe file, but it stops trying to run it after a few seconds and basically leaves me at my desktop.
There are no error messages at all - WoW just doesn't run for me anymore. It can't open the .exe file (although the launcher works fine).

Any suggestions on how to fix this?

(I have all administrative access on my account - only way I can get even more control at this point is by logging in as root)

Thanks in advance.

---

### Post by hikaricore on 2009-01-29
Did you pay attention to the updates?
If a new version of WINE was released and you installed it this could be the issue.

Also you may have installed a new kernel or video drivers and something didn't get configured or go right.

The problem is you didn't provide enough info.

Does this happen when you try to run other 3d games?
Other titles under WINE?
Have you rebooted your system since the updates?
What happens when you run WoW from a terminal?
Etc, etc, etc... provide more info.

---

### Post by Martin Wolflux on 2009-01-29
Hi,
Yes, I did. And according to WineHQ.com, Wine has not been updated yet.
There were a lot of driver updates, though and I have been looking through my driver settings, having read your response, and found the ATI Proprietary Driver to be deactivated (and it refuses to re-activate). I currently have no other 3D games installed on Ubuntu Intrepid Ibex, however I happen to have gotten my hands on a handy set of free, easy-going 3D games two days ago. I will try and see if those respond too.

Yes, I've restarted the system after the updates, although I have not successfully run WoW from a terminal just yet (it could not find the folder, but I'll try it now that I moved it to a proper folder). I can try and just run the program as root (of course, not logging in as that would be a security breach) and see what happens as well.

[edit]: Trying to force the program to run as root gives this message:
```

Could not load Mozilla. HTML rendering will be disabled.
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  3264
  Current serial number in output stream:  3264
err:process:__wine_kernel_init boot event wait timed out
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  135
  Current serial number in output stream:  135


```

[edit2]: I found the missing file (Microsoft.VC80.CRT) and put it in the folder. This is the error message in the terminal:
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  135
  Current serial number in output stream:  135

```


[edit3]
```
wine: /home/wolflux/.wine is not owned by you
```

Could this be the problem? I've owned .wine until about half an hour ago and I find that particularly strange.


[edit4]: Other 3D applications do not work with Wine anymore.

---

### Post by hikaricore on 2009-01-29
Those X errors:
> 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  135
  Current serial number in output stream:  135

Are a sign that something is wrong with your video drivers.

The output of:

> wine: /home/wolflux/.wine is not owned by you

Means that at some point you ran WINE as root which you should not really do.

So yea start with your video drivers and once you get that problem fixed WoW should work.

---

### Post by Martin Wolflux on 2009-01-29
Since I am rather Linux illiterate at the moment (still learning), could you help me configure Wine to run on my user account?

Thanks for the help, by the way.

Also, I'm working on the drivers at the moment - I'll try upgrading to the latest driver for my graphics card (ATI Radeon X300 series), and if that does not work, I'll try downgrading to see if that solves the problem.

---

### Post by hikaricore on 2009-01-29
Open a terminal and type:

> sudo chown wolflux:wolflux -R /home/wolflux/.wine

This will change the owner of your WINE directory as well as every file and directory inside of it to wolflux.
(i'm assuming that's your username as it was in one of quoteblocks in the posts you've made)
Depending on the number of files this may take some time.

In the future avoid running WINE as root with sudo for the best possible security. :)

---

### Post by Martin Wolflux on 2009-01-29
Thanks! I have changed ownership now!

I have discovered that with the new driver, a new option appeared on my Applications menu called "ATI Catalyst Control Center". I'd like to uninstall it so that I can use the proprietary driver (which ceased to function with the introduction of that ATI-thing). I checked with the AMD website, and the version that came onto my Ubuntu was apparently meant for another distribution of Linux (Red Hat or Hardy Heron), so I am surprised at how it got there to begin with.

Alternatively, I do have a functional laptop that can run WoW as well (it has Windows Vista, unfortunately) so this isn't really much of an hindrance - although I did really enjoy WoW on Linux (as, opposed to the time I used Windows, I have around 100 FPS, going up from Windows' crappy 20 FPS =/).

Upgrading and downgrading hasn't worked.

Alternatively, I can just clear our my harddrive entirely and re-install Linux from scratch. I can just back-up the software I need on my web server.

---

### Post by Martin Wolflux on 2009-01-29
Problem solved =) I found the solution. It was a driver error which had to be fixed manually as root, but WoW is running fine now.

What I did was to uninstall Wine using > sudo apt-get autoremove wine

And then I re-installed it. Then I did the following:

# apt-get remove --purge xserver-xorg-video-radeon

# apt-get remove --purge fglrx-kernel-source

# apt-get install fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev

After restarting X everything worked perfectly!

---

