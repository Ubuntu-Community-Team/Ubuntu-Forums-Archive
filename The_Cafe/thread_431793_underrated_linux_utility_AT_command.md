---
title: "underrated linux utility: AT command"
date: 2007-05-03
forum: The Cafe
---

### Post by Mateo on 2007-05-03
this command is simply great.  Once you figure out how to use it (it took me a while), it's super easy and quite powerful.  all you have to do is type something like:

```
at 10:00pm tomorrow
```

And then it will give you a **at>** prompt where you can type in your commands to run and then **ctrl+d** saves them.  Where it gets neat is that you can get even more complex with how you enter your dates.  Like this:

```
at 7:00am + 3 weeks
```

Will execute the commands 3 weeks from now.  Or you can also give a specific date like this:

```
at teatime Jul 31 2008
```

'teatime' is 4pm.  You can also use midnight or noon.  I use **at** for recording shows on my tv tuner.  It's much simpler than using the clanky mythtv.  I do something like this:

```
at 7:59pm
at> ivtv-tune -c 40
at> cat /dev/video0 > myshow.mpg
```

and then stop the recording when the show is over like this:

```
at 9:01pm
at> killall cat
```

You can do a lot of other things with it as well.  Say you want your computer to shutdown at midnight (maybe you are away).  Assuming you have given your computer permission to use halt and reboot you'd just do:

```
at midnight
at> sudo shutdown -h now
```

and bam, it's done.

There's also the **atq** command which shows what tasks are in the queue, and the **atrm** to remove tasks that you don't want to be done.

---

### Post by qpieus on 2007-05-03
Does the PC need to remain on until whatever date/time you chose for a future task? That is, is the task and time remember (saved) so that even if the pc is turned off, the task is not lost?

---

### Post by Mateo on 2007-05-03
The task is remembered.  But of course, the computer has to be on to **run** the task ;).

---

### Post by newlinux on 2007-05-03
how does using sudo work inside this command (such as your example with shutdown)? Does it ask you for the password inside the "at" shell or would it at midnight ask you for a password?

---

### Post by Mateo on 2007-05-03
it won't work with sudo unless you have given your user permission to use the command. 

It *might* work if you use sudo before issuing the at command like this:

```
sudo at midnight
at> sudo shutdown -h now
```

I'll have to try this later.  I would guess this works, because the at command works per user, so I'm assuming you can use it with sudo also to make it work system-wide.

---

### Post by newlinux on 2007-05-03
When I get home if I remember I'll try it out a bit. Good stuff. Thanks.

---

### Post by Mateo on 2007-05-03
I can confirm that using sudo before the at command makes the task system-wide.  If you feel like testing do this:

```
sudo at now + 1 minute
at> shutdown -h now
```

You don't have to place sudo before shutdown because you're already in sudo from issuing the at command.  Then type:

```
sudo atq
```

Which will show that the task you just made is listed as under root.  Normal tasks should have your user name (this way multiple users can all have their own tasks).

The one thing I wonder now is if one user, let's pretend their name is Jane, has a task and another user, let's pretend their name is Sam, is using the computer at the time Jane's task is supposed to run, will it?  I'm guessing it would, but I have no way of testing since I only have one user on this computer.

---

