---
title: "Folding@home people a bit confused about linux?"
date: 2008-08-11
forum: The Cafe
---

### Post by damis648 on 2008-08-11
I was on my way to download folding@home for Ubuntu (No longer use Windows at all :-D ), which I use on my PS3 about every other night. For those that do not know what it is, visit the [homepage]("http://folding.stanford.edu"). Anyway, I went to the download page and downloaded the Linux version. It came as a gzipped tarball with two executables inside. I was not sure exactly which to use.. so I checked the "Installation" instructions.

> LINUX CONSOLE MODE SOFTWARE

(Version 6 beta now available!)

We provide a console mode version of the client. There are no fancy graphics -- it simply sits in the background running at lowest priority and making use of the CPU cycles not being used by other processes. The latest Linux version can be found at [http://folding.stanford.edu/Download](http://folding.stanford.edu/Download)

To launch: To use this program, make sure that you can execute it (chmod +x fah6.exe) and then run it ./fah6.exe

If you were previously using a Linux SMP client, the v6 client provides integrated SMP capabilities. Run with the command-line argument -smp for multi-processor operation/


Seems we got a bit of a misunderstanding about EXE's. They are **Windows** Executables! Fine, if they wanted to they could have set the extension of the executables to .exe if they wanted, thats fine with me (well maybe not completely)... although it is customary to leave no extension on a Linux executable. It is mainly the fact that they said "exe" in the directions but the file is not labeled that way... Still funny. Just thought I'd point that out. Found at: [http://folding.stanford.edu/English/LinConsoleInstallSMP](http://folding.stanford.edu/English/LinConsoleInstallSMP)

---

### Post by zmjjmz on 2008-08-12
Actually, EXE is just a way of archiving a bunch of binaries and making it executable.
It's a windows executable when it starts making system calls unique to Windows.

FAH runs fine btw.

---

### Post by keiichidono on 2008-08-12
.EXE exists in Linux too but it's entirely different.

---

### Post by 3rdalbum on 2008-08-12
```

chris@chris-desktop:~$ cd folding
chris@chris-desktop:~/folding$ ls
client.cfg        FahCore_79.exe   FAHlog.txt            unitinfo.txt
client.cfg~       FahCore_81.exe   machinedependent.dat  work
FAH504-Linux.exe  FahCore_82.exe   MyFolding.html
FahCore_78.exe    FAHlog-Prev.txt  queue.dat

```

The file is labelled with an exe on Version 5. If it's not in Version 6, then maybe they just forgot to change the instructions.

Interestingly enough, Mono applications have .exe.

---

### Post by TheConstruct on 2008-08-12
I've dealt with .EXE files for Linux before. They're just regular Linux binaries with an .EXE extension, nothing more. Can be confusing though.

---

### Post by kevin11951 on 2008-08-12
now then .MSI *that* is a microsoft specific executable.

---

### Post by Tomosaur on 2008-08-12
Yeah the exes from FAH will work fine on Linux - they're using it in the literal sense: 'Executable'. .exe files are not Windows specific, they're just 99.999999% used on Windows.

---

### Post by Kvark on 2008-08-12
The file name doesn't define the file type so being named .exe doesn't make the file a Windows executable. If you rename a png image to .ogg or whatever it's still a png image.
```
$file screenshot.ogg
screenshot.ogg: PNG image data, 1280 x 1024, 8-bit/color RGB, non-interlaced
```
If the file command says it's a DOS or Windows executable then yes they are confused. On the other hand if the file command says it's an ELF (Executable and Linking Format) file then they're using the correct file format. It's unnecessary to name executables .exe but it is just as unnecessary to name png images .png and nobody complains about that.

---

### Post by damis648 on 2008-08-12
> **Kvark said:**
> The file name doesn't define the file type so being named .exe doesn't make the file a Windows executable. If you rename a png image to .ogg or whatever it's still a png image.
```
$file screenshot.ogg
screenshot.ogg: PNG image data, 1280 x 1024, 8-bit/color RGB, non-interlaced
```
If the file command says it's a DOS or Windows executable then yes they are confused. On the other hand if the file command says it's an ELF (Executable and Linking Format) file then they're using the correct file format. It's unnecessary to name executables .exe but it is just as unnecessary to name png images .png and nobody complains about that.

I completely know what you are talking about, although I did state in my OP that my main issue was that I did not like how they chose to add an extension, and chose EXE, even when the files are not actually labeled that way. I knew it was a Linux executable, regardless of the extension. I just had a problem with that there wasn't actually one, and in the direction they had one. Specifically that EXE was chosen. As you said, I would have liked ELF or SELF. Makes much more sense, to me at lease.

---

### Post by kirsis on 2008-08-12
Well, the extension EXE is also used with Mono/.NET executables.

Since those can, in theory, run on both platforms, the .exe suffix should be there so Windows knows its an executable.

Now, this is probably not the case, since you mentioned the real executable didn't have .exe appended to it, but im just pointing out a reason why linux executables might be named that :)

---

