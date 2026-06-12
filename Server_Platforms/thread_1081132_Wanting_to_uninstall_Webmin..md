---
title: "Wanting to uninstall Webmin."
date: 2009-02-26
forum: Server Platforms
---

### Post by falconed7 on 2009-02-26
Hey everyone!

As the title says, I want to completely uninstall webmin so that I can test out eBox. How would I go about doing it?

Cheers.

---

### Post by bigbearomaha on 2009-02-26
apt-get remove webmin

---

### Post by volkswagner on 2009-02-26
> **bigbearomaha said:**
> apt-get remove webmin


If you did not use apt to install then use the following from the webmin [FAQ]("http://www.webmin.com/faq.html").

> # How can I uninstall Webmin?

Just run the command /etc/webmin/uninstall.sh .
If you have installed the RPM version of Webmin, you can also use rpm -e webmin, or if you have installed the Solaris package you can use pkgrm WSwebmin .


---

