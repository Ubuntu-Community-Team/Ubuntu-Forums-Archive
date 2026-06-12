---
title: "Linux Guide"
date: 2007-06-09
forum: The Cafe
---

### Post by nirelan on 2007-06-09
Hey guys whats up? Im new to Linux and I was wondering if someone out there would like to show me around a bit and answer some questions, My name is nickirelanon Yahoo. Send me a message if you want to help.
Thanks
Nick

---

### Post by orange2k on 2007-06-09
Why not?
Go right ahead and ask your questions...
But sometimes youre not going to like the answers...

---

### Post by nirelan on 2007-06-09
thanks for the reply man, i was hoping i could find someone on yahoo so they could kinda walk me through the stuff that drives people crazy like installing programs and stuff
thanks 
Nick

---

### Post by DJ Wings on 2007-06-09
How can installing programs drive you crazy? Just fire up Synaptic and let 'er rip!
Don't use Yahoo for questions. Ask them here so other people can learn from you.

---

### Post by nirelan on 2007-06-09
well then can someone give me a walk through on installing apache

---

### Post by orange2k on 2007-06-09
there is nothing easier than installing stuff on your computer...
For instance, go to "Add/remove programs", add Amarok, and then click on playlists, choose "cool streams" and doubleclick SLAY radio...
Thats what I`m listening right now... 

cool, hah?

OK you probably have to install the proper mp3 codecs to be able to do that, but how hard is THAT?

---

### Post by johnc4510 on 2007-06-09
nirelan, here are some guides to look over:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

[http://easylinux.info/wiki/Ubuntu_Edgy](http://easylinux.info/wiki/Ubuntu_Edgy)

Hope these help you :)

---

### Post by orange2k on 2007-06-09
Apache?
No problem, ask someone else, I don`t use it...

What do you need it for, anyways?

It`s not like you`re gonna maintain a server, are you? Kidding right?

---

### Post by nirelan on 2007-06-09
I program on Windows and Id like to give Linux a try. I want to get used to Apache and some of the compilers on Linux.

---

### Post by nirelan on 2007-06-09
Ive seen alot of those how to install guides, but there are so many possibilities that it makes them hard to use. Heres what I got while trying to install apache

> 
nirelan@nirelan-laptop:~$ cd '/home/nirelan/Desktop/httpd-2.2.4' 
nirelan@nirelan-laptop:~/Desktop/httpd-2.2.4$ ./configure
checking for chosen layout... Apache
checking for working mkdir -p... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1

Configuring Apache Portable Runtime library ...

checking for APR... reconfig
configuring package in srclib/apr now
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
Configuring APR library
Platform: i686-pc-linux-gnulibc1
checking for working mkdir -p... yes
APR Version: 1.2.8
checking for chosen layout... apr
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr


---

### Post by macogw on 2007-06-09
> **nirelan said:**
> Ive seen alot of those how to install guides, but there are so many possibilities that it makes them hard to use. Heres what I got while trying to install apache

Stop compiling!  This isn't Gentoo.  This is EASY Linux.

Go to System > Administration > Synaptic Package Manager.  Click the checkmark for Apache.  Click Apply.  Put in your password.  Wait.


The issue you have there, by the way, is that Ubuntu doesn't come with development tools by default since it's mainly aimed at "normal use" things, and most people don't compile their programs or do development.  To get the compilers and stuff,
```
sudo aptitude install build-essential
```
but you shouldn't really need to do that if you just use Synaptic and get the .deb (like Windows .msi) files from the repositories.

---

### Post by ixus_123 on 2007-06-10
Getting support on Yahoo / an IM client is all well & good but it would be much better to do it via the forums.

Present any problems you have in this thread - more people will be able to reply and more importantly - more people will be able to benefit from any solutions to common problems. That's the beauty of the forum - once it goes to IM then others can't benefit from any solutions now or in teh future with the search facility :)

---

