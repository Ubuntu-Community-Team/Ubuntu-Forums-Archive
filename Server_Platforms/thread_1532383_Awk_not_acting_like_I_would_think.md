---
title: "Awk not acting like I would think"
date: 2010-07-16
forum: Server Platforms
---

### Post by terazen on 2010-07-16
If I have a file that looks like this:
one   two   three    four
one   two   three    four
one   two   three    four
one   two   three    four

And I want to have the output say:
four one two
four one two
four one two
four one two

I would normally use:
awk '{ print $4 , $1 , $2 }'

It's not working right for some reason.  When I use the above I'm seeing this:
  one   two
  one   two
  one   two
four  one   two

When I open the file in vi I see ^M newline chars at the end of the first 3 lines only so I assume that's the cause, but I'm not sure.  Any ideas?

---

### Post by KiLaHuRtZ on 2010-07-16
Open the file in vi/vim and do this...

```
:%s/Ctrl-V[ENTER]//g
```

Where Ctrl-V is Control + V then hit enter to get the ^M.

```
awk -F " " '{print $4", "$1", "$2}'
```

---

### Post by terazen on 2010-07-16
Thank you!  That was it.  I ended up doing it like this:
```
awk '{sub(/^M/, ""); print $4 , $1 , $2 }'
```
It had to be scripted because the input comes from a form on a webpage I made so I just put your subs in there.  How this worked for 4 years and stopped today is just strange.  Maybe some software package changed when I update/upgraded earlier this week.

---

