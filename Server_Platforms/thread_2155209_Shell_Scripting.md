---
title: "Shell Scripting"
date: 2013-06-17
forum: Server Platforms
---

### Post by ally_uk on 2013-06-17
Hi guys I have developed a interest in Linux and Open Source Technologies I wish to develop my skills further and to become more productive in my spare time and actually learn some stuff. 

I am pretty comfortable using the command line and am willing to get my hands dirty. The first area of interest is Shell Scripting, Now I am not a programmer I don't think like a programmer or have the programmers godlike mentality Variables? For? Loops? it currently all goes over my head :)

So for somebody who knows nothing about scripting or programming concepts how do you begin to learn to script? am I out of my depth here? is there a suitable beginners course or tutorial or book out there? which starts you off with the basics i.e hello world and takes it a step further with introduction of variables etc.


How did you guys start with Linux? what kind of projects did you start with and how much time do you need to dedicate to it to develop a solid understanding.

Thanks for the help appreciate the insight :)

---

### Post by Cheesemill on 2013-06-17
Check out the Ubuntu wiki, specifically the links on this page...

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by prodigy_ on 2013-06-17
Well, I learned bash when I was creating a script that would install and auto-configure xl2tpd (my ISP uses L2TP for user auth). Initially I wrote a small script but eventually it grew to over 1k lines and at some point the project became too time consuming for me to maintain. My code was really naive and quite ugly but it worked. :)

You don't need programmer's mentality but you still need to think before and while writing any piece of code. If it feels wrong and clumsy, it probably is. Sometimes perfection isn't worth it but often better algorithm is also shorter and clearer. So learn your tools - use control flow statements (for/while, if, case) whenever possible. Split any complex problem into smaller problems and solve them one by one. Read man pages, use Google and don't be afraid to ask for help.

---

### Post by CharlesA on 2013-06-17
I started out the same ay prodigy_ did. I think my first shell script was one to handle daily backups and it was a mess at first but kept getting refined as time went on. I eventually wrote up a virtualbox startup script to gracefully shutdown/startup any VMs that were running and now I think vbox has one of those scrips builtin now.

One thing that has been invaluable to me is testing my scripts on a test box.... don't run anything on production unless you want a lot of pain and tears. ;)

---

### Post by 3L33T on 2013-06-17
These days, google is your best bet in learning shell programming for free.

The basic shell programming examples dating back from year 2000 from the tldp.org in one of the google search results is still very much accurate even to this day.   The logic operators has not changed much, if at all.

---

### Post by chrisguk on 2013-06-17
Hi ally_uk,

You have chosen a great subject and one that is very close to my heart.  I certainly commend you for wanting to have a dabble at shell scripting.  So here is my two cents:

Before you think about shell scripting I always found the following questions helpful when evaluating my expectations:

1.   What do you expect to get out of it?
2.   What do you think it will do for you?
3.   Do I have enough base knowledge to understand the scripting elements?

So, for question one.  Shell scripting is fairly lightweight and in my opinion there is a real for that.  It won't do everything, it's not a programming language and as such it has limitations.  Have you ever thought about Python?

For question two, this is quite fundamental in itself really because there and tonnes of things you need to know about the system you want your script to work on.  For example; a shell script that works on Ubuntu may not necessarily work on Arch Linux and vice versa.  This is no way to put you off, just an attempt to get your mind going.  As it was suggested above "Google" has a lot of search returns regarding the subject and its for that reason people don't really need any knowledge because you can just cut and paste things and hope it works.

It is very important to understand the pseudocode basics though for example:

What will the command "**echo**" do for you or "** echo -e "This is my text"** "

"**IF**" statements and "while loops" are your friend.  They will help you with an endless list of options in order to make your scripting as interactive as possible for the end user.

Most programmers and I include myself this this example, sit down with some paper and sketch out the base structure of what we want to achieve.  The we start punching out the keys in front of the monitor.

