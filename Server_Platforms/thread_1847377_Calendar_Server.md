---
title: "Calendar Server"
date: 2011-09-20
forum: Server Platforms
---

### Post by bonfire89 on 2011-09-20
Hey there,

I'm looking to setup a calendar server. Thunderbird/Lightning needs to be able to attach to it and maybe some point later in time attach a web interface to it.

Any suggestions on what to install?

Thanks

---

### Post by agillator on 2011-09-20
Use apache as the server. All you really need is a web server with DAV capabilities activated. Once DAV is working, the magic is in the format of the date file(s) - ics, not in the server.

---

### Post by bonfire89 on 2011-09-20
I'm currently looking into [http://httpd.apache.org/docs/2.0/mod/mod_dav.html](http://httpd.apache.org/docs/2.0/mod/mod_dav.html) looks really cool! Thanks for the tips.

I'll leave the thread open for a day or two see what else comes in, but this like be it!

Makes sense though, at the moment I'm using google calendar, and the address I input to Lightning is simply an address to an xml file.

Thanks again!


EDIT: Successfully followed [http://www.ubuntugeek.com/howto-setup-a-remote-calendar-using-webdav-with-mozilla-sunbird.html](http://www.ubuntugeek.com/howto-setup-a-remote-calendar-using-webdav-with-mozilla-sunbird.html)

Good enough, case closed, thanks!!

---

