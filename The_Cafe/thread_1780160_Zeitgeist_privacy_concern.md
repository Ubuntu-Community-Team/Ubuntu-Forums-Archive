---
title: "Zeitgeist privacy concern"
date: 2011-06-11
forum: The Cafe
---

### Post by Nonno Bassotto on 2011-06-11
I recently installed Natty. While browsing System Monitor, I noticed that the processes
```

zeitgeist-daemon
zeitgeist-datah
zeitgeist-datahub

```
are running in the background.

Now, if I understand correctly, the purpose of the Zeitgeist daemon is to collect as much information as possible about everything I do with my computer, in order to be able, say, to connect received emails to related files, contacts to activities and whatnot. All this information should be presented through various clients, which will allow "intelligent" retrieval of data on my computer (e.g. the mail I received in March with design guidelines for that site).

Of course I am a little concerned by a daemon collecting all this information in an automated way, even if it is going to remain on my computer. More so considering that I never really started the daemon, but it was automatically added.

Is there a way to
- figure out what data Zeitgeist has collected so far
- instruct Zeitgeist about what data should be collected and what data should be ignored
- at worst, preventing Zeitgeist from running without breaking other parts of the Ubuntu desktop which may be dependent on it, and without it reappearing a few months later without notice due to some updates?

---

### Post by Jesus_Valdez on 2011-06-11
Activities Journal?

Or

Install Activity Log Manager for Zeitgeist and on the "Files" tab blacklist the folders where you keep your private files (porn). You can also completely disable Zeitgeist by clicking the "Logging active" button at the bottom but no files will show up in Dash after doing this so its better to only backlist certain folders (or applications). You can also use this to clear the Zeitgeist history (and thus the Dash history).

