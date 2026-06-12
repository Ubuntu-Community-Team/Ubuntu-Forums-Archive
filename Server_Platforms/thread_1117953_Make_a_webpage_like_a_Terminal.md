---
title: "Make a webpage like a Terminal"
date: 2009-04-06
forum: Server Platforms
---

### Post by oneadvent on 2009-04-06
I'm sure  you've seen them, peoples webpages look like a terminal, where they have a limited set of commands and can play around a bit. I want to set one of those up, where can i find a starting point?

Thanks.

---

### Post by volkswagner on 2009-04-06
Do you have a link?

---

### Post by oneadvent on 2009-04-06
Actually no. I found them by stumbleupon before, and i looked back on my stumbling history to try to find them. Unfortunately I have stumbled 10k pages. I couldn't find an example. I tried Googling, and still nothing.

I was hoping someone else had seen them and knew what I was talking about, or a good idea on how to proceed forward with that kind of design idea. 

It kinda looks like an ssh connection of somekind, but no flash or active-x stuff. I am thinking CGI of some kind.

---

### Post by oneadvent on 2009-04-08
Did I stump the Linux community? I hope not, I have seen them before.

I just cant think of a good way to make a black webpage with a prompt that looks like a terminal. Thats really all it would take, then just interpreting the commands they put in, which while time consuming, not impossible.

</rant>

---

### Post by benj1 on 2009-04-08
do you mean like goosh?

[http://goosh.org/](http://goosh.org/)

---

### Post by oneadvent on 2009-04-08
YES exactly. I am so happy you pointed me to one.

Do you know the process behind it?

---

### Post by hictio on 2009-04-08
I have some implementations like this on [Webmin](http://www.webmin.com/), or, better yet, within the same Webmin.
One is called "Command Shell", you have a small input box, and you can execute a command, and get the printed output, obviouslly, that wont't work for interactive tasks, IE: editing a file :D

The other one its called "SSH/Telnet Login" and requires a Java enabled
browser, which I don't use.

I have used the first one, but only on extreme emergency situations, in which, for whatever reason, I can't access the server thru a regular SSH connection.
I guess you might be able to limit which programs they can use, one thing is true, any system command that needs auth, they won't be able to do so, using the Webmin's plain vanilla "Command Shell".

If you chose this route, for the love of Jeebus, no matter what you do, make sure you are protecting your Webmin with SSL.

---

### Post by benj1 on 2009-04-08
> **oneadvent said:**
> YES exactly. I am so happy you pointed me to one.

Do you know the process behind it?


not sure, its built on googles api, i know that much, i seem to remember reading somewhere it was ajax and php but don't quote me.

---

### Post by oneadvent on 2009-04-08
Yes, looking at the source code for that website is giving me a whole bunch of ideas.

They want to pull from google, and I dont so there is a lot of cutting to make it what I want.

I am btw, working on my own website, "jonakcomputers.com"

Its not for public useage but i want it to look cool when i log in.

---

### Post by koenn on 2009-04-08
I tried something like that once. Basically the "prompt" was a form with an input bux, and [Enter] was mapped to "submit" through client-side javascript. Then a bit of CSS to make it look terminal-like (say : all backgrounds black, no borders or all borders black, all the rest green ) 

On the server side, you take wathever 'command' is submitted as a parameter to a serverside script, and handle it from there. That does mean you need server-side script (php, ...) to generate output for every command you want to implement. Could be quite a bit of work, and I didn't go that far, just "help" to show available commands, and 2-3 commands to see if it was possible.

---

### Post by oneadvent on 2009-04-08
It sounds like you were doing exactly the same thing as me. 

I am already making progress, I will just need to interpret things on the go rather than post, and i'll be doing much better.

Thanks for the great tips guys!

---

### Post by aktiwers on 2009-04-08
Another link
[http://www.commandlinefu.com/commands/browse](http://www.commandlinefu.com/commands/browse)

Love these style of websites :)

EDIT: Sorry not completely what you where talking about. Goosh is great too

---

### Post by R.Bucky on 2009-04-08
OneAdvent - funny site. I like your login/password errors!!

---

### Post by pa55 on 2012-02-14
> **volkswagner said:**
> Do you have a link?

[http://gorecki.de/](http://gorecki.de/)

---

### Post by Habitual on 2012-02-14
[http://kendalltristan.com/](http://kendalltristan.com/) fits the subject but I'm not sure it's goosh, but it is a VERY Cool page design.[]("http://kendalltristan.com/")

---

