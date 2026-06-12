---
title: "Help help my third post"
date: 2007-08-03
forum: Repositories &amp; Backports
---

### Post by catch2two on 2007-08-03
I posted this on Ab Beg. forum but no body could help i am going to reinstall soon if i do net hear anything:

I posted further down this page i just want my comp to work again i cant update add/remove or use synaptic :

If i click on the orange square update i get this:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Id i go into synaptic and try and remove contacts i get this:

E: contacts: subprocess post-removal script returned error exit status 139

and it is highlighted in red.

I was very happy with my system but now it sucks

---

### Post by heimo on 2007-08-03
Sounds like package managers database - a bunch of text files - has corrupted. Happens quite rarely, and is usually possible to fix. May need some work though. It'd help if you could run that command in a terminal, and post us any lines with errors and warnings:
```
sudo apt-get install -f
```

Then we'll probably need to uninstall some packages, maybe move or rename couple files, reinstall packages and run the command above couple times. There are several threads with instructions how to do this on these forums, but names of the files vary depending on which file / package is corrupt.

---

### Post by catch2two on 2007-08-03
catch2two@catch2two:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  beryl-core libgsf-gnome-1-114 libgoffice-0-common kword-data
  linux-headers-2.6.20-15-generic libcairo-ruby beryl-settings-bindings
  libatk1-ruby libglib2-ruby libpango1-ruby gnumeric-common libberylsettings0
  libgdk-pixbuf2-ruby libakode2 libcairo-ruby1.8 libgoffice-0-3 beryl-plugins
  linux-headers-2.6.20-15 beryl-plugins-data libxul-common libberyldecoration0
  libwv2-1c2 kpresenter-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  contacts
0 upgraded, 0 newly installed, 1 to remove and 19 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 295kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 161099 files and directories currently installed.)
Removing contacts ...

(update-desktop-database:14605): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing contacts (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 contacts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by heimo on 2007-08-03
Disclaimer. There's always a slight chance of screwing up your system even further when trying to fix package manager database and/or using sudo/root permissions. Be careful.

If at any point apt-get or aptitude suggests removing half of your system, like tens, hundreds or thousands of packages, don't let it.

This is what I'd try next:
```
cd
mkdir bak
sudo mv /var/lib/dpkg/info/contacts.* bak
sudo aptitude --purge remove contacts
sudo aptitude install contacts
sudo aptitude -f install

```

---

