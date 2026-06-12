---
title: "binary permissions"
date: 2009-11-29
forum: Server Platforms
---

### Post by tomdagreek on 2009-11-29
hi -
i think i have a permissions problem.'
i am trying to execute a bin file and it terminal says that file or directory not found
i have even tried to setup a new user and wget this bin and still nogo.
i will give e.g 
$/home/tom/file
chmod +x file.bin
./file.bin
 terminal says no such file or directory
i have also chmod 777 just for giggles

i have created a newuser called test and have downloaded this bin into a new directory under test user and still no go
any suggestions?
tom

---

### Post by Bachstelze on 2009-11-30
Aren"t you trying to execute a 64 bit binary on a 32 bit system (or vice versa)?

---

### Post by BkkBonanza on 2009-11-30
Is the name file or file.bin?
You appear to be doing it right so it should work (assuming you're using the right name). Must be something else odd. If the file is a script dependent on a language, make sure you have that language installed and the first line of the script has the shabang to indicate where to find it.

eg. for a bash script first line would be
#!/bin/bash

and for a perl script it might be like,
#!/usr/bin/perl

This is just something to check because you have the right idea with permissions and it must be something else wrong.

Also, just to be sure, you need to correctly specify the path to the file when you run it.

Cannot put file.bin at /home/tom/file.bin and then run ./file.bin unless you are in your /home/tom directory. If not currently there (check with pwd command) then run it as /home/tom/file.bin

This question ought to have been posted in general help not server platform forum.

---

### Post by tomdagreek on 2009-11-30
sorry i always type these questions fast...
directory  is as follows (off top of head)
/home/tom/file/file.bin

when i execute file.bin it says:
-bash no such file or directory
i am trying to exe from file dir

as far as i know i am running 32 on both sides...

---

### Post by tomdagreek on 2009-11-30
sorry for the spam.
what strikes me as odd is this bin will work with a gui. i am still learning the terminal side.
do i have to run a script to get this exe to work?

---

### Post by BkkBonanza on 2009-11-30
Sounds like your'e doing it right.

If you are in the same directory as the file.bin then you need to type ./file.bin to run it. If you are somewhere else, or anywhere really, you can type 

/home/tom/file/file.bin

to run it.

If it is a gui program then typing it in a terminal should popup the gui interface. I don't think that is the issue as the message bash is giving is what happens when you forget the ./ in front or the full path, or you type the name wrong.

If you still can't make progress here then type,

ls -lsaf file.bin

paste in here what you get back, showing permissions etc.

---

### Post by tomdagreek on 2009-12-01
here she is edited

---

### Post by tomdagreek on 2009-12-01
now i realize that i have tried this on a 64 bit flavor,but my first attempt was on a 32 bit.
one notable is that i was messing around and got this to work on a debian terminal and of course of ubuntu server w/gui.
looks to me like this bin is a executable and should fire but i do not know why here...
thanks

---

### Post by BkkBonanza on 2009-12-01
A little hard to read clearly but it appears to be correct.
You should be able to run it assuming it is executable.
Typically the message you got would indicate a miss-spelling not a problem with the file contents. I don't see a reason why it is not working.
You don't need to run a script, just make sure ./file.bin (the dot slash is needed if in current directory).

---

