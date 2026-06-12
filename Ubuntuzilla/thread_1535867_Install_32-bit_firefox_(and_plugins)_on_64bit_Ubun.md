---
title: "Install 32-bit firefox (and plugins) on 64bit Ubuntu (Intrepid)"
date: 2010-07-21
forum: Ubuntuzilla
---

### Post by coolguy4 on 2010-07-21
Hello,

I want to use some software called webex, which runs in the java plugin, but it only works with 32-bit java for some reason.

My plan is to install 32-bit firefox and 32-bit java and hopefully it will work.

I have looked on Google and IRC for some detailed instructions about this but I couldn't find anything that gave me confidence that it would actually work.

I downloaded firefox-mozilla-build_3.6.7-0ubuntu1_i386.deb from the ubuntuzilla repositories and tried to install it with gdebi but it complained that it was the wrong architecture.

I am willing to install firefox from source if someone can promise me that it will actually work.

Please help me if you can, I am at my wit's end.

Thank you.

---

### Post by nanotube on 2010-07-21
download firefox manually from mozilla.com, unzip, run.

for 32bit java, install the relevant ia32 packages of java from the repos.

there are some instructions on the old ubuntuzilla site:
[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BThunderbird.2C_Firefox.5D_For_64-bit_Ubuntu_users](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BThunderbird.2C_Firefox.5D_For_64-bit_Ubuntu_users)

also, it's probably a good idea not to share your profile between the mozilla 32bit build and the 64bit ubuntu build, so make sure to start a new profile.

---

### Post by coolguy4 on 2010-07-22
Thanks for the reply nanotube.

I downloaded firefox from the mozilla website, extracted it and tried to run it from a sub-dir in my home folder. This is the message I received:

./firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

but libgtk-x11-2.0.so.0 is in /usr/lib ?

Do I need to install 32-bit libraries for this to work?

---

### Post by nanotube on 2010-07-22
Hi,
yes - that link i posted earlier also tells you about the ia32libs packages you need to install...

---

### Post by coolguy4 on 2010-07-24
Oh thanks,


I did sudo aptitude install ia32-libs , and this was the result:

Unpacking ia32-libs (from .../ia32-libs_2.2ubuntu18.1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.2ubuntu18.1_amd64.deb (--unpack):
 unable to create `./usr/lib32/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.2ubuntu18.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas?

---

### Post by nanotube on 2010-07-24
no idea... that sounds like a good question to ask in the general support forum...

---

### Post by coolguy4 on 2010-07-25
Ok, thanks for your help nanotube.

---

