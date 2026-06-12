---
title: "Netflix on Chrome/Chromium/OS"
date: 2011-08-28
forum: The Cafe
---

### Post by Mars11 on 2011-08-28
You can catch up on our efforts [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1754594") and [[COLOR="blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1821942&page=4"). This will be the continuation of the first thread since it became locked. But for those of you who don't want to go back and read it all here's a summary: 

We extracted the Netflix Plugin from a Chromebook and have attempted to get it working in Chrome/Chromium (Browser), but get error: ```
Netflix Video Player Unavailable
Error Code: NPL3

Our apologies - we cannot find the Netflix Video Player on your Chromebook.

If this problem persists, please update you Chromebook from the "About Chrome OS" menu.
```
When we try it in Chromium OS we get this error: ```
Developer Mode Unsupported
Error Code: NPL15925257

Please ensure you are not running your Chromebook in Developer Mode.

If the problem persists, please call Netflix Customer Support at 1-866-716-0414.
```
We are still working on it and that is what this thread will be for.

---

### Post by user1397 on 2011-08-28
I'm just gonna say that it's awesome how you all are working on this!  We all appreciate it, and if there's anything I can do to help (testing comes to mind) let me know!

---

### Post by PC_load_letter on 2011-08-28
> **Mars11 said:**
> You can catch up on our efforts [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1754594") and [[COLOR="blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1821942&page=4"). This will be the continuation of the first thread since it became locked.

That was a shocker to me this morning. I was always checking on that thread to see your progress guys. I think you should complain for the reason it got locked (off-topic). How is that possible in the Community Cafe? I'm now doubting some of the moderators here can read English. 

As per the question in the poll, I voted "No". I'm not optimistic as it seems to me the culprit here is Netflix as they are unwilling to make anything run on Linux. I heard that they are in the process of encoding all their videos using HTML5 (or H264 I guess), maybe then someone will figure out a way to make it run on Linux.

---

### Post by Mars11 on 2011-08-29
At first I was a bit surprised, but I don't really care, this way it gives me more control over the thread.

---

### Post by cheat117 on 2011-09-27
Where was the Netflix plugin located inside your chromebook? maybe me must emulate the location (i.e. /usr/bin/chromeOS/netflixvideo.sucksballscausewedontgiveoutinfomationeasily)

---

### Post by dozycat on 2011-09-27
[http://www.thisweekinlinux.com/2011/05/twil051511/]("http://www.thisweekinlinux.com/2011/05/twil051511/")
May be...... May be we have hope.

---

### Post by Mars11 on 2011-10-03
Okay, it looks like it's official. [I think we're getting Netflix on Linux]("http://www.omgubuntu.co.uk/2011/10/native-netflix-client-coming-linux-in-12-months/"), but this has happened before. Let's hope this isn't fake like the rest of `em.

---

### Post by dniMretsaM on 2011-10-03
> **Mars11 said:**
> Okay, it looks like it's official. [I think we're getting Netflix on Linux]("http://www.omgubuntu.co.uk/2011/10/native-netflix-client-coming-linux-in-12-months/"), but this has happened before. Let's hope this isn't fake like the rest of `em.

That's good news! It's proprietary, which is bad, but it's a step in the right direction to wider GNU/Linux acceptance among major companies.

---

### Post by rg4w on 2011-10-04
I made my semi-annual call to NetFlix this morning to ask about Linux support.  The rep was enthusiastic to note the Chrome deployment, and suggested that this could mean a Linux port not far down the road.  But he was also quick to note that at this time there are no specific plans to do so.

---

### Post by dniMretsaM on 2011-10-04
> **rg4w said:**
> I made my semi-annual call to NetFlix this morning to ask about Linux support.  The rep was enthusiastic to note the Chrome deployment, and suggested that this could mean a Linux port not far down the road.  But he was also quick to note that at this time there are no specific plans to do so.

You call them once every other year? Anyway, that seems to be the run-of-the-mill answer people are getting from the customer service people.

---

### Post by rg4w on 2011-10-04
> **dniMretsaM said:**
> You call them once every other year?
~Twice a year, which is about as often as the next round of rumors surface about NetFlix finally supporting Linux.

---

### Post by dniMretsaM on 2011-10-04
> **rg4w said:**
> ~Twice a year, which is about as often as the next round of rumors surface about NetFlix finally supporting Linux.

So wouldn't that mean you call them biannually, not semiannually?

---

### Post by rg4w on 2011-10-05
> **dniMretsaM said:**
> So wouldn't that mean you call them biannually, not semiannually?
Semi = half
Bi = two

---

### Post by dniMretsaM on 2011-10-05
> **rg4w said:**
> Semi = half
Bi = two

Appaently they mean the same thing.

> **Dictionary.com]***bi·an·nu·al*** /b&#299 said:**
> 

[QUOTE=Dictionary.com]*s**em·i·an·nu·al ***/&#716;sem&#275;&#712;anyo&#862;o&#601;l/
Noun: A **semiannual** plant.
Adjective: Occurring twice a year; half-yearly:  "their **semiannual** meetings".

I didn't realize that.

---

### Post by Mars11 on 2011-11-29
Sorry about my absence. Has anyone done anything that might be considered progress?

---

### Post by kingtiger01 on 2012-02-16
Well you can forget the supposed support, those Developers dont even work at Netflix anymore... I Awesume the project was scrapped...

----

Whats the progress note on the plugin?

Useragent string changes are specifying that, if the plugin is present, it should work.

---

### Post by drawkcab on 2012-02-16
I wouldn't hold your breath.  Netflix just doesn't see a market so they don't care.

---

### Post by iamwhatiseem on 2012-04-08
The best hope for this is the announcement that a soon to be future kernel will support android apps natively. (Not through an Android AVD which works but resolution sucks)
I have been saying this for some time - there is an Android Netflix app - HELLO??? - how hard can it be to get that to work natively.

---

### Post by skierkyles on 2012-04-08
> **iamwhatiseem said:**
> The best hope for this is the announcement that a soon to be future kernel will support android apps natively. (Not through an Android AVD which works but resolution sucks)
I have been saying this for some time - there is an Android Netflix app - HELLO??? - how hard can it be to get that to work natively.

Well Android doesn't use X (The windowing system on every linux distro). So that's kind of a big deal. Lots of things like digital rights management would need reworking too I'd imagine. Really Android and Linux as its known on the desktop are not that similar.

---

### Post by irv on 2012-09-24
Well it's been about 6 months since the last post, and we still don't have Netflix on our Linux OS. Today I see Netflix has made some improvements for Android Netflix app: [http://www.slashgear.com/netflix-for-android-gets-tablet-esque-update-24248975/]("http://www.slashgear.com/netflix-for-android-gets-tablet-esque-update-24248975/")
I can watch Netflix videos on my Sony Blu-Ray, Roku, and Windows but I am afraid it will be a cold day in "H" before I can do it on my Ubuntu.

---

### Post by josephmills on 2012-09-24
I do not have the $$ for netflixs but could someone try this. 

1)  Install Wine and Wine tricks, 

2) Install safri to your wine 

