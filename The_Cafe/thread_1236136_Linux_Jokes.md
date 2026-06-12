---
title: "Linux Jokes"
date: 2009-08-10
forum: The Cafe
---

### Post by chessnerd on 2009-08-10
I've got two:

> Being a Linux user is sort of like living in a house inhabited by a large family of carpenters and architects. Every morning when you wake up, the house is a little different. Maybe there is a new doors, or some walls have moved. Or perhaps someone has temporarily removed the floor under your bed...

> Three friends, Bill, Steve, and Linus, walk into a bar. The bartender asks them what they would like to drink. Bill orders a basic beer, Steve orders an expensive imported draft, and Linus gets a glass of water. Bill and Steve are confused by this and ask why Linus doesn't want a drink. 

He responds, "Don't you see? This water is free. I'll be able to go to my baker friend to get yeast, a farmer friend to get hops, and another friend has got a brewery. Together, we can turn this glass of water into the best beer in the world! It'll only take a few days and it'll be totally free!"

Bill and Steve roll their eyes and say, "Linus, one of these days you're going to have to understand that the idea of free beer isn't that important."

Anyone else know some Linux jokes?

---

### Post by jrusso2 on 2009-08-10
I always like the Linux airlines one where you have to build your own seat on the plane with a set of instructions.

The seat is very comfortable and the ride is free.  But when you tell your friends all they can say is you had to do what with the seat?

---

### Post by MikeTheC on 2009-08-10
Hmm...

> **Joke #1]Two guys walk into a bar. The third one ducks.[/quote]

[quote=Joke #2]**PENGUIN 1:** Squak squak squak screech squak squak *shake head* squak.
**PENGUIN 2:** Screech squak?
**PENGUIN 1:** Squak said:**
> ***

Sorry, I'm right out of Linux jokes now.

---

### Post by DeadSuperHero on 2009-08-10
> **MikeTheC said:**
> Hmm...





Sorry, I'm right out of Linux jokes now.

I really liked your second one.

---

### Post by geekygirl on 2009-08-10
Q: Why did the penguin cross the road?

A: Because it can.

---

### Post by roharme on 2009-08-10
One Windows Joke(No Offence).
 
Never go for Windows airlines. When you are in situation to open your parachute, you will get a message "Do you wish to open the parachute? Yes No"

---

### Post by lisati on 2009-08-10
> **roharme said:**
> One Windows Joke(No Offence).
 
Never go for Windows airlines. When you are in situation to open your parachute, you will get a message "Do you wish to open the parachute? Yes No"

Are you sure? Yes/No.
Parachute needs permission to continue. Allow/Ignore/Cancel.

---

### Post by DeadSuperHero on 2009-08-10
Eh, screw it. Cancel.

---

### Post by chessnerd on 2009-08-10
> **roharme said:**
> One Windows Joke(No Offence).
 
Never go for Windows airlines. When you are in situation to open your parachute, you will get a message "Do you wish to open the parachute? Yes No"

> **lisati said:**
> Are you sure? Yes/No.
Parachute needs permission to continue. Allow/Ignore/Cancel.

"The Windows registry has reported that one or more required files are damaged or missing. To correct this problem, please reinstall Parachute."

Now, to be fair, Linux doesn't have support for Parachute, but I hear there is this great open source alternative called Free Falling...

---

### Post by DeadSuperHero on 2009-08-10
Stallman's a big fan of Free Falling. With his weight configuration, I hear he FALLS FASTER than the average skinny Linux user.

---

### Post by Giant Speck on 2009-08-10
> **Mr. Psychopath said:**
> I really liked your second one.

Me, too.

---

### Post by starcannon on 2009-08-10
> **chessnerd said:**
> "The Windows registry has reported that one or more required files are damaged or missing. To correct this problem, please reinstall Parachute."

Now, to be fair, Linux doesn't have support for Parachute, but I hear there is this great open source alternative called Free Falling...
Yeah, it'd be better if they'd get a GUI on that; I heard somuns working on freefall-gtk but I haven't been able to locate a package or source for it.

I get some weird errors when I run freefall.
```

starcannon@starcannon-desktop:~$ freefall -terminalvelocity -3 -waterlanding 1

> *terminal velocity has been increased.
> *warning, you have chosen an ammo dump as your landing zone.
> *error, program exited unexpectedly, unable to save user data.

starcannon@starcannon-desktop:~$ 

```

---

### Post by TheNosh on 2009-08-10
> **Mr. Psychopath said:**
> Stallman's a big fan of Free Falling. With his weight configuration, I hear he FALLS FASTER than the average skinny Linux user.

he'd be offended by that. not because of anything you said about his weight, but because you didn't say "I hear he FALLS FASTER than the average skinny _**GNU**_/Linux user."

---

### Post by DeadSuperHero on 2009-08-10
TheNosh, you make a good point.

But I have a better one.

Can he use his beard as a Parachute? Or do the birds that live in it pull him to safety?

---

### Post by Nevon on 2009-08-10
This is not directly related to Linux - in fact, it's not really a joke - but it makes me giggle anyway.

> - Does the c compiler not tell you what you did wrong?
- C is great!
- The Java compiler is all like: "you have an uninitialised variable there, would you like a hug?"
- Gcc is like "raaagh! I do no bounds-checking!"

---

### Post by infestor on 2009-08-10
couldn't stop myself:

[IMG]http://imgs.xkcd.com/comics/sandwich.png[/IMG]

---

### Post by koshatnik on 2009-08-10
f(x) walks into a bar and orders some chips. The barman says sorry we don't cater for functions.

---

### Post by lisati on 2009-08-10
Q: How many users of MS products does it take to change a light-bulb?
A: Who needs a light-bulb when you have Windows?

---

### Post by Trail on 2009-08-10
> **Nevon said:**
> This is not directly related to Linux - in fact, it's not really a joke - but it makes me giggle anyway.

Well, first of all, it's not gcc's "fault", it's C's "fault".

Second, use proper compiler flags and warnings, then the compiler will issue warnings for things you are not even aware of :) The ones I use, and I'm quite satisfied, are usually:
```

-std=c++98
-ffor-scope
-fno-gnu-keywords
-foperator-names
-pipe
-Wall
-Wextra
-Wold-style-cast
-Wpointer-arith
-Woverloaded-virtual
-ggdb3
-Weffc++ //usually good, but annoying when you HAVE to inherit from a class without virtual destructor (kinda buggy, does not respect -Wno-non-virtual-dtor, it's treated differently)
-Wsign-promo
-Wshadow
-Wcast-align
-Wconversion
-Wsign-conversion
-Wmissing-declarations
-Wpadded
-Winline
-Wdisabled-optimization

-D_GLIBCXX_CONCEPT_CHECKS
-D_GLIBCXX_DEBUG
-D_GLIBCXX_DEBUG_PEDANTIC

-fno-threadsafe-statics //single-threaded
-march=native
-mtune=native
-findirect-inlining

```

