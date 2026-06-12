---
title: "Ubuntuzilla ceasing^Wcontinuing operation"
date: 2011-03-05
forum: Ubuntuzilla
---

### Post by nanotube on 2011-03-05
Greetings loyal users, and newcomers alike.

We've had a great few years with ubuntuzilla - for a while there was no better way to get timely updates for stable releases of mozilla products than the ubuntuzilla repository.

It seems that those days are over - now the official ubuntu repositories move swiftly to include updates for firefox, thunderbird, and seamonkey - often the very next day after their release from mozilla.

Thus, it seems that there is no longer a need in the ubuntu community for a third party repository to host these official builds. 

As a result, I have pushed out what will probably be the last update to the ubuntuzilla repository, Firefox 3.6.15, Thunderbird 3.1.9, and Seamonkey 2.0.12.

Unless someone steps up and wants to continue updating the ubuntuzilla repository (there's a handy script that'll /almost/ do everything for you automagically), this will mark the conclusion of the project.

I thank you all for your help and support. 

-nanotube

UPDATE: since lucid has not been following along with the latest mozilla releases, I am continuing to update ubuntuzilla with the latest. looks like ubuntu just won't let ubuntuzilla die. :)

---

### Post by Tank Jr on 2011-03-05
A word of thanks to you for making it easy for noobs like me to stay up to date with the latest firefox, seamonkey and thunderbird. I will miss this project.
Once again, a heartfelt thanks.

---

