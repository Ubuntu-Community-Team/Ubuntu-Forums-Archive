---
title: "C++ Library? (For Idle Time)"
date: 2009-02-19
forum: Ubuntu Dev Link Forum
---

### Post by LonelyHowl on 2009-02-19
Hi,

I was looking for a library to access the idle time of the computer in Ubuntu - defined as: current_time - last_user_input_time.

I trying to develop a small application that uses this. So I was wondering if there was a library out there that has this. If it was for C++ it would be nice. Would anyone know?

I tried googling for the solution and found this thread:
[http://ubuntuforums.org/showthread.php?t=931676](http://ubuntuforums.org/showthread.php?t=931676)
which led me nowhere.

Please note that I am a university student and I may not be familiar with things.

Thanks a lot for the help.

---

### Post by rharriso on 2009-02-20
do you mean you are trying to have a program run in the CPU idle time?

---

### Post by LonelyHowl on 2009-02-20
no, i'm just trying to get the idle time - get some primitive of the idle time returned from a function.

---

### Post by rharriso on 2009-02-22
I think you're going to have to look more into system calls, than C++ libraries. 

Well you could have a program listen for inputs from the mouse and keyboard and then update a marker every time that happens, and then just spin around the loop the rest of the time, but as far as just pulling out of thin air the last time input was raised, that might be impossible.

This woudl be kinda intense kernel work.

---

### Post by LonelyHowl on 2009-02-22
oh..... thought it would be easier than that haha. i'm doing my operating systems course right now, so i guess i'll stop from here.

thanks for the help.

---

