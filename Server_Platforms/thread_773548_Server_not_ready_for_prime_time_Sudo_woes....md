---
title: "Server not ready for prime time? Sudo woes..."
date: 2008-04-28
forum: Server Platforms
---

### Post by sroussey on 2008-04-28
So after installing the new 08.04 we went about setting up the new server like we ordinarily would. One of the first things we did was to copy over the master hosts file so this one would would be able to talk with the others.

That basically killed the server. We can't su to root to fix since there is no root access. (It was on my list of things to change -- notice to anyone else -- do this first).

The way to do things is to use sudo. But that gives us a "unable to resolve host" error. I'd try and change the hostname, but that requires sudo. I'd try and change the hosts file, but that requires sudo.

Of course, I can sit in front of it and go into recovery mode, etc. But the use case of a server is not that of a desktop. The server is in a rack an hour away. If I have to drive down there, it will be with a CD with CentOS5. Sigh.

---

### Post by Oldsoldier2003 on 2008-04-28
> **sroussey said:**
> So after installing the new 08.04 we went about setting up the new server like we ordinarily would. One of the first things we did was to copy over the master hosts file so this one would would be able to talk with the others.

That basically killed the server. We can't su to root to fix since there is no root access. (It was on my list of things to change -- notice to anyone else -- do this first).

The way to do things is to use sudo. But that gives us a "unable to resolve host" error. I'd try and change the hostname, but that requires sudo. I'd try and change the hosts file, but that requires sudo.

Of course, I can sit in front of it and go into recovery mode, etc. But the use case of a server is not that of a desktop. The server is in a rack an hour away. If I have to drive down there, it will be with a CD with CentOS5. Sigh.

Even though I am a Ubuntu supporter I have to admit that I removed Ubuntu Server in favor of Debian Etch. I wish that Canonical would step back from the server market and throw its combined resources into developing the desktop.

With redhat basically out of the desktop business by their own admission, it only makes sense for Ubuntu to push harder and faster in the desktop arena, and leave the servers to someone else.

---

### Post by Brazen on 2008-04-29
Ubuntu 6.06 has been rock-solid for several different servers I manage.  I certainly hope they keep improving and expanding their server capabilities.  I don't touch the hosts file though; I have too many servers for anything other than dns to be reasonable.  I will not throw in 8.04 until it has been thoroughly tested, either, and I am particularly interested in it's virtualization features.  That sucks about your problem, though I would never enable the root account.  I was even disabling the root account on my Redhat servers before Ubuntu came along.

---

### Post by bluefrog on 2008-04-29
generally when a car goes into a tree, it is not the fault of the car nor the tree.

---

### Post by netztier on 2008-04-29
> **sroussey said:**
>  One of the first things we did was to copy over the master hosts file so this one would would be able to talk with the others.

Ewww! Hosts file, the dinosaur? The old dusty ting at /etc/hosts? 
And you *copied* it (instead of merging) over from the old server (probably containing the host's self-reference with wrong IP address and hostname?), and /etc/hosts is your only name resolution mechanism? Oh well...

I cordially invite you to step into the third decade of TCP/IP and to start using DNS!  ;-)

And while it's a good idea keeping your server off-site, consider some sideband access mechanism such as a serial line terminal server or a remote KeyboardVideoMouse-thingy. They have been invented for a reason...

regards

Marc

---

### Post by jernejk on 2008-04-29
Just insert ubuntu server cd, boot, go to rescue mode, when in console use vi to edit /etc/hosts

---

### Post by lex1 on 2008-04-29
ubuntu server 8.04 is not ready it comes no where near debian etch which is rock solid .The finance may good in ubuntu but still 
it is not tested enough before release.


lex1

---

### Post by hyper_ch on 2008-04-29
yeah, for some reason the hostname/hosts file are still tight together to the sudo usage somehow.... you need first to fix that...

And I also recommend using etch as server ;)

---

### Post by Brazen on 2008-04-29
> **hyper_ch said:**
> yeah, for some reason the hostname/hosts file are still tight together to the sudo usage somehow.... you need first to fix that...

And I also recommend using etch as server ;)

pfft... real men use Woody.

---

### Post by tubezninja on 2008-04-29
> **lex1 said:**
> ubuntu server 8.04 is not ready it comes no where near debian etch which is rock solid .The finance may good in ubuntu but still 
it is not tested enough before release.



And your basis for this statement is...?

Ubuntu 7.10 and now 8.04 have worked just fine for me, and has actually been quite forgiving in spite of my occasional bumblings.

---

### Post by mspIggy on 2008-07-13
> **jernejk said:**
> Just insert ubuntu server cd, boot, go to rescue mode, when in console use vi to edit /etc/hosts

i am a compleet rookie in 8.04 server and needed to rescue the boot file /scripts/local and could not for the life of me figure out how to use rescue mode... seems it wanted to reinstall system and when done did not boot...

how does this 'rescue' mode work?  is there a use guide somewhere i can study?


thank you

---

### Post by windependence on 2008-07-13
> **mspIggy said:**
> i am a compleet rookie in 8.04 server and needed to rescue the boot file /scripts/local and could not for the life of me figure out how to use rescue mode... seems it wanted to reinstall system and when done did not boot...

