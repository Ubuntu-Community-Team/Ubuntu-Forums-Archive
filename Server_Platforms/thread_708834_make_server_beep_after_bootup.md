---
title: "make server beep after bootup"
date: 2008-02-26
forum: Server Platforms
---

### Post by Compactman on 2008-02-26
I looked through other posts but I don't know to much about setting up my own boot scripts if someone could just give me a how to make my server beep after its booted before login and where to put it that would be wonderful.

I have installed the beep package from the universe if that helps.

---

### Post by fedex1993 on 2008-02-26
i think it ahs to do with something in sudo contrab or something like that. I dont rembmer exaclty my server beeps every hour on the hour and on bootup thats because of script becaus ei run openbox with it

---

### Post by frankelr on 2008-02-27
At last, I can help someone!

Hi, Just did this my self.  

Threre are two parts to the solution

1) What you need to do is apt-get or Synaptic
a program called "Beep"  Beep allows you to select pc speaker sound
for a given length, number of repeats and frequency.  You can test the sound at the command line till you get one  you like.

2) You need to go to System, Preferences,Secessions, StartUp Programs
and select +add. You get a new startup program which allows you to add Beep startup command. 

Now for some limitations of this method: only works for a single command line, if you want to play a song you got to write a script

Also the Beep gets activated after login to runlevel 5.

If you want to execute at other run levels eg level 3 you must add a script to .the correct  rc.  files ... that a lot more complicated for a beginner like me.  Finally I can't remember whether I had to supply the fully path to Beep ie /bin/Beep or whether the os found it  just by calling Beep

Hope I helped and if some real experts wants to explain how to use the rc. files i'll be glad to learn

Bob

---

### Post by Dr Small on 2008-02-27
Just add your beep code to the end of /etc/rc.local

Dr Small

---

### Post by Compactman on 2008-02-27
Thanks frankelr but I'm not using GUI.  This is a headless server.


I wasn't sure if it was RC local or not.  

Do I have to specify which run level in my beep code?  Is rc.local ran after run level 3?

---

### Post by Compactman on 2008-02-27
Okay I got it!

Here is the full instruction for anyone else


1. sudo apt-get install beep
2. sudo nano -w /etc/rc.local

Add this line before the exit 0. ctrl+c to copy and ctrl+insert to paste

```
beep -f 300.7 -r 2 -d 100 -l 400
```

3. CTRL+O   to save

---

