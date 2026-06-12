---
title: "I can't seem to most of my windows applications"
date: 2008-07-14
forum: The Cafe
---

### Post by Markissocoollike on 2008-07-14
Hi I'm finding trouble with most of my windows apps in ubuntu I've tried using wine 10 still no luck is there something which will work better than wine? Perhaps something which would just open the program without any menu problems and drawing problems? Thankyou!

---

### Post by avtolle on 2008-07-14
I'd suggest you either dual boot Windows for those apps or run Windows within a virtual machine.

---

### Post by Markissocoollike on 2008-07-14
> **avtolle said:**
> I'd suggest you either dual boot Windows for those apps or run Windows within a virtual machine.

do you guys endlessly repeat yourselves? I've already got a dual boot it comes with the installation, GOD!

---

### Post by avtolle on 2008-07-14
Well, you didn't mention you were dual booting; seems reasonable to me to presume since you didn't mention you were dual booting, you weren't.

Anyway, you aren't going to run those Windows apps natively on Linux, and I've no idea why you think you should be able to do so. If Wine doesn't work, then you could purchase Crossover and see whether it helps you. Otherwise, you'll need to run the Windows apps under (surprise) Windows.

---

### Post by avtolle on 2008-07-14
And, if you mean by "it comes with the installation" you installed through Wubi, you will need to restart your system to move from Ubuntu to Windows. Not too complex a solution, right?

---

### Post by Tomatz on 2008-07-14
> **Markissocoollike said:**
> do you guys endlessly repeat yourselves? I've already got a dual boot it comes with the installation, GOD!

I was about to help you...

That was before i saw this post!

:mad:

---

### Post by LowSky on 2008-07-14
People always forget WINE = Wine is not an Emulator. It cannot run Windows based programs that need access to Windows' registry files. Some thing cannot be duplicated and that includes those registry files.

Markissocoollike What programs are you trying to use?
Have you checked for compatability on WINE's website: [http://winehq.org/](http://winehq.org/)

---

### Post by estyles on 2008-07-14
Do not feed the troll.

---

### Post by Markissocoollike on 2008-07-14
> **avtolle said:**
> And, if you mean by "it comes with the installation" you installed through Wubi, you will need to restart your system to move from Ubuntu to Windows. Not too complex a solution, right?

no I install boot WHAM dual boot now whats hard about that?

---

### Post by Markissocoollike on 2008-07-14
> **LowSky said:**
> People always forget WINE = Wine is not an Emulator. It cannot run Windows based programs that need access to Windows' registry files. Some thing cannot be duplicated and that includes those registry files.

Markissocoollike What programs are you trying to use?
Have you checked for compatability on WINE's website: [http://winehq.org/](http://winehq.org/)

Flash MX and that I've even tried some of the main applications like notepad and paint but they don't work even warcraft 3 doesn't work which is a disappointment 

If you guys aint going to suggest anything other than dual boot and run a virtual desktop leave this thread as I'm not interested!

---

### Post by Markissocoollike on 2008-07-14
> **estyles said:**
> Do not feed the troll.

If you mean off simon the sorcerer yes I take that advice but if you are referring to me then I'm insulted!

---

### Post by oarion7 on 2008-07-14
> **Markissocoollike said:**
> do you guys endlessly repeat yourselves? I've already got a dual boot it comes with the installation, GOD!

Hey Mark, aside here's just a small word of casual advice, I've been surprised how much the community tolerates on this forum but in any case a post like that is really going to be interpreted very negatively and honestly most of the people who see someone ask for help and then respond like that would just close out the thread and move on rather than provide any assistance--just be patient and thankful that we are lucky enough to have such a great community of people who do take the time out of their day to help us maneuver this fine operating system. :)

One thing you might want to consider doing, if you haven't already, is googling specifically for the applications you want to work in wine--google *microsoft chat using WINE* for example--it may take a little bit of additional research, but you may find something--also, there may be DLLs that you simply need to copy from your windows installation into your WINE folders, and doing that **COULD** honestly make them work just fine (or as fine as they're gonna get) depending on what software we are trying to run and what they require...

actually, if you don't mind posting specifically what programs you are trying to run, there's a chance one of us has already got it working and would be more than happy to assit.:guitar:

EDIT: Nevermind I see you already mentioned notepad, paint, and flash mx.

Did your wine installation come with a notepad-like app built in? It does look and runs an awful like like the actual Windows notepad. As far as Flash MX goes I'll let you know if I find anything.

---

### Post by estyles on 2008-07-14
Seriously, Mark, you seem to be most interested in getting Ubuntu to run and look exactly like Windows... Why not just run Windows?  Didn't your computer come with it pre-installed?  And with XP or Vista, you can just run as Administrator and not have to worry about typing in your password like you've complained about.  After your system gets completely bogged down with viruses and bloatware, come on back and I'm sure the community would be happy to help you move back to Ubuntu.

---

### Post by tramir on 2008-07-14
I completely agree with oarion - the community provides help on a voluntary basis, so be nice in order to be treated nice.

