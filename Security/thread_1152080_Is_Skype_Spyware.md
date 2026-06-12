---
title: "Is Skype Spyware ?"
date: 2009-05-07
forum: Security
---

### Post by momo971 on 2009-05-07
Open Skype without login.
Open terminal an enter this command to get PID's:
```
ps aux | grep skype
```


You should get something like : 
```
momo     30234  0.0  0.0   4024   584 ?        S    19:03   0:00 /bin/sh /usr/bin/skype
momo     30235  4.1  0.9  87708 39120 ?        Rl   19:03   0:25 /usr/bin/skype.real
momo     30554  0.0  0.0   7540   912 pts/0    R+   19:14   0:00 grep skype
```
Get PID from skype.real ( here 30235 )

Now let's use some system calls and signals application over skype ( strace) :
```
strace -f -p30235 &>skype.log &
```

Now log into your skype account.

After login into skype launch this command in terminal:
```
grep bookmarks skype.log
```
This shows us the result of system calls and signals application of skype :```
[pid 30848] stat64("/home/momo/.mozilla/firefox/kpu1qtt3.default/bookmarks.html", {st_mode=S_IFREG|0644, st_size=28240, ...}) = 0
[pid 30848] stat64("/home/momo/.mozilla/firefox/kpu1qtt3.default/bookmarkbackups/bookmarks-2009-05-06.json", {st_mode=S_IFREG|0600, st_size=8807, ...}) = 0
[pid 30848] stat64("/home/momo/.mozilla/firefox/kpu1qtt3.default/bookmarkbackups/bookmarks-2009-04-30.json", {st_mode=S_IFREG|0600, st_size=6286, ...}) = 0
[pid 30848] stat64("/home/momo/.mozilla/firefox/kpu1qtt3.default/bookmarkbackups/bookmarks-2009-05-05.json", {st_mode=S_IFREG|0600, st_size=6651, ...}) = 0
[pid 30848] stat64("/home/momo/.mozilla/firefox/kpu1qtt3.default/bookmarkbackups/bookmarks-2009-04-29.json", {st_mode=S_IFREG|0600, st_size=6286, ...}) = 0
[pid 30848] stat64("/home/momo/.mozilla/firefox/kpu1qtt3.default/bookmarkbackups/bookmarks-2009-05-07.json", {st_mode=S_IFREG|0600, st_size=8807, ...}) = 0

```

So why a chat and VOIP software looks for my  bookmarks ???

---

### Post by Murrquan on 2009-05-07
I apologize, but perhaps you could summarize for the illiterate? (Although I guess they probably don't come to this forum that often ^.^; )

---

### Post by mojorising on 2009-05-07
Nice work, momo. Guess we shouldn't be very surprised.

I've never really used Skype so I'm not sure how it works but I wonder if you could sniff traffic from Skype to see if it's sending your bookmarks data anywhere with ngrep or similar. I'm betting it does send that info out. 


Murrquan, momo basically used a program (strace) to get a little more info on what Skype is doing in the background. With it, momo could see what files Skype was accessing on their system. 

Here's a quick description of strace from it's man page for you:

It  intercepts  and records the system calls which are called by a process and the signals which are received by a process.  The name of each system call, its arguments and its return value are printed on standard error or to the file specified with the -o option.

Check out the man page (man strace at the command line) on your system, visit [http://en.wikipedia.org/wiki/Strace](http://en.wikipedia.org/wiki/Strace), or check Google to find out more on strace. 


Mike

---

### Post by brian_p on 2009-05-07
> **momo971 said:**
> 

So why a chat and VOIP software looks for my  bookmarks ???

Maybe there is an answer here:

[http://ubuntuforums.org/showthread.php?t=548898](http://ubuntuforums.org/showthread.php?t=548898)

---

### Post by MysticalRiotCandy on 2009-05-08
I'm curious as to whether or not Skype does this in Windows and Mac OS X as well.

---

### Post by shadowlemon on 2009-05-29
if skype manages to spy upon a linux system then be sure that it will on a windows system

---

