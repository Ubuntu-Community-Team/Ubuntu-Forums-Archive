---
title: "Can Python3 with VSCode work on Windows 10 offline?"
date: 2023-01-24
forum: Windows
---

### Post by smith73 on 2023-01-24
So there's Windows 10 pre-installed and I will not connect it to the Internet. 
I downloaded distutils and some other Python libraries' sources, as well as Python3.11 installer offline and clicked an option:
"Disable path length limit Changes your machine configuration to allow programs, including Python, to bypass the 260 character 'MAX_PATH' limitation".

Now while cd'ing in Windows Powershell it does not find the distutils Desktop ~(sub)4folder and other subfolders.
Though they are accessible from the Desktop GUI.

Should I reinstall Python3 without this option?
Is it worth to bother with Python and VSCode offline?
Will Python imports work offline?

---

### Post by TheFu on 2023-01-24
Path limitations are dependent on the file system AND the OS.  Windows NT+ had 4K length limits for decades.  Mostly similar for all the Unix file systems.
[https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits) says "No limit" ... which means it is set in the limits.h header file and passed into the kernel then file system. See footnote quoted below.

Now, the length of a filename is usually around 255 byte-sized characters, though NTFS (32,767 Unicode characters with each path component) is using Unicode now ... Unicode sizes are different for different characters, but I think they are all less than 4 bytes. Don't quote me.   When I was coding professional, we didn't have unicode and were using "double-byte" characters for our east Asian clients.  Unicode really makes things easier, if you have the RAM to waste (we didn't in the mid-1990s).

Almost all the file systems with "no limit", have this footnote:
> The on-disk structures have no inherent limit. Particular Installable File System drivers and operating systems may impose limits of their own, however. Limited by its Current Directory Structure (CDS), DOS does not support more than 32 directory levels (except for DR DOS 3.31-6.0) or full pathnames longer than 66 bytes for FAT, or 255 characters for LFNs. Windows NT does not support full pathnames longer than 32,767 bytes for NTFS. Older POSIX APIs which rely on the PATH_MAX constant have a limit of 4,096 bytes on Linux but this can be worked around. Linux itself has no hard path length limits.

Recompiling the kernel is needed to increase the PATH_MAX on Unix OSes.  I've had to do it a few times and it surprised me when is worked. ;) I wouldn't expect that would be possible on Windows, but I honestly don't know. Interesting if possible.

Short answer is that python imports are local and I've never seen any that reference internet locations.  GoLang does use internet includes, and I've seen those fail completely when no internet was available.  But not for python.

Python imports are within the python libraries, stored on a file system that can be reached by the OS.  That can be local, network storage or elsewhere.  If you use typical "import module" instructions and have a python module search directory environment variable that only refers to local storage, then no networking is needed.  

Any networking required is due to the specifics of the code in the module or the program.  If those don't use any network calls, then no network is needed.   There are thousands of modules that don't use any networking.  Of course, if you are creating a web-crawler in python, I expect a few modules and the program will require networking so the program can work.  If you create a local disk indexing tool, then no networking would be needed by the program or any of the modules, unless you add something to the code to force it - say phoning home to say the program was being run or to pull internet advertising into the program to nag the users.  Python **is** a general purpose language. It can be used to create almost any type of program, almost.

Desktop GUI means nothing to real code.  Pull up a powershell or cmd.exe terminal. If those can access the location using non-network access modes, then python won't require networking.

I prefer a more powerful editor, vim.  ;) I've been using vim to code since the mid-1990s.  The internet was created using vi by the elders of the internet.  I use my Linux X/Windows desktop as an IDE.  [https://blog.sanctum.geek.nz/unix-as-ide-introduction/](https://blog.sanctum.geek.nz/unix-as-ide-introduction/)  because that's what everyone where I worked used.  We had access to other IDEs and we could choose any. The company would buy anything we wanted.  We had some software libraries that were $10K/developer, so cost wasn't really any issue.  We all used vi/vim.  However, vim does have a steep learning curve, but in the hands of an intermediate vim users, it is, by far, the most productive editor I know, even today.

Writing python on Windows feels ... er ... wrong.  Same for ruby and perl.  People do it, but there are a number of reasons why they tend to fail long term if they don't switch.  The terminals on Windows OSes pretty much suck.  Use Linux, if you can.  Heck, use MacOS.  The Unix environment really is useful for coding.  It is hard to explain, except to say that coding on Windows is like entering a  race with 1 leg as everyone else has all there limbs racing to the finish.  Again, the learning curve is steep, but it will stick with you for a lifetime.  Code created on Linux generally runs on Windows and all Unix-like OSes with no to minimal changes.  Code created by Windows-centric people seldom ports easily.  I've seen this in my development teams over decades.

---

### Post by smith73 on 2023-01-24
While customizing Windows settings I logged in without a password (didn't choose).
After I wanted to install a downloaded offline Foobar app, Windows won't install it, even the latest stable version of it due to some errors like "An admin account blocked this app from installation" or "File corrupted". I added a password, but this doesn't change that.

Can it be that powershell can't access some nested subfolders due to some account settings?

I've installed python and VSCode to just have them ready, in case I'd like to use them while working with other Windows (CAD etc) apps.
I will install Ubuntu in dual boot, but I can't believe Windows 10 is so crappy.

---

