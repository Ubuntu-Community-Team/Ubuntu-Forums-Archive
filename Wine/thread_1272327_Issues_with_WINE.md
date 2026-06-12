---
title: "Issues with WINE"
date: 2009-09-22
forum: Wine
---

### Post by Grukmuck on 2009-09-22
so i installed WINE to play wow, and here are my troubles:

1st, my resolution changed when i installed wow and i cant get it back with out having to restart my comp.

2nd, Im having problems getting past the accept EULA. the accept button stays grey and i cant click it.

Im sure these problems have been answered already, so if someone can point me to where i can find them, or tell me how to update WINE that would be great.

thanks in advance,

-gruk

---

### Post by Grukmuck on 2009-09-23
so here is what is happening now.

I updated WINE and WoW installed with a few problems, but i got past them. the resolution problem still persits, and now the game crashes once i start to move my char. Im at a loss.

-gruk

---

### Post by hikaricore on 2009-09-23
You didn't mention anything about your hardware..

---

### Post by Grukmuck on 2009-09-23
sorry, but im not too sure exactly what hardware i have. this is an old emachine that i bought from a friend of mine. will lspci give you the info you need?

---

### Post by Grukmuck on 2009-09-25
ok so i upgraded back to 9.04, re-installed WINE and WoW. Everything went smooth until i opened WoW for the 1st time. The problem is the in-game resolution is too big for the window that its in, so i cant see anything except the EULA text, not even the accept button. I tried changing the resolution with Config.wtf, but that only made the window bigger. 

I have been unable to find a solution, or even hear about this particular problem.

this is what lspci says about my hardware:

```
brian@Mosheen:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:02.0 ATM network controller: Intel Corporation LE80578 (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
brian@Mosheen:~$ 
```


I hope someone can help me to solve this problem, but in the mean time I will keep searching for solutions.

thanks in advance,

-gruk

---

### Post by Grukmuck on 2009-09-29
So here's an update for my issues with WINE.

I was thinking that WoW was crashing my system because I'm using the integrated graphics card and its just not powerful enough. So I decided to build my own computer, and the first thing I ordered was my graphics card. So now I'm just waiting for it to arrive via Newegg.com I'm gonna try to put the card in this machine first to see if that will help any.

So then I decided I want to install iTunes. I did and low and behold, when I opened it up it crashed my comp, just like WoW does. Well, not exactly crash. iTunes really bogged my system down though. Almost to the point where I thought it crashed. My guess is it has to be a configuration problem. Maybe I don't have WINE configured correctly. I think I'm going to try to install something else and see if it crashes my system, or boggs it down as well.

One I get something else installed in WINE I will post another update.

-Gruk

p.s.
     This thread almost sounds like a blog :lolflag: :popcorn:

---

### Post by hikaricore on 2009-09-29
iTunes also isn't really a good judge of how well WINE runs as it barely does such and has limited usability.
Without terminal output or further info I can only say it's still probably your Video card or overall system hardware.
Let us know how it works out when you get the new card.
Btw what did you order/

---

### Post by Grukmuck on 2009-10-06
Here is another long awaited update of my issues with WINE, lol.

I haven't really had time to try any other apps in WINE to see if I'm having a configuration problem. So I've just been trying to figure out if it's a hardware problem. 

The problem so far: I can open WoW and long into my account and make it as far as the character selection/creation screen. Once I create or choose a character to enter the world with my system freezes. I cant move my mouse or anything. Though the music keeps playing. I have to do a hard reset to get back to my desktop. I followed the instruction for integrated Intel Graphics chips [***here***]("http://ubuntuforums.org/showthread.php?t=1130582"). The only noticeable difference after follow the instructions was that I can move my mouse cursor. I still have to do a hard reset to get out of it. Since that didn't work, I ran WoW from the terminal to see what it said. I didn't even make past the account log in before my system froze.

This part was the most fun. Since I couldn't read the terminal due to the freeze, I had to set it to 'always on top' and physically write down the info it was spitting out. I had to do it twice to get the top half and the bottom half. This is what it said:

```
brian@Mosheen:~$ '/home/brian/.wine/dosdevices/c:/Program Files/World of Warcraft/Wow.exe' 
get fences failed: -1
param: 6, val: 0
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed4c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39eb4c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f390,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f524,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f558,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1465c0) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null)),0,0x39f0e0,(0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x159560,0x159460): stub!
fixme:win:EnumDisplayDevicesW ((null)), 0,0x39de8c,(0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null)),0,0x39deb4,(0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null)),0,0x39de48,(0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:INternetSetOptionW Iternet OPTION_SEND/RECIEVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:INternetSetOptionW Iternet OPTION_SEND/RECIEVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Iternet OPTION_SEND/RECIEVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x3740524), using GetSystemInfo ()
fixme:wininet:InternetSetOPtionW Option INTERENET_OPTION_CONTEXT_VALUE; Stub
fixme:wininet:InternetSetOPtionW Option INTERENET_OPTION_CONTEXT_VALUE; Stub
fixme:wininet:InternetSetOPtionW Option INTERENET_OPTION_CONTEXT_VALUE; Stub
```

Now, this may not be 100% accurate, but its the best I could come up with. It looks like I'm back to the 'ol drawing board. 

p.s. here is a link to the card I bought. The only reason I bought this piece first was because I read the description wrong and thought it would fit into the PCI slots in my current computer. Obviously I was wrong, so now its just sitting around waiting for all the other pieces to be orderd and slapped together. [***Click Me!***]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130395")

---

### Post by asdfoo on 2009-10-06
> **Grukmuck said:**
> Here is another long awaited update of my issues with Wine, lol.

I haven't really had time to try any other apps in Wine to see if I'm having a configuration problem. So I've just been trying to figure out if it's a hardware problem. 

The problem so far: I can open WoW and long into my account and make it as far as the character selection/creation screen. Once I create or choose a character to enter the world with my system freezes. I cant move my mouse or anything. Though the music keeps playing. I have to do a hard reset to get back to my desktop. I followed the instruction for integrated Intel Graphics chips [***here***]("http://ubuntuforums.org/showthread.php?t=1130582"). The only noticeable difference after follow the instructions was that I can move my mouse cursor. I still have to do a hard reset to get out of it. Since that didn't work, I ran WoW from the terminal to see what it said. I didn't even make past the account log in before my system froze.

This part was the most fun. Since I couldn't read the terminal due to the freeze, I had to set it to 'always on top' and physically write down the info it was spitting out. I had to do it twice to get the top half and the bottom half. This is what it said:

```
brian@Mosheen:~$ '/home/brian/.wine/dosdevices/c:/Program Files/World of Warcraft/Wow.exe' 
get fences failed: -1
param: 6, val: 0

```

Now, this may not be 100% accurate, but its the best I could come up with. It looks like I'm back to the 'ol drawing board. 

p.s. here is a link to the card I bought. The only reason I bought this piece first was because I read the description wrong and thought it would fit into the PCI slots in my current computer. Obviously I was wrong, so now its just sitting around waiting for all the other pieces to be orderd and slapped together. [***Click Me!***]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130395")

If your system freezes it's a problem with the video drivers rather than Wine itself.  A common occurrence with Intel and ATI.

Just a note also, you should cd to the install directory and then run programs when you use Wine as this is how it works on Windows when you run a shortcut to the program or double click on the file in explorer.

---

### Post by Grukmuck on 2009-10-08
I followed the guide on integrated intel cards, but that didnt help, and neither did the WINE wiki. so is there anything else I can try to get this problem solved? Or is there any other info you need from me to help determine exactly what the problem is and how to fix it?

-Gruk

---

