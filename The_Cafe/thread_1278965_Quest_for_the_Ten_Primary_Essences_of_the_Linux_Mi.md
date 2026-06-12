---
title: "Quest for the Ten Primary Essences of the Linux Mindset."
date: 2009-09-30
forum: The Cafe
---

### Post by Sean Moran on 2009-09-30
Evolving is not as simple as it looks at first, for one might be familiar with the major differences between the popular antique flavours of desktop systems and tomorrow's operating systems (aka Linux), but in the heat of the moment, I have found that (personally) many of the errors that have cost me the most time over these last forty days have been due to my 'subconsciously' thinking with the established 'Windows/DOS' mindset, and as expected, trying to run Linux properly when you're using a Windows mindset is possible, but not very efficient nor neccesarily successful.

A friend told me at the start of this year some wise words about languages, "To speak Thai you must THINK in Thai, and to speak English, then THINK English." I see some parallel with her wise axiom and with the Linux-Windows adaptation conundrum.

I am fortunate to maintain the two arms I was born with, and each still retains four fingers + one thumb or five points, and together that comprises ten digits. I wrote this thread because I yearn to have a simple way of solving problems on Ubuntu (and at the Nautilus/terminal level Linux) where I can just put both my hands upon the screen and tie a remedy to each finger - that makes ten simple hints to be remembered, so I guess.

The basics of C: and D: vs / and /home are very simple, but other than those kindergarten skills, I would like to compile five basic mnemonics for both my hands which can be practiced and remembered until they might become as familiar as riding a bicycle when one's mind is meant to be focused on more productive cognitions.

What ten rules can be remembered with a digit on your hand for each one, that will help to promote the adaptation from that old operating system towards Linux?

---

### Post by openfly on 2009-09-30
10 Rules of Thumb for Linux:

[LIST]
[*]Your Shell has environment variables.
[*]Your logs are in /var/log.
[*]Permissions can be seen on files with ls -larht.
[*]lsof can tell you which files and sockets are currently being used by applications.
[*]find, grep, sed, and awk will help you find your way.
[*]cat head and tail are all part of the same file reading animal.
[*]ps auxwwff or ps aux for short will list all processes currently running.
[*]STDOUT is great, STDERR is not so great, STDIN is all you.
[*]> will dump to a file, >> will append to a file, | will pipe to a command.
[*]RTFM, man commands , and command --help or -h flags tend to be descriptive.
[/LIST]

Just came up with that off the top of my head.  Might be helpful.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-09-30
This should be included in a tips apps for Ubuntu ;]

---

### Post by red_Marvin on 2009-09-30
To find,grep,sed,awk I would also like to add *cut*, *sort* and *tr*.
Once you get confident with these tools, and some general bash syntax, you will be able to glue together tasks in wonderful ways.

---

### Post by Tristam Green on 2009-09-30
> **openfly said:**
> 10 Rules of Thumb for Linux:

[LIST]
[*]RTFM, man commands , and command --help or -h flags tend to be descriptive.
[/LIST]

Just came up with that off the top of my head.  Might be helpful.

RTFM is a very professional way of "helping" someone.

---

### Post by Bachstelze on 2009-09-30
> **Tristam Green said:**
> RTFM is a very professional way of "helping" someone.

OP wasn't asking for help, though.

---

### Post by openfly on 2009-09-30
> **Tristam Green said:**
> RTFM is a very professional way of "helping" someone.

It's somewhat new to non unix people that every command has a help file that's actually helpful available for it.  Lots of windows users are just completely used to useless help files and no logging.  So reminding them that they should always hit up the helpful documentation before seeking help is just another way of ensuring their continued success.

---

### Post by markbuntu on 2009-09-30
man and info are your friends.

---

### Post by forrestcupp on 2009-09-30
11. Don't piss off the Free Software Community; they're almost like their own mafia.  :)

---

### Post by red_Marvin on 2009-09-30
Ey, Lenny, I think I know who the snitch that's been sellin us out is, take Sonny and Mike and pay him a visit.

---

### Post by Tristam Green on 2009-09-30
> **Bachstelze said:**
> OP wasn't asking for help, though.

That's not what I was getting at.  Telling *anyone* to "RTFM" who is just switching from one OS to another OS, is just dirty pool, especially if you (hypothetical "you") had a hand in facilitating that switch.

