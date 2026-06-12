---
title: "An Uninvited Opinon ..."
date: 2008-08-17
forum: Testimonials &amp; Experiences
---

### Post by linuixjosh on 2008-08-17
To give myself some credit, let me say that I'm a 15 (nearly 20 year -- I'm dating myself) vet. of Unix and Linux. A few years ago I even used Fedora (I think 5) to setup and install a server farm as well as web server for a company.  I've developed complex networking apps for Linux and written Unix device drivers.

Recently I installed Ubuntu to see the news for myself.  I found several issues.
1. There is no option at install time to setup a root password.
   A big no-no in Linux (or Unix)
2. There is no firewall
3. The WiFi support was very poor.  It worked but it dropped a
   lot of packets and I found only about 75% - 80% pings worked.
4. I found response time to common apps like OpenOffice much
   slower.

Other issues I have are the uninstall didn't work as advertised. I tried doing the uninstall from WinXP and it failed. I found a note on this site that said I had to blow away the partition w/ Unbuntu and the do Boot w/ XP disk -> Repair -> fixmbr

As an aside, I found problems w/ recent Fedora 9. Although I did not have the same problems (lack of wifi support) on Fedora 8.  Also uninstall of Fedora was same as Ubuntu.

OpenSuse has a bad disk.  Still not sure why the disk has error as I've downloaded twice and get the same checksum.  It boots but during install it gives a disk error. 

Getting rid of OpenSuse was a bit more of a challenge.  I blew away the OpenSuse partion and did fixmbr, but this didn't work.
I had to edit boot.ini, to delete the OpenSuSe boot option.

So far, for my money ... I'd stick with the older versions of Fedora. 

Josh

---

### Post by tamoneya on 2008-08-17
let me address 1 and 2.  

1.  There is no root password set because in ubuntu you are not supposed to use the root account.  Instead you use sudo.  By not setting the root password it is not possible to login as root.
2. IPTables is installed by default but you need to just set the rules.  Take a look at ufw.

---

### Post by bmac on 2008-08-18
IP Tables....Hmmm

Root Password....Hmmmm

> 
So far,** for my money** ... I'd stick with the older versions of Fedora. 

Ubuntu is free - as in no money.... If you don't like it don't use it. Use Fedora - I doubt it will have a major impact on other Ubuntu forum members.... But I could be wrong.... 

Must be tough when you're endeavoring to recruit on the Ubuntu Forum and you don't understand the basics...

---

### Post by kspncr on 2008-08-18
> **bmac said:**
> Ubuntu is free - as in no money.... If you don't like it don't use it. Use Fedora - I doubt it will have a major impact on other Ubuntu forum members.... But I could be wrong....

Don't worry, bmac, I really don't think you're wrong.

---

### Post by wolfen69 on 2008-08-18
1. there is no need to be root when you can just sudo when neccessary.

2.yes there is. it is called iptables. you can install something such as firestarter if you desire a gui front end for it. do some research next time.

3.as with any linux distribution, wifi support could be better, but ive installed ubuntu on more than a few machines with wifi with very little trouble. i find ubuntu to be one of the best at this.

4.maybe your computer is slow? response time for me is very good.

someone with your experience should know that you can't judge an OS on just your own computer. talk to me when you've installed it on at least 25 different computers. your uninformed and "uninvited" opinion is weak at best.

---

### Post by sstusick on 2008-08-18
The OP doesn't sound like a 15-20 year old vet of Linux/Unix to me.

---

### Post by tact on 2008-08-18
Welll...  whether the OP has 15-20 yrs experience with unix-like operating systems, or not, really doesn't matter.

Having 20yrs experience with past systems does not make one qualified to judge a just released system.  What matters more is keeping up with latest developments and thinking and trends.

Classic example - his criticism of the installer not doing what he is used to, giving opportunity to set up a root password.   Shows the OP is unaware of a shift in thinking regarding security of systems (not enabling "root" login) and the convenience of using "sudo".

---

### Post by billgoldberg on 2008-08-18
> **sstusick said:**
> The OP doesn't sound like a 15-20 year old vet of Linux/Unix to me.

That's what I was thinking.

---

### Post by stalkingwolf on 2008-08-18
Maybe I am just one of the lucky ones, but I have never had a
major problem with wifi.  But then in  the beginning I did a
bit of research and chose a USB adapter that just worked.  I have
always had 2 or 3 pcmcia cards that just worked and recently bought another Dlink card that works great.

Also recently I bought an HP nc8000.  After some problems with trying to set up dual boot I said ******.  Installed 8.04 and 
was much amazed when not only did the internal wifi work out of the box, so did my ATI graphics!!!

