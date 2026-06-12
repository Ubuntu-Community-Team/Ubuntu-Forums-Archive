---
title: "Apache2 in Jaunty - what has happened???"
date: 2009-07-22
forum: Server Platforms
---

### Post by wetinwales on 2009-07-22
Jaunty 9.04 AMD 64bit dual core.
Had apache2 running in jaunty for a month (only to preview website when designing IN PHP) all OK.

Sunday last, apache2 fails to show website as listed in 'sites-available'

Removed apache manually using sudo find / -name apache2 to locate everything and purge.
Used remove -purge.
Nothing allows apache2 to reinstall untill I find on [http://ubuntuforums.org/showthread.php?t=813725:-](http://ubuntuforums.org/showthread.php?t=813725:-)

the line is :-
sudo apt-get remove --purge $(dpkg -l apache* | grep ii | awk '{print $2}') && sudo apt-get install apache2

Finally apache2 is back in Jaunty and shows the 'It Works!' page as in /var/www/index.html

I canot get apache to preview 'mysite'
I am very familiar with changing the sites-available lines to whatever website I;m working on.
I still have it on my 8.04 machine and have it on XP on another

Has something changed in Jaunty??

I know the /etc/.hosts file is different and there may be issues with IPv4 and IPv6 but am lost.

To recap:-
I can get apache2 to show 'It Works!'  but it will not show my usual mod in apache2/sites-available to view my PHP site.

I have checked web file permissions and they are in place (same as set on Heron 8.04 machine

PHP5 appears to be installed.

I have crawled and crawled forums files etc etc but cannot make progress.

Can anyone guide me please?

---

### Post by wetinwales on 2009-07-22
Answered my own question.

I still haven't got it in my simple mind that permissions for access go back from the file you want, right through the directory structure to root.

Absolutely every directory has to be modified...?

Am I mad... do we have to modify permissions in every directory in the tree manually right back to root??

!

---

### Post by alastair on 2009-07-22
You need execute permission to enter or list a directory. Maybe that's the problem. But without a bit more detail of what you've got/found, it's hard to say what your problem is or was. Perhaps something basic that you'll kick yourself over.

---

