---
title: "hard lesson learned using CLI blindly"
date: 2021-03-27
forum: Ubuntu, Linux and OS Chat
---

### Post by T6&amp;sfpER35% on 2021-03-27
thought i'd share the danger of running commands that you not sure of what it actually does .
so the other day i installed protonvpn via [this]("https://protonvpn.com/support/official-linux-client/") site ,played around with it for a bit and found it didn't suit my needs .
uninstalled it with the commands found on same fore mentioned site, only i made a typing error (long story why i didn't copy paste) and inserted a space between ~/ and .directory
command i'm talking about is ```
[COLOR=#000000][FONT=SFMono-Regular]rm -rf ~/.cache/protonvpn[/FONT][/COLOR]
``` 
the space , together with the -rf command,as i later learned , means it will force remove your home (~/) directory and then the .cache/protonvpn files.
be careful when using -rf ,actually, never use it lol
lucky for me i had my home directory backed up ,so did a clean install and was back to normal in no time.
PS. btw , i tried restoring with timeshift , then realised my "home" is not included in timeshift's settings.

moral of the story ,  a simple space inserted where it shouldn't be,could wipe your system

](*,)

---

### Post by rbmorse on 2021-03-27
Actually, the moral of this story is there is no substitute for testing and validating your backup scheme before you *need* it. 

You got lucky in that you had an alternative backup of /home.  Otherwise, you would have been in trouble because you assumed Timeshift was doing something it was not (and does not by developer's intent). A test restore of a Timeshift backup would have made the issue obvious. 

Your initial mistake was one anybody could have made. It's easy, especially when working on a tablet or smaller laptop, to miss an inadvertent space character in a command string.  Gnu himself knows I done it many times...and worse. An effective *and tested* backup is all that keeps anyone from turning a simple typing error into a significant disruption of one's day, or worse. Your experience is a timely reminder that little things can lead to big problems and can happen to anyone, at any time, and in any circumstance. 

TheFu has written volumes here about backup.  If you're really interested in what's required for an effective backup strategy it is worth the time to search out some of his more recent posts on the subject and spend some time with them.

---

### Post by mastablasta on 2021-03-30
best is:
are you sure?
Y
prompt:_

wait... never mind, it's done.

---

### Post by scorp123 on 2021-03-30
When I was a newbie back in 1996 (long time ago, LOL) I wanted to wipe all my "dot" config files (stuff like ".bashrc", ".profile", ".vim" and so on) ... So I typed in this ***DANGEROUS*** command:
```
rm -rf .*
```

**[COLOR=#FF0000]DO NOT TRY THIS!! [/COLOR]**

What I did not consider: The directories one level up ".." are included in a ".*" wildcard construct. 

And I was "root" at that time.... ](*,)

Things I learned that day:

[LIST]
[*]NEVER EVER work as "root" unless you REALLY need to and YOU KNOW EXACTLY what you are doing... 
[*]don't use wildcards ("*") if you don't really have to, you might accidentally affect waaaaay more files than you actually wanted... 
[*]"rm" is really really fast at deleting stuff :shock: 
[*]Any backup is only as good as its working restore procedure ... 
[/LIST]

Long story short: Everyone here has messed up at some point. Consider it being part of the initiation ritual :lolflag:

---

