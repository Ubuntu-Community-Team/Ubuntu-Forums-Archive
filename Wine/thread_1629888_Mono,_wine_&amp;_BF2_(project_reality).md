---
title: "Mono, wine &amp; BF2 (project reality)"
date: 2010-11-24
forum: Wine
---

### Post by masterskop on 2010-11-24
Hi,

Just wondered if anyone is an well acquainted with mono and bf2 (project reality)?  I installed mono due to the fact that wine cannot run project reality(pr).  Pr needs Net framework 3.5 in order to run.  Net Framework 3.5 doesn't work in wine.  I'm using wine 1.3.7 atm.

Here's what happens when I run pr through mono:

~$ mono ~/.wine/drive_c/Program\ Files/EA\ GAMES/Battlefield\ 2/mods/pr/pr.exe

Unhandled Exception: System.Exception: There was an error writing a new file in the profiles directory. Details as follows.
 ---> System.IO.DirectoryNotFoundException: Could not find a part of the path "/home/user/Battlefield 2/Profiles/home/user/Battlefield 2/Profiles/0001/General.con".
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, Boolean anonymous, FileOptions options) [0x00000] in <filename unknown>:0 
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare)
  at System.IO.StreamWriter..ctor (System.String path, Boolean append, System.Text.Encoding encoding, Int32 bufferSize) [0x00000] in <filename unknown>:0 
  at System.IO.StreamWriter..ctor (System.String path, Boolean append) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.StreamWriter:.ctor (string,bool)
  at System.IO.File.CreateText (System.String path) [0x00000] in <filename unknown>:0 
  at c.c (Boolean A_0) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---


Any suggestions would be helpful on how to solve the first part of this problem:


 ---> System.IO.DirectoryNotFoundException: Could not find a part of the path "/home/marty6/Battlefield 2/Profiles/home/marty6/Battlefield 2/Profiles/0001/General.con".
  

Any help is appreciated!

---

### Post by directhex on 2010-11-24
I think you want to install Mono for Windows, inside Wine - which would be someplace like ~/.drive_c/program files/mono/bin

---

### Post by masterskop on 2010-11-24
directhex,

Yes, I do have mono installed into wine.  However, it does not work.  I've tried using the command prompt, but nothing happens.  Perhaps a setup issue?  Don't know.  I've used the mono command at the regular prompt in a terminal.  That's what I have been using.  

Would the command then be as such?

$wine mono ~/.wine/drive_c/Program\ Files/EA\ GAMES/Battlefield\ 2/mods/pr/pr.exe

I won't be able to try this until after I get back from Thanksgiving tomorrow night.  Please let me know if there is something that I'm missing.

---

### Post by masterskop on 2010-11-26
directhex,

I've installed mono for windows on my ubuntu box.  How do I start mono correctly in order to start the pr.exe file or rather what would the terminal command be?  I've tried the command prompt within the wine drop down menu under applications.  I could get the mono cmd prompt at all.  

Any help is appreciated.

---

### Post by masterskop on 2010-11-26
Hi,

I've noticed that Project Reality has 3 exe files that are loaded.  I was wondering if there was a way to get all 3 exe files loaded in wine?

The files are as follows:

BF2.exe
pr.exe
tr.exe

The pr.exe file calls on the BF2.exe to load as well as the tr.exe file.  This maybe part of my problem in getting this game to start.

Any help is appreciated.

---

