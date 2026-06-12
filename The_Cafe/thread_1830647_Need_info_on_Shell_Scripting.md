---
title: "Need info on Shell Scripting"
date: 2011-08-22
forum: The Cafe
---

### Post by mixint27 on 2011-08-22
Hello everybody!

Im currently learning how to do scripts. I was wondering what books you recommend to read for beginners. Somehow I'm finding it hard to find some good info online; some info is really outdated (dont know if it matters though), and there are not that many examples of scripts.  I followed some examples on youtube and on other websites but I cant find anything that i can follow step by step. Everything seems to be thrown out there for you.

I went to my local library and could not find anything. I checked out Linux Bible but only has a chapter on Shell Scripts. I went to Barnes and Noble and nothing.

Also, for those who create scripts, why do think its important to learn? how can i use it in my every day life?

I created a simple script, and im impressed with what i came up with even though its cheesy haha...how do you run it without running the terminal? I have tried everything! 

Thanks in advanced for your input.

---

### Post by sanderd17 on 2011-08-22
[http://linuxcommand.org]("http://linuxcommand.org")

You can just double click on a script, or let it execute at certain times with cron, or at boot time by putting it in certain configuration files.

---

### Post by FreeTheBee on 2011-08-22
There is the advanced bash scripting guide
[http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

The 'Linux Command Line and Shell Scripting Bible' is quite a nice book, I think.

---

### Post by aeiah on 2011-08-22
> **mixint27 said:**
> how do you run it without running the terminal? I have tried everything! 



most of my scripts are run automatically at specific times of the day/week using cron. other ones, if i don't need any feedback (or the feedback is provided by notify-send) i just set as a menu item. others, i may set as a menu item but make them run in a terminal, so i can see the progress etc by launching with the command:
```

gnome-terminal -e ~/path/to/script.sh
```


i dont think i ever really set out to learn how to script. over the years ive just wanted to do things, and so i learn how to do specific things.

---

### Post by sisco311 on 2011-08-22
Check out the Bash Guide at [Greg's Wiki]("http://mywiki.wooledge.org/") alongside with BashFAQ and BashPitfalls on the same page. 

I don't recommend the Advanced Bash Scripting Guide, unless you know how to filter out the junk...

---

### Post by alan2796 on 2011-08-22
> **mixint27 said:**
> 
Also, for those who create scripts, why do think its important to learn? how can i use it in my every day life?


I use scripts on a daiiy basis, mainly for backup purposes.

I wrote a few scripts, one for backing up my important files such as my android workspace, documents, pictures etc... to a encrypted 7z Archive. -  I keep a copy on my USB Keyring which i carry with me at all times (encrypted incase i loose it) and it also has a copy of puppy linux and software for mac and windows to decrypt the archives incase want to use them on my macbook or at work.

I use another script other for copying the archives into my dropbox folder for offsite storage, and another which rsync's my home folder to a external USB hardrive, can you see im paranoid about loosing data ?.

One more because I dont have a static ip address and incase I want to access my PC from my phone or another PC I have a script run every hour via crontab which gets my external ip address and saves it into a txt file in my dropbox folder saves using any of them no-ip type services.

---

### Post by ninjaaron on 2011-08-22
> **mixint27 said:**
> Also, for those who create scripts, why do think its important to learn? how can i use it in my every day life?
I don't use them for cron tasks like most of the posters in this thread.  I use them to do weird stuff that would otherwise take a long time manually.  I started scripting when I had 4000 files that I needed to change from uppercase to lowercase, and I wasn't about to do it by hand.

I also wrote a script to invert the directory structure of the Faenza icon theme, so it would be like any other theme (so I could mix and match certain icons if I wanted).  I also wrote a script that would download thousands images off of a site by following the links because I couldn't access the directory directly (like Zuckerberg does in the Social Network at the beginning; and yes, they were pictures of girl's butts, if you must know).

I also wrote a whole bunch of scripts to combine a bunch of programs to rebuild the interface for my netverible, so it would have independent modes for netbook and tablet operation, as well as landscape and portrait screen orientations.  I'm most proud of that.

> I created a simple script, and im impressed with what i came up with even though its cheesy haha...how do you run it without running the terminal? I have tried everything!

Well if you have the permissions of the script set to executable, as I assume you must if they are running at all, you should get a question for what you want to do (run in terminal, display, run, cancel).  If you just hit run, it will execute without a terminal.  You can also set scripts as commands for launchers or even key combinations, or run them with alt+f2.

Of course, if the script requires user input, you will need to run them in a terminal.  There is a program called zenity that allows you to create simple GUI elements for interacting with bash scripts, but I've never tried it.

If you want to script more advanced GUI interfaces with full gtk+ support, you will need to learn a more advanced scripting language like Python or Perl.

---

### Post by mixint27 on 2011-08-23
> **FreeTheBee said:**
> The 'Linux Command Line and Shell Scripting Bible' is quite a nice book, I think.

Thank you everybody for your input! Im gonna have to look into Linux Command Line and Shell Scripting Bible....

Zenity was what i was looking for. Thanks for bringing it up!

By reading the bible hopefully I get to create some really nice scripts!

Again, thanks!

---

### Post by handy on 2011-08-23
This is a good place to start, & its in the Ubuntu wiki too:

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

---

### Post by amiacamal on 2011-08-23
[QUOTE

The 'Linux Command Line and Shell Scripting Bible' is quite a nice book, I think.[/QUOTE]

+1.

I'v only glossed over this, but found it quite good.

---

