---
title: "64bit UZ PPA update?"
date: 2011-07-16
forum: Ubuntuzilla
---

### Post by jamesisin on 2011-07-16
It would appear that Mozilla is finally providing a 64bit release for Thunderbird.  I have written an article about the current state of the matter here:

[http://jamesisin.com/a_high-tech_blech/index.php/2011/07/64bit-ubuntuzilla-blues/](http://jamesisin.com/a_high-tech_blech/index.php/2011/07/64bit-ubuntuzilla-blues/)

Is the 64bit repository right around the corner?

I'm excited to get my 64bit 10.04 machine up to date.

---

### Post by lovinglinux on 2011-07-16
Although Mozilla doesn't officially release a 64bit build of Firefox and Thunderbird, they do build them along with the 32bit version. The builds you get from Ubuntu repositories are 64bit.

If you want to get the latest Firefox 5 and Thunderbird 5 on your machine, completely uninstall Ubuntuzilla and install the mozillateam ppa:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
```

```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
sudo apt-get upgrade
```

Those repositories are maintained by the people responsible for Firefox and Thunderbird on Ubuntu.

For additional info, see [Firefox 4,5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

---

### Post by jamesisin on 2011-07-16
I trust, by the inclusion of the word stable, these are not the nightlies?

---

### Post by lovinglinux on 2011-07-16
> **jamesisin said:**
> I trust, by the inclusion of the word stable, these are not the nightlies?

Exactly. I suspect they come from [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/5.0.1/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/5.0.1/linux-x86_64/) and [http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/5.0/linux-x86_64/]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/5.0.1/linux-x86_64/")

---

### Post by nanotube on 2011-07-17
> **lovinglinux said:**
> Exactly. I suspect they come from [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/5.0.1/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/5.0.1/linux-x86_64/) and [http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/5.0/linux-x86_64/]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/5.0.1/linux-x86_64/")

if only they'd add a seamonkey-stable stream to the mozilla-team ppas... then maybe ubuntuzilla can really finally retire. :)

---

### Post by nanotube on 2011-07-17
> **jamesisin said:**
> It would appear that Mozilla is finally providing a 64bit release for Thunderbird.  I have written an article about the current state of the matter here:

[http://jamesisin.com/a_high-tech_blech/index.php/2011/07/64bit-ubuntuzilla-blues/](http://jamesisin.com/a_high-tech_blech/index.php/2011/07/64bit-ubuntuzilla-blues/)

Is the 64bit repository right around the corner?

I'm excited to get my 64bit 10.04 machine up to date.

are the mozilla team -stable streams satisfactory for you? or do you still have a preference for having 64bit builds in ubuntuzilla?

---

### Post by lovinglinux on 2011-07-17
> **nanotube said:**
> if only they'd add a seamonkey-stable stream to the mozilla-team ppas... then maybe ubuntuzilla can really finally retire. :)

BTW, I didn't see any announcements about Firefox 64bit being officially released, but I think they are doing that now, since it is available in the releases ftp site, at least for Firefox 5 version.

---

### Post by jamesisin on 2011-07-18
nanotube - You're saying these are the 32bit builds then?  How can I be sure?

---

### Post by nanotube on 2011-07-19
> **lovinglinux said:**
> BTW, I didn't see any announcements about Firefox 64bit being officially released, but I think they are doing that now, since it is available in the releases ftp site, at least for Firefox 5 version.

indeed, i see ff and tb having 64bit builds on the releases server, so that's official enough for me. :)

---

### Post by nanotube on 2011-07-19
> **jamesisin said:**
> nanotube - You're saying these are the 32bit builds then?  How can I be sure?

ubuntuzilla is 32bit builds only. 
the mozilla team -stable... i don't know. haven't used those repos myself.

---

### Post by jamesisin on 2011-07-19
Cool.  I'm going to assume they are 64bitters.

Does anyone know of a test I can perform on a piece of software on my system to determine if it's 32 v 64?  I'd like to know if that's possible.

---

### Post by jamesisin on 2011-07-19
You can read my final write-up here:

[http://jamesisin.com/a_high-tech_blech/index.php/2011/07/keep-stable-thunderbird-current-on-64bit-ubuntu/](http://jamesisin.com/a_high-tech_blech/index.php/2011/07/keep-stable-thunderbird-current-on-64bit-ubuntu/)

---

### Post by lovinglinux on 2011-07-19
> **nanotube said:**
> ubuntuzilla is 32bit builds only. 
the mozilla team -stable... i don't know. haven't used those repos myself.

They have 32bit and 64bit.

---

### Post by jamesisin on 2011-07-19
Thanks.  That was my assumption.

Do you know of a test I can run on a piece of software to determine if it's 32 v 64 bit?

---

### Post by nanotube on 2012-01-09
jamesisin: fyi, ubuntuzilla now includes 32 and 64 bit builds.

---

### Post by jamesisin on 2012-01-10
Thanks, nanotube.  I have updated my article to say as much.

[http://jamesisin.com/a_high-tech_blech/index.php/2011/07/keep-stable-thunderbird-current-on-64bit-ubuntu/](http://jamesisin.com/a_high-tech_blech/index.php/2011/07/keep-stable-thunderbird-current-on-64bit-ubuntu/)

---

### Post by nanotube on 2012-01-10
> **jamesisin said:**
> Thanks, nanotube.  I have updated my article to say as much.

[http://jamesisin.com/a_high-tech_blech/index.php/2011/07/keep-stable-thunderbird-current-on-64bit-ubuntu/](http://jamesisin.com/a_high-tech_blech/index.php/2011/07/keep-stable-thunderbird-current-on-64bit-ubuntu/)

cool :)

---

