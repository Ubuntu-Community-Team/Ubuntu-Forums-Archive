---
title: "My wife's becoming Apple-fied..."
date: 2006-06-27
forum: The Cafe
---

### Post by aysiu on 2006-06-27
My wife and I had very similar computer journeys.

We both grew up in the 80s. We both came from DOS/Windows families. We both grew up using built-from-scratch computers (my dad built his own computers, and her parents bought from someone who built computers).

We also both had jobs out of college that forced us to use Mac OS 9, which was comparable to Windows ME in terms of usability.

Eventually, we moved away from Windows. She had to get a Powerbook for school, and I just wandered over to Ubuntu because I was bored with Windows.

Well, last night, she was complaining about how Apple's Mail program doesn't pay attention to what mailbox you're in when you compose a new message. I told her she should consider going back to Thunderbird because Thunderbird *does* pay attention to what folder you're in and put in the appropriate return address.

It's kind of weird. She has no problems using Firefox (and she actually really doesn't like Safari), but she's always had this struggle with Thunderbird. I think it's because Thunderbird, until recently, was unstable on the Mac. It would crash for no particular reason, and when quitting would hang for about ten seconds before actually quitting.

Converting her over to Thunderbird was like converting someone from Windows to Ubuntu, though! It was painful.

She had complaints all over the place. *Is there any way to get all the trash cans combined? Why does it look so ugly? How do I decrease this font size?*

When you're used to something, you want it that way, and you tend to be fairly critical of the imperfections of the new system and forgiving of the imperfections of the old system. I had to convince her that it's no more of a pain to use Cmd-Shift-M to compose a new message in Thunderbird as it was a pain to use Cmd-Shift-J to mark a message as junk mail in Mail.

I also started off with a little mind-reading gone bad. At first I thought she'd like the Tiger Mail Thunderbird theme, but she thought it was ugly (she didn't seem to find Mail's own interface ugly), but when she saw the Crossover theme I was using in Ubuntu, she said, "Oh! I want blue and white stripes in my mail, too." So I put her on Crossover in Thunderbird.

I think we're good now, though.

It took me about an hour to get her properly set up. I had to research a bunch of extensions and figure out how to do this userChrome.css thing (a lot of guides will tell you to edit this file, but few of them mention that you actually have to *create* the file first!).

Personally, I don't care if she uses closed source or open source applications. It just pains me to see someone complain about something for which there's a relatively easy solution--use something else.

But using something else isn't always so easy. You easily become accustomed to doing things a certain way, and it can be painful to learn to do things a different way.

She seems happy with her new Thunderbird setup, and I learned a few things in the process, too. I even found some extensions she wanted that I then decided I wanted too!

**Things I now hate about Thunderbird**
It defaults to autosaving messages every five minutes, which can be a pain in IMAP
It defaults to quoting above text
Its font settings apply to only the messages themselves and not the entire interface (this is where userChrome.css comes in)
It can't combine IMAP inboxes into one and then uncombine them at will (this is a nifty feature in Mail)

Okay... random blahblahblah post over.

---

### Post by bruce89 on 2006-06-27
If people couldn't complain, what else would they do?
Also people don't really like change, and if they are forced to, every problem they find has something to do with the new thing.  People get used to annoyances with time, and learn to live with them (usually).

---

### Post by hizaguchi on 2006-06-27
Heh, at least she lets you fix those things for her.  My wife gets really nervous when I do things to her powerbook.  Especially if the command line is ever involved.

---

### Post by aysiu on 2006-06-27
[QUOTE=bruce89]If people couldn't complain, what else would they do?
Also people don't really like change, and if they are forced to, every problem they find has something to do with the new thing.  People get used to annoyances with time, and learn to live with them (usually).[/QUOTE]
Yeah, that's basically what I learned. [quote=hizaguchi]Heh, at least she lets you fix those things for her. My wife gets really nervous when I do things to her powerbook. Especially if the command line is ever involved.[/quote] My wife's not tech-phobic at all. She's in charge of her computer, and she just had me do that stuff because she didn't want to bother researching all that herself... plus, it was my idea to bring her back to Thunderbird...

---

### Post by hizaguchi on 2006-06-27
Mine's not afraid of technology either.  She's afraid of me messing with her technology.:mrgreen:

---

### Post by bruce89 on 2006-06-27
[QUOTE=hizaguchi]Mine's not afraid of technology either.  She's afraid of me messing with her technology.:mrgreen:[/QUOTE]
Same with my sister actually.  You should have seen her when I tried Ubuntu on her laptop when she was out.

---

### Post by aysiu on 2006-06-27
[QUOTE=hizaguchi]Mine's not afraid of technology either.  She's afraid of me messing with her technology.:mrgreen:[/QUOTE]
Ah, good distinction! Touche.

---

### Post by Ptero-4 on 2006-06-27
Well at least your wives doesn't use Windoze.

---

### Post by aysiu on 2006-06-27
[QUOTE=Ptero-4]Well at least your wives doesn't use Windoze.[/QUOTE]
She actually once told me that she's more likely to use Linux than go back to Windows.

---

### Post by bruce89 on 2006-06-27
[QUOTE=aysiu]She actually once told me that she's more likely to use Linux than go back to Windows.[/QUOTE]
You just need to find a load of problems in MacOS X then!
Only kidding.

---

