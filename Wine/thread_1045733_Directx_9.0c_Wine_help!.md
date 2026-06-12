---
title: "Directx 9.0c Wine help?!?"
date: 2009-01-20
forum: Wine
---

### Post by mr_x408 on 2009-01-20
hey everyone, i am trying to get a game to work in wine and in order to do that i have to install directx 9 using this tutorial:
[INDENT]   
[LIST=1]
[*]Install a native **mscoree.dll** and **streamci.dll** into* /system32 *from a windows install and set then to native Windows.
[*]Go to _~/.wine/drive_c/windows/system32 _and rename **d3d8, d3d9, ddraw, dsound, dsound.vxd, quartz dlls** to ****.bak***
[*]You will need to set a large number of dlls to native for the install to work properly. Here is the full list of dlls that need to be set.
       
       "d3d8"="builtin"
"d3d9"="builtin"
"d3dim"="native"
"d3drm"="native"
"d3dx8"="native"
"d3dx9_24"="native"
"d3dx9_25"="native"
"d3dx9_26"="native"
"d3dx9_27"="native"
"d3dx9_28"="native"
"d3dx9_29"="native"
"d3dx9_30"="native"
"d3dx9_31"="native"
"d3dx9_32"="native"
"d3dx9_33"="native"
"d3dx9_34"="native"
"d3dx9_35"="native"
"d3dx9_36"="native"
"d3dxof"="native"
"dciman32"="native"
"ddrawex"="native"
"devenum"="native"
"dinput"="builtin"
"dinput8"="builtin"
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
[*]Now, download the [Installer]("http://filehippo.com/download_directx/") and run it.
[*]Go through the installation. - No you don't need to reboot ;)
[*] wine DXSETUP.EXE[FONT=Verdana][/FONT]
[/LIST]
Im just a little confused  on how to set the dlls to native/ bultin... thx in advance for the replys
 [/INDENT]

---

### Post by mr_x408 on 2009-01-20
nevermind... figured it out

---

