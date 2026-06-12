---
title: "BitTorrent: Now Closed Source"
date: 2007-08-09
forum: The Cafe
---

### Post by starcraft.man on 2007-08-09
Reference Article: [Here.]("http://www.slyck.com/story1566_BitTorrent_Addresses_Closed_Source_Issues")

Well, like the title says the mainline client for BitTorrent is now closed source. I will clarify that from what I've read this covers both the actual client and the protocols in development. The client being closed source isn't a shock really, since the acquisition of uTorrent by Bram, the protocol however is. The reason that was stated for keeping the main client closed source is as follows:
> 
There are two aspects to the BitTorrent open source debate - the protocol itself, and the client. What helped motivate BitTorrent's decision to close the mainline client?

"There are two issues people need to come to grips with. Developers who produce open source products will often have their product repackaged and redistributed by businesses with malicious intent. They repackage the software with spyware or charge for the product. We often receive phone calls from people who complain they have paid for the BitTorrent client."


Frankly, I don't get it. Closing the main client won't prevent scams, there's nothing stopping people from repackaging the installer itself and adding (or slipping in) things that users would click through (as has been done to uTorrent itself far too many times). An observant commenter brought this up, fifth post down (link at bottom of article to discussion).

The protocols also will not be publicly available either. Instead anyone wishing to get at them will have to get an SDK license (I don't know how easy or difficult this is, I'm not a developer of a client). I don't see a use in not publishing the protocols... who is this aimed at stopping? Surely any malicious person can still impersonate being a developer and get a license?

This affects only the latest client (6.0), the older versions will remain as they are open, however I don't like this one bit. To me, it doesn't feel right at all. BitTorrent is about openness and sharing with everyone, and the main client has always represented that it seems by well being open and cross-platform (least to my knowledge. I may not have liked or used the main client, but it was always there). Doesn't really seem to be consistent with the whole concept behind BitTorrent, does it?

One last note to make, uTorrent, for those that don't know, is a Windows only client (the 6.0 beta is accordingly only Windows too). Unless something drastic happens, I assume it will remain as such for the foreseeable future. I mean I don't get the impression the uTorrent developers were ever interested in porting to Mac or *nix.

So, how do you feel? Thoughts? Comments? Please leave piracy out of this, what people share is a discussion for another day. P2P does have very legitimate uses such as Linux Distros (and other giant files), Creative Commons media, as well as original content shared with small communities on both private and public trackers.

