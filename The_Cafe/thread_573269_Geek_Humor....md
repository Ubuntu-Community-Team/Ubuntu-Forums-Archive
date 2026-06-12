---
title: "Geek Humor..."
date: 2007-10-11
forum: The Cafe
---

### Post by Sporkman on 2007-10-11
:lol:

[img]http://imgs.xkcd.com/comics/exploits_of_a_mom.png[/img]

---

### Post by corney91 on 2007-10-11
You gotta love XKCD :D

---

### Post by DoctorMO on 2007-10-11
"Little Bobby Tables" :KS

---

### Post by Sunnz on 2007-10-11
LMAO... ah jeez, I am such a geek... :(:(:(

---

### Post by Sporkman on 2007-10-11
> **corney91 said:**
> You gotta love XKCD :D

Ah, so that's where it came from!

I'll replace the attachment with a link...

---

### Post by Dragonbite on 2007-10-11
Oh, that is sooo good!  Especially because I have a son (named Thomas) who is a little hacker!

---

### Post by Kingsley on 2007-10-11
Oh god, I got none of that.

---

### Post by Sporkman on 2007-10-11
> **Kingsley said:**
> Oh god, I got none of that.

It's about a hacking technique called "SQL injection", where a hacker can enter a data item that subverts the syntax of the subsequent database access - in this case, the woman injected a database command to delete the whole student database table.

---

### Post by Sporkman on 2007-10-11
Here's a more detailed explanation:

[http://en.wikipedia.org/wiki/SQL_injection](http://en.wikipedia.org/wiki/SQL_injection)

---

### Post by Tundro Walker on 2007-10-11
Had a similar issue where I worked.  They used a sql database to store values that .ASP pages used to generate content.  There was a "description" field for something, and I wanted to provide description to end-users, but also wanted to track internal descriptions for my own dept's purposes.  So, since anything in the "description" field got translated as HTML when used, I originally used !-- to make hidden comments.  The pages got all hosed up, because it seems their system took the "--" sql comment command as precedence over the "!--" HTML commenting command.  Dumb.  So, I had to clean a bunch of stuff up in the db back-end, because it not only hosed up the end-user output, but also the front-end we used to fill in the stuff.  I ended up switching to <META> tags to hide my content.

But, it never dawned on me to piggy-back SQL-executable statements...I'll have to keep that in mind.  I'm sure the IS folks would love me more than they already do if I start embedding executables in stuff.  LOL!

---

### Post by RAV TUX on 2007-10-11
"Geek, taking the "r" out of Greek"

---

