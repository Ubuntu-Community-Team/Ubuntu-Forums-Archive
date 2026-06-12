---
title: "[SOLVED] The real reason people go back to windows..."
date: 2008-12-15
forum: Testimonials &amp; Experiences
---

### Post by PaulWhipp on 2008-12-15
Actually, I wont go back, there are too many things I like about Linux but...

This is a complaint because I can't currently enter bugs. I hope the suggestion at the end is constructive.

I started this morning with updates required in 8.10. This happens fairly often which is fine.

However, as usual some of the updates failed - reporting corrupt packages (attempting to report the bugs gave me a line of tabs in firefox with 'this address isn't on launchpad error which is unusual).

Later, I found no help files in open office 2.4. I reinstalled it after problems a while back so that is possibly my fault. I try using the package manager to get the english gb help files -

lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-help-en-us_1%3a2.4.1-9ubuntu1_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/help/en/sbasic.db')
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-help-en-us_1%3a2.4.1-9ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cleaned the cache and repeated the attempt with the same error. So I try the US help files and get an almost identical failure.

It seems almost every time I use the, conceptually very nice, repository/package system I end up with install failures or broken packages that require cleanups and visits to the forums and manual work to try to fix.
[B]
These errors should never occur in supported package downloads.[/B]

Perhaps a system could be developed so that when packages are submitted to the repositories they are automatically tested before publication and the download process is set up to encapsulate the installation such that the errors are automatically reported and the packages withdrawn or reverted appropriately if a critical threshold of failures is reached. Such automation would not test everything but it could guarantee clean installation (and uninstalls) on any fully updated supported Ubuntu release.

The experience on initially installing and using ubuntu was fantastic.

The frequency of update failures and 'corrupt packages' makes the Ubuntu feel unreliable and weak.

---

### Post by Art3mis on 2008-12-15
Well.....


Isn't 8.10 still in beta???

---

### Post by Twitch6000 on 2008-12-15
> **Art3mis said:**
> Well.....


Isn't 8.10 still in beta???

LOL no... it is done.

---

### Post by howefield on 2008-12-15
> **Art3mis said:**
> Well.....


Isn't 8.10 still in beta???

No.

---

### Post by diabolik on 2008-12-15
Do you install a lot of packages manually (i.e., without using the package manager)?  I think that sometimes causes these issues.

I'm not saying it's your fault... ideally, the package manager could at least fail more gracefully, like you're suggesting.  I think it's a general problem, though, for package managers to understand changes that are made by other means.

---

### Post by evilkastel on 2008-12-15
8.10... well you should check your server for updates, might be corrupted or not working properly.And would be a good a idea to do a fresh install of ubuntu. this errors are not supossed to happen and in almos all of cases they don't. There is something wrong with your install or/and your download server. Also, if you use different ways to install apps, you can be the one who is tempering with the dependencies. 8.10 does not generate this erros out of blue.

---

### Post by PaulWhipp on 2008-12-15
I do use apt-get when advised to do so on the forums so I guess that is manual installing.

Its good to hear that most people don't get these problems. That restores some of my faith in Ubuntu.

I don't want to reinstall - I make my living out of my PC and my backup is still running XP. reinstalling tends to be at least a whole day out and the frequent advice to 'just reinstall' is a factor in why I've moved away from Windows. Is there some way to safely and cleanly reinstall whatever it is in my system that is making it unreliable in this way?

---

### Post by PaulWhipp on 2008-12-15
btw, these errors are not dependency errors, they are package corruption and short reads so they are not part of the 'hard' problem of the installer knowing what is or is not already on the system - the ubuntu package managers seem to do a very good job of that bit.

---

### Post by evilkastel on 2008-12-15
if you want, you might  swing by #ubuntuforums-beginners (IRC channel) for a better advice. Yet mine will have to be, reinstall.... there is a way you can do this in 2 hours tops, without losing data. neither ubuntu or xp data. if you do not feel like oing to the irc channel let me know and i'll ask the guys and make a nice post for you. We certainly want you to keep running ubuntu, and to run it properly. cheers.

---

### Post by cariboo on 2008-12-15
If you are always getting corrupted downloads from the same server, I would suggest trying a different server. Go to System-->Administration-->Software Sources, and select other from the download from drop down.

Jim

---

### Post by PaulWhipp on 2008-12-15
Thanks Jim,

I'll try the source setting first - It was set on "Server for Australia" which, under other, lists a number of sources.

