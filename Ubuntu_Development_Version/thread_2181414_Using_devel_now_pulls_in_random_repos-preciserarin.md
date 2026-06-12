---
title: "Using /devel/ now pulls in random repos-/precise/raring/trusty"
date: 2013-10-17
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-10-17
I changed the sources.list on fully updated saucy:

```


$ sudo sed -i 's/saucy/devel/g' /etc/apt/sources.list

```

and got this :

```

...


Ign http://ca.archive.ubuntu.com devel-backports/universe Translation-en_CA    
Fetched 19.6 MB in 2min 2s (160 kB/s)                                          
W: Conflicting distribution: http://ca.archive.ubuntu.com devel Release (expected devel but got precise)
W: Conflicting distribution: http://ca.archive.ubuntu.com devel-updates Release (expected devel-updates but got precise)
W: Conflicting distribution: http://ca.archive.ubuntu.com devel-backports Release (expected devel-backports but got precise)
W: Conflicting distribution: http://security.ubuntu.com devel-security Release (expected devel-security but got precise)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/devel/main/source/Sources  404  Not Found

...

```

---

### Post by ventrical on 2013-10-17
I 

```


sudo apt-get dist-upgrade


```

and got this:

```

ventrical@ventrical-System-Product-Name:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ventrical@ventrical-System-Product-Name:~$ 

```

 so it's not downgrading or borking system.. at least for now.

---

### Post by cariboo on 2013-10-17
If you check the date on the repositories, you'll see that haven't been updated since 2012:

```
Index of /ubuntu/dists/devel

[ICO]	Name	Last modified	Size
[DIR]	Parent Directory	 	 -
[   ]	Contents-amd64.gz	26-Apr-2012 05:30	 21M
[   ]	Contents-i386.gz	26-Apr-2012 06:11	 21M
[   ]	Release	25-Apr-2012 22:49	 48K
[   ]	Release.gpg	25-Apr-2012 22:49	198
[DIR]	main/	05-Dec-2011 18:03	 -
[DIR]	multiverse/	14-Oct-2011 00:29	 -
[DIR]	restricted/	14-Oct-2011 00:29	 -
[DIR]	universe/	14-Oct-2011 00:29	 -
```

---

### Post by ventrical on 2013-10-17
> **cariboo907 said:**
> If you check the date on the repositories, you'll see that haven't been updated since 2012:

```
Index of /ubuntu/dists/devel

[ICO]    Name    Last modified    Size
[DIR]    Parent Directory          -
[   ]    Contents-amd64.gz    26-Apr-2012 05:30     21M
[   ]    Contents-i386.gz    26-Apr-2012 06:11     21M
[   ]    Release    25-Apr-2012 22:49     48K
[   ]    Release.gpg    25-Apr-2012 22:49    198
[DIR]    main/    05-Dec-2011 18:03     -
[DIR]    multiverse/    14-Oct-2011 00:29     -
[DIR]    restricted/    14-Oct-2011 00:29     -
[DIR]    universe/    14-Oct-2011 00:29     -
```


 I was just curious  because this method was deferring to the saucy repos by default  - but now , since release of saucy, the precise repos ? So I would assume then that  this method will not line up us with any *next* development release .

---

### Post by grahammechanical on 2013-10-18
It is 12.00 UTC here in England and I just logged in and run update and I did not get those errors. Just the usual two about the non-existing devel extras repositories. May be my server is a little bit behind your server. There has not been anything to update in the devel repositories, not yesterday or today. I would expect this if those repositories are to be used as parallel T-name repositories. I did see this yesterday. See Step 4

[https://wiki.ubuntu.com/Touch/Install](https://wiki.ubuntu.com/Touch/Install)

[COLOR=#333333][FONT=Ubuntu Beta]Note that there are other channels available:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta][TABLE]
[TR]
[TD]**channel**[/TD]
[TD]**description**[/TD]
[/TR]
[TR]
[TD]devel[/TD]
[TD]alias to current development channel (saucy)[/TD]
[/TR]
[TR]
[TD]devel-proposed[/TD]
[TD]alias to -proposed version of development channel (saucy-proposed)[/TD]
[/TR]
[TR]
[TD]devel-customized[/TD]
[TD]alias to -customized version of development channel (saucy-customized)[/TD]
[/TR]
[TR]
[TD]saucy[/TD]
[TD]latest development image which passed QA[/TD]
[/TR]
[TR]
[TD]saucy-proposed[/TD]
[TD]latest development image before QA[/TD]
[/TR]
[TR]
[TD]stable[/TD]
[TD]alias to current stable channel (saucy)[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
I do not understand all that is on that page.

Regards.

Edit: My thoughts. If devel is an alias to the current development channel then some time over the next few days it should become the alias to the T-name development channel. Perhaps someone is experimenting with getting this working and does not realise that there are nosy people like us around. May be the lack of a T code name is not helping.

---

### Post by zika on 2013-10-18
I'm somehow in the middle: I've got redirected to Raring... ;P
Random choice?

---

### Post by ventrical on 2013-10-18
> **zika said:**
> I'm somehow in the middle: I've got redirected to Raring... ;P
Random choice?


 Interesting.  I'm stumped at this point .. but will keep trying to see whats up with this.

---

### Post by ventrical on 2013-10-18
> **zika said:**
> I'm somehow in the middle: I've got redirected to Raring... ;P
Random choice?

I too now have raring...:) lol ... I'm not sure if it is random though.

---

### Post by ventrical on 2013-10-18
> **grahammechanical said:**
> It is 12.00 UTC here in England and I just logged in and run update and I did not get those errors. Just the usual two about the non-existing devel extras repositories. May be my server is a little bit behind your server. There has not been anything to update in the devel repositories, not yesterday or today. I would expect this if those repositories are to be used as parallel T-name repositories. I did see this yesterday. See Step 4

[https://wiki.ubuntu.com/Touch/Install](https://wiki.ubuntu.com/Touch/Install)

[COLOR=#333333][FONT=Ubuntu Beta]Note that there are other channels available:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta][TABLE]
[TR]
[TD]**channel**[/TD]
[TD]**description**[/TD]
[/TR]
[TR]
[TD]devel[/TD]
[TD]alias to current development channel (saucy)[/TD]
[/TR]
[TR]
[TD]devel-proposed[/TD]
[TD]alias to -proposed version of development channel (saucy-proposed)[/TD]
[/TR]
[TR]
[TD]devel-customized[/TD]
[TD]alias to -customized version of development channel (saucy-customized)[/TD]
[/TR]
[TR]
[TD]saucy[/TD]
[TD]latest development image which passed QA[/TD]
[/TR]
[TR]
[TD]saucy-proposed[/TD]
[TD]latest development image before QA[/TD]
[/TR]
[TR]
[TD]stable[/TD]
[TD]alias to current stable channel (saucy)[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
I do not understand all that is on that page.

Regards.

Edit: My thoughts. If devel is an alias to the current development channel then some time over the next few days it should become the alias to the T-name development channel. Perhaps someone is experimenting with getting this working and does not realise that there are nosy people like us around. May be the lack of a T code name is not helping.


  Oh gee .. I hope they don't name the next release .. 'Touchy Tarantula' :) lol being Holloween is just around the corner.

---

### Post by grahammechanical on 2013-10-18
I am now getting those error messages. Conflicting distributions.

devel-security got raring
devel got saucy
devel-updates got raring
devel-backports got raring.

I am moving more and more in favour of guessing that someone is experimenting and wants to see what apt-get reports. It at least shows that someone is at work and not relaxing on beach 13.10. :)

Regards.

---

### Post by ventrical on 2013-10-18
I dunno .... it's like  on the sea in the equatorial zone... it's called a 'dead calm' or doldrums .. (or both)  :) lol If I didn't have Overclcocking to do I'd get awfully bored. :)   Thank God for my day job! :) lol

.. and the TT guessing game goes on... :)

---

### Post by Alan F on 2013-10-18
/devel now working in UK with todays dates

alan@alan-Ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty
alan@alan-Ubuntu:~$

---

### Post by ventrical on 2013-10-18
> **Alan F said:**
> /devel now working in UK with todays dates

alan@alan-Ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
alan@alan-Ubuntu:~$

Thanks Allan.. but nothing here yet in Canada..

---

### Post by zika on 2013-10-18
> **Alan F said:**
> /devel now working in UK with todays dates

alan@alan-Ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
alan@alan-Ubuntu:~$That is quick... LTS is/was on the way... ;)
Update&#8321;: It is now working with „trusty“...
„devel“ is questionable```
W: Conflicting distribution: http://archive.canonical.com devel Release (expected devel but got trusty)
W: Conflicting distribution: http://archive.ubuntu.com devel Release (expected devel but got precise)
W: Conflicting distribution: http://archive.ubuntu.com devel-updates Release (expected devel-updates but got precise)
W: Conflicting distribution: http://archive.ubuntu.com devel-security Release (expected devel-security but got precise)
W: Conflicting distribution: http://archive.ubuntu.com devel-backports Release (expected devel-backports but got precise)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/devel/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/devel/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by slickymaster on 2013-10-18
> **ventrical said:**
> I changed the sources.list on fully updated saucy:

```


$ sudo sed -i 's/saucy/devel/g' /etc/apt/sources.list

```

and got this :

```

...


Ign http://ca.archive.ubuntu.com devel-backports/universe Translation-en_CA    
Fetched 19.6 MB in 2min 2s (160 kB/s)                                          
W: Conflicting distribution: http://ca.archive.ubuntu.com devel Release (expected devel but got precise)
W: Conflicting distribution: http://ca.archive.ubuntu.com devel-updates Release (expected devel-updates but got precise)
W: Conflicting distribution: http://ca.archive.ubuntu.com devel-backports Release (expected devel-backports but got precise)
W: Conflicting distribution: http://security.ubuntu.com devel-security Release (expected devel-security but got precise)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/devel/main/source/Sources  404  Not Found

...

```

It's 19:06 GMT here in Portugal, and I'm getting precise and raring simultaneously. It's really random:```
...
W: Distribuição em conflito: http://pt.archive.ubuntu.com devel Release (esperado devel mas obtido raring)
W: Distribuição em conflito: http://pt.archive.ubuntu.com devel-updates Release (esperado devel-updates mas obtido [COLOR=#ff0000]raring[/COLOR])
W: Distribuição em conflito: http://pt.archive.ubuntu.com devel-backports Release (esperado devel-backports mas obtido [COLOR=#ff0000]raring[/COLOR])
W: Distribuição em conflito: http://security.ubuntu.com devel-security Release (esperado devel-security mas obtido [COLOR=#ff0000]precise[/COLOR])
W: Falhou obter http://extras.ubuntu.com/ubuntu/dists/devel/main/source/Sources  404  Not Found...

```

---

### Post by ventrical on 2013-10-18
> **slickymaster said:**
> It's 19:06 GMT here in Portugal, and I'm getting precise and raring simultaneously. It's really random:```
...
W: Distribuição em conflito: http://pt.archive.ubuntu.com devel Release (esperado devel mas obtido raring)
W: Distribuição em conflito: http://pt.archive.ubuntu.com devel-updates Release (esperado devel-updates mas obtido [COLOR=#ff0000]raring[/COLOR])
W: Distribuição em conflito: http://pt.archive.ubuntu.com devel-backports Release (esperado devel-backports mas obtido [COLOR=#ff0000]raring[/COLOR])
W: Distribuição em conflito: http://security.ubuntu.com devel-security Release (esperado devel-security mas obtido [COLOR=#ff0000]precise[/COLOR])
W: Falhou obter http://extras.ubuntu.com/ubuntu/dists/devel/main/source/Sources  404  Not Found...

```

  Thanks @slikymaster,zika

 Looks like it is taking some time to get distributed. I'm getting absoultely nothing here on two installs(different machines). I have one set up in sources.list with /devel/ and one with /trusty/ No matter .. still no update/upgrade.

---

### Post by grahammechanical on 2013-10-18
It must be a question of mirrors being used. I am in London and on devel and there is nothing upgraded so the release is still saucy. I am on gb.archive.ubuntu.com.

You know you are bored when you run apt-get update every 30 minutes!

---

### Post by ventrical on 2013-10-18
> **grahammechanical said:**
> It must be a question of mirrors being used. I am in London and on devel and there is nothing upgraded so the release is still saucy. I am on gb.archive.ubuntu.com.

You know you are bored when you run apt-get update every 30 minutes!


hahahaha.. more like every thirty seconds ! :) lol  I even went to some obscure mirror in the UK to see if I could get it .. geeesh.... I must need a fix real bad ... :) lol

I am on Main.. think I'll switch to Canada then.
edit.. Nope .. still in the boondocks here :)

---

### Post by grahammechanical on 2013-10-18
I just tried again. Still got the conflicting distributions error but this time there was stuff to upgrade. Sadly the release is still saucy. So, the devs are once more sticking stuff into the devel repositories.

A thought comes into my tired brain. Perhaps these missing repositories are the ones with the source code in? All the repositories are there in Other software including those for source code, which I do not need.

Unchecking the source code repositories did not change anything. Any more bright ideas, Graham? Keep them to yourself. ;)

Regards.

---

### Post by xc3RnbFO8P on 2013-10-18
rig@rig-Aspire-R3600:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty
rig@rig-Aspire-R3600:~$ 

[[img]http://farm6.staticflickr.com/5494/10350944465_b4fd028d94_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/10350944465/)
[Screenshot from 2013-10-18 22:25:36](http://www.flickr.com/photos/96052779@N07/10350944465/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr
[[img]http://farm6.staticflickr.com/5489/10351354413_de7d1c9576_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/10351354413/)
[Screenshot from 2013-10-18 22:06:13](http://www.flickr.com/photos/96052779@N07/10351354413/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by zika on 2013-10-19
By switching (only) to Trusty branch at this moment You could lose some  of upgrades that are coming for Saucy... Toolchain is expected (as I  see) on 24.10. so... It will catch up but...

---

### Post by xc3RnbFO8P on 2013-10-19
I got update today (5 screenshots)

[[img]http://farm4.staticflickr.com/3699/10358642763_f2a25b249d_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/10358642763/)
[Screenshot from 2013-10-19 11:00:26](http://www.flickr.com/photos/96052779@N07/10358642763/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by zika on 2013-10-19
> **Ringi said:**
> I got update today (5 screenshots)

[[IMG]http://farm4.staticflickr.com/3699/10358642763_f2a25b249d_c.jpg[/IMG]]("http://www.flickr.com/photos/96052779@N07/10358642763/")
[Screenshot from 2013-10-19 11:00:26]("http://www.flickr.com/photos/96052779@N07/10358642763/") by [ringi_is]("http://www.flickr.com/people/96052779@N07/"), on Flickr
I might be wrong but looking at version #s I would say that these are from PPAs other than default...

---

### Post by grahammechanical on 2013-10-19
I just got an update to base-files which included lsb_release. I am now on 

> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty

and still getting those conflicting distribution errors at the same time.

Now all I need is for someone to explain how to pronounce Tahr. Is it the same way we pronounce Linux? :)

---

### Post by VinDSL on 2013-10-19
> **grahammechanical said:**
> Now all I need is for someone to explain how to pronounce Tahr. Is it the same way we pronounce Linux? :)
You pronounce it TAR, as in tar file.

Trusty Tar...  LoL!  :D

I hope that isn't a harbinger!

---

### Post by ventrical on 2013-10-19
> **VinDSL said:**
> You pronounce it TAR, as in tar file.

Trusty Tar...  LoL!  :D

I hope that isn't a harbinger!

  I just had a visual .... nevermind  :)

---

### Post by ventrical on 2013-10-19
I'm in ..

```

