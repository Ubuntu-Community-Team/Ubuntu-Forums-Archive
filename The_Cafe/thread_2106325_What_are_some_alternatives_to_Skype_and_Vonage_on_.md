---
title: "What are some alternatives to Skype and Vonage on Ubuntu"
date: 2013-01-18
forum: The Cafe
---

### Post by West201 on 2013-01-18
I'm looking for a VOIP service provider with phone number capabilities. Thou Skype is great and has great features, I'm unsure if it will be reliable on Ubuntu. 

Are there any VoIP providers that support Ubuntu better than Skype ? (with phone number support)

Thanks

---

### Post by Docaltmed on 2013-01-18
I use diamondcard in combination with Empathy. There's also a couple of other VOIP applications you can download. The prices are excellent, and the quality is decent.

---

### Post by pissedoffdude on 2013-01-18
I haven't had any issues with Skype, but if you want alternatives, give Ekiga (might be pre-installed) and Google Voice a try

---

### Post by West201 on 2013-01-18
hank you very much for you responses. 

Just to clarify, I'm looking to use a VoIP service to stay in touch with my relatives in the U.S. My understanding is that Skype offers U.S based phones numbers for a fee, and for an additional charge, I'm able to call a landline phone number as well as receive phone calls on skype (from landline). I'm looking for a company that offers a similar service, but that has more Linux support.

---

### Post by Adam_GUI on 2013-01-18
I've not had any issues using skype in calls to friends on Windows machines.
Outside of me not having access to their games.  But, eh...

I believe Ekiga offers phone number support.  Their default client worked awful for me last time I tried it.  But, I had good luck using [_Linphone_]("http://www.linphone.org/") to connect with my Ekiga account.  
***EDIT***
Ekiga was really picky about port forwarding for being able to connect upstream.  Check with your ISP about opening ports before going this route.

I can't think of anything else using a SIP client for telephony.

---

### Post by gifford on 2013-01-18
I have not had any issues with Skype in Ubuntu 12.04.

Also, Google voice is available with video chat and works great for me.

---

### Post by Paddy Landau on 2013-01-18
> **jessejj89 said:**
> … to clarify, I'm looking to use a VoIP service to stay in touch with my relatives in the U.S.
That depends on where you are calling from. For me (in the UK), Skype is a particularly expensive option. I use selected providers over the landline instead to call the US and elsewhere.

I have found the new Skype for Linux to run perfectly on 12.04. Have you tried it yet? If you can Skype people using the free service without problem, you'll be able to use the paid service fine.

---

### Post by Nr90 on 2013-01-18
Been using skype for a while now on ubuntu.
The client is a bit more basic then the windows/OSX versions, but has been flawless.

---

### Post by Linuxratty on 2013-01-18
Google +
 The hangouts. VOIP.
 Ten people can use it at a time and as each person speaks,it jumps to their cam image. It's also free.
Extremely cool.
We use it for our poker games on LI and it adds such an additional entertaining level to playing.:D

---

### Post by helpee on 2013-01-18
If you search for voip in the ubuntu software centre, there's a few alternatives :)

---

