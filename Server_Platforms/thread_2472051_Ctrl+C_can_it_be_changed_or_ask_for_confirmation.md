---
title: "Ctrl+C can it be changed or ask for confirmation"
date: 2022-02-16
forum: Server Platforms
---

### Post by bigmonmulgrew on 2022-02-16
Today I messed up.

I was running a release upgrade on my server and pressed Ctrl-C

Thought I was in a web browser but my focus was apparently in my remote session.

It was at the point where it was asking me to resolve differences in configuration files.

Well that's not my point for this post. It's just my game server and I was considering a fresh install anyway. I am trying to fix it to see if I can but that's another story.

I've used Ctrl C at the wrong moment before. Usually times it doesn't really matter and I just re run the command. Given that it can cause some serious issues can it be reassigned or maybe have a prompt added. Is there a way to do that.

---

### Post by MAFoElffen on 2022-02-16
Start a terminal session and 
```

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get upgrade
sudo apt-get autoremove

```

---

### Post by bigmonmulgrew on 2022-02-16
Already done. Thankfully all looks good, except I have a janky version of MOTD and a nicely formatted one.

---

### Post by LHammonds on 2022-02-16
Rather than trying to re-define a global standard, you might want to consider doing things different if that concerns you.

For example, instead of leaving whatever command you issued to be running in the foreground, try running it in the background or a different screen session so that you can do other things and not potentially mess up what the command is doing.

For example, you can run a command starting with "nohup" which means "no hang up" if you lose your terminal connection....it will continue to process even if you X out of your PuTTY session.  The 2nd part is an ampersand at the end which sends it into the background task.

```
nohup bash ~/myscript.sh &
```

Once you execute the command, it will happily run in the background and you have your prompt to continue doing other things.

If you want to bring it back into the forground (in case it is prompting you for a response), just type fg which is short for "foreground"

```
fg
```

But be aware that when you start the command, nohup will redirect all output that normally went to standard out and standard error to a file called nohup.out by default but of course, you can redirect output as you see fit.

Another option is to use "screen" and rather than me writing a book to explain it, I'll post a link (guess I should have done that with nohup too)

[https://www.howtogeek.com/662422/how-to-use-linuxs-screen-command/](https://www.howtogeek.com/662422/how-to-use-linuxs-screen-command/)

**EDIT: **If you put your command(s) inside a Bash script, you can trap CTRL+C temporarily to allow the script to continue.

[https://rimuhosting.com/knowledgebase/linux/misc/trapping-ctrl-c-in-bash](https://rimuhosting.com/knowledgebase/linux/misc/trapping-ctrl-c-in-bash)

LHammonds

---

### Post by bigmonmulgrew on 2022-02-25
Ok this is probably the best reply I could have gotten, thanks Lhammonds. 

While it does not achieve what I asked for, it does what I intended. This will work great.

---

