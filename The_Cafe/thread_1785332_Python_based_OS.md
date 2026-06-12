---
title: "Python based OS"
date: 2011-06-18
forum: The Cafe
---

### Post by ki4jgt on 2011-06-18
I thought of PyOS, but it was already taken. Here's the OS concept (spent the last 10 minutes on it.) I'm wanting to put 2 more folders in rootfs (applications and network cache) the rootfs wouldn't be accessible by the user (only the user's personal use folder). If the Python script stopped running, the system would shut down. The system would have access to everything normal desktops have access to, and would automount, so the user wouldn't have to issue a command. Have any suggestions?

---

### Post by ki4jgt on 2011-06-18
Why is this marked as solved?

---

### Post by Spice Weasel on 2011-06-18
[IMG]http://i.imgur.com/J5l6c.jpg[/IMG]

---

### Post by ki4jgt on 2011-06-18
> **Spice Weasel said:**
> [IMG]http://i.imgur.com/J5l6c.jpg[/IMG]

Get the pic. LOL, sorry, I just love the concept. It's kind of cool having a completely text based os.

---

### Post by fatality_uk on 2011-06-18
Where does Python get info about what's on the HD to display in a text based file manager?

---

### Post by Joe of loath on 2011-06-18
Write a kernel in Python. Go on, I dare you :lol:

---

### Post by Tibuda on 2011-06-18
Are you Kenny Strawn on a new account?

---

### Post by ki4jgt on 2011-06-18
> **Joe of loath said:**
> Write a kernel in Python. Go on, I dare you :lol:

OK, LOL, the entire OS, is obviously not in Python :-) I was going with Linux kernel. But, seriously, here's what I have so far. . .

The initial file is PYOS.py

---

### Post by ki4jgt on 2011-06-18
> **Tibuda said:**
> Are you Kenny Strawn on a new account?

Nope

---

### Post by Tibuda on 2011-06-18
> **ki4jgt said:**
> Nope

Too bad, I loved his posts before he was b&.  But I'm starting to enjoy yours.

---

### Post by ki4jgt on 2011-06-18
> **Tibuda said:**
> Too bad, I loved his posts before he was b&.  But I'm starting to enjoy yours.

May I ask why? If it's in my character, I may want to produce more LOL

---

### Post by Tibuda on 2011-06-18
It is just the motivation to make stuff happen or change the world.

---

### Post by ki4jgt on 2011-06-18
> **Tibuda said:**
> It is just the motivation to make stuff happen or change the world.

Thanks for the compliment (I Think :-))

---

### Post by undecim on 2011-06-18
ITT: Confusion about the phrase "Operating System"

I think a Python-based OS built on the Linux kernel would be awesome. It would be easy for code newbies to change just about anything.

Device drivers and such will still need to be binary, though, and maybe some computationally intensive tasks.

Though this would end up being a lot of work to do. You would pretty much be refactoring the entire OS, except the kernel. Perhaps it would be better to just a python based DE.

