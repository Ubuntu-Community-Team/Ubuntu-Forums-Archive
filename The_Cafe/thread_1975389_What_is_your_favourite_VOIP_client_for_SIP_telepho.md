---
title: "What is your favourite VOIP client for SIP telephony?"
date: 2012-05-07
forum: The Cafe
---

### Post by dzsobacsi on 2012-05-07
Currently I use Twinkle but I really hate it. My wireless headset acts as a separate audio card and this circumstance makes the usage of this piece quite painful. 
I tried Ekiga but it did not connect.
I tried Empathy which works but it seems that I cannot save a contact if it is only a phone number and does not belong to any IM  provider.
(I have a subscription at Voipalot.)

===============================================
Update:

Well, that is not a lot of votes until now. But I have tried Linphone and it seems to be working flawlessly.
I am still curious about the results anyway.

---

### Post by VanillaMozilla on 2012-05-08
Twinkle.  Because it works, and works well.  I tried several others that didn't work at all.  And very good rates and other services with DiamondCard.

There's also a nice, prominent Java program (name has been changed) that I liked a lot.

---

### Post by VanillaMozilla on 2012-05-08
Dzso Bacsi, try Jitsi.  The last time I looked it was excellent.  I must say Twinkle is also excellent, although I haven't had your problem.  You will probably have to adjust the microphone volume with the operating system.  If you are using Ubuntu, that is on the Sound Preferences thing.

---

### Post by Docaltmed on 2012-05-08
Empathy is the only one that works decently at all, imho. Twinkle is nice, but the UI is so dated that it makes my eyes hurt. Jitsi has never worked for me, across 5 computers and two releases. Linphone is what I use for my diamondcard account on my smartphone. Works great there, can't even find it's way to the door on my computer.

Basically, most of the others don't work at all for me. And though the Empathy VOIP interface is umm, less than optimal, it works and the software is integrated into the desktop. 

I don't really ask for all that much.

---

