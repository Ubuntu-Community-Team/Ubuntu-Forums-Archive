---
title: "Ubuntu 7.04 !!"
date: 2011-03-31
forum: Server Platforms
---

### Post by elliotbeken on 2011-03-31
Hi all i have an old Dell Power edge 2400 and i have Ubuntu 7.04 installed, all seems to work well but i cant seem to install apache etc i want to create a LAMP server but from what i am guessing 7.04 in not supported any more...

so how do i install the packages if i even can thanks

Elliot Beken

---

### Post by BkkBonanza on 2011-03-31
You should upgrade it to a newer version that is supported. By using an old version like that you will be open to known security attacks. If you update to at least one of the long-term supported releases you will get security fixes right up to now (even though the version is older).

See [this page for release support]("https://wiki.ubuntu.com/Releases") dates and choose one that isn't "end of life" too soon. You will also find that fixes may may it work better as well. You can upgrade online without doing a re-install. 

I'd suggest 8.04 (til 2013) or 10.04.1 (til 2015).

Running a web server on an out dated OS is a bad idea.

---

### Post by elliotbeken on 2011-03-31
yeh i would like to use a different version but the dell wont run anything newer that 7.04 with out big problems such as screen resolutions.

thanks

---

### Post by BkkBonanza on 2011-03-31
You could try just downloading the deb file and installing from that.

I'd try the [8.04 version]("http://packages.ubuntu.com/hardy/all/apache2/download") as that's fairly close to your 7.04 install.

I'm not sure what they may have changed. You could also go to the upstream Debian source but I suspect that will be more different than the regular 8.04 one. Newer versions may be preferable but also may have some problem on an old install (no idea what though).

Once you have the deb file you can install with the command,

**sudo dpkg -i apache2_2.2.8-1ubuntu0.19_all.deb**
(or whatever version you end up with)
(if it doesn't seem to go well you can remove it, see **man dpkg**)

Likewise for other packages you may need like mysql, php etc.

---

### Post by Vegan on 2011-03-31
I would suggest a clean install of the current version.

This way security updates are regularly posted

---

### Post by arrrghhh on 2011-03-31
> **elliotbeken said:**
> yeh i would like to use a different version but the dell wont run anything newer that 7.04 with out big problems such as screen resolutions.

thanks

Screen resolutions?  On a server?  That should be the least of your concerns when building a server... Especially with no GUI!

---

### Post by elliotbeken on 2011-03-31
i know all my other servers are headless and mainly ssh configured but the purpose of this server is to allow students to play with the ubuntu interface and also allow them to install and configure a server

---

### Post by arrrghhh on 2011-03-31
> **elliotbeken said:**
> i know all my other servers are headless and mainly ssh configured but the purpose of this server is to allow students to play with the ubuntu interface and also allow them to install and configure a server

Install and configure a server?  No GUI on the server...

Play with the Ubuntu interface?  In what way?  The CLI...?

If you mean GNOME, that's not really the "Ubuntu interface".  It also has nothing to do whatsoever with the server edition...

I would think if you're teaching people how to install the server edition, they'd install and work with the server edition...

---

