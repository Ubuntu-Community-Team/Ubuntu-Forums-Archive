---
title: "Thank You everyone"
date: 2006-12-15
forum: Testimonials &amp; Experiences
---

### Post by danieltowsey on 2006-12-15
I will now give it another try with a fresh install. I have learned alot about Linux in the past few days. I think its going to be interesting to learn. I am looking at it as a hobby. But I will still have to use windows xp. I have many optional programs that I need to use on XP...But I think Linux is going to have its uses. If I can ever get past all these strange problems....MERRY CHRISTMAS EVERYONE

---

### Post by deadgobby on 2006-12-15
> **danieltowsey said:**
> I will now give it another try with a fresh install. I have learned alot about Linux in the past few days. I think its going to be interesting to learn. I am looking at it as a hobby. But I will still have to use windows xp. I have many optional programs that I need to use on XP...But I think Linux is going to have its uses. If I can ever get past all these strange problems....MERRY CHRISTMAS EVERYONE
 You too. Helps us help you. What option programs are you running on XP. There is load of help and you may run in Linux using a alternative program or running the MS program using Wine. 
 I got to go and tape off all the cat hair on me. Welcome to Linux. The next best thing since...Well  Windows.
Gobby

---

### Post by danieltowsey on 2006-12-15
Thanks..I have alot to learn..but in windows I actually have hundreds of programs..but I need to learn what wine is....another thing which is unnfortunate..I have no access to my other huge hardrives that are loaded with music and video files...

---

### Post by meng on 2006-12-15
My 2 cents: prioritize your problems, try to solve them one at a time in separate threads asking for help. Another approach that is commonly used is to itemize/enumerate the problems in a single thread, but I would advise that you concentrate on one thing at a time, then you'll feel you're making progress as each one is addressed. Provide full details of what you need, what you've tried, and don't be afraid to search the forums, search the wiki or search google.

---

### Post by xpod on 2006-12-15
I was going to comment in your "other" thread dt but my kids arrived home and the chaos ensued .

None of your issues are strange m8 it`s just that it`s all new to you.All will become clear if you just give it some time & patience
If you want to run windows programs then mabey keeping windows for that would be your best bet just now possibly?
Im just one of those that dont see the point in installing some program in linux to go back and run windows programs.:-k 
If i was a games player then im sure i would just keep windows etc etc

Anyway,Ubuntu dosent just have hundreds of programs you can use but it in fact  has thousands and theres usually many alternatives to whatever your used of in windows.A lot better alternatives in many cases too.

As you were advised on your "other" thread all your issues are fixable so just spend some time reading up and asking questions in a decent way
Remember....theres no such thing as a stupid question,just stupid answers and attitudes..;) 

Good luck and enjoy the best Xmas pressie you could ever have hoped for.

---

### Post by ajgreeny on 2006-12-15
> **danieltowsey said:**
> Thanks..I have alot to learn..but in windows I actually have hundreds of programs..but I need to learn what wine is....another thing which is unnfortunate..I have no access to my other huge hardrives that are loaded with music and video files...

Assuming the huge hard drives you can't access but are on the same machine, and are winxp ntfs, you can mount them easily by adding:-

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

 to the bottom of your /etc/fstab file as root

If they are winxp on fat32 add this line instead:-

/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

If you already knew this and the situation is totally different, my apologies; I don't wish to teach my grandmother to suck eggs, to use an old UK expression.

---

### Post by danieltowsey on 2006-12-15
> **ajgreeny said:**
> Assuming the huge hard drives you can't access but are on the same machine, and are winxp ntfs, you can mount them easily by adding:-

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

 to the bottom of your /etc/fstab file as root

If they are winxp on fat32 add this line instead:-

/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

If you already knew this and the situation is totally different, my apologies; I don't wish to teach my grandmother to suck eggs, to use an old UK expression.

How do I do this mounting?

---

### Post by wesley_of_course on 2006-12-15
> **deadgobby said:**
> You too. Helps us help you. What option programs are you running on XP. There is load of help and you may run in Linux using a alternative program or running the MS program using Wine. 
 I got to go and tape off all the cat hair on me. Welcome to Linux. The next best thing since...Well  Windows.
Gobby

       Checked out the [www.,](www.,) and found it very interest'in to say the least .
 It don't surprise me tho !

                 Linux all the way .

                             8)

---

### Post by DoctorMO on 2006-12-16
> How do I do this mounting?

Once you have configured your hard drives for mounting you can use the mount tool:

```
mount /dev/hda1
```

or perhaps:

```
mount /media/windows
```

If you not much into the whole reconfiguration by command line thing then you can always use some of the gui tools, I have forgotten their names though. sorry.

---

### Post by TooRight on 2006-12-16
Here's an awesome link that explains it perfectly... plus he's got loads of other ubuntu help on his site too!!

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)


Good luck babe!!! :D

---

