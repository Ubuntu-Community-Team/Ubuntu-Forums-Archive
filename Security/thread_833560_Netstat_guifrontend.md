---
title: "Netstat gui/frontend"
date: 2008-06-18
forum: Security
---

### Post by tigerstripedcat on 2008-06-18
So windows has this cool program called xnetstat which bascially shows everything that's connected and the bytes in and out.   Netstat for linux does this minus the bytes in and out. Does anyone know of a gui/frontend that would make viewing my connections easier that's:

not firestarter (pain, old, a mess)
not watchdog (doesn't monitor connections)
not gnome-nettool (doesn't do what I wan't)
not knetstat (what a deceiving name that is)

?

Thanks!
TSC

---

### Post by Dr Small on 2008-06-18
Anything against wireshark, or is that not what you are looking for?

---

### Post by The Cog on 2008-06-19
ntop does that and more but it's a bit of an overkill for your requirements probabaly (its a server with a web gui).

iftop probably fits what you want to do, but it's text based, not a full GUI. I like it though.

---

### Post by tigerstripedcat on 2008-06-21
These might do the job but I'll have to play around with them.

Wireshark- seems more like a packet analyzer than a network analyzer, and a bit too complicated.  I just want to know who's connecting and what takes away my speed.

iftop -  I think this can work.  It seems to jump around a lot and is not sorted by ip source or ip dest, but it's probably in the options.

Thanks guys!
TSC

---

### Post by bobyy on 2008-06-21
Iptraf do the trick... :)

---

### Post by L_V on 2008-07-22
Iptraf is not a GUI front-end but a TUI (Terminal Front End).

I also wonder why there are so many netstat GUI interfaces for windows and none for  linux, especially KDE.

---

### Post by hyper_ch on 2008-07-22
because linux people know how to use the command line and aren't just button-pushing monkeys ;) (ok, that was mean expressed)

---

### Post by L_V on 2008-07-22
> **hyper_ch said:**
> because linux people know how to use the command line and aren't just button-pushing monkeysMay I say this is a really poor answer, especially in 2008  ?
Ok. Thanks in advance !

---

### Post by hyper_ch on 2008-07-22
why is it poor and what does the year have to do with it?

---

### Post by L_V on 2008-07-22
> **hyper_ch said:**
> why is it poor and what does the year have to do with it?
When you say "*because linux people blabla*", don't forget you just represent yourself, and only yourself.
Talking about "linux users" is as crazy as talking about "windows users".
Why it is poor in 2008 ?
Because what you call "linux users" in 2008, is much more than people using lynx as main browser and scared of using applications based on Xorg.

In summary, linux is not limited to server applications anymore.

Now, why people are looking for a netsat GUI ?
Because it is simply far more convenient to use, especially for those being using in the past to zone-alarm firewall, or any good netstat GUI tool.

Open your eyes !

---

### Post by hyper_ch on 2008-07-22
> **L_V said:**
> In summary, linux is not limited to server applications anymore.

Now, why people are looking for a netsat GUI ?
Because it is simply far more convenient to use, especially for those being using in the past to zone-alarm firewall, or any good netstat GUI tool.

Open your eyes !

Don't forget the newly introduces POWER SHELL on Windows ;) Open your eyes also ;)

---

### Post by L_V on 2008-07-22
> **hyper_ch said:**
> Don't forget the newly introduces POWER SHELL on WindowsI don't forget, but just don't care especially on a **ubuntu** forum, and especially because looking for a GUI tool and not a CLI tool.

Don't you miss the subject ? Back to it now, if you don't mind.

The best GUI netstat tool I've found is [_KConnections_](http://www.kde-apps.org/content/show.php/KConnections?content=71204) , but could be improved by adding the URL names of visited sites.

Open to other netstat GUI solutions.

---

### Post by hyper_ch on 2008-07-22
> **L_V said:**
> Don't you miss the subject ? Back to it now, if you don't mind.

Not really... but you started it with year 2008 and so on ;)

---

