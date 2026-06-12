---
title: "USP behaviour"
date: 2008-01-08
forum: Ubuntu System Panel
---

### Post by Sugz on 2008-01-08
Ok, Im using Feisty. and the latest version of USP and Compiz fusion.
My problem.. 

Well here is a screenshot. 

[IMG]http://img223.imageshack.us/img223/1564/screenshot1zx5.th.png[/IMG]

As you can see, when i click on the thems option in USP, this window pops up.
However when i use the command line for example, its fine, no problems.

Notice.. That Usp is still "focused" i have a feeling that this may be linked to the problem. I have tried to get "click off to close" to work (just like Gnome-menu) with sucess, including the pin menu option in USP configuration panel. 

Im wndering how can i get USP to act just like a normal Applet in gnome where clicking off it closes the menu?

---

### Post by delfick on 2008-01-10
when you say latest version, do you mean svn version [http://code.google.com/p/ubuntu-system-panel/wiki/Installation](http://code.google.com/p/ubuntu-system-panel/wiki/Installation) ?? :D

also, can you post a larger screenshot please ?
(can't read that one)

thnx :D

---

### Post by Sugz on 2008-01-10
Yup i have that version that you posted. 
Oh dont worry about the screenshot, that problem rectified itself. :)

Still the focus problem is still present :confused:

Any help fella? cheers!

---

### Post by delfick on 2008-01-10
try clicking the little button in the top left of the usp when you have it open :D

---

### Post by Sugz on 2008-01-12
Yup tried that and nothing.. 
I have even looked through the code for it and nothing seems out of the ordinary.

---

### Post by Sugz on 2008-01-14
Bumping this topic as there is generally litle activity on this forum

---

### Post by delfick on 2008-01-14
that's because the two main developers, chanders and malac, both decided to move to different houses (seperately), and so development stopped....

though that was quite a while ago, so I'm wondering what's happening....

---

### Post by Malac on 2008-02-02
> **delfick said:**
> that's because the two main developers, chanders and malac, both decided to move to different houses (seperately), and so development stopped....

though that was quite a while ago, so I'm wondering what's happening....
Okay, okay, I'm back.
Finally got into my new house, Hurrah! and Never Again, etc....
8 months of moving house, total nightmare.:(
Totally behind with everything to do with Ubuntu so am trying to catch up frantically.
I'm currently trawling through a seriously large backlog of e-mails most of which will be rubbish or already dealt with.
I'm just too paranoid I'll miss something if I don't check them all out. :)
And also going through updating to Gutsy from Feisty as I haven't even done that yet. Should be sorted in time for Hardy release :)
Will try and start answering posts on the forum again (waits for deluge). And get back up to speed on USP development asap.
I've seen that Quikee has done a core code revamp which is on my "check-it-out" priority list.
Hope chanders is back soon and sorted.

So, sorry for disappearing on you's all and hopefully I can start helping again.

---

### Post by Sugz on 2008-02-02
Welcome back! Good to hear that you are continuing development, good luck for it!.:popcorn:
-Sugz

---

### Post by delfick on 2008-02-02
> **Malac said:**
> Okay, okay, I'm back.

yay! :D

> 8 months of moving house, total nightmare.:(

was it really that long ? 

that's incredible.

> I'm currently trawling through a seriously large backlog of e-mails most of which will be rubbish or already dealt with.

good luck with that :)

> And also going through updating to Gutsy from Feisty as I haven't even done that yet. Should be sorted in time for Hardy release :)

lol

> And get back up to speed on USP development asap.

:D :D

> Hope chanders is back soon and sorted.

same.

> So, sorry for disappearing on you's all and hopefully I can start helping again.

it's all good.

---

### Post by sweetthdevil on 2008-02-03
Great news to have you back!! 

I really don't want that project to be stop!

looking forward for your next release!

---

### Post by chanders on 2008-03-26
> **delfick said:**
> that's because the two main developers, chanders and malac, both decided to move to different houses (seperately), and so development stopped....
 
though that was quite a while ago, so I'm wondering what's happening....
 
Guess who dropped in! LOL. Hi guys, how have you all been? I know it seemed that I dropped off the face of the earth but in between moving jobs and a new house my time has been so limited. The major factor though is that my new job confines me to Windoze so programming only can happen after work (very little time). I should really look into gtk for windows..
 
I was so pleasantly surprised to see the familar faces here, Delfick. And to see the one who has kept this going, Malac still fighting it out. And even more happy to see that Quikee has decided to do a rewrite which I am assuming makes it even easier to install/run/configure?
 
But the most exciting thing is that USP lives! It has not been replaced by some other program. Over the past year (yes it has been that long!) I have been checking in but didnt want to post to give people false hope about USP3. I still have the main framework for USP3 but that is about it. I can pass it on to the developers who have time to work on it. Also if anyone is interested in gaining developer access to the SVN let me know. I still have to have to chat with Malac and he/myself will let you guys know.
 
I was a bit dishearthened though that the Mint distribution has been using USP as a default and has not credited Malac of myself anywhere. Not sure how it works but some credit would have been nice, dont ya think? (if it was, let me know)
 
So guys, I am back and I will be phasing in SLOWLY as I havent done any programming since the beginning of USP3. I am hoping that some of the frameworks that we were hoping for has been implemented (what do you say Malac :-D )
 
I would like to see a screenie of the new usp that quickee has done, so if anyone has it, let me know.
 
Again, it feels great to be back.

---

### Post by Malac on 2008-03-26
Hi chanders, It's great that you're back. I too had a nightmare move and have only just got back myself apart from fending the odd query whilst I was on dialup.

I haven't had a chance to look at Quikee's re-write myself yet so I don't know where it is up to or even whether the current plugins are compatible or not, though I seem to remember on one of the threads he said he was re-writing the plugin interface as part of the re-code.

I know I definitely wanted to tidy the code of some of the plugins before all this moving stuff got in the way. I have
 yet to re-look at the transparent tabs problem, too.

Haven't tried the mint distribution but you would hope that some credit would be listed in the about window. Perhaps I'll download it and check it out.

Good to have you back, we missed you.

---

### Post by Quikee on 2008-03-26
Hello chanders and malac.

Well my USP rewrite is not nearly as finished as the old USP 2.0 - you can't even add plugins to it, but I've been figuring out how to do it as generic and clean as possible, so future changes could be added easily. 

One of the things that I had to prove to myself is that plugins can be written to be size independent (as much as possible) - only width and height of the plugin should be defined fixed / configurable bu
t not any other element - and I succeeded to create USP2 like that. 

Plugins aren't compatible but modifications should be only slight, however plugin interface is not fixed yet either as I have to figure out a good way to communicate between core an plugins without exposing the internals from either core or plugin.

The bad thing is that I have so many project going on now that I hardly find much time to work on it (currently I have been working in Vala - I have even tried a Vala version of USP but I would like to have a mature python version first).

I will put the source code of USP2 into USP svn so you can all fiddle with it if you like. It would be cool if current USP3 code could also be put up. 

I had made a screen cast for USP2 but I have already put it down... i will made it available again [here]("http://freeweb.siol.net/tvajng/usp2.ogg").

EDIT: usp2 source is now available in [http://ubuntu-system-panel.googlecode.com/svn/trunk/usp2](http://ubuntu-system-panel.googlecode.com/svn/trunk/usp2)

---

### Post by delfick on 2008-03-26
> **chanders said:**
> Guess who dropped in! LOL. Hi guys, how have you all been? I know it seemed that I dropped off the face of the earth 

:D :D :D

> but in between moving jobs and a new house my time has been so limited. The major factor though is that my new job confines me to Windoze so programming only can happen after work (very little time). I should really look into gtk for windows..

ahh, didn't think moving house would have taken that long....

unless you had an absurd amount of stuff :p
 
> I was so pleasantly surprised to see the familar faces here, delfick.

:) 
 
> Over the past year (yes it has been that long!)

past couple of years have been quick for me :)
(uni started last year)

>  I have been checking in but didnt want to post to give people false hope about USP3.

probably a good thing :)

