---
title: "Webinterface for Ubuntu repositories?"
date: 2005-01-02
forum: The Cafe
---

### Post by zeroK on 2005-01-02
Is there a listing comparable to packages.gentoo.org for Ubuntu? IMO it would be quite nice for example to see what packages have been released today for example in hoary/universe :-)

---

### Post by charleyramm on 2005-01-03
So far as i can tell, no. Best i came up with was 
apt-cache dump | grep Package: > output.txt

or taking a look in synaptic. Web interface shouldn't be too hard for someone who knows their stuff though.  How about it, devs?

---

### Post by zeroK on 2005-01-03
[QUOTE=charleyramm]So far as i can tell, no. Best i came up with was 
apt-cache dump | grep Package: > output.txt

or taking a look in synaptic. Web interface shouldn't be too hard for someone who knows their stuff though.  How about it, devs?[/QUOTE]
 Ah, apt-cache dump was it :-) Perhaps I've some time tonight to write at least a small Perl or Python script around it :-)

---

### Post by zeroK on 2005-01-03
:-( No time/date stored there

---

### Post by jdong on 2005-01-04
I once asked developer Daniel Stone (user daniels) about this. He liked the idea...

I really want to see a packages.debian.org equivalent for Ubuntu.

---

### Post by zeroK on 2005-01-05
[QUOTE=jdong]I once asked developer Daniel Stone (user daniels) about this. He liked the idea...

I really want to see a packages.debian.org equivalent for Ubuntu.[/QUOTE]
 Yes, but please also with something like a  "what's new today" view ;-) Is perhaps the date of the addition stored somewhere in the files themselves? Going on the mtimes on the primary FTP would be quite an overkill IMO.

---

### Post by oddabe19 on 2005-01-05
[QUOTE=zeroK]Is there a listing comparable to packages.gentoo.org for Ubuntu? IMO it would be quite nice for example to see what packages have been released today for example in hoary/universe :-)[/QUOTE]
 just goto distrowatch, and compare there.

---

### Post by jdong on 2005-01-05
It's not up-to-date always, doesn't sport the cool features (at-a-glance dependencies, changelog browsing, linking to appropriate source package) that the real packages.debian.org does.

---

### Post by zeroK on 2005-01-05
[QUOTE=jdong]It's not up-to-date always, doesn't sport the cool features (at-a-glance dependencies, changelog browsing, linking to appropriate source package) that the real packages.debian.org does.[/QUOTE]
 I first thought that perhaps the *-changes mailing lists could come in useful here (because of the timestamps in the mails) , but there seems to be quite a delay between the actual changes and the mails.

Or is there perhaps public svn/cvs (read) access?

---

