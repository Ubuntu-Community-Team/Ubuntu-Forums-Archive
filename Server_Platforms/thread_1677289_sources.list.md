---
title: "sources.list"
date: 2011-01-28
forum: Server Platforms
---

### Post by JonCCrawley on 2011-01-28
Hi all, 

I am new to linux and I just got my openssh server up and going and now when I run update my comp gives me the list of error messages bellow.

How can i fix this?
 
```
ser@ubuntu:/etc/apt$ sudo apt-get update
Err [URL="http://security.ubuntu.com"]http://security.ubuntu.com maverick-security Release.gpg
Temporary failure resolving 'security.ubuntu.com'
Err [URL="http://security.ubuntu.com/ubuntu/"]http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Temporary failure resolving 'security.ubuntu.com'
Err [URL="http://security.ubuntu.com/ubuntu/"]http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Temporary failure resolving 'security.ubuntu.com'
Err URL="http://security.ubuntu.com/ubuntu/"]http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Temporary failure resolving 'security.ubuntu.com'
Err URL="http://security.ubuntu.com/ubuntu/"]http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Temporary failure resolving 'security.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com"]http://us.archive.ubuntu.com maverick Release.gpg
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://security.ubuntu.com/ubuntu/"]http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Temporary failure resolving 'security.ubuntu.com'
Err [URL="http://security.ubuntu.com/ubuntu/"]http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Temporary failure resolving 'security.ubuntu.com'
Err [URL="http://security.ubuntu.com/ubuntu/"]http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Temporary failure resolving 'security.ubuntu.com'
Err [URL="http://security.ubuntu.com/ubuntu/"]http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Temporary failure resolving 'security.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com"]http://us.archive.ubuntu.com maverick-updates Release.gpg
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Temporary failure resolving 'us.archive.ubuntu.com'
Err [URL="http://us.archive.ubuntu.com/ubuntu/"]http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2[/SIZE]*]("http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2")*[SIZE=2] Temporary failure resolving 'us.archive.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg[/SIZE]*]("http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg")*[SIZE=2] Temporary failure resolving 'security.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2[/SIZE]*]("http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2")*[SIZE=2] Temporary failure resolving 'security.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2[/SIZE]*]("http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2")*[SIZE=2] Temporary failure resolving 'security.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2[/SIZE]*]("http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2")*[SIZE=2] Temporary failure resolving 'security.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2[/SIZE]*]("http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2")*[SIZE=2] Temporary failure resolving 'security.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2[/SIZE]*]("http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2")*[SIZE=2] Temporary failure resolving 'security.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2[/SIZE]*]("http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2")*[SIZE=2] Temporary failure resolving 'security.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2[/SIZE]*]("http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2")*[SIZE=2] Temporary failure resolving 'security.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Failed to fetch [/SIZE]*[*[SIZE=2]http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2[/SIZE]*]("http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2")*[SIZE=2] Temporary failure resolving 'security.ubuntu.com'[/SIZE]*
*[SIZE=2]W: Some index files failed to download, they have been ignored, or old ones used instead.[/SIZE]*
*[SIZE=2]user@ubuntu:/etc/apt$[/SIZE]*
 
 
 
[FONT=Times New Roman][SIZE=3][COLOR=red]I think it is my sources.list file but I don&#8217;t know what to do to fix it I have attached a copy of that file as well[/COLOR][/SIZE][/FONT]
 
 
[FONT=Times New Roman]*[SIZE=2]# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted[/SIZE]*[/FONT]
 
[FONT=Times New Roman]*[SIZE=2]#deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]# newer versions of the distribution.[/SIZE]*[/FONT]
 
[FONT=Times New Roman]*[SIZE=2]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted[/SIZE]*[/FONT]
 
[FONT=Times New Roman]*[SIZE=2]## Major bug fix updates produced after the final release of the[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## distribution.[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted[/SIZE]*[/FONT]
 
[FONT=Times New Roman]*[SIZE=2]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## team. Also, please note that software in universe WILL NOT receive any[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## review or updates from the Ubuntu security team.[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe[/SIZE]*[/FONT]
 
[FONT=Times New Roman]*[SIZE=2]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## team, and may not be under a free licence. Please satisfy yourself as to[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## your rights to use the software. Also, please note that software in[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## multiverse WILL NOT receive any review or updates from the Ubuntu[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## security team.[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse[/SIZE]*[/FONT]
 
[FONT=Times New Roman]*[SIZE=2]## Uncomment the following two lines to add software from the 'backports'[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## repository.[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## N.B. software from this repository may not have been tested as[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## extensively as that contained in the main release, although it includes[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## newer versions of some applications which may provide useful features.[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## Also, please note that software in backports WILL NOT receive any review[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## or updates from the Ubuntu security team.[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse[/SIZE]*[/FONT]
 
[FONT=Times New Roman]*[SIZE=2]## Uncomment the following two lines to add software from Canonical's[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## 'partner' repository.[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## This software is not part of Ubuntu, but is offered by Canonical and the[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## respective vendors as a service to Ubuntu users.[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner[/SIZE]*[/FONT]
 
[FONT=Times New Roman]*[SIZE=2]## Uncomment the following two lines to add software from Ubuntu's[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## 'extras' repository.[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## This software is not part of Ubuntu, but is offered by third-party[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]## developers who want to ship their latest software.[/SIZE]*[/FONT]
[FONT=Times New Roman][SIZE=2]*# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main*[/SIZE][/FONT]
[FONT=Times New Roman]*[SIZE=2]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse[/SIZE]*[/FONT]
[FONT=Times New Roman]*[SIZE=2]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse[/SIZE]*[/FONT]
```

