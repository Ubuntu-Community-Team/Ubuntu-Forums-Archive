---
title: "Starting a proces that wont stop unless killed."
date: 2011-01-22
forum: Server Platforms
---

### Post by simolokid4 on 2011-01-22
Dear Ubuntu forums,

I've recently discovered streamripper, and I've gotten a ds210j nas from synology.

I tried setting up a cronjob but that hasn't worked as far as I can tell.

Since the linux distro running on my ds210j is pretty much a stripped version of linux, i figure the cli will be the same.

I'd like streamripper to run continuously, 24/7, and save the 'ripped' to a certain folder. I'm always root so that something like /volume1/music/

A cronjob would run for xx time and then simply run it again, which would either stop the first and thereby cutting the current song or creating 2 instances of the streamripper proces.
[B]So basicly:
[/B][I][B]Is there a way to create a proces, trough ssh, that won't be killed when i log out of the ds210j?
[/B][/I]Feel free to think out of the box, big, or in any way not-usual.

Kind regards :)

P.S.: The cronjob i had; was in /etc/crontab and contained the following:
```
00 8 0 0 0 streamripper http://urlhere:porthere/ -d /volume1/music/ > /dev/null 2>&1
```

And I have now deleted the latter part of that; I've kept the following:
```
00 8 0 0 0 streamripper http://urlhere:porthere/ -d /volume1/music/
```

But I'm guessing that wont work either.

---

### Post by SeijiSensei on 2011-01-22
Putting an ampersand ("&") at the end of a command will make it execute in the background as a separate process.  Then you can log out of the shell, and it will continue to run.

---

### Post by simolokid4 on 2011-01-22
I'm sorry but that didnt do the trick; here's what i tried to test that method:

- ssh'd into my nas
- ```
streamripper urlhere &
```
- and it immediatly began.
- tried exiting with the 'x' of the ssh window since typing exit would have exited the proces (it immidieatly has output 'connecting' 'stream: .. ' etc. )
Got warned about killing the proces.
Started a new terminal (closed the other one)
ssh'd into nas again
did ```
ps -ax
```, nothing to be found 'streamripper' wise. To be sure i ran
```
ps -ax | grep str
``` and got someting named 'kstriped' as the only output.

Any more idea's?

---

### Post by amra.sonntag on 2011-01-22
Try using

```
ssh -f you@yourhost yourcommand
```

This way you will send ssh into the background before starting your command and it will keep running on the server with your user.

---

### Post by simolokid4 on 2011-01-23
Meh, that doesn't work either;

```
ssh -f user@server.com streamripper http://urlhere:porthere/ -d /volume1/music/
```Gives back: ```
ash: streamripper: not found
```While if i ssh into it and do ```
streamripper http://urlhere:porthere/ -d /volume1/music
```it simply works.

I did not make a typo with ssh -f.

Also tried ```
ssh -f user@server.com "streamripper http://urlhere:porthere/ -d /volume1/music"
```
with both " and ', both return the same ash: streamripper: not found
Starting to think it might be me, who's having things to want that simply arent that normal =P

Thanks tough, as I'll keep trying now and then, any further help is greatly appreciated.

---

### Post by koenn on 2011-01-23
processes will stop when their controlling terminal "hangs up" i.e. when the user who initiated the process logs out - background or not.

you need 'nohup' (no hangup) to keep processes running after you log out : 
[http://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html](http://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html)

'screen' has similar functionality

---

### Post by simolokid4 on 2011-01-23
Yuy, that seems to be working :O

I'll check in around 21.00 local time again, to see if the directory has gained substantial size.

For now, thanks and I'll mark this thread solved. Altough when im:
```
ps ax | grep str
```
i get streamripper <url here> -d /volume1 instead of /volume1/music.

(21.00 because the folder I have build up by simply letting it run across ssh with my behind my laptop is already around 400mb, cnt notice much diffrence in about 5 mins =p )

Is there some sort of maximum amount of characters appearing in ps ax or is it doing somethg very  wrong? ;x

---

### Post by koenn on 2011-01-23
> **simolokid4 said:**
> 
Is there some sort of maximum amount of characters appearing in ps ax 
the width of your terminal, in fixed-width characters.
usually ~80

---

### Post by simolokid4 on 2011-01-23
Nvm, it works.

I removed everytihng after -d, and simply cd'd into /volume1/music
Thereby removing the need for the -d parameter.

Then i exited ssh screen (ctrl a, ctrl d)
exited ssh session itself
exited terminal just to be sure
start terminal
ssh'd into nas
ran ```
ps ax | grep str
```
got streamripper as result
to test it to be 10000% sure:
```
du -h /volume1/music
```
Ran that 1st, then again 10 seconds later. The volume had become bigger, and so it works ;D

I'll mark this thread as solved as soon as i find out how.

Thank you, and thank the ubuntu community :)

---

