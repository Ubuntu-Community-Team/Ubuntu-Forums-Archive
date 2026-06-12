---
title: "pretty good ubuntu review"
date: 2004-11-02
forum: The Cafe
---

### Post by jdodson on 2004-11-02
[check it out here.](http://www.osnews.com/story.php?news_id=8754).  overall its a good review though the author says its "impossible" to burn an Audio CD with ubuntu.  to elaborate a bit more, the author found it difficult.  in the end the author is still using ubuntu:)

---

### Post by jwb on 2004-11-02
I just switched from Fedora 2, and one of the primary things I love about Ubuntu is the fact that updating and installing software just plain work- every time. I used yum in Fedora, and had the craziest yum.conf you'd ever see. Sometimes it worked, sometimes it didn't. Using up2date only worked about 50% of the time. Yum worked most of the time, but seemed to get hung up quite a bit.

I installed the RC right before WW final (from mid-September) and when I upgraded it after install, it upgraded over 300 packages- bing, WW Final. No stalls or problems. And after 1 week, every single time I've used apt-get or Synaptic, it just works.

Good review, though.

---

### Post by jwb on 2004-11-02
Another thing I like about Ubuntu vs. Fedora. When you got an email from Fedora about a security update- it might be in up2date or yum, it might not.

Every single time I get an email about security stuff from Ubuntu- it's *there*.

Nice.

---

### Post by jdodson on 2004-11-02
[QUOTE=jwb]I just switched from Fedora 2, and one of the primary things I love about Ubuntu is the fact that updating and installing software just plain work- every time. I used yum in Fedora, and had the craziest yum.conf you'd ever see. Sometimes it worked, sometimes it didn't. Using up2date only worked about 50% of the time. [/QUOTE]

i hear ya.  i switched over from 'the core' as well.  i dig the core for servers and such, but for the desktop it is painful.

---

### Post by Slapdash on 2004-11-04
I read this one [REVIEW](http://www.newsforge.com/article.pl?sid=04/10/12/1421241) 

Sorta OK but touches on some problems.
I would like to know if it is maybe just in the users case?

---

### Post by jwb on 2004-11-04
[QUOTE=Slapdash]I read this one [REVIEW](http://www.newsforge.com/article.pl?sid=04/10/12/1421241) 

Sorta OK but touches on some problems.
I would like to know if it is maybe just in the users case?[/QUOTE]

It sounds like he was using one of the release candidates, or had not updated his system. 

For instance, the issue they mentioned with Firefox PR1(10.0)- I had that same issue with it on Fedora Core 2. I went back to FF 9.3, and the problem vanished. When FF 10.1 came out, I used it, and the problems with 10.0 were gone. I doubt too many people even noticed the bump from 10.0 to 10.1, but it gave me problems on Mandrake and Fedora with 10.0- clearly a FF issue.

The video issue wasn't an issue..... he was missing some stuff, just as he identified. This is an issue with the Linux distro's that are more careful about what they put in their distro for legal reasons or whatever. Like mp3 playback on RH/Fedora. You must know going in it ain't supported officially.

The network browsing issue- good chance it was his network. Anytime you deal with a network, there's a good chance somebody don't have their network set up. All nautilus is doing is some basic SMB stuff. If those pieces aren't in place right- Nautilus ain't your issue. 

(Of course, I could be 100% wrong...... computers are hateful that way, sometimes.) :-)

NTFS- As far as I know, NTFS is supported only as read-only under the 2.6 kernel. I've heard a technical explanation that made sense, but I don't recall it fully. Something about the actual spec for NTFS is propriety, and so you can only (legally) guess at reading and writing the drive correctly. I *believe* it has to be compiled as a kernel module to fully read and write. There again, this is a legal deal...... MDK and others seem to do it, while RH/Ubuntu and others don't. (I'm not real clear on the details, so some or all of this may be completely wrong, but I believe I'm hitting around the target.)

One thing I've noticed about reviews if Linux. If they are by the "tech press", often it's a Windows guy who dabbles in Linux, and never keeps a distro on his machine for more than a few weeks, and only as an oddity. Unless something ends up looking and working *exactly* like Windows, they'll always say "Nah."

Other reviews are by average users- which is great- but often they don't have the skills to accurately review and assess whether an issue is distro, environment or application level. I know I've been using Linux for 3+ years every single day- desktop and servers- and have used all flavors: Mandrake from 7.2 on; Redhat & Fedora from 8.0 up until now; SUSE; Ubuntu and several others- and I still run into things that make me realize there's far more I don't know than I do know. Most times I guess at a problem- and as often as not I'm wrong. (Though I'm getting better.....) ;-)

I don't mean to take away from the validity of "average Joe" reviews at all. No matter if the issue is distro or application or lack of user knowledge- to the user, it's a *problem* period. (Or a great thing when it works.) So those types of reviews are really valuable and interesting. 

Still, when you see a review, and the tag line at the end says "Joey So-and-So has been using Linux for 6 months and really likes it"..... take it with a grain of salt. He may or may not have great experience. His viewpoint is valid and interesting and may give great insight. Yet he may be a complete *bonehead*- or maybe just learning. He may be the next big thing- you never know. 

I mean, at some point, even Linus Torvalds pointed to a computer and said "what is that *thing*?" :-)

Every computing experience is *so* different because of OS, hardware, software and user knowledge. I never had any problems with Windows 98- ever. Over 200 days uptime on my '98 box was normal. ME...... sucked. Same hardware. XP has not given me any problems. 

I've done Linux installs that I loved, and I'd hand the CD's to a friend- and he couldn't even get it working. The first time I tried to install Ubuntu, it didn't like my partition scheme, and wouldn't mount my existing /home partition. Threw the CD back in the drawer for a week. A friend said "try it again..... I think you'll like it." So I did, blew out the existing partitions- no problems. I love it. Did I solve the original problem? No. Could've been an Ubuntu issue, or my own lack of knowledge, or a previously jacked up partition scheme. (I suspect the latter.)

Anyway...... I'm saying things most everybody knows. It's either look busy here at work, or actually *be* busy. For the same hourly pay, I choose to look busy. :-)

Everyone around me is impressed with my dilligence!

---

### Post by emperor on 2004-11-04
[QUOTE=jwb]I just switched from Fedora 2, and one of the primary things I love about Ubuntu is the fact that updating and installing software just plain work- every time. I used yum in Fedora, and had the craziest yum.conf you'd ever see. Sometimes it worked, sometimes it didn't. Using up2date only worked about 50% of the time. Yum worked most of the time, but seemed to get hung up quite a bit.
  [/QUOTE] Apt-get and Synaptic are optional with Fedora. I have been using apt for RPM now since RH9 and on through Fedora Core 2. I just did not like the other package managers including: Yum, Yast, and Urpmi. However, I did do like Arch Linux's pacman, but there is no X interface yet!

---