### Post by aysiu on 2006-07-21
> **bruce89 said:**
> You just need to find a load of problems in MacOS X then!
Only kidding.
Well, we found a big problem yesterday, but I think it just made my wife want me to keep using Ubuntu. I don't think she's going to switch over.

She has a Powerbook, but she also has an external monitor she sometimes uses for dual display. Yesterday, she was working on single display (just her Powerbook--no external monitor), and whenever she tried to get the Extract dialogue to come up in Photoshop, the dialogue would appear on the non-existent external monitor.

At first, I didn't believe her: "Are you sure it's not just hidden behind one of these other menus?" She was certain it was on the other monitor. So we plugged the other monitor in, and she was correct--it was appearing on the other monitor. So we dragged it back to the Powerbook monitor.

But then when she tried to open the Extract dialogue for the next picture, it opened on "the other monitor" (the one not hooked up any more) again.

She was starting to get pissed. We tried to "detect displays." We tried to change the resolution to a lower one and then select the higher one again. Nothing worked. So we did online research. She found something called [DisplayWatcher](http://www.brunchboy.com/displaywatcher.shtml) and thought it might help, so she installed it. Well, not only did it not help, but once she ran it, she couldn't quit, and she also couldn't eject the white disk on her desktop because Mac OS X said it was in use.

So now we had two problems.

Well, I solved both of them (go me!). The first solution I just knew from Ubuntu. I opened up a terminal, typed ```
top
``` found that DisplayWatcher was still running, typed ```
killall DisplayWatcher
``` and then ejected the white disk.

The second solution came from a Mac forum--delete the ~/Library/Preferences/*application name* folder. So I renamed all the Photoshop preference folders to something else, and my wife restarted Photoshop... and it worked!

She's not going to switch over to Ubuntu any time soon, but... I'll tell you the problems we've had with my wife's Powerbook--I can't believe people say Mac OS X "just works."

---

### Post by adam.tropics on 2006-07-21
You should have admitted defeat, rather than fixing it, saying, 'sorry dear, if it were Ubuntu, I'd know what to do, but I just have no idea.....' She'd come round soon enough!

---

### Post by aysiu on 2006-07-21
> **adam.tropics said:**
> You should have admitted defeat, rather than fixing it, saying, 'sorry dear, if it were Ubuntu, I'd know what to do, but I just have no idea.....' She'd come round soon enough!
I hadn't thought of that...

---

### Post by Lord Illidan on 2006-07-21
> **aysiu said:**
> I hadn't thought of that...

It is the standard windows techie approach for me too, now..

Actually, sometimes, I get a windows machine so cracked up that I really don't know what to do, beyond formatting and re-installing it.

---

### Post by Lord Illidan on 2006-07-21
EDIT : Double post, sry!

---

### Post by adam.tropics on 2006-07-21
> **Lord Illidan said:**
> It is the standard windows techie approach for me too, now..

Actually, sometimes, I get a windows machine so cracked up that I really don't know what to do, beyond formatting and re-installing it.

..and yet Mac and Windows friends alike always go to the Linux person for tech support. I never worked that one out. I suspect they reckon, well if they can fix Linux, then windows should be simple. hmm another car analogy involving a mini and a Rolls Royce comes to mind!

---

### Post by Lord Illidan on 2006-07-21
> **adam.tropics said:**
> ..and yet Mac and Windows friends alike always go to the Linux person for tech support. I never worked that one out. I suspect they reckon, well if they can fix Linux, then windows should be simple. hmm another car analogy involving a mini and a Rolls Royce comes to mind!

Actually in my case, it is because I am the computer techie of the house, I suppose. But true...we linux users do tend to have a higher computing knowledge than most windows users. Not being elitist, just stating the facts. Somehow, linux hardens us in a way.

---

### Post by Derek Djons on 2006-07-21
> **adam.tropics said:**
> You should have admitted defeat, rather than fixing it, saying, 'sorry dear, if it were Ubuntu, I'd know what to do, but I just have no idea.....' She'd come round soon enough!

Well I totally stopped doing that. Friends, colleagues and their friends started to ask me question more often and even in weekends, calling me, emailing me and what not. I really got tired of that. So I started to tell everybody that I wasn't some kind of 24/7 helpdesk and they should stop calling / mailing me.

Problem with friends and family is, they are very grateful. But when something goes bad (whether it's a hardware issue or their own fault) it's immediately all your fault! ](*,)

---

### Post by RAV TUX on 2006-07-21
My wife refuses to use Windows or Mac. She insist on Ubuntu only.

---

### Post by adam.tropics on 2006-07-21
how true, and they always say...I don't know what you did, but you did something, or broke something or whatever..............very helpful. Aysiu, you must have the patience of a saint, but what do I know, I am divorced!!

---

### Post by Lord Illidan on 2006-07-21
> **Derek Djons said:**
> Well I totally stopped doing that. Friends, colleagues and their friends started to ask me question more often and even in weekends, calling me, emailing me and what not. I really got tired of that. So I started to tell everybody that I wasn't some kind of 24/7 helpdesk and they should stop calling / mailing me.

Problem with friends and family is, they are very grateful. But when something goes bad (whether it's a hardware issue or their own fault) it's immediately all your fault! ](*,)

Yeah that what happens. And as for being grateful and stuff...it's not like they're paying you..they just treat you like a free helpdesk instead of taking the extra step of googling their problem or figuring it out themselves!

---

### Post by 0per4t0r on 2009-06-29
She could dual-boot with ubuntu, and use evolution. It works pretty well for me.

---

