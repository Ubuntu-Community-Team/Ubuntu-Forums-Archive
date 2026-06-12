---
title: "New Backports Mirror"
date: 2005-07-04
forum: Ubuntu Backports
---

### Post by Mez on 2005-07-04
I'm pleased to announce the launch of a new Backports Mirror!

[http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/)

Kindly provided by Brian Puccio !

---

### Post by TravisNewman on 2005-07-04
stickied, at your request :)

---

### Post by Rory on 2005-07-05
Thank you!!!

---

### Post by Xian on 2005-07-05
[QUOTE=Mez]Kindly provided by Brian Puccio ![/QUOTE]
Thank you, Brian! :)

---

### Post by Zhyntil on 2005-07-09
I know this is a stupid question (I am new at using apt-get and SPM), but how do we add this to the repository list in synaptic package manager or into apt-get, I can click the link and see it is live, but it says:

> The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

I know I am messing up something in the address or the index location, but am not sure what it is.

 :?

---

### Post by ubuntu_demon on 2005-07-09
thnx brian!

---

### Post by jcohen on 2005-07-09
If you want to use this mirror, add these lines to your /etc/apt/sources.list

sudo gedit /etc/apt/sources.list


deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-backports main universe multiverse restricted

deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-extras main universe multiverse restricted

---

### Post by mohaham on 2005-07-09
thnx Brian

---

### Post by Brian Puccio on 2005-07-09
No problem, things may not be uber-fast the next few days as I'm shuffling data around to a new server with a larger harddrive, but things should still work 100%

Glad I could give back, once things are done, I should have an Ubuntu mirror as well complete (right now its only x86 binary only)

---

### Post by btdown on 2005-07-16
Repo no working above...

---

### Post by humdinger70 on 2005-07-16
Mirrormax still down as of today (July 16). Used Brian's and they're working.

---

### Post by XDevHald on 2005-07-16
[QUOTE=btdown]When I add the above repo address to my sources.list, it doesnt find it.[/QUOTE]
 It'll be touched in the next couple of hours when it's reported.

---

### Post by btdown on 2005-07-16
ah ok...I was getting 404 errors and thought I had the repo link wrong. Thanks.

---

### Post by ShaneAu on 2005-07-17
[QUOTE=humdinger70]Mirrormax still down as of today (July 16). Used Brian's and they're working.[/QUOTE]
 Really? Seems fine for me... :). And the thousands of others using it each day. Somethings up there. Could you please do this command in shell:
```

host ubuntu-backports.mirrormax.net

```

You should get either 66.90.101.204 or 70.84.217.98. Currently it's setup for 66.90.101.204 to take the entire load because 70.84.217.98 was munching up it's bandwidth too fast.

66.90.101.204 is kind of slower but can use more overall bandwidth, 70.84.217.98 will back in the mix soon (that is super fast).

Gone over 100,000 unique users so far this month.   :roll:. About 3 TB bandwidth used.

