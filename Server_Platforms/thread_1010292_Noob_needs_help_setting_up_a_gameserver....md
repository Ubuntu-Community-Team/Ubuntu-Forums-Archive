---
title: "Noob needs help setting up a gameserver..."
date: 2008-12-13
forum: Server Platforms
---

### Post by Anonymous111 on 2008-12-13
Well ive pretty much given up getting battlefield 2142 working on linux but i still want to set up a server, which i know is possible.  I downloaded the server install file, bf2142-linuxded-1.10.48.0-installer.sh, (btw im using the desktop edition of ubuntu cuz im not familiar with the CLI yet), and this might be really stupid, but i cant figure out how to open the file. 

 So just need to know how to open and install and .sh file and then if i need any more help ill post here.

thanks

---

### Post by insane_alien on 2008-12-13
i know your not familiar with the commandline but just copy and paste this command into the terminal and follow any instructions that may come up.

NOTE: i am assuming that the installer is in your home folder

```
./bf2142-linuxded-1.10.48.0-installer.sh
```

if it says it is not executable do this:

```
chmod +x ./bf2142-linuxded-1.10.48.0-installer.sh
```

---

### Post by Anonymous111 on 2008-12-13
Well, it didnt work, but heres what it came up with:

drew@drewscomp-ubuntu:~$ ./bf2142-linuxded-1.10.48.0-installer.sh
bash: ./bf2142-linuxded-1.10.48.0-installer.sh: Permission denied
drew@drewscomp-ubuntu:~$ chmod +x ./bf2142-linuxded-1.10.48.0-installer.sh
drew@drewscomp-ubuntu:~$ ./bf2142-linuxded-1.10.48.0-installer.sh
Verifying archive integrity...Error in MD5 checksums: 477822da897e7597cb813f6268493273 is different from b8945897ad0049396e4902f968a1fefa
drew@drewscomp-ubuntu:~$ 

so is it a problem with the download hash?

---

### Post by insane_alien on 2008-12-13
yep your download is corrupted. try redownloading, torrent it if possible as that has built in checks.

---

### Post by Anonymous111 on 2008-12-13
Ok I got it to install.  Now I need to run it in the terminal so that i can monitor it (the file to start the server is in /home/drew/bf2142/start.sh).  I though there was an option in properties to run in terminal but i couldnt find it, i also tried to open it in the terminal with ./home/drew/bf2142/start.sh and it came up with an error

EDIT: Also theres a program that lets me access the server remotely, 2142cc (2142cc.com for info), and I was reading a guide for setting it up that can be found here:  [http://infinity-gamehosting.net/howto/Battlefield2142_and_2142CC_on_Linux/index-01.html](http://infinity-gamehosting.net/howto/Battlefield2142_and_2142CC_on_Linux/index-01.html)     The directions asked me to open the file "bf2ccd.exe" with mono...heres the results

drew@drewscomp-ubuntu:~$ mono bf2ccd.exe
Cannot open assembly bf2ccd.exe.
drew@drewscomp-ubuntu:~$ mono /home/drew/bf2142/bf2ccd.exe

** (/home/drew/bf2142/bf2ccd.exe:12741): WARNING **: The following assembly referenced from /home/drew/bf2142/bf2ccd.exe could not be loaded:
     Assembly:   System.Runtime.Remoting    (assemblyref_index=7)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/drew/bf2142).


** (/home/drew/bf2142/bf2ccd.exe:12741): WARNING **: Could not load file or assembly 'System.Runtime.Remoting, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Runtime.Remoting, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
File name: 'System.Runtime.Remoting, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'
drew@drewscomp-ubuntu:~$ 

so....yeah...i have no idea...

---

### Post by directhex on 2008-12-14
libmono-system-runtime2.0-cil

---

