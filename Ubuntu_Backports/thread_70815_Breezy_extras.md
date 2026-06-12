---
title: "Breezy extras?"
date: 2005-10-01
forum: Ubuntu Backports
---

### Post by ricardo on 2005-10-01
I've noticed that breezy-extras dirs are empty in the servers.

When will have breezy-extras working?

Thanks.

---

### Post by DJ_Max on 2005-10-01
[QUOTE=ricardo]I've noticed that breezy-extras dirs are empty in the servers.

When will have breezy-extras working?

Thanks.[/QUOTE]
[http://ubuntuforums.org/showpost.php?p=372181&postcount=5](http://ubuntuforums.org/showpost.php?p=372181&postcount=5)

---

### Post by ricardo on 2005-10-02
[QUOTE=DJ_Max][http://ubuntuforums.org/showpost.php?p=372181&postcount=5](http://ubuntuforums.org/showpost.php?p=372181&postcount=5)[/QUOTE]

I say breezy-extras, not breezy-backports.

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=ricardo]I've noticed that breezy-extras dirs are empty in the servers.
When will have breezy-extras working?
Thanks.[/QUOTE]


Are you asking for w32codecs and such? We might never have those again. The backport team got a legal warning for that stuff, so unless you know a free server in France or whatever that wants to play along, we might be stuck using semi-incompatible Debian repos.

---

### Post by ubuntu_demon on 2005-10-05
[QUOTE=poofyhairguy]Are you asking for w32codecs and such? We might never have those again. The backport team got a legal warning for that stuff, so unless you know a free server in France or whatever that wants to play along, we might be stuck using semi-incompatible Debian repos.[/QUOTE]


A lot of normal users really need w32codecs.

w32codecs is in this repo :
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) hoary main

poofy are there any additional repos you recommend ?

---

### Post by dasunst3r on 2005-10-06
I don't think you will have to resort to old repositories for this.  The codecs are available on the MPlayer web site, at [http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

Just extract the contents to /usr/lib/win32 (switch to root and/or make the directories as needed) :)

---

### Post by bugi on 2005-10-06
[QUOTE=dasunst3r]Just extract the contents to /usr/lib/win32 (switch to root and/or make the directories as needed) :)[/QUOTE]

There is not root ;-)
Just ```
sudo mkdir /usr/lib/win32
``` and copy all codecs to this folder :-)

---

### Post by poofyhairguy on 2005-10-06
[QUOTE=ubuntu_demon]A lot of normal users really need w32codecs.

w32codecs is in this repo :
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) hoary main

poofy are there any additional repos you recommend ?[/QUOTE]


Nope. Thats all we have for now. Sad to see thing go backwards.

---

### Post by jdong on 2005-10-06
Breezy extras will be "launched" again when Breezy releases (or maybe a week after), since unfortunately the API is still bouncing around in Breezy :).

Breezy-extras "restricted" packages will be made to Gentoo-style (fetch from internet and extract from there), to allow us to distribute "restricted" software.

---

### Post by cowlip on 2005-10-06
[QUOTE=jdong]Breezy extras will be "launched" again when Breezy releases (or maybe a week after), since unfortunately the API is still bouncing around in Breezy :).

Breezy-extras "restricted" packages will be made to Gentoo-style (fetch from internet and extract from there), to allow us to distribute "restricted" software.[/QUOTE]
Interesting...thank you for keeping us updated

---

### Post by cowlip on 2005-10-06
[QUOTE=ubuntu_demon]A lot of normal users really need w32codecs.

w32codecs is in this repo :
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) hoary main

poofy are there any additional repos you recommend ?[/QUOTE]
Thanks too :):)

---

### Post by jdong on 2005-10-06
```

deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main restricted universe multiverse

```

w32codecs is syncing to breezy-extras-staging. This version fetches at install-time from mplayerhq.hu, making it perfectly OK for Backports Team to distribute :)


Java and other restricted packages are currently being worked on in the same fashion.

---

### Post by ubuntu_demon on 2005-10-07
[QUOTE=jdong]```

deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main restricted universe multiverse

```

