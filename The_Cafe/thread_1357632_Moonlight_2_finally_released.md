---
title: "Moonlight 2 finally released"
date: 2009-12-17
forum: The Cafe
---

### Post by Keyper7 on 2009-12-17
[http://tirania.org/blog/archive/2009/Dec-17.html](http://tirania.org/blog/archive/2009/Dec-17.html)

That was one hell of a long security audit, but it's finally done.

I had hopes that it would be ready in time for Karmic... oh well, at least it will probably be on Lucid.

---

### Post by n0glu3 on 2009-12-17
It doesn't work with Xbox UK :(

---

### Post by D3ath on 2009-12-17
I wonder if this is going to finally get Netflix Instant Streaming to linux? Currently have to use the xbox for it would be great if i can use linux.

---

### Post by gnomeuser on 2009-12-17
What is more interesting Novell and Microsoft managed to expand the patent agreement to explicitly include 3rd parties. I know some people were concerned about this and I am happy to see the show of good faith from Microsoft in being inclusive. It is yet another major step in the right direction.

Aside that we get new cooperation agreements announced on Silverlight 3 and 4 as well as rough roadmap milestones for the upcoming Moonlight release.

I am a happy camper.

---

### Post by SunnyRabbiera on 2009-12-17
and in other news silverlight 4 is released and yet again moonlight is still 2 years behind.
Bloody broken standards, Novell should shoot itself in the foot for trusting Microsoft, with a tank cannon.

---

### Post by HappyFeet on 2009-12-17
Go to [this]("http://www.go-mono.com/moonlight/download.aspx") page to get Monnlight 2.

---

### Post by gnomeuser on 2009-12-17
Sadly the plugin still only supports Firefox, with Google releasing ChromeOS there was actually a question on Silverlight support for which Google didn't have an answer. I think a good investment in time would be to ensure that Moonlight runs on Chromium and by extensions ChromeOS. It would be a perfect fit for the project, it's already web heavy and there is demand. They could really expand and enter some interesting cooperations with Google as well.

---

### Post by flloyd on 2009-12-18
> **D3ath said:**
> I wonder if this is going to finally get Netflix Instant Streaming to linux?

I only want Moonlight for two reasons, NBCOlympics.com and Netflix. Unfortunately NBCOlympics still doesn't work and Netflix will never work.

From the OP's link, "Miguel,

Can you comment on the status of the DRM stack in moonlight? I.e. Is it planned for inclusion? When can we expect Netflix "watch it now" to work on our Linux boxes? I believe the is the biggest application that your uses want.

-Jack

migueldeicaza	
It is very unlikely that we will get PlayReady DRM on Linux."

Also, "Microsoft licenses PlayReady today for certain use cases, but they do not have a port for Linux which prevents Moonlight from using it."

I have officially given up hope of getting Netflix Instant Watch on my linux desktop.

I'll keep Moonlight on desktop until the Olympics are done with assuming they get support for it) but after that, it's in the trash bin.

---

### Post by heldal on 2009-12-19
It may be useful for some forms of interactive content, but is a blind alley when video is concerned because:

1. DRM is used to discriminate against some platforms.

2. Missing codecs likewise.

3. HTML5 is rapidly approaching a very useable state in many browsers and platforms, and doesn't discriminate against anybody.

---

### Post by Keyper7 on 2009-12-19
> **heldal said:**
> 1. DRM is used to discriminate against some platforms.

Yeah, this sucks. Then again, DRM is a problem all by itself and should die.

> **heldal said:**
> 2. Missing codecs likewise.

I think Moonlight has a gstreamer backend.

> **heldal said:**
> 3. HTML5 is rapidly approaching a very useable state in many browsers and platforms, and doesn't discriminate against anybody.

Careful there. The standardization for Ogg Theora failed, so each browser is free to implement whatever discrimination it wants.

IIRC, Safari does not support Ogg and does not intend to, for example.

---

### Post by Hallvor on 2009-12-19
> **SunnyRabbiera said:**
> and in other news silverlight 4 is released and yet again moonlight is still 2 years behind.
Bloody broken standards, Novell should shoot itself in the foot for trusting Microsoft, with a tank cannon.

This pretty much sums it up. Thank you!

---

### Post by heldal on 2009-12-19
> **Keyper7 said:**
> 
I think Moonlight has a gstreamer backend.

That doesn't prevent those who control the server platform from choosing codecs which work best on their preferred client(s).


> **Keyper7 said:**
> 
Careful there. The standardization for Ogg Theora failed, so each browser is free to implement whatever discrimination it wants.

Except HTML5 doesn't wrap an extra layer of proprietary obfuscation around the codecs. That makes it funtamentally different from SL and Flash.

> **Keyper7 said:**
> 
IIRC, Safari does not support Ogg and does not intend to, for example.
Yet there are native browsers for OSX which do. 

Theora/Vorbis may not be the only codecs used with HTML5. I'm happy as long as it remains an alternative and that whichever codec becomes the "industry standard" at least can be licensed at non-discriminatory terms from someone who doesn't prefer one product over others.

---

### Post by gnomeuser on 2009-12-19
> **heldal said:**
> It may be useful for some forms of interactive content, but is a blind alley when video is concerned because:

1. DRM is used to discriminate against some platforms.


This is a specific problem with the vendors not with Microsoft or Silverlight. We have previously been successful in convincing many of the recording companies that DRM as implemented currently was a bad idea and now most online music stores will sell you DRM free tracks. Surely we could do the same for video, the same arguments apply.

> 
2. Missing codecs likewise.


What missing codecs, you mean the ones provided you have a licenses (or don't need one in your country as there are no software patents) you can get by compiling against ffmpeg or the  completely licensed codec pack that Microsoft will PAY for you to have access too (code audited and fixed by Novell).

Also in Silverlight 3, and with Moonlight 2 you have support for any codec that has a managed implementation. This means that Moonlight 2 ships with Ogg Vorbis and Dirac support (a Theora port is being worked on if I remember correctly). These are the same codecs Ubuntu can legally distribute for anyone regardless so it makes no difference. 

Except that with Moonlight there is the option of offering licensed codecs to people who need them without asking them to pay (like we currently refer these people to Fluendos excellent codec pack when it comes to GStreamer). On top of that you get the option of using your existing license or if none is needed where you live to compile against ffmpeg after which you get every codec supported and the code to look at.

In other words you get the best of both worlds (in a world where software patents and entities who collect payment for these such as the MPEG-LA exist).

> 
3. HTML5 is rapidly approaching a very useable state in many browsers and platforms, and doesn't discriminate against anybody.

HTML5 is all nice and well but it doesn't define default codecs (like Silverlight and flash does). This is also about more than just video playback, Silverlight is a framework to build applications with offline as well as online now. You get to use the .NET framework and all it's capabilities, in whatever language you might desire (any language that compiles into CLR I believe will be supported). With HTML5 you are forced into Javascript, a language with lacking standardization, a history of poor security and performance. There is as far as I know no easy way to use the same framework to work on applications that will run both online and offline (you do have the HTML5 offline cache but this is still thinking centered around the idea that you are going online again later).

Additionally I have been playing with HTML5 as a replacement for Flash on YouTube, probably one of the biggest drivers of Flash today. It is not measuring up, the site loads strangely, the videos don't play and you lack every feature that isn't a play/pause button, e.g. no voting. This could be done but an actual demonstration of HTML5 replacing a major site and remaining fairly bugfree, performance as well as featureful has not happened to the best of my knowledge. Silverlight I need not mention has been rolled out on several major sites for a while now and the technology added creates vivid, fast and pleasurable user experiences (e.g. just look into adaptive streaming).

Moonlight lets us not just replace html5 and flash but also GTK+ and QT. It is a tremendous piece of technology.

---

### Post by SunnyRabbiera on 2009-12-19
> **gnomeuser said:**
> 
Moonlight lets us not just replace html5 and flash but also GTK+ and QT. It is a tremendous piece of technology.

Feh, then how come it will always be behind then?
Silverlight and Moonlight were supposed to be a collaboration between Microsoft and Novell and supposed to be equal to eachother.
But instead its the same ol BS, Silverlight/Moonlight is yet another broken standard from Microsoft.
Screw Silverlight, screw HTML5, Screw flash.
Maybe its time the open source developers should make a open source alternative that works on everything, not just on one or two browsers and one or two OS's

---

### Post by gnomeuser on 2009-12-19
> **SunnyRabbiera said:**
> and in other news silverlight 4 is released and yet again moonlight is still 2 years behind.
Bloody broken standards, Novell should shoot itself in the foot for trusting Microsoft, with a tank cannon.

We have been over this before you and I if I remember correctly.

Firstly Moonlight 1 was started after Silverlight 1 was released as the technology wasn't interesting till the Silverlight 2 preview came out. This means they were behind then, another thing to note is that the amount of code needed from nothing to SL1 was reasonable but SL1 to SL2 was a major step that required a lot of changes. SL2 to SL3 is a much smaller step and Moonlight 2 which was released recently includes a number of these.

Now to the claim that SL4 was released, it was not, the beta was as a technology preview. We can see the technology that we are required to implement but it is not technology like before with SL2 that is in use. This buys us time to develop the most needed features before SL4 is deployed and in use. Additionally Silverlight 4 implements and standardized functionality that has been in Moonlight for a while (namely running Silverlight apps on the desktop). 

Microsoft and Novell will be working together bringing the full Silverlight experience to Linux and BSD. You get both paid codecs but Microsoft has also made compliance test suites available to Novell which can be run against Moonlight meaning you are assured 100% compliance with Silverlight. On top of this Microsoft has been open sourcing key pieces of technology so they can be used amongst other places in Moonlight meaning a win for both sides and less code duplication.

It will be some time before we see a fully compliant Silverlight 3 release of Moonlight yes but it is not an eternal catch up game as you claim. There has a been a setback mainly by the sheer size of the Silverlight 2 upgrade but now it is fairly smooth sailing from now on, people should expect Moonlight to catch up nicely.

---

### Post by SunnyRabbiera on 2009-12-19
> **gnomeuser said:**
> We have been over this before you and I if I remember correctly.

Firstly Moonlight 1 was started after Silverlight 1 was released as the technology wasn't interesting till the Silverlight 2 preview came out. This means they were behind then, another thing to note is that the amount of code needed from nothing to SL1 was reasonable but SL1 to SL2 was a major step that required a lot of changes. SL2 to SL3 is a much smaller step and Moonlight 2 which was released recently includes a number of these.

Now to the claim that SL4 was released, it was not, the beta was as a technology preview. We can see the technology that we are required to implement but it is not technology like before with SL2 that is in use. This buys us time to develop the most needed features before SL4 is deployed and in use. Additionally Silverlight 4 implements and standardized functionality that has been in Moonlight for a while (namely running Silverlight apps on the desktop). 

Microsoft and Novell will be working together bringing the full Silverlight experience to Linux and BSD. You get both paid codecs but Microsoft has also made compliance test suites available to Novell which can be run against Moonlight meaning you are assured 100% compliance with Silverlight. On top of this Microsoft has been open sourcing key pieces of technology so they can be used amongst other places in Moonlight meaning a win for both sides and less code duplication.

It will be some time before we see a fully compliant Silverlight 3 release of Moonlight yes but it is not an eternal catch up game as you claim. There has a been a setback mainly by the sheer size of the Silverlight 2 upgrade but now it is fairly smooth sailing from now on, people should expect Moonlight to catch up nicely.

BS, its another broken format and you know it.
Stop sucking at Miguel De Icaza's and Microsofts teat, and think for a change...
Moonlight/Silverlight is yet another Microsoft product that is designed to stop any competition.

---

### Post by zekopeko on 2009-12-22
> **SunnyRabbiera said:**
> BS, its another broken format and you know it.
Stop sucking at Miguel De Icaza's and Microsofts teat, and think for a change...
Moonlight/Silverlight is yet another Microsoft product that is designed to stop any competition.

How do you stop competition with a FOSS implementation of something?

---

### Post by BigCityCat on 2009-12-22
Forget it.

---

### Post by phrostbyte on 2009-12-22
Silverlight has been out for *several years*, Microsoft has been hyping it for just about as long (read: billions of dollars in developer evangelism). Yet the most notable use of Silverlight is to stream DRM encumbered media from Netflix. Good luck with your attempts to "take back the web" Microsoft. :P

---

### Post by phrostbyte on 2009-12-22
> **SunnyRabbiera said:**
> and in other news silverlight 4 is released and yet again moonlight is still 2 years behind.
Bloody broken standards, Novell should shoot itself in the foot for trusting Microsoft, with a tank cannon.

Silverlight 4 also adds COM support, meaning two things:

(1) Microsoft is trying to recreate ActiveX 
(2) Silverlight "cross platform" support has already been permanently broken

---

### Post by zekopeko on 2009-12-22
> **phrostbyte said:**
> Silverlight has been out for *several years*, Microsoft has been hyping it for just about as long (read: billions of dollars in developer evangelism). Yet the most notable use of Silverlight is to stream DRM encumbered media from Netflix. Good luck with your attempts to "take back the web" Microsoft. :P

If they can deliver with Silverlight 4 it could rock for desktop/web apps.

BTW IIRC they said that some 45% of user base has Silverlight (I'm guessing Win/Mac user base)

---

### Post by phrostbyte on 2009-12-22
> **zekopeko said:**
> If they can deliver with Silverlight 4 it could rock for desktop/web apps.

BTW IIRC they said that some 45% of user base has Silverlight (I'm guessing Win/Mac user base)

I agree, Silverlight 4 will rock for some desktop apps.

For one Microsoft has added ActiveX-like abilities to Silverlight, making it an attractive platform for malware developers. :P Unfortunately that functionality is not available on Mac or Linux (Microsoft = developer, Windows only functionality = inevitable). So no cross platform Silverlight adware for you. :(

---

### Post by zekopeko on 2009-12-22
> **phrostbyte said:**
> I agree, Silverlight 4 will rock for some desktop apps.

For one Microsoft has added ActiveX-like abilities to Silverlight, making it an attractive platform for malware developers. :P Unfortunately that functionality is not available on Mac or Linux (Microsoft = developer, Windows only functionality = inevitable). So no cross platform Silverlight adware for you. :(

ZOMG!!!! NOOOOOO!!!! Why can't we be malware compatible?!

---

### Post by phrostbyte on 2009-12-22
> **zekopeko said:**
> ZOMG!!!! NOOOOOO!!!! Why can't we be malware compatible?!

I figure native calls will be useful for malware. But this restriction applies to anyone using that functionality for even non-malware things (which is highly tempting given how "restrictive" the CoreCLR is). COM enabled Silverlight apps will not work on Linux OR Mac. And unless Moonlight starts bundling Wine it never will.

---

### Post by zekopeko on 2009-12-22
> **phrostbyte said:**
> I figure native calls will be useful for malware. But this restriction applies to anyone using that functionality for even non-malware things (which is highly tempting given how "restrictive" the CoreCLR is). COM enabled Silverlight apps will not work on Linux OR Mac. And unless Moonlight starts bundling Wine it never will.

Couldn't you simply ship an embbeded library you need in the application? Silverlight is sandboxed and I know you can load managed codecs inside it without installing them on your system.

---

### Post by phrostbyte on 2009-12-22
> **zekopeko said:**
> Couldn't you simply ship an embbeded library you need in the application? Silverlight is sandboxed and I know you can load managed codecs inside it without installing them on your system.

Silverlight is only sandboxed in "browser mode", COM works in "desktop mode".

Problem is COM is nonexistent on OS X or Linux. And even if it was, there is a plethora of COM libraries you can not legally distribute (as they are part of Windows).

The same issue is why you can't just run any .NET app on Linux, even tho we have Mono. Once it tries to PInvoke into the OS, Mono asplodes.

---

### Post by tubezninja on 2009-12-23
> **SunnyRabbiera said:**
> 
Maybe its time the open source developers should make a open source alternative that works on everything, not just on one or two browsers and one or two OS's

Oh, you mean how like how Linux is so universal that it readily plays modern, increasingly common multimedia standards?  Oh wait, it doesn't....

My point being: creating yet ANOTHER standard, with backing that's questionable at best, doesn't solve the problem.  It just pluralizes it.  You can make what you want; Netflix is still going to use Silverlight, as will many other media providers.  And then you're still stuck with the same problem.

I see this as a self-fulfilling prophecy.  Microsoft throws the FOSS community a bone with this, and immediately the militant among the FOSS community come out with fangs bared talking about what an evil ploy this is.  Lack of support means lack of development.  So, the FOSS community glares at Microsoft and their "broken" standard, while Microsoft says "See?  They didn't want it, and this is the last time we'll do anything to extend an olive branch."

Everyone got exactly what they expected out of this venture, remaining as insular as ever and taking away more ammunition to fuel their agendas.  And so remains the status quo.  And I continue to happily rent netflix videos on my mac, while my linux  boxes are relegated to other, less media-friendly uses.

---

### Post by SunnyRabbiera on 2009-12-23
> **scaredpoet said:**
> Oh, you mean how like how Linux is so universal that it readily plays modern, increasingly common multimedia standards?  Oh wait, it doesn't....

My point being: creating yet ANOTHER standard, with backing that's questionable at best, doesn't solve the problem.  It just pluralizes it.  You can make what you want; Netflix is still going to use Silverlight, as will many other media providers.  And then you're still stuck with the same problem.

I see this as a self-fulfilling prophecy.  Microsoft throws the FOSS community a bone with this, and immediately the militant among the FOSS community come out with fangs bared talking about what an evil ploy this is.  Lack of support means lack of development.  So, the FOSS community glares at Microsoft and their "broken" standard, while Microsoft says "See?  They didn't want it, and this is the last time we'll do anything to extend an olive branch."

Everyone got exactly what they expected out of this venture, remaining as insular as ever and taking away more ammunition to fuel their agendas.  And so remains the status quo.  And I continue to happily rent netflix videos on my mac, while my linux  boxes are relegated to other, less media-friendly uses.

Feh, microsoft suckup

---

### Post by schauerlich on 2009-12-23
> **SunnyRabbiera said:**
> Feh, microsoft suckup

[LinuxHateIsMicrosoftLove™](http://www.tmrepository.com/trademarks/linuxhateismicrosoftlove/)

---

### Post by zekopeko on 2009-12-23
> **SunnyRabbiera said:**
> Feh, microsoft suckup

Your argumentative skills are amazing to behold. They bring so much to the discussion! Why I couldn't hope to ever out-debate you!

---

### Post by perspectoff on 2010-02-13
I am watching the Winter Olympics over NBC's streaming video service using the Moonlight 2.99 plugin for Firefox.

It runs nicely. 

NBC requires that you are a cable customer if you want to access their live or recent replay videos. (I am, so I was required to sign in with my cable provider to be eligible to watch the streaming videos).

You may quibble with the restrictions, but kudos must be given to Novell's Moonlight project in bringing Moonlight 2.99 to readiness in time for the Olympics.

The plugin can be downloaded from:

[http://www.go-mono.com/moonlight/prerelease.aspx](http://www.go-mono.com/moonlight/prerelease.aspx)

And, duh, you don't watch it on your computer. You buy a cable that runs from the video output of your computer (you have a laptop, right?) to your TV (an HDI cable for newer computers or an S-video cable/audio cord for you dinosaurs) and then watch over your big screen. Only takes a quick trip to your electronics store to find the cables...

Aside:

We only rarely watch regular TV anymore. It's Hulu or other online content, piped through the TV as described, nearly exclusively.

Oh yeah, I forgot to mention. If you are watching online TV, you may want to learn about QOS (Quality of Service) filters in your router. You can give priority to certain net services (such as Hulu or NBC streaming) if you don't want to be interrupted by your kids whenever they are playing on the Internet...

---

### Post by stalet on 2010-02-17
i just installed novell-moonlight-2.99.0.3-x86_64.xpi but i get like 1 frame per second - and in full screen the resolution is really bad. Is there a way to tune this ?

(btw its not my internet connection as my mac plays this just fine...)

---

### Post by Twitch6000 on 2010-02-17
> **gnomeuser said:**
> What is more interesting Novell and Microsoft managed to expand the patent agreement to explicitly include 3rd parties. I know some people were concerned about this and I am happy to see the show of good faith from Microsoft in being inclusive. It is yet another major step in the right direction.

Aside that we get new cooperation agreements announced on Silverlight 3 and 4 as well as rough roadmap milestones for the upcoming Moonlight release.

I am a happy camper.
As am I :D. Now if only flash would get fixed up.

---

### Post by phrostbyte on 2010-02-17
> **Twitch6000 said:**
> As am I :D. Now if only flash would get fixed up.

Maybe the Mono team could work on Flash afterwards. It can be called "Flashlight"

---

### Post by Frak on 2010-02-17
> **phrostbyte said:**
> Maybe the Mono team could work on Flash afterwards. It can be called "Flashlight"
Neat name.

---

### Post by gnomeuser on 2010-02-17
> **phrostbyte said:**
> Maybe the Mono team could work on Flash afterwards. It can be called "Flashlight"

Why should they do that? The FSF already has an open source flash implementation and there is swfdec as well. The FSF could if they so desired enter into a similar deal with Adobe to get comformance tests and specifications. 

Why does the Mono project and Novell have to do all the work, they already contributed a near full implementation of the .NET framework and Silverlight, they also ensured that people who need legal access to codecs have that at zero cost.

Gnash takes donations, if you think open source flash is important that seems like the approach to take to me.

[http://www.openmedianow.org/?q=node/32](http://www.openmedianow.org/?q=node/32)

---

### Post by zekopeko on 2010-02-17
> **stalet said:**
> i just installed novell-moonlight-2.99.0.3-x86_64.xpi but i get like 1 frame per second - and in full screen the resolution is really bad. Is there a way to tune this ?

(btw its not my internet connection as my mac plays this just fine...)

Look at the Moonlight page you downloaded from. There should be a link to "Issues" page. IIRC you need to disable some effects for Moonlight to work nicely since the effects aren't optimized and they are heavy on CPU.

---

### Post by arnab_das on 2010-02-18
well this is good news. i hope moonlight gets supported by other browsers as well.

having said that, i really dont like moonlight's implementation via an add on. but then again, this is microsoft territory, we really cant complain.

---

### Post by Frak on 2010-02-18
> **arnab_das said:**
> well this is good news. i hope moonlight gets supported by other browsers as well.

having said that, i really dont like moonlight's implementation via an add on. but then again, this is microsoft territory, we really cant complain.
You can bug Novell to create new versions. As far as I can remember, though, the plugin can be ported to any other browser that implements the NPAPI, which is just about everything.

---

### Post by arnab_das on 2010-02-18
> **Frak said:**
> You can bug Novell to create new versions.

if i do that i'll only give Greg Kroah more ammunition to blast canonical. :P

kidding.

---

### Post by gnomeuser on 2010-02-18
> **arnab_das said:**
> well this is good news. i hope moonlight gets supported by other browsers as well.

having said that, i really dont like moonlight's implementation via an add on. but then again, this is microsoft territory, we really cant complain.

Being worked on:
[http://lists.ximian.com/pipermail/moonlight-list/2010-February/000868.html](http://lists.ximian.com/pipermail/moonlight-list/2010-February/000868.html)

---

