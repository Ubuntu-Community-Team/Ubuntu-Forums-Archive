---
title: "Synapse IM client alpha release"
date: 2009-03-16
forum: The Cafe
---

### Post by FireRabbit on 2009-03-16
Hi everyone,

I just released an alpha version of Synapse, an IM application for Linux.

The website is [http://synapse.im/](http://synapse.im/), Ubuntu packages are of course available :).

Please let me know what you think! A few screenshots are below.

[CENTER]
[IMG]http://synapse.im/images/synapse-promo2.png[/IMG]
Buddy list window in grid mode and conversation window showing Flickr photo preview.

[IMG]http://synapse.im/images/screenshots/synapse-webpreview1.png[/IMG]
YouTube previews (NOTE: requires Jaunty)

[/CENTER]

---

### Post by chrish01 on 2009-03-16
It's been working great for me on jaunty, Congrats on the release! :P

---

### Post by Mr. Picklesworth on 2009-03-16
Oooh, looks fantastic. I like the XMPP focus :)

When this hits Windows it should be just enough to coax the more ninny-like of my friends away from MSN Messenger.
Then I can use Jabber exclusively and be happy.


Impressions after installing:
Cool graphics. I love how the faces move around when I resize the window and zoom in on them. Sadly, no buddy icons because, as mentioned, all my friends are on MSN (so it's through a Jabber-MSN transport).

Preferences->Add Account: "This feature is not yet implemented" WT?!!
I figured it out, don't worry.

Qt is almost indistinguishable from GTK now, with Jaunty, so I'm not mad at you for choosing it.

Not a huge fan of how this handles its own window dragging, even if it does mean awesome smooth interface. (Although it would be fine if the technology was more sensible, like we could create a window title bar widget that the window manager picked up and treated exactly like its own title bar). I miss being able to middle click on the title bar and have that drop the window to the bottom of the stack already.

I wish you the best of luck with this. With a client like this, we can leverage XMPP for as capable a social networking experience as, for example, Facebook... except more extensible and without the scary corporations being quite as scary. Oh, and better integrated, too, which is always awesome.

---

### Post by sports fan Matt on 2009-03-16
This looks interesting! What im protocols does it support? I cant seem to find this info.

---

### Post by FuturePilot on 2009-03-16
This looks very interesting. I also like the focus on XMPP. Keep up the good work! :D

---

### Post by FireRabbit on 2009-03-16
> **sox fan Matt said:**
> This looks interesting! What im protocols does it support? I cant seem to find this info.

Synapse supports XMPP natively, and will support other protocols through server-side transports. I explain why I decided on doing it this way in my blog post: [http://eric.extremeboredom.net/2009/03/15/336](http://eric.extremeboredom.net/2009/03/15/336).

---

### Post by sports fan Matt on 2009-03-16
just got an error trying to install and add the repo..just letting you know: W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 04508D5C1654E635

---

### Post by FireRabbit on 2009-03-16
> **sox fan Matt said:**
> just got an error trying to install and add the repo..just letting you know: W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 04508D5C1654E635

Hi Matt,

Sorry about that! I need to update the download page to explain how to fix this. The fast is way is to run the following command from a terminal:

```
sudo apt-key adv –recv-keys –keyserver keyserver.ubuntu.com 83419668f12469157bcd4be904508d5c1654e635
```

Official directions explaining how to do this are [here]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories"). You'll quickly see that it's a big pain in the butt, hopefully future versions of Ubuntu will automate some of this!

---

### Post by bryonak on 2009-03-16
First of all thumbs up for the work, it really looks nice!

When do you think will it support ICQ? Otherwise I've not much reason to try it ;)

How does your underlying "engine" compare to, lets say, the Telepathy framework?

Also I'd like to know how dependant it is on KDE libraries... actually I don't want to load any of those, since I don't feel that the additional CPU cycles and RAM space are justified on my laptop.

*EDIT: That is to say.. feel invited to convince me that your app justifies them ;)*

---

### Post by FuturePilot on 2009-03-16
> **bryonak said:**
> 

When do you think will it support ICQ? Otherwise I've not much reason to try it ;)

Also I'd like to know how dependant it is on KDE libraries... actually I don't want to load any of those, since I don't feel that the additional CPU cycles and RAM space are justified on my laptop.


I'm pretty sure Jabber/XMPP supports ICQ transports. Therefore it should work.

Also Qt != KDE. A pure Qt app will only depend on plain old Qt libs, nothing KDE would be involved.

---

### Post by FireRabbit on 2009-03-16
> **bryonak said:**
> First of all thumbs up for the work, it really looks nice!

When do you think will it support ICQ? Otherwise I've not much reason to try it ;)

How does your underlying "engine" compare to, lets say, the Telepathy framework?

Also I'd like to know how dependant it is on KDE libraries... actually I don't want to load any of those, since I don't feel that the additional CPU cycles and RAM space are justified on my laptop.

Thanks! As mentioned earlier, Synapse only speaks XMPP, but will be able to communicate with other protocols such as ICQ via transports in the near future. If you configure transports using another client such as Gajim they'll work in Synapse.

No KDE dependencies are required, only Qt which shouldn't be a big deal.

---

### Post by Twitch6000 on 2009-03-16
A rpm package would be nice :(.

---

### Post by Calmatory on 2009-03-16
Hmm, wasn't IRC invented in 1988, not in 1993 as your blog implies?

> IRC was created by Jarkko Oikarinen in late August 1988 to replace a program called MUT (MultiUser Talk) on a BBS called OuluBox in Finland. From wikipedia

...or did I misinterept something? :)

---

### Post by FireRabbit on 2009-03-16
> **Calmatory said:**
> Hmm, wasn't IRC invented in 1988, not in 1993 as your blog implies?

 From wikipedia

...or did I misinterept something? :)

