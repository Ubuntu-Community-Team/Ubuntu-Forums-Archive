---
title: "This is my story (it's not pretty)"
date: 2008-12-18
forum: The Cafe
---

### Post by sleepingdragon on 2008-12-18
I've held out until now because I wasn't sure where to post this event. I was tempted to go to Testimonials, but I think this is better off in the Cafe.

To protect the innocent (and the oh-so guilty), I've changed the names and places, but here's a quick Who's Who of those involved:


[LIST]
[*]SD - myself
[*]Mr Smith - A senior manager where I work
[*]Mr Jones - the owner of a neighbouring company (to my own place of work) that I will call "ACS"
[*]Jones Junior (JJ) - Mr Jones' son
[*]Alice - Main secretary to ACS
[*]ACS - Acme Chemical Suppliers. It provides chemicals of various types (oxyacetalene/butane/grease/solvents/adhesives) to local industrial companies. Owned by Mr Jones
[*]My own employers are an engineering company specialising in electro-mechanical devices. If it needs an electric motor with a gearbox, we can design and build it.
[/LIST]
Well, this all started about three weeks ago when I got a *tap* on the shoulder, it was Mr Smith.
"Do you have a minute?" *Like I have a choice... *"Sure".
He invited me into his office, where, in one of the chairs was sitting Mr Jones. I'd seen him quite a few times as he owned the neighbouring business, but I'd never spoken to him before.
"Hi..." [I]UH-oh. This doesn't look good.
[/I]Mr Smith started off the conversation.
"As you know, Mr Jones is our neighbour and supplier of various chemicals that we use. He's here in person today because we cannot place an order on his automated system. His computers are not working..." **twitch* *tic* I know what's gonna happen next *"... and since you have done some really useful things with a few of the computers here, I thought it would be a good idea if you could spend a little time looking at Mr Jonses' machines before there's the need to call out any expensive I.T chaps. Don't you think that's a good idea SD?"
*Slowly shaving your skin off with a blunt spoon sounds like a really fun game about now... *"Sure! No problem Mr Smith! Let me just a couple of things and I'll be right back."
I stormed off to find my usual range of tools for taking computers apart; screwdrivers, light, rescue CD's, and a WD portable drive I use for emergency backups.

Resigned to my fate, I returned to Mr Smiths office where business seemed to have concluded -
"Oh don't worry, he's very good. He'll have it up and running in no time" [I]No stress there then...
[/I]I left the offices and wandered back with Mr Jones. Now I've never been inside ACS before, but it was surprisingly very clean, tidy and well lit. My own place has a permanent veneer of grease about it.
"Well, this is it" Mr Jones invited me into the offices. There was one for himself, then a small kitchen, and finally an open plan room with desks for JJ, Alice and Mike (chief sales rep). Along the back wall was a range of cupboards, one was open with something that looked like a tower case and CRT monitor inside, and on top was a slightly ageing HP laser printer. At least the desktops looked sensible, all had decent LCD displays, 1.8Ghz Duo with 1Gb RAM.
"It's not much, but it works. Well, until yesterday anyway. The problem is our little server thing. I'm not clever with computers. My son (JJ) built it years ago from one of our old office computers, but it does the trick. We use it manage the printer, check emails and store files, that's about it."
I gave the tower a basic glance. White plastic had tanned to a deep nicotine yellow colour... [I]nice.
[/I]"I'll give it a look, but I can't promise anything. By the way, if JJ built it, why can't he fix it?"
"JJ is currently in Germany checking new suppliers, he can't get back for a few days. It's all bad timing really. He's always busy, spends a lot of evenings doing overtime too. He's a good worker".

