---
title: "terminal logger using script command"
date: 2011-07-03
forum: The Cafe
---

### Post by niki+a on 2011-07-03
Hi,

every time I open up a terminal to do some cml magic, I'd like the entire session to automatically be logged. (Including what is set by PS1 variable before the $, I already added a timestamp + date to PS1 so I can know when I did what.)

I was trying to do something like so inside .bashrc file:

```

#log everything i do in terminal 
script -afq ~/log/shell.log.txt

```

But it does not work, I get really strange output and the standard .bashrc run does not exit properly. I have to ctrl + c and that obviously kills the .bashrc invocation because I do not get my ps1 colors/date formatted.

It's hard to Google this strategy also, because every time I type in .bashrc + logger + script in Google I get newbie tutorials about "running scripts and what is purpose of bashrc".

Next step would be to write a bash script to archive every terminal run in individual files with a time stamp. But I'm sure that will be a breeze once I get this figured out.  

One more thing, if I run script inside terminal, output is formatted very strangely. I get weird line feed characters like so: 

```
^C^[]0; 
```

Any advice on how I can format the output I get from script command? And if you have advice or a resource on how I can Google script command examples or tutorials I would appreciate it, because when I Google script + format output, I don't get the most pertinent results.

---

### Post by papibe on 2011-07-03
I've tried the script command interactively, and it has work for me in the past (except when running an editor like vi though). Have you tried just running it manually when you initiate a session?
 
BTW, are you running Ubuntu Desktop edition? Because another alternative would be to modify your gnome-terminal launcher, and add the -e option:

[LIST]
[*]Right click on the launcher.
[*]Select properties.
[*]Modify the command line so it looks like this:
```
gnome-terminal -e "script ./log/shell.log.txt"
```
[/LIST]
Just a thought, I hope it helps.

---

### Post by niki+a on 2011-07-05
> **papibe said:**
> 
```
gnome-terminal -e "script ./log/shell.log.txt"
```


I thought that would do the trick, but unfortunately it doesn't work. I have a shortcut mapped to pop open a terminal and when I hit it, the terminal blinks open for a millisecond then dies.

Any other suggestions?

---

### Post by jerenept on 2011-07-05
> **niki+a said:**
> I thought that would do the trick, but unfortunately it doesn't work. I have a shortcut mapped to pop open a terminal and when I hit it, the terminal blinks open for a millisecond then dies.

Any other suggestions?

The only thing I can think of is bash history, using the command "history", the output of which can be grepped etc.

For example:
```
jerenept@media-server:~$ history | grep -i "sheep"
 1994  man electricsheep-preferences 
 1995  electricsheep
 1996  electricsheep-preferences 
 1997  electricsheep
 1998  electricsheep-preferences 
 1999  history | grep -i "sheep"
jerenept@media-server:~$ 

```
history | grep -i "sheep"

does a case-insensitive (-i) search for the string "sheep" in my command history.

Not exactly what you were looking for, but I hope it helps.

---

### Post by niki+a on 2011-07-05
Problem solved thanks to this post.

[https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/7131](https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/7131)

```

if [ -z "$UNDER_SCRIPT" ]; then
        logdir=$HOME/terminal-logs
        if [ ! -d $logdir ]; then
                mkdir $logdir
        fi
        gzip -q $logdir/*.log
        logfile=$logdir/$(date +%F_%T).$$.log
        export UNDER_SCRIPT=$logfile
        script -f -q $logfile
        exit
fi

```

Code is courtesy of a poster on that link. 

(you put it in .bashrc)

---

