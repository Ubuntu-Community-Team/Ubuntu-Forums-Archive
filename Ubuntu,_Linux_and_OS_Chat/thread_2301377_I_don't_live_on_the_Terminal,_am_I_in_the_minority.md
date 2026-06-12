---
title: "I don't live on the Terminal, am I in the minority"
date: 2015-11-02
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2015-11-02
4 years, I've been using Xubuntu, started out with 12.04, now on 14.04, I tend to stick with LTS releases, and I've never used the Terminal for everyday use, I only use it to fix a problem, and I rarely get any. There's a reason why I don't use the Terminal for everyday use, a year after I switched from Windows Vista, I decided to explore the Terminal, biggest mistake ever, I ended up borking my system, had to spend the entire afternoon reinstalling my system, so from that day forward, I never use the Terminal, only when instructed to do so.

4 years using Xubuntu, not touching the Terminal, only do when the need comes, what am I missing from the Linux experience?

---

### Post by speedwell68 on 2015-11-02
I use the Terminal everyday just using the shell would be so time consuming.

---

### Post by Sweet_Baby_Jamie on 2015-11-02
I think you're definitely in the majority!  I rarely ever use the terminal.  I think the last time I did was during installation, and only to add a PPA for a favorite application that isn't in the Ubuntu repositories.  Point-and-click is how I roll, and I think most "ordinary" users do the same.  Every OS has a terminal, even Windows!  But most people never use it.

---

### Post by ajgreeny on 2015-11-02
There is nothing to beat the terminal for getting information when something goes wrong and will not work, and in many cases it is much faster than a GUI application for carrying out procedures.  I use terminal many times every day for a lot of things and would find it very frustrating not to do so.

An example; I want to know the disk space used by the files in each folder in my home.
I am not even sure how I would list that from a GUI application quickly, though I suspect it is possible, but the command ```
du -h -d 1 | sort -h
```gets it in seconds sorted by size; not difficult and very speedy.

However, I suspect you are like a great many other users to whom terminal is a foreign language, and therefore to be feared.  That's a pity; get to use it for simple tasks and you will quickly find out how useful it can be for those and probably quickly move on to more complicated uses for it.

If you don't, it really doesn't matter as long as your OS does everything you want it to.

---

### Post by buzzingrobot on 2015-11-02
> **ardouronerous said:**
> 4 years, I've been using Xubuntu, started out with 12.04, now on 14.04, I tend to stick with LTS releases, and I've never used the Terminal for everyday use, I only use it to fix a problem, and I rarely get any. There's a reason why I don't use the Terminal for everyday use, a year after I switched from Windows Vista, I decided to explore the Terminal, biggest mistake ever, I ended up borking my system, had to spend the entire afternoon reinstalling my system, so from that day forward, I never use the Terminal, only when instructed to do so.

4 years using Xubuntu, not touching the Terminal, only do when the need comes, what am I missing from the Linux experience?

If you're doing what you need to do, you're not missing anything.

It's easy to forget that the "Terminal" (which is really Bash or a similar program running in an emulation of a bare Unix console) is as much of an interface as any GUI. It's just different. There's nothing you can do in a shell that can't be done in a GUI, or vice versa.  Shells are traditionally less forgiving and more demanding of user expertise. I.e., you can write your own interface rather than rely on a GUI writer to have done it.

 GUI's are typically easier because they display a range of options and we can click on one of them.  When we enter commands at the command line, we need to remember things. But, fundamentally, there's not much to distinguish entering "foo --help" in a terminal versus clicking "Foo->Help" in a menu.  Both versions are metaporic creations that mean something to humans and nothing to the hardware.

If a GUI doesn't prepackage a capability you need, you're out of luck.  The shell -- the terminal -- is more amenable to being made to do what you want, as long as you are amenable to learning how to do it.

