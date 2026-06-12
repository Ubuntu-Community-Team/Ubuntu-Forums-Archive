---
title: "5 Million PI"
date: 2011-05-08
forum: The Cafe
---

### Post by physic.dude on 2011-05-08
In my seemingly infinite spare time, I have created what seems to be the only web page to host the first five million consecutive digits of Pi in one place.
* (Warning: Loading times of 5-15 seconds are imminent. Browser crashes are possible. )*

[url removed] (Read Edit)

It's just a simple apache/ubuntu web server of mine. I probably wont keep it up for very long. :D

It was going to be to one BILLION digits, and I have the log file from the terminal session when I calculated it, but soon realized a 1GB text file is too hard to work with, let alone download from a server.


_**Edit**_: Sorry, it got kinda boring, off line forever. 

Here is the last few digits of 5 Million Pi from the 4,999,949th to 4,999,999th decimal places

```
[FONT=Arial][SIZE=2]604886585519184670236542176178350518172132076461971[/SIZE][/FONT]
```

---

### Post by matt_symes on 2011-05-08
You have too much spare time :rolleyes:

I was going to count them  but i do not have much spare time as you. :D

---

### Post by dh04000 on 2011-05-08
That website crashed my browser. I hope your happy.

---

### Post by physic.dude on 2011-05-08
> **dh04000 said:**
> That website crashed my browser. I hope your happy.

Sorry, I didn't mean it...  :(

I've added a warning for the future.

---

### Post by Rasa1111 on 2011-05-08
haha!

Almost crashed my FF to. 
Well, Made it stutter for a few seconds anyway. lol

That's a lot of digits! 
impressive. :P

oh yes.. and congrats! lol :)

p.s.. where did i put my car keys?

---

### Post by m_duck on 2011-05-08
Mmm, Pi...

---

### Post by skierkyles on 2011-05-08
Here's pie to 438,400 pixels.
[IMG]http://www.applepierecipe.org/wp-content/uploads/2010/07/Classic-Apple-Pie-Recipe-Picture1.jpg[/IMG]

---

### Post by matt_symes on 2011-05-08
Hmmm. Apple pie with clotted cream. I'm off to the kitchen.

---

### Post by sammiev on 2011-05-08
<---- counted them and you have one too many! :popcorn:

---

### Post by cgroza on 2011-05-08
> **sammiev said:**
> <---- counted them and you have one too many! :popcorn:
That must be because the loop started at 0. :p:p
By the way, what did you use to calculate it?

---

### Post by sammiev on 2011-05-08
> **cgroza said:**
> That must be because the loop started at 0. :p:p
By the way, what did you use to calculate it?

A few cases of beer. :D

---

### Post by physic.dude on 2011-05-08
> **cgroza said:**
> That must be because the loop started at 0. :p:p
By the way, what did you use to calculate it?

I used the the program 'pi'
```
sudo apt-get install pi
```

---

### Post by cgroza on 2011-05-08
> **physic.dude said:**
> I used the the program 'pi'
```
sudo apt-get install pi
```
Hmm, lets check his manpage.

---

### Post by physic.dude on 2011-05-08
> **sammiev said:**
> <---- counted them and you have one too many! :popcorn:

You probably just counted the file size (5000217 bytes).

Some of those bytes are from the HTML headers and formatting code.
1 byte is from from the point between 3 and 1.

There are actually only 4999999 decimal places. I suppose I should have said Pi to 5 million digits, not places.


Edit: I just changed all instances where I said 'places' to 'digits' on the site. :)

---

### Post by aaaantoine on 2011-05-08
If you know how to script you can set something up that pulls down 1000 digits at a time, per each click.

Example:

0000000000000000000000000000000000000000000000000000000000000000000000000000000000... [Click for 1000 more digits](example.com)

For it to work seamlessly you need to set up what basically amounts to AJAX though.  Either that or have Javascript calculate pi for you.

---

### Post by physic.dude on 2011-05-08
> **aaaantoine said:**
> If you know how to script you can set something up that pulls down 1000 digits at a time, per each click.