[http://www.webupd8.org/2011/05/keep-files-from-showing-up-in-unity.html](http://www.webupd8.org/2011/05/keep-files-from-showing-up-in-unity.html)

---

### Post by Nonno Bassotto on 2011-06-11
Thank you for your advice. It's not really a matter of porn. It is creepy to have all I do recorded in this way. It is sad to see that desktops are going down this way.

---

### Post by Thewhistlingwind on 2011-06-11
To call the zeitgeist project, well zeitgeist, is so ironic and so wrong on SO many levels.

---

### Post by dmizer on 2011-06-11
I suggest you start here -> [http://zeitgeist-project.com/](http://zeitgeist-project.com/)
and here -> [https://launchpad.net/zeitgeist-project](https://launchpad.net/zeitgeist-project)

---

### Post by 3rdalbum on 2011-06-11
At the moment, Zeitgeist keeps a list of recent documents and recent programs.

Gnome has always done the same.

Zeitgeist will eventually store more meaningful data ("user played this MP3", as opposed to "user opened this file") but it does not log what gets typed into files, for instance.

What does it matter if some information about what files you've opened sits on your computer? Your computer already logs a lot more than that - it logs when files were created and when they were last modified, it logs what times you've logged in and for how long, it logs when you connected to wifi and when a program has crashed. And it does all that without Zeitgeist.

---

### Post by Legendary_Bibo on 2011-06-11
> **3rdalbum said:**
> At the moment, Zeitgeist keeps a list of recent documents and recent programs.

Gnome has always done the same.

Zeitgeist will eventually store more meaningful data ("user played this MP3", as opposed to "user opened this file") but it does not log what gets typed into files, for instance.

What does it matter if some information about what files you've opened sits on your computer? Your computer already logs a lot more than that - it logs when files were created and when they were last modified, it logs what times you've logged in and for how long, it logs when you connected to wifi and when a program has crashed. And it does all that without Zeitgeist.

I think he thinks that it's sending the data to an online server, or something.

---

### Post by Quadunit404 on 2011-06-11
If a database on your hard drive means some shady site, then I don't know what does anymore.

---

### Post by Paqman on 2011-06-12
> **3rdalbum said:**
> 
What does it matter if some information about what files you've opened sits on your computer? Your computer already logs a lot more than that - it logs when files were created and when they were last modified, it logs what times you've logged in and for how long, it logs when you connected to wifi and when a program has crashed. And it does all that without Zeitgeist.

Exactly. Logging the behaviour of the user and it's own processes is bread and butter stuff for an OS. If you don't like that, you're welcome to throw your computer into the gears of a loom.

---

### Post by Nonno Bassotto on 2011-06-12
> **Legendary_Bibo said:**
> I think he thinks that it's sending the data to an online server, or something.

I am not worried about Zeitgeist sending my data online, I am worried about Zeitgeist saving this data on my computer. I am well aware that every OS saves timestamps and some other information, and that Gnome had a plain linst of recently opened files.

Still the kind of logging performed by Zeitgeist is on another level entirely. First, it stores all information conveniently accessible in a single place, as opposed to timestamps. Second, it keeps the list forever, as opposed to Gnome recent files (yes, I know I can erase something if I want). Third, it tries to make connections in an automatic fashion which relate together everything I do with my computer. To do so, it does not only store recent files, but also which programs were used to open it, what other programs were open and so on.

Sorry, but I am not aware of any other piece of software that performs the same kind of intrusive logging before Zeitgeist.

---

### Post by timZZ on 2011-06-12
Known fact: Automatic suggestions based off a users interests is the best way of proposing new products to a user.  Even open-source needs a way to get heard amongst the crowd.

---

### Post by Quadunit404 on 2011-06-12
I remember that there was a proposal to have Zeitgeist encrypt the database file (activity.sqlite) but I am not aware of the status on that proposal.

---

### Post by Paqman on 2011-06-12
> **Nonno Bassotto said:**
> I am not worried about Zeitgeist sending my data online, I am worried about Zeitgeist saving this data on my computer.

Fair enough. You're probably not the only one whose raised this concern, which is why they built the Activity Log Manager. Zeitgeist doesn't have to log anything you don't want it to.

---

### Post by sg1efc on 2011-07-08
> **Nonno Bassotto said:**
> Thank you for your advice. It's not really a matter of porn. It is creepy to have all I do recorded in this way. It is sad to see that desktops are going down this way.

I agree with you. I left Windows for many reasons, one of which is the crazy amount of unnecessary running processes that everyone wanted to have running on My computer. Each process takes up ram memory and for those of us who do not have many Gigs of Ram, we need what little we have for the processes we really want and need to run. It is like all that Evolution integration. I use Thunderbird for my email and Pidgin for my instant messaging so having Evolution running all the time is a waste to me of my ram.

From the  [http://zeitgeist-project.com/](http://zeitgeist-project.com/)  website:

"The Element of Intelligence             A new approach adapting the user experience to ones own needs, by:
              **Logging**

                          the user's activities and notifications with and from his data.             
             **Associating**

                          the data with each other by learning from the user's history.             
             **Providing Intelligence**

                          for other applications and services to enhance the user experience."

"What is Zeitgeist? Zeitgeist is a service which logs the users’ activities and events,  anywhere from files opened to websites visited and conversations had."

------------------------------------------------

"anywhere from files opened to websites visited and conversations had."

Umm, isn't this very redundant? I mean, my browser already can log info, so does Pidgin and so on..., Does this not mean that Zeitgeist is completely redundant and a waste to me? :confused:

From what that tells me, these Zeitgeist processes will not really help me at all. My question is, does anyone know if it is ok to permanently disable these processes and if so, how would I do this? Thanks very much in advance for any and all info and opinions.  :)

---

### Post by cariboo on 2011-07-09
You could probably remove zeitgeist if you don't want it to do what it does. BTW the way Linux manages memory is different from the way XP manages it. Linux will always uses as much memory as it can, releasing it when it's needed by another process. Unless you are running into swap fairly often, I wouldn't worry about ram usage.

---

### Post by sg1efc on 2011-07-09
> **cariboo907 said:**
> You could probably remove zeitgeist if you don't want it to do what it does. BTW the way Linux manages memory is different from the way XP manages it. Linux will always uses as much memory as it can, releasing it when it's needed by another process. Unless you are running into swap fairly often, I wouldn't worry about ram usage.

Thank you very much for your reply Cariboo907. :)  This is one of the many things I love about Ubuntu/Linux in general = lots of nice people willing to answer questions.

Btw, if anyone thinks that my theory of Zeitgeist being redundant is not accurate, please feel free to        post here so I/we can learn more about this. :grin:

---

### Post by sg1efc on 2011-07-09
Ok, also found this at the Zeitgeist site:

"Experience Zeitgeist
**Using Zeitgeist**

 Unity makes use of Zeitgeist in its dash where it provides the user  with easy access to its most and recently used data  (files/folders/applications) as well as searching over the Zeitgeist FTS  (Full Text Search) extension."
--------------------------------------------------------------


Well I didn't like anything about Unity at all, so had switched back to the standard Gnome interface anyway. One of the Zeitgeist processes was a zombie just now(perhaps maybe from my not using Unity?), so just uninstalled all Zeitgeist processes in synaptic.  More free memory and less unneeded processes, yay. :D


Thanks again Cariboo907 and everyone else here.  ;)

---

### Post by Mr. Picklesworth on 2011-07-09
> **3rdalbum said:**
> What does it matter if some information about what files you've opened sits on your computer? Your computer already logs a lot more than that - it logs when files were created and when they were last modified, it logs what times you've logged in and for how long, it logs when you connected to wifi and when a program has crashed. And it does all that without Zeitgeist.

It also stores those files and it knows their full contents ;)

