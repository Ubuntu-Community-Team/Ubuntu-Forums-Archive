---
title: "setting up a mini deb pool on my server"
date: 2007-12-19
forum: Server Platforms
---

### Post by rbprogrammer on 2007-12-19
i have a server at home, but when i am away at college i use it to store files and programs and whatever i want it to...

my question is, how do i set it up so that i can store my deb's on it, then be able to search through the programs in synaptic.  i'm sure its easy, but i dont know *exactly* how to set it up.

my thoughts are that its probably deb files saved on a http server (i have that running).  the files are probably sorted in some way for organization but i dont know how to do that do so that synaptic works correctly.  then in synaptic i would add a repositoy (that would be my server) under the "Third party software".  but adding that line into the synaptic file, i have no idea what it would be.  since the archives are sorted by distribution (ie, gutsy, etc..)??  and then when i start to finally have the time to make my own software, how to i make it so that i would have the binaries and the source code downloadable??

from my understanding, i think that is how it kind of works.. but like i said i dont know how to set this whole thing up.. any help is appreciated.

---

### Post by peitschie on 2007-12-19
Hi,

I had this issue just a little while ago.  Since then I have found a few examples that might be helpful.  

Here are some useful links that helped me: 
[http://www.debian.org/doc/manuals/repository-howto/repository-howto]("http://www.debian.org/doc/manuals/repository-howto/repository-howto")
[http://wiki.debian.org/HowToSetupADebianRepository#head-d0e1d14efdb65af19f15b52e95e96c38ed14d3f8]("http://wiki.debian.org/HowToSetupADebianRepository#head-d0e1d14efdb65af19f15b52e95e96c38ed14d3f8")
[http://ianlawrence.info/random-stuff/setting-up-a-personal-debian-repository](http://ianlawrence.info/random-stuff/setting-up-a-personal-debian-repository)

---

### Post by rbprogrammer on 2007-12-20
thanks, i will work on it within the next few days..

---

### Post by koenn on 2007-12-20
the quick and dirty approach is

- have a web server with a directory where all your .deb files are
- add a reference to it in the client apt sources list,
something like " deb [http://myserver/my](http://myserver/my) packages ./" the ./ is important.
- create a Packages.gz file. Install dpkg-scanpackages on the server, it can create packages.gz for you. you may need also an 'override' file, which is just a list of packages in a text file called 'override'
you can also make it by hand/script, based on the control files of your packages.

it's a "dirty" approach in that it doesn't follow the customary file and directory hierarchy of 'real' debian/ubuntu repo's, but is quick to set up, and it works.
If you want it to resemble official repo's however, the links in the previous post will help you get started.

---

### Post by rbprogrammer on 2008-01-07
question.... what if i have a deb package that is a newer version of a program?  will synaptic just display the most recent version??

an example program might be deluge.  i think i installed a newer version from the website than what is already in the default repositories.  i will be using the server for debs that i create and debs that i find to work on my computer that i like...
:guitar:

---

### Post by peitschie on 2008-01-07
Yes.  Synaptics will by default only install and display the most recent version.  You can force a specific version to be installed by right-clicking on the package in Synaptics

---

