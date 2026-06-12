---
title: "Pidgin 2.5.6 Released!"
date: 2009-05-20
forum: The Cafe
---

### Post by Kosimo on 2009-05-20
Pidgin 2.5.6 has been quietly released. 

Here the changelog:

>  libpurple:
     * Improve sleep behavior by aggregation of longer timeouts on second
       boundaries to allow better power saving.  (Arunan Balasubramaniam)
     * Fix various crashes on exit.
     * Make XML parsing more resilient to interactions with other libraries.
       This, along with the fix for libxml2 bug 564217, fixes the crashes
       on connect in XMPP with recent gst-plugins-bad (see #8830 for details).
     * Many security related fixes
 .
   IRC:
     * Correctly handle WHOIS for users who are joined to a large number of
       channels.
     * Notify the user if a /nick command fails, rather than trying
       fallback nicks.
 .
   MSN:
     * Fix a race condition causing occasional Pidgin crashes.
     * Fix some errors about the friendly name changing too fast caused
       by MSN/Yahoo integration buddies.
 .
   XMPP:
     * Less likely to pop up a new conversation window in disregard of
       the "Hide new IM conversations" preference.
 .
   Yahoo:
     * Fix a crash when sending very long messages.
     * Fix a bug where UTF-8 status messages get garbled when going idle.



It'll appear in pidgin.im website soon.


At the moment you can get it from Getdeb.net

[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

Or by adding Pidgin's official Repo for Ubuntu

[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by hanzomon4 on 2009-05-20
When will pidgin actually have a new release?  It hasn't changed since dapper.

---

### Post by Kosimo on 2009-05-20
> **hanzomon4 said:**
> When will pidgin actually have a new release?  It hasn't changed since dapper.

Pardon? 

It has been releasing new releases every three months (approximately)

---

### Post by quinnten83 on 2009-05-20
I think he means a 3.x release, not a 2.5.x release.
I just want to know when it will support webcam intergration with sound in msn.

---

### Post by meeples on 2009-05-20
yea i refuse to use it till it support webcam in msn.

its a nice app but i'll stick to amsn till i get webcam in pidgin.

---

### Post by Kosimo on 2009-05-20
Guys, if you have a look into the Roadmap, you'll see that there is just one missing bug to finalize the Video and Audio conference


[http://developer.pidgin.im/roadmap](http://developer.pidgin.im/roadmap)

---

### Post by Saint Angeles on 2009-05-20
ehh... nothing here that really makes me wanna go get the deb for it. i'll just wait until ubuntu updates it for me.

---

### Post by Kosimo on 2009-05-20
> **Saint Angeles said:**
> ehh... nothing here that really makes me wanna go get the deb for it. i'll just wait until ubuntu updates it for me.

You won't get updates unless there is some serious security bug which is not the case.  If you don't want to get .deb's you can use the official Pidgin Repo as mentioned on the first post.

---

### Post by Cammy on 2009-05-20
I love pidgin.  Thanks for the update.

---

### Post by Polygon on 2009-05-20
msn is STILL the buggiest protocol in pidgin, i still get random things like my msn friends don't respond to my messages until i restart pidgin, and then they say the never got them. Yay for a new release, but I am sad that there is only a few msn fixes.


and even though there is 'one ticket left' for Audio/video conference in pidgin, the only ticket left is the ticket saying that pidgin does not yet have video/voice

[http://developer.pidgin.im/ticket/34](http://developer.pidgin.im/ticket/34)

---

### Post by Changturkey on 2009-05-20
If you use MSN, use emesene.

---

### Post by RiceMonster on 2009-05-20
> **Changturkey said:**
> If you use MSN, use emesene.

With the music tracker plugin, the latest version of pidgin has all of the msn features emesene does, though.

---

### Post by Kosimo on 2009-05-20
Now sourcecode is available in pidgin.im

---

### Post by Kosimo on 2009-05-21
Official repo isn't updated yet

---

### Post by andrewabc on 2009-05-21
Wow, I just tried default ubuntu 9.04 pidgin (2.5.5) and they finally fixed http connection for msn. First time I've ever been able to connect using pidgin on this network.

Too bad not many people use msn anymore. It's all on facebook.

---

### Post by chriswyatt on 2009-05-23
I expected the PPA to be updated by now.

---

### Post by Johnsie on 2009-05-23
I'm sorry, but in this day and age I expect more from an instant messenger than text based chat. All the big boys have audio/video and these are NOT implemented in pidgin. This is the default IM client in Ubuntu so standards should be alot higher than they are. As such I will continue to use alternative programs like Skype which does offer these features. Skype seem to be the only one of the big boys who come close to taking instant messaging on Linux seriously.

---

### Post by cdekter on 2009-05-23
> **Johnsie said:**
> I'm sorry, but in this day and age I expect more from an instant messenger than text based chat. All the big boys have audio/video and these are NOT implemented in pidgin. This is the default IM client in Ubuntu so standards should be alot higher than they are. As such I will continue to use alternative programs like Skype which does offer these features. Skype seem to be the only one of the big boys who come close to taking instant messaging on Linux seriously.

+1

Hear hear!

---

### Post by Mister LinOx on 2009-05-23
> **Johnsie said:**
> I'm sorry, but in this day and age I expect more from an instant messenger than text based chat. All the big boys have audio/video and these are NOT implemented in pidgin. This is the default IM client in Ubuntu so standards should be alot higher than they are. As such I will continue to use alternative programs like Skype which does offer these features. Skype seem to be the only one of the big boys who come close to taking instant messaging on Linux seriously.

I actually dont have a problem with the mostly text based chatting. I sort of like it, actually. Makes it feel different than other clients, yet you can still talk to friends who have those clients.

---

### Post by Swarms on 2009-05-23
> **andrewabc said:**
> Wow, I just tried default ubuntu 9.04 pidgin (2.5.5) and they finally fixed http connection for msn. First time I've ever been able to connect using pidgin on this network.

Too bad not many people use msn anymore. It's all on facebook.

Adium has Facebook integration, not for Ubuntu though.

---

### Post by Kosimo on 2009-05-23
> **chriswyatt said:**
> I expected the PPA to be updated by now.

They are just so lazy...

---

### Post by Kosimo on 2009-05-23
> **Johnsie said:**
> I'm sorry, but in this day and age I expect more from an instant messenger than text based chat. All the big boys have audio/video and these are NOT implemented in pidgin. This is the default IM client in Ubuntu so standards should be alot higher than they are. As such I will continue to use alternative programs like Skype which does offer these features. Skype seem to be the only one of the big boys who come close to taking instant messaging on Linux seriously.

What??!?!? Skype released the latest Linux version about one year ago, it has tons of issues that aren't fixed, there is no blog or any roadmap in their website that plans to fix all Issues we currently have in jaunty + Pulseaudio...     I agree with you about that Pidgin should offer more multimedia features, but Skype isn't the right example to follow about how an application should be developed in Linux.

---

### Post by chriswyatt on 2009-05-23
You can hardly compare an application like Skype to Pidgin.  Skype supports just the one IM standard whereas Pidgin supports loads, also Skype is a commercial product.  I'm a little disappointed with the lack of Skype updates as well, but the client works reasonably well as it is, does crash occasionally for me though.

---

### Post by Kosimo on 2009-05-25
Finally guys, Pidgin's official PPA is updated.

[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by 3rdalbum on 2009-05-25
I'm also disappointed with Pidgin - they keep fixing bugs but it never gets better.

I switched to Meebo a while back. It doesn't have the same featureset (or as many features) but what it does, is done perfectly. There's Vv chat from Meebo to Meebo and of course your settings are available everywhere. It does MyspaceIM and Facebook as well as the "classic" IM protocols; only thing that's "missing" is Skype text support so I can talk to all the random Chinese girls who only want to talk to me to practice their English.

I'd agree that Pidgin doesn't cut it these days. To be fair, Kopete is in a similar hole. If Acer merged their Acer Messenger Vv support with Pidgin, then we'd be getting somewhere; but I don't think they're doing it.

---

### Post by -grubby on 2009-05-25
> **Kosimo said:**
> there is no blog or any roadmap in their website that plans to fix all Issues we currently have in jaunty + Pulseaudio...

[http://share.skype.com/sites/linux/](http://share.skype.com/sites/linux/)

---

### Post by Hells_Dark on 2009-05-25
I really like pidgin but the msn protocole is way too buggy now&#8230;

---

### Post by joey-elijah on 2009-05-25
> **Swarms said:**
> Adium has Facebook integration, not for Ubuntu though.

Galaxium is going to support facebook chat.

---

### Post by Kosimo on 2009-05-25
> **grubby- said:**
> [http://share.skype.com/sites/linux/](http://share.skype.com/sites/linux/)

Last post, January 2009.....    :(

---

### Post by qamelian on 2009-05-25
> **joey-elijah said:**
> Galaxium is going to support facebook chat.
And there is a plugin for Pidgin that already supports Facebook chat.

---

### Post by Polygon on 2009-05-25
there is already a plugin for facebook chat, but as meebo (which has libpurple devs and might use libpurple itself) used to have facebook chat, but the facebook developers asked them to take it down, because apparently they are just going to have an XMPP interface to facebook anyway, which is much better then the virtual browser window hack that the facebook plugin is right now

---

### Post by mustang on 2009-05-25
just installed it from the repositories. thanks for the link!

---

### Post by SomeGuyDude on 2009-05-25
There's really no need to make a new announcement every time pidgin makes a 2.5.x update. From an end-user perspective it's like telling me you replaced the tire air caps and door handles on my car. Too miniscule for me to care.

---

### Post by andrewabc on 2009-05-25
> **SomeGuyDude said:**
> There's really no need to make a new announcement every time pidgin makes a 2.5.x update. From an end-user perspective it's like telling me you replaced the tire air caps and door handles on my car. Too miniscule for me to care.

It's important for people who are waiting for bugs to be fixed.
They see new version, check if bugs affecting them were fixed.

---

### Post by bcboybuzz on 2009-08-03
> **SomeGuyDude said:**
> There's really no need to make a new announcement every time pidgin makes a 2.5.x update. From an end-user perspective it's like telling me you replaced the tire air caps and door handles on my car. Too miniscule for me to care.
Spoken like a true American...

Perhaps others would like to know?

---

