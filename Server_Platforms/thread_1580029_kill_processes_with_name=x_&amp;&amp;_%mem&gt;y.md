---
title: "kill processes with name=x &amp;&amp; %mem&gt;y"
date: 2010-09-22
forum: Server Platforms
---

### Post by jcooke22 on 2010-09-22
Hi all,

I have an issue on one of my servers whereby the [normally very helpful] du and tar programs are somehow using up too much or my system resources (du 40% mem, tar 20% mem) and causing problems.

I am after a command which is able to kill a process without knowledge of a PID but by process name e.g. "du" and memory usage e.g. >= 10%.

Something along the lines of:
kill $(pgrep du) grep %MEM > 10
Although I know that is invalid syntax I cannot fathom the correct/best way to achieve this end!

Any helpful hints would be much appreciated!
Thanks

---

### Post by stlsaint on 2010-09-22
have you not tried:

```
 kill -9 <name_of_process> 
``` 

Usually you should use a pid here as in 

```
kill -9 <PID>
```

---

### Post by CharlesA on 2010-09-22
I usually just use:

```
ps aux | grep process
```

Then kill it by the PID. Easier then typing out a long command.

---

### Post by slooksterpsv on 2010-09-22
[php]
ps aux | grep $1 | awk '{print $2,$4,$11}' | 
awk '{ if ($2>0.5) print $1,$2,$3;}' |
awk '{ if ($2>3.0) system("echo " $3) }'
[/php]

I could save that to a file and run it doing the following (assume I name it fmemuse)
sh ./fmemuse chrome
Here's the output:
/opt/google/chrome/chrome

So I'm testing to see if the memory is above 0.5 if it is test to see if its above 3.0 if it is print the location of the file chrome, I could change $3 on the last line to $1 to see its PID or $2 to see it's memory, or even change echo, to kill and do kill $1

---

### Post by LightningCrash on 2010-09-23
> **slooksterpsv said:**
> [php]
ps aux | grep $1 | awk '{print $2,$4,$11}' | 
awk '{ if ($2>0.5) print $1,$2,$3;}' |
awk '{ if ($2>3.0) system("echo " $3) }'
[/php]

I could save that to a file and run it doing the following (assume I name it fmemuse)
sh ./fmemuse chrome
Here's the output:
/opt/google/chrome/chrome

So I'm testing to see if the memory is above 0.5 if it is test to see if its above 3.0 if it is print the location of the file chrome, I could change $3 on the last line to $1 to see its PID or $2 to see it's memory, or even change echo, to kill and do kill $1
roughly what i was going to say. good job.

---

### Post by slooksterpsv on 2010-09-23
> **LightningCrash said:**
> roughly what i was going to say. good job.

Yeah, but there is a flaw with it, if a program contains the name you type in, it'll kill those programs so if you typed in fmemuse a and accidently pressed enter, all programs with a in it, above memory usage x, would be killed.

---

### Post by LightningCrash on 2010-09-23
I wouldn't really call that a flaw though... it happily does whatever you tell it to ;)

---

### Post by jcooke22 on 2010-09-23
Thanks slooksterpsv!

I ended up with:
ps aux | grep du | awk '{ if ($4>10) system("kill "$2)}'
Running via a cron job, it seems to work a treat!

Cheers
:)

---

### Post by LightningCrash on 2010-09-23
> **jcooke22 said:**
> Thanks slooksterpsv!

I ended up with:
ps aux | grep du | awk '{ if ($4>10) system("kill "$2)}'
Running via a cron job, it seems to work a treat!

Cheers
:)
Now that you've started down the dark side, get a book on Awk ;)

---

### Post by slooksterpsv on 2010-09-23
> **LightningCrash said:**
> Now that you've started down the dark side, get a book on Awk ;)

I need one too lol, I did that just by examples and some awk documentation.

---

### Post by SeijiSensei on 2010-09-23
Just a note that you can kill a process by name, rather than PID, using "killall programname" instead of "kill".  As the name implies, though, it kills all processes running programname, which may or may not be what you want to do.

killall takes the same switches as kill; -15 is "graceful," while -9 lowers the boom.

---

### Post by BkkBonanza on 2010-09-24
Killing seems so brutal. Couldn't you just set their niceness so they run at low priority? Or is this some hog user on your system you want to rid yourself of?

**man renice**

---

### Post by LightningCrash on 2010-09-24
> **SeijiSensei said:**
> Just a note that you can kill a process by name, rather than PID, using "killall programname" instead of "kill".  As the name implies, though, it kills all processes running programname, which may or may not be what you want to do.

killall takes the same switches as kill; -15 is "graceful," while -9 lowers the boom.

I would not advise becoming accustomed to using `killall`, as it has drastically different behaviors on other *nix platforms.

pkill is much preferred.

---

### Post by slooksterpsv on 2010-09-24
> **LightningCrash said:**
> I would not advise becoming accustomed to using `killall`, as it has drastically different behaviors on other *nix platforms.

pkill is much preferred.

I haven't made scripts that do killall or kill, but I do use those quite a bit with stuck programs. Why pkill? (googling now).

---

### Post by LightningCrash on 2010-09-24
> **slooksterpsv said:**
> I haven't made scripts that do killall or kill, but I do use those quite a bit with stuck programs. Why pkill? (googling now).

If you're on a Solaris box and you type
> killall firefox

It will kill **everything** on the machine. Solaris' killall doesn't accept processname arguments.

---

