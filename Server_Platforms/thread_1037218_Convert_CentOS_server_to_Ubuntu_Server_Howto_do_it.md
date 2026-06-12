---
title: "Convert CentOS server to Ubuntu Server? Howto do it?"
date: 2009-01-11
forum: Server Platforms
---

### Post by uberbuntufan64y on 2009-01-11
I am currently trying to convert my entire setup to Ubuntu 100%.

I had a friend of mine set up a CentOS server in my house so I could store my files basicly and back up to it. He put some kind of compression program on it so that it can back up very nicely to blue ray discs, which is pretty neat.

He recently went on a service project in Morroco and will be gone for a year, and I want to convert this server to Ubuntu, and he won't be around to help.

I was wondering what I should back up in order to make this work right and what I need to prepare??? Thanks in advance!

---

### Post by whoop on 2009-01-11
It's not really possible converting centos to ubuntu. There different distro's that are based on different distro's. Ubuntu is based on Debian and CentOS is based on red hat (I think). Maybe you can best to a multi boot keeping your old centos for the time being.
Do a clean install of ubuntu and install the packages you require. There are probably some configuration files in CentOS you can reuse or use as a reference. Once everything is working you can remove CentOS.

If you want/need to remove CentOS you should at least backup the user directory of the account you login with and (configuration files in) the /etc/ dir.

---

### Post by uberbuntufan64y on 2009-01-11
I've tried to multiboot before and it's always resulted in a bucket of fail...

I am starting a backup of my /etc to my flash drive, then I need to backup user profiles or something? I'll copy that next. I have about a tons worth of data or more I think so it will take awhile.

---

### Post by uberbuntufan64y on 2009-01-11
btw where are the user profiles in Linuz?

---

### Post by AlexDudko on 2009-01-11
> **uberbuntufan64y said:**
> I've tried to multiboot before and it's always resulted in a bucket of fail...

I am starting a backup of my /etc to my flash drive, then I need to backup user profiles or something? I'll copy that next. I have about a tons worth of data or more I think so it will take awhile.

This is almost completely useless. 
First of all not all conf files contain the entire list of used directives. Many of them simply contain links to other conf files. They differ a lot from a distro to a distro.
Secondly, file names and directories also can differ.
For example, apache config file in Ubuntu is /etc/apache2/apache2.conf whereas in CentOS it must be /etc/httpd/httpd.conf.
Also vsftpd.conf file in Ubuntu can be found in the /etc directory, whereas in CentOS it will be /etc/vsftpd/vsftpd.conf.
You should just "pick up" the mere directives from config files.

---

### Post by cariboo on 2009-01-11
I would suggest if it ain't broke, why fix it.

Jim

---