Oh and as for me, I guess I'm just gonna add BitTorrent/uTorrent to my list of black listed programs that I don't use/recommend (which includes BitComet, Norton, McAfee and a few others I don't like) . Sad day I think, really sad.

---

### Post by smartboyathome on 2007-08-09
I don't like this either. I always looked up at BitTorrent. Now, I will probably just keep away from torrents.

---

### Post by juxtaposed on 2007-08-09
They didn't close source the main client. They just started using uTorrent as the main client, which is closed source.

Oh, and about it being windows only - they are aparently making a mac version, and I think a linux version after that. I'm not sure though.

>  P2P does have very legitimate uses such as Linux Distros (and other giant files),

What's illegitimate about piracy? =P

---

### Post by cmat on 2007-08-09
I use bittorent to download LiveCDs. I wonder how projects like Azureus and uTorrent are going to work out now in the future. Oh and uTorrent has been ported to work 100% in WINE.

---

### Post by Hex_Mandos on 2007-08-09
How is selling Free Software a scam? There's nothing illegal in selling Free Software.

---

### Post by starcraft.man on 2007-08-09
> **smartboyathome said:**
> I don't like this either. I always looked up at BitTorrent. Now, I will probably just keep away from torrents.

Well, avoiding torrents as a whole isn't really a solution I don't think. I mean it's a sound system, it's been integrated into large services like Joost, Akami and several other media services like the back ends for ustream and Stickam I believe. It's here to stay regardless. 

> **juxtaposed said:**
> They didn't close source the main client. They just started using uTorrent as the main client, which is closed source.

Kinda semantics from my view point... regardless when it's released it will be the main client, and as such represent BitTorrent as a whole (Bram is the creator after all). It sends mixed messages that I don't like IMO. I certainly don't see it stopping the scams or malicious trackers/seeds of some zealous MPAA backed companies.

> Oh, and about it being windows only - they are apparently making a mac version, and I think a linux version after that. I'm not sure though.

Never heard mention of any such thing... regardless I'm of course not interested in a close sourced torrent client when options like Ktorrent and Deluge exist for us. I just don't like the idea of the openness being hampered.

> 
What's illegitimate about piracy? =P
LOL! Let's not get started...

> **cmat said:**
> I use bittorent to download LiveCDs. I wonder how projects like Azureus and uTorrent are going to work out now in the future. Oh and uTorrent has been ported to work 100% in WINE.
Really? Didn't know. That doesn't really constitute cross-platform though, in the same way games running under WINE aren't really played on Linux, their played in a reimplementation of Windows.

As for future projects, I dunno. I suppose it depends on the SDK/licensing and the developers themselves. I don't have any insight into development.

---

### Post by starcraft.man on 2007-08-09
> **Hex_Mandos said:**
> How is selling Free Software a scam? There's nothing illegal in selling Free Software.

It was a scam because some sites were offering uTorrent for a fee when it was the exact same client with no modifications (which was deceptive in the way they presented it). Some even wrapped malicious code in the installer/package and other such bad things in it. uTorrent has been targeted by a number of these due to it's popularity. Selling free software in and of itself isn't bad, but being deceptive/malicious about it is.

---

### Post by @trophy on 2007-08-09
> **juxtaposed said:**
> What's illegitimate about piracy? =P

+1!!! =D>

---

### Post by augied on 2007-08-09
Fork the protocol anyone?

---

### Post by Polygon on 2007-08-09
so is the protocol closed source? like, will all the bittorent programs now have to get "sdk licences" or whatever?

---

### Post by psusi on 2007-08-09
Good for them.  The rest of the world will continue to use the existing protocol with other open source clients, like BitTornado.

---

### Post by DoctorMO on 2007-08-09
It just means that uTorrent will wonder off on it's own, if it breaks with current open format in any way then it'll just die off.

The only way a tool like uTorrent or a protocol like torrent can live in this world is if it's open. trying to do a bait and switch like BitKeeper tried on the Linux Kernel, developers are a very practical and fickle bunch;

If there is something interesting that we can't do with the current torrent specs then the community will move it forwards without the help of uTorrent; just like svg1.1 and inkscape/Adobe.

---

### Post by kelvin spratt on 2007-08-09
uttorent was always closed source and then sold out to bram, who had already sold out to the mpaa, and they needed a closed source client to pursue their spy operations thats why they got Utorrent, but its not going to effect things really is it, just speed up the development of a new  downloading client thats faster and more secure so don't worry its all in hand.

---

### Post by reacocard on 2007-08-09
Not nice of them at all. :(

At least keep the protocol open. I don't care much about the client, but an open protocol is essential.

---

### Post by starcraft.man on 2007-08-09
> **Polygon said:**
> so is the protocol closed source? like, will all the bittorent programs now have to get "sdk licences" or whatever?

Essentially yes, that's right. From my understanding you can only get the new protocol by getting an SDK. It won't be published until it is obsolete by version 7 of the client.

> **DoctorMO said:**
> It just means that uTorrent will wonder off on it's own, if it breaks with current open format in any way then it'll just die off.


That seems a bit doubtful. uTorrent, I believe, represents the largest single p2p user base out there with 17-19 million (numbers vary, they seem to float in that range though from what I've read). That's a huge number and likely enough to bully the rest of the community to go it's way or have trouble.
> 
The only way a tool like uTorrent or a protocol like torrent can live in this world is if it's open. trying to do a bait and switch like BitKeeper tried on the Linux Kernel, developers are a very practical and fickle bunch;

If there is something interesting that we can't do with the current torrent specs then the community will move it forwards without the help of uTorrent; just like svg1.1 and inkscape/Adobe.
Hopefully. Best luck to devs, I'm sticking to FLOSS clients from now on.

---

### Post by Hex_Mandos on 2007-08-09
> **starcraft.man said:**
> It was a scam because some sites were offering uTorrent for a fee when it was the exact same client with no modifications (which was deceptive in the way they presented it). Some even wrapped malicious code in the installer/package and other such bad things in it. uTorrent has been targeted by a number of these due to it's popularity. Selling free software in and of itself isn't bad, but being deceptive/malicious about it is.

µTorrent was always proprietary. The official BitTorrent, however, was free/open source. It can be legally sold with or without modifications. It'd be the same thing as selling copies of OpenOffice. 

As for being deceptive, it's the downloader's responsibility to check what they're downloading. There's nothing you can do about that, other than educating the users.

---

### Post by starcraft.man on 2007-08-09
> **Hex_Mandos said:**
> µTorrent was always proprietary. The official BitTorrent, however, was free/open source. It can be legally sold with or without modifications. It'd be the same thing as selling copies of OpenOffice. 


I know this. No problem with anything said, even selling OpenOffice.

> As for being deceptive, it's the downloader's responsibility to check what they're downloading. There's nothing you can do about that, other than educating the users.

I agree. Some sites were just down right malicious though in trying to take advantage of poor users (some of whom aren't as savvy). Some I think were even payed by the MPAA, really despicable to do some things like this. Don't think it's been proven though... I do wish people were a bit more careful and only when to reputable download sites and large scale tracker sites like mininova and such. We can hope.

---

### Post by SunnyRabbiera on 2007-08-09
Guess I am going to resort to using frostwire to get all my download wants... what a pain :mad:

---

### Post by racoq on 2007-08-09
> **starcraft.man said:**
> 

That seems a bit doubtful. uTorrent, I believe, represents the largest single p2p user base out there with 17-19 million (numbers vary, they seem to float in that range though from what I've read).

I doubt that, i think azureus is the torrent client that has a more users base. Not to say that its far more advanced

---

### Post by BW~Merlin on 2007-08-09
Many peopel saw this coming when bittorrent signed deals with the mpaa.  I can't say its a suprise to me but I am very disapointed.  I think we will see some of the other major torrent clients band together and start implementing their own code amongest themself where the free bittorrent protocal left off.  Either that or a totaly new form of p2p app.

---

### Post by starcraft.man on 2007-08-09
> **racoq said:**
> I doubt that, i think azureus is the torrent client that has a more users base. Not to say that its far more advanced

Maybe not, I don't have rock solid belief in any numbers anyway. At worst, uTorrent represents a significant portion of p2p user traffic. I know on almost all my torrents around 60% are uTorrent (most of rest are azureus and a small portion other), that could just be random luck though.

> **BW~Merlin said:**
> Many peopel saw this coming when bittorrent signed deals with the mpaa.  I can't say its a suprise to me but I am very disapointed.  I think we will see some of the other major torrent clients band together and start implementing their own code amongest themself where the free bittorrent protocal left off.  Either that or a totaly new form of p2p app.

I would definitely support this any way I could. Perhaps it should have already been done by now anyway.

---

### Post by Dimitriid on 2007-08-09
Whats the worry? Can they legally "close" old software that was previously open?  I'd be pretty stupid to go around basically saying "you are legally obligated to forget everything you know"

Reminds me of the "indian giver" bets on Seinfeld.

---

### Post by Jordanwb on 2007-09-02
Sorry but I don't understand what this topic is talking about. :confused:

---

### Post by BW~Merlin on 2007-09-02
> **Jordanwb said:**
> Sorry but I don't understand what this topic is talking about. :confused:

What is there not to understand?  Like the topic says bittorrent is now closed source.  Your post is pointless.  If you don't understand something specific like why or what then say that instead of I just don't understand.

---

### Post by Jordanwb on 2007-09-02
Very well; I don't understand what the problem is with Utorrent being closed sourced. What's the big deal?

---

### Post by hanzomon4 on 2007-09-02
> **BW~Merlin said:**
> What is there not to understand?  Like the topic says bittorrent is now closed source.  Your post is pointless.  If you don't understand something specific like why or what then say that instead of I just don't understand.

Well you don't have to be an *** about it.... If you think the question is stupid just ignore it.

---

### Post by Jordanwb on 2007-09-02
Thank You hanzo.

---

### Post by ~LoKe on 2007-09-02
> **juxtaposed said:**
> What's illegitimate about piracy? =P

Are you hellbent on starting this argument in every damn thread?

---

### Post by starcraft.man on 2007-09-02
> **Jordanwb said:**
> Very well; I don't understand what the problem is with Utorrent being closed sourced. What's the big deal?

Ok... I thought I explained that in the first post. It's not any one thing, it's a whole slew of them. The first thing is that Bit Torrent (at least way I see it) has always been about openness and sharing (both in code and in purpose), this of course flies in the face of that by being closed (client completely, and new protocols to whatever degree they make it difficult to get). 

To add to that, the fact that they adopted a Windows only client as their mainline (with apparently no design/rush for cross platform at this time it appears) is a direct snub to all the non-Windows folks. Granted, not so many Mac and Linux folks use the main client, that isn't the point though. The point is that the main client is supposed to (at least as I see it) be the flagship, the example, by which other clients should be. Lead by example and all that, which this doesn't seem to be in my eyes.

So that's about it, I just think the main client should represent the openness/sharing of the technology. You of course might not care one lick about it being open/closed (just about torrenting), but I (and other's here) do care about the openness of software (we use FLOSS daily after all). It's one of the most important parts of Linux...

Oh and to another extent you might add how Bram (originator of bittorrent) signed the deal with the MPAA not so long ago and has turned the main page into a site that's aiming to commercialize bittorrent... whether that furthers the aims of closed along I dunno. It simply doesn't feel right to me at all >.>.

---

### Post by LookTJ on 2007-09-02
I think it's time to fork BitTorrent and call it OpenBitTorrent?

---

### Post by Fbot1 on 2007-09-02
It says you _won't_ need a devkit. This all seems fine to me.

---

### Post by Seisen on 2007-09-02
I was wondering when they were going to make Bittorrent closed-source since i heard that had sold Bittorrent.

---

### Post by Jordanwb on 2007-09-02
Okay I think I get it now so: The problem is that Bittorrent (or uTorrent?) becoming closed source will go against their desire for file sharing.

---

### Post by Andrewie on 2007-09-03
ktorrent and azureus will always be there. I'm sure someone will make another light weight client so all is good in the end. I don't see a reason for them to close the protocol anyway

---

### Post by starcraft.man on 2007-09-03
> **Jordanwb said:**
> Okay I think I get it now so: The problem is that Bittorrent (or uTorrent?) becoming closed source will go against their desire for file sharing.

Well no. You can file share with a closed app just as good as an open one, a desire to share files doesn't necessitate openness of the code/protocol. Mostly it's about the principle of the matter I think, at least the way I see the principle.

> **Andrewie said:**
> ktorrent and azureus will always be there. I'm sure someone will make another light weight client so all is good in the end. I don't see a reason for them to close the protocol anyway

Aye, so will the old versions of the main client I suppose. It just seems disappointing and seems to be pointing to a more closed future... though that's just speculative.

---

### Post by DjBones on 2007-09-04
really, the existing open source clients like Deluge/Ktorrent/Azureus are perfectly functional and show alot of promise.
uTorrent feels pretty bloated, Deluge doesn't even make a dent in htop.. besides, like people have already said, if people get fed up with closed source crap they'll switch to open or not do it all.
for my music library's sake i hope they choose the former haha

---

### Post by karellen on 2007-09-04
I use utorrent and I don't care whether it's closed source or not as long as it suits my needs and it's free (freeware)

---

