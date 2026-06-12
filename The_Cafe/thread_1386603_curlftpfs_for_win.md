---
title: "curlftpfs for win?"
date: 2010-01-20
forum: The Cafe
---

### Post by earthpigg on 2010-01-20
curlftpfs lets you mount an ftp server you have access to as a 'local' folder so you can transfer stuff by simply dragging and dropping in nautilus/pcmanfm/whatever.

i recently learned about it so i could use the [ftp subdomain]("http://masonux.geekconnection.org/") geekconnection.org was awesome enough to set up for me. (i still don't know what else i can do with it from the command line. necessity is how i learn :P )

as i learn linux tools to administer and accomplish various tasks on linux servers, i like to somewhat keep track of how windows users go about the same things. 

for example, after i learned about ssh... i learned about [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") and have it filed away in the back of my brain in case i ever need to use it on a win machine.

there is, as i understand it, no equivalent of sshfs on windows.

is there a windows tool that lets users mount ftp servers as 'local' folders?

if not, what is the most popular method or two that windows users use to manage ftp servers?

---

### Post by jabjoe on 2010-02-10
Mounting things as a folder in Windows is barely supported. It's implemented at a per filesystem level, and out of the few filesystems Windows supports, only NTFS supports this. A far more Windows like way of doing this is to mount the ftp server as a drive, and Windows supports that out of the box, there is also WebDrive,FTPDrive and maybe others.

As for sshfs, there is a Windows version, [http://dokan-dev.net/en/](http://dokan-dev.net/en/)

Hope this helps. :-)

---

### Post by Tibuda on 2010-02-10
I just use FileZilla in both Linux and Windows.

---

### Post by Grenage on 2010-02-10
I use Filezilla, but now I'm going to look at curlftpfs, sounds like a great addition.

---

### Post by WyoGuy on 2011-01-03
Other options for connecting to Unix boxes via ssh:  

One of the utilities that comes with PUTTY is [INDENT]PSCP (Putty Secure Copy).  

[/INDENT]Although it is command-line it works.  Might be good for a batch file from time to time.  An option in PSCP is to use a PUTTY session (in which many other options can be saved.  

Another free utility is WinSCP.  This provides a windows GUI for accessing the entire Unix file system and does not require any drivers (it is a very in-obtrusive, stand-alone program).  There are two modes of display and I find that one mode works faster than the other on slower computers.  

WinSCP.net

---