ventrical@ventrical-System-Product-Name:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by xc3RnbFO8P on 2013-10-19
Huston I have a problem, I cant open **software-properties-gtk**
I  change to the old sources.list and got update on software-properties-gtk  , but the problem remains.

[[img]http://farm8.staticflickr.com/7404/10365401145_669ce838f0_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/10365401145/)
[Screenshot from 2013-10-19 13:55:56](http://www.flickr.com/photos/96052779@N07/10365401145/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by zika on 2013-10-19
> **Ringi said:**
> Huston I have a problem, I cant open **software-properties-gtk**
I  change to the old sources.list and got update on software-properties-gtk  , but the problem remains.

[[IMG]http://farm8.staticflickr.com/7404/10365401145_669ce838f0_c.jpg[/IMG]]("http://www.flickr.com/photos/96052779@N07/10365401145/")
[Screenshot from 2013-10-19 13:55:56]("http://www.flickr.com/photos/96052779@N07/10365401145/") by [ringi_is]("http://www.flickr.com/people/96052779@N07/"), on Flickr
There is a file that (before toolchain) has to be edited manually, my notebook is not at my side...
There is a post on every new testing period about that file (even with my name I think as author in some of the latest cycles...)...
I'll find that in couple of minutes...

---

### Post by sammiev on 2013-10-19
The fun begins:

```
sam@sam-L650:~$ lsb_release -a
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:cxx-4.1-amd64:cxx-4.1-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:desktop-4.1-amd64:desktop-4.1-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:graphics-4.1-amd64:graphics-4.1-noarch:languages-3.2-amd64:languages-3.2-noarch:languages-4.0-amd64:languages-4.0-noarch:languages-4.1-amd64:languages-4.1-noarch:multimedia-3.2-amd64:multimedia-3.2-noarch:multimedia-4.0-amd64:multimedia-4.0-noarch:multimedia-4.1-amd64:multimedia-4.1-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:printing-4.1-amd64:printing-4.1-noarch:qt4-3.1-amd64:qt4-3.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty
sam@sam-L650:~$ 

```

---

### Post by zika on 2013-10-19
Here it is:```
sudo gedit /usr/share/python-apt/templates/Ubuntu.info
```
Add(on the top):```
Suite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 14.04 'Trusty Tahr'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: trusty
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 14.04 'Trusty Tahr'

Suite: trusty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*14.04
MatchURI: cdrom:\[Ubuntu.*14.04
Description: Cdrom with Ubuntu 14.04 'Trusty Tahr'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb
Description: Recommended updates

Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb
Description: Pre-released updates

Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb
Description: Unsupported updates

Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates
```

---

### Post by xc3RnbFO8P on 2013-10-19
This is my Ubuntu.Info :)

```
ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: saucy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 13.10 'Saucy Salamander'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: saucy
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 13.10 'Saucy Salamander'

Suite: saucy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*13.10
MatchURI: cdrom:\[Ubuntu.*13.10
Description: Cdrom with Ubuntu 13.10 'Saucy Salamander'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: saucy
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: saucy
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: saucy-security
ParentSuite: saucy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: saucy-security
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: saucy-updates
ParentSuite: saucy
RepositoryType: deb
Description: Recommended updates

Suite: saucy-updates
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: saucy-proposed
ParentSuite: saucy
RepositoryType: deb
Description: Pre-released updates

Suite: saucy-proposed
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: saucy-backports
ParentSuite: saucy
RepositoryType: deb
Description: Unsupported updates

Suite: saucy-backports
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: raring
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 13.04 'Raring Ringtail'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: raring
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 13.04 'Raring Ringtail'

Suite: raring
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*13.04
MatchURI: cdrom:\[Ubuntu.*13.04
Description: Cdrom with Ubuntu 13.04 'Raring Ringtail'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: raring
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: raring
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: raring-security
ParentSuite: raring
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: raring-security
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: raring-updates
ParentSuite: raring
RepositoryType: deb
Description: Recommended updates

Suite: raring-updates
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: raring-proposed
ParentSuite: raring
RepositoryType: deb
Description: Pre-released updates

Suite: raring-proposed
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: raring-backports
ParentSuite: raring
RepositoryType: deb
Description: Unsupported updates

Suite: raring-backports
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: quantal
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 12.10 'Quantal Quetzal'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: quantal
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 12.10 'Quantal Quetzal'

Suite: quantal
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*12.10
MatchURI: cdrom:\[Ubuntu.*12.10
Description: Cdrom with Ubuntu 12.10 'Quantal Quetzal'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: quantal
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: quantal
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: quantal-security
ParentSuite: quantal
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: quantal-security
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: quantal-updates
ParentSuite: quantal
RepositoryType: deb
Description: Recommended updates

Suite: quantal-updates
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: quantal-proposed
ParentSuite: quantal
RepositoryType: deb
Description: Pre-released updates

Suite: quantal-proposed
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: quantal-backports
ParentSuite: quantal
RepositoryType: deb
Description: Unsupported updates

Suite: quantal-backports
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: precise
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 12.04 'Precise Pangolin'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: precise
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 12.04 'Precise Pangolin'

Suite: precise
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*12.04
MatchURI: cdrom:\[Ubuntu.*12.04
Description: Cdrom with Ubuntu 12.04 'Precise Pangolin'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: precise
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: precise
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: precise-security
ParentSuite: precise
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: precise-security
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb
Description: Recommended updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb
Description: Pre-released updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb
Description: Unsupported updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: oneiric
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 11.10 'Oneiric Ocelot'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: oneiric
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 11.10 'Oneiric Ocelot'

Suite: oneiric
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*11.10
MatchURI: cdrom:\[Ubuntu.*11.10
Description: Cdrom with Ubuntu 11.10 'Oneiric Ocelot'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: oneiric
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: oneiric
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: oneiric-security
ParentSuite: oneiric
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: oneiric-security
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: oneiric-updates
ParentSuite: oneiric
RepositoryType: deb
Description: Recommended updates

Suite: oneiric-updates
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: oneiric-proposed
ParentSuite: oneiric
RepositoryType: deb
Description: Pre-released updates

Suite: oneiric-proposed
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: oneiric-backports
ParentSuite: oneiric
RepositoryType: deb
Description: Unsupported updates

Suite: oneiric-backports
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: natty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 11.04 'Natty Narwhal'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: natty
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 11.04 'Natty Narwhal'

Suite: natty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*11.04
MatchURI: cdrom:\[Ubuntu.*11.04
Description: Cdrom with Ubuntu 11.04 'Natty Narwhal'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: natty
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: natty
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: natty-security
ParentSuite: natty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: natty-security
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: natty-updates
ParentSuite: natty
RepositoryType: deb
Description: Recommended updates

Suite: natty-updates
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: natty-proposed
ParentSuite: natty
RepositoryType: deb
Description: Pre-released updates

Suite: natty-proposed
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: natty-backports
ParentSuite: natty
RepositoryType: deb
Description: Unsupported updates

Suite: natty-backports
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: maverick
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 10.10 'Maverick Meerkat'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: maverick
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*10.10
MatchURI: cdrom:\[Ubuntu.*10.10
Description: Cdrom with Ubuntu 10.10 'Maverick Meerkat'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: maverick
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: maverick
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: maverick-security
ParentSuite: maverick
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: maverick-updates
ParentSuite: maverick
RepositoryType: deb
Description: Recommended updates

Suite: maverick-proposed
ParentSuite: maverick
RepositoryType: deb
Description: Pre-released updates

Suite: maverick-backports
ParentSuite: maverick
RepositoryType: deb
Description: Unsupported updates

Suite: lucid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 10.04 'Lucid Lynx'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: lucid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*10.04
MatchURI: cdrom:\[Ubuntu.*10.04
Description: Cdrom with Ubuntu 10.04 'Lucid Lynx'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: lucid-security
ParentSuite: lucid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: lucid-updates
ParentSuite: lucid
RepositoryType: deb
Description: Recommended updates

Suite: lucid-proposed
ParentSuite: lucid
RepositoryType: deb
Description: Pre-released updates

Suite: lucid-backports
ParentSuite: lucid
RepositoryType: deb
Description: Unsupported updates

Suite: karmic
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 9.10 'Karmic Koala'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: karmic
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.10
MatchURI: cdrom:\[Ubuntu.*9.10
Description: Cdrom with Ubuntu 9.10 'Karmic Koala'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: karmic-security
ParentSuite: karmic
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: karmic-updates
ParentSuite: karmic
RepositoryType: deb
Description: Recommended updates

Suite: karmic-proposed
ParentSuite: karmic
RepositoryType: deb
Description: Pre-released updates

Suite: karmic-backports
ParentSuite: karmic
RepositoryType: deb
Description: Unsupported updates

Suite: jaunty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 9.04 'Jaunty Jackalope'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: jaunty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.04
MatchURI: cdrom:\[Ubuntu.*9.04
Description: Cdrom with Ubuntu 9.04 'Jaunty Jackalope'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: jaunty-security
ParentSuite: jaunty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: jaunty-updates
ParentSuite: jaunty
RepositoryType: deb
Description: Recommended updates

Suite: jaunty-proposed
ParentSuite: jaunty
RepositoryType: deb
Description: Pre-released updates

Suite: jaunty-backports
ParentSuite: jaunty
RepositoryType: deb
Description: Unsupported updates

Suite: intrepid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 8.10 'Intrepid Ibex'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: intrepid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.10
MatchURI: cdrom:\[Ubuntu.*8.10
Description: Cdrom with Ubuntu 8.10 'Intrepid Ibex'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: intrepid-security
ParentSuite: intrepid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: intrepid-updates
ParentSuite: intrepid
RepositoryType: deb
Description: Recommended updates

Suite: intrepid-proposed
ParentSuite: intrepid
RepositoryType: deb
Description: Pre-released updates

Suite: intrepid-backports
ParentSuite: intrepid
RepositoryType: deb
Description: Unsupported updates


Suite: hardy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 8.04 'Hardy Heron'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: hardy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.04
MatchURI: cdrom:\[Ubuntu.*8.04
Description: Cdrom with Ubuntu 8.04 'Hardy Heron'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hardy-security
ParentSuite: hardy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: hardy-updates
ParentSuite: hardy
RepositoryType: deb
Description: Recommended updates

Suite: hardy-proposed
ParentSuite: hardy
RepositoryType: deb
Description: Pre-released updates

Suite: hardy-backports
ParentSuite: hardy
RepositoryType: deb
Description: Unsupported updates


Suite: gutsy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
BaseURI-sparc: http://archive.ubuntu.com/ubuntu/
MatchURI-sparc: archive.ubuntu.com/ubuntu
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 7.10 'Gutsy Gibbon'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: gutsy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.10
MatchURI: cdrom:\[Ubuntu.*7.10
Description: Cdrom with Ubuntu 7.10 'Gutsy Gibbon'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: gutsy-security
ParentSuite: gutsy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-sparc: http://security.ubuntu.com/ubuntu/
MatchURI-sparc: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: gutsy-updates
ParentSuite: gutsy
RepositoryType: deb
Description: Recommended updates

Suite: gutsy-proposed
ParentSuite: gutsy
RepositoryType: deb
Description: Pre-released updates

Suite: gutsy-backports
ParentSuite: gutsy
RepositoryType: deb
Description: Unsupported updates


Suite: feisty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 7.04 'Feisty Fawn'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: feisty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.04
MatchURI: cdrom:\[Ubuntu.*7.04
Description: Cdrom with Ubuntu 7.04 'Feisty Fawn'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: feisty-security
ParentSuite: feisty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: feisty-updates
ParentSuite: feisty
RepositoryType: deb
Description: Recommended updates

Suite: feisty-proposed
ParentSuite: feisty
RepositoryType: deb
Description: Pre-released updates

Suite: feisty-backports
ParentSuite: feisty
RepositoryType: deb
Description: Unsupported updates

Suite: edgy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 6.10 'Edgy Eft'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: edgy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.10
MatchURI: cdrom:\[Ubuntu.*6.10
Description: Cdrom with Ubuntu 6.10 'Edgy Eft'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: edgy-security
ParentSuite: edgy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: edgy-updates
ParentSuite: edgy
RepositoryType: deb
Description: Recommended updates

Suite: edgy-proposed
ParentSuite: edgy
RepositoryType: deb
Description: Pre-released updates

Suite: edgy-backports
ParentSuite: edgy
RepositoryType: deb
Description: Unsupported updates

Suite: dapper
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 6.06 LTS 'Dapper Drake'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained (universe)
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software (Multiverse)
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: dapper
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.06
MatchURI: cdrom:\[Ubuntu.*6.06
Description: Cdrom with Ubuntu 6.06 LTS 'Dapper Drake'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: dapper-security
ParentSuite: dapper
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: dapper-updates
ParentSuite: dapper
RepositoryType: deb
Description: Recommended updates

Suite: dapper-proposed
ParentSuite: dapper
RepositoryType: deb
Description: Pre-released updates

Suite: dapper-backports
ParentSuite: dapper
RepositoryType: deb
Description: Unsupported updates

Suite: breezy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: Ubuntu.mirrors
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.10 'Breezy Badger'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: breezy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.10
MatchURI: cdrom:\[Ubuntu.*5.10
Description: Cdrom with Ubuntu 5.10 'Breezy Badger'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: breezy-security
ParentSuite: breezy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.10 Security Updates

Suite: breezy-updates
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Updates

Suite: breezy-backports
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Backports

Suite: hoary
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 5.04 'Hoary Hedgehog'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: hoary
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.04
MatchURI: cdrom:\[Ubuntu.*5.04
Description: Cdrom with Ubuntu 5.04 'Hoary Hedgehog'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hoary-security
ParentSuite: hoary
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.04 Security Updates

Suite: hoary-updates
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Updates

Suite: hoary-backports
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Backports

Suite: warty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
Description: Ubuntu 4.10 'Warty Warthog'
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: warty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*4.10
MatchURI: cdrom:\[Ubuntu.*4.10
Description: Cdrom with Ubuntu 4.10 'Warty Warthog'
Available: False
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: warty-security
ParentSuite: warty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 4.10 Security Updates

Suite: warty-updates
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Updates

Suite: warty-backports
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Backports

```

---

### Post by xc3RnbFO8P on 2013-10-19
Thanks @zika it worked  :)

---

### Post by zika on 2013-10-19
> **Ringi said:**
> Thanks @zika it worked  :)
:-\" Waiting for toolchain, but not sure if I will make that promise to myself... ;)