### Post by the.phantom on 2011-03-05
you and this project will be missed !!!
(still haven't got 3.X.15 from the repo's of ubuntu ;-(

and will have a breakdown when ff 4 comes out and i want to stay with my LTS

but you have helped out several of us that would rather use ubuntu but don't know linux at all !

it was a very usefull program and i do appreciat the effort you put into it !

thanks very much for the effort you have put into this project for so long !!!!!

---

### Post by dashaus on 2011-03-06
> **nanotube said:**
> 
It seems that those days are over - now the official ubuntu repositories move swiftly to include updates for firefox, thunderbird, and seamonkey - often the very next day after their release from mozilla.
-nanotube

Nanotube! Thank You very much for all your great help. I found it very convienient to use Ubuntuzilla repo to update FF & Thunderbird.

Would You be so kind to advise: which repo should I add to receive benefits of "repositories [that] move swiftly to include updates for firefox"? I've tried ppa:mozillateam/firefox-stable but it doesn't seem to make any difference to my Ubuntu 10.04. On the other hand ppa:ubuntu-mozilla-daily/ppa seems to me to offer unstable future releases. Would You mind proposing any substitute for ubuntuzilla?

---

### Post by Karlchen on 2011-03-06
Hello, dashaus.

If you read nanotube's words carefully, >  now **the official ubuntu repositories** move swiftly to include updates for firefox, thunderbird, and seamonkey(bold emphasis by me), you will see that the answer is pretty simple: in future, please, use the official Ubuntu repositories in order to get the current versions of Firefox, Thunderbird and Seamonkey. No PPA repository needed any longer.

For the moment, you can still get FF3.6.15, TB3.1.9 and Seamonkey 2.0.12 using the Ubuntuzilla repository located at [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation").

Kind regards,
Karl

---

### Post by dashaus on 2011-03-06
Karlchen,

would you mind being more specific? What should I do to get next FF/TB update from the official ubuntu repositories (i.e 3.6.16 and so on)? Right now I can find in Synaptic Firefox 3.6.8. So far I thought it's outdated due to Canonical's policy of ceasing to update FF after releasing next Ubuntu. 
But now I feel as being the only one receiving stable updates only from ubuntuzilla. 
Please, tell me, how will you update FF to 3.6.16 when the time comes?

regards, dashaus

---

### Post by abumaia on 2011-03-06
In my Synaptic, Firefox is at 3.6.14 and Thunderbird is at 3.1.8. Just a little bit behind still, but I guess it's close enough to current to be usable.

---

### Post by dashaus on 2011-03-06
Abumaia, what is the repository that contains FF 3.6.14? Have you done anything special to get it or it simply turned up by itself? In may case it didn't and I wonder why.

---

### Post by aysiu on 2011-03-06
nanotube, it's been many years, and the whole time I have very much appreciated all the work you've put into this program. Kudos!

---

### Post by Karlchen on 2011-03-06
Hello, dashaus.

Provided you are really using Ubuntu 10.04 (Lucid Lynx) Synaptic should currently offer to install Firefox 3.6.14. (Column "Latest Version") - Yep, they have not added v3.6.15, yet.

Where do you see v3.6.8? In the column "Installed version" or in the column "Latest version"? (Sorry, if my translation of the column names is not 100% correct, I am looking at a German Lucid Lynx version right now.) 
In case the answer is "Installed version", then this simply means that you have stopped using the Canonical Firefox version at v3.6.8.
In case the answer is "Latest version", then this might suggest that you have not configured Synaptic to update the list of available packages automatically.

In order to make sure that Synaptic will always display the current state of the available software packages proceed like this, please (this will only update this list, nothing will be installed without your consent):


[LIST]
[*]System => System Administration => Software Package Sources
[*]Tab "Ubuntu Software": Tick everything except source codes
[*]Tab "Updates": Section "Ubuntu Updates"
Tick "lucid-security" and "lucid-updates"
[*]Tab "Updates": Section "Automatic Updates"
Tick "Check for updates: [daily]" => will make Synaptic update the list once per day
Tick "Only notify about available updates" (=> you will have to confirm when and which updates to install)
[/LIST]

In order to tell Synaptic to update the list on demand (now), proceed like this, please: Launch Synaptic and press <Ctrl>R (reload package information).

In order to switch from the Ubuntuzilla provided Firefox to the one provided by the Canonical repositories, proceed like this, please:


[LIST]
[*]Backup the current Firefox user profile(s). - Just in case anything goes wrong.
[*]You may uninstall Firefox-Mozilla-Build now (provided by Ubuntuzilla) with the help of Synaptic e.g. But you do not have to unless you are worried about recovering the disk space which the Firefoy binaries occupy.
You may uninstall using Snaptic or using the commandline provided by Ubuntuzilla [**here**]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Removal").
[*]With the help of Synaptic select and install the following Firefox packages:
+ Firefox
+ Firefox Gnome Support (might be irrelevant to KDE users)
+ Firefox Branding
(Once you select "Firefox" Synaptic should make sure all required packages get pre-selected as well.)
[*]Apply the selection thus installing Firefox 3.6.14, Build for Ubuntu.
[/LIST]
HTH,
Karl

---

### Post by dashaus on 2011-03-06
Karl, thank you very much for your assistance. My "Ubuntu Updates" settings prevented any updates for some time (apparently ever since FF3.6.8 became available). It seemed strange to me but I could not figure out a reason. Now I now. Thank You very much indeed.

---

### Post by witeshark17 on 2011-03-06
I thank those who ran the Ubuntuzilla repos, it was a very cool way to update. But during the last week or so, I encountered some glitches; trying to update and then replace the Ubuntuzilla version with the Ubuntu repos version caused some directories to break. I now have neither version as the Ubuntu repo version crashes on attempt to download as can be seen in this [ thread](http://ubuntuforums.org/showthread.php?t=1605884&page=4) Is there a CLI command or script that can correct the issue please?

---

### Post by auh2o on 2011-03-09
nanotube, you've provided an excellent and much appreciated service with the Ubuntuzilla project, and I'd like to add my heartfelt thanks! One of the first things I did after moving to Linux/Ubuntu with the advent of Karmic was removing Ubuntu's out-of-date Firefox and adding your repository, and I've been on it ever since. Flawless all the way. It's good news that Canonical have cleaned up their act when it comes to Mozilla updates now, but thanks to you it's never really been a concern whether they did or not.

---

### Post by nanotube on 2011-03-14
Thank you all for your kind words! :)

I'll keep the ubuntuzilla repos updated until Ubuntu Karmic stops being supported, which should be April 2011.

---

### Post by Ev1L on 2011-03-22
firefox is going to accelerate its release schedule (chrome-like), but did Canonical promise to keep up with their updates somewhere?
because in that case perhaps they will lag behind and the only viable alternative to ubuntuzilla (R.I.P. and a very big thank you) seems to be mozilla team PPA (which released ff4 already, canonical didn't yet).
any trusted info about this? :)

---

### Post by auh2o on 2011-03-23
Ev1L: See this thread: [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by Ev1L on 2011-03-23
thanks, i already installed it (worth it :) ) with the mozillateam PPA and i saw the expectation about faster Canonical updates in the future, however my concern was if they really promised that, which i doubt.
i will keep the mozillateam PPA and hope we won't stay too much behind schedule. i honestly don't want to keep an eye on firefox releases and manually install it every time.
before the updates timing was:
-ubuntuzilla: now
-mozillateam: next weeks
-canonical: next semester :)

---

### Post by interfix on 2011-03-23
Bummer!
I suspect I'm not the only one from the Debian camp relying on Ubuntuzilla for timely, painless updates of real Firefox and real Thunderbird.
Okay, so what can I do? Nanotube, I might be interested in taking over. In that case, would you be willing to give me a tour of the premises?

---

### Post by nanotube on 2011-03-24
> **interfix said:**
> Bummer!
I suspect I'm not the only one from the Debian camp relying on Ubuntuzilla for timely, painless updates of real Firefox and real Thunderbird.
Okay, so what can I do? Nanotube, I might be interested in taking over. In that case, would you be willing to give me a tour of the premises?

Hey interfix, sent you a PM. :)

---

### Post by kansasnoob on 2011-04-08
You'll be missed :cry:

Should you ever need someone to perform testing with a future project send me a PM and I'll certainly do my best to help.

This was a rockin' project and IMHO no effort is truly ever wasted since everything learned continues to benefit those who invested their Grey matter :D

---

### Post by nanotube on 2011-04-14
> **kansasnoob said:**
> You'll be missed :cry:

Should you ever need someone to perform testing with a future project send me a PM and I'll certainly do my best to help.

This was a rockin' project and IMHO no effort is truly ever wasted since everything learned continues to benefit those who invested their Grey matter :D

thanks for your kind words. :)

