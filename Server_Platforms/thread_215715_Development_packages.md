---
title: "Development packages?"
date: 2006-07-14
forum: Server Platforms
---

### Post by bbatsell on 2006-07-14
Hello all.  New to ubuntu (and any Debian derivative), and still learning my way around apt-get and such.  I prefer using package-based systems, but I haven't been able to find almost any of the *-devel packages (typically found in other package systems, include libraries and headers for compiling programs against them).  So far I've tried to find mysql-devel, openssl-devel; also tried other variants like *-libs, *-includes to no avail.  Just in case, I uncommented the universe repository and ran apt-get update, but I'm still coming up with nothing.  Is there a way to get these packages on Ubuntu?  I've searched the forums and the Ubuntu documentation and haven't found anything specific to this.  TIA.

Using Dapper (6.06) Server, PowerPC.

---

### Post by az on 2006-07-14
[http://packages.ubuntu.com/dapper/libdevel/libmysqlclient15-dev](http://packages.ubuntu.com/dapper/libdevel/libmysqlclient15-dev)
[http://packages.ubuntu.com/dapper/libdevel/libssl-dev](http://packages.ubuntu.com/dapper/libdevel/libssl-dev)

---

### Post by muppetmaster on 2006-08-14
I am on 6.0.6 and attempting to install openssl-devel and ncurses-devel, but I do not understand the response above.  How does one obtain these via the Synaptic Package Manager?

---

### Post by adamc55 on 2006-08-14
If you click on the search button in synaptic and type in "libssl-dev", you should find it... I did.:p

---

### Post by muppetmaster on 2006-08-14
I did on the libssl, but not on the ncurses one.  I ended up doing an apt-get and got them that way.  I may just be confused...

---

