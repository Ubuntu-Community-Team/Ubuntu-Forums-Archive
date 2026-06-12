---
title: "dansguardian default list: mimetype and extention"
date: 2009-07-25
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-07-25
For the start, let us decide what to allow and mimetype and extention. Below is the default banned, please let me know which ones should be removed. I have decided to remove .exe files from banned list in near future so that people would nat have difficulty in installing e-Sword.
Please bear in mind that this is for your kids, not for you. For you, you could just disable dansguardian altogether if dansguardian is blocking you.

DK

# banned MIME types
audio/mpeg
audio/x-mpeg
audio/x-pn-realaudio
audio/x-wav
video/mpeg
video/x-mpeg2
video/acorn-replay
video/quicktime
video/x-msvideo
video/msvideo
application/gzip
application/x-gzip
application/zip
application/compress
application/x-compress
application/java-vm

#Banned extension list

# File extensions with executable code 

# The following file extensions can contain executable code.
# This means they can potentially carry a virus to infect your computer.

.ade  # Microsoft Access project extension
.adp  # Microsoft Access project
.asx  # Windows Media Audio / Video
.bas  # Microsoft Visual Basic class module
.bat  # Batch file
.cab  # Windows setup file
.chm  # Compiled HTML Help file
.cmd  # Microsoft Windows NT Command script
.com  # Microsoft MS-DOS program
.cpl  # Control Panel extension
.crt  # Security certificate 
.dll  # Windows system file
.exe  # Program
.hlp  # Help file
.ini  # Windows system file
.hta  # HTML program
.inf  # Setup Information
.ins  # Internet Naming Service
.isp  # Internet Communication settings

.lnk  # Windows Shortcut
.mda  # Microsoft Access add-in program 
.mdb  # Microsoft Access program
.mde  # Microsoft Access MDE database
.mdt  # Microsoft Access workgroup information 
.mdw  # Microsoft Access workgroup information 
.mdz  # Microsoft Access wizard program 
.msc  # Microsoft Common Console document
.msi  # Microsoft Windows Installer package
.msp  # Microsoft Windows Installer patch
.mst  # Microsoft Visual Test source files
.pcd  # Photo CD image, Microsoft Visual compiled script
.pif  # Shortcut to MS-DOS program
.prf  # Microsoft Outlook profile settings
.reg  # Windows registry entries
.scf  # Windows Explorer command
.scr  # Screen saver
.sct  # Windows Script Component
.sh   # Shell script
.shs  # Shell Scrap object
.shb  # Shell Scrap object
.sys  # Windows system file
.url  # Internet shortcut
.vb   # VBScript file
.vbe  # VBScript Encoded script file
.vbs  # VBScript file
.vxd  # Windows system file
.wsc  # Windows Script Component
.wsf  # Windows Script file
.wsh  # Windows Script Host Settings file
.otf  # Font file - can be used to instant reboot 2k and xp
.ops  # Office XP settings 



# Files which one normally things as non-executable but
# can contain harmful macros and viruses

.doc  # Word document
.xls  # Excel document
.pps


# Other files which may contain files with executable code

.gz   # Gziped file
.tar  # Tape ARchive file
.zip  # Windows compressed file
.tgz  # Unix compressed file
.bz2  # Unix compressed file
.cdr  # Mac disk image
.dmg  # Mac disk image
.smi  # Mac self mounting disk image
.sit  # Mac compressed file
.sea  # Mac compressed file, self extracting
.bin  # Mac binary compressed file
.hqx  # Mac binhex encoded file
.rar  # Similar to zip


# Time/bandwidth wasting files

.mp3  # Music file
.mpeg # Movie file
.mpg  # Movie file
.avi  # Movie file
.asf  # this can also exploit a security hole allowing virus infection
.iso  # CD ISO image
.ogg  # Music file
.wmf  # Movie file
.bin # CD ISO image
.cue # CD ISO image

---

### Post by Aronzak on 2009-07-26
> **david_kt said:**
> For the start, let us decide what to allow and mimetype and extention. Below is the default banned, please let me know which ones should be removed. I have decided to remove .exe files from banned list in near future so that people would nat have difficulty in installing e-Sword.
Please bear in mind that this is for your kids, not for you. For you, you could just disable dansguardian altogether if dansguardian is blocking you.

