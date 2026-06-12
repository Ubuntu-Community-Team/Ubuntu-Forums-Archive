---
title: "Notorious Games - Xsyon"
date: 2011-01-20
forum: Wine
---

### Post by Layvian on 2011-01-20
Notorious Games, is working on a game named [COLOR=DeepSkyBlue][Xsyon]("http://xsyon.com/")[/COLOR].  I am having an issue with the game after the install(Of which goes very smooth.)  As soon as the game launches to the patcher, and after I sign in, I get a message that pops up saying there is a deficiency in Wine.

Here is what I have done so far:

[LIST]
[*]Installed Wine
[*]Installed Winetricks
[*]Installed (sh Winetricks) - [d3dx9, vcrun2005, corefonts, dotnet20, msxml6, physx, and vb6run]
[*]Installed Xsyon.exe
[*]Ran Xsyon
[*]Signed-in (Username, and Password)
[*]Error Message
[/LIST]
There was a guy(sxe) who posted about it working on his system a few months ago. Here is his [COLOR=DeepSkyBlue][link]("http://www.xsyon.com/forum/showthread.php/1997-Xsyon-on-linux")[/COLOR].

Here is what I am using:

[LIST]
[*]Ubuntu 10.10 (x64)
[*]Core i7
[*]6 Gigs RAM
[*]Nvidia 250 GTS (2x - SLI Configured)
[*]Driver Version: 260.19.06
[*]Ethernet 10/100/1000 Hard Wired Connection at 40/20 Mps
[*]300 Gigabyte 10,000 RPM Western Digital VR
[*]1 TB 7,200 RPM Seagate
[*]Intel Sound 5.1/7.1
[*]Sony Blu-ray Drive Read-Only
[*]Up-to-Date Software
[/LIST]
Any help would be awesome.  I will mention I have not posted this elsewhere, excluding to Sxe on Xsyon Forms[COLOR=DeepSkyBlue][URL="http://www.xsyon.com/forum/showthread.php/1997-Xsyon-on-linux/page2"]
[Listed on Page 2][/URL][/COLOR].

Thanks,

Layvian

---

### Post by fain on 2011-02-09
I got this too, then I found this thread.

[http://www.xsyon.com/forum/showthread.php/1997-Xsyon-on-linux](http://www.xsyon.com/forum/showthread.php/1997-Xsyon-on-linux)

Edit: just seen your link lol

Did this

```
winetricks d3dx9
```

and it works pretty well now :D hope it works for ya...

I think I have vcrun2008 for another game I play as well. Not sure if that matters or not.

---

