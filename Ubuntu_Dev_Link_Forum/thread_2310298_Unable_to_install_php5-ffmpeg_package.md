---
title: "Unable to install php5-ffmpeg package"
date: 2016-01-18
forum: Ubuntu Dev Link Forum
---

### Post by alfirdaous on 2016-01-18
Hello everybody,

I am trying to install the php5-ffmpeg package, but I got this error:


```

# sudo apt-get install php5-ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 php5-ffmpeg : Depends: phpapi-20090626
E: Unable to correct problems, you have held broken packages.

```

Some helpful information:

```

# whereis ffmpeg
ffmpeg: /bin/ffmpeg /usr/bin/ffmpeg /usr/bin/X11/ffmpeg /usr/share/man/man1/ffmpeg.1.gz

```

```

# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

```

```

# apache2 -v
Server version: Apache/2.4.16 (Ubuntu)
Server built:   

```

Thanks for your support

---

### Post by SeijiSensei on 2016-01-18
You can try to install that [phpapi](http://packages.ubuntu.com/precise/phpapi-20090626) package manually and see what happens.

---

### Post by alfirdaous on 2016-01-18
I tried to install using command line, this is what happens, it seems some packages are on hold:

```

# apt-get install libapache2-mod-php5 libapache2-mod-php5filter php5-cgi php5-cli php5-fpm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5-cgi is already the newest version.
php5-cli is already the newest version.
libapache2-mod-php5 is already the newest version.
php5-fpm is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libapache2-mod-php5 : Conflicts: libapache2-mod-php5filter but 5.5.31+dfsg-2+deb.sury.org~precise+1 is to be installed
 libapache2-mod-php5filter : Conflicts: libapache2-mod-php5 but 5.5.31+dfsg-2+deb.sury.org~precise+1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by SeijiSensei on 2016-01-19
Maybe you should consider upgrading to 14.04.  That phpapi-20090626 package doesn't even exist past 12.04.

---

### Post by alfirdaous on 2016-01-19
May be I should do that, thanks [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195") for the help

---

### Post by FakeOutdoorsman on 2016-01-26
Why do you need php5-ffmpeg? It's ancient and dead. Do you even need a wrapper for ffmpeg? Can you just use the ffmpeg binary directly in your scripts?

[http://trac.ffmpeg.org/wiki/PHP](http://trac.ffmpeg.org/wiki/PHP)

---

### Post by Sonia69 on 2016-05-04
> **FakeOutdoorsman said:**
> Why do you need php5-ffmpeg? It's ancient and dead. Do you even need a wrapper for ffmpeg? Can you just use the ffmpeg binary directly in your scripts?
[http://]("https://ahref.site/4ar5Y/")[trac.ffmpeg.org/wiki/PHP]("http://trac.ffmpeg.org/wiki/PHP")

Can you just use the ffmpeg binary directly in your scripts?
Thanks ! :confused:

---

