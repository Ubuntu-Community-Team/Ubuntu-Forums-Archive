---
title: "Proposal: Replace Pidgin with Empathy by Ubuntu 9.04"
date: 2008-08-01
forum: Ubuntu Brainstorm
---

### Post by DPic on 2008-08-01
There has been a lot of positive talk about replacing pidgin with a client that uses Telepathy but now there's one that looks like it's almost ready to do that! I posted the idea on brainstorm [http://brainstorm.ubuntu.com/idea/11705/](http://brainstorm.ubuntu.com/idea/11705/)

**_*Update 2009.01.19:_** Vote here on the NEW brainstorm [http://brainstorm.ubuntu.com/idea/17102/](http://brainstorm.ubuntu.com/idea/17102/)*

Empathy ( [http://live.gnome.org/Empathy](http://live.gnome.org/Empathy) ) has much more potential than Pidgin since Empathy uses Telepathy ( [http://telepathy.freedesktop.org](http://telepathy.freedesktop.org) ). Although i don't think Empathy is quite ready for this in Intrepid, it certainly will be for the next release.

(If you'd like to give it a try, don't use the old version in the Hardy repos, look here: [http://cass.no-ip.com/~cassidy/blog/index.php/post/2008/04/14/Voice-and-video-c](http://cass.no-ip.com/~cassidy/blog/index.php/post/2008/04/14/Voice-and-video-c) alls-with-Empathy )

The fact that Empathy uses Telepathy to manage all the different protocols it supports is what makes it so great. Why is it that Pidgin supports file transfers on AIM but not Jabber? Why can't i use VoIP to talk to my Google Talk friends?

The bottom line is that Empathy has been making much more progress and improving much faster than Pidgin thanks to Telepathy and including it in Ubuntu will only help the process along!

[I]**_Update:_** Empathy works great now! File transfers now work and it picks up my webcam/mic! I think it's time to reconsider Empathy for inclusion. 
KEEP IN MIND that anyone who is not completely happy with Empathy can easily install Pidgin so there's nothing to lose! Including Empathy will just drive improvements faster[/I]

---

### Post by grossaffe on 2008-08-01
considering that pidgen stopped working for me over some dependency conflict, i'll have to check it out.

---

### Post by DPic on 2008-08-01
ah, wonderful pidgin. don't expect empathy to be bug-free, though! that's why it isn't ready yet, but by 9.04 everything major should be ironed out. Hopefully, you'll be able to see how Empathy has a big advantage over Pidgin once the remaining major bugs are taken care of

---

### Post by bp1509 on 2008-08-01
Empathy might as well be alpha software to me.  Mozilla's Instantbird is higher quality if for no other reason than Empathy (even the latest off svn) only supports 3 protocols, Jabber, Gtalk (if you can consider those seperate protocols), and some other thing i've never heard of.  Oh yeah MSN.. so make that 4.  No AIM, no yahoo, no irc.

---

### Post by loell on 2008-08-01
this is the result of not understanding what empathy really is, people now a days just look on screenshots and then :idea: wow!!

---

### Post by zachtib on 2008-08-01
> **bp1509 said:**
> Empathy might as well be alpha software to me.  Mozilla's Instantbird is higher quality if for no other reason than Empathy (even the latest off svn) only supports 3 protocols, Jabber, Gtalk (if you can consider those seperate protocols), and some other thing i've never heard of.  Oh yeah MSN.. so make that 4.  No AIM, no yahoo, no irc.

empathy can support everything that libpurple can, there's a wrapper for it

granted, native implementation is the way to go, but it's a temporary solution

---

### Post by Vadi on 2008-08-01
> **loell said:**
> this is the result of not understanding what empathy really is, people now a days just look on screenshots and then :idea: wow!!

qft

---

### Post by Polygon on 2008-08-02
1: empathy looks worse then pidgin. Other then that, it looks exactly the same, it just uses the native gtk theme and apart from a few things its exactly like pidgin

2. like stated above, no native implementations of some protocols. 

3. as stated on brainstorm, there are some licensing issues with it getting into gnome.

4. as stated on brainstorm, there is no documented api

5. pidgin is WAYYYYYYYYYYYY more popular

6. pidgin most likely has way more plugins and developer+plugin support then empathy (at the moment)

7. what isnt broke, don't fix it

8. pidgin is getting better msn support next release, which solves a lot of people's problems

9. pidgin has been hinting that they are getting close to releasing a version with audio/video support

10. why does telepathy make 'empathy show much more promise' then pidgin? i see no reason other then it uses dbus....which pidgin can as well...

---

### Post by bp1509 on 2008-08-02
Oh I wish Empathy was more top notch with more plugins and more protocols oh god how do I wish.  Either Empathy or Kopete or InstantBird, or anything for that matter.  I despise the pidgin devs.

They waste so much time coding trivial crap like how to take already existing features away and then refusing to change when the majority of their userbase gets mad at it.

They get aid from Google Summer of Code, and what do they squander it on? Finch.  We already have plenty of commandline chat programs, Finch was not needed in the least.  Other than maybe irssi, commandline chat apps are gimmicky anyways, no one seriously uses them on a regular basis.

But how many years have we been promised video support? How many years have we been promised Jingle integration?   

I think the pidgin devs are utter fail, and I can't wait for a true alternative.  But even so, Empathy's no replacement.  Not for a long time anyways.   I have more hope for InstantBird.

---

### Post by bp1509 on 2008-08-02
> **zachtib said:**
> empathy can support everything that libpurple can, there's a wrapper for it

granted, native implementation is the way to go, but it's a temporary solution

ya have a link that could show where to get the wrapper and how to make it work?

---

### Post by Polygon on 2008-08-02
they made a blog post saying that audio/video support is coming soon (as in they are working on it atm). We shall see

i dont like the pidgin devs any more then you but making a proposal to replace pidgin, which is still my favorite instant messaging program (even on windows) with another that looks like its still in alpha state, and has the problems that i already stated above.... maybe when ubuntu 9.04 rolls around i will re-evaluate but for now its not even close to surpassing pidgin in features/functionality.

i do wish however that adium had a linux port. THAT is a nice im program. and you have a submit button and can resize the text entry window!

---

### Post by Superkoop on 2008-08-02
Does Empathy support webcam with MSN? If not, IMO, there is no reason to replace pidgin.

---

### Post by bp1509 on 2008-08-02
> **Polygon said:**
> they made a blog post saying that audio/video support is coming soon (as in they are working on it atm). We shall see

i dont like the pidgin devs any more then you but making a proposal to replace pidgin, which is still my favorite instant messaging program (even on windows) with another that looks like its still in alpha state, and has the problems that i already stated above.... maybe when ubuntu 9.04 rolls around i will re-evaluate but for now its not even close to surpassing pidgin in features/functionality.

i do wish however that adium had a linux port. THAT is a nice im program. and you have a submit button and can resize the text entry window!
I agree with adium.  And don't get me wrong i wasn't arguing about pidgin being included now, it's our best option i was just complaining about the devs. ANd they've made plenty of blog posts about audio/video support for a long time.  I don't trust them.  They're too busy making crappy UI decisions to do anything useful.

---

### Post by Polygon on 2008-08-03
there already is a plugin to add back the enter button, and while i disagree with the text entry thing, its not THAT ba

however some of their ui decisions like removing the protocol icons in the buddy list are actually good ideas. of course they came from adium first =P

---

### Post by mrgnash on 2008-08-03
There is no need to manually resize the text entry area, period.

---

### Post by trash on 2008-08-03
> **Polygon said:**
> 1: empathy looks worse then pidgin. Other then that, it looks exactly the same, it just uses the native gtk theme and apart from a few things its exactly like pidgin

2. like stated above, no native implementations of some protocols. 

3. as stated on brainstorm, there are some licensing issues with it getting into gnome.

4. as stated on brainstorm, there is no documented api

5. pidgin is WAYYYYYYYYYYYY more popular

6. pidgin most likely has way more plugins and developer+plugin support then empathy (at the moment)

7. what isnt broke, don't fix it

8. pidgin is getting better msn support next release, which solves a lot of people's problems

9. pidgin has been hinting that they are getting close to releasing a version with audio/video support

10. why does telepathy make 'empathy show much more promise' then pidgin? i see no reason other then it uses dbus....which pidgin can as well...

wasn't pidgin just a name change from gaim and only so popular because it's installed and ready to use... it didn't look that much better and gaim-vv or whatever, was hinted at for a few years before it never happened. It's an ok app. but thats about it.

---

### Post by trash on 2008-08-03
> **Polygon said:**
> i do wish however that adium had a linux port. THAT is a nice im program. and you have a submit button and can resize the text entry window!

Now that would rock:)

---

### Post by Polygon on 2008-08-03
i think pidgin is more then 'an ok program', apart from the devs questionable ui decisions, it eliminated me  having to use several im clients at once. It is very simple and too the point, the interface is clean (albiet a bit too clean...aka submit button!) Ive tried several other clients including trillian and miranda (both multi protocol clients for windows) and i still come back to pidgin. Other ones like emensene are nice, but i need multi protocol support. i have not seen a program that even comes close to replacing pidgin. Empathy might, but it needs a lot of work to do.

---

### Post by crhylove on 2008-08-03
Pidgin is great.  It suffers from a few problems (what FOSS doesn't?), but gets me through the day in IM on:

AIM
MSN
ICQ
Y!
MySpace
gTalk
Jabber
IRC

And I only need one app.  I wish it did file transfer more reliably (and faster), had speex and did video, too (and submitted a brainstorm wish for it, too), but for basic IM, it is great!

If it's VOIP and video you are after, go vote:
[http://brainstorm.ubuntu.com/idea/11738/](http://brainstorm.ubuntu.com/idea/11738/)

---

### Post by Mateo on 2008-08-03
Empathy is far too complicated. I first installed it and found out that I could not log-on to anything.  so i had to go back into synaptic and search around trying to find some kind of aim plugin.  there wasn't one.  so i eventually guessed tht -core package would do it.  luckily i was right.  this is far too complex of a way to get a simple IM program.

---

### Post by gjoellee on 2008-08-03
what about AMSN? It looks pretty much like the original MSN and at least  find it much more user-friendi

---

### Post by Mateo on 2008-08-03
> **gjoellee said:**
> what about AMSN? It looks pretty much like the original MSN and at least  find it much more user-friendi

Your suggesting Ubuntu replace a multi-protocol (16 at my count) messaging client for one that supports only 1?

---

### Post by FuturePilot on 2008-08-10
Well, it looks as though it might make it into Intrepid. It's been officially accepted into Gnome.
Here's the discussion.
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-August/005070.html]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-August/005070.html")

---

### Post by Mr. Picklesworth on 2008-08-10
I should point a few things out before this debate gets disproportionate:

Most of the 'user friendliness' are with packaging, and with the version from Hardy (or *shudder* before Hardy). The Empathy we have incoming for 2.24 is great :)

Empathy is built around core GNOME and desktop Linux technologies like glib, dbus and GTK. It is not going with a one-size-fits-all methodology, which means that it fits much better into the Ubuntu experience.

MSN is not the centre of the universe. We don't have video / audio support for that yet, but there is for Google Talk (Jabber). More is not far off.

Empathy is bigger than an instant messaging client; it is a tool to manage People and to communicate with them without needing to think about protocol. Instead of stopping there (like Pidgin), this nice abstraction extends beyond what the user does and into the realm of other software on your system. That stuff is the joy of libempathy, although it is still incoming. We need Empathy to be comfortable, however, because this can be very big for desktop Linux. Look around at the Empathy developer's logs or the wiki page and you will hopefully see what I am on about.
Imagine wanting to play a computer game with a friend over the Internet. Instead of needing to share IP addresses and whatnot, you could look up that friend on your Empathy buddy list and *boom* it starts living. Same process whether it's local network, Internet, Bluetooth... anything with a messaging protocol. This could get interesting.

---

### Post by zachtib on 2008-08-10
> **bp1509 said:**
> ya have a link that could show where to get the wrapper and how to make it work?

I just apt-get installed it, and it supports most protocols.

I've got pidgin and empathy installed side-by-side.  I still use pidgin for my day-to-day chatting, but empathy supports voice in google talk, which pidgin does not.

---

### Post by Erunno on 2008-08-10
> **zachtib said:**
> empathy can support everything that libpurple can, there's a wrapper for it

granted, native implementation is the way to go, but it's a temporary solution

Why should all the work that went into libpurple be duplicated? Actually, it was a great move from the pidgin developers to move the functionality into an OS and DE independent library and allow other people to use it for their own purposes. Case in point: Adium, which uses libpurple and builds a very nice interface with Cocoa on top of it (and it integrates with Mac OS X system facilities nicely). Are there any grave design or license issues with libpurple that would warrant a rewrite of this core component?

---

### Post by Mr. Picklesworth on 2008-08-10
Okay, here's a nice blog post about what I was just babbling about:
[http://blogs.gnome.org/xclaesse/2008/04/21/announce-empathy-0231/](http://blogs.gnome.org/xclaesse/2008/04/21/announce-empathy-0231/)

---

### Post by BTMark on 2008-08-10
> **bp1509 said:**
> 

They get aid from Google Summer of Code, and what do they squander it on? Finch.  We already have plenty of commandline chat programs, Finch was not needed in the least.  Other than maybe irssi, commandline chat apps are gimmicky anyways, no one seriously uses them on a regular basis.


I use IrcII as my only IRC Application, so if I'm one of the only, that makes me pretty darn cool, right?


Pidgin is fine, and asking Ubuntu to entirely switch a software package they bundle to a piece of untested software that natively supports only four protocols? Just seems like the OP jumped the gun a little.

---

### Post by FuturePilot on 2008-08-10
> **Mr. Picklesworth said:**
> Okay, here's a nice blog post about what I was just babbling about:
[http://blogs.gnome.org/xclaesse/2008/04/21/announce-empathy-0231/](http://blogs.gnome.org/xclaesse/2008/04/21/announce-empathy-0231/)

Wow talk about desktop integration :D

---

### Post by smartboyathome on 2008-08-10
I installed Empathy on my Arch install, but it doesn't come with any protocols, so I can't really say I have an opinion of it. :(

---

### Post by zachtib on 2008-08-10
> **Erunno said:**
> Why should all the work that went into libpurple be duplicated? Actually, it was a great move from the pidgin developers to move the functionality into an OS and DE independent library and allow other people to use it for their own purposes. Case in point: Adium, which uses libpurple and builds a very nice interface with Cocoa on top of it (and it integrates with Mac OS X system facilities nicely). Are there any grave design or license issues with libpurple that would warrant a rewrite of this core component?

Well, there are some things that libpurple doesn't do (well), like voice and file transfer for Jabber/Gtalk

---

### Post by castrojo on 2008-08-10
> **BTMark said:**
> Pidgin is fine, and asking Ubuntu to entirely switch a software package they bundle to a piece of untested software that natively supports only four protocols? Just seems like the OP jumped the gun a little.

Empathy isn't "untested", the telepathy stack has been shipping on Nokia tablets for years and Empathy is based on Gossip, which was around for a very long time as well. 

It's not like Empathy just appeared overnight. :)

---

### Post by mysticmatrix on 2008-08-10
Well the blocker bug for me is that Empathy has no support for authenticated proxy. I primarily use a gmail jabber account, and would have been nice if could have used Empathy for voice chat.
[http://bugs.freedesktop.org/show_bug.cgi?id=16034](http://bugs.freedesktop.org/show_bug.cgi?id=16034)

---

### Post by Erunno on 2008-08-11
> **zachtib said:**
> Well, there are some things that libpurple doesn't do (well), like voice and file transfer for Jabber/Gtalk

Well, maybe it's just me but my first thought would be working with the libpurple maintainers to get the missing functionality in instead duplicating the parts which already do work.

---

### Post by Vadi on 2008-08-11
I checked out empathy from hardy-backports, and... I really hope that the 8.10 version is a lot, lot better if it'll be default in Ubuntu.

Just need to make 8.10 start first :(

---

### Post by loell on 2008-08-11
> **whiprush said:**
>  the telepathy stack has been shipping on Nokia tablets for years 

may i ask for the links ;) 

> **whiprush said:**
> 
and Empathy is based on Gossip, which was around for a very long time as well. 

It's not like Empathy just appeared overnight. :)

sure the SIP and jabber side of telepathy are solid, its the other closed and proprietary protocols is the problem, which makes libpurple the better choice as of this writing.

---

### Post by Vadi on 2008-08-11
Well, I gave it a try myself. I don't think it's *that much* better than Pidgin *yet*, and it has a number of usability issues:

[http://bugzilla.gnome.org/show_bug.cgi?id=547321](http://bugzilla.gnome.org/show_bug.cgi?id=547321)
[http://bugzilla.gnome.org/show_bug.cgi?id=547322](http://bugzilla.gnome.org/show_bug.cgi?id=547322)
[http://bugzilla.gnome.org/show_bug.cgi?id=547323](http://bugzilla.gnome.org/show_bug.cgi?id=547323)
[http://bugzilla.gnome.org/show_bug.cgi?id=547326](http://bugzilla.gnome.org/show_bug.cgi?id=547326)
[http://bugzilla.gnome.org/show_bug.cgi?id=547327](http://bugzilla.gnome.org/show_bug.cgi?id=547327)


I gave up after those bugs.

---

### Post by DPic on 2008-08-11
Hey, we included firefox 3 beta, we're including openoffice 3 beta, and many would argue that gvfs and pulse weren't solid. Think of this like Gstreamer-- [http://blog.ibeentoubuntu.com/2008/08/gnome-has-empathy-for-you.html](http://blog.ibeentoubuntu.com/2008/08/gnome-has-empathy-for-you.html)

Anyone who isn't trying the version of empathy with Intrepid shouldn't be complaining. Empathy has been getting better FAST-- and this will only make it faster. On the developer list, most people seem to be in support of this. Besides, the discussion right now is just whether or not to TEST intrepid with empathy. If we don't, we could be missing out on something really great. If it does make it into intrepid, i don't see any downside. Anyone who already uses pidgin can either switch to empathy and if they somehow don't like it, they can install pidgin. Newbies will be fine and happy with empathy and all of it's benefits.

---

### Post by b3n87 on 2008-08-11
There seems to be a lot of false information on this thread. Its intended to be included in 8.10, the next ubuntu release, its only just been accepted in GNOME due to documentation issues I believe. It also does everything that Pidgin does plus more.

Check "Current Features":

[http://live.gnome.org/Empathy]("http://live.gnome.org/Empathy")

---

### Post by loell on 2008-08-11
> **DPic said:**
> Hey, we included firefox 3 beta, we're including openoffice 3 beta, and many would argue that gvfs and pulse weren't solid. Think of this like Gstreamer-- [http://blog.ibeentoubuntu.com/2008/08/gnome-has-empathy-for-you.html](http://blog.ibeentoubuntu.com/2008/08/gnome-has-empathy-for-you.html) 

which actually gave problems when it shipped with ubuntu for the first time. 


> **DPic said:**
> 

Anyone who isn't trying the version of empathy with Intrepid shouldn't be complaining. Empathy has been getting better FAST-- and this will only make it faster. On the developer list, most people seem to be in support of this. Besides, the discussion right now is just whether or not to TEST intrepid with empathy. If we don't, we could be missing out on something really great. If it does make it into intrepid, i don't see any downside. Anyone who already uses pidgin can either switch to empathy and if they somehow don't like it, they can install pidgin. Newbies will be fine and happy with empathy and all of it's benefits.

its not plain complaining, its skepticism with openness to accept the inescapable change, there is no doubt that empathy is the way to go, i think the relevant question raise here is,.. **Isn't it too soon to make it the default**?

---

### Post by _oOMOo_ on 2008-08-12
> **b3n87 said:**
> It also does everything that Pidgin does plus more.

Check "Current Features":

[http://live.gnome.org/Empathy]("http://live.gnome.org/Empathy")

ORLY? It's certainly stronger than Pidgin in some areas but behind in others. Have you seen the preferences window? What about blocking users in msn? Still I like it and will keep using it alongside pidgin and amsn.

One thing that I DON'T like one bit is that it added itself to my default session so it launched on startup. Bad Empathy.

---

### Post by steeleyuk on 2008-08-12
> One thing that I DON'T like one bit is that it added itself to my default session so it launched on startup. Bad Empathy.

Is that the old version from the Hardy repo's because I'm using 2.23.6 and it doesn't do that.

> Have you seen the preferences window?

What's the problem with it?

---

### Post by _oOMOo_ on 2008-08-12
> **steeleyuk said:**
> Is that the old version from the Hardy repo's because I'm using 2.23.6 and it doesn't do that.

Yes I did install that first before adding the launchpad ppa. Glad it's been changed.

Re. preferences window:

> What's the problem with it?

There aren't any! Well not many.

---

### Post by steeleyuk on 2008-08-12
Thats the case with a lot of GNOME apps though. I'm sure more options will come as the frontend develops.

---

### Post by Mr. Picklesworth on 2008-08-12
> **_oOMOo_ said:**
> There aren't any! Well not many.Well, what is it you want to change?

Empathy will never have a huge number of options, because if someone wants to morph his client into something else he could just as easily install a different front-end. (When libempathy becomes libtelepathy, at least). The multi-layered design permits this quite nicely.

---

### Post by Vadi on 2008-08-12
Hm, sounds very nice. You want this feature? Install a different client! This one? Here, use this client.

Really defeats the purpose of a one multi-purpose client, heh.

---

### Post by helino on 2008-08-12
I think that Empathy shows a lot more potential than Pidgin, especially on the integration with GNOME. Give Empathy the time to mature until 9.04 by embracing it early, and we will have a really nice IM client.

The default programs in Ubuntu get changed all the time (BitTorrent -> Transmission) and I think it's time to change the IM client.

---

### Post by steeleyuk on 2008-08-12
Gnomebaker was never in Ubuntu. Though I agree about it showing more potential. Its certainly improved since I used it last on about 0.14. Back then it would crash at anything.

---

### Post by Speed Demon on 2008-08-22
100000% no. Empathy sucks. Keep pidgin or instantbird. Just my $0.02

---

### Post by b3n87 on 2008-08-23
> **Speed Demon said:**
> 100000% no. Empathy sucks. Keep pidgin or instantbird. Just my $0.02

Any chance you could expand on that? Why does it suck?

---

### Post by Vadi on 2008-08-23
See mtp's usability review. It's a much more expanded version of my several bugs that I found within 15 mins of using it.

[https://wiki.ubuntu.com/EmpathyVsPidginUsability](https://wiki.ubuntu.com/EmpathyVsPidginUsability)

In short, empathy isn't good enough to replace Pidgin, so no point. "Don't fix it if it isn't broken", and we had enough experiences with broken things.

---

### Post by AusIV4 on 2008-08-23
Does Empathy support Off-The-Record? I haven't been able to find anything to indicate that it does. It's a fairly widely used IM encryption system, and it's a must for my IM software.

Does Empathy have plugin support? Searching for "Empathy Plugins" yielded a lot of comparisons of Empathy and Pidgin, and it looked like all of them were talking about Pidgin's plugins. There are some things that will never be added into an instant messenger's core software that are nice additions via plugins. For example, my laptop has an LED that would, in windows, inform you that you had received an e-mail. I use a Pidgin plugin to turn that light on when I have a new IM.

There are a number of things I consider essential that I can't find for empathy. I may not be looking hard enough, but they don't seem to be there.

---

### Post by Mr. Picklesworth on 2008-08-23
> **Vadi said:**
> See mtp's usability review. It's a much more expanded version of my several bugs that I found within 15 mins of using it.

[https://wiki.ubuntu.com/EmpathyVsPidginUsability](https://wiki.ubuntu.com/EmpathyVsPidginUsability)

In short, empathy isn't good enough to replace Pidgin, so no point. "Don't fix it if it isn't broken", and we had enough experiences with broken things.

Please don't link to a usability review as if it's a definitive source of "why something is bad". Doing so is basically morphine a generous individual's constructive feedback into something destructive. That is material for development, identifying a bunch of bugs in need of fixing, preferably during Intrepid's development. Both the Empathy and the Pidgin developers are working on their bugs dilligently. The folks behind Empathy, of course, were very involved with this review and are being extremely responsive -- no doubt because Empathy is targetted specifically at the GNOME desktop. We will see who fixes their bugs first.

It needs to be pointed out, very clearly, that this is all fixable and is being fixed. It is no different from [this]("https://bugs.edge.launchpad.net/ubuntu").

It has been mentioned that Empathy could replace Ekiga for now, which I think is a reasonably compromise. (Although we need to make sure it has the right SIP functionality, just in case somebody actually uses Ekiga :P -- Kidding, kidding!).

While the core program does not have a plugin system exactly, one can tie software to it via a very deep dbus interface. What we need is a rapid dbus scripting GUI -- maybe a little nodes editor.

---

### Post by highlandsun on 2008-10-12
Well, after trying to use Empathy for a while and failing to get a clean connection to a SIP echo test server, I switched over to Ekiga, which works great. I also tried adding a few of my IM accounts to Empathy, and found that the whole UI just felt too primitive. So, back to Pidgin.

Personally I believe too much choice can be a bad thing, especially when the choices are not all functionally equivalent. Empathy is not a suitable replacement for any of the other apps it's aimed at replacing; the energy going into turning it into a stable app is mostly wasted effort IMO. Competition is stupid; it's what you do in a closed-source proprietary world because you have no other choice. Cooperation is the most efficient way forward, and it's the way Open Source is supposed to be done.

---

### Post by gnomeuser on 2008-10-13
> **_oOMOo_ said:**
> ORLY? It's certainly stronger than Pidgin in some areas but behind in others. Have you seen the preferences window? What about blocking users in msn? Still I like it and will keep using it alongside pidgin and amsn.

One thing that I DON'T like one bit is that it added itself to my default session so it launched on startup. Bad Empathy.

Clearly you haven't checked the empathy preferences.. you can actually turn that off..

---

### Post by ubulette on 2008-10-19
Some of you may be interested by [_this thread_]("http://ubuntuforums.org/showthread.php?p=5994576") as I saw Instantbird mentioned a few times here.

---

### Post by jaduncan on 2008-10-24
> **AusIV4 said:**
> Does Empathy support Off-The-Record? I haven't been able to find anything to indicate that it does. It's a fairly widely used IM encryption system, and it's a must for my IM software.

It does not, and it does not appear to be on the roadmap - I'd agree that it's quite important as I have slowly dragged people over to using it on Windows and Linux. There are network effects here, let's not give up on widely adopted encryption standards. It's also worth noting that Kopete are bringing in OTR for their 4.1.0 release, so it will be cross desktop.

---

### Post by danf_1979 on 2008-11-26
Am I blind or empathy just can't send files yet? Did someone said show stopper?

---

### Post by bruce89 on 2008-11-26
> **danf_1979 said:**
> Am I blind or empathy just can't send files yet? Did someone said show stopper?

[http://cass.no-ip.com/~cassidy/blog/index.php/post/2008/11/14/File-Transfer-in-Telepathy-and-Empathy](http://cass.no-ip.com/~cassidy/blog/index.php/post/2008/11/14/File-Transfer-in-Telepathy-and-Empathy)

---

### Post by DPic on 2009-01-09
> **bruce89 said:**
> [http://cass.no-ip.com/~cassidy/blog/index.php/post/2008/11/14/File-Transfer-in-Telepathy-and-Empathy](http://cass.no-ip.com/~cassidy/blog/index.php/post/2008/11/14/File-Transfer-in-Telepathy-and-Empathy)

Now everything i could ask for works in Empthy! I just tried the newest version and it looks much better-- I was waiting for this along with my webcam/mic to start working and now they all do! I think empathy is officially ready and should be reconsidered for inclusion. 

KEEP IN MIND anyone who is not completely satisfied with empathy can easily install pidgin. it doesn't need to be included by default

---

### Post by Mr. Picklesworth on 2009-01-09
> **DPic said:**
> KEEP IN MIND anyone who is not completely satisfied with empathy can easily install pidgin. it doesn't need to be included by default

It should be added that Empathy benefits from being shipped default more than Pidgin does, as well, to justify it to the non-believers. As mentioned, Telepathy's magic is in desktop integration; it's a central service for all things related to communicating with people. As applications start to adopt it, its power will become greater and people will start to say it has *more* options than Pidgin even though Empathy's Preferences dialog is far less crowded.

For that magic to happen, we need developers to see this as a legitimate option - begging to be linked to in the most popular distro - instead of a weighty dependency.

---

### Post by Vadi on 2009-01-09
Empathy is on it's way to take over. The Telepathy framework just makes sense - we need more smart apps like this. GStreamer already showed that frameworks are a great thing.

Just not there yet though.

---

### Post by DPic on 2009-01-11
I also started discussion back up on the ubuntu-desktop and ubuntu-devel-discuss lists: 
[https://lists.ubuntu.com/archives/ubuntu-desktop/2009-January/001898.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2009-January/001898.html)
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-January/006647.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-January/006647.html)

---

### Post by Neon Lights on 2009-01-11
I still have two issues with it.

1. It just shows people who are mobile as "available" with no indication that they are mobile.
2. It doesn't show idle times.

If someone's actually on the computer versus on their cell, I'm more likely to IM them, especially in the late hours. the second reason isn't a big thing, but it's still something that's nice to know.

---

### Post by DPic on 2009-01-12
> **Neon Lights said:**
> I still have two issues with it.

1. It just shows people who are mobile as "available" with no indication that they are mobile.
2. It doesn't show idle times.

If someone's actually on the computer versus on their cell, I'm more likely to IM them, especially in the late hours. the second reason isn't a big thing, but it's still something that's nice to know.

The first is already being worked on and i've submitted a new bug report for the second. 

Part of the reason to include empathy is how much it faster it will improve to really be a killer app to be included in the next LTS

---

### Post by loell on 2009-01-12
howdy dpic, I would just like to ask if empathy's xmpp is already fully compatible google talk's implementation? 

[http://lists.freedesktop.org/archives/telepathy/2008-May/001971.html]("http://lists.freedesktop.org/archives/telepathy/2008-May/001971.html")

---

### Post by DPic on 2009-01-15
> **loell said:**
> howdy dpic, I would just like to ask if empathy's xmpp is already fully compatible google talk's implementation? 

[http://lists.freedesktop.org/archives/telepathy/2008-May/001971.html]("http://lists.freedesktop.org/archives/telepathy/2008-May/001971.html")

I'm not sure what you mean by that...of course you can talk to Google talk users. XMPP is n open standard...

Also, you can vote for it on Ubuntu Brainstorm [http://brainstorm.ubuntu.com/idea/17102/](http://brainstorm.ubuntu.com/idea/17102/)

---

### Post by durand on 2009-01-15
I've been using it for a few hours and I have a few small problems with it:

* No support for custom smileys in MSN and jabber
* No easy access smiley button
* Truncation of nicknames is annoying
* No sound notifications! (very annoying)
* No grouping of multi-protocol contacts

I'll try to add these bugs to the bugtracker when I get the time. Apart from them, it's pretty nice and shows a lot of potential.

---

### Post by JSorrell on 2009-01-16
The only problem I have with it is the way it reports new messages. I'd like some system tray notification like Pidgin. The way I have my desktop set up, I can't really see when new messages come in unless there's a system tray notifier or toaster-like popups in pidgin via guifications. The dock icon jumps once, but it's so easy to miss.

---

### Post by tgpraveen on 2009-01-16
>  	
Re: Proposal: Replace Pidgin with Empathy by Ubuntu 9.04
The only problem I have with it is the way it reports new messages. I'd like some system tray notification like Pidgin. The way I have my desktop set up, I can't really see when new messages come in unless there's a system tray notifier or toaster-like popups in pidgin via guifications. The dock icon jumps once, but it's so easy to miss. 

good looking and functional notifications is a hot new feature in 9.04 and hopefully empathy will be supported so ur problems are gone.

>  	
Re: Proposal: Replace Pidgin with Empathy by Ubuntu 9.04
I've been using it for a few hours and I have a few small problems with it:

* No support for custom smileys in MSN and jabber
* No easy access smiley button
* Truncation of nicknames is annoying
* No sound notifications! (very annoying)
* No grouping of multi-protocol contacts

I'll try to add these bugs to the bugtracker when I get the time. Apart from them, it's pretty nice and shows a lot of potential. 


i am guessing that u used the empathy from the 8.10 repository.
as the latest version has many of your problems covered for eg sound notifications are a feature in the 2.25 gnome version so in 9.04 ubuntu you will be happier also a lot of work is being done on the ui.

---

### Post by Vadi on 2009-01-16
Empathy people have a PPA available here: [https://launchpad.net/~telepathy/+archive](https://launchpad.net/~telepathy/+archive)

It's preferred to use that since some of the bugs might be fixed and you'll be wasting time reporting them.

---

### Post by Mr. Picklesworth on 2009-01-16
Someone is working on a patch to add libnotify bubbles for new messages As We Speak. (There's a feature request filed in the bug tracker). Indeed, the current approach is quite ugly...

---

### Post by durand on 2009-01-16
> **tgpraveen said:**
> good looking and functional notifications is a hot new feature in 9.04 and hopefully empathy will be supported so ur problems are gone.




i am guessing that u used the empathy from the 8.10 repository.
as the latest version has many of your problems covered for eg sound notifications are a feature in the 2.25 gnome version so in 9.04 ubuntu you will be happier also a lot of work is being done on the ui.

Actually, I'm using 9.04 and I don't have that feature. I'll try the PPA. Thanks.

EDIT: The PPA doesn't have a jaunty version...

---

### Post by smartboyathome on 2009-01-16
> **durand said:**
> Actually, I'm using 9.04 and I don't have that feature. I'll try the PPA. Thanks.

EDIT: The PPA doesn't have a jaunty version...

Use the intrepid version, it will work.

---

### Post by durand on 2009-01-16
Just did that. For some reason, it's still using jaunty's version. Probably because it's newer..

---

### Post by DPic on 2009-01-19
Here it is on the new ubuntu brainstorm [http://brainstorm.ubuntu.com/idea/17102/](http://brainstorm.ubuntu.com/idea/17102/)

---

### Post by durand on 2009-01-19
Empathy supports screen sharing? Would that be between two users of the same protocol or two empathy users of the same protocol?

---

### Post by tgpraveen on 2009-01-20
no empathy does not support screen sharing nor is it in the current roadmap.

probably further down the road using the telepathy framework a elegant soplution to screen sharing can be done.

---

### Post by tgpraveen on 2009-01-20
no empathy does not support screen sharing nor is it in the current roadmap.

probably further down the road using the telepathy framework a elegant soplution to screen sharing can be done.

---

### Post by durand on 2009-01-20
> **DPic said:**
> Here it is on the new ubuntu brainstorm [http://brainstorm.ubuntu.com/idea/17102/](http://brainstorm.ubuntu.com/idea/17102/)

Umm, so it is just theoretical that we could use empathy for screen sharing in the future..

I'm still not sure how to get sound support in empathy. Should I just compile from svn? Neither Jaunty's repos nor the PPA have been updated in the past week.. Or maybe it's just me.

---

### Post by Mr. Picklesworth on 2009-01-26
Here's a goodie for you folks! Collaborative editing in Abiword achieved smoothly with Tubes. (And a reminder about how awesomely flexible that application is, UI-wise... and how unappreciated Sugar's awesome collaborative interface is).

Not the best screencast; you'll have to use your imagination for the "over the Internet" part, but it definitely is there.

[http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/01/24/Desktop-integration-of-the-Abiword-collaboration](http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/01/24/Desktop-integration-of-the-Abiword-collaboration)

This brings Abiword beyond feature parity with OpenOffice Writer with about a sixteenth the load time :b

Meanwhile, we also have [this]("http://ubuntuforums.org/showpost.php?p=6619983&postcount=18"). In a short while, the Linux desktop's collaboration related functionality will obliterate any competition on that space.

Err, and thankfully it looks like that's happening; doesn't seem many people are too concerned about swapping Pidgin and Empathy when GNOME starts shipping it.

---

### Post by durand on 2009-01-26
> **durand said:**
> Umm, so it is just theoretical that we could use empathy for screen sharing in the future..

I'm still not sure how to get sound support in empathy. Should I just compile from svn? Neither Jaunty's repos nor the PPA have been updated in the past week.. Or maybe it's just me.

BTW, still holding onto empathy. Sound support has apparently been added but it doesn't work at all and I don't get any errors. I also cannot change the sound files that it uses but this is sort of a pointless complaint next to it not working at all. Any ideas?

---

### Post by bruce89 on 2009-01-26
> **durand said:**
> BTW, still holding onto empathy. Sound support has apparently been added but it doesn't work at all and I don't get any errors. I also cannot change the sound files that it uses but this is sort of a pointless complaint next to it not working at all. Any ideas?

I think the default "Ubuntu" sound theme hasn't got the necessary sounds in it.

---

### Post by sroland81 on 2009-01-29
I agree as many people arround that Pidgin sucks sometiems. But... I use GNOME so i wont install Kopete or whatever... I don't like the artwork and overall aspect of aMSN... it's too MSN clone... and Pidgin... the little bird... i think it's light and not bloated like aMSN... it's a nice GTK app very well integrated with the GNOME Desktop. It's easy to use and the artwork is simple but really nice! I tried Empathy for a couple of days but here is what i think: Empathy doesn't play any sound when somebody writes to me in MSN chat. Empathy doesn't check for my hotmail accounts and have a direct click option to open hotmail inbox in a snap. So, i admit it, Pidgin doesn't handles MSN connections very well, it's always disconnecting and i'm always Retrying the connections... BUT when i tried Empathy, it was the same story!! i read so much about empathy replacing Pidgin... but developers really need to try to make a better software than Pidgin and if that happens, i want to see it. Pidgin has plugins that empathy doesn't and it has more configuration options than empathy... both i tried and installed from the Intrepid repos and ... i stay with Pidgin for now... and for the Pidgin developers... Pidgin is a nice piece of software that needs some adjustments in handling MSN connections and i think that Skype protocol would be very nice... may be just for text chat only. ... and for Empathy developers, i understand the telepathy framework thing.... but make it nice, configurable, with nice icons, sounds and tray notifications... the version i tried didn't have any... and as always... the faster, the better... hahahaha!

PD: what of all things that i just complained about are already fixed or improved in the newest version of Empathy? i used the intrepid repos...

Ubuntu saved my life.

---

### Post by Redache on 2009-01-29
It doesn't seem that different to Pidgin in terms of functionality although Voice support is nice. 

If it can be integrated well into ubuntu I think it'll take over from Pidgin quite well.

---

### Post by bruce89 on 2009-01-29
I'm going to try to respond to a huge block paragraph. Please don't write like this.

> **sroland81 said:**
> Empathy doesn't play any sound when somebody writes to me in MSN chat.

The latest unstable version of Empathy does.

> **sroland81 said:**
> Pidgin has plugins that empathy doesn't and it has more configuration options than empathy

I suppose a plugin system could be added to Empathy (not much point as there is libempathy), and the lack of configuration is a good thing for GNOME.

> **Redache said:**
> If it can be integrated well into ubuntu I think it'll take over from Pidgin quite well.

Well, the fact is that Empathy is split into a library, which means that GNOME programs could implement parts of IM into them (think Evolution, nautilus-sendto etc.).

---