### Post by Mikeb85 on 2013-01-18
Skype works fine on Linux.  And calling a US landline over the internet is quite cheap, I use Skype to call Canada from abroad (for reference, from Guyana, Barbados, France, etc...) and it costs me around $0.02 Cdn per minute...  Check out their rates:  [http://beta.skype.com/en/rates/#learnMore](http://beta.skype.com/en/rates/#learnMore)

Not that I'm trying to sell you on them, but I've found them to be very reliable, the Linux and Android apps work fine, and it's convenient.

---

### Post by monkeybrain2012 on 2013-01-19
I have never had any issue with Skype. But you can also call phone in gmail, don't know the rate though.

---

### Post by sdowney717 on 2013-01-19
> **Linuxratty said:**
> Google +
 The hangouts. VOIP.
 Ten people can use it at a time and as each person speaks,it jumps to their cam image. It's also free.
Extremely cool.
We use it for our poker games on LI and it adds such an additional entertaining level to playing.:D

Interesting never tried that.
I do use Google voice a lot and have a Google phone number to receive calls.

If you setup google voice in the USA when you go overseas will it still be free vs setting it up overseas?

---

### Post by Linuxratty on 2013-01-19
> **monkeybrain2012 said:**
> I have never had any issue with Skype.

 I have..It freezes and crashes mostly when people send files, but also for no reason other than another person logging in.
 You also can't have more than one person in a video chat without paying for it,unlike G+ hangouts,which allow 10.

---

### Post by Paddy Landau on 2013-01-19
> **Linuxratty said:**
> It freezes and crashes…
I wonder what different set-ups people have? I am using Skype 4.1.0 from the standard Ubuntu repositories on Ubuntu 12.04 64-bit. Mine works perfectly. What do you have?

---

### Post by monkeybrain2012 on 2013-01-19
> **Linuxratty said:**
> I have..It freezes and crashes mostly when people send files, but also for no reason other than another person logging in.
 You also can't have more than one person in a video chat without paying for it,unlike G+ hangouts,which allow 10.

Yeah if you want to have conference call G talk is the way to go, I have also install jitsi, but haven't got a chance to try it out.

---

### Post by Linuxratty on 2013-01-19
> **Paddy Landau said:**
>  Mine works perfectly. What do you have?

I'm using the latest version of Skype with the 12.04 version of Ubuntu..Every version of Skype I've ever used has been crashy,but the newer the versions,the more crashy they seem to be.
 It also crashes on the Windows and the Mac people,so I'm not alone.

---

### Post by Paddy Landau on 2013-01-20
> **Linuxratty said:**
> … Every version of Skype I've ever used has been crashy,but the newer the versions,the more crashy they seem to be.
That makes me suspect a hardware driver problem. Maybe start Skype from a terminal and keep the terminal running in the background. When Skype crashes, start a new thread with the error output.

---

### Post by zerubbabel on 2013-01-22
I switched from Skype to [Jitsi]("http://jitsi.org") for instant text and audio communication, file transfers, and screen sharing -- all with encryption. Coupled with [anveo.com]("http://anveo.com") as my SIP provider, I can make and receive calls to regular phones. A US phone number for incoming calls costs $1/month, plus about a penny a minute for calling most anywhere in the western world. anveo.com also support sending and receiving faxes and SMS text messages.

---

### Post by ugm6hr on 2013-01-22
I am in UK, but sipgate have a similar US service:
[http://www.sipgate.com/editions](http://www.sipgate.com/editions)

Only company I have encountered that has a free VOIP number (US or UK). Unfortunately, it appears there is a queue for free packages.

No Linux "support" per se, but works perfectly with any VOIP phone (including many open source options), and on Android etc. Just remember, no SMS support to my knowledge.

---

### Post by unbuntu77 on 2013-06-15
if all you want to do is make video calls with people you know in the USA, then I'd expect Google Voice / G+ hangouts to have everything you need. they're both FREE. Just verify your account with an already existing phone number and you're all set. Skype is fair priced but I personally think its overly prone to crashes and other problems. (mobile versions of it, anyways).

[http://getapps.cc/what-are-the-best-skype-alternatives/](http://getapps.cc/what-are-the-best-skype-alternatives/)

---

### Post by MissMonicaE on 2013-06-24
I use Jitsi--it's a client, but they'll also give you a free XMPP account if you want one. It works for AIM, Facebook Chat, Google Talk, ICQ, Ippi, Iptel.org, MSN, SIP, and Yahoo accounts as well as XMPP, which is handy. Also it comes with crypto out of the box! :)
ETA: Also, unlike Skype, you can video conference for free.

---

### Post by Paddy Landau on 2013-06-25
> **MissMonicaE said:**
> I use Jitsi … Also, unlike Skype, you can video conference for free.
And, presumably, unlike Skype it has no backdoor mandated by the USA government.

---

### Post by Linuxratty on 2013-06-26
WebRTC...The version of Fire Fox you got this morning, well it's available to you right now.
 The down side is it only works for two people.
> "Following the recent introduction of full Web Real-Time Communications to Chrome, Tuesday's update to Firefox makes it the second browser to support the plugin-free protocol.

The debut of WebRTC, as the protocol is known, in Firefox 22 (download for Windows | Mac | Linux) is no small potatoes. "Plugins are the single largest source of security and stability issues that we see," said Johnathan Nightingale, Mozilla's vice-president of engineering for Firefox.

WebRTC is planned for Firefox for Android (download), which also updated Tuesday, but it has yet to be added to the mobile browser.

On the surface, WebRTC sounds a lot like Skype. It lets you conduct voice and video calling one browser to another via its PeerConnection component, but it also lets you transfer data directly between two browsers thanks to a component called DataChannels. These were both added in Tuesday's new version of Firefox stable."

[http://news.cnet.com/8301-1001_3-57590928-92/new-firefox-earns-full-webrtc/](http://news.cnet.com/8301-1001_3-57590928-92/new-firefox-earns-full-webrtc/)




---