### Post by gradinaruvasile on 2012-05-08
Jitsi. It works very well, it has tons of features including peer-to-peer encryption and whatnot.
It also has some very nice codecs like Silk (this is the base of Skype's codec) that uses minimal bandwidth with very good sound quality. It has absolute codec control, you can enable/disable/reorder them as you wish, it has google contacts support (if you use google talk account) and whatnot. I use it for all my messenger needs, i have google talk/sip/yahoo/facebook accounts in it.
Another thing is that it has everything packed in, it doesnt depend on any other system-level codecs or anything.
It is very actively developed (the nightly builds are very freqvently updated) - just in now there is native pulseaudio support.
BTW besides SIP it supports Google/XMPP(Jabber) voice/video, it works well with Google Talk (if both sides use Jitsi, you'lll get end-to-end supplementary encryption as bonus, meaning the google servers can "hear/see" only already encrypted audio/video streams).

Other clients:
1. Empathy: has crap SIP routing - it doesnt work if you have the SIP server through VPN connections etc. Not o mention you cant add SIP users to the roster.
It has tons of dependencies and whatnot, it isnt clear for a casual user what he/she needs to install to enable feature x. Also you dont have any control over codecs.
2. Linphone: This would be my choice of SIP client if i hadnt use Jitsi for everything. It is very stable, has very good SIP routing, worked for me in every scenario. It has another very good addition - a text-mode client (linphonec) that works from terminal. Very nice to use over ssh (i use it for baby monitoring on a Dell Mini laptop). Good spy software also (OOPS...).
It is a robust piece of software, it is also cross platform. I recommend this if you look for only a SIP client.
3. Sflphone - very good also, the problem is that doesnt have video support. The accounts are very configurable, you can specify custom gateways/sip servers and whatnot for every one of them, and it has IAX support (i believe it is the only one here).
4. Ekiga - Good if you are on the same LAN with the server, but it doesnt really work well in other circumstances (through VPN for example).
5. Qutecom - the project is almost dead. Pity, it showed promise to be something like Jitsi. The latest version has SIP routing issues.
6. Yate - this is an interesting animal. It seems that it launches an entire SIP server (maybe not all but it has quite some threads), and uses constantly CPU cycles even if idle (the latest 4.1 version seems to use less). Other than that, it works very well with SIP and Google Talk. Again, it would be a good contender but Jitsi has more stuff packed in (Yahoo support/file transfer, zrtp etc).
7. Blink - works well it seems, but this also uses CPU cycles when idle (it seems it keeps audio streams open even it shouldnt). It has some weird stuff in it, like some custom file transfer that is probably used in the Apple universe (Blink is primarily built for apple).
8. Twinkle - it is a KDE app, looks like crap in GTK (i use Xfce). Other than that + its weird interface it seems to do the job quite well.

The above statements are the result of me looking for SIP applications. I tested these (seems to be the most proeminent) because i needed a program that has good SIP support. I use SIP over a VPN connection and rather surprisingly big names like Ekiga failed to work in these conditions. Ekiga 2 series worked though, but the 3 series not anymore.

---

### Post by dzsobacsi on 2012-05-09
> **VanillaMozilla said:**
> Dzso Bacsi, try Jitsi.  The last time I looked it was excellent.  I must say Twinkle is also excellent, although I haven't had your problem.  You will probably have to adjust the microphone volume with the operating system.  If you are using Ubuntu, that is on the Sound Preferences thing.
In Twinkle settings the default input and output was my wireless headset. Then if my headset is set as input and output in the system's sound preferences and I want to make a call it says that it cannot reach the audio card and it cancels the call. In this case I had to shut down Twinkle, to set my built in audio as input and output in the sound settings, to restart Twinkle and after all this struggling it works. Not counting the fact that now I cannot set the volume with the buttons on the headset. When I have to I go to sound settings again, change the input and output back to the headset (during the call!) and now I can adjust the volume as well. 
Well, in a nutshell, that was why Twinkle made me crazy and why I decided to look after some other solution. 

Jitsi sounds a nice piece to try. I will check it out.

---

### Post by dzsobacsi on 2012-05-09
> **Docaltmed said:**
>  Linphone is what I use for my diamondcard account on my smartphone. Works great there, can't even find it's way to the door on my computer.


You can download it easily from Ubuntu Software Center

---

### Post by dzsobacsi on 2012-05-09
gradinaruvasile,
Thanks for this comprehensive answer.
I think that linphone will completely satisfy my needs.

---

### Post by markbl on 2012-05-09
WT? This poll omits what is almost certainly the most popular voip client on linux!?

It's also the most popular on every other platform ...

---

### Post by Docaltmed on 2012-05-09
> **dzsobacsi said:**
> You can download it easily from Ubuntu Software Center

Me being funny was also me being not clear. My problem with most of the SIP clients, including Linphone, is getting them to work on my computer. I can install Linphone, I just can't get it to run. Same with Jitsi, etc.

The fact that my problem is nearly universal makes me think it's me not them, but I have no idea why. Empathy does work, so as limited as it is, I ran with it.

---

### Post by Docaltmed on 2012-05-09
> **markbl said:**
> WT? This poll omits what is almost certainly the most popular voip client on linux!?

It's also the most popular on every other platform ...

Skype doesn't do SIP, the OP specified SIP clients.

---

### Post by Dry Lips on 2012-05-09
I must admit that I've never tried it, but Blink is perhaps the only one of these clients that comes for Linux, Mac *and* Windows. (I'm not sure if it is open source, though.)

---

### Post by dzsobacsi on 2012-05-09
> **markbl said:**
> WT? This poll omits what is almost certainly the most popular voip client on linux!?

It's also the most popular on every other platform ...

I have made some research before I have compiled this poll. I am sorry if something has escaped my notice. 

Do not be secretive. What did I miss out?

By the way, this was my source:
[http://en.wikipedia.org/wiki/Comparison_of_VoIP_software](http://en.wikipedia.org/wiki/Comparison_of_VoIP_software)

---

### Post by gradinaruvasile on 2012-05-09
> **Docaltmed said:**
> Me being funny was also me being not clear. My problem with most of the SIP clients, including Linphone, is getting them to work on my computer. I can install Linphone, I just can't get it to run. Same with Jitsi, etc.

The fact that my problem is nearly universal makes me think it's me not them, but I have no idea why. Empathy does work, so as limited as it is, I ran with it.

What exactly "cant get it to run" means? They dont start up?
They are 2 very different architectures, so both not working means that you have some other issues on your computer.

---

### Post by Docaltmed on 2012-05-09
> **gradinaruvasile said:**
> What exactly "cant get it to run" means? They dont start up?
They are 2 very different architectures, so both not working means that you have some other issues on your computer.

Last time I tried Linphone I could not, for the life of me, get it to register with my diamondcard account. I tried everything, but it just wouldn't. 

Jitsi just boots up and disappears. No splash screen, no interface, nothing hanging out in the system tray or indicator area, no nothing. But with system monitor, I can find it just sleeping on the system. Weird.

---

### Post by gradinaruvasile on 2012-05-09
How did you set up Linphone? You have the option to see the actual debug messages (help->show debug window).
As for Jitsi, what java version do you have installed?

---

### Post by areteichi on 2012-05-09
> **Dry Lips said:**
> I must admit that I've never tried it, but Blink is perhaps the only one of these clients that comes for Linux, Mac *and* Windows. (I'm not sure if it is open source, though.)

Jitsi is available on those three platforms:
[http://jitsi.org/index.php/Main/Download](http://jitsi.org/index.php/Main/Download)

Don't know how well it works on other systems, but it works quite well for me on Ubuntu.

---

### Post by Dry Lips on 2012-05-10
> **areteichi said:**
> Jitsi is available on those three platforms:
[http://jitsi.org/index.php/Main/Download](http://jitsi.org/index.php/Main/Download)

Don't know how well it works on other systems, but it works quite well for me on Ubuntu.

Great! I didn't know that! Does you know if Jitsi encrypt calls and instant messages?

---

### Post by Lars Noodén on 2012-05-10
I've been moving back and forth between Blink and Jitsi.  Blink has better logging for when network errors pop up.

---

### Post by dzsobacsi on 2012-05-10
> **Dry Lips said:**
> Great! I didn't know that! Does you know if Jitsi encrypt calls and instant messages?

Check out this site:
[http://en.wikipedia.org/wiki/Comparison_of_VoIP_software](http://en.wikipedia.org/wiki/Comparison_of_VoIP_software)

Here you can find a lot of info about a great amount of VOIP software with details about suppported platforms, license, supported protocols, encryption and so on. 

Jitsi provides voice encryption and signaling encryption whatever it means :)

---

### Post by Dry Lips on 2012-05-10
> **dzsobacsi said:**
> Check out this site:
[http://en.wikipedia.org/wiki/Comparison_of_VoIP_software](http://en.wikipedia.org/wiki/Comparison_of_VoIP_software)

Here you can find a lot of info about a great amount of VOIP software with details about suppported platforms, license, supported protocols, encryption and so on. 

Jitsi provides voice encryption and signaling encryption whatever it means :)

Thanks! I'm no expert on those encryption standards either. ;)

But Ekiga and Empathy don't have encryption? That's a quite serious lack IMO.

---

### Post by gradinaruvasile on 2012-05-10
> **Lars Noodén said:**
> I've been moving back and forth between Blink and Jitsi.  Blink has better logging for when network errors pop up.

They are more human readable. Jitsi has logs that show errors usually:

```

tail -f ~/.sip-communicator/log/jitsi0.log.0

```

It is full of java-specific mess but there are relevant lines also.

BTW in the Jitsi nightlies (build 4020 and up) there is native pulseaudio support.

> 
But Ekiga and Empathy don't have encryption? That's a quite serious lack IMO.


Encryption can be 2 tiered: 
1. The transport layer encryption:
What this means: the communication between you and the server is encrypted so a third part "onlooker" sees only encrypted data flowing.
Now this is fine and dandy, but the stream is decoded on the server so anything flows through the server can be recorded/listened to on the server.

This is used in Jabber/XMPP based  networks (google talk too) by default. All jabber clients support it because it is included in the specifications.
SIP - it has optional (very optional) tls encryption (not part of the standard rather an afterthought).
This is NOT supported by Ekiga at all and i think Empathy too lacks support for it. Jitsi, Sflphone,  supports SIP/TLS.

2. End-to-end encryption (also called zrtp or srtp): This is a supplementary layer of encryption, not really protocol dependent. It can be used through SIP or XMPP connections.
What it does: it encrypts the data BETWEEN THE 2 ENDPOINTS (the 2 talkers) so anything is said is encrypted BEFORE it is submitted to the transport layer (that can encrypt it again) so the data that reaches the server is already encrypted. This encryption has a on-the-fly method, called zrtp (or srtp) that is very handy in the regard that no encryption keys are needed (they are generated on the fly and a 4 letters phrase is presented to both sides, if it matches it means that the stream is not listened to) and it is built specifically to thwart "man-in-the-middle" attacks.
This type of encryption is supported by Jitsi on both SIP and XMPP protocols (i use it via google talk), by sflphone and Linphone (the recent 3.5 series) via SIP.

Notes: The SIP protocol is NOT designed with encryption in mind (it is built for controlled network environments). It can be used as an add-on feature but strictly the SIP standard doesnt include it so the implementations may vary and may be incompatible between various clients. Also SIP servers may not permit the pass through of encrypted data only if specific patches are applied to them (for example plain Asterisk doesnt work with zrtp).
The XMPP protocol on the other hand is designed by default with better default security not to mention more features like file transfer and much better internet traversal capability.

---

### Post by Dry Lips on 2012-05-10
**@gradinaruvasile: **Wow! Thanks a *lot*, sir! 

I think I might have found a replacement for Skype. :) Are zrtp enabled by default when using Jitsi with Google Talk and Jabber? (If both parts use Jitsi)

And what can you do with those keys that you can create for your accounts in Jitsi?

---

### Post by gradinaruvasile on 2012-05-11
zrtp is enabled by default. Also there are configurable options in the options menu (security->call tab->zrtp ninja). But in this case make sure that both jitsi instances use the same settings.

PS zrtp sometimes takes a couple seconds to complete the handshake process. Until the padlock is "unlocked" and has red beckground, it means encryption is not (yet) active.
After completion ther is nothing to be done, you do have the option to save the other sides zid, but thats not manadatory.

---

### Post by Dry Lips on 2012-05-12
> **gradinaruvasile said:**
> zrtp is enabled by default. Also there are configurable options in the options menu (security->call tab->zrtp ninja). But in this case make sure that both jitsi instances use the same settings.

PS zrtp sometimes takes a couple seconds to complete the handshake process. Until the padlock is "unlocked" and has red beckground, it means encryption is not (yet) active.
After completion ther is nothing to be done, you do have the option to save the other sides zid, but thats not manadatory.

Again, thanks a lot! :)

---

### Post by TheLastWilson on 2012-05-30
I went for Blink purely because I like the Google contacts sync. 

Do any of them integrate with the unity messages menu other then empathy(which I can not get to work with my SIP provider)?

---

### Post by Elv13 on 2012-05-30
SFLPhone KDE
[http://www.youtube.com/watch?v=VTnPd-gRzWY&noredirect=1](http://www.youtube.com/watch?v=VTnPd-gRzWY&noredirect=1)

(yes, I have a bias here)

---

### Post by gradinaruvasile on 2012-06-01
> **TheLastWilson said:**
> I went for Blink purely because I like the Google contacts sync. 


Jitsi has Google Contact sync too.

---

### Post by KegHead on 2012-07-02
Hi!

I've followed this tread and I'm curious what actually works with 12.04?

Thanks!

KegHead

---

### Post by dzsobacsi on 2012-07-03
I think that most of the previous mentioned programs shall run without any problem with 12.04
I use linphone right now. As a matter of fact I changed to Mint 13 since the start up this thread but it should not make any difference.
Jitsi seems to be another nice piece to try.

---

