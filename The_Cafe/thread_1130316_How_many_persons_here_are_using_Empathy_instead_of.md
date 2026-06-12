---
title: "How many persons here are using Empathy instead of Pidgin"
date: 2009-04-19
forum: The Cafe
---

### Post by sefs on 2009-04-19
Yes, how many persons are using Empathy with success.

---

### Post by kevdog on 2009-04-19
Haven't tried Empathy yet!  Its been pidgin for me all the way particularly the developers branch thats working with a/v support.

---

### Post by s3a on 2009-04-19
Does empathy support the MSN protocol and have audio/video support for it? If so, then which version of empathy has these changes embedded into it? I wouldn't uninstall pidgin from my hard drive but I think I would start using empathy much more if this were a reality.

---

### Post by Bölvaður on 2009-04-19
I use xfire so I have use pidgin with the gfire extention. Does empathy have something similar for xfire users (wasnt when I checked).

but about audio conversations..... get skype.. seriously why would you use msn for it?

---

### Post by blueshiftoverwatch on 2009-04-19
What are the advantages of using Empathy over Pidgin? Why not attempt to make Pidgin better rather than further balkanize the world of open source IM clients by spreading the resources needed to make better software even thinner than they already are?

Or maybe I'm missing something.

---

### Post by -grubby on 2009-04-19
Pidgin and Gajim

---

### Post by BazookaAce on 2009-04-19
LOL. 100% uses Pidgin, including me. 

Pidgin and Emesene.

---

### Post by Mehall on 2009-04-19
> **Bölvaður said:**
> I use xfire so I have use pidgin with the gfire extention. Does empathy have something similar for xfire users (wasnt when I checked).

but about audio conversations..... get skype.. seriously why would you use msn for it?

Because I don't always want to make video calls. And I don't want two programs running, when one can do what I want.

And also when I know all of 3 people with Skype, and 100 or more with MSN.

---

### Post by whoop on 2009-04-19
I run aMSN actually

---

### Post by Mr. Picklesworth on 2009-04-19
> **blueshiftoverwatch said:**
> What are the advantages of using Empathy over Pidgin? Why not attempt to make Pidgin better rather than further balkanize the world of open source IM clients by spreading the resources needed to make better software even thinner than they already are?

Or maybe I'm missing something.

Empathy is built on the Telepathy stack, which if anything will strengthen the world of IM clients. It's incredibly modular and connected via dbus, designed to run happily on pretty much any Linux-based platform. For example, Nokia's Maemo platform uses Telepathy. It is a FreeDesktop specification, which while not a standard does mean that it's serious about interoperability.

Telepathy supports video and audio chat, and although support for that over MSN is currently nonexistent (just XMPP for now) there is lots of interest in making that happen.

Telepathy is being integrated smoothly into GNOME. Because it is so modular, it can be used for a type of "people" framework, where the technology does WAY more than just instant messaging. For example, with Telepathy Tubes support someone could open a card game, choose to play online and then pick a person from his buddy list to play with. No concern what protocol / software is involved or any of that stuff; it just works. This could also be applied to, for example, collaborating on an audio file using a VOIP protocol.

