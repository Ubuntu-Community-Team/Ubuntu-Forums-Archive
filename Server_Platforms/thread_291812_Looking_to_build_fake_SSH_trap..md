---
title: "Looking to build fake SSH trap."
date: 2006-11-03
forum: Server Platforms
---

### Post by hikaricore on 2006-11-03
Over the last few months I've noticed in my /var/log/auth.log there have been hundreds (by hundreds I mean from hundreds of different IP addresses/networks) of ssh login attempts from dictionary hackers.  Now this doesn't bother me since after the first attempt I noticed, I increased the security greatly by making my passwords alot more difficult to stumble upon.  I also setup a denyhosts service to run which blocks nonexistant users after 2 attempts and actual users after 3 attempts with the wrong password.  Since the time I started I managed to filter this list to a few lines as such:

```

ALL: 58.*
ALL: 59.*
ALL: 61.*.*.*
ALL: 69.63.*.*
ALL: 125.*
ALL: 165.98.*.*
ALL: 200.*.*.*
ALL: 201.*.*.*
ALL: 202.*.*.*
ALL: 203.*.*.*
ALL: 204.8.1.*
ALL: 204.8.2.*
ALL: 204.8.3.*
ALL: 210.*.*.*
ALL: 218.*.*.*
ALL: 220.*.*.*
ALL: 222.*.*.*
ALL: 62.90.175.132
ALL: 124.32.238.85

```

If you look closer many of these IP address blocks belong entirely to ChinaNet, others include israel, brazil, and somewhere I believe to be russia.

Anyway I'm fairly sure the majority of these attempts are done by the same person/persons through shell accounts, possibly even for profit by those willing to pay people to look for unsecure systems for similar use.  Now the curiousity is finally getting to me as to what exactly the hell they're looking to use my system for.  I've attempted to contact every offense to the network it's coming from, but as you can probably imagine, this yeilds no response and the abuse attempts continue.  So what I'm looking for is a way to setup a fake ssh login for the list of invalid user accounts I've collected since I noticed, this way I could collect more extensive logs to study and contact my own ISP with.  I still need to be able to access my own accounts via ssh as I connect from time to time while I'm at work. (but this is optional if not possible any other way)  If anyone knows how I would go about doing this, it would be greatly appreciated.

--Aaron

---

### Post by towsonu2003 on 2006-11-03
Disclaimer: I do not know what I'm talking about...

You could use an emulated server. vmware server... But I don't know how to separate your emulated SSH trap from your real SSH server. 

Or, you could use what people call "honeypots". I have no idea how to do that. 

I'm writing this just to give an idea, and invite solutions from those who know something about these suggestions. 

Also, you might wanna disable password logins and use gpg keys. [this one is a blind suggestion too heuhe]

---

### Post by rabid emu on 2006-11-03
You know, ever since I got firestarter I've been seeing attempted scans or connections from this one ISP in China, frequently.  Like once every 10 minutes, all day.  It's freaking me out although I'm not too worried about the security of my box.  Just that I have no clue why this one guy or group (probably) keeps scanning me.

---

### Post by hikaricore on 2006-11-03
> **towsonu2003 said:**
> Disclaimer: I do not know what I'm talking about...

You could use an emulated server. vmware server... But I don't know how to separate your emulated SSH trap from your real SSH server. 

Or, you could use what people call "honeypots". I have no idea how to do that. 

I'm writing this just to give an idea, and invite solutions from those who know something about these suggestions. 

Also, you might wanna disable password logins and use gpg keys. [this one is a blind suggestion too heuhe]

I may have to look into honeypots, I've seen mention of them but havn't had a chance to track down a detailed walkthrough of setting one up.  As for gpg keys, I don't really have a need for that much security, with my luck I wouldn't be able to access my own system from elsewhere lol...hell that's even happened twice with my denyhosts script.  >.<

But thank you for the ideas.


> **rabid emu said:**
> You know, ever since I got firestarter I've been seeing attempted scans or connections from this one ISP in China, frequently.  Like once every 10 minutes, all day.  It's freaking me out although I'm not too worried about the security of my box.  Just that I have no clue why this one guy or group (probably) keeps scanning me.

There's a market for shell accounts is my guess.  :)

I believe some of my activity may be related to torrents, think about it, users connecting to trackers and the tracker servers selling lists of ip addresses to a third party for port scanning and login attempts.  I'm almost always downloading one thing or another..Just a guess but it would explain the exact same activity on a daily basis, while my ip address changes every day and a half via my cable's iprenewal system.

---

### Post by Chayak on 2006-11-03
I've seen the same thing on my systems though it's more of a shotgun spread method than someone selling your ip.  They do a wide scan of a block of addresses looking for SSH replies and then mark the addresses that reply.  It's a bot basically.  The easiest way to take care of that kind of thing is change your SSH to a non-standard port ;)

---

### Post by MJN on 2006-11-03
> **hikaricore said:**
> So what I'm looking for is a way to setup a fake ssh login for the list of invalid user accounts I've collected since I noticed, this way I could collect more extensive logs to study and contact my own ISP with.

Your ISP isn't going to want to see them - they'll have enough on their plate investigating reports of their users' abuse across the 'net. They'll just tell you to report the abuse to the relevant netblock owners which may or may not want to investigate.

Just a note on your supernetting the banned netblocks, be very careful - you could end up banning an IP that you might want to connect from. Sure, the Class A's from Russia/China may not be relevant, but you've banned a number of Class C's at the /8 boundary which massively increases the chances of blocking a Class C that you might want to connect from.

Of course, if you're not in the habit of connecting from all over the place then just limit access to locations (networks) that you will connect from (e.g. work) and your problem will go away!

Just read through my post and see that it's all a bit negative! Don't mean it to be, just pointing out a couple of things which you might not be aware of. Continue as you intend from purely interest sakes however do be careful of what you let your hijacked machine be used for - either knowingly or unknowingly... You don't want to add to the problem!

Mathew

---

