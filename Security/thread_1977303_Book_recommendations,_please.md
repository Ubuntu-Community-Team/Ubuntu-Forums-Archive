---
title: "Book recommendations, please?"
date: 2012-05-09
forum: Security
---

### Post by computeratin on 2012-05-09
OK, loooooong time very, very advanced doze *end user*. I've grown to hate it.

I've been playing with UB in VMs for about year now. So I'm not a noob any more. But I'm by no means any where near being an expert. But, I think I'm ready to dump my doze install entirely and take the plunge. (I found a spiffy tool that let me turn my whole doze install in to a VM, just in case.)

I tried these forums for a few months when I first started. (On a log in whose information I've lost.)

I haven't been here in about 6-8 months because I got very frustrated.

I had a bad habit of asking questions that were evidently too technical for the folks that hang out in the general forums, because I almost never got answers.

On the other hand when I would ask questions over here ,half the time the answers were over my head.

So, I'm looking for books that will help me get from where I am to where I want to be. I've looked at several dozen books and hundreds of web sites. They all seem to fall in to two categories:

1) Written for people who don't know that's not a cup holder.

2) Written for people who have a sixth degree black belt in comp sci.

Does anybody know of any good *nix books in the middle; especially ones on Debian in general or UB in particular?

Also, since I'm entirely self educated there are gaps in my knowledge. The biggest one being anything to do with creating or administrating a network. (I've never had the money to play with more than one box at a time.)

I'd like to fix that. I finally have a really nice box to play with. Nice enough that I should be able to set up small virtual networks and start to play with them and learn. Does anybody know where I can find:

1) An easy to follow (no that's not a cup holder) tutorial on creating virtual networks with Virtual Box? All the ones I've been able to find so far make my head hurt.

2) A good beginning book on mixed network architecture and administration; just practical stuff like in XP this setting is here and in BSD the same setting is here and in *nix it's over there.

Thanks for the help.

---

### Post by cryptotheslow on 2012-05-09
> **computeratin said:**
> OK, loooooong time very, very advanced doze *end user*. I've grown to hate it.

I've been playing with UB in VMs for about year now. So I'm not a noob any more. But I'm by no means any where near being an expert. But, I think I'm ready to dump my doze install entirely and take the plunge.

I tried these forums for a few months when I first started. (On a log in whose information I've lost.)

I haven't been here in about 6-8 months because I got very frustrated.

I had a bad habit of asking questions that were evidently too technical for the folks that hang out in the general forums, because I almost never got answers.

On the other hand when I would ask questions over here ,half the time the answers were over my head.

So, I'm looking for books that will help me get from where I am to where I want to be. I've looked at several dozen books and hundreds of web sites. They all seem to fall in to two categories:

1) People who don't know that's not a cup holder.

2) People who have a sixth degree black belt in comp sci.

Does anybody know of any good *nix books in the middle; especially ones on Debian in general or UB in particular?

Also, since I'm entirely self educated there are gaps in my knowledge. The biggest one being anything to do with creating or administrating a network. (I've never had the money to play with more than one box at a time.)

I'd like to fix that. I finally have a really nice box to play with. Nice enough that I should be able to set up small virtual networks and start to play with them and learn. Does anybody know where I can find:

1) An easy to follow (no that's not a cup holder) tutorial on creating virtual networks with Virtual Box? All the ones I've been able to find so far make my head hurt.

2) A good beginning book on mixed network architecture and administration; just practical stuff like in XP this setting is here and in BSD the same setting is here and in *nix it's over there.

Thanks for the help.

I think I can see why you got no answers previously. Your questions are not focused. Even in this post you have two question 1) and two question 2) - how is anyone supposed to form readable answers for you - let alone the ensuing discussion be followable?

By "virtual network" do you mean multiple virtualised machines running on the same metal talking to each other?

---

### Post by computeratin on 2012-05-09
> **cryptotheslow said:**
> I think I can see why you got no answers previously. Your questions are not focused. Even in this post you have two question 1) and two question 2) - how is anyone supposed to form readable answers for you - let alone the ensuing discussion be followable?

By "virtual network" do you mean multiple virtualised machines running on the same metal talking to each other?

See, this is one of the reasons why I gave up here: There's no need to be snarky.

And I don't think it was because of how I wrote my questions. I would ask very focused questions. Like how do I recompile this broken driver with a known typo when all the directions in the tutorial are not working for me and I am getting XYZ copy and pasted error message.

And yes, I mean: "multiple virtualised machines running on the same metal talking to each other".

---

### Post by cryptotheslow on 2012-05-09
I really wasn't being snarky, sorry if it came across that way - not the intention at all. :(

