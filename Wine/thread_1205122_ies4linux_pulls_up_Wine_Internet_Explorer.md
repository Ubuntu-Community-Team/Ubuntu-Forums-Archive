---
title: "ies4linux pulls up Wine Internet Explorer?"
date: 2009-07-05
forum: Wine
---

### Post by Jesdisciple on 2009-07-05
I just tried using ies4linux for the first time since I reinstalled, and it gives me a Wine Internet Explorer window with a title bar and the WineHQ homepage...  No address bar or any functionality at all except links and textual highlighting...  I'm certain that this isn't the intended behavior because it's useless for web development; it's like a Wine-specific help-browser.

Help, please?

EDIT: By the way, I didn't come straight here.  Google wasn't very helpful, and neither was the ies4linux faq.

---

### Post by ackanao on 2009-07-05
It shouldn't behave like that - when you start IE it should take you to ies4linux homepage; Tell me exactly what you did to install IE with ies4linux?

---

### Post by aysiu on 2009-07-05
It is intentional to run Internet Explorer using Wine, but it should have an address bar.

---

### Post by Jesdisciple on 2009-07-05
Well, it's been a while since I did it, but I took all IE versions and left Flash off [because...]("http://ubuntuforums.org/showthread.php?t=1194316")  Should I un- and re-install to get the exact CLI output?

---

### Post by ackanao on 2009-07-05
Here's how to install IE wit ies4linux:

Extract ies4linux-latest.tar.gz

Start terminal and goto ies4linux extracted folder:
```
cd ies4linux-*
```

If you have nautilus-open-terminal installed, right-click on a folder and chose "Open In Terminal"

Start ies4linux and follow instructions:
```
./ies4linux
```

You'll see an IE shortcut on your desktop.

Delete "bin" and ".ies4linux" folder and then try again.

---

### Post by Jesdisciple on 2009-07-05
```
$ ./ies4linux
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

**
Gtk:ERROR:/build/buildd/gtk+2.0-2.16.1/gtk/gtktextview.c:3519:gtk_text_view_validate_onscreen: assertion failed: (text_view->onscreen_validated)
ui/pygtk/python-gtk.sh: line 6:  6452 Aborted                 python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py
$ ./ies4linux
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

/home/coder/ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py:268: GtkWarning: gtk_text_layout_real_invalidate: assertion `layout->wrap_loop_count == 0' failed
  self.textbuffer.insert_with_tags(self.textbuffer.get_end_iter(), line, tag)
/home/coder/ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py:399: GtkWarning: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
You can apply tags and insert marks without invalidating your iterators,
but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)
will invalidate all outstanding iterators
  gtk.main()