---

### Post by ukripper on 2008-08-18
> **sstusick said:**
> The OP doesn't sound like a 15-20 year old vet of Linux/Unix to me.

I am a predator from outer space and I am here to annihilate this human kind until all human race has extinct from the face of this planet I will keep posting on forums. 

But sorry guys I would like to sit in Boing 747 first and enjoy the ride to LA and then i will think again if humans really need to die. Perhaps, i may join the GNU/Linux community later if I enjoyed it that much living with human beings.

 huh..how Random...??

Now would you believe that?

---

### Post by armandh on 2008-08-18
I tried some of those early Linux boxed OS and I was lucky to get them working at all. On those that I got a working desktop I could not connect to the internet and had no sound. they did not stick to any of my computers [back to 98se] Knoppix was the first that worked for me but I could not install it. My db admin brother in-law recommended Ubuntu and last summer I tried 7.04

wow it just worked. I then discovered distrowatch and tried many others only to discover why Ubuntu is at the top of that list.

Ubuntu is way easier to install and use [IMHO] and I hope someone does for wireless what medibuntu does for dvds

---

### Post by loell on 2008-08-18
well, sticking with fedora 8 is a good move, but a user with 15 to 20 yrs of nix experience should  know **a lot** to get around with these problems no matter what distro he's in, don't ya'll think? ;)

---

### Post by tact on 2008-08-18
> **loell said:**
> well, sticking with fedora 8 is a good move, but a user with 15 to 20 yrs of nix experience should  know **a lot** to get around with these problems no matter what distro he's in, don't ya'll think? ;)


Well there is the thing...  An "old hand" who perhaps is not up on whats new in the mix might see a problem involving a network adapter, drop to a terminal and use CLI to set up the interface - just like the old days.

Of course we know that manually setting up a network adapter removes all control from networkmanager.  But an "old hand" used to the old ways, and not up to date, would not...  and likely would (if he is a bit anal) come into a forum with his fists swinging saying how much crap these "so-called new improvements are, cos networkmanager doesnt work!".

He would't know that by using his 20yo commandline commando skills to get a network adapter up - he has himself disabled networkmanager.

(all that just one hypothetical example...  but its like that in many ways with "old hands")

---

### Post by CarlosNYB on 2008-08-19
Good point on the 'old hand' approach.  Now, I'm not entirely new to Linux, but I didn't spend years with it either.  I had to use Unix at work as a programmer, but only rarely.  I explored Red Hat and Mandrake around 2001, because I liked the movement.  But I just installed and poked around a little and then everything else distracted me.

When I came to Ubuntu about a month ago, I installed Ubuntu Studio.  When I had trouble with my USB WiFi dongle, I started trying to install ndiswrapper from the command line, etc., it just wasn't working for me.  Later on I decided to just start with a basic Hardy install, and then added the gtk gui for ndiswrapper through synaptic (I didn't know anything about synaptic when I first came to Ubuntu, and I didn't know the gtk gui for ndiswrapper would fix my problem), and then installed the Ubuntu Studio ALSA and Music meta-packages from Synaptic and everything worked fine.

If I had just figured it was Linux so I'd have to putter around with the CLI, I'm sure I would have had a much more frustrating experience.

---

### Post by yabbadabbadont on 2008-08-19
Actually, if you enable the expert option when installing, you will be asked if you want to enable the root account.

---

### Post by tact on 2008-08-20
> **CarlosNYB said:**
> Good point on the 'old hand' approach.  Now, I'm not entirely new to Linux, but I didn't spend years with it either.  I had to use Unix at work as a programmer, but only rarely.  I explored Red Hat and Mandrake around 2001, because I liked the movement.  But I just installed and poked around a little and then everything else distracted me.

When I came to Ubuntu about a month ago, I installed Ubuntu Studio.  When I had trouble with my USB WiFi dongle, I started trying to install ndiswrapper from the command line, etc., it just wasn't working for me.  Later on I decided to just start with a basic Hardy install, and then added the gtk gui for ndiswrapper through synaptic (I didn't know anything about synaptic when I first came to Ubuntu, and I didn't know the gtk gui for ndiswrapper would fix my problem), and then installed the Ubuntu Studio ALSA and Music meta-packages from Synaptic and everything worked fine.

If I had just figured it was Linux so I'd have to putter around with the CLI, I'm sure I would have had a much more frustrating experience.

Spot on...  I cannot count the number of times I made things terribly more complicated than they needed to be with ubuntu...  either by doing things the (old) way I "knew" should work, or following guides written for days gone by....  then only to find out how easy it would have been had just used synaptic or apt-get or some other new tool to just sort it all out for me.  *chuckle*

