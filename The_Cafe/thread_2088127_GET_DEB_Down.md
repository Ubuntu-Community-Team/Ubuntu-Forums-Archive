---
title: "GET DEB Down?"
date: 2012-11-25
forum: The Cafe
---

### Post by Uncle Spellbinder on 2012-11-25
Is [http://www.getdeb.net/](http://www.getdeb.net/) down?
Just went to check for updates and getdeb fails. Curious if it's just me or everyone.

---

### Post by Bandit on 2012-11-25
getting untitled blank page..

---

### Post by Uncle Spellbinder on 2012-11-25
Thanks.

Seems Ubuntu is down, too. At least ubuntu-extras...

```
Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/Release.gpg  Unable to connect to extras.ubuntu.com:http:
Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/Release.gpg  Unable to connect to archive.getdeb.net:http:
Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/i18n/Translation-en_US  Unable to connect to extras.ubuntu.com:http:
Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/i18n/Translation-en  Unable to connect to extras.ubuntu.com:http:
Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-en_US  Unable to connect to archive.getdeb.net:http:
Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-en  Unable to connect to archive.getdeb.net:http:
Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages  Unable to connect to extras.ubuntu.com:http:
Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/binary-i386/Packages  Unable to connect to archive.getdeb.net:http:
Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Jakin on 2012-11-25
Its been down since atleast 4am EST (for me), i tried about that time and got a blank page.

---

### Post by ssam on 2012-11-25
[http://www.downforeveryoneorjustme.com/http://www.getdeb.net/](http://www.downforeveryoneorjustme.com/http://www.getdeb.net/)

:-)

---

### Post by Uncle Spellbinder on 2012-11-26
Hmmm. They've been down for several days now.

---

### Post by Uncle Spellbinder on 2012-11-27
They were back last night, as I updated my Xubuntu without any error messages. Seems down again today, though.

---

### Post by DukeOfMixture on 2012-11-27
Maybe they were down temporarily to remove some dead screen shot links.

Nope, looks like they're still there.

---

### Post by Uncle Spellbinder on 2012-12-05
Damn. Down again. Seems they're down more than they're up. Seriously considering ditching them from my sources.

---

### Post by Primefalcon on 2012-12-05
guess the webmaster forgot to pay their hosting fees... or has discontinued operation or is having server issues.... could just be out having a beer too....

---

### Post by Uncle Spellbinder on 2012-12-05
> **Primefalcon said:**
> ...could just be out having a beer too....

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Animated/icon_lol_zps859982c7.gif[/IMG]

---

### Post by zombifier25 on 2012-12-06
> **Primefalcon said:**
> guess the webmaster forgot to pay their hosting fees... or has discontinued operation or is having server issues.... could just be out having a beer too....
[I'm glad he's a normal human being.](https://xkcd.com/705/)

---

### Post by Primefalcon on 2012-12-06
> **zombifier25 said:**
> [I'm glad he's a normal human being.](https://xkcd.com/705/)
Thanks for posting that, that actually gave me a laugh.... trust me.. I've been needing that

---

### Post by Valentini on 2012-12-06
Seems like it's completely gone atm. The server doesn't even listen on port 80.

---

### Post by dnairb on 2012-12-06
[http://forums.linuxmint.com/viewtopic.php?f=47&t=118809&p=656166#p656112](http://forums.linuxmint.com/viewtopic.php?f=47&t=118809&p=656166#p656112) and be sure to change lucid-getdeb to your distro, e.g. quantal-getdeb, etc.

---

### Post by forrestcupp on 2012-12-06
> **Primefalcon said:**
> could just be out having a beer too....That reminds me of the good old BBS days when the BBS sysop had to have his computer turned on for people to be able to log in. :)

---

### Post by Uncle Spellbinder on 2012-12-06
> **dnairb said:**
> [http://forums.linuxmint.com/viewtopic.php?f=47&t=118809&p=656166#p656112](http://forums.linuxmint.com/viewtopic.php?f=47&t=118809&p=656166#p656112) and be sure to change lucid-getdeb to your distro, e.g. quantal-getdeb, etc.

Excellent! Worked perfectly. I commented out the 'proper' getdeb repo and added the mirror:

```
#### GetDeb - http://www.getdeb.net
## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
# deb http://archive.getdeb.net/ubuntu quantal-getdeb apps

#### GetDeb - MIRROR for http://www.getdeb.net
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A8A515F046D7E7CF
deb http://mirrors.dotsrc.org/getdeb/ubuntu quantal-getdeb apps
```

---

### Post by gandalf3 on 2012-12-11
it's still down for me.. have they said when they're going to be back up?

EDIT: the mirror worked though, thanks :)

---

### Post by Taigen on 2012-12-13
noobie question, I need the deb mirror and the deb-src mirror right?

---

### Post by Primefalcon on 2012-12-13
> **Taigen said:**
> noobie question, I need the deb mirror and the deb-src mirror right?
you don't really need the src... that for the source code, and unless you want to inspect the code... or compile from source.... which tbh if I am going to compile from source I usually download the app directly from sourceforge or the programs specific site anyhow... but thats personal preference

---

### Post by monkeybrain2012 on 2012-12-13
Actually the src is automatically installed if you just paste the first line.

Thanks for the hint, the mirror works.

---

### Post by zonah on 2012-12-14
According to blog.getdeb.net it's down due to some sort of power failure. They usually post some sort of info about downtime in their blog!:smile:

---

### Post by DeadlyOats on 2012-12-15
I was just at the [[COLOR="Red"]blog[/COLOR]]("http://blog.getdeb.net/").  It was a power outage WITH hardware failure.  Maybe they need help with new hardware, or is it just taking a long time to set up new servers and configuring them and recovering the data from the old servers?  The trouble is that post was on 9 Dec.  It's 15 Dec, and no updates on the blog...  Anyone here have any insight on what's happening?

---

### Post by MadmanRB on 2012-12-19
There needs to be more then one mirror for this, getdeb is very vital

---

### Post by persiano on 2012-12-26
No news about GetDeb?

today ...
"
W:Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg)  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-i386/Packages](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-i386/Packages)  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en)  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-it](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-it)  Unable to connect to archive.getdeb.net:http:
, E:Some index files failed to download. They have been ignored, or old ones used instead.
"

---

### Post by Harsh Kumar Narula on 2012-12-26
Its Still Down.. I am removing it from my sources.list

---

### Post by TBeholder on 2012-12-28
...and again. :mad:

Did anyone here deal with this mirror at **mirrors.dotsrc.org** and can comment?
[http://www.webupd8.org/2010/05/getdeb-playdeb-repositories-down-what.html](http://www.webupd8.org/2010/05/getdeb-playdeb-repositories-down-what.html)

---

### Post by pqwoerituytrueiwoq on 2012-12-28
```
~$ cat /etc/apt/sources.list | grep getdeb
# deb http://archive.getdeb.net/ubuntu quantal-getdeb games apps
# deb-src http://archive.getdeb.net/ubuntu quantal-getdeb games apps
deb http://mirrors.dotsrc.org/getdeb/ubuntu quantal-getdeb games apps
deb-src http://mirrors.dotsrc.org/getdeb/ubuntu quantal-getdeb games apps
```
just added the last 2 lines and it worked, did not add a key as i had it before the site was down

---

### Post by zombifier25 on 2012-12-30
It's only a mirror though, so still no updates. It's time the getdeb guys use the mirror as the real repo.

---

### Post by pqwoerituytrueiwoq on 2012-12-30
```
if [ $(ping archive.getdeb.net -c 1 | grep "1 received" | wc -l) -eq 1 ];then notify-send --icon info GetDeb.net 'It is BACK!!!';fi
```
maybe we should use a cronjob that runs that every 3 hours or so, so we will know when it is back

---

### Post by cthlhu1987 on 2013-01-02
Awwwww, man, that blows, hope they'll be up fast.

---

### Post by MadmanRB on 2013-01-09
Its been almost two months now, I think its safe to say that Getdeb is done for, there has been no news or updates.
Maybe there should be a replacement now?

---

### Post by pqwoerituytrueiwoq on 2013-01-09
[IMG]http://i.imgur.com/HUUPp.jpg[/IMG]

---

### Post by owinoc on 2013-01-17
could this be reason for below error msg?

"Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources."

---

### Post by gandalf3 on 2013-01-22
> could this be reason for below error msg?

"Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources."i doubt it..
what are you trying to install/update?

>                                                                              [IMG]http://i.imgur.com/HUUPp.jpg[/IMG]
lol, nice!
EDIT: I'm curious, what program did you use?

on they&#8217;re [blog]("http://www.blogger.com/comment.g?blogID=2595167294312025647&postID=2685605913266961432") there's a post that says this..

> 
GetDeb and PlayDeb discontinue

After  the server crash where also the GetDeb and PlayDeb database was lost  and given the fact that GetDeb and PlayDeb now have too many packages to  be handled as a one-man-project I decided to discontinue GetDeb and  PlayDeb.
In the last years I have spent so many hours in the project that now it is just too much for me to maintain beside my usual job.

But  this does not mean that all the work in GetDeb and PlayDeb is lost. The  repository is still completely mirrored, e.g.:  [http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/pool/](http://mirror.informatik.uni-mannheim.de/pub/mirrors/getdeb/ubuntu/pool/)  (Google search: 'quantal-getdeb-testing intitle:"Index of"' should give  you a good list).
Also all the package script (i.e. the debian  directory) for every package in the precise and quantal repository are  available in my GitHub repositories:
* [https://github.com/ckorn/GetDeb](https://github.com/ckorn/GetDeb)
* [https://github.com/ckorn/PlayDeb](https://github.com/ckorn/PlayDeb)
* For special upstream watchers there is this repository: [https://github.com/ckorn/Upstream-watchers](https://github.com/ckorn/Upstream-watchers)

The  web interface of both GetDeb and PlayDeb is called apt-portal which is  specialised for viewing the information in an apt repository:
* [https://code.launchpad.net/apt-portal](https://code.launchpad.net/apt-portal)

And finally there are the scripts and little helpers of the automated build process:
* [https://code.launchpad.net/debfactory](https://code.launchpad.net/debfactory)

The entire repository of Debian packages can be downloaded with this script:
* [http://pastebin.com/raw.php?i=JaVkvFFZ](http://pastebin.com/raw.php?i=JaVkvFFZ)

It  is currently 84GiB in size so please only download it if you really  want all the packages. If you just want some simply use a mirror.

Let  me also thank everybody of you for the trust you had in GetDeb and  PlayDeb as an unofficial repository. I think GetDeb and PlayDeb were one  of the greatest unofficial repositories for Ubuntu packages.
I think to spend some time to bring some of the packages in the official repository.

Thank you and bye!
--
Thats all Folks. GetDeb & PlayDeb are dead for now.  January 19, 2013 at 4:56 AM
 this sucks..   :cry:

---

### Post by cthlhu1987 on 2013-01-22
> **gandalf3 said:**
> [...]lol, nice!
EDIT: I'm curious, what program did you use?[...]
There's a ton of grave stone image generators, just pick one and have fun :)

---

### Post by pqwoerituytrueiwoq on 2013-01-22
> **gandalf3 said:**
> i doubt it..
what are you trying to install/update?

lol, nice!
EDIT: I'm curious, what program did you use?

on they&#8217;re [blog]("http://www.blogger.com/comment.g?blogID=2595167294312025647&postID=2685605913266961432") there's a post that says this..

this sucks..   :cry:
crap i posed in the wrong thread last time...
[http://ubuntuforums.org/showthread.php?p=12463251#post12463251](http://ubuntuforums.org/showthread.php?p=12463251#post12463251)
i finally get news before someone else did here and look how i messed that up...
used this to make that
[http://www.jjchandler.com/tombstone/](http://www.jjchandler.com/tombstone/)

---

### Post by MadmanRB on 2013-01-23
Man it sucks that getdeb went down as it was not a community project but a personal one.
Of course this is the flaw with ppa's once the maintainer goes down so goes the whole thing and many packages are lost frever.
Or just mirrored on a far less accessible website.

---

### Post by Artemis3 on 2013-01-23
If Ubuntu moves into a rolling release model, as suggested by Canonical's Kernel Team Manager, it might not be needed anymore...

[http://www.youtube.com/watch?v=AQvOIExkCaw](http://www.youtube.com/watch?v=AQvOIExkCaw) (minute 42)

---

### Post by MadmanRB on 2013-01-23
Yes but get deb did provide a lot of packages that were not in the main repositiories and if you dont have a lot of ppa's enabled it would never make up for the loss.
So for now we have mirrors until maybe more people contribute to what used to be getdeb.

---

### Post by Primefalcon on 2013-01-24
gone for good
[https://plus.google.com/u/0/110683567928974511220/posts/FF1gRuZN7pM](https://plus.google.com/u/0/110683567928974511220/posts/FF1gRuZN7pM)

---

### Post by MadmanRB on 2013-01-24
Yes and a damned shame, therevare many packages that were on getdeb that are not in the main repos.
I hope the mirror remains, or some ppa takes on some of the load.
I use gens-gs, vba-m, umplayer,and a few other apps that were on getdeb.
None of these are not in the main repos or in any single ppa's so I would need to load many ppa's to make up for the loss so I do hope the mirror remains or its all wine for me, as I really dont want to compile.

---

### Post by gandalf3 on 2013-02-12
it's back!!!!! :D :D
imagine my surprise when i got an update from getdeb in my morning updates...

here's some info.. [http://blog.getdeb.net/](http://blog.getdeb.net/)

EDIT:

now it's down again??

---

### Post by MasterNetra on 2013-02-12
> **gandalf3 said:**
> it's back!!!!! :D :D
imagine my surprise when i got an update from getdeb in my morning updates...

here's some info.. [http://blog.getdeb.net/](http://blog.getdeb.net/)

EDIT:

now it's down again??

Yea looks it, down for me too, well the website seems to be, the repos seem to be fine?

---

### Post by gandalf3 on 2013-02-13
the website is back up again, i guess the were doing some maintenance?

---

### Post by zombifier25 on 2013-02-13
Perfect. Let's hope something like this never happens again.
Now start handing me the games.

---

