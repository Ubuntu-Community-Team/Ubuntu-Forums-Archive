---
title: "Can someone explain the  /dev/null"
date: 2016-01-31
forum: Ubuntu, Linux and OS Chat
---

### Post by big_z2 on 2016-01-31
I'm kind of new to linux and still learning it. I came across a device (/dev/null) that drives me crazy. 

I understand that its a bit bucket and gets rid of the unwanted outputs, but why do I really need it? Can someone please explain it to me the easiest way so that I can fully understand it?

---

### Post by ian-weisser on 2016-01-31
You don't "really need it."
It is sometimes a convenient tool to use.
Think of it like a 'mute' or 'suppress' feature. A way to stop output that you don't want.

Example: Cron provides lots of helpful output when something goes wrong. Cron has no setting to turn the output off, so some users redirect to /dev/null to mute the output.

---

### Post by SeijiSensei on 2016-02-01
Suppose I have a program that I want to run on a schedule.  I can use a program in Linux called "[cron]("https://help.ubuntu.com/community/CronHowto")" to manage when my program is run.  So I set up this program, and every time it runs it writes some output like "Program completed at 14:53:48".  If I run the program from the  terminal, I will see this text on the screen, but what does the automated scheduler do with that output?  Since it can't write to the screen, it emails that text to the owner of the program which quickly gets annoying.  I can stop this from happening by using /dev/null:

```
/path/to/some/program > /dev/null
```

which sends the output text into a black hole.

You can also create a zero-length file with /dev/null:

```
cat /dev/null > somefile
```

though you can accomplish the same thing with "touch somefile".

If the program writes output to "stdout" and error messages to "stderr" you can route the latter to /dev/null as well like this:

```
/path/to/some/program > /dev/null 2>&1
```

The "2>&1" item tells the operating system to send stderr to stdout which is then sent to /dev/null.

---

