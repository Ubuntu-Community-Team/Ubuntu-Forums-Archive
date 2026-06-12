---
title: "How to preseed using local repo (cannot import key during install) - 18.04"
date: 2018-03-20
forum: Ubuntu Development Version
---

### Post by gregster on 2018-03-20
I've got a build system using TFTP, stock netboot images, and preseeding. My builds rely on packages in the local repo (which is signed).
My preseed looks like this:
d-i apt-setup/local0/repository string [http://example.com/reponame](http://example.com/reponame) bionic main
d-i apt-setup/local0/key string [http://example.com/reponame/keys/my-keyring.gpg](http://example.com/reponame/keys/my-keyring.gpg)
d-i apt-setup/local0/source boolean false
This setup added my repo tp /etc/apt/sources.list, and made packages in that repo available during the initial install (using 'd-i pkgsel/include string my-pkg-name')

It has worked very well for a number of years, but 18.04 test builds reliably fail.
It appears as though apt-key has been removed from the apt udeb, so preseeding is no longer able to import a key. This is apparently intentional - see [here]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=851774").

Although the bug report hints at some possibilities I've yet to figure out how to use my local repo in bionic builds.

I've tried a number of methods already, such as rebuilding initrd with the keys inserted to various locations, early_command to add key, etc. but no joy so far.

Does anyone have any idea how to do it now?

---

### Post by dreibh on 2018-03-22
The only possibility to add custom repositories to Ubuntu Bionic seems to be a late_command. See my VM template script here: [https://github.com/simula/melodic-nornet/tree/master/src/images](https://github.com/simula/melodic-nornet/tree/master/src/images) . late_command is the most reliable way to work around broken features in the installer. I also use it to set the keyboard layout (see [https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1553147](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1553147)).

---

### Post by gregster on 2018-04-10
Sorry, I should have responded sooner.
I got it working using your template, so thanks!
I sure hope a less contorted method is coming.

---

