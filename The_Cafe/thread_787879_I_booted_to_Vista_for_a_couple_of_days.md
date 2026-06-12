---
title: "I booted to Vista for a couple of days"
date: 2008-05-09
forum: The Cafe
---

### Post by forrestcupp on 2008-05-09
So I booted to Vista for a few days.  I mainly wanted to install SP1 and clean things up.  I hadn't even booted to Vista for a very long time.

If I'm unbiased about my experience, Vista really isn't a bad OS.  I never intended to just go back to using Vista, but I thought it would be nice for a couple of days to experience once again the fact that I could just install any program I wanted and it would work.  But it just didn't feel right.  

It wasn't long before I realized that I really missed a lot of things from Linux that Windows doesn't have.  I missed the zoom feature of Compiz/Fusion a lot.  But I was especially surprised that I missed the command line.  I have been a big proponent of the GUI, so missing the CLI kind of surprised me.  After installing SP1, Thunderbird didn't work anymore.  I could click on it and nothing at all happened.  So I opened up Windows' pitiful excuse called the Command Prompt, navigated to the Thunderbird folder, and executed it from the prompt, and nothing happened.  There was no error output telling me what was wrong.  I was forced to just uninstall it.

So I'll keep Vista around just in case I need it for some silly tech support who has never heard of Linux.  But I don't think I'll ever be tempted to get rid of Linux.

---

### Post by LaRoza on 2008-05-09
> **forrestcupp said:**
> So I booted to Vista for a few days.  I mainly wanted to install SP1 and clean things up.  I hadn't even booted to Vista for a very long time.

If I'm unbiased about my experience, Vista really isn't a bad OS.  I never intended to just go back to using Vista, but I thought it would be nice for a couple of days to experience once again the fact that I could just install any program I wanted and it would work.  But it just didn't feel right.  


When I am in Vista, which is very rarely, I feel crippled. First, I miss wmii my fingers automatically go to the appropriate keys for doing everything. Secondly, there is one desktop. It makes me feel like I am in a fish bowl.

---

### Post by logos34 on 2008-05-09
> **forrestcupp said:**
> SBut I was especially surprised that I missed the command line.  I have been a big proponent of the GUI, so missing the CLI kind of surprised me.

You're not alone.  I just got done helping a friend unlock some private folders in XP home, and what would have taken a single command in the linux terminal instead required hours of fiddling with security settings in Safe Mode.  

I'll make double sure to avoid vista if I can help it.

---

### Post by the yawner on 2008-05-09
I'm having a bad habit of typing ls instead of the appropriate command whenever I'm on a CLI. Instead of dir on a command prompt, show run on a Cisco terminal.. etc. Haha!

---

### Post by LaRoza on 2008-05-09
> **logos34 said:**
> You're not alone.  I just got done helping a friend unlock some private folders in XP home, and what would have taken a single command in the linux terminal instead required hours of fiddling with security settings in Safe Mode.  

I'll make double sure to avoid vista if I can help it.

That can be done in the command line. I am not sure exactly what the situation was, but ```

attrib /?

```

should give you some help in permission setting.

---

### Post by Tundro Walker on 2008-05-09
When it's all set up the way you like it, Vista's not bad.  But getting to that point is a pain.  God forbid you ever have to take Administrative control of a file/folder.  You have to jump through incredible hoops to do so, because "Admin" authority you're given is not real Admin authority, and gets trumped by the "Trusted Software Install" authority.

And then there's all these scheduled tasks going, doing ... something.  And the services running that you don't need.  And the security panel constantly complaining about something.

The road to getting it the way you want just seems more aggravating than with Ubuntu.  Ubuntu just requires uninstalling a few packages, and setting up the desktop for me.  In fact, I went through my checklist the other day for "Ubuntu installation" (IE: stuff I do to "fix" Ubuntu after an install, EG: to get wireless to work), and 90% of it is pointless now because the dev's have fixed the issues I was having.

EDIT: I forgot to mention, I think the most annoying part was when Windows Update was screwing up with error codes.  I went online to search for a problem, and it turns out MS had rolled out a fix for Vista Ultimate, but not for Home Premium, which I have.  MS' preferential treatment of customer base just annoys the crap out of.  Ignoring my versions' needs doesn't make me want to upgrade to Ultimate; it just makes me want to give up Windows again.  But, they finally fixed it later on in SP1.

---

### Post by logos34 on 2008-05-09
> **LaRoza said:**
> That can be done in the command line. I am not sure exactly what the situation was, but

I'm sure you're right, but then why do none of the help pages I encountered refer to it?  Despite the gui-centric nature of all the support docs, you'd think they would mention it in a case like this.  (especially if it's easier).  

A word of warning to any windows users reading this: If you have C: (system files) on a separate partition from My Documents and you reinstall, folders with 'Private' option enable will be inaccessible.

---

### Post by beercz on 2008-05-09
Did it hurt?

---

### Post by koenn on 2008-05-09
> **LaRoza said:**
> That can be done in the command line. I am not sure exactly what the situation was, but ```

attrib /?

```
should give you some help in permission setting.

attrib sets file attributes (Read-Only, Hidden, ...)
the command to manage filesystem security is CACLS (Change Access Control Lists), and (but only available in resource kits ) XCACLS (Extendeed CACLS) and TakeOwn (take ownership).

ACLs are far more complex that the simple Unix permission bits : There are something like 15 different permissions, each of which can be applied to groups and users, and permissions can be inherited from parent folders by files, subfolders, or both, and can be applied to current directory only, directory + files, and/or directory+subdirectories, or a combination of those. That's without considering the DENY settings that overrule the ALLOW settings.
It's a pain, really. Changing permissions on system files (which, in XP at least, you sometimes want to do to get stuff working without all users being administrators) can easily get you to the point where everything stops working and re-installing is easier and faster than getting the permissions right.

---

### Post by Calash on 2008-05-09
That is the one thing I really miss when at work.  On my Ubuntu I have Compiz set to do Expose when the mouse goes to the top left, and to rotate all the windows with the top right corner.   At work, I am constantly moving the mouse to try and change applications, only to remember I have to go to the task bar and click.


I miss my Compiz when on Windows :(

---

### Post by Tundro Walker on 2008-05-10
I stopped using my Vista machine a while back when I switched back to my Linux box for Hardy's arrival.  I haven't found a reason to go back to the Vista box.  All I'm really doing is surfing the net, and I can do that safer with Linux.

Really, the Vista comp was a stupid purchase to begin with, because I just got it for some gaming, which turned out to be pretty boring.  And now it just sits there doing folding projects all day by itself while I neglect it and play on my Linux box.  Guess I should install Ubuntu on it one of these days, but frankly, I'm trying to cut back on my computer time so I can spend it doing other things.

One thing I have noticed, since using Linux more now, I'm not posting a blog entry every other day complaining about how aggravating Windows is.  In fact, I'm back to just "using the computer".  No more defrag, virus scan, etc time-consuming BS.  It's quite tranquil.

---

