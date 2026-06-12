---
title: "libapache2-mod-php5 ?"
date: 2005-10-12
forum: Server Platforms
---

### Post by Aven on 2005-10-12
Alright, I have no idea where it is but can anyone please tell me? I've looked and searched, etc. etc. SO hard to install PHP on ubuntu.

but anyway, does anyone know where I get the libapache2-mod-php5 file so that I can load it as module in apache?


Thanks

---

### Post by Aven on 2005-10-13
eh.. no one knows? ... =\

---

### Post by user-jon on 2005-10-13
Hi, don't take my word for it but...

don't you just run the synaptic package manager (or aptitude
or apt-get from the command line) and install
   libapache2-mod-php5

(that's about it, unless there are any additional instructions
 in /usr/share/doc/libapache2-mod-php5 )

??
enjoy your web developing :)

---

### Post by Aven on 2005-10-13
says "package not found" :(

---

### Post by user-jon on 2005-10-14
hi!
i just went to  [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  
(a very useful tool to find packages)
and searched for   "mod-php"  in  "all"  ubuntu versions
(i take it you understand about the Main and Universe repositries etc..)
------
libapache2-mod-php4
    * warty: 4.3.8-3ubuntu7.12    (main)
    * hoary: 4.3.10-10ubuntu4.1   (main)
    * breezy: 4.4.0-3              (universe)

libapache2-mod-php5
    * breezy: 5.0.5-2ubuntu1   (main)
------
so the "ubuntu plan" appears to be either
 - stick with 'ubuntu hoary hedgehog' and use  PHP4
 - or upgrade to 'ubuntu breezy badger'  if you *need*  PHP5

(there does seem to be a  "hoary backports"  repositry, which
 i thought was for making newer stuff available for the older
 platform? but i have no experience of that..
 sometimes third parties make 'ubuntu packages' available
 but i don't think that is the "recommended" way to go...
 i just like to keep everything as upgraded as possible)

hope that helps -
ps.never quit on ubuntu, it just keeps getting better and has a great
roadmap for the future! 
get past the initial quirks and you'll love it :)

have fun with the badger!

---

### Post by Aven on 2005-10-14
w00t. Ok, it says that I have that package, however..

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

is what I keep getting.. I also did it as root.

so, what could be the problem?

---

### Post by user-jon on 2005-10-14
hi,
a message like that means one of two things is going on:

1) you have more than one program (or more than one copy of the same program) running and trying to perform the same exclusive action at the same time -- the one that got there first created a "lock file" to stop the second one from treading on its toes.

2) a previous invokation of such a program crashed in some way and although it is no longer running and performing the exclusive action - it has left behind a "stale lock file"
----

#1 is more likely:
-- so make sure you are not running any of  synaptic/kynaptic/adept/aptitude/apt-get  on any screens/terminals/command-prompts etc. then try again.

failing that:
 -- either remove the lock file by running the command
     sudo rm /var/lib/dpkg/lock
 -- or maybe try the "lazy man's fix" and reboot because this might clear out all stale lock files

good luck -- and have fun becoming an ubuntu guru :)

---

### Post by SuperMike on 2005-11-25
I think I'm seeing a pattern of an undocumented Ubuntu Breezy bug in PHP5 and PHP4 installs with the libapache2-mod-php4 or libapache2-mod-php5. If you uninstall and reinstall multiple times, you'll find that it just sort of works if you repeat the process several times. I had to repeat the same exact process like 5 times on my PC before it just worked. And when you uninstall PHP, it will warn you that libapache2-mod-php(x) didn't get installed in the first place, so it can't remove it.

My running theory here is that either there's a bug in the Canonical web farm with some of the mirror servers we're hitting. I cannot figure out any other reason why the libapache2-mod-php(x) would install one time and not another.

And if you do a search on ubuntuforums.org, you'll find that a lot of people are having this issue. The net effect of this is that even though you have installed Apache2, PHP(x), and libapache2-mod-php(x), and have cleared your Firefox cache, you find that Firefox still asks you what to do with the PHP file, instead of Apache2 pre-processing it at the server. This is because the libapache2-mod-php(x) is failing to be compiled and inserted properly into the Apache2 framework -- even though you can clearly see the various .conf files are properly updated and the libphp(x).so file is in the proper place.

I finally got my PHP4 to work in Breezy. A couple days ago, I also had my PHP5 working too. So it *can* be done. Just keep playing with Synaptic and the install, trying different ways to install it, or install just what you need first and add other extra PHP items you need as you go. You'll find if you keep fighting with it for like 4 hours, it finally just *works*, somehow.

I wish there was a way I could easily report this as a bug to be checked. If you all know where to post this, let me know. The bug can be easily reproduced. Just upgrade from Hoary (with a loaded PHP4 install) to Breezy, and then uninstall completely the PHP4 and/or PHP5. Then, reboot. Then, try to install PHP4 again with Universe option enabled. Or, for that matter, try on a separate PC to install PHP5 again. Both PHP4 and PHP5 will intermittently have the same issue of not compiling the libapache2-mod-php(x) file properly.

I'd also like to know how I can become a tester for Canonical's PHP installs. It sounds like they didn't test this very well and could stand to have a developer help them.

---

