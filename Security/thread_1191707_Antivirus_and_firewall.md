---
title: "Antivirus and firewall"
date: 2009-06-19
forum: Security
---

### Post by John M2009 on 2009-06-19
I have been hunting for a suitable firewall for my version of Ubuntu,  but cant find onem  even after following links from the sticky post up top,  can someone point me in the right direction please? I (think) I need some kind of antivirus software,  I used AVG free edition for windows.  I dont knowe how prone to viruses Ubuntu is,  im guessing not quite as prone as windows,  but I want full protection anyway.   

Finally, I know this is not the right forum for it,  but it will save me making two seperate posts.  I cant get any sound.  Since I lost the driver disc for my mother board, I have been using a USB headset,  which does not seem to work with Ubuntu for some reason.  Im pretty sure its not a problem with the USB ports,  as Ubuntu can see my pen drive and my USB mouse fine.

I liked windows when everything would just work,  well,  most of the time anyway lol

---

### Post by Tobywuk on 2009-06-19
**Firewall**
Ubuntu comes with a great filewall built in - called 'IPTables' but it can be quite complicated to set up. it is basically a file with a list of rules which is essentially what a firewall is. There are GUI frontends available for it. for more info on iptables [See here](https://help.ubuntu.com/community/IptablesHowTo)

One thing to note is that ubuntu comes with no services listing on ports seen by the outside by default which means there are no places for a potential hacker to get in. In this case a firewall is not needed because there is nothing to protect.  You dont need to worrie about installing a firewall like you would on windows.

Im also guessing but you are probably behind a router which uses NAT (network address translation). As long as you have no ports redirected or you are in a DMZ then you are protected from outside traffic by this.

**Viruses**
Ubuntu does not suffer from viruses like windows does. I was reading a list of viruses for ubuntu the other day and it came to a total of around 15, not much against the hundreds/thousands for windows. [Here](http://www.gnu.org/fun/jokes/evilmalware.html) is a great little article showing how you may get a virus on ubuntu. it-s a bit of a joke as it shows how much harder it is for a linux system to become infected.

With ubuntu you are much more secure than with windows. The most important thing is to be smart. do not download and run programs/scripts from people or sources you do not trust. Keep the programs and services you have installed up to date so they are patched and protected against exploits.


As for sound, thats a different matter. your probably best of creating a new thread for that :)

---

### Post by lovinglinux on 2009-06-19
I strongly recommend reading the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial, so you can understand which are the real threats.

The recommended firewall manager is UFW, which is installed by default. To install the graphical interface [click here](apt:gufw) [apt-get]. Keep in mind that once you configure the firewall manager, you don't have to keep it running. The real firewall (iptables) runs in the background all the time. Additionally, if you have a router, then you probably don't need a firewall. 

You don't need an anti-virus to protect the Ubuntu machine, but if you want to scan Windows partitions or protect other Windows machine on your network, then I recommend [BitDefender](https://help.ubuntu.com/community/BitDefender).

---

### Post by pietjanjaap on 2009-06-19
Firewall is not needed, but if you have a network at home, then you can block more things, like sharing files or ssh tunnel, then you can make this more secure.
Firewall is installed bij default on ubuntu, but you need a gui(grafical interface) for it. Try "guarddog". Wenn you install guarddog then everything is blocked, also firefox, so everything you need to give permission.


Antivirus is not needed for linux, but for windows software you download you need it. Clamav is in ubuntu, is a open source scanner. Install clamav and clamtk(is a gui).
Avg is also free for ubuntu, i think that avg is better, but it is not free software(you can use it for free).
To start avg " avgscan -p -b -a -b \*" in the terminal, to scan everthing. "avgupdate" in terminal to update.

---

### Post by dvn7035 on 2009-06-19
If you want you can get avast for Linux workstation although it only protects against windows malware.

---

### Post by boof1988 on 2009-06-19
> **dvn7035 said:**
> If you want you can get avast for Linux workstation although it only protects against windows malware.

Is this true only for [Avast](http://www.avast.com/eng/avast_4_home.html)?  Or is it true in general (for all [anti-virus software](http://en.wikipedia.org/wiki/List_of_antivirus_software))?

There are many people saying this but where is the data to back it up?  I have looked some and haven't found it yet.  I would really like to know the answer cause I'd like to be able to give the appropriate answer.

The following quote (regarding [Clam AntiVirus](http://www.clamav.net/)) is from... [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses#Cross-platform_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses#Cross-platform_viruses)...

> Because they are predominately used on mail servers which may send mail to computers running other operating systems, Linux virus scanners generally use definitions for, and scan for, all known viruses for all computer platforms. For example the open source ClamAV "Detects ... viruses, worms and trojans, including Microsoft Office macro viruses, mobile malware, and other threats."[12]

...which includes a quote from...

[http://www.clamav.net/doc/latest/clamdoc.pdf](http://www.clamav.net/doc/latest/clamdoc.pdf)

So if anyone can either clarify this or give a link to a good/clear answer, I (among others) would appreciate the help in finding the answer.

---

### Post by rookcifer on 2009-06-19
> **boof1988 said:**
> Is this true only for [Avast](http://www.avast.com/eng/avast_4_home.html)?  Or is it true in general (for all [anti-virus software](http://en.wikipedia.org/wiki/List_of_antivirus_software))?

There are many people saying this but where is the data to back it up?  I have looked some and haven't found it yet.  I would really like to know the answer cause I'd like to be able to give the appropriate answer.

Sure.  Here are some links for you to read so that you can "see the data" and understand why AV on Linux is a complete waste of time.

[http://linuxmafia.com/~rick/faq/index.php?page=virus](http://linuxmafia.com/~rick/faq/index.php?page=virus)

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

> The following quote (regarding [Clam AntiVirus](http://www.clamav.net/)) is from... [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses#Cross-platform_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses#Cross-platform_viruses)...

Many viruses have been written for Linux (hundreds, if not thousands) as the articles I link above acknowledge.  However, they do not spread in the wild very well.  I am not aware of **any** Linux viruses in the wild (with a few exceptions where server machines have not been updated for, literally, *years*).  And, if you do your own research, you will be hard-pressed to find even one example of a Linux virus propagating in the wild right now.  Many people say "but there are Linux viruses out there" but if asked to provide one example of such a virus in the wild, they can't (with the exception of a few old server machines running a 2.4 kernel or something of that sort).  Again, the articles I linked above go into detail.

---

### Post by bodhi.zazen on 2009-06-19
I am going to close this thread now as IMO the question has been asked and answered.

There is general information in the security sticky and that should answer our general questions.

Please feel free to start a new thread if you have a specific question, otherwise these threads "degenerate" into opinions regarding the merits of firewalls and antivirus.

---

