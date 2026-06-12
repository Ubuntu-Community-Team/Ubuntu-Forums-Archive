---
title: "How-to create breezy web server"
date: 2005-10-18
forum: Server Platforms
---

### Post by flebber on 2005-10-18
I wanted to use breezy to set up a web server are there any good guides to setting up a web server but also maintaining it securely.

Any help greatly appreciated

PS will there shouldn't be too much difference between setting up and maintenace from an existing debian articles wiki's should there?

sorry i am just having trouble locating the breezy web server how-to....please remove

---

### Post by flebber on 2005-10-18
I still can't find the server how-to could someone post a link please .I have gone to the wiki but a search for web server turns up 0 results. Forgive me maybe its very obvious were the how to is but i can't see it maybe I am too tired could be my month old baby daughter . 

I would appreciate a pointer maybe the link could be posted in the sticky .

---

### Post by WW on 2005-10-18
It isn't a detailed how-to, but it might get you started:
   [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by flebber on 2005-10-19
Thanks for the reply. I need more info though so is it ok to use debian docs for ubuntu as there doesn't appear to be many ubuntu docs on this. For example this is the configuration how-to from the debian docs [http://www.debian.org/doc/manuals/network-administrator/ch-www.html]("http://www.debian.org/doc/manuals/network-administrator/ch-www.html")

---

### Post by OneSeventeen on 2005-10-19
I will be creating a breezy web server here at work.  (since nobody else, including debian, seems to support PHP5... I guess olmost 2 years with corporate sponsorship doesn't make a package "stable" just yet?)

Just post what you are looking to do here, and I'll see if I can figure it out and put it in a tutorial.

Here's what I'm doing:

Apache/PHP5/PostgreSQL/MySQL/Perl webserver.  (got to be well-rounded!)

this will have multiple subdomains, all within the same domain.  (meaning I'll have a.example.com, b.example.com, etc.  but not [www.example.com](www.example.com))

I will have a thawte SSL certificate for the primary subdomain.

I will have a single FTP user, hopefully using "secure FTP".

The MySQL and PostgreSQL databases will only be available when on the server, or on a specific computer with a static IP address.  (that way random people can't just start trying to log into my databases from a remote location)

And finally, it will have a very extensive and cool website with all sorts of PHP magic going on, shiny graphics, and tons of XHTML/CSS!

---

### Post by Randall311 on 2005-10-19
you're all way off... There is an excellent tutorial at  [http://www.howtoforge.com/book/print/59](http://www.howtoforge.com/book/print/59) on how to configure a server on Ubuntu.  ... Now, can somebody please tell me how to fix my dyndns headaches?  the details are here [http://ubuntuforums.org/showthread.php?t=77834](http://ubuntuforums.org/showthread.php?t=77834) your help is deeply appreciated.  The problem lies in my traceroute.  the hop after my ISP seems to be firewalled or something.  nothing I do is working. :???:

---

### Post by OneSeventeen on 2005-10-19
I'm not sure about the others in this thread, but I am looking for a good Ubuntu 5.10 Breezy Badger web server setup.

I would like to use the best software available that will be supported by Ubuntu.

There is no reason not to use PHP5, IMO, and since Breezy is the first release to incorporate this, there will be differences in the installation process.

I hope you find out the solution to your dydns issue, but I'm still going to be posting in here and hopefully making my own tutorial on a well rounded Breezy Web Server.  (thanks for the Hoary link though, that is a good starting point!)

---

### Post by Randall311 on 2005-10-19
Thanks. I hope the link helps you.  I think that except for PHP5, the install of a server should be realitvely the same on Breezy.  I think the Apache 2 installation of PHP modules would just be PHP5 instead of 4... but don't hold me to that. ;)  There is also a server specific installation for Breezy, comes with all the things you need.  here.  [http://ftp.litnet.lt/pub/ubuntu-cd/ubuntu-server/breezy/](http://ftp.litnet.lt/pub/ubuntu-cd/ubuntu-server/breezy/)  (this is a server only edition.. i.e. no desktop environment) so only for professional webmaster type people.

---

### Post by OneSeventeen on 2005-10-19
I just thought I'd mention that anyone interested in making something as serious as a server using any version of linux should do 3 things, in this order:

1. Download .iso via Bittorrent
2. Check MD5 sums!!!!
3. Burn to CD using slower-than-normal speeds

I forgot to check the MD5sum, then burned with high-speed, and thus lost 2 hours of my day.  (and for lazy, procrastinating yet impatient people like me, that's a lot!)

---

### Post by Randall311 on 2005-10-20
yikes that stinks.  I don't check the MD5 nearly as often as I should.  Esp with 600+ Mb files.  It always takes like 5 minutes just to hash it.  Of course that 5 minutes would save 2+ hours of bad installing.  ;)

---

### Post by flebber on 2005-10-20
What I basically wanted to acheive was intially just a development environment while I learn what I am doing a bit better. Ok I never have set up a web server before so I am starting right at the start, having been learning both html and python from online docs lately and will decide whether I move onto PHP or Perl6 (apparently parrotcode may integrate support for pytho & Perl use of CPAN). Sorry offtopic.

I am looking intiall at developing 2 websites 1 to host my partners home business which will kick off in about 6 months and mine which will be a raciing news and tipping site which will need to host a database of results and possibly forum. For my girlfriends I may also require merchant banking facilites and security, security security

If I have left important information out please tell me....

Ah just reading the how-to posted for hoary, I did a default install of breezy meaning I didn't create /usr /var etc. I need to do a clean install and begin again wouldn't I.

---