in other news... it seems that lucid users are still SOL as far as firefox4 goes.
so much for my excitement of official ubuntu repos being up to date on mozilla releases... 
i've pushed out ff4 to the repos for the moment...

---

### Post by cfth on 2011-04-15
> **nanotube said:**
> thanks for your kind words. :)

in other news... it seems that lucid users are still SOL as far as firefox4 goes.
so much for my excitement of official ubuntu repos being up to date on mozilla releases... 
i've pushed out ff4 to the repos for the moment...
Hi, first off thanks a bunch for the Ubuntuzilla repo. I've been a proud user for a while now.

So I want to stick with Firefox 3.6.x until all of my extensions and sites work in it. I want to keep Firefox updated so I don't want to remove/disable the Ubuntuzilla repo, but I also don't want to upgrade to 4 just yet, so I'm not sure what to do.

Could the Firefox 4 or 3.6.x package be renamed so people that want to stick with 3.6.x can and not be prompted to upgrade to 4?

---

### Post by kansasnoob on 2011-05-04
I tried to downgrade to 3.6.18 via this PPA today:

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa?field.series_filter=natty](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa?field.series_filter=natty)

It's an ugly undertaking and things show up broken afterwards.

Would you be interested in creating a decent way to revert to 3.6.* :confused:

I'd try to help :)

---

### Post by Karlchen on 2011-05-07
Hello, kansasnoob.

Downgrading e.g. F.F. 4.01 to 3.6.17 works this way:

