---
title: "battle of wesnoth package too old to allow to join official server"
date: 2007-02-01
forum: Repositories &amp; Backports
---

### Post by glabouni on 2007-02-01
I just discovered[ battle of wesnoth]("http://www.wesnoth.org/"). 
played the tutorial and felt like trying to play online.

there's only one problem though. the wesnoth package available from the repositories is too old to meet minimal version required to join the server. 
server requires at least 1.1.12, current edgy universe repository version is 1.1.8, current stable version is 1.2.1

not really an issue for me as I know how to compile, but it is not really user friendly to offer a half usable package and not really the desktop experience one might expect from ubuntu.

---

### Post by randomas on 2007-02-03
Considering that Dapper Drake is LTS version and it has wesnoth 1.0.2 this is obviously a problem. 

Unfortunately all packages that have to interface with services that require updated versions to function suffer from these issues, amsn is one of these, the supported version cannot logon using the http method because new protocols were made. It would be nice if this kind of packages had a continuous upgrade policy, without it they just become a waste of digital space.

---

### Post by bmartin on 2007-02-06
I agree: not having a new Wesnoth is very painful. In addition to not being able to connect to servers, I had to disable the ALT+SPACE keyboard shortcut (brings up application menu) in order to use the keyboard shortcut to end my turn.

---

### Post by agiamba on 2007-02-10
wesnoth's site has a fairly easy guide to compile it from source, currently it's not in any of the repositories but thatll probably change soon.

---

### Post by Fluffy, the jolly sheep on 2007-02-14
FYI, I've [requested]("https://bugs.launchpad.net/edgy-backports/+bug/79139") a backport to edgy some time ago, but seems they haven't gotten around to it. 
There is a 1.2.1 deb package [here]("http://www.getdeb.net/search.php?release=Edgy&keywords=wesnoth") available at getdeb.net however.

---

### Post by deadlydeathcone on 2007-02-15
Ive been using the [debian version]("http://www.ubuntuforums.org/showthread.php?t=326787&highlight=wesnoth") on Edgy without any problems.

edit: I probably should have read the second page of the thread I linked to. Just use Fluffy's link instead.

---