Whoops, I wonder where I got 1993 from! Fixed, thanks :).

---

### Post by alex_esplin on 2009-03-23
Any plans to not store passwords in plain text???

I was a little alarmed to see my gmail and work mail server paswords just sitting there in the open when I was looking through the config files.

The interface looks good, but plaintext passwords are kind of a deal-breaker for me...

---

### Post by Starlight on 2009-03-23
That looks awesome! :) But almost everyone I know uses MSN, so I have a question... do MSN transports for XMPP support things like custom smileys, personal messages, and group chats?

---

### Post by FuturePilot on 2009-03-23
> **alex_esplin said:**
> Any plans to not store passwords in plain text???

I was a little alarmed to see my gmail and work mail server paswords just sitting there in the open when I was looking through the config files.

The interface looks good, but plaintext passwords are kind of a deal-breaker for me...

Almost every IM program does this, it's nothing new. Even Pidgin stores them in plain text.

---

### Post by MasterNetra on 2009-03-23
> **FuturePilot said:**
> Almost every IM program does this, it's nothing new. Even Pidgin stores them in plain text.

* has officially been discouraged from using Instant Messengers now*

---

### Post by binbash on 2009-03-23
Looks promising!

---

### Post by igor. on 2009-03-23
I read a blog post a while ago ([linky](http://carlo.zottmann.org/2007/01/19/jabber-openid-and-teh-shiny/)) that tries to explain why so many people use MSN messenger. As we all know, most people do not care about free software and open protocols. What they care about it "teh shiny". In order to make people switch to free software and open protocols, we must offer teh shiny. Synapse definately offers teh shiny.

Another interesting aspect is, that unlike pidgin Synapse only supports XMPP. If someone wants to use Synapse, he will have to use XMPP. I hope this will have success!

Very nice UI, I must say. It has a large shiny potential. :)

---

### Post by Polygon on 2009-03-23
> **MasterNetra said:**
> * has officially been discouraged from using Instant Messengers now*

at least pidgin held a survey and one of the features that they listed on the question 'what should we work on next?" is encrypted passwords.

but yeah encrypted passwords would be nice.

and this program looks sweet, but sadly i have a lot of people on aim/msn/yahoo........ and a lot of them are computer illiterate so telling them the benefits of xmmp over whatever they are using is like talking to a brick wall.

---

### Post by sardamil on 2009-09-15
I agree. Synapse looks great, but I need to be able to connect to msn, because like other people here most of my friends are on msn.

> **Mr. Picklesworth said:**
> 

Preferences->Add Account: "This feature is not yet implemented" WT?!!
I figured it out, don't worry.


Would you care to tell us how, because I got the same message?

If somebody can tell me how to install a msn transport, I'll start using Synapse now.

---

### Post by misfitpierce on 2009-09-15
Is it able to connect to AIM and how so? Is it built in or do you have to do this transport thing? If it's through a transport how would I set it up with AIM?

---

### Post by gnomeuser on 2009-09-15
> **alex_esplin said:**
> Any plans to not store passwords in plain text???

I was a little alarmed to see my gmail and work mail server paswords just sitting there in the open when I was looking through the config files.

The interface looks good, but plaintext passwords are kind of a deal-breaker for me...

I think we have have a solution for this coming up. The gnome-keyring people and the kwallet developer have been working on supporting a common dbus API for secrets meaning you should be able to store and request your entire keyring easily and securely over dbus regardless of which desktop you are using without degrading the experience.

Collaboration at it's finest thanks to FreeDesktop.org and people seeking solutions to real problems.

Hopefully the api will be helpful for applications like this.

also thank you for using Mono to create kickass applications, it always warms my heart to see that.

---

