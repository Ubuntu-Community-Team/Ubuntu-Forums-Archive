---
title: "how do I run DOS commands on bootup - similar to a rc.local bootup script.."
date: 2007-08-25
forum: Windows
---

### Post by billdotson on 2007-08-25
I want to make it so when I boot into XP it copies all my files that I regularly keep backed up (save games, school docs, etc.) and I am having some issues.  I know how to do this when I am booting into Ubuntu i.e. copy stuff off my Windows partition by making a script and referencing its location in /etc/rc.local but with DOS and XP I am lost. 

 I have not worked much with Windows or DOS (have not done much with Linux either as far as learning technical stuff goes, but by comparison I do not know much about Windows at all)  I looked up xcopy and how to use it and I can successfully copy files I want after some tinkering.. (why do you have to put "s around the source and destination to avoid getting invalid number of parameters error.. dumb)
I do not know how to make the command run at bootup, although I have an idea.  Either I make a batch file and reference that file in autoexec.bat (which for some reason even though I have the option set to "see all hidden files and folders" I cannot see in C:\) or actually enter the command in autoexec.bat

Am I on the right track?  

I just need to take off of school for about one or two years, and have a good supply of money to get books on stuff (if the information is too hard to get from the web) and just learn about stuff of importance (for me electricity/electronics, programming, networks,  OSes (mainly Windows and Linux)) Too bad life does not work that way.. hehe

---

### Post by InGunsWeTrust on 2007-08-25
Well if you don't care about a little box popping up after you log into XP you could do it like this: make a batch file with the following contents

```
xcopy C:\StuffYouWannaSave\* C:\WhereYouWannaSaveIt\
xcopy C:\OtherStuffYouWannaSave\* C:\WhereYouWannaSaveIt\
```

Then open the registry editor by typing regedit at the run box. Then navigate to the key [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run]
Add a key of the same type as all the other keys in that directory and have it reference C:\WhereYouStoreYourCopyingScript\YourCoolScript.bat

Then each time you start you will see a little black box saying it is copying the files then it will disappear.

---

### Post by billdotson on 2007-08-25
I do not want to have the black box pop up.  I want it to copy the files as part of the bootup process, like Linux (specifically Ubuntu) does when you reference a script in /etc/rc.local

---

### Post by InGunsWeTrust on 2007-08-25
Then I am pretty sure adding a line that references the script you create in autoexec.bat will do it as part of the boot up process. However be forwarned that some virus scanners might think your system is being hijacked and can produce false positives on virus scans (especially norton)

---

### Post by billdotson on 2007-08-25
nope, putting the path, in quotes or without quotes it still does not do anything.  Anything that I can notice anyway.

---

### Post by InGunsWeTrust on 2007-08-26
It it were Linux I could ask for the output... haha. I don't know then maybe there is some kind of special syntax we don't know. since autoexec.bat is already a batch file you could attempt to just put the desired commands in the file

---

### Post by billdotson on 2007-08-28
Ok, I have figured it out.  Here are the links: 
[http://support.microsoft.com/kb/314488]("http://support.microsoft.com/kb/314488")

These links tell how to either:

Run boot up or shutdown scripts

or set certain programs to run at logon

Both of these accomplish the same purpose if you are doing what I want to do, that is run commands to copy files to a backup partition.  You can run the batch file either as a program or you can run it as a script.

Kinda neat.  Even though it is not the same as referencing the name of the shell script in rc.local like in Ubuntu, it still is pretty simple.  Different strokes for different.. OSes.  That does not rhyme.. but oh well same principle.  Good luck.

---

