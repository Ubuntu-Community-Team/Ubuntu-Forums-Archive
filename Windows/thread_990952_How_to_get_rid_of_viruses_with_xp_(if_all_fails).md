---
title: "How to get rid of viruses with xp (if all fails)"
date: 2008-11-23
forum: Windows
---

### Post by EnGorDiaz on 2008-11-23
There are some secret tips if you have a virus and your anti virus does not get rid of it. 

(do this operations in safe mode)

goto start and run and type
```
msconfig
```

now look through the start up files and try and pick through the unwanted beast and delete it once thats done 

find the path of the file which is the virus 

open command prompt and type 
```
cd (check the path of the virus goto the folder)
```

once your in the folder in command prompt type
```
del /s /q /f "path of virus" (with the commas)
```
this will force delete

now goto control panel then admin tools and services find the service of the file in there and delete it 

now if you cant run task manager bcus of the virus disabling the bind on ctrl alt delete

then do this command in run
```
taskmgr
```

if this works then kill the process from there

or in command prompt
```
start taskmgr
```

if that fails then do 
```
tasklist
```

Note: xp home users can download tasklist here 
[http://www.computerhope.com/download/winxp.htm](http://www.computerhope.com/download/winxp.htm)



if tasklist works sort through the tasks and services and delete the ones you want to this is recommended way to see the virus in the tasklist 

when you got the file you want to kill do these commands
```
tskill /A /V (name of process)
```

with /V there you get diagnostic you will be able to see what is happening to the file if it comes back or not or if it fails you will see the attributes

UPDATE: how to disable an autorun

Since users have been giving out good suggestions i want more aswell i want critism ppl give me it please i am adding this little thing i found

```
regsvr32 /u + [name of virus dll]
```

If you know the registry key which i will update this soon with a how to to pinpoint the registry keys then you can disable the virus from undeleting and other possible damage it could cause



COMING SOON: how to pinpoint virus and spyware registry keys

well those are just some tips correct me on some of them :D

---

### Post by Bablefish on 2008-11-23
When all else fails you could always reinstall your OS. By the way I got that from a friend who repairs computers for a living.

---

### Post by EnGorDiaz on 2008-11-23
> **Bablefish said:**
> When all else fails you could always reinstall your OS. By the way I got that from a friend who repairs computers for a living.

im just going for the ppl who want to spare there installation:P

---

### Post by Izek on 2008-11-23
> **EnGorDiaz said:**
> im just going for the ppl who want to spare there installation:P

What if the path/to/file happens to be C:\WINDOWS?

---

### Post by EnGorDiaz on 2008-11-24
> **Izek said:**
> What if the path/to/file happens to be C:\WINDOWS?

then a recursive force delete like that one is not recommended just take out the /f

---

### Post by Calash on 2008-11-24
That will not help if the virus ties into winlogin, like Vundo or it's many....many....many variants.  Even in safe mode they get started, and will undo what you try to clean.

---

### Post by Thelasko on 2008-11-24
I could never trust that machine again unless I did a complete reinstall.

---

### Post by rockface on 2008-11-24
> **Thelasko said:**
> I could never trust that machine again unless I did a complete reinstall.

Would you trust ANY machine again once it has been shown to be compromised, no matter what OS it may be? 

As you say a 'complete reinstall' is in order, unless you have sufficient and bona fide backups available before the infestation took place (and this is putting faith against human nature).

---

### Post by Bibek on 2008-11-25
just pop in your ubuntu live cd, mount the windows partition and delete any suspecious files.

---

### Post by madverb on 2008-11-25
[http://technet.microsoft.com/en-us/sysinternals/bb963902.aspx](http://technet.microsoft.com/en-us/sysinternals/bb963902.aspx)

---

### Post by Giant Speck on 2008-11-25
I was half expecting someone to say install Ubuntu over Windows.  I am relieved that no one has.  Good work, community!  =D>

---

### Post by EnGorDiaz on 2008-11-25
> **Giant Speck said:**
> I was half expecting someone to say install Ubuntu over Windows.  I am relieved that no one has.  Good work, community!  =D>

i would think suggesting that would be quite stupid:P

---

### Post by EnGorDiaz on 2008-11-25
im going to be updating this guide with more tips and other things like how to disable a virus auto run

---

### Post by kernelhaxor on 2008-11-29
Some viruses do cause irrepairable damage right? by replacing/deleting/overwriting important system files and other things ..
Isn't reinstallation of the OS the only way to detect and recover from such things?

---

### Post by EnGorDiaz on 2008-12-01
> **kernelhaxor said:**
> Some viruses do cause irrepairable damage right? by replacing/deleting/overwriting important system files and other things ..
Isn't reinstallation of the OS the only way to detect and recover from such things?

i just want users to know that this is more educational :)

---

### Post by will1911a1 on 2008-12-02
Great info, although as someone stated earlier, I'd be more inclined to just wipe the machine and start over.

---

### Post by EnGorDiaz on 2008-12-03
> **will1911a1 said:**
> Great info, although as someone stated earlier, I'd be more inclined to just wipe the machine and start over.

remember educational:P

---

