---
title: "automated start end time recording"
date: 2012-03-27
forum: The Cafe
---

### Post by jonathonblake on 2012-03-27
All:

I've got to test how long a program takes to start, with various different starting criteria.

However, I don't have source code for the program, so I can't throw in a line "create file(blah)" when the program starts, and a second, similar line, when the program is ready for the user to do something.

Does anybody have any suggestions on how to automate tracking the length of time. Something other than sitting with a stop watch, clicking "Start", and "Stop".

jonathon

---

### Post by koenn on 2012-03-27
quick&dirty:

wrap a script around it that puts out a date stamp before the program starts, and another one when it stops.

if you then manually shutdown the program as soon as it's ready to accept user input, you'd have some idea of how long it took to start up (+ shutdown + time it took for you to react, but you could assume that will be more or less the same every time, and therefore negligible)

the 'time' command van be used in a similar way. 


if the program does something that will let you detect "ready for user input" (eg write in a log file, or reply to network requests, or accept input from stdin, ...) you might be able to use that to further automate this

---

### Post by jonathonblake on 2012-03-28
> **koenn said:**
> quick&dirty:
wrap a script around it that puts out a date stamp before the program starts, and another one when it stops.

That requires babysitting the program.  
The only way to know it is ready for user input, is by watching the screen, and not moving away from it at all. Considering the start up times range from 5 seconds to 45 minutes, or more, that might not be a practical option.

However, it does give me an idea. :)

Start a screen capture video program.
Then start the program.
Once the program is ready for user input, shut down both of them.
Edit the screen capture program, deleting everything from before I started the program, and after the program was ready for user input, and measure the length of time that takes.

Virtue # 2 of that approach, is that I can post the results to the Internet showing just how long the program takes, under different starting conditions. Don't know where I could post it:
[LIST]
[*]Youtube rejected the video I made showing that Win7 takes more than an hour from startup, untill it was ready for user input;
[*]Vimeo is for professional videography;
[/LIST]

Now to find a screen capture video program.

jonathon

---

### Post by cariboo on 2012-03-28
I haven't tried it yet, but [Sikuli ]("http://sikuli.org/")comes highly recommended, when it comes to automated tasks.

---

### Post by forrestcupp on 2012-03-28
> **jonathonblake said:**
> 
Youtube rejected the video I made showing that Win7 takes more than an hour from startup, untill it was ready for user input;

How does Win7 take more than an hour from startup? Did you install it on a 75Mhz Pentium or something? :)

Also, no one is going to watch an hour long video of Windows starting up. ;)

---

### Post by koenn on 2012-03-29
> **jonathonblake said:**
> That requires babysitting the program.  
The only way to know it is ready for user input, is by watching the screen, and not moving away from it at all.

Well, I did say "if the program does something that will let you detect 'ready for user input'  you might be able to further automate this", but since you've neglected to provide any information about what program or what sort of programs you want to check, that  suggestions was necessarily vague. 

Cariboo's suggestion of Sikuli looks interesting; if it's GUI programs we're talking about, a Sikuli script might be able to open and close the application, and then all you have to do is time it.

---

### Post by jonathonblake on 2012-04-03
> **forrestcupp said:**
> How does Win7 take more than an hour from startup? Did you install it on a 75Mhz Pentium or something? :)

It has an Intel Core Duo chip.
I attribute the long time for booting up to Microsoft's usual incompetence in writing software.
> 
Also, no one is going to watch an hour long video of Windows starting up. ;)

By putting the video on YouTube, or somewhere similar, people can verify for themselves that the bootup does take that long.

I'll grant that it is probably the most boring video to watch.

jonathon

---

### Post by forrestcupp on 2012-04-03
> **jonathonblake said:**
> 
By putting the video on YouTube, or somewhere similar, people can verify for themselves that the bootup does take that long.

I'll grant that it is probably the most boring video to watch.

jonathon

Last time I checked, which has been a while, YouTube only allowed you to upload 10 minute videos. I've seen special cases where people had longer videos, but I don't know how they got that permission. The way people got around this was to split their long video into 10 minute sections and put the order number in the title.

And I have a Core2Duo that I've been running Windows 7 on for a long time that boots up just as quickly as Ubuntu. It takes longer for the hard drive to quit spinning, but it's usable with a regular arrow mouse pointer. I'd say your problem is not Microsoft's fault.

---