3) in safri get siverlight using there browser 

4) restart wine 

5) start safri 

6) go watch netflix's


I think that it would work maybe a little bit of wine tweeking.

---

### Post by Gremlinzzz on 2012-09-24
Write them call them ask when Netflix will be Linux compatible.
Squeaky wheel gets the oil:popcorn:

---

### Post by irv on 2012-09-24
> **josephmills said:**
> I do not have the $$ for netflixs but could someone try this. 

1)  Install Wine and Wine tricks, 

2) Install safri to your wine 

3) in safri get siverlight using there browser 

4) restart wine 

5) start safri 

6) go watch netflix's


I think that it would work maybe a little bit of wine tweeking.

I tried this but I still get this message:
> To watch instantly, you''ll need a computer that meets the following minimum requirements:

Windows
Windows Vista or Windows 7
Internet Explorer 8 or higher; or the latest version of Firefox; or the latest version of Chrome
1.2 GHz processor
512 MB RAM
Mac
An Intel-based Mac with OS 10.4.11 or later
Safari 4 or higher; or the latest version of Firefox; or the latest version of Chrome
1 GB RAM
Chrome OS
A Google Chromebook or Chromebox running Chrome OS 20 or higher
The Safari runs OK, and I am running version 5 which is higher that 4.
[ATTACH]224607[/ATTACH]
I don't thing this is going to work. Or at least I can't get it to work.