Terminal commands dominate Linux media and blog posts because it is easy to include text in an article, but it's difficult to write a narrative guiding people through the equivalent GUI-fied approach. This creates the false impression that using those shell commands is the *only* way to get something done.And, of course, very few authors ever bother to explain how those command lines they tell you to copy-and-paste actually work.

---

### Post by grahammechanical on 2015-11-02
What are you missing? In your own words: "I ended up borking my system."

Ubuntu lets me fulfill my reason for having a computer and without ever using the terminal. But I also want to help out on this forum and that means, in my opinion,

a) being able to explain how to use the user interface to do things. I limit myself to one UI and that is Unity.
b) understanding the printouts of commands because commands that give information about a user's system work across all user interfaces.
c) understanding that commands to fix things help users who do not have the same UI as I have.

And then there is my natural curiosity that forces me to look inside any black box with wires coming out of it. Now, transferred to a computer operating system. And often the only way to unscrew the lid of the box and peek inside is to use some commands.

Regards.

---

### Post by speedwell68 on 2015-11-02
> **Sweet_Baby_Jamie said:**
> Every OS has a terminal, even Windows!  But most people never use it.

When I started using x86 based PCs all you could get were command line OSes.  Good old MS-DOS 3.1.  I think the first OS I used with a dedicated GUI was Amiga OS.:D

---

### Post by SeijiSensei on 2015-11-02
I started using computers in the late 1960's; there were no GUI's then.  When I started building Linux-based servers around 1995, using the shell was pretty much the standard.  Now that I manage servers remotely, I do everything in the shell via SSH.

My experience doesn't really map to most contemporary computer users who have grown up only knowing GUI's.  However there are just some tasks for which the shell is much faster and easier than graphical programs.  Finding files is faster with commands like "locate filename" than searching from the GUI.  Where the shell really shines is when you need to use things like "[pipes]("https://en.wikipedia.org/wiki/Pipeline_%28Unix%29")," which allow you to chain a series of commands, or write a script to perform a task repeatedly.  Here are two examples I've written about before:

A client had a mailing list of over 40,000 email addresses in a text file and wanted to (a) eliminate some domains from the list, (b) remove duplicates, then (c) sort them by domain.  He tried using a spreadsheet for this task but couldn't figure out the right functions to use. I told him I could do it in a couple of seconds from the command prompt like this:
```
tr '[A-Z]' '[a-z]' < mailing_list | grep -v baddomain\.com | sort -t '@' -k 2 | uniq > sorted_mailing_list
```
That converts the file "mailing_list" to lower-case, excludes "baddomain.com", sorts by the domain part of the address, eliminates duplicates, and saves the result in a new file.  Tasks like these are pretty easy if you know the basics of Unix utilities like grep, awk, tr, and the like.

