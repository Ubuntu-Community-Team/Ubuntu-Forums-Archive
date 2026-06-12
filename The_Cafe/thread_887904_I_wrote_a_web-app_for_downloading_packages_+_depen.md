---
title: "I wrote a web-app for downloading packages + dependencies."
date: 2008-08-12
forum: The Cafe
---

### Post by kaens on 2008-08-12
Hey everyone, I'm not entirely sure if this is the best place to stick this semi-announcement, but since the actual announcement forum is locked, and it doesn't seem to fit anywhere else, I guess this will do.

I wrote a little web-app using python and cherrypy that allows people to download a package and it's dependencies as a tarfile. I've run into a couple situations where I had one box that didn't have internet access, needed to do some installation on it, and had lots of fun manually resolving package dependencies, until I found apt-get build-dep, and then it's still two commands to get the package and it's dependencies, etc.

Anyhow, it's open source (of course), and can be viewed / used at [http://packagedepends.homelinux.org:8080]("http://packagedepends.homelinux.org:8080"). It's currently hosted on my personal machine, so I don't think it can handle too much of a hit as far as load goes, but if you're interested or could use it, feel free to check it out.

---

### Post by blithen on 2008-08-12
Wow! Works great. Pretty cool program. Great job!

---

### Post by eldragon on 2008-08-12
freakin awesome, how do i install it on my personal apache web server so that i dont kill your bw...?

i suppose it uses the local package cache to pack things.......right?

---

### Post by koenn on 2008-08-12
I get 
```

404 Not Found
The path '/download' was not found.
``` with each package I try. Then when I try the same package again, it works. 

Other than that, it seems to be doing what you intended. Nice work.

---

### Post by kaens on 2008-08-12
> **eldragon said:**
> freakin awesome, how do i install it on my personal apache web server so that i dont kill your bw...?


Branch from launchpad, bzr branch lp:pd or something like that. I'm not sure about setting up cherrypy to run behind apache. There are install instructions, the funkiest thing you have to do is add a line to /etc/sudoers for apt-get build-dep -dy

> 
i suppose it uses the local package cache to pack things.......right?

No, I don't think so. I'm not actually sure what you mean by local package cache. It actually runs aptitude download packagename and apt-get build-dep -dy -oDir::Cache:Archives=path packagename. It does keep the tarfile handy in canse someone else downloads the same package, but the packages are generated on the fly. 

[quote=blithen]
Wow! Works great. Pretty cool program. Great job! 
[/quote]

Thanks!

---

### Post by kaens on 2008-08-12
> **koenn said:**
> I get 
```

404 Not Found
The path '/download' was not found.
``` with each package I try. Then when I try the same package again, it works. 

Other than that, it seems to be doing what you intended. Nice work.

Odd, I don't have any 404's in my logs. What browser are you using, and what packages are you searching for?

Edit: I found the 404s... apt-proxy - looks like it's sending you the download link before actually making the package, weird.

---

### Post by koenn on 2008-08-12
> **kaens said:**
> Odd, I don't have any 404's in my logs. What browser are you using, and what packages are you searching for?

Edit: I found the 404s... apt-proxy - looks like it's sending you the download link before actually making the package, weird.

yep, that would be me. I tried apt-proxy, bash, and something virtualbox - same result each time.

I use FF 3.0.1 through a squid proxy - could the proxy affect how your app works ?

---

### Post by kaens on 2008-08-12
> **koenn said:**
> 
I use FF 3.0.1 through a squid proxy - could the proxy affect how your app works ?

That's definately possible. I haven't tried accessing it through a proxy at all. When download?package=packagename is hit, it then downloads / generates the package and serves it back - download corresponds to a method, not to an actual file. If the proxy tries to fetch the "page" before the method was finished (and it looks like it is), it would 404.

---

### Post by eldragon on 2008-08-12
> **kaens said:**
> Branch from launchpad, bzr branch lp:pd or something like that. I'm not sure about setting up cherrypy to run behind apache. There are install instructions, the funkiest thing you have to do is add a line to /etc/sudoers for apt-get build-dep -dy



No, I don't think so. I'm not actually sure what you mean by local package cache. It actually runs aptitude download packagename and apt-get build-dep -dy -oDir::Cache:Archives=path packagename. It does keep the tarfile handy in canse someone else downloads the same package, but the packages are generated on the fly. 



Thanks!

well, when you do apt-get update, you download a list of available packages and their versions..


anyway, browsing through launchpad i found it how it worked, quite clever :D

this should come as an option directly through apt-get

say: apt-get pack-dep package

---

### Post by OutOfReach on 2008-08-12
Haha works like a charm!
Nice work ;)

---

### Post by kaens on 2008-08-12
> **eldragon said:**
> well, when you do apt-get update, you download a list of available packages and their versions..


Oh, yes. It uses those, if you're referring to the files in /var/lib/apt/lists.

> 
anyway, browsing through launchpad i found it how it worked, quite clever :D

this should come as an option directly through apt-get

say: apt-get pack-dep package

It almost does, it comes _so frustratingly close_ to being there as one command.

---

### Post by koenn on 2008-08-12
> **kaens said:**
> That's definately possible. I haven't tried accessing it through a proxy at all. When download?package=packagename is hit, it then downloads / generates the package and serves it back - download corresponds to a method, not to an actual file. If the proxy tries to fetch the "page" before the method was finished (and it looks like it is), it would 404.

I seem to get the same problem also without proxy.
Let me know if there's anything I can do if you want to investigate this further.

---

### Post by kaens on 2008-08-12
> **koenn said:**
> I seem to get the same problem also without proxy.
Let me know if there's anything I can do if you want to investigate this further.

I'd really like to know what's going on, but you seem to be the only person it's happening to, and I frankly don't have any clue why.

I've tried it in firefox 3.0.1, so I don't think that's the problem.

Maybe it will happen to some other people and we can figure it out. I'm a bit stumped, as it is.

It is happening consistently, right?

---

### Post by Newuser1111 on 2008-08-12
It crashed FireFox.

---

### Post by kernelhaxor on 2008-08-12
thts a cool idea .. I guess ur hard disk is getting full with all the tarballs it prepares for other ppl .. Oh well, I guess u can delete the tarballs as and when required ..

thanks mate!

---

### Post by kaens on 2008-08-12
> **Newuser1111 said:**
> It crashed FireFox.

Are you the person who searched for "a"? It certainly might crash firefox if you tried to load such a huge results list.

Edit: if not, what did you search for that crashed it?

[quote=kernelhaxor]thts a cool idea .. I guess ur hard disk is getting full with all the tarballs it prepares for other ppl .. Oh well, I guess u can delete the tarballs as and when required[/quote]

The tarballs tend to be pretty small. The tarball directory is currently taking up 278M, a lot of that is gcc-4.2-source and eclipse tarballs.

If I had a dedicated server / real host for this, I would just make sure to have enough hard-drive space for them, and perhaps clean cache every once in a while, or when packages get updated.

---

### Post by Newuser1111 on 2008-08-12
> **kaens said:**
> Are you the person who searched for "a"? It certainly might crash firefox if you tried to load such a huge results list.

Edit: if not, what did you search for that crashed it?
I typed "WINE" or something similar.

---

### Post by kaens on 2008-08-12
> **Newuser1111 said:**
> I typed "WINE" or something similar.

Could it have just been a random firefox crash? Does is crash again when you try it again? If so, what version of firefox?

---

