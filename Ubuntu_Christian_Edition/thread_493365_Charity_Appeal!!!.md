---
title: "Charity Appeal!!!"
date: 2007-07-05
forum: Ubuntu Christian Edition
---

### Post by raid517 on 2007-07-05
Hi, sorry for the double post. I posted this in the science and education section first, but I wondered if you guys might be more inclined to help?

You see I work for a charity in the North East of England in the UK. We have a problem in that our IT resources have grown rapidly, but so far we have not been able to put the management of these resources, or the staff training in place in order to utilise these resources effectively. 

One example of this is that we have a large number of machines with files belonging to various members of staff scattered over several desktops within the organisation. (When I say 'large' I mean in one specific location we probably have about 30 machines and a similar number spread over about 5 separate locations. I am however responsible (for the time being) only for the 30 machines at my current location).

I am somewhat new to this post and I work on a purely voluntary basis, but my observations of the IT Infrastructure (if one can be said to exist) of this organisation is that it is utterly disheveled and completely disorganised.

Currently the way staff access files which are directly related to the running of the organisation, is to simply dump them on any random desktop that they might be working on and to then attempt to remember (at some point in the future) where exactly they might have put them.

The charity in question also works with disadvantaged young people, providing access to ICT technologies and training - and a similar scenario is evident in this regard, with students having files, images, mp3 music files and all kinds of garbage scattered across their desktops. There is no sever side administration (and no central server) and literally no organisation evident whatsoever.

So... since I am new here and since I have volunteered, I thought I should probably do something to try to sort some of this mess out.

I do have some Linux experience. So I thought one way of sorting this out was possibly to use a Linux distro on one of the slightly older machines which ran a SAMBA and/or FTP server and organising staff files and student files into their own specific/unique directories. This way at least things might be a little more organised.

So (as well as being open to suggestions of possible other ways to sort this mess out) I am now currently in the market for a simple, easily manageable Linux distro that will give me fully functioning FTP/SAMBA/WebMin servers out of the box.

Oddly, probably one of the better distros that I have used (and still use regularly) is Gentoox - which runs on my old Xbox 1 as my home based file server. It pretty much gave me all of these facilities from the outset and required both very little configuration and very little maintenance. However (despite whatever some enthusiasts might say) my experience is that Gentoo in general might be a little too complex and involved for this kind of environment - and in any case I certainly can't use an old XBox as a central file server for a small to medium scale charity. So as I am somewhat familiar with it, I have opted to go with Ubuntu.

One other dilemma that we face is that we desperately need a way to share information (case files, accounts, progress reports and so on) not just between departments, but between different offices in different geographical locations too. Again I think FTP might be a good answer, but here's the rub, although I am trying to do the best job I can, I am by no means a professional. All of my experience to date (both Linux and Windows) has been home based. So hopefully you will forgive if I ask a potentially dumb question, which is specifically, how do I make a FTP server visible over the Internet?

Again when setting up a FTP server in the past I have always been satisfied to just have my files available locally on my own network. However despite several attempts I have never been able to access any FTP server I have configured over the Internet.

So my next question is, how exactly do I do that?

I don't think I can convince them to ditch Windows entirely, since part of the aim of the project is to expose these young people to as similar an environment to a common workplace environment as possible - and from their perspective (and probably with some cause) this means Windows. But as a Windows server licence costs probably way more than these folks can afford (or at least the money would be better spent on helping the kids) then hopefully I can at least help them organise things a bit better and possibly comminicate more effectively - and maybe use Linux to save them some money on a server licence.