(Also, I Haven't looked at your script yet, but from what you're describing, I think you've basically written a shell... PART of the OS, but not an OS.)

---

### Post by Joe of loath on 2011-06-18
In the old days there was cshell, where the syntax was similar to that of C. What about pyshell, where the syntax is similar to that of python, for scripting?

---

### Post by undecim on 2011-06-18
> **Joe of loath said:**
> In the old days there was cshell, where the syntax was similar to that of C. What about pyshell, where the syntax is similar to that of python, for scripting?

in a terminal, type 'python' and press enter.

---

### Post by Thewhistlingwind on 2011-06-18
> **Spice Weasel said:**
> [IMG]http://i.imgur.com/J5l6c.jpg[/IMG]

#Fail

---

### Post by ki4jgt on 2011-06-18
> **undecim said:**
> ITT: Confusion about the phrase "Operating System"

I think a Python-based OS built on the Linux kernel would be awesome. It would be easy for code newbies to change just about anything.

Device drivers and such will still need to be binary, though, and maybe some computationally intensive tasks.

Though this would end up being a lot of work to do. You would pretty much be refactoring the entire OS, except the kernel. Perhaps it would be better to just a python based DE.

(Also, I Haven't looked at your script yet, but from what you're describing, I think you've basically written a shell... PART of the OS, but not an OS.)

Well, I was sort of insinuating a DE. The networking and such would still be done by NM. All the programs would be terminal based. It could go on top of an Ubuntu LiveCD, or any other distro for that matter. That way, USB, WIFI, Sound, would already be included.

---

### Post by krapp on 2011-06-18
Please enlighten a Linux user completely ignorant of code: what would be the advantage of a Python OS?

---

### Post by Joe of loath on 2011-06-18
> **krapp said:**
> Please enlighten a Linux user completely ignorant of code: what would be the advantage of a Python OS?

Someone who knows python (probably the easiest language to learn) could modify the OS incredibly easily, I guess?

---

### Post by ki4jgt on 2011-06-19
> **Joe of loath said:**
> Someone who knows python (probably the easiest language to learn) could modify the OS incredibly easily, I guess?

Don't forget BASIC :-) That's why I switched to Python. Besides being interchangable between computers, It's text based. . . Which is what I love most about it.

---

### Post by Dustin2128 on 2011-06-19
What does the python interpreter run on? :P It'd be pretty sweet though if you could figure it out.

---

### Post by earthpigg on 2011-06-19
> **ki4jgt said:**
> Well, I was sort of insinuating a DE. The networking and such would still be done by NM. All the programs would be terminal based. It could go on top of an Ubuntu LiveCD, or any other distro for that matter. That way, USB, WIFI, Sound, would already be included.

What you are describing is not a computer operating system.

It is a user interface.

And there is absolutely not a single thing wrong with creating or working on a user interface that you see potential value in. In fact, I would say that is a very **good** thing - if you see value in something, it is almost certain that other people will see value in it as well. So by all means, hack away, have a blast, learn, all that good stuff, and continue to share what you are working on.

But please call it what it is: it is a user interface, not an operating system. Your credibility is damaged if you claim otherwise, and I don't think you want that.

---

### Post by Tibuda on 2011-06-19
> **earthpigg said:**
> But please call it what it is: it is a user interface, not an operating system. Your credibility is damaged if you claim otherwise, and I don't think you want that.

Don't be harsh. He is just confused.

---

### Post by ki4jgt on 2011-06-19
Well, the OS, is actually based on Python. It's not harsh, though, it's fact. Most people would assume it to be labeled a UI, The terminology was misleading, He was simply stating this. No harshness to it, on that note. . .

Does anyone know any apps I can include with this, I mean, real, quality, command-line apps, which have been created in python?

---

### Post by jerenept on 2011-06-19
> **ki4jgt said:**
> Well, the OS, is actually based on Python. It's not harsh, though, it's fact. Most people would assume it to be labeled a UI, The terminology was misleading, He was simply stating this. No harshness to it, on that note. . .

Does anyone know any apps I can include with this, I mean, real, quality, command-line apps, which have been created in python?

Start out with cat, it's pretty simple.

---

### Post by ki4jgt on 2011-06-19
> **jerenept said:**
> Start out with cat, it's pretty simple.

have a link? All I keep getting is a Python eating a Cat from Youtube. . .

---

### Post by ki4jgt on 2011-06-19
> **Quadunit404 said:**
> [IMG]http://s3.amazonaws.com/kym-assets/photos/images/original/000/131/351/eb6.jpg?1307463786[/IMG]

An OS written entirely in Python? Really? Well... Python is a scripting language, and scripting languages are not known for their speed compared to compiled languages, so an OS based entirely around Python would be v e r y s l o w.

Answer to question already answered please ref: post #18

Since it is command-line based, it will require less resources to pull off, and less speed. The places where speed will be an issue, it will be up to the programmer of that particular program to maneuver the obstacles.

---

### Post by jeffathehutt on 2011-06-19
If you can't find one pre-made, you could probably create your own cat in python.  I can't imagine it would be more than 20 lines. :)

---

### Post by Hwæt on 2011-06-19
> **ki4jgt said:**
> Answer to question already answered please ref: post #18

Since it is command-line based, it will require less resources to pull off, and less speed. The places where speed will be an issue, it will be up to the programmer of that particular program to maneuver the obstacles.

Even as a text-based language, Python is extremely slow. If you really think that you can go somewhere with it, though, give it a shot. I'm sure plenty of people called Linus crazy. :)

---

### Post by earthpigg on 2011-06-19
> **ki4jgt said:**
> have a link? All I keep getting is a Python eating a Cat from Youtube. . .

open a terminal

```
cat .bashrc
man cat
```

---

### Post by Barrucadu on 2011-06-19
> **ki4jgt said:**
> Well, the OS, is actually based on Python. It's not harsh, though, it's fact. Most people would assume it to be labeled a UI, The terminology was misleading, He was simply stating this. No harshness to it, on that note. . .

I might be misinterpreting you, but how is the OS written in Python of you're using the Linux kernel and sticking this on top of Ubuntu (using, as you said, NetworkManager for example)?

---

### Post by NightwishFan on 2011-06-19
Please start from the basics and work your way up..

---

### Post by KiwiNZ on 2011-06-19
I have removed a number of posts from this thread, why ?  Read the following section of the Code of Conduct, it is self explanatory.....

"3. Trolling, Attacks and Flaming: These are always forbidden......"

---

### Post by ki4jgt on 2011-06-19
> **Barrucadu said:**
> I might be misinterpreting you, but how is the OS written in Python of you're using the Linux kernel and sticking this on top of Ubuntu (using, as you said, NetworkManager for example)?

I didn't say it was written in Python. I said it was based on Python. As in that's the theme of the OS. This is why I said it could be misleading. Based could also be interpreted as founded or starting off of, Python, that is why I said Most people assume it to be labeled a UI, but the theme of the OS, is Python, so it is based on Python. However base could be interpreted as actual base where the OS, would bootup from a python kernel. I think it's possible, but VERY COMPLEX to achieve. I know I'm not going to attempt it :-) but from perspective of theme, it is based on Python. All the programs will be Python. I'm even looking into ncurses and a little more into threading for multiprocessing.

---

### Post by Quadunit404 on 2011-06-19
> **KiwiNZ said:**
> I have removed a number of posts from this thread, why ?  Read the following section of the Code of Conduct, it is self explanatory.....

"3. Trolling, Attacks and Flaming: These are always forbidden......"

And I suppose that my posts were among the victims.

On topic: If you want to succeed, find a good book on Python, and make sure it's up-to-date. You did state you have no programming experience, right?

And further, what about your Python-centered DOS distribution you wanted to make a few months back? What happened to that? :|

---

### Post by ki4jgt on 2011-06-19
> **Quadunit404 said:**
> And I suppose that my posts were among the victims.

On topic: If you want to succeed, find a good book on Python, and make sure it's up-to-date. You did state you have no programming experience, right?

And further, what about your Python-centered DOS distribution you wanted to make a few months back? What happened to that? :|

This is an offshoot of that project. You guys said it had security glitches, so I've made some improvements :-) Linux based now. . . I do have programming expirience. I programmed in BASIC (on and off) for the last 9 years. I would've brought this back up there, but it was just too hopeless, the idea was DOS, now it's Linux.

***EDIT: not to mention the over whelming amount of people, who would've opened the thread, read the first few posts, and then said. . . Hmmm. . . DOS won't work. So, new idea required new thread.

---

