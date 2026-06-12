---
title: "PHP: Function works in CLI but not through browser"
date: 2007-02-09
forum: Server Platforms
---

### Post by feenster on 2007-02-09
Hi all,
Further from my Informix post a bit down the forum, I have struck a new problem.

Informix support is actually installed and configured fine, but I can only use the ifx_*() functions through CLI. If i try to use them through the browser, I get the "Fatal error: Call to undefined function ifx_connect()" error.

I have copied the php.ini from /etc/php5/cli to /etc/php5/apache2 and forced a reload on Apache2 using "/etc/init.d/apache2 force-reload". However, I still cannot access the ifx_*() functions.

What other files/folders could be affecting this? I assumed that it would just be php.ini, but does apache2.conf have a hand in it too? If not, what else should I be looking at?

Cheers,
  Matt

---

### Post by kidders on 2007-02-09
Hi there,

The only other files that would affect how external libraries work via Apache are the libraries themselves, I'd say. Here are some things to check, although I'm afraid they're all long shots!

[LIST]
[*]Do you have multiple versions of PHP or Apache installed. Basically, I'm wondering if Apache is using PHP4, while you're editing the configuration for PHP5.
[*]Are there any errors in your system logs that might indicate PHP is failing to load things?
[*]Do your third-party libraries mention any caveats about running them with mod_php. It's rare (but possible) that they might prefer to run with php_cgi (which would be less desirable).
[/LIST]

I have no idea if this is relevant, but I found the following at [http://forums.gentoo.org/viewtopic.php?t=245249](http://forums.gentoo.org/viewtopic.php?t=245249) ...

> the /etc/init.d/apache2 scripts clears the environment (env -i) before starting the Apache daemon, but we need to preserve some variables if we want mod_php to work, so modify the script this way (the original lines are commented): 
#env -i PATH=$PATH /sbin/start-stop-daemon --quiet \ 
# --start --startas /usr/sbin/apache2 \ 
# --pidfile ${PIDFILE} -- -k start ${APACHE2_OPTS} 
env -i \ 
PATH=$PATH:/opt/informix/bin \ 
INFORMIXSERVER=firm_name_01 \ 
INFORMIXDIR=/opt/informix \ 
ODBCINI=/opt/informix/etc/odbc.ini \ 
/sbin/start-stop-daemon --quiet \ 
--start --startas /usr/sbin/apache2 \ 
--pidfile ${PIDFILE} -- -k start ${APACHE2_OPTS}

Without installing Informix myself, I can't be sure whether this is relevant, but you can check for yourself, if you like. Here's the reference, translated into Ubuntu-speak:

It seems (on Gentoo at least!) as though there are some special environment variables required for Informix to run properly. If this is true, you need to find them, and set them in Apache's startup script. Apache takes special measures to discard environment settings when it starts (mostly as a security precaution), which is why this may be necessary. Anything you want to keep has to be explicitly defined, without using the "export" or "set" commands.

```
$ nl /etc/init.d/apache2 |grep ENV
     5  ENV="env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin"
    21  APACHE2="$ENV /usr/sbin/apache2"
    22  APACHE2CTL="$ENV /usr/sbin/apache2ctl"
```This shows the line containing the environment specification, and any lines that reference it. We're interested in line 5. You need to be quite careful when you change it ... special characters must be escaped correctly, and spaces must only appear where they're expected. To add an Informix-related environment variable, you would change the "ENV" line to something like **ENV="env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin INFORMIXDIR=/opt/informix"**. Be sure to add them all.

If this does indeed solve your problem, there's one more step to perform, since this change will create problems any time Ubuntu updates Apache for you. Let me know!

I hope this helps.

---

### Post by feenster on 2007-02-10
Hi,
Many thanks for taking the time to write such a detailed reply. I'll give it a try later today and report back here :-)

Cheers,
  Matt

---

### Post by kidders on 2007-02-10
No problem. :-) I just hope one of my suggestions is the *right* one!

---

### Post by feenster on 2007-02-13
Hi,
Well, i've tried it out, and unfortunately, i already had all the necessary variables declared in the /etc/init.d/apache2 script :(

