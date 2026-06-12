---
title: "&quot;Permission denied&quot; trying to access external USB drive"
date: 2012-05-14
forum: Security
---

### Post by bertmung on 2012-05-14
I'm running 11.10 with a AMD Athlon(tm) XP 2400+ processor and 750 MiB of memory.

I have two external USB hard drives, NewVolume and My Book. 

The external hard drives have stopped showing up on the GUI. My Book stopped appearing and I assumed the connection was loose. NewVolume was working fine and I didn't need My Book that often.

I checked the connection and My Book was indeed plugged in properly. Now neither appears on the GUI.

From a terminal both appear in the output of the ls command.  However, when I try cd to NewVolume I get the message: bash: cd: NewVolume Permission denied

Bash doesn't even recognize My Book (perhaps the space in the drive name?)

I would be very grateful for any suggestions.

---

### Post by CharlesA on 2012-05-14
There is a space probably.

```
cd /media/My\ Book
```

As for the permission, problem, are these NTFS drives? Permissions are set on mount for those.

---

### Post by bertmung on 2012-05-14
I beg your pardon.

I had assumed that since NewVolume was showing up in an "ls" on the media directory that it must of been plugged in. Plugged in, NewVolume is now working just fine.

---

### Post by roelforg on 2012-05-14
> **bertmung said:**
> I beg your pardon.

I had assumed that since NewVolume was showing up in an "ls" on the media directory that it must of been plugged in. Plugged in, NewVolume is now working just fine.

Sometimes the automounter doesn't clean up it's unused directories, can be mighty confusing (well, it would be if i didn't mostly use the cli and mount them myself).

(i fell for that one once as well)

---

### Post by bertmung on 2012-05-14
Thanks for that.
when in the directory media

cd /media/My\ Book yields the Permission denied message.

I even tried it with the exact same cables that work on NewVolume. Same result.

I'm assuming these are NTFS drives. They both have the formatting they came with.

---

### Post by bertmung on 2012-05-14
Problem solved, I think.

I tried to power off My Book and it wouldn't. I unplugged the power. Plugged it back in and now it works.

Everything is working as far as I can tell. Are there any problems possibly lurking that could come back to haunt me later?

Thank you roelforg and CharlesA for your suggestions.

---

### Post by bertmung on 2012-05-17
I'm going to mark this as solved. The non-functioning drive has been operating without problems. Something else has come up, but that's an issue for a new thread.

Thanks,

---

