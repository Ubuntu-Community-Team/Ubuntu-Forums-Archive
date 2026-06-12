---
title: "Request: PHP5"
date: 2005-04-23
forum: Ubuntu Backports
---

### Post by gbusse on 2005-04-23
Along with the Apache module and MySQL and MySQLi extensions. Thanks in advance... this would be one of the last things still keeping me from completely abandoning Windows.

Thanks,
Gord

---

### Post by Virtual DarKness on 2005-04-23
Hi, I had php5 on ArchLinux and that's one of the reason that made me use kubuntu..

But I think it would be nice to have PHP 5 also in ubuntu, but the user should be able to choose wich version to use (I think it's the same now with php3 and php4, right?).

bye,
Giovanni.

---

### Post by gbusse on 2005-04-25
I would just like to know why the Ubuntu developers have such a big problem with including PHP5 as an alternative installation possibly in Universe or something like that. I really don't see what the big deal is. It is not like we are asking them to add KDE to the main repository, oh wait a minute they already did that. I was looking in the current packages for breezy and I still don't see any sign of PHP5 being added?!?

Ok, just had to get that off my chest.

Thanks,
Gord

---

### Post by Virtual DarKness on 2005-05-04
Hi,
I found this one and it work fine both with php4 / php5:

[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)


bye,
Giovanni.

---

### Post by jdong on 2005-05-04
Current PHP5 packages available for Debian are of "highly experimental" quality, so I do not feel it's responsible to make them available to the general public.

PHP5 is very new, which means potentially many undiscovered bugs and security holes, so that's why it's not really picking up momentum for packaging.

Think of GCC 4.0, Reiser4, and other experimental stuff -- how quickly do they get adopted? Not very.

---

### Post by Virtual DarKness on 2005-05-04
Yes, I agree with jdong..

I also had problems with php5 and the mysql extension (was forced to use the mysqli extension) and so for now I see it as too much bleeding..

but if you really need it, xampp can be a good solution for ubuntu

bye,
Giovanni.

---

### Post by jdong on 2005-05-04
Remember -- the Backports project isn't meant to transform the stable Ubuntu release into a "BreakMyGentoo"-type bleeding edge release -- that's what Debian Experimental is for!

I do not like going newer than Breezy/Sid, because packages that haven't made it into Sid/Breezy are of a lower quality, and also because upgrading to Breezy will be a royal pain if backports aren't overridden properly (I have some better scripts for handling this situation in development)

---

### Post by gbusse on 2005-05-19
I love Ubuntu and am keeping it on my PC. I have to use PHP5 for my development work as the OO in PHP5 is so good I can't even think about going back to PHP4. So, I will be doing all of my PHP development on my Windows XP partition where I have PHP5 installed and running very stable. Haven't had a crash yet with some very complex code. As soon as Ubuntu has PHP5 available via apt-get I am sold. That is the only thing that is still keeping me from completely getting rid of my Windows partition.

Thanks anyways...
Gord

---

### Post by Mirzabah on 2005-05-20
[QUOTE=jdong]PHP5 is very new, which means potentially many undiscovered bugs and security holes, so that's why it's not really picking up momentum for packaging.[/QUOTE]I think it's about time people got over their PHP5 phobia. I've been using for the past few months on a very high traffic commercial site. Predictably there were some initial problems in 5.0.0 and 5.0.1, but 5.0.4 is very stable.

---

### Post by UzLA on 2005-05-24
[QUOTE=gbusse]Along with the Apache module and MySQL and MySQLi extensions. Thanks in advance... this would be one of the last things still keeping me from completely abandoning Windows.

Thanks,
Gord[/QUOTE]

Why you just not compile PHP5 in the configuration your want??? Why you are waying for apt-get  stuff???  ](*,) Just give me ANY reason of haveing PHP5 via apt-get agaist of normal compiling?

---

### Post by THEspacemonkey on 2005-06-08
[QUOTE=UzLA]Why you just not compile PHP5 in the configuration your want??? Why you are waying for apt-get  stuff???  ](*,) Just give me ANY reason of haveing PHP5 via apt-get agaist of normal compiling?[/QUOTE]

Sure - when 5.0.5 comes out, then 5.0.6, then 5.0.7...

I mean, if we wanted to hang out and compile all the freaking time, we'd be using gentoo:p

I do understand though the merits of keeping 'experimental' apps out of the main distribution tree. What I do not understand is the reluctance to package 5.0.4 as 'stable'. Especially when I see sites that get almost 8 million page views daily on only one webserver and one database server, with no stability issues whatsoever.

IMHO 5.0.4 is most definitely 'stable', and am wondering if it is really the package that makes it 'unstable'? I found the PHP5 packages at debian, and will be testing them out on my local development server to see if there are any issues.

Manual installation of PHP is a real hassle, so I can imagine that packaging it up is no less an easy task! Thanks to the people that put all that effort into making the packages, this is definitely not meant as criticism but just trying to understand why things are the way they are;)

---

### Post by gbusse on 2005-06-08
[QUOTE=UzLA]Why you just not compile PHP5 in the configuration your want??? Why you are waying for apt-get  stuff???  ](*,) Just give me ANY reason of haveing PHP5 via apt-get agaist of normal compiling?[/QUOTE]

Because it is the UBUNTU/DEBIAN way... apt-get makes installation and upgrades a breeze!!!! Like SpaceMonkey says, if I wanted to compile all day long I would be using Gentoo (which I have successfully installed BTW) but I have much better things to be doing with my time!!!

---