---

### Post by irv on 2012-09-24
> **Gremlinzzz said:**
> Write them call them ask when Netflix will be Linux compatible.
Squeaky wheel gets the oil:popcorn:

I have been one of the most squeakiest wheel you ever seen and they must be getting tired of me calling but when you call all you are doing is talking to a tech and they say they will pass the message on. The even tell me that many others have called but the company is going to do what they are going to do, and that is not support us Linux users. (Do you think MS might have some pull on what there are doing?)

---

### Post by pqwoerituytrueiwoq on 2012-09-24
anyone tried booting chrome os in a virtualbox and running netflix in that?

---

### Post by Merk42 on 2012-09-24
> **irv said:**
> (Do you think MS might have some pull on what there are doing?)Considering it's supported on OS X (as well as things like Android), no.

---

### Post by irv on 2012-09-25
> **pqwoerituytrueiwoq said:**
> anyone tried booting chrome os in a virtualbox and running netflix in that?

I thought I would give it a try, but ran into a problem. I downloaded Chrome OS for Virtualbox but all it did was reboot my laptop every time I tried to run it. Then I downloaded the USB version and tried running it off a USB drive. I couldn't get it to boot up. I am starting to believe my hardware is not able to run it. So I gave up.

Does anyone know of a version of Android that would run on a PC? I would give that a try if it does.

---

### Post by thatguruguy on 2012-09-25
> **pqwoerituytrueiwoq said:**
> anyone tried booting chrome os in a virtualbox and running netflix in that?

If you're going to do that, why not just open Windows in virtualbox and use Windows to run Netflix?

---

### Post by irv on 2012-09-25
> **thatguruguy said:**
> If you're going to do that, why not just open Windows in virtualbox and use Windows to run Netflix?

I know what you are saying, but this is the first time in my life I am windows free and I kinda like it that way. I have Windows on one old desktop, but the only little people that use it is my grandkids. They use it for games.
The only reason I try things like this is because I like to. I can live without running Netflix on my laptop because I have so many other things it runs on. I guess it get me that some of these company just ignore use Linux users. 
Just for the record I had winxp running in a virtualbox a few years ago and it ran Netflix but not well enough for me. It keep stopping and was ran jerky.

---

### Post by Frogs Hair on 2012-09-25
Only if it is in the best interest of Netflix.

---

### Post by neu5eeCh on 2012-09-25
[broken record] Netflix will appear on Ubuntu/Linux when Shuttleworth plays ball with them. By his own admission, he's not interested in playing ball with Netflix. The person you have to persuade is not Netflix, but Shuttleworth.

Ahem. And I quote: 

> **OMG Ubuntu:** Has Canonical spoken to Netflix about bringing the service to Ubuntu TV?

 **Shuttleworth:** Netflix is EVERYWHERE so i think it would be a natural conversation  to have, but i’m not aware of the status one way or another, and  besides, today is not the day for announcements.
[/broken record]

---

### Post by aysiu on 2012-09-25
It's a bummer Netflix isn't on desktop Linux, but it is by no means strictly on Windows/OS X. It's on Chrome OS, Android, Roku, PS3... even Nintendo 3DS. If you refuse to use Windows, there are still plenty of non-Windows ways to get Netflix streaming.

---

### Post by emedina on 2012-10-07
I called Netflix this morning and was told that they want to work with Linux but the only thing holding them up is to hear back from Linux to get the ball rolling. :popcorn:

---

### Post by hydn79 on 2012-10-07
I doubt it. How many casual home users are on Linux.

It is disappointing though.

Nice poll though! Start a petition, I'll sign it :)

---