DK

# Files which one normally things as non-executable but
# can contain harmful macros and viruses

# Other files which may contain files with executable code

# Time/bandwidth wasting files


Dansguardian is designed as a corporate gateway filter for use in a network that gets infected with Windows viruses. Many of these mimetype/extensions are designed to make life easier for system administrators.

Basically, I'd say leave the obscure Windwos config types, but get rid of all the mimetypes, the Office document formats, compressed archives and multimedia.

---

### Post by Caraibes on 2009-07-28
David, I am finding myself in a awkward position: if I don't "stop" Dansguardian, I can't log into my kids PC from mine thru ssh (you know, the "connect to server" button in Nautilus)...

I wish I could whitelist ssh login, somehow, so I would not have to go thru unnecessary steps when sharing files over my local network, between PCs...

-What is your take ?

---

### Post by david_kt on 2009-07-28
> **Caraibes said:**
> David, I am finding myself in a awkward position: if I don't "stop" Dansguardian, I can't log into my kids PC from mine thru ssh (you know, the "connect to server" button in Nautilus)...

I wish I could whitelist ssh login, somehow, so I would not have to go thru unnecessary steps when sharing files over my local network, between PCs...

-What is your take ?

I think that is because of firehol blocking the connection, not dansguardian. I found of a way to run dansguardian without firehol, I will send you the package to try once I completed it.

The removal of firehol is also one step I want to take to be able to share internet connection to the LAN.
 
DK

---

### Post by Caraibes on 2009-07-29
Sounds good... Thanks David !

---

### Post by david_kt on 2009-07-30
> **Caraibes said:**
> Sounds good... Thanks David !

Caraibes,

Please help to test the attached dansguardian gui.
It should solve your problem of ssh login.
If you run autoconfigure, it would also remove all blacklist of mimetype and extension.

DK

---

### Post by Caraibes on 2009-07-31
David, I confirm being able to ssh login into my kids box over my local network while having both PCs using Dansguardian2...

Good job ! Thanks...

God bless !

---

### Post by shane2peru on 2009-08-01
I agree, that if we can run it without firehol, it would make nfs and ssh much easier.  Those are two large draw backs.  Is that deb for 64bit?  I wouldn't mind running it and testing it as well.

Shane

---

### Post by david_kt on 2009-08-01
> **shane2peru said:**
> I agree, that if we can run it without firehol, it would make nfs and ssh much easier.  Those are two large draw backs.  Is that deb for 64bit?  I wouldn't mind running it and testing it as well.

Shane

Yes it could be use for 64 bit as well. Later on I plan to write simple firewall as well, but just let me know what port to open. For ssh I already know the port to open, but for nfs I do not know yet.

By writing my own firewall, I could customize according to people requirement here easily.

DK

---

### Post by shane2peru on 2009-08-01
> **david_kt said:**
> Yes it could be use for 64 bit as well. Later on I plan to write simple firewall as well, but just let me know what port to open. For ssh I already know the port to open, but for nfs I do not know yet.

By writing my own firewall, I could customize according to people requirement here easily.

DK

I really don't understand Dan's Guardian and the need for firehol, so this may be an irrelevant question.  Is there any way to incorporate UFW as a replacement for firehol?  Then GUFW (Graphical Uncomplicated Firewall) could be used to add the appropriate services, cutting down on your having to customize for specific circumstances.  That is what I'm using, but as I stated, I really don't understand the role that firehol plays in DG, so it may be a mute point.

Shane

---

### Post by david_kt on 2009-08-01
> **shane2peru said:**
> I really don't understand Dan's Guardian and the need for firehol, so this may be an irrelevant question.  Is there any way to incorporate UFW as a replacement for firehol?  Then GUFW (Graphical Uncomplicated Firewall) could be used to add the appropriate services, cutting down on your having to customize for specific circumstances.  That is what I'm using, but as I stated, I really don't understand the role that firehol plays in DG, so it may be a mute point.

Shane

What I have find out is to set up transparent proxy. Without firehol, I have to find a way to manage iptables directly to do that. Otherwise, when you on dansguardian, you have to change proxy setting in firefox in order to be filtered.
 or in other words, if the proxy setting is not change the dansguardian is by passed.

DK

---

