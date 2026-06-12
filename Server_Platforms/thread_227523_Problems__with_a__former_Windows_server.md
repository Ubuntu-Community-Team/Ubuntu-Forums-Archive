---
title: "Problems  with a  former Windows server"
date: 2006-08-01
forum: Server Platforms
---

### Post by bobpur on 2006-08-01
I came was given a server that ran Win NT Server v4.0. It's been a project of mine for about a month. 
Windows is gone and Ubuntu v5.04 server is installed and working (after a fashion). It takes a long time to boot up. I suspect a too small Harddrive and too little memory. I'm working to fix both issues. 
However, as it boots it gets to a message that says "You have mail" and prompts for a command. I don't know what to enter here. What ever I enter, the next line starts out -bash:~$
I've heard of Bash commands but that is the extent of my knowledge. 
Where do I go from here? 
Specs: Not a lot known. 2 gb hard drive. Server is from mid 1990's. That's why v5.04 server.
                               Thanks.

---

### Post by cavalier on 2006-08-01
Unfortunately, what you have here is exactly what you signed up for when you did a server install of 5.04. It drops you right at a shell prompt -- there's no graphical interface installed at all. So, it's doing the right thing, but you need to know where to go from here.

I'd recommend looking at the Server Documentation (see the sticky topic at the top of the Server forum page. And maybe a crash course on how to navigate around in the shell.

---

### Post by reclusivemonkey on 2006-08-03
> **bobpur said:**
> I came was given a server that ran Win NT Server v4.0. It's been a project of mine for about a month. 
Windows is gone and Ubuntu v5.04 server is installed and working (after a fashion). It takes a long time to boot up. I suspect a too small Harddrive and too little memory. I'm working to fix both issues.

Without X, you won't need much memory at all. I am pretty sure my "X-less" server uses very small amounts of memory (<64Mb), even with a few services running. Use

```

free -m

```

To see how much memory is being used. Also

```

tload

```

and

```

top

```

should give you a good view of what is going on.

> **bobpur said:**
> 
However, as it boots it gets to a message that says "You have mail" and prompts for a command. I don't know what to enter here. What ever I enter, the next line starts out -bash:~$
I've heard of Bash commands but that is the extent of my knowledge.

mutt is the default console mail reader on slack, not sure what it is on Ubuntu server, but pine and elm are other alternatives (I'm at work now so can't check on my machine).

> **bobpur said:**
> 
Where do I go from here? 
Specs: Not a lot known. 2 gb hard drive. Server is from mid 1990's. That's why v5.04 server.
Thanks.

I would heartily recommend buying O'Reilly's "Linux in a Nutshell" which will tell you just about everything you wish to know about command line Linux.

By far the easiest way to find out what's in there is open up the box and take a look ;-)

---

