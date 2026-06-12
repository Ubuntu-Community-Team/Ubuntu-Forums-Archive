---
title: "Debian / Ubuntu Command Line Interface"
date: 2013-04-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Drenriza on 2013-04-24
So i primarily come from the networking "world", where i heavily use Cisco equitment (because it is the best in my opinion).
And of course on this equitment you work 100% in the CLI(yes their is a web interface).

And their was a thing that struck me, which i'am now pondering on.

When you hit ? in the Cisco CLI, you get a overview of available commands.
If you start a command and then hit ? you get a overview of available options, or you will get a notion of what to do next.

Example you type
```
router eigrp ?
```
Then you'll be told to enter a process ID.

Why is such not available in Debian / Ubuntu.
If you start a rsync command (for example), they can be quite long.

So you start
```
rsync -v -r --log-file=/path
```
And maybe now wonder "whats next?".

Then you would either need to open a new terminal and see the synopsis in the manual or go [HTML]http://linux.die.net/man/1/rsync[/HTML].
Here a ? could tell you.

[LIST]
[*]Enter source path.
[/LIST]
or

[LIST]
[*]Enter user@ip: (of remote system)
[/LIST]
So if you go
```
rsync -v -r --log-file=/path user1@10.0.0.1:
```
and hit ?
it could tell you.
[LIST]
[*]Enter the path of the file you want to move from the remote system
[/LIST]
```
rsync -v -r --log-file=/path user1@10.0.0.1:/random/file/path
```
?
[LIST]
[*]Enter destination on local system to where you want to save the file
[/LIST]
```
rsync -v -r --log-file=/path user1@10.0.0.1:/random/file/path .
```

Now i don't have a problem using the rsync command ,)
But is it only me who think the general idea could be usefull, for different commands?

**The descriptions could be boiled way down, just an example.**

Let me hear your thoughts of why this is not available. If it was a decision taken or people just didnt add it to the commands.

Kind regards.

---

### Post by Lars Noodén on 2013-04-24
bash's tab completion does let you get some ideas of your options for some programs, but maybe not so detailed in all cases.  I guess that's the area you would like to see developed.  Below are some work-around in addition to the one about opening a second terminal.

If you are browsing a manual page, you can press bang (!) and then enter a command which will run before returning back to the manual page.  

Of you could use the terminal multiplexer tmux and have several panes open at the same time.

---

### Post by grahammechanical on 2013-04-24
What you are asking about is not properly called the Debian/Ubuntu Command Line Interface but the BASH Shell Command Processor. And as such the limitations or freedoms of Bash are those coded in by the developers.

[http://ss64.com/bash/](http://ss64.com/bash/)

---

### Post by coldraven on 2013-04-24
I use a combination of guake (drop down terminal with tabs) and the browser.
That way I can just copy/paste from the man page in the browser or the other terminal tab.
Compared to the old DOS terminal I'm in heaven.

---

### Post by CharlesA on 2013-04-24
Aww, I was going to suggest looking at the man pages, but coldraven beat me to it. :)

If you contrinue to use the terminal, you will get a better idea of what commands do what. I've used rsync the longest, but I sometimes need to look at the man pages if I am need to use different options than what I am used to.

---

### Post by apmcd47 on 2013-04-24
I don't know much about the Cisco CLI but I'm guessing it is a monolithic system containing all commands as part of the system. When you type a command in the Cisco CLI and hit "?" it knows what you are typing and is able to make suggestions as to what goes next.

Unix went a different way, and Ubuntu is basically a clone of Unix. Unix created a minimal CLI command processor and allowed its users to add new commands in the execution path.  The Unix shell, in the case of Ubuntu this is bash, doesn't know what should come next, unless it can interrogate the command somehow, and I imagine this could add an overhead to the process of typing in a command. Bash could do this for all its built-in commands but then you have the counter-intuitiveness of some commands grok the "?" and others don't.

It's also a matter of expectation. thanks to Cisco you are used to it and expect it. I, on the other hand, have used Unix for something like 20 years, never expected it and therefore don't miss it.

It could be done, but at the cost of an awful lot of rewriting an awful lot of code.

Andrew

---

