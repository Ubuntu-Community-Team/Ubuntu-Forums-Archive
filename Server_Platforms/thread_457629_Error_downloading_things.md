---
title: "Error downloading things"
date: 2007-05-28
forum: Server Platforms
---

### Post by chimerical_brio on 2007-05-28
I'm trying to set up Drupal within my Ubuntu-server box, per the instructions [here]("http://ubuntuforums.org/showthread.php?t=182166"), but I'm having trouble installing things. I can't really remember how I got here, but, when I try to install something like php5-mysql, I get the following message:

'Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  drupal-5.1: Depends: php5 but it is not going to be installed
              Depends: php5-gd but it is not going to be installed
  libapache2-mod-php5: Depends: php5-common (= 5.2.1-0ubuntu1) but 5.2.1-0ubuntu1.1 is to be installed
  php5-mysql: Depends: php5-common (= 5.2.1-0ubuntu1.2) but 5.2.1-0ubuntu1.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).'

And when I try to run 'sudo apt-get -f install', I get the error:

'Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libapache2-mod-php5 5.2.1-0ubuntu1.1
  404 Not Found [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main php5-common 5.2.1-0ubuntu1.1
  404 Not Found [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main php5 5.2.1-0ubuntu1.1
  404 Not Found [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main php5-gd 5.2.1-0ubuntu1.1
  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.2.1-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.2.1-0ubuntu1.1_i386.deb)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.1-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.1-0ubuntu1.1_i386.deb)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.1-0ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.1-0ubuntu1.1_all.deb)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.1-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.1-0ubuntu1.1_i386.deb)  404 Not Found [IP: 82.211.81.138 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?'

Any ideas?

---

### Post by chimerical_brio on 2007-05-28
...anyone?

---

### Post by Alterax on 2007-05-30
The abundance of 404 errors are telling me that you are having trouble connecting.  Captain obvious, I know, I know.  So the best bet is to find out WHY.  Let's start with checking your network to see if you can get anything back.

ping [www.google.com](www.google.com)
(you'll have to CTRL-C to quit, after 4 it should be evident).
If you're getting 100% packet loss, try:

ping 216.239.51.99
(same rules apply, this is the IP address for google.com)
If you get something back, then it's your DNS settings, which can be set in /etc/resolv.conf
If NOT, check /etc/network/interfaces to make sure that your IP address is set up correctly.  Change it if you must, then sudo /etc/init.d/networking restart and try again.

Once both of these above work fine, try the apt-get install again.  If this doesn't work, it may be that the repository you are trying to download from is out for a bit.  Here's how to try another one:

You may want to look in your software sources panel (in System, Administration) to see if there's another place you could get the files from.

If you aren't using a GUI/Desktop manager, just let me know and I'll give you a copy of my repository sources.  They've yet to fail me.

Let me know if this helps!

--Alterax

---

### Post by cookfromfrozen on 2007-05-30
sudo apt-get update

---

### Post by chimerical_brio on 2007-05-30
Well, strangely enough, after a reboot, it worked fine. Thanks anyway!

---

### Post by FoxFive50 on 2007-10-15
I can get to google and security.ubuntu.com etc on a browser (firefox) when i use cli and try to ping they both give 'destination host unreachable' errors.

Ideas?

---

