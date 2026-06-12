---
title: "Pidgin 2.3.1 Released!"
date: 2007-12-08
forum: The Cafe
---

### Post by Kosimo on 2007-12-08
Just two weeks later, pidgin folks have a new present for us:

Pidgin 2.3.1

Here the changelog:

>     * libpurple
          o Fixed a number of MSN bugs introduced in 2.3.0, resolving problems connecting to MSN and random local display name changes
          o Going idle on MySpaceIM will no longer clear your status and message.
          o Idle MySpaceIM buddies should now appear online at login.
          o Fixed crashes in XMPP when discovering a client's capabilities
          o Don't set the current tune title if it's NULL (XMPP/Google Talk)
          o Don't allow buddies to be manually added to Bonjour
          o Don't advertise IPv6 on Bonjour because we don't support it
          o Compile fixes for FreeBSD and Solaris
          o Update QQ client version so some accounts can connect again
          o Do not allow ISON requests to stack in IRC, preventing flooding IRC servers when temporary network outages are restored
          o Plug several leaks in the perl plugin loader
          o Prevent autoaccept plugin overwriting existing files 


As always:
Download the source code:

```

./configure
make
sudo make install
```If you don't want to compile it, just wait some days to get an easy .deb from getdeb.

Get it from here:

[http://pidgin.im/download/source/](http://pidgin.im/download/source/)

Finally:  


> Fixed a number of MSN bugs introduced in 2.3.0, resolving problems connecting to MSN and random local display name changes



EDIT:

Here the fantastic deb from GETDEB.
[http://www.getdeb.net/app.php?name=Pidgin]("http://www.getdeb.net/app.php?name=Pidgin")

---

### Post by altonbr on 2007-12-08
They LOVE pushing my MSN-related bugs back. One of mine was supposed to be fixed in 2.1.0.. hmm, 2.3.1?

I really wish they'd include their changesets in Trac, but they use Mono instead of SVN and there is a stable enough plugin for it yet :S

---

### Post by Kosimo on 2007-12-08
> **altonbr said:**
> They LOVE pushing my MSN-related bugs back. One of mine was supposed to be fixed in 2.1.0.. hmm, 2.3.1?

I really wish they'd include their changesets in Trac, but they use Mono instead of SVN and there is a stable enough plugin for it yet :S


Witch one is it?

Is the ticket still open in the roadmap?

---

### Post by Kynan on 2007-12-08
yes that friendly name bug really annoyed me. thank god thats fixed. tho in a way it was a blessing, because of it i went in search of other programs to do my IM with for msn. 
And i found the beautiful emesene still in its pre release stages and already better than pidgin... display pics work properly, i can see the song my friends are listening too, i can see msn plus features, songs dont transfer painfully slow, my hotmail inbox checking button doesnt stuff up after using it once, i can set what im lisening to on exaile and get my display pic to change to my album art, all in all its lovely and can't wait untill its developed further. Sadly i think this is the end of my use of pidgin. 

Tho i might use it from time to time just to see how things are progressing :)

---

### Post by Kosimo on 2007-12-08
> **Kynan said:**
> yes that friendly name bug really annoyed me. thank god thats fixed. tho in a way it was a blessing, because of it i went in search of other programs to do my IM with for msn. 
And i found the beautiful emesene still in its pre release stages and already better than pidgin... display pics work properly, i can see the song my friends are listening too, i can see msn plus features, songs dont transfer painfully slow, my hotmail inbox checking button doesnt stuff up after using it once, i can set what im lisening to on exaile and get my display pic to change to my album art, all in all its lovely and can't wait untill its developed further. Sadly i think this is the end of my use of pidgin. 

Tho i might use it from time to time just to see how things are progressing :)

I just want to say WOW  :)

I downloaded the latest svn deb from emesene website.. And its really nice.
Clean, with almost (all) features that windows live offers me...
I didn't know about this emesene one, and it looks great. Gonna use it for a while to test it.

Thanks ;)

---

### Post by Turin Turambar on 2007-12-08
Why those Pidgin guys do not release deb file, when it's a well known stuff that Pidgin is heavily used in Ubuntu? !