> **openfly said:**
> It's somewhat new to non unix people that every command has a help file that's actually helpful available for it.  Lots of windows users are just completely used to useless help files and no logging.  So reminding them that they should always hit up the helpful documentation before seeking help is just another way of ensuring their continued success.

Telling the person that man pages exist isn't bad at all.  Telling them to "Read the fscking manual" is just *wrong.*

> **forrestcupp said:**
> 11. Don't piss off the Free Software Community; they're almost like their own mafia.  :)

In some cases, it's like a militia or the CoS too.

---

### Post by steveneddy on 2009-09-30
The simple rule that is normally learned over time by the best business managers and leaders is not knowing everything, but knowing where to go for information about anything.

Relating this to Ubuntu:

1. Try a search on Ubuntu Forums
2. Google, Google, Google
3. The links in **my **sig
4. If it's software other than the OS, go to the software's main website for support.
5. Try one of the many Ubuntu book on the market.
6. Did I mention Google?

---

### Post by red_Marvin on 2009-09-30
> **Tristam Green said:**
> That's not what I was getting at.  Telling *anyone* to "RTFM" who is just switching from one OS to another OS, is just dirty pool, especially if you (hypothetical "you") had a hand in facilitating that switch.
Well, being able and prepared to read documentation is a big part of the linux mindset. Perhaps the wording of the acronym is unfortunate, but [s]he is going to be familiar with it sooner or later anyway, since it is the commonly used "term", like it or not.

---

### Post by Sean Moran on 2009-09-30
Thank you all for the suggestions so far, (including the funny ones).  I went to bed not long after starting the thread, and apologise for that approach, but I've ummed and ahh'd over how to put this into words for days now, and thought that the best way to find the courage to jump in the deep end was to drink a large amount of mid-strength beer until late in the night, which was why I was obliged to pass out shortly afterwards.  It seems to have *almost* worked, from the look of the replies.  Thanks to all.

If I may commend the /var/log *** suggestion without prejudice as one of those that probably contains the sort of format I imagined - short and quick and easy to learn to associate subconsciously with perhaps the left 'ring' finger, or if right-hand  thumb = R0 and left-hand little finger = L4, then /var/log = L3 or R3 ?

In fact, I can see now that the information I began with was lacking in some dimension.  Ten points to cover the entire knowledge-base is far too few, but you've hit the nail on the head with the main filesystem locations, such as /var/log, /etc, /home, /usr etc. as one set of digits in itself.

If we could assign more than one pair of hands to various components of the 'Linux mindset', eg. 
1. filesystem layout, 2. permissions? 3. ???, could we start with the filesystem and come up with the ten most often used or important to remember directories and assign each one to a finger for easier memorisation?

Please consider this as a bit of freestyle brainstorming as I'm not really sure where it's going exactly, but I believe thate might be something worth working out at the end of it.

---o0o---

*** reading over the thread the second time, there are some really good suggestions.  There's enough here already to keep me busy all day.  Thanks again to all.

---

### Post by earthpigg on 2009-09-30
[dd is the disk destroyer.]("http://en.wikipedia.org/wiki/Dd_%28Unix%29") it is also an outstanding and powerful tool.

[dotfiles are funfiles.]("http://en.wikipedia.org/wiki/Dotfile#Unix_and_Unix-like_environments") when you completely break a program, you can usually simply delete the dotfile and it will start with the 'factory defaults'. you can also play with the dotfiles in your /home without much risk to your system.

_When in doubt, click "advanced" or "manual"._ If you can't make heads or tails of it and don't feel like learning, ***then*** go back and do the "automatic".

[UNIX/Linux/Ubuntu was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things.]("http://en.wikipedia.org/wiki/Unix_philosophy#Quotes")

you have the [Four Fundamental Software Freedoms]("http://en.wikipedia.org/wiki/Four_Freedoms_%28software%29#Definition") assigned to a finger(s) already, right?

---

### Post by Dimitriid on 2009-09-30
Im not sure there is a "mindset" Linux users share other than maybe common sense.

---

### Post by Sean Moran on 2009-09-30
> **earthpigg said:**
> [dd is the disk destroyer.]("http://en.wikipedia.org/wiki/Dd_%28Unix%29") it is also an outstanding and powerful tool.

