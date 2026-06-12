---
title: "So, apparently it is incredibly vital but completley unstated anywhere..."
date: 2009-05-05
forum: Server Platforms
---

### Post by PaganBlasphemy on 2009-05-05
...that you MUST upgrade older Ubuntu's before they are discontinued, or else you'll be stuck with the older version, unable to escape or upgrade in the future.  I have a 7.10 server that I have in a closet and never think about.  Was helping my brother-in-law set up a new Ubuntu server and remembered mine, which just purrs 24/7/365 and never gives me any headache.  Logged in and ran apt-get update, which failed.  Found that I can change "archive." to "old-releases." and grab the final updates, but can't upgrade the distribution from 7.10 to anything newer.

Haha, the joke's on me:

```
garrett@server:~$ sudo do-release-upgrade
Checking for a new ubuntu release
current dist not found in meta-release file
No new release found
garrett@server:~$ :(
```

---

### Post by Therion on 2009-05-05
> **PaganBlasphemy said:**
> ...that you MUST upgrade older Ubuntu's before they are discontinued...

Haha, the joke's on me...
Huh... You mean like on the download page where it says: 

Ubuntu 9.04 Desktop (the latest version): Includes the latest enhancements and **is maintained until 2010**

Ubuntu 8.04 LTS Desktop: Released April 2008 and **maintained until April 2011** &#8211; ideal for large deployments"... 

Like that you mean?

---

### Post by snowpine on 2009-05-05
Edit your /etc/apt/sources.list file and change all instances of "gutsy" to "hardy" (and change back whatever you changed to old-releases, obviously).
Then try to upgrade again.
This is the "Debian way" but it should work ok in Ubuntu as well.
Hardy should last you for quite some time, as it is the LTS. :)

---

### Post by PaganBlasphemy on 2009-05-06
@Therion: I don't know why I chose a non-LTS release for my server to begin with.  The box was never any problem so I never though to upgrade it to 8.04 (until it was too late hah).

@snowpine: thanks for the suggestion.  I couldn't find *anything *with reference to Ubuntu regarding this situation of forgetting to upgrade until after the distribution is abandoned, I'll give your method a go and see what happens.

---

### Post by cariboo on 2009-05-06
There is a way to keep your older version running try this link:

[Old releases]("http://old-releases.ubuntu.com/releases/")

there won't be any more security updates, but if your server is running the way you want it to why change anything.

---

