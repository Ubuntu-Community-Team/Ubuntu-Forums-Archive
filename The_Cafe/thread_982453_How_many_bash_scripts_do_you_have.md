---
title: "How many bash scripts do you have?"
date: 2008-11-14
forum: The Cafe
---

### Post by lovinglinux on 2008-11-14
I'm becoming addicted to bash scripts. I already have 93 of them on my ~/bin folder and I use all of them.

Just for the sake of curiosity, I was wondering what would be the average number of bash scripts Ubuntu users have and how many scripts someone would be capable of using on a regular basis?

So please, post how many you have and how many do use regularly.

---

### Post by init1 on 2008-11-14
Just a few that deal with xkcd :D
This one displays a random xkcd comic
```

wget http://dynamic.xkcd.com/comic/random/ -O -| grep \<img\ src=\"http\://imgs.xkcd.com/comics | sed s/\<img\ src=\"// | sed s/\"[a-z]*.*// | wget -i - -O -| display

```
You'll need Image Magick first
```

sudo apt-get install imagemagick

```

---

### Post by Joeb454 on 2008-11-14
I fixed the poll :)

And currently I have about 6

---

### Post by lovinglinux on 2008-11-14
> **Joeb454 said:**
> I fixed the poll :)

And currently I have about 6

Thank you.

---

### Post by qazwsx on 2008-11-14
Well, I have written  about 1-20 or 20-50 for my personal usage.



+1 bash addict :)


By the way even booting relies heavily on shell (so called init scripts in Ubuntu dash).

---

### Post by Grant A. on 2008-11-14
93?! Wow, and I thought 5 was a lot...

Now .py scripts, that's a COMPLETELY different story ;)

---

### Post by smartboyathome on 2008-11-14
1-20, I currently only have 1 which I use for my Insignia for conversion. What I do have a lot of, though, are aliases which I basically make like scripts, using the && to separate commands. I guess you can call me an alias addict. :P

---

### Post by cardinals_fan on 2008-11-14
None.  I use either sh or Zsh, the **real** shells :)

---

### Post by Eisenwinter on 2008-11-14
> **Grant A. said:**
> 93?! Wow, and I thought 5 was a lot...

Now .py scripts, that's a COMPLETELY different story ;)
Heh, yeah, I don't have any bash scripts, but I do have Perl scripts.

---

### Post by smartboyathome on 2008-11-14
> **cardinals_fan said:**
> None.  I use either sh or Zsh, the **real** shells :)

Hey, I use ZSH too! Its great! :D

But, technically, you *can* run bash scripts in ZSH, as ZSH is compatible with bash. So you could be using bash without knowing it. ;)

---

### Post by cardinals_fan on 2008-11-14
> **smartboyathome said:**
> Hey, I use ZSH too! Its great! :D

But, technically, you *can* run bash scripts in ZSH, as ZSH is compatible with bash. So you could be using bash without knowing it. ;)
Yes, but the shell scripts I write all start with #!/bin/sh or #!/bin/zsh :D

---

### Post by lovinglinux on 2008-11-14
> **Grant A. said:**
> 93?! Wow, and I thought 5 was a lot...

Now .py scripts, that's a COMPLETELY different story ;)

I probably have that much because I'm not experienced enough to make a decent one :D 

54 of them are related. They are for moving videos I record from the TV card to other computers on my home network. Instead of setting up a media server, I transfer the videos to other computers based on user preference. So the scripts sort and copy only new videos that each user like to watch and also archive those that I like the most. Everything is done based on show title, so I have a base script to select new recorded shows and each show has it own script that distribute the video to the users folders accordingly. Probably not a elegant way of doing this, but it works for me.

I wish I could write a script to make my cable TV provider broadcast better shows :D

---

### Post by gn2 on 2008-11-14
What's a bash script? :confused:

---

### Post by lovinglinux on 2008-11-14
> **cardinals_fan said:**
> Yes, but the shell scripts I write all start with #!/bin/sh or #!/bin/zsh :D

I didn't know that those even existed, otherwise I would choose a better title for this thread. :oops:

Since they are all scripts, I guess it doesn't matter the type for the purposes of this poll.

Anyway, what is the difference between them?

EDIT: I have found [[COLOR="DarkRed"]**this comparison chart**[/COLOR]]("http://en.wikipedia.org/wiki/Comparison_of_command_shells"), but it sounds like Greek to me. I guess they all do similar stuff.

---

### Post by cardinals_fan on 2008-11-14
> **lovinglinux said:**
> I didn't know that those even existed, otherwise I would choose a better title for this thread. :oops:

Since they are all scripts, I guess it doesn't matter the type for the purposes of this poll.

Anyway, what is the difference between them?

EDIT: I have found [[COLOR="DarkRed"]**this comparison chart**[/COLOR]]("http://en.wikipedia.org/wiki/Comparison_of_command_shells"), but it sounds like Greek to me. I guess they all do similar stuff.
If you're counting all scripts... I have a lot.  Mostly Perl and shell scripts, plus some Ruby.

Zsh and BASH are comparable, though I prefer Zsh for its better tab completion and more thorough configuration.  Sh is very basic, and I only use it in scripts (not as my main shell).

---

### Post by lovinglinux on 2008-11-14
> **cardinals_fan said:**
> If you're counting all scripts... I have a lot.  Mostly Perl and shell scripts, plus some Ruby.

Zsh and BASH are comparable, though I prefer Zsh for its better tab completion and more thorough configuration.  Sh is very basic, and I only use it in scripts (not as my main shell).

a lot = ? :D

I guess would be better to count only shell scripts.

---

### Post by cardinals_fan on 2008-11-14
> **lovinglinux said:**
> a lot = ? :D

I guess would be better to count only shell scripts.
I'm not sure - I'm rather disorganized with them.  I would guess ~60 shell, ~60 Perl, and ~20 Ruby, but I'm not sure.  That isn't really that many, but it's too many for me to keep track of.

---

### Post by spupy on 2008-11-14
My ~30 bash scripts are the most cherished programs on my hard disk. They are the spice that makes my system unique. :P

---

### Post by Irihapeti on 2008-11-14
I was surprised to find that I've actually got 30 scripts in my ~/bin directory, but a number of them were experimental things that I forgot to delete. 

I figure that I use about 10 or so on a regular basis.

---

### Post by Cracauer on 2008-11-14
Counting only those that were worth putting into my CVS tree permanently, which is the minority, a quick `find` comes to 764.

---

### Post by sujoy on 2008-11-15
i do not use a lot of shell scripts, most of them gets transformed in python/perl in the long run

---

### Post by lisati on 2008-11-15
I haven't had the need to set up any new scripts (yet), so other than whatever might be lurking "behind the scenes" of a consequence of setting things up, the answer is NONE.

---

### Post by mentallaxative on 2008-11-15
Woah! I'd like to know what you need +5000 bash scripts for!

I only have a few bash scripts that get any actual use. I've written more Python scripts, as I find Python easier to grasp than bash.

One of these days I'll have a look at a bash tutorial again....

---

### Post by lovinglinux on 2008-11-15
> **mentallaxative said:**
> Woah! I'd like to know what you need +5000 bash scripts for!

I don't know. When I was creating the poll I thought that if a Linux noob like me have almost 100, then those who use Ubuntu for years could have thousands. But now I'm curious to know if those people who voted for 5000+ really have such a huge number of scripts or are just messing with the poll? :D

---