---

### Post by zugu on 2007-12-09
> **Turin Turambar said:**
> Why those Pidgin guys do not release deb file, when it's a well known stuff that Pidgin is heavily used in Ubuntu? !

If you'll ask them, one probable answer is: "we're not package maintainers for Ubuntu".

---

### Post by Kosimo on 2007-12-09
> **zugu said:**
> If you'll ask them, one probable answer is: "we're not package maintainers for Ubuntu".

Typical answer...


I can't imagine myself creating software hat is not usable for normal people without compiling knowledge.  If I made a software I would do all my efforts to make all people use it... Anyway....

Let's learn how to compile well ;)

---

### Post by LookTJ on 2007-12-09
Isn't that what getdeb is here for?

---

### Post by Kosimo on 2007-12-09
> **Taylor said:**
> Isn't that what getdeb is here for?

Yes and not.
Getdeb is making an excellent job for the entire community. (Specially for userrs)

But, I'm sure that pidgin developers can make a better .deb and in my opinion this is what they should do. Considering the amount of debian users.

Anyway, I'm sure that in some time, all this will change..
There is no way that a program have to be compiled in order to run it, (with lots of problems with dependencies, etc etc....) (for the average user I mean)

I guess that some day we'll have some kind of auto builder or something like this in ubuntu that you just give the source and ubuntu will do the rest...  

Or, finally programmers will create (.run's) or (.deb's) at once and for all.

---

### Post by ImpressMe on 2007-12-09
But they SHOULD be package maintainers. They should compile DEBS and RPM's, and an autopackage that would cover the major distros, ENSURING that their product WORKS perfectly on these distros. Don't they want satisfied users? Do we have to go to third party sites to get an installer - imagine the kind of security hole that opens.

And hey, before suggesting compiling it... wait... and don't recommend it. Don't recommend it to anyone but programmers.

Not providing debs for the most widespread distro is just arrogant.

---

### Post by kadath on 2007-12-09
> **ImpressMe said:**
> Not providing debs for the most widespread distro is just arrogant

It's also arrogant to assume that just because you use the most widespread distro that every F/OSS project should offer you a deb.

Would it be nice if the Pidgin devs offered up-to-date DEBs/RPMs directly on the site? Sure it would be.

But, it's really the job of the package maintainers of your distro of choice to do that, in the end.

Not trying to start a flamewar; just saying...

---

### Post by altonbr on 2007-12-09
> **Turin Turambar said:**
> Why those Pidgin guys do not release deb file, when it's a well known stuff that Pidgin is heavily used in Ubuntu? !

This always comes up. I've submitted a bug for it too and they close it pointing me to this article: [http://developer.pidgin.im/wiki/WhyPackagesExist](http://developer.pidgin.im/wiki/WhyPackagesExist)

---

### Post by altonbr on 2007-12-09
> **kadath said:**
> It's also arrogant to assume that just because you use the most widespread distro that every F/OSS project should offer you a deb.

Would it be nice if the Pidgin devs offered up-to-date DEBs/RPMs directly on the site? Sure it would be.

But, it's really the job of the package maintainers of your distro of choice to do that, in the end.

Not trying to start a flamewar; just saying...

Well the way that Linux distro's work compared to Windows is that the distribution chooses what version of a certain program to include and it only gets updated when they feel like it.

With Windows, they give you a base operating system and you can install whatever program you'd like with two-clicks.

One is more stable and secure while the other one gives the more amateur user more freedom. What paradigm is better? That's what the whole Linux vs. Windows debate is about.

---

### Post by ImpressMe on 2007-12-09
It is not arrogant to expect a little customer awareness. Sure, everyone in the Linux "community" wants everything to be the way it always was, but lets see if the "costumers" reward the strategy. Linux failure to gain mass acceptance is not just because of "an evil monopoly" ... the product itself could be flawed.

---

