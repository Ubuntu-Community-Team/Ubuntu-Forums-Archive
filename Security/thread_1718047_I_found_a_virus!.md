---
title: "I found a virus!"
date: 2011-03-30
forum: Security
---

### Post by victorhugo289 on 2011-03-30
Hi, I hope you can help me.

Recently I've been finding two strange-looking files on my Windows shared folders! Their names are 'khy' and 'qffhtx.exe', they appear as hidden, and they're hard to delete!! especially the first one because it has no extension.
I use Ubuntu 10.10, but I am worried because I also dual-boot Windows XP.

Today I tried to open the .exe file in nautilus to see what is inside and I received the message "Unable to open archive", 'khy' is apparently an empty text file.

Then I unmounted my /home partition so my files are out of the way,
and I ran the .exe file using WINE,

Now I have a strange-looking applet on my top panel!! and it says "Script paused", also it says "Exit', and also Wine command prompt says something strange about "LockWindowUpdate", don't imagine it I'll post the screenshots so you can see it for yourselves. Also --and this is weird-- the virus apparently is trying to call a Windows process named csrcs.exe!! Again, I'll post the screenshots.

If this is a virus, then it's like a fish out of the water on my Ubuntu, it's probably trying to do something but it can't find its way around, it's kinda funny, but Im worried because I also dual-boot Windows XP, please help!!!

Believe me, I'm having a hard time trying to remember the name KHY, it's a very weird acronym, it's the acronym of a disease, according to what I googled, i'm sure it's a virus!!! Anyway it's HARD to remember!!!


-------what can I do about this? How can I see the "script"? 
-------can Ubuntu kick its ***?
-------how can I clean my Windows?

