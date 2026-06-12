---
title: "Any SED experts here?"
date: 2006-02-18
forum: The Cafe
---

### Post by xmastree on 2006-02-18
I need to filter some log files, and I want to do it by erasing every line which does not contain a certain string.

e.g. the file is like this:

10:15 Station 10 Time started
10:25 Station 15 Time Started
11:25 Station 10 Time Ended
11:55 Station 15 Time Ended

Only much, much longer (2,800 lines). I wish to generate (from this example) two files. One containing only Station 10's information and one for Station 15's. There are more stations than just those two, so I figured i could run a command on the file a few times (or from a script) to delete every line not containing "Station 10" and output the remainder to a file, which would just contain 10's data.

etc. for the rest.

Or is there an easier way?

---

### Post by jrib on 2006-02-18
From my limited knowledge,

```
sed -n '/Station 10/p' logfile > logfile_station10
```

would send all the lines that have 'Station 10' to logfile_station10.  The 'p' is the print command in sed.

This is the same as ```
grep 'Station 10' logfile > logfile_station10
```

I don't know if I am simplifying what you are trying to do too much though...

[edit] by the way I've just started reading [http://doc.novsu.ac.ru/oreilly/unix/sedawk/index.htm](http://doc.novsu.ac.ru/oreilly/unix/sedawk/index.htm) which is why I looked at this post :)

---

### Post by xmastree on 2006-02-18
[QUOTE=_jason]```
sed -n '/Station 10/p' logfile > logfile_station10
```[/quote]
Perfect! \\:D/ 

> I don't know if I am simplifying what you are trying to do too much though...
Oh yes, very much so. At first I was looking through it line by line... ](*,) 
It was when my eyes started watering that I thought there **must** be an easier way. :rolleyes: 

Thanks for saving my eyesight.

---

