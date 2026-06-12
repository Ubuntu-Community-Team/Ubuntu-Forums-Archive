---
title: "Guide for Directx in WINE, please clarify this"
date: 2009-03-13
forum: Wine
---

### Post by sp176 on 2009-03-13
I found this on the web and I hope it works, but could someone clairify for this noob please?  I numbered the steps for ease.  The url is: [http://www.smokinglinux.com/gaming/play-your-windows-games-with-wine-and-directx](http://www.smokinglinux.com/gaming/play-your-windows-games-with-wine-and-directx)

1.  To make a good installation of DirectX on Wine you have to install native mscoree.dll and streamci.ddl in /system32 from a windows Install and set them as native Windows Libraries.

2.  You have to wrap with winecfg many DirectX dlls, so you can add "d3d8" with winecfg and then with "sudo gedit /home/your_user/.wine/user.reg" add this list of dlls:

    [Software\\Wine\\DllOverrides]
    "d3d8"="builtin"
    "d3d9"="builtin"
    "d3dim"="native"
    "d3drm"="native"
    "d3dx8"="native"
    "d3dxof"="native"
    "dciman32"="native"
    "ddrawex"="native"
    "devenum"="native"
    "dinput"="builtin"
    "dinput8"="native"
    "dmband"="native"
    "dmcompos"="native"
    "dmime"="native"
    "dmloader"="native"
    "dmscript"="native"
    "dmstyle"="native"
    "dmsynth"="native"
    "dmusic"="native"
    "dmusic32"="native"
    "dnsapi"="native"
    "dplay"="native"
    "dplayx"="native"
    "dpnaddr"="native"
    "dpnet"="native"
    "dpnhpast"="native"
    "dpnlobby"="native"
    "dsound"="builtin"
    "dswave"="native"
    "dxdiagn"="native"
    "mscoree"="native"
    "msdmo"="native"
    "qcap"="native"
    "quartz"="native"
    "streamci"="native"

3.  Now, you have DirectX wrappers configured correctly but you have to install DirectX 9.0c to complete succesfully your job. Download DirectX form here: [http://filehippo.com/download_directx/](http://filehippo.com/download_directx/)

4.  you have to extract DirectX in a directory of your choice (z:\home\your_user\directx) and then run setup:

    $ wine directx_nov2007_redist.exe
    $ cd /home/your_user/directx/
    $ wine DXSETUP.EXE

5.  God Job! You have installed DirectX with Wine on your Linux Desktop. To test it you can run dxdiag.exe:

    $ cd /home/your_user/.wine/drive_c/windows/system32
    $ wine dxdiag.exe

I do not understand steps 1 & 2, but I included 3-5 so others can use this as a complete guide.  Can someone please spell it out easily what 1 & 2 mean?

---

### Post by hikaricore on 2009-03-13
Be aware that this guide was written in 2007...
**You should not be installing DirectX** under WINE unless you have good reason to as WINE had DX support native.

If you run into one of the few cases where you need any DirectX libraries, please follow specific guides for the game you are installing.

---

### Post by sp176 on 2009-03-13
Do you mind telling me where to look?  I type directx in the search query and I get nothing.  I tried google, and this is what I found.

I am new to ubuntu, and I have been trying to get my oblivion to work.  I realize there are tons on this site about that.  It tells me to wine regedit, and find the folder hKEY_CURRENT_USER/Software/Wine/Direct3d...only there is no direct3d folder.

Other people have had this problem from what I saw in the thread, but I couldnt find an answer there.  500+ entries, so I may have missed it.

---

### Post by sp176 on 2009-03-13
FYI I have wine 0.9.46 on Ubuntu 7.10.  Could you tell me how to update past wine 1.0.  I have tried to update and it says I have newest version, I tried synaptic as well.

---

### Post by cogadh on 2009-03-13
That registry entry is not created by installing DirectX (which I must reiterate, you should not be installing in Wine), you need to create it yourself with the registry editor.

As for updating Wine, the only way to do it on 7.10 is to compile it yourself. If you want to get pre-built packages, you will need to upgrade Ubuntu to a more recent (supported) version like 8.04 or 8.10.

---

### Post by sp176 on 2009-03-13
Could you please point me in the right direction?  You guys tell me not to install but I have tried many different search queries and that is the only info I find, is on installation, not creating it myself.

---

### Post by aaronb on 2009-03-14
Wine has its own implementation of Direct X. Installing direct X from Microsoft will not help games run better. 

The link that you stated is out of date and wine 0.9.46 is quite old now.

Version 1.0.0 of wine is available here [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) 

To get more recent versions of wine there are the following options:

**Option 1**

Compile and install the newest wine from source.

**Option 2**
Update your Ubuntu to a newer version and then follow instructions found here: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
Although upgrading to a new version of Ubuntu has always worked for me, take a few minutes to read the release notes just in case there are any "surprises".

---