Now I know to triage any guides I find when trying to solve an issue.... and look hard..  not just follow the advice I see in the first 3 or 4 guides I read.   

I used to preface any google search for help with "ubuntu"....  but with Hardy (so much thats new in it) even that may get one some "old hat" information...  so I preface all google searches with "ubuntu" and "hardy" nowadays.

Isn't it good we have a distro thats so popular that there is so much info floating about that you really MUST filter to get to the good stuff.     hehehe

Somewhere someone will complain and say that "ubuntu sucks" because there is so much "wrong info" out there...  but really its a matter of making sure you have the right guide first.  And that has to be the user's responsibility.   

Can you  imaging someone complaining their car is ruined because they got a workshop manual for some DIY repairs... and the manual was for a carburetted engine, whilst their model is fuel injected.  Hardy really is that much different to even its predecessor...  and the changes came less than 6mths ago!  :)

---

### Post by CarlosNYB on 2008-08-20
It always was weird figuring things out.  Sure there's the FM (as in RTFM :popcorn:), but there's usually the question of where to look and what terminology to use.  I've been enjoying fluxbox lately.  Took a while to get my background working but now it's fine, had to use the -l option on the background setup progam, though, and that wasn't obvious, but my on-board graphics card doesn't play well with some of the effects commonly used in graphics programs, isn't fully supported in linux... so I needed a little switch on the command, I had to do things just a little differently -- but now it's working fine.  Incidentally, one thing I like about Fluxbox and Xfce compared to Gnome is that it was easier for me to find out where the text files that configured menus were, and just how to modify them (I dislike ala carte and I put linux on this machine because I wanted speed improvements anyhow -- and you can't edit a menu any faster than with a text editor)

---

### Post by CarlosNYB on 2008-08-20
I should change that to STFM for SKIM!  :guitar:

---

### Post by linuixjosh on 2008-08-21
Most of you were wet behind the ears, when I was writing unix port from 3B2 to the intel i386 architecture. 

And for you who responded to my earlier thread and have no knowledge of unix history, I'll tell you that 3B2 and 3B2000 were the original Bell Labs platforms for Unix invented by Kernighan, Ritchie, Pike et.al. Later given to universities and
eventually turned into the public domain linux. 

Having said that I'm not looking at these as a cog-head. I'm looking at these as suitable desktop replacements.  Especially since this is the claim to fame for ubuntu. What's more I'm not trying to recruit anyone to anything. I'm reporting my results.
Let people pick their own poison. 

I will proceed to my evaluation of SUSE.  SUSE first disk was corrupt as I used HTTP download. The 2nd attempt was successful
(torrent). But the install was a failure. YAST was worst than ubuntu.  SUSE (and Fedora) setup a root account and also had a firewall. SUSE like fedora 9 had problems setting up the USB wifi device. SUSE also failed to setup the built in wifi in my laptop.  But uninstall of SUSE was far worst than either ubuntu or Fedora.

Following an uninstall about 10 G or so have been left corrupt. Neither XP disk management or even Partition Magic are able to recover these 10Gs.

Although the ubuntu uninstall wasn't as easy as advertised at least it was possible w/o disk corruption. Same for Fedora 9.

Overall Fedora 8 and earlier seem to have had the least problems in install, security, wi-fi support, and performance. 

So flame on .... I'm going to stand by the evaluations I've done on all three major linux flavs floating around.

p.s.
You folks who seem to know linux so well w/o doing a google tell me what is an IOCTL ? :-({|=

---

### Post by loell on 2008-08-21
> **linuixjosh said:**
> 
p.s.
You folks who seem to know linux so well w/o doing a google tell me what is an IOCTL ? :-({|=

sure, i just did a yahoo search and this came up 

[http://rds.yahoo.com/_ylt=A0oGkiW6CK5IqdAAVF9XNyoA;_ylu=X3oDMTEzZjQ1NjRhBHNlYwNzcgRwb3MDMQRjb2xvA3NrMQR2dGlkA0Y5NDVfMTIy/SIG=11m9k5nd6/EXP=1219451450/**http%3a//en.wikipedia.org/wiki/Ioctl]("http://rds.yahoo.com/_ylt=A0oGkiW6CK5IqdAAVF9XNyoA;_ylu=X3oDMTEzZjQ1NjRhBHNlYwNzcgRwb3MDMQRjb2xvA3NrMQR2dGlkA0Y5NDVfMTIy/SIG=11m9k5nd6/EXP=1219451450/**http%3a//en.wikipedia.org/wiki/Ioctl")



see? ;)

people here seem to know linux, but never have i heard/read that they claim to have a *nix expertise. atleast not until today.

for me atleast, i don't speak for everyone, i always welcome ubuntu critics, uninvited opinion? sure even.

but an **Elitist Opinion**? nah.. uh..[-X

---

### Post by CarlosNYB on 2008-08-21
I was never interested in a pissing contest.

In my experience Ubuntu has been FAR more user friendly and 'just works' with a large variety of equipment out of the box compared to other operating systems/distros I've used in the past, whether it's been Windows or *nix-like.

---

### Post by linuixjosh on 2008-08-21
My only reason for establishing my creds was to stop the usual retorts that any criticism must be wining from someone who doesn't understand linux.  Because if  I did, I wouldn't have any complaints.  

Even with this, read the earlier responses and you see a variant of the same thing.  Specifically, I must not be up to speed on the newest stuff.  

All I'm doing is reporting to people who are new my experience with all three major distros. 

ciao

---

### Post by wolfen69 on 2008-08-21
> **linuixjosh said:**
> Most of you were wet behind the ears, when I was writing unix port from 3B2 to the intel i386 architecture. 



:rolleyes: spare me.

how many computers have you tested suse, fedora, and ubuntu on? 1? your 1 computer must be the standard by which all OS's are judged. forgive me, oh great one. i've had many successful installs of ubuntu on many different machines. i guess that doesnt matter to you, because of *your* computer.

---

### Post by wolfen69 on 2008-08-21
> **linuixjosh said:**
> My only reason for establishing my creds was to stop the usual retorts that any criticism must be wining from someone who doesn't understand linux.  Because if  I did, I wouldn't have any complaints.  

Even with this, read the earlier responses and you see a variant of the same thing.  Specifically, I must not be up to speed on the newest stuff.  

All I'm doing is reporting to people who are new my experience with all three major distros. 

ciao

i may not have the unix "creds" that you have, but i have what i like to call "street cred" when it comes to linux. i have a small pc repair business that focuses on windows. it affords me the luxury of installing or trying out live cd's on a wide variety of systems. from my experience, it seems that 5-10% of all computers will have problems running linux. some wont run at all. that's life. either you dont know what you are doing, or your computer falls into that 10% range. which is it?

if you really want to give modern distros a shot, try it on several different machines. your opinion really doesnt mean much to the "new kids on the block" if you are going to give a "state of linux" speech without really attempting to dig deep through trial and error.

---

### Post by CarlosNYB on 2008-08-22
I'd just re-assert my own experience that old-school Unix is different from these new *nixes, and I'd gather that newer Unixes are quite different from the old ones, also.

Repositories are your friend, many computers work great with Ubuntu out of the box, many require only minor adjustments.  Sorry sometimes things don't work well with computers.  Can always improve things, tweak.

---

### Post by Oram on 2008-08-22
> **linuixjosh said:**
> 
3. The WiFi support was very poor.  It worked but it dropped a
   lot of packets and I found only about 75% - 80% pings worked.

Josh

Maybe a year back or so I used fedora and I strongly disliked it.  Took me days to get WiFi to finally work.  I ended up not using it after a few months of having it.  I then decided to use Ubuntu and I have not had any WiFi problems with it at all. I must say wifi on Ubuntu was a lot easier than spending hours of my weekend setting up fedora(Maybe it was just a very unsupported internet card.)

---

### Post by tact on 2008-08-22
> **linuixjosh said:**
> My only reason for establishing my creds was to stop the usual retorts that any criticism must be wining from someone who doesn't understand linux.  Because if  I did, I wouldn't have any complaints.  

Even with this, read the earlier responses and you see a variant of the same thing.  Specifically, I must not be up to speed on the newest stuff.  

All I'm doing is reporting to people who are new my experience with all three major distros. 

ciao


Oh puhleeeease...  no one has flamed you and no one has attacked you personally and no one has acted like a fan boi and said "if you understood linux you'd have no complaints".

Geez.   Get a bit of reality around you and realise that, first up, it really, truly,  does not matter a shred if you have 50 yrs *nix experience or even could claim to have been Linus' ghost-writer for the first linux kernels....  if you are not up with the latest trends (despite all your experience on legacy systems) then you are not at all qualified to say things like:
"1. There is no option at install time to setup a root password.
   A big no-no in Linux (or Unix)"

Thats just patently wrong.  And it would never be said by someone who is in th eleast up to date with the discussion on root accounts and sudo and such.  

Can you swallow your great pride in your legacy experience and show great intelligence and strength of character and admit same?

For completeness on the topic (root accounts in linux) - I will grant that the jury is still out on the matter and that there is a strong group who believe strongly in setting up a root account.  But there is also a strong group who stand by the notion it is much more secure, "better", to NOT set up a root account and just use sudo when needed.

If you were at least acquainted with the security issues and the root/sudo debate then you would never call it a "big no-no" and mislead the newcomers you pretend to write to.

you also wrote - "2. There is no firewall" as if this is a deficiency.

The need for any firewall is another topic that is subject to much debate and misunderstanding amongst the best and most up-to-date in the field.  Yet you dare to pronounce it an essential feature thats missing -  based on your legacy experience.  Can you see how foolish this looks to all except the newcomers you state you write to enlighten?

You further wrote: "3. The WiFi support was very poor.  It worked but it dropped a
   lot of packets and I found only about 75% - 80% pings worked."

Grand observation and does not need a 20, 30, or 50 yr pedigree in legacy systems to give it any legs.   What you neglect is that your observation is based on your hardware.  How small is your sample that you base your observation comments upon?  One PC?  One laptop?

Do you dare to deny my following statement (based on my experience with my hardware) - "Ubuntu has excellent wifi support as it works fantastic straight out of the box".

Do you dare to wake up and realise now that your singular (negative) wifi/ubuntu experience, as well as my singular (positive) wifi/ubuntu experience, are nothing more than specious comments.

More intelligent and helpful to newcomers would be a comment like "I found that my xxx brand, yyy model, wifi adapter is not supported in ubuntu".  (with no hint of an unreasonable attitude that ubuntu (or any other *nix)  fails because it does not support ALL brands/models).

You further wrote:  "4. I found response time to common apps like OpenOffice much
   slower."

"Slower"...  you know what the word "subjective" means?  Slower than what?  An E10k running 32 processors, a 1 TB RAM, and some line editor program you wrote as part of your doctorate in computer science 20 yrs ago?

C'mon man...  you state you want to be helpful to newcomers?   You say so -  Yet you make incorrect statements and valueless subjective comment that benefits no one...  try to shore up your opinion with some specious reference to long legacy experience and in subsequent posts act like you are being attacked or flamed.

Well now you have been... (if you can call this a flame - sheesh I speak more bluntly to my kids!)

Cheers...

---

### Post by cardinals_fan on 2008-08-22
> **linuixjosh said:**
> 
Recently I installed Ubuntu to see the news for myself.  I found several issues.
1. There is no option at install time to setup a root password.
   A big no-no in Linux (or Unix)
2. There is no firewall
3. The WiFi support was very poor.  It worked but it dropped a
   lot of packets and I found only about 75% - 80% pings worked.
4. I found response time to common apps like OpenOffice much
   slower.

1. I think that there is an option on the alternate CD.  I also dislike this practice (I don't get the idea of using the user's password for system administration).

2. IPtables is installed but not entirely configured.  A "ufw --enabled (or something similar)" should fix that.

3. I've found Ubuntu to have very good WiFi support.

4. I have a great deal of difficulty imagining anyone concerned with system responsiveness using *shudder* OpenOffice.  But yes, the auto-configuration in Ubuntu does have a price.  That price is performance.

I'm not an Ubuntu user.  I find that Slackware suits my needs much better.  However, you could just go back to Fedora and relax.  Everybody has different preferences.

---

### Post by yabbadabbadont on 2008-08-22
If you enable the Expert option when installing, you are asked if you would like to enable the root account.

---

### Post by Ethyrdude on 2008-08-31
I did set up a root and password for root on my Ubuntu but there's not much point in doing so, sudo is less likely to get me into trouble so I gave root the boot.  If not having a user root is so bothersome, then make a root user, I have root on my Debian computer but I was kind of glad I didn't need root for Ubuntu.

After having used Debian for the past couple of years, I found Ubuntu refreshingly simple to use, in spite of all my whining.  I'm not thrilled with compiz but I'm going to give that the boot tomorrow, after doing a bit of testng this is definitely the source of all my trouble with Ubuntu.

---

### Post by swoll1980 on 2008-08-31
> **linuixjosh said:**
> To give myself some credit, let me say that I'm a 15 (nearly 20 year -- I'm dating myself) vet. of Unix and Linux. A few years ago I even used Fedora (I think 5) to setup and install a server farm as well as web server for a company.  I've developed complex networking apps for Linux and written Unix device drivers.


You are fabricating this story. From your post I obviously know more about Linux than you and I'm just a casual desktop user. There is a firewall,(there's no graphical front end for it, but since your such an uber Linux hero you should know that) and your never logged in as root so why (unless your an experienced user that knows how to "passwd root" anyhow) would this matter?

---