---

### Post by xc3RnbFO8P on 2013-10-19
> **zika said:**
> :-\" Waiting for toolchain, but not sure if I will make that promise to myself... ;)

I bet that you cant wait :)

---

### Post by ventrical on 2013-10-19
> **zika said:**
> Here it is:```
sudo gedit /usr/share/python-apt/templates/Ubuntu.info
```
Add(on the top):[code]Suite: trusty


Thank you sen zika :)

---

### Post by sparker256 on 2013-10-19
I'm in now by using /trusty

```

bill@billsim-64-1404:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty
bill@billsim-64-1404:~$ 

```

Bill

---

### Post by VinDSL on 2013-10-19
> **sparker256 said:**
> I'm in now by using /trusty

```

bill@billsim-64-1404:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty
bill@billsim-64-1404:~$ 

```

Bill
Hi Bill,

Long time; no see.  Glad you made it!  ;)



Greetz from Gnome3 Staging (ant's eyeview)...

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-19-oct-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-19-oct-2013-1.png")[/INDENT]

** I was a little worried when I saw some [ricotz trusty/testing upgrades]("https://launchpad.net/~ricotz/+archive/testing/+packages?field.name_filter=&field.status_filter=published&field.series_filter=trusty") being included, but it survived a cold boot.  

Yay, Rico!



And, last but not least...

> **zika said:**
> Here it is:```
sudo gedit /usr/share/python-apt/templates/Ubuntu.info
```
Add(on the top)...

Thanks, zika!

I remembered the concept, but forgot the file name.

You saved us a lot of keyboarding...

---

### Post by QDR06VV9 on 2013-10-19
```
 					[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **zika** 					[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12821131#post12821131") 				
 				Here it is: 	Code:
 	sudo gedit /usr/share/python-apt/templates/Ubuntu.info 
Add(on the top)...


```

Thanks Bud Gald I looked first! I would have forgot this..;)

---

### Post by QDR06VV9 on 2013-10-19
> **zika said:**
> :-\" Waiting for toolchain, but not sure if I will make that promise to myself... ;)
To Add to our wait:confused:

   October 24th Toolchain Uploaded  From Here[https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule)

---

### Post by cariboo on 2013-10-19
> **runrickus said:**
> To Add to our wait:confused:

   October 24th Toolchain Uploaded  From Here[https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule)

The release schedule is already linked in my sticky [here]("http://ubuntuforums.org/showthread.php?t=2181769"). I'm in the process of updating the pages.

---

### Post by zika on 2013-10-20
As usual after release date... There are lots of upgrades this weekend... That is why I did not regret waiting...
Not all from default PPAs but... It takes time for PPAs (especially non-default) to open +1 branch...
What's the state of &#8222;devel&#8220; symbolic linking?

---

### Post by zika on 2013-10-20
> **runrickus said:**
> ```
                     [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **zika**                     [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12821131#post12821131")                 
                 Here it is:     Code:
     sudo gedit /usr/share/python-apt/templates/Ubuntu.info 
Add(on the top)...


```

Thanks Bud Gald I looked first! I would have forgot this..;)&#8222;Bud Gald&#8220;=?...
;)

---

### Post by VinDSL on 2013-10-20
Rico is [on a roll]("https://launchpad.net/~ricotz/+archive/testing/+packages?field.name_filter=&field.status_filter=published&field.series_filter=trusty").

Does he never sleep?!?!?  :D

---

### Post by QDR06VV9 on 2013-10-20
> **zika said:**
> „Bud Gald“=?...
;)
Opps Glad(Happy) Dang fat old fingers!LOL

---

### Post by slickymaster on 2013-10-21
Alea Jacta Est!

```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
3.12.0-031200rc5-generic

```

Strangest thing is I lost TTY1 through TTY6. The fun has indeed began.

---

### Post by Alan F on 2013-10-21
What is the point of having both /devel and /trusty repos?

---

### Post by grahammechanical on 2013-10-21
> **Alan F said:**
> What is the point of having both /devel and /trusty repos?

That is what some of us want to know. We are guessing that by having software sources point to devel repositories instead of saucy repositories the development branch will roll over from saucy to trusty and then on to the 14.10 development branch.

Usually at the start of a development cycle we run this command to get on the development branch

```
sudo sed -i 's/trusty/saucy/g' /etc/apt/sources.list
```

That will rename the sources list from saucy to trusty and then with an update we are away onto the trusty development branch. Another way is to wait until the first daily ISO images are made available for download and put in a fresh installation. But we are hoping that this command will do away with the need to do all that every six months.

```
sudo sed -i 's/devel/saucy/g' /etc/apt/sources.list
```

I have one saucy install converted to devel and I am testing to see if it updates into the trusty development branch and it seems to be doing that. At least this install is updating with only a few errors about conflicting distributions.

Regards.

---

### Post by zika on 2013-10-21
But, let us be reasonable and sincere: That way (either via sed or via symlink) is not the &#8222;proper&#8220;/full/kosher way of getting into a new version...
There is (a small bit but existing one) &#8222;more proper&#8220; way of doing that...
I was hoping that symlink is just a sign of a whole procedure that could be automated...

---

### Post by Alan F on 2013-10-21
> **grahammechanical said:**
> That is what some of us want to know.

I have one saucy install converted to devel and I am testing to see if it updates into the trusty development branch and it seems to be doing that. At least this install is updating with only a few errors about conflicting distributions.

Regards.

I have exactly the same. 

So, as I see it, we can expect /trusty to track /devel until April 04 when /trusty becomes the LTS, then /devel will automatically change the repos to /u***** and continue. Thus /devel is the "rolling release".

EDIT
Or is /devel likely to move further forward than /trusty before next April?

---

### Post by grahammechanical on 2013-10-21
A "more proper" way? Now, you are teasing me, Zika. :) I also an waiting to test an "official" way that would automate getting on the development branch.

---

### Post by zika on 2013-10-21
> **grahammechanical said:**
> A "more proper" way? Now, you are teasing me, Zika. :) I also an waiting to test an "official" way that would automate getting on the development branch.
Too old to tease anybody...
&#8222;Debian way&#8220; is name for it I found appropriate and most used for it...
Not anything more elaborate than this shortcut but (in my humble opinion) safer and...

---

### Post by ventrical on 2013-10-23
> **grahammechanical said:**
> That is what some of us want to know. We are guessing that by having software sources point to devel repositories instead of saucy repositories the development branch will roll over from saucy to trusty and then on to the 14.10 development branch.

Usually at the start of a development cycle we run this command to get on the development branch

```
sudo sed -i 's/trusty/saucy/g' /etc/apt/sources.list
```

That will rename the sources list from saucy to trusty and then with an update we are away onto the trusty development branch. Another way is to wait until the first daily ISO images are made available for download and put in a fresh installation. But we are hoping that this command will do away with the need to do all that every six months.

```
sudo sed -i 's/devel/saucy/g' /etc/apt/sources.list
```

I have one saucy install converted to devel and I am testing to see if it updates into the trusty development branch and it seems to be doing that. At least this install is updating with only a few errors about conflicting distributions.

Regards.

correction.. it's

```


sudo sed -i 's/saucy/trusty/g' /etc/apt/sources.list


```

and

```



sudo sed -i 's/saucy/devel/g' /etc/apt/sources.list


```


Regards..

;)

---

### Post by cariboo on 2013-10-23
@Ventrical, does using the devel repos bypass the need for editing /usr/share/python-apt/templates/Ubuntu.info, so that software-properties-gtk works?

---

### Post by ventrical on 2013-10-24
> **cariboo907 said:**
> @Ventrical, does using the devel repos bypass the need for editing /usr/share/python-apt/templates/Ubuntu.info, so that software-properties-gtk works?

Yes .. and as stated by another contributor, it is because the .iso dailys are now open for buinsess. So if you download a daily-live or do the rename/zsync proceedure as I have done and then :
sudo apt-get update
sudo apt-get dist-upgrade

The Ubuntu.info file will be updated with /devel/. I had also noticed that the Ubuntu.info has this changelog prefix at the top that I did not notice in previous development cycles. So, from what I can see , the insertion of the original file that was being utilized before the toolchain and iso were available is no longer needed and why  there is this  marraige between /devel/ and /trusty I have not yet determined. However, it appears at current that  this whole development cycle is  extremely dynamic and fluid and may get to  a point where the insertion of the previously mentioned Ubuntu.info file may indeed be needed.

  It is only my opinion that the current  frameworks and templates in these early stages are extremely stable.

Regards..

---

### Post by VinDSL on 2013-10-24
> **ventrical said:**
> It is only my opinion that the current  frameworks and templates in these early stages are extremely stable.
Nope.  It's not only your opinion, vent...

I've consistently declared -- here and elsewhere -- that 'pre-alpha' (for want of another word) is the best stage of the Ubu +1 test cycle, e.g. after the toolchain but before the dev party.

Everything works soooo well that I'm always tempted to cease upgrading, but like a [moth_to_flame]("https://en.wikipedia.org/wiki/The_Merchant_of_Venice")...  :)

---

### Post by grahammechanical on 2013-10-24
I would say that the issue regarding ubuntu.info is a case of giving the devs a little time. 

Install #1: From trusty ISO image 23rd October. Software and Updates does not load and throws out a crash message. Updated and ubuntu.info was edited to have references to both trusty and devel and software and Updates no longer crashes.

Install #2: A saucy install with the software sources pointing to devel repositories which are listed in the Other Software tab. This installation has been updated into trusty and the ubuntu.info file has now been edited to have references to both trusty and devel. The repositories are still listed in the Other Software tab and they are listed as Ubuntu Development Series. And it is all done by just doing daily updates.

Installing trusty from today's ISO and onward should not find an issue with software-properties-gtk unless it is another issue. I think that anyone installing Trusty Tahr development ISO image from now on will find themselves on a development branch that rolls onward.

We will have to find another answer to those who ask: If I continue updating will 14.04 beta become 14.04 released? Yes, and then some, might be an accurate answer. I also wonder if people have forgotten about Ubuntu and rolling release.

Regards.

---

### Post by ventrical on 2013-10-24
> **VinDSL said:**
> Nope.  It's not only your opinion, vent...

I've consistently declared -- here and elsewhere -- that 'pre-alpha' (for want of another word) is the best stage of the Ubu +1 test cycle, e.g. after the toolchain but before the dev party.

Everything works soooo well that I'm always tempted to cease upgrading, but like a [moth_to_flame]("https://en.wikipedia.org/wiki/The_Merchant_of_Venice")...  :)

Thanks for the reminder Vin. I remember those discussions and I even stated it myself once and made a folder called <super-isos> which contain pre-alpha isos. :) Yep they are fast and furious until after UDS. :)lol

---

### Post by ventrical on 2013-10-24
> **grahammechanical said:**
> I would say that the issue regarding ubuntu.info is a case of giving the devs a little time. 

.

+1 .. I should curb my enthusiasms :)

---

### Post by Redalien0304 on 2013-10-24
Ok This might be Long Post Here Sorry. Excuse me also for being net seeing it also.
Installed Ubuntu 14.04 Trusty after i downloaded Ubuntu 13.10 Saucy amd64 & run zsync on it, all good there. Run update no problems.
run sudo apt-get update my Reusults

