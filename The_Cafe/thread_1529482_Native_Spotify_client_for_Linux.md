---
title: "Native Spotify client for Linux"
date: 2010-07-12
forum: The Cafe
---

### Post by qualtch on 2010-07-12
Shortly: Dear fellow Ubuntuers. Linux users' wishes have been heard, behold the [native linux version of Spotify!]("http://www.spotify.com/fi/blog/archives/2010/07/12/linux/") ^_^

---

### Post by [h2o] on 2010-07-12
Using it now, and although there are still some quirks I'd be surprised if they weren't fixed quite soon.

---

### Post by RussellGee on 2010-07-12
awesome news :) although wine does actually work perfectly this is great news. installing right now.

---

### Post by Old Marcus on 2010-07-12
Awesome, now I just have to wait for it to be available to free members. (Yes, I'm a tightwad. :P)

---

### Post by wolf_3d on 2010-07-12
Yes its good news, but this is only available if you have a Premium Account as they haven't found a way for the ads to work.

I hope they come up with a way for the free accounts to work but I suspect they'll keep it only for premium users.

---

### Post by gnomeuser on 2010-07-12
Waiting for the danish licensing agencies to agree to the payout terms, but much yay!

Now hopefully they won't be opposed to something like despotify so we can have completely open support for their excellent service and more importantly, integration with our platform (in my case a Banshee plugin would be great).

---

### Post by Johnsie on 2010-07-12
Nice, although spotify ran pretty well with Wine. Looking forward to checking it out next time I boot into Ubuntu

---

### Post by xpod on 2010-07-12
Seems i no longer have need of Wine, not that i had too much *need* of it in the first place. Spotify though was one of the 2 programs i found myself installing Wine for about a year or so after i first began using Ubuntu. I`d never needed Wine for any Windows only software but Spotify seemed like such a great idea, especially for the kids. 
The other program was Teamviewer but of course that too now has a native Linux client so Wine is pretty pointless for me once again, just as it had been to start out with.

---

### Post by Åtta on 2010-07-12
Too bad it's only for premium users. I can't wait to try it out once it becomes available for Free and Open users.

---

### Post by FuturePilot on 2010-07-12
> **xpod said:**
> 
The other program was Teamviewer but of course that too now has a native Linux client 
It actually uses a static version of Wine like Picasa does so it's not native, but that is a different discussion.

---

### Post by xpod on 2010-07-12
> **FuturePilot said:**
> It actually uses a static version of Wine like Picasa does so it's not native, but that is a different discussion.

Yeah, i actually remember now. Cheers for reminding me.:D
My brains like a sieve at times so it is.

---

### Post by [h2o] on 2010-07-12
> **wolf_3d said:**
> I hope they come up with a way for the free accounts to work but I suspect they'll keep it only for premium users.
Looking at the comments from their support forums it seems like this is a technical problem, and not a political/marketing issue.
I can't really think of anything to gain from not allowing free accounts play music from the native Linux client when it works under Wine.

---

### Post by wolf_3d on 2010-07-12
> **'[h2o] said:**
> Looking at the comments from their support forums it seems like this is a technical problem, and not a political/marketing issue.
I can't really think of anything to gain from not allowing free accounts play music from the native Linux client when it works under Wine.

Yeh I can see what your saying. I was thinking that it could end up being an extra incentive to get people to renew or upgrade to premium accounts.

---

### Post by 1Michael1 on 2010-07-12
Hmm, that's weird.

I did everything as the page said.

Although I get this message when I try to install the package (apt-get install spotify-client-gnome-support).

The following packages have dependencies that can not be satisfied:
  spotify-client-gnome-support: Depends on: gconf2 (> = 2.28.1-2) but 2.28.1-0ubuntu1 will be installed
E: Broken packages

So, apt-get install spotify-client-qt seems to work while apt-get install spotify-client-gnome-support doesn't seem to work.

I know that I might just be able to skip that package and that it'd work without that package as I've been told but the Spotify client doesn't seem to show up under my Applications. (It's at usr/bin and works from there)

Anyone familiar with the problem?

Thanks.

---

### Post by Åtta on 2010-07-12
> **1Michael1 said:**
> Anyone familiar with the problem?
Yeah, it's been posted pretty much everywhere. For now, you can just install it using aptitude instead of apt-get, and it'll work fine.

---

### Post by chewit on 2010-07-12
Does anyone have a Spotify Unlimited Account? Can you log into Spotify Linux with an Unlimited Account?

Since its an Ad issue, unlimited accounts should have access also.

---

### Post by LakesideLoafer on 2010-07-12
Tried using aptitude to install but still have unmet dependencies and I am not certain how to resolve by hand. Any clues?

---

### Post by hallon on 2010-07-13
Get the same problem :S  spotify-client-gnome-support:
  Depends: gconf2 (>=2.28.1-2) but 2.28.1-0ubuntu1 is to be installed

But the QT version runs very well so it's no problem really :)

---

### Post by AbtZ on 2010-07-13
> **LakesideLoafer said:**
> Tried using aptitude to install but still have unmet dependencies and I am not certain how to resolve by hand. Any clues?
Here:
[http://www.google.com/buzz/bishillo/iHivbFm1sZd/How-to-fix-spotify-packages-for-installing-in](http://www.google.com/buzz/bishillo/iHivbFm1sZd/How-to-fix-spotify-packages-for-installing-in)

Tried it, liked it -- although it has some issues, it better obeys the WM than when running it through Wine. It works properly with the Grid Compiz plugin now for example, the mouse pointer doesn't change to look like some ugly Windows XP pointer, and fonts are anti-aliased. Yay.

---

### Post by hallon on 2010-07-13
> **AbtZ said:**
> Here:
[http://www.google.com/buzz/bishillo/iHivbFm1sZd/How-to-fix-spotify-packages-for-installing-in](http://www.google.com/buzz/bishillo/iHivbFm1sZd/How-to-fix-spotify-packages-for-installing-in)

Tried it, liked it -- although it has some issues, it better obeys the WM than when running it through Wine. It works properly with the Grid Compiz plugin now for example, the mouse pointer doesn't change to look like some ugly Windows XP pointer, and fonts are anti-aliased. Yay.

:) thanks for that link, gonna try it now!

worked wonderfully! here's a dropbox link to anyone too lazy to follow the discriptions under AbtZ link :) all fixed and ready to install.
[http://dl.dropbox.com/u/1551430/spotify-client-gnome-support_0.4.6.50.g0aa5286-1_all.deb](http://dl.dropbox.com/u/1551430/spotify-client-gnome-support_0.4.6.50.g0aa5286-1_all.deb)
I take no responsibilities to whatever happens to your pet if you install the above package. ^_^

---

### Post by LakesideLoafer on 2010-07-13
Anyone had any success using playlist links from web sites such as sharemyplaylists? Only just got it set up to integrate into the Wine version last week and now, even when I try to get it to use the native Spotify client, nothing happens.

---

### Post by suoko on 2010-07-14
unfortunately here in italy i'm behind proxy idiots
can you open them pls ?

---

### Post by chriswyatt on 2010-07-14
Balls, you can't get the free version in the UK, also my internet connection is terrible so it probably wouldn't be able to stream properly anyway.

---

### Post by LakesideLoafer on 2010-07-19
Upgraded a few days ago. The Gnome client is now present but I can't see what difference it has made, and editing preferences now crashes the program. :(

---

### Post by beetleman64 on 2010-07-19
With Steam and Spotify on board, this could be a sign of Linux coming of age. Let's hope the FSF don't get in the way.

---

### Post by qualtch on 2010-07-19
> **beetleman64 said:**
> Let's hope the FSF don't get in the way.

What do you exactly mean by this?

EDIT: I'm going offtopic again... Never mind. :)

---

### Post by devolute on 2010-07-28
Any suggestions on how to get links from Firefox working now we have a native (well, -ish) client would be greatly appreciated.

---

### Post by bjornolai on 2010-08-05
> Any suggestions on how to get links from Firefox working now we have a native (well, -ish) client would be greatly appreciated. 

Combining a few articles on adding protocols to Firefox I have it working after running these two commands in terminal:

```
gconftool-2 -s /desktop/gnome/url-handlers/spotify/command '/usr/bin/spotify /uri %s' --type String
```

```
gconftool-2 -s /desktop/gnome/url-handlers/spotify/enabled --type Boolean true
```

This should associate the Spotify protocol with Sportify (which after a normal install is located at /usr/bin/spotify and requires the argument "uri" to open links). 

No more: "Firefox doesn't know how to open this address, because the protocol (spotify) isn't associated with any program"

---

### Post by repunante on 2010-11-11
I upgraded but the multimedia keys don't work, I think I will stay with Wine.

---

### Post by Mmmbopdowedop on 2010-11-11
> **chriswyatt said:**
> Balls, you can't get the free version in the UK, also my internet connection is terrible so it probably wouldn't be able to stream properly anyway.

You can get the free version in the UK;
Just not the native linux app, you can still use Spotify in Wine for free. :)

---