ui/pygtk/python-gtk.sh: line 6:  7746 Segmentation fault      python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py
```

---

### Post by ackanao on 2009-07-05
I think I know why you're getting this errors; First I've tried to install IE and Flash with Wine 1.1.25 installed on my system and it fails.

Then I've tried with 1.0.1 version of Wine and IE and Flash installs just fine. 

So, uninstall Wine, delete .wine folder and anything related to Wine in "/.config/menus/aplications-merged" folder. Install "stable" Wine version and then try again. Hope this helps...

*It seems that Flash do not work - although I didn't have problems installing it.*

---

### Post by Jesdisciple on 2009-07-05
On my first try, I kept Flash selected and got the same rundll error, and had to kill the installer.  Then I tried it without Flash and got an identical notice regarding wineboot; the installer went gray immediately (before I killed it, unlike last time).

Should I be doing any cleanup between failed installations?

Thanks.

---

### Post by ackanao on 2009-07-05
I think you need to. 

Delete "bin" folder or IE script in it, delete .ies4linux folder;

Uninstall Wine and wine-gecko, delete .wine folder and anything related to Wine in "~/.config/menus/application-merged" folder;

Install Wine 1.0.1 and then try again - as I said IE and Flash installs without problems with Wine 1.0.1 installed on my system but it seems that Flash does not work.

---

### Post by Jesdisciple on 2009-07-05
Well, I found part of the problem...  Running from the command line (ie7 in this case) opens ies4linux, but using the iexplore.exe in ~/.ies4linux/ie*/drive_c/Program Files/Internet Explorer opens the ordinary Wine Internet Explorer with no toolbars.

As for the mostly working method (calling ie7 from the CLI), I get that same GUI error about a program not working for IEXPLORE.EXE - right after a notice about a privacy icon and cookies.  Then the page keeps loading, and the progress bar goes a lot slower than the initial one.

=\

---

### Post by ackanao on 2009-07-05
Sorry I haven't tested IE7 installation and it looks like it's really buggy with ies4linux. Take a look at this page maybe it's better to do it that way:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4195]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4195")

---

### Post by Jesdisciple on 2009-07-06
Umm...> Doesn't show any page
...
Internet Explorer, but it will not be possible to view any page with it.

Also, I ran IE 6 and had to kill my computer because it locked (after having it open for a while).  Is this just one of those semi-expected hazards that come with the territory?

Thanks again.

---

### Post by ackanao on 2009-07-06
> **Jesdisciple said:**
> Umm...

Also, I ran IE 6 and had to kill my computer because it locked (after having it open for a while).  Is this just one of those semi-expected hazards that come with the territory?

Thanks again.

Yes after a while IE6 turns to zombie process and you have to kill it or it will lock your computer.

Did you read the last post by jim burns on appdb page - follow his suggestions, maybe will work for you too...

---

### Post by Jesdisciple on 2009-07-06
Oh...  So should I uninstall IEs4Linux before trying that solution?

I also have no clue how to mess with DLLs, or what difference is between builtin and native.  And where would I get a DLL that's not automatically installed by Wine?  I don't have a Win install anymore (except at my parents').

[http://ftp.winehq.org/pub/wine/docs/en/wineusr-guide.html#WINECFG-DLL-OVERRIDES]("http://ftp.winehq.org/pub/wine/docs/en/wineusr-guide.html#WINECFG-DLL-OVERRIDES")

---

### Post by ackanao on 2009-07-06
You don't need to uninstall ies4linux.

OK. Installing IE 7 can (and probably will) break your Wine installation so it's better to create new wineprefix for IE.

To create new wineprefix, use this command:

```
WINEPREFIX=~/Desktop/IE wineboot
```
*This will create IE wineprefix on Desktop - use another path if you want*

To Install IE7, type this command:
```
env WINEPREFIX=~/Desktop/IE wine /path/to/IE/Installer/IE7_Setup.exe
```
*follow jim burns suggestions about this*

Download winetricks:
```
wget http://www.kegel.com/wine/winetricks
```

And use this command to install what is needed for IE7:
```
WINEPREFIX=~/Desktop/IE sh winetricks msxml3 msxml4
```

Use this command to start IE7:
```
env WINEPREFIX=~/Desktop/IE wine "C:\Program Files\wherever_it_is\IE.exe"
```

About overrides:
There's only one dll you need to download from internet - actxprxy. Here's the link: [http://www.dlldump.com/]("http://www.dlldump.com/")

To override mentioned dll's, use this command:
```
WINEPREFIX=~/Desktop/IE winecfg
```

Goto Libraries tab and in the "New override for library" textbox type the name for the dll file you want to override - For example:

To override **mshtml.dll** just type **mshtml** (without ".dll") and click "Add"

For **actxprxy.dll**, you need to copy it first to system32 directory.

If you still having problems let me know - I'll try to install it myself and post my results.

---

### Post by Jesdisciple on 2009-07-06
> **ackanao said:**
> To create new wineprefix, use this command:

```
WINEPREFIX=~/Desktop/IE wineboot
```Several modules were not found; I'm not sure if this is a problem or just Wine's beta status.

> **ackanao said:**
> *This will create IE wineprefix on Desktop - use another path if you want*So for this 'sandbox' application of WINEPREFIX, it works as a parameter rather than a permanent env var, correct?

When I ran it, I got the usual GUI boilerplate about iexplore.exe.

It may be significant that I forgot and put actxprxy in the config dialog first.  When I moved it to system32, Nautilus said one already existed so I replaced it.  However, I did move it before clicking OK.

---

### Post by ackanao on 2009-07-06
> Several modules were not found; I'm not sure if this is a problem or just Wine's beta status.

I think this is OK. - you didn't posted full terminal output so I can't say for sure.

> So for this 'sandbox' application of WINEPREFIX, it works as a parameter rather than a permanent env var, correct?

It is environment variable.

I don't understand last part of your post - is IE7 installed or not and what happens when you run it? 

(sorry for my bad english...)

---

### Post by Jesdisciple on 2009-07-06
Yeah, IE7 is installed, but running it gives this notice in a GUI dialog:[QUOTE=Program Error]The program iexplore.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.[/QUOTE]Also, the console hung when I closed IE, even after Ctrl+Z and Ctrl+C and Ctrl+V (keys which exit when I don't want them to) so I had to close it.

Heh, you really think I mind English errors while you assist me?  ;)  I'm glad to get the help.

---

### Post by ackanao on 2009-07-06
OK. I'll try to install it myself. I'll let you know how it goes.

---

### Post by Jesdisciple on 2009-07-06
I just remembered that I didn't restart when it told m to, but doing so didn't help.  I'll have to try again tomorrow; should I empty the prefix directory first?

---

### Post by ackanao on 2009-07-07
Jesdisciple,

It's working and is really easy to make it work.

I'll start from begining (Delete old IE wineprefix and create a new one):

Create a new wineprefix for IE7:
```
WINEPREFIX=~/Desktop/IE wineboot
```

Download winetricks:
```
wget http://www.kegel.com/wine/winetricks
```

Use winetricks to install necessary stuff:
```
WINEPREFIX=~/Desktop/IE sh winetricks comctl32 comctl32.ocx corefonts gdiplus gecko msls31 msxml3 msxml4 msxml6 riched20 riched30 tahoma
```

Now, copy this into your texteditor and save it as **ie7.reg**
```

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"browseui"="native,builtin"
"comctl32"="builtin"
"crypt32"="native,builtin"
"gdiplus"="native"
"hhctrl.ocx"="native,builtin"
"hlink"="native,builtin"
"iernonce"="native,builtin"
"iexplore.exe"="native,builtin"
"itircl"="native,builtin"
"itss"="native,builtin"
"jscript"="native,builtin"
"mlang"="native,builtin"
"mshtml"="native,builtin"
"msimtf"="native,builtin"
"msxml3"="native,builtin"
"riched20"="native,builtin"
"riched32"="native,builtin"
"secur32"="native,builtin"
"shdoclc"="native,builtin"
"shdocvw"="native,builtin"
"shlwapi"="native,builtin"
"url"="native,builtin"
"urlmon"="native,builtin"
"usp10"="native,builtin"
"uxtheme"="native,builtin"
"wininet"="builtin"
"wintrust"="native, builtin"

