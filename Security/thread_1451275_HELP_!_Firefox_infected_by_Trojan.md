---
title: "HELP ! Firefox infected by Trojan"
date: 2010-04-10
forum: Security
---

### Post by gusteman on 2010-04-10
Hi there, I hope someone can give me a solution for the following problem.
Recently I discovered strange flashes on my screen when I started up Firefox. Sometimes they occured, sometimes they didn't. I found out that my hard disk contains quite a lot of bad sectors so I intended to have it replaced. Today I could not get Firefox started, i.e. it could not get to the Google site. At that time I was working in Hardy, which is still my main OS. When going into preferences and changing the start-up page, Firefox could not start up in Ubuntu home page. So I tried "using current page". And there it was: **"http:/about : blank"**. A well known Browser Hijacker. 
I changed to Karmic where I could get Firefox working as normal.
So here it is: has anyone any idea on how to remove this malware?
I would be very gratefull.

---

### Post by Jigen on 2010-04-10
> **gusteman said:**
> Hi there, I hope someone can give me a solution for the following problem.
Recently I discovered strange flashes on my screen when I started up Firefox. Sometimes they occured, sometimes they didn't. I found out that my hard disk contains quite a lot of bad sectors so I intended to have it replaced. Today I could not get Firefox started, i.e. it could not get to the Google site. At that time I was working in Hardy, which is still my main OS. When going into preferences and changing the start-up page, Firefox could not start up in Ubuntu home page. So I tried "using current page". And there it was: **"http:/about : blank"**. A well known Browser Hijacker. 
I changed to Karmic where I could get Firefox working as normal.
So here it is: has anyone any idea on how to remove this malware?
I would be very gratefull.

are you still working on the defective hard disk, or did you replace it?

---

### Post by gusteman on 2010-04-10
Effectively still working on the old hard disk. I was planning to buy a new one next monday.

---

### Post by Jigen on 2010-04-10
> **gusteman said:**
> Effectively still working on the old hard disk. I was planning to buy a new one next monday.
  actually I don't know whether the reason for your issue may be found in the defective HDD or in some other stuff like [http://www.ubuntu.com/usn/USN-921-1](http://www.ubuntu.com/usn/USN-921-1)
in fact, I am just reading of other people complaining for browser hijacking at my mother-tongue ubuntu forum
 :confused:

---

### Post by gusteman on 2010-04-10
Hi there Jigen, thanks for your quick reply.
I quickly checked out the link you posted, and am not quite sure if it could be one of those possibilities.
Of course I am not a programmer so when it gets to this kind of problems I an really a rookie.
Somehow it must be a bug or whatever in Firefox. I was running Firefox 3.0, maybe the answer should be found there?
What interests me the most is how to get rid of this malware.
I remember having the same infection about 4 years ago. I still was working with Windows and Explorer. At that time it was enough to install Firefox to have the problem soved. Afterwards I changed to Ubuntu and never got back to Windows, mainly a question of security. Apparently the guys who write these Trojan patches have found a way to infiltrate through Firefox as well.
By the way, you mentioned your "mother-tongue Ubuntu forum". Which might that be? I myself am Flemish but have no problems understanding French or English. German on the other hand is not my strongest point, if you see what I mean. If it would help finding a solution, just let me know what language you prefer.
Once again, thanks for your support so far, greetings, Gusteman

---

### Post by Jigen on 2010-04-10
> **gusteman said:**
> Hi there Jigen, thanks for your quick reply.
I quickly checked out the link you posted, and am not quite sure if it could be one of those possibilities.
Of course I am not a programmer so when it gets to this kind of problems I an really a rookie.
Somehow it must be a bug or whatever in Firefox. I was running Firefox 3.0, maybe the answer should be found there?
What interests me the most is how to get rid of this malware.
I remember having the same infection about 4 years ago. I still was working with Windows and Explorer. At that time it was enough to install Firefox to have the problem soved. Afterwards I changed to Ubuntu and never got back to Windows, mainly a question of security. Apparently the guys who write these Trojan patches have found a way to infiltrate through Firefox as well.
By the way, you mentioned your "mother-tongue Ubuntu forum". Which might that be? I myself am Flemish but have no problems understanding French or English. German on the other hand is not my strongest point, if you see what I mean. If it would help finding a solution, just let me know what language you prefer.
Once again, thanks for your support so far, greetings, Gusteman

