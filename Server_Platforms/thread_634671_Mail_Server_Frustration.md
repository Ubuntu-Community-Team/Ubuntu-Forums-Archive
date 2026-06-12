---
title: "Mail Server Frustration"
date: 2007-12-07
forum: Server Platforms
---

### Post by Bob_Mendon on 2007-12-07
I have tried about every iteration of mail server found on the net but I just can't get it all together. I am currently running a Clark Connect server for my mail but I want to get some additional utility by running a mail server with the advantages of gnome desktop and my distro of choice is Ubuntu. CC does not have a desktop environment.

I have tried everything but sadly my skills just don't match what it takes to install a simple email server with pop3 and IMAP and some kind of spam and AV protection just to use for my private mail. Are there any packages out there for techno-dolts like me? I tried Citadel but it was just too cheesy and I still couldn't figure out how to setup my own account.

Any suggestions? Maybe somebody would like to earn a few bucks by helping me out?

---

### Post by HermanAB on 2007-12-08
Quickly read this: [http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
Note the part about setting up the DNS and Hostname first.

Then go here: [http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

and in about 20 minutes, you'll have a full fledged mail system and much more!

To make it less cheesy, install the Blue Citadel theme.  Also, you don't have to use WebCit at all.  Citadel works very well with Thunderbird, use IMAP for full functionality.

Cheers,

Herman

---

### Post by KCPokes on 2007-12-08
There are a few other options, outside of Citadel, for a full fledged mail solution including Scalix and Zimbra.  Personally I've found Zimbra to suit my needs the best.  I've been running it for a couple years without any issues.

---

### Post by HermanAB on 2007-12-08
The nice thing about Zimbra and Citadel is that you *can* use the web interface, but you don't *have* to.  Most common folk like the web interfaces, since they are easy to use.  

However, some people prefer to use a traditional mail client like Thunderbird or Outlook and those work very well with these servers too - just select the IMAP protocol and Bob's your uncle.

---

### Post by Bob_Mendon on 2007-12-08
well...Zimbra totally bites it! It's designed for 6.06 and even when you do the hacks to spoof the version, the install scripts still pukes. 

Installing packages

    zimbra-core......zimbra-core_4.5.10_GA_1575.DEBIAN3.1_i386.deb...done
    zimbra-ldap......zimbra-ldap_4.5.10_GA_1575.DEBIAN3.1_i386.deb...done
    zimbra-logger......zimbra-logger_4.5.10_GA_1575.DEBIAN3.1_i386.deb...done
    zimbra-mta......zimbra-mta_4.5.10_GA_1575.DEBIAN3.1_i386.deb...done
    zimbra-snmp......zimbra-snmp_4.5.10_GA_1575.DEBIAN3.1_i386.deb...done
    zimbra-store......zimbra-store_4.5.10_GA_1575.DEBIAN3.1_i386.deb...done
    zimbra-apache......zimbra-apache_4.5.10_GA_1575.DEBIAN3.1_i386.deb...done
    zimbra-spell......zimbra-spell_4.5.10_GA_1575.DEBIAN3.1_i386.deb...FAILED
###ERROR###

zimbra-spell_4.5.10_GA_1575.DEBIAN3.1_i386.deb installation failed

Installation cancelled

Any other ideas?

---

