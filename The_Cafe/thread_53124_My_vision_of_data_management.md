---
title: "My vision of data management"
date: 2005-07-30
forum: The Cafe
---

### Post by man.life on 2005-07-30
I'm going to give you an example of how would be THE way to store (meta)data. And I will do it with the film Closer.

Let's think you want to check what movies you have, where Natalie Portman appears and Mike Nichols directs. 

Right now, doing that with Nautilus is impossible. Beagle can't do that either. Storage is a baby.

First, take a look at attachment #1 and think this is the way you see files when you edit metadata. Maybe in Nautilus, maybe in a program called "Metadata Organizer".

Now, in Nautilus you open a sidebar to sort files. (attachment #2)

You go to Movies (attachment #3) >> Actors >> Natalie Portman and you check the option. (attachment #4)

All movies where NP appears will show up. (e.g. Closer, Star Wars I, II, III show up)

Then you go to Director >> Mike Nichols and check the option. Only Closer will show up and the two search factors will be highlighted. (attachment #5)

Now, think about being able to do this with all your files. Questions like...

Documents written in 2004 about Ubuntu
Photos taken in 2002 where I appear

...would be a matter of some clicks. And a program that could answer questions directly (GNOME Storage) would be much easier to write.

---

### Post by TravisNewman on 2005-07-30
There are some specific ideas about this. I think rather than clicking checkboxes, having either a plain text box and/or a drop down menu would be better.

There are already photo organizers, media organizers, etc, that can do this, but unfortunately no full-on data management. Beagle would rock hard with this. Er... rock hardER.

---

### Post by sonny on 2005-07-30
Is that a real program or is it beta?? Cuz it sounds too cool.

Idea: Maybe movies and documents should have something like idtag like the mp3 files have, and most audio formats (wma, and so on), it would help in this quest. Can tags be added to movies and documents?

---

### Post by TravisNewman on 2005-07-30
if I read it correctly, this isn't even a beta, just a mockup.

But tags can be added to ANYTHING if it's done in the framework of a database. The file itself actually doesn't have any tags, but it's entry in the database does, and that gets indexed so that searching for files is almost instant. That's kinda how Beagle works already, but it hasn't lived up to its full potential yet. But when it does... oooohhhhh..

---

### Post by sonny on 2005-07-30
[QUOTE=panickedthumb]if I read it correctly, this isn't even a beta, just a mockup.

But tags can be added to ANYTHING if it's done in the framework of a database. The file itself actually doesn't have any tags, but it's entry in the database does, and that gets indexed so that searching for files is almost instant. That's kinda how Beagle works already, but it hasn't lived up to its full potential yet. But when it does... oooohhhhh..[/QUOTE]
So if you want to add tags you only have to use a database manager, right? Is beagle in the repo's? Can you give me a page so I can found out more about this?

---

### Post by man.life on 2005-07-30
[QUOTE=panickedthumb]There are already photo organizers, media organizers, etc, that can do this, but unfortunately no full-on data management.[/QUOTE]

Yeah, this is something like "F-Spot for all your files". What I called "Metadata organizer".

---

### Post by TravisNewman on 2005-07-30
[QUOTE=sonny]So if you want to add tags you only have to use a database manager, right? Is beagle in the repo's? Can you give me a page so I can found out more about this?[/QUOTE]
 beagle is in breezy and has been backported (see the backports forum) 

beaglewiki.org has loads of info about it.

It's not as simple as just using a database manager to add tags. As far as I know this hasn't been implemented in Beagle, or anywhere else. But I don't think it would be all that hard to add it (though I could be wrong, I'm not an uber-leet programmer).

---

### Post by sonny on 2005-07-30
[QUOTE=panickedthumb]beagle is in breezy and has been backported (see the backports forum) 

beaglewiki.org has loads of info about it.

It's not as simple as just using a database manager to add tags. As far as I know this hasn't been implemented in Beagle, or anywhere else. But I don't think it would be all that hard to add it (though I could be wrong, I'm not an uber-leet programmer).[/QUOTE]
Thanks panickedthumb, they're right when they say the thumb is the most useful finger, you've probe it again.

---

### Post by TravisNewman on 2005-07-30
[QUOTE=sonny]Thanks panickedthumb, they're right when they say the thumb is the most useful finger, you've probe it again.[/QUOTE]
 *LOL*

---

### Post by Omnios on 2005-07-30
Interesting that could have a lot of uses. Might prove interesting for a app modual.

---

### Post by poofyhairguy on 2005-07-30
[QUOTE=man.life]I'm going to give you an example of how would be THE way to store (meta)data. And I will do it with the film Closer.

Let's think you want to check what movies you have, where Natalie Portman appears and Mike Nichols directs. 

Right now, doing that with Nautilus is impossible. Beagle can't do that either. Storage is a baby.

First, take a look at attachment #1 and think this is the way you see files when you edit metadata. Maybe in Nautilus, maybe in a program called "Metadata Organizer".

Now, in Nautilus you open a sidebar to sort files. (attachment #2)

You go to Movies (attachment #3) >> Actors >> Natalie Portman and you check the option. (attachment #4)

All movies where NP appears will show up. (e.g. Closer, Star Wars I, II, III show up)

Then you go to Director >> Mike Nichols and check the option. Only Closer will show up and the two search factors will be highlighted. (attachment #5)

Now, think about being able to do this with all your files. Questions like...

Documents written in 2004 about Ubuntu
Photos taken in 2002 where I appear

...would be a matter of some clicks. And a program that could answer questions directly (GNOME Storage) would be much easier to write.[/QUOTE]


I believe this sort of thing will come when media content is delivered by the companies rather than P2P. The closest I've seen to what you describe is iTunes.

---

### Post by man.life on 2005-07-30
Below is an accurate mock-up of the Metadata Organizer. And, is it difficult to create a database with metadata for your files? Is it difficult to make Nautilus be able to access it?

Let's hope something like this and Beagle make things easier.

---