To make matters worse, the script has stopped working through the command line too - I now get the ifx_connect() is not defined message. Oddly, I don't remember changing anything since it was last working :twisted:

I'm going to go back over my files now to see what I might have changed. The only thing that might be different is the environment variables, although entering **php -i | grep -i "informix"** on the command line gives the following:

```

PATH => /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/opt/informix/bin 
INFORMIXSERVER => servername
_SERVER["PATH"] => /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/opt/informix/bin 
_SERVER["INFORMIXSERVER"] servername
_ENV["PATH"] => /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/opt/informix/bin
_ENV["INFORMIXSERVER"] => servername

```

It seems like the INFORMIXDIR variable is missing, but declaring it manually with **export INFORMIXDIR=/opt/informix** doesn't seem to help :(

I'm downloaded a Gentoo VMWare appliance to experiment with, but i'd much prefer to get it working on Ubuntu as i already have a server up and running.

Any further ideas to try?

Cheers,
 Matt

---

### Post by kidders on 2007-02-14
> **feenster said:**
> the script has stopped working through the command line tooEek! :confused:

> **feenster said:**
> It seems like the INFORMIXDIR variable is missing, but declaring it manually with **export INFORMIXDIR=/opt/informix** doesn't seem to help :(No, it won't. You need to specify these values in a particular way (see my last post), as apache clears its working environment before it starts ... which I wouldn't recommend changing. *All* **export**-ed values would be lost.

Have you taken a look at the informix website? Whenever things don't work all by themselves (which is fairly often!), I tend to just configure them manually, based on the developer's instructions.

---

### Post by feenster on 2007-02-14
Hi Kidders,
Well, I got the CLI working again by recompiling PHP - still doesn't work through Apache unfortunately.

The annoying thing with Informix is that the documentation is exceptionally poor. The only real guides I could find were either vague, or based on other Linux distro's (e.g. Gentoo), and I couldn't translate the instructions across well enough.

Is it possible that the informix functions need to be compiled into some sort of module that can then be enabled to run alongside Apache with **a2enmod**?

Cheers,
  Matt

---

### Post by kidders on 2007-02-14
I have no idea :-( I wish I were more familiar with this particular software. Documentation-wise, I use Gentoo & Ubuntu ... could I be of some help translating instructions?

---

### Post by feenster on 2007-02-15
Humm, I'm really stuck with this.

So far, i've tried to install Gentoo on a spare PC, but it kept erroring towards the end of the install. I've then put a new install of Ubuntu on a spare machine and tried to compile PHP5.2 and Apache 2 from source with Informix support. That ended up giving me plenty of errors too.

So I land back where I started. It appears that I have sucessfully recompiled php-cli with Informix support, but mod_php has either not been recompiled, or the new version is not loaded by Apache.

By reconfiguring PHP from source, should mod_php be recompiled? If so, will it be stored somewhere waiting for me to activate it (and hence Apache is using the old version without informix support)??

<grasping at straws>

Matt

---

### Post by feenster on 2007-02-15
Kidders - i've done it!

The trick was as above, mod_php needed recompiling seperately from the normal php version. So, to do this, I downloaded the source for using:
```
apt-get source libapache2-mod-php5
```

I then used:
```
./configure --with-apxs2=/usr/bin/apxs2 --with-informix=/opt/informix
```
 followed by ```
make 
```and ```
make install
```.

After then loading the PHP5 module into Apache via:
```
a2enmod php5
```

I restarted Apache, and it works! However, the Informix SQL syntax seems to be tricky. I'm getting funny errors like
```
Open cursor fails (E [SQLSTATE=IX 000 SQLCODE=-200]) 
```

...But at least I've got the functions working now!

So, thank you again for your help - it is most appreciated. I can now crack on with my project :-)

Cheers,
  Matt

---

### Post by kidders on 2007-02-16
Yay! That's excellent news. :-) (Especially since I was *no* help hehe.)

---

### Post by feenster on 2007-02-16
But you still had the kindness to try which is the main thing ;)

No seriously, thanks again. A big weight off my shoulders that is :)

Matt

---