[LIST]
[*]uninstall the current Firefox version, in the given example v4.0.1, using Synaptic.
[*]remove your current F.F. profile, i.e. $HOME/.mozilla/firefox/{weird looking number}.default/* (keep the folder itself, but not its content)
[*]restore the recent backup of the profile which you created right before updating v3.6.X to v4.0.1  to that folder
 (You have created a backup before upgrading, else you will have got a minor problem now: Like a lot of programmes Firefox, too, can upgrade an older profile to the current version. But an older Firefox version may not be able to use a profile created or modified by a newer FF version. In particular it will not be able to downgrade the profile.)
[*](re-)install F.F. 3.1.7 from the official  Canonical Ubuntu repositories
[*]launch F.F. 3.1.7. Doing so will update the restored profile to v3.1.7
[/LIST]
Yet, as you offer your help, I assume you know all this or maybe you know even better. ;)

Cheers,
Karl
--
P.S.:
But how is dowgrading related to "Ubuntuzilla ceasing operation"? Might downgrading not deserve a dedicated thread of its own perhaps?

[LEFT]
[/LEFT]

---

### Post by Karlchen on 2011-06-26
It might seem as if *ceasing operation* can be a really slow process and may take quite a while, because even today Synaptic on Lucid Lynx (v10.04) tells me that both, Firefox-Mozilla-Build v5.0 and  Thunderbird-Mozilla-Build v3.1.11, are available in nanotube's  Ubuntuzilla repository. :D 
I am not going to complain ... :wink:

Karl

---

### Post by witeshark17 on 2011-06-27
Seems reasonable... :popcorn:

---

### Post by nanotube on 2011-07-11
ok, so ubuntu lucid repositories haven't been following along with the latest mozilla releases... so i am continuing to update ubuntuzilla with the latest releases.

---

### Post by kansasnoob on 2011-07-11
> **nanotube said:**
> ok, so ubuntu lucid repositories haven't been following along with the latest mozilla releases... so i am continuing to update ubuntuzilla with the latest releases.

Cool! Even beyond Lucid Ubuntu is once again falling behind. When i go to the Firefox website I get this:

[ATTACH]197265[/ATTACH]

Personally I've become quite used to this procedure from playing upstream:

> Move "firefox-x.x.x.tar.bz2" to /home
then:
mv firefox-x.x.x.tar.bz2 /usr/lib/
cd /usr/lib/
tar -jxvf firefox-x.x.x.tar.bz2
ln -s /usr/lib/firefox/firefox /usr/bin/firefox

But I remember when Ubuntuzilla was very important to me and I'm always willing to do any testing required to keep this project alive :D

---

### Post by witeshark17 on 2011-07-11
Looks like fun actually... :popcorn:

---

### Post by Karlchen on 2011-07-12
> **nanotube said:**
> ok, so ubuntu lucid repositories haven't been following along with the latest mozilla releases... so i am continuing to update ubuntuzilla with the latest releases.Great. \\:D/

Karl

---

### Post by witeshark17 on 2011-07-13
> **Karlchen said:**
> Great. \\:D/

Karl Yes it is :KS

---

### Post by Karlchen on 2011-12-30
Hello, nanotube.

May we look forward to seeing the current Firefox and Thunderbird versions, i.e. v9.0.1 at the time of writing this, in the Ubuntuzilla repositories soon? [-o<
Seems as if Canonical does not really intend to provide the latest versions of Firefox and Thunderbird in their official repositories, not even for Oneiric Ocelot. ](*,)
Therefore, our hope is on Ubuntuzilla somehow ...

Kind regards,
Karl

---

### Post by nanotube on 2012-01-06
Hi Karl,
Yes you may. Just pushed the new versions out.
Not only that, but Ubuntuzilla now proudly supports 32bit and 64bit versions of all mozilla software. :) I'll sticky up a separate announcement thread for the happy occasion.

---

### Post by witeshark17 on 2012-01-06
Wow; that is quite cool! :popcorn:

---

### Post by nanotube on 2012-01-06
> **witeshark17 said:**
> Wow; that is quite cool! :popcorn:

hehe glad someone's still watching :)

---

### Post by Karlchen on 2012-01-06
Hello, nanotube,
> Just pushed the new versions out. Not only that, but Ubuntuzilla now proudly supports 32bit and 64bit versions of all mozilla software.  This is good news at the beginning of the new year. \\:D/

Cheers,
Karl

---

