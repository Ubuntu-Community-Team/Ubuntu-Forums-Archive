---
title: "problem downloading FF3 on Gutsy"
date: 2008-07-07
forum: Ubuntuzilla
---

### Post by mr_git on 2008-07-07
Hi, I've used ubuntuzilla on versions of ubuntu from dapper onwards, and it's great - thanks for all your hard work on it nanotube!

I'm having a problem trying to install FF3 on Gutsy (using Ubuntuzilla version 4.5.0) - it looks like the script is failing to find the package name it wants to download, as I get this when it's trying to download the file with wget:

```

Retrieving package name for Firefox ...
Success!: [FILE]

Downloading Firefox archive from the Mozilla site

Warning: wildcards not supported in HTTP.
--10:35:40--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-GB/[FILE]
           => `[FILE]'

```

...this fails to work, as the filename should not be [FILE].

lines 389/90 look like they might be where this problem occurs:
```

self.packageFilename = self.util.getSystemOutput(executionstring="w3m -dump ftp://" + mirror + self.options.package + "/releases/" + self.releaseVersion + "/linux-i686/" + self.locList[self.locChoice] + " | grep '"      + self.options.package + "' | grep -v '\.asc' |grep -v 'ftp://' | awk '{print $1}'", numlines=1)
print "Success!: " + self.packageFilename

```

I've hacked that line, and set self.packageFilename = 'firefox-3.0.tar.bz2' - and the rest of the installation works fine from them on.

```

#self.packageFilename = self.util.getSystemOutput(executionstring="w3m -dump ftp://" + mirror + self.options.package + "/releases/" + self.releaseVersion + "/linux-i686/" + self.locList[self.locChoice] + " | grep '" + self.options.package + "' | grep -v '\.asc' |grep -v 'ftp://' | awk '{print $1}'", numlines=1)
self.packageFilename = 'firefox-3.0.tar.bz2'
print "Success!: " + self.packageFilename

```

Sorry I don't have time right now to figure out how to fix the problem properly - if it's going to affect other users, then hopefully the fix will be obvious to someone else.

---

### Post by nanotube on 2008-07-07
Hi,
hmm... could you please post the output of this command:
```
 w3m -dump ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US
```

---

### Post by mr_git on 2008-07-09
Hi, thanks for replying.

this only happens on my work machine, which is behind a proxy - hence the odd results. Here's the output:

```

$ w3m -dump ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US
FTP Directory: ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/
linux-i686/en-US/

[DIRUP] Parent Directory
[FILE] firefox-3.0.tar.bz2. . . . . . . Jun 10 19:07   8871K [DOWNLOAD]
[FILE] firefox-3.0.tar.bz2.asc. . . . . Jun 11 09:22    186  [DOWNLOAD]

&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;


Generated Wed, 09 Jul 2008 14:40:53 GMT by not.the.real.proxy.example.com (squid/
2.5.STABLE14)


```

I suppose that explains what was happening to me - not sure how easy it would be to get round this in the script (or if you want to cater for the different output of different proxy software - I'd have thought squid is pretty common though).

Thanks for looking at this.

---

### Post by nanotube on 2008-07-09
ah yea, that must be due to the proxy... 

well, i made the package-name-getter more generic, so now should work both on non-proxied and proxied systems. attaching the latest ubuntuzilla.py to this thread - could you please test it on your proxy machine (and the non-proxy one too, why not :)) and see if it works as advertised?

thanks for taking the time to report this and to help me in solving this problem. :)

---

### Post by mr_git on 2008-07-10
Hi, thanks again for working to fix this issue - good news first then...

5.4.1 works great now on the machine behind the proxy:

```

Retrieving package name for Firefox ...
Success!: firefox-3.0.tar.bz2

Downloading Firefox archive from the Mozilla site

--13:19:43--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-GB/firefox-3.0.tar.bz2
           => `firefox-3.0.tar.bz2'
Resolving proxy.example.com... 172.18.5.61
Connecting to proxy.example.com|172.18.5.61|:3128... connected.
Proxy request sent, awaiting response... 200 OK
Length: 8,861,824 (8.5M) [application/octet-stream]

19% [====================================>

```

Well done - looks like ubuntuzilla works behind a proxy now :-)

...bad news is there's a problem on a machine which is not behind a proxy (this is hardy, not gutsy):

```

Retrieving list of available localizations for Firefox ...
w3m -dump ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.

```

I'm not sure if this error is even related to the first one?

If I run the w3m command by itself:

```

$ w3m -dump ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/.

```

...and the same result without the pipe to grep.

I can load the URL okay in, for example, konqueror though ([ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/))

```

$ w3m -version
w3m version w3m/0.5.1+cvs-1.968, options lang=en,m17n,image,color,ansi-color,mouse,gpm,menu,cookie,ssl,ssl-verify,external-uri-loader,w3mmailer,nntp,gopher,ipv6,alarm,mark,migemo

```

I'd be happy to start another thread is this issue is not related, and that would let you mark the proxy problem as fixed etc...

---

### Post by nanotube on 2008-07-10
Hi!
glad it's fixed.
about the problem with releases.mozilla.org - i'm seeing it too, started seeing it some time ago. i think it's some configuration problem on releases.mozilla.org itself, because i can't open that ftp link in firefox either, nor in w3m. 