I'm not sure of the criteria I should use for making a pick or which server is use by default. I clicked on "Select best server" and it just hangs with a dialog box showing with nothing on it... I left it 5 minutes.

I've chosen the top server ([http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu)) and will see what happens before I try the re-install.

---

### Post by PaulWhipp on 2008-12-15
Thanks elvikastel,

It may come to the re-install. I will try Jim's suggestion first.

I'm pretty good at backing up the data, its the applications I use that take the time to put back - Zend studio, Mysql command line, navicat, subversion command line...

---

### Post by PaulWhipp on 2008-12-15
reloading ftp.iinet.net.au repository indexes caused errors with index files failing to download...

trying next in the list (netspace)... that had an even longer list of failures.

On the next one... aarnet.edu.au I was close to giving up (especially as the window just closed with no info) but it seems happy and reloading in synaptic worked fine:

Test with openoffice.org-help-en-gb (in synaptic package manager):

Its downloading around 3-5 times faster than it was before this change.

Changes applied successfully!

I'll restart later today and try the updates again but this is looking good. It also implies that the reinstall would have left me with the same problem. I think its generally better to identify and fix the problem than to reinstall and hope a problem goes away.

Thanks for the help Jim (I clicked on that little thanks button for what its worth)

---

### Post by frankleeee on 2008-12-15
You might post the apt source list for a look to see if something is amiss, and I always use the main server.

---

### Post by konungursvia on 2008-12-15
I always dual boot windows, because there are a handful of things I prefer to do in xp: WP11, WoW, Audacity, CIV III, Illustrator and Photoshop... But I spend 90% of my time in Ubuntu 8.04, both at home and at work. 

I see your frustration and sympathize. But linux is always a bit bleeding edge, like extreme off track skiiing. Don't go there if you can't accept a bit of tinkering. I've had no major problems I didn't enjoy solving with x.

That said, I would say apt-get is not manually installing, as dependencies are very well managed. Manual would be unpacking a tar and running a binary, in my view.

Try letting 8.10 update itself for a month, while using xp as well. You may find our problems in linux are quickly dealt with by the devs.

P

---

### Post by PaulWhipp on 2008-12-15
I know what you mean about waiting for a new release to stabilize - I guess that is why you haven't upgraded to Vista ;)

I am trying to eliminate my need for MS Windows altogether. I don't see Ubuntu as bleeding edge - I see it as a contender to be a real and generally preferable alternative.

I want to feel able to promote it to friends and establishments that will not expect to have to tinker to make it work and I think its very close to achieving that.

Personally, I love to tinker and I see the transparency of open source as crucial in an OS that is going to evolve and ultimately depose Windows but tinkering should be a choice, not a necessity.

---

### Post by solwic on 2008-12-16
> **PaulWhipp said:**
> I know what you mean about waiting for a new release to stabilize - I guess that is why you haven't upgraded to Vista ;)

I am trying to eliminate my need for MS Windows altogether. I don't see Ubuntu as bleeding edge - I see it as a contender to be a real and generally preferable alternative.

I want to feel able to promote it to friends and establishments that will not expect to have to tinker to make it work and I think its very close to achieving that.

Personally, I love to tinker and I see the transparency of open source as crucial in an OS that is going to evolve and ultimately depose Windows but tinkering should be a choice, not a necessity.

I totally agree with you, but I'm afraid Linux won't be a competitor until it can get its share of the "Gamer" market.  Video games are too popular to be totally blown off.  

Sad, really.  Ubuntu is a great OS.  I hate to see it held back by something it really can't control.  :(

---

### Post by 3rdalbum on 2008-12-16
In theory, corrupted packages should be detected. Apt uses hashing to determine that:

a. The package hasn't been maliciously altered in transit
b. The package hasn't been corrupted in transit

The only way you could get corrupted packages is if they were corrupted before the hash was generated.

Ubuntu does have a staging-post for updates - it's called the Proposed repository, and it's there so the technical users can test new updates before they get pushed out to non-technical users. It's relatively safe to have Proposed enabled anyway, but I don't recommend using it unless you have to.

---

### Post by evilkastel on 2008-12-16
Well Paul, auch. Please read my answer for a second time and you will see that i suggetsed the reinstall as a second option.

> well you should check your server for updates, might be corrupted or not working properly

> There is something wrong with your install or/and your download server

Well, it is my fault not to point at the procedure to change siftware sources, yet is very very intuitive. do not get me wrong, i am happy you found your solution, and i am glad you are running a clean and properly working ubuntu. 
Cheers.

