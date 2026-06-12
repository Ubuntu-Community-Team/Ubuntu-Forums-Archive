---
title: "CPAN and libgd"
date: 2010-12-07
forum: Server Platforms
---

### Post by JasonFWard on 2010-12-07
I am trying to insall CPAN, apparently I do this by typing CPAN at the command line.

After much else, this results in```
[COLOR=#000000][FONT=Times New Roman][COLOR=#272727][FONT=Verdana]**UNRECOVERABLE ERROR**
Could not find gdlib-config in the search path. Please install libgd 2.0.28 or higher.
If you want to try to compile anyway, please rerun this script with the option --ignore_missing_gd.
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
Warning (usually harmless): 'YAML' not installed, will not store persistent state
  LDS/GD-2.45.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Could not read '/home/gt/.cpan/build/GD-2.45-YKSQJZ/META.yml'. Falling back to other methods to determine prerequisites[/FONT][/COLOR][/FONT][/COLOR]
```[COLOR=#000000][FONT=Times New Roman][COLOR=#272727][FONT=Verdana]

[FONT=Arial]I've tried to install libgd but only get```
root@lamp gt/geniustrader# apt-get install libgd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgd

```[Google was no great help]("http://www.google.com/search?client=ubuntu&channel=fs&q=libdg+ubuntu&ie=utf-8&oe=utf-8#sclient=psy&hl=en&q=libgd+ubuntu+install&aq=1c&aqi=g1g-c2g-m1&aql=&oq=&gs_rfai=&pbx=1&fp=4824b41ba0d4cfd8").

Any other ideas?
[/FONT][/FONT][/COLOR][/FONT][/COLOR]

---

### Post by windependence on 2010-12-07
```
apt-get install libgd 2.0.28 
```

[COLOR=#272727]Make sure you have the correct repositories installed also.[/COLOR]
[COLOR=#272727][/COLOR] 
 

-Tim

---

### Post by JasonFWard on 2010-12-08
Erm that's never going to work, it will attempt to install two packages one called "libdg" and another called "2.0.28"

I've done a lot more research on this, and I still don't understand.

[http://www.google.co.uk/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=Could+not+find+gdlib-config+in+the+search+path.+Please+install+libgd+2.0.28+or+higher#q=Could+not+find+gdlib-config+in+the+search+path.+Please+install+libgd+2.0.28+or+higher&hl=en&prmd=iv&ei=KJb_TK3mH4O1hAfA-529Cw&start=10&sa=N&fp=24ebbf6bcd184597](http://www.google.co.uk/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=Could+not+find+gdlib-config+in+the+search+path.+Please+install+libgd+2.0.28+or+higher#q=Could+not+find+gdlib-config+in+the+search+path.+Please+install+libgd+2.0.28+or+higher&hl=en&prmd=iv&ei=KJb_TK3mH4O1hAfA-529Cw&start=10&sa=N&fp=24ebbf6bcd184597)

These are all examples of people with same problem

[http://www.thegeekstuff.com/2010/05/install-bugzilla-on-linux/](http://www.thegeekstuff.com/2010/05/install-bugzilla-on-linux/)
[http://fixunix.com/mozilla/520838-gd-install-trouble.html](http://fixunix.com/mozilla/520838-gd-install-trouble.html)
[http://www.tek-tips.com/viewthread.cfm?qid=1546828&page=2](http://www.tek-tips.com/viewthread.cfm?qid=1546828&page=2)
[http://joshuahunter.com/pmwiki/pmwiki.php?n=Main.RT381InstallNotes](http://joshuahunter.com/pmwiki/pmwiki.php?n=Main.RT381InstallNotes)
[http://markmail.org/message/qo2kg3plffrbmymj#query:+page:1+mid:qo2kg3plffrbmymj+state:results](http://markmail.org/message/qo2kg3plffrbmymj#query:+page:1+mid:qo2kg3plffrbmymj+state:results)

But I still dont see how I can fix this in Ubuntu :(

---

### Post by JasonFWard on 2010-12-08
Ok solved

```
sudo apt-get -y install libgd2-xpm-dev build-essential
```

---

### Post by tver3305 on 2011-06-12
> **JasonFWard said:**
> Ok solved

```
sudo apt-get -y install libgd2-xpm-dev build-essential
```

Thanks....your post helped me too

---

### Post by NickyRuggs on 2013-03-27
same here.

thank you

---

### Post by dumparun on 2013-06-11
> **JasonFWard said:**
> Ok solved

```
sudo apt-get -y install libgd2-xpm-dev build-essential
```

Thanks for this solution, this helped me too.

---

