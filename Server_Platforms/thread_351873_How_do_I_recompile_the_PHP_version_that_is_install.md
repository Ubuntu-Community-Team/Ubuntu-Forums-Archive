---
title: "How do I recompile the PHP version that is installed with Ubuntu 6.10 server edition?"
date: 2007-02-02
forum: Server Platforms
---

### Post by Keith_S on 2007-02-02
I'm trying to get an extension for our Mediawiki to work (PageProtectionPlus), and it requires that we install GMP for best performance. It also requires that we install PHP by using the --with-gmp option. However, it appears that it has BCMath installed instead.

I'm hoping that I can recompile PHP to add that option without losing any other installations (although getting rid of BCMath would be ok), but I'm at a bit of a loss as to how to do it. The other requirements have packages specifically for PHP (such as mcrypt) that can be installed through Synaptic. I found a PHP-GMP debian installation file through Google and a RPM for another distro (through Alien), but neither seemed to work.

I've had a very little bit of compiling experience, but not very much at all. What would be the best way recompile the version of PHP that came installed with 6.10 to get GMP working and recognized by it?

Thanks!

---

### Post by Keith_S on 2007-02-03
Quick bump!

---

### Post by lamego on 2007-02-03
You need to apply a procedure similar to this:
[http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/](http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/)

---

### Post by Keith_S on 2007-02-06
Thanks. I've tried downloading PHP 5.2 from their site, and doing ./configure, make and make install, but when I check my Apache, it still doesn't list the GMP support. It's also still listed as 5.16, which makes me think that I didn't do something correctly.

What I'm really curious is how do other php extensions (like php5-mcrypt) work so that they don't have to reinstall php entirely? I tried reinstalling that extension and tried to watch the output, but it didn't give me any clues as to how I could do this manually.

---

### Post by Brunellus on 2007-02-06
I'm moving this to server talk.

---

### Post by Ztech72 on 2007-02-07
I know that this is not specific to your issue, but I had a similar problem. I needed to recompile PHP with cURL support.

After much research what worked was very simple. Try this.

sudo apt-get install php5-gmp

Then restart Apache, run a phpinfo page and see if it worked. 

I was taking the same approach you were, this worked for me. Hopefully it will help you out.

Z

---

### Post by Keith_S on 2007-02-08
Thanks, but when I tried that, it couldn't find the package.

---

### Post by Keith_S on 2007-04-20
Any new answers for Feisty? I'd still like to add GMP support for PHP, and it doesn't appear that Feisty has php5-gmp.

Thanks!

---

### Post by Keith_S on 2007-08-16
I finally found a quick and easy tutorial at [http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606]("http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606") that showed me how to recompile it.[/URL] It's using MSSQL as an example, but just in case that site ever goes down, here's a quick recap. All credit goes to that site, I'm just rewording it for GMP here.

Steps to enter at the command line:
[B]
1. apt-get install build-essential debhelper[/B]

(More tools might be needed depending on what you already have installed, but you will tend to get warnings about what is missing)

Then, download the PHP sources:

**2. apt-get source php5**

My version is 5.1.6, but yours may be different.

Get all the dependencies for building PHP:

**3. apt-get build-dep php5**

Change into the debian build directory for PHP:

**4. cd php5-5.1.6/debian**

Let's  edit the _modulelist_ file. 

**5. gedit modulelist**

Insert a line below the one that says

gd GD

with the contents:

```
gmp GMP
```

Next, edit the _rules_ file. Either open it from gedit directly or use:

**6. gedit rules**

Look for the line that says:

--with-curl=shared,/usr \

Open a line below this with the contents:

```
--with-gmp=shared,/usr/local \
```

Make sure not to forget the backslash on the end. Also, GMP installed itself into /usr/local on my machine. Your location may be different. 

Now, we edit the _control _file. Again, either use the gedit GUI to open the file or type:
[B]
7.gedit control[/B]

Add this to the end of the file:

```
[I]Package: php5-gmp
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}, ${php:Depends}, php5-common (= ${Source-Version})
Description:GMP module for php5
 This package provides a module for GMP to be used with PHP5.
 .
 PHP5 is an HTML-embedded scripting language. Much of its syntax is borrowed
 from C, Java and Perl with a couple of unique PHP-specific features thrown
 in. The goal of the language is to allow web developers to write
 dynamically generated pages quickly.[/I]
```

Make sure that you keep all that text as one big block with no extra lines between it. It's ok to have an extra line after it, but not between it. Just see how the other entries are entered and go from there.

Move up a directory.

**8. cd ..**

Now, run:

**9. sudo dpkg-buildpackage**

This will do the whole configure/compile for PHP and create debs in the parent directory. This does take awhile, though. When this process is done, move up to the parent directory:
[B]
10. cd ..[/B]

And, you will see all of the PHP debs, including the new php5-gmp_[version].deb

Run a dpkg -i on the ones you need (I just used the gmp one):
[B]
11.dpkg -i php5-gmp_5.1.6-1ubuntu2.6_i386.deb[/B]

It may give an error about the dependencies. You can run the Synaptic Package manager and choose "Fix Broken Packages", and it should update them. You should be all set. If any of the commands don't work or say permission denied, try to sudo them.

Voila! You now have an Ubuntu PHP5-GMP package!

---

### Post by Juan_VCS on 2007-09-11
That didn't work in feisty :(

---

### Post by Keith_S on 2007-09-12
One thing to try if GMP support doesn't pop up is to try installing libgmp as well. I think I tried this on a recent install of 7.04 and following these instructions, I couldn't get PHP to recognize that I had compiled it myself. I tried everything, and then when I installed libgmp (and I believe two other libgmp related items such as libgmp-dev), I restarted Apache. There it was!

---

### Post by scragar on 2008-03-01
I followed all these steps(and ran "apt-get build-dep php5" twice, before and after the edits since it wouldn't let me build the .deb without running it again), and after installing the package it still doesn't work(I installed both libgmp3-dev and libgmp3c2).

I'm running Gutsy on a 64 bit machine if that's of any use(package was called "php5-gmp_5.2.3-1ubuntu6.3_i386.deb" , just though more info would help).

---

