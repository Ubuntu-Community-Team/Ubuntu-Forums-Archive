---
title: "can I share AMSN profile between Ubuntu and Windows?"
date: 2007-03-20
forum: Windows
---

### Post by 1002285 on 2007-03-20
I'd like to have AMSN profile in the same place for both Windows XP and Ubuntu, like it's possible with mozilla apps. I already have the FAT32 partition for those.
On Windows, I couldn't find the conf file to change the profile's location.

---

### Post by jclmusic on 2007-03-22
yep, that should work fine.

**/home/you/.amsn** or **/usr/share/amsn** on linux
**/program files/amsn** on windows

---

### Post by 1002285 on 2007-03-22
> **jclmusic said:**
> yep, that should work fine.

**/home/you/.amsn** or **/usr/share/amsn** on linux
**/program files/amsn** on windows"

OK, thank you. I guess I can take my profile and copy it where I want to?
But where is the place where I tell AMSN that "the profile is now on /media/fat32 ... (Ubuntu)
or on G:/.... (Windows)

---

### Post by joao82 on 2007-06-16
I would also like to know how to do that.

---

### Post by Kwunman on 2008-01-27
I have discovered how to do it!

Basically, open the file "C:\Program Files\aMSN\scripts\amsn" and copy what has been done below:

Replace "Z:" with the name of the drive containing your ubuntu msn profiles, and replace "daniel" with your own username.
> 
############################################################
### Setup other important directory paths
### depending on the platform
############################################################

if { [OnDarwin] } {
   set HOME "[file join $env(HOME) Library/Application\ Support/amsn]"
} elseif { [OnUnix] } {
   set HOME "[file join $env(HOME) .amsn]"
} elseif { [OnWin] } {
  if {[info exists env(USERPROFILE)]} {
     set HOME "[file join [COLOR="Red"]Z:[/COLOR] [COLOR="Red"]daniel[/COLOR] .amsn]"
  } else {
   set HOME "[file join [pwd] amsn_config]"
  }
} else {
   set HOME "[file join [pwd] amsn_config]"
}
set HOME2 $HOME

At this stage, if you try and run amsn in windows, it wont log on due to missing tls.

to overcome this problem, in the same file, change it to:

> 
############################################################
### And setup where to find optional packages
############################################################

proc lprepend {varName args} {
   upvar $varName var
   set var [eval [list linsert $var 0] $args]
}

lprepend auto_path [file join [COLOR="Red"]C: "Program Files" aMSN lib[/COLOR]]
#Specific folder to check for package on platforms
if { [OnDarwin] } {
	lprepend auto_path [file join utils macosx]
} elseif { [OnWin] } {
	lprepend auto_path [file join utils windows]
} elseif { [OnLinux] } {
	lprepend auto_path [file join utils linux]
} elseif { [OnBSD] } {
        lprepend auto_path [file join utils linux] 
}
lprepend auto_path [file join utils]

set libtls ""

catch { source [file join $HOME tlsconfig.tcl] }

if { $libtls != "" && [lsearch $auto_path $libtls] == -1 } {
    lprepend auto_path $libtls
}


Hope this helps!

---

