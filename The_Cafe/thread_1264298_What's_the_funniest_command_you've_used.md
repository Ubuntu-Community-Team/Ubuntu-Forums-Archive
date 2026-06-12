---
title: "What's the funniest command you've used?"
date: 2009-09-12
forum: The Cafe
---

### Post by greenstar on 2009-09-12
What is the funniest command you've actually used?

Backstory:
I was sitting at my laptop burning off to DVD some files I recovered for a client today. I'm dealing with a couple of issues in the process.

[LIST=1]
[*]Files with names that are not Joliet compliant for burning to disc; either too long (more than 65 chars.) or with illegal characters.
[*]Multiple directories with large numbers of files that needed to be split up to be able to fit on 4.7 GB DVDs. I toyed with making a big archive, split at 4.2 GB. That wasn't really practical, and isn't exactly easy for a computer novice to use. I also tried a package called tarlimit from sourceforge, after reading about it in the forum archives. Thanks to [strider1551]("http://ubuntuforums.org/member.php?u=90870") here on the forums for tarlimit. Tarlimit allowed me to create a set of archives at 4.2 GB each automatically separating the files to fit. This divided files from a single sub-directory over two discs. Once again, not exactly novice friendly for my client. tarlimit was excellent at optimizing space usage on the DVDs, but not exactly what I needed. I finally decided to just manually separate the directories in an easy to find and navigate manner.
[/LIST]
So, I got the 2nd issue handled, but that 1st one is a pain. So I was digging in Synaptic and found a package called detox. So I'm checking it out, first running:
```
detox -h
```and then, the logical next command for learning to use detox:
```
man detox
```:D

I started laughing as soon as the text hit the screen and I thought about the words I had typed.

So there it is: ***man detox***. Let's hear your funniest command.

---

### Post by steveneddy on 2009-09-12
```
cowsay
```

as in

```
cowsay steveneddy is kewl
```

Don't have **cowsay**?

```
sudo apt-get install cowsay
```

---

### Post by greenstar on 2009-09-12
> **steveneddy said:**
> ```
cowsay
```as in

```
cowsay steveneddy is kewl
```Don't have **cowsay**?

```
sudo apt-get install cowsay
```

That's cool. I've seen that cow before. Now I have my very own.

```
cowsay greenstar is a weisenheimer
```

---

### Post by mcduck on 2009-09-12
```
glxgears --iacknowledgethatthistoolisnotabenchmark
```

I don't think I'll ever be able to forget that parameter. Its absolutely genious. :)

(For the background, Glxgears used to require you to add that parameter to show the frames/second reading. I suppose the authors of the program really wanted people to understand that it shouldn't be used as a benchmark.. ;))

---

### Post by Gen2ly on 2009-09-12
```
fsck /dev/partition
```

Think that someone may see me typing this and throwing out an expletive.

---

### Post by conehead77 on 2009-09-12
```
locate skynet
```

---

### Post by schauerlich on 2009-09-12
*Redacted - in bad taste*

---

### Post by TheLions on 2009-09-12
> **conehead77 said:**
> ```
locate skynet
```

:lolflag:

---

### Post by dragos240 on 2009-09-12
Yes is my favorite command.

---

### Post by greenstar on 2009-09-12
> **dragos240 said:**
> Yes is my favorite command.

At risk of sounding a bit dense, do you care to explain that one?

---

### Post by RiceMonster on 2009-09-12
> **greenstar said:**
> At risk of sounding a bit dense, do you care to explain that one?

type yes followed by a string of words into a terminal, and it will repeatedly print them until you kill it. For example,

```
yes RiceMonster
```

Or, you can just type yes and it will print y repeatadly.

---

### Post by Tibuda on 2009-09-12
> **greenstar said:**
> At risk of sounding a bit dense, do you care to explain that one?

```
$ yes is my favorite command.
is my favorite command.
is my favorite command.
is my favorite command.
is my favorite command.
is my favorite command.
is my favorite command.
is my favorite command.
is my favorite command.
is my favorite command.^C

```
[quote="man yes"]yes - output a string repeatedly until killed[/quote]

---

### Post by wojox on 2009-09-12
```
wojox@wojox0:~$ %blow
bash: fg: %blow: no such job
```

---

### Post by subdivision on 2009-09-12
I giggle at fsck.

---

### Post by K.L. on 2009-09-12
Maybe this one?

```
apt-get moo
```

---

### Post by RiceMonster on 2009-09-12
> **K.L. said:**
> Maybe this one?

```
apt-get moo
```

```
cowsay cowsay is better
```

---

### Post by K.L. on 2009-09-12
Okay, how about this one. Hit ALT+F2 and type "free the fish" :D AFAIK, it works only with GNOME.

It's not a command, more like an app, but still... :D

---

### Post by juancarlospaco on 2009-09-12
If the GEGL can be executed by command i said the GEGL
:)

---

### Post by mcduck on 2009-09-12
> **K.L. said:**
> Okay, how about this one. Hit ALT+F2 and type "free the fish" :D AFAIK, it works only with GNOME.

It's not a command, more like an app, but still... :D

Since you mentioned that one, try typing "Require Quarter" as user name in the GDM login screen.. ;)

What comes to "yes", I actually find "false" a lot funnier. Not because running it would be fun, but because of what it does: "false - do nothing, unsuccessfully". ;)

---

### Post by darsu on 2009-09-12
kdontchangethehostname.

I don't know what it's for. I tried it once just to see whether it really doesn't do what it promises to not do.

---

### Post by Barrucadu on 2009-09-12
```
man which
```

---

### Post by K.L. on 2009-09-12
> **mcduck said:**
> Since you mentioned that one, try typing "Require Quarter" as user name in the GDM login screen.. ;)

I am using KDE right now, but I'll try this one for sure (some time later) :D

---

### Post by donkyhotay on 2009-09-12
From a Tshirt somewhere...
```

man woman
segmentation fault (core dumped)

```

---

### Post by aaaantoine on 2009-09-12
> **mcduck said:**
> Since you mentioned that one, try typing "Require Quarter" as user name in the GDM login screen.. ;)

What comes to "yes", I actually find "false" a lot funnier. Not because running it would be fun, but because of what it does: "false - do nothing, unsuccessfully". ;)

Its counterpart is "true - do nothing, successfully".  I'm guessing they're both used for scripting purposes.

---

### Post by lisati on 2009-09-12
```

xyzzy

```
or
```

plugh

```
To which a common response is something along the lines of "nothing happens".

Now to wander off before I get stuck in a maze of twisty little passages, all alike. (Or is that a twistly little maze of passages?)

---

### Post by mcduck on 2009-09-13
> **aaaantoine said:**
> Its counterpart is "true - do nothing, successfully".  I'm guessing they're both used for scripting purposes.

Yes, I know that. But there's still something special in a program that does nothing and still fails. :D

Actually "true" works better, since when you run "fail" in a terminal it does nothing. To truly do what it's description says it should actually do something..

(Yes, I know that this would not make sense considering the actual purpose of the program)

---