Great, I got myself comfortable by pulling around of one the office chairs from behind a desk - it happened to be JJs chair. Leaning back, I nearly fell out of the damn thing! The recline had been set all the way back! At least Alice made decent coffee to steady me. 
So, first up, try the power button and see what happens - nothing. 
Checked power leads, all ok.
Checked all other cables and fuses/switches - ok too.
Pull the tower out and smelt the sweet aroma of cooked plastic and silicon - [I]*damn*
[/I]After following my nose, I pinpointed the smell down the PSU, some carbon streaks confirmed suspisions. 
"The power supply is blown. It should be possible to swap it out with a new one, but I'll need to take it apart."
Alice piped up, "Great. Expensive?"
"No, pocket change stuff, but let me check the rest of it first."
Just as well I did. As soon as I got the side panel off, the game was over for that old tower. Dust fell out as soon as I moved the panel. The rear fan grill was just a fluffy circle. The CPU fan was worse (afterwards it took a soaking in some serious solvents to clean the CPU heatsink). The fan had probably not seen decent airflow in years. 
I came to the conclusion that even if I replaced the PSU, the rest of it was only hanging on by a thread. Stuff on the MoBo has been heat-stressed for years. Even then, if something did fail, parts were going to be a problem. It was a 500MHz machine, not exactly *modern*.
"Er, Alice? This isn't good. I think this computer has had it. You might want to think about getting another one. Something a little more modern?"
Naturally, Mr Jones wasn't too impressed, but after convincing him that a slightly used machine would easily do the job, he knew he wasn't looking at a huge bill. I knew a local supplier who could put me together a nice little unit for about £200.
"Ok then SD, we'll get the new machine. What about the stuff on it, all our server things?"
"Ah, I've got something here that'll take care of that, it's called Ubuntu Server - and it's free."
"What?"
"Er... free? As in, "you don't open your wallet" free?" [I]Business men are so easy to please.
[/I]"Right! Splendid! You do that then and I'll order lunch, my treat!" [I]Told you so...
[/I]
So, next day, I collect the new tower. It turns out to be an HP Duo-core with an 80Gb and 160Gb drive pair and decent cooling. *Nice... simple and nothing clever, and a surprisingly good 2nd-user guarantee too.*
Anyway, in it went and I kitted up Ubuntu Server. Everything went nice and smooth (with some minor niggles over Samba, but the forums helped as always!)
The only thing I really had to do was try and recover any data from the old hard drive. It was the old file share and there were important things on it, not least the emails. Since JJ was away, I took off the cover from his tower and slaved the old drive into it. I ran from a Xubuntu Live CD and mounted the drive - thankfully it was intact. However, something was missing - the emails.
"Er, there's nothing stored here for emails..."
Alice didn't seemed concerned. "I've got mine and Mike said his were there yesterday, but he couldn't send anything..." *Now that's strange.* The emails were being stored locally on each desktop, not on the server. The folder share was simple, it was just another folder somewhere in the root folder of Windows. Not the best place in the world for a share, but it seemed to work until now. Overall, the whole thing was a poor hack. It only probably worked by sheer luck and possibly a lot of software installs until JJ found something that did the job for him without any real admin skills involved.
I copied the share folder over to the server drive. Alice checked the first folder and confirmed all the files were there right up to the point where the machine failed - at least that was the good news...
"Funny," she looked puzzled, "I don't remember there being four folders. What is the Archive?" [I]*twitch* *tic* My PC Spidy-Senses were NOT liking this.
[/I]"I'm not sure..."
The look on Alice's face said it all. I didn't see her screen initially, but how can I put this delicately... oh yes...