---

### Post by stinger30au on 2009-08-10
> **lisati said:**
> Are you sure? Yes/No.
Parachute needs permission to continue. Allow/Ignore/Cancel.

error

parachute  failed to open as your license has expired or is non genuine and you may be in possession of counterfeit software

lol!

---

### Post by lisati on 2009-08-10
> **stinger30au said:**
> error

parachute  failed to open as your license has expired or is non genuine and you may be in possession of counterfeit software

lol!

I'll just have to go for the reserve chute, a.k.a. Ubuntu. (and yes, I did have two parachutes come out once at more-or-less the same time once back in the 1980s - and I managed to catch one of them somehow! This is a true anecdote.)

---

### Post by megamania on 2009-08-10
> **Trail said:**
> Well, first of all, it's not gcc's "fault", it's C's "fault".

Second, use proper compiler flags and warnings, then the compiler will issue warnings for things you are not even aware of :) The ones I use, and I'm quite satisfied, are usually:

That's the best joke so far! ;-)

---

### Post by The Real Dave on 2009-08-10
Parents, warn your kids about Linux!!

[IMG]http://imgs.xkcd.com/comics/cautionary.png[/IMG]


Some other good XDCD stuff :D 

"Frustration"

[IMG]http://imgs.xkcd.com/comics/frustration.png[/IMG]

"Sporks"

[IMG]http://imgs.xkcd.com/comics/forks_and_spoons.png[/IMG]

"Designated Drivers"

[IMG]http://imgs.xkcd.com/comics/designated_drivers.png[/IMG]

---

### Post by izizzle on 2009-08-10
Not really a Linux joke, but...

After a long night, Bill Gates and his wife woke up with smiles on their faces. His wife remarked: "Oh Bill! Now I know why you named your company MICRO-SOFT!"

I always chuckle at that one...

---

### Post by Nevon on 2009-08-10
> **Trail said:**
> Well, first of all, it's not gcc's "fault", it's C's "fault".
That's one way to completely kill a joke.

---

### Post by Keyper7 on 2009-08-10
> **Giant Speck said:**
> Me, too.

I'm not sure if I agree. The first penguin sounded a little racist.

However, the phrase he said is very complex and open to a lot of different interpretations, so I could be wrong.

---

### Post by sydbat on 2009-08-10
> **Keyper7 said:**
> I'm not sure if I agree. The first penguin sounded a little racist.

However, the phrase he said is very complex and open to a lot of different interpretations, so I could be wrong.And the award for 'Best answer to a quote of a quote of a post' goes to...

---

### Post by chessnerd on 2009-08-10
> **infestor said:**
> couldn't stop myself:

[IMG]http://imgs.xkcd.com/comics/sandwich.png[/IMG]

I knew someone would have to bring up xkcd...

---

### Post by freebeer on 2009-08-10
> **chessnerd said:**
> 
Now, to be fair, Linux doesn't have support for Parachute, but I hear there is this great open source alternative called Free Falling...

Who needs a parachute when you can just "cd ~"?

---

### Post by bodyharvester on 2009-08-10
> **freebeer said:**
> Who needs a parachute when you can just "cd ~"?

haha, sherlock holmes said that the right answer was almost always the simplest, or something like that

---

### Post by TheNosh on 2009-08-10
> **bodyharvester said:**
> haha, sherlock holmes said that the right answer was almost always the simplest, or something like that

it was something along those lines, but he took it from [occam's razor]("http://en.wikipedia.org/wiki/Occam's_razor")

---

### Post by Elep.Repu on 2009-08-10
You're doing an administrative activity, please type your password.

---

### Post by Eviltechie on 2009-08-10
> **Elep.Repu said:**
> You're doing an administrative activity, please type your password.

Just hope that parachute doesn't require root access.

---

### Post by racerraul on 2009-08-10
[IMG]http://lh4.ggpht.com/_j__cjyJkwjM/SS2b5P-O4aI/AAAAAAAAEDk/uHT--e85Fww/s800/diveadamn.gif[/IMG]

---

