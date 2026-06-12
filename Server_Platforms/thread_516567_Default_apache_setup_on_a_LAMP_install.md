---
title: "Default apache setup on a LAMP install"
date: 2007-08-03
forum: Server Platforms
---

### Post by Viruk on 2007-08-03
Hi, 

I am trying to solve a problem with cacti (see [http://ubuntuforums.org/showthread.php?t=515833](http://ubuntuforums.org/showthread.php?t=515833)) as it is not detecting the php binary. 

I don't know enough about the default installation when choosing a LAMP install to know where to direct the cacti setup. It is looking for /usr/bin/php but the binary doesn't exist there.

After some reading round I have found some information about php being installed as a CGI binary or as an apache module. 
Are both of these options included on a default LAMP install from Ubuntu server 6.06.1 ? 

I know that php is on the system and working as I get a result from a test page with the code ```
<? phpinfo();?>
``` 
The displayed page states that I have PHP version 5.1.2

Can anyone tell me where the binary is located or if it is something that I have to setup/install seperately?

Let me know if you need any more information.

---

### Post by zanglang on 2007-08-03
Hmm, I don't remember having much trouble when installing Cacti. Maybe it's having trouble following symlinks? Try changing the php path to /usr/bin/php5 (or /usr/bin/php5-cgi).

---

### Post by Viruk on 2007-08-03
There are no binaries (or sym links) for php, php5 or php5-cgi

Should any of those be there with a default LAMP install?

Did you install cacti from a package btw?

---

### Post by zanglang on 2007-08-03
Ah, you're right, the PHP binaries may not be installed. Try manually installing then, e.g
> sudo aptitude install php5

And yeah, I installed it from the 'cacti' package on the universe repository.

---

### Post by Viruk on 2007-08-03
Are the binaries just left out of the LAMP installation? Or has something gone wrong here?

I'll try installing the package on Monday morning - I have to alarm the building here now and wont be back in till after the weekend. 

I might give it a try on my test box at home if I get chance over the weekend...

Thanks for your help :)

---

### Post by zanglang on 2007-08-03
Yes, LAMP probably only comes with the PHP module for Apache (libapache-mod-php5 or 4) and common PHP files (php5-common), but not php5-cli, which packages the executable binaries. Wish I could confirm for you, but I'm on Gutsy at the moment, so just checking this off [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by Viruk on 2007-08-06
Thanks for your help with this one, I'm going to give it a try now :)

---

### Post by Viruk on 2007-08-09
I just thought I'd update this one - I got it all sorted thanks to your advice - thanks again for the help :)

---