```
"craig@craig-Latitude-D830:~$ sudo apt-get update
[sudo] password for craig: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release    
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg [933 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release [49.6 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources [1,018 kB]              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources [4,759 B]         
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources [6,260 kB]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources           
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages    
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages     
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources [177 kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages [1,255 kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages [9,348 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages [5,751 kB]   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages [133 kB]  
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages [1,253 kB]       
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages [9,688 B]  
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages [5,759 kB]   
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages [134 kB]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US
Fetched 21.8 MB in 48s (448 kB/s)
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
craig@craig-Latitude-D830:~$ "
Run Gui Update get "Failed to Download Repository information" Click on Ok & Get "not all update can be installed" Click on "Partial Upgrade"
``` 
Here is the Upgrade partial List Screenshots
[http://i1337.photobucket.com/albums/o679/redalien0304/Partialupgradelsist1_zps1fbe133a.jpg](http://i1337.photobucket.com/albums/o679/redalien0304/Partialupgradelsist1_zps1fbe133a.jpg)
[http://i1337.photobucket.com/albums/o679/redalien0304/Partialupgradelsist2_zps72205a2b.jpg](http://i1337.photobucket.com/albums/o679/redalien0304/Partialupgradelsist2_zps72205a2b.jpg)

Did not Run Partial upgrade list yet.
ok should i run the Upgrade? or do meed to do something else 1st?
Any info will be helpful. Thanks
Sorry is post too Long

---

### Post by cariboo on 2013-10-24
The extra repositories haven't been updated to trusty yet, just disable them using Software & Updates in system settings, then do an:

```
sudo apt-get update && sudo apt-get -y dist-upgrade
```

---

### Post by QDR06VV9 on 2013-10-24
> **ventrical said:**
> +1 .. I should curb my enthusiasms :)

Now Where's the fun in that!;)

---

### Post by ventrical on 2013-10-24
> **runrickus said:**
> Now Where's the fun in that!;)


You're right. There is no fun in that. :) I would then become a crumudgeon grumpy pants whining about the days of Outlook Express past. :) lol

---

### Post by QDR06VV9 on 2013-10-24
> **ventrical said:**
>  whining about the days of Outlook Express past. :) lol

Careful your datelining yourself now!!:) 
Thanks Vent its to the point now I have to look for your posts here, Your Appreciated.
Regards

---

### Post by kevpan8152 on 2013-10-25
Did you read Cariboo907's Warning NOT to Install pre-release updates (I'm guessing from Trusty-Preposed although I am waiting for him to clarify)? It's in the Sticky.

---

### Post by kevpan8152 on 2013-10-25
Well looks like I did NOT follow directions either, as i installed the Trusty Updates, and there were indeed some Trusty Updates although 53 of them or so were held back as the package dependencies have NOT yet been met.

---

### Post by grahammechanical on 2013-10-25
It is now just over a week since development moved on to trusty and I have seen a lot of updates come through in this week. Just now I even got an upgrade to Libreoffice. I did not expect that. If you are using Update Manager (and that does need to be tested as well) never accept when it offers a partial upgrade. Just OK the message and the update process will continue as usual. There are certain repositories such as Extras that come on line later in the cycle. So, we may get messages about that. This is usual.

Regards.

---

### Post by kevpan8152 on 2013-10-25
As far as I know, I have Trusty-Proposed Disabled. What I did was I used Ventrical's Original Oneric to Precise Command and replaced the word Oneric with Saucy, and Precise with Trusty (his Oneric to Precise Command is mentioned in his Sticky). I then did a Sudo Apt-Get Update and a Sudo Apt-Get Upgrade. I am hoping that I did NOT use the wrong Command.

---

### Post by ventrical on 2013-10-25
> **kevpan8152 said:**
> As far as I know, I have Trusty-Proposed Disabled. What I did was I used Ventrical's Original Oneric to Precise Command and replaced the word Oneric with Saucy, and Precise with Trusty (his Oneric to Precise Command is mentioned in his Sticky). I then did a Sudo Apt-Get Update and a Sudo Apt-Get Upgrade. I am hoping that I did NOT use the wrong Command.


Hey .. thats interesting. Let us know what happened.


Regards..

---

### Post by slickymaster on 2013-10-25
> **grahammechanical said:**
> It is now just over a week since development moved on to trusty and I have seen a lot of updates come through in this week. Just now I even got an upgrade to Libreoffice. I did not expect that. If you are using Update Manager (and that does need to be tested as well) never accept when it offers a partial upgrade. Just OK the message and the update process will continue as usual. There are certain repositories such as Extras that come on line later in the cycle. So, we may get messages about that. This is usual.

Regards.

It's has been six days since I moved to Trusty and I would say that I've already downloaded more than 150 MB in updates/upgrades this week, and I'm not including LibreOffice since I don't have it.

---

### Post by ventrical on 2013-10-25
> **slickymaster said:**
> It's has been six days since I moved to Trusty and I would say that I've already downloaded more than 150 MB in updates/upgrades this week, and I'm not including LibreOffice since I don't have it.

same here .. and then some ..

---

### Post by cariboo on 2013-10-25
> **grahammechanical said:**
> It is now just over a week since development moved on to trusty and I have seen a lot of updates come through in this week. Just now I even got an upgrade to Libreoffice. I did not expect that. If you are using Update Manager (and that does need to be tested as well) never accept when it offers a partial upgrade. Just OK the message and the update process will continue as usual. There are certain repositories such as Extras that come on line later in the cycle. So, we may get messages about that. This is usual.

Regards.

There was a notification over on [Discourse]("http://ubuntu-discourse.org/t/libreoffice-4-0-6-released-and-already-available-for-ubuntu-13-04/1140") that LibreOffice 4.0.6 was released, and seeing as there weren't any upstream changes aside from the name, it was released without much fanfare.

---

### Post by kevpan8152 on 2013-10-25
So in other words, all it (Libre Office) was is a Maintance Release correct?

---

### Post by cariboo on 2013-10-25
> **kevpan8152 said:**
> So in other words, all it (Libre Office) was is a Maintance Release correct?

The LibreOffice 4.0.6 release notes can be found [here]("http://www.libreoffice.org/download/release-notes/").

---

### Post by philinux on 2013-10-25
I'm getting this after changing to devel.

```
W: Conflicting distribution: http://archive.canonical.com devel Release (expected devel but got trusty)
W: Conflicting distribution: http://archive.ubuntu.com devel Release (expected devel but got trusty)
W: Conflicting distribution: http://archive.ubuntu.com devel-updates Release (expected devel-updates but got trusty)
W: Conflicting distribution: http://archive.ubuntu.com devel-backports Release (expected devel-backports but got trusty)
W: Conflicting distribution: http://archive.ubuntu.com devel-security Release (expected devel-security but got trusty)
Reading package lists... Done

```

---

### Post by ventrical on 2013-10-25
I am getting the same thing here with the marriage of /devel/ and /trusty/ and the most bizzare thing is that I am getting both i386 and amd64 packages.

```

Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages          
Hit http://archive.ubuntu.com trusty-updates/restricted i386 Packages          
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages            
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages             
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages         
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages              
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages        
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages        
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages          
Hit http://archive.ubuntu.com trusty-backports/main Translation-en             
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en       
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en       
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en         
Get:26 http://ca.archive.ubuntu.com devel/multiverse i386 Packages [135 kB]    
Hit http://ca.archive.ubuntu.com devel/main Translation-en_CA                  
Hit http://ca.archive.ubuntu.com devel/main Translation-en                     
Get:


```

---

### Post by philinux on 2013-10-25
Ventrical , that's not the same as i'm getting. Those are the only errors I'm getting and all of sources is set to devel.

I've not hit the Y on the upgrades yet.

---

### Post by ventrical on 2013-10-25
Thats was truncated:

```

Fetched 44.3 MB in 2min 33s (288 kB/s)
W: Conflicting distribution: http://ca.archive.ubuntu.com devel Release (expected devel but got trusty)
W: Conflicting distribution: http://ca.archive.ubuntu.com devel-updates Release (expected devel-updates but got trusty)
W: Conflicting distribution: http://ca.archive.ubuntu.com devel-backports Release (expected devel-backports but got trusty)
W: Conflicting distribution: http://security.ubuntu.com devel-security Release (expected devel-security but got trusty)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/devel/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/devel/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/devel/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
ventrical@ventrical-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libgtkglext1 libraw9 libtiff5 rtkit
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 681 kB of archives.
After this operation, 10.2 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ devel/main libraw9 amd64 0.15.4-1 [356 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ devel/main libtiff5 amd64 4.0.3-5ubuntu1 [171 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ devel/universe libgtkglext1 amd64 1.2.0-3.1fakesync2 [119 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ devel/main rtkit amd64 0.10-3 [35.7 kB]
Fetched 681 kB in 3s (223 kB/s) 
(Reading database ... 198382 files and directories currently installed.)
Preparing to replace libraw9:amd64 0.15.3-1ubuntu1 (using .../libraw9_0.15.4-1_amd64.deb) ...
Unpacking replacement libraw9:amd64 ...
Preparing to replace libtiff5:amd64 4.0.2-4ubuntu3 (using .../libtiff5_4.0.3-5ubuntu1_amd64.deb) ...
Unpacking replacement libtiff5:amd64 ...
Preparing to replace libgtkglext1 1.2.0-3.1fakesync1 (using .../libgtkglext1_1.2.0-3.1fakesync2_amd64.deb) ...
Unpacking replacement libgtkglext1 ...
Preparing to replace rtkit 0.10-2ubuntu1 (using .../rtkit_0.10-3_amd64.deb) ...
Unpacking replacement rtkit ...
Processing triggers for man-db ...
Setting up libraw9:amd64 (0.15.4-1) ...
Setting up libtiff5:amd64 (4.0.3-5ubuntu1) ...
Setting up libgtkglext1 (1.2.0-3.1fakesync2) ...
Setting up rtkit (0.10-3) ...
Processing triggers for libc-bin ...

```

 I went ahead and installed updates.

---

### Post by QDR06VV9 on 2013-10-25
> **philinux said:**
> Ventrical , that's not the same as i'm getting. Those are the only errors I'm getting and all of sources is set to devel.  I've not hit the Y on the upgrades yet.  Phil did you see post #31 on this thread [http://ubuntuforums.org/showthread.php?t=2181414&page=4](http://ubuntuforums.org/showthread.php?t=2181414&page=4)

---

### Post by ventrical on 2013-10-25
.. it may be that we may need to roll back to that file, especially in these early stages of dev testing.

Thanks for the memory peg :)

---

### Post by philinux on 2013-10-25
> **runrickus said:**
> Phil did you see post #31 on this thread [http://ubuntuforums.org/showthread.php?t=2181414&page=4](http://ubuntuforums.org/showthread.php?t=2181414&page=4)

Cheers. I have partners and extras disable and all src's.

---

### Post by kevpan8152 on 2013-10-25
I re-did the Update Process with Cariboo907's Commands instead of Sudo Apt-Get Upgrade and a whole lot more Updates downloaded than with Cariboo907's Commands and no Updates were held back, and the Laptop did Reboot Successfully. Sometimes when I force all updates to install by doing a Partial Upgrade the Computer fails to boot on first Re-Boot. This time that did NOT happen. I don't know what the -y switch does but it seems to be right on. Thank You Ventrical and Cariboo907 for helping me realize that I was using the wrong command.

---

### Post by VinDSL on 2013-10-25
> **grahammechanical said:**
> I have seen a lot of updates come through in this week[...]
Me too.  I'm shocked, actually.

Here's a list from this morning, alone... LoL!