### Post by Chang An on 2007-12-09
I just use this repository 
[http://www.linuxmint.com/forum/viewtopic.php?f=47&t=7177](http://www.linuxmint.com/forum/viewtopic.php?f=47&t=7177)
It upgraded me to 2.3.1 this morning real smoothly.  It seems they maintain this repo very well.

They finally fixed the qq protocol too!!!

---

### Post by ImpressMe on 2007-12-10
> **Chang An said:**
> I just use this repository 
[http://www.linuxmint.com/forum/viewtopic.php?f=47&t=7177](http://www.linuxmint.com/forum/viewtopic.php?f=47&t=7177)
It upgraded me to 2.3.1 this morning real smoothly.  It seems they maintain this repo very well.

They finally fixed the qq protocol too!!!

Cool, thanks. I use the repository from Bruce89, that also provided me with GIMP 2.4.x

---

### Post by Kynan on 2007-12-10
Hahahaha that was funny when i found out it was my own post ;)

---

### Post by Kosimo on 2007-12-10
> **Chang An said:**
> I just use this repository 
[http://www.linuxmint.com/forum/viewtopic.php?f=47&t=7177](http://www.linuxmint.com/forum/viewtopic.php?f=47&t=7177)
It upgraded me to 2.3.1 this morning real smoothly.  It seems they maintain this repo very well.

They finally fixed the qq protocol too!!!

Can anyone confirm that this repository works perfectly on Gutsy?

Thank you

---

### Post by Polygon on 2007-12-10
> **Turin Turambar said:**
> Why those Pidgin guys do not release deb file, when it's a well known stuff that Pidgin is heavily used in Ubuntu? !

none of the developers use ubuntu so therefore they cant create debian/ubuntu debs.

maybe if someone has experience with creating REAL debs, they can offer to become the ubuntu package maintainer for them

---

### Post by Chang An on 2007-12-10
> **Kosimo said:**
> Can anyone confirm that this repository works perfectly on Gutsy?

Thank you

Yes, It worked perfectly on two of my computers both running gutsy.  Hope that helps.

---

### Post by Kosimo on 2007-12-10
> **Chang An said:**
> Yes, It worked perfectly on two of my computers both running gutsy.  Hope that helps.

Thank you :)  

Just the answer I was waiting for.

Gonna try it now

---

### Post by Kosimo on 2007-12-10
Confirmed as well:

Works gorgeous ;)

Thank you guys from Linux Mint

---

### Post by PC-Ente on 2007-12-10
But there are no 64bit-Packages in this Repo, Just to Say it.=P~

---

### Post by Turin Turambar on 2007-12-11
Works here too!

---

### Post by bruce89 on 2007-12-11
Uploaded to my PPA.

---

### Post by Vinno on 2007-12-12
> **PC-Ente said:**
> But there are no 64bit-Packages in this Repo, Just to Say it.=P~

So there is a 64bit package for pidgin?

So if pidgin dont put out packages, then do ubuntu team or only when its a security fix?

---

### Post by ImpressMe on 2007-12-13
> **bruce89 said:**
> Uploaded to my PPA.

Thanks again, Bruce. Impatiently I tried the Mint repo until you upgraded, and then Synaptic wanted to up/downgrade some files, GIMP and what not.

Next time I'll wait patiently for your repo to update!

---

### Post by bruce89 on 2007-12-13
> **ImpressMe said:**
> Thanks again, Bruce. Impatiently I tried the Mint repo until you upgraded, and then Synaptic wanted to up/downgrade some files, GIMP and what not.

GIMP 2.4.2 is in my PPA too, removing gimp-print.

> **ImpressMe said:**
> Next time I'll wait patiently for your repo to update!

I'll try to be quick in the future.

> **Vinno said:**
> So there is a 64bit package for pidgin?