---

### Post by arrrghhh on 2011-01-28
For one, please put stuff you paste in ```
 brackets - makes it much MUCH easier to read.

Second, it seems like your internet connection can't resolve security.ubuntu.com (or any of the other sites).

Can you ping them?  [code]ping security.ubuntu.com
``` - if you can't you may have a DNS issue.  If you have a static IP address, you need to enter in DNS servers manually in your resolv.conf.

---

### Post by JonCCrawley on 2011-01-28
> **arrrghhh said:**
>  if you can't you may have a DNS issue. If you have a static IP address, you need to enter in DNS servers manually in your resolv.conf.
 I cant ping it.
```

user@ubuntu:~$ ping security.ubuntu.com
ping: unknown host security.ubuntu.com

```
 So how would i put them in the resolv.conf file. This is a copy of my curent one
```

nameserver 10.0.1.100
domain hsd1.co.comcast.net.
search hsd1.co.comcast.net.

```

---

### Post by arrrghhh on 2011-01-28
> **JonCCrawley said:**
> I cant ping it.
```

user@ubuntu:~$ ping security.ubuntu.com
ping: unknown host security.ubuntu.com

```
 So how would i put them in the resolv.conf file. This is a copy of my curent one
```

nameserver 10.0.1.100
domain hsd1.co.comcast.net.
search hsd1.co.comcast.net.

```

Well I would delete all of that out there, and you have some choices here.  You can use your ISP's DNS, you can use Google's, or you can use OpenDNS.  I prefer OpenDNS, but the choice is yours.

For Google:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

For OpenDNS:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Or you could put in all four, wouldn't hurt anything.

You'll have to look at your router to see what is coming in for your ISP's DNS if you want to use them...  I usually don't, because OpenDNS is usually so fast - however, I've had instances where the ISP's DNS server were better, so it's really up to you.  DNS servers on a server probably aren't so important, you just need basic name resolution really ;).

---

### Post by JonCCrawley on 2011-01-28
Thank you my frind :P

---

### Post by arrrghhh on 2011-01-28
> **JonCCrawley said:**
> Thank you my frind :P

I assume it's working?  Good to hear.

There's a link under the "Thread Tools" drop down menu to mark the thread [SOLVED].  Please do so if you feel that it is!

This issue caught me as well a while back... Just another thing to keep in mind when going to a static IP ;).

---