[dotfiles are funfiles.]("http://en.wikipedia.org/wiki/Dotfile#Unix_and_Unix-like_environments") when you completely break a program, you can usually simply delete the dotfile and it will start with the 'factory defaults'. you can also play with the dotfiles in your /home without much risk to your system.

_When in doubt, click "advanced" or "manual"._ If you can't make heads or tails of it and don't feel like learning, ***then*** go back and do the "automatic".

[UNIX/Linux/Ubuntu was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things.]("http://en.wikipedia.org/wiki/Unix_philosophy#Quotes")

you have the [Four Fundamental Software Freedoms]("http://en.wikipedia.org/wiki/Four_Freedoms_%28software%29#Definition") assigned to a finger(s) already, right?

Yes!  dd IMHO qualifies for the middle finger on the left hand, L2, perhaps along with other scary things like rm ?, or would you have other ideas?  

Dotfiles is another jargon I'd long forgotten, and should that get the right-hand little finger R4, lr the left?

Also, much appreciated the explanation given on the Autodesk thread earlier. 
[IMG]http://lobby.oz.netau.net/images/smilies/02twin/icon_chongao.gif[/IMG]

> **Dimitriid said:**
> Im not sure there is a "mindset" Linux users share other than maybe common sense.

Thanks again.  Common sense is a great idea that I don't have much of but friends have sometimes told me that it might even be divided into parts, or art/science or logical/<stuff like this thread> and maybe reside on both index fingers, R1 and L1.  What digit would you suggest best fits one or more kinds of common sense?
[IMG]http://lobby.oz.netau.net/images/smilies/02twin/icon_chongao.gif[/IMG]

---o0o---

I should mention something regarding the interpretation of hexadecimal by the pentadactyl appendage.
Maybe when I think like a 'geek' it's one thumb and fifteen fingers,  but as an human being, we would seem to prefer decimal and it's much easier to count in for biological organisms.  (ed. primates anyway. 9-) 
Just a thought.

---

### Post by undecim on 2009-10-01
To ask me to put years of experience into only ten lines? I say that your request is unreasonable, but I will do my best to fulfill it. Below are what I believe to be the 10 most important parts of **MY** Linux mindset:

[LIST=1]
[*] An hour of learning prevents a lifetime of inefficiencies and mistakes.
[*]Complexity is the enemy of reliability.
[*]The most powerful tools are the most dangerous
[*]Computers are made for humans, not computers. One of the primary advantages to being human is that you are able to learn from your mistakes.
[*]HOW and WHY are the two most important pieces of knowledge when troubleshooting. Find these, and all else will follow.
[*]Any program worth installing should be documented. First try the "man" and "info" commands, then try Google.
[*]Inconveniences are unacceptable. If you find an inconvenience, fix it. If you are in a hurry when you find it, make a note of it, so that it you can have it fixed before your next rush.
[*]If you don't know your computer, who does?
[*]Getting what you want depends on two factors: ability and desire. Use of either one both compensates for and begets the other.
[*]Ignorance is bliss, but freedom is satisfaction.
[/LIST]
The above is the best I could do to put my thoughts into words. Though some things were lost in translation, much like translating Thai to English, I hope these words can help point your thoughts in the right direction, and help you find your mindset.

---

### Post by Sean Moran on 2009-10-01
Thank you Undecim.  I can see already that my entire weekend is now allocated to sorting through all this excellent wisdom, and it's not even tieng wan in Krungthep yet! (not even noon in Bangkok).   This is phenomenal!
[IMG]http://lobby.oz.netau.net/images/smilies/02twin/icon_chongao.gif[/IMG]

PS: I agree that it is a totally unreasonable request.  That is the point of it, in some ways, so thanks for persevering.

---

### Post by Frak on 2009-10-01
> **forrestcupp said:**
> 11. Don't piss off the Free Software Community; they're almost like their own mafia.  :)
With squirt guns.

---

### Post by Sean Moran on 2009-10-01
> **Frak said:**
> With squirt guns.

NOW we're onto something!!! You've pointed out exactly where this is leading but I'm not sure if it warrants another thread, or work along with this one, but surely it is possible to teach a monkey to fire a water pistol?

So therefore, what is to stop someone wiring up a solar/wind powerered robust Ubuntu system with screen, keyboard and mouselike object on a platform up a tree in the jungles of the Congo (both sides if yer that way inclined) so that we can train a few chimpanzees to teach the local populace to communicate inter-special with us like Project Ubuntu Doolittle? Why would that not be feasible if we can work out how to associate those ten USER function keys with the right operations and prove that Ubuntu is so easy to use that even monkeys in the jungles of the heart of darkness can twitter on it?