That said, it would be nice to have a system settings panel for Zeitgeist, much like we have one for any of the brute-force search indexers. Zeitgeist is a nice approach, but does take up a noteworthy chunk of resources. Not really much at runtime, but on the hard drive it can add up. An Off switch, at least, could be a nice addition.

> **sg1efc said:**
> I agree with you. I left Windows for many reasons, one of which is the crazy amount of unnecessary running processes that everyone wanted to have running on My computer. Each process takes up ram memory and for those of us who do not have many Gigs of Ram, we need what little we have for the processes we really want and need to run. It is like all that Evolution integration. I use Thunderbird for my email and Pidgin for my instant messaging so having Evolution running all the time is a waste to me of my ram.

I think you'll find that Linux *loves* small daemon processes, and it has a lot more of these than Windows does. (Just look at System Monitor and tell it to show all processes!). Because of its design, lots of stuff ends up in userspace instead of the kernel. (Eg: Xorg). There is nothing wrong with this - the kernel knows what it's doing - unless they happen to spike into the >10% CPU and RAM usage territory. In short, it's either a bunch of little processes or one really big process that breaks everything when it crashes.

---

### Post by Aquix on 2011-07-09
I don't know if zeitgeist is a security concern since it does exactly what it promises and one needs to opt in by installing it.

---

### Post by sg1efc on 2011-07-09
> **Mr. Picklesworth said:**
> It also stores those files and it knows their full contents ;)

That said, it would be nice to have a system settings panel for Zeitgeist, much like we have one for any of the brute-force search indexers. Zeitgeist is a nice approach, but does take up a noteworthy chunk of resources. Not really much at runtime, but on the hard drive it can add up. An Off switch, at least, could be a nice addition.


I think you'll find that Linux *loves* small daemon processes, and it has a lot more of these than Windows does. (Just look at System Monitor and tell it to show all processes!). Because of its design, lots of stuff ends up in userspace instead of the kernel. (Eg: Xorg). There is nothing wrong with this - the kernel knows what it's doing - unless they happen to spike into the >10% CPU and RAM usage territory. In short, it's either a bunch of little processes or one really big process that breaks everything when it crashes.

Yes an off switch is a cool idea.  Yep, I am not too concerned about many running processes in Ubuntu, because I know that Ubuntu is very different than Windows processes = I trust Ubuntu/Linux processes much more. However processes that do not really help me are the ones I can live without running on my pc. 

Currently I have 10 processes using  over 10Meg or more each, FireFox is using the most at 870.4Meg but I have around 50 tabs open in it, LoL. :p  There are lots of those small daemon processes running as you mention, but they seem to be behaving themselves quite nicely, compared to the evil Windows processes I usually see on other's computers, like the one that had 77 running processes in Windows Vista I was trying to repair a couple hours ago due to a BSOD, LoL.  ](*,):lolflag:

> **Aquix said:**
> I don't know if zeitgeist is a security concern  since it does exactly what it promises and one needs to opt in by  installing it.

Not sure, but I think my zeitgeist was installed automatically when I upgraded to Ubuntu 11.04, can not remember if I was given the choice to install it, or to refuse installation though. :confused:

Thanks again everyone for your thoughts. :D

---

### Post by cgroza on 2011-07-09
Well, you could always take a peek into the source code to see what it is doing with your data.
This is open source remember?

---

### Post by cariboo on 2011-07-09
> **cgroza said:**
> Well, you could always take a peek into the source code to see what it is doing with your data.
This is open source remember?

That's way to easy, it's better to post a complaint about something, before doing any research. :) :) :)

---

### Post by sg1efc on 2011-07-09
> **cgroza said:**
> Well, you could always take a peek into the source code to see what it is doing with your data.
This is open source remember?

That won't help people like myself who are coding illiterate.   :frown:  I understand how to read code as well as I know how to read Ancient or Gho'uld languages from StarGate.  LoL  :biggrin:

---

### Post by rockney on 2011-08-28
"What does it matter if some information about what files you've opened sits on your computer?"