```
Commit Log for Thu Oct 24 19:54:44 2013


Removed the following packages:
libperl5.14
libvlccore5

Upgraded the following packages:
aisleriot (1:3.8.0-2) to 1:3.10.1-1
apparmor (2.8.0-0ubuntu31) to 2.8.0-0ubuntu32
apparmor-easyprof (2.8.0-0ubuntu31) to 2.8.0-0ubuntu32
apparmor-easyprof-ubuntu (1.0.40) to 1.0.41
aptdaemon (1.1.1-0ubuntu3) to 1.1.1-1ubuntu1
aptdaemon-data (1.1.1-0ubuntu3) to 1.1.1-1ubuntu1
aptitude (0.6.8.2-1ubuntu2) to 0.6.8.2-1ubuntu3
aptitude-common (0.6.8.2-1ubuntu2) to 0.6.8.2-1ubuntu3
at (3.1.13-2ubuntu2) to 3.1.14-1ubuntu1
at-spi2-core (2.10.0-0ubuntu2) to 2.10.1-0ubuntu1
audacious (3.4-1) to 3.4.1-1
audacious-plugins (3.4-2) to 3.4.1-1
audacious-plugins-data (3.4-2) to 3.4.1-1
autopoint (0.18.1.1-10ubuntu3) to 0.18.3.1-1ubuntu1
base-passwd (3.5.26) to 3.5.28
binutils (2.23.52.20130913-0ubuntu1) to 2.23.90.20131017-1ubuntu1
bsd-mailx (8.1.2-0.20111106cvs-1ubuntu1) to 8.1.2-0.20131005cvs-1
busybox-initramfs (1:1.20.0-8.1ubuntu1) to 1:1.20.0-9ubuntu2
busybox-static (1:1.20.0-8.1ubuntu1) to 1:1.20.0-9ubuntu2
bzip2 (1.0.6-4) to 1.0.6-5
ca-certificates (20130610) to 20130906
cordova-ubuntu-2.8 (2.8.0+13.10.20130917.1-0ubuntu1) to 2.8.0+14.04.20131024.4-0ubuntu1
cordova-ubuntu-2.8-dev (2.8.0+13.10.20130917.1-0ubuntu1) to 2.8.0+14.04.20131024.4-0ubuntu1
cpp-4.7 (4.7.3-7ubuntu3) to 4.7.3-8ubuntu1
cpp-4.8 (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
cracklib-runtime (2.8.22-1) to 2.9.0-1ubuntu1
cups-browsed (1.0.40-0ubuntu1) to 1.0.40-0ubuntu2
cups-filters (1.0.40-0ubuntu1) to 1.0.40-0ubuntu2
dconf-cli (0.16.1-1) to 0.18.0-1
dconf-editor (0.16.1-1) to 0.18.0-1
dconf-gsettings-backend (0.16.1-1) to 0.18.0-1
dconf-service (0.16.1-1) to 0.18.0-1
dconf-tools (0.16.1-1) to 0.18.0-1
debhelper (9.20130630ubuntu1) to 9.20130921ubuntu1
debugedit (4.11.1-2) to 4.11.1-3
dh-apparmor (2.8.0-0ubuntu31) to 2.8.0-0ubuntu32
dialog (1.2-20130523-1) to 1.2-20130928-1
dictionaries-common (1.20.2) to 1.20.3
diffstat (1.56-1) to 1.57-1
diffutils (1:3.2-8) to 1:3.3-1
duplicity (0.6.21-0ubuntu4) to 0.6.22-1ubuntu2
eog (3.10.0-0ubuntu1~saucy1) to 3.10.1-0ubuntu1~saucy1
evolve-gtk-theme (201308132228-0~96~saucy1) to 201310240015-0~99~ubuntu13.10.1
flac (1.3.0-1) to 1.3.0-2
fonts-droid (1:4.2.r1-2) to 1:4.3-1
fonts-liberation (1.07.3-2) to 1.07.3-3
fonts-lyx (2.0.6-1) to 2.0.6-1build1
fonts-opensymbol (2:102.3+LibO4.1.2~rc3-0ubuntu1) to 2:102.3+LibO4.1.2~rc3-0ubuntu2
g++-4.7 (4.7.3-7ubuntu3) to 4.7.3-8ubuntu1
g++-4.8 (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
gcc-4.7 (4.7.3-7ubuntu3) to 4.7.3-8ubuntu1
gcc-4.7-base (4.7.3-7ubuntu3) to 4.7.3-8ubuntu1
gcc-4.8 (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
gcc-4.8-base (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
geoip-database (20130813-1) to 20131007-1
gettext (0.18.1.1-10ubuntu3) to 0.18.3.1-1ubuntu1
gettext-base (0.18.1.1-10ubuntu3) to 0.18.3.1-1ubuntu1
giblib1 (1.2.4-8) to 1.2.4-9
gir1.2-atspi-2.0 (2.10.0-0ubuntu2) to 2.10.1-0ubuntu1
gir1.2-freedesktop (1.38.0-0ubuntu1) to 1.39.0~git20131022.f7acdd34-0ubuntu1~14.04~ricotz0
gir1.2-glib-2.0 (1.38.0-0ubuntu1) to 1.39.0~git20131022.f7acdd34-0ubuntu1~14.04~ricotz0
gir1.2-gtk-2.0 (2.24.20-1ubuntu1) to 2.24.21-1ubuntu1
gir1.2-gtk-3.0 (3.11.0~git20131016.9bd87b37-0ubuntu1~14.04~ricotz0) to 3.11.0~git20131023.cf00c431-0ubuntu1~14.04~ricotz0
gir1.2-gtksource-3.0 (3.10.0-0ubuntu1~saucy1) to 3.10.1-0ubuntu1~saucy1
gir1.2-gtop-2.0 (2.28.5-2~saucy1) to 2.28.5-2
gir1.2-javascriptcoregtk-3.0 (2.1.90.1-1~saucy1) to 2.2.0-2~saucy1
gir1.2-mutter-3.0 (3.10.1+git20131014.badebfae-0ubuntu1~13.10~ricotz0) to 3.10.1.1-0ubuntu1~saucy1
gir1.2-networkmanager-1.0 (0.9.8.4-0ubuntu1~saucy1) to 0.9.8.8-0ubuntu1~saucy1
gir1.2-pango-1.0 (1.35.3-0ubuntu1~13.10~ricotz0) to 1.36.0-1ubuntu1~saucy1
gir1.2-rb-3.0 (3.0.1-0ubuntu1~14.04~ricotz0) to 3.0.1-1ubuntu2
gir1.2-soup-2.4 (2.42.2-6) to 2.44.1-1
gir1.2-telepathyglib-0.12 (0.20.4-1) to 0.22.0-1
gir1.2-telepathylogger-0.2 (0.8.0-1) to 0.8.0-2
gir1.2-upowerglib-1.0 (0.9.22-1ubuntu1) to 0.9.23-2
gir1.2-vte-2.90 (1:0.34.8-0ubuntu1~saucy1) to 1:0.34.8-1ubuntu1
gir1.2-webkit-3.0 (2.1.90.1-1~saucy1) to 2.2.0-2~saucy1
gjs (1.38.1-0ubuntu1~13.10~ricotz0) to 1.38.1-0ubuntu1~saucy1
glib-networking (2.38.0-1~ubuntu5) to 2.38.1-1
glib-networking-common (2.38.0-1~ubuntu5) to 2.38.1-1
glib-networking-services (2.38.0-1~ubuntu5) to 2.38.1-1
gnome-common (3.10.0-1~saucy1) to 3.10.0-1
gnome-control-center (1:3.10.0-0ubuntu1~saucy2) to 1:3.10.1-0ubuntu1~saucy2
gnome-control-center-data (1:3.10.0-0ubuntu1~saucy2) to 1:3.10.1-0ubuntu1~saucy2
gnome-icon-theme-symbolic (3.10.0-0ubuntu1~saucy1) to 3.10.1-1~saucy1
gnome-settings-daemon (3.10.0-0ubuntu1~saucy0) to 3.10.1-0ubuntu1~saucy2
gnome-terminal (3.10.0-0ubuntu1~saucy1) to 3.10.1-0ubuntu1~saucy1
gnome-terminal-data (3.10.0-0ubuntu1~saucy1) to 3.10.1-0ubuntu1~saucy1
gnote (3.8.1-2) to 3.10.0-1~saucy1
gnumeric (1.12.6-1) to 1.12.6-2
gnumeric-common (1.12.6-1) to 1.12.6-2
gnumeric-doc (1.12.6-1) to 1.12.6-2
gparted (0.16.1-1) to 0.16.2-1
graphviz (2.26.3-15ubuntu4) to 2.34.0-0ubuntu4
grep (2.14-3) to 2.14-4
grub-common (2.00-19ubuntu2) to 2.00-19ubuntu3
grub-pc (2.00-19ubuntu2) to 2.00-19ubuntu3
grub-pc-bin (2.00-19ubuntu2) to 2.00-19ubuntu3
grub2-common (2.00-19ubuntu2) to 2.00-19ubuntu3
gtk-3-examples (3.11.0~git20131016.9bd87b37-0ubuntu1~14.04~ricotz0) to 3.11.0~git20131023.cf00c431-0ubuntu1~14.04~ricotz0
gtk2-engines-pixbuf (2.24.20-1ubuntu1) to 2.24.21-1ubuntu1
hplip (3.13.9-1) to 3.13.9-2
hplip-data (3.13.9-1) to 3.13.9-2
htop (1.0.2-2) to 1.0.2-3
hwdata (0.234-1) to 0.249-1
icedtea-netx (1.4-3ubuntu2) to 1.4.1-1ubuntu1
icedtea-netx-common (1.4-3ubuntu2) to 1.4.1-1ubuntu1
iftop (1.0~pre2-3) to 1.0~pre2-4
ifupdown (0.7.44ubuntu3) to 0.7.45ubuntu1
imagemagick (8:6.7.7.10-5ubuntu3) to 8:6.7.7.10-5ubuntu4
imagemagick-common (8:6.7.7.10-5ubuntu3) to 8:6.7.7.10-5ubuntu4
init-system-helpers (1.7) to 1.11
initramfs-tools (0.103ubuntu1) to 0.103ubuntu2
initramfs-tools-bin (0.103ubuntu1) to 0.103ubuntu2
iproute (1:3.10.0-1ubuntu1) to 1:3.11.0-1
iproute2 (3.10.0-1ubuntu1) to 3.11.0-1
iptables (1.4.18-1.1ubuntu1) to 1.4.20-2ubuntu1
iso-codes (3.46-1) to 3.47-1
kmod (9-3ubuntu1) to 15-0ubuntu2
leafpad (0.8.18.1-3) to 0.8.18.1-4
lftp (4.4.9-1) to 4.4.10-1
libalgorithm-diff-xs-perl (0.04-2build3) to 0.04-2build4
libapparmor-perl (2.8.0-0ubuntu31) to 2.8.0-0ubuntu32
libapparmor1 (2.8.0-0ubuntu31) to 2.8.0-0ubuntu32
libapt-pkg-perl (0.1.29) to 0.1.29build1
libasan0 (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
libasprintf-dev (0.18.1.1-10ubuntu3) to 0.18.3.1-1ubuntu1
libasprintf0c2 (0.18.1.1-10ubuntu3) to 0.18.3.1-1ubuntu1
libass4 (0.10.1-1ubuntu1) to 0.10.1-3
libassuan0 (2.1.0-1) to 2.1.1-1
libatomic1 (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
libatspi2.0-0 (2.10.0-0ubuntu2) to 2.10.1-0ubuntu1
libaudclient2 (3.4-1) to 3.4.1-1
libaudcore1 (3.4-1) to 3.4.1-1
libaudio-flac-header-perl (2.4-1build2) to 2.4-1build3
libaudio-scan-perl (0.93+dfsg-2build1) to 0.93+dfsg-2build2
libaudio2 (1.9.3-6) to 1.9.4-1
libblas3 (1.2.20110419-5) to 1.2.20110419-7
libblas3gf (1.2.20110419-5) to 1.2.20110419-7
libbluray1 (1:0.2.3-1) to 1:0.4.0-1
libbz2-1.0 (1.0.6-4) to 1.0.6-5
libcairo-perl (1.103-2) to 1.104-1
libchamplain-0.12-0 (0.12.5-1~saucy1) to 0.12.5-1
libchamplain-gtk-0.12-0 (0.12.5-1~saucy1) to 0.12.5-1
libchromaprint0 (0.7-1) to 0.7-2
libclone-perl (0.34-1) to 0.35-1
libcloog-isl4 (0.18.0-2) to 0.18.1-1
libclucene-contribs1 (2.3.3.4-4) to 2.3.3.4-4build1
libclucene-core1 (2.3.3.4-4) to 2.3.3.4-4build1
libcmis-0.3-3 (0.3.1-3ubuntu1) to 0.3.1-3ubuntu2
libcrack2 (2.8.22-1) to 2.9.0-1ubuntu1
libcss-perl (1.08-1+nmu3) to 1.09-1
libcupsfilters1 (1.0.40-0ubuntu1) to 1.0.40-0ubuntu2
libdatrie1 (0.2.6-2) to 0.2.7.1-1
libdc1394-22 (2.2.1-1ubuntu1) to 2.2.1-2
libdconf-dbus-1-0 (0.16.1-1) to 0.18.0-1
libdconf1 (0.16.1-1) to 0.18.0-1
libdiscid0 (0.5.1-1) to 0.6.1-2
libedit2 (3.1-20130712-1) to 3.1-20130712-2
libegl1-mesa (9.2.1-1ubuntu3) to 9.2.2-1ubuntu1
libegl1-mesa-drivers (9.2.1-1ubuntu3) to 9.2.2-1ubuntu1
libemail-valid-perl (0.190-1) to 1.192-1
libenca0 (1.14-3) to 1.15-1
libept1.4.12 (1.0.9) to 1.0.12
liberror-perl (0.17-1) to 0.17-1.1
libfile-desktopentry-perl (0.04-3) to 0.07-1
libfile-fcntllock-perl (0.14-2) to 0.14-2build1
libfile-mimeinfo-perl (0.16-2) to 0.20-1
libfile-slurp-perl (9999.19-2) to 9999.19-4
libflac8 (1.3.0-1) to 1.3.0-2
libfontembed1 (1.0.40-0ubuntu1) to 1.0.40-0ubuntu2
libgail-3-0 (3.11.0~git20131016.9bd87b37-0ubuntu1~14.04~ricotz0) to 3.11.0~git20131023.cf00c431-0ubuntu1~14.04~ricotz0
libgail-common (2.24.20-1ubuntu1) to 2.24.21-1ubuntu1
libgail18 (2.24.20-1ubuntu1) to 2.24.21-1ubuntu1
libgbm1 (9.2.1-1ubuntu3) to 9.2.2-1ubuntu1
libgcc-4.7-dev (4.7.3-7ubuntu3) to 4.7.3-8ubuntu1
libgcc-4.8-dev (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
libgcc1 (1:4.8.1-10ubuntu8) to 1:4.8.2-1ubuntu2
libgd3 (2.1.0-2) to 2.1.0-3
libgeoip1 (1.5.1-1ubuntu1) to 1.5.1-2ubuntu1
libgettextpo-dev (0.18.1.1-10ubuntu3) to 0.18.3.1-1ubuntu1
libgettextpo0 (0.18.1.1-10ubuntu3) to 0.18.3.1-1ubuntu1
libgfortran3 (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
libgirepository-1.0-1 (1.38.0-0ubuntu1) to 1.39.0~git20131022.f7acdd34-0ubuntu1~14.04~ricotz0
libgjs0d (1.38.1-0ubuntu1~13.10~ricotz0) to 1.38.1-0ubuntu1~saucy1
libgl1-mesa-dev (9.2.1-1ubuntu3) to 9.2.2-1ubuntu1
libgl1-mesa-dri (9.2.1-1ubuntu3) to 9.2.2-1ubuntu1
libgl1-mesa-glx (9.2.1-1ubuntu3) to 9.2.2-1ubuntu1
libglapi-mesa (9.2.1-1ubuntu3) to 9.2.2-1ubuntu1
libgles2-mesa (9.2.1-1ubuntu3) to 9.2.2-1ubuntu1
libglib-perl (3:1.301-1) to 3:1.302-1
libglib2.0-0 (2.39.0~git20131016.c5748328-0ubuntu1~14.04~ricotz0) to 2.39.0~git20131022.efecfe0f-0ubuntu1~14.04~ricotz5
libglib2.0-bin (2.39.0~git20131016.c5748328-0ubuntu1~14.04~ricotz0) to 2.39.0~git20131022.efecfe0f-0ubuntu1~14.04~ricotz5
libglib2.0-data (2.39.0~git20131016.c5748328-0ubuntu1~14.04~ricotz0) to 2.39.0~git20131022.efecfe0f-0ubuntu1~14.04~ricotz5
libglib2.0-dev (2.39.0~git20131016.c5748328-0ubuntu1~14.04~ricotz0) to 2.39.0~git20131022.efecfe0f-0ubuntu1~14.04~ricotz5
libglib2.0-doc (2.39.0~git20131016.c5748328-0ubuntu1~14.04~ricotz0) to 2.39.0~git20131022.efecfe0f-0ubuntu1~14.04~ricotz5
libglm-dev (0.9.4.4-1ubuntu1) to 0.9.4.6-2
libglu1-mesa (9.0.0-1) to 9.0.0-2
libglu1-mesa-dev (9.0.0-1) to 9.0.0-2
libgmime-2.6-0 (2.6.18-1ubuntu1~saucy1) to 2.6.18-1ubuntu1
libgmime2.6-cil (2.6.18-1ubuntu1~saucy1) to 2.6.18-1ubuntu1
libgnome-control-center1 (1:3.10.0-0ubuntu1~saucy2) to 1:3.10.1-0ubuntu1~saucy2
libgomp1 (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
libgpgme11 (1.4.2-0.1ubuntu3) to 1.4.3-0.1ubuntu2
libgssdp-1.0-3 (0.14.4-1) to 0.14.5-1
libgtk-3-0 (3.11.0~git20131016.9bd87b37-0ubuntu1~14.04~ricotz0) to 3.11.0~git20131023.cf00c431-0ubuntu1~14.04~ricotz0
libgtk-3-bin (3.11.0~git20131016.9bd87b37-0ubuntu1~14.04~ricotz0) to 3.11.0~git20131023.cf00c431-0ubuntu1~14.04~ricotz0
libgtk-3-common (3.11.0~git20131016.9bd87b37-0ubuntu1~14.04~ricotz0) to 3.11.0~git20131023.cf00c431-0ubuntu1~14.04~ricotz0
libgtk2-perl (2:1.247-2) to 2:1.248-1
libgtk2.0-0 (2.24.20-1ubuntu1) to 2.24.21-1ubuntu1
libgtk2.0-bin (2.24.20-1ubuntu1) to 2.24.21-1ubuntu1
libgtk2.0-common (2.24.20-1ubuntu1) to 2.24.21-1ubuntu1
libgtkhtml-4.0-0 (4.6.6-1) to 4.6.6-2
libgtkhtml-4.0-common (4.6.6-1) to 4.6.6-2
libgtkhtml-editor-4.0-0 (4.6.6-1) to 4.6.6-2
libgtksourceview-3.0-1 (3.10.0-0ubuntu1~saucy1) to 3.10.1-0ubuntu1~saucy1
libgtksourceview-3.0-common (3.10.0-0ubuntu1~saucy1) to 3.10.1-0ubuntu1~saucy1
libgtkspell3-3-0 (3.0.3-1) to 3.0.4-1
libgtop2-7 (2.28.5-2~saucy1) to 2.28.5-2
libgtop2-common (2.28.5-2~saucy1) to 2.28.5-2
libgupnp-1.0-4 (0.20.4-1) to 0.20.7-1
libgvc5 (2.26.3-15ubuntu4) to 2.34.0-0ubuntu4
libgvpr1 (2.26.3-15ubuntu4) to 2.34.0-0ubuntu4
libhpmud0 (3.13.9-1) to 3.13.9-2
libhtml-parser-perl (3.71-1) to 3.71-1build1
libhtml-tree-perl (5.02-1) to 5.03-1
libhtml-wikiconverter-perl (0.68-1) to 0.68-2
libieee1284-3 (0.2.11-11) to 0.2.11-12
libimage-exiftool-perl (9.13-1) to 9.27-1
libio-pty-perl (1:1.08-1build3) to 1:1.08-1build4
libisl10 (0.11.2-1) to 0.12.1-1
libitm1 (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
libjack-jackd2-0 (1.9.9.5+20130622git7de15e7a-1) to 1.9.9.5+20130622git7de15e7a-1ubuntu1
libjavascriptcoregtk-1.0-0 (2.1.90.1-1~saucy1) to 2.2.0-2~saucy1
libjavascriptcoregtk-3.0-0 (2.1.90.1-1~saucy1) to 2.2.0-2~saucy1
libjson-c2 (0.11-2ubuntu1) to 0.11-3ubuntu1
libjson0 (0.11-2ubuntu1) to 0.11-3ubuntu1
libkeyutils1 (1.5.5-7) to 1.5.6-1
libkmod2 (9-3ubuntu1) to 15-0ubuntu2
libkpathsea6 (2013.20130529.30792-1build2) to 2013.20130729.30972-2
liblapack3 (3.4.2+dfsg-2) to 3.4.2+dfsg-4
liblapack3gf (3.4.2+dfsg-2) to 3.4.2+dfsg-4
libldap-2.4-2 (2.4.31-1+nmu2ubuntu3) to 2.4.31-1+nmu2ubuntu4
liblightdm-gobject-1-0 (1.8.2-0ubuntu1) to 1.9.0-0ubuntu1
liblist-moreutils-perl (0.33-1build2) to 0.33-1build3
liblocale-gettext-perl (1.05-7build2) to 1.05-7build3
libmagickcore5 (8:6.7.7.10-5ubuntu3) to 8:6.7.7.10-5ubuntu4
libmagickcore5-extra (8:6.7.7.10-5ubuntu3) to 8:6.7.7.10-5ubuntu4
libmagickwand5 (8:6.7.7.10-5ubuntu3) to 8:6.7.7.10-5ubuntu4
libmail-spf-perl (2.9.0-1) to 2.9.0-2
libmhash2 (0.9.9.9-2) to 0.9.9.9-4
libmodule-implementation-perl (0.06-1) to 0.07-1
libmono-addins-gui0.2-cil (0.6.2-2) to 1.0+git20130406.adcd75b-3
libmono-addins0.2-cil (0.6.2-2) to 1.0+git20130406.adcd75b-3
libmpfr4 (3.1.1-2) to 3.1.2-1
libmtp-common (1.1.6-2) to 1.1.6-20-g1b9f164-1ubuntu2
libmtp-runtime (1.1.6-2) to 1.1.6-20-g1b9f164-1ubuntu2
libmtp9 (1.1.6-2) to 1.1.6-20-g1b9f164-1ubuntu2
libmutter0c (3.10.1+git20131014.badebfae-0ubuntu1~13.10~ricotz0) to 3.10.1.1-0ubuntu1~saucy1
libneon27-gnutls (0.29.6-3) to 0.30.0-1
libnet-dbus-perl (1.0.0-2) to 1.0.0-2build1
libnet-dns-perl (0.68-1.2) to 0.68-1.2build1
libnet-domain-tld-perl (1.69-1) to 1.70-1
libnet-ssleay-perl (1.55-1) to 1.55-1build1
libnetaddr-ip-perl (4.062+dfsg-1) to 4.062+dfsg-1build1
libnetfilter-conntrack3 (1.0.3-1) to 1.0.4-1
libnm-glib-vpn1 (0.9.8.4-0ubuntu1~saucy1) to 0.9.8.8-0ubuntu1~saucy1
libnm-glib4 (0.9.8.4-0ubuntu1~saucy1) to 0.9.8.8-0ubuntu1~saucy1
libnm-util2 (0.9.8.4-0ubuntu1~saucy1) to 0.9.8.8-0ubuntu1~saucy1
libnuma1 (2.0.8-3) to 2.0.9~rc5-1
libobjc4 (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
libopenvg1-mesa (9.2.1-1ubuntu3) to 9.2.2-1ubuntu1
liborc-0.4-0 (1:0.4.17-2) to 1:0.4.18-1
liborcus-0.6-0 (0.5.1-4ubuntu1) to 0.5.1-6ubuntu1
libpam-modules (1.1.3-8ubuntu3) to 1.1.3-10ubuntu1
libpam-modules-bin (1.1.3-8ubuntu3) to 1.1.3-10ubuntu1
libpam-runtime (1.1.3-8ubuntu3) to 1.1.3-10ubuntu1
libpam0g (1.1.3-8ubuntu3) to 1.1.3-10ubuntu1
libpango-1.0-0 (1.35.3-0ubuntu1~13.10~ricotz0) to 1.36.0-1ubuntu1~saucy1
libpango-perl (1.224-1) to 1.224-2
libpango1.0-0 (1.35.3-0ubuntu1~13.10~ricotz0) to 1.36.0-1ubuntu1~saucy1
libpangocairo-1.0-0 (1.35.3-0ubuntu1~13.10~ricotz0) to 1.36.0-1ubuntu1~saucy1
libpangoft2-1.0-0 (1.35.3-0ubuntu1~13.10~ricotz0) to 1.36.0-1ubuntu1~saucy1
libpangoxft-1.0-0 (1.35.3-0ubuntu1~13.10~ricotz0) to 1.36.0-1ubuntu1~saucy1
libparams-classify-perl (0.013-4build1) to 0.013-4build2
libparams-validate-perl (1.06-1) to 1.06-1build1
libpathplan4 (2.26.3-15ubuntu4) to 2.34.0-0ubuntu4
libpci3 (1:3.1.9-6ubuntu9) to 1:3.1.9-6ubuntu11
libpisock9 (0.12.5-5ubuntu2) to 0.12.5-5ubuntu3
libplist1 (1.8-2) to 1.10-1
libportaudio2 (19+svn20111121-1build1) to 19+svn20111121-2
libpthread-stubs0-dev (0.3-3) to 0.3-4
libpurple-bin (1:2.10.7-0ubuntu4.1) to 1:2.10.7-0ubuntu4.2
libpurple0 (1:2.10.7-0ubuntu4.1) to 1:2.10.7-0ubuntu4.2
libqt4-dbus (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-declarative (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-designer (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-help (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-network (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-opengl (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-script (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-scripttools (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-sql (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-sql-mysql (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-sql-sqlite (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-svg (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-test (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-xml (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqt4-xmlpatterns (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqtcore4 (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libqtgui4 (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
libquadmath0 (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
libqupzilla1 (1.4.1-1) to 1.4.4-2
libquvi-scripts (0.4.18-1) to 0.4.19-1
libraptor2-0 (2.0.9-1) to 2.0.10-1
libreoffice (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-base (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-base-core (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-calc (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-common (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-core (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-draw (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-emailmerge (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-gnome (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-gtk (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-help-en-us (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-impress (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-java-common (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-l10n-en-za (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-math (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-ogltrans (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-pdfimport (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-presentation-minimizer (1.0.4+LibO4.1.2~rc3-0ubuntu1) to 1.0.4+LibO4.1.2~rc3-0ubuntu2
libreoffice-report-builder-bin (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-style-human (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-style-tango (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
libreoffice-writer (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
librhythmbox-core8 (3.0.1-0ubuntu1~14.04~ricotz0) to 3.0.1-1ubuntu2
libroar-compat2 (1.0~beta9-2) to 1.0~beta10-1
libroar2 (1.0~beta9-2) to 1.0~beta10-1
librpm3 (4.11.1-2) to 4.11.1-3
librpmbuild3 (4.11.1-2) to 4.11.1-3
librpmio3 (4.11.1-2) to 4.11.1-3
librpmsign1 (4.11.1-2) to 4.11.1-3
librsvg2-2 (2.37.0-0ubuntu1~saucy1) to 2.40.0-1~saucy1
librsvg2-common (2.37.0-0ubuntu1~saucy1) to 2.40.0-1~saucy1
libsane-hpaio (3.13.9-1) to 3.13.9-2
libsbc1 (1.1-1) to 1.1-2
libselinux1 (2.1.13-2) to 2.1.13-3
libsemanage-common (2.1.10-2) to 2.1.10-3
libsemanage1 (2.1.10-2) to 2.1.10-3
libsnmp-base (5.7.2~dfsg-8ubuntu1) to 5.7.2~dfsg-8ubuntu2
libsnmp30 (5.7.2~dfsg-8ubuntu1) to 5.7.2~dfsg-8ubuntu2
libsocket6-perl (0.23-1build3) to 0.23+ds-0+nmu1
libsoundtouch0 (1.7.1-2) to 1.7.1-4
libsoup-gnome2.4-1 (2.42.2-6) to 2.44.1-1
libsoup2.4-1 (2.42.2-6) to 2.44.1-1
libsqlite3-0 (3.7.17-1ubuntu1) to 3.8.0.2-1ubuntu1
libstdc++-4.8-dev (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
libstdc++6 (4.8.1-10ubuntu8) to 4.8.2-1ubuntu2
libstdc++6-4.7-dev (4.7.3-7ubuntu3) to 4.7.3-8ubuntu1
libsub-name-perl (0.05-1build3) to 0.05-1build4
libtaglib2.1-cil (2.1.0.0-2) to 2.1.0.0-3
libtalloc2 (2.0.8-0.1) to 2.1.0-1
libtar0 (1.2.19-1) to 1.2.20-1
libtdb1 (1.2.11-2.1) to 1.2.12-1
libtelepathy-glib0 (0.20.4-1) to 0.22.0-1
libtelepathy-logger3 (0.8.0-1) to 0.8.0-2
libtevent0 (0.9.18-1) to 0.9.19-1
libtext-charwidth-perl (0.04-7build2) to 0.04-7build3
libtext-iconv-perl (1.7-5build1) to 1.7-5build2
libtry-tiny-perl (0.16-1) to 0.18-1
libtxc-dxtn-s2tc0 (0~git20121227-1) to 0~git20121227-2
libudisks2-0 (2.1.0-4) to 2.1.1-1~saucy1
libunicode-string-perl (2.09-5) to 2.09-5build1
libupower-glib1 (0.9.22-1ubuntu1) to 0.9.23-2
libupstart1 (1.10-0ubuntu7) to 1.10-0ubuntu8
libusb-1.0-0 (2:1.0.16-3) to 2:1.0.17-1
libusbmuxd2 (1.0.8-1ubuntu1) to 1.0.8-2ubuntu1
libuuid-perl (0.02-5) to 0.05-1
libv4l-0 (0.8.9-4) to 1.0.0-1
libv4lconvert0 (0.8.9-4) to 1.0.0-1
libvlc5 (2.2.0~~git20131017+r3084-0~r106~ubuntu13.10.1) to 2.2.0~~git20131023+r3097-0~r111~ubuntu13.10.1
libvo-aacenc0 (0.1.2-1) to 0.1.3-1
libvo-amrwbenc0 (0.1.2-1) to 0.1.3-1
libvte-2.90-9 (1:0.34.8-0ubuntu1~saucy1) to 1:0.34.8-1ubuntu1
libvte-2.90-common (1:0.34.8-0ubuntu1~saucy1) to 1:0.34.8-1ubuntu1
libvte-2.90-doc (1:0.34.8-0ubuntu1~saucy1) to 1:0.34.8-1ubuntu1
libwebkitgtk-1.0-0 (2.1.90.1-1~saucy1) to 2.2.0-2~saucy1
libwebkitgtk-1.0-common (2.1.90.1-1~saucy1) to 2.2.0-2~saucy1
libwebkitgtk-3.0-0 (2.1.90.1-1~saucy1) to 2.2.0-2~saucy1
libwebkitgtk-3.0-common (2.1.90.1-1~saucy1) to 2.2.0-2~saucy1
libwxsqlite3-2.8-0 (3.0.0.1~dfsg0-2) to 3.0.5~dfsg0-1
libx11-6 (2:1.6.1-1ubuntu1) to 2:1.6.1-1ubuntu2
libx11-data (2:1.6.1-1ubuntu1) to 2:1.6.1-1ubuntu2
libx11-dev (2:1.6.1-1ubuntu1) to 2:1.6.1-1ubuntu2
libx11-doc (2:1.6.1-1ubuntu1) to 2:1.6.1-1ubuntu2
libx11-xcb-dev (2:1.6.1-1ubuntu1) to 2:1.6.1-1ubuntu2
libx11-xcb1 (2:1.6.1-1ubuntu1) to 2:1.6.1-1ubuntu2
libxatracker1 (9.2.1-1ubuntu3) to 9.2.2-1ubuntu1
libxfce4ui-1-0 (4.10.0-3) to 4.10.0-5
libxml-parser-perl (2.41-1build2) to 2.41-1build3
libxmmsclient-glib1 (0.8+dfsg-6) to 0.8+dfsg-8
libxmmsclient6 (0.8+dfsg-6) to 0.8+dfsg-8
libxres1 (2:1.0.6-1+deb7u1) to 2:1.0.7-1
libxtables10 (1.4.18-1.1ubuntu1) to 1.4.20-2ubuntu1
libyaml-tiny-perl (1.51-2) to 1.56-1
libyelp0 (3.8.1-0ubuntu2) to 3.10.1-1~saucy1
libzbar0 (0.10+doc-9) to 0.10+doc-9build1
libzvbi-common (0.2.33-7) to 0.2.35-2
libzvbi0 (0.2.33-7) to 0.2.35-2
lightdm (1.8.2-0ubuntu1) to 1.9.0-0ubuntu1
linux-firmware (1.116) to 1.117
m4 (1.4.16-5) to 1.4.17-1
meld (1.8.1-1) to 1.8.2-1
mesa-common-dev (9.2.1-1ubuntu3) to 9.2.2-1ubuntu1
miredo (1.2.3-1.1) to 1.2.6-1
module-init-tools (9-3ubuntu1) to 15-0ubuntu2
mtr-tiny (0.85-1) to 0.85-2
mutter (3.10.1+git20131014.badebfae-0ubuntu1~13.10~ricotz0) to 3.10.1.1-0ubuntu1~saucy1
mutter-common (3.10.1+git20131014.badebfae-0ubuntu1~13.10~ricotz0) to 3.10.1.1-0ubuntu1~saucy1
nautilus-dropbox (1.4.0-3) to 1.6.0-1
normalize-audio (0.7.7-11) to 0.7.7-12
pciutils (1:3.1.9-6ubuntu9) to 1:3.1.9-6ubuntu11
perl (5.14.2-21build1) to 5.18.1-4
perl-base (5.14.2-21build1) to 5.18.1-4
perl-modules (5.14.2-21build1) to 5.18.1-4
pidgin (1:2.10.7-0ubuntu4.1) to 1:2.10.7-0ubuntu4.2
pidgin-data (1:2.10.7-0ubuntu4.1) to 1:2.10.7-0ubuntu4.2
printer-driver-escpr (1.2.3-1) to 1.2.3-2
printer-driver-hpcups (3.13.9-1) to 3.13.9-2
printer-driver-hpijs (3.13.9-1) to 3.13.9-2
printer-driver-m2300w (0.51-9) to 0.51-10
printer-driver-postscript-hp (3.13.9-1) to 3.13.9-2
printer-driver-ptouch (1.3-6) to 1.3-7
printer-driver-pxljr (1.4+repack0-1) to 1.4+repack0-2
procps (1:3.3.3-2ubuntu8) to 1:3.3.8-2ubuntu1
ptouch-driver (1.3-6) to 1.3-7
pxljr (1.4+repack0-1) to 1.4+repack0-2
python-apt (0.8.9.1ubuntu1) to 0.9.1
python-apt-common (0.8.9.1ubuntu1) to 0.9.1
python-aptdaemon (1.1.1-0ubuntu3) to 1.1.1-1ubuntu1
python-aptdaemon-gtk (1.1.1-0ubuntu3) to 1.1.1-1ubuntu1
python-aptdaemon.gtk3widgets (1.1.1-0ubuntu3) to 1.1.1-1ubuntu1
python-aptdaemon.gtkwidgets (1.1.1-0ubuntu3) to 1.1.1-1ubuntu1
python-boto (2.9.6-1) to 2.10.0-1
python-crypto (2.6-5) to 2.6.1-2
python-cupshelpers (1.4.2+20130920-0ubuntu1) to 1.4.2+20130920-0ubuntu2
python-egenix-mxdatetime (3.2.5-1) to 3.2.6-1
python-egenix-mxtools (3.2.5-1) to 3.2.6-1
python-gi (3.10.0-1ubuntu1) to 3.10.1-1
python-gi-cairo (3.10.0-1ubuntu1) to 3.10.1-1
python-gobject (3.10.0-1ubuntu1) to 3.10.1-1
python-keyring (1.6-1) to 2.1-1
python-pam (0.4.2-13ubuntu6) to 0.4.2-13.1ubuntu1
python-requests (1.2.3-1) to 2.0.0-1
python-six (1.3.0-1) to 1.4.1-1
python-sqlite (1.0.1-9) to 1.0.1-10
python-ubuntu-sso-client (13.10-0ubuntu1) to 13.10-0ubuntu2
python-urllib3 (1.6-2) to 1.7.1-1
python3-apt (0.8.9.1ubuntu1) to 0.9.1
python3-aptdaemon (1.1.1-0ubuntu3) to 1.1.1-1ubuntu1
python3-aptdaemon.gtk3widgets (1.1.1-0ubuntu3) to 1.1.1-1ubuntu1
python3-crypto (2.6-5) to 2.6.1-2
python3-distupgrade (1:0.205) to 1:0.207
python3-gi (3.10.0-1ubuntu1) to 3.10.1-1
python3-gi-cairo (3.10.0-1ubuntu1) to 3.10.1-1
python3-mako (0.8.1-1) to 0.9.0-1
python3-markupsafe (0.15-1build3) to 0.18-1
python3-six (1.3.0-1) to 1.4.1-1
python3-uno (1:4.1.2~rc3-0ubuntu1) to 1:4.1.2~rc3-0ubuntu2
qdbus (4:4.8.4+dfsg-0ubuntu18) to 4:4.8.4+dfsg-0ubuntu19
qpdf (4.2.0-2) to 5.0.1-1
qtdeclarative5-cordova-2.8-plugin (2.8.0+13.10.20130917.1-0ubuntu1) to 2.8.0+14.04.20131024.4-0ubuntu1
qupzilla (1.4.1-1) to 1.4.4-2
rfkill (0.4-2ubuntu1) to 0.5-1ubuntu1
rhythmbox (3.0.1-0ubuntu1~14.04~ricotz0) to 3.0.1-1ubuntu2
rhythmbox-data (3.0.1-0ubuntu1~14.04~ricotz0) to 3.0.1-1ubuntu2
rhythmbox-mozilla (3.0.1-0ubuntu1~14.04~ricotz0) to 3.0.1-1ubuntu2
rhythmbox-plugins (3.0.1-0ubuntu1~14.04~ricotz0) to 3.0.1-1ubuntu2
rpm (4.11.1-2) to 4.11.1-3
rpm-common (4.11.1-2) to 4.11.1-3
rpm2cpio (4.11.1-2) to 4.11.1-3
ruby-locale (2.0.5-6) to 2.0.8-1
ruby-text (1.0.3-1) to 1.2.1-1
sed (4.2.2-1ubuntu1) to 4.2.2-2ubuntu1
sqlite3 (3.7.17-1ubuntu1) to 3.8.0.2-1ubuntu1
sudo (1.8.6p3-0ubuntu3) to 1.8.8-2ubuntu1
sysstat (10.1.6-2) to 10.1.7-1
system-config-printer-common (1.4.2+20130920-0ubuntu1) to 1.4.2+20130920-0ubuntu2
system-config-printer-gnome (1.4.2+20130920-0ubuntu1) to 1.4.2+20130920-0ubuntu2
system-config-printer-udev (1.4.2+20130920-0ubuntu1) to 1.4.2+20130920-0ubuntu2
tdb-tools (1.2.11-2.1) to 1.2.12-1
telepathy-haze (0.6.0-1) to 0.8.0-1
telepathy-logger (0.8.0-1) to 0.8.0-2
ttf-liberation (1.07.2-6ubuntu1) to 1.07.3-3
ubuntu-release-upgrader-core (1:0.205) to 1:0.207
ubuntu-release-upgrader-gtk (1:0.205) to 1:0.207
ubuntu-sso-client (13.10-0ubuntu1) to 13.10-0ubuntu2
ubuntu-sso-client-qt (13.10-0ubuntu1) to 13.10-0ubuntu2
udisks2 (2.1.0-4) to 2.1.1-1~saucy1
unar (1.7-1) to 1.8.1-1
uno-libs3 (4.1.2~rc3-0ubuntu1) to 4.1.2~rc3-0ubuntu2
upower (0.9.22-1ubuntu1) to 0.9.23-2
upstart (1.10-0ubuntu7) to 1.10-0ubuntu8
ure (4.1.2~rc3-0ubuntu1) to 4.1.2~rc3-0ubuntu2
usbmuxd (1.0.8-1ubuntu1) to 1.0.8-2ubuntu1
vim-common (2:7.4.000-1ubuntu2) to 2:7.4.052-1ubuntu1
vim-tiny (2:7.4.000-1ubuntu2) to 2:7.4.052-1ubuntu1
vinagre (3.10.0-0ubuntu1~saucy1) to 3.10.1-1~saucy1
vlc (2.2.0~~git20131017+r3084-0~r106~ubuntu13.10.1) to 2.2.0~~git20131023+r3097-0~r111~ubuntu13.10.1
vlc-data (2.2.0~~git20131017+r3084-0~r106~ubuntu13.10.1) to 2.2.0~~git20131023+r3097-0~r111~ubuntu13.10.1
vlc-nox (2.2.0~~git20131017+r3084-0~r106~ubuntu13.10.1) to 2.2.0~~git20131023+r3097-0~r111~ubuntu13.10.1
vlc-plugin-notify (2.2.0~~git20131017+r3084-0~r106~ubuntu13.10.1) to 2.2.0~~git20131023+r3097-0~r111~ubuntu13.10.1
vlc-plugin-pulse (2.2.0~~git20131017+r3084-0~r106~ubuntu13.10.1) to 2.2.0~~git20131023+r3097-0~r111~ubuntu13.10.1
w3m (0.5.3-11) to 0.5.3-12
xdiagnose (3.6.1) to 3.6.2
xfce-keyboard-shortcuts (4.10.0-3) to 4.10.0-5
xmms2-core (0.8+dfsg-6) to 0.8+dfsg-8
xmms2-plugin-alsa (0.8+dfsg-6) to 0.8+dfsg-8
xmms2-plugin-id3v2 (0.8+dfsg-6) to 0.8+dfsg-8
xmms2-plugin-mad (0.8+dfsg-6) to 0.8+dfsg-8
xmms2-plugin-vorbis (0.8+dfsg-6) to 0.8+dfsg-8
xserver-common (2:1.14.3-3ubuntu2) to 2:1.14.3-3ubuntu3
xserver-xephyr (2:1.14.3-3ubuntu2) to 2:1.14.3-3ubuntu3
xserver-xorg-core (2:1.14.3-3ubuntu2) to 2:1.14.3-3ubuntu3
yelp (3.8.1-0ubuntu2) to 3.10.1-1~saucy1
yelp-tools (3.6.1-2) to 3.10.0-1
yelp-xsl (3.8.1-2) to 3.10.1-1
zip (3.0-7) to 3.0-8

Installed the following packages:
geoclue-gypsy (0.12.99-2ubuntu1)
gir1.2-gnomekeyring-1.0 (3.8.0-2)
libboost-date-time1.54.0 (1.54.0-4~ubuntu2)
libboost-iostreams1.54.0 (1.54.0-4~ubuntu2)
libboost-system1.54.0 (1.54.0-4~ubuntu2)
libcdt5 (2.34.0-0ubuntu4)
libcgraph6 (2.34.0-0ubuntu4)
libdb5.3 (5.3.21-2)
libgypsy0 (0.8-0ubuntu6)
libperl5.18 (5.18.1-4)
libprocps1 (1:3.3.8-2ubuntu1)
libproxy-tools (0.4.11-0ubuntu4)
libqpdf13 (5.0.1-1)
libvlccore7 (2.2.0~~git20131023+r3097-0~r111~ubuntu13.10.1)

```