```

Now import ie7.reg - this will set-up needed dlloverrides:
```
WINEPREFIX=~/Desktop/IE regedit /home/Jesdisciple/Desktop/ie7.reg
```

Install IE7:
```
env WINEPREFIX=~/Desktop/IE wine /path/to/IE/Installer/IE7_Setup.exe
```

Run IE7:
```
env WINEPREFIX=~/Desktop/IE wine "C:\Program Files\Internet Explorer\iexplore.exe"
```

Don't know for Flash or ActiveX but webpage navigation seems to work.

*I'm using the latest version of Wine (1.1.25)*

---

### Post by Jesdisciple on 2009-07-07
This time I told it to Restart Now after IE's installation and it said:[QUOTE=Program Error]The program services.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.[/QUOTE]

Here's what showed in the console, with the initial fixme notice (everything before the unhandled exception) appearing about a hundred times:```
fixme:shell:DllGetClassObject failed for CLSID={a07034fd-6caa-4954-ac3f-97a27216f98a} (Query file associations)
err:ole:CoCreateInstance apartment not initialised
err:shell:SHCoCreateInstance failed (0x800401f0) to create CLSID:{a07034fd-6caa-4954-ac3f-97a27216f98a} (Query file associations) IID:{c46ca590-3c3f-11d2-bee6-0000f805ca57} (unknown)
err:shell:SHCoCreateInstance class not found in registry
Unhandled exception: page fault on read access to 0x00000189 in 32-bit code (0x7ee22ef0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ee22ef0 ESP:0074e9d0 EBP:0074ea38 EFLAGS:00210206(  R- --  I   - -P- )
 EAX:00000189 EBX:7ee3cff4 ECX:00000000 EDX:00113f10
 ESI:00114400 EDI:00113f10
Stack dump:
0x0074e9d0:  00113f7c 706e5f6e 00114800 00000000
0x0074e9e0:  00000002 00114b18 0074ea38 7bc44830
0x0074e9f0:  00110058 0074ea40 00000004 0074ea80
0x0074ea00:  00000000 7bc9db20 0074ea38 7bc94ff4
0x0074ea10:  001149a8 00110000 00000002 7bc34f61
0x0074ea20:  00000001 0074ea40 00000000 7bc94ff4
Backtrace:
=>0 0x7ee22ef0 in rpcrt4 (+0x42ef0) (0x0074ea38)
  1 0x7bc7771d in ntdll (+0x6771d) (0x0074ea98)
  2 0x7bc6b6d8 call_thread_func+0xc() in ntdll (0x0074eaa8)
  3 0x7bc6b8e0 call_thread_entry_point+0x70() in ntdll (0x0074eb78)
  4 0x7bc73a5b in ntdll (+0x63a5b) (0x0074f3b8)
  5 0xb7da44ff start_thread+0xbf() in libpthread.so.0 (0x0074f4b8)
  6 0xb7d1e49e __clone+0x5e() in libc.so.6 (0x00000000)
0x7ee22ef0: movl	0x0(%eax),%eax
Modules:
Module	Address			Debug info	Name (22 modules)
ELF	7b800000-7b954000	Deferred        kernel32<elf>
  \-PE	7b820000-7b954000	\               kernel32
ELF	7bc00000-7bcb1000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ed71000-7ed80000	Deferred        libgcc_s.so.1
ELF	7ed80000-7edd6000	Deferred        advapi32<elf>
  \-PE	7ed90000-7edd6000	\               advapi32
ELF	7edd6000-7ee43000	Export          rpcrt4<elf>
  \-PE	7ede0000-7ee43000	\               rpcrt4
ELF	7ee43000-7ee66000	Deferred        services<elf>
  \-PE	7ee50000-7ee66000	\               services
ELF	7ee66000-7ee72000	Deferred        libnss_files.so.2
ELF	7ee72000-7ee8b000	Deferred        libnsl.so.1
ELF	7ee8b000-7ee94000	Deferred        libnss_compat.so.2
ELF	7efcc000-7eff2000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c36000-b7c3a000	Deferred        libdl.so.2
ELF	b7c3a000-b7d9d000	Export          libc.so.6
ELF	b7d9e000-b7db7000	Export          libpthread.so.0
ELF	b7dc5000-b7f01000	Deferred        libwine.so.1
ELF	b7f03000-b7f21000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000002c (D) C:\windows\system32\services.exe
	00000041    0 <==
	00000040    0
	0000002a    0
	0000002b    0
0000003d 
	00000039    0
	0000003b    0
	0000003f    0
	0000003e    0
Backtrace:
=>0 0x7ee22ef0 in rpcrt4 (+0x42ef0) (0x0074ea38)
  1 0x7bc7771d in ntdll (+0x6771d) (0x0074ea98)
  2 0x7bc6b6d8 call_thread_func+0xc() in ntdll (0x0074eaa8)
  3 0x7bc6b8e0 call_thread_entry_point+0x70() in ntdll (0x0074eb78)
  4 0x7bc73a5b in ntdll (+0x63a5b) (0x0074f3b8)
  5 0xb7da44ff start_thread+0xbf() in libpthread.so.0 (0x0074f4b8)
  6 0xb7d1e49e __clone+0x5e() in libc.so.6 (0x00000000)
```

---

### Post by ackanao on 2009-07-07
I really don't know what you're doing wrong - do me a favour and:

Uninstall Wine:
```
sudo apt-get --purge autoremove wine
```

Delete "~/.wine" folder

Enabe WineHQ repositories:
[http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

Install Wine:
```
sudo apt-get install wine
```

And try again... There's even easier way to install IE7 but I think that your Wine is somehow messed up so you need to fix this first.

---

### Post by Jesdisciple on 2009-07-07
Well, that helped a little bit.

Installing, everything seemed to go fine, but the terminal hung.  Interrupting with Ctrl+C worked.

Running, I got this twice:> Cannot find 'about:Security Risk'.  Make sure the path or Internet address is correct.

Using, I get this no matter where I try to go:> Windows cannot find 'http://www.example.com/'.  Check the spelling and try again.

---

### Post by ackanao on 2009-07-07
OK. I want to check something - delete IE wineprefix and .wine folder; then run "winecfg" and post full terminal output. Also, could you try this IE installer - this is the one I use (it's legit so you don't have to worry about that):

[http://www.softpedia.com/get/Internet/Browsers/Internet-Explorer-7.shtml]("http://www.softpedia.com/get/Internet/Browsers/Internet-Explorer-7.shtml")

Which version of Wine do you use?

---

### Post by Jesdisciple on 2009-07-07
I got the prefix deleted, but when I went to delete .wine it wasn't there.  So, after winecfg made .wine, I tried installing IE7 the long way again - and it worked!

Thanks for your patience!

Anyway, here are the version and output you asked for.  Note that I didn't delete the prefix because it's finally working. =P```
$ wine --version
wine-1.1.25
$ winecfg
wine: created the configuration directory '/home/coder/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cf94
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x33c960 (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0x60ae908, overlapped 0x60ae910): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x33ca50 (nil)
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[194778]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
fixme:shell:DllCanUnloadNow stub
get fences failed: -1
param: 6, val: 0
wine: configuration in '/home/coder/.wine' has been updated.
```

---

### Post by ackanao on 2009-07-07
So we can tag this thread as "solved"! I'm glad you finally did it!

Now, do you want to know the easier way to install IE7 - it only takes few clicks...

OK. You can use PlayOnLinux to install IE7 - here's the POL's homepage:
[http://www.playonlinux.com/en/]("http://www.playonlinux.com/en/")

When you run it click on "Install" button, goto "Internet" section, click on "Internet Explorer 7" and then click "Apply".

It's a very useful frontend for Wine and I think it will serve you well.

I'm a bit troubled with last lines in your terminal output:

```

get fences failed: -1
param: 6, val: 0

```

... but it doesn't matter as long as your Wine and IE works well. :p

---

### Post by Jesdisciple on 2009-07-07
Unfortunately, they removed the "solved" and "thanks" features a while back...  :(  I've been missing them.  (I edited the original post's title just in case, but it's not reflected in the forum index.)

> I'm glad you finally did it!You are waaayy too kind, but you know that.

I tend to refer back to my threads a lot, so I'll look at POL next time I need something from Windows.  Meanwhile, I already remember the pain caused by cross-browser testing...  *sigh*

---

### Post by ackanao on 2009-07-07
OK. Cheers Jesdisciple! I'm really glad we solved your IE problem; cross-browser testing should be easier now (I think) - please don't ask me how to install Safari via Wine... :p

---

### Post by Jesdisciple on 2009-07-07
*idea*  Oh, yeah.  I remember that I had trouble with that on my last install; I'll see if it will work this time...

---

### Post by Jesdisciple on 2009-07-07
Safari seemed way easier, but maybe that was because of my bad wine.  I checked POL as I concluded the installation...  Maybe I'll remember sooner next time.  [http://www.playonlinux.com/repository/?script=118](http://www.playonlinux.com/repository/?script=118)

I managed it by following [this]("http://alicious.com/2009/safari-4-on-linux-with-wine-update/") guide,  along with an extra command from the comments [here]("http://phorolinux.com/how-to-run-safari-in-linux-using-wine.html").  The command is:```
winetricks vcrun2005
```(I also used a separate prefix for Safari.)

---

### Post by kickwin on 2009-08-18
I have IE6 installed using ies4linux. As some have mentioned before, I do not see any address bar. I tried what is given [here]("http://ubuntuforums.org/showpost.php?p=4158076&postcount=17") but it doesn't work for me. I am afraid to go through the hassle of fixing it the right way but is there any shortcut (say, by modifying ie/wine installation files) to change the homepage of ie to google.com? The homepage now is winehq.org.

---

### Post by Jesdisciple on 2009-08-19
Hi Kickwin.  As Ackanao may not be familiar with that detail of IE (nor with IE6 in general), I suggest that you make a new thread.

As an aside, I'm not sure what "the right way" is in your mind but you might try manually installing IE6 (definitely in its own prefix).  With the correct DLLs etc., it just might work great on Wine.  However, Wine *is* still in beta and the correct downloads may be elusive.

EDIT: Oh, also...  [http://www.playonlinux.com/repository/?script=120](http://www.playonlinux.com/repository/?script=120)

---

### Post by kickwin on 2009-08-21
> **Jesdisciple said:**
> Hi Kickwin.  As Ackanao may not be familiar with that detail of IE (nor with IE6 in general), I suggest that you make a new thread.

As an aside, I'm not sure what "the right way" is in your mind but you might try manually installing IE6 (definitely in its own prefix).  With the correct DLLs etc., it just might work great on Wine.  However, Wine *is* still in beta and the correct downloads may be elusive.

EDIT: Oh, also...  [http://www.playonlinux.com/repository/?script=120](http://www.playonlinux.com/repository/?script=120)

Thanks a lot for the link. I was able to change my homepage to google.com. It solved my problem partially but I will have to do a complete reinstallation.

---

### Post by balaji31d on 2011-02-08
Thanks.. This thread helped to solve my issue with IE

---

### Post by Geremia on 2011-04-09
> **ackanao said:**
> I'll start from beginingThank you very much! I had to "start from begining," too. Thank you

---

