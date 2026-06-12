---
title: "shell script question for Rsync"
date: 2006-04-19
forum: Server Platforms
---

### Post by cragmonkey on 2006-04-19
I've been trying for several hours now to make a shell script do what I need and I can get it 90% right but I need a little help. 

The Object:
use Rsync to copy the ENTIRE (even hidden files and directories) contents of the /home folder on server1 to the /home folder of server2. 

This is the script I have so far. I can get it to sync all the typical files and directories but I cannot get the hidden files/directories (specifically there is a .cpan directory in /home that my script is not grabbing)

<code>
rsync -r --rsh=/usr/bin/ssh /home/* my.dns.name:/home
</code>

I'm sure I'm just missing a switch or something but I have been through all the man pages and looked on the internet for help but can't find anything specific  enough. Any help is appreciated.

---

### Post by jazzmuzik on 2006-04-19
[QUOTE=cragmonkey]rsync -r --rsh=/usr/bin/ssh /home/* my.dns.name:/home[/QUOTE]

Try it without the asterisk:

rsync -r --rsh=/usr/bin/ssh /home/ my.dns.name:/home


BTW, you could shorten it to:

rsync -r -e ssh /home/ my.dns.name:/home

---

### Post by cgjones on 2006-04-19
Try using this:
```
rsync -a --rsh=/usr/bin/ssh /home/ my.dns.name:/home/
```
The -a is for archive, which is the same as -rlptgoD. Depending on your setup, you may not want to use the -a.
Definitely try it without the asterisk, and add the trailing slash to the destination.

---

### Post by cragmonkey on 2006-04-19
Thanks guys. That got it. This is what my new script looks like....

rsync -a -e ssh /home/ my.dns.name:/home/

BTW - this is my first shell script ever.

---

### Post by jazzmuzik on 2006-04-19
You can specify the user as well if you are connecting to a remote site:

rsync -a -e ssh /home/ [email]username@my.dns.name[/email]:/home/

With compression and more verbosity:

rsync -avz -e ssh /home/ [email]username@my.dns.name[/email]:/home/

---