Another example came from a request on this forum from someone who had 8,000 photos and needed to rotate any that were in portrait mode to landscape.  I proposed a simple script that would iterate over the 8,000 files and rotate only those in portrait.  You can see it here: [http://ubuntuforums.org/showthread.php?t=1951949&p=11814807](http://ubuntuforums.org/showthread.php?t=1951949&p=11814807)

Shells like bash are quite powerful when you need to handle tasks like these.

---

### Post by Bashing-om on 2015-11-02
My response;

I too live in the terminal, and activate a GUI as on-demand. I find that generally the GUI is restrictive of what I want to accomplish - though admittedly there are those times that the GUI is easier and faster for some tasks.
However, my formative years were also before there was a GUI and I am the more comfortable in terminal .

One can not know the power of the system until the terminal is unleashed, and one can not be the master of system until they master the terminal.

Then again, a little bash knowledge, can go a long way .

[INDENT][INDENT]then again
[INDENT][INDENT][INDENT]all in what use you put the tools too .
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Old_Grey_Wolf on 2015-11-02
Most of the people I know that use Linux distros just install it and use the GUI. **That is all they need**. The only time they visit help forums is when they have problems. They don't understand the commands provided to them. They just cut and paste.

On the other hand, I am quite familiar with the CLI; but, that is just my choice. I find it beneficial; but not necessary for a lot of people.

---

### Post by mikodo on 2015-11-02
To OP. I dunno.

I started with computers too late in life to have the time and remaining firings neurons to learn the cli. I like it but, *depend on gui.

To stray from the topic, I wonder what it will be like in say, 20 years from now? Linux is a little older than 20 years. It then and its' predecessors were almost exclusively cli (maybe one can say it all was). I suspect the development will always be cli, but, I wonder if there will be less and less to the point of almost extinction of experienced end-users with the knowledge of the cli. I hope I am wrong. I like watching the, may I call you this, "old-hands", do their magic. They bring much experience and ways of solving problems to the table. Would be a shame to see that knowledge and use in help forums diminish significantly.

Luckily, there remains a plethora of information to learn from for, newer generations than mine.

---

### Post by Sweet_Baby_Jamie on 2015-11-02
> **Old_Grey_Wolf said:**
> They don't understand the commands provided to them. They just cut and paste.

I think it would be a good idea to write down that terminal stuff so if and when you have the same problem you can fix it.  Maybe keep a little notebook of cool helpful commands for this and that, and refer to it.

---

### Post by Old_Grey_Wolf on 2015-11-02
That seems like a good idea. That is until the PPAs don't exist anymore, or the software version numbers change. :)

---

### Post by ardouronerous on 2015-11-03
Do you think there'll come a time where a computer could translate human speech into terminal commands? Like in Star Trek?
[video=youtube;DiPXuo753i8]https://www.youtube.com/watch?v=DiPXuo753i8[/video]

---

### Post by Old_Grey_Wolf on 2015-11-03
> **ardouronerous said:**
> Do you think there'll come a time where a computer could translate human speech into terminal commands? Like in Star Trek?

There already is voice recognition software. I tried it; but, with my accent the results were humorous.

---

### Post by Bashing-om on 2015-11-03
Shucks !

> 
 I wonder what it will be like in say, 20 years from now?


Will be brain waves, and we will be integrated with our computers. Networking to the max !
Voice will be so old fashioned .


[INDENT][INDENT]living off the grid ?
[/INDENT][/INDENT]

---

### Post by yoshii on 2015-11-03
I only know how to do a few basic file management commands at the terminal other than that I use the GUI.  
It works out OK but i sorta wish I knew more of the console commands just to be a power user.

---

### Post by poorguy on 2015-11-05
i go into terminal to find or learn information about my computer etc. i seem to find a lot of info about temps and fan speed control or if i have the sensors available to install use system monitoring software.
i have also fixed a few minor issues i have had by using the terminal. 
copy and paste is my friend when i am in the terminal.

---

### Post by ardouronerous on 2015-11-09
Thanks for the replies to this thread, anyway, I still haven't changed my mind about the Terminal, I treat it like a tool and not as a way of life, and that's because I didn't grow up with MS-DOS, my first operating system was Windows 2000, so I grew up in the GUI era.

Even my Dad was put off by the Terminal, and said that it's been a long time since he'd seen a computer with a black screen with white text and a blinking cursor, he didn't like it, and his reason is, we're in the 21st century and he thought computers of this day and age should be past the MS-DOS style of computing, he remembers how difficult CLI was to use in the 80s and 90s, he once recalled getting stuck when he couldn't recall the commands to get his word processor program to start, so yeah, he was thankful for the advent of the GUI, made things easier.

---

### Post by at35z on 2015-11-10
The everyday user uses the Terminal rarely and that's fine. Those who simply don't need that kind of information will stick to the GUI. Graphic designers, gamers or grandparents sending holiday pictures to family members through the internet will never use it unless there's something unusual.

I only use the terminal if I want to kill a process that really doesn't want to quit, but this only happens rarely and only with a single game, OR install something which is not in the Software Center.

---

