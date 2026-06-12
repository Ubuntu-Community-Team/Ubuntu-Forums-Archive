---
title: "UPDATED *** 5/30/2005 - Please Read This Regarding Backports ***"
date: 2005-05-27
forum: Ubuntu Backports
---

### Post by ubuntu-geek on 2005-05-27
Hello Everyone,

We ask that you update your sources.list and take out backports.ubuntuforums as your main repo and use one of the mirrors.

We are currently looking for another server that will better suit the needs of the main backports repo but until then everyone **NEEDS TO USE A MIRROR** otherwise we will run out of bandwidth to keep the mirrors synced.

[color=Red][b]5/30/2005 - UPDATES
[/b][color=Black]
Thanks for the kind donations of many of our users we were able to get a server with more bandwidth. This server will act as the main hub for mirrors and will not provide a direct repo for end users.

Why? We need to maintain a fair amount of available bandwidth on this server so the mirrors can update fast, if we opened the main server for public use the 10mbit connection would be maxed out within a few hours.
[/color][/color]
Users can choose from one of the follow mirrors.. Thanks again for supporting the backports project. If we can get enough donations to get a 2nd server we will and open that to the repo for public use. As of today we need $300 more in order to get that second server.

Mirrors are as follows:

1. [ftp://ftp2.caliu.info/backports/]("ftp://ftp2.caliu.info/backports/") - **Spain**
 2. [http://public.planetmirror.com/pub/ubuntu-backports/]("http://public.planetmirror.com/pub/ubuntu-backports/") - **Brisbane, Queensland, Australia**
 3. [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") - **Dallas, Texas, USA**

---

### Post by jdong on 2005-05-27
To make it more clear, accessing backports.ubuntuforums.org will result in a **FORBIDDEN** error.

---

### Post by bored2k on 2005-05-27
[QUOTE=jdong]To make it more clear, accessing backports.ubuntuforums.org will result in a **FORBIDDEN** error.[/QUOTE]
 I got package does not exist trying out mirrormax mirror. :?

---

### Post by jdong on 2005-05-27
Strange, that's the mirror I use.

```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

```

---

### Post by bored2k on 2005-05-27
[QUOTE=jdong]Strange, that's the mirror I use.

```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

```[/QUOTE]
 Looks like I made a mistake in sources.list because it now works :D

---

### Post by ShaneAu on 2005-05-29
I'm getting connection refused when trying to connect to [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/).

Apache down?  ](*,)

---

### Post by Markrian on 2005-05-29
[QUOTE=ShaneAu]I'm getting connection refused when trying to connect to [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/).

Apache down?  ](*,)[/QUOTE]

Ahem:[quote="jdong"]To make it more clear, accessing backports.ubuntuforums.org will result in a FORBIDDEN error.[/quote]

---

### Post by ShaneAu on 2005-05-29
[QUOTE=Markrian]Ahem:[/QUOTE]
 But I thought only the access would be forbidden to the archive via [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/), not the whole Ubuntu Backports site.

---

### Post by ubuntu-geek on 2005-05-29
Thanks for everyones kind donations we were able to purchase 6 months on a 10mbit unmetered server for the backports project.

Apache was taken down so the svn repo could be synced faster to the new server. The new server will NOT serve as a repo but as main rsync hub for the mirrors.

More details to follow as we get things moved..

---

### Post by ShaneAu on 2005-05-29
[QUOTE=ubuntu-geek]Thanks for everyones kind donations we were able to purchase 6 months on a 10mbit unmetered server for the backports project.

Apache was taken down so the svn repo could be synced faster to the new server. The new server will NOT serve as a repo but as main rsync hub for the mirrors.

More details to follow as we get things moved..[/QUOTE]

Sounds good! Was terribly slow syncing at a shared 3 Mbps before, haha.

So far my mirror (mirrormax) has only used 3.43 Gig. So it seems that barley anyone is using it yet.

What will happen with all the people using the main server now? They'll just get forbidden until they change to a mirror?

Or is that to be coverd in the "More details to follow as we get things moved.." part of your post. ;).

