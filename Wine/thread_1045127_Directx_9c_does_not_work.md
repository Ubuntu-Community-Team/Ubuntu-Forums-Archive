---
title: "Directx 9c does not work"
date: 2009-01-20
forum: Wine
---

### Post by pancham on 2009-01-20
I have installed directx 9c in wine as given in [http://howto.landure.fr/gnu-linux/install-directx-9-0c-on-linux-using-wine](http://howto.landure.fr/gnu-linux/install-directx-9-0c-on-linux-using-wine) but with the latest ie nov-2008 redist but still when i try to insall a game from the cd it says you have to install directx before you proceed,,, what is the problem:(

---

### Post by Brynster on 2009-01-20
Ok Firstly

Directx 9.0 should not be installed as it can and does break .dll's written especially for wine that handle directx compatibility/emulation*

SO step one i would completely remove and reinstall wine to ensure you have cleared out the possibility.

Then check on [http://appdb.winehq.org/](http://appdb.winehq.org/) to see if the game is supported and if there is a special process for getting it installed.

Sice you have not said what game is your wanting to run thats is the best advice i can give.

(*I know already its not emulating anything really but substituting widows dx calls into an equivalent Linux call)

---

### Post by cogadh on 2009-01-20
No need to uninstall/reinstall Wine, if you want to start fresh, you just need to delete the .wine directory from you home directory. When you install DX, it doesn't actually overwrite the Wine DLLs, it just overwrites the pointer/placeholders in your .wine directory, which are re-created when you make a new .wine directory.

Otherwise, Brynster is correct, you don't need to install DX in Wine and in most cases, you really shouldn't. From the [Wine FAQ]("http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2"):
> **8.1. Does Wine support DirectX? Can I install Microsoft's DirectX under Wine?**

Wine itself provides a DirectX implementation that, although it has a few bugs left, should run fine. Wine supports DirectX 9.0c at this time. Plans for DirectX 10 are underway.

/!\ **If you attempt to install Microsoft's DirectX, you will run into problems.** It is not recommended nor supported by Wine HQ to attempt this. You can install the runtime, but it will not run. The runtime needs access to the Windows drivers, and Wine cannot access them for obvious reasons. The only native Microsoft DLLs that could be useful anyway are the d3dx9_xx.dll type ones, and these require you to accept Microsoft's license. Additionally these DLLs are now part of the Wine tree. So, as Wine improves these DLLs will only become less relevant.

That said, there are some guides out there which describe how you can install Microsoft's DirectX. I reiterate: It is not recommended nor supported by Wine HQ to attempt this. Furthermore it is considered off topic in Wine HQ support mediums (such as the forums). Please use a clean Wine configuration folder before seeking help. (You may need to rm -rf ~/.wine and re-install your Windows applications.)

As for your installation issue, that was likely created by the fact that you installed DX. On its own, Wine usually does not have a problem with games forcing you to install DX, though you might be offered the option to install it (which you should decline).

---

### Post by pancham on 2009-01-20
Thanks alot to you both for the advise

---