Unfortunately it's the italian forum, however at the moment the few people having browser hijacking issues do not seem to have solved the problem. I will post here to inform you if any solution is found. Currently, some users are suggesting to backup your bookmarks, delete the ~/mozilla folder in your /home (this will cause the loss of all of your preferences and bookmarks so it's important that you backup as much of these data as you can) and then restart firefox. If it works normally, then install the noscript extension.
:)

---

### Post by gusteman on 2010-04-10
> **Jigen said:**
> Unfortunately it's the italian forum, however at the moment the few people having browser hijacking issues do not seem to have solved the problem. I will post here to inform you if any solution is found. Currently, some users are suggesting to backup your bookmarks, delete the ~/mozilla folder in your /home (this will cause the loss of all of your preferences and bookmarks so it's important that you backup as much of these data as you can) and then restart firefox. If it works normally, then install the noscript extension.
:)

Thanks again for the quick reply, Jigen.
Yes, Italian is not one of the languages I master, but once again I find that the Ubuntu mentality covers the entire world, with people helping out each other all around this planet.
Untill now I just kept surfing through my Karmic OS where I do not have the same problem. Initially I upgraded one partition (on the same defective HD) from Hardy to Karmic just to find out the changes and get the feeling of it.
For your info: in my Hardy I already removed Firefox through Synaptic, after having made a backup of my favourites, so this might have solved the problem. Nevertheless I will first go check on the Terminal if everything was really removed. Afterwards, I am going to re-install Firefox, hoping this will have resolved the problem. 
If not, I will be coming back to this forum and this thread, which I will monitor anyway, looking for your posts.
Once again, many thanks for your replies, and wish you enjoy a fine weekend;
Greetings, Gusteman. :popcorn:

---

### Post by HermanAB on 2010-04-10
Howdy, note that you can download the latest Firefox Beta and untar and run it from your home directory.  The you can compare the performance of the two versions - old and new - to see where the problem lies.

---

### Post by gusteman on 2010-04-10
> **HermanAB said:**
> Howdy, note that you can download the latest Firefox Beta and untar and run it from your home directory.  The you can compare the performance of the two versions - old and new - to see where the problem lies.

Hi there HermanAB.
Thanks for the suggestion, but you see, as a plain rookie, the solution you forwarded gives me the feeling like as jumping off a ship in the middle of the ocean when you know you can't swim! If you see what I mean.
I have experienced a little bit with the terminal and know it is a very powerful device. Maybe so powerful that it frightens a bit. I am aware that I have not enough knowledge of how computers REALLY work and don't want to mess up my PC.
But, as I said, thanks a lot, and maybe (maybe!) I will try it out anyway.
You see, the problem is, when you are not familiar with computer-language even the forums (Ubuntu, Linux and others) are quite difficult to understand and sometimes I get lost in the mass of information that is provided. Usually I start with opening a topic or thread, and then I jump from example to example untill I am totally lost. I am still searching for a tutorial that explains step by step how to get familiar with the terminal, but most of the time I end up on pages where abbreviations are used, or references to actions that I never heard of, and so forth. 
I have all the respect of the world for people who do their utter best to explain the terminal, but personally I don't understand even half of it. 
Once again, thank you very much for looking into my problem.
Greetings, Gusteman
P.S. Even if I don't understand half of what I should know about computing, I will NEVER return to Windows and keep on studying Ubuntu (and Linux) until I really know what I am doing on my PC. I have gotten too fond of the Ubuntu principal!

---

### Post by cariboo on 2010-04-10
You may want to create a new firefox profile and see if the problem still exists. Press ALt-F2 and type:

```
firefox -ProfileManager
```

This will allow you to create a new profile. If it works with no problems, you can copy your bookmarks from the old profile to the new one.

---

### Post by lovinglinux on 2010-04-10
[COLOR="Sienna"]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by DrMelon on 2010-04-10
About:Blank is just an empty page - it's firefox's placeholder for "nothing".

