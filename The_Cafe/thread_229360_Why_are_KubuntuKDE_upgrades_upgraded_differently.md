---
title: "Why are Kubuntu/KDE upgrades upgraded differently?"
date: 2006-08-04
forum: The Cafe
---

### Post by Jucato on 2006-08-04
Just a simple question that has been lingering in my head for quite a while. I'm not bashing anyone. I'm not implying any bias. I'm just really curious as to how things are developed "behind the scenes", specially with regards to Kubuntu. So here it goes:

- Firefox 1.5.0.3, the Firefox version shipped with Ubuntu Dapper, is found in Dapper main.
- Amarok 1.3.9, the version shipped with Kubuntu Dapper, is also found in Dapper main.
- KDE 3.5.2, the release shipped with Kubuntu Dapper, is also found in Dapper main.

- When Firefox 1.5.0.4 and 1.5.0.5 came out, the upgrades were made available through dapper-security main
- When Amarok 1.4 and 1.4.1 were released, a special repository had to be created and added in order to upgrade.
- When KDE 3.5.3 and, just recently, KDE 3.5.4 were released, a special repository also had to be created and added.

Now, by definition, packages in Main are those that are fully supported by Ubuntu, and would come with security updates. Now, it could be argued that the Amarok releases are not strictly security related updates, but KDE's releases are.

Now my question really is: Why do upgrades in Kubuntu have to be put in a special repository? What's the development/upgrade process in Kubuntu?

Just really interested to know. Hope I haven't offended anyone with the post.

---

### Post by ComplexNumber on 2006-08-04
although i don't have a definitive answer to your question, i would reason that firefox is many peoples only browser, and because it is in constant connection with the internet, security for it is of much greater importance than the need to have the latest amorak or kde. although kde could include important security updates, perhaps, in this case, that didn't apply.
not quite sure if that helps.

---

### Post by asimon on 2006-08-04
As I understand it amarok and KDE weren't updated in main because generally there should go no new versions into the repo after a release - therefore it's called stable. Thus amarok and KDE were made available via a seperate repo by Kubuntu to make it easy to install them.

The new Firefox versions got into main because they fixed important security issues. Just backporting the fixes into the dapper firefox version was probably pointless because the security fixes were nearly the only changes in these new versions.

But I see that now a new Gnome version entered Dapper, but KDE 3.5.4 didn't. So whatever the update policy for Dapper is, it's not consistent.

---

### Post by Jucato on 2006-08-04
@ComplexNumber: "Firefox is many peoples only browser" - quite understandable. But then again, KDE is the only/main desktop environment of Kubuntu, so the same reasoning should apply, right? Of course, Firefox is a web browser, which makes upgrading to the latest versions doubly important. 

@asimon: as I understand it, no new packages should go into a repo after release. But new versions are allowed because of bug fixes and security patches, but only through the other non-main repos: security-updates, dapper-updates and backports.

Which begs the question: What's the use of the backport repositories, anyway?

It hasn't only happened in Dapper, but in Breezy as well. I'm quite confused about their update policy. Don't get me wrong. I'm glad that they're making the latest versions of KDE, Amarok, and KOffice available, even if it's through extra repositories. However, I just want to try to understand why it has to be like that. Also, adding repositories in order to upgrade a system isn't something newbies should have to go through, right?

---

### Post by givré on 2006-08-04
I don't now as well the utility of dapper-backport if don't use it for that kind of things.
For the kde upgrade in main, i think it couldn't happens because they add new feature. What they could do is just to take only the bugfixing of kde-3.4 and to backport them to the official one, but i guess it's something too big to be all done (but i guess they do that for a great part).

---

### Post by Jucato on 2006-08-04
@givre: If you don't mind, I just have to quote this from that other thread:

> **givré said:**
> Security update of firefox are important because it is the door to the net.
Amarok 1.4.1 & kde 3.5.4 add new feature so they can't put them in main, but they are kind enough to creat a special repo for them.
But you will probably ask why they update gnome and not kde. In fact the update of gnome to 2.14.3 are just bug fixing update, not like kde one.
In my view, all update that just fix bug and don't add feature (that could add bug) can be push in main, but not the other.
The excpetion will probably be openoffice 2.0.3 which is for the moment in dapper-proposed.

Now for my rebuttal...