### Post by L_V on 2008-07-22
Then if you have new GUI netstat tool for **ubuntu** and not windows, and better than **Kconnections**, please don't hesitate to inform.

---

### Post by hyper_ch on 2008-07-22
I did already ;)

---

### Post by L_V on 2008-07-22
> **hyper_ch said:**
> I did already ;)Ok. How to you install "POWER SHELL of Windows" on ubuntu. I really don't catch your GUI proposal because I thought "POWER SHELL of windows" was a CLI tool and not a GUI tool.
Can you make a snapshot to clarify ?

---

### Post by hyper_ch on 2008-07-22
> **L_V said:**
> Ok. How to you install "POWER SHELL of Windows" on ubuntu. I really don't catch your GUI proposal because I thought "POWER SHELL of windows" was a CLI tool and not a GUI tool.
Can you make a snapshot to clarify ?

Have a read through this:
> **L_V said:**
> Iptraf is not a GUI front-end but a TUI (Terminal Front End).
I also wonder why there are so many netstat GUI interfaces for windows and none for  linux, especially KDE.
and this:
> **hyper_ch said:**
> because linux people know how to use the command line and aren't just button-pushing monkeys ;) (ok, that was mean expressed)

Got it?

---

### Post by L_V on 2008-07-22
> **hyper_ch said:**
> Got it? I just got that you just completely miss the subject :

Netstat **gui**/frontend, GUI for **Graphical User Interface**.

You cannot talk at all for the "Linux users", but just for you, and only you, like nobody is representing "windows users". That's a complet nonsense.
I thought you already understood before.

Thank you anyway.
Still open for better GUI netstat proposals.

---

### Post by hyper_ch on 2008-07-22
> **L_V said:**
> I just got that you just completely miss the subject
I don't miss it ;) I just am not as narrow-minded and think only in gui terms ;)

> **L_V said:**
> You cannot talk at all for the "Linux users", but just for you, and only you, like nobody is representing "windows users". That's a complet nonsense.
Where did I say I speak for them all? I thought you already understood before ;)

---

### Post by L_V on 2008-07-22
> **hyper_ch said:**
> I just am not as narrow-minded Sorry to say you are just narrow minded to think that you are the guy like God to decide what is good or bad for people on earth, and decide what people should like or dislike.

Please use what you like, and if possible, stop trying to block the discussion, especially because you are not concerned by the subject.

---

### Post by hyper_ch on 2008-07-22
> **L_V said:**
> Sorry to say you are just narrow minded to think that you are the guy like God to decide what is good or bad for people on earth, and decide what people should like or dislike.

Please use what you like, and if possible, stop trying to block the discussion, especially because you are not concerned by the subject.

Well, if you are not open for new suggestions then it is not me who is narrow minded ;)

---

### Post by L_V on 2008-07-22
@hyper_ch

To be very clear.
You are a real boring narrow minded guy, and even much more.
Please, you lonely man, never talk on behalf of "linux users" or "windows users".
I stop this useless discussion with **you**.

---

### Post by hyper_ch on 2008-07-22
> **L_V said:**
> You are a real boring narrow minded guy, and even much more.
I'm open for new things but seems to me you aren't ;)

---

### Post by Dr Small on 2008-07-22
> **L_V said:**
> @hyper_ch

To be very clear.
You are a real boring narrow minded guy, and even much more.
Please, you lonely man, never talk on behalf of "linux users" or "windows users".
I stop this useless discussion with **you**.
PLEASE, no debating and arguing.
hyper_ch is more knowledgable in many subjects than I am, and I regard his comments with high esteem. I am honored that he talks on behalf of the linux users.

Please drop this fighting, as this is not the place to do so.

Regards,
Dr Small

---

### Post by Oldsoldier2003 on 2008-07-23
> **Dr Small said:**
> PLEASE, no debating and arguing.

Please drop this fighting, as this is not the place to do so.

Regards,
Dr Small

+1

/me nudges the conversation back toward the intended topic and gently reminds everyone that the forum is supposed to be a friendly helpful place.

