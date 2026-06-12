---
title: "iptables question"
date: 2010-01-20
forum: Server Platforms
---

### Post by shred_eng on 2010-01-20
hi, can anyone tell me how this iptables rule should be laid out,  i copied it from a post somewhere but it brings up an error : unknown arg'  --set-mark

iptables -t mangle -A FORWARD -p tcp --dport 27960 -j MARK --set-mark $MARKPRIO1

this is with ubuntu server 9.04

iptables v1.4.1.1

thx,

---

### Post by Lars Noodén on 2010-01-20
Is the right module loaded to allow **mark** ? If I recall correctly it is CONNMARK.

Is the variable MARKPRIO1 containing a valid mark value and or mask?  It looks like the error might be with the value in the variable.

---

### Post by shred_eng on 2010-01-20
"Is the variable MARKPRIO1 containing a valid mark value and or mask? It looks like the error might be with the value in the variable."

im not sure what you mean, what kind of values and masks are there? 

i guess MARKPRIO1 just means high priority, sorry i cant come up with a clearer answer, i just literally copied it and tried to apply it.

is the module "mark" included with ubuntu server 9.04? cos i didnt realise i might have to load it, if i do how would i go about it?

i'll try CONNMARK first though and see what happens,  :)

thanks for the reply ,

---

### Post by shred_eng on 2010-01-21
well, i tried CONNMARK but it says bad argument CONNMARK

this isnt a very important thing as i'm only experimenting with iptables and most of the things i've tried seem to end in some error or other, all im trying to do is get iptables-restore to load some rules testing with /etc/iptables.test.rules but using some examples that i've found, dont seem to use the same syntax or something. anyone got some rules in a restore-save file working on ubuntu 9.04 that i can copy as an example ? :)

---

### Post by Lars Noodén on 2010-01-21
> **shred_eng said:**
> "Is the variable MARKPRIO1 containing a valid mark value and or mask? It looks like the error might be with the value in the variable."

im not sure what you mean, what kind of values and masks are there? 


When you put this echo into the script, what does it show?

```

echo The value of MARKPRIO1 is "$MARKPRIO1"

```

---

### Post by shred_eng on 2010-01-21
i havent actually managed to get a script to work, it always fails on line 1

i typed the line that i put in my first post, directly into the terminal, i've mostly been using ufw to add stuff but i want to try and understand iptables and the things i have entered into iptables has been by using the terminal ie: sudo iptables -A INPUT then some stuff which appears to have worked. so i dont know how i can add your code to a script that doesnt work, sorry, but i'm pretty clueless at this time, 

thanks for trying but i need to find a simple example to add more things to and learn how its put together, i presume the versions of iptables must change syntax over time. :confused:

thx,

---

### Post by Lars Noodén on 2010-01-21
> **shred_eng said:**
> i presume the versions of iptables must change syntax over time. 

Nope.  Still the same after all these years.  ipchains was a little different, but it was a different tool.  You do get some new modules for IPTables from time to time, though.  But the syntax is the same.  


When editing filter rules, you have several ways of creating rules for IP Tables:

1) shell script - you only need a few items in your script to work with iptables, but the generic guides are here:

[http://steve-parker.org/sh/intro.shtml](http://steve-parker.org/sh/intro.shtml)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

2) the utilities [iptables-save](http://manpages.ubuntu.com/manpages/karmic/en/man8/iptables-save.8.html) and [iptables-restore](http://manpages.ubuntu.com/manpages/karmic/en/man8/iptables-restore.8.html) - save a copy of the working tables, save a second copy to edit, work on that second copy with your favorite text editor

[indent]
```

# make a backup, for this session only
sudo iptables-save > /tmp/last-known-working-filter.iptables

```

then

```

# get a working copy
sudo iptables-save > /tmp/play-copy-of-filter.iptables

# make your changes with kate or geany
kate  /tmp/play-copy-of-filter.iptables

# clear the deck
sudo iptables -F

# test them
sudo iptables-restore < /tmp/play-copy-of-filter.iptables

```

Your changes will go away upon reboot  but if you want to undo them sooner

```

# clear the deck
sudo iptables -F

# make a backup, for this session only
sudo iptables-restore < /tmp/last-known-working-filter.iptables

```
[/indent]


3) [ufw](http://manpages.ubuntu.com/manpages/karmic/en/man8/ufw.8.htmlhardy.html) - which is a simple text UI for IPTables

4) Firestarter or Fwbuilder - these are graphical programs to work with several types of filter, including IPTables


In the long run, options 1 and 2 are the most powerful.  Option 1 is easiest if you are also doing system administration because it is shell-based.  Option 2 is easiest if 'all' you want to do is edit a file, I'd recommend that one.

If you are working on the rules for remote machine, then ask about how to keep from locking yourself out.

---

### Post by shred_eng on 2010-01-21
thanks for the link to shell scripting, i'll read through that. 

i have kind of opted for iptables-save and iptables-restore but need to write some rules that work first.

thanks for your help

---

