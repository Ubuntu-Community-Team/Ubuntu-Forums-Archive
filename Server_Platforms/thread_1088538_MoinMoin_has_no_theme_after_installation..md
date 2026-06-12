---
title: "MoinMoin has no theme after installation."
date: 2009-03-06
forum: Server Platforms
---

### Post by wilager on 2009-03-06
Hello,

This is my first post in this forum (although I am an ubuntu user since 7.04).

I have a problem with moinmoin installation. I installed it in 8.10 server (and desktop) in many different machines following exactly the instructions provided in the official ubuntu documentation ([here]("https://help.ubuntu.com/8.10/serverguide/C/moinmoin.html")).

The problem is that when I direct firefox to

> [http://localhost/mywiki](http://localhost/mywiki)

I see the wiki but it has no theme. It's printed completely unformatted with bullets and numbers.

It seems others encountered the same problem ([Cannot get themes to work]("http://moinmoin.wikiwikiweb.de/MoinMoinQuestions/Installing#head-280e8976bdb06e5a83b898785dd93a963856a7fe")) but their suggestions are already met in the ubuntu guide (alias /wiki "/usr/share/moin/htdocs").

I also tested this:

> You can try this without moin by accessing [http://server/wiki/modern/css/screen.css](http://server/wiki/modern/css/screen.css) (it should show some css source code in that case). -- ThomasWaldmann 2006-01-19 08:34:00 

and I see CSS code.

What could be going wrong?

Thank you for your time,
wilager

---

### Post by colonhyphenp on 2009-03-13
Hi,

I was having the same problem, but found a workaround:

Apparently, instead of looking for your css files in /wiki, MoinMoin looks in /moin_staticXYZ, where XYZ is your MoinMoin version.  For me, this is /moin_static171, since I'm using version 1.7.1 of MoinMoin.

So, just change your apache config file line:

> alias /wiki "/usr/share/moin/htdocs"

To:

> alias /moin_static171 "/usr/share/moin/htdocs"

You can check your moin version by running:

> $ moin --version

---

### Post by wilager on 2009-03-18
Thank you for your help.

It worked!

---

### Post by neosar on 2009-09-24
I too am having this issue.  My wiki page comes up and it is as if there is no CSS being seen by the script, everything is 100% unformatted.  It appears as though the instructions on the Server Guide have been updated to reflect the suggestion above, and I have verified that my alias points correctly, but I still have the issue.

---

### Post by neosar on 2009-09-24
Nevermind, it appears that the install is currently version 1.8.2, and the server guide is for version 1.8.1 which is why the issue was happening to me too.  For reference running moinmoin --version is really important

---

### Post by dmberry4 on 2010-09-15
THANK YOU!

I installed moinmoin 1.9.2, but could get no theme working.

My /etc/apache2/apache2.conf had 

> 
alias /moin_static160 "/usr/share/moin/htdocs" 

which I changed to 

> 
alias /moin_static192 "/usr/share/moin/htdocs" 

And now I have THEMES!

---