> The Archive folder contain a number of photos showing many men of supposed Thai origin. They had all decided in careers in female impersonation. Many were very skilled in their trade and some were so convincing that they had gone to the trouble of proving their original gender by having photos taken of them in various stages of undress. They appeared to be enjoying themselves *immensely*.JJ had a hidden folder on the server. I never got around to figuring out the folder share permissions from the old tower (a Win200 Pro unit), but it was a no-brainer that he had exclusive access to /Archive. Overtime probably involved him downloading as much as was possible in company time, and on company bandwidth. It would not have been difficult either to remote-access from anywhere in the world (including Narnia in JJ's case).
Poor Alice didn't know what to do. She couldn't tell Mr Jones, it would really upset him, but she now knew about JJ - and she would have to work with him everyday. I didn't envy her one bit.

We came to the conclusion that it was probably the best thing to simply wipe the folder. It had no place on the network and Alice could deny ever seeing it. JJ didn't know me so I could also deny everything. It was about thirty minutes later when the phone rang: it was JJ in Germany.
*"Hi. Only me, everything OK there?"*
Alice ~ "Yeah, we're all good here! How's Germany?"
[I]"Fantastic! Good some good leads and I'm looking at an adhesive supplier tomorrow. Er, I can't seem to connect to the sales brochures on the office computer. Is something wrong there?"
[/I]"Nope, not at all." Alice had gone bright red. "We had some trouble with the server earlier, but it's working again now."
[I]"What sort of trouble?" 
[/I]"Oh, I don't know, it just sort of died on us but it's sorted now..." Alice was shaking her head... [I]he's going to find out sooner or later.
"Right... ok. Not to worry, I'll take care of it properly when I get back. Can you email the brochures to me?"
[/I]"Sure! No problem! Just give me two minutes and they'll be on their way."
[I]"Thanks. I'll reply when I've got them."
[/I]With that, he hung up. For at least a minute we sat there in silence.
"He's going to know..."
"Yes..."
"How am I going to tell him?"
"Don't look at me..."
"Oh hell... hold on, I've got an idea..."

> From: [EMAIL="alice@acs.co.uk"]alice@acs.co.uk[/EMAIL]
To: [EMAIL="jj@acs.co.uk"]jj@acs.co.uk[/EMAIL]
Subject: Sales Brochures
Attached: brochure2008.pdf
Message: Here's the brochure you wanted. PS, next time, look at suppliers in Thailand...
... and off it went. Mr Jones popped his head into the office a little while later.
"How's it all going? Everything seems to be working again. Splendid!"
"Err... yes, it's all gone really well. The server is running again, it's certainly going to be a lot faster from now on, and you get some extra features for your money. Alice can now create auto-replies to general emails, and there's none of those massive delays you used to have moving your accounting files to and from the server."
"Fantastic! Mr Smith was right to trust you. I've got a little something for you..."
"Oh, thank you very much..." [I]a "20-year single malt and a small envelope roughly the size of bank notes" moment later and I'm a happy bunny. Not bad for 48 hours work, and I was still being paid by my own employer.

[/I]I never did find out what happened with Alice and JJ. Nobody seems to have left ACS and it appears Mr Jones is blissfully unaware he's unlikely ever to have grandchildren (unless JJ adopts), but at least the server works great. It now collects and archives email, each desktop collects from the server. File sharing is more consistent with both public and private folders for each user (but admin sees all - and it's *not* JJ). The printer was incredibly easy and CUPS is doing its thing. All this was managed through Webmin to which each user has a (very) limited set of functions they can control. SSH is on for remote access. Full admin access is held back from everyone until the day they need it... I'll keep hold of that for now.

Finally, Mr Jones did get back to me one thing: he'd been busy reading about Linux. This is a warning: when your boss (or any boss for that matter) takes an interest in what you've done - Lie, Deny All Knowledge, Fake Your Identity and preferable Fake Your Own Death.
"I've been taking a look at this Linux thing, it all seems very clever..."
"Yes, it certainly works for me."
"Tell me, since my computers are business machines, would SuSE be the best thing for me?"
**twitch* *tic* *gnash* I need a spoon, a nice blunt spoon...*

---

### Post by DeadSuperHero on 2008-12-18
This was an excellent read. So glad that it worked out for you!

However, I suggest to please not judge Mr. JJ. We all have our own fetishes, and although I believe it's wrong that he hid it at work, there is no shame when it comes to having a different sexual preference than most people. They're human beings, after all.

Back on subject, though. It's great that you got to promote Linux in this way! Any idea as to whether they're still using it?

---

