---
title: "Not ready for primetime on netbooks"
date: 2009-07-08
forum: Testimonials &amp; Experiences
---

### Post by ryantollefson on 2009-07-08
Sorry, I need to vent...
 
I keep wanting to love Ubuntu... I try it every 6 months or so, but there is always something that makes it not worth it.  It always feels so close, but not quite there... Here's my latest experience:
 
I was demonstrating to my wife how far the Linux/Ubuntu world has come, and telling her that it was getting really close to being usable for normal everyday use.  I handed her the netbook with Ubuntu on it, and let her give it a try.  She started browsing, everything worked fine, and she was decently impressed.  Then she checked her email and found an attachment that she needed to download for work. She's smart enough to know that editing photos isn't to work well on a netbook, so she went to save the file to our NAS so she could access it later on her desktop...
 
You can see where this is going.
 
She wasn't able to do so.  I looked at it, found that it wasn't just a simple error, so I mapped the network drive.  Still no luck.  After searching around for a while I came across [this thread ]("http://ubuntuforums.org/showthread.php?t=1163683")and realized it was a limitation within Linux/Firefox.  My wife rolled her eyes at me, and asked why I even put Ubuntu on there if it wasn't going to work right.  I got to thinking about it, and I realized that she's right.  I ran into what I consider to be a show-stopper issue within the first hour of using the system.  I knew there were bound to be little issues here and there; that's what I would expect, and I can live with that... but to run into such a stupid (yet *very* annoying) problem within the first hour of using it... I know you can do some other work arounds to get this issue solved, but I shouldn't have to.  This made me realize that the system just isn't mature enough to use in any type of production/non-test/non-geek environment yet.
 
I installed Windows 7 (RC) in less time than it took to troubleshoot this issue, and everything has been working without issue since.  To me, it is worth paying for Windows if it is going to save me hours of frustration with issues like this.
 
Ubuntu is doing some great work, but when I run across something like this, it really shows me how much Ubuntu really isn't ready for prime-time use.  I understand that there are ways to force saving to a network drive to work, but I shouldn't have to do that.  I don't have to do that in OSX or Win XP/Vista/7, why doesn't this just work?
 
From the front page:
 
>  
**Ubuntu 'Just works'**
We've done all the hard work for you. Once Ubuntu is installed, all the basics are in place so that your system will be immediately usable.