[http://ppa.launchpad.net/bruce89/ubuntu/pool/main/p/pidgin/](http://ppa.launchpad.net/bruce89/ubuntu/pool/main/p/pidgin/)

---

### Post by Vinno on 2007-12-14
Added these 2 sources Bruce.

deb [http://ppa.launchpad.net/bruce89/ubuntu](http://ppa.launchpad.net/bruce89/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/bruce89/ubuntu](http://ppa.launchpad.net/bruce89/ubuntu) hardy main

Did sudo apt-get update
then sudo apt-get upgrade

Nothing to upgrade :(

Edit: 

Failed to fetch [http://ppa.launchpad.net/bruce89/ubuntu/dists/hardy/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/bruce89/ubuntu/dists/hardy/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/bruce89/ubuntu/dists/hardy/main/source/Sources.gz](http://ppa.launchpad.net/bruce89/ubuntu/dists/hardy/main/source/Sources.gz)  404 Not Found
Reading package lists... Done

Edit 2:

Ops, had to change the hardy to gutsy and it seem to work :)

Reading state information... Done
The following packages have been kept back:
  gimp gimp-data gimp-python
The following packages will be upgraded:
  libflac8 libgimp2.0 libpurple0 libtheora0 pidgin pidgin-data rhythmbox
7 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 8654kB of archives.
After unpacking 2372kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libflac8 libgimp2.0 pidgin libpurple0 pidgin-data libtheora0 rhythmbox
Install these packages without verification [y/N]? y


Woot, Thanks.

---

### Post by altonbr on 2007-12-14
> deb [http://ppa.launchpad.net/bruce89/ubuntu](http://ppa.launchpad.net/bruce89/ubuntu) gutsy main
deb [http://ppa.launchpad.net/bruce89/ubuntu](http://ppa.launchpad.net/bruce89/ubuntu) gutsy universe

This is excellent! Thank you so much!

I get this error, however, with the epiphany browser:
> E: /var/cache/apt/archives/epiphany-browser-data_2.20.0-3ubuntu1~ppa2_all.deb: trying to overwrite `/usr/share/applications/bme.desktop', which is also in package epiphany-browser

Still can't complain though :P

---

### Post by isaacj87 on 2007-12-15
Quick question...

I have the debs from getdeb.net (pidgin 2.2.1) for feisty...and I'm looking to upgrade...

This repo, is it okay to use on Feisty? Should I compile or are there some debs available? 

Thanks!

---

### Post by ftmichael on 2007-12-28
My partner just got a new Ubuntu laptop from Dell - an Inspiron 6400n - which came with Feisty installed and a Gutsy CD.  Today he installed Gutsy and then installed the 149 updates that were waiting for him.  Upon rebooting after installing the updates, he found that Pidgin would no longer connect, unless he went into his Accounts window and systematically disabled and re-enabled each account.  This was the version currently in the Gutsy repositories - 2.2.0, is it? - so I had him add a third party repository and install 2.3.1.  It's the same repository I got mine from for my Gutsy machine.  It still wouldn't connect without going through the same song and dance.

We tried completely uninstalling pidgin, pidgin-data, and libpurple0, deleting the .purple directory, and reinstalling, then re-adding a single account.  Same problem - it connected, and then when he tried restarting Pidgin, it wouldn't connect unless he went into the Accounts window and disabled and re-enabled the account.  He has an internet connection and can use Firefox without issue.

Wtf is going on?  We assume that one of the 149 updates screwed things up, but why does my completely up-to-date Gutsy machine not have an issue while his does?

Edit: [http://ubuntuforums.org/showthread.php?t=587907](http://ubuntuforums.org/showthread.php?t=587907) addresses this.

Michael

---

### Post by ShelJ on 2007-12-29
Hey thanks!!  This worked for me.  Tried three or four times to get updates thru Ubuntu, but couldn't, even downloaded the code but couldn't get it working  ...

---

### Post by Kosimo on 2008-01-02
Pidgin .deb from Getdeb ;)

[http://www.getdeb.net/app.php?name=Pidgin]("http://www.getdeb.net/app.php?name=Pidgin")

---

### Post by kevdog on 2008-01-02
Compile it from source!!  Ok is it just me but it really doesnt seem any different from the previous version.  I do not understand why many people are scared of this solution.  Doing this allows it to work on any platform, including 64 bit.  It takes about 30 minutes.  (Mostly of down time doing nothing).  In addtion you can compile the purple plugin pack and the otr plugin.  These are great additions if you like using pidgin.

---

### Post by Sockerdrickan on 2008-01-02
This reallly depends on the hardware, it takes <3 minutes for me.

---

### Post by kevdog on 2008-01-02
Wow, if it took <3 minutes for me, I think I would wet my pants.  Wouldnt have time to make it to the bathroom, go eat lunch, read the paper, and then come back.

---

### Post by Tumpster on 2008-01-05
Dumb question, but is there a deb for 2.3.1 for Fiesty users or do we use that one thats marked for gutsy? Thanks!  :)

---

### Post by altonbr on 2008-01-05
> **Tumpster said:**
> Dumb question, but is there a deb for 2.3.1 for Fiesty users or do we use that one thats marked for gutsy? Thanks!  :)

2.3.1 isn't even in the Hardy repositories as of yet. It's at 2.2.2... [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=pidgin&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=pidgin&searchon=names&subword=1&version=all&release=all)

This is your safest bet: [http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)... You can try the Gutsy repository in Feisty but it might not install due to bad dependancies. If you can install the dependancies properly then you *SHOULD* be in good shape. I would advise not to try, but that's just me.

---

### Post by bruce89 on 2008-01-05
> **altonbr said:**
> 2.3.1 isn't even in the Hardy repositories as of yet. It's at 2.2.2... [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=pidgin&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=pidgin&searchon=names&subword=1&version=all&release=all)


I wonder why they haven't bothered to merge Debian's version yet (like I have).

---

### Post by steveneddy on 2008-01-05
> **Kosimo said:**
> Typical answer...


I can't imagine myself creating software hat is not usable for normal people without compiling knowledge.  If I made a software I would do all my efforts to make all people use it... Anyway....

Let's learn how to compile well ;)

I like to compile my own software.

All the cool kids compile their own stuff.

---

### Post by BreathEasy on 2008-01-05
> **steveneddy said:**
> I like to compile my own software.

All the cool kids compile their own stuff.
Until you get an error despite having all the dependencies, then you scratch your head wondering why you bothered and end up getting the packages.

/experience. :)

---

### Post by kevdog on 2008-01-05
What dependencies are you missing?

---

### Post by BreathEasy on 2008-01-05
I just said, I had all the dependencies.

If you must know, it was a pre-1.0 version of Linuxdcpp, in Feisty. Long story short, it wouldn't compile because a particular package I had installed was sliently conflicting with ANOTHER package. The configure script must have chosen the wrong header files out of the two or something, so the compilation bombed out half way. Making a few educated guesses and uninstalling packages until I found out what was going on, fixed things.

Who's fault it was for chosing the wrong stuff during configure, I dunno, but it certainly reinforced my belief that pre-built packages are a godsend for keeping one's mind sane.

EDIT: Other times, it's just not really worth it. What do I gain by compiling something like Pidgin? Geek cred? Gimme a break. It's an IM, it doesn't need special optimizations or anything. Having it all contained in easy to use packages makes perfect sense. One of the reasons why I'll never bother with Gentoo.

---

### Post by kevdog on 2008-01-05
Im not saying anything about being a geek, but once you compile pidgin once (and go through the pain of finding all the dependencies), you can easily upgrade to the next version within minutes.  In addition you have the skills to compile the numerous extensions available for pidgin that are only available as source code.  Im not saying that you couldnt add the plugins to a pre-built version, however Im speculating that there are not many people who install the prebuilt version, but then go on to compile and install the plugins.

One thing that I hate is that pidgin doesnt offer an svn source.  With svn sources its so easy to upgrade your current version.

Pidgin doesnt give you a lot by compiling the source code (other than the ability to run a newer version), however there are a lot of other programs that when you compile the source, you can configure additional options -- two programs off the top of my head that I can think of in just a few seconds are conky_svn and gnupg_svn.  

So maybe its geeky of me to thinks its great to compile some selected programs from source.  However with pidgin, its just about as painful to search for a third party repository offering the latest release, try a few times to download the version (and fail), keep looking, and then finally be successful.  I dont exactly trust the getdeb repository for opinions numerously voiced by others.

---

### Post by BreathEasy on 2008-01-05
Well I do agree it would be nice if the Pidgin developers built their own packages for download, like the Deluge Torrent developers too. At least with those you'd have no worries, given the source. Also I was probably a bit too harsh about the problems with compiling before. Just now I downloaded version 1.0.1 of Linuxdcpp, and after installing the remaining dependencies (it's a freshly formatted system, so started from scratch), it compiled and ran without trouble on my 64-bit system. Very clean. :)

Side note: what's wrong with getdeb again? Haven't read much into it, but it's been quite useful for me.

---

### Post by kevdog on 2008-01-06
Im not the only one, but some of getdebs builds have not worked on my system -- some have referred getdebs builds as "low quality", however I really dont know what that means.  If you haven't had any problems, that that is good for you.  Im under the moto -- if I can compile it without too much trouble -- I will.  I know that moto isn't for everyone.  

Fundamentally I love the concept of getdeb, I just haven't had that great of success with their packages.  I haven't tried releases in some time, so perhaps they have improved.

---

### Post by RasmusB on 2008-01-08
Well, seems like I'm the only one having problems then...

Had the standarg pidgin client installed (running gutsy), i think it was version 2.2 something. Worked perfectly, but I wanted to upgrade anyway...

I removed my install, installed the packages from getdeb, and it couldn't connect to msn... ICQ worked though. 

Anyways, I uninstalled pidgin again and tried rolling back to the 2.2.x that came with ubuntu... but that version cant connect either! The reason given is 

"Unable to authenticate: Unable to connect"

which doesen't really tell me much... The wierd part is that 2.2.x was running perfectly, but somehow I managed to break something while installing 2.3.1.

Any suggestions on how to get any version running again? I have tried clearing the .libpurple folder between installations, doesen't help.

---

### Post by rhc on 2008-01-11
Why can't i see status messages in pidgin contact list? Version 2.3.1.
Doesn't support it?

And one more question

is there no way to group consecutive messages for the same person?

it s a bad display like this:

Jo: Hi
Jo: How are you?
Jo: You there?
Jo:
Jo:
Jo:

---

### Post by koleoptero on 2008-01-11
Thanks guys for the gutsy debs. Worked fine.

---

### Post by virx on 2008-01-13
About msn:
Can I see in Pidgin what music contact is listening to?
or those long (usually pointless) contact name description written in italic?

---

### Post by altonbr on 2008-01-13
> **virx said:**
> About msn:
Can I see in Pidgin what music contact is listening to?
or those long (usually pointless) contact name description written in italic?

Not yet, the newer MSN protocol isn't compiled with Pidgin (unless done by choice). If you'd like a more MSN-like IM, I suggest Emesene: [http://emesene.org/trac/wiki/WikiStart](http://emesene.org/trac/wiki/WikiStart)

The Ubuntu repository for it is:
deb [http://apt.emesene.org/](http://apt.emesene.org/) ./

Emesene has the features you're looking for.

---

### Post by desperado315 on 2008-01-13
I got this error " pidgin: error while loading shared libraries: libpurple.so.0: cannot oper shared object file: no such file or directory"
So anyone can help me out plz. Thanks

---

### Post by virx on 2008-01-14
> **altonbr said:**
> Not yet, the newer MSN protocol isn't compiled with Pidgin (unless done by choice). If you'd like a more MSN-like IM, I suggest Emesene: [http://emesene.org/trac/wiki/WikiStart](http://emesene.org/trac/wiki/WikiStart)

The Ubuntu repository for it is:
deb [http://apt.emesene.org/](http://apt.emesene.org/) ./

Emesene has the features you're looking for.


Thx for suggestion. Found out bout it from this thread. Any idea why isn't it in official repository. Still raw?

---

### Post by altonbr on 2008-01-14
> **virx said:**
> Thx for suggestion. Found out bout it from this thread. Any idea why isn't it in official repository. Still raw?

It think it's a brand new project (6 months old maybe?) and it still in an almost beta format. Ubuntu wouldn't have time to put it in 7.10 as it was so new when 7.10 came out, and it may not be out in 8.04 as it hold 3 years of support for all packages and they're probably not sure of the future of Emesene.

Ubuntu likes to ship with 1 package per use (by default) and allow people to switch to whatever they prefer, however, since Pidgin already supports 10+ protocols, they MIGHT find it a waste to ship a 'duplicate' program.

Pidgin DOES have the same functionality of Emesene, but they find that it's unstable and will only like to release it when it's fully stable.

For now, you can compile Pidgin (using a .tar.gz) and enable MSNP14 using these commands:
```
$ ./configure --enable-msnp14
$ make
$ sudo make install
```

---

### Post by virx on 2008-01-14
Thx **altonbr**, after 1 hour and few errors still can't see those silly italic names, allthough before compile should be done 
[http://developer.pidgin.im/wiki/FAQssl#UbuntuFeisty7.04andGusty7.10](http://developer.pidgin.im/wiki/FAQssl#UbuntuFeisty7.04andGusty7.10)
to get SSL working. - It wasn't ment as accusation :)

That reminds me that I have never compiled a program from source, besides kernel in my 2 years Ubuntu history.

after 
$ ./configure --enable-msnp14

I see
Protocols to build dynamically : .... msnp9 ... and not msn14 - is that why this italic name feature didn't get working?

---

### Post by kevdog on 2008-01-14
virx

Here's a good link I found about how-to compile pidgin from source.  Im sure if you combine this link with your configure statement above, you might get what you are looking for:

[http://ubuntuforums.org/showthread.php?t=658244&highlight=pidgin](http://ubuntuforums.org/showthread.php?t=658244&highlight=pidgin)

---

### Post by virx on 2008-01-16
OK, this is what I did:

```

sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude remove pidgin pidgin-data
sudo aptitude install build-essential linux-headers-`uname -r` checkinstall
sudo aptitude install libexpat1-dev libintl-perl gettext bcp libx11-dev libgcrypt11-dev libgtk2.0-dev libxss-dev libsm-dev libstartup-notification0-dev libgtkspell-dev libsqlite3-dev libecal1.2-dev libncursesw5-dev libgconf2-dev libgstreamer0.10-dev libmeanwhile-dev libavahi-client-dev libavahi-glib-dev libavahi-compat-howl-dev libsilc-1.1-2-dev libgadu-dev libperl-dev libgnutls-dev doxygen xsltproc tcl8.4-dev tk8.4-dev check libnss3-dev dot2tex libecal1.2-dev libedata-book1.2-dev flex libnm-glib-dev libmng-dev libmono-dev libsasl2-dev libzephyr-dev libkrb5-dev

rm /usr/local/bin/pidgin -rf
rm ~/.purple -rf

wget http://downloads.sourceforge.net/pidgin/pidgin-2.3.1.tar.bz2
tar jxfv pidgin-2.3.1.tar.bz2
cd pidgin-2.3.1
./configure --prefix=/usr --enable-mono --enable-nm --enable-msnp14
make
make install

```
(sudo is used where needed)

Maybe this "Personal message" thing must be enabled from some configuration file? 
Does anybody have seen MSN Live personal messages from Pidgin?
U sure msnp14 should do the trick?

---

### Post by Prisma on 2008-01-16
mmmmm... no video and audio support yet? ok i will check back next year if this crappy IM client ever gets usable. Until that i will stick with the horrendous rendering of Amsn, better that than nothing. :(

---

### Post by altonbr on 2008-01-17
> **Prisma said:**
> mmmmm... no video and audio support yet? ok i will check back next year if this crappy IM client ever gets usable. Until that i will stick with the horrendous rendering of Amsn, better that than nothing. :(

Yeah, ain't vendor lock-in a bitch?

---

### Post by koleoptero on 2008-01-17
> **Prisma said:**
> mmmmm... no video and audio support yet? ok i will check back next year if this crappy IM client ever gets usable. Until that i will stick with the horrendous rendering of Amsn, better that than nothing. :(

I use amsn for msn and pidgin for the rest. If you want better rendering in amsn try this: [http://ubuntuforums.org/showthread.php?t=297676](http://ubuntuforums.org/showthread.php?t=297676)

---