Also which version of Ubuntu would you guys recomend? I know there is a server version and a Desktop version - but although I can to an extent work OK with a headless Linux install, the main IT guy there (who although he does his best isn't really a qualified IT admin either) would be likely to be very lost/confused by this.

I know it's even more of a long shot, but I don't suppose there are any good Linux admins on this forum from the North East of England who would be willing to help out in some direct way do you? As I said, I am by no means a professional, so any input at all (even just inso far as giving us a basic overview and breakdown of our needs) would be very helpful indeed.

Thanks in advance to anyone who can offer any help whatsoever. It's a shame that things have become so disorganised for this charity and I guess it's not ideal that I am all they have right now in terms of trying to put together some kind of consolidated IT strategy and/or infrastructure. But even if I can help organise things a little, it is likely to be a thousand times better than anything they have right now.

GJ

---

### Post by lisati on 2007-07-05
All the best....

---

### Post by tak1150 on 2007-07-05
What version of Ubuntu have you installed?
If you haven't, I definitely recommend installing Ubuntu 7.04 Desktop Edition, and not the server edition. If you would like more security out-of-the-box, you can try Ubuntu 7.04 Christian Edition, which comes with a firewall and antivirus (it's also called Ubuntu CE 3.2). If you go the latter route, there is one more extra thing you need to do to allow Samba, but it's not difficult.

Let us know what OS you're going to go with and we'll help you :p

---

### Post by raid517 on 2007-07-05
As unfortunate as it may be, I don't think we can go with Ubuntu CE. The reason is that we work with people (including refugees) not just from this country - but from all over the world also - and these often come from very diverse ethnic and religious backgrounds - so we can't be seen to be promoting one perspective (or one faith) over another - and indeed, there may even be government regulations in this country which might prevent us from doing so.

So I think it will have to be a straight out Ubuntu install, if we choose anything.

So far however we are still evaluating if Linux really is an option for us - and as such we have not installed anything yet.

---

### Post by tak1150 on 2007-07-05
> As unfortunate as it may be, I don't think we can go with Ubuntu CE. The reason is that we work with people (including refugees) not just from this country - but from all over the world also - and these often come from very diverse ethnic and religious backgrounds - so we can't be seen to be promoting one perspective (or one faith) over another - and indeed, there may even be government regulations in this country which might prevent us from doing so.

I hear you. But you know that's restriction on religious freedom. It's too bad that you can't express anything Christian these days (have you noticed it's ok to have religious expression as long as it's not Christianity?).

Anyhow, I run Ubuntu 6.10 at work to serve as a web server / SFTP (SSH FTP) server / MySql server (for forum, etc) for the people at work. It's working great. If these are the things that you need, I can give you some directions. I know you wrote a long post, but I'm still not 100% sure exactly what you need. However, I definitely think that Linux is a good option for your situation.

Blessings,
Tak

---

### Post by mysticrider92 on 2007-07-06
> **tak1150 said:**
> I hear you. But you know that's restriction on religious freedom. It's too bad that you can't express anything Christian these days (have you noticed it's ok to have religious expression as long as it's not Christianity?).
That is where we are quickly headed, sadly. 

I also have a small computer running at home with some of that same stuff (HTTP/FTP/LAMP). [Here]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html") is a good blog that could get you started with some of the basic stuff you want. I would recommend starting like that page says (use either 7.04 or 6.06 instead of 6.10 for longer support) with the command line system, then you could add ubuntu-desktop to get the GUI you are looking for. That should do what you want, and possibly be a learning experience.

---

### Post by lisati on 2007-07-06
> **tak1150 said:**
> I hear you. But you know that's restriction on religious freedom. It's too bad that you can't express anything Christian these days (have you noticed it's ok to have religious expression as long as it's not Christianity?).

I was going to comment on how Christianity is the only religion whose founder's name is commonly used as a cuss word, but wasn't sure how it would go down....

---

### Post by raid517 on 2007-07-06
I understand what you guys mean. However there is cause for some maturity in these matters. We show no favoritism, or bias towards ANY religion. Remember, we work with young people from all around the world, from all cultures, regardless of their social status or their religious convictions. It simply wouldn't be decent to attempt to promote one perspective over another. That is not what we do and it is not what we are about.

Harbouring some misguided form of persecution complex, particularly when it is a policy all of those who work within the project are not only bound by - but also agree with fully, is unlikely to be helpful to our cause.

---

### Post by tak1150 on 2007-07-06
When something is true, upholding it as true is not the same as favoritism.
I really believe that what every young person needs is Jesus, a Savior that loves them enough that He was willing to die for them :-D