w32codecs is syncing to breezy-extras-staging. This version fetches at install-time from mplayerhq.hu, making it perfectly OK for Backports Team to distribute :)


Java and other restricted packages are currently being worked on in the same fashion.[/QUOTE]
so you are recommending : use that breezy-extras-staging repo until 1 week after breezy releases and then switch to official breezy-extras ?

---

### Post by jdong on 2005-10-07
I am recommending to the impatient to use the staging repository. For those who don't get twitchy without extras for a few weeks, just wait for a while!

---

### Post by ubuntu_demon on 2005-10-07
[QUOTE=jdong]I am recommending to the impatient to use the staging repository. For those who don't get twitchy without extras for a few weeks, just wait for a while![/QUOTE]
yeah ofcourse we shouldn't recommend breezy to anyone except the impatient for now :)

---

### Post by wirjo on 2005-10-09
Lol, Breezy is going to be out in a week... I will save me the trouble by getting breezy when it's actually released :D

---

### Post by Kyral on 2005-10-09
Nice move jdong with getting around the legal trouble. You don't know how awkward it is to say stuff like "Umm...we can't give you that....because of some stupid legal crap..." to people.

BTW will you need any help with Backporting stuff from Dapper in a while? 'cause I'm eager to get package building experiance

---

### Post by chiefofthejojos on 2005-10-10
[QUOTE=jdong]```

deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main restricted universe multiverse

```

w32codecs is syncing to breezy-extras-staging. This version fetches at install-time from mplayerhq.hu, making it perfectly OK for Backports Team to distribute :)


Java and other restricted packages are currently being worked on in the same fashion.[/QUOTE]

Very nice work.  I like how it works.  In order to be completely safe, however, should the installation display the license agreement and force the user to accept before continuing?

---

### Post by jdong on 2005-10-10
I'm going by what Gentoo does -- Gentoo's been distributing w32codecs this way for quite a while. However, Java will require a license agreement and manually fetched downloads, so I'm still working on how that'll play out.

---

### Post by laltopi on 2005-10-14
[QUOTE=ubuntu_demon]yeah ofcourse we shouldn't recommend breezy to anyone except the impatient for now :)[/QUOTE]

Are the extras available now that Breezy has been released? the extras-staging has w32codecs but extras is empty

---

### Post by dare2dreamer on 2005-10-15
will FreeNX make it into the breezy-extras?

---

### Post by jdong on 2005-10-15
Currently we're moving the master server.... once it comes back, w32codecs will make it into extras.

Then, I'm going to attempt a FreeNX build for Extras-staging.

---

