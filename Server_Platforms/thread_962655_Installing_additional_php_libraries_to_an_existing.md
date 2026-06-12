---
title: "Installing additional php libraries to an existing installation"
date: 2008-10-29
forum: Server Platforms
---

### Post by Daimonan on 2008-10-29
Hello Ubuntu Community!

I've recently been trying to use the libcurl library within php5, but I've realized that it wasn't configured with the original php install.  I've managed to download and instal the cURL library, however I haven't reconfigured php to use libcurl.

The big problem is that the main server admin is away this week, and I'm not sure what sort of libraries she originally installed, or if she made any other 'special considerations'.  

In short, I'm wondering if it is possible to 'append' libcurl to an existing php install without completely redoing everything.  The server isn't actually running Ubunutu, but it is Debian, and reading the forum here has been a huge help in the past (I have Ubuntu at home!)

Yes, I'm rather new at this.  If I've somehow logic'd out the process wrong, let me know!

---

### Post by lykwydchykyn on 2008-10-29
yes.  php in Ubuntu is broken up into modular packages containing various libraries like this.

The package you probably need to install is called php5-curl.
```

sudo aptitude install php5-curl

```

---

### Post by Daimonan on 2008-10-30
Unfortunately I'm not running ubuntu - just debian.  Will aptitude still work?

---

### Post by lykwydchykyn on 2008-10-30
Yes.  aptitude is the recommended package manager for Debian, per the Etch release notes.

You can use apt-get too, it doesn't matter.

Apart from specific package/version issues, Debian and Ubuntu are pretty much the same thing from a use standpoint (don't take that out of context and start a flame war, everyone).

---

### Post by Daimonan on 2008-10-31
Hey, thanks!
I ended up using the phpinfo(); command, which apparently displays the exact string used to configure the current install.  From there I just re-configured, made and made installed with the previous command, appending the --with-curl option.

I appreciate the help.  For some reason I thought apt was only a ubunutu thing.  That's good to know.

---

### Post by lykwydchykyn on 2008-11-01
While that works, if this is a production server I highly recommend using the repository packages.  If some security hole comes up in php and you need to upgrade, you're going to have a mess on your hands dealing with compiled packages.

That's your call, though; depends how comfortable you are with Linux.

---

### Post by sarafoster on 2008-11-01
Dear friends its the 100% rite way 
to earn money online i want to share it
if u r intrested then u can 
also do it easily free of cost thanks
 [http://howtomakemoneyonline1.weebly.com/](http://howtomakemoneyonline1.weebly.com/)

---