BTW, nothing is being held back, and everything is working fine...

---

### Post by QDR06VV9 on 2013-10-25
> **philinux said:**
> Cheers. I have partners and extras disable and all src's.

What about gnome3 ppa & gnome next & Ricotz staging and testing?
They certainly keeps you on your toes...LOL
Regards

---

### Post by philinux on 2013-10-26
> **runrickus said:**
> What about gnome3 ppa & gnome next & Ricotz staging and testing?
They certainly keeps you on your toes...LOL
Regards

I like to keep to a vanilla install for testing purposes. I'm still getting same errors too.

---

### Post by philinux on 2013-10-26
Ok I've reinstalled from the daily iso and added those lines to top of /usr/share/python-apt/templates/Ubuntu.info as it was still missing the trusty bits.

So is it fine to go ahead and do an upgrade? Or wait.

```
ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 14.04 'Trusty Tahr'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: trusty
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 14.04 'Trusty Tahr'

Suite: trusty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*14.04
MatchURI: cdrom:\[Ubuntu.*14.04
Description: Cdrom with Ubuntu 14.04 'Trusty Tahr'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb
Description: Recommended updates

Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb
Description: Pre-released updates

Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb
Description: Unsupported updates

Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates
```

Still getting these. 
```
W: Conflicting distribution: http://gb.archive.ubuntu.com devel Release (expected devel but got trusty)
W: Conflicting distribution: http://gb.archive.ubuntu.com devel-updates Release (expected devel-updates but got trusty)
W: Conflicting distribution: http://gb.archive.ubuntu.com devel-backports Release (expected devel-backports but got trusty)
W: Conflicting distribution: http://security.ubuntu.com devel-security Release (expected devel-security but got trusty)

```