I guess so, but this is just a random site created out of boredom. I didn't build it to be a functional tool, but rather just a proof of concept.

---

### Post by kostageas on 2011-05-08
I'm currently running it to 1 billion.  5 Million took me about 10 seconds, so I'm hoping a billion won't take TOO long, but eh.  Gonna upload it to my blog for people to see.  :popcorn:

---

### Post by physic.dude on 2011-05-08
> **kostageas said:**
> I'm currently running it to 1 billion.  5 Million took me about 10 seconds, so I'm hoping a billion won't take TOO long, but eh.  Gonna upload it to my blog for people to see.  :popcorn:

Lol, good luck with that. I hope you have a task killing button on one of your panels. 

Even if you do manage to get the entire thing on your blog, well, I'll let you figure that one out.  :popcorn:

---

### Post by kostageas on 2011-05-08
Terminal crashed on me so I booted into command line only mode.  This time it worked, but I couldn't figure out how to save it as a .txt file.  Any advice?

---

### Post by Rasa1111 on 2011-05-09
can probably use the '>' command. 

so, say you wanted to save the output of lspci..
```
lspci > listpcidevices.txt
```this will "route" the output of lspci to a listpcidevices.txt file in the current (home by default) directory .
sorry if it wont help.

---

### Post by physic.dude on 2011-05-09
> **kostageas said:**
> Terminal crashed on me so I booted into command line only mode.  This time it worked, but I couldn't figure out how to save it as a .txt file.  Any advice?

I remember when I calculated Pi to a billion places, use this command:
```
pi 1000000000 >file.txt
```It will save the billion digits of Pi in a file named file.txt in your home folder.

---

### Post by Bandit on 2011-05-09
> **physic.dude said:**
> In my seemingly infinite spare time,.....

LOL nice one. Sounds like something I would do in Javascript or PHP.

---

### Post by entangled on 2011-05-09
The question is; how do you know it is pi to 5 million dps? Why do you trust that program? Could it be just churning out digits at random?
A more interesting task is to set up an accuracy check. Calculate pi in at least two independent ways and compare for a few thousand dps.
This is a question for any large computational task, how do you know it is right?

---

### Post by leviathan8 on 2011-05-09
Well, that was a nice workout for my browser. :P

---

### Post by cgroza on 2011-05-09
> **entangled said:**
> The question is; how do you know it is pi to 5 million dps? Why do you trust that program? Could it be just churning out digits at random?
A more interesting task is to set up an accuracy check. Calculate pi in at least two independent ways and compare for a few thousand dps.
This is a question for any large computational task, how do you know it is right?
Computers generally use pseudo ranom numbers. The generator only makes a lot of numbers, and when that "a lot" is reached, it usus the same list of numbers again. Therefore you would see repetition in cases of of 5 million numbers.

---

### Post by physic.dude on 2011-05-09
> **entangled said:**
> The question is; how do you know it is pi to 5 million dps? Why do you trust that program? Could it be just churning out digits at random?
A more interesting task is to set up an accuracy check. Calculate pi in at least two independent ways and compare for a few thousand dps.
This is a question for any large computational task, how do you know it is right?
and 
> **cgroza said:**
> Computers generally use pseudo ranom numbers. The  generator only makes a lot of numbers, and when that "a lot" is  reached, it usus the same list of numbers again. Therefore you would see  repetition in cases of of 5 million numbers.


Its not random numbers, go to the following site and search for the last few digits from my calculation of Pi. (2076461971) Or any other position for that matter.

[http://www.angio.net/pi/bigpi.cgi](http://www.angio.net/pi/bigpi.cgi)

You can also do it in reverse, have that site fetch 10 digits starting from the position of 4999990 and those will be the last 10 digits in my version.

---

### Post by forrestcupp on 2011-05-09
Fail! The 531st place should be a 5, not a 7. ;)

---

### Post by physic.dude on 2011-05-09
> **forrestcupp said:**
> Fail! The 531st place should be a 5, not a 7. ;)

Don't lie to me... Junior. :wink:

---