Although Pidgin has a split back-end, it does not use fancy stuff like dbus to do it (among other things; it's a one-size-fits-all-platforms type), making Telepathy, and by extension Empathy, a better choice. So yeah, it's justified. Don't worry :)

---

### Post by khc on 2009-04-19
> **Mr. Picklesworth said:**
>  with Telepathy Tubes support someone could open a card game, choose to play online and then pick a person from his buddy list to play with. No concern what protocol / software is involved or any of that stuff; it just works. This could also be 


As far as I know telepathy tubes only work on XMPP. So ya, no concern as long as everyone is using XMPP and Telepathy.

---

### Post by gnomeuser on 2009-04-19
> **khc said:**
> As far as I know telepathy tubes only work on XMPP. So ya, no concern as long as everyone is using XMPP and Telepathy.

You assume support cannot be expanded, which it surely will be.

Regardless I use Empathy for superior integration, clean UI and the use of Telepathy which I find to be a design with a lot of promise to deliver next generation integration of People as Objects and IM/VoIP functionality into the desktop.

I am all about taking the desktop to the next level, to do that we need flexible designs that lets application developers do new things. IM has moved so vastly beyond text chat and there still is a whole unexplored world of integration to be seen yet. 

I would love for sharing an object, be that a song, collaboration on a document e.g. with someone be just a simple click away in a seamless experince. To get there the road goes through Empathy and Telepathy, not Pidgin.

---

### Post by blueshiftoverwatch on 2009-04-19
> **gnomeuser said:**
> I would love for sharing an object, be that a song, collaboration on a document e.g. with someone be just a simple click away in a seamless experince. To get there the road goes through Empathy and Telepathy, not Pidgin.
Half or more of the people that I talk to are using the official first party IM clients though, mostly AIM. It doesn't sound like I'll be able to do stuff like that unless the other person is using Empathy/Telepathy too.

---

### Post by Polygon on 2009-04-19
once empathy actually delivers on its promises of cool things you can do with integration, and all the other stuff it promises, sure i'll use it

but its not there yet. At the moment it just looks like a feature stripped version of pidgin. the icons are ugly (blue square, red triangle...seriously?)

maybe in the future, but for now its pidgin.

---

### Post by kevdog on 2009-04-19
Im not a pidgin developer but I'm here to clear up a few misconceptions regarding the development of pidgin.  The vv development branch (voice and video), is built upon the farsight2 project that makes up an integral part of telepathy.  Although pidgin as an IM client may be far behind others in terms of providing video capabilities, they are moving in the same direction towards use of the telepathy framework.  

Here are a few links just in case anyone thinks I am making this up, and I would recommend a few of you to actually compile and try the vv branch.  It works with Yahoo, and the Gchat -- it has audio but no video working as of yet.

[http://developer.pidgin.im/wiki/vv](http://developer.pidgin.im/wiki/vv)
[http://farsight.freedesktop.org/wiki/](http://farsight.freedesktop.org/wiki/)

---

### Post by etnlIcarus on 2009-04-20
Recently returned to Pidgin after using Emesene SVN for about a year. Tried the version of Empathy in the repos but wasn't particularly impressed: used as much memory as Emesene, only had 1/4 the functionality for the MSN protocol.

---

### Post by gnomeuser on 2009-04-20
> **blueshiftoverwatch said:**
> Half or more of the people that I talk to are using the official first party IM clients though, mostly AIM. It doesn't sound like I'll be able to do stuff like that unless the other person is using Empathy/Telepathy too.

Not as such, there are several scenerios that doesn't involve a full on commitment to Empathy. Considering that this will be in terms of application development integration of backend libraries to do the magic then all you would need would be to share the buddy list (and something like pidgin could either have the dbus API required or use the telepathy buddy list.). Once you have the backend of telepathy for the collab features and you know your friends then you don't need to transfer everything to Empathy (it just becomes much easier to do it that way). For Windows users a static build of something like abiword could do the same, yes this is more work and you would need a shim to pull out information from im services that are registered with the machine (typically msn) to get people information. It is though perfectly possible to do.

Aside that you get pretty much all of this free just by using GNOME in it's many incarnations. 

It's not dependent on everyone using Empathy, it is dependent on more people using telepathy and that we can hide underneath for users on other platforms. It will be built into upcoming versions of mobile platforms such as Fremantle and the OLPC Sugar interface also makes extensive use of many telepathy features. The userbase is much wider than people think.

The focus for a lot of the companies working on Telepathy right now is mobile computing. Making location awareness work along with other features of that nature. There isn't much going on in the desktop space just yet as Empathy as an IM client is pretty complete (protocol features are missing but as a client Empathy is in a good place - stable and secure, the UI is polished and integration is going well). Applications are slowly picking up Empathy libraries along with Telepathy for doing things, e.g. one proposed Summer of Code project for Banshee is sharing information between friends using this technology.  

I think we need a little bit of time for developers to figure out how best to take advantage of this very specific connectivity in their applications. Remembering that nobody has had this kind of technology before, outside of something like Facebook that is.

It is easier to do on a mobile platform where you control pretty much everything, on the desktop it will take a bit just in that people have established clients and making it compelling to join the revolution is a harder sell. Eventually though, the notion of instant messaging and VoIP as a standalone applications will die out and instead this features will be a more integral part of the computing environment. Hopefully without flag days, flags days are notoriously bad and we should not rely on getting everyone to switch over on a certain day. It will sneak in, GNOME just takes a front runner position currently by commiting to the long term vision.

---

### Post by conehead77 on 2009-04-20
> **Mr. Picklesworth said:**
> 
Although Pidgin has a split back-end, it does not use fancy stuff like dbus to do it ...

It does not? Just run dbus-monitor and do something with pidgin...

---

### Post by 3rdalbum on 2009-04-20
I'm currently on Meebo but I'm very excited to hear of vv support on Linux, and I'm very excited to hear that Telepathy is continuing to be developed - for a little while it was all the rage and then I didn't hear from it for a while.

---

### Post by Kareeser on 2009-04-20
Empathy user here. Pidgin just seems like it's built on old technology, and it would be easier to start afresh instead of altering the codebase bit by bit.

I also use emesene.

---

### Post by khc on 2009-04-20
> **kevdog said:**
> Im not a pidgin developer but I'm here to clear up a few misconceptions regarding the development of pidgin.  The vv development branch (voice and video), is built upon the farsight2 project that makes up an integral part of telepathy.  Although pidgin as an IM client may be far behind others in terms of providing video capabilities, they are moving in the same direction towards use of the telepathy framework. 

Well I am ;-) Although pidgin will use farsight2 (I believe shipping empathy uses farsight1, I am not sure about the development version), that's a very farcry from saying that it uses the telepathy framework.

There's a GSoC project this year that will add telepathy protocol support to pidgin though.

---

### Post by khc on 2009-04-20
> **gnomeuser said:**
> You assume support cannot be expanded, which it surely will be.

Speaking from someone who knows a thing or 2 about proprietary IM protocols, you are handing waving a bit too much.

That said, I don't think Telepathy Tubes is a bad idea at all, even if it only works over XMPP.

---

### Post by will1911a1 on 2009-04-20
Pidgin only.

---

### Post by SKLP on 2009-04-20
Of course I'm using Empathy ;-)
Previously I mostly used Gossip, though. 
Never liked the Pidgin GUI, looks a bit unpolished and KDEish, even though it's a bit better than the old gaim ui.

---

### Post by SomeGuyDude on 2009-04-20
Empathy requires GNOME.

Pidgin doesn't.

Advantage: Pidgin.

EDIT: apparently Empathy no longer requires GNOME, but now it can't authenticate a single one of my accounts, no matter the protocol. Still a failure.

---

### Post by s3a on 2009-04-20
Can someone please tell me as of which version empathy supports the MSN protocol with audio/video support please?

Also, do you need to be using GNOME 2.26 to use the latest version?

---

### Post by SomeGuyDude on 2009-04-21
Now that I got it working, I'll say this. It's VERY slick and I think well on its way. However, I'm still on Pidgin and here's why:

1) I don't want to have to use gnome-keyring to store passwords. Again, I don't have GNOME, don't want to need it.

2) Contact list doesn't play nice with tint2. I can't close the window and have it get outta my taskbar.

3) VERY limited preferences section.

4) Slow. Takes a while between clicking on a name and getting it to open an IM window.

Still, I -like- it, just don't think it's ready to take over just yet.

---

### Post by stewacide on 2009-04-21
Between Pidgin on Linux and Windows and especially Adium on Mac (I would assume far-and-away the most used open-source IM client?) it's hard to imagine how Telepathy will ever gain momentum over LibPurple, even if its architecturally superior.

Just my 2c.

---

### Post by SomeGuyDude on 2009-04-21
What does Kopete use?

---

### Post by sefs on 2009-04-21
How did those last two options get in there ... I can't remember putting them in.

---

### Post by RiceMonster on 2009-04-21
> **sefs said:**
> How did those last two options get in there ... I can't remember putting them in.

A mod added them.

---

