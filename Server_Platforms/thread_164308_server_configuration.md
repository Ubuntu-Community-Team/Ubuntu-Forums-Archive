---
title: "server configuration"
date: 2006-04-22
forum: Server Platforms
---

### Post by gymsmoke on 2006-04-22
I setup qmail and vpopmail according to the setup pages at qmailrocks.org ...
During that installation, sendmail, postfix, and exim are removed.

Now, apt-get upgrade, apt-get install clamav, and apt-get spamassassin all produce errors like this:

root@mgjventures:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  maildrop: Depends: exim but it is not installed or
                     mail-transport-agent
  mailx: Depends: postfix but it is not installed or
                  mail-transport-agent
E: Unmet dependencies. Try using -f.

Is there a way that I can specify that I don't want these packages in my upgrade or install list?

Update: apt is completely broke now.  Every apt-get operation fails with the same error as noted above...

Why would Ubuntu setup these dependencies this way??????

---

### Post by fdoving on 2006-04-22
Hi.
You can use a dummy package like the one i have at: [http://ubuntu.lnix.net/misc/mta-dummy/](http://ubuntu.lnix.net/misc/mta-dummy/)

download and install:
```

wget http://ubuntu.lnix.net/misc/mta-dummy/mta-dummy_1.0_all.deb

sudo dpkg -i mta-dummy_1.0_all.deb

```


The problem is that all packages depending on a MTA depends on 'mail-transport-agent' which is a virtual package provided by the .deb packages of postfix, exim and so on.

If you install the MTA, in your case qmail, without telling dpkg about it, the packages installed with dpkg/apt are not aware of your qmail installation and tell you that they can't do their job without the mail-transport-agent service. By installing the mta-dummy package you tell dpkg/apt that you handle your MTA yourself without dpkgs help, and that you provide the services expected by an MTA. That way everyone is happy.

- Frode

---

### Post by gymsmoke on 2006-04-22
frode~
Thanks!!! 
Would it also help if i re-installed qmail/vpop (or any other source packages for that matter) with something called "checkinstall"  - i think that's what it's called

??

---

### Post by fdoving on 2006-04-22
That would help a little bit. It would make uninstalling easier at least. Packages made with checkinstall are generally not very good. They are basically just useful to keep track of the files and which package they belong to. Using it to make packages for distribution is not recommended. For personal use just to keep track of files, better than nothing. 

- Frode

---

### Post by gymsmoke on 2006-04-22
frode~
Thanks an awful lot for the help!
the dummy package calmed apt...
I guess the real solution is for an Ubuntu package for qmail, vpopmail, and the rest of the packages that I don't have...
Is it very difficult to build a package for Ubuntu ?

---

