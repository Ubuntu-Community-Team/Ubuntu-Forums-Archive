---
title: "Is there a power off command?"
date: 2009-11-23
forum: The Cafe
---

### Post by dragos240 on 2009-11-23
I'm curious if there is a power off command, that actually shuts the computer off without killing all the processes, and not unmounting filesystems. Literally telling the computer to shut off, without doing anything else.

---

### Post by Skripka on 2009-11-23
> **dragos240 said:**
> I'm curious if there is a power off command, that actually shuts the computer off without killing all the processes, and not unmounting filesystems. Literally telling the computer to shut off, without doing anything else.

Hold the Power button for ~5-10 seconds.

---

### Post by vigalance on 2009-11-23
sudo shutdown -h now

---

### Post by dragos240 on 2009-11-23
> **vigalance said:**
> sudo shutdown -h now

Trying it.

---

### Post by alphaniner on 2009-11-23
> **dragos240 said:**
> > sudo shutdown -h now Trying it.

No, that's a proper shutdown.

Maybe you could do Alt+SysRq+REISUO without the EISU.

---

### Post by earthpigg on 2009-11-23
have you tried hitting it with a sledge hammer? :D

---

### Post by Bachstelze on 2009-11-23
"It's easy to solve the halting problem with a shotgun."

-- Larry Wall

---

### Post by pizza-is-good on 2009-11-23
> **vigalance said:**
> sudo shutdown -h now

Now you put an icon on your desktop that will execute the command. oh wait! That already exists! Username>Shutdown>Shutdown.

OK, sorry for the sarcasm....:lolflag: it is actually interesting stuff. Not that I'd ever use it, but............

---

### Post by lykwydchykyn on 2009-11-23
> **vigalance said:**
> sudo shutdown -h now

shutdown is a safe shutdown.  It will kill processes, unmount drives, etc.

you want:
```

sudo halt -f

```

---

### Post by koenn on 2009-11-23
'shutdown -h' will go through the entire cleanup of stopping services, unmounting filesystems, bringing down network interfaces, ...

read
```
 man poweroff
```




edit: oops, late ...

---

### Post by fatality_uk on 2009-11-23
> **dragos240 said:**
> Trying it.

[http://manpages.ubuntu.com/]("http://manpages.ubuntu.com/")
Do a search for shutdown for as much info as you need.

---

### Post by Skripka on 2009-11-23
> **lykwydchykyn said:**
> shutdown is a safe shutdown.  It will kill processes, unmount drives, etc.

you want:
```

sudo halt -f

```

For the OP, FYI--this is not something you want to do to a system with data on it that you care about...all manner of bad things have the potential to happen...

---

### Post by Dharmachakra on 2009-11-23
Why would you want to do this?

---

### Post by ratcheer on 2009-11-23
Another (old fashioned) way is: sudo init 0

Tim

---

### Post by NoaHall on 2009-11-23
I would write what I did before, but I presume a mod deleted it(as I hit post before putting the warning there, so good catch mod)

Anyway, there's ways of doing it, but it could cause major system damage.

I suggest, if you REALLY want to do this, you make a old system, load arch or something on it quick, and then do a quick search for "Rasing Elephants Is So Utterly Boring" Note - this could well destroy your system.

---

### Post by dragos240 on 2009-11-23
> **Dharmachakra said:**
> Why would you want to do this?

Just because I'm curious.

---

### Post by ZankerH on 2009-11-23
Asking people for help with destroying your system. There's a new one.

Is this one of those "I forgot my credit card password, is there a way to figure it out?" threads?

---

### Post by fatality_uk on 2009-11-23
> **ZankerH said:**
> Asking people for help with destroying your system. There's a new one.

For the members of the tin-foil hat brigade,

> DESCRIPTION
shutdown arranges for the system to be brought down in a safe way.

All logged-in users are notified that the system is going down and,within the last five minutes of TIME, new logins are prevented.

There is NOTHING wrong with using shutdown in the correct way.

---

### Post by koleoptero on 2009-11-23
> **ratcheer said:**
> Another (old fashioned) way is: sudo init 0

Tim
I remember using this (or something like it) once or twice when my power button wasn't properly connected to the m/b of a pc I had 7years ago, and the proper shutdown wouldn't work.

---

### Post by NoaHall on 2009-11-23
> **fatality_uk said:**
> For the members of the tin-foil hat brigade,



There is NOTHING wrong with using shutdown in the correct way.

He's not asking about shutdown. He's asking(effectively) how to bring down a system by simply turning it off without protecting the system filesystem and so on.

---

### Post by RiceMonster on 2009-11-23
Does anyone know of an object that I could hit my computer with and will make it stop running?

---

### Post by NoaHall on 2009-11-23
> **RiceMonster said:**
> Does anyone know of an object that I could hit my computer with and will make it stop running?

Car, I guess. Usually works for me, but some say a hammer is faster.

---

### Post by dragos240 on 2009-11-23
I wonder if /g/ will have an answer........

---

### Post by Skripka on 2009-11-23
> **NoaHall said:**
> Car, I guess. Usually works for me, but some say a hammer is faster.

You can borrow the 20lb sledge hammer in my office if you like.

---

### Post by dragos240 on 2009-11-23
Okay. Well, I asked /g/ and they said to use alt + sysrq + o, nothing happened. So then they told me to update my kernel.sysrq. I did, and it worked! YESH!

---

### Post by NoaHall on 2009-11-23
Yes... which is pretty much what I posted the first time. Now, are you pleased with yourself?

Oh wait! Turns out I posted in the wrong thread! Look here - [http://ubuntuforums.org/showpost.php?p=8374271&postcount=33](http://ubuntuforums.org/showpost.php?p=8374271&postcount=33)

***DANGER!***
I guess, you could try 
"alt + sysrq/printscr" + r, then + b
---DANGER!---
That one will reboot the system.

---

### Post by tom66 on 2009-11-23
For one of my old machines, I've got a 3 second shutdown. That includes syncing to the disks. 

Basically:

```
sync
swapoff /dev/sda7
poweroff -f
```

---

### Post by dragos240 on 2009-11-23
> **NoaHall said:**
> Yes... which is pretty much what I posted the first time. Now, are you pleased with yourself?

Oh wait! Turns out I posted in the wrong thread! Look here - [http://ubuntuforums.org/showpost.php?p=8374271&postcount=33](http://ubuntuforums.org/showpost.php?p=8374271&postcount=33)

***DANGER!***
I guess, you could try 
"alt + sysrq/printscr" + r, then + b
---DANGER!---
That one will reboot the system.
It's okay. It's solved. See my last post.
/thread

---

### Post by NoaHall on 2009-11-23
I know. I did post it ages ago... it would have solved the thread about 10 posts ago.. I just did it in the wrong thread.

---

### Post by CharlesA on 2009-11-23
I thought the OP meant making the machine hibernate from the command-line. I was wrong. :o

---

### Post by t0p on 2009-11-23
I don't understand what this "danger" is that some of you are talking about.  A few times now there have been power cuts that effectively did the same as what's being discussed here (I haven't got an interruptible power supply) and my computer hasn't died or anything.  I mean, isn't this what journalled file systems were invented for?

---

### Post by tom66 on 2009-11-23
Sort of, but journaled file systems aren't fool proof - they can still leave the disk in an inconsistent state, it's just not so common.

---

