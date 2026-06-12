---
title: "WOW in Ubuntu 9.10 messed up gfx"
date: 2009-10-20
forum: Wine
---

### Post by tehg on 2009-10-20
Hello, all I was using a different linux distro, but it didn't understand my video card. Ubuntu seems to compiz works I have DRI etc. I have a Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller.

When I run WOW it looks f'd up.. here is a pic link: [http://i37.tinypic.com/ohstqp.png](http://i37.tinypic.com/ohstqp.png)

When I run wow in terminal this is what terminal spits out:

wine "/home/george/Games/WOW/Wow.exe" -opengl
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed9c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ec8c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f578,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f574,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f4f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f4e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39eff8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f130,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39defc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df24,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x37404084) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x20024, 0x133e30): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x39eb3c,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub                                                  

Also yes, I did do all the speal in the wine regedit, winecfg, config.wt file in the wow data folder etc

THANK YOU, hopefully someone know whatsup :D

I just did an update.. and here is what it says now

fixme:win:EnumDisplayDevicesW ((null),0,0x39ed9c,0x00000000), stub!
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  495
  Current serial number in output stream:  495

---

### Post by tehg on 2009-10-24
No one knows what's up?

---

### Post by tehg on 2009-10-24
lol, it's me again!

---

### Post by P4man on 2009-10-24
This may or may not help:
[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

But tbh running windows games on wine is already a hack at best, running either compiz on linux or WoW on windows using an intel onboard video decelerator is not a great idea, mixing them all together has to be a recipe for disaster.

---

### Post by themusicalduck on 2009-10-24
Are you disabling compiz before playing?

---

### Post by tehg on 2009-10-24
> **P4man said:**
> This may or may not help:
[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

But tbh running windows games on wine is already a hack at best, running either compiz on linux or WoW on windows using an intel onboard video decelerator is not a great idea, mixing them all together has to be a recipe for disaster.

yeah, i followed that to the "t".

also compiz isn't on i use gnome-shell, and it was recommended to disable compiz while using it; so i did.

---

### Post by shae on 2009-10-25
Gnome-shell is also using composite I bet.  You should try running Wow in just plain Metacity.

---

### Post by nj.pemberton on 2009-10-30
hum i had similar results after some update and i lost my glx, 
I had 2 do a complete reinstall of my nvidia drivers (remove anything existing) and start from scratch. 
the way i could c that the glx wasnt working was under, nvidia settings> i had no information under the opengl/glx information tab. 
hope this helps

---

### Post by ArcaVex on 2009-11-02
I wouldn't recommend playing even a low-mid graphic game like WoW with an integrated graphics card in the first place.

Make sure the card/driver supports OpenGL, make sure you use proprietary drivers for this.
Do

sudo lshw -C display


to see what driver you are using

---

