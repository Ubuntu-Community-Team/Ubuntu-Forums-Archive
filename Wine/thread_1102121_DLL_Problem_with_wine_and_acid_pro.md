---
title: "DLL Problem with wine and acid pro"
date: 2009-03-21
forum: Wine
---

### Post by withnail420 on 2009-03-21
Basically I wanted to see if acid pro 4 (last version before Sony bought them out and added the same rootkit as they had on their cds) would work with wine since it went to version 1.0
I remember using it a couple of years ago and I get get the program to appear but not run sound. Now I can't even get it to load up.
When I try doing a wine acid40.exe from the commandline it spits out a long list of dlls it can't load, here's a sample.

err:module:import_dll Library sfs4rw.dll (which is needed by L"C:\\Program Filesonic Foundry\\ACID 4.0\\acid40.exe") not found

Basically a pagesworth of that.

I've tried copying the dlls to the system32 directory, nothing. I've tried chmoding them to 777 out of desperation in case it was file permissions, nothing. 

I know this must be fixable as I've got further than this before, I just don't know how to.

Any ideas people? Any help very much appreciated

---

### Post by asdfoo on 2009-03-23
> **withnail420 said:**
> Basically I wanted to see if acid pro 4 (last version before Sony bought them out and added the same rootkit as they had on their cds) would work with wine since it went to version 1.0
I remember using it a couple of years ago and I get get the program to appear but not run sound. Now I can't even get it to load up.
When I try doing a wine acid40.exe from the commandline it spits out a long list of dlls it can't load, here's a sample.

err:module:import_dll Library sfs4rw.dll (which is needed by L"C:\\Program Filesonic Foundry\\ACID 4.0\\acid40.exe") not found

Basically a pagesworth of that.

I've tried copying the dlls to the system32 directory, nothing. I've tried chmoding them to 777 out of desperation in case it was file permissions, nothing. 

I know this must be fixable as I've got further than this before, I just don't know how to.

Any ideas people? Any help very much appreciated

how are you trying to run the application?

did you cd into the install directory first like the Wine FAQ says?

---

### Post by withnail420 on 2009-05-14
back again, with the same problem, didn't think anyone had replied before.
Yes, I changed to the directory that the program is in and ran wine from the commandline. It says that it can't find dll's that are in the same directory as the exe. tried putting them in system32, does nothing. 
The wine configuration program only allows overriding system dlls, not adding third party ones.
I KNOW there is a way of doing this though as I have got the program to load on an earlier install years ago. Anyone, please help, this is driving me bloody mad!

---

### Post by asdfoo on 2009-05-14
> **withnail420 said:**
> back again, with the same problem, didn't think anyone had replied before.
Yes, I changed to the directory that the program is in and ran wine from the commandline. It says that it can't find dll's that are in the same directory as the exe. tried putting them in system32, does nothing. 
The wine configuration program only allows overriding system dlls, not adding third party ones.
I KNOW there is a way of doing this though as I have got the program to load on an earlier install years ago. Anyone, please help, this is driving me bloody mad!

sounds like you're doing something wrong

please show us the commands you are using and the result...  do not put application dlls in system32

---

### Post by withnail420 on 2009-06-02
Can't be arsed now.
I know I haven't done anything different, and besides, the first thing i tried was a simple wine "acid40.exe". 
No configuration change has given me different output since then. This is a problem on the development side

---