---

### Post by xenon2000 on 2008-07-25
L_V, I agree with you. This thread should be about GUI Netstat alternatives for LINUX like you originally asked for by starting this thread. And that people suggesting non-GUI and non-Linux solutions are completely wasting everyone's time. I ran into your thread here on my search and I ended up wasting my time because of Hyper_ch writing a lot of stuff that is useless to this thread. I am only posting to support you and to let you know that I applaude you for holding your ground to try and bring the comments BACK to the thread topic. 

Though sadly I don't have any suggestions myself, as that is why I was reading this thread in the first place. I wish mods could clean up threads like this. Basically pages 2 & 3 are useless, and even a good part of page 1. Actually, your first post gave more alternatives and the ONLY real alternatives to your own question. How sad is that.

I have used Linux and Windows forever it seems now. Well down to DOS 3 and the original Slackware and Redhat. And with such powerful machines, I welcome Linux GUIs! I didn't buy fast machines so I could type all my commands. LOL.

Oh yeah, Hyper_ch might be smart, funny, and an all around great guy (made all that up, I don't know him); but I completely agree that he missed the point about your question specific to asking for GUI Linux Netstat alternatives. Anyone reading from post #1 can see that. Talking about Windows, non-GUI app, or how the "general Linux" user is CMD savvy, is pointless.

---

### Post by ice60 on 2008-07-26
you can run some windows standalone programs with wine, like CurrPorts. it runs and seems to work.
[http://www.nirsoft.net/utils/cports.html](http://www.nirsoft.net/utils/cports.html)

and hyper_ch was correct when he said "because linux people know how to use the command line and aren't just button-pushing monkeys" it might sound rude, but if there's another reason what is it?

i've got a few netstat aliases that update every 2 seconds, the output is no different to a gui frontend

---

### Post by schmendrick on 2008-07-31
cool idea ice60! thank you, i didnt think of that but using CPorts with Wine on ubuntu works like charm! 

unfortunately i cannot pass the chance to also say something to the discussion....


please note:

the question of L_V is: 
*Is there a GUI ? *

it is not: 
*can i do the same in linux that i can do in windows with 'xnetstat'?* 

actually he does not care about solutions for the commandline. if he would, the question would have been different. 

and its not only L_V, but everybody searching the net/ the forum that finds this thread will have the same question like him. They all do not care about commandline utilities at this point. they/him/me are searching for a GUI way to do it.

it would be too much (and much too much emotional) to now go into the discussion if GUIs are a good thing, or if the world would be a better place without any GUIs and only having commandline  :) 

so i wont pick up any of the comments of hyper_ch and L_V though it is tempting ...


its always fascinating to watch how fast such a topic can get emotional between ... i will call them linux-purists favoring commandline and ... the rest of the world :)

don't get me wrong, its the same for me i also get emotional.

but i just couldnt help to write that i understand L_Vs resentment to the answer.

to conclude this with something positive now:
the thread helped, and thats the main point!

---

### Post by Pentatox on 2008-08-01
Oh Man Sounds Like You Should Rather Use Windows (Vista):lolflag:

---

### Post by Pentatox on 2008-08-01
> **L_V said:**
> When you say "*because linux people blabla*", don't forget you just represent yourself, and only yourself.
Talking about "linux users" is as crazy as talking about "windows users".
Why it is poor in 2008 ?
Because what you call "linux users" in 2008, is much more than people using lynx as main browser and scared of using applications based on Xorg.

In summary, linux is not limited to server applications anymore.

Now, why people are looking for a netsat GUI ?
Because it is simply far more convenient to use, especially for those being using in the past to zone-alarm firewall, or any good netstat GUI tool.

Open your eyes !

The Last Post Was In Reply To This

---

### Post by Oldsoldier2003 on 2008-08-01
Since there is nothing new being brought to this thread I'll close it. If you folks want to discuss cli vs gui, I'm sure you can find plenty of threads in recurring posts.

---