### Post by emedina on 2012-10-07
Since Mark Shuttleworth is the dude that needs to get the ball rolling, Lets contact him directly. We want Netflix Dammit!!! :biggrin::biggrin:

[http://www.markshuttleworth.com/contact-details](http://www.markshuttleworth.com/contact-details)

---

### Post by Blackmag+c on 2012-10-07
Who would they speak to in regard to 'linux'?

That's quite a wide field.

Is Marky Mark the man with his finger in the right pie? 

I don't know, but it is the ONLY thing stopping me from making the switch. Who wants to virtualize everytime they want to watch a movie?

---

### Post by neu5eeCh on 2012-10-07
> **Blackmag+c said:**
> Who would they speak to in regard to 'linux'?

Shuttleworth.

> **Blackmag+c said:**
> That's quite a wide field.

Ubuntu is the 800 Pound Gorilla -- not Fedora, not Opensuse, not PCLOS. Ubuntu.

> **Blackmag+c said:**
> Is Marky Mark the man with his finger in the right pie? 

Yes. He's the man. That said, there are probably vast swaths of fossier-than-thou Linux Muhlahs who would issue Fatwahs based on the kind of deal Shuttleworth would likely agree to.

> **Blackmag+c said:**
> I don't know, but it is the ONLY thing stopping me from making the switch. Who wants to virtualize everytime they want to watch a movie?

Yes, it's too bad. Shuttleworth seems to think he can get 200,000,000 users solely through the introduction of exceedingly pretty and clever lenses, all while ignoring the mass market appetite for products like Netflix. However, it's fair to say that the  Linux high priests also need to back up such a deal. The problem is _**not**_ with Netflix. They're easy. All they want is a market and income.

---

### Post by lovinglinux on 2012-10-08
> **hydn79 said:**
> I doubt it. How many casual home users are on Linux.

It is disappointing though.

Nice poll though! Start a petition, I'll sign it :)


There are already petitions that are running for a long time.

[http://ubuntuforums.org/showthread.php?t=944446](http://ubuntuforums.org/showthread.php?t=944446)


[http://www.petitiononline.com/Linflix/petition.html](http://www.petitiononline.com/Linflix/petition.html) (24932 signatures)


There are also new ones:

[http://www.change.org/petitions/netflix-support-linux-os-s](http://www.change.org/petitions/netflix-support-linux-os-s) (2 supporters)

---

### Post by aysiu on 2012-10-08
I don't think it matters whether or not Shuttleworth says "We want Netflix on Linux" or not.

In 2007, Linux users wanted Netflix. No Netflix.
In 2007, Android basically didn't exist.
In 2008, Android came into being. And now it's 2012 and almost every Android device (phone or tablet) can do Netflix streaming, and no traditional Linux desktop/laptop can do Netflix streaming (with some kind of Windows-related workaround like dual-booting).

Even Chromebooks can do Netflix streaming.

What Shuttleworth needs to do is work with an OEM to release a product that has and will continuously support preinstalled and upgraded versions of Ubuntu indefinitely. It has to be a product people can buy off-the-shelf that has a unique design (not just Ubuntu installed on a normal Windows computer) and competitive pricing. If he does that and markets it well, Netflix will come to that device, I assure you.

But I doubt he'll do it. It's 2012. Back in 2008, I already laid out all the steps that Ubuntu needed to compete:
[http://www.psychocats.net/ubuntucat/ubuntu-the-open-source-apple-challenger/](http://www.psychocats.net/ubuntucat/ubuntu-the-open-source-apple-challenger/)

None of that has happened yet, and so no Netflix.

---

### Post by neu5eeCh on 2012-10-08
> **aysiu said:**
> Even Chromebooks can do Netflix streaming.

What Shuttleworth needs to do is work with an OEM to release a product that has and will continuously support preinstalled and upgraded versions of Ubuntu indefinitely...

I disagree that that's a per-requisite for Netflix. Your mentioning Chrome OS is a case in point.  Chrome OS hardly meets any of the requirements you laid out for Ubuntu. Chrome OS's survival is far from guaranteed. It's far from certain that the product will be continuously supported. Google played ball with Netflix. Canonical/Shuttleworth, for whatever reason, has not.

---

### Post by aysiu on 2012-10-08
> **VTPoet said:**
> I disagree that that's a per-requisite for Netflix. Your mentioning Chrome OS is a case in point.  Chrome OS hardly meets any of the requirements you laid out for Ubuntu. Chrome OS's survival is far from guaranteed. It's far from certain that the product will be continuously supported. Google played ball with Netflix. Canonical/Shuttleworth, for whatever reason, has not.
Actually, Chrome OS meets all of the requirements I laid out. They are custom-designed products (not just off-the-shelf Windows laptops with Chrome OS installed on them). They're guaranteed updates and full compatibility with future Chrome OS versions. And they're competitively priced.

---

### Post by neu5eeCh on 2012-10-08
> **aysiu said:**
> Actually, Chrome OS meets all of the requirements I laid out. They are custom-designed products (not just off-the-shelf Windows laptops with Chrome OS installed on them). They're guaranteed updates and full compatibility with future Chrome OS versions. And they're competitively priced.

> **aysiu said:**
> ...release a product  that has and will continuously support preinstalled and upgraded  versions of Ubuntu indefinitely.

No.

"How many versions back do you support? [We support only the most current dev, beta, and stable channel releases]("http://support.google.com/chromeos/a/bin/answer.py?hl=en&answer=188447")" 

> **aysiu said:**
> "It has to be a product people can buy  off-the-shelf that has a unique design (not just Ubuntu installed on a  normal Windows computer)"

No. Google is simply using dumbed-down WIndows computers. The only facet of the design that's unique is its deliberate curtailment of specs without a commensurate drop in price. They're deliberately handicapped "windows computers". As is repeatedly pointed out by users on _this_ forum (among others), why should they buy a Chromebook when they can spend the same or less on a Windows computer with several times the capability?

> **aysiu said:**
> ... and competitive pricing. 

No again. [Here's]("http://www.amazon.com/b?ie=UTF8&node=2858603011") an Amazon price list. I can drive down to Radioshack, today, and get a 299 dollar computer with superior specs all around.

The issue, for Netflix, is **_not_** the platform, it's the $market$ and the $money$.

---

### Post by litiform on 2012-10-12
I would subscribe to netflix if I could download the movies and watch the download. I don't like the whole streaming concept though because of inability to rewind/fast forward etc smoothly.

---

### Post by irv on 2012-10-12
> **litiform said:**
> I would subscribe to netflix if I could download the movies and watch the download. I don't like the whole streaming concept though because of inability to rewind/fast forward etc smoothly.

I guess I kinda disagree with this. I just move the slider back to where on want to rewind too. Downloads are nice if you just watch on one device, but I have Netflix on my Nook, Roku, Sony Blu-Ray DVD player and two computers. So I would have to keep moving my movie around or put it on a server and take up storage. I like streaming.

---

### Post by gary987 on 2012-10-12
I have seen bluerays player running linux, and I have a mediabox running linux.. both have netflix. Its not about whether it can be done for traditional linux, but whether netflix will ever do it.. I'm guesssing they could release something in less than a day, but they wont.

As soon as I see another service like netflix that supports linux, I will drop netflix and probably never look back

---

### Post by evilsoup on 2012-10-13
I'm pretty sure that Android and Chromebooks both use hardware-based DRM. That's why you can't just install ChomeOS on a VM and expect Netflix to work; and that's why the Android integration with the kernel probably won't be much help.

We'll have to either hope that Microsoft ports Silverlight DRM over to Moonlight (lol), or someone else can do it; or in five years, when Netflix changes from Silverlight to whatever, that that solution will be cross-platform.

---

### Post by deh_p3000 on 2012-12-13
a bit late for a reply but, here is netflix official stance, 


Thank you for contacting Netflix customer support.
Here is the transcript from your recent chat with customer support:

> Netflix Tanya:
Hey there! This is Tanya, how can I help you?


You:
hi
You:
I would like to ask exactly why netflix will work on damn near any computer/phone/tablet etc.... except one running linux?

Netflix Tanya:
Good question! And I have an answer for you! May I ask (quickly) who I'm chatting with please?

You:
my name is Garry #$%^&, and i am a current subscriber, and the only thing holding me back from moving to linux full time is netflix.

You:
and if another streaming service adds support for linux you can bet i will cancel. and move to them.

Netflix Tanya:
I can understand your frustration Garry! And what I was able to find is that Netflix is not compatible with Linux. The reason why is we use Silverlight to stream movies. The Microsoft Silverlight plugin uses DRM. Although there is a Linux/Ubuntu alternative to Silverlight called Mono/Moonlight, it does not have any DRM built in and it is very unlikely Microsoft will ever make a DRM option for it. I'll gladly take your feedback on getting Linux available for our super tech-savvy users like you, though!"

You:
so basically netflix allows microsoft, to dictate what operating systems you can use... thats great.... wonderful. Honestly i'm sick of "microsoft" you guys need to find another may to manage digital rights.

Netflix Tanya:
I totally understand what you're saying and I'll be glad to take your feedback to our Development Team so that you can be heard. You are not alone in your thoughts about Microsoft and hopefully in the near future Linux will be a viable option for Members to utilize.

You:
so how is it any dvd player pretty much can play the streaming? i still am a little unsure as to why you can't write your own .app for linux......

Netflix Tanya:
It's something that Technical Support has been looking into but at this moment Netflix and Linuz have not been able to create an application that won't stop crashing! I guess it's not as easy as it sounds in theory....yet!

Netflix Tanya:
But we are not giving up!


Check out our Help Center if you have any more questions. 

- Your Friends at Netflix

Please note this is the entire conversation, the chat was terminated right after her last message without any other comments or without checking if i had other questions.

---

### Post by monkeybrain2012 on 2012-12-13
> my name is Garry #$%^&, and i am a current subscriber, and the only thing holding me back from moving to linux full time is netflix.

That is kind of lame if you tried to make a demand.:) Why would they listen to you if the bottom line is that you would choose netflix over Linux full time? After that conversation they could be rest assured that they would continue be getting your money.

---

### Post by sdowney717 on 2012-12-13
> **monkeybrain2012 said:**
> That is kind of lame if you tried to make a demand.:) Why would they listen to you if the bottom line is that you would choose netflix over Linux full time? After that conversation they could be rest assured that they would continue be getting your money.

He was talking to a borg. A robotic person programmed to offer nothing of substance. You might as well have talked to someone working at Walmart.

---

### Post by scorpiosnake on 2012-12-24
> **gary987 said:**
> 
As soon as I see another service like netflix that supports linux, I will drop netflix and probably never look back

Here you go: [Amazon Prime]("http://www.amazon.com/gp/prime/signup/videos/ref=nav_menu_video_redirect_combined/182-8171501-5784325")

I have never had a problem watching tv shows or movies on Amazon.

What I don't understand is, if Amazon and Google can do it, why can't Netflix?

---

### Post by irv on 2012-12-24
Yes I use Amazon Prime and others. I also keep Netflix because I have a Sony BlueRay and a Roku box. Plus if I want to watch a movie or TV show on Netflix I have a Asus Transformer and a Nook with Netflix. It seems that Netflix supports everything but Linux. I truly believe that MS has something to do with Netflix not supporting Linux. If Linux keeps growing Netflix might come around that is why I voted "Yes".

---

### Post by irv on 2012-12-25
This was on the News this morning.
[URL="http://gigaom.com/cloud/christmas-eve-aws-outage-stings-netflix-but-not-amazon-prime/"][SIZE="3"]Dec 25, 2012 - 6:14AM PT
Christmas Eve AWS outage stings Netflix but not Amazon Prime[/SIZE][/URL]

EDIT:  This was the best tweet.
> '"Twas the night before Christmas and all through the house, not a @netflix was streaming, not even Mickey Mouse."
[http://www.cnn.com/2012/12/26/tech/web/netflix-down-tweets/]("http://www.cnn.com/2012/12/26/tech/web/netflix-down-tweets/")

---

