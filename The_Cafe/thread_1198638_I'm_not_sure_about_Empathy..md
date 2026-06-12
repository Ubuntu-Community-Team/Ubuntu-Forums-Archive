---
title: "I'm not sure about Empathy."
date: 2009-06-27
forum: The Cafe
---

### Post by calrogman on 2009-06-27
Now, I don't know about you guys, but from what I have heard a lot of you are upset that Pidgin is being scrapped in favor of Empathy in Ubuntu 9.10.

I tried Empathy (3 times) and whenever my laptop dropped its wifi connection, Empathy wouldn't let me reconnect to MSN.  Everything else was fine, but when I clicked the reconnect button, it'd say "network error" (after no delay, it wasn't checking) and I'd be prompted to hit the reconnect button again.  The only way to fix this without closing Empathy was to run ```
killall -9 telepathy-butterfly
```in a terminal.

I'm not really sure about you, but I don't consider that a good, or even stable piece of software.

Which do you prefer, Pidgin or Empathy, and why?

---

### Post by MikeTheC on 2009-06-27
Well, I use Adium X myself, so I'm not sure if I can empathize with you on this.

Then again...

---

### Post by steeleyuk on 2009-06-27
The network error bug is known. Fix is still being waited on though.

---

### Post by calrogman on 2009-06-27
> **steeleyuk said:**
> Fix is still being waited on though.

What's hard about pinging www.google.com and messenger.hotmail.com, comparing the resuts and figuring out if the network is up, down or if MSN is simply temporarily offline?

---

### Post by Spiritous on 2009-06-27
Not too bothered... If it lets me log on, I'm a happy hippo :)

---

### Post by calrogman on 2009-06-27
And if it doesn't let you log in?

---

### Post by Spiritous on 2009-06-27
Can't find any kind of rhyming animal for that...

---

### Post by calrogman on 2009-06-27
Alliterating animal actually.  Another alliteration, amazing!

---

### Post by Spiritous on 2009-06-27
My _**head hurts**_... Omg more alliteration o.O!

---

### Post by LookTJ on 2009-06-27
As of right now, My Multi-IM of choice is Pidgin.

---

### Post by 0per4t0r on 2009-06-27
Pidgin and Emesene are great.

---

### Post by heyyy on 2009-07-27
why Pidgin is being scrapped in favor of Empathy ?
is it better?
is it a license thing?
does it have more features?

---

### Post by ibuclaw on 2009-07-27
Now I prefer to rhyme in sync with ten.
Iambic pentameter for the win!
Since simplicity says it all for me.
That is why I opted for bit-l-bee!

:D

btw: please don't put in useless tags. Stay ontopic, and keep it constructive. Thank-you.

---

### Post by calrogman on 2009-07-27
> **heyyy said:**
> why Pidgin is being scrapped in favor of Empathy ?
is it better?
is it a license thing?
does it have more features?

It's more "user-friendly" and integrates better with GNOME apparently.

Here have a [link]("https://lists.ubuntu.com/archives/ubuntu-desktop/2009-June/002099.html") to a post in the mailing list.

---

### Post by potrick on 2009-07-27
There's also the non-trivial inclusion of audio and video messaging support in Empathy. Pidgin's promised this for years with seemingly no results, but Empathy has it now. For many new user's Ubuntu not being able to do this out of the box is a real show-stopper. 

I just hope by the new Ubuntu release someone's worked out a way to import Pidgin logs into Empathy--if Empathy could do that I'd switch right now.

---

### Post by Regenweald on 2009-07-27
I don't use instant messengers at all but my understanding is that Empathy is in heavy development/testing to be ready for inclusion in karmic final. File those bug reports and help development along. It may not be 100% currently but it could be very soon with your help. it's been decided that this is the way forward for Ubuntu so rather than a vs thread why not start a collective bug report thread ?

---

### Post by calrogman on 2009-07-27
> **potrick said:**
> There's also the non-trivial inclusion of audio and video messaging support in Empathy

And the non-trivial lack of support for file transfers.

---

### Post by Tibuda on 2009-07-28
> **heyyy said:**
> why Pidgin is being scrapped in favor of Empathy ?
is it better?
is it a license thing?
does it have more features?

Empathy got less features, but it supports video chat in some protocols, so I think it is better for the default IM program. I'll stick to Pidgin, as I don't use video chat.

---

### Post by sertse on 2009-07-28
> **calrogman said:**
> And the non-trivial lack of support for file transfers.

Alternatives to file transfering (email?) is much easier than alternatives to video/audio chat (i.e , get your you and your friend to sign up for skype, and use the skype client etc etc).

Anyways maybe I just haven't explore it well enough, but where are the options for text formatting and avatars?

---

### Post by Regenweald on 2009-07-28
> **calrogman said:**
> And the non-trivial lack of support for file transfers.

look up BaShare.

---

### Post by calrogman on 2009-07-28
> **sertse said:**
> where are the options for text formatting and avatars?

In pidgin.

---

### Post by Mr. Picklesworth on 2009-07-28
> **calrogman said:**
> And the non-trivial lack of support for file transfers.

This isn't true. Empathy supports file transfers with XMPP, and I believe telepathy-butterfly support for that is coming when the API gets touched up.

Also, the integration stuff is not specific to GNOME. It is desktop-neutral functionality and could be extremely cool when it gets to be widely used. (GNOME 2.28 will at least use it for multiplayer in Sudoku - yes, Sudoku -, to give you a taster). It's absolutely worthwhile to drop Pidgin for Empathy. It's understandable so long as people don't fall into the assumption that instant messaging == a buddy list. Empathy is about a lot more than the buddy list and the chat window. In very vague terms, it is about harnessing messaging protocols as proper infrastructure instead of specific applications.

---

### Post by potrick on 2009-07-28
Okay guys, here's how it works.

Scenario 1: Pidgin as default

New Users: What the crap? No support for video messaging? Ubuntu sucks. 

Old Users: LOL, NEWB. Install Skype and somehow convince all of your friend to as well. 

Scenario 2: Empathy as default

New Users: use video and audio as expected, without noticing Pidgin lacks file transfers. 

Old Users: type "sudo apt-get install pidgin" 



The End.

---

### Post by Nevon on 2009-07-28
> **potrick said:**
> Scenario 2: Empathy as default

New Users: use video and audio as expected, without noticing Pidgin lacks file transfers.

I assume you mean Empathy lacks file transfers? In that case, I think that it will go more like this:

Empathy as default

New Users: try to use video and audio in MSN. Doesn't work. Try to send files over MSN. Doesn't work. Go to support forums and ask for help. Gets the following reply:

sudo apt-get install amsn

New user: Takes one look at amsn, cries and asks their slightly tech savvy friend to install a pirated version of Windows XP instead.

---

### Post by Orlsend on 2009-07-28
I used Pidgin Since 8.04, a couple days ago I gave Empathy a try. (Similar, but I still think pidgin is better)

I guess ill be ticked off in karmic....

---

### Post by Mr. Picklesworth on 2009-07-28
Here are the slides from a nice presentation on the collaborative desktop, from GCDS:

[http://people.canonical.com/~jriddell/gcds-presentations-2009/Guillaume%20Desmottes,%20make%20GNOME%20a%20collaborative%20desktop.pdf](http://people.canonical.com/~jriddell/gcds-presentations-2009/Guillaume%20Desmottes,%20make%20GNOME%20a%20collaborative%20desktop.pdf)

Sorry, can't find a video, but the slideshow is pretty cool. Mostly mockups, but I think it pretty nicely shows the potential here and why it matters :)

---

### Post by SQuark on 2009-08-24
> **Nevon said:**
> Gets the following reply:

sudo apt-get install amsn

New user: Takes one look at amsn, cries and asks their slightly tech savvy friend to install a pirated version of Windows XP instead.

Alternatively, they'll be told to install Emesene 1.5 and new user will be a happy bunny.

> **Mr. Picklesworth said:**
> [http://people.canonical.com/~jriddell/gcds-presentations-2009/Guillaume%20Desmottes,%20make%20GNOME%20a%20collaborative%20desktop.pdf](http://people.canonical.com/~jriddell/gcds-presentations-2009/Guillaume%20Desmottes,%20make%20GNOME%20a%20collaborative%20desktop.pdf)

Sorry, can't find a video, but the slideshow is pretty cool. Mostly mockups, but I think it pretty nicely shows the potential here and why it matters :)

Looking good! Can't wait to try some of that. :D

---