[http://mail.gnome.org/archives/devel-announce-list/2006-August/msg00001.html](http://mail.gnome.org/archives/devel-announce-list/2006-August/msg00001.html)
(then read the notes for each category)

There are also some added features besides the bug fixes as well. AFAIK, both GNOME and KDE do not allow significant or big new features when they release maintenance releases (GNOME 2.14.3, KDE 3.5.4).

What has really made me wonder about this whole process is the still existing problem with FLAC support in Amarok 1.4.1, which seems to be a problem with libxine. Some people have been able to solve it by compiling a more current version of libxine/xine-lib. However, no patch or update has come from Kubuntu, even if they officially released Amarok 1.4.1. It has made wonder if the situation would have been the same if Amarok 1.4.1 was upgraded through the official repositories.

... no one seems to know what the backports are for... :(

---

### Post by Terracotta on 2006-08-04
> **givré said:**
> I don't now as well the utility of dapper-backport if don't use it for that kind of things.
For the kde upgrade in main, i think it couldn't happens because they add new feature. What they could do is just to take only the bugfixing of kde-3.4 and to backport them to the official one, but i guess it's something too big to be all done (but i guess they do that for a great part).

These are only new features in the 3.5.x series (because of the postponement of KDE 4), but in hoary you also had to use extra repositories to get KDE 3.4.1 (I think) or more. I understand why they don't upgrade from 3.4 to 3.5, but I don4t understand why they don't upgrade from 3.4.0 to 3.4.1 for example. Once KDE 4 is released the 4.x.1-3 version will all be just bugfixes. But ok, at this very moment ;-) it's understandable to just use extra repositories.

---

### Post by Jucato on 2006-08-04
Breezy ships with KDE 3.4.3. To upgrade to KDE 3.5, you need to add the extra repositories. Understandable. But to get KDE 3.5.1, you need another extra repository. Same with KDE 3.5.2 in Breezy. Then rinse and repeat for Dapper, this time starting with KDE 3.5.2 instead.

Oh well, another one of the mysteries of Ubuntu development. Is there a more appropriate venue for questions like this? I rarely see anyone directly involved with Ubuntu development browse through here...

---

### Post by dissidentcitizen on 2006-08-04
I don't recall ever hearing anything specific on the subject but I've been messing about with Ubuntu/Kubuntu since warty and I believe it has to do with stability and bug-squashing. During the development of a new ubuntu version they keep upgrading newer software versions until they reach a "freeze" point, where they keep that snapshot and then the devs work on fixing major and minor bugs in the release to polish it up for the final release, which for obvious reasons have to be very stable and secure.

So in the case of Ubuntu, they have the Gnome +1 release date which allows them to get the newest version and they spend a month on quality control before the release the product.

Now since Kubuntu and Xubuntu are tied directly to Ubuntu they also run along the Gnome release schedule, whereas the KDE and XFCE issue arbitrary releases when they're done. Interestingly I think mark shuttleworth was talking recently about Kubuntu getting its own release schedule when it matures a bit more, but I don't know how that would work with still using the same Ubuntu base.

So what happened in Dapper development was they froze with KDE 3.5.1 but then 3.5.2 came out and since release was pushed back I guess they issued a freeze exemption to put it in and iron out all the bugs. So the release version has a KDE with additional bigfixes but an updated KDE would just be the binaries from the latest KDE source. It would be redundant to fix these new KDE versions or Dapper because thats what they're doing in Edgy, and they're focusing their energies on developing the new Kubuntu.

I guess what I'm getting at is that, putting in a new KDE, even it has bigfixes and things like that, is too great a potential for breakage, something that the devs want to avoid people having on mission critical systems and things like that. KDE 3.5.4 is a really good example. Even the "fixed" release hosed my computer. Wireless stopped working, Konqueror couldn't add new search engines, font antialiasing broke were just a few of the problems I had.

Getting the newest KDE was always a problem for the less tech savvy users such as myself. People are always going to do it, but at least Kubuntu has a good mechanism for those people that mainly stops them breaking their systems. Back in the Mandriva days people would put up their own unofficial rpms of new versions which often were bit dodgy to say the least. So the great thing about Riddell doing them for Kubuntu is that since he's the main developer they are almost always of excellent quality. I tend to think of them as "presents" to Kubuntu users from the devs. Little Amarok bugfix releases started a tradition of putting up the new versions, as well as KOffice more recently. Since the new versions weren't particularly likely to break your system I think the devs are happy to have them out there but they just dont want to make them compulsory and risk breaking everyones distro as would have happened if they have shoved the initial 3.5.4 in main.

Individual repos I guess is a better idea than something like debian unstable because it allows you to pick and choose which version and applications you want to upgrade, and since I plan on going back to KDE 3.5.3 with Amarok 1.4.1 this is quite handy. If you want to always have one listing in your sources list to always get the latest KDE there is a KDE-latest subfolder on the Kubuntu.org server..... Source-o-matic can generate one which will always fetch the latest KDE/Amarok/KOffice.

On the subject of newbies given there are minor risks  I think it also falls in line with the unspoken Ubuntu philosophy of "if they don't know how to do it, they probably shouldn't be doing it yet".

Firefox didn't used to get updated. It would just stick at the freeze version until the next Ubuntu release. Backports started unofficially as a way to get the updated programs, and were eventually recognised by the devs and made official. Recently I've noticed the security team keeping Firefox current, presumeably because so many people are demanding the latest version as well as the security benefits as the systems browser. Also considering its 'flagship application' status it pays to show it some love. Backports I guess handles other updated programs the devs aren't interested in.

The issues to do with updating one program like Firefox or Amarok are small enough that I believe its easy to keep it stable and prevent breakage, and therefore make it an official update.Remember there was no official Firefox 1.5 backport for Breezy because the devs said it was too much of an undertaking. Firefox is so embedded in the centre of Ubuntu a major revision would have forced them to update a whole load of other stuff. Minor bugfixes like 1.5.0.4 dont have this problem. The distinction between Firefox and Amarok is that Amarok doesn't have the same security necessity to see it "officially" updated in main I think.

Anyway there is a bit of inconsistency in the update policy but I still think it works as well as it can. I hope this rambling tale of magic and heroism and demonstrated there is a little bit of method to this madness :)

