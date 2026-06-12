---
title: "can not get any game in wine to work"
date: 2011-04-01
forum: Wine
---

### Post by f4rm0r on 2011-04-01
Hi, I am having trouble getting any game in wine to work...
well, it's not the games that are the trouble, the trouble are that directx do not want to start, I do not know how to fix this, can you guys help me?

the games I tried are:

Starcraft 2 (followed a guide, it worked for everyone else, except me)
Call of Duty: Modern Warfare 2 (installed through steam)
Mirrors Edge (will not start at all)

My system specs are:

lenovo thinkpad W500
ATI Mobility HD Radeon 3650
Intel Centrino 2 inside @  2.66 GHz
4GB RAM

ubuntu 10.10 64-bit

---

### Post by f4rm0r on 2011-04-01
here is an update:
I installed Graphic card Drivers and then I can start most of the games...
but I can not start Call of Duty: Modern Warfare2 - Multiplayer
but I can start all other games

---

### Post by elnetotaca on 2011-04-02
maybe your wine installation is not complete.
if you want, follow my little tutorial here;


open a terminal
we have to erase the current wine you have
sudo apt-get autoremove wine --purge

cd
rm -rf .wine
sudo apt-get update
sudo aptitude install wine
wine --version
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update && aptitude install wine
winecfg
cd
cd .wine
wget wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
chmod +x ./winetricks
./winetricks d3dx9
./winetricks droid
./winetricks physx
./winetricks allfonts
./winetricks allcodecs
./winetricks winxp
./winetricks sound=alsa
./winetricks volnum
./winetricks glsl-disable
./winetricks vcrun2008
./winetricks dcom98
./winetricks dotnet20
./winetricks d3dx9 droid winxp sound=alsa volnum vcrun2008 dotnet20 ie6 corefonts


now, some games use lots of resources from your pc
so you might have to do this;
look up the file user.reg
and add;
[Software\\Wine\\Direct3D] 1258821033
"DirectDrawRenderer"="opengl"
"Nonpower2Mode"="repack"
"OffscreenRenderingMode"="fbo"
"RenderTargetLockMode"="auto"
"UseGLSL"="readtex"
"VertexShaderMode"="hardware"
"VideoDescription"="NVIDIA GeForce 8500 GT"
"VideoDriver"="nv4_disp.dll"
"VideoMemorySize"="256"


enjoy

---

