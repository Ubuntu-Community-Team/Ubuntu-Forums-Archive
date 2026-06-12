---
title: "samhain init and check problem"
date: 2008-12-15
forum: Security
---

### Post by mihalisla on 2008-12-15
Hello to all of you I Have aserious problem with samhain
1.I am trying to install samhain from source with the options :

./configure --with-gpg=/usr/bin/gpg --with-fp=DBAB3E5EBD75A9FFD65D0EEAECACA2758C9ACA18 --with-checksum=no --enable-login-watch  --enable-suidcheck --enable-install-name=name  --enable-stealth=197 --with-log-file=/var/log/name/name.log --with-config-file=/etc/name/namerc --with-data-file=/var/state/name/name_file --with-pid-file=/var/run/name/name.pid

I know that some options are not supported for ubuntu such as --with-kcheck
Is so far something unsupported

2.when I don't edit the /etc/name/namerc file(the cfg file of samhain)
samhain initiates but it doesn't checks with the cmd "sudo name -t check"
and i don't have a logfile nor a warning msg.

3.when I edit the cfg file it does not initiate!!!
When editing the file i use
I "name_stealth -g namerc>foo"
  "edit the foo file"
  "gpg -a --clear-sign --not-dash-escaped foo"
  "rm foo"
  "mv foo.asc foo"
  "name_stealth -s namerc foo"
  "name -t init "



Is there a cfg file for ubuntu with this options???

##name = the defined name of the --enable-install-name=name

---

### Post by jcsteele on 2008-12-15
samhain is available in the package system (universe) - why not use the package instead of installing from source?

```
$ sudo apt-get install samhain
```

---

### Post by mihalisla on 2008-12-15
I want at least gpg support !!!
My point of view is to see how the most advanced hids works on ubuntu.

---

### Post by mihalisla on 2008-12-15
Another thing is that with your solution i get the error msg 
"According to uname, your nodename is localhost, but your resolver
library cannot resolve this nodename to a FQDN.
Rather, it resolves this to localhost.
For more information, see the entry about self-resolving under
'Most frequently' in the FAQ that you will find in the docs/ subdirectory."
and I don't know what to do....:popcorn:

---

### Post by jcsteele on 2008-12-15
Check the samhain documents section.

Its complaining that your machine of "localhost" isn't corresponding to a Fully Qualified Domain Name (FQDN)...I don't think that is a show stopper though.  Check out the samhain site and their documents section, its covered in there.

---

### Post by mihalisla on 2008-12-15
how to solve this issue?
I didn't find anything referring to this than that "you should configure your dns"
How can I do this?

---

### Post by jcsteele on 2008-12-15
[http://www.la-samhna.de/samhain/manual/](http://www.la-samhna.de/samhain/manual/)

I don't know your particular setup, however the manual above is very detailed...skip the installation section if you installed the package.  the rest should help you get things underway.

---

### Post by mihalisla on 2008-12-15
thanx mate I'll try it out

---

### Post by hongri1998 on 2008-12-17
Manually operated **[ball valve](http://www.valvesupplier.net/petro-valve.htm)** can be closed quickly and thus there is a danger of water hammer. Some ball valves are equipped with an actuator that may be pneumatically or motor (electric) operated. These [ball valves]("http://www.valvesupplier.net/petro-valve.htm") can be used either for on/off or flow control.

---