---

### Post by jiyuu0 on 2005-05-29
[QUOTE=ShaneAu]Sounds good! Was terribly slow syncing at a shared 3 Mbps before, haha.

So far my mirror (mirrormax) has only used 3.43 Gig. So it seems that barley anyone is using it yet.

What will happen with all the people using the main server now? They'll just get forbidden until they change to a mirror?

Or is that to be coverd in the "More details to follow as we get things moved.." part of your post. ;).[/QUOTE]

>So it seems that barley anyone is using it yet.
u ask for it... ;P

i've updated ubuntuguide.org sources.list to point to mirrormax

so expect lot's of bandwidth sucking soon :)

---

### Post by ShaneAu on 2005-05-29
[QUOTE=jiyuu0]>So it seems that barley anyone is using it yet.
u ask for it... ;P

i've updated ubuntuguide.org sources.list to point to mirrormax

so expect lot's of bandwidth sucking soon :)[/QUOTE]
 Excellent.... Bring it on! :p.

---

### Post by AlexandreP on 2005-05-30
I guess something utile would be to tell us were the servers are located, since we could pick up the one which is closest to our location :)

---

### Post by ShaneAu on 2005-05-30
[QUOTE=AlexandreP]I guess something utile would be to tell us were the servers are located, since we could pick up the one which is closest to our location :)[/QUOTE]
 1. [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) - **Spain**
2. [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) - **Brisbane, Queensland, Australia**
3. [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) - **Dallas, Texas, USA**

---

### Post by AlexandreP on 2005-05-30
Thanks :)

---

### Post by tcamargo on 2005-05-30
What about DNS round-robin?

---

### Post by oddabe19 on 2005-05-30
[QUOTE=tcamargo]What about DNS round-robin?[/QUOTE]
 i'm using mirror max, i still get the 403 error.

