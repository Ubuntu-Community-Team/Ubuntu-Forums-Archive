---
title: "Ubuntu Thin Client for Dummies"
date: 2012-02-26
forum: Server Platforms
---

### Post by iangarforth on 2012-02-26
Hi all,

This kind of developed from out of nowhere, but I'm hoping I can get support on building a small, simple thin client network using Ubuntu.  The idea was brought up by Roelforg in [this]("http://ubuntuforums.org/showthread.php?t=1931232") thread, but I'll just summarise the key bits.

I work in a secondary school that has developed an extraordinarily  complicated network, that has been mended by applying patch over patch, until it finally got to the stage that not even our managed providers could really remember what was doing what.

This Summer, it seems likely that we'll wipe the slate clean and start again.  I'm personally a huge Ubuntu/opensource fan, but the gamble is too great to persuade the school to jump in.  Therefore, I've convinced the head to give me 15 legacy machines, and show what can be done with Ubuntu.  

The big sell for him will be cost, and maybe to a lesser extent being able to use legacy machines.  Therefore it would be helpful if whatever I can do ends up being scaleable - it may get (a lot) bigger.

It's important to recognise that I'm no expert.  This will be the first Linux server I've built or worked on.  I'm game though, and I'm a fast learner...

Now - after the other thread, I'm now changing track.  The idea of thin client has been floated before, and the idea of creating and being responsible for the thin client Ubuntu side is fantastic - and we can't divorce yet otally from the Windows side (SIMS is still effectively compulsory for teachers).

Therefore, my plan is to create a small thin client Linux network, that runs Ubuntu as we know and love it.  I think the timing of this is great, with 12.04 on the horizon as a long term release giving us the stability we need.

So this week, a box will be delivered from eBay that will be my play pen - my chance to configure and play.  I'm keen at this stage that if possible, I deploy Ubuntu rather than Edubuntu, as I think for students who may go home and download it, Ubuntu is an OS for life, and not just for school ;-)  (I'm being facetious - nothing against Edubuntu...)

So - from the previous thread, Roelforg details a way to deploy thin client (I think) via an NFS share.

Can I start with that question?  

What are the pros and cons with regards to ways to deploy a Ubuntu Thin Client network?  Specifically, what are the pros and cons between TC via NFS, and TC via LTSP (which is what I gather Edubuntu uses..?)

Secondly, if I go the NFS route, is this workflow the beginnings of a meaningful 'to do' list..?

0.5) Sweettalk current systems administrator into giving me a fixed IP for the Ubuntu server and exclude said IP from the existing whole school DHCP
1) Receive box from eBay
2) Install Ubuntu Server
3) Install SSH
3a) Does this set-up need a DHCP server running from the box for the virtual clients when they log on?
4) Install Apache2
5) Install NFS4
6) Follow Roelforg's tutorial to get thin client working with a generic log on - eg: 'student'
6a) Configure any old client machine to run the Thin Client protocol and log on into a virtual Ubuntu session on the server
7) Work out a way to get folks' existing authorisation process (LDAP?  Need to find out...) to work and to then mount their files to their virtual Ubuntu log on

Right.  What have I got wrong?

---

### Post by iangarforth on 2012-02-26
The more I try to research this, the more it seems that there is more history and support in LTSP.  Have I got this wrong?  There must be more to the relative advantages and disadvantages?

Which would be easier to set up?
Would there be any difference to speed?

What would my 'to do' list look like if I were deploying LTSP across an Ubuntu server (and client)?  Something like this..?

0.5) Sweettalk current systems administrator into giving me a fixed IP for the Ubuntu server 
1) Receive box from eBay
1a) Ensure box has 2 NICS in it
2) Install Ubuntu Server (though the tutorial [here]("http://ubuntuforums.org/showthread.php?t=599166&highlight=ltsp") uses the desktop version..? 
3) Install SSH
3a) Don't install a DHCP server - I think one gets installed as part of LTSP?
4) Install LTSP on the server
5) Configure LTSP on server
6) Build client environment on server (have no idea what happens when this command is invoked - all of the tutorials go a bit quiet at this stage...)
7) Configure any old client machine to run the Thin Client protocol and log on into a virtual Ubuntu session on the server
8) Work out a way to get folks' existing authorisation process (LDAP? Need to find out...) to work and to then mount their files to their virtual Ubuntu log on

---

### Post by Exonimus on 2012-03-08
I'm posting here because I'm also rather interested (in a similar situation, albeit on a way smaller scale at home). At least an answer to some of your points

the client building thing is basically a command one invokes to have a (rather long!) process go automatically. One can change settings before or after this build process, and update the image, thus taking less time. That being said, I'd also love a more central ltsp documentation thing, although the page on help.ubuntu is rather helpful.

You'd also need to be aware of stuff like playing videos: although I'm not ltsp expert, from what I've read this is usually an issue, but can be solved several ways, the most effective (I've found at least) having some applications run locally. This, in effect, means that one would not have purely thin clients, yet from your story I'm assuming the clients will be old leftover boxes with at least some ram, basically. 

Another thing you'd have to consider is wireless: I've read stories on people getting it to work, but there's hardly any proper documentation on it. Where expandability is concerned, I'm guessing wireless might be a necessity where students/teachers laptops etc. are concerned.

I know I haven't answered many of your questions, but I hope I've at least helped you somewhat (and bumped the thread, at that! :D)

---

### Post by spynappels on 2012-03-08
I've not done a lot on LTSP, I only set one up as a test a few years agao, it worked and that was that.

However, I would suggest that if you get a static IP, you put a small router on that and segregate your Thin Client setup into a small LAN of it's own. That way you don't need to worry too much about the DHCP server in your terminal server clashing with the main DHCP server and allows you to play without messing up anything on the main network.

Oh, and the Alternate Install ISO contains everything you need to install a LTSP server.

Once you have it working, you can get the main DHCP server to reconfigure slightly to point all PXE boot DHCP requests to your LTSP server, having a GbE connection is necessary though, even for a small number of clients. If it scales and grows, use multiple NICs and bond them.

But walk before you run is my advice.

---

