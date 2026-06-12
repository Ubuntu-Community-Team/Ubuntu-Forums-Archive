---
title: "better .bash_history?"
date: 2011-10-26
forum: Server Platforms
---

### Post by lolium on 2011-10-26
i know we can use the history command and itll come up with like
1 ssh ...
2 ls -l 

etc, is there a way to set it up to capture what the command prints out?

for example if i use custom command awe use at work lets say "db" to search database and it brings up - name - server - password and things like that, is there anything i can set in a .bash* file to capture that so to speak a more advanced bash history

Ive looked online and i cant find anything like this

Can anybody advise any solution which would fit my desire?

apologies that doesnt appear too clear i mean for all commands aswell for example bash_history will say 
ping google.com


but i wish it to say something along the lines of

 ping google.com
PING google.com (209.85.148.99): 56 data bytes
64 bytes from 209.85.148.99: icmp_seq=0 ttl=52 time=22.690 ms
64 bytes from 209.85.148.99: icmp_seq=1 ttl=52 time=21.933 ms
^C
--- google.com ping statistics ---
2 packets transmitted, 2 packets received, 0% packet loss
round-trip min/avg/max/stddev = 21.933/22.312/22.690/0.378 ms


hopefully this is more clear

Thanks in advanced

Sam

---

### Post by haqking on 2011-10-26
> **lolium said:**
> i know we can use the history command and itll come up with like
1 ssh ...
2 ls -l 

etc, is there a way to set it up to capture what the command prints out?

for example if i use custom command awe use at work lets say "db" to search database and it brings up - name - server - password and things like that, is there anything i can set in a .bash* file to capture that so to speak a more advanced bash history

Ive looked online and i cant find anything like this

Can anybody advise any solution which would fit my desire?

Thanks in advanced

Sam

you can redirect all output to a text file with > filename.txt

not sure if you can store that in the command history though, i think it is a per command basis

---

### Post by Lars Noodén on 2011-10-26
> **haqking said:**
> you can redirect all output to a text file with > filename.txt

not sure if you can store that in the command history though, i think it is a per command basis

You can do something like this:

```

[bash](http://manpages.ubuntu.com/manpages/oneiric/en/man1/bash.1.html) 2>&1 | [tee](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tee.1.html) /tmp/filename.txt

```

That will get everything.

---

### Post by Jonathan L on 2011-10-26
> **lolium said:**
> 
etc, is there a way to set it up to capture what the command prints out?


Hi Sam

There are two ways to do this which might help you, both designed for making teaching materials or logging what you're doing for your notes.  I don't know that either is suitable for running all the time though.

_**1.  script**_

This is a program which is like a shell, but which makes the file you describe.
Do this:
```
cd /tmp
script
```And then in that 'shell', do```

pwd
exit
```It makes this file:
```
Script started on Wed 26 Oct 2011 13:15:59 BST
$ pwd
[COLOR=Red]/tmp[/COLOR]
$ exit
exit
Script done on Wed 26 Oct 2011 13:16:09 BST
```See [http://manpages.ubuntu.com/manpages/lucid/man1/script.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/script.1.html)

_**2.  xterm logging**_

You can run an xterm with the flag -l for logging, and you get a very similar result.  I don't believe that the default Gnome terminal will do this.
```

xterm -l
```Makes a file called for example Xterm.log.computer.2011.10.26.13.12.46.6810

[http://manpages.ubuntu.com/manpages/lucid/man1/xterm.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/xterm.1.html)

Hope those help.

Kind regards
Jonathan.

---