> I still have the main framework for USP3 but that is about it. I can pass it on to the developers who have time to work on it.

*thumbs up*

> So guys, I am back and I will be phasing in SLOWLY as I havent done any programming since the beginning of USP3. I am hoping that some of the frameworks that we were hoping for has been implemented (what do you say Malac :-D )

good to have you back *insert another smiley here*
(I ran out of smilies, this forum only allows 8 in a post, lol)

---

### Post by Malac on 2008-03-27
Had a look at Mint and you do get a credit in the about box. see attached.
[ATTACH]64000[/ATTACH]
They're not using uspconfig or any of my plugins and I only tweaked with the ones they are using so I'm not bothered really......:^o:)
[ATTACH]64001[/ATTACH]
Though even in the credits would have been nice. :)

---

### Post by chanders on 2008-03-27
^^ Thanks malac.  Did it look like they did any work with the code? Doesnt look so..

---

### Post by Malac on 2008-03-27
> **chanders said:**
> ^^ Thanks malac.  Did it look like they did any work with the code? Doesnt look so..
I've not had time to check the code thoroughly yet. On first viewing I'd say they've not changed much.
Though they aren't using the recent plugin by default when I tried to add it to the menu it errored. Will take a closer look tonight.

[COLOR=DimGray] Edit : Well they have left in the uspconfig sections of the plugins even though they are not using them. It looks like a lot of it was just a search for "usp" in the files and replace it with "mintMenu" :).

They have done some code tidying as well and tweaked some of the code here and there. The recent plugin was just as in usp version just with the search replace done on it. It must have been an older version as it didn't have the new toggle code in it, which was part of the reason it was throwing out an error.
I fixed it for them if they're interested. :)[/COLOR]

---