Easy - because 1) I didn't ask for it,  2) it takes system resources I did not allocate,  3) it keeps information that serves no practical purpose that I care about,  4) I don't know what is done with that data, i.e. is it being sent off my computer? (And don't say "trust us").

It is no ones business what files I have on my computer or what I do with them.

So it's either someone's bad idea of turning my work desktop into some mobile touch i-toy with all kinds of wasteful flash and dance that I DO NOT care a thing about ... and/or someone is collecting the data and "profiling" computer users.  THAT is completely unacceptable and cannot be tolerated.

btw - I read in another post that "user's don't want to have to be bothered with whether a file is on their computer or in the cloud" --- sorry, that is utter stupidity talking. Unity and this whole virtual "the Internet is everything" mobile attitude is totally wrong for any real desktop user making a living on a computer.  

It's just wrong to shove this very poor paradigm down everyone's throat and tell them "get used to it".

I'm reformatting my HD and choosing a different distro ... it seems Ubuntu is populated with people who text instead of talking to each other and believe their own marketing rhetoric.

---

### Post by smellyman on 2011-08-28
Agreed.

I really hate the /var/log directory too.

It logs everything!  stupid computer.

don't get me started on caches and history....

---

### Post by ninjaaron on 2011-08-28
> **sg1efc said:**
> That won't help people like myself who are coding illiterate.   :frown:  I understand how to read code as well as I know how to read Ancient or Gho'uld languages from StarGate.  LoL  :biggrin:

I actually do read six ancient languages, and I can't make heads or tails of C.:P

Also, this:
[IMG]http://www.cartoonstock.com/newscartoons/cartoonists/rma/lowres/rman198l.jpg[/IMG]

---

### Post by sg1efc on 2011-08-29
> **ninjaaron said:**
> I actually do read six ancient languages, and I can't make heads or tails of C.:P


Lots of laughs!  :)

---

### Post by Larkspur on 2011-08-30
> **rockney said:**
> "What does it matter if some information about what files you've opened sits on your computer?"

Easy - because 1) I didn't ask for it,  2) it takes system resources I did not allocate,  3) it keeps information that serves no practical purpose that I care about,  4) I don't know what is done with that data, i.e. is it being sent off my computer? (And don't say "trust us").

It is no ones business what files I have on my computer or what I do with them.

So it's either someone's bad idea of turning my work desktop into some mobile touch i-toy with all kinds of wasteful flash and dance that I DO NOT care a thing about ... and/or someone is collecting the data and "profiling" computer users.  THAT is completely unacceptable and cannot be tolerated.

btw - I read in another post that "user's don't want to have to be bothered with whether a file is on their computer or in the cloud" --- sorry, that is utter stupidity talking. Unity and this whole virtual "the Internet is everything" mobile attitude is totally wrong for any real desktop user making a living on a computer.  

It's just wrong to shove this very poor paradigm down everyone's throat and tell them "get used to it".

I'm reformatting my HD and choosing a different distro ... it seems Ubuntu is populated with people who text instead of talking to each other and believe their own marketing rhetoric.

It's probably too late, but you could've just uninstalled zeitgeist (unless it breaks something?  I don't know).  Whatever distro you use, however, make sure its not Gnome-based; if you think Zeitgeist is an invasion of privacy, wait until you read up on Geoclue.  And gedit: I opened that the other day, and it logged almost all of my keystrokes!

---

### Post by sg1efc on 2011-08-30
> **Larkspur said:**
> It's probably too late, but you could've just uninstalled zeitgeist (unless it breaks something?  I don't know).  Whatever distro you use, however, make sure its not Gnome-based; if you think Zeitgeist is an invasion of privacy, wait until you read up on Geoclue.  And gedit: I opened that the other day, and it logged almost all of my keystrokes!

I uninstalled Zeit when I read this thread. Have not noticed any side effects at all, however I don't use Evolution-stuff in my Ubuntu (if Evolution somehow uses Zeit?).  Prefer to use Pidgin, Ekiga and Skype for friends that don't use Ekiga.  :P

Geoclue... just researched what that is and not particularly fond of some of the potential uses Geoclue usage might have.  Is it safe to remove Geoclue from Ubuntu 11.04?  :confused:  I do not have or connect a cell phone, etc., to my PC.

Thanks for all the info everyone.  :)

---

### Post by cariboo on 2011-08-30
Instead of asking, why don't you remove geoclue and see. If something breaks, you can always re-install it.

---

### Post by sg1efc on 2011-09-01
> **cariboo907 said:**
> Instead of asking, why don't you remove geoclue and see. If something breaks, you can always re-install it.

Might removing something possibly seriously break other things, if for example GeoClue were somehow integrated with other programs?  :confused:

This is why I asked first instead of taking a risk.  :)

---

