---
title: "apache won't parse php"
date: 2006-05-07
forum: Server Platforms
---

### Post by Yawgmoth on 2006-05-07
Let me start out by saying that I just switched over from windows to ubuntu last month so speak slowly to the newb :-P .

Anywho, I wanted to set up a LAMP on my new ubuntu machione so I checked out the wiki  and found this great tutorial, [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

apt-get installed apache wonderfully and, with a little help from another tutorial, It's working great as a web server and a SOCKS proxy.

However, I don't think that I'm installing php correctly. I follow the tutorial and do
```
sudo apt-get install php4
```
It says everything installed correctly so I restart apache and try to run a small php script( by going to [http://myserver/test.php](http://myserver/test.php)) and it doesn't parse it. Firefox just gives me a nasty "Do you want to download this" box.

so I follow the troubleshooting advice on the wiki page and run
```
sudo apt-get install libapache2-mod-php4
```
but It gives me this error
```
The following packages have unmet dependencies:
  libapache2-mod-php4: Depends: apache2-mpm-prefork (> 2.0.52) but it is not installable
E: Broken packages

```
and when I try to run
```
sudo a2enmod php4
```
it says
```
This module does not exist!
```

I've tried removing and reinstalling apache2 and php4 multiple times and restarting apache 2 multiple times.(I also tried to install php5 but it gives me another wierd error saying that it doesn't have an installation candidate) 

Did I do anything wrong? 

your help is greatly appreciated,
--Yawgmoth

---

### Post by harisund on 2006-05-07
First make sure you have enabled your repositories. I am thinking you will need universe and multiverse. 

Then, let's start fresh, shall we? 

Go ahead and wipe out your apache. ```
sudo apt-get --purge remove apache2-common apache2 php4 libapache2-mod-php4
```

Now rerun the same code, this time erase the --purge option and substitute remove with install. 

Hopefully it would work. 

And I am really hoping you are using apache2, right?

---

### Post by Yawgmoth on 2006-05-07
wow that was fast!

so I wiped out everything and it said it did everything fine, but I'm worried about this part
```
Purging configuration files for apache2-common ...
dpkg - warning: while removing apache2-common, directory `/var/www' not empty so not removed.
dpkg - warning: while removing apache2-common, directory `/etc/apache2/conf.d' not empty so not removed.
dpkg - warning: while removing apache2-common, directory `/etc/apache2/mods-enabled' not empty so not removed.
dpkg - warning: while removing apache2-common, directory `/etc/apache2' not empty so not removed.
Removing php4 ...

```

is it ok that it's not removing those?

here's the what the console says when I try to install the packages using the command you gave me.

```
$ sudo apt-get install apache2-common apache2 php4 libapache2-mod-php4
Reading package lists... Done
Building dependency tree... Done
Note, selecting apache2-mpm-worker instead of apache2
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libapache2-mod-php4: Depends: apache2-mpm-prefork (> 2.0.52) but it is not installable
E: Broken packages

```

yes, i'm using apache2 (at least that was the package I installed with apt-get)

thanks for the help,
--Yawgmoth

EDIT: sorry, still a newb :( what's a  repository and how do I enable it?

EDIT AGAIN: ok so repositories are different packages ... how can I make sure they're enabled?

EDIT AGAIN AGAIN:
so deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe  was already enabled
and I enabled  deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse in sources.list but i got the same result :( am I enabling the wrong ones?

---

### Post by harisund on 2006-05-07
I am guessing this is a problem with your repositories. 
Can you post the listing of your /etc/apt/sources.list here?

---

### Post by Yawgmoth on 2006-05-07
k, here's my entire sources.list

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe

```

it's all commented out except for the last line so I guess I don't have the multiverse repository enabled?

---

### Post by harisund on 2006-05-07
There are some lines in that you will have to uncomment. 

For a quick example, use my file list temporarily. ```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
```
Then try
```
sudo apt-get update
```
And then do what I suggested earlier.

---

### Post by Yawgmoth on 2006-05-07
dude you're so awesome!
it all works now

thank you so much!

*hugs harisund*

---

### Post by LeeM on 2006-05-08
Hi, I'm a relative newbie to ubuntu also. I've had the same problem (i.e., after I install php5, Firefox gives me nasties, instead of interpreting phpinfo.php.) I've followed the discussion, but am a little preplexed at the solution. I thought that enabling "multiverse" and "universe" was a pretty drastic action, and left you open to all kinds of problems. No??

Thanks!

---

### Post by harisund on 2006-05-08
Good point. 

Frankly, I don't care and so I have left *all* repositories enabled. 

But if you are worried about breaking your system, I would suggest you start a new thread asking people what repositories are the safest to have.

---

