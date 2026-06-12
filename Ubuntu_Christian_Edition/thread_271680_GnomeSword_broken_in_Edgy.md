---
title: "GnomeSword broken in Edgy"
date: 2006-10-05
forum: Ubuntu Christian Edition
---

### Post by LaserJock on 2006-10-05
Hi!
  I'm not sure if many of you have been testing the up-coming Edgy release but it appears GnomeSword is broken. The Sword library has been updated but GnomeSword won't build using the new library. If somebody wants to look into this raphink or I can sponsor an upload.

-LaserJock

---

### Post by Raphink on 2006-10-05
Some more debugging infos:

@LUCENE_LIBS@ is not defined at build. This seems to come from a lack of declaration in the m4 file. Adding a declaration for the clucene libs might allow it to build properly.

---

### Post by brokencrystal on 2006-10-08
I am having the same problem.  Even with the beta version of edgy.  Scary, with the final release so close...

---

### Post by sawjew on 2006-10-08
Gnomesword would not install because it had a broken dependency on libsword5c2a.  libsword6 is in the repositories not libsword5c2a.  I just manually downloaded and installed libsword5c2a from the Dapper repositories and it now works fine.

---

### Post by pirast on 2006-10-19
Still broken.. Maybe it should be investigated into this problem so that the Edgy based Ubuntu CE can ship with gnomesword.

Changing libsword is not the solution.

---

### Post by mhancoc7 on 2006-10-19
> **pirast said:**
> Still broken.. Maybe it should be investigated into this problem so that the Edgy based Ubuntu CE can ship with gnomesword.

Changing libsword is not the solution.

I currently have no plans to move Ubuntu CE to Edgy. Ubuntu CE will probably stay with Dapper until the next LTS release.
God Bless, Jereme

---

### Post by pirast on 2006-10-20
Sorry, but what's the point in using Ubuntu CE then? 

I have nothing against Dapper but users definitely want to have the features and bug fixes that are released in Edgy for Ubuntu CE.

---

### Post by mhancoc7 on 2006-10-20
> **pirast said:**
> Sorry, but what's the point in using Ubuntu CE then? 

I have nothing against Dapper but users definitely want to have the features and bug fixes that are released in Edgy for Ubuntu CE.

Well, Ubuntu CE is based on Dapper for a reason. It is an LTS (Long Term Support) release and is going to be the more stable than Edgy. I feel that it is more important to offer a stable distro as opposed to offering one that may offer some new and cool features that is less than stable. Once the next LTS release comes out we will move in that direction. Of course the thing about Ubuntu CE is that it can flow with Ubuntu. So if Edgy proves to be very stable and becomes the accepted install of the majority then it will of course be considered. However, I am more than likely going to want to stick to Dapper until the next LTS release.

I hope that helps explain my thought process.

Thanks, Jereme

---

### Post by Raphink on 2006-10-20
> **mhancoc7 said:**
> Well, Ubuntu CE is based on Dapper for a reason. It is an LTS (Long Term Support) release and is going to be the more stable than Edgy. I feel that it is more important to offer a stable distro as opposed to offering one that may offer some new and cool features that is less than stable. Once the next LTS release comes out we will move in that direction. Of course the thing about Ubuntu CE is that it can flow with Ubuntu. So if Edgy proves to be very stable and becomes the accepted install of the majority then it will of course be considered. However, I am more than likely going to want to stick to Dapper until the next LTS release.

I totally understand where you come from on this decision. However, Dapper being more stable than Edgy is more of a belief than a fact in my opinion. LTS as you pointed out means "Long Term Support". Although it is true that the Ubuntu team made their best to actually make it more stable and thus sustainable on the long run. 

What LTS means is only that it will be officially supported by Canonical for 3 years on the desktop and 5 years on the server side, releasing security updates for these for all this time. 

LTS releases are not predictable. They happen when the open-source world provides a suitable environment for a release that is likely to be more stable.

I really doubt Canonical is going to support more than 2 LTS at the same time, which obviously means that there won't be another LTS before at least 2 years...

The stability of a release relies mostly on the work of developers. Users of Ubuntu CE are average users and won't wait 2 years for a new release, so if no one fixes Gnomesword, Ubuntu CE will be broken next month, and for the next 6 months. I hope you understand Ubuntu CE is currently the only project to ship Gnomesword by default...

