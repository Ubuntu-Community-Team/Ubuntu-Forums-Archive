---
title: "Taking steps for getting [SOLVED] back, at least."
date: 2009-05-06
forum: The Cafe
---

### Post by BslBryan on 2009-05-06
Hello, all! :-)

Recently, I sent a PM to ubuntu-geek.  

I would post the exact message but I didn't request a copy to be sent to me.  #-o

Anyway, basically my PM mentioned a possible workaround to the [SOLVED] withdrawal.

Since the tags to solve something eat up too many database resources, I suggested that the OP to a certain thread be allowed to edit the title of the thread, but be limited to the string of characters [,S,O,L,V,E,D, and ].

I know this is harder to do than the previous way, but so many people are wanting this back that I think ten seconds of somebody's time to edit the thread title isn't too terribly difficult. :P

Also, it's a choice, completely, by the OP.  If you don't wanna, you don't gotta.  

This workaround will let people have their solved functionality back, and stop eating up database resources, causing database errors like the one that happened last night.  

Ubuntu-geek still probably hasn't even read the message, but just maybe my plan will be possible, and maybe it could be implemented. 

What do you all think?

---

### Post by Kareeser on 2009-05-06
You can edit titles, but they just won't show up in the forum itself, but rather in the header of the message... I think that's what you were getting at, right?

Personally, I'd much rather scrap the Community Games forum and bring back Other OS Talk and the Solved function. However, that's just my opinion :)

Only other problem is that it'll be hard to teach newbies why and where to edit "SOLVED" into their title strings.

---

### Post by BslBryan on 2009-05-06
True, there will be posts about it here, probably, and eventually a sticky. :P

But it would be pretty simple, I mean just click an "edit" button under the title, or even have it available in "Thread Options."  

Even before, there were stickys and posts about how to Thank people and mark something solved, because they were little icons in the bottom corner.

I know that editing the original title can be done, as I've seen it on other forums.  The reason that I'd confine it to only include [SOLVED], and maybe [solved], is because with the power to change something, there could be a thread that looks like this:
```
Windows 7 RC.

OP: Well, will you try it?

New Poster: I certainly will!

```

but they could edit the title to something like this:
```
Killing a man.

OP: Well, will you try it? 

New Poster: I certainly will!
```

...

Self-explanatory, I think. :lol:

Anyway.  Thanks for your quick reply.  I was curious as to how people would react to the suggestion, hence the poll. :-)

---

### Post by mikezila on 2009-05-06
For a group of people who put together an operating system, a kernel, and countless packages to form the most popular Linux distribution on the planet, I really, really don't see how it's impossible to program a simple checkbox that lets you mark a thread as [Solved] in the title without being able to directly edit the title.  Just add a checkbox that only the owner of the thread has when they post in the thread that adds and removes the solved text from the thread title.

forumtitle = "Oh god guys I am on fire"
solvedbanner = "[Solved] "
forumtitle = solvedbanner + forumtitle

---

### Post by BslBryan on 2009-05-06
Well, I mean, that's what used to happen, but for whatever reason or another it ate up a lot of database resources.

I don't necessarily know why, though, and that could potentially mean that my solution would cause just as many problems.  

Since most people are getting home around this time (in Eastern USA, at least) I'm going to bump this back up to the first page to get some more opinions.

:-)

---

### Post by Skripka on 2009-05-06
> **BslBryan said:**
> Well, I mean, that's what used to happen, but for whatever reason or another it ate up a lot of database resources.

I don't necessarily know why, though, and that could potentially mean that my solution would cause just as many problems.  


Because they have been trying to keep this place up and running without daily brownouts...and the way they've been able to is by removing as much metadata from threads as they can--as the server overload problems are related to the massive number of queries UbuntuForums gets on an hourly basis.

The easy solution is to have a good Wiki site that eliminates the need for 10,000 threads on how to install the Nvidia drivers, and the 20,000 threads on how to get one's wireless card working, and the 100,000 search queries daily on why KDE sucks.

---

### Post by betrunkenaffe on 2009-05-06
Umm, why not just put a "Solved" flag for the user to hit, if it is flagged, the system updates the name with [SOLVED] at the beginning.

There are a dozen ways of getting around database issues and they all require more server side work.