---

### Post by grahammechanical on 2013-10-26
Are the repositories pointing to devel or trusty? I have just used the sed command to switch an updated saucy over to trusty and I do not get that conflicting distribution error. Nor, do I get it on an fresh install of trusty from the 23rd. In both installations ubuntu.info has references for both devel and trusty with devel at the top. They have trusty repositories.

I have another install of saucy that had its repositories pointing to devel and that has updated to trusty. I have not needed to edit ubuntu.info in the way that you have. An update a day ago replaced ubuntu.info and the present ubuntu.info has references for both devel and trusty but it still gets those conflicting distribution errors. It has devel repositories that are listed in the Other Software tab as Ubuntu Development Series.

I think what we are getting is something in preparation for the 14.04 development branch rolling into the 14.10 development branch.

Regards.

---

### Post by philinux on 2013-10-26
> **grahammechanical said:**
> Are the repositories pointing to devel or trusty? I have just used the sed command to switch an updated saucy over to trusty and I do not get that conflicting distribution error. Nor, do I get it on an fresh install of trusty from the 23rd. In both installations ubuntu.info has references for both devel and trusty with devel at the top. They have trusty repositories.

I have another install of saucy that had its repositories pointing to devel and that has updated to trusty. I have not needed to edit ubuntu.info in the way that you have. An update a day ago replaced ubuntu.info and the present ubuntu.info has references for both devel and trusty but it still gets those conflicting distribution errors. It has devel repositories that are listed in the Other Software tab as Ubuntu Development Series.

