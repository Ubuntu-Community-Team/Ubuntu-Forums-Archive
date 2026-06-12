---
title: "proxy problem with ports"
date: 2008-03-10
forum: Repositories &amp; Backports
---

### Post by DAC1138 on 2008-03-10
I'm having to connect to the internet via a proxy with my university.

I have apt-get setup through the proxy, and it seems to be able to partially download a the sources list. I found this out when I was playing around with the manual proxy settings with synaptic and the apt-get with command line.

I've already added the proxy info to the apt.conf file.

I think I've narrowed my problems down to it being a ports problem. I don't know which ports the university is using. I've tried 80 and 8080, and none of them have worked.

How can I figure out which ports to connect through to be able to apt-get and install programs?

By the way, I'm typing this on firefox on ubuntu through the proxy settings.

---

### Post by bapoumba on 2008-03-11
Please post the apt.conf file.
You can try port 3128, which is usual, or ask your network admins.

using the apt.conf file, you have to remove any proxy occurrence in synaptic.

---

### Post by DAC1138 on 2008-03-11
This is my apt.conf

DPkg::Post-Invoke {"echo Running prelink, please wait...;/etc/cron.daily/prelink";}

Acquire::http::Proxy "http://username:password@proxy.domain:8080";
Acquire::ftp::Proxy "ftp://username:password@proxy.domain:8080";

username/password/proxy.domain are all replaced by the proper settings, where my username is my student number and my password is my student password, and the domain is the proxy to the school. port 8080 i've changed to 80, and 3128 and nothing has worked.

---

### Post by bapoumba on 2008-03-14
> **DAC1138 said:**
> This is my apt.conf

DPkg::Post-Invoke {"echo Running prelink, please wait...;/etc/cron.daily/prelink";}

Acquire::http::Proxy "http://username:password@proxy.domain:8080";
Acquire::ftp::Proxy "ftp://username:password@proxy.domain:8080";

username/password/proxy.domain are all replaced by the proper settings, where my username is my student number and my password is my student password, and the domain is the proxy to the school. port 8080 i've changed to 80, and 3128 and nothing has worked.
I've never seen a line with dpkg in this file. Please try to comment it out (add a # at the beginning).
When you declare the proxy in GNOME or Firefox, what port do you use ?

---

### Post by DAC1138 on 2008-03-15
> **bapoumba said:**
> I've never seen a line with dpkg in this file. Please try to comment it out (add a # at the beginning).
When you declare the proxy in GNOME or Firefox, what port do you use ?

The DPKG line just runs prelink after new programs and libraries are installed. It's what yast does after you install apps. It helps with system load speeds. It doesn't affect proxy settings.

In firefox, the settings are automatic. There's manual proxy settings and automatic. When I use the automatic settings, it just asks for the proxy url, and when it accesses the URL and gets a response, it asks for a username and password. And it works from there.

---

### Post by bapoumba on 2008-03-15
> **DAC1138 said:**
> The DPKG line just runs prelink after new programs and libraries are installed. It's what yast does after you install apps. It helps with system load speeds. It doesn't affect proxy settings. Okay.

> **DAC1138 said:**
> 
In firefox, the settings are automatic. There's manual proxy settings and automatic. When I use the automatic settings, it just asks for the proxy url, and when it accesses the URL and gets a response, it asks for a username and password. And it works from there.
Is this an ISA proxy ?
Do you have parameters to try it out on manual settings from firefox ?

Side note: my univ also uses an automatic proxy (a .pac). To perform updates, I use the old proxy they have not disabled (after talking with the network admins).

---

### Post by DAC1138 on 2008-03-16
> **bapoumba said:**
> Okay.


Is this an ISA proxy ?
Do you have parameters to try it out on manual settings from firefox ?

Side note: my univ also uses an automatic proxy (a .pac). To perform updates, I use the old proxy they have not disabled (after talking with the network admins).

I don't have any parameters to try other manual settings for firefox. I would find it much easier to check with the admin for all this, however, there's only 1 and he's hardly around (or he's busy with other problems around the campus)

---

### Post by bapoumba on 2008-03-16
> **DAC1138 said:**
> I don't have any parameters to try other manual settings for firefox. I would find it much easier to check with the admin for all this, however, there's only 1 and he's hardly around (or he's busy with other problems around the campus)
May be with a nice email, and quoting this thread ?

---

