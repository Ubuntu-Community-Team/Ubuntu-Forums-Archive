---
title: "php alternative"
date: 2007-01-16
forum: Server Platforms
---

### Post by Ubuntuud on 2007-01-16
I am designing a website for my school (not the entire thing, just some pages for the students).
So I began...
But half-way I got to know I wont be able to use PHP.
...
So I'm looking for an alternative.
I believe they got a Windows server, so ASP would be a solution, but I'm having a hard time getting it to work on my apache server. The mods give errors and such...

Are there any other solutions?

I mainly need to edit databases and process forms...
Any ideas? Thanks in advance!

---

### Post by Brazen on 2007-01-16
Why will you not be able to use PHP?  There are lots of alternatives, but PHP is the best for database access.  Ruby would be a nice alternative, but without knowing why PHP is out, Ruby might be out, also.

---

### Post by Ubuntuud on 2007-01-16
I don't know exactly why.
I believe they just renewed the server and changed to Windows 2003. They probably don't mind installing php because they don't need it. And since I'm just a 14 year old student, thay don't give me any access :)
I'll see if I can use the old server. But I have serious doubts...

But... You never know...

---

### Post by Brazen on 2007-01-16
So you are limited by what the server admin installs on the Windows 2003 web server then?  They only thing you can do, beside talking them into installing php on the web server (which they would be nuts NOT to do), is ask them what web programming languages they do have available on the server and use one of those.

---

### Post by gnaunited on 2007-01-16
Frontpage FTW!

Seriously, I had the same problem when creating a webpage on my schools server. Your best bet is to get hosting somewhere else and just use frames on the schools server.

---

### Post by Ubuntuud on 2007-01-17
Well, I asked him (the maintainer, my physics teacher :D) and he is worried about the possible security risk of installing PHP since it is not so tightly integrated.
But.
If I make a nice enough website, he will install it.
Or, I could use the 'student server' for the informatics students. But that one wont arrive the coming 3 months (we just moved in a new building)... And it will probably be a very slow one.

I'll see tomorrow.

EDIT: hosting somewhere else is not an option btw. We don't have any money, and our school is very greedy :(

---

### Post by Brazen on 2007-01-17
Going by the history of the various options, PHP would be less of a security risk than enabling ASP.  If he was REALLY concerned about security, he would install Apache on Debian :D

As for using a slow server, unless you are getting thousands, or tens of thousands of hits per day, even old Pentium2 or Pentium3 -era machines are plenty powerful enough for serving up web pages, even dynamic database-driven ones.  I have a 500 mhz Celeron machine at home with LAMP and Samba on it, and it is plenty responsive.

---