since i have a bunch of different mirrors that can be used, the error is not "fatal", since it just goes on and tries the next mirror, and it works, so i haven't bothered to figure out what they did with releases.mozilla.org to break it. ;)

anyway, i'll make the 4.5.1 release, thanks for reporting the bug and for testing the fix!

---

### Post by Zajeec5u on 2008-09-01
Hi All,

> **nanotube said:**
> Hi,
hmm... could you please post the output of this command:
```
 w3m -dump ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US
```

I can't update to 3.0.1 on 7.10 and get the same timeout with this command like as with the script [4.5.2]
I tried a couple of things (to see if it's a network related thing etc.) and now it appears as if *w3m *likes to have a trailing "**/**" at the end of the line.

IOW,  
*w3m -dump [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US)*
gets a timeout (*[COLOR="Navy"]w3m: Can't load [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US).[/COLOR]*), while 
*w3m -dump [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/)*
replies instantly:
[I][COLOR="Navy"]Index of [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/)

[Upper Directory]
firefox-3.0.tar.bz2 . . Jun 10 19:07  8,66M
firefox-3.0.tar.bz2.asc Jun 11 09:22    186[/COLOR]
[/I]

Before I dig further and reinvent the weel, does that sound familiar?

Thanks a lot (also for that brilliant work!), 
   Michael.

---

### Post by Zajeec5u on 2008-09-01
> **Noiseconformist said:**
> 
it appears as if *w3m *likes to have a trailing "**/**" at the end of the line.

I further checked if there's a difference in using *ftp *or *http*.
Since *http *worked for a quick and dirty workaround I changed the protocol identifier for *executionstring *in line 389 of the script from *ftp *to *http*:

*...[COLOR="Navy"](executionstring="w3m -dump http://" + mirror + [/COLOR]...*

This hack (not advisible since I don't know this script!) worked and installed FF 3.0.1 for me.
I'm aware of that any new release of *ubuntuzilla *will overwrite this.
Admittedly I've no clue what's going on, hence I'm pretty curious . 
Any idea? 

Thanks a lot, Michael.

[UPDATE]
I again looked at the executionstring where to insert the final slash and changed line 389 to

         ```
self.packageFilename = self.util.getSystemOutput(executionstring="w3m -dump ftp://" + mirror + self.options.package + "/releases/" + self.releaseVersion + "/linux-i686/" + self.locList[self.locChoice] + "/" + " | grep '" + self.options.package + "' | grep -v '\.asc' |grep -v 'ftp://' | awk '{ print substr($0,index($0, \"" + self.options.package + "\"))}' | awk '{print $1}' | sed -e 's/\.*$//'", numlines=1)
```

I'm just wondering why it's (obviously?) just me encountering this problem.

---

### Post by nanotube on 2008-09-04
Hi,

indeed, weird - the w3m dump works for me without the trailing '/' (and with the trailing '/' as well, by the way). And I have not seen anyone else ever report this... Would you by any chance happen to be behind some proxy server? Or have any other unusual network configuration?

Let me know if you can think of anything.

At any rate, it seems that adding a trailing '/' doesn't hurt anything (works both ways for me without any difference), so I just might add that to the next release for "just in case"... :)

---

### Post by Zajeec5u on 2008-09-26
> **nanotube said:**
> Hi,

indeed, weird - the w3m dump works for me without the trailing '/' (and with the trailing '/' as well, by the way). And I have not seen anyone else ever report this... Would you by any chance happen to be behind some proxy server? Or have any other unusual network configuration?

Let me know if you can think of anything.

So far I only had a chance to check if it's just my machine or not:
On a colleague's 7.10 installation within the same network segment the exactly same happens:
```

$ w3m -dump ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US
w3m: Can't load ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US.
$ w3m -dump ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/
Index of ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/
en-US/

[Upper Directory]
firefox-3.0.tar.bz2 . . Jun 10 19:07  8,66M
firefox-3.0.tar.bz2.asc Jun 11 09:22    186

$ uname -a
Linux mubuntu 2.6.22-15-generic #1 SMP Wed Aug 20 18:39:13 UTC 2008 i686 GNU/Linux

```

I'm trying to find out what could be the reason. Will take some while though. Funnily enough since the last update I did (somewhen in April) we deactivated the squid proxy ... :confused:

> 
At any rate, it seems that adding a trailing '/' doesn't hurt anything (works both ways for me without any difference), so I just might add that to the next release for "just in case"... :)

A **_BIG_** **thank you** for that, makes living a lot easier with that!

   :-)  Michael.

---

### Post by nanotube on 2008-10-20
Hi,
Please test this latest version and make sure it works as advertised. :)

See the changelog for details of all changes:
[http://ubuntuzilla.cvs.sourceforge.net/ubuntuzilla/ubuntuzilla/CHANGELOG.TXT?view=markup](http://ubuntuzilla.cvs.sourceforge.net/ubuntuzilla/ubuntuzilla/CHANGELOG.TXT?view=markup)

Please let me know how it goes. :)

---

### Post by nanotube on 2008-10-22
oops, forgot to attach the file. here it comes.

---

