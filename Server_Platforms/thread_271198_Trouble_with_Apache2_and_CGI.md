---
title: "Trouble with Apache2 and CGI"
date: 2006-10-04
forum: Server Platforms
---

### Post by jaclynL on 2006-10-04
I am trying to do a test-run of some stuff before integrating it into my website, but I can't seem to get Apache2 configured currectly.

Whenever I try to view ~/www/cgi-bin/[myfile].cgi, it just asks if I want to download the file or open it in a text editor.  I presume I just don't have some necessary library (probably perl-related) installed, but I've been googling and installing and looking around the forums and I can't spot what I'm missing.  

Any ideas?

---

### Post by Endwin on 2006-10-04
Where are you putting your cgi scripts? By default in Ubuntu the apache2 cgi folder is located in:

```
/usr/lib/cgi-bin
```

You can make a symbolic link to this directory in /var/www with the command:

```
sudo ln -s /usr/lib/cgi-bin /var/www/cgi-bin
```

If you just make a normal folder cgi-bin in /var/www/ it will not work unless you change in /etc/apache2/apache2.conf to allow cgi scripts outside of that directory (generally not recommended)

Also make sure Perl is installed.

---

### Post by jaclynL on 2006-10-04
I'm putting them in my www folder, located in my home directory.  I tried the symlink and still the same deal.  As I originally suspected, it seems I'm missing perl packages and I don't know which ones I need at this point.

---

### Post by real_gollum on 2006-10-06
hey,
i'm in no way skilled in apache2 config, but you definitely need to:

apt-get install libapache2-mod-perl2

---

### Post by jaclynL on 2006-10-06
Yeah, the troubling part is I do have that package =C

I think I'm just going to go with another solution for now, one that doesn't involve messing around with CGI

---

