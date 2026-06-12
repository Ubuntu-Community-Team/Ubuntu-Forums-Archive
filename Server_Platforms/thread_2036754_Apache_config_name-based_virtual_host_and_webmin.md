---
title: "Apache config name-based virtual host and webmin"
date: 2012-08-02
forum: Server Platforms
---

### Post by tseb on 2012-08-02
Hi all.

I have been using Ubuntu server since system 8, but I am really a Mac user. 

I have been asked to set up a simple server for a very small company to host their websites, and thought "ah, Ubuntu - simple". But since my own server runs 10.04 and the new one I have just installed is on 12.04 there seems to have been some major changes in the config of Apache.

I have the system installed no problem. I can ssh in from home over VPN no problem. I have installed the latest Webmin, but now I tried to setup name-based virtual hosts, and it seems so much more difficult. Before in webmin (I avoid CLI as much as I can...) I would be able to add virtual server either through webmin itself or manually adjusting the config file within the apache-global part of webmin. That would change a global conf file where all the virtual hosts were listed in order. Is it still like that? I tried to add virtual hosts but it only saw the first in the list. The others didn't seem to have any effect at all. 
I really want the setup so the local guy at the company can add web sites by copying into this one file rather than a lot of separate files to which he has to add another (he is a windows user and not used to any command line or permissions or anything - he connects to the server using samba to change web files, and webmin for anything else).

I have looked through the forums and found several posts about this subject but nothing detailing how to add virtual hosts using webmin and it actually working!

Any help would be very appreciated.

Tseb.

---

### Post by tseb on 2012-08-07
No reply? Can anybody help with this please? Or point me in the right direction. 

Thanks. 
Tseb

---

### Post by koenn on 2012-08-08
he debian/ubuntu approach is that there's a seperarte file for each apache vhost; adding a site is as simple as copying one of those and edit the bits that make it unique (set a server name, point it to the relevant directory, ...)

Never used webmin, so can't help you there.

I'm also not a big fan of the "I have no idea what I'm doing but i can point and click until it works"-approach to system administration. 

Ubuntu servers are CLI machines; even Webmin is, afaik, not supported. Maybe you need something else.

---

### Post by rukiaEnix on 2012-08-08
Is better doing things by hand, I also don't like just click here and there and see what happens.

---

### Post by mikeatvillage on 2012-08-10
Doubt if this helps, but I've just had to do something similar, but mine are only Intranet virtual sites ... eg.
 
[www.mysite.com/~onesite]("http://www.mysite.com/~onesite")
[www.mysite.com/~othersite]("http://www.mysite.com/~othersite")
 
etc.
 
If you're trying to set up sites accessible from the outside world .. eg.
 
[www.mysite1.com]("http://www.mysite1.com")
[www.mysite2.com]("http://www.mysite2.com")
 
etc., don't these need to be registered in DNS somewhere?

---

### Post by koenn on 2012-08-10
> **mikeatvillage said:**
> don't these need to be registered in DNS somewhere?
yes.

---

