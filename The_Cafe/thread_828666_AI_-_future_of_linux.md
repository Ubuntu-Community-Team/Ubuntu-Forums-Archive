---
title: "AI - future of linux"
date: 2008-06-14
forum: The Cafe
---

### Post by bannik on 2008-06-14
well its a question and a topic, i wanted to ask from your experiences (games, programmes other software etc)how powerful is the current AI

I ask because of a feature of linux that some people say is amazing whilst others think it ruins linux chances of success

the terminal

yep that little command line programme gets everyone worked up, but in my opinion it should not be removed even if its complex but it should be mixed with some form of AI (not real AI)

the main problem with the terminal is the need to remember lots of commands for simple actions that most users dont want to learn but if you make an AI that recognizes commands and helps you out when you don't could make linux even better..

take this for example

sudo shutdown -h +50    this command makes the computer shutdown after 50 min, it took me 3 days to find that command line so wouldnt it have been better for me to type

shutdown the computer in 50 min

and the terminal with built in AI would recognize it and continue the command...

this way even new users should not find it hard to use




ps i am a hippie (hint hint) so i am sorry for the lack of sanity

---

### Post by lisati on 2008-06-14
I don't think we'll be able to completely do away with some form of command-line interface Yes - it can be daunting learning the commands, but on occasion, the command line is simpler, quicker and more to-the-point. 

We can all be thankful that we don't have to toggle switches to get the BIOS or bootloader up and running!

```

C:
C:\DOS
C:\DOS\RUN
run\dos\run

```
(just teasing!)

---

### Post by Silpheed2K on 2008-06-14
I really think we should just add an interface to what would normally be handled strictly in the terminal. That would make it a lot easier.

---

### Post by bannik on 2008-06-14
> **Silpheed2K said:**
> I really think we should just add an interface to what would normally be handled strictly in the terminal. That would make it a lot easier.

sure it would but in my eyes the terminal is part of linux, you cant remove it, its like a trademark, all you can do is make it better.

also if you do make an interface 1 its going to be huge and it will just make linux closer in look and feel to windows.

[http://wackyrobot.com/ace/src/preloebnertestchat.php](http://wackyrobot.com/ace/src/preloebnertestchat.php)
[http://www.woomerang.com/zalphachat/](http://www.woomerang.com/zalphachat/)
[http://www.pandorabots.com/pandora/talk?botid=f5d922d97e345aa1](http://www.pandorabots.com/pandora/talk?botid=f5d922d97e345aa1)


here are a few chat bots AI - imagine not only giving your linux a command but it talking back and giving you hints...

its the future and the future smells great

---

### Post by shadylookin on 2008-06-14
adding artificial intelligence to simple commands would cause a lot of bloat and it's not a lot of developer's strong point. It just sounds like a lot of work for a developer just so a user can avoid reading man pages(even then you'd probably still have to read them to figure out all the possible options) 

I don't see it happening because there isn't a big desire for it.

---

### Post by keiichidono on 2008-06-14
> **shadylookin said:**
> adding artificial intelligence to simple commands would cause a lot of bloat and it's not a lot of developer's strong point. It just sounds like a lot of work for a developer just so a user can avoid reading man pages(even then you'd probably still have to read them to figure out all the possible options) 

I don't see it happening because there isn't a big desire for it.
I agree, the terminal is fine as it is as that would only add a ton of bloat and slow it down. If you wanna find/develop a GUI tool that customize the shutdown time then go ahead and put it in a repo. Otherwise the terminal shouldn't change. Bash itself is a "programming language" because you can make it do powerful things, you don't see people requesting to make C++ have AI so you can type in "Make a browser faster than Firefox but still easy to use with a nice GUI" and expect results.

---

### Post by madjr on 2008-06-14
The closest thing you could get is Hotwire (a powershell)

[http://hotwire-shell.org/](http://hotwire-shell.org/)

a .deb here (says gutsy but works in hardy, no dep. problems):
[http://getdeb.net/app/Hotwire](http://getdeb.net/app/Hotwire)

it **auto-completes commands** and even has an **integrated file browser** so you don't have to type in manually the location of a file or directory.

the problem with a powershell is that it has **too many features**, so it's kinda bloated. It has features most users won't use.

i would love **something simpler in between** the normal terminal and hotwire. 

Someone should fork it and remove all other features and just leave the auto-complete (file browser + other features could be added as a plugin)

---