---

### Post by Coreigh on 2008-12-16
Please be aware of the difference between a problem and a "bug." A problem is some difficulty you are having with some software or process which may be a bug but is not considered a bug unless it can be duplicated by another user and is in fact a behavior NOT intended by the developers.

[See this link on posting bug reports.]("http://ubuntuforums.org/showthread.php?t=1011078&highlight=launchpad")

I do not mean to make light of your troubles only to add clarification.

It is fun to have the latest and greatest release, but sometimes they aren't that great. If it is important to have the best possible stability stick with the LTS releases. 8.04 is the latest LTS or Long Term Support. While they aren't necessarily any better at release time the longer they are out the better they get.

---

### Post by mdsmedia on 2008-12-16
Actually I don't agree that LTS releases are any more or any less stable than other releases.

Granted, I've upgraded directly from 6.06 (LTS) to 8.04 (LTS).

But that was simply because the last release I upgraded to was 6.06, and after 6.10 I couldn't directly upgrade until 8.04.

LTS releases are just that, Long Term Support....not more stable or less buggy.

I've heard great reports about Intrepid, and I ran the upgrade after a few weeks of it being available. Yes, I ran into problems for the first time with Ubuntu (since 5.04) so I'm not sure. I'm waiting for Intrepid to appear on my magazine DVD and then will do a clean install. I'm currently back on 8.04 and happy as Larry.

---

### Post by solwic on 2008-12-16
> **mdsmedia said:**
> Actually I don't agree that LTS releases are any more or any less stable than other releases.

Granted, I've upgraded directly from 6.06 (LTS) to 8.04 (LTS).

But that was simply because the last release I upgraded to was 6.06, and after 6.10 I couldn't directly upgrade until 8.04.

LTS releases are just that, Long Term Support....not more stable or less buggy.

I've heard great reports about Intrepid, and I ran the upgrade after a few weeks of it being available. Yes, I ran into problems for the first time with Ubuntu (since 5.04) so I'm not sure. I'm waiting for Intrepid to appear on my magazine DVD and then will do a clean install. I'm currently back on 8.04 and happy as Larry.

I would imagine the LTS releases are considered more stable because they're supported longer, meaning more of the bugs, in the end, get worked out and, in the end, they are more stable because of that.  

As for Intrepid...I've had no issues with it.  Granted, I use my PC for pretty basic stuff (music, videos, surfing, e-mail, word processing), but I've had no hanging or crashing or freezing.  Pulse audio, when used in conjunction with Skype, maxes my CPU to 100%...but Pulse was broken long before Intrepid Ibex came along.  

Good luck with Hardy; it's a great release.  :)

---

### Post by PaulWhipp on 2008-12-16
Bug blizzard. If they were to create Linux versions of their games they would make the (commercially important) korean internet cafes very happy and it would begin the gamer swing. There is a petition [http://www.petitiononline.com/ibpfl/petition.html](http://www.petitiononline.com/ibpfl/petition.html) but nothing beats asking in your local store or pointing out to your local internet cafe owner how much money they could save by running ubuntu (its amazing how influential a few buyers can be).

---

### Post by PaulWhipp on 2008-12-16
Thanks for the info 3rdalbum, it does sound good in theory.

It looks like the sources are the issue although I thought they were just like mirrors so I'm not sure how they are causing these problems. I think there is a bug in here somewhere but I agree with Coreigh and while I can repro it by changing my source back to iinet I can't report it as a bug unless I can reliably get a repro that anyone can generate.

---

### Post by Tamlynmac on 2008-12-19
> mdsmedia
I've heard great reports about Intrepid, and I ran the upgrade after a few weeks of it being available. Yes, I ran into problems for the first time with Ubuntu (since 5.04) so I'm not sure. I'm waiting for Intrepid to appear on my magazine DVD and then will do a clean install. I'm currently back on 8.04 and happy as Larry.

+1
Except I started with FF (7.04). Hardy is rock solid and fully functional on all 5 of our systems.

What new magazine DVD?

---

### Post by stalkingwolf on 2008-12-19
there is a process nobody has mentioned.
If you are dual booting, at the grub menu select the Recovery option.
it will run then when it is finished should give you the option to
" fix broken packages".

If you are running just Ubuntu , when the grub starts hit ESC.  Choose
recovery, then the fix package option when it is presented.

Hope this helps.

---