There maybe two different subjects in this so please don't let me take my own thread too off-topic.

---o0o---

I should mention that I used the term 'monkey' colloquially up there.  Chimpanzees are not monkeys, but apes.

---

### Post by openfly on 2009-10-01
RTFM can also mean read the fine manual... if you are viewing the world through disney goggles.

KISS method, keep it simple stupid.  always important to remember in any task.

Lunix mo like lolnix.

---

### Post by forrestcupp on 2009-10-01
> **red_Marvin said:**
> Well, being able and prepared to read documentation is a big part of the linux mindset. Perhaps the wording of the acronym is unfortunate, but [s]he is going to be familiar with it sooner or later anyway, since it is the commonly used "term", like it or not.

Well, the correct wording makes all the difference.  If you sound cocky and make someone feel inferior, they will get mad and not listen to you, so you're wasting your breath.

You can either say, "RTFM", or you can say, "I'm not sure about that, but try checking out the man pages and see if that helps."  It means exactly the same thing, but it doesn't make people mad. ;)

Now watch a bunch of people start using that sentence in every support thread to boost their post counts. :D

---

### Post by red_Marvin on 2009-10-02
**@forestcupp:** I almost never use the term anyway, and then only if I am sure that it will be understood in the right way. I guess what actually bugs me is that it provokes such a debate *every* time: I mean, 7/23 posts (this one and the original mention not included) = 30% of the posts in this thread, are debating or commenting on the use of the word.
It's not *that* offensive. People need to grow some thicker skin.

---

### Post by Sean Moran on 2009-10-02
> **red_Marvin said:**
> **@forestcupp:** I almost never use the term anyway, and then only if I am sure that it will be understood in the right way. I guess what actually bugs me is that it provokes such a debate *every* time: I mean, 7/23 posts (this one and the original mention not included) = 30% of the posts in this thread, are debating or commenting on the use of the word.
It's not *that* offensive. People need to grow some thicker skin.
Agreed, if I may soothe things as an humble OP.
First time I ever hears the acronym RTFM was from the service manager of the place where I was working as a workshop techie on HP, Compaq, Toshiba, NEC  386 gear in the early '90s,  Dot-matrix printers and HP plotter settings mainly, because I used to have good eyesight once.

Sometimes even now, when everything else I can glean from Google fails me,  I remember good old Ross and wonder what he would have done with my kind of user probkem, and I can bet you 50c that I  could guess the first four letters uttered from his mouth, but Ross knew what he was doing better than us humans should be allowed to in this life, and he taught me a few things beyond RTFM in the process.

---o0o---

I would like to ask if it maybe possible for Karmic, that Code takes the left hand and Data on the right.  That is how my desktop looks now, if it's okay with others. ***

*** What it means to me is that the left-margin on this browser ends up center of the whole screen if I size my desktop windows carefully.

---o0o---

It also means a nice relaxing desktop with just the browser and maybe some IM thing opposing.  Like those four quadrants they say about urgent and important.  Important Firefox takes the centre and right, with Urgent and important Nautilus around 33% on the less. 

If you're wise that leaves room below for gTerm and gEdit to cover the not urgent OR not important or both on a 1400x1050 resolution.  

I reckon that the larger window on the right of screen centres better for good focus on poetry and that other thing.

---

### Post by t0p on 2009-10-02
I want to add my support to the idea that RTFM is important if you want to learn how to use Linux.  Though I wouldn't actually tell an innocent newbie to "RTFM".

Instead, I say:


[LIST]
[*]Google Is Your Friend!
[*]Try "commandname --help" (or -h);
[*]"man commandname" is also a fount of wisdom;
[*]If you don't know which command/application you need, you can use the command "apropos subject" to find out what commands are available.  For instance, you want to do something related to networks.  So type into the terminal "apropos network" and you get a list of related commands.  Possibly the most useful command I know of.
[*]Oh, and don't forget Google!  She's your friend, y'know?
[/LIST]
Never be frightened of asking for help, in these forums, in IRC, in newsgroups, wherever.  But please, try helping yourself first.  There are many ways to search for information.  And people are much more willing to help you out if it's clear that you've at least tried to find the info for yourself.

