---
title: "[for pre-alpha review] Terminal Trianing Software"
date: 2008-07-14
forum: The Cafe
---

### Post by dracule on 2008-07-14
I whipped up this python program which I hope will help people learn some basics about the Terminal. 

Note: I am kind of a noob, so everything may not be 100% accurate, so please double check my work.

I also made it so it is very easy to make your own tutorial using a dead simple system. However, it is not commented so I will have to add that in, if you want to help I can help you learn it (it honestly takes <2 min)

Currently it only has 4 sections:

Intro
Navigating through directories
Doing stuff to the files you have in those directories.
Super-user commands.

I want to add more.

I had to kind of emulate the shell for it, but it is run inside of the terminal.

I was wondering if you guys could look it over and give me some feed back about what to add and if everything is correct in it.

If anybody wants to help to create a section or something just ask. The code for it is very simple:

```

%WOOO this will show up as text, the '>cont' will wait until the user hits enter to clear the screen and go on.

>cont

%the '>loop cd ~' will show a simulated PS1 prompt and not let the user continue unless he types in 'cd ~'

>loop cd ~

%As you can see a '%' denotes text that will be displayed and a > denotes a predefined command.

>cont

$ this is the end of the file
```

that is basically what the code looks like for making the tutorial.

And here is a screenshot:

[[IMG]http://img254.imageshack.us/img254/2898/screenshotphunubuntudesnn2.png[/IMG]](http://imageshack.us)


like i said. this is pretty unfinished and super alpha. I just wanted input from you to see what i need to change.

---