I do not see the problem here. Likewise, firefox also has an about:config section for advanced configuration.

---

### Post by rookcifer on 2010-04-10
> **DrMelon said:**
> About:Blank is just an empty page - it's firefox's placeholder for "nothing".

I do not see the problem here. Likewise, firefox also has an about:config section for advanced configuration.

But saying it's a trojan is so much more fun and gets more people to read the thread. :guitar:

---

### Post by Jive Turkey on 2010-04-10
Your firefox profile is probably just the latest of the data to be lost on your failing HDD.  Backup now, and replace ASAP.

about:config is not a "famous trojan."  Now I'm curious what problem the Italians are discussing.

---

### Post by Jigen on 2010-04-10
> **Jive Turkey said:**
> Your firefox profile is probably just the latest of the data to be lost on your failing HDD.  Backup now, and replace ASAP.

about:config is not a "famous trojan."  Now I'm curious what problem the Italians are discussing.

They have been discussing about the problem few users are experiencing with a supposed browser hijacking. However this had nothing to do with about:config, user reported a strange webpage appearing and also a popup message about downloading some strange file, plus a general slowing of internet connection and the machine itself. User was asked to provide more information but didn't reply so far, maybe beacuse it's saturday night :)

---

### Post by gusteman on 2010-04-11
> **rookcifer said:**
> But saying it's a trojan is so much more fun and gets more people to read the thread. :guitar:

Hi there, all you ubuntu addicts,
first of all, I did not do this "just for the fun of it".
I just kept in mind the quote you can find with bodhi.zazen (ubuntu guru):
“Paranoia will get you through times of no enemies better than enemies will get you through times of no paranoia”
As I have experienced a few years ago, the "about:blank" page comes as a Trojan spyware infection through Internet Explorer under Windows.
Since then I got rid of Windows and switched over to Ubuntu.
Nevertheless I don't understand that for example Firefox still uses something like a "about:blank" expression, knowing that this must create confusion.
Once again I must point out that I am NOT an experienced programmer or so.
This means that anything that is not "plain" language has on me the effect of someone talking Chinese: I don't understand what they are saying!
Does this mean that I should not keep on using Linux oriented OS's? I don't think so IMHO.
But, as I tried to explain a few posts earlier, finding solutions for problems (or what I think might be a problem) is not really an easy task when you are not familiar with computer language. As I pointed out, when searching for solutions I stumble upon abbreviations that mean really nothing to me, so I have to go look it up somewhere else. This results in finding myself completely lost in a mass of information that I am not really searching for. See what I mean?
But thanks anyway for the hints you gave.
I will try them out, AFTER having replaced the HD.
Have a nice day,
greetings, gusteman

---

### Post by OpSecShellshock on 2010-04-11
Have you tried clearing out all the temporary data? Try this:

Open Firefox to whatever page allows it to open. In the top menu, go to Tools-->Clear Recent History. A little window will open up. There's a drop-down menu at the top where you should select "Everything." There will be a tiny arrow next to the word "Details" that expands to let you check what you want to clear. Make sure all the boxes in there are checked. Click the button to clear all of that, and then close Firefox.

Then in the main menu on your desktop, select Places-->Home. Press Ctrl + H so that you can see hidden folders. You're looking for a folder called .macromedia (take note of the dot in front of it). Open that folder, highlight everything in there and press Shift + Delete. When it asks if you want to permanently delete, hit OK.

At this point you can either restart your computer or just try to open Firefox again, and see if the issue's been fixed. It might not fix anything, but that stuff should all be regularly cleaned out anyway.

---

