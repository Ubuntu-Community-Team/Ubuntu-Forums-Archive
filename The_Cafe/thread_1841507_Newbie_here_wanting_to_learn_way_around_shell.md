---
title: "Newbie here wanting to learn way around shell"
date: 2011-09-09
forum: The Cafe
---

### Post by Bandanna on 2011-09-09
First of all, sorry if this is the complete wrong place to post this, but it seems to be the catch-all area so I feel safe.

Background: I started playing around with ubuntu intermittently starting about 3 years ago when I was a sophomore in highschool. 
I really had no idea what I was doing, but it was at this point in my life when I realized I had a strong interest in electronics. I stumbled upon ubuntu (looking for "cool desktop wallpapers" I do believe :p) and then this alien-like operating system essentially consumed me for a couple of weeks. It took quite a while, but I managed to get a dual-booted system and then I enabled compiz, customized my own 'cube', and let me tell you, I was in heaven.  lol
But the flames of passion extinguished quickly, I began to feel like it was "too much trouble" to just do things like install flash because the OS was so incredibly foreign to me. Packages, gnomes and synaptics? To be honest I was intimidated.
Too make a long story short... Now that I am a few years older, I actually know how to research things correctly, and am a bit more focused, I figured I would start learning my way around the shell. 


I remember that in the past this community had been so receiving of me. I come here now not only to ask for some help, but also just to display to the public that I am setting a few goals to better myself. 

For now my goal is to learn the shell, then after some time I think I am going to start working on getting python down.

I have had a few weeks worth of exposure to C, C++ and programming in general. I learned about IDE's, object oriented languages, interpreted languages, libraries, functions, loops, etc. I am not a complete novice,I have had some exposure, I am just looking for more at this point. 

This brings me to what I actually wanted to ask from you all. 
I have found some really awesome sites, with tons of info. The problem is, I really want to be able to read the stuff off paper during some of the downtime I have at my job/ inbetween classes.

I have been literally copy and pasting page by page sites like this: 
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

and printing it out. This is excruciatingly time consuming.
I was wondering if, and this would probably be some real charity work so I understand if no one is up to it, it were possible to have a script made that can speed up the process of getting the text off those pages,onto a file in my system, put them together and let me print them out.

I have an idea that as to how it might be possible with wget and cat commands, I really dont know though. If someone took the time out of their day to make a script and possibly annotate it really well, or explain what they were doing to make it, I would be so so grateful.

Or if someone even just explained thoroughly how I could do something like that, anything. This is really about me trying to learn than getting the script itself. I'll get it on paper either way.

P.S: Also, if you took the time just to read through all of this, thank you!  :)

---

### Post by nothingspecial on 2011-09-09
Hi Bandanna,

You know, the best way to learn bash (or any kind of coding) is to find something you'd _really_ like to do, and then try to do it.

Traversing web pages, downloading them and automatically printing them sounds like the perfect thing.

Please don't consider me rude, but this seems like your opportunity. Yes, you can read page after page but until you actually try to do something on your own you won't learn properly.
If you do get a script in this thread then fine but my suggestion is to try and do it yourself. :)

---

### Post by sisco311 on 2011-09-09
That tutorial is outdated. (Last updated on Wednesday, April 24, 2002. )

Try this: :)
```

# download the bash guide form Greg's Wiki
wget http://stuff.lhunath.com/BashGuide.pdf
# print it
lpr BashGuide.pdf

```

---

### Post by CharlesA on 2011-09-09
+1 to Greg's Wiki.

Just start playing around with it. If you don't want to break your main system by running something, you can always run a copy of Ubuntu in a virtual machine or from a livecd.

---

### Post by disabledaccount on 2011-09-09
Learn sed syntax - everything else in shell is piece of cake ;)
best available guide: [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

Sed is master of all other commands - You can do almost everything with strings/text and even numbers, besides this will teach You RegExp - base for shell scripting.

---

### Post by nothingspecial on 2011-09-09
> **CharlesA said:**
> +1 to Greg's Wiki.



It really should be the official recommended bash guide. There is so much stuff out there that is horribly out of date.

---

### Post by Bandanna on 2011-09-09
Thank you for all of the good sources guys! ^^
If there is anything else that you think might be of use please post it!
I work night shifts for a security company, so there is usually a lot of down-time sitting on a bench/in a lobby of some building. :P 
A lot of time to read over the stuff, then I will probably mess with actually practicing it tomorrow or the next day when I get some time off.

---

