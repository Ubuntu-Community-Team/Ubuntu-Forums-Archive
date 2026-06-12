---
title: "Dreamweaver worked in Lucid 32bit but not in 64bit"
date: 2010-06-18
forum: Wine
---

### Post by charonred on 2010-06-18
I had Dreamweaver running in Wine in Lucid 32 bit; but now I've moved to Lucid 64bit (clean install) it installed fine, and attempts to start, but then just stops - any ideas how to fix this? 

I use Dreamweaver a fair bit, and I really don't want to have to do a clean install of 32bit Lucid if there's a fix to get it working in 64bit. I went to 64bit because it handles memory better and I intend adding another 4Gb to the existing 4Gb.

---

### Post by asdfoo on 2010-06-18
> **charonred said:**
> I had Dreamweaver running in Wine in Lucid 32 bit; but now I've moved to Lucid 64bit (clean install) it installed fine, and attempts to start, but then just stops - any ideas how to fix this? 

I use Dreamweaver a fair bit, and I really don't want to have to do a clean install of 32bit Lucid if there's a fix to get it working in 64bit. I went to 64bit because it handles memory better and I intend adding another 4Gb to the existing 4Gb.

I'm thinking the difference might be the Wine version you were using prior.

The most recent beta available from winehq.org is 1.2-rc4 which I suggest you try out and report back.

---

### Post by charonred on 2010-06-18
I'm using Wine 1.1.42, so I'll look into 1.2-rc4

---

### Post by charonred on 2010-06-18
I added the repository for Ubuntu ppa:ubuntu-wine/ppa and ran Update manager; it installed Wine 1.2-rc3, but still have same problem, Dreamweaver attempts to start, but then stops.

For the moment I have Dreamweaver working in Virtualbox Windows XP and using my Vbox shared folders ... not an ideal solution, but at least I can use DW.

---

### Post by asdfoo on 2010-06-18
Does it give any indication of what might be wrong in the terminal output?

eg. if you cd to the install directory and then run the main executable?

[http://wiki.winehq.org/FAQ#head-8d8c06cf7fb33269c085a07531b61e5c730566e0](http://wiki.winehq.org/FAQ#head-8d8c06cf7fb33269c085a07531b61e5c730566e0)

---

### Post by charonred on 2010-06-19
this what I get from Terminal
```
~$ wine start "C:\Program Files\Macromedia\Dreamweaver MX 2004\Dreamweaver.exe" 
fixme:exec:SHELL_execute flags ignored: 0x00000100
:~$ err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Macromedia\\Dreamweaver MX 2004\\Dreamweaver.exe" failed, status c0000005

```

---

### Post by asdfoo on 2010-06-20
> **charonred said:**
> this what I get from Terminal
```
~$ wine start "C:\Program Files\Macromedia\Dreamweaver MX 2004\Dreamweaver.exe" 
fixme:exec:SHELL_execute flags ignored: 0x00000100
:~$ err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Macromedia\\Dreamweaver MX 2004\\Dreamweaver.exe" failed, status c0000005

```

I'm not sure why it's not working out of the box, but you can try installing native odbc using the following two commands:

# first download winetricks:
wget kegel.com/wine/winetricks
# then tell winetricks to download and install mdac25
sh winetricks mdac25

---

### Post by charonred on 2010-06-20
Champion ... Dreamweaver works; strange I didn't have to do that in 32bit Lucid, but at least it works now :p

Many many thanks

---

### Post by charonred on 2010-07-08
updated Wine the other day through Update Manager (as prompted), now Dreamweaver won't start again - how do I get it to work again ?

thought I'd try this script again, but this is what I got
```
sh winetricks mdac25
err:service:validate_service_config Service L"Mountrgrv" has an unknown service type
err:service:scmdatabase_load_services Invalid configuration of service L"Mountrgrv" - skipping
wine: Install the Windows version of Mono to run .NET executables
err:process:__wine_kernel_init boot event wait timed out

```

---

### Post by asdfoo on 2010-07-08
> **charonred said:**
> updated Wine the other day through Update Manager (as prompted), now Dreamweaver won't start again - how do I get it to work again ?

thought I'd try this script again, but this is what I got
```
sh winetricks mdac25
err:service:validate_service_config Service L"Mountrgrv" has an unknown service type
err:service:scmdatabase_load_services Invalid configuration of service L"Mountrgrv" - skipping
wine: Install the Windows version of Mono to run .NET executables
err:process:__wine_kernel_init boot event wait timed out

```

well, mdac25 is already installed if you haven't removed your wine prefix.

what's the terminal output when you try to start dreamweaver?

---

### Post by charonred on 2010-07-08
how do I start Dreamweaver in Terminal

this is the desktop command
```
env WINEPREFIX="/home/johnno/.wine" wine "C:\Program Files\Macromedia\Dreamweaver MX 2004\Dreamweaver.exe" 
``` but it doesn't do anything if I paste into terminal

---

### Post by jinlongyu85 on 2010-07-09
i think 64bit is better.why canot use? thanks

---

### Post by charonred on 2010-07-09
I'm using 64bit cause it is better; but Dreamweaver won't run in it again for some reason since doing usual Updates.

---

### Post by asdfoo on 2010-07-09
> **charonred said:**
> how do I start Dreamweaver in Terminal

this is the desktop command
```
env WINEPREFIX="/home/johnno/.wine" wine "C:\Program Files\Macromedia\Dreamweaver MX 2004\Dreamweaver.exe" 
``` but it doesn't do anything if I paste into terminal

sorry for the late reply, been busy, this should do it:

cd ~/.wine/drive_c/Program\ Files/Macromedia/Dreamweaver\ MX\ 2004/
wine Dreamweaver.exe

---

### Post by charonred on 2010-07-10
this is what I get
```
err:service:validate_service_config Service L"Mountrgrv" has an unknown service type
err:service:scmdatabase_load_services Invalid configuration of service L"Mountrgrv" - skipping
wine: Install the Windows version of Mono to run .NET executables
```

---

### Post by asdfoo on 2010-07-10
> **charonred said:**
> this is what I get
```
err:service:validate_service_config Service L"Mountrgrv" has an unknown service type
err:service:scmdatabase_load_services Invalid configuration of service L"Mountrgrv" - skipping
wine: Install the Windows version of Mono to run .NET executables
```

Well, the last line suggests that it's asking for .NET to be installed, you can do that with winetricks dotnet20

I don't know what the reason is, have you installed any other software? 
Did you originally have dotnet20 installed to run dreamweaver?

Alternatively, you could try removing/moving your wine prefix, reinstalling dreamweaver, mdac25 and then see if it starts, which will be my next answer if winetricks dotnet20 doesn't work.

---

