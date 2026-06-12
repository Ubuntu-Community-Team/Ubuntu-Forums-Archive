---
title: "oracle and virtual box ideal settings"
date: 2012-02-07
forum: Virtualisation
---

### Post by degarb on 2012-02-07
I have at lest 4 questions.

I recently disconnected the cable.  But wife and kids are not happy with the 27 local tv stations via antenna, plus Netflix, plus library dvds.  So, I poked around "googled play Hulu on Wii".  I quickly found playon.tv, which gave the wii, hulu/disney/nick/hgtv and scores of other tv stations for free, by transcoding flv and serving it via dlna--all controlled with the wii remote.  This works pretty good, using my 1.6 atom xp machine as the playon server.  However, I want to use my 3.4 p4 Unbuntu as the playon server (playon.tv doesn't have a linux server, and I doubt if wine can do ie7+dotnet+ffmpeg+and the server, in wine).

I have a virtualbox xp running on this p4 machine 3.4 ghz.  However, the video serve very poorly (bridged network), like on a 1.5 ghz.   I cannot get logged into the virtualbox forum for last few days, to find out ideal settings.  My attempts to tweak the virtualbox have severely degraded the machine performance to point of locking up the entire linux machine.

I spent 3 days googling, and concluded there is no alternative to playon.tv, certainly no linux alternative.  The only windows alternative is tversity, which lacks channels, but allows rss feeds (pita).  The problem with tversity is I cannot get even any online video to transcode and serve, on my 1.6 atom or 2.4 p4.  So, since it is such a pig, it probably is not worth effort trying in the linux box.   ....  My other alternative is to buy a ruku2 or sone, or boxee, but I seriously doubt they will offer much free programming, unlike playon, and they are pricey, cutting into my savings toward the next $400 laptop I wish to buy and for which I am putting away $2 each month for the last few years.

With that background, you can guess my 4 questions: 1. What do I need to do to get playon.tv to serve video smoothly, in a virtualbox and on a p4 3.4 hyperthreading intel?2. What is Up with forum at virtualbox.org ? 3. How soon will there be a playon.tv alternative (not just a dnla, which is boring.) that an average person can get running in 5 minutes or less (not usual 2 days)? 4. How much free stuff can you get (on a 768kps cable) on the sony, ruku2, and boxee?

---

### Post by japzone on 2012-02-07
I never reccomend Converting Video(Especially Transcoding) on a VM because you'll always suffer decreased performance and often get undesirable effects. Unless you're willing to install  Windows to a Second Partition and Boot into that, you'll have to just stick with using the Windows Machine you already have.

Here's my streaming expirience:

I've used a Wii before and Streaming content for it just never worked out even after SoftModding it. The Wii just isn't well suited for Streaming media because the only way to do it is by using Flash( v8 ) in the Browser and that hardly ever worked right. The Wii is just outdated and never got the same attention from the Media Companies like the PS3 and 360 got. However, if you SoftMod your Wii and install [**WiiMC**]("http://wiibrew.org/wiki/WiiMC") then the Wii works great for Playing Standard Def videos from an External Harddrive or Local Network (FTP,SMB). Other than that I'd reccomend at looking into the Below options.

Look into getting a [**Roku Box**]("http://www.roku.com/roku-products#3"). They're cheap(Models start at $50) and have 400+ channels of content supported including Netflix and Hulu Plus. My Family cut the cable awhile ago and now use OTA channels and Roku boxes(with Netflix Subscription) for everything else. You can browse the Official Roku Content Selection, which contains alot of Free Content on it's own, [**here**]("http://www.roku.com/roku-channel-store"). You can browse Private channels, which contains mostly free content, (Content available outside of the Official Store) [**here**]("http://www.roku-channels.com/"). I also recommend any Content made by [**TheNowhereMan**]("http://www.thenowhereman.com/roku/").

Besides that I'd recommend looking into making an HTPC using Boxee or XBMC. I have XBMC setup on a Laptop and I can stream from Many sources Including Hulu(Normal and Plus supported) and Amazon VOD(Buy content using PC first)/Prime Streaming(XBMC Eden Beta required for some Plugins like Hulu and Amazon). You can also get Netflix support if you use Windows as the Base OS for the HTPC.

Plex is a possible Playon replacement as it has a Linux Server but it's still lacking in the Content department.

PS: I'm having no trouble getting on Virtualbox.org so I don't know why you can't.

---

### Post by CharlesA on 2012-02-07
You can do Netflix in a VM, but the performance might be spotty, depending on what specs the host machine has.

I'd go with a bluray player, console or even a Roku for streaming to a TV - easier to deal with, and that's what I use.

---

### Post by Habitual on 2012-02-08
> **japzone said:**
> ...Look into getting a [**Roku Box**]("http://www.roku.com/roku-products#3"). They're cheap(Models start at $50) and have 400+ channels of content supported including Netflix and Hulu Plus....

+1 roku

---

### Post by degarb on 2012-02-08
> **japzone said:**
> I never reccomend Converting Video(Especially Transcoding) on a VM because you'll always suffer decreased performance and often get undesirable effects. Unless you're willing to install  Windows to a Second Partition and Boot into that, you'll have to just stick with using the Windows Machine you already have.

Here's my streaming expirience:

I've used a Wii before and Streaming content for it just never worked out even after SoftModding it. The Wii just isn't well suited for Streaming media because the only way to do it is by using Flash( v8 ) in the Browser and that hardly ever worked right. The Wii is just outdated and never got the same attention from the Media Companies like the PS3 and 360 got. However, if you SoftMod your Wii and install [**WiiMC**]("http://wiibrew.org/wiki/WiiMC") then the Wii works great for Playing Standard Def videos from an External Harddrive or Local Network (FTP,SMB). Other than that I'd reccomend at looking into the Below options.

Look into getting a [**Roku Box**]("http://www.roku.com/roku-products#3"). They're cheap(Models start at $50) and have 400+ channels of content supported including Netflix and Hulu Plus. My Family cut the cable awhile ago and now use OTA channels and Roku boxes(with Netflix Subscription) for everything else. You can browse the Official Roku Content Selection, which contains alot of Free Content on it's own, [**here**]("http://www.roku.com/roku-channel-store"). You can browse Private channels, which contains mostly free content, (Content available outside of the Official Store) [**here**]("http://www.roku-channels.com/"). I also recommend any Content made by [**TheNowhereMan**]("http://www.thenowhereman.com/roku/").

Besides that I'd recommend looking into making an HTPC using Boxee or XBMC. I have XBMC setup on a Laptop and I can stream from Many sources Including Hulu(Normal and Plus supported) and Amazon VOD(Buy content using PC first)/Prime Streaming(XBMC Eden Beta required for some Plugins like Hulu and Amazon). You can also get Netflix support if you use Windows as the Base OS for the HTPC.

Plex is a possible Playon replacement as it has a Linux Server but it's still lacking in the Content department.

PS: I'm having no trouble getting on Virtualbox.org so I don't know why you can't.


Great post.  I was hoping to hear from someone with experience.

My head is reeling with all the info and more questions. I will try an initial list:

1.  I read Roku requires a code each time you wish to watch a private free channel, which could be a real pain.

2.  I read [Western Digital TV Live]("https://www.google.com/search?q=western+digital+live+player&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a") may be better.  But I am unsure still of the details, like if you need to run a server to watch channels with it.

3.  I am thinking that adding an extra 1 gig ram to the 3.2 ghz p4 and bumping up vbox xp to gig isn't going to be enough.  Perhaps, the vmachine cannot see both cores (or simulated cores on my case).  Also, I bet adding ram won't help, since  I see the xp in the vbox process using 100 percent cpu when trying to run playontv server in vbox, whereas I only use about 40 percent of my atom 1.6 xp, in which runs well.

4.  I had no luck trying to install tversity and playon under wine.  Even, ruined my wine explorer 6, trying to upgrade.

5. If I install xp in another partition, wont it grab the boot loader?

6.  I have no info if any box can do hulu for free.   For the low quality of pro they offer, I would value Hulu at about $2 a month, though better than just Netflix (which is still lacking in quality movies) alone. No good comparison chart or review, other than one poster that tried several.

7.  My local target has a Sony something-200 for $69.  Not sure if a good deal.

8.  Home-brew is tempting, until you weigh the risks of bricking the unit  the confusing doc regarding method on their wiki, and low quality of home-brew aps (I don't see real games for the kids.)  I bet bricking it would be outside the warranty.  I won't ask if it is hard, since I am in a Linux community, which are hisorically known for high tolerance for non intuitive, non humanly readable, lack of memorable methods, and obfuscation......So far, I think the wii is perfect for netflix (480p) and sure the Hulu via Playon isn't the visual quality of Netflix, but many of the programs (served from my wireless atom 1.6 and on a sub par 768 cable connection) are at least in the class of NTSC and mpeg 2 (480p) OTA signals.  Trying for a tad more quality with an wimc flash 10 (which may soon come anyway via official wii update), is a risk I will take after reading a thread with unanimous success of other users.

9.  In regards to the need to installing xp as primary boot (which sucks, because my dream OS is Ubuntu with XP in a virtualbox on a fast machine):   Also the concern about vbox going slow on encoding video worries me.  Apart from the ton on audio transcoding my machine does daily, I also do a good deal of ripping and brakedir encoding, to back up my stuff in the now unlikely event of a late fee or a scratch.  I use a windows only script that I had to spend a week to write because I couldn't get anything but ad hominid ridicule (by their moderator) for suggesting an improvement (settings that always stick and one click encoding of entire directories, without further dialogs)

---

### Post by japzone on 2012-02-08
> **degarb said:**
> Great post.  I was hoping to hear from someone with experience.

My head is reeling with all the info and more questions. I will try an initial list:

1.  I read Roku requires a code each time you wish to watch a private free channel, which could be a real pain.

2.  I read [Western Digital TV Live]("https://www.google.com/search?q=western+digital+live+player&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a") may be better.  But I am unsure still of the details, like if you need to run a server to watch channels with it.

3.  I am thinking that adding an extra 1 gig ram to the 3.2 ghz p4 and bumping up vbox xp to gig isn't going to be enough.  Perhaps, the vmachine cannot see both cores (or simulated cores on my case).  Also, I bet adding ram won't help, since  I see the xp in the vbox process using 100 percent cpu when trying to run playontv server in vbox, whereas I only use about 40 percent of my atom 1.6 xp, in which runs well.

4.  I had no luck trying to install tversity and playon under wine.  Even, ruined my wine explorer 6, trying to upgrade.

5. If I install xp in another partition, wont it grab the boot loader?

6.  I have no info if any box can do hulu for free.   For the low quality they offer, I would value Hulu at about $2 a month, though better than just Netflix (which is still lacking in quality movies) alone. No good comparison chart or review, other than one poster that tried several.

7.  My local target has a Sony something-200 for $69.  Not sure if a good deal.

8.  Home-brew is tempting, until you weigh the risks of bricking the unit  the confusing doc regarding method on their wiki, and low quality of home-brew aps (I don't see real games for the kids.)  I bet bricking it would be outside the warranty.  I won't ask if it is hard, since I am in a Linux community, which are hisorically known for high tolerance for non intuitive, non humanly readable, lack of memorable methods, and obfuscation......So far, I think the wii is perfect for netflix (480p) and sure the Hulu via Playon isn't the visual quality of Netflix, but many of the programs (served from my wireless atom 1.6 and on a sub par 768 cable connection) are at least in the class of NTSC and mpeg 2 (480p) OTA signals.  Trying for a tad more quality with an wimc flash 10 (which may soon come anyway via official wii update), is a risk I will take after reading a thread with unanimous success of other users.

9.  In regards to the need to installing xp as primary boot (which sucks, because my dream OS is Ubuntu with XP in a virtualbox on a fast machine):   Also the concern about vbox going slow on encoding video worries me.  Apart from the ton on audio transcoding my machine does daily, I also do a good deal of ripping and brakedir encoding, to back up my stuff in the now unlikely event of a late fee or a scratch.  I use a windows only script that I had to spend a week to write because I couldn't get anything but ad hominid ridicule (by their moderator) for suggesting an improvement (settings that always stick and one click encoding of entire directories, without further dialogs)

Answers:

1. You only nead a Code to Install the Private Channel to your Roku, once installed the Private Channel will sync to all Rokus attached to your account and they will Update automatically or whenever you Enter and Exit the Channel Store.

2. WDLive
Pros: Has Youtube, and has robust File Support for playing Videos over your Home Network(SMB,FTP,UPNP,ect) or from an External USB Drive
Cons: Streaming Content Library is significantly smaller than the Roku's

3. As I stated before, Converting/Transcoding inside a VM is not reccomended. 32-bit PCs and OSs can only see about 3gb of RAM unless you install the PAE kernal for Ubuntu which bumps the supported RAM to 4gb. It's still a better Idea to have a Dedicated PC for such uses and not a VM.

4. Installing Transcoders inside Wine has never worked out for me. WineHQ reports that nobody has successfully gotten PlayOn to work and Tversity has had no useful progress.

5. Refer to this guide in order to Dual-Boot Windows and Ubuntu: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

6. Currently the only way to watch Hulu for free on a TV(Without a Transcoder like PlayOn) is to use a PC hooked up to the TV(aka: an HTPC) and either Open hulu.com in a Web Browser, Download the [**Hulu Desktop client**](http://www.hulu.com/hulu-desktop), or Install [**XBMC Eden Beta**](http://xbmc.org/download/) and the [**Hulu Plugin from Bluecop**](http://forum.xbmc.org/showthread.php?t=121023) and ensure that librtmp v2.4 is installed(available in the Universe repositories in Ubuntu under the name librtmp0)

7. Not really, WDLive and Roku are better deals

8. Wii will never get an Updated Flash Plugin. Wii Homebrew is actually not that risky unless you start doing some really fancy things(like running Wii Games from an External Drive). Your Wii's Warranty has probably expired already anyway, unless you bought it second quarter of Last Year or sooner. Hacking the Wii is pretty simple and Nintendo has pretty much given up on trying to squash it. [http://wiibrew.org/wiki/Homebrew_Channel](http://wiibrew.org/wiki/Homebrew_Channel) and [http://wiibrew.org/wiki/Homebrew_Browser](http://wiibrew.org/wiki/Homebrew_Browser) and [http://wiibrew.org/wiki/WiiMC](http://wiibrew.org/wiki/WiiMC)

9. Refer to Answer 3

Anything else?

---

### Post by degarb on 2012-02-08
Thanks.  To the point and clear!  I will ponder for a few days and further research several of the point above.  Some interesting suggestions, and sounds like you tried them.

I really don't want to have to boot into xp, if I can avoid it.  One last thing to note on my system, I am about 1 version behind on my virtual box.  Not on the linux machine now, but I think like virtualbox 4.0 and could go to 4.1, or something similar like that.  Probably, no performance difference, I suppose.  But I guess I need to update it.  Problem is that Ubuntu will not let me.  I must fully remove old off, then install new.  Will it remove the VM?  I have vague recollections in back of my mind, of doing this before and it didn't remove the VM.  Maybe.  Simply clicking remove package and install new, via synaptic wouldn't work for some odd reason.

Also, while I bought $100 of the accessories or more for this Wii, the actual wii was a gift from someone else to my daughter.  So, I need to be 100 percent certain, I don't brick it with home brew.  I do admit I see a big improvement in Flash in the last year.  Does come close to silverlight or wmv for smoothness, yet, on single cores, but finally it has become watchable in full screen with a single core 2 ghz.  So, an improvement on the wii v 8 flashplayer is very tempting.  But, as my mother always asked, "Would you jump off a bridge, if your friend told you to?" I now, in this century, could reply that it depends on how many lives one has left.

---

### Post by japzone on 2012-02-09
> **degarb said:**
> Thanks.  To the point and clear!  I will ponder for a few days and further research several of the point above.  Some interesting suggestions, and sounds like you tried them.

I really don't want to have to boot into xp, if I can avoid it.  One last thing to note on my system, I am about 1 version behind on my virtual box.  Not on the linux machine now, but I think like virtualbox 4.0 and could go to 4.1, or something similar like that.  Probably, no performance difference, I suppose.  But I guess I need to update it.  Problem is that Ubuntu will not let me.  I must fully remove old off, then install new.  Will it remove the VM?  I have vague recollections in back of my mind, of doing this before and it didn't remove the VM.  Maybe.  Simply clicking remove package and install new, via synaptic wouldn't work for some odd reason.

Also, while I bought $100 of the accessories or more for this Wii, the actual wii was a gift from someone else to my daughter.  So, I need to be 100 percent certain, I don't brick it with home brew.  I do admit I see a big improvement in Flash in the last year.  Does come close to silverlight or wmv for smoothness, yet, on single cores, but finally it has become watchable in full screen with a single core 2 ghz.  So, an improvement on the wii v 8 flashplayer is very tempting.  But, as my mother always asked, "Would you jump off a bridge, if your friend told you to?" I now, in this century, could reply that it depends on how many lives one has left.

Uninstalling Virtualbox shouldn't delete your VMs. You need to Uninstall VirtualBox and then install it from the VirtualBox.org website via the DEB or PPA, not the Ubuntu Repositories.

Yeah if it isn't your Wii then it wouldn't be a good idea to Mod your Daughter's. Also what I said regarding Flash on the Wii was that it is currently Flash v8(While PC is v11) and it will not be updated because: 1, Nintendo isn't interested/doesn't care, 2, Nintendo ended it's deal with Opera(the makers of the Wii's Browser) , 3, Adobe has dropped developement for Flash on all Platforms Except PC, and 4, The Wii probably couldn't handle it anyway.

---