ubunutuforums.org is mostly a place where people come for assistance with a particular issue, the issue is described and those who know the answer provide a solution.

We're all just Ubuntu users here, but chances are someone has faced the same issues as yourself, solved it and is willing to spend time to help someone else facing the same issue.

No-one here knows where you reside on the cup-holder to 6th degree black belt in comp sci curve, so sometimes the advice proffered may be simple, sometimes out of reach - that's the way it goes. It's all relative, don't get so angry about it.

As for your virtual boxes, it really depends on your network setup. If you have a router or server on the network running as a DHCP server make sure to set you virtual boxes to run in Bridge mode as opposed to NAT. That way they will acquire their own IP address on the network. I find it easier to get various VB's talking that way without developing a headache.

As for book recommendations - I have none. Once you have the basics down it's best to getting stuck in and figure things out as they come up. No library of books is going to tell you everything you ever need to know, you need to learn as you go. Sorry if this is not the answer you seek.

---

### Post by computeratin on 2012-05-09
> **cryptotheslow said:**
> I really wasn't being snarky, sorry if it came across that way - not the intention at all. :( 

Thankx :)

> As for your virtual boxes, it really depends on your network setup. If you have a router or server on the network running as a DHCP server make sure to set you virtual boxes to run in Bridge mode as opposed to NAT. That way they will acquire their own IP address on the network. I find it easier to get various VB's talking that way without developing a headache.Well as it stands I'll have no network set up for all intents and purposes. So I can build whatever my metal will handle and I can figure out.

 My stupid bleeeeeeeep doze install got infected yet again after taking many, ridiculous, over the top security precautions. I managed to dig it all out but, I'm done. MS can go suck an egg. 

I've verified that 12.04x64 will run all of my hardware. So I'll be starting with a clean install. I have some spiffy VMs setup right now in VB on doze. I'll transfer them all over to the new install. And I'll carry over my whole doze install as a VM inside UB. But, I have zero, none, nada idea about how to get them to start talking to each other.

My box has one LAN card, one wireless card and I have an NAT router between me and the outside world. I'd like to run everything directly on my laptop. I think I can run the host OS and probably up to three, maybe four VMs at the same time. But, one of the security precautions that I had to take in crappy doze was to uninstall the bridge network drivers. (Stupid, I know. But doze sucks and if you don't want to take the chance of catching a cold you have to do lots of stupid things.)

So, when I go to the new install: Install the VB bridged network drivers and the process is easier?

> No library of books is going to tell you everything you ever need to know, you need to learn as you go.I agree. I'm just having a hard time finding intermediate level information so I can progress in my knowledge base. Gotta walk and all that jazz.

---

### Post by rookcifer on 2012-05-09
I have generally found Linux books to be of little value. By the time the go through the editing process, get to the printing press and then released, they are already obsolete.  The Linux world moves very fast.

It's better to just get your hands dirty, experiment and ask questions on forums such as this.

---

### Post by hansdown on 2012-05-09
Welcome to the forum, computeratin.

Not sure of any books, but this should help explain some of the things you need to know.

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial?shared=email&msg=fail](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial?shared=email&msg=fail)

[http://idilix.net/ubuntu12.04-tutorial-2-beginner](http://idilix.net/ubuntu12.04-tutorial-2-beginner)

Hope this helps.

---

### Post by cryptotheslow on 2012-05-10
> **computeratin said:**
> Thankx :)

Well as it stands I'll have no network set up for all intents and purposes. So I can build whatever my metal will handle and I can figure out.

 My stupid bleeeeeeeep doze install got infected yet again after taking many, ridiculous, over the top security precautions. I managed to dig it all out but, I'm done. MS can go suck an egg. 

I've verified that 12.04x64 will run all of my hardware. So I'll be starting with a clean install. I have some spiffy VMs setup right now in VB on doze. I'll transfer them all over to the new install. And I'll carry over my whole doze install as a VM inside UB. But, I have zero, none, nada idea about how to get them to start talking to each other.

My box has one LAN card, one wireless card and I have an NAT router between me and the outside world. I'd like to run everything directly on my laptop. I think I can run the host OS and probably up to three, maybe four VMs at the same time. But, one of the security precautions that I had to take in crappy doze was to uninstall the bridge network drivers. (Stupid, I know. But doze sucks and if you don't want to take the chance of catching a cold you have to do lots of stupid things.)

So, when I go to the new install: Install the VB bridged network drivers and the process is easier?

I agree. I'm just having a hard time finding intermediate level information so I can progress in my knowledge base. Gotta walk and all that jazz.
 
MS is just a software house, they produce and sell a popular OS (this is not the place to discuss the strategy they choose to put their OS out there) - result of which they became a target. That's the way it goes - big target lots of attention.

