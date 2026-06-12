---
title: "Request : Eclipse,"
date: 2005-08-03
forum: Requests
---

### Post by geearf on 2005-08-03
Hello,

I just wanted to request a backport for Eclipse as it is in breezy now :)

Thanks.

---

### Post by ubuntu_demon on 2005-08-03
cool!

I second this request. 

eclipse is a nice development environment for java.

---

### Post by Sam on 2005-08-03
It's quite easy to install Eclipse:

[Wiki EclipseIDE](https://wiki.ubuntu.com/EclipseIDE)

---

### Post by GeneralZod on 2005-08-03
Is this the natively compiled version you're referring to? Because I'd love to get hold of that!

---

### Post by Sam on 2005-08-03
[QUOTE=GeneralZod]Is this the natively compiled version you're referring to? Because I'd love to get hold of that![/QUOTE]
Yes, the page contains a link to download Eclipse, with the choice of the architecture you're using.

---

### Post by geearf on 2005-08-03
it may be easy but not as easy of having in in a repos and getting new versions . :)

---

### Post by Sam on 2005-08-03
[QUOTE=geearf]it may be easy but not as easy of having in in a repos and getting new versions . :)[/QUOTE]
Seen on the Wiki page (but I haven't tested):
> Eclipse 3.0.1 has been uploaded to Breezy. Finally. You should be able to simply apt-get install it.

Actually these breezy packages should build fine for Hoary too. You can probably just apt-get source them and let it rip.

The Help system has been disabled completely because we don't yet have a free Tomcat. Working on that. Enjoy.
```
apt-get install eclipse-jdt
```

---

### Post by geearf on 2005-08-03
Yes but I am not using Breezy !)

I trie apt-get source eclipse, but it gives me old dependences (jdk 1.3 for exemple), so not the right way. And if i need to go at packages.ubuntu.com to get the breezy sources and compile them, might not be that good too :(

---

### Post by Luke Redpath on 2005-08-03
Just my opinion, but I think it might be better to just download and install from eclipse.org - its only a case of unpacking it somewhere (/opt/eclipse will suffice).

Eclipse in Breezy is already out of date...Eclipse 3.1 is now out and is a welcome improvement over 3.0.x.

It's also quite a big file so I'm not sure if the repository maintainers would appreciate the bandwidth hog.

---

### Post by Sam on 2005-08-03
[QUOTE=Luke Redpath]Just my opinion, but I think it might be better to just download and install from eclipse.org - its only a case of unpacking it somewhere (/opt/eclipse will suffice).[/QUOTE]
This is described [here](https://wiki.ubuntu.com/EclipseIDE) ! ;-)

---

### Post by geearf on 2005-08-04
it only needs to be unpacked right, but here I have many computers to install, so it would be easier for me, and easier for the one who will maintain this after me to have it in a .deb format, but before leaving I'll use the one on the wiki I guess :)

---

### Post by Luke Redpath on 2005-08-05
I guess you could always download the latest version and create a deb from that?

Easier said then done though, I don't know how to make debs myself ;)

---

### Post by geearf on 2005-08-06
I only know how to make them with checkinstall, but anyhow it's too late from my work, as I've stopped yesterday, and for me kate is enough for java :)

---

### Post by d0nk on 2005-10-01
Currently, i can not get eclipse (package eclipse-sdk) via apt or synaptic.  Apt returns the following error:
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  eclipse-sdk: Depends: eclipse-jdt (= 3.1-0ubuntu7) but it is not installable
               Depends: eclipse-pde (= 3.1-0ubuntu7) but it is not installable
E: Broken packages

```

So then i try eclipse-jdt, as the wiki says to use eclipse-jdt:
```
Package eclipse-jdt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package eclipse-jdt has no installation candidate

```

Right now i'm stuck running it out of my homedir.  I would like it to work from apt, so its kept up to date, and installed system wide.

---