Now about your problem - what exactly seems to go wrong? the WineAppDB lists Flash MX as platinum, running just fine in Gutsy (so I guess it should be the same in Hardy) -- see [this link]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1027"). Can you provide more details? What does wine say when you try to run these applications from the command line? What I mean is, open a terminal window, cd to the folder where you have the program, and run it via wine:

```
cd folder/of/application
wine application_name
```

And then post here the output. Then we can provide more help.

Also: guys, lay off of him. Everybody makes mistakes. One bashing is enough...

---

### Post by lavinog on 2008-07-14
> **Markissocoollike said:**
> Hi I'm finding trouble with most of my windows apps in ubuntu I've tried using wine 10 still no luck is there something which will work better than wine? Perhaps something which would just open the program without any menu problems and drawing problems? Thankyou!

What applications are you trying to use?
Are you trying to run them from your windows partition...if so that wont work.
you have to install them through wine to use them...once installed you should see a link under wine>programs

---

### Post by Markissocoollike on 2008-07-14
...the problem is now solved I used Winedoors now my applications work like a charm honestly, if you guys actually answered my question instead of your block of text on how insulting I am to other people which repeat themselves then this thread would had been finished sometimes I hate the support I get from you guys

---

### Post by Markissocoollike on 2008-07-14
And here's the link for wine doors:

[http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3)

click on the one that says: 
0.0.1 Debian/Ubuntu

And I used a youtube video to help me find it:
[http://www.youtube.com/watch?v=Nl7VHGNZ3xU&NR=1](http://www.youtube.com/watch?v=Nl7VHGNZ3xU&NR=1)

---

### Post by rossjman1 on 2008-07-14
> **Markissocoollike said:**
> ...the problem is now solved I used Winedoors now my applications work like a charm honestly, if you guys actually answered my question instead of your block of text on how insulting I am to other people which repeat themselves then this thread would had been finished sometimes I hate the support I get from you guys
Haha, what a douche. How can you expect us to help when you give us barely any information (such as error messages)?

---

### Post by estyles on 2008-07-14
> **rossjman1 said:**
> Haha, what a douche. How can you expect us to help when you give us barely any information (such as error messages)?

Try reading some of his other posts.  If you got a laugh out of this one, prepare to fall out of your chair...  :popcorn:

---

### Post by jocko on 2008-07-14
> **Markissocoollike said:**
> ...if you guys actually answered my question instead of your block of text on how insulting I am to other people which repeat themselves then this thread would had been finished sometimes I hate the support I get from you guys

If you have a problem that you need help with, do you really think the people that TRIES TO HELP YOU will be interested in helping you after you blow them off like this:
> **Markissocoollike said:**
> do you guys endlessly repeat yourselves? I've already got a dual boot it comes with the installation, GOD!
or like this:> **Markissocoollike said:**
> If you guys aint going to suggest anything other than dual boot and run a virtual desktop leave this thread as I'm not interested!

Those guys were trying to be helpful, and you practically called them idiots... Of course you will be labelled a troll... Do you think they will ever try to help you again after your comments?

They gave you the only possible answer to your question: If you're not happy with wine or cedega/crossover, then a virtual machine (which is not the same as virtual desktop, by the way...) or dual boot are the only options if you want to run windows programs.

Next time you have a question, be more patient.
If it seems like you don't get the answer you're looking for, you may consider that the cause is that you haven't given enough information about your problem?

---

### Post by Retro Gamer on 2008-07-14
..Warcraft 3 works just fine in Wine with out much help... I run it straight from a ntfs formatted USB HD... BTW to the rest of you there are plenty of non-douche people out here who need help... ;-P

---

### Post by Markissocoollike on 2008-07-14
> **jocko said:**
> 
They gave you the only possible answer to your question: If you're not happy with wine or cedega/crossover, then a virtual machine (which is not the same as virtual desktop, by the way...) or dual boot are the only options if you want to run windows programs.


They gave me? You must be joking I just answered my own answer and you guys get pissed just because you keep giving the your god damn repetitive messages if you quit treating me like a troll- "For the horde!" then maybe we'd get my threads finished quicker and no that is none of those things which you and others posted are not the only way round it you calling me the douche? You're the douche for arrogantly repeating what you just said and not realizing that I didn't ask for dual boot and other virtual machines... you obviously don't know what it means!

> **jocko said:**
> 
Next time you have a question, be more patient.
If it seems like you don't get the answer you're looking for, you may consider that the cause is that you haven't given enough information about your problem?

How about next time you stop treating me like a jerk and answer my question, I didn't give you any error information cos you didn't need what idiot gave you that idea and for those who have sight problems
[SIZE="6"]this is a thread for running windows applications in ubuntu[/SIZE]Now quit your wining and leave you are wasting my time

---

### Post by LaRoza on 2008-07-14
> **Markissocoollike said:**
> 
this is a thread for running windows applications in ubuntu

That requires Wine or a similar app. (The other's aren't free, and wouldn't likely be any better). That is the only way, besides running Windows in a virtual machine or dual booting. Remember, Linux isn't Windows! Try running Linux apps in Windows; you can't. (Given the open source model, you can usually recompile them and run them or use Cygwin, but you can't use the native binaries). 

> 
Now quit your wining and leave you are wasting my time

Thread Closed.

---

