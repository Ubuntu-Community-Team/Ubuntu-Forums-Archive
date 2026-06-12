---
title: "internet radio?"
date: 2009-05-08
forum: Ubuntu Studio
---

### Post by higashi on 2009-05-08
I just recently decided to make an internet radio station (no idea why... just randomly decided to) and i need to know more about it before i start...

Basically, i just need to know how the hell to do this. I've looked around the internet and read about SHOUTcast but i'm still not 100% sure what exactly it is or how to use it.

Is SHOUTcast the best thing for me to use? This is what i want to be able to do:

allow people to listen to my music, be able to talk on my station using my mic if i feel like it, be able to set a playlist to play random songs from for when i'm not at my computer...  i think thats all for now.

Can someone provide me with a tutorial that a complete noob can understand, or just tell me what i need to know urself?
TIA

EDIT: [This program]("http://www.onlymeok.nildram.co.uk/") looks pretty cool. is it up-to-date enough? Would you recommend i use it?

---

### Post by pastalavista on 2009-05-08
I don't know much about it but my son uses icecast2 (it's in the repositories). He uses Crunchbang-linux which is an Ubuntu-based system so it shouldn't be too hard. He isn't all that smart.. haha.

---

### Post by higashi on 2009-05-08
lol

icecast looks pretty cool, i think thats what i want to use. I'm not having much luck installing though. 

I went System>administration>synaptic package manager  and added it, (also added ices2 since it was required)  and everything seemed to go fine, but once i closed synaptic and looked under applications, it just wasnt there. :(

When i run icecast2 in a terminal, i get this:
> me@my desktop:~$ icecast2
Icecast 2.3.2

usage: icecast [-b -v] -c <file>
options:
	-c <file>	Specify configuration file
	-v		Display version info
	-b		Run icecast in the background



how can i get it to run, and get it in my main menu so that i dont have to run it in the terminal each time ?

---

### Post by pastalavista on 2009-05-08
I asked my son and he said you also need something like "idjc" or "ampache". I made him spell ampache. He said they were gui clients. He has used both but also said he doesn't mess with it any more. Sorry... you know how kids are

---

### Post by higashi on 2009-05-08
Ahah, yeah.

Now, i installed ampache and idjc. I tried running idjc but there were some errors with JACK (which im not gunna bother listing right now cuz im more interested in ampache)  and i still have no idea what icecast2 is... Oh and ampache isn't listed in my main menu either, and when i type it in a terminal, it says "command not found".
I am so lost right now @.@

---

### Post by Samhain13 on 2009-05-09
> **higashi said:**
> Oh and ampache isn't listed in my main menu either, and when i type it in a terminal, it says "command not found".
I am so lost right now @.@

I don't think you'll find this type of application in the menu. Looking at the wiki ([http://ampache.org/wiki/](http://ampache.org/wiki/)) right now because this thread got me interested. :)

Anyway, try to open this URI in your web browser: [http://localhost/ampache](http://localhost/ampache). I believe that if you don't get a 404 error (page not found), Ampache is probably running already. You can also check if there's an entry for it in System > Administration > Services, and if such entry is checked.

Good luck. I might look more into this, but I may take some time.

---