how does this 'rescue' mode work?  is there a use guide somewhere i can study?


thank you

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-rescuemode.html#gainrootinstallcd](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-rescuemode.html#gainrootinstallcd)

You have to type "rescue" at the boot prompt to get into rescue mode. Then, you have to mount your file system read/write in order to be able to fix anything.

-Tim

---

### Post by windependence on 2008-07-13
> **scaredpoet said:**
> And your basis for this statement is...?

Ubuntu 7.10 and now 8.04 have worked just fine for me, and has actually been quite forgiving in spite of my occasional bumblings.

I would have to agree here, and my basis is using servers in real world production applications in real data centers. I really want to use Ubuntu server for my VMware hosts but it has not been stable enough in testing where CentOS, SuSE, and RedHat have been fine in 32 bit and 64 bit modes. For my guest OSs, I am still using some form of *BSD and probably always will because of the small footprint and rock solid stability.

While I understand the reason for using sudo completely, there are times when this just isn't feesible on a server box. All the other server distros understand this.

Just an idea as a workaround for being able to be at the console, everything I put into production lately is in a VM guest. That way, I can log in to the VMware console and get right to the server console without actually being there. 

-Tim

---

### Post by koenn on 2008-07-14
> **sroussey said:**
>  ... One of the first things we did was to copy over the master hosts file so this one would would be able to talk with the others.

Maybe next time test your migration procedure before applying it to a production server ?

---

### Post by Krupski on 2008-07-20
> **sroussey said:**
> So after installing the new 08.04 we went about setting up the new server like we ordinarily would. One of the first things we did was to copy over the master hosts file so this one would would be able to talk with the others.

That basically killed the server. We can't su to root to fix since there is no root access. (It was on my list of things to change -- notice to anyone else -- do this first).

I use 8.04.1 server and the first thing I have to do is enable a root password.

The very first thing I type after logging in with the user account (created during install) is "sudo passwd root", then go from there.

In fact, since I'm running server in a stand-alone NAS box, I don't even HAVE user accounts... I even "userdel" the original logon account created during install.

I log in remotely using "root" and do all the maintenance with a free SSH client (Tunnelier - [[COLOR="Green"]LINK[/COLOR]]("http://www.bitvise.com/tunnelier")).

Try logging in as the user you setup as, then "sudo passwd root" - it may fix your problem.

-- Roger

---

### Post by songshu on 2008-07-20
```
sudo passwd root
``` will do it indeed, if i'm correct you could choose "expert" as an install option to enable root and skip the user account to start with.

offtopic:
to some of the other posters, i don't think anybody will say ubuntu server is good for nothing, but lets be honest here, the multitude of possible server configurations do simply not fit in the Gnome release schedule.

i would second the opinion that ubuntu should let go the server market in the Unix/red hat/debian arena and stick a bit more to Bug #1, if ubuntu server would limit itself more to be a easy user friendly home / small business server it would be for the best..

personally i stick with Debian on the server.

---

### Post by Krupski on 2008-07-20
> **songshu said:**
> personally i stick with Debian on the server.

Since Ubuntu server is basically the bare OS without a desktop... and since it's Debian based... where's the difference between Debian and Ubuntu in *server*? :confused:

---

### Post by songshu on 2008-07-20
> **Krupski said:**
> Since Ubuntu server is basically the bare OS without a desktop... and since it's Debian based... where's the difference between Debian and Ubuntu in *server*? :confused:

the difference is this
DEBIAN:
debian has 3 versions
unstable
testing
stable

new packages/versions go to the unstable branch and if it proves to be without bugs for 6 months it moves on to testing.
once in a while they freeze testing, not allowing any more packages coming from unstable, and they focus on bug fixing the testing branch after all bugs are squashed they move the entire testing branch and call it stable.
This process cycle usually takes 2 or 3 years but its very thoroughly tested before its called stable. There is no time limit, its ready when its ready.

Ubuntu:

Every 6 months after a release Ubuntu grabs the entire Debian unstable branch and starts bug fixing that for 6 months. After 6 months they call it a release.

so to sum it up: 
debian is old but very well tested
ubuntu is new and not so well tested

---

### Post by Krupski on 2008-07-20
> **songshu said:**
> the difference is this
DEBIAN:
debian has 3 versions
unstable
testing
stable


Well... now we're getting off topic (sorry admins)... but one more question:

Ubuntu specifically has a SERVER and a DESKTOP distro. Debian seems to not have that differentiation. Is there a "server" and "desktop" version of Debian? And if so, how does one find the proper distro?

Thanks!

-- Roger

---

### Post by songshu on 2008-07-20
absolutely offtopic:

yes they do

what people usually call debian is debian base, like the ubuntu server edition.
but there are also gnome, kde and xfce cd's, its very well usuable but a little less polished then Ubuntu and you have to do a few more things yourself.

[http://www.debian.org/CD/http-ftp/#stable](http://www.debian.org/CD/http-ftp/#stable)

---

### Post by Krupski on 2008-07-20
> **songshu said:**
> yes they do

[http://www.debian.org/CD/http-ftp/#stable](http://www.debian.org/CD/http-ftp/#stable)

Thanks! I'll take a look. 

-- Roger

---

