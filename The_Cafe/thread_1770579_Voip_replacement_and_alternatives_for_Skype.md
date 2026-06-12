---
title: "Voip replacement and alternatives for Skype"
date: 2011-05-29
forum: The Cafe
---

### Post by Willynux on 2011-05-29
I've been looking for a Skype alternative and since the announcement that Skype is now Microsoft I'm looking for an urgent replacement software. No luck until now to find something that is:
-Simple to use so that my mother can install it too
-Has more or less the same features (audio/video/chat/file transfer/desktop sharing)
-Is cross-platform (GNU/Linux, Mac OS, Windows)
-Is Free Software

(edit) The best way to do this seems to be with SIP addresses and SIP software clients. (Get a sip address here for example: iptel.org)

I have looked on the fsf website for Skype replacement:
[http://www.fsf.org/campaigns/priority-projects/#skypereplacement](http://www.fsf.org/campaigns/priority-projects/#skypereplacement)

(edit) And GNU projects for telephony:
[http://www.gnutelephony.org](http://www.gnutelephony.org)

And Wikipedia Voip comparison page:
[http://en.wikipedia.org/wiki/Comparison_of_VoIP_software](http://en.wikipedia.org/wiki/Comparison_of_VoIP_software)

The best software options until now seem to be[B]
-Jitsi [/B](Cross platform but not in Ubuntu repos yet)[B]
-QuteCom[/B][B]
-Ekiga[/B] (not available for Mac)
**-Blink** (Open Source but not gratis: 10-50$)

Has anyone had some experience with these software? Any other suggestion?
Please, any help on this is appreciated!!! (also participate if you are looking for this software, hopefully push the developers to create/improve Free Software alternatives)

---

### Post by ssam on 2011-05-29
the nice thing about SIP is that any client can talk to any other client. no need for everyone to use the same one. ekiga is probably the best one on linux.

the FSF/GNU are making progress: [http://planet.gnu.org/gnutelephony/?p=14](http://planet.gnu.org/gnutelephony/?p=14)

---

### Post by Bölvaður on 2011-05-29
one guy in first year of computer science recommended **Jitsi **after MS bought Skype.

---

### Post by Willynux on 2011-05-29
thanks for the link ssam and this essential piece of information that sip is independent from software.

I had trouble with Ekiga, it puts my icon green (suposedly available) but a message appears saying it could not register SIP:*me*@ekiga.net... Still have to spend time to understand SIP and Ekiga. Being free can be very time consuming! 
I'm waiting for this GNU free call to be released to use it ASAP

@[Bölvaður]("http://ubuntuforums.org/member.php?u=338535")
I will try to intall Jitsi but doesn't look so easy to do (no success until now)

---

### Post by Linuxratty on 2011-05-29
> **Willynux said:**
> thanks for the link ssam and this essential piece of information that sip is independent from software.

I had trouble with Ekiga, 

* Several of us at Linuxinternationals.org had problems with Ekiga as well, mostly related to volume control in group chats.
 I was only able to get it to work four times,after that it would not allow me to join any chats. 

* Me and another person using Empathy were presented with a red box and could go no further. Must be something we did not understand. 

* Have not used Jitsi,but it looks promising. Downloaded but not tested.

* Pidgin works.

* Everyone could use Team Viewer but me. It worked once and I was able to screen share with another Ubuntu user...After that every time I tried to use it, my desktop froze.

---

### Post by tgalati4 on 2011-05-29
Google voice with the chat/talk plug-in for gmail.  Works well under Chrome browser.  Need to sign up for a gmail account.  It's easy to install Chrome browser and easy to install the chat plug-in, but sometimes the plug-in requires some tweaking in the settings to see the audio and video hardware.  Once it is set up, it works well.  Does not have the send-file feature, but you can use gmail just as easily to send files.

---

### Post by Linuxratty on 2011-05-29
> **tgalati4 said:**
> Google voice with the chat/talk plug-in for gmail.  Works well under Chrome browser.  Need to sign up for a gmail account. .

  Our problem at LI.org is it's just for the USA and there is no screen sharing.

---

### Post by Macskeeball on 2011-05-29
> **Linuxratty said:**
> Our problem at LI.org is it's just for the USA and there is no screen sharing.

Google Voice is just for the USA. Google Talk is worldwide. Two different services.

---

### Post by Willynux on 2011-05-29
As much as I love Google I don't want to rely on it for all my personal stuff. I don't use gmail as webmail any more because I don't like the add appearing according to what I just typed... 

I will definitely try teamviewer although it's not free software and oriented to remote desktop control from what I read.

---

### Post by v41 on 2011-05-29
Skype also offers a paid service called skype-out which enables calls and text-messages to any telephone.  Do any of the alternatives to skype include this capability?

---

### Post by Ric_NYC on 2011-05-29
> **Macskeeball said:**
> Google Voice is just for the USA. Google Talk is worldwide. Two different services.

"[B]Cheap calls
[/B]Free calls & text messages to the U.S. & Canada.
Super low rates everywhere else."
(Google Voice)

---

### Post by Macskeeball on 2011-05-29
> **Ric_NYC said:**
> "[B]Cheap calls
[/B]Free calls & text messages to the U.S. & Canada.
Super low rates everywhere else."
(Google Voice)

Right. That's talking about people in the U.S. calling and texting people in other countries. It doesn't mean that Google Voice accounts are available outside the US, because they're not. [http://www.google.com/support/voice/bin/answer.py?hl=en&answer=115061](http://www.google.com/support/voice/bin/answer.py?hl=en&answer=115061)

[Google Talk](http://www.google.com/talk/), on the other hand, is something anyone can sign up for no matter where they are in the world.

---

### Post by beew on 2011-05-29
Tried this the other day, both sound and video quality are on par with Skype and no installation needed.
[URL="http://www.faceflow.com/"]
http://www.faceflow.com/[/URL]

---

### Post by XubuRoxMySox on 2011-05-30
Jajah.com is pretty cool for the phone call stuff. No software at all, just web stuff. Works with any browser.

-Robin

---

### Post by Willynux on 2011-05-30
> **v41 said:**
> Skype also offers a paid service called skype-out which enables calls and text-messages to any telephone.  Do any of the alternatives to skype include this capability?

Ekiga offers "Audio (and video) calls to landlines and cell phones with support to the cheapest service providers."
[http://ekiga.org/ekiga-softphone-features#voip_services](http://ekiga.org/ekiga-softphone-features#voip_services)

---

### Post by jefelex on 2011-05-31
I have problems with Ekiga - I don't like their install features, since it originally looked like I had to purchase a plan from some 3rd party (and I got duped into it) to use it.  I don't have any friends who use it - they continue to use Skype (who I also have an account with) 

They have a very poor support page (ekiga)  Also, I have uninstalled ekiga, and the problem I have is that it still thinks it's there, since right now as I type, it is still downloading something from ekiga.net, and I have yet to figure out why!!  I've been racking my brains with netstat, ifconfig, iptables, etc to find out where all that data is going, but no luck yet.  I don't like it, and I may not reinstall it even if and when I figure out what is going on.  It tests okay and everything, just not anywhere enough documentation to make me feel that I can use it without concerns.

my 2 cents!

John

---

### Post by Matiss.Jekabsons on 2011-06-01
I am also searching for good VoIP Softphone.
But like i see... there is NO Linux Softphone with capability of autorecord af outgoing call. Thats a reeeeaaaalll pain in the *** :( Ore mabey someone knows a right Softphone with that function?

---

### Post by Alpinist on 2011-06-12
Thanks for mention of Jitsi.  So far it is the only application I've found that is a complete feature replacement for Skype.

If you want software to call telephones or to allow telephones to call you then what you want is SIP Software and a SIP service provider.  There are a handful of software packages and a couple of dozen service providers available.

On the other hand if what you want is software for computer to computer communication for free internet chat (text, voice, video) then your best bet is to use xmpp software and services.  Google Talk is an xmpp service but I might recommend Jabber as a more free and open provider.  There are several others, in fact you can pop up your own xmpp server.  The nice thing is that you can add people to your Buddy list across services, you can add Google Talk friends to your Jabber account.

Jitsi is the only software I know of off hand that will connect to both all your SIP accounts and all your chat accounts at the same time.   Also it is the only one I know of that you can host multi user audio conferences.

You could do a pseudo audio conference with chat software like Pidgin or Empathy by having each person open up a one on one audio chat with every other person but that would be awkward and inconvenient.

Also Jitsi will let you encrypt computer to computer chats but I haven't tried that feature at all.  I find both the Audio and Video quality of xmpp software to be superior to Skype.

---

### Post by Matiss.Jekabsons on 2011-06-13
SFL Phone latest RC ir full enterprise VoIP Softphone with capability of auto record.

---

### Post by Random_Dude on 2011-06-13
I didn't know that skype was bought by microsoft.
Are there any announcements about the continuity of the Linux version?

---

### Post by Dry Lips on 2011-06-13
> **Random_Dude said:**
> I didn't know that skype was bought by microsoft.
Are there any announcements about the continuity of the Linux version?

We've already had a looooong thread about this. Check out:
[http://ubuntuforums.org/showthread.php?t=1754414](http://ubuntuforums.org/showthread.php?t=1754414)

---

### Post by Random_Dude on 2011-06-13
> **Dry Lips said:**
> We've already had a looooong thread about this. Check out:
[http://ubuntuforums.org/showthread.php?t=1754414](http://ubuntuforums.org/showthread.php?t=1754414)

Thanks. ;)
I don't seem able to remember that thread, it's weird. I visit ubuntuforums quite often and that is the sort of stuff I would remember.

Cheers :cool:

---

### Post by Quadunit404 on 2011-06-13
I used to like [application] but ever since [company] bought it/took over its development, I have been looking for a replacement for [application]. Besides, I don't know if [company] will continue developing [application] for [OS] any further, as they support [other OS] and not [OS], so I am writing off [application] before the development status is really made public.

:roll:

---

### Post by SE7EN-LOCSTA on 2011-06-13
well said quadunit.

---

### Post by Quadunit404 on 2011-06-13
> **SE7EN-LOCSTA said:**
> well said quadunit.

Do I win something? :D

---

### Post by Spice Weasel on 2011-06-13
> **Quadunit404 said:**
> Do I win something? :D

Yes. A certificate.

[IMG]http://i.imgur.com/u6hHL.jpg[/IMG]

It's signed by Neptune, which is kind of cool I guess.

This IWontUseItBecauseMicrosoftTouchedIt™ stuff is getting ridiculous. Skype is not going anywhere.

---

### Post by Quadunit404 on 2011-06-13
I wonder what will happen if Microsoft and Canonical engage in some sort of agreement...

:wink:

---

### Post by beew on 2011-06-13
> **Quadunit404 said:**
> I used to like [application] but ever since [company] bought it/took over its development, I have been looking for a replacement for [application]. Besides, I don't know if [company] will continue developing [application] for [OS] any further, as they support [other OS] and not [OS], so I am writing off [application] before the development status is really made public.

:roll:

It is quite rational to look for alternatives just in case. Well if MS is good on its words (or its words based on the most optimistic interpretation) then it is all fine and dandy and most Linux users will probably still use Skype. 

In any case, it is always good to have choices and alternatives. Whatever MS is going to do it highlights the vulnerability of Linux users on the VOIP front if we have to rely so much on the good will of one company. What is wrong for saying that we shouldn't put all the eggs in one basket? Are you saying that the community shouldn't develop and search for alternatives until after the axe is dropped? That would be quite late.

---

### Post by Alpinist on 2011-06-13
> **Spice Weasel said:**
> 
This IWontUseItBecauseMicrosoftTouchedIt™ stuff is getting ridiculous. Skype is not going anywhere.

Certainly Skype isn't going to change in the next couple of months.  But it is also true that the Linux version of Skype was already not nearly as well developed as the Windows version, always lagging behind and it is reasonable to think that it will lag further behind with the change in ownership.

And even if nothing happens to the service at all, it never hurts to look at your options.

For calling phones, if you live in the U.S. you can get Google voice for free with free calling to US and Canada and cheaper than Skype calling elsewhere, also a free incoming number with considerable more options in voicemail and other settings than Skype allows.  Also Google Voice does texting both in and out and doesn't charge you for it.

If you don't live in the US, or your don't trust Google, or you want a paid service that will give you tech support, you can get SIP softphone software and a SIP provider with plans cheaper than Skype or with more features.  So not only are there alternatives to Skype but the alternatives are BETTER.

Also for free chatting over the Internet, I have been recently trying xmpp services (Google Talk and Jabber - there are others) and both the Audio and Video quality are noticeably superior to Skype.

For gaming Skype is possibly the worst solution you can use for Audio chatting with your friends during a game.  It uses more bandwidth and system resources than pretty much any other chat software I have tried, it very distinctly will slow down your games.

Probably the best chat software for gaming is Mumble with it's low latency but xmpp chatting with the convenience of the IM style buddy list and seeing when people are online and the ease of connecting up is a good compromise between Mumble and Skype.  (just get a Google Talk or Jabber account)

---

### Post by Quadunit404 on 2011-06-13
> **Alpinist said:**
> For gaming Skype is possibly the worst solution you can use for Audio chatting with your friends during a game.  It uses more bandwidth and system resources than pretty much any other chat software I have tried, it very distinctly will slow down your games.

Huh, never noticed this before, and I've played a LOT of games online with Skype voice chat active.

I've played Portal 2 co-op with Skype open, voice chat active, and saw no lag whatsoever. I've played Team Fortress 2 under the same conditions and no lag. Minecraft; no lag (any lag was due to the host, not me.) I do understand that what I just said might not be true for everybody, but for me it is.

---

### Post by Alpinist on 2011-06-13
> **Quadunit404 said:**
> Huh, never noticed this before, and I've played a LOT of games online with Skype voice chat active.

I've played Portal 2 co-op with Skype open, voice chat active, and saw no lag whatsoever. I've played Team Fortress 2 under the same conditions and no lag. Minecraft; no lag (any lag was due to the host, not me.) I do understand that what I just said might not be true for everybody, but for me it is.

Probably your system is powerful enough that the effect Skype has on your games is too small to care about. But Skype IS slowing down your games a little.  I'll bet if you could really objectively measure fps with Skype and without  (Clean boot with Skype never started) that it would show up, though probably not worth worrying about on your system.

I will admit it depends on the game and the quality of the computer hardware but I have seem Skype noticeably slow down games (sometimes even make them unplayable) and have had several people I know report the same thing. Also using Skype as a game chat much more often there are break ups and sometimes even dropped calls because of bandwidth conflicts than other chat software.

Again Mumble is the best software for game chatting but if you have enough bandwidth and system resources that Skype isn't a problem then go ahead and continue to use it, though the alternatives are less of a drain and may be even better for your friends that don't have as powerful machines or good of Internet providers as you do.

---

### Post by Quadunit404 on 2011-06-14
[The first seven minutes of this video has communication through Skype]("http://www.youtube.com/watch?v=FK9n377JZn4") (along with irl friends of mine other than the person I was playing Portal 2 with) and the remainder is through Steam's chat system. Tell me, can you see any lag in that video when Skype was being used? Because other than the obligatory frame rate lag that comes with recording via Fraps, I don't see any.

No, you don't have to watch all 46 minutes of that video.

---

### Post by manoka on 2012-01-14
> **Alpinist said:**
> ...

For calling phones, ...

If you don't live in the US, or your don't trust Google, or you want a paid service that will give you tech support, you can get SIP softphone software and a SIP provider with plans cheaper than Skype or with more features.  So not only are there alternatives to Skype but the alternatives are BETTER.

...

So, e.g. for international phone calls from Portugal, would Jitsi be at least equal to Skype as far as audio quality and simplicity of use go?

Any recommendations for VoIP software and SIP providers would be highly appreciated!

---

### Post by imachavel on 2012-01-14
why don't you just install glx gears then bench mark your fps? it works great with linux idk with windows. You can bench mark your desktop fps while running a game, while not running a game, while running a game with skype also working at the same time. Also, if you are going to skype, it'd be smarter wouldn't it not to play games at the same time right??

---

### Post by HermanAB on 2012-01-14
As far as SIP VoIP goes, give Ekiga a try - it is as good/bad as any and it is in the repos.  You would probably have to open some ports in your router for it - read the Ekiga Wiki for that.

---

### Post by Fíona on 2012-02-02
I recently looked at using Skype for making calls to landlines in other countries (europe). The rates are very attractive compared with my phone company. 
An update to the linux version of skype was well overdue before microsoft bought skype and I really don't expect an update anytime soon from microsoft.

Skype worked well for me in the past but looking at the skype forum I wondered just how secure skype is, many stories on hacked accounts, stolen credit and strange internet traffic to eastern european ip's.
Skype looks to be anything but secure and the resonspe from skype to the concerns of customers are discouraging. 
For security reasons, I am looking for an alternative.

---

### Post by Willynux on 2012-02-02
I have switched to Ekiga, after a long time using skype. I have also subscribed to the landline calls (diamondcard.us) and I'm quite pleased with the service. The quality of the sound (national, international, land line, mobile...) is excellent and it is cheaper than skype (sometimes half the price or less depending on destination and carrier). 
I'm using Ekiga 3.3.2 on Ubuntu 12.04 alfa and they are both remarkably stable for an "unstable release".

The thing I had to understand though, is that it doesn't matter what software you use. All of them (Ekiga, Twinkle, Qutecom, Jitsy...) they all use a SIP protocol. With one SIP account (that looks like an e-mail address) you can switch from one software to another. Same thing for the credits you buy to call land-line phones, they do not depend on the software you use. If you don't like a software you can still use your credits with another if you want to. With diamondcard.us you don't even need a software, you can login their website and go to "call now", you inform your phone number and the destination phone number and they will call you and connect to your destination phone (I haven't tried that though).

---

### Post by treacl on 2012-04-21
I've installed Jitsi and am getting ready to try it out.

Can anyone provide a key for the various options in the "ZRTP Ninja" security popup? The options are indicated by cryptic abbreviations, and there isn't a perfect 1:1 correspondence between what's there and what is listed in the [ZRTP FAQ]("http://jitsi.org/index.php/Documentation/ZrtpFAQ") on Jitsi's web site. Also, there's no other documentation on Jitsi's web site, no Jitsi support forum, etc.

Any help much appreciated.

treacl

---

### Post by morgan141 on 2012-04-21
> **Alpinist said:**
> Probably your system is powerful enough that the effect Skype has on your games is too small to care about. But Skype IS slowing down your games a little.  I'll bet if you could really objectively measure fps with Skype and without  (Clean boot with Skype never started) that it would show up, though probably not worth worrying about on your system.

I will admit it depends on the game and the quality of the computer hardware but I have seem Skype noticeably slow down games (sometimes even make them unplayable) and have had several people I know report the same thing. Also using Skype as a game chat much more often there are break ups and sometimes even dropped calls because of bandwidth conflicts than other chat software.

Again Mumble is the best software for game chatting but if you have enough bandwidth and system resources that Skype isn't a problem then go ahead and continue to use it, though the alternatives are less of a drain and may be even better for your friends that don't have as powerful machines or good of Internet providers as you do.

That depends on the circumstances. For modern games, a system is usually bottlenecked by the GPU, not the CPU. There are exceptions to this, but in the majority of cases this is true. You can spot this quite simply by looking at GPU and CPU usage in game, and you should spot virtually of the GPU being used and a percentage of the CPU.

Skype clearly has no impact on the GPU. However, if the spare CPU power is sufficient to run skype, it'll have no impact on the game. To be honest, if your computer is capable of playing high end games, a high end game + skype should be absolutely no problem at all, especially on quad core CPUs where most games run on two threads.

edit: Wow I just noticed the time stamp on that post! Oops...

---

### Post by VanillaMozilla on 2012-05-08
> **Fíona said:**
> I recently looked at using Skype for making calls to landlines in other countries (europe). The rates are very attractive compared with my phone company.  ...I am looking for an alternative.
That's easy.  Twinkle or Jitsi should work fine, and you will find very attractive rates to telephones in most countries through DiamondCard.*  Ekiga is very attractive, but in the past it was not trouble-free.  I've used Twinkle for some years, and it has been very reliable.  You need to adjust the microphone level with the Sound Preferences gadget.  The last time I looked at Jitsi it looked excellent.

*(Naturally, SIP calls to computers are free.)  DiamondCard also offers attractive phone-to-phone rates and other services over the Internet.

---

### Post by VanillaMozilla on 2012-05-09
> **manoka said:**
> So, e.g. for international phone calls from Portugal, would Jitsi be at least equal to Skype as far as audio quality and simplicity of use go?
I think any of them would.  Which program probably doesn't make a lot of difference as long as they work.  The sound quality is usually good telephone quality as long as there is a good Internet connection.

Make sure you adjust the microphone volume, try to avoid a microphone in front of a speaker, and you'll be fine.

Some programs have had problems, such as connection problems, in the past.  They rely on an external server to make connections, and some of the servers were (are?) not the best.  You can easily test this with an Echo from the server.  If you have a problem, it's easy to change service or program or both.  The only part you might pay for (you would be risking a whole $10) is a VOIP-to-telephone account, and people have had very good service (and very cheap!) from either DiamondCard or Google.  SIP is the way to go.  Just go for it.

---

### Post by MZ250Supa5 on 2012-09-01
Trying Ekiga... but having HUGE problems, but I'm suspecting that I'm also having the usual problems with the still quite lousy implementation of pulse audio in Ubuntu as I'm having microphone problems with Skype too - I want to ditch Skype after reading about the rather dubious ethical issues and the fact that it's close source - never good in my book, and just yet another part of the creeping corporatisation of our societies.  The Ekiga documentation is bad, really bad, and obviously written by geeks, for geeks and just about unfathomable by mere mortals.  Plain language, step-by-step set-up guides are what are needed.  If anyone knows of such a simple, easy to follow set-up guide, I'd be interested to know about it :)

---

### Post by Primefalcon on 2012-12-11
I use google chat/voice myself, I used to use skype but since Microsoft got... it's just gotten a bit too resource intensive for my liking

---

### Post by monkeybrain2012 on 2012-12-11
Use flash?

There is also faceflow
[http://www.faceflow.com/](http://www.faceflow.com/)

---

### Post by monkeybrain2012 on 2012-12-11
[https://jitsi.org/](https://jitsi.org/)

and here is a video presentation for jitsi.

[http://vimeo.com/36396972](http://vimeo.com/36396972)

---

### Post by Linuxratty on 2012-12-11
> **Macskeeball said:**
>  Talk is worldwide. Two different services.

 Gotcha..We set up a poker hangout in G+ and found out this is correct.
All 4 people  came in very well with only one person crashing due to her isp...
It was really nice that it switched the large screen image as each person spoke..Far better than Skype.
Google went all out here!

---

### Post by mJayk on 2012-12-12
> **Alpinist said:**
> Probably your system is powerful enough that the effect Skype has on your games is too small to care about. But Skype IS slowing down your games a little.  I'll bet if you could really objectively measure fps with Skype and without  (Clean boot with Skype never started) that it would show up, though probably not worth worrying about on your system.

I will admit it depends on the game and the quality of the computer hardware but I have seem Skype noticeably slow down games (sometimes even make them unplayable) and have had several people I know report the same thing. Also using Skype as a game chat much more often there are break ups and sometimes even dropped calls because of bandwidth conflicts than other chat software.

Again Mumble is the best software for game chatting but if you have enough bandwidth and system resources that Skype isn't a problem then go ahead and continue to use it, though the alternatives are less of a drain and may be even better for your friends that don't have as powerful machines or good of Internet providers as you do.

No offence but I really doubt Skype now slows down your computer more now Microsoft have bought it.

Of course programs like mumble, vent and TS are better for talking whilst gaming.  Its what they are built for.

---

### Post by Sebjectivist on 2012-12-15
> **monkeybrain2012 said:**
> [https://jitsi.org/](https://jitsi.org/)

and here is a video presentation for jitsi.

[http://vimeo.com/36396972](http://vimeo.com/36396972)

Nice, thanks. Finally something else then Twinkle for my Diamondcard account. Too bad it's still a bit of a hassle to [get the settings right]("http://wiki.diamondcard.us/podwiki?page=Jitsi").. 

Nice read if not already mentioned; [Free and Open Source alternatives to Skype VoIP]("http://idilix.net/foss-alternative-skype-replacement")

---

### Post by mr john on 2012-12-16
Actually Google and Microsoft are more trustworthy than many other software companies. And their software usually works very well if you use it right. Why? because they invest more resources into their software.

Everything you do online is tracked, so don't think avoiding those big companies is going to protect you in anyway. There are alot of worse smaller companies out there. Like zynga etc.

---