---

### Post by Sean Moran on 2009-10-02
> **t0p said:**
> I want to add my support to the idea that RTFM is important if you want to learn how to use Linux.  Though I wouldn't actually tell an innocent newbie to "RTFM".

Instead, I say:


[LIST]
[*]Google Is Your Friend!
[*]Try "commandname --help" (or -h);
[*]"man commandname" is also a fount of wisdom;
[*]If you don't know which command/application you need, you can use the command "apropos subject" to find out what commands are available.  For instance, you want to do something related to networks.  So type into the terminal "apropos network" and you get a list of related commands.  Possibly the most useful command I know of.
[*]Oh, and don't forget Google!  She's your friend, y'know?
[/LIST]
Never be frightened of asking for help, in these forums, in IRC, in newsgroups, wherever.  But please, try helping yourself first.  There are many ways to search for information.  And people are much more willing to help you out if it's clear that you've at least tried to find the info for yourself.

I hope you don't mind that it is more the opinions of experts more aware of the 'Linux Mindset' to respond in the cafe than to revise all the info and man pages I've read in the last 12 years, but it certainly seems that RTFM needs to be foregrounded, as Karmic retains that same duo with Firefox and HELP! with Evolution transcended to the User side on the right.  <- the Data side of the desktop #1 IMHO.>

---

### Post by forrestcupp on 2009-10-02
Some people forget that the whole point of these forums is for people to come and ask questions and get viable answers to the questions.  That's why the forums are here.  If not, then maybe every time anyone loads up ubuntuforums.org, the only thing they should see is a great big

[SIZE="7"]RTFM[/SIZE]

---

### Post by earthpigg on 2009-10-02
> **forrestcupp said:**
> Some people forget that the whole point of these forums is for people to come and ask questions and get viable answers to the questions.  That's why the forums are here.  If not, then maybe every time anyone loads up ubuntuforums.org, the only thing they should see is a great big

[SIZE="7"]RTFM[/SIZE]

i think that would be a pretty great April 1 joke :lolflag:

---

### Post by markbuntu on 2009-10-02
RTFMing does not help at all for some stuff. You have to WYOFM.

---

### Post by fela on 2009-10-02
I think something to remember about the free software community is that there are four groups of Linux users (roughly speaking):

1) The people who use Linux because they know it's better for what they do on their computer than stuff like windows, and understand Linux very well.

2) The people who don't really understand Linux but think it's god's operating system and that nothing surpasses it, and annoyingly inflict their opinion on everyone around them.

3) The people who understand Linux but not its philosophy.

4) The people who don't really understand Linux and don't really care what OS people use.

Feel free to add some more groups. Just use addgroup ;)

---

### Post by Sean Moran on 2009-10-02
> **fela said:**
> I think something to remember about the free software community is that there are four groups of Linux users (roughly speaking):

1) The people who use Linux because they know it's better for what they do on their computer than stuff like windows, and understand Linux very well.

2) The people who don't really understand Linux but think it's god's operating system and that nothing surpasses it, and annoyingly inflict their opinion on everyone around them.

3) The people who understand Linux but not its philosophy.

4) The people who don't really understand Linux and don't really care what OS people use.

Feel free to add some more groups. Just use addgroup ;)
In all honesty that sounds something more like the political mindset rather than the Linux mindset - a problem-making mindset instead of a problem-solving mindset.  Still, what fingers on what hands would you associate with each group and what would you suppose the possible alternatives has a chimpanzee on a platform up a tree in the jungles of the Congo? 
:lolflag:


> **markbuntu said:**
> RTFMing does not help at all for some stuff. You have to WYOFM.
That's cool.  It's funny how it can happen that, depending on the time one has available, WYOFM is not only a possible help to someone else embarking on the same road one day in the future, but it's great way to properly memorise the way to do something new.  

They say that a good thing to do when you get to the stage of completing something new and complext for the first time, it's a good idea to pull it down and build it one more time to make sure you remember how.
WYOFM must be an expansion on that, but I'm puzzled as to whether it should take up something more like an aura over the set of hands, rather than any specific finger.

---

### Post by red_Marvin on 2009-10-03
> **markbuntu said:**
> RTFMing does not help at all for some stuff. You have to WYOFM.

And in some cases WYOFP.

---