### Post by Limulus on 2005-10-17
Will Boinc! (boinc-client and boinc-manager) get moved into extras from
[http://pkg-boinc.alioth.debian.org/binary/](http://pkg-boinc.alioth.debian.org/binary/)

Its funny because kboincspy is in Breezy, but boinc-client (needed to actually do anything) isn't ^_-

---

### Post by jdong on 2005-10-17
I'm inspecting the quality of that package right now -- but it stands a great chance.

---

### Post by mrfrost on 2005-10-22
[QUOTE=jdong]I'm inspecting the quality of that package right now -- but it stands a great chance.[/QUOTE]

Hi,
I am one of the maintainer of the BOINC packages and would encourage you to send in patches etc. if you modify our packages for breezy-extras. I am open for every suggestion!

Thanks,
Frank S. Thomas

---

### Post by mazirian on 2005-10-22
Thanks for the win32codecs deb in this repo:
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main restricted universe multiverse

In order to make the deb work for me as of the date of this post, I had to edit the preinst control file and change "www1" to "www2".  Apparently www1.mplayerhq.hu is down.

---

### Post by jdong on 2005-10-22
[QUOTE=mazirian]Thanks for the win32codecs deb in this repo:
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main restricted universe multiverse

In order to make the deb work for me as of the date of this post, I had to edit the preinst control file and change "www1" to "www2".  Apparently www1.mplayerhq.hu is down.[/QUOTE]

Yep, noticed that....

---

### Post by jimix on 2005-10-23
> Thanks for the win32codecs deb in this repo:
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main restricted universe multiverse

In order to make the deb work for me as of the date of this post, I had to edit the preinst control file and change "www1" to "www2". Apparently www1.mplayerhq.hu is down.
I had to edit w32codecs.postinst, for what its worth.  Also, if you are a dummy like me you should probably know that the file is located in /var/lib/dpkg/info

---

### Post by tikal26 on 2005-10-25
Hey:
how do you get breezy extras not staging?

How do you changed www1 to www2?

---

### Post by duffman25 on 2005-10-25
There's a folder called contrib in [http://ubuntu-backports.mirrormax.net/dists/breezy-extras/contrib/](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/contrib/)

is this part of the breezy-extras? What does it have?

---

### Post by sneax on 2005-10-25
I came here by search. My question is:
Which repositries do I have to use in order to install w32codecs and libdvd using synaptic?

Also, I downloaded a package from mplayer's site - I think they are the codecs but where do I put them? The readme gives some info, but I want to be sure they are available to all players installed (system wide)?!

---

### Post by Jenda on 2005-10-30
Ohh... This place died.

Sneax: [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) debian sarge
BE SURE TO REMOVE OR COMMENT OUT BEFORE YOU APT-GET UPGRADE!!!

Any news on the extras?

---

### Post by asimon on 2005-10-30
[QUOTE=jimix]I had to edit w32codecs.postinst, for what its worth.  Also, if you are a dummy like me you should probably know that the file is located in /var/lib/dpkg/info[/QUOTE]

This problem is quite old and still unfixed. Is it possible to upload a fixed package?

The most simple fix is:
```

sed -e s/www1/www4/g -i /var/lib/dpkg/info/w32codecs.postinst

```

Thanks.

---

### Post by sciurus on 2005-10-31
How long until we can expect a working, fully-stocked breezy extras?

---

### Post by ricardo on 2005-11-08
[QUOTE=sciurus]How long until we can expect a working, fully-stocked breezy extras?[/QUOTE]

I ask the same question.

---

### Post by stubby on 2005-11-08
I guess whenever whoever is in charge gets off their arse.

Doesn't look like anytime soon though

---

### Post by Jenda on 2005-11-08
And who might that be?

---

### Post by imagine on 2005-11-08
I don't know what happened to extras. It went to down from around 50 packages to 1 (broken) package and then it became silent, ie nothing happened anymore.

You may want to have a look at PLF. It contains packages which cannot be included into the official Ubuntu repositories for legal reasons, so it's much like extras was. Only five packages are marked stable at the moment, but according to the wiki page and mailing list there are lots of things going on.

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by jdong on 2005-11-08
What kind of packages do we want to see in Extras? Currently, these would probably be "debian-marillat" clones, which need quite a substantial development effort to make sort-of-legal wrapper packages. I am not willing to expose myself to legal trouble in order to keep Extras up.


Currently, FreeNX 0.4.x packages are under final stages of testing, and are almost ready to be pushed out to the -staging branch.


Acrobat Reader, implementations of Java, etc are all in Multiverse now, so packages in Hoary-extras no longer apply to Breezy.

---

### Post by jdong on 2005-11-08
As far as restricted media formats, I **recommend people to check out PLF** for Ubuntu, as linked above. Understand that I do not wish to put my future at stake for providing these packages.... I'm sorry.

---

### Post by imagine on 2005-11-08
You don't have to be sorry, that's what PLF was created for.
But nice to see you back in "your" forum : )

---

### Post by jdong on 2005-11-08
Sorry about that, too... College applying season is a busy time :)

---

### Post by sander marechal on 2005-11-08
Hint: Create a new sticky with the info about breezy extra's, breezy backports and the non-free breezy packages at PLF. Close the sticky (so no-one can reply) and *unsticky all the incorrect and old outdated stickes that confuse the hell out of anyone that wants to simply play DVD's and view WMV's*.

Took me hours and hours and hours to find what I needed in all the crud that's been slowly accumulating in this place.

---

