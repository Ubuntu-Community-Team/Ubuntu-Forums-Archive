---
title: "apt-cache question"
date: 2005-04-28
forum: Repositories &amp; Backports
---

### Post by k.ODOMA on 2005-04-28
Is there a way to limit apt-cache (the search function specifically) to *installed* packages (or an equivelent command for apt-get/dpkg)? I'm doing this over ssh so synaptic is not a possibility.

---

### Post by bored2k on 2005-04-28
Use the parameter --installed.

man apt-cache:
  --installed
              Limit  the  output  of depends and rdepends to packages which are currently installed. Configuration Item: APT::Cache::In&#8208;
              stalled.

---

### Post by k.ODOMA on 2005-04-28
[QUOTE=bored2k]Use the parameter --installed.

man apt-cache:
  --installed
              Limit  the  output  of depends and rdepends to packages which are currently installed. Configuration Item: APT::Cache::In&#8208;
              stalled.[/QUOTE]

When I do that (apt-cache search --installed mozilla-thunderbird), it spits out a bunch of packages, most of which *aren't* installed.  Am I doing something wrong?

---

### Post by mendicant on 2005-04-28
The man page also says that --installed only applies to depends and rdepends.  You might want to try:

% aptitude search ~imozilla

the ~i says to just look at the installed stuff.   aptitude has lots of other search patterns, too.  install aptitude-doc-en and check out:

file:///usr/share/doc/aptitude/html/en/ch02s03.html

for more info.

---

### Post by az on 2005-04-29
1.  Aptitude rocks!

2.  dpkg -l|grep thunder

---

### Post by mendicant on 2005-04-29
I did forget the 'search' argument, which I've corrected in my first post.  

For dpkg, I would use dpkg -l "*thunder*", so you avoid 'clipping' problems.  For instance, searching for firefox:

```

# dpkg -l "*firefox*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mozilla-firefo 1.0.2-0ubuntu5 lightweight web browser based on Mozilla
ii  mozilla-firefo 1.0.2-0ubuntu5 Support for Gnome in Mozilla Firefox
ii  mozilla-firefo 1.0.1lang20050 Mozilla Firefox English language/region pack

```

vs

```

# dpkg -l | grep firefox

```

Actually, I guess you really want dpkg --get-selections "*mozilla*" to avoid getting listing stuff you may have had installed at one point:
```

# dpkg -l "*mozilla*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  flashplayer-mo 7.0.25-0.0     Macromedia Flash Player
un  mozilla-browse <none>         (no description available)
ii  mozilla-firefo 1.0.2-0ubuntu5 lightweight web browser based on Mozilla
ii  mozilla-firefo 1.0.2-0ubuntu5 Support for Gnome in Mozilla Firefox
ii  mozilla-firefo 1.0.1lang20050 Mozilla Firefox English language/region pack
un  mozilla-psm    <none>         (no description available)

```

vs

```

dpkg --get-selections "*mozilla*"
flashplayer-mozilla                             install
mozilla-firefox                                 install
mozilla-firefox-gnome-support                   install
mozilla-firefox-locale-en-gb                    install

```

I also prefer aptitude, because if I want to search from the available packages, the command is almost the same:
# aptitude search mozilla
and because it rocks  :)

---