I think what we are getting is something in preparation for the 14.04 development branch rolling into the 14.10 development branch.

Regards.
Here it is.
```
cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20131021.1)]/ devel main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ devel main restricted
#deb-src http://gb.archive.ubuntu.com/ubuntu/ devel main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ devel-updates main restricted
#deb-src http://gb.archive.ubuntu.com/ubuntu/ devel-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ devel universe
#deb-src http://gb.archive.ubuntu.com/ubuntu/ devel universe
deb http://gb.archive.ubuntu.com/ubuntu/ devel-updates universe
#deb-src http://gb.archive.ubuntu.com/ubuntu/ devel-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ devel multiverse
#deb-src http://gb.archive.ubuntu.com/ubuntu/ devel multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ devel-updates multiverse
#deb-src http://gb.archive.ubuntu.com/ubuntu/ devel-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ devel-backports main restricted universe multiverse
#deb-src http://gb.archive.ubuntu.com/ubuntu/ devel-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu devel-security main restricted
#deb-src http://security.ubuntu.com/ubuntu devel-security main restricted
deb http://security.ubuntu.com/ubuntu devel-security universe
#deb-src http://security.ubuntu.com/ubuntu devel-security universe
deb http://security.ubuntu.com/ubuntu devel-security multiverse
#deb-src http://security.ubuntu.com/ubuntu devel-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu devel partner
# deb-src http://archive.canonical.com/ubuntu devel partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
#deb http://extras.ubuntu.com/ubuntu devel main
#deb-src http://extras.ubuntu.com/ubuntu devel main
```

---

### Post by grahammechanical on 2013-10-26
Yes, it seems we get those errors when the software sources are devel. We do not get them when the software sources are trusty. I think it will be an interesting experiment to see what happens to an install of Ubuntu with devel repositories over the next six months.

Regards.

---

### Post by philinux on 2013-10-26
> **grahammechanical said:**
> Yes, it seems we get those errors when the software sources are devel. We do not get them when the software sources are trusty. I think it will be an interesting experiment to see what happens to an install of Ubuntu with devel repositories over the next six months.

Regards.

Yes interesting development. So just go ahead and dist-upgrade even with those errors?

---

### Post by ventrical on 2013-10-26
I just did a fresh install on a  partiton <something else>, sudo update/dist upgrade and got this.

```

ventrical@ventrical-MS-7798:~$ sudo apt-get update
[sudo] password for ventrical: 
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://extras.ubuntu.com trusty InRelease                 
Hit http://security.ubuntu.com trusty-security Release.gpg     
Ign http://extras.ubuntu.com trusty Release.gpg                
Hit http://security.ubuntu.com trusty-security Release         
Ign http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security/main Sources    
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Err http://extras.ubuntu.com trusty/main Sources                               
  404  Not Found
Err http://extras.ubuntu.com trusty/main i386 Packages                         
  404  Not Found
Ign http://extras.ubuntu.com trusty/main Translation-en_CA     
Ign http://extras.ubuntu.com trusty/main Translation-en        
Ign http://security.ubuntu.com trusty-security/main Translation-en_CA
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_CA
Ign http://security.ubuntu.com trusty-security/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com trusty InRelease        
Ign http://ca.archive.ubuntu.com trusty-updates InRelease
Ign http://ca.archive.ubuntu.com trusty-backports InRelease
Get:1 http://ca.archive.ubuntu.com trusty Release.gpg [933 B]
Hit http://ca.archive.ubuntu.com trusty-updates Release.gpg
Hit http://ca.archive.ubuntu.com trusty-backports Release.gpg
Get:2 http://ca.archive.ubuntu.com trusty Release [49.6 kB]
Hit http://ca.archive.ubuntu.com trusty-updates Release                        
Hit http://ca.archive.ubuntu.com trusty-backports Release                      
Get:3 http://ca.archive.ubuntu.com trusty/main Sources [1,017 kB]              
Get:4 http://ca.archive.ubuntu.com trusty/restricted Sources [4,759 B]         
Get:5 http://ca.archive.ubuntu.com trusty/universe Sources [6,267 kB]          
Get:6 http://ca.archive.ubuntu.com trusty/multiverse Sources [177 kB]          
Get:7 http://ca.archive.ubuntu.com trusty/main i386 Packages [1,250 kB]        
Get:8 http://ca.archive.ubuntu.com trusty/restricted i386 Packages [9,688 B]   
Get:9 http://ca.archive.ubuntu.com trusty/universe i386 Packages [5,769 kB]    
Get:10 http://ca.archive.ubuntu.com trusty/multiverse i386 Packages [135 kB]   
Hit http://ca.archive.ubuntu.com trusty/main Translation-en_CA                 
Hit http://ca.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ca.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://ca.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ca.archive.ubuntu.com trusty/universe Translation-en_CA             
Hit http://ca.archive.ubuntu.com trusty/universe Translation-en                
Hit http://ca.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://ca.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://ca.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://ca.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://ca.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://ca.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://ca.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://ca.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://ca.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://ca.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://ca.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://ca.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://ca.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://ca.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://ca.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://ca.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://ca.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://ca.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://ca.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://ca.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://ca.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://ca.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://ca.archive.ubuntu.com trusty/multiverse Translation-en_CA           
Ign http://ca.archive.ubuntu.com trusty/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com trusty-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com trusty-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com trusty-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com trusty-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com trusty-backports/main Translation-en_CA
Ign http://ca.archive.ubuntu.com trusty-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com trusty-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com trusty-backports/universe Translation-en_CA
Fetched 14.7 MB in 1min 3s (230 kB/s)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
ventrical@ventrical-MS-7798:~$ 

```

&

```

ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu development series
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: devel
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu development series

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: devel-security
ParentSuite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: devel-security
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb
Description: Recommended updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb
Description: Pre-released updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb
Description: Unsupported updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 14.04 'Trusty Tahr'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: trusty
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 14.04 'Trusty Tahr'

Suite: trusty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*14.04
MatchURI: cdrom:\[Ubuntu.*14.04
Description: Cdrom with Ubuntu 14.04 'Trusty Tahr'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb
Description: Recommended updates

Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb
Description: Pre-released updates

Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb
Description: Unsupported updates

Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

```

---

### Post by ventrical on 2013-10-26
> **philinux said:**
> Yes interesting development. So just go ahead and dist-upgrade even with those errors?


  Thats what I'm doing .. I just roll with it... and it seems to be ironing itself out.

---

### Post by philinux on 2013-10-26
> **ventrical said:**
> Thats what I'm doing .. I just roll with it... and it seems to be ironing itself out.

Figured that upgrade half hour ago.

What is the purpose of this file. /usr/share/python-apt/templates/Ubuntu.info

I've no devel bits in it at the top like yours.

---

### Post by ventrical on 2013-10-26
It's a template file that is sort of like a symlink that works in unison with the sources list .  If we don't have it we can't be directed to mirrors , urls and such to get updates. 


edit:

It is my assumption that the /devel/ is a psuedo vanilla pointer. You can use any word actually and it will roll you over to Trusty, but with the caveat of having those  conflicting error reports.

If I put:

```

[B]sudo sed -i 's/saucy/whatchmacallit/g' /etc/apt/sources.list

[/B]
```[B]

It will roll over to trusty tahr.


edit 

they are called 'repository templates'


[/B]

---

### Post by philinux on 2013-10-26
My /usr/share/python-apt/templates/Ubuntu.info

Is huge going all the way back to Warty!!

---

### Post by ventrical on 2013-10-26
> **philinux said:**
> My /usr/share/python-apt/templates/Ubuntu.info

Is huge going all the way back to Warty!!

Same here ... it just keeps appending itself. Honestly  why ? I don't know but I do know that the top section is the one that matters. python-apt is a reference to a compiler . etc.. so when some source files are being compiled for gtk it refers to that template file Ubuntu.info to set the repositories in conjunction with the sources.list. Thats why we can't just have the sources.list by sudo sed'ing because synaptic will break - until the Ubuntu.info file is updated.

  I am not familiar with how the developers at Canonical set their network frameworks up but I am investigating it and studying it ..


At this end .. so far .. so good .. no breakage as of yet...

---

### Post by ventrical on 2013-10-26
Ubutu.info is related to software-properties-gtk.

---

### Post by grahammechanical on 2013-10-26
There are other similar files in the usr/share/python-apt/templates folder - debian.info, debian.mirrors, gNewSense.info, gNewSense.mirrors, ubuntu.info and ubuntu.mirrors. And boy oh boy have we gone off topic! Our own secret little investigation that will never appear in any search index. :)

Regards.

My wild guess is that those info and mirror files act like an address book for software-properties-gtk.

---

### Post by ventrical on 2013-10-26
Overall, it gives me a better understanding of  how the sources.list, ubuntu.info file and the development release works so when we see new changes it will not be such a shocker.

Regards..

---

### Post by QDR06VV9 on 2013-10-26
> **ventrical said:**
> Overall, it gives me a better understanding of  how the sources.list, ubuntu.info file and the development release works [U][COLOR=#ff0000]so when we see new changes it will not be such a shocker.[/COLOR]
[/U]
Regards..

Your taking all the fun out of it now!LOL
Great work ventrical +1

---

### Post by ventrical on 2013-10-26
I am trying to be on my best behavious so I don't keep getting bumped to Other Linux OS or The Cafe ..oy .. it's a dungeon in there.... :)lol

---