Lastly I don't think Kubuntu devs hang out much on the forums. They mainly work through IRC (default connection through Konversation will take to the Kubuntu channel) and the development mailing lists. They have blogs with email addresses and things like that though...

---

### Post by Jucato on 2006-08-05
Thanks for those points. 

I do understand the thing about the feature freeze phase of development. But AFAIK, Ubuntu updated to GNOME 2.14.3 just recently, but they didn't have a special repo for it.

The discrepency between the release schedules of GNOME/KDE and Ubuntu/Kubuntu has been one of the strongest (or probably just the most famous) justification for those wishing to have a separate release date for Kubuntu. 

Anyway, I personally don't mind having to add extra repositories to upgrade KDE, Amarok or KOffice. In fact, I'm quite grateful. You're right, it's sort of a gift from the Kubuntu devs. By all means, no new versions should even make it into the upgrades, even GNOME 2.14.3, unless they are critical bug fixes/security patches. But I've seen too many people stumble on this and thought that they could have made it a bit easier if upgrades were incorporated into a more permanent repository. Perhaps they could also just introduce the upgrades into the backports, so that mission critical systems can just safely ignore it, while people who do want to upgrade can safely enable it. I've also seen some people approach the Kubuntu extra repository with suspicion just because it's not part of the original Ubuntu repositories. I can't blame them for trying to be safe.

One thing I don't agree with you on is the "if they don't know how to do it, they probably shouldn't be doing it yet" point. Most new users don't know how to add MP3 support in Ubuntu. But it doesn't mean they shouldn't be doing it yet, right? If it weren't for projects like Automatix and EasyUbuntu, some of them would probably still be stuck.

Anyway, thanks for the input. I just wish there was a dev who could clarify this. (Maybe I should ask J. Riddell?)

---

### Post by dissidentcitizen on 2006-08-05
I think its definitely worth giving Riddel a PM on IRC or at least an email.

I was unaware of the Ubuntu Gnome 2.14.3 update, that is something that really doesn't fit with update policy and should be questioned. I guess the only justification they would come up with would be its security/bugfix status and that it was a majority decision by the devs based on a review of its stability. It raises all sorts of questions about the KDE updates then. I guess the fact that the new features and not just bugfixes could be a sticking point.

I still think keeping Amarok in a different repo to KDE and to KOffice is the way to go though, gives people more freedom in choosing updates for their system! Maybe KOffice and Amarok could join, but for me a KDE update sometimes isn't a good thing.

Keep up posted if you hear anything from the Devs!

---

### Post by Jucato on 2006-08-05
I will probably just send him an e-mail. I'm a bit "IRC-shy". :p

I think new Amarok and KOffice versions don't really need to be put in the main repositories, unless they are very serious bug/security fixes. But new versions of KDE and GNOME are different matters. Also, Firefox is a different issue, so I think it justifies new versions being included in the main repos.

I'm thinking of two alternatives to this upgrading thing:

