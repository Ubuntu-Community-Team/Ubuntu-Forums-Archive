---
title: "manual installation of web applications"
date: 2006-09-06
forum: Server Platforms
---

### Post by mentecat on 2006-09-06
Hi,
I just installed ubuntu server, I'd like to install a web application not present in the ubuntu repositories. Do you think I should try to install it following the debian/ubuntu guidelines or I should follow the installation instructions of the authors of the application? :-k 

Thanks

---

### Post by Jussi Kukkonen on 2006-09-06
Name the application, it'll be easier to help you... 

By the way, I'm a seasoned debian/ubuntu user and I'm not sure what you mean by debian/ubuntu software installation guidelines... You might want to be more specific.

---

### Post by mentecat on 2006-09-06
Hi,
I'd like to install Dokeos ([http://www.dokeos.com/](http://www.dokeos.com/)) and dotProject ([http://www.dotproject.net/)](http://www.dotproject.net/)).

I'm referring to this: [http://webapps-common.alioth.debian.org/draft/html/](http://webapps-common.alioth.debian.org/draft/html/)

things like web apps files under /usr/share/PACKAGE-NAME and configuration files under /etc/PACKAGE-NAME, usually I put everything under my web root

---

### Post by Jussi Kukkonen on 2006-09-07
> 
I'm referring to this: [http://webapps-common.alioth.debian.org/draft/html/](http://webapps-common.alioth.debian.org/draft/html/)


I see, thanks for the link. That is a packaging policy, so it'll probably be a little overkill for a single installation... Then again, if you are familiar with debian packaging, go ahead.

> usually I put everything under my web root
If you do a manual installation (as in not through dpkg), putting stuff in one place might be smarter... Just make sure you're not putting everything (like config files) in a web-accessible place, that is not smart.

---

