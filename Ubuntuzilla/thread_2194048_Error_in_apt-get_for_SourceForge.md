---
title: "Error in apt-get for SourceForge"
date: 2013-12-16
forum: Ubuntuzilla
---

### Post by DPMR on 2013-12-16
In followed the guide lines on the site but after running sudo apt-get update I get an error.

W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release) 
Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

New at this so I don't really know what this means, as far as where I went wrong.

The instruction page is a little different than my verson, but it seamed to go well until I verified.

Any help would be great.

DPMR

---

### Post by raja.genupula on 2013-12-16
we would like to help you but its only possible with your sources list. show us your sources.list with

> cat /etc/apt/sources.list

---

### Post by DPMR on 2013-12-16
niverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main
deb-src [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by nanotube on 2013-12-16
> **DPMR said:**
> In followed the guide lines on the site but after running sudo apt-get update I get an error.

W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release) 
Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)


Could be you just got directed to a borked sourceforge mirror. Just try the 'sudo apt-get update' again a few times and see if this goes away.
Let know how that goes.

---

### Post by Bashing-om on 2013-12-16
DPMR; Hello ;

I see two points in your sources list file that needs addressing:
The first is :
> 
deb [http://downloads.sourceforge.net/pro...la/mozilla/apt](http://downloads.sourceforge.net/pro...la/mozilla/apt) all main

Should be expanded to this URL:
```

deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
deb-src http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main

```
Copy paste into your sources list file (make a back up prior to editing !) 
Not real sure about that "all" ?????? _ never seen that option in the field before - maybe Mozilla accepts that format(?).

2nd:
oneiric has reached end of life and is no longer supported. If this fetch line is a duplicate of one for precise, then delete these lines.
Else change "oneric" to "precicse".

Give it a run and let us know the results.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by nanotube on 2013-12-17
> **Bashing-om said:**
> DPMR; Hello ;
Should be expanded to this URL:
```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
deb-src http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```


Actually ubuntuzilla doesn't host sources, only mozilla-built binaries. so deb-src won't do anything even if you try to apt-get source. 
So his one line, 
```

deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main

``` 
should be just fine.

> 
Copy paste into your sources list file (make a back up prior to editing !) 
Not real sure about that "all" ?????? _ never seen that option in the field before - maybe Mozilla accepts that format(?).


The ubuntuzilla (mozilla) binaries are not distribution-version specific, they're the same for any ubuntu/debian version. Hence they just live under 'all'.

> 
2nd:
oneiric has reached end of life and is no longer supported. If this fetch line is a duplicate of one for precise, then delete these lines.
Else change "oneric" to "precicse".

Yes, that seems weird, that he's mixing precise and oneiric. You're right, if he's running precise, should probably edit that. That said, it should not have anything to do with the ubuntuzilla repo failing.

---

