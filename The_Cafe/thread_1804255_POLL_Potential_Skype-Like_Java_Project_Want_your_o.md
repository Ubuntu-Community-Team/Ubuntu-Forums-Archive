---
title: "POLL: Potential Skype-Like Java Project: Want your opinion"
date: 2011-07-14
forum: The Cafe
---

### Post by Keiran230 on 2011-07-14
TL;DR version: Free, cross-platform, and open source Skype-like program: would you use it?

Background:
Let's face it: Skype hasn't updated the *nix versions in years, and hasn't implemented simple features such as joining an ongoing group call. Other than the leak, it's also closed source. Since it's owned by Microsoft, it will most likely never be customizable, use any open standards whatsoever, or release its source to the public. The users are also bound to its EULA, which will most likely be modified in the near future to allow Microsoft to directly eavesdrop on your conversations (Patent Serial number: 645485)

The Project:
To avoid having the same issues Skype had, where one operating system would get features another would not, this project will be written entirely in Java and use GPLv3. It will probably mature and support more codecs and standards in the future, but until then, it will use Vorbis-encoded UDP audio streams for voice calls and raw TCP connections for chat. I plan on later encrypting these connections once the rest of the program is functional. It will also be entirely P2P, requiring no servers to coordinate anything. It will work best through VPNs (like Hamachi, for those who want a simple version) or internal LANs.

Of course my friends and I will use it when completed, but as for knowing how the (Ubuntu) Linux community would like it, from the random sample of which users stumble on this thread, how is your interest in such a program?

---

### Post by mikewhatever on 2011-07-14
Skype for Linux has been last updates on Apr 6 2011. Not sure how you came up with years, was that pure imagination?

Anyway, the problem with open source cross platform VIOP solutions is that there are too many of them, but none is as good as even the seemingly perpetual lame beta of the Skype for Linux. Do we really need yet another project? If you have what it takes, why not simply contribute to one of the existing one.

For example, there is already a java based cross-platform, and seemingly promising project called Jitsi.
[http://jitsi.org/](http://jitsi.org/)

---

### Post by Keiran230 on 2011-07-14
> **mikewhatever said:**
> Skype for Linux has been last updates on Apr 6 2011. Not sure how you came up with years, was that pure imagination?

You're right, that was badly worded. It *has *been updated, but look at the versions: Linux is on version 2.x, and Windows is on version 5.x.

---

### Post by mikewhatever on 2011-07-14
Version numbers don't mean anything beyond version numbers. They are not a measure of quality or features, in fact, I very much dislike the latest versions of skype for Windows because of problems and adds they display, the Linux version is OK though.

---

### Post by catlover2 on 2011-07-14
> **Keiran230 said:**
> TL;DR version: Free, cross-platform, and open source Skype-like program: would you use it?

Background:
Let's face it: Skype hasn't updated the *nix versions in years, and hasn't implemented simple features such as joining an ongoing group call. Other than the leak, it's also closed source. Since it's owned by Microsoft, it will most likely never be customizable, use any open standards whatsoever, or release its source to the public. The users are also bound to its EULA, which will most likely be modified in the near future to allow Microsoft to directly eavesdrop on your conversations (Patent Serial number: 645485)

The Project:
To avoid having the same issues Skype had, where one operating system would get features another would not, this project will be written entirely in Java and use GPLv3. It will probably mature and support more codecs and standards in the future, but until then, it will use Vorbis-encoded UDP audio streams for voice calls and raw TCP connections for chat. I plan on later encrypting these connections once the rest of the program is functional. It will also be entirely P2P, requiring no servers to coordinate anything. It will work best through VPNs (like Hamachi, for those who want a simple version) or internal LANs.

Of course my friends and I will use it when completed, but as for knowing how the (Ubuntu) Linux community would like it, from the random sample of which users stumble on this thread, how is your interest in such a program?

I'd really love to see the source for the eavesdropping statement above.

---

### Post by zerubbabel on 2011-07-14
I'd vote for improving jitsi rather than starting a new project.

---

### Post by Keiran230 on 2011-07-14
One of the biggest problems (but not the only issue) I've had with the Linux version was group conferencing. I am always in an ongoing group chat, which periodically starts a call. If another person starts the call and I'm not there to answer it, TOO BAD. I have to either ask the call leader to call me again, or wait until another one starts up. This feature has been missing since I first started using Skype, and since the simple issue was reported long ago, that's the reason I assumed it wasn't updated beyond stability fixes. On the Windows version, I've never had this issue, and can hop in and out of a conference call at any time.

The other issues are mainly small annoyances which I can just turn a shoulder to, such as the incomming call noise layering on itself multiple times, for each person in the call.

I just took a look at Jitsi, and wow. I didn't like Ekiga, but I'm definately going to give this one a shot, and if I like it, F... this project.

---

### Post by Keiran230 on 2011-07-14
> **catlover2 said:**
> I'd really love to see the source for the eavesdropping statement above.

[http://lmgtfy.com/?q=patent+645485](http://lmgtfy.com/?q=patent+645485)
(sorry, I couldn't resist)

I actually stumbled on that issue a couple days ago and figured it was a bunch of paranoid users, since there are a lot of people who hate Microsoft and don't have a logical reason why. (I am NOT implying there aren't reasons, though) Then, I looked it up myself to humor the issue and came across a patent for Skype eavesdropping technology which Microsoft has/has pending, with serial number 645485. They would PROBABLY only use it for  marketing or something like that, but that doesn't make it any less creepy.

---

### Post by Famicube64 on 2011-07-14
Skype is still the best until Micro$oft sabotages it for all non-Windows systems. #-o

---

### Post by mikewhatever on 2011-07-14
Jitsi is still a beta, and they pump out up to three nightly builds in 24 hours. If they could manage to make a stable version by the end of the year, I'd be happy to switch.

---

### Post by Keiran230 on 2011-07-14
Regardless, I think I'll be snooping around Jitsi's source code, since I found this on Wikipedia:
"...if both sides are 'trapped' behind NAT routers, [Jitsi will] obtain a reachable IPv6 address via a tunnel-broker."
As a networking student, that interests me.

Jitsi's website's FAQ mentioned development of an Android app, which I would find pretty awesome if they do make it, since the Android Skype is a nightmare. For example, it keeps auto-launching without my permission and then crashing itself in an endless cycle...

---

### Post by mikewhatever on 2011-07-14
You may also want to take a look at this ebook:
[http://www.aosabook.org/en/jitsi.html](http://www.aosabook.org/en/jitsi.html)
Written by the lead Jitsi's developer, it discusses some of the details and strategies.

---

### Post by Linuxratty on 2011-07-15
> **Keiran230 said:**
> TL;DR version: Free, cross-platform, and open source Skype-like program: would you use it?

, how is your interest in such a program?

Intense..Over at linuxinternationals.org we have been beating this subject like a dead horse.
 We have tried several alternatives to Skype and despite it's flaws,none live up to Skype.No matter what we tried,one of us,sometimes more would hit a snag and there was no work-around.
What we need:

*VOP for multiple users.

* Easy,intuitive screen sharing.

* Chat

* World wide,not just USA.

* No complicated,convoluted sign ins with multiple hoops to jump through.

Do this and we will be falling all over ourselves to use it.

---

