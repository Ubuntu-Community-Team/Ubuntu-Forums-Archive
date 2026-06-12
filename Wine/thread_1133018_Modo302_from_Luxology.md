---
title: "Modo302 from Luxology"
date: 2009-04-22
forum: Wine
---

### Post by Gorlist on 2009-04-22
Hi, over the last six or so months ive been trying to run & use [Modo302 from Luxology]("http://www.luxology.com") with various versions of Wine and Ubuntu 8.04, 8.10 and now 9.04rc. 

For the most part the program seems to function fine, though to you quad viewports opengl extension "GL_ARB_vertex_buffer_object" needs to be disabled(or VBO within the program). 

The main ongoing problem appears to be related to modo's interface and application focus - the whole GUI seems to run with upto a 2 second delay, so any mouse click to select a tool, or drag and drop geometry is followed by a short pause before the screen is updated.

Interestingly the opengl viewports themselves are running perfectly fine, you can zoom, rotate, pan at the correct speed when displaying geometry - it appears to be only caused by the UI.

The only other problem of note is drop down menu focus, majority of the options are un-electable, however the the UI can be modified to remove these, so not a real problem :)

Posted on the wine forums a number of months ago with no response - posting here for hopefully some suggestions.

Ive tried a number of wine revisions, from 1.00 to currently 1.1.19. Running the latest Nvidia graphics drivers installed from their website, and hardware specs as follows:

Intel 2 Quad Core, Q6600 2.4Ghz
Geforce 8800GT
3.9gig of ram

Ive also tested this on other systems (some with ATI) and can confirm they all suffer from the same bug.

Best Regards.

---

### Post by Gorlist on 2009-04-23
Just to add to that ive attached a PNG with a list of DLLS Modo normally uses within Windows XP.

From what I can read you can go through and tell wine to use Win DLLs until it no longer functions??

You can find the ongoing Modo on Ubuntu thread over at the Lux [forums]("http://forums.luxology.com/discussion/topic.aspx?id=28801&show=ubuntu").

[IMG]http://dev.ironfoot.co.uk/ubuntu_modo302.png[/IMG]

---

### Post by Gorlist on 2009-05-04
tested DLLS:

> advapi32 - license is lost, UI freeze.
comctl32 - no effect
comdlg32 - no effect
crypt32 - no effect
dciman32 - no effect, a DLL wine is missing.
ddraw - no effect
dnsapi - no effect
dnssd - no effect

------ NOT IN SYS32 -----
frame3
font3 
------

gdi32 - prevents modo from loading.
glu32 - no effect
hnetcfg - no effect
iertutil - no effect
imagehlp -no effect
imm32 - no effect
iphlpapi - no effect
kernel32 - no effect, reverted

locus3.dll - Missing

msasn1 - no effect
MSCTF - no effect
msimg32 - no effect
msvcr71 - wine permission denied**
msvcrt - no effect
mswsock - no effect, causes crash on close.

nexus3.dll - Missing

normaliz - no effect
ntdll - no effect
nvoglnt - no effect
ole32 - crash on load.
oleaut32 - no effect
opengl32 - fails to load

perl58 - Missing DLL
python24 - Missing DLL

rasadhlp - no effect
rpcrt4 - no effect
secur32 - no effect
setupapi - no effect
shell32 - no effect
shfolder - no effect
shlwapi - no effect
user32 - crash on load.
uxtheme - no effect

valet3.dll - Missing DLL.
wininet - no effect
winmm - no effect
winrnr - no effect
Wintab32 - no effect
wldap32 - no effect
ws2_32 - no effect


---

