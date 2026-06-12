---
title: "Firefox 2 on Ubuntu6.06.1LTS?"
date: 2007-06-06
forum: Ubuntuzilla
---

### Post by bazzer on 2007-06-06
Hi there
I've got a bunch of computers running Dapper LTS that I want to have FF2 installed as a default. 

A little background first: I chose the LTS version of Ubuntu to make sure that I'd be getting the security updates until 2009. As a result, I now have remastered the install disc and run a script to install a minimal system (think Kiosk environment....). It's fairly key to the project to have the latest version of FF installed all the time, but I have to use my remastered disc to 'build' the computers...

So, my system is installed by a script but the latest version of FF int eh repos for Dapper is 1.5.x and I want 2.0 at least. I understand there is a script here to update the installed version, but can I ask how I can install FF2 fresh from the beginning, to use in place of 'apt-get install firefox' like I am doing at the moment. Ideally I'd like some kind soul to give the script lines to do so. Please!

Cheers

---

### Post by nanotube on 2007-06-06
> **bazzer said:**
> Hi there
I've got a bunch of computers running Dapper LTS that I want to have FF2 installed as a default. 

A little background first: I chose the LTS version of Ubuntu to make sure that I'd be getting the security updates until 2009. As a result, I now have remastered the install disc and run a script to install a minimal system (think Kiosk environment....). It's fairly key to the project to have the latest version of FF installed all the time, but I have to use my remastered disc to 'build' the computers...

So, my system is installed by a script but the latest version of FF int eh repos for Dapper is 1.5.x and I want 2.0 at least. I understand there is a script here to update the installed version, but can I ask how I can install FF2 fresh from the beginning, to use in place of 'apt-get install firefox' like I am doing at the moment. Ideally I'd like some kind soul to give the script lines to do so. Please!

Cheers

well, you'd put the ubuntuzilla script into your remastered disk, and run it along with the other stuff you are doing. you might replace your "apt-get install firefox" with "python ubuntuzilla.py -p firefox -a install" 
if you want it to run non-interactively, you'd probably have to modify the script so as to make it install without waiting for user interaction (unless you are ok with that)... currently the "unattended" mode is not implemented in ubuntuzilla.
also note that this script installs ff2 alongside the repositories version, so both versions are available, but ff2 is the default (in fact, ubuntuzilla does an "apt-get install firefox" in the process). 

i hope that helps? feel free to tell more about exactly what you are trying to do and stuff... i've never done a remastered install disk, so don't know the details of how it works; i hope i'm not way off base on what you can do with it. :)

---

### Post by bazzer on 2007-06-06
Ok, I'll have a go at adding it and report back. Great help, thanks very much!

---

### Post by nanotube on 2007-06-06
> **bazzer said:**
> Ok, I'll have a go at adding it and report back. Great help, thanks very much!

cool, i'm looking forward to finding out how it all comes out! :)

---

### Post by nanotube on 2007-06-08
i have implemented "unattended" mode in ubuntuzilla.
you may wish to take a look at it - it should be very helpful for automated installation.
you can get the latest version out of CVS:
[http://pykeylogger.cvs.sourceforge.net/pykeylogger/ubuntuzilla/](http://pykeylogger.cvs.sourceforge.net/pykeylogger/ubuntuzilla/) (since it's just one file, it's easiest to just get it through the viewcvs web interface).
see ```
ubuntuzilla.py -h
``` for the options, post here if you have questions. :)

---

### Post by bazzer on 2007-06-13
Well... I found some useful stuff in there about how to install FF2.0 properly over the top of the 'official' 1.5 install. I haven't actually used the script in my automated install, as it's all so simple it's not really required. But I have to say thanks very much nano, you saved me a lot of time searching....!;)

---

### Post by nanotube on 2007-06-13
> **bazzer said:**
> Well... I found some useful stuff in there about how to install FF2.0 properly over the top of the 'official' 1.5 install. I haven't actually used the script in my automated install, as it's all so simple it's not really required. But I have to say thanks very much nano, you saved me a lot of time searching....!;)

cool, have fun. :)

---

