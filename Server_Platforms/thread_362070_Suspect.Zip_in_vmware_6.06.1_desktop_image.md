---
title: "Suspect.Zip in vmware 6.06.1 desktop image?"
date: 2007-02-15
forum: Server Platforms
---

### Post by coolreason on 2007-02-15
I use clamwin (0.88.7) on windows and it show up a virus called "Suspect.Zip" in a

  [http://isv-image.ubuntu.com/vmware/Ubuntu-6.06.1-desktop-i386.zip](http://isv-image.ubuntu.com/vmware/Ubuntu-6.06.1-desktop-i386.zip)

I did an md5 of the file in quarantine (on cygwin).

$ ls -l infected.Ubuntu-6.06.1-desktop-i386.zip.000
-rwx------+ 1 James None 779465218 Feb 13 19:04
$ md5sum.exe infected.Ubuntu-6.06.1-desktop-i386.zip.000
8b30644ee79831b97d15bea4bbf9917b *infected.Ubuntu-6.06.1-desktop-i386.zip.000

These images don't seem to be on the vmware.com appliances site.

Oddly it does not find the virus in the extracted files.  I used 7zip to extract the desktop image and the virus only show up on a later scheduled run of my tmp directory. My system appears fine after doing a full scan overnight.

Has anyone else had a problem? Can someone get some md5/sha1 digests with the images on the isv-images? 

James

---

### Post by jamez011 on 2008-03-14
When clamav returns Suspect.Zip, it does **_not_** mean that a file matched one of its signatures, or that there is a virus in the file.  It simply means that the zip/compressed file looks suspicious (something wrong in the headers?).  

You can normally ignore this message.

---

