---
title: "&quot;Updating software catalog...this may take a moment.&quot;"
date: 2012-07-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jerrylamos on 2012-07-12
I'm installing Opera from the .deb file.

It takes far longer to "Updating software catalog...this may take a moment." than to do the install.

If Opera is installed, I sure don't need it in the "software catalog".

Any ideas how to do a "dpkg -i xxxxx.deb" without getting the penalty of a "Updating software catalog" which is useless?

Thanks for any ideas.

Jerrry

---

### Post by mc4man on 2012-07-12
It only occurs with some packages, in this case Opera

So why?

Well Opera's postinst script does a whole bunch of things inc. 
```
if available update-software-center
	then
		update-software-center
	fi
```

It also, among other things does this - 
```
# MIME associations
	if available update-mime-database
	then
		update-mime-database /usr/share/mime
	fi

```
Which is why I got these warning while installing Opera with dpkg

> Warning in file "/usr/share/applications/pcmanfm.desktop": usage of MIME type "x-directory/normal" is discouraged ("x-directory" is an old media type that should be replaced with a modern equivalent)
Warning in file "/usr/share/applications/marlin.desktop": usage of MIME type "x-directory/gnome-default-handler" is discouraged ("x-directory" is an old media type that should be replaced with a modern equivalent)
Warning in file "/usr/share/applications/marlin.desktop": usage of MIME type "x-directory/normal" is discouraged ("x-directory" is an old media type that should be replaced with a modern equivalent)



---

### Post by jerrylamos on 2012-07-12
mc4man, thanks for a clear explanation of why the update occurs.  My install messages were a bit different see below.  Two "updating software catalog" actions.  Since I put Opera in the launcher I'll never look for Opera in the catalog anyway.  

BTW, only reason I'm running Opera is mail.aol.com under Quantal Firefox won't do replies or compose or forward - can't enter into the text box.  Yes I entered a bug, no interest from Ubuntu or Firefox.

jerry@Aspire1:~$ sudo dpkg -i /run/media/jerry/ArchiveB/Downloads/opera_12.00.1467_i386.deb
Selecting previously unselected package opera.
(Reading database ... 161441 files and directories currently installed.)
Unpacking opera (from .../opera_12.00.1467_i386.deb) ...
Setting up opera (12.00.1467) ...
update-alternatives: using /usr/bin/opera to provide /usr/bin/x-www-browser (x-www-browser) in auto mode
update-alternatives: using /usr/bin/opera to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for software-center ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.

Jerry

---

### Post by ronacc on 2012-07-12
jerry , you don't need to "install" Opera . Just dl the tgz un pack it in your /home and make yourself a launcher or run it from term by cd'ing to the opera dir and running ./opera . I use that trick to run more than 1 version of Opera .

---

### Post by mc4man on 2012-07-12
The first instance "Updating software catalog...this may take a moment ..." comes from the postinst script
The 2nd instance is a bit  different  - it's part of the "Processing triggers for " group & has nothing to do with the postinst script

You'll notice that different packages may Process triggers for different things, what determines that in the course of building a package I don't really know
By & large unless a package contains an error in one of it's scripts I'd just let it do whatever it was set up to do.

---

### Post by jerrylamos on 2012-07-13
> **ronacc said:**
> jerry , you don't need to "install" Opera . Just dl the tgz un pack it in your /home and make yourself a launcher or run it from term by cd'ing to the opera dir and running ./opera . I use that trick to run more than 1 version of Opera .

Thanks, ronacc!  You people will teach me a little about linux yet.  It's like dumping a bucket of water onto a coke bottle, only a little gets in each time.

Jerry

---

### Post by dino99 on 2012-07-13
> **jerrylamos said:**
> Thanks, ronacc!  You people will teach me a little about linux yet.  It's like dumping a bucket of water onto a coke bottle, only a little gets in each time.

Jerry

that it, as the title says "this may take a moment" ):P

---

### Post by zika on 2012-07-13
> **ronacc said:**
> jerry , you don't need to "install" Opera . Just dl the tgz un pack it in your /home and make yourself a launcher or run it from term by cd'ing to the opera dir and running ./opera . I use that trick to run more than 1 version of Opera .The same "trick" could be used for Firefox-trunk or any other available in tar-ed directories of builds... :)

---

