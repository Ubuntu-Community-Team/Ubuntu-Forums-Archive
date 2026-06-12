---
title: "Installing Dreamfall: TLJ (Ubuntu Lucid 10.04 &amp; Wine 1.3.6)"
date: 2010-11-19
forum: Wine
---

### Post by Evanah on 2010-11-19
Hi all!

First of all, has anyone tried to install Dreamfall with these versions of wine and ubuntu and made it work ok? 

I've seen some old threads about installing this game, but nothing recent, so I'm not sure should I go with a few years old HowTo...

I tried to install this from a cd, so far I've installed the .exe game file (then DirectX setup window popped out, but trying to install it gave an error). I've read somewhere that d3dx9_27.dll file should be downloaded and copied to Wine's \system32 folder. So I did that. Then tried to run the game but an error pops out saying:
"Failed to initialize Direct3D. Aborting."

Now what??

Any help would be highly appreciated!

---

### Post by Evanah on 2010-11-21
Case solved!

I'm posting the solution so If someone has a similar problem, they could find this useful :).

I followed all the steps in this HowTo:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5305](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5305)

but after that still was getting the "Failed to initialize Direct3D. Aborting." message.

So I ran the game from terminal and it turned out that this part in the output:

>err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1024x768x32 @0

..was the problem, so I enabled Virtual Screen in Wine cfg, and the game finally works! (in a window, that is, but it works!) ! Yay! :))))))))))

---