1. Put all KDE-specific upgrades in one single separate Kubuntu repository which can be included during installation. Something like a "deb [http://archive.ubuntu.com/kubuntu](http://archive.ubuntu.com/kubuntu) dapper...." something. 

2. Put them in the other existing/available Ubuntu repositories, like the Backports.

Users have always had the choice of upgrading their system, when, and how. Heck, they can even choose not to upgrade, by disabling the other repositories, or ignoring the updates.

Another question (which I mentioned earlier) comes to mind: what happens when the latest upgrade has an issue with something from the main repositories? Specific example: Amarok 1.4.1 and libxine. 

And another question: What are dapper-upgrades for? What's the difference between dapper-upgrades and security-upgrades.  So now we have 3 repositories that we have little knowledge (or very basic knowledge) of: backports, security-upgrades, and dapper-upgrades.

A new user might not be interested in this. But I am. :D

---

### Post by Terracotta on 2006-08-05
> **Fenyx said:**
> I will probably just send him an e-mail. I'm a bit "IRC-shy". :p

I think new Amarok and KOffice versions don't really need to be put in the main repositories, unless they are very serious bug/security fixes. But new versions of KDE and GNOME are different matters. Also, Firefox is a different issue, so I think it justifies new versions being included in the main repos.

I'm thinking of two alternatives to this upgrading thing:

1. Put all KDE-specific upgrades in one single separate Kubuntu repository which can be included during installation. Something like a "deb [http://archive.ubuntu.com/kubuntu](http://archive.ubuntu.com/kubuntu) dapper...." something. 

2. Put them in the other existing/available Ubuntu repositories, like the Backports.

Users have always had the choice of upgrading their system, when, and how. Heck, they can even choose not to upgrade, by disabling the other repositories, or ignoring the updates.

Another question (which I mentioned earlier) comes to mind: what happens when the latest upgrade has an issue with something from the main repositories? Specific example: Amarok 1.4.1 and libxine. 

And another question: What are dapper-upgrades for? What's the difference between dapper-upgrades and security-upgrades.  So now we have 3 repositories that we have little knowledge (or very basic knowledge) of: backports, security-upgrades, and dapper-upgrades.

A new user might not be interested in this. But I am. :D


You can have the latest amarok kde koffice in your sources.list:
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main 
deb [http://kubuntu.org/packages/koffice-stable](http://kubuntu.org/packages/koffice-stable) dapper main 
# deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main 
deb [http://kubuntu.org/packages/amarok-stable](http://kubuntu.org/packages/amarok-stable) dapper main 
# deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main 

Difference between amarok/koffice-stable and amarok/koffice-latest is that amarok/koffice-latest contains beta versions as well, where as amarok/koffice-stable does not.
I have no idea why they don't include it in the original sources.list (but commented out of course) for kubuntu.

---

### Post by Jucato on 2006-08-09
I was able to have a (very) brief conversation with Jonathan Riddell over at the IRC (#kubuntu) and I asked him about these questions. These were the answers I got:

1. Why isn't KDE 3.5.4 in dapper-updates:
- KDE 3.5.4 had some problems so he didn't want to put it in -updates
- manpower issues
- the Kubuntu team has more freedom to do what they want/need to do if it's in just in Kubuntu.org

2. Is the special repositories for KDE official?
- Yes, it is official Kubuntu (take note, Kubuntu, not Ubuntu), since it was made by Jonathan Riddell. And for those who might not know it yet, Jonathan Riddell is Kubuntu. :D

3. Will it ever be put into the Backports?
- While backports is the best place for it, backports has been non-functional for quite some time and has no signs of changing, so it can't be used

Well, that has satisfied my curiousity and taken away my doubts. I would have asked Riddell more, but I immediately got sweaty hands an butterflies in my stomach just talking to him. :D

---

### Post by bailout on 2006-08-22
> **Fenyx said:**
>  Jonathan Riddell is Kubuntu. :D



I thought and hoped kubuntu had moved on from being a one-man band?

I still think kbuntu gets treated a bit like the ginger stepchild of ubuntu tbh.

I have been pleased to see the updated kde packages in the kubuntu repos.

---

### Post by Jucato on 2006-08-23
> **bailout said:**
> I thought and hoped kubuntu had moved on from being a one-man band?

It's has moved on. What I meant to say was that since it came from Jonathan Riddell, it's official Kubuntu, because what he does is Kubuntu. Of course, the number Kubuntu developers have increased and are still increasing.

Well, let's just think of Kubuntu as a younger sibling of Ubuntu, which would be chronologically accurate. That makes Xubuntu the youngest, and Edubuntu, a cousin. :D

---

