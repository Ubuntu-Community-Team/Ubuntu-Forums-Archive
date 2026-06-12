---
title: "Dirvish, should start at 22:00, starts at 03:30!"
date: 2023-12-06
forum: Server Platforms
---

### Post by civilpolisen on 2023-12-06
Why is Dirvish delayed at start? 
Why is Dirvish two days behind? One day is the normal... ?

I did some Pi-talk:

> Me: /dev/vdb        4.9T  4.3T  371G  93% /srv 
Maybe there is too little space left on the device? 

> AI: Bingo! I think you hit the nail on the head. It looks like the /srv partition on
 the server in question is 93% full, which is dangerously close to the point where there's
 no more room for the backup process to write data. That's definitely going to cause 
performance issues, since the server will start trying to juggle data around to make room. 
If you're able to free up some space, that should help speed things up. Is there anything 
that can be moved off of that partition, or perhaps a larger hard drive that can be
 added to the server?

[https://pi.ai/talk](https://pi.ai/talk)

---

### Post by MAFoElffen on 2023-12-06
In my maintenance backup scripts:
I setup some storage space check routines as functions to be called. Eval'ed what needed to be backed up, and the space that was available in the backup storage pools.

I setup a routine to email me the results or any warnings/error through my smtp server to my admin account.

I called these:
- At the start, I have a storage space check to see what was available.
- At the end, I have a storage space check to see what was left.

Why? I don't want to run a backup if there isn't enough room to do it. At the end of a backup, I want to know then, before the next maintenance cycle, if I needed to add more storage to my backup pool.

I got emailed about the conduct of the maintenance jobs. When I got to work, the first thing I did was to check the admin email account to see what happened the night before... I wanted to know, hopefully before things happened to prepare for something, better than after an unforeseen failure that could have been prevented. I wanted to be "aware".

I setup my storage thresholds based on what it's job was, and what it needed to do.

Just some things to think about...

---

### Post by civilpolisen on 2023-12-07
Thank you for your input! It's valuable!

```
civilpolisen@jango-fett:~$ dirvish-status-t0
 dirvish-kin success 20231206 0G   20.04
 dirvish-t1 success 20231206 0G   20.04
 fors ...... success 20231206 0G   20.04 KVM-server
 kind ...... success 20231206 0G   20.04 KVM-server
 tull1 ..... success 20231206 0G   20.04 KVM-server
/dev/vdb        492G  310G  157G  67% /srv
civilpolisen@jango-fett:~$ 

```

I have a little script that I trigger from the Terminal at my workstation. It's similar to yours, I can live without the e-mails...
We have three of these kinds and it gives me an overview that is good enough for me. As for above, it says 0G and of-course, that's not an optimal solution...
But in this case, the last line is helpful enough! :-) 

There are 27 servers backed up at the T1 -machine. My solution would be to move backed up servers from T1 to T0 ... that will help me in the short term! We have plenty of disk, but some are speedy SSDs and some are slow-food-diesel hangarounds from the past...

---