Good luck by the way and feel free to ask more questions, though I think we may be abusing shell scripting in this section of the forum as technically it's not just for server platforms.

---

### Post by ally_uk on 2013-06-18
Thanks for the replies :) I basically want to learn how to automate some administration tasks, such as backups, creating users, package updating script. Plus the learning about essentially the basics to build a solid foundation once I have become comfortable I will learn Python. You wrote over 1000 lines of code? I can write two lines :)

---

### Post by localhost8080 on 2013-06-18
> **ally_uk said:**
>  You wrote over 1000 lines of code? I can write two lines :)


lol, they all start with two lines and grow and grow!

I'd recommend setting up a github repository and storing your scripts there, that way you can edit them and keep them for longer and move the scripts to new machines easily :)

---

### Post by ally_uk on 2013-06-18
Hehe so what resources did you use to learn to write over 1000 lines of code right now I am struggling to get off the mark

---

### Post by CharlesA on 2013-06-18
> **localhost8080 said:**
> lol, they all start with two lines and grow and grow!

Ain't that the truth. I've got a simple vbox script i wrote to power down the VMs before the system rebooted and that went from simple and a monster.

> **ally_uk said:**
> Hehe so what resources did you use to learn to write over 1000 lines of code right now I am struggling to get off the mark

All it takes is practice. Depending on the language, of course.

This one is pretty cool :D

[http://www.learnpython.org/](http://www.learnpython.org/)

---

### Post by koenn on 2013-06-18
> **chrisguk said:**
> Hi ally_uk,
 It won't do everything, it's not a programming language and as such it has limitations.  
.
While they certainly have their limitations, unix shells, at least the wellknown ones like bash and such, are Turing complete programming languages


> **chrisguk said:**
> Hi ally_uk,
 there and tonnes of things you need to know about the system you want your script to work on.  For example; a shell script that works on Ubuntu may not necessarily work on Arch Linux and vice versa.  .
depends on what you're doing and how you do it. A shell script that works on my Ubuntu might not even work on your Ubuntu, if it happens to call an external program that I have installed and you haven't; or if it looks for a file that is present on my system but not on yours. But there are ways to avoid such obvious bugs. The same is true for programs written in more sophisticated languages - they're just likely to have better facilities to avoid or work around such problems. 


I think for an absolute beginner who wants a quick intro in "how do a make a computer do stuff automatically", bash is a readily available good-enough solution.

---

### Post by koenn on 2013-06-18
> **CharlesA said:**
> 
All it takes is practice.]
you mean lack of practise ?  :-)

---

### Post by ally_uk on 2013-06-19
It's all well saying practice but how do you practice when you don't know where to start? :P

Where are the guides / howtos?

---

### Post by Lars Noodén on 2013-06-19
> **ally_uk said:**
> It's all well saying practice but how do you practice when you don't know where to start? :P

Where are the guides / howtos?

There are a lot of sources listed in this thread:

[http://ubuntuforums.org/showthread.php?t=2155675](http://ubuntuforums.org/showthread.php?t=2155675)

I can't propose an order in which to read them.  You'll have to skim them and decide which to tackle first.

---

### Post by CharlesA on 2013-06-19
> **ally_uk said:**
> It's all well saying practice but how do you practice when you don't know where to start? :P

Where are the guides / howtos?

Depends on the language. If you want to check out Python, check the link I posted earlier as they have some very nice tutorials. There is also a "Learning Python" book which is also handy.

---

### Post by 3L33T on 2013-06-20
> **ally_uk said:**
> It's all well saying practice but _how do you practice when you don't know where to start_? :P

Where are the guides / howtos?

Well first you have to have a goal: where DO YOU want to start? :D

You indicated earlier that you want to do backup, so, start googling for basic backup shell scripts and you'll find plenty.  Keep in mind, in linux/unix, any backup utilizes one or combination of the linux/unix 'tar' , 'cpio', and 'rsync' commands.

---

