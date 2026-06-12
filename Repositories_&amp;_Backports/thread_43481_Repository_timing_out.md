---
title: "Repository timing out"
date: 2005-06-22
forum: Repositories &amp; Backports
---

### Post by pompeyjohn on 2005-06-22
Hello all,

I have just installed Ubuntu, and after overcoming two slight issues (resolution stuck at 640 and ipv) I am now up and running - online, and at a workable resolution. So far I am delighted (and the Mahjongg game is excellent.) I have a problem with synaptic I hope someone can help with;

I am trying to connect to the community maintained repository, and I get the following messages;

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)

Any ideas?

Many thanks in advance.

John

ps. Before coming across this distribution I read in a book (called Notes from a Hip Hop planet) a different definition for the term Ubuntu. It is; People are people through people. I like that. Just thought I would share that.  :)

---

### Post by eskaypey on 2005-06-22
Rather then having that in your source.list, replace with this -- 

########  updated software
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
########  major bug fixes
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

########   universe / multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

---

### Post by pompeyjohn on 2005-06-22
thanks for the response - have updated the sources file accordingly.

Now when opening synaptic get the following error message;

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by pompeyjohn on 2005-06-22
and I am getting time out messages when trying to do an apt get.

 ](*,)

---

### Post by pompeyjohn on 2005-06-22
anybody ?!?!

---

### Post by eskaypey on 2005-06-22
[QUOTE=pompeyjohn]anybody ?!?![/QUOTE]
 [http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html)

---

### Post by pompeyjohn on 2005-06-22
I dont think there is a problem in the sources file - I have it as specified in the unoffical starter guide from this site.

Yet I cant seem to get a response from those sources.  Running 'sudo apt-get update' results in 'Could not connect to ....<whichever>.... connection timed out'

So, I am wondering if this might be a router issue? As I am happily typing this online using Ubuntu. If it is a router config problem, it could also explain why Gaim is not connecting........could that be the case?

---

### Post by pompeyjohn on 2005-06-22
Ok I am guessing the problem is the DNS server. After all 'Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out' 1.0.0.0 cant be right right??

I am confused though because I can get online at the moment.

These are the DNS server settings I have set on my router;
 
  	Preferred DNS Server 		 194.72.9.39
  	Alternate DNS Server 	         197.74.65.68

Which I believe are the correct ones for the British Telecom (BT) Broadband service I am using. 

Oh I am confused now.....

---

### Post by pompeyjohn on 2005-06-22
ok fixed it !!!

The way I solved it was to put my ISP DNS in resolv.conf instead that of the router that ubuntu automaticaly gets.

so ...

$ sudo gedit /etc/resolv.conf

coment out the old nameserver by proceeding it with #

#nameserver [whatever number]

and then add your ISP dns. It appears to be working for me. I hope it works for you too.

 \\:D/  :grin: 

John

---

### Post by cenithx on 2005-07-31
[QUOTE=pompeyjohn]ok fixed it !!!

The way I solved it was to put my ISP DNS in resolv.conf instead that of the router that ubuntu automaticaly gets.

so ...

$ sudo gedit /etc/resolv.conf

coment out the old nameserver by proceeding it with #

#nameserver [whatever number]

and then add your ISP dns. It appears to be working for me. I hope it works for you too.

 \\:D/  :grin: 

John[/QUOTE]
 You legend.

I've been searching all over for a fix to this problem.. plenty of people talking about it but the first to give a straight forward answer/solution :)

Thanks heaps.

Is this a permanent fix? No need to 'lock' the file or anything? (noob to linux sorry)

---

### Post by pompeyjohn on 2005-09-16
It should be a permanent fix! Although I have to set it evertime I boot up (because my router automatically sends out a different IP and I have not worked out how to stop it doing that yet!) 

Lucky I dont have to reboot ubuntu much really! Really happy to hear that it helped your setup.  :)

---

