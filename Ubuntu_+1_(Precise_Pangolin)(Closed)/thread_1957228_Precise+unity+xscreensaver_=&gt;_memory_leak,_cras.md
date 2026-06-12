---
title: "Precise+unity+xscreensaver =&gt; memory leak, crash"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shadowfirebird on 2012-04-12
Fiddling with xscreensaver and previewing screensavers seems to cause a massive memory leak and then, of course, a hang / crash.

Can anyone shed any light on this?  It doesn't happen in Unity 2D, so it would appear to be Compiz related.   It might be just one or two screensavers (somewhere in the "Is", alphabetically.  Interferometry?)

I can live without Compiz, but not without the basic configuration options in Unity 3D!


_**UPDATE**_
Running top while duplicating the problem didn't work as well as I had hoped.  The lockout happens so quickly that top freezes up before it gets a chance to update.  (Or, it's some other freeze, not a memory leak?)

I *can* now confim that AFAIK it's just one screensaver: interferometry.  Pressing 'preview' or 'settings' on this one screensaver causes a memory consumption increase of > 1Gb, and eventually freezes the system entirely, forcing a reboot.  So I suppose that that's something.

---

### Post by NHclimber on 2012-04-12
Please file a bug against compiz with screenshot of top (press 'M' to sort by memory usage).
```
ubuntu-bug compiz
```

---

### Post by shadowfirebird on 2012-04-13
> **NHclimber said:**
> Please file a bug against compiz with screenshot of top (press 'M' to sort by memory usage).
```
ubuntu-bug compiz
```

Love to.  Sorry to be thick: where exactly do I file this bug report?  I mean, I could take a guess.  But it might be wrong.

EDIT: Wow.  Sorry, I *was* being a bit behind the times.  I love the idea of a command that files a bug report.   Will do.

---

### Post by grahammechanical on 2012-04-13
Where did you get the screensavers from. It was my understanding that 12.04 does not come with a screensaver option because it was decided that they were no longer necessary.

Have you tried running this command?

```
top
```

That will give you a real time listing of CPU and memory usage and you might be able to prove that this or that is using excessive memory.

There were issues a few months ago with Compiz slowly using more and more memory. They seem to have been fixed.

At the moment on my system Compiz is using 12% memory But it can go higher.

Make sure that it really is Compiz that is causing this and that there really is a memory leak.

A lot of bug reports do not do any good because they do not provided enough information to help the Bug Squad work out which package maintainer is responsible for fixing the bug or the report does not give the developer enough information to reproduce the bug.

What if this problem is being caused by this screensaver. How is are the Compiz developers going to reproduce the problem that you are having?

Inaccurate bug reporting just clogs up the system and slows down the fixing of bugs.

Regards.



Regards.

---

### Post by shadowfirebird on 2012-04-13
> **grahammechanical said:**
> Where did you get the screensavers from. It was my understanding that 12.04 does not come with a screensaver option because it was decided that they were no longer necessary.

I don't mean to seem rude, but this is kind of an odd question.  This is Linux we're talking about!  I didn't "get" it "from" anywhere.  I just typed 'apt-get install xscreensaver'.  

> Make sure that it really is Compiz that is causing this and that there really is a memory leak. 

Given that Unity's system load indicator was showing a topped-out dark green in it's memory meter, and that simple commands were taking two minutes or more to complete, I'm pretty certain my memory was overrun ;)    Also, I tried it again, and it did it again ... and a third time in Unity 2D and it didn't.  So it seems at least likely that compiz might have something to do with it.

But I'll try and get a 'top' output to the ubuntu-bug program today.


> A lot of bug reports do not do any good because they do not provided enough information to help the Bug Squad work out which package maintainer is responsible for fixing the bug or the report does not give the developer enough information to reproduce the bug.

What if this problem is being caused by this screensaver. How is are the Compiz developers going to reproduce the problem that you are having?

Except that this was not a bug report.  It was a request for help.  If I had enough information to report a bug, I would have done so in Launchpad.  Thanks to some of the other people responding to my post, I can now do that.

> Inaccurate bug reporting just clogs up the system and slows down the fixing of bugs.

Thank you for your help and support in this matter. :/

---

### Post by ubuntu27 on 2012-04-13
Hi shadowfirebird. So did you report the bug?

It will be nice if you could post the URL here for others to confirm.

---

### Post by shadowfirebird on 2012-04-13
> **ubuntu27 said:**
> Hi shadowfirebird. So did you report the bug?

It will be nice if you could post the URL here for others to confirm.

Sure!   [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/980895](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/980895)

---