---

### Post by Idefix82 on 2009-05-06
> **Skripka said:**
> 
The easy solution is to have a good Wiki site that eliminates the need for 10,000 threads on how to install the Nvidia drivers, and the 20,000 threads on how to get one's wireless card working, and the 100,000 search queries daily on why KDE sucks.

Surely, the "BUMP thread", "The off-topic thread", "the no you are not allowed to post here thread" and so on are just the most stupid way to occupy a Ubuntu forum server! I agree that a good wiki would be nice, but I don't understand why scrap useful features and leave this ever-growing collection of data garbage.

---

### Post by Skripka on 2009-05-06
> **Idefix82 said:**
> Surely, the "BUMP thread", "The off-topic thread", "the no you are not allowed to post here thread" and so on are just the most stupid way to occupy a Ubuntu forum server! I agree that a good wiki would be nice, but I don't understand why scrap useful features and leave this ever-growing collection of data garbage.

You did not read my post.

_***It is my understanding that it is NOT ABOUT DRIVE SPACE.  It is about SEARCH QUERIES to the database.  NO ONE searches for the Bump Thread or the Off Topic Thread.***_

If there was good Wiki documntation, there wouldn't be a need to index the10,000s  of duplicate threads on this board and query them for help.

---

### Post by collinp on 2009-05-06
> **Skripka said:**
> The easy solution is to have a good Wiki site that eliminates the need for 10,000 threads on how to install the Nvidia drivers, and the 20,000 threads on how to get one's wireless card working, and the 100,000 search queries daily on why KDE sucks.

We *do* have a Wiki: [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/) and [http://help.ubuntu.com/](http://help.ubuntu.com/) (the last being actual documentation).

[quote=Idefix82]Surely, the "BUMP thread", "The off-topic thread", "the no you are not allowed to post here thread" and so on are just the most stupid way to occupy a Ubuntu forum server! I agree that a good wiki would be nice, but I don't understand why scrap useful features and leave this ever-growing collection of data garbage.[/quote]

Queries are requests for data from the server. Those take up space, nothing more.

---

### Post by Skripka on 2009-05-06
> **Hellow said:**
> We *do* have a Wiki: [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/) and [http://help.ubuntu.com/](http://help.ubuntu.com/) (the last being actual documentation).


Yes but it is often incomplete, or outdated, or both.

---

### Post by BslBryan on 2009-05-06
True.  It seems like since configuring nVIDIA drivers, etc.  varies from user to user they decided that the forums were a good enough place for that kind of information, and perhaps too much work to maintain both adequately, and simultaneously.

So, instead of maintaining a good wiki and a good forum, they make a wiki that doesn't get updated because the forums exist, and they sacrifice the forum and its features because people are flocking to it, and posting problems that nine times out of ten are solvable with information from existing threads.

Not that this is Ubuntu's fault, of course.  It's just that the smartest choice at the time of the choice isn't always the best option for the long run, and is such with the way the wiki is maintained.

---

### Post by Polygon on 2009-05-06
> **Skripka said:**
> Because they have been trying to keep this place up and running without daily brownouts...and the way they've been able to is by removing as much metadata from threads as they can--as the server overload problems are related to the massive number of queries UbuntuForums gets on an hourly basis.

The easy solution is to have a good Wiki site that eliminates the need for 10,000 threads on how to install the Nvidia drivers, and the 20,000 threads on how to get one's wireless card working, and the 100,000 search queries daily on why KDE sucks.

but any wiki page, no matter how good, can cover all the bases.

---

### Post by stwschool on 2009-05-06
Depending on the density of data it could be solved with a fairly minimal overhead in terms of space.

Method 1: The non-normalised approach
Add a bool to the threads table called boolSolved. It'll take 1 bit (1/8 of a byte for non-techies) per thread.

Method 2: The normalised approach
Add a table of tags (just id and name, a list featuring Ubuntu, Kubuntu, Solved, etc). Add a link table with thread_id and tag_id so for instance thread 3948 "How big is a monkey?" has tag 4 "Garbage" could be one entry in the link table. This would allow unlimited tags per thread.

Method 2 has a larger overhead unless the solved tag is used for a very very small percentage of threads, but offers greater flexibility.

---

