---
title: "Advice from a curious newbie"
date: 2014-05-27
forum: Ubuntu, Linux and OS Chat
---

### Post by rook3 on 2014-05-27
Sometimes, the smart folks know too much. From one noob to another... This is going to sound really silly... Use  the info supplied in the terminal. 
[U][I]
Of course, Google/forums are still generally faster for any SPECIFIC problem. 
[/I][/U]
The internet is a really good  resource, but the folks writing make  assumptions about new folks. It's practically muscle memory for  them to deal with linux, their distribution, or the commandline. If you're actually curious, the in box manual is VERY thorough; you won't be left asking "what steps did you skip or take to get there?". If you play around in the terminal, it will make life a lot easier when you're too stressed to play. 

Eventually  you'll run into an issue where you have to use the terminal(like  command prompt or DOS), or ask a smarter geek. It REALLY helps to be  familiar with it. Sometimes you can surprise the helpful folks lending you their time. Whether it's a friend you're abusing, gracious volunteers, or paid tech support. 

"info"  is awesome. It even gives you info on how to read the info.  Press "?"  to see the buttons you should be pressing to navigate. Move  to a topic and hit enter to read that section. "(l)ast" is rather  important for going back a node. If you get lost, go back to an index.

"help (command)" is great, but you need to know the command name to "help (commandname)".  Not always the case, so, google or the info function(Especially if you don't have internet...) 

"(man)ual" is underrated. "man (commandname)" is useful. "man man" is a  bit silly- if you're capable of this much depth reading the manual on  how to read the manual, your patience is incredible. 
"man -a intro" shows every manual page that's part of the intro. It  tells you how to get help. If you don't have an internet connection...  Worth a read. A crappy netbook in a place without internet is like a  sub-par book. 
"man woman" is not as useful as you would think; but it's very true. The manual function does not lie.

 "info  coreutils" is the basics of how to deal with the terminal. Highlight an  entry and press enter for that helpfile. "Directory listing" and "basic  operations" are useful... 
(l)ist(s)tuff, (m)o(v)e, (r)e(m)ove, (c)hange(d)irectory, etc... are all listed there. The stuff you need to manipulate files and move around. 

Some of the "simple" commands are more powerful than you may be used to if you came from windows. "shred", as an example, is very simply a delete function. But it performs multiple overwrites of the file to prevent forensic recovery on sensitive info(With exceptions). Deletion or a recycle bin is not comparable. 

More complicated commands like "apt-get" are often more commonly used  than some of the simpler commands. But being able to navigate the  help/manual pages can help a ton; it can help you put together those arcane terminal lines with tons of regex and options people are recommending you use. man/info/help are the basis for using everything else...

---

### Post by buzzingrobot on 2014-05-27
Online howto's are typically expressed in terminal commands because those commands will, within reason, work on any reader's system.  Guidance that relies on a GUI tool requires that GUI tool be available to everyone, which is often a bad assumption.  Besides, it is often tedious and time-consuming to write a narrative describing how to point-and-click all the right spots. Web sites who want to attract clicks and page views will take the quickest and most popular approach.

And, frankly, many users do not really want to learn anything.  They just want to blindy copy-and-paste something. The ironic thing is, very often, the GUI tool simply collects info from the user, buillds a command, and passes it along to the shell or a character-based tool, just as happens when we use a terminal.

---

### Post by mastablasta on 2014-05-27
no what he is saying is that ther eis plennty of how to's and info available in command line itself.

this goes for MSdos based systems as well only their switches are different and sometimes explanations are not so detailed.

---

### Post by SeijiSensei on 2014-05-27
When I first started out with Unix, I found man pages overwhelming.  I was hardly a newcomer to computing either having worked on mainframes and in DOS/Windows for many years.  Man pages are designed to document a command and all its switches.  While some include helpful examples, most assume you'll understand the syntax description and the available options and go from there.  For a good example, look at "man mount".  It is nearly 2000 lines long and provides detailed information about all the options available for all mountable file systems.  For someone coming to Ubuntu from Windows, even the notion of a "filesystem" is unfamiliar since Windows has only one, NTFS.

---

### Post by LastDino on 2014-05-27
Well, MS doesn't really expect 99% of their users to even touch the command line. And they purposefully made that thinking streamline in their products, I think that has been the case since MS ME came out, which was also the era when dos-games were replaced by other alternatives and you didn't need to manually format drives through dos to install your OS, that didn't help either.  
The ones who actually do know about it, probably also know how to use it enough to not need as detailed explanations as LInux command lines do. 

Before coming to Linux, the only thing I used MS-Dos was for  to check ''ipconfig'' and ''ping IP'' to check connectivity :3

Now, I have at least one command line window open somewhere whenever I turn on the PC. I wish I had came over to this side when I first came to know about Ubuntu & Fedora in 2007. I feel like; I would've learned lot more than what I managed with Windows, and now even idea of me using Windows seems silly. Not that I'm being extremist, but for what I use my PC for, its overkill to pay that much amount just for an OS when there are better alternatives available for free which do the same job.

---

### Post by buzzingrobot on 2014-05-27
> **SeijiSensei said:**
> When I first started out with Unix, I found man pages overwhelming...   Man pages are designed to document a command and all its switches.  While some include helpful examples, most assume you'll understand the syntax description and the available options...

True, true. man pages are not tutorials.  They're written to be reference material for knowledgable admins.

Unix was the first OS I was exposed to, way back when.  I had an experienced Unix person helping me along, but it was not easy.  The "a-ha" moments came from understanding the underlying principles and organization of the OS, and that came after reading a number of books about it, including those authored by its original developers.

Clicking away at a GUI tends to obscure the differences between operating systems, because the most obivous differences are visual.

---

### Post by stalkingwolf on 2014-05-27
In my experience new users of Linux fall into two areas, 1. those that used windows for years and 2 those with limited experience on any system, for instance preteen kids.
In the first instance they will stubbornly try to "do it the way they always have."  I have run into this so much that I have started prefacing any help instructions with, " you have two choices, either do what i tell you how i tell you or do it your way and possibly screw it up in which case you can repair it your way."
In the second case my experience has been primarily with 7 -12 yr olds. Their experience seems to have been largely from school with the teacher giving instruction as they go. so I give basic instruction (or their parents do) such as where things are found etc. then i give them what i think is the most important instruction they can get. GO PLAY, try things. you cant hurt it , if you break it we can fix it."

And you know i have yet to get a call that its broke. I have got calls telling me they found things that i didnt know were in there.  In one instance I gave a laptop to the son of a family member for his birthday.  We were on a skype call when it was delivered.  we watched enthralled as he opened it then she set it up, showed him how to log in, i had installed ubuntu with the edubuntu packages.
for the net 3 solid hours we watched as he discovered new games and this and that.  He had homework he had to do over the spring break. to that point it was a chore to get him to do 1 hour.  the next day he asked to do a second hour and the a 3rd. which she told him 2 was enough for right then.  by the end of the break his scores had doubled and he had created his own screen saver for one of the games.

---

### Post by rook3 on 2014-05-28
@Stalkingwolf- That's kind of awesome :-D We did the same thing in the martial arts (for older students); before/after class was a great time to train, when it's NOT a specific technique. Just throw eachother around. I think it's a good mentality to have, if you don't have a problem in front of you.

If you're not comfortable being hit or knocking someone down, that's a bigger issue than not knowing technique. 

Context:
I came to ubuntu mostly from 95/XP, not entirely a kid, but I feel like one. Windows 7 and 8(particularly) **** me off; I really slow down on them. Lubuntu was initially a good match because the layout is almost the same as XP; eventually I had to use the terminal because the windows key wasn't opening the start menu, and I ended up smashing it entirely too often. My first task was to set the windows key to open the menu :P I played dwarf fortress for awhile, played MUDs back in the day, and mostly use my keyboard to navigate, not the mouse, within a desktop environment. 

I don't think manual is too bad, you don't have to understand everything; only take important bits away from it, or find stuff to [FONT=times new roman]info[/FONT]/[FONT=times new roman]help. [/FONT]If it's too much, even just underlined words is enough :) Especially if man is open in one window, and info/help in other terminals.

---

### Post by stalkingwolf on 2014-05-29
One of the best lessons the great Bruce Lee taught. The best technique is no technique. use what works.

---

### Post by hacksonfive on 2014-05-29
This post is actually really informative, especially coming from someone that claims to be a "newbie''. It reminds me of something that I read earlier today:
+ If you don't desire to learn, you can't be helped. 
+ If you desire to learn, you can't be stopped.

Or something like that. It was on an inspirational poster or something. It didn't make me think about Linux at the time, but this post is a good application of the message that the message was trying to convey. 

> **rook3 said:**
> 
 "(man)ual" is underrated. "man (commandname)" is useful. "man man" is a bit silly- if you're capable of this much depth reading the manual on how to read the manual, your patience is incredible.

 I actually found this comment quite entertaining. I laughed out loud as I recall reading the "man man" page when I first started with Linux. Some of the things that I tried to grasp all at once by reading that page (along with many other man pages) I am just now grasping today (after about 5 years of using Linux). The desire to learn is a good thing. I find it alarmingly uncommon amongst new users of Linux. 

People come to Linux for a variety of reasons, I would assume mostly because it's a free operating system that works (now!) "out of the box". That is, until someone mentions the command line, which people automatically think that it takes a programmer to operate. I really like to see people wanting to actually learn the system as opposed to wondering why they have to use the terminal to apply cryptic commands like "tar" and "mv" and "cp" just to get YouTube working. Say something like "sed", "cut" or "tail" and you can hear sighs of distress and brains breaking around the world.   

When I first joined these forums (under a different name which I can no longer find) I was told to read an article called "Linux is NOT Windows". I guess that was recommended because a willingness to learn the ins and outs of something new is important to getting the most out of it. I, at first, thought is was discouraging, but my own willingless to learn helped me overcome being discouraged.

I guess that's why I like to see that there are people out there like myself in today's world.

---

