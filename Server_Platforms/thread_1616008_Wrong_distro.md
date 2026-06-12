---
title: "Wrong distro"
date: 2010-11-07
forum: Server Platforms
---

### Post by timbertens on 2010-11-07
Hello,

I have a kind of weird problem on one of our servers.  The server software was upgrade a couple times now and it went from 8.04 to 8.10 to 9.04 to 9.10 to eventually 10.04

Now I'm 100% sure the current version should be 10.04 but all of the sudden an 'apt-get update' does not work anymore, so I dig some further why that could be...

A simple 'cat /etc/lsb-release' gives me this answer

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

Totally not expected, but at least it explains why the 'apt-get update' gives me some trouble, since the resources in [http://archive.ubuntu.com](http://archive.ubuntu.com) where removed for that distribution as it has reached EOL.


Now, again I'm 100% sure I'm running the 10.4 version of that server, how can I fix this ?  Do I do a distribution upgrade again (what are the risks??) or should I do something else?

You're help would be very much appreciated !

Thanks,
Tim

---

### Post by snowpine on 2010-11-07
What is the output of

```
cat /etc/apt/sources.list
```

and

```
uname -a
```

please?

---

### Post by timbertens on 2010-11-07
Hi,

it's 

```
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted

```

rg,
Tim

---

### Post by timbertens on 2010-11-07
sorry didn't catch the second one

```
Linux xxx.xxxxxxxxx.com 2.6.32.12-linode25 #1 SMP Wed Apr 28 19:25:11 UTC 2010 i686 GNU/Linux
```

---

### Post by snowpine on 2010-11-07
Looks to me like you're running Intrepid with the Lucid kernel. :)

Can you describe your typical update process, which might shed some light on what's going on here?

---

### Post by timbertens on 2010-11-07
yes, it looks like it... 
Do you mean the normal ubuntu updating process?  

```

apt-get update
apt-get upgrade

```

---

### Post by snowpine on 2010-11-07
> **timbertens said:**
> yes, it looks like it... 
Do you mean the normal ubuntu updating process?  

```

apt-get update
apt-get upgrade

```

Those commands are for applying security patches and bug fixes to a specific Ubuntu release (such as 8.10).

Please read for more info on updating from release to release (such as 8.10 to 9.04): [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by timbertens on 2010-11-07
Ok for the last upgrade (the one to 10.4 back in May) I used 

```
sudo do-release-upgrade
```

---

### Post by snowpine on 2010-11-07
> **timbertens said:**
> Ok for the last upgrade (the one to 10.4 back in May) I used 

```
sudo do-release-upgrade
```

I am surprised 'do-release-upgrade' did not modify your /etc/apt/sources.list correctly. If you are feeling brave, I suppose you could try manually editing the file and changing all instances of "intrepid" to "lucid." This method is not officially recognized/recommended by Ubuntu (but Debian users do it all the time, and Ubuntu is based on Debian, so it *might* work). 

Another method is a fresh reinstall of 10.04. This method is labor-intensive but foolproof. :)

---

### Post by timbertens on 2010-11-07
Ok, I'll make an image before doing so...
Is it just the /etc/apt/sources.list I need to change or are there others too.

Many thanks for your help,
rg,
Tim

---

### Post by snowpine on 2010-11-07
> **timbertens said:**
> Ok, I'll make an image before doing so...
Is it just the /etc/apt/sources.list I need to change or are there others too.

Many thanks for your help,
rg,
Tim

Any time. :)

You should also check if there are any additional repositories listed in the /etc/apt/sources.list.d/ folder. 

Once you've changed the software sources, you can do:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

I hope it works; I've done this before with Debian but have never tested with Ubuntu 8.10 to 10.04. :(

---

### Post by timbertens on 2010-11-07
Thanks again.  I'll let you know the outcome!

regards,
Tim

---

### Post by Vegan on 2010-11-07
I went to the trouble of developing a backup script that takes daily snapshot of everything of interest.

So when a new release surfaces, I can simply install fresh, install my scripts to /home/me and poof I am up quickly.

I wanted to be faster on the draw and a custom script or 5 make all the difference.

---

### Post by timbertens on 2010-11-10
> **snowpine said:**
> Any time. :)

You should also check if there are any additional repositories listed in the /etc/apt/sources.list.d/ folder. 

Once you've changed the software sources, you can do:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

I hope it works; I've done this before with Debian but have never tested with Ubuntu 8.10 to 10.04. :(

@snowpine.  As promised a short update... your method worked perfectly.  Had a few side-problems (had to reinstall upstart-job, it prevented the distribution upgrade and mysql-server, did not start up anymore), but after some puzzling it came all together and the server runs smooth again and most important knows what version it actually runs on.

Again, thanks!

regards,
Tim

---

