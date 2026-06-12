---
title: "Which Ubuntu mirror do you use?"
date: 2010-02-20
forum: The Cafe
---

### Post by arnab_das on 2010-02-20
I used to download my updates from the Ubuntu main server. But its just way too slow, dont know why but while updating it takes around 3-4 mins to check for updates, coz it actually downloads some stuff to check, around 5-6 MB of data.

but while updating from say a South African mirror, ubuntumirror.ac.za, the updates take place within a second.

any idea why this is so?

which mirror do you use?

---

### Post by Bachstelze on 2010-02-20
> **arnab_das said:**
> 
any idea why this is so?


Knowing where you are located would help...

---

### Post by PuddingKnife on 2010-02-20
anl.gov

---

### Post by FuturePilot on 2010-02-20
> **PuddingKnife said:**
> anl.gov

This.

But it's actually mirror.anl.gov ;)

---

### Post by arnab_das on 2010-02-20
> **Bachstelze said:**
> Knowing where you are located would help...


i live in India, but the Indian mirror has the same problems as the Ubuntu main server. downloads a lot of packages even while checking.

---

### Post by eriktheblu on 2010-02-20
I think it's the one in Chicago, but I just set the update manager to pick the best one.

---

### Post by arnab_das on 2010-02-20
question: does it matter if I download the updates from some other mirror, other than my local one?

will i miss any updates?

---

### Post by NightwishFan on 2010-02-20
I think the official mirrors are inspected pretty close. I use:
```
ubuntu.media.mit.edu
```

It generally is selected as the fastest mirror for me as well under software sources.  As for your question, I think that you will not miss updates, but I do not know for sure.

---

### Post by arnab_das on 2010-02-20
just checked for updates, the nearest server actually downloaded around 7MB of data. and it was just 'checking' for updates.

---

### Post by cariboo on 2010-02-20
When checking for updates, it always downloads a package list, otherwise how would your system know what packages are installed and what new packages are available. If you are worried about bandwidth limits, it may be better to stay with a version, eg: Januty or Intrepid, that don't update as often.

---

### Post by MichealH on 2010-02-20
UK server

---

### Post by arnab_das on 2010-02-20
> **cariboo907 said:**
> When checking for updates, it always downloads a package list, otherwise how would your system know what packages are installed and what new packages are available. If you are worried about bandwidth limits, it may be better to stay with a version, eg: Januty or Intrepid, that don't update as often.

data usage is not a problem for me. my current ISP package doesnt have data limits. but its speed which is a problem for me. believe it or not, i'm having to survive on 256kbps :(

---

### Post by venator260 on 2010-02-20
Just decided to do the automatic selection thing again, to see if things have changed. They have. I'm now using mirrior.umoss.org

---

### Post by RandomJoe on 2010-02-21
I was experiencing very slow updates with the "US" server so finally tried the auto-selection.  It picked the one that is just an IP.  76.73.4.58, which reverse-lookup says is mirrordenver.fdcservers.net.

It is blazing fast compared to any of the others for me (OKC, OK on Cox cable).  Traceroute says it's on Comcast, Cox takes me to Dallas then Comcast back to Denver.

Huh, I just checked the route to us.archive.ubuntu.com and it's located in UK.  If it's really overseas, that could explain the difference.  I had always assumed it would actually be in the US...

---

### Post by freeball1 on 2010-02-21
I've selected 'German Server', and it always downloads fullspeed for me. The dpkg thing takes ages though ('Reading Database'), far longer than the update itself. Any advice?

---