If only that were true.  I understand this might not still be considered "the basics;" however, for a netbook I would think sharing to a network drive really would be considered basic use (since you probably aren't saving much/anything to it).  
 
I don't mean to just bash Ubuntu here.  I think it has real potential, otherwise I wouldn't bother to even post on this message board; however, I think it's important to share real world frustrations with it so that hopefully someone with more programming skills than I can make it much more usable for the rest of us.

---

### Post by ddrichardson on 2009-07-08
With respect as I understand your frustration but as is often the case with this section there is no point in suggesting improvement here, as very few developers read it.  These two are however:

[https://bugs.launchpad.net/netbook-remix](https://bugs.launchpad.net/netbook-remix)
[https://answers.launchpad.net/netbook-remix](https://answers.launchpad.net/netbook-remix)

I'm sure they'd appreciate the feedback.

You said it yourself though:> it is worth paying for Windows if it is going to save me hours of frustration with issues like this.
We're not being paid!

---

### Post by aysiu on 2009-07-08
I'm sorry you couldn't get NAS working. I don't even know what NAS is, but you can probably get help for it on the forums if you post a support thread.

If you think it's a bug in the software, you can report it as a bug:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

If you think it's a missing feature, you can post a Brainstorm:
[http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)

And I think everyone participating in this thread should read this:
[http://www.psychocats.net/ubuntucat/the-linux-communitys-mixed-messages/](http://www.psychocats.net/ubuntucat/the-linux-communitys-mixed-messages/)

---

### Post by owise1 on 2009-07-08
I am currently using an old linux box as NAS (network attached storage) and it serves files via NFS and samba and is visible to both linux and windows machines.

I am also about to buy a commercial NAS and found that most do not support the unix (linux) NFS so to access and store files you will need to install samba.  You can do this on your netbook via the package manager (the linux killer feature IMHO).

Alternatively you could buy a NAS with NFS support - QNAP for example.

I somehow think that you are a little disingenuous in your complaint and really wanted to place a little advert for win 7.

I have found that the free support from the community is fantastic but you must share and do a little homework first.

---

### Post by ddrichardson on 2009-07-08
> **aysiu said:**
> I'm sorry you couldn't get NAS working. I don't even know what NAS is, but you can probably get help for it on the forums if you post a support thread.Network Attached Storage, most likely samba share issues.

> **aysiu said:**
> And I think everyone participating in this thread should read this:
[http://www.psychocats.net/ubuntucat/the-linux-communitys-mixed-messages/](http://www.psychocats.net/ubuntucat/the-linux-communitys-mixed-messages/)Sorry, I don't see what you're getting at with this link.  I've read it twice and the only relevant sentance is> “It’s free. How can you complain about something that’s free?You make the assumption that when we say free we mean inferior but it swing both ways - if you aren't paying for something you can't expect a developer to drop everything and fix your issue - when there's less time available to work on a project (which is true when developing outside your normal working day) then there will always be prioritisation.

---

### Post by ryantollefson on 2009-07-08
> **ddrichardson said:**
> As does my comment. Reporting an issue in the wrong channel and threatening to go back to Windows deserves a gentle reminder that we are volunteers. I didn't suggest it as an excuse.
 
It wears volunteers down listening to ridiculous remarks such as the one you just made.
 
Thanks for the links ddrichardson, I may go and post feedback to the other areas.
 
Just so we're clear here, I wasn't threatening to go back to Windows... I did go back to Windows (at least for the forseable future).  I also certainly *wasn't complaining about the support in any way*.  I have had good luck searching the forums/documents for almost all issues regarding my various endeavours into Ubuntu.  I am not looking for support on this specific issue (nor am I expecting it) - that's why I wrote in the "Ubuntu Testimonials & Experiences" section.  I just wanted to share my experience in the hopes that it might stimulate discussion/encourage development for real world end user issues.
 
I can also see that the forums are very active, and it's good to know that they will be useful the next time that I try out Ubuntu on a machine.

---

### Post by ryantollefson on 2009-07-08
> **aysiu said:**
> I'm sorry you couldn't get NAS working. I don't even know what NAS is, but you can probably get help for it on the forums if you post a support thread.
 
If you think it's a bug in the software, you can report it as a bug:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
 
If you think it's a missing feature, you can post a Brainstorm:
[http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)
 
And I think everyone participating in this thread should read this:
[http://www.psychocats.net/ubuntucat/the-linux-communitys-mixed-messages/](http://www.psychocats.net/ubuntucat/the-linux-communitys-mixed-messages/)
 
 
Thanks for the links. 
 
Someone mentioned above, but NAS is Network Attached Storage.  The issue is that from Firefox on Ubuntu you can't save directly to a network location (without jumping through all sorts of hoops first).

---

### Post by ryantollefson on 2009-07-08
> **owise1 said:**
> I am currently using an old linux box as NAS (network attached storage) and it serves files via NFS and samba and is visible to both linux and windows machines.
 
I am also about to buy a commercial NAS and found that most do not support the unix (linux) NFS so to access and store files you will need to install samba. You can do this on your netbook via the package manager (the linux killer feature IMHO).
 
Alternatively you could buy a NAS with NFS support - QNAP for example.
 
I somehow think that you are a little disingenuous in your complaint and really wanted to place a little advert for win 7.
 
I have found that the free support from the community is fantastic but you must share and do a little homework first.
 
I don't think it's related to my NAS (which shows up as a normal Windows share).  From Firefox in Ubuntu you can't save directly to a shared location (didn't seem to matter what type of a share, just network locations in general).  From within the OS the network shares would work fine (e.g. if you save from Firefox to the desktop first, then transfer to the network share it was fine, just couldn't save directly).
 
You can think I'm being disingenuous all you want.  Perhaps you aren't used to hearing criticism on these boards, but I was sharing my Ubuntu Experience in the Testimonials & Experience thread, and *my* experience on this netbook was not so good.  
 
I don't work for Microsoft, I'm really not an MS fanboy, I don't particularily like Microsoft (nor do I dislike them), I would actually like to see more legitimate competition within the OS market.  But that's just me saying this, you probably don't have any way to verify this, and it's within your right to think I'm not being honest if that what you want to think.  Truthfully, I think that's a little lame that you are that quick to judge me since you probably don't know me at all, other than this one post that I've made, but that is your decision.  
 
I specifically wrote in the Testimonials & Experiences section because it seemed like the place to share my experience so far.  I have tried to be truthful & forthcoming on it.  I would like Ubuntu to work for me.  It didn't work as well as I expected.  I switched back to Windows on that machine because it fits my (& my wifes) needs better at this point in time.  
 
I know there are ways I could get this to work if I spend a lot of time with it... but that was my whole point of writing this post.  I don't think Ubuntu is quite at the "It just works" level... maybe it is for some things, but not everything... which to me means that it doesn't "just work" yet.  I think it is getting close.  I hope it continues to progress.  I would like to use it at some point in the future, and I will continue to try it out from time to time; but, this is my experience with it thus far.

---

### Post by michaelzap on 2009-07-08
I'm confused by the issue that you had. I have two NAS drives at home (a Buffalo Linkstation and an HP MediaVault), and I've never had any trouble saving files from Firefox or any other program to them. I switched to Linux from Windows when the latest version was Feisty, and I've never seen this issue using any Ubuntu version since then.

Mounting network shares permanently in Ubuntu used to be a pain (it required you to create a mount point and edit the fstab file). I think that on previous versions you also had to install the smbfs package of Samba client libraries (now I believe that package comes preinstalled). Once you did that, however, your mount point directory worked just like any local directory for all apps (Firefox included).

In Jaunty I now mount my network shares (all six of them) using GVFS, which is a feature of new versions of Gnome. It works like a charm and doesn't require any edits to fstab or sudo commands or anything. More info here:
[http://ubuntuforums.org/showthread.php?p=7563868](http://ubuntuforums.org/showthread.php?p=7563868)

I also highly recommend Eeebuntu for regular netbook Ubuntu installations, since it pre-configures a lot of things for you so that they work better on a netbook.

---

### Post by Arup on 2009-07-08
I see......its OK for paid Windows to use their customers as guinea pigs and yet, because the fool has paid for it, the vanity makes sure there is no outrage. For years Windows has been peddling off buggy OS and then starts the process of service packs, finally when they see that service packs have made the OS a bit mature and stable, they come out with the same OS in new packing and charge you again. So far for every PC i have installed Ubuntu in, it JUST WORKS out of the box with no issues and if there is every any, its fixed with ease as Linux is transparent. Don't demand, no one gets paid in Linux, its voluntary effort and I am sick of Win Fanboyz coming over here and making direct comparisons, if Win is so good, why are you here in the first place anyways.

---

### Post by HappyFeet on 2009-07-08
> **Arup said:**
> I see......its OK for paid Windows to use their customers as guinea pigs and yet, because the fool has paid for it, the vanity makes sure there is no outrage.

Well said.

How come just about every windows computer I come across runs so poorly that I consider it unusable? Because windows is great? I know what some of you will say, and it's probably- "that is the users fault if they don't know how to manage their windows computers". I say that if an OS makes you walk on eggshells on the internet, requires maintenance, is intrusive, and generally annoying, how is that easier for the average person? Linux requires little or none of the above.

I know about 15 people that now use linux and love it. It just works. I understand that nothing is perfect, but the way I see it, linux comes pretty damn close.

Also, linux is community driven. You are either part of the solution, or part of the problem. Don't like that last sentence? Oh well, use something else then.

All I know is my computer has never run better, and will never use windows again except for 1 game that I might play once a month. To me, that's all windows is good for. Games.

---

### Post by Arup on 2009-07-08
A OS that comes in a DVD and doesn't even have basic office suite, spell check or a image manipulation program and costs close to $300+ is good for only one thing, pride of paying for it. Had linux been paid, we wouldn't see this much of bitching.

---

### Post by 3rdalbum on 2009-07-09
I don't have any problems saving straight to my home server from within any program.

I have the .gvfs directory inside my Bookmarks in Gnome and KDE, so it appears in the side panel of my Open/Save dialogs. Click that, and you get access to your mounted shares.

I agree, it should be there from the start (or a specialised button placed in the Open/Save dialogs to navigate to there); but that's no reason to start a flamewar.

---

### Post by Narcolepsy06 on 2009-07-09
It is a bit odd to see ryantollefson's story met with hostility.  Anyone in tech service knows that no matter how good you're product is, or how much you've improved on it, there are still situations, or people, that find a problem.  I think that since we are the willing members of the Ubuntu community we should be taking his problem in stride, and ask ourselves, "what can we do to make this situation more user friendly?"

---

### Post by cariboo on 2009-07-09
This is not a support forum, the op came here to rant about how something that didn't work, never asking for help to solve his problem. The only 4 posts he has made are in this thread.

---

### Post by jimv on 2009-07-09
> **HappyFeet said:**
> Well said.

How come just about every windows computer I come across runs so poorly that I consider it unusable? 

Because you're exaggerating.

---

### Post by marshmallow1304 on 2009-07-09
> **ryantollefson said:**
> From Firefox in Ubuntu you can't save directly to a shared location (didn't seem to matter what type of a share, just network locations in general).  From within the OS the network shares would work fine (e.g. if you save from Firefox to the desktop first, then transfer to the network share it was fine, just couldn't save directly).


This is interesting.  Just yesterday, I found that if I save a file directly to my Windows shared directory from FF3 in Windows, I can't do anything with it on my Ubuntu machine.  Perhaps these are related issues in FF.

---

### Post by Tamlynmac on 2009-07-10
> cariboo907
This is not a support forum, the op came here to rant about how something that didn't work, never asking for help to solve his problem. The only 4 posts he has made are in this thread.+1

Thank You for stating the obvious. This section of the forum is labeled "Ubuntu Testimonials & Experiences" under the heading of "Other Community Discussions". I doubt that many would come to this section bypassing the main support categories, if they were actually seeking assistance.

I've always wonder why anyone would search the forum and decide that this section was the appropriate section to post for assistance. Or use this section to circumvent the support categories, as a form of entitlement. I'm aware that any OS can be frustrating at times, but by posting a rant in this section of the forum in an attempt to gain assistance, one should not be surprised that the responses are targeted at the rant.

I'm also aware that the staff constantly move threads to other categories in an effort to assure responses. IMHO, this one is a candidate for the "Recurring Discussions" section.

Instead of naming this section Testimonials & Experiences, perhaps Rants & Complaints would have been more appropriate. ;)

---

### Post by 3rdalbum on 2009-07-10
> **cariboo907 said:**
> This is not a support forum, the op came here to rant about how something that didn't work, never asking for help to solve his problem.

Don't we have the right to response, to defend what is *not* an Ubuntu shortcoming?

---

### Post by cariboo on 2009-07-10
Of course you have the right to defend what the op sees as a shortcoming. I have my own opinion about some of these post that magically appear here, and you very rarely if ever see the op asking questions in the support forums, or anywhere else for that matter.

---

### Post by jimv on 2009-07-10
> **cariboo907 said:**
> Of course you have the right to defend what the op sees as a shortcoming. I have my own opinion about some of these post that magically appear here, and you very rarely if ever see the op asking questions in the support forums, or anywhere else for that matter.

It's not uncommon for someone to make a alternate account just to vent in order to keep their identity secret.

---

### Post by ddrichardson on 2009-07-10
> **cariboo907 said:**
> Of course you have the right to defend what the op sees as a shortcoming. I have my own opinion about some of these post that magically appear here, and you very rarely if ever see the op asking questions in the support forums, or anywhere else for that matter.
This is the reason [I proposed]("https://wiki.ubuntu.com/Forum/Spec/TestimonialTeam") a new team to work in the testimonial section.  It seems that there are often people whos first reaction is to  rant that can be turned around but its more than placating everyone as some people just like to whine (which i'm not suggesting in this instance).

---

### Post by cariboo on 2009-07-10
I agree with your idea, it just that some people don't want to be helped. 

> It's not uncommon for someone to make a alternate account just to vent in order to keep their identity secret. 

If you read the Code of Coduct ip addresses are recorded, if any one is found to have created an account to hide thier identity the account is usually banned.

---

### Post by ddrichardson on 2009-07-10
> **cariboo907 said:**
> I agree with your idea, it just that some people don't want to be helped.
True but some are just misguided, some don't grasp that it isn't a company that can be yelled at to make it work and some are just those sort of people.  Gary Larson expressed it pretty well: [http://is.gd/1tT95](http://is.gd/1tT95)

---

### Post by Tamlynmac on 2009-07-10
> ddrichardson
This is the reason [I proposed]("https://wiki.ubuntu.com/Forum/Spec/TestimonialTeam") a new team to work in the testimonial section.

Might I suggest that one of the primary focuses of this group is to divert posts that are ranting in an attempt to obtain assistance, to the proper help section. Even to the point of editing their post (eliminating the rant). I'm not certain how that could be accomplished, but with direction communications between the ranting OP and one of the staff a compromise could potentially be reached in a brief period of time. Refusal of compromise is an issue that can be debated in the RC or simply permit the thread to follow the anticipated path to it's demise.

Perhaps, the solution resides in a few dedicated staff members whose sole purpose is to monitor this section and endeavor to selectively address threads that appear to contain rants that are influenced by frustration involving a potentially correctable issue. Of course, these staff members don't have to be totally dedicated to that objective - but it would be their primary.

If the goal is truly to retain individuals who project a specific behavior pattern (words) in their posts, I believe this is a feasible and a worthy objective. I would suggest that the staff members be knowledgeable enough to ascertain the difference between issues that are or are not correctable. For example, a hardware incompatibility issue may require replacement and the OP may not be in a position to replace said hardware. Or if said OP doesn't receive any responses to their assistance request, the monitoring staff member should intervene within a reasonable period of time.

I'm certain specific criteria would need to be established identifying how to negotiate with this type of poster and an effort should be made to minimize hostility. I think this is an admirable concept that is riddle with potholes and the forum should be extremely cautious when implementing such a concept. IMHO the individuals who are assigned this task will need to be screened for their ability to negotiate with individuals of this nature.

I can visualize many issues resulting from this type of intervention. Some may even complain that their right of free speech and expression is being negated by the actions of the staff. This concept on the surface appears fundamentally based in good intentions. However, I might suggest investigating and perhaps even testing the viability of this concept prior to implementation. But I'm certain you've already considered that.

Just my $0.02

---

### Post by Garrovick on 2009-07-11
Ubuntu and Netbooks work fine.  IF one remembers to keep it simple and remembers that Netbooks are for music, e-mail and web surfing.

I have VLC and commercial DVD capabilities, Music, and Podcasts.

I think of my Acer as a giant "iTouch", NOT one of those $1000 dollar MACs

---