There are no drivers to install to run VB instances in Bridge mode, at least not that I have come across - just look at the settings for the VB and set it to Bridge before starting it. This is assuming you are running VB from a desktop rather than command line only on a server install - even on a server it is not hard to achieve, just a slightly steeper learning curve if you are not familiar with command line stuff.

I think I lost track typing that - do you want a book or some help?

---

### Post by Ms. Daisy on 2012-05-10
It sounds like your most pressing need right now is to learn how the virtual network will function. You're using Virtualbox?  If so, the only way to understand it is to read the virtualbox manual.  In my experience Virtualbox is deceptively simple, where it looks like you can just intuitively set it up.  But there are some details such as installing guest additions and sharing USB & CD drives that you can only figure out from the manual.  The manual will also explain how to set up various networking options. But I promise that if you don't read the manual, you will be hopelessly lost. No one can boil it down into a quick post.

[http://www.virtualbox.org/manual/](http://www.virtualbox.org/manual/)

Something worth noting: the version of Virtualbox in the Ubuntu Software Center doesn't behave as well as the version you can download directly from the [Oracle website]("https://www.virtualbox.org/wiki/Downloads").

Things to consider: When you have several virtual machines running simultaneously, your system will require lots of resources.  [This ]("https://www.virtualbox.org/wiki/End-user_documentation")will help you begin to understand what virtualization needs to work.

---

### Post by CharlesA on 2012-05-10
You can find an outstanding book here:

[http://www.amazon.com/Ubuntu-Unleashed-2012-Edition-Covering/dp/0672335786](http://www.amazon.com/Ubuntu-Unleashed-2012-Edition-Covering/dp/0672335786)

---

### Post by computeratin on 2012-05-10
> **cryptotheslow said:**
> I think I lost track typing that - do you want a book or some help?

                                  I'll take whatever I can get.  
 

 (And the command line is not one of my strong suites. I'm a GUI guy. If I HAVE to code I copy, paste and compile. Or better yet, deconstruct something existing that is almost what I want and make a couple of tweaks. )
 

 I appreciate all of the info.  
 

 Everybody has given me a lot to chew on. I've got this thread bookmarked and I'll be going through everything closely.
 

 I appreciate the links Ms. Daisy. There's some stuff there I hadn't seen yet. It looks like turning my old doze install into a VM is not going to be a straightforward as I had hoped. But, I'm sure I'll figure it out. I'm really good at troubleshooting.
 

 Since I've never had more than one box at a time I always rip all of the networking stuff out of doze. Why open up potential holes for stuff you're not using? (Besides, it makes the box faster.)  
 

 Like I said, I have some cool VMs. (One is a fully functional Ice Cream Sandwich install.) The troubleshooting stuff for how to setup Virtual Box will come in handy, as will the stuff about Ubuntu. I think my biggest &#8220;stuck&#8221; point right now is the fact that I have no idea where to start looking inside the guest OS's to tell them to start talking to each other. That's why I was asking about a practical guide to mixed network architecture settings.
 

 Getting books is a pain in the neck where I'm at now. We don't have any of the mega-bookstores like I'm used to back east. I called over to the local college about used text books today, but I missed the season. The next turn over won't come until August. I'm going to look around this weekend and see if anybody has a copy of Unleashed. (I hate buying books blind.)  
 

 Do you guys have a suggestion for an area of this forum to ask fairly technical questions. I didn't have much luck before over in the general forums. Some place where I can get some help getting in to the nitty gritty of things like enabling hybrid graphics, clocking (not really &#8220;over&#8221; clocking per se, but that's another thread), cooling policies, recompiling broken drivers, etc.?

---

### Post by Ms. Daisy on 2012-05-10
> **computeratin said:**
> Getting books is a pain in the neck where I'm at now. We don't have any of the mega-bookstores like I'm used to back east. I called over to the local college about used text books today, but I missed the season. The next turn over won't come until August. I'm going to look around this weekend and see if anybody has a copy of Unleashed. (I hate buying books blind.) 
IMO you're better off getting electronic books & manuals for computers. Too much changes too quickly for hard cover books to be much use.  

However, you need to read Shakespeare in hard cover (but I digress). > **computeratin said:**
> Do you guys have a suggestion for an area of this forum to ask fairly  technical questions. I didn't have much luck before over in the general  forums. Some place where I can get some help getting in to the nitty  gritty of things like enabling hybrid graphics, clocking (not really  “over” clocking per se, but that's another thread), cooling policies,  recompiling broken drivers, etc.? 	 Best thing is to start a new thread in the relevant sub-forum in Ubuntu Forums.  Stick to one problem per thread.

---