Anyhow,
> use either 7.04 or 6.06 instead of 6.10 for longer support
I agree. I'm only using 6.10 b/c that was the newest version when I set up the server. I'm intending to replace it with Gutsy (7.10) when it comes out.

On whether to use the server edition of the desktop edition though, I definitely think that raid517 should use the desktop version because it's easier to install server application into the desktop v. than installing the GUI desktop into the non-GUI server version.

The how-to page that mysticrider92 provided looks very impressive and perfect for newbies (I wish I had known of that page long time ago).

If you want to see the screenshot tour of Ubuntu 7.04, click [here]("http://debianadmin.com/copper/displayimage.php?pos=-874")
Installation of the OS itself is very self-explanatory, but [this site]("http://www.wikihow.com/Switch-to-Ubuntu-Feisty-Fawn") might help.

---

### Post by raid517 on 2007-07-06
Well how would you like it if I chose instead to use Ubuntu Muslim Edition, or Ubuntu Hindu Edition (if indeed these existed) and I used this to covertly promote a single particular perspective and you were one of the young people in question. How would you like it, given the nature of your own personal 'strong conviction', if I then told you that I strongly believed what most young people needed was Vishnu, or Mohamed - what if I kept trying to sneak small hidden messages into everything I did - is it possible that at some point you might become offended?

There are certain situations where your particular message may in fact as surprising to you as it may seem be genuinely unwelcome.

Nonetheless please do not derail this discussion and allow it to descend into a childish debate over which brand of religion is 'better' or more accurate than the other. This will do nothing to help my cause - nor will it do very much to help the young people in question - and is also pointless since as well as not being allowed to show this kind of bias I have no personal desire whatsoever to use my work as a means of attempting to indoctrinate anyone to my own particular way of thinking in any case.

It is not part of the job I do, I am not allowed to do it and I have no interest in doing it anyway.

Regardless of this I think I may have found the answer I was looking for. Unfortunately it's not Ubuntu (although I do use this at home) and it's a distro called SMS server - which seems much better suited to the task at hand. So I expect if I can get to grips with it, that this is what we may use.

---

### Post by jonathonblake on 2007-07-13
> **raid517 said:**
> Well how would you like it if I chose instead to use Ubuntu Muslim Edition,
*Ubuntu Muslim Edition* is a metapackage.  I *think* the splashscreen contains the first pillar of Islam.   It also announces when it is time to pray.  It also creates a menu off the start menu, called "religion".   If Minbar is uninstalled, and the wallpaper replaced, people won't recognize it as Ubuntu Muslim Edition.

Ubuntu Satanic Edition currently is a collection of splashscreens, wallpaper, and themes.  IOW, change the wallpaper, and it isn't Ubuntu Satanic Edition anymore.

Ubuntu Christian Edition is a full blown distro.   Changing the wallpaper, or splashscreen wont' change the Bible verse in the lower right hand side. That is the only telltale that can't, AFAIK, be removed.

I'm not sure what the status of Ubuntu Jewish Edition is.  I *think* it does not exist, but I've seen a couple of references that imply otherwise. The only list of what it contains was meant as an exercise of what different religious distributions of Ubuntu would contain.

Ubuntu Daoist Edition is a reference to installing the theme from TheTao dot info on Ubuntu. :)

Ubuntu Gnostic Edition, *Ubuntu Hindu Edition*, Ubuntu Thelmic Edition, and Ubuntu Kabbalistic Edition do not currently exist, but are used as reasons to block the construction of Ubuntu Christian Edition.  

> It is not part of the job I do, I am not allowed to do it and I have no interest in doing it anyway.

a) Your message was posted in **Ubuntu Christian Edition** .  The most logical recommendation would be Ubuntu Christian Edition, since it has built in web filtering.

b) Ubuntu Muslim Edition also contains preconfigured web filtering software.  

c) AFAIK, none of the other distributions of Ubuntu are preconfigured with web filtering software.    (I'm assuming that under UK law you are under similar requirements as US law --- publicly accessible terminals have to contain content filters.)

xan

jonathon

---

