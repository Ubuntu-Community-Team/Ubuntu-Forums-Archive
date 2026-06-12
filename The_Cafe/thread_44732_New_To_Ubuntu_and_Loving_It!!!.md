---
title: "New To Ubuntu and Loving It!!!"
date: 2005-06-27
forum: The Cafe
---

### Post by gdboling on 2005-06-27
I just wanted to thank the Ubuntu team.  I just installed the newest release and all I can say is wow!  Specifically I have been trying several other distros trying to get something to work on my Dell XPS system.  I always have a problem getting my ATI Mobile 9800 to work correctly, if at all.  

I installed Ubuntu and it just worked.  IT JUST WORKED!!  That is awesome.  Thanks to everyone for a great distro.  I'll never look back.  Now, to figure out how to update all my software with apt-get..... ;)

Gregg Bolinger
[Weblog](http://greggbolinger.blogspot.com)

---

### Post by Leif on 2005-06-27
[http://ubuntuguide.org/](http://ubuntuguide.org/) is your friend

---

### Post by UbuWu on 2005-06-27
> **gdboling]Now, to figure out how to update all my software with apt-get.....  said:**
> Weblog[/url]

sudo apt-get update
sudo apt-get upgrade

Or use synaptic...

---

### Post by mike998 on 2005-06-27
Synaptic may be easier for you to deal with.
If you want to get the flexibility that everyone talks about in linux, then the man pages are you friend..  (man synaptic)

---

### Post by Optimal Aurora on 2005-06-27
Agreed, Hay how do you like that XPS system, just curious...

I had some problems because of my Gateway 64bit system isn't all that compatible with other OS's, so that is why I switched to 64bit version of Ubuntu...

Enjoy the community...

---

### Post by gdboling on 2005-06-27
[QUOTE=Optimal Aurora]Agreed, Hay how do you like that XPS system, just curious...

I had some problems because of my Gateway 64bit system isn't all that compatible with other OS's, so that is why I switched to 64bit version of Ubuntu...

Enjoy the community...[/QUOTE]

I love it.  It's not 64bit but works really really well.  It's my laptop and my main development box that has also become my main gaming box (still need windows for that so dual boot).

I am in the process of trying to get 3D support going.  I thought I had it since the video works and all but can't run any GL apps.  This will be fun.  Worst case I don't get GL support which won't be an end all, but I'd really like it since I do develop opengl apps in Java.

---

### Post by Optimal Aurora on 2005-06-27
Cool, that a nice system... and don't feel bad about having to dual boot, because I use windows for gaming and so I dual boot my 64bit system...

---

### Post by garnertr on 2005-06-28
[QUOTE=UbuWu]sudo apt-get update
sudo apt-get upgrade

Or use synaptic...[/QUOTE]


Is there a way to make this "one command", I'm a newbie to Linux, so, I might be using the wrong word/phrase, but I'm lazy, is there a way to type in both sudo apt-get update and sudo apt-get upgrade as one command like say "upgrade", make it a script???  is that the right word?

Coming from windoze, if I wanted to do that I'd make a batch file that had the two commands listed (one after the other)... is that what a script file is??

thanks sorry for being silly in my ????'s...

---

### Post by Leif on 2005-06-28
Open up your ~/.bashrc and put this at the end : alias upgrade="sudo apt-get update && sudo apt-get upgrade"

---