```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by jarrett.wold on 2005-05-30
[QUOTE=oddabe19]i'm using mirror max, i still get the 403 error.[/QUOTE]

I'm also getting a 403 off of mirrormax.  Apache config problems over there?

---

### Post by AndyAWS on 2005-05-30
[QUOTE=jarrett.wold]I'm also getting a 403 off of mirrormax.  Apache config problems over there?[/QUOTE]


Same here...

---

### Post by tzutolin on 2005-05-30
[QUOTE=AndyAWS]Same here...[/QUOTE]
 me too. it seems there is something going wrong with mirrormax !?

---

### Post by thechitowncubs on 2005-05-30
[QUOTE=tzutolin]me too. it seems there is something going wrong with mirrormax !?[/QUOTE]
 ditto

---

### Post by rabidninjawombat on 2005-05-31
Yep.  Me too.  getting 403 error, double checked sources.list everything appears to be right.

---

### Post by ShaneAu on 2005-05-31
[QUOTE=rabidninjawombat]Yep.  Me too.  getting 403 error, double checked sources.list everything appears to be right.[/QUOTE]
 Erm... *Checks it out*.

Edit: Haha, it mirrored the archives .htaccess :(. Which on the main server is to deny access so people use the mirrors, which was mirrored, so my mirror seems to have been denying access also, I'll disable mirroring of .htaccess files.

Sorry about that. :)

- Shane. 
(MirrorMAX)

---

### Post by tzutolin on 2005-05-31
[QUOTE=ShaneAu]Erm... *Checks it out*.

Edit: Haha, it mirrored the archives .htaccess :(. Which on the main server is to deny access so people use the mirrors, which was mirrored, so my mirror seems to have been denying access also, I'll disable mirroring of .htaccess files.

Sorry about that. :)

- Shane. 
(MirrorMAX)[/QUOTE]

It works now!! Thanks, Shane :)

---

### Post by jdong on 2005-05-31
LOL, that's just hilarious :) :) :)

We'll have to find a "better" way of blocking access!

---

### Post by ShaneAu on 2005-05-31
[QUOTE=jdong]LOL, that's just hilarious :) :) :)

We'll have to find a "better" way of blocking access![/QUOTE]
 chmod -r foo/ -R ? :D.

---

### Post by jdong on 2005-05-31
we're using username/password protection on /ubp/dists via httpd.conf now. We should be htaccess-free now.

---

### Post by kwennemar on 2005-06-01
Your suggestions to change my sources.list file worked great.  It also gave me a reason to do some house cleaning there too. :grin:

---

### Post by xbaez on 2005-06-01
this is my /etc/apt/sources.list

Failed     0 B     [http://blabla.com](http://blabla.com)     hoary-extras     Release.gpg

# deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted  
# deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted  
# deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted  
# deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted  
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted  
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports-staging main universe multiverse restricted  
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted  
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras-staging main universe multiverse restricted  
# deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports main universe multiverse restricted 
# deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports-staging main universe multiverse restricted 
# deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted 
# deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras-staging main universe multiverse restricted 

However, when I search for Gaim, it works (actually I'm downloading the latest Gaim version from [ftp://ftp.caliu.info](ftp://ftp.caliu.info).

So it seems there is a problem with the packages descriptions in ALL the backports repositories

---

### Post by adamcs on 2005-08-06
[COLOR=DimGray]The great work Ubuntu has done as well as the contributions of everyone else that made it so successful really helped me make that donation.   I've been on many platforms and never have I seen is works so well, easily, and successfully.[/COLOR]   :D

**[SIZE=2][COLOR=RoyalBlue]Keep up the great work, look for more contributions from me in the future....[/COLOR][/SIZE]**

---

### Post by madjimisimi on 2005-10-11
I am having problems with all the backports repos. I've tried all three mirrors, and have similar problems with all three.  Here are the messages I get at the end of apt-get update:
```
Failed to fetch ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch ftp://ftp2.caliu.info/backports/dists/hoary-backports/universe/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch ftp://ftp2.caliu.info/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch ftp://ftp2.caliu.info/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to open file.  '
Reading package lists... Done
W: Couldn't stat source package list ftp://ftp2.caliu.info hoary-backports/main Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp2.caliu.info hoary-backports/universe Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp2.caliu.info hoary-backports/multiverse Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp2.caliu.info hoary-backports/restricted Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp2.caliu.info hoary-backports/main Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp2.caliu.info hoary-backports/universe Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp2.caliu.info hoary-backports/multiverse Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp2.caliu.info hoary-backports/restricted Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Leif on 2005-10-12
**madjimisimi**, the unofficial hoary repos have been shut down. use 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

instead

---

### Post by madjimisimi on 2005-10-12
[QUOTE=Leif]**madjimisimi**, the unofficial hoary repos have been shut down. use 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

instead[/QUOTE]


Thanks a bunch!

---

### Post by tomski on 2005-10-13
[QUOTE=ShaneAu]1. [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) - **Spain**
2. [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) - **Brisbane, Queensland, Australia**
3. [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) - **Dallas, Texas, USA**[/QUOTE]


so what repo's do i use over here in england or do we not exist

i have been haveing major problems trying to get transcode and a few other apps but because i am using hoary i now cant get them due to repo's being changed  (why???)
 im seriusly confused as i use transcode a lot and ditched a kanotix install for this and since then have not been able to get the apps i need.
i have been told to use the above repo's  but they have never worked is this because they are for breezy or just that i live in uk ?????

i have also tried :
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

but yet again it does not contain transcode and the other apps i need
so i have been trying to compile from src and have hit multiple brickwalls and im on the edge of giving all this up.....

help help help

i dont want to go back to kanotix as i really like ubuntu but if i have to i will  

:confused:

---

### Post by dcstar on 2005-10-24
[QUOTE=tomski]so what repo's do i use over here in england or do we not exist
.......
i have also tried :
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted
.......
help help help

i dont want to go back to kanotix as i really like ubuntu but if i have to i will  

:confused:[/QUOTE]

The Mirror backports are for "Hoary-extras" packages, you get the main backports from:

[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

and, for your location, also put in:

[http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Hopefully that will give you full access to all the Hoary backports.

---