### Post by sleepingdragon on 2008-12-18
Thanks for reading! His fetish doesn't really bother me either - I have my own too, but trying to hide it like that on somebody else's system is a bit naughty! Perhaps he felt the need to hide it, Mr Jones is a little *old fashioned* in some of his views... oh well. 

And yes, they're still using it, it's doing a great job. All I need now is for Mr Jones to tell all his business friends.

*blunt spoon... blunt spoon....*

---

### Post by Prefix100 on 2008-12-18
haha, careful, he might tell his business friends to get Suse.

Good story.

---

### Post by MaxIBoy on 2008-12-18
Oh dear, not SuSE...


Have 'em try Mint if they're interested in Linux.

---

### Post by bsharp on 2008-12-18
Lol nice. At least *some* good came out of it...

---

### Post by kk0sse54 on 2008-12-18
> **MaxIBoy said:**
> Oh dear, not SuSE...


Have 'em try Mint if they're interested in Linux.

As a server? :-?

---

### Post by Bracken on 2008-12-18
That's a funny story!  I'm glad that I didn't run across folders of that sort while working as a tech.  At least you got paid. 8)

You may be interested in submitting this to [The Daily Worse than Failure]("http://thedailywtf.com/").  They regularly run stories of this caliber.

---

### Post by MaxIBoy on 2008-12-18
> **C!oud said:**
> As a server? :-?

Oh, in that case have 'em try CentOS. (I just don't like SuSE.)

---

### Post by sleepingdragon on 2008-12-19
> SuSE as a server?

Ha ha... nice one.

It's just suddenly dawned on me... now I know why that chair reclined... he got himself very comfortable in those overtime sessions - and I sat in the same chair.

I feel really unclean about now. :cry:

---

### Post by SupaSonic on 2008-12-19
Great story, very well written. Glad it all worked out!

I know people who don't delete their "hidden" porn from "Recent files". I never mentioned it to them though.

---

### Post by billgoldberg on 2008-12-19
Nice story.

---

### Post by mmck on 2009-02-11
very nice story... it is pretty mate...

---

### Post by etnlIcarus on 2009-02-11
> Mr Jones is blissfully unaware he's unlikely ever to have grandchildrenThat ship was already at half-mast, coasting towards the sunset with his son being a geek. :p

And I don't know how extensively you checked //Archive but you're perhaps jumping to conclusions based upon a few gender-ambiguous images. I know people who've got *way* crazier stuff (hell, I've got crazier stuff than that) hidden amongst source files, yet they're getting engaged to members of the opposite sex and having kids, etc. Besides, transgender stuff tends to be more the realm of the curious, rather than the closeted.

Still, good story. Smart people who leech their boss' bandwidth take portable HDDs/laptops to work (I know a couple of *those* people, as well).

> **SupaSonic said:**
> I know people who don't delete their "hidden" porn from "Recent files". I never mentioned it to them though.The one thing I miss about doing lots of volunteer support for Windows users was getting people to cough up their links before I would tell them how to delete their IE history. :p

---

### Post by sharathpaps on 2009-02-11
@sleepingdragon

LOL... That's a really nice story. You know what..? You have a talent for writing. Its not easy to put together a story like that so fluidly. You should consider writing as a part time career or something.. :)

---

### Post by zakany on 2009-02-11
> **sleepingdragon said:**
> Ha ha... nice one.

It's just suddenly dawned on me... now I know why that chair reclined... he got himself very comfortable in those overtime sessions - and I sat in the same chair.

I feel really unclean about now. :cry:

Any sticky keys on the keyboard?

---

### Post by TravisNewman on 2009-02-11
sleepingdragon, this is one major reason I don't want to work with the public anymore when it comes to PC repair. I've worked in a few repair shops, and it's just amazing what you unwittingly find out about your customers. 

Fantastic read though, you should put this on dailywtf or customers suck. Somewhere. More people need to read it!

---

### Post by lukjad on 2009-02-11
Interesting post... slightly disturbing, but interesting.

---

