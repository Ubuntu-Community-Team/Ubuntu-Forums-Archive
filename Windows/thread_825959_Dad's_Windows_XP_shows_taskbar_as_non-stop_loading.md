---
title: "Dad's Windows XP shows taskbar as non-stop loading (unusable)"
date: 2008-06-11
forum: Windows
---

### Post by Tuxoid on 2008-06-11
My dad is dual-booting Windows XP Home and Ubuntu Hardy. He has been enjoying both Windows and Ubuntu. Windows has been acted strange the past few days though. While loading Windows, the Desktop just crawls. I don't know if it's even loading past showing a Desktop Background most times, or if we're lucky, showing the taskbar. With a huge spell of luck, he'll occasionally be able to fully use Windows. He can't even click on anything at all. Ctrl+Alt+Del doesn't even work.

My dad maintains his computer very well. He performs Virus and Spyware scans daily, Defraging weekly, always running a firewall, and cleans the registry daily. I don't get why it's slowing down so much.

I'd like to know, is there anything I could look at or do to backtrace and fix this?

---

### Post by KingTermite on 2008-06-11
That sounds awfully odd. If he's so diligent about maintenance, it sounds like a hardware problem (or a virus that slipped through his AV).

Have there been any noticeable differences in Ubuntu?

---

### Post by melrom on 2008-06-11
Does he use CCleaner? I usually use this to get rid of stuff and also to check for registry errors.

I wouldn't guess hardware, as my Windows gets buggy like this all the time. But it's worth a shot, comparing it to Ubuntu. Actually, I reinstalled Windows, because my virus scan [mcaffee] started going nuts and hogging all of CPU usage. But I agree...this sounds virus-esque unless you've got a program that's running wrong and hogging all the usage. Consider downloading a program to monitor CPU usage since you can't do it from the GUI. Or you could do it from terminal: 
```

Start->Accessories->Command Prompt
tasklist /? 

```

find the appropriate one. I believe it's ```
 tasklist /s computernamehere 
```, but I might be incorrect, as I'm not used to doing maintenance from the command prompt. This should bring up the sysprocess list that would be obtained through control-alt-delete, though.

also, if you suspect something is hanging, try looking for the thing that is not responding:

```

tasklist /fi "status eq not responding"

``` 

hopefully, this can point you in the right direction. tasklist can be a nice tool.

---

### Post by Tuxoid on 2008-06-11
> **KingTermite said:**
> That sounds awfully odd. If he's so diligent about maintenance, it sounds like a hardware problem (or a virus that slipped through his AV).

Have there been any noticeable differences in Ubuntu?

No, he's says Ubuntu has been fine. He said that it has seemed to become faster.

yes he uses CCleaner.

---

### Post by Vince4Amy on 2008-06-11
> and cleans the registry daily.

That's probably the problem, this is just not necessary not every day anyway.

---

### Post by melrom on 2008-06-11
> **Tuxoid said:**
> No, he's says Ubuntu has been fine. He said that it has seemed to become faster.

yes he uses CCleaner.

CCleaner backs up the registry, so he could easily restore, if that's the problem. 

Did you try the tasklist commands?

---

### Post by Tuxoid on 2008-06-11
I tried the tasklist commands, but Windows did not recognize the commands. I ran CCleaner and it seemed to fix the problem.

edit: The father says: Nothing running...!

He has tried to run CCleaner, Spybot, Firefox. No Window pops up, no task in the task bar shows up.

---

### Post by melrom on 2008-06-11
Okay, that's _not_ good. Does he have previous reg. backups saved somewhere on his computer??

-MelRom

---

### Post by Tuxoid on 2008-06-12
yes I just applied one from Friday. It's fully working now.

---

### Post by melrom on 2008-06-12
Awesome! :)

---

