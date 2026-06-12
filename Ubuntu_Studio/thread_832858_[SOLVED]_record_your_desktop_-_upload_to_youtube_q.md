---
title: "[SOLVED] record your desktop - upload to youtube question!"
date: 2008-06-18
forum: Ubuntu Studio
---

### Post by Dutch70 on 2008-06-18
Hi, I just made a video of my desktop, and dont understand how to convert it from .ogg and upload it to youtube. I am following this guide...[http://ubuntuforums.org/showthread.php?t=294605](http://ubuntuforums.org/showthread.php?t=294605)

This is all very new to me, and I dont understand it at all. I have the video made and named "out.ogg.dave"

I also installed mencoder via "sudo aptitude install mencoder" but dont know where its at, or how to use it. and dont have a clue what this example is about...(from the link above)
```
mencoder -idx input.ogg -ovc lavc -oac mp3lame -o output.avi 
```

I would really appreciate some idiot proof help if someone has the time.
Please!

---

### Post by thorgal on 2008-06-18
it's a command line application. It means you need to open a unix shell (most likely bash) or a terminal window if that makes more sense to you. If you are familiar with the DOS prompt in MS windows, the unix shell is something similar in appearence (but only in appearence).

Once you open a terminal window, just copy paste the command line you reported here. You of course need to be in the right directory (where your ogg file is located) for the shell will by default open in your home directory. Welcome to unix :)

EDIT: I did not check, you need to replace input.ogg by your ogg filename. I would avoid adding an extra extension that does not reflect the type of the file (the suffix .dave you added is not necessary and can confuse applications that rely on file extensions, like graphical file browsers or other).

---

### Post by Dutch70 on 2008-06-18
Thanks for the quick response and the welcome! I love it here. not just the system but the community, the whole Idea is definitely for me.

 I'm not exactly sure what you mean to be in the directory or home folder where it is located. I have the home folder open, if that is all, but I am getting this message in terminal...

note: I changed the name to DaveandDee.ogg and tried changing it in the command I put in. like this.
```
mencoder -idx DaveandDee.ogg -ovc lavc -oac mp3lame -o DaveandDee.avi 
```

and I get this...
```
david@david-desktop:~$ mencoder -idx DaveandDee.ogg -ovc lavc -oac mp3lame -o DaveandDee.avi 
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
File not found: 'DaveandDee.ogg'
Failed to open DaveandDee.ogg.
Cannot open file/device.

Exiting...
david@david-desktop:~$ 


```

maybe you can see where I am getting lost. I also just tried the exact command, and got almost the same message -the name.

---

### Post by Dutch70 on 2008-06-18
bump, due to your edit. 
 I changed the name, and I'm not sure you saw my post. hope thats not bad ethics...:lolflag:
"since its at the top anyway"

---

### Post by Tomatz on 2008-06-18
There is a gui desktop video app. Its called istanbul.


```
sudo apt-get install istanbul
```


;)

---

### Post by ad_267 on 2008-06-18
What folder is that file in?

You use the "cd" command to change directories to go to the directory containing the file.

Eg if it's in the folder videos, you need to enter "cd videos"

Be aware than commands are case sensitive.

---

### Post by cszikszoy on 2008-06-18
The output from mencoder shows you what the problem is.  It is complaining that it can't find the video file you specified to.  For the "input.ogg" you need to specify the path to the file.  For example, if your video was in your home/videos folder, you would need to call put /home/dave/videos/input.ogg for the input video file.

Bash treates these arguments as absolute paths.  If you just put dave.ogg for the input file, mencoder will look for the file in the root directory "/".

Try putting the path/to/the/file as the input to mencoder.

---

### Post by Dutch70 on 2008-06-18
Hahaa, I'm a happy camper now. It was in the video folder. I just moved it out and it worked like a charm. Thanks so much everyone. That little bit of knowledge is def. gonna be useful for everything.

---

### Post by loell on 2008-06-18
> **Dutch70 said:**
> 
```
mencoder -idx DaveandDee.ogg -ovc lavc -oac mp3lame -o DaveandDee.avi 
```

and I get this...
```
david@david-desktop:~$ mencoder -idx DaveandDee.ogg -ovc lavc -oac mp3lame -o DaveandDee.avi 
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
File not found: 'DaveandDee.ogg'
Failed to open DaveandDee.ogg.
Cannot open file/device.

Exiting...
david@david-desktop:~$ 


```

maybe you can see where I am getting lost. I also just tried the exact command, and got almost the same message -the name.

recordmydesktop default file is **out.ogg**

so it should be something like this

```
mencoder -idx out.ogg -ovc lavc -oac mp3lame -o DaveandDee.avi 
```


if you have several recordings already, the succeeding file names are **out.ogg.1** , **out.ogg.2** so on..

---

### Post by Dutch70 on 2008-06-18
Thanks to you to loell, I know you were working on that too, while I was making my reply.

edit...and I thought that one was going to be tough to get help with...:lolflag:

---

### Post by Tomatz on 2008-06-18
You can mark this thread as solved.

[I]
Thread tools, mark thread as solved[/I]

It will help others that run into the same problem ;)


[edit] Oh you did lol *duh*

---

### Post by thorgal on 2008-06-18
Dutch70,

What I will suggest to you now is not at all mandatory but if you truly want to know and master the power of unix (linux), you would certainly benefit from knowing more about the unix shell (command line stuff, scripting). There are many books around (online or not). Usually, the unix in a nutshell serie is a good set of reference guides to have at home.

---

### Post by Dutch70 on 2008-06-18
Reply to Tomatz: 
 Yes, in the past I have made my reply and then marked it solved, however, I, now, see the need to mark it solved and then reply.

To thorgal: 
 Thanks again for the tip, that is obviously what I am having a hard time with. Everywhere I have found something about it online, it has been choppy and difficult to understand. Especially since this is my first PC, and only 4 months old, (came with Vista) 
 
"unix in a nutshell" that sounds good!

---

