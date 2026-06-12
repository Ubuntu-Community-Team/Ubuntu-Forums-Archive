---
title: "[SOLVED] mixing 2 mp3 file"
date: 2008-08-14
forum: Ubuntu Studio
---

### Post by rahul_bhise on 2008-08-14
i have 2 mp3 file i want to mix it and make it one mp3 file. which application should i use.

---

### Post by ajgreeny on 2008-08-14
Try **audacity** which can import two or more mp3 files, and other audio file types, and then allows you to move either one separately backwards or forwards so you can have them play together or one after the other.  If all you want is to just add one mp3 to another and play more like an album, use **mp3wrap**.  After using this you can then split the mp3s with **mp3splt** (note there is no i in this applications name)  I use them a lot for my mp3 player which seems to play tracks randomly, so I need to join album tracks into one file for some albums where tracks merge one into another.

---

### Post by ryanisablond on 2008-08-14
If you want to dabble in the command line a little bit, the **cat** command is very powerful and very handy. Basically, it takes multiple files and just sticks them together. Sounds like exactly what you want to do.

It is pretty easy to learn, too. Open up the terminal and do the following:

```

cd ~/Path/to/your/music
cat file1.mp3 file2.mp3 > name-me.mp3

```

Navigate to the folder with your music, then use **cat** with the files you want to join (in order), and replace "name-me" with whatever you want the joined file´s name to be.

The best part about **cat** is that you can join a couple mp3s or a couple waves. How about a few text files? Simple. :)

Just FYI: there will be no cross-fades between the files, so you might get a pop at the transition. If you are more interested in editing the files, Audacity (as ajgreeny suggested) would be a better choice.

Good luck!

---

### Post by Stochastic on 2008-08-14
ryanisablond, I don't think cat is a very useful tool when working with audio (other than low-level hacks), as it doesn't separate the audiofile header from the actual audio data.  Furthermore the OP sounds like he/she wants to MIX the two files together, not JOIN the two files together.  For batch file work, try reading up on ecasound.

I'd stick with audacity for the task at hand.  There are many other audio editors out there as well, if you don't like audacity.

---

### Post by loboc on 2008-08-14
> **ryanisablond said:**
> If you want to dabble in the command line a little bit, the **cat** command is very powerful and very handy. Basically, it takes multiple files and just sticks them together. Sounds like exactly what you want to do.

It is pretty easy to learn, too. Open up the terminal and do the following:

```

cd ~/Path/to/your/music
cat file1.mp3 file2.mp3 > name-me.mp3

```

Navigate to the folder with your music, then use **cat** with the files you want to join (in order), and replace "name-me" with whatever you want the joined file´s name to be.

The best part about **cat** is that you can join a couple mp3s or a couple waves. How about a few text files? Simple. :)

Just FYI: there will be no cross-fades between the files, so you might get a pop at the transition. If you are more interested in editing the files, Audacity (as ajgreeny suggested) would be a better choice.

Good luck!

Thats the first thing i tried after reading the thread title you beat me to the post though

---

### Post by rahul_bhise on 2008-08-15
> **Stochastic said:**
> Furthermore the OP sounds like he/she wants to MIX the two files together, not JOIN the two files together.
I'd stick with audacity for the task at hand.  There are many other audio editors out there as well, if you don't like audacity.
yes i want to mix it together. my one mp3 has a sound of sea waves and author file has a sound of birds sound. and i want to mix it together so that i can hear both the tracks at same time. and audacity did the job

> **ajgreeny said:**
> Try **audacity** which can import two or more mp3 files, and other audio file types,
thank you. audacity did the job after importing the two files i again exported it to a single file
> **ryanisablond said:**
> ```

cd ~/Path/to/your/music
cat file1.mp3 file2.mp3 > name-me.mp3

```
The best part about **cat** is that you can join a couple mp3s or a couple waves. How about a few text files? Simple. :)
Good luck!
i didn't now **this** use of cat command. thanks for information.

---

### Post by Stochastic on 2008-08-16
Another fun cat audio hack is to send files directly to the /dev/dsp device.  But that's not normal audio, it's binary file data being sent to your audio device;)  (try a .pdf or a .jpg) But now I've drifted off topic.

---

