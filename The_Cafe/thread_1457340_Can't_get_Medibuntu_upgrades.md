---
title: "Can't get Medibuntu upgrades"
date: 2010-04-18
forum: The Cafe
---

### Post by cjnkns on 2010-04-18
Any other Lucid users having issues with the Medibuntu repos this morning?

I am not sure if I should just ignore this message and update or wait until this is fixed....

> Failed to fetch [http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11). - connect (110: Connection timed out)
Failed to fetch [http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.medibuntu.org:http:
Failed to fetch [http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.medibuntu.org:http:
Failed to fetch [http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to fetch [http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz)  Unable to connect to packages.medibuntu.org:http:
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Paddy Landau on 2010-04-18
Not just Lucid. It's happening on Hardy and Jaunty too.

Just try again tomorrow.

---

### Post by Linuxforall on 2010-04-18
And Karmic too here as well.

---

### Post by theozzlives on 2010-04-18
I just installed the libdvdcss2 file from the .deb I downloaded. I wouldn't expect much to work until the final release.

---

### Post by cjnkns on 2010-04-18
Ok - I'll try tomorrow.

Thanks for the help.

---

### Post by barney385 on 2010-04-18
Is anyone else having problems upgrading from the Medibuntu repository?

---

### Post by jaycee23 on 2010-04-18
Same here Barney

---

### Post by barney385 on 2010-04-18
Ahhh...thx. I was worried I broke something...


:smile:

---

### Post by WinterRain on 2010-04-18
There may simply be no upgrades available at the moment.

---

### Post by eys on 2010-04-18
Looks like Medibuntu server is down.

---

### Post by jaycee23 on 2010-04-18
Maybe it's this volcanic ash which has grounded all flights in the UK (and parts of Europe!)

It could be in the ether(net)

:lolflag:

---

### Post by barney385 on 2010-04-18
> **WinterRain said:**
> There may simply be no upgrades available at the moment.

Naw...it would still make the check...

---

### Post by mikodo on 2010-04-18
> **barney385 said:**
> Is anyone else having problems upgrading from the Medibuntu repository?
As of last nite, I had the problem.

---

### Post by howefield on 2010-04-18
The website is up, but anything to do with the packages is down. They'll most likely be back up shortly, just keep trying every so often.

---

### Post by barney385 on 2010-04-18
> **howefield said:**
> The website is up, but anything to do with the packages is down. They'll most likely be back up shortly, just keep trying every so often.

Yeah...I haven't found anything else out about it. It might just be some maintenance or somethin...

---

### Post by Elfy on 2010-04-18
There are some mirrors listed in [https://bugs.launchpad.net/medibuntu/+bug/565810](https://bugs.launchpad.net/medibuntu/+bug/565810)

you could edit your medibunt.list or even comment them out if you so wished.

---

### Post by barney385 on 2010-04-18
> **forestpiskie said:**
> There are some mirrors listed in [https://bugs.launchpad.net/medibuntu/+bug/565810](https://bugs.launchpad.net/medibuntu/+bug/565810)

you could edit your medibunt.list or even comment them out if you so wished.

Thanks. Those are Lucid repos though and I'm staying with Hardy until the 29th...


:smile:

---

### Post by howefield on 2010-04-18
> **barney385 said:**
> Those are Lucid repos though and I'm staying with Hardy until the 29th...

They mirror all the Ubuntu releases.

Try clicking on here

[http://mirrors.ucr.ac.cr/medibuntu/hardy/index.html](http://mirrors.ucr.ac.cr/medibuntu/hardy/index.html)

---

### Post by barney385 on 2010-04-18
> **howefield said:**
> They mirror all the Ubuntu releases.

Try clicking on here

[http://mirrors.ucr.ac.cr/medibuntu/hardy/index.html](http://mirrors.ucr.ac.cr/medibuntu/hardy/index.html)

heh...OK...I'll try it...thx

---

### Post by mikodo on 2010-04-18
> **howefield said:**
> They mirror all the Ubuntu releases.

Try clicking on here

[http://mirrors.ucr.ac.cr/medibuntu/hardy/index.html](http://mirrors.ucr.ac.cr/medibuntu/hardy/index.html)

I tried for the Karmic install of Realtime  posted from forestpiskie here  [https://bugs.launchpad.net/medibuntu/+bug/565810](https://bugs.launchpad.net/medibuntu/+bug/565810)

The automatic Helix player downloader for RealPlayer 10 (non-free/graphics) on this site
for Karmic stalled and eventually gave a screen that it failed to fetch it.

I'll just wait until the Medibuntu packages are available from their site.

Thanks.

---

### Post by goldshirt9 on 2010-04-18
i picked the wrong weekend to dump windows and install ubuntu completely on my laptop
:lolflag:

well not everything is lost.
hope its up soon

---

### Post by barney385 on 2010-04-18
Wouldn't work for me. I'm probably not doing something right though.

I added mirror #1 to my third party source list, but it didn't work for me.

What is the proper way to add a repo? 

I haven't done it in some time...

---

### Post by fooman on 2010-04-18
>  What is the proper way to add a repo? first,  open the *sources.list* file in gedit with root privileges ....to do that,  open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
gksudo gedit /etc/apt/sources.list 
```when it opens,  find the non-working medibuntu lines and place a # in front of each one.  then add (copy/paste) the following 2 lines to the bottom of the file.

```
deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) hardy free non-free
deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) hardy free non-free
```save and close the file.  then while in the terminal, update the repos with this command:

```
sudo apt-get update
```hope that helps.

---

### Post by barney385 on 2010-04-18
> **fooman said:**
> first,  open the *sources.list* file in gedit with root privileges ....to do that,  open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
gksudo gedit /etc/apt/sources.list 
```when it opens,  find the non-working medibuntu lines and place a # in front of each one.  then add (copy/paste) the following 2 lines to the bottom of the file.

```
deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) hardy free non-free
deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) hardy free non-free
```save and close the file.  then while in the terminal, update the repos with this command:

```
sudo apt-get update
```hope that helps.

They are not listed!!! Here's my source list...

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports restricted main multiverse universe

---

### Post by barney385 on 2010-04-18
I went ahead and added the repo to my source list, and I still could not update.

I checked my software sources by going through Administration and the original repos are still there but they don't show up  on my source list.

Hmmm

---

### Post by foxy123 on 2010-04-18
> **theozzlives said:**
> I just installed the libdvdcss2 file from the .deb I downloaded. I wouldn't expect much to work until the final release.
i wonder where you got it from? I need urgently to install it and medibuntu is down :(

---

### Post by jangal on 2010-04-18
just entered the world of ubuntu - i was bumbling around all day thinking i was doing something wrong. ha! ha! ha! i was also trying to upgrade to the studio but received a similar connection failed/timed out...

---

### Post by howefield on 2010-04-18
> **foxy123 said:**
> I need urgently to install it and medibuntu is down :(

I'll send it to you if you still need it.

---

### Post by foxy123 on 2010-04-18
> **howefield said:**
> I'll send it to you if you still need it.

thanks a lot, but i've just found the mirrors here

[http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html]("http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html")

---

### Post by fooman on 2010-04-18
there may be another place where the medibuntu repos are hiding.  see if you have a file called /etc/apt/sources.list.d/medibuntu.list

run this in terminal:

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

if the file opens and is not blank,  then you should see the medbuntu lines there.   go ahead and put a # in front of each of them.  save and close the file,  then run:

```
sudo apt-get update
```

hope that works for you.

---

### Post by barney385 on 2010-04-18
> **fooman said:**
> there may be another place where the medibuntu repos are hiding.  see if you have a file called /etc/apt/sources.list.d/medibuntu.list

run this in terminal:

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```if the file opens and is not blank,  then you should see the medbuntu lines there.   go ahead and put a # in front of each of them.  save and close the file,  then run:

```
sudo apt-get update
```hope that works for you.

Yes. It was there and I commented them out. I didn't see the Medibuntu repo check when I updated though.

:confused:

---

### Post by fooman on 2010-04-18
> **barney385 said:**
> Yes. It was there and I commented them out. I didn't see the Medibuntu repo check when I updated though.

:confused:

remove the 2 medibuntu mirror lines you added in */etc/apt/sources.list* and instead place them in */etc/apt/sources.list.d/medibuntu.list* (leaving the original medibuntu lines commented out).  save and close the files...and then once again:

```
sudo apt-get update
```

---

### Post by barney385 on 2010-04-18
> **fooman said:**
> remove the 2 medibuntu mirror lines you added in */etc/apt/sources.list* and instead place them in */etc/apt/sources.list.d/medibuntu.list* (leaving the original medibuntu lines commented out).  save and close the files...and then once again:

```
sudo apt-get update
```

Yeah...I did that, and I'm not seeing the Medibuntu check. I checked my third-party software source list and the two new ones of the mirrored site are checked.

I don't know, maybe the new mirror site just doesn't say Medibuntu. 

Yeah. It just says either free or non-free release now it looks like.

So, I think I'm successfully checking for updates for Medibuntu again, though it really should be substantiated by someone else.

:P

---

### Post by barney385 on 2010-04-18
There are mirror sites and other instructions on this thread:

[http://ubuntuforums.org/showthread.php?t=1457340](http://ubuntuforums.org/showthread.php?t=1457340)

---

### Post by fooman on 2010-04-18
> **barney385 said:**
> Yeah...I did that, and I'm not seeing the Medibuntu check. I checked my third-party software source list and the two new ones of the mirrored site are checked.

I don't know, maybe the new mirror site just doesn't say Medibuntu. 

Yeah. It just says either free or non-free release now it looks like.

So, I think I'm successfully checking for updates for Medibuntu again, though it really should be substantiated by someone else.

:P

no it won't say medibuntu,  but you should see something like these in the output of *apt-get update*:

```
Hit http://mirrors.ucr.ac.cr hardy/free Sources        
Hit http://mirrors.ucr.ac.cr hardy/non-free Sources
```

if so,  then its all good.  btw,  when the medibuntu repo is back up...just go back and uncomment the original lines and comment out the mirrors.

---

### Post by cariboo on 2010-04-18
Merged two threads on the same subject, and moved to the Cafe.

---

### Post by Linuxforall on 2010-04-19
Hope this is solved soon, I have some new installs to do.

---

### Post by pbateman on 2010-04-19
Still waiting here too, glad i found this page and see its not just me having issues, i too thought i might have broken something.....

---

### Post by mountain_goat on 2010-04-19
Yep, me too here in Australia.
Noticed it some days ago.
I'm happy to wait until it comes back up, but it was a relief to note that it wasn't me foolin' about with Lucid that was the cause.

---

### Post by goldshirt9 on 2010-04-19
i dont suppose there is any news as to when it will be back up and running

---

### Post by taurolyon on 2010-04-19
Those looking for libdvdcss2 please see my post here:

[http://ubuntuforums.org/showthread.php?p=9143933&posted=1#post9143933](http://ubuntuforums.org/showthread.php?p=9143933&posted=1#post9143933)

there's an older mirror with the .deb's posted. They're working fine, and should get updated once the repository is up!

---

### Post by Paddy Landau on 2010-04-19
> **goldshirt9 said:**
> i dont suppose there is any news as to when it will be back up and running
Actually, do the people in charge know that the repository is down? Do we need to report it somewhere? It's been quite a while already.

---

### Post by magnetra7 on 2010-04-19
They're still down ...

As a quick fix you could use the back-end server (as mentioned in the bug report) which is an official server, too.

Open up your /etc/hosts with the editor of your choice, and put in this line:
```

88.191.101.8 packages.medibuntu.org

```

Try doing an 'aptitude update' afterwards.

---

### Post by coffeecat on 2010-04-19
> **Paddy Landau said:**
> Actually, do the people in charge know that the repository is down? Do we need to report it somewhere? It's been quite a while already.

I found this link on another thread:

[https://bugs.launchpad.net/medibuntu/+bug/565810](https://bugs.launchpad.net/medibuntu/+bug/565810)

[quote="Launchpad Thread post #12"]Maxence is aware of the problem. Unfortunately, it's likely that the  front-end, which is what is currently down, won't be back up until  Wednesday.[/quote]

---

### Post by goldshirt9 on 2010-04-19
[taurolyon]("http://ubuntuforums.org/member.php?u=1020146") as i stated in the linked post .
MANY THANKS for that:P

coffeecat - good point but to who / where :confused:
we all assume that the people in charge would be aware of this fault .
but do they know:confused:

---

### Post by magnetra7 on 2010-04-19
Isn't it ridiculous that we cannot update packages if just one repository is down? At least here I couldn't update successfully the other repositories since the medibuntu one down is (until I applied the fix I posted above this post).

Maybe APT needs some tweaking so that it won't hang if updating one repository fails. It stays right now at 'connecting to packages.medibuntu.org' for a long time.

---

### Post by goldshirt9 on 2010-04-19
a good point and hopefully a lesson learned

---

### Post by Technomouse on 2010-04-19
Here is my fix 

[http://ubuntuforums.org/showthread.php?t=1457944&highlight=medibuntu.org](http://ubuntuforums.org/showthread.php?t=1457944&highlight=medibuntu.org)

---

### Post by Elfy on 2010-04-19
> **magnetra7 said:**
> Isn't it ridiculous that we cannot update packages if just one repository is down? At least here I couldn't update successfully the other repositories since the medibuntu one down is (until I applied the fix I posted above this post).

Maybe APT needs some tweaking so that it won't hang if updating one repository fails. It stays right now at 'connecting to packages.medibuntu.org' for a long time.

As I am not that worried at the moment about medibuntu I just commented the medibuntu repo in it's list - I'll put it back later on. No need to wait for it to hang then.

---

### Post by Paddy Landau on 2010-04-19
> **coffeecat said:**
> I found this link on another thread:

[https://bugs.launchpad.net/medibuntu/+bug/565810](https://bugs.launchpad.net/medibuntu/+bug/565810)
Ah, thanks.

They think it will be up on Wednesday.

I'll wait.

---

### Post by magnetra7 on 2010-04-19
Just use the hosts file fix - you'll have complete access to medibuntu again (from the official server).

> **forestpiskie said:**
> As I am not that worried at the moment about medibuntu I just commented the medibuntu repo in it's list - I'll put it back later on. No need to wait for it to hang then.
Yeah, that's one solution. But what about the new Ubuntu users? They don't know anything about a sources.list. Not very user friendly isn't it?!

---

### Post by Eddie Wilson on 2010-04-19
> **fooman said:**
> first,  open the *sources.list* file in gedit with root privileges ....to do that,  open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
gksudo gedit /etc/apt/sources.list 
```when it opens,  find the non-working medibuntu lines and place a # in front of each one.  then add (copy/paste) the following 2 lines to the bottom of the file.

```
deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) hardy free non-free
deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) hardy free non-free
```save and close the file.  then while in the terminal, update the repos with this command:

```
sudo apt-get update
```hope that helps.

Well that's one way to do it. As a matter of fact I use to do it that way myself but there's a better way now. Go to System and click on Administration and then click on Sources. There you can enter the repo into the third party sources, hit add and then reload (or update) the sources and you are done. :)

---

### Post by barney385 on 2010-04-19
I have the medibuntu package site commented out now and I was able to update today. I guess it's suppose to be fixed Wednesday.

The Medibuntu site that is...

---

### Post by nomnex on 2010-04-19
Same here.
Wednesday, UTC Time?

---

### Post by cjnkns on 2010-04-19
Ok - I am STILL getting the same error as above!

Are the medibuntu server(s) still down?

---

### Post by stardustdk on 2010-04-19
In a couple of days it seems like medibuntu.org is down.
When i try to sudo aptitude update, i don't get updates, 
"Unable to connect to packages.medibuntu.org".

Any idea why?

Best regards

---

### Post by MaxIBoy on 2010-04-19
Same here, I'm not getting it either. Pretty irritating.

---

### Post by ThatBum on 2010-04-19
Me too, I have Lucid beta 2.

I thought I broke something too...

---

### Post by diablo75 on 2010-04-20
I'm trying to install DeVeDe and when I go to install it appears to stall waiting on a package to download from them.  Just wanted to check and see if anyone else is having this problem.

---

### Post by sandyd on 2010-04-20
medibuntu BETTER get it up and running before the 29th or there will be hell to pay...

---

### Post by PLI200872 on 2010-04-20
Same here - all request to packages.medibuntu.org timing out.

---

### Post by garvinrick4 on 2010-04-20
> **diablo75 said:**
> I'm trying to install DeVeDe and when I go to install it appears to stall waiting on a package to download from them.  Just wanted to check and see if anyone else is having this problem.
Started yesterday and will be up and running Wed. they say. Couple more days.

---

### Post by Paddy Landau on 2010-04-20
> **carlee said:**
> medibuntu BETTER get it up and running before the 29th or there will be hell to pay...
You'll demand your money back? LOL

---

### Post by ranch hand on 2010-04-20
Does anyone have a clue what is actually going on or are we just pounding sand here?  I would really like to know what is up.

I am using on of the other mirrors so it is not a problem for me but it is very troubling.

The fact is when I ran a search for info the first 8 links, different address' all took me to a hillarious warning that my computer was infected with malware and I need to download some exe file got old and I gave up on that.  This also concerns me as it appears that some one is trying to exploit this problem.

---

### Post by Paddy Landau on 2010-04-20
> **ranch hand said:**
> The fact is when I ran a search for info the first 8 links, different address' all took me to a hillarious warning that my computer was infected with malware and I need to download some exe file...
Quirky! Maybe you have a malware that's redirecting to the site saying that you have malware. :)

---

### Post by ranch hand on 2010-04-20
> **Paddy Landau said:**
> Quirky! Maybe you have a malware that's redirecting to the site saying that you have malware. :)
Yup, I better go download the .exe file and run here on my 10.04-testing install and get it all cleaned up.

---

### Post by Paddy Landau on 2010-04-20
> **ranch hand said:**
> Yup, I better go download the .exe file and run here on my 10.04-testing install and get it all cleaned up.
:lol:

---

### Post by Hobgoblin on 2010-04-20
> **ranch hand said:**
> 

The fact is when I ran a search for info the first 8 links, different address' all took me to a hillarious warning that my computer was infected with malware and I need to download some exe file got old and I gave up on that.  This also concerns me as it appears that some one is trying to exploit this problem.

I noticed that most of the Google search results had a warning about malware as well.

The problem with just commenting out the medibuntu packages is some of the official packages want to "upgrade" the medibuntu ones.  ffmpeg for instance, I assume upgrading with the official version will lose the functionality which the medibuntu version brought.

---

### Post by nilarimogard on 2010-04-20
There are [mirrors]("http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html") available if you can't wait...

---

### Post by goldshirt9 on 2010-04-21
still no luck with the site as yet :(

---

### Post by polly1 on 2010-04-21
Hi  
 
This may be helpful

Please see this thread [http://ubuntuforums.org/showthread.php?t=1458747](http://ubuntuforums.org/showthread.php?t=1458747)

Start Synaptic Manager, then Settings,and then Repositories. Take the action per Morius1`s post and your Update Manager problem should be solved.

It just worked for me on Karmic and (beta) Lucy and will presumably do so on previous Ubuntu s. 

Cheers

:guitar:

---

### Post by 0100TheGeek on 2010-04-21
[nilarimogard]("http://ubuntuforums.org/member.php?u=483836") Awesome find...

Here is the full path for those who don't want to scour the page...

[http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html](http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html)

---

### Post by zander1013 on 2010-04-21
the mirrors go dark if the source image goes down.

i ( and others ) could not get the mirrors to work.

---

### Post by zander1013 on 2010-04-21
the medibuntu servrs are still down at 11:24hrs pst.

btw; mirrors don't work if the source image goes down.

if the source image goes down the mirrors go dark (thats how mirrors work).:lolflag:

will someone post a notice when medibuntu comes back up please?

---

### Post by goldshirt9 on 2010-04-21
cheers for that .
cannot fathom where in the repository to change though :confused:
all i get when i try to update ny synaptic is 
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by barney385 on 2010-04-21
I took the comments off the medibuntu site and it works now.

sudo apt-get update

---

### Post by Bachstelze on 2010-04-21
> **foxy123 said:**
> i wonder where you got it from? I need urgently to install it and medibuntu is down :(

[http://download.videolan.org/pub/libdvdcss/1.2.10/deb/](http://download.videolan.org/pub/libdvdcss/1.2.10/deb/)

Get it straight form the developers instead of getting in second-hand from a third-party. ;) I actually never got the point of this Medibuntu thing.

---

### Post by tgalati4 on 2010-04-21
Seems to be working now.

sudo apt-get update

---

### Post by sandyd on 2010-04-21
its back up.[offtopic]
and I guess the ubuntu packagers have begun their feature freeze cause I havent had any updates in the past 3 days.

---

### Post by Paddy Landau on 2010-04-22
> **Bachstelze said:**
> Get it straight form the developers instead of getting in second-hand from a third-party. I actually never got the point of this Medibuntu thing.
Simple. Put everything in a repository, for two reasons:

[LIST=1]
[*]It makes it dead easy to install, upgrade automatically, and uninstall programs. Way easier, especially for beginners!
[*]Things in the repository have been checked, so you can (reasonably) download from there without worrying about it messing up your machine.
[/LIST]

---

### Post by Linuxforall on 2010-04-22
> **Paddy Landau said:**
> Simple. Put everything in a repository, for two reasons:

[LIST=1]
[*]It makes it dead easy to install, upgrade automatically, and uninstall programs. Way easier, especially for beginners!
[*]Things in the repository have been checked, so you can (reasonably) download from there without worrying about it messing up your machine.
[/LIST]

Welcome to classic example of FOSS hypocrisy, thats why for total newbies coming over from Windows, I only recommend MINT and not Ubuntu.

---

### Post by Paddy Landau on 2010-04-22
> **Linuxforall said:**
> Welcome to classic example of FOSS hypocrisy
:confused: What does this have to do with the post or the thread? It's nothing to do with FOSS, it's to do with making life easier and safer.

---

### Post by Linuxforall on 2010-04-22
> **Paddy Landau said:**
> :confused: What does this have to do with the post or the thread? It's nothing to do with FOSS, it's to do with making life easier and safer.

Its everything to do with it, Ubuntu shares FOSS philosophy and therefore only free stuff allowed, no proprietary or non free allowed and therefore the need for medibuntu repos.

---

### Post by Paddy Landau on 2010-04-22
> **Linuxforall said:**
> Its everything to do with it, Ubuntu shares FOSS philosophy and therefore only free stuff allowed, no proprietary or non free allowed and therefore the need for medibuntu repos.
Whoever told you that is mistaken. Proprietary and non-free is definitely allowed. I use proprietary software, including paid-for. None of this breaks any contract or law.

---

### Post by proxess on 2010-04-22
packages.medibuntu.org is down.

There are mirrors tho.

```
proxess@PRXSS-Laptop:~$ cat /etc/apt/sources.list.d/medibuntu.list
## Please report any bug on https://bugs.launchpad.net/medibuntu/
# deb http://packages.medibuntu.org/ lucid free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx"
# deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx"

## Mirrors
# deb http://mirrors.ucr.ac.cr/medibuntu/ lucid free non-free
# deb-src http://mirrors.ucr.ac.cr/medibuntu/ lucid free non-free
# deb http://mirror.oscc.org.my/medibuntu/ lucid free non-free
# deb-src http://mirror.oscc.org.my/medibuntu/ lucid free non-free
deb ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/ lucid free non-free
# deb-src ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/ lucid free non-free

```

---

### Post by Linuxforall on 2010-04-22
> **Paddy Landau said:**
> Whoever told you that is mistaken. Proprietary and non-free is definitely allowed. I use proprietary software, including paid-for. None of this breaks any contract or law.

I agree with you, I myself use non free stuff but Canonical has this as policy and therefore the medibuntu repos, even Fedora follows the same procedure.

---

### Post by pbateman on 2010-04-22
Seems to be back up? I just added the regular deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free source and it went trough fine this time.....

---

### Post by Laxman_prodigy on 2010-04-22
I think its up?

I added the repository for Karmic and downloaded everything.

---

### Post by Laxman_prodigy on 2010-04-22
I think its up?

I added the repository for Karmic and downloaded everything.:lolflag:

---

### Post by lotus49 on 2010-04-22
> **Linuxforall said:**
> Its everything to do with it, Ubuntu shares FOSS philosophy and therefore only free stuff allowed, no proprietary or non free allowed and therefore the need for medibuntu repos.

You should do your research a bit better.

To quote the Medibuntu site:

"Medibuntu (Multimedia, Entertainment & Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc)."

This is nothing to do with FOSS or the opinion of Canonical. As a company, they have to ensure they comply with the law and are not seen as party to breaches of licensing, copyrights etc. Fedora is in the same position. There is no hypocrisy here, just ignorance on your part.

---

### Post by bapoumba on 2010-04-22
Threads merged.

---

