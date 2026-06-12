---
title: "Calliope MP3 server help"
date: 2009-06-15
forum: Server Platforms
---

### Post by bcdudley on 2009-06-15
I am hoping for a little help on this. I am trying to get an mp3 server going for my house (yes it is all legal, it is to play music on my patio). I am attempting to use a program called Calliope (sourceforge.net : kalliope). It is an older program, but it looks like exactly what I wanted. I have gotten it most of the way going, but I am stuck on the last few steps.

It is telling me I am missing the following modules:

Apache::RequestIO (optional, external) failed to load -- used with mod perl v2
Shout (optional, external) failed to load -- for icecast, download from icecast.org
Channel::Stream (optional, internal) failed to load -- used to stream songs via Icecast
Web::ModPerl (optional, internal) failed to load -- used to preload modules into Apache for speed

I think the Shout and Channel::Stream are not that important, but the other two are most likely keeping me from working correctly.

The server is constantly playing random mp3's (as it is supposed to) and the web page will come up, however, when I try to queue up a song to be played, I get an internal server error

The last few lines of my Apache2 error log are:

[Mon Jun 15 10:28:53 2009] [notice] SIGHUP received.  Attempting to restart

[Mon Jun 15 10:28:53 2009] [warn] NameVirtualHost *:80 has no VirtualHosts

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mcrypt.so' - /usr/lib/php5/20060613+lfs/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0

[Mon Jun 15 10:28:54 2009] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.

[Mon Jun 15 10:28:54 2009] [notice] mod_python: using mutex_directory /tmp

[Mon Jun 15 10:28:54 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch mod_python/3.3.1 Python/2.6.2 mod_apreq2-20051231/2.6.0 mod_perl/2.0.4 Perl/v5.10.0 configured -- resuming normal operations

I am pretty sure the error is the PHP warning. I would appreciate any assistance possible with this.

Thank you,

---

### Post by bcdudley on 2009-06-15
ok, scratch the part about the PHP warning being the problem. I go that fixed and it is still giving me the same internal server error. I still show the perl modules missing however. Please help.

---

### Post by v3xtra on 2009-06-15
Have you installed the perl modules for Apache?  Simple question, but I guess it doesn't seem that way by the errors.  This guide should help you install Perl support for Apache.

[http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html)

Also, have you installed PHP-mcrypt?  ```
sudo aptitude install php5-mcrypt
```
You should probably also see if mcrypt was added to your php.ini file:

```
sudo nano /etc/php5/apache2/php.ini
``` and add
```
extension=mcrypt.so
```
to the end of the file if it is not there already.  See if that gets rid of the error.  Otherwise I have not been able to find anything even on this program online, unless it goes by either of those names online somewhere.  Hope I was somewhat helpful, and good luck!

---

### Post by bcdudley on 2009-06-15
It looks like my perl is not working. When I go to the perltest as suggested on the page you linked, I get the exact same error: Internal Server error. I have installed everything that was suggested and I am at a loss as to why it is not working. Should I purge and reinstall perl?

The homepage for the project is
 [http://neil.verplank.org/opensource/calliope/](http://neil.verplank.org/opensource/calliope/)

The sourceforge for it is 
 [http://sourceforge.net/projects/kalliope](http://sourceforge.net/projects/kalliope)

Also, adding the mcrypt.so line give me the error back and kills php. Getting rid of that line fixes my php. Is that something I need for perl to work?

Thank you for the help

---

### Post by v3xtra on 2009-06-16
You're welcome for the help, however probably not helpful it may be though.  :)

What is the output of this command ( I'm sorry to say I don't know what it SHOULD look like, but I am just kind of wondering. )

```
perl /usr/local/calliope/lib/Main.pm
```

And also, this may be silly and rude, but have you read the INSTALL file forwards and backwards to make sure that you didn't miss anything?

[Install](http://neil.verplank.org/opensource/calliope/help/INSTALL)

I hope that we can figure this out, I'd like to see this working because this is a very interesting topic!  I may end up using this for myself as well if we can try and figure out the bugs!

---

### Post by bcdudley on 2009-06-16
Ok, I just got it working. I did something that got Perl working a little earlier, but I am not sure what. Then after re-reading the install manual several times over (yes I did read it and I almost have the thing memorized, lol) I found one tiny step I missed. I had to set the user for calliope in the conf file to the same user as Apache uses.

Thank you for your help. The server is working great and I now have a jukebox for my back patio and my garage. In the process, I learned a great deal about how Apache, php and perl work. 

If you are interested in setting this up, I would be happy to repay the favor.

---

### Post by v3xtra on 2009-06-16
Awesome, if / when I do get my server running ( I had a bad hard drive that pooped on my this weekend, will most likely be getting an entirely new one for cheap ), I will definitely be knockin' on your door for some help with this!  Glad it works for you though, hope you enjoy it!

---

