---
title: "Am I sane to think this would work?"
date: 2012-01-11
forum: Server Platforms
---

### Post by cryptotheslow on 2012-01-11
Hi,

I'm just mulling over an idea to reduce my monthly bills by bringing a few things in-house.

I have 10.04.3 64bit server installed on a little intel atom box at home that is only on a couple of hours a day to receive an ftp backup from my webhosting server and as a place to dump desktop backups to. So I'd like to put this to a little more use.

My vague plan is to bring the following in-house (that I currently pay $$ for others to host for me):
1. An eggdrop bot - currently sat on a shell host
2. A couple of very under-visited websites that I ended up having to take a VPS for as some of the functionality uses persistent http connections - which is a no-no on shared or reseller type plans.
3. Possibly (later on if I can improve my upstream b/w) a rather under-utilised shoutcast server with an sctrans based auto-dj setup.

Naturally I want to separate my stuff I have on there already away from these new t'internet accessible things - so is the best way to go to run up some virtual servers for these new things?

I've used virtualbox quite a lot from GUI and see that it has a CLI interface too....  would that give me the separation I need? i.e. is there anyway if say the eggdrop gets compromised it could be used to escape the confines of the vbox to access my files?

I have a feeling I want to look to see if my router will support separate VLANs to lock these virtual boxes too also...  I also have a feeling I know just enough to get all this working but not enough to do it securely :(

Any suggestions on other hypervisors etc welcome - as are any comments on my sanity :D

Thanks for reading 
~crypto~

---

### Post by Dangertux on 2012-01-11
> **cryptotheslow said:**
> Hi,

I'm just mulling over an idea to reduce my monthly bills by bringing a few things in-house.

I have 10.04.3 64bit server installed on a little intel atom box at home that is only on a couple of hours a day to receive an ftp backup from my webhosting server and as a place to dump desktop backups to. So I'd like to put this to a little more use.

My vague plan is to bring the following in-house (that I currently pay $$ for others to host for me):
1. An eggdrop bot - currently sat on a shell host
2. A couple of very under-visited websites that I ended up having to take a VPS for as some of the functionality uses persistent http connections - which is a no-no on shared or reseller type plans.
3. Possibly (later on if I can improve my upstream b/w) a rather under-utilised shoutcast server with an sctrans based auto-dj setup.

Naturally I want to separate my stuff I have on there already away from these new t'internet accessible things - so is the best way to go to run up some virtual servers for these new things?

I've used virtualbox quite a lot from GUI and see that it has a CLI interface too....  would that give me the separation I need? i.e. is there anyway if say the eggdrop gets compromised it could be used to escape the confines of the vbox to access my files?

I have a feeling I want to look to see if my router will support separate VLANs to lock these virtual boxes too also...  I also have a feeling I know just enough to get all this working but not enough to do it securely :(

Any suggestions on other hypervisors etc welcome - as are any comments on my sanity :D

Thanks for reading 
~crypto~

Will it work and can you secure it. Yes.

Caveats - if you are talking virtualization you might want a little more oomph then the atom system you currently have. Which comes with power concerns and thus higher bills. Not sure if you'd be saving in the end. 

Honestly, I would not bother with virtualization but instead move the eggdrop and http sites to the server in your home (if the traffic is low on the sites). And save money on the shell and VPS.

I wouldn't do the shoutcast because your'e going to need a considerably higher amount of bandwidth so if you're talking about saving money it might not be the best idea.

As far as hypervisors I recommend Xen or KVM. KVM is better supported in Ubuntu, though I would actually run a CentOS (or RHEL if you have access to it) host and virtualize ubuntu if you want it as a guest. They're lighter on resources , considerably. 

Hope this helps.

---

### Post by cryptotheslow on 2012-01-11
Thanks Dangertux

My only reason for considering virtualisation was that to my mind it compartmentalises things quite neatly. If I can secure the various processes using just the one host OS then great.

The atom box runs to about 40W flat out which on my current electric tariff would stand me at ~5GBP / month. The VPS alone is running me at 45USD / month and the shell 10USD / month. So just bringing the web-hosting and shell stuff in-house will be a significant saving.

Just to note - none of this stuff is *critical* it's just hobbyist stuff. I probably need to consider what to do about resilience for email if I can the webhosting stuff.

I'm vaguely familiar with CentOS as that is what the VPS runs, so rpm based distros don't send me running for the hills immediately :D But then if there is no need to virtualise anything is there any reason to move away from Ubuntu server?

As for the shoutcast stuff - that's not costing a lot now, is reliable and comes with a fairly slick auto-dj setup that I've managed to integrate control for into my website so the dj's can't mess with anything they shouldn't. So yeh - that's a possible consideration for further down the line .

The main priority is the VPS stuff. The sites get next to no traffic but thanks to the nature of one element on them no normal hoster will stand them on lower packages (and I perfectly understand why and have no beef about that).

Maybe I should tackle this one thing at a time. The eggdrop should be simple to move - should I look to lock it up with apparmour or something?


*edited for clarity - * the element that hosting providers don't like is a php based chatroom (PCPin) that maintains persistent http connections for every chatter in the room. Just thought I should explain as some may have interpreted "the nature of" to mean adult or otherwise sensitive contents. It's just a chat-room on a rather old-school internet radio site.

---

