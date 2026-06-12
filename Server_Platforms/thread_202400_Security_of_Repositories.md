---
title: "Security of Repositories"
date: 2006-06-23
forum: Server Platforms
---

### Post by Oceola on 2006-06-23
I noticed a change in the URLs for the US Repositories and the extention was .gov.
Not to let the cat out of the bag if their is one, were the repositories moved to US Government provided servers or is that a State indication. I wouldn't want any "government modified" packages on my computer. :confused:

---

### Post by aysiu on 2006-06-23
I've noticed no such thing. Where did your repositories list come from?

---

### Post by Oceola on 2006-06-23
The repositories show up in the Synaptics list, just like the normal repositories should. This is what is under edit and also in the resources.list
[http://us.archive.ubuntu.com/ubuntu/breezy-updates](http://us.archive.ubuntu.com/ubuntu/breezy-updates) main restricted (for example)
What occurs in watching iptraf on a reverse lookup is the following:
alpaca-ii.it.anl.gov.... for what is for the main restricted ubuntu updates and also for the backports.
I tried to track the original URL and it appeared to be Berkely in California.
This is what shows on the reverse look up every time, however the Security main is still Auckland. It is no longer the 82 or 85 starting url but this other thing.
If this is the way it's supposed to be fine if not let me know as my system must be borged.

 Edit:Below is the Copied Resources.list
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

##Major bug fix updates produced after the final release of the distribution
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse main restricted

# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse


#deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main
#deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) breezy main

---

### Post by Oceola on 2006-06-25
Sorry for the double post on this but since there wasn't an answer and things seemed to have changed a little. There appears to be a URL which is in my ISP's domain which appears to be the blocking and redirecting cause of this possible anomaly in the URL location for the US Repositories. It appears to be 141.157.242.9 which is identified with Net tools as:
Verizon Internet Services Inc. VIS-141-149 (NET-141-149-0-0-1) 
                                  141.149.0.0 - 141.158.255.255
Verizon Internet Services VZ-DSLDIAL-NYCMNY-14 (NET-141-157-192-0-1) 
                                  141.157.192.0 - 141.157.255.255
Reversal of the URL to 9.242.157.141 provides the following:
OrgName:    IBM Corporation 
OrgID:      IBMCOR-8
Address:    1311 Mamaroneck Ave.
City:       White Plains
StateProv:  NY
PostalCode: 10605
Country:    US

** If I block either URL I cannot gain access to the US Update or Main Repository**

It's as it is with no guessing, just a bunch of questions without answers at this point.:-k

---

### Post by RavenOfOdin on 2006-06-27
I'm getting that same connection now through a netstat and traceroute, and I'm updating my second comp to 6.06.

I could imagine IBM having valid reasons to or being in the position of hosting Linux servers.  If they're where the buck stops I wouldn't concern myself with it.

(EDIT: Maybe IBM is hosting the files, Verizon is their carrier and the Alpaca address is simply a mirror?)

(EDIT #2: Oceola, you can breathe easier on the Alpaca thing for two reasons:

#1. At least the address isn't "dod.gov" or "nsa.gov" :p 
#2. Even if it were, I don't think the US government wants your crappy little iMac to conduct DDOS attacks.  They most likely have far faster and more high-end systems at their disposal.)

---

### Post by Oceola on 2006-06-27
[QUOTE=RavenOfOdin]I'm getting that same connection now through a netstat and traceroute, and I'm updating my second comp to 6.06.[/quote]
I've ordered the Dapper discs and am looking forward to it.
[QUOTE=RavenOfOdin]I could imagine IBM having valid reasons to or being in the position of hosting Linux servers.  If they're where the buck stops I wouldn't concern myself with it.
(EDIT: Maybe IBM is hosting the files, Verizon is their carrier and the Alpaca address is simply a mirror?) [/quote]
I'm never against making a buck, as long as it's honest, just don't understand why blocking the one url stops access to the other url if the initial url was not shown in the log or tcp/udp screens prior to the access to the repository's URL

[QUOTE=RavenOfOdin](EDIT #2: Oceola, you can breathe easier on the Alpaca thing for two reasons:
#1. At least the address isn't "dod.gov" or "nsa.gov" :p 
#2. Even if it were, I don't think the US government wants your crappy little iMac to conduct DDOS attacks.  They most likely have far faster and more high-end systems at their disposal.)[/QUOTE]
I'm not concerned about anyone wanting my system, I salvaged it. I do get plenty of port 1026 hits and on occasions port#2 and 4 hits from DOD sites. They're not as bad as the annoying rascals coming from the Virginia  or Washington locations. I think most of those hits are due to some of the DOD ranges terminals having been zombied from spammers, unless the Army has digressed to spam for recruitment.

In these days of paranoid delusions from all sorts of directions my concern was over the change in the URL more than the .gov suffix, though if memory serves me there was some arguing over PGP back in the late 1980's when a few government agencies sought to have the developers modify it for snoop access by whatever non-descript agency needed it. I can't help having a good memory.
You and the rest of those Ravens in Arkansas stay happy. ;)

---

### Post by RavenOfOdin on 2006-06-27
[QUOTE=Oceola]
I'm never against making a buck, as long as it's honest, just don't understand why blocking the one url stops access to the other url if the initial url was not shown in the log or tcp/udp screens prior to the access to the repository's URL[/quote]

It could be a redirection issue somewhere down the line of computers.

[QUOTE=Oceola]
I do get plenty of port 1026 hits and on occasions port#2 and 4 hits from DOD sites.
[/quote]

messenger spam. . .Meh.
You'd think enough people would have disabled the "Messenger" service in their Windows services.msc file to make this outdated.

[QUOTE=Oceola]
 They're not as bad as the annoying rascals coming from the Virginia  or Washington locations. I think most of those hits are due to some of the DOD ranges terminals having been zombied from spammers, unless the Army has digressed to spam for recruitment.
[/quote]

I was wondering as to whether or not it should be a felony for Army computers to be hijacked in that fashion.

[QUOTE=Oceola]
 though if memory serves me there was some arguing over PGP back in the late 1980's when a few government agencies sought to have the developers modify it for snoop access by whatever non-descript agency needed it. I can't help having a good memory.[/quote]

Yeah, and the whole "Clipper" crypto issue after that.

[QUOTE=Oceola]
You and the rest of those Ravens in Arkansas stay happy. ;)[/QUOTE]

Sure thing. :) You too.

---

### Post by Oceola on 2006-06-28
I've been mulling this over and the following comes to mind...

Windows Messenger - supposedly removed or made inoperative  in XP but my guess is there's lots of Grannies unconcerned as long as the email works and MS has done it's usual best on a clean up.

Felony ??? - Misappropriation of Government  Property, Espionage or Treason. At least 10 years or a $10,000 fine. Consider the terminal which should be used for a government purpose engaged in an active military operation, the TIME needed to extrapolate the data causes a delay or a failure in the action, certainly indirect fifth column. Should the person be aware of the degradation and losses on the system most certainly treason unless on foreign soil then maybe an act of war or espionage again. I think the firing squad would be sufficient , could we add telemarketers since most of them are behind the spam as well.

I was out of the loop for the Clipper Crypto thing. :wink:

---

### Post by RavenOfOdin on 2006-06-28
[QUOTE=Oceola]
I was out of the loop for the Clipper Crypto thing. :wink:[/QUOTE]

That was where the government wanted strong (AES or so) encryption to only be available via military or judicial channels.

I can't find a link on it atm.

---

