---
title: "FreeNX - Dependency Problem"
date: 2005-06-11
forum: Ubuntu Backports
---

### Post by electroglas on 2005-06-11
When I try to install FreeNX, I get the error " Depends: expect  but it is not installable".

I tried installing expect by itself, but I get the same error.

Any ideas???

---

### Post by Xian on 2005-06-11
I don't get that error message. 
Have you enabled the [extra repos](http://ubuntuguide.org/#extrarepositories)?

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by jdong on 2005-06-11
FreeNX is a 3rd party package, maintained by the Ubuntu Backports Team. You get it from the "hoary-extras" repository.

Can you post the EXACT error, along with your sources.list. Also, post the output to **apt-get install expect**

---

### Post by electroglas on 2005-06-11
[QUOTE=jdong]FreeNX is a 3rd party package, maintained by the Ubuntu Backports Team. You get it from the "hoary-extras" repository.

Can you post the EXACT error, along with your sources.list. Also, post the output to **apt-get install expect**[/QUOTE]

apt-get install expect
Reading package lists... Done
Building dependency tree... Done
Package expect is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package expect has no installation candidate

I believe you are right about the repositories issue. Please take a look and make recommendations to resolve this issue with "expect" and to add power to my overall repository selection.


## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted

---

### Post by jdong on 2005-06-11
Man, your sources.list is a MESS.


Replace it with Xian's suggested sources.list. That comes from ubuntuguide.org, and I recommend that.

---

### Post by electroglas on 2005-06-11
[QUOTE=jdong]Man, your sources.list is a MESS.


Replace it with Xian's suggested sources.list. That comes from ubuntuguide.org, and I recommend that.[/QUOTE]



That fixed the FreeNX issue!!!

Yes, I know they are a mess...

I got tired of playing around with Hoary and just started using it. In the process, I left the repositories in a mess.


Thanks

---

### Post by electroglas on 2005-06-11
I didn't get a menu entry for FreeNX.

I tried in vain to get menus straightened out before, but got tired of trying different things from the forums and have just lived with it.

Any suggestions on fixing my underlying menu issue???

---

### Post by jdong on 2005-06-11
FreeNX doesn't have a menu entry. It's just the server component. The client component is called 'nxclient'. It also doesn't come with menu entries (only KDE ones... :( ). You can start it by ALT+F2 and running 'nxclient'. If you get really pissed, create a menu entry ;)

---

### Post by Ozitraveller on 2005-06-13
Does FreeNX have any impact on Firestarter? 

I can see the other winxp pc's on my network and copy from/to them. Also I can see the ubuntu node in network heighbourhood, but now access is denied.

The winxp NXclient tests ok with their testdrive server.

---

### Post by jdong on 2005-06-13
No it doesn't. FreeNX just sets up a new user account for SSH (login name 'nx', pubkey authentication)

---

### Post by Ozitraveller on 2005-06-14
[QUOTE=jdong]No it doesn't. FreeNX just sets up a new user account for SSH (login name 'nx', pubkey authentication)[/QUOTE]


Thanks jdong. I was affraid somebody was going to say that! ](*,)

---

