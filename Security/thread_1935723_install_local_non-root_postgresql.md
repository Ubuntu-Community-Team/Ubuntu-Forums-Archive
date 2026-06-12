---
title: "install local non-root postgresql?"
date: 2012-03-04
forum: Security
---

### Post by zephyr707 on 2012-03-04
Hi there,

I think this would be the appropriate place to post.  I'm trying to install afanasy, a render queue manager, and it requires postgresql (I get afserver: error while loading shared libraries: libpq.so.5: cannot open shared object file: No such file or directory).

I don't have root access to the machine I'm on, and I've tried to find a way to install it locally to my home directory, but I can't figure it out and have not been able to find any leads on google or forums.  I don't have a lot of experience making things from source (I've done it, but when it doesn't work i'm clueless as to how to fix errors...), so would prefer a binary or something simple that I can point afanasy to.

Is this impossible or standard fare?  I'm pretty lost, so thanks for any help!

z

amd64 10.04.3 LTS

---

### Post by zephyr707 on 2012-03-04
ok, I found [this]("http://askubuntu.com/questions/339/how-can-i-install-a-package-without-root-access") helpful page.  It seems simple enough to install with dpkg, but how do I easily resolve all the dependencies?  I found a ppa [here]("http://ppa.launchpad.net/pitti/postgresql/ubuntu/pool/main/p/"), do I just download all the relevant debs for my distro and run dpkg on them?  seems kludgy...

---

### Post by Diametric on 2012-03-05
dpkg doesn't handle dependencies - only apt, aptitude and/or synaptic can mange that for you.  If you cannot use these tools because you're not root, you may have to install the dependencies manually.  

Good luck.

---

### Post by OpSecShellshock on 2012-03-05
If this is in an enterprise, make a request for the administrator to bring in the dependencies. If it's necessary then I wouldn't expect it to be a problem. Anything other than what the system owner allows gets awfully close to circumvention of controls, and in order to follow the rules here we can't really advise on how to do that.

---

### Post by dreafdoonry on 2012-03-09
Ok, I downloaded it again from scratch and the install went fine.  I completed ./configure ./make and ./make install with no errors.  Now I just need to figure out how to run it.  I tried commands like this and got nothing...


Code:

---

### Post by zephyr707 on 2012-03-21
> **OpSecShellshock said:**
> If this is in an enterprise, make a request for the administrator to bring in the dependencies. If it's necessary then I wouldn't expect it to be a problem. Anything other than what the system owner allows gets awfully close to circumvention of controls, and in order to follow the rules here we can't really advise on how to do that.

fair enough.  it is on my university workstation.  it took them 2 months to let me know through their ticketing system that I could plug in my own US layout keyboard... so I think i'll just find another way.

thanks

---

### Post by SeijiSensei on 2012-03-21
By default "make install" will place the PG files in /usr/local/pgsql.  However you need to be root to write into /usr/local so it's unlikely they've been placed there.  See if you can determine where it put the "postmaster" binary and the pg_hba.conf file.  Let's call these the "pgbin" and "pgdata" directories.

Now try creating the basic database with "/path/to/pgbin/initdb /path/to/pgdata".  It might work or it might fail because it wants root privileges.  If it works, you can try starting the server with "/path/to/pgbin/postmaster -p 5432 /path/to/pgdata".

I'll be surprised if you can get this stuff running without root privileges, though.

---