Now if that's your choice to only use LTS releases, see you in 2 years :)


God bless

Raphaël

---

### Post by linux_learner on 2006-10-20
I don't think it's GS (Gnomesword) that is broken. I think it's sword-1.5.9. I just tested gnomesword 2.1.7 with sword-1.5.8 and it works. I will give sword-1.5.9 a try from the source, and see how that goes.

---

### Post by Raphink on 2006-10-20
> **linux_learner said:**
> I don't think it's GS (Gnomesword) that is broken. I think it's sword-1.5.9. I just tested gnomesword 2.1.7 with sword-1.5.8 and it works. I will give sword-1.5.9 a try from the source, and see how that goes.

No, sword 1.5.9 works perfectly well. It's gnomesword that lacks clucene libs detection in m4 files to build properly. Gnomesword builds fine with sword 1.5.8 because clucene libs are not activated in sword 1.5.8, that's all. But since using clucene is an option in sword, gnomesword should support it. So it's a gnomesword issue, and it should be patched.

---

### Post by linux_learner on 2006-10-20
I would suggest reading the sword mailing list. [http://www.mail-archive.com/sword-devel@crosswire.org/msg11289.html](http://www.mail-archive.com/sword-devel@crosswire.org/msg11289.html)

---

### Post by Raphink on 2006-10-20
> **linux_learner said:**
> I would suggest reading the sword mailing list. [http://www.mail-archive.com/sword-devel@crosswire.org/msg11289.html](http://www.mail-archive.com/sword-devel@crosswire.org/msg11289.html)

Yes, the issue is linked to this. This thread is about including the clucene m4 file in sword, which has been done already, and allows to build using clucene now. This is how sword 1.5.9 was built with clucene support. Now Gnomesword needs to use this aswell, in order to build with clucene.

---

### Post by mhancoc7 on 2006-10-20
> **Raphink said:**
> I totally understand where you come from on this decision. However, Dapper being more stable than Edgy is more of a belief than a fact in my opinion. LTS as you pointed out means "Long Term Support". Although it is true that the Ubuntu team made their best to actually make it more stable and thus sustainable on the long run. 

What LTS means is only that it will be officially supported by Canonical for 3 years on the desktop and 5 years on the server side, releasing security updates for these for all this time. 

LTS releases are not predictable. They happen when the open-source world provides a suitable environment for a release that is likely to be more stable.

I really doubt Canonical is going to support more than 2 LTS at the same time, which obviously means that there won't be another LTS before at least 2 years...

The stability of a release relies mostly on the work of developers. Users of Ubuntu CE are average users and won't wait 2 years for a new release, so if no one fixes Gnomesword, Ubuntu CE will be broken next month, and for the next 6 months. I hope you understand Ubuntu CE is currently the only project to ship Gnomesword by default...

Now if that's your choice to only use LTS releases, see you in 2 years :)


God bless

Raphaël

Thanks for clearing up a little of my misunderstanding of the LTS release. I guess I was thinking that when the 3/5 years ran out on Dapper there would be a new LTS release ready. Well, in light of this new info I will basically follow what will provide the most stable and funtional desktop. As for waiting two years for a new release. I will not have to wait for two years for a new release. Yes the base may not change, but there will be tweaks and such along the way.

So you say that Gnomesword is going to be broken. So do you mean that the version available via the Dapper repos will be broken? I definitely want to keep my eye on this. Will this affect BibleTime?

Thanks, Jereme

---

### Post by Raphink on 2006-10-20
> **mhancoc7 said:**
> Thanks for clearing up a little of my misunderstanding of the LTS release. I guess I was thinking that when the 3/5 years ran out on Dapper there would be a new LTS release ready. Well, in light of this new info I will basically follow what will provide the most stable and funtional desktop. As for waiting two years for a new release. I will not have to wait for two years for a new release. Yes the base may not change, but there will be tweaks and such along the way.

What I'm saying is that users will switch to Edgy soon, they will not stick to Dapper for years, and if you don't support Edgy, there will be breakage. There might actually even be upgrading issues when switching to Edgy.

However, you want to still work on a Dapper basis, are you familiar with backports?


> So you say that Gnomesword is going to be broken. So do you mean that the version available via the Dapper repos will be broken? I definitely want to keep my eye on this. Will this affect BibleTime?

So you really don't mind to fix your main program. You rather close your eyes, cross your fingers and hope someone else will do it for you. The Dapper version will not be broken. Dapper is frozen, the versions in it won't change. As of BibleTime, we have version 1.6 in Edgy now, built on top of sword 1.5.9, and it works like a charm.


Raphaël

---

### Post by mhancoc7 on 2006-10-20
> **Raphink said:**
> What I'm saying is that users will switch to Edgy soon, they will not stick to Dapper for years, and if you don't support Edgy, there will be breakage. There might actually even be upgrading issues when switching to Edgy.

However, you want to still work on a Dapper basis, are you familiar with backports?

So you really don't mind to fix your main program. You rather close your eyes, cross your fingers and hope someone else will do it for you. The Dapper version will not be broken. Dapper is frozen, the versions in it won't change. As of BibleTime, we have version 1.6 in Edgy now, built on top of sword 1.5.9, and it works like a charm.


Raphaël

  	 	 	 	 	 	 	 	 	  Wow! Just when I think we are going to have a civil discussion...

Are you aware of how things like, "So you really don't mind to fix your main program. You rather close your eyes, cross your fingers and hope someone else will do it for you.", sound? I mean really is this how you want our "relationship" to continue?

I wished you could just understand what the Ubuntu CE project is about. We are offering a pre-tweaked version of Ubuntu for Christians. This allows us to incorporate things that Ichthux will not be able to due to the fact that we will always choose the users needs and desires over a philosophical need to stay completely open-source. We of course will choose open-source solutions over non-open-source ones when available.

I don't have any current plans to delve into working on the base Ubuntu. I plan to continue doing what I am doing. I plan to tweak Ubuntu CE to be usable for the end user offering the best features possible. Is it a "hackish" way of doing it? Yes one could call it that. I like to think that I am doing a lot of the "tweaking" that we all do post Ubuntu install. I am not trying to bash Ubuntu. I love Ubuntu and think it is the BEST Linux distro ever. That is why I chose it to base Ubuntu CE on.

I really can't express how frustrated I am with your attitude. I have considered posting in the Ichthux forums from time to time to give my opinion, but I didn't want to come across as trying to "cherry-pick" from your user base which is what it sometimes seems you are doing. I have tried to so support for your project from day one. I just wished you could do the same for me. I know that you think that somehow you are trying to help my pushing me to your way of thinking. I am also aware of the fact that you tried my method before without success. I know this because you told me so let's not revisit that. I have watched your project for a number of years. 

The Ubuntu CE project is NOT the same as the Ichthux project. For those who have not noticed the obvious tension between Raphael and myself, I apologize and would just like to say that this has been boiling for quite a while. I really wished we could get along, but I feel as though my project is under attack. It is amazing, I thought after Ubuntu CE proved that it was a valid project to those who are not Christian that I could just move forward. Now it seems that another Christian Linux project is doing the attacking. 

Raphael your unwillingness to open your mind to my vision dissappoints me. I wish you the best with your project. Considering our obvious issues would you like me to remove the link to your project site from my sites?

God Bless, Jereme

---

### Post by Raphink on 2006-10-20
Jereme,

It really seems we have a communication problem. The reason why I've been posting on this forum before and today again is because I care that users get the best quality of service when using the OS they choose, whether it's Ichthux or Ubuntu CE. Now as it is, I do not have the time to fix Gnomesword, and users of Ubuntu CE will eventually upgrade to Edgy and find a broken Gnomesword if no one fixes it. I am just warning you of this fact, and I am sorry you see this as an attack. I do not intend to criticize you or bash your project, I am just saying "be careful, this is going to break soon." If someone comes and tell me my house is going to break down, I'll thank him, I won't tell him he should be quiet and not point it out, and obviously I won't tell him "Oh, shut up, I only live in this house, the fact that the wall is going to fall is not my problem, someone else will fix it."

I really don't mind that you work the way we do or not. I mind that the users can rely on what they use, and be sure that Ubuntu systems will provide proper technical solutions to there needs.

When it comes to the Ichthux forums, you have always been welcome to them to suggest or point out anything about Ichthux. If there is anything that needs to be improved or fixed in Ichthux, I'm happy when people tell me. Some people have even come and posted about other distributions on the Ichthux forums and have been welcome. Again, I don't mind what people use. I mind that it works for them, on the long run. And Ubuntu CE is going to break if you don't do anything to fix it.

You are listed as a distribution on many websites, and as such people consider you are responsible for the packages you ship. I hope you are also aware that many users consider you are an official Ubuntu developer running an official Ubuntu project because of the name of this project. I am not inventing this, I saw it on several forums on the Internet. I have been warning you about that: because of your choices, people expect things from you that you can't provide.

When it comes to frustration, I could say I am very frustrated by the way new users give in totally into scripts without considering how bad it will bork their install in the near future, and of the fact that the name you have chosen will make people think Ubuntu is responsible for the breakage. I am frustrated by the fact that people see the nice paint on Ubuntu CE but they don't see the wood that's breaking under it.

I am not attacking you, Jereme, I am warning you. I am frustrated by your pride in thinking you can reinvent a stable distribution system from scratch when it took years to develop by tens of developers, and by what you are letting new users to think about the stability of it.

I am very sorry for the people who will read this thread and I just want to say that I do all this because I care for my brothers and sisters in Christ. I care for you, Jereme, and for the time I see you spending on a solution that will eventually break, and I care for the users who will soon upgrade to Edgy and be disappointed by the issues they'll have and blame Ubuntu for them. I wouldn't post this if I didn't care. I would just shut up and not take the risk to be taken as a troller.

Now if you still think my goal is to bash you and put you down, alright. I took the risk once again to let you know about imminent problems you might have, and once again you have replied agressively. I guess I should have stayed quiet as I did in the last few weeks, and so I will in the future. I have spoken enough, and what will happen is not up to me.


Good luck & God bless

Raphaël

---

### Post by mhancoc7 on 2006-10-20
@Raphael

I am sorry that you see me as the aggressor. I would appreciate your "warnings" if you didn't say things like, "So you really don't mind to fix your main program. You rather close your eyes, cross your fingers and hope someone else will do it for you". Can you see how I could be angered by this.

As far as our projects name. We asked for permission from Canonical and they gave us permission. So that should be enough discussing that. 

As for users who opt to upgrade to Edgy. First, I know that many linux users think that everyone will want to upgrade to the latest and greatest. There are lots of linux users who would rather stay with Dapper since it is stable. If it meets your needs then why upgrade? If an Ubuntu CE user decides to upgrade to Edgy then they probably know a little more than the average user or at least have done their homework. I will be following the development of Edgy and will move to it when I feel that it will be a better base for Ubuntu CE.

I am aware that Ubuntu CE is listed as a distro. To me this is an argument over semantics. I mean would only be more confused if we made more of a distinction between what constitutes a "true" distribution. Ubuntu CE is a distro in the sense that you can download/buy it and install it to your computer. It comes with all the great Ubuntu apps and some added tools for Christians. Now, you could also say that it is not a distro, but it is an elaborate "hack" Ubuntu.

As for my "pride". I take offense to you judging me in that way. This is not about pride. This is about how you have treated me. I am not the only one who has noticed by the way. I have received emails from those who have watched our transactions and have given me their encouragement. 

As for those who assume that I am responsible for all the packages and what not. There really isn't much I can do about that. I have tried to make things clear in the FAQ page. I can only do my best to promote and explain my project and hope that users will read the documentation.

I apologize for being aggressive, but I am just tired of some of your remarks. I know that I am not just being defensive because I have read and responded to LaserJocks posts and have not felt slighted the way your posts do. LaserJock feels the same as you, but he does not make the same type of undermining comments. 

Anyway, I really see no end to this dispute and that distresses me greatly.

I hope and pray that we can resolve our differences. I also want to wish you well with your project. 

God Bless, Jereme

---

### Post by pirast on 2006-10-20
> 
We are offering a pre-tweaked version of Ubuntu for Christians.


Offering a pre-tweaked version of Ubuntu does not make it a distribution..

As raphink already said, it may confuse users that it is called "Christian Ubuntu" - it seems to be official. But it isn't. You are not even working together with the Ubuntu developers. Maybe you should make a visible note on your website that Christian Ubuntu is NOT official. 

> I don't have any current plans to delve into working on the base Ubuntu.

It is your bread.. But there's no real point in using Christian Ubuntu when it does not ship gnomesword. And there's no real point in using Christian Ubuntu when it is based on an old Ubuntu Release.

> There are lots of linux users who would rather stay with Dapper since it is stable. 
But they are not Ubuntu CE candidates.

---

### Post by mhancoc7 on 2006-10-20
> **pirast said:**
> Offering a pre-tweaked version of Ubuntu does not make it a distribution..

Again this is an [semantics]("http://en.wikipedia.org/wiki/Semantics") argument.

> **pirast said:**
>  As raphink already said, it may confuse users that it is called "Christian Ubuntu" - it seems to be official. But it isn't. You are not even working together with the Ubuntu developers. Maybe you should make a visible note on your website that Christian Ubuntu is NOT official.

This has been discussed at great length. The fact is that I approached Canonical and they gave me permission. So really that should be the end of the discussion. As for letting users know. That is what the [FAQ]("http://http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/faq.html") page is for. Notice what the first Q/A is.

> **pirast said:**
>  It is your bread.. But there's no real point in using Christian Ubuntu when it does not ship gnomesword.

As long as Ubuntu CE is based on Dapper Gnomesword will not be broken and will be included.

> **pirast said:**
> And there's no real point in using Christian Ubuntu when it is based on an old Ubuntu Release.

I disagree. Dapper is an LTS release. Not every user wants the newest thing out. Some of us just want it to work.

> **pirast said:**
>   			 				[quote=mhancoc7;1639907]  			 				There are lots of linux users who would rather stay with Dapper since it is stable. But they are not Ubuntu CE candidates.[/quote]

Again, I disagree. Many of those that have found Ubuntu CE have never used Linux. I assume you mean that every Ubuntu CE user will want to upgrade to Edgy. I do not agree. The fact is that for now Ubuntu CE is based on Dapper. We may move it to Edgy when we feel that it makes sense. For those that want to upgrade Ubuntu CE to Edgy they are more than welcome to. I feel that they will probably be more "seasoned" linux users and probably know the risks.

Jereme

---

### Post by Raphink on 2006-10-20
@Jereme

I am sorry of the way it goes really. I wish we could just sit around a table and talk. I feel frustrated by our failure of communication on the forums and over email.

As of following the development of Edgy, it's a bit too late, because Edgy will be released in 6 days. In 6 days it will be frozen and nothing will be changed in it anymore.

I do not want to have two communities fighting. I'd like us to be united and share, and I am sorry we are not able to communicate a proper way.

I'll pray for the relationship between our two projects.


God bless

Raphaël

---

### Post by mhancoc7 on 2006-10-20
> **Raphink said:**
> @Jereme

I am sorry of the way it goes really. I wish we could just sit around a table and talk. I feel frustrated by our failure of communication on the forums and over email.

As of following the development of Edgy, it's a bit too late, because Edgy will be released in 6 days. In 6 days it will be frozen and nothing will be changed in it anymore.

I do not want to have two communities fighting. I'd like us to be united and share, and I am sorry we are not able to communicate a proper way.

I'll pray for the relationship between our two projects.


God bless

Raphaël

Thank you for that. I totally agree. I do think that the loss of body language and such on a forum makes it difficult to communicate. Especially when differences of opinion arise. 

I too would like us to communicate better. I will do my best to do what I can to be less sensitive and hopefully more receptive to discussion.

I don't view Ichthux as a competitor, but as a similiar project that is trying to supply a Christian distro and honor the Lord in the process. I hope you feel the same. 

Now as far as the switch to Edgy. I am not opposed to it if it proves to be a stable platform for me to work from. I will just have to do some testing. Maybe I will offer a Dapper version and an Edgy version. :)

God Bless, Jereme

---

### Post by Raphink on 2006-10-20
When it comes to meeting physically, I would like to be able to attend the ICCM (International Conference on Computing and Mission) in February 2007.

The next edition of it will be in Chiang Mai, Thailand. This is very far for me, but God willing I might be able to go, and I would love it to be a place to meet with other Christian open-source developers.

Do you think you would be able to be there?

Edit: Doh! Forgot the link: [http://www.iccm-asia.org/](http://www.iccm-asia.org/)


God bless

Raphaël

---

### Post by mhancoc7 on 2006-10-20
> **Raphink said:**
> When it comes to meeting physically, I would like to be able to attend the ICCM (International Conference on Computing and Mission) in February 2007.

The next edition of it will be in Chiang Mai, Thailand. This is very far for me, but God willing I might be able to go, and I would love it to be a place to meet with other Christian open-source developers.

Do you think you would be able to be there?

Edit: Doh! Forgot the link: [http://www.iccm-asia.org/](http://www.iccm-asia.org/)


God bless

Raphaël

That sounds like a great event. I will not be able to attend however. We just do not have room in our budget for the trip. My wife is expecting our second child in March as well so I don't think February. :)

God Bless, Jereme

---

### Post by UberKnight on 2006-10-29
Hi Guys

Back to the actual topic ;) .

I discovered this error and [posted]("http://www.ubuntuforums.org/showthread.php?t=285641") a question about it a few days ago.

Does anyone know if a solution is being sought by the developers of Gnomesword, or how to bring their attention to the problem?

Please don't suggest I try and fix it as I'm a fairly new user :rolleyes: .

Regards
UberKnight

---

### Post by matthew on 2006-10-29
I found a solution and posted it in the thread UberKnight just mentioned.

---

### Post by shane2peru on 2006-10-29
Ok, I'm on Edgy, and GnomeSword works fine for me.  I'm very interested in Ubuntu CE upgrading to Edgy.  I have been waiting for Edgy, and actually left Dapper for a while, as it had issues with my computer.  When I came back and found Edgy working with my Palm, I was happy.  When I checked to see if CE had the upgrade script, I was saddened.  

  Do you think it is possible to make a conversion script for those of us Edgy users that would like to convert to CE, and see how many hits it gets.  I may be willing to be the guinea pig and give it a try.  I have found Edgy to be stable, and I have been very happy with it.  I switched a day or two before the actual release.  I don't know what it was about Dapper, but it didn't sit well with me, I also had problems with Dan's Guardian in Dapper, and actually ended up having to remove it.  I was hoping to see it in Edgy, new and improved.  That is my vote.  :-D 

Shane

---

### Post by mhancoc7 on 2006-10-29
> **shane2peru said:**
> Ok, I'm on Edgy, and GnomeSword works fine for me.  I'm very interested in Ubuntu CE upgrading to Edgy.  I have been waiting for Edgy, and actually left Dapper for a while, as it had issues with my computer.  When I came back and found Edgy working with my Palm, I was happy.  When I checked to see if CE had the upgrade script, I was saddened.  

  Do you think it is possible to make a conversion script for those of us Edgy users that would like to convert to CE, and see how many hits it gets.  I may be willing to be the guinea pig and give it a try.  I have found Edgy to be stable, and I have been very happy with it.  I switched a day or two before the actual release.  I don't know what it was about Dapper, but it didn't sit well with me, I also had problems with Dan's Guardian in Dapper, and actually ended up having to remove it.  I was hoping to see it in Edgy, new and improved.  That is my vote.  :-D 

Shane

The current plan for Ubuntu CE is to stay with Dapper since it is considered to be the more stable of the two. I might put together a special script for Edgy users. I will have to do some testing first.
God Bless, Jereme

---

### Post by shane2peru on 2006-10-29
Jereme,

   Great!  I will look forward to the script.  Thanks!

God Bless,
Shane Rice

---

### Post by theicyj on 2006-10-31
Has anyone got gnomesword working in Edgy yet?  I keep getting this error:
> gnomesword:
 Depends: libsword5c2a (>=1.5.8-7) but it is not installable

Any ideas?

---

### Post by matthew on 2006-11-01
> **theicyj said:**
> Has anyone got gnomesword working in Edgy yet?  I keep getting this error:


Any ideas?[http://www.ubuntuforums.org/showpost.php?p=1682605&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1682605&postcount=4)

---

### Post by theicyj on 2006-11-01
Awesome!  Thanks Matthew.

---