### Post by gusteman on 2010-05-12
Hi there,
sorry it took me quite a while to get back to this thread.
@ Jive Turkey: I nowhere stated that "about:config" might be a famous Trojan. I only mentioned this for "about:blank".
@ OpSecShellshock: thank you for the hints. They will come in handy in the future. 
As I stated several times on this Forum, working with the Linux oriented desktop can sometimes be quite confusing for people who have no knowledge whatsoever in soft- and/or hardware. The Terminal is very powerfull, but this power is also somewhat frightening for people who do not really know what they are "messing around" with. 
Up to this day I still am searching for an easy, understandable tutorial or howto for the Terminal. Until now I only found tutorials that are written by people who KNOW the terminal inside-out (which seems quite obvious). Unfortunately they all do their explaining beginning from the commands and then explaining what those commands really do. A newbie on the other hand is looking for a SOLUTION and wants to know which command he should insert. See what I mean? For example, if I want to know how to unzip a tar file and install a program using the terminal, supposing I don't know the exact command, I have to open a tutorial and check out ALL the commands until I find the right one. Wouldn't it be much easier if a tutorial was written where you first get the SOLUTION and THEN the command you should use? This way it could be much simpler to resolve problems and there should no more be entered hundreds, maybe thousands of threads in different Ubuntu/Linux forums. Look at it this way: as I already mentioned to a Guru on another Linux forum: most people who drive cars are not really interested in HOW the engine works. As long as it does the job, they will be quite satisfied. And if it fails, they only expect from a technician that he would be able to explain them WHAT happened an HOW they can fix it. They don't want a thorough course in car mechanics. They just want an answer to their problem.
And as Linux/Ubuntu gives a satisfying answer to the Microsoft/Windows problem (and personally I believe there is a MAJOR and growing Microsoft/Windows problem) people tend more and more to make the switch to the non-commercial operating systems. Even if it only were to get rid of the racketeering business of unsafe operating systems that need expensive anti-virus protection. Somewhat like buying a car but having to pay extras for efficient brakes, safety belts and steering wheel.

---

### Post by rookcifer on 2010-05-12
> **gusteman said:**
> Hi there,
sorry it took me quite a while to get back to this thread.
@ Jive Turkey: I nowhere stated that "about:config" might be a famous Trojan. I only mentioned this for "about:blank".

But that's simply incorrect (and laughable really) as has been explained a couple of times in this thread already.  about:blank is nothing but a way of denoting a blank page.  That's all, nothing more, nothing less.  It has nothing to do with trojans.

At any rate, good luck in your quests to understand the terminal.  There are lots of good tutorials out there.

---

### Post by impert on 2010-05-12
> Then in the main menu on your desktop, select Places-->Home. Press Ctrl + H so that you can see hidden folders. You're looking for a folder called **.macromedia** (take note of the dot in front of it). Open that folder, highlight everything in there and press Shift + Delete. When it asks if you want to permanently delete, hit OK.
I think you'll find that .macromedia is a slip of the tongue, as you might say. It should be **.mozilla**

I think it's improbable that you have a Trojan/worm/other nasty beastie. More likely your .mozilla file is corrrupt, or (less likely) a hard disk problem.
gusteman, in my limited experience free software is very robust, and any vulnerabilities get patched quickly. Don't lie awake worrying about malware, with Linux and commonsense, you're safe.
The greatest danger to a computer is its owner. If you have a separate /home partition, and back up frequently, you can always reinstall your OS, for the same price: 0.00, in whatever money you choose. Relax. 
You can go one better, and multiboot two or more Linux systems, which will let you boot a working Linux and tinker with the one that has the problem. You can have twenty systems for the same price. I do.

---

### Post by OpSecShellshock on 2010-05-12
> **impert said:**
> I think you'll find that .macromedia is a slip of the tongue, as you might say. It should be **.mozilla**

I think it's improbable that you have a Trojan/worm/other nasty beastie. More likely your .mozilla file is corrrupt, or (less likely) a hard disk problem.
gusteman, in my limited experience free software is very robust, and any vulnerabilities get patched quickly. Don't lie awake worrying about malware, with Linux and commonsense, you're safe.
The greatest danger to a computer is its owner. If you have a separate /home partition, and back up frequently, you can always reinstall your OS, for the same price: 0.00, in whatever money you choose. Relax. 
You can go one better, and multiboot two or more Linux systems, which will let you boot a working Linux and tinker with the one that has the problem. You can have twenty systems for the same price. I do.

Oh, I was talking about Flash cookies, which are stored in .macromedia separately from the mozilla folder.

---