Here are the screenshots, please help:
(I am not clicking on the images, I'm just pointing with the mouse)

Thanks.

---

### Post by mmsmc on 2011-03-30
.exe files will not run on linux thats why you get that waring, is this affecting your system, is  your computer slow, are there unusual processes running, are you getting pop ups of your system asking to run as root

---

### Post by uRock on 2011-03-30
Have you tried deleting it via cli?```
man rm
```

---

### Post by alphacrucis2 on 2011-03-30
> **victorhugo289 said:**
> Hi, I hope you can help me.

Recently I've been finding two strange-looking files on my Windows shared folders! Their names are 'khy' and 'qffhtx.exe', they appear as hidden, and they're hard to delete!! especially the first one because it has no extension.
I use Ubuntu 10.10, but I am worried because I also dual-boot Windows XP.

Today I tried to open the .exe file in nautilus to see what is inside and I received the message "Unable to open archive", 'khy' is apparently an empty text file.

Then I unmounted my /home partition so my files are out of the way,
and I ran the .exe file using WINE,

Now I have a strange-looking applet on my top panel!! and it says "Script paused", also it says "Exit', and also Wine command prompt says something strange about "LockWindowUpdate", don't imagine it I'll post the screenshots so you can see it for yourselves. Also --and this is weird-- the virus apparently is trying to call a Windows process named csrcs.exe!! Again, I'll post the screenshots.

If this is a virus, then it's like a fish out of the water on my Ubuntu, it's probably trying to do something but it can't find its way around, it's kinda funny, but Im worried because I also dual-boot Windows XP, please help!!!

Believe me, I'm having a hard time trying to remember the name KHY, it's a very weird acronym, it's the acronym of a disease, according to what I googled, i'm sure it's a virus!!! Anyway it's HARD to remember!!!


-------what can I do about this? How can I see the "script"? 
-------can Ubuntu kick its ***?
-------how can I clean my Windows?

Here are the screenshots, please help:
(I am not clicking on the images, I'm just pointing with the mouse)

Thanks.

You could install an anti virus program in Ubuntu such as Avast and try scanning the windows partition. If that doesn't help then you could try downloading the Malwarebytes anti malware Windows installer and then copy it to the Windows partition. Reboot into Windows safe mode and install Malwarebytes and scan.

---

### Post by victorhugo289 on 2011-03-30
> **mmsmc said:**
> .exe files will not run on linux thats why you get that waring, is this affecting your system, is  your computer slow, are there unusual processes running, are you getting pop ups of your system asking to run as root

1. I know .exe files do not run on Ubuntu, that is why I used WINE. By running this .exe file on Wine here on Ubuntu I feel a lot safer.

2.  I haven't noticed any slowdown on my Windows XP --I dual-boot-- I am experiencing no problems whatsoever, but these files are evil, they must be doing something, they keep the host alive for a reason.

3. I don't have any Anti-virus or Anti-malware on Windows XP, I just use Zone Alarm free firewall.

---

### Post by mmsmc on 2011-03-30
if there is no problem with xp than do not worry about it, the script may still be running, but it says the text file is empty so it is not running anything really, not sure how to delete it try doing what uRock says

---

### Post by victorhugo289 on 2011-03-30
Why does it say "Script paused"?
How can I "read" the .exe file so I know what's the script all about??

> **uRock said:**
> Have you tried deleting it via cli?```
man rm
```

I'll do that of course, I'll search the Windows partition for the names and remove them.

---

### Post by victorhugo289 on 2011-03-30
Whoa! I found something else!! Look what it's trying to do!!

---

### Post by SeijiSensei on 2011-03-30
WINE is a great environment for testing suspicious files like this.  Just make sure you've backed up your $HOME/.wine directory first so you can restore if after testing.

I'm guessing you ran a program that tried to run a script that works in Windows, but that WINE refuses to execute.  I've seen this before. 

Your best method to "blow away" anything the malware might have left behind is to move $HOME/.wine to $HOME/.wine.old just to be safe, then starting over with WINE.  You'll have to reinstall Windows programs like Office, just as you would if you had a brand-new Windows machine.  That's why you want to keep a backup of the .wine directory.

If you've ever backed up your home directory, try using the copy of .wine that's stored there and see what you have.

That LockWindowsUpdate call probably does what it says, locks the Window Update program from running while the malware is active.  WINE, of course, cares not at all about Windows Update and doesn't provide a handler for that call.  Good for it and you.

---

### Post by cariboo on 2011-03-30
You could try running strings on the file eg:

```
strings qffhtx.exe
```

the command will echo back all the text strings it finds in the file, it's more than like a compiled executable created using VB.

---

### Post by victorhugo289 on 2011-03-30
> **cariboo907 said:**
> You could try running strings on the file eg:

```
strings qffhtx.exe
```the command will echo back all the text strings it finds in the file, it's more than like a compiled executable created using VB.

COOL, it output a lot of text!

```

N}z}S
|&MY
Nxfu
~IELL
K++6
DJ)j
6SMx
D1sO
Dg:59
#+rG
Bk]h
tjP    !j
^i@7
cI)B
Bkx9
k]C.%
s8==
... 
PJ)c
k#~I
XmMT0#
|)Ax
WJIh
v2h'
R^@[
<OA{1;
dRJ*
eYzEQ
|~\7
EIDAT
m)em
P)%m
u]7RJE
uppp
vkkk
jwww
yE    (
lWQi
chG    X
nRIX
2TWq
IEND
PA`=
                
       
'            /
>>>j
F            2
;;;    ;;;
8            7
222p
9            0            *
:AAA
++0l
b%%%p222|<<<
===    >>>
222 222 222 111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!111!///",,,$(((&###+
Iggg
k&&&w111
+++e
;;;!:::$999'888(666*444-222.111/00000000///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///1///2...2+++4)))7%%%;!!!@
Wqqq
777x
;;;%;;;+:::/999388866669333<222>000@///A///B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B...B---C,,,D+++F(((I%%%M!!!T
["""
<<<'<<</<<<5;;;:999?888B666F333I111M///O...Q...R---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---S---T+++U***W)))Y%%%^
oaaa
<<<#===-<<<6<<<=;;;C:::H?=<NPPE^_\Lj`\Lq]ZJt\YIv[XHx[XHx[XHx[XHy[XIy[XIy[XIy[XIy\XIy\XJy\YKy\YKy\YKy\ZKy\ZKy\ZLy\ZLy\ZLy\ZLy\ZMy]ZMy][My][My][Ny][Ny][Ny][Ny]\Ny^\Ny\ZNz\ZMzYWJ|VTH~RPE
===&===2===;===C<<<JNICV
>>>)===5===?===GPNFX
   [!!!J
>>>+>>>6===AED@Mywf
$$$X"""K!!!<
>>> >>>+>>>7>>>B_]Vz
&&&V$$$J###:###*"""
!!!       
>>>+>>>7>>>A
(((T&&&F%%%7%%%(&&&
>>>*>>>5>>>@
)))W***@)))2'''%)))
>>>(>>>2>>><
@@@f)))"...
>>>$>>>.>>>7
+++"111
555    333
>>>    >>>
>>> >>>(>>>1
>>>">>>(
RRRY<<<
>>>    >>>
9990>>>
>>>    >>>
fffvXXX
OOO    
```5
[[[i
pniF
YYYT
ppp^
YYYk
\\\[
ttt3>>>
                
888    666
5%%%Y
KKKs
H***Q
666$222'111)000)000)000)000)000)000)000)000)000)000)///*'''0
?OOO
;;;g
<<<+:::;?>;JA@:X?=8]>=7]>=7]>=8]>=8]>>8]?>9]?>9]?>9]?>9]?>9]>=8_983d10-~
===9[YNq
   H
AAAA
%%%E$$$
JJJM
KKK@
LLL.
5~~~
(]]]
DDEu
E'''P777]FFFjTTTuccc
ZZZy            *
;;;1<<9C:95N984P985P995P995P996P:96P:96P541UIIG
===$][Tx
>>>k
>>>#
'^^^
KKK|???hMMMo[[[zkkk
\\\z            %
DC@Dss\
@@@H$$$
rrr'
ttts
886-6640664066402203ggf
SSSs
YXVb
rrrh
fff0}}}_~~~_~~~_~~~_~~~_~~~_~~~_~~~_~~~_~~~_oooS
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    <!-- Identify the application security requirements. -->
    <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">
        <security>
            <requestedPrivileges>
                <requestedExecutionLevel
                     level="asInvoker"
                    uiAccess="false"
                />
            </requestedPrivileges>
        </security>
    </trustInfo>
    <!-- Identify the application dependencies. -->
    <dependency>
        <dependentAssembly>
            <assemblyIdentity
                type="win32"
                name="Microsoft.Windows.Common-Controls"
                version="6.0.0.0"
                language="*"
                processorArchitecture="*"
                publicKeyToken="6595b64144ccf1df"
            />
        </dependentAssembly>
    </dependency>
</assembly>
KERNEL32.DLL
ADVAPI32.dll
COMCTL32.dll
COMDLG32.dll
GDI32.dll
MPR.dll
ole32.dll
OLEAUT32.dll
PSAPI.DLL
SHELL32.dll
USER32.dll
USERENV.dll
VERSION.dll
WININET.dll
WINMM.dll
WSOCK32.dll
LoadLibraryA
GetProcAddress
VirtualProtect
VirtualAlloc
VirtualFree
ExitProcess
GetAce
ImageList_Remove
GetSaveFileNameW
LineTo
WNetGetConnectionW
CoInitialize
EnumProcesses
DragFinish
GetDC
LoadUserProfileW
VerQueryValueW
FtpOpenFileW
timeGetTime



```

---

### Post by SeijiSensei on 2011-03-30
> **cariboo907 said:**
> it's more than like a compiled executable created using VB.

Thanks, cariboo.  I don't know anything about programming for Windows, though I guessed from what I know about Windows viruses, VB seemed a likely method of development.

@victor
The stuff at the top is entirely binary; it's represented by the text you'd get if you treated each 32-bit byte as a standard character.

After that ends, you have a human-readable declaration using [XML]("http://xml.silmaril.ie/").  It appears to [interact]("http://msdn.microsoft.com/en-us/data/bb190600") with the security controls in Windows.  A quick search for "windows xml" suggests XML is often used by Microsoft in conjunction with Windows Installer.  The malware might use that to install itself into the operating system.

Following that section, there's a list of .DLL files.  These are "dynamic link libraries" that provide universal services like drawing on the screen.  Linux has tons of similar libraries in /usr/lib.

The end appears to be a list of calls the program makes to the Windows environment.  That FTPOpen call looks really dangerous.  It's probably trying to download something from a remote site that would infect a real copy of Windows.  I doubt WINE would have let that happen and, again, even if it did, you can remedy the problem by removing .wine.

---

### Post by Dutch70 on 2011-03-30
Running XP without an anti-virus??? That's kind of like crossing a major highway with your eyes closed isn't it?

You can get a good free anti-virus from here...
[[COLOR="royalblue"]http://download.cnet.com/security-starter-kit?tag=rb_content;main[/COLOR]]("http://download.cnet.com/security-starter-kit?tag=rb_content;main")

If it's resources you're concerned about, check this out...
[[COLOR="royalblue"]http://download.cnet.com/Advanced-SystemCare-Free/3000-2086_4-10407614.html[/COLOR]]("http://download.cnet.com/Advanced-SystemCare-Free/3000-2086_4-10407614.html")

---

### Post by victorhugo289 on 2011-03-30
> **SeijiSensei said:**
> WINE is a great environment for testing suspicious files like this.  Just make sure you've backed up your $HOME/.wine directory first so you can restore if after testing.

I'm guessing you ran a program that tried to run a script that works in Windows, but that WINE refuses to execute.  I've seen this before. 

Your best method to "blow away" anything the malware might have left behind is to move $HOME/.wine to $HOME/.wine.old just to be safe, then starting over with WINE.  You'll have to reinstall Windows programs like Office, just as you would if you had a brand-new Windows machine.  That's why you want to keep a backup of the .wine directory.

If you've ever backed up your home directory, try using the copy of .wine that's stored there and see what you have.

That LockWindowsUpdate call probably does what it says, locks the Window Update program from running while the malware is active.  WINE, of course, cares not at all about Windows Update and doesn't provide a handler for that call.  Good for it and you.

I umounted my /home partition before running this. It's Ubuntu alone.

Uh oh, If I have to reinstall all Windows programs... I think I'll check for a Anti-virus now, and anti-malware, I really don't want to reinstall all that stuff. Having just 1GB of ram makes me not want to install anti-virus software but I'll do it anyway.

Thanks a lot everyone, if anyone has any idea as to what this script output by "Strings" is doing please tell me, thanks.

---

### Post by uRock on 2011-03-30
Install Microsoft Security Essentials. It is free and great.

---

### Post by SeijiSensei on 2011-03-30
I recommend first installing **clamav** from the Ubuntu repositories. Then, from Ubuntu, run clamscan against the XP partition.  If you told Ubuntu to mount it at /windows or /dos during installation, then just run

```
sudo clamscan --verbose /windows | egrep -v 'OK|Scanning'
```

That limits clamscan's output to infected files, error messages, and the overall summary table at the end.

This way you can scan your Windows installation without having to boot Windows.  You'll at least know what's there and whether you should feel safe booting into XP.

You can also get commercial virus scanners that run on Linux if you want a second opinion. I don't use these, but I hear [Avast!]("http://www.avast.com/linux-home-edition") is good.

One other thing you might consider is running Windows inside a [VirtualBox]("http://www.virtualbox.org/") virtual machine.  You can create snapshot backups of VirtualBox VMs and preserve a known, clean version of Windows with all your software installed as a backup.

---

### Post by crispy_420 on 2011-03-31
Boot into your Windows system with the option of Safemode w/ Networking. Download and install [Malwarebytes]("http://www.malwarebytes.org/"). Update and scan the system, a quick scan should be fine in most cases.

Or you want to go the Linux route, try Bitdefender for Linux. It is fast and free. And most importantly it works.

Like mentioned before, AV and Windows is a must. But on another note most AV software fails to catch the newer generations of malware out there that can cripple a system. For example this recent one called "System Tool 2011" is a huge hassle to remove completely and has a nasty habit of coming back when you think you are done. If that is the case let me know and I can go into more detail.

---

### Post by The Cog on 2011-03-31
> **SeijiSensei said:**
> WINE is a great environment for testing suspicious files like this.  Just make sure you've backed up your $HOME/.wine directory first so you can restore if after testing.
Also, make sure you remove the drive mappings in wineconfig that maps Z: to /, otherwise the malware will have full access to all your files.
> That LockWindowsUpdate call probably does what it says, locks the Window Update program from running while the malware is active.
I'm not so sure about that, it's LockWindowUpdate (singular), so I think it may be more to do with manipulating the GUI. I'm guessing though.

---

### Post by SeijiSensei on 2011-03-31
> **The Cog said:**
> Also, make sure you remove the drive mappings in wineconfig that maps Z: to /, otherwise the malware will have full access to all your files

Thanks for adding that!  I'd forgotten about that mapping.  It's been quite a while since I've used WINE.  I just run Win7 in a VM when I need to run some Windows program.

> I'm not so sure about that, it's LockWindowUpdate (singular), so I think it may be more to do with manipulating the GUI. I'm guessing though.

I was guessing, too, though without the "s" you guess makes the most sense.

---

### Post by Duncan Williams on 2011-04-02
upload the files to jottis and scan them for possible infection.
[http://my.opera.com/internetsecurity/blog/linux-internet-security](http://my.opera.com/internetsecurity/blog/linux-internet-security)

---

### Post by needhelppeeps on 2011-04-02
Malware can get on Windows systems regardless of what AV is used. I've seen them routinely get past Symantec, AVG, Trend, etc. If the windows app does not require network access, might be worthwhile to setup a machine specifically for it. Then you could only plug it in when you need windows and application updates. On a positive note, I have not seen these malware or heard of the capturing credit card information, mostly just mass mailers and fake anti-virus.

---

### Post by chowno on 2011-04-02
Isn't this solution obvious?  When I first started using Wine I remember reading off of their wiki that wine under linux will not solve the windows virus problem as wine is still happy to run the code.  However linux in general doesn't run these so why not just stop using wine to run windows viruses?  If you turn off the wineserver service this virus you have will not execute.

Further - If you are dual booting as you say why are you trying to run any windows applications in linux?  Wine is great but it's no substitute. Why not just seperate your linux and windows applications to each os?  Also running windows in general without any antivirus protection is highly discouraged by Microsoft - the makers of Windows - so I would probably listen to that nugget of information.  There are plenty of very good open source windows applications to help you with your windows problem, but it still just a windows problem.  Google the OSSWin project for more information.

---

### Post by Duncan Williams on 2011-04-12
I agree with chowno.
Keeping the two operating systems onboard.
A reboot only takes a matter of minutes.
Then you have full updated access to all your general files. 
(*not system files*). on both platforms. 
and if one goes down you can fix it from the other one (*to a degree*).
Ubuntu sees the windows files and allows transfer.
_**[Linux reader]("http://www.diskinternals.com/linux-reader/")**_ can be used in windows to transfer files from ubuntu.

---