I only have stats on one server so have to kind of guess the other server (just double the server with the stats because it's 50/50 of the load across them).

Donations are welcome - [http://mirrormax.net/](http://mirrormax.net/). :p.

---

### Post by humdinger70 on 2005-07-18
[QUOTE=ShaneAu]Really? Seems fine for me... :). And the thousands of others using it each day. Somethings up there. Could you please do this command in shell:
```

host ubuntu-backports.mirrormax.net

```

You should get either 66.90.101.204 or 70.84.217.98. Currently it's setup for 66.90.101.204 to take the entire load because 70.84.217.98 was munching up it's bandwidth too fast.

66.90.101.204 is kind of slower but can use more overall bandwidth, 70.84.217.98 will back in the mix soon (that is super fast).

Gone over 100,000 unique users so far this month.   :roll:. About 3 TB bandwidth used.

I only have stats on one server so have to kind of guess the other server (just double the server with the stats because it's 50/50 of the load across them).

Donations are welcome - [http://mirrormax.net/](http://mirrormax.net/). :p.[/QUOTE]

I was getting a lot of "connection refused" messages on the mirrormax site during "sudo apt-get update", which is why I switched my sources.list file to Brian's.  I will try the mirrormax site again the next time I try an update.

---

### Post by darkaudit on 2005-07-21
hmm... tried both mirrormax and Brian's, and everything from the main backports repo is showing local or obsolete as of 10pm EDT Thurs..

---

### Post by abandoned_hussam on 2005-07-22
[QUOTE=darkaudit]hmm... tried both mirrormax and Brian's, and everything from the main backports repo is showing local or obsolete as of 10pm EDT Thurs..[/QUOTE]
 same here, a lot of packages have been removed.

---

### Post by darkaudit on 2005-07-22
According to ShaneAu, the Packages.bz2 file is missing from the main server. The server he can't fix. :(

Thanks for the info anyway, Shane. We appreciate it.

---

### Post by ShaneAu on 2005-07-22
[QUOTE=darkaudit]According to ShaneAu, the Packages.bz2 file is missing from the main server. The server he can't fix. :(

Thanks for the info anyway, Shane. We appreciate it.[/QUOTE]
 But I never said it was the cause of this, the .bz2 file has always been missing, but I think apt likes to check both .bz2 and .gz.

But yes, I can't do anything to fix the current problem. :(. Since it's happening on all (?) mirrors, it HAS to be a problem with the main server we all sync with.

---

### Post by ericsp on 2005-09-02
[QUOTE=btdown]Repo no working above...[/QUOTE]
 What happened with the msttfonts in backport?

---

### Post by Simon Bridge on 2005-10-10
[QUOTE=ShaneAu]Really? Seems fine for me... :). And the thousands of others using it each day. Somethings up there. Could you please do this command in shell:
```

host ubuntu-backports.mirrormax.net

```

You should get either 66.90.101.204 or 70.84.217.98. Currently it's setup for 66.90.101.204 to take the entire load because 70.84.217.98 was munching up it's bandwidth too fast.

66.90.101.204 is kind of slower but can use more overall bandwidth, 70.84.217.98 will back in the mix soon (that is super fast).

Gone over 100,000 unique users so far this month.   :roll:. About 3 TB bandwidth used.

I only have stats on one server so have to kind of guess the other server (just double the server with the stats because it's 50/50 of the load across them).

Donations are welcome - [http://mirrormax.net/](http://mirrormax.net/). :p.[/QUOTE]
I get:```
simon@infrared:~$ host ubuntu-backports.mirrormax.net
ubuntu-backports.mirrormax.net has address 70.84.217.98

``` Which, I guess, is why I get this kind of thing:
```
Synaptic Trouble:
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-l10n-en_1.1.3-8ubuntu2.3_all.deb
  Error reading from server. Remote end closed connection [IP: 82.211.81.151 80]
```

:???:

---

### Post by tomski on 2005-10-13
these have never worked for me so i gave up using them

---

### Post by Julian David Pitt on 2005-10-14
Can someone please tell me where I am going wrong from below cheers

Failed to fetch [http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/main/binary-i386/Packages.gz](http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/universe/binary-i386/Packages.gz](http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/restricted/binary-i386/Packages.gz)  404 Not Found

Thanks guys, and gals i guess

---

### Post by poofyhairguy on 2005-10-14
[QUOTE=Julian David Pitt]Can someone please tell me where I am going wrong from below cheers

Failed to fetch [http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/main/binary-i386/Packages.gz](http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/universe/binary-i386/Packages.gz](http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/hoary-backports/restricted/binary-i386/Packages.gz)  404 Not Found

Thanks guys, and gals i guess[/QUOTE]


I don't think this repo exists anymore.

---

### Post by glug101 on 2005-10-14
[QUOTE=poofyhairguy]I don't think this repo exists anymore.[/QUOTE]
ok, i am finally saying what I have thought a thousand times....

Isn't there someplace that we could point to in order to get a decent listing of major repositories?

I've looked all over and I can't find squat except for a few mentions in forums of sites, and half of those report not working in the next post I find.  I even keep seeing references to repositories that I do not have, and they way it's mentioned it sounds like the most basic thing.  

**Did I miss the memo?**

---

### Post by glug101 on 2005-10-14
P.S.  Could somebody remove the sticky from this is these repositories don't work?

(sorry if I sound crabby in my posts, had a long day and i don't mean it.  I'll get you a virtual beer if offended :) )

---

### Post by aysiu on 2005-10-14
Try following these instructions:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by glug101 on 2005-10-18
**bump**

(whisper)..if nobody can reach this repo, it should probably not be a sticky anymore.. (/whisper)

---

### Post by blastradius on 2005-10-20
Added to my /etc/apt/sources.list but doesn't seem to work!

I get:-

W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-backports/main Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubuntu...ts-repository_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-backports/universe Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubuntu...ts-repository_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubuntu...ts-repository_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-backports/restricted Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubuntu...ts-repository_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-extras/main Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubuntu...ts-repository_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-extras/universe Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubuntu...ts-repository_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubuntu...ts-repository_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://mirror.brianpuccio.net](http://mirror.brianpuccio.net) hoary-extras/restricted Packages (/var/lib/apt/lists/mirror.brianpuccio.net_ubuntu...ts-repository_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

when i start synaptic, and i get:-

[http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-backports/main/binary-i386/Packages.gz:](http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-backports/main/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-backports/universe/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-backports/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-extras/main/binary-i386/Packages.gz:](http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-extras/main/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-extras/universe/binary-i386/Packages.gz:](http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-extras/universe/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-extras/multiverse/binary-i386/Packages.gz:](http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-extras/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-extras/restricted/binary-i386/Packages.gz:](http://mirror.brianpuccio.net/ubuntu...ts-repository/dists/hoary-extras/restricted/binary-i386/Packages.gz:) 404 Not Found

when i try a reload.

I'm running Hoary.

---

### Post by stubby on 2005-10-20
how hard is it to remove this from being a sticky ?

---

### Post by hafuch on 2005-10-29
Thanks a million, Brian!!

---