### Post by jdong on 2005-11-08
Done.

Also, I'm working on a Wiki-ish setup.

---

### Post by ubuntu_demon on 2005-11-08
[QUOTE=jdong]Done.

Also, I'm working on a Wiki-ish setup.[/QUOTE]
Nice sticky. Very clear!

What kind of wiki-ish setup are you talking about ?

Did you know about this wiki-ish project of King Bahamut : [http://doc.gwos.org/index.php/BreezyCust](http://doc.gwos.org/index.php/BreezyCust)

---

### Post by jasay on 2005-11-08
Nice work jdong.  Much clearer.

---

### Post by jdong on 2005-11-08
ubuntu-demon: A long time back ( 10 months or so), Seb Payne created a Mediawiki homepage for Backports. At that time, I felt that I was able to keep the info fresh enough that such a dynamic site would not be necessary. However, times have changed :).


Yes, I know about the King's documentation collection, I just want to overhaul the ubuntubackports.org site... Right now it's simply pathetic.

---

### Post by ubuntu_demon on 2005-11-08
[QUOTE=jdong]ubuntu-demon: A long time back ( 10 months or so), Seb Payne created a Mediawiki homepage for Backports. At that time, I felt that I was able to keep the info fresh enough that such a dynamic site would not be necessary. However, times have changed :).


Yes, I know about the King's documentation collection, I just want to overhaul the ubuntubackports.org site... Right now it's simply pathetic.[/QUOTE]
ok
yeah maybe a wiki for the backports site is a good idea :)

---

### Post by stubby on 2005-11-09
Good to know that something is being done about backports, and to know where backports stands in relation to everything.

It's been tragic seeing how everything went to the dog house these few weeks

---

### Post by sander marechal on 2005-11-09
[QUOTE=jdong]Done.

Also, I'm working on a Wiki-ish setup.[/QUOTE]

Thanks heaps. That should save other people like me a lot of time searching :)

--
Sander

---

### Post by macleod199 on 2005-11-11
[QUOTE=jdong]What kind of packages do we want to see in Extras? Currently, these would probably be "debian-marillat" clones, which need quite a substantial development effort to make sort-of-legal wrapper packages. I am not willing to expose myself to legal trouble in order to keep Extras up.


Currently, FreeNX 0.4.x packages are under final stages of testing, and are almost ready to be pushed out to the -staging branch.


Acrobat Reader, implementations of Java, etc are all in Multiverse now, so packages in Hoary-extras no longer apply to Breezy.[/QUOTE]

What about stuff like Azureus? I never understood why it couldn't be packaged legally. And is the realplayer in multiverse still 2 major version numbers behind?

---

### Post by jdong on 2005-11-11
[QUOTE=macleod199]What about stuff like Azureus? I never understood why it couldn't be packaged legally. 
[/quote]
Sure, Azureus is fine for packaging, but you're gonna have to provide your own JRE manually before the package works.... Just the way Debian does it (contributed uploads) will NOT work under Ubuntu.

> 
And is the realplayer in multiverse still 2 major version numbers behind?
I don't maintain that, and the maintainer doesn't use the forums, like most of the other devs (sadly). You're gonna have to go to #ubuntu-devel or #ubuntu-motu and ask.

---

### Post by brian g on 2005-11-12
is this the proper thread to ask for [gaim-rhythmbox]("http://gaim-rhythmbox.sourceforge.net/") to be added someplace so i can install it via synaptic? :confused:

wasn't sure if "extras" were to go under "Ubuntu Backports > Requests"

---

### Post by jdong on 2005-11-12
Start a new thread under the Requests subforum. Note that it'll still be a while before I can get to Extras submissions...

---

### Post by macleod199 on 2005-11-12
[QUOTE=jdong]Sure, Azureus is fine for packaging, but you're gonna have to provide your own JRE manually before the package works.... Just the way Debian does it (contributed uploads) will NOT work under Ubuntu.
[/QUOTE]

Yeah, I re-remembered the JRE 1.5 thing a few minutes after I posted this. Such a pain because it's such a popular program.

---

