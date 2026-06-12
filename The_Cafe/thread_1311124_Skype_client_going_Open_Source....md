---
title: "Skype client going Open Source..."
date: 2009-11-02
forum: The Cafe
---

### Post by solitaire on 2009-11-02
I just read an interesting article on Slashdot about the Linux Skpye client going opensource soon.
[https://linux.slashdot.org/story/09/11/02/1353245/Skype-For-Linux-To-Be-Open-Sourced-In-the-Nearest-Future](https://linux.slashdot.org/story/09/11/02/1353245/Skype-For-Linux-To-Be-Open-Sourced-In-the-Nearest-Future)

The Site linked to the article is currently down (slashdotted!) But it looks like the main core will be a compiled binary with the rest of the client being open sourced. Which might help with some of the issues people have been having with the Skype client...

Official Statement from Skype:
[http://share.skype.com/sites/linux/2009/11/skype_open_source.html](http://share.skype.com/sites/linux/2009/11/skype_open_source.html)

---

### Post by Excedio on 2009-11-02
> **solitaire said:**
> I just read an interesting article on Slashdot about the Linux Skpye client going opensource soon.
[https://linux.slashdot.org/story/09/11/02/1353245/Skype-For-Linux-To-Be-Open-Sourced-In-the-Nearest-Future](https://linux.slashdot.org/story/09/11/02/1353245/Skype-For-Linux-To-Be-Open-Sourced-In-the-Nearest-Future)

The Site linked to the article is currently down (slashdotted!) But it looks like the main core will be a compiled binary with the rest of the client being open sourced. Which might help with some of the issues people have been having with the Skype client...

I like the sound of that. Hopefully it will get some major improvements.

---

### Post by Keyper7 on 2009-11-02
(let's see if I'm the first posting this... ;))

[http://linux.slashdot.org/story/09/11/02/1353245/Skype-For-Linux-To-Be-Open-Sourced-In-the-Nearest-Future?from=rss](http://linux.slashdot.org/story/09/11/02/1353245/Skype-For-Linux-To-Be-Open-Sourced-In-the-Nearest-Future?from=rss)

rysiek writes "Seems like there might be a revolution in the works, as far as VoIP software for Linux is concerned. After mailing Skype support about Skype providing Mandriva RPM packages, Olivier Faurax got an answer which suggests that the Linux Skype client [will be open-sourced](http://ofaurax.free.fr/blog/index.php5/2009-10-31-00h31-0100.xml). After asking for verification of whether that was the case, the tech support answer claimed it is going to happen, and that it's supposed to happen 'in the nearest future.' Now, this probably only means the client (the underlying protocol will probably be handled by a binary-only library), but even if that's the case, it seems like there is still reason to celebrate."

EDIT: Enough speculation, here is the [official statement](http://share.skype.com/sites/linux/2009/11/skype_open_source.html).

---

### Post by BackwardsDown on 2009-11-02
Wow, never expected that! And only the client-ui (not the protocol) seems good enough for me.

---

### Post by FuturePilot on 2009-11-02
:o:o:o:o:o 


Whoa!

---

### Post by Dougie187 on 2009-11-02
Personally, I would think the library would be far more useful than the client. But who knows.

---

### Post by aaaantoine on 2009-11-02
> **Dougie187 said:**
> Personally, I would think the library would be far more useful than the client. But who knows.

1. They have to monetize the service somehow.
2. The most significant thing about open sourcing the client: 64-bit port; ARM port; you name it, someone can make a port for it.

---

### Post by eragon100 on 2009-11-02
And in other news, we have a news team on-site: hell has just frozen over!

---

### Post by FuturePilot on 2009-11-02
> **aaaantoine said:**
> 
2. Two words: 64-bit port.

Whoohoo! Also, hopefully this means we can make it not suck so much with PulseAudio.

---

### Post by Dougie187 on 2009-11-02
> **aaaantoine said:**
> 1. They have to monetize the service somehow.
2. The most significant thing about open sourcing the client: 64-bit port; ARM port; you name it, someone can make a port for it.

True, The 64-bit port would be very nice. But that still doesn't change that I think the protocol would be significantly nicer to have than the client. Though you can't get everything.

And I do understand they are a company trying to make money, and thats why they don't open-source the library, because they still want money.

Either way this is still helpful.

---

### Post by Keyper7 on 2009-11-02
I only have one comment.

Die, tray icon, die! No place to run, now! Mwahahahaha!

---

### Post by aktiwers on 2009-11-02
My skype sucks up 100% of one of my CPU's when its just idle.. :S

---

### Post by Bölvaður on 2009-11-02
so it could be put as a plugin for pidgin... hmm....

---

### Post by hanzomon4 on 2009-11-02
Oh Snap! This thing is really jumping off... FOSS ati drivers, tons of linux smart phones, Dell, netbooks, Kindles, now skype... The Apocalypse is near

---

### Post by aaaantoine on 2009-11-02
Now that I think about it, the binary library is probably also platform dependent... so possibly it's not as portable as I'm hoping.

Eh, I can't use skype anyway, my mic doesn't work.

---

### Post by hessiess on 2009-11-02
> **aaaantoine said:**
> 1. They have to monetize the service somehow.
2. The most significant thing about open sourcing the client: 64-bit port; ARM port; you name it, someone can make a port for it.

This would ONLY be possible if the *ENTIRE* application was open source, if only the GUI will be open source, with everything else handled by some binary lib, it would not be possable to port it to ARM, or even x86_64.

> 
so it could be put as a plugin for pidgin... hmm....


Potentially yes, however there would be licence comparability issues with the GPL.

---

### Post by lykwydchykyn on 2009-11-02
I hate to be cynical, but my guess is they just don't want to expend any more resources developing/packaging a client front-end for Linux, so they're dumping the code on "the community".  c.f. XaraLX.

---

### Post by Grifulkin on 2009-11-02
I don't even own a mic, I use an old pair of Koss headphones with one of them acting as a microphone.  Amazing the things you can do with stuff you can do with random stuff.  And supposidly, the headphones act as a very nice microphone from what I'm told by people I talk to on them.

---

### Post by lykwydchykyn on 2009-11-02
> **Grifulkin said:**
> I don't even own a mic, I use an old pair of Koss headphones with one of them acting as a microphone.  Amazing the things you can do with stuff you can do with random stuff.  And supposidly, the headphones act as a very nice microphone from what I'm told by people I talk to on them.

I'm surprised it has decent high-end response.  I don't suppose you have a picture of what you look like with a headphone strapped over your mouth?  :D

---

### Post by Dragonbite on 2009-11-02
> **aaaantoine said:**
> 1. They have to monetize the service somehow.
2. The most significant thing about open sourcing the client: 64-bit port; ARM port; you name it, someone can make a port for it.

You mean like the Android? iPhone? Netbooks? and embedded linux on Land-line-like video phones?

---

### Post by FuturePilot on 2009-11-02
> **lykwydchykyn said:**
> I hate to be cynical, but my guess is they just don't want to expend any more resources developing/packaging a client front-end for Linux, so they're dumping the code on "the community".  c.f. XaraLX.

That's a lot better than having a program that doesn't know what the heck a modern audio stack is.

---

### Post by solitaire on 2009-11-02
Skype runs fine on my 86_64 machine, No audio problems (unless i try to use "recordmydesktop" with the audio option on then i loose the mic!) Otherwise there's no problems! ^_^


p.s. I posted this 5 hours ago ^__^
[http://ubuntuforums.org/showthread.php?t=1311124](http://ubuntuforums.org/showthread.php?t=1311124)

---

### Post by Warpnow on 2009-11-02
Skype works perfectly if you buy the USB soundcard that comes with some versions of the headset. The card is C-media and its drivers perform perfectly with Skype. There's really not much chance of it not working if you get it. Audio, anyway.

An os version will be nice. It will be nice to see if any new features are implemented...or if this translates into pidgin/empathy having skype voice support.

---

### Post by lykwydchykyn on 2009-11-02
> **FuturePilot said:**
> That's a lot better than having a program that doesn't know what the heck a modern audio stack is.

Yeah, I'm not saying it's all bad; though it depends how much functionality is hidden away in the binary-only library.  We'll see, maybe they'll really get behind the OSS project.

---

### Post by szymon_g on 2009-11-02
[http://ofaurax.free.fr/blog/index.php5/2009-10-31-00h31-0100.xml](http://ofaurax.free.fr/blog/index.php5/2009-10-31-00h31-0100.xml)

nice :)

---

### Post by NoaHall on 2009-11-02
We know, we all know... :)

---

### Post by Crunchy the Headcrab on 2009-11-02
Skype doesn't work well with some of my gtk themes, maybe that will change with an open-source development.  :D

---

### Post by FuturePilot on 2009-11-02
[http://ubuntuforums.org/showthread.php?t=1311124]("http://ubuntuforums.org/showthread.php?t=1311124")

---

### Post by TheLions on 2009-11-02
horray! will have 1001 different forks of skype and non of them would fully functional...:(

---

### Post by Flimm on 2009-11-02
> **TheLions said:**
> horray! will have 1001 different forks of skype and non of them would fully functional...:(
Skype isn't fully functional as it is.

---

### Post by zekopeko on 2009-11-02
So let me get this straight.
This information is based on an email exchange between a Linux Skype user and Skype's customer service?
So some dude from customer service has the inside scoop from Skype developers and he's talking left and right about it while Skype developers remain silent on one of the most popular moves that they could do?

Real reliable source there.

---

### Post by Flimm on 2009-11-02
> **zekopeko said:**
> So let me get this straight.
This information is based on an email exchange between a Linux Skype user and Skype's customer service?
So some dude from customer service has the inside scoop from Skype developers and he's talking left and right about it while Skype developers remain silent on one of the most popular moves that they could do?

Real reliable source there.
You missed the [confirmation on skype.com](http://share.skype.com/sites/linux/2009/11/skype_open_source.html).

---

### Post by Zoot7 on 2009-11-02
I've always really disliked the linux version of skype. It never worked for me behind the proxy I'm sitting behind, audio and picture was always very jittery. As much as I hate doing it, I have to boot into Windows these days for Video calls on skype. :(

Anything that has the potential to make skype better on Linux in general has my vote. :)

---

### Post by virusiidx on 2009-11-02
> **zekopeko said:**
> 
Real reliable source there.

[http://share.skype.com/sites/linux/2009/11/skype_open_source.html](http://share.skype.com/sites/linux/2009/11/skype_open_source.html) ?

Edit: beat me to it.

---

### Post by zekopeko on 2009-11-02
> **Flimm said:**
> You missed the [confirmation on skype.com](http://share.skype.com/sites/linux/2009/11/skype_open_source.html).

The OP should link to that then (now that is). Not some random dude on the internet.

---

### Post by Keyper7 on 2009-11-02
> **zekopeko said:**
> So some dude from customer service has the inside scoop from Skype developers and he's talking left and right about it while Skype developers remain silent on one of the most popular moves that they could do?

Are you seriously saying that silence from Skype developers about the Linux client is something you wouldn't expect? :)

---

### Post by phrostbyte on 2009-11-02
They are just open sourcing a small part of it. Don't get too excited. :D

---

### Post by KIAaze on 2009-11-02
This move will reduce the motivations to create FOSS alternatives to Skype and thereby make their current quasi-monopoly even safer. :(

+ the protocol is still closed. (imagine TCP/IP being a closed protocol)

Interestingly, they can't even completely open source it apparently, because they don't "own its core P2P technology" and "don’t even have access to the source code"!
cf: [http://www.techcrunch.com/2009/09/18/new-lawsuit-brings-clarity-to-skypes-ip-problem/](http://www.techcrunch.com/2009/09/18/new-lawsuit-brings-clarity-to-skypes-ip-problem/)
[http://ofaurax.free.fr/blog/index.php5/2009-11-03-00h40-0100.xml](http://ofaurax.free.fr/blog/index.php5/2009-11-03-00h40-0100.xml)

Another interesting bit:
>  Skype's EULA grants Skype the use of the system on which it is installed. Article 4 of the Skype end user license agreement states, "You hereby acknowledge that the Skype Software may utilize the processor and bandwidth of the computer (or other applicable device) You are utilizing, for the limited purpose of facilitating the communication between Skype Software users." Enough said.

[http://searchsecurity.techtarget.com/tip/0,289483,sid14_gci1188174,00.html](http://searchsecurity.techtarget.com/tip/0,289483,sid14_gci1188174,00.html)

P.S.: Has anybody found a good alternative to Skype (allowing audio, video, PC-to-phone, encrypted, Windows client, GNU/Linux client, free client + free PC-to-PC communication)?
Does QuteCom work well?
I had a look at [this list]("http://en.wikipedia.org/wiki/Comparison_of_VoIP_software"), but haven't had a chance to try out some of them.
Personnally, I wouldn't have any problems just using text-based chat, but that's not the case of my family. :/

---

### Post by Keyper7 on 2009-11-02
> **KIAaze said:**
> "You hereby acknowledge that the Skype Software may utilize the processor and bandwidth of the computer (or other applicable device) You are utilizing, **for the limited purpose of facilitating the communication between Skype Software users**."

What's the problem with that? You *need* processor and bandwidth for such communication.

---

### Post by KIAaze on 2009-11-02
> Elves from the magical kingdom transporting the data with pink unicorns and showing video in the air, on a screen made of magical dust?
Yes! :lolflag:

Ok, I may have extrapolated too much (just like the article). ^^'
But it's interesting. I wonder if it means that communications between other skype users also go through my PC if it makes them go faster. (which would be strange since it means going from the ISP to me and back)

edit: :( You edited your sarcastic message. I kept a trace of it for historic purpose. :P

---

### Post by dragos240 on 2009-11-02
What liscense will it be under?

---

### Post by Keyper7 on 2009-11-02
> **KIAaze said:**
> Ok, I may have extrapolated too much (just like the article). ^^'
But it's interesting. I wonder if it means that communications between other skype users also go through my PC if it makes them go faster. (which would be strange since it means going from the ISP to me and back)

Yes, it sounds way too much overhead for a real-time application like Skype. But I now understand better what you meant. When I read your quote I was like "Wait... he does NOT want the communication to be facilitated?" ;)

> **KIAaze said:**
> edit: :( You edited your sarcastic message. I kept a trace of it for historic purpose. :P

My greatest concern was offending you unintentionally. Since that didn't happen, I won't try to hide the past. :)

---

### Post by Foster Grant on 2009-11-02
> **szymon_g said:**
> [http://ofaurax.free.fr/blog/index.php5/2009-10-31-00h31-0100.xml](http://ofaurax.free.fr/blog/index.php5/2009-10-31-00h31-0100.xml)

nice :)

Blah. The driver won't be GPL'd, only the OS-specific shell. The driver will still be a closed-source binary blob.

And it's still [full of security holes](http://www.theregister.co.uk/2008/07/25/skype_backdoor_rumours/).

---

### Post by Foster Grant on 2009-11-02
> **KIAaze said:**
> This move will reduce the motivations to create FOSS alternatives to Skype and thereby make their current quasi-monopoly even safer. :(

+ the protocol is still closed. (imagine TCP/IP being a closed protocol)

Interestingly, they can't even completely open source it apparently, because they don't "own its core P2P technology" and "don’t even have access to the source code"!
cf: [http://www.techcrunch.com/2009/09/18/new-lawsuit-brings-clarity-to-skypes-ip-problem/](http://www.techcrunch.com/2009/09/18/new-lawsuit-brings-clarity-to-skypes-ip-problem/)
[http://ofaurax.free.fr/blog/index.php5/2009-11-03-00h40-0100.xml](http://ofaurax.free.fr/blog/index.php5/2009-11-03-00h40-0100.xml)

Another interesting bit:

[http://searchsecurity.techtarget.com/tip/0,289483,sid14_gci1188174,00.html](http://searchsecurity.techtarget.com/tip/0,289483,sid14_gci1188174,00.html)

P.S.: Has anybody found a good alternative to Skype (allowing audio, video, PC-to-phone, encrypted, Windows client, GNU/Linux client, free client + free PC-to-PC communication)?
Does QuteCom work well?
I had a look at [this list]("http://en.wikipedia.org/wiki/Comparison_of_VoIP_software"), but haven't had a chance to try out some of them.
Personnally, I wouldn't have any problems just using text-based chat, but that's not the case of my family. :/


Some other interesting bits: [http://www.theregister.co.uk/2008/07/25/skype_backdoor_rumours/](http://www.theregister.co.uk/2008/07/25/skype_backdoor_rumours/) and [http://wikileaks.org/wiki/Skype_and_SSL_Interception_letters_-_Bavaria_-_Digitask](http://wikileaks.org/wiki/Skype_and_SSL_Interception_letters_-_Bavaria_-_Digitask)

Thanks but no thanks.

---

### Post by doorknob60 on 2009-11-02
Yes, native 64 bit port :) That alone is enough to satisfy me, although using the 32 bit one works fine, it's always nice when companies open source their apps and/or release native 64 bit ports.

---

### Post by overdrank on 2009-11-02
Threads merged

---

### Post by bryncoles on 2009-11-03
[http://www.theregister.co.uk/2009/11/02/open_source_skype/](http://www.theregister.co.uk/2009/11/02/open_source_skype/)

> When Faurax asked for clarification of that assertion, customer-support minion "Joerg" affirmed the statement, saying: "Yes, indeed, the Linux Skype version will become open source in the nearest future."

Given the popularity of this software (especially amongst my international peers), this is exciting news!

---

### Post by P4man on 2009-11-03
Woohoo

[http://www.theinquirer.net/inquirer/news/1560804/skype-source-linux](http://www.theinquirer.net/inquirer/news/1560804/skype-source-linux)

Sorry if this is inappropriate here, not sure where else to post it, but Ive been bugging them since forever to open up skype so the community can make it work better on linux, so this makes me happy :) Skype finally understands their core business is providing services and not selling (free) software.

---

### Post by soni1770 on 2009-11-03
"Although Skype has confirmed that the user interface will go open sauce, customers expressed concerns in comments on the announcement that Skype's Internet protocol software might remain closed.

prob they have to keep it closed as all the people on windows etc would have to upgrade otherwise

---

### Post by P4man on 2009-11-03
Well I understand they want to keep their secret sauce secret. Its not with the internet protocol stack that we have problems, nor with the voice compression protocols. These work great, thats why we love Skype. We got problems with retarded GUIs (inability to do headless skype, integrate in other IMs, heck even send SMS,..), problems with the sound system interfacing (alsa, pulse,..). Opening up the GUI, assuming they take that far enough, and providing an API to a closed source binary is perfectly sensible IMHO and opens a lot of perspectives.

---

### Post by motang on 2009-11-04
[Here]("http://share.skype.com/sites/linux/2009/11/skype_open_source.html") is the official news. :guitar:

---

### Post by Soul-Sing on 2009-11-04
It would be great if Skype is going opensource. :popcorn:

---

### Post by Andreas1 on 2009-11-04
i don't care whether the client software is open source or not. what's really important is the protocol, and that is as proprietary as ever.

usually i am not so stallmanesque, but using proprietary protocols obviously forces others to do so as well, which is far more problematic in my opinion. that's why skype is truly evil.

this ought to be moved to the community discussion though...

---

### Post by 0cton on 2009-11-04
It is really irrelevant for me
First: there are already many voip open source applications out there.
Second: I really don't use skype that much, probably cause I am busy most of the time and also cause I have free voip telephony in USA (any mobile or broad line phone number )  and a bunch of countries in europe and many Telephone companies are doing this (especially in Europe free calls in many countries)
edit: also as many already mentioned the GUI is just a front-end it really doesn't make a difference if the GUI goes open-source or not <.<

---

### Post by Dougie187 on 2009-11-04
This is already posted in the community cafe.

---

### Post by aaaantoine on 2009-11-06
> **hessiess said:**
> This would ONLY be possible if the *ENTIRE* application was open source, if only the GUI will be open source, with everything else handled by some binary lib, it would not be possable to port it to ARM, or even x86_64.


Yes, I came to that realization immediately one post prior to yours. :P

---

### Post by areteichi on 2009-11-09
Apparently, Skype is releasing UI portion of its code to better cope with the diversity of Linux distributions and for a quicker and more efficient development. This certainly is a great news for many people!!! :KS
I already can't wait :-\"

> Yes, there's an open source version of Linux client being developed. This will be a part of larger offering, but we can't tell you much more about that right now. Having an open source UI will help us get adopted in the "multicultural" land of Linux distributions, as well as on other platforms and will speed up further development. We will update you once more details are available.

[http://share.skype.com/sites/linux/2009/11/skype_open_source.html](http://share.skype.com/sites/linux/2009/11/skype_open_source.html)
[http://linux.slashdot.org/story/09/11/02/1353245/Skype-For-Linux-To-Be-Open-Sourced-In-the-Nearest-Future](http://linux.slashdot.org/story/09/11/02/1353245/Skype-For-Linux-To-Be-Open-Sourced-In-the-Nearest-Future)

---

### Post by NoaHall on 2009-11-09
About 1 month too slow. ;)

---

### Post by RedSingularity on 2009-12-15
Has anyone heard any news on the open source skype project?

---

### Post by lukeiamyourfather on 2009-12-15
What open source Skype project? The protocols that Skype uses are proprietary and not documented. I've heard that Skype is making the interface open source in the future (not sure if that's true or not), but not the protocols. Cheers!

---

### Post by Physical Hook on 2009-12-15
Such things doesn't happen overnight ..

---

### Post by Exodist on 2009-12-15
> **lukeiamyourfather said:**
> What open source Skype project? The protocols that Skype uses are proprietary and not documented. I've heard that Skype is making the interface open source in the future (not sure if that's true or not), but not the protocols. Cheers!
Pretty sure that is what he meant.

---

