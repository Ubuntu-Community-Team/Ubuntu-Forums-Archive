---
title: "Network Manager - Show all networks?"
date: 2007-05-07
forum: The Cafe
---

### Post by nigelenki on 2007-05-07
This should be an interesting topic...

Many people still use WEP and rely on disabling their Wifi beacon and MAC filtering to protect their Wireless networks.  What if we actually had the default Wireless network manager supply a mode that .. well.. breaks this?

Imagine an option in Network Manager, "Discover hidden networks and keys."  This completely passive option would, hypothetically, do a number of things:

[LIST]
[*]Put the card into Promiscuous or Monitor Mode
[*]Passively identify SSIDs from packets, to discover networks not broadcasting SSID
[*]Passively identify MAC addresses utilizing specific SSIDs
[*]Passively collect packets with weak IVs for a FMS attack to crack WEP keys
[/LIST]

As time progressed, networks would be shown as "Weak."  Weak networks would be those which can be connected to now, but couldn't before.  Any network without encryption but with MAC filtering or with SSID broadcast disabled is instantly Weak; while WEP networks are Weak once the WEP key has been cracked.

Suppose a user connects to a Weak network.  Obviously this can't be allowed, that's breaking the rules.  A dialog box would pop up saying you're not allowed to do that, and that this is illegal and unethical hacking.  Modifying a configuration file by hand would allow the user to click a "Connect Anyway" button; this forces them to consciously acknowledge what they are doing.

Obviously we know that most of us can grab Kismet, AirCrack, and a few other tools and do this in a few minutes.  Why would we bother with this anyway?  Let's examine this deeper...

People who hack into Wireless networks are an elite breed of computer cybercriminals that can create packets in airgap firewalls with the simplest  thought.  They get your hidden, non-broadcast-SSID network because they can telepathically sense it and command their computer to connect with their leet mind powers.  Most people do not have this level of elite skill, so of course SSID hiding and MAC filtering, as well as 128-bit WEP, are all great solutions that make you much less vulnerable; after all, these technomages can just as easily magic away your WPA/AES encryption.

..... okay back to reality.  None of this stuff is hard, the media overplays hackers as super genius evil dark overlords from an alternate plane of existence, and you can't break WPA because TKIP deforms the key on every packet and AES doesn't have a known crack.  The 16 year old who fixes your computer can hack you, he doesn't know how yet but if he decides one day he really wants to he'll have all the tools in 5 minutes of Googling.  Right now he comes over and sets up WEP and MAC filtering and leaves SSID broadcasts on because that would make it too hard for you.

What do you think the impact of actually releasing a system with the default Wireless network management tool containing a mode that discovers and prepares connections to "protected" networks?  Now a popular OS tells you that these settings are just smoke and mirrors and these other settings really work.  Everyone is forced to realize both truths:  These hackers aren't dark servants of Antioch, and WEP and hiding/filtering protections are weak.

Does this get attention?  Maybe.  Panic?  In a minor way.  Change?  I don't know.  We generally know WEP is "weak" but also feel it's "better than nothing;" now suddenly WEP is nothing.  We generally feel that not broadcasting an SSID makes us "Invisible;" now we're suddenly visible and highlighted.  We believe MAC filtering "locks our network down" to only us; now suddenly anyone can become us.  Does anything change?

I can't answer these interesting questions here.  What I can find out is limited to what we really think.  So what do you think?  Would this be a "good" thing to do?  A "Bad" thing?  Would it "not matter at all" even?  Do you think making this stuff so accessible-- or rather, ceasing to pretend it's not easily accessible-- would be unethical?  Or is it our moral duty to make it so clear that people are wearing the emperor's new clothes for armor?  I don't know.. let's see.

---

### Post by eltorodeoro on 2007-05-09
i can see where you're going with this.  but... fact is that most people aren't looking for this functionality.  most folks who want wireless want it to "just work" at the office, school, home, and the coffee place...  not to see how many of their neighbor's networks they can pirate.    if there is a user who wants to crack someone's WEP, he should be forced to collect the tools and do it.

so, would it be ethical?  i don't really think so, as people take privatization steps for a reason, and we ought to respect that.  also, uncovering the hidden SSIDs around a user who might not otherwise care only creates situations where that user might break into it simply because now he knows it's there.

the bigger question i think is - should a distro waste its time including code that most people could care less about?

just my 2 cents

---

### Post by [h2o] on 2007-05-09
> **eltorodeoro said:**
> the bigger question i think is - should a distro waste its time including code that most people could care less about?
Or more important: Should it ship with code that breaks the law in a number of countries without the user ever knowing? I think not.

---

