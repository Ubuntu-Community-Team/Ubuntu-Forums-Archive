---
title: "need help installing postfix"
date: 2008-11-16
forum: Server Platforms
---

### Post by meomike2000 on 2008-11-16
I am trying to setup a mail server using postfix on an ubuntu 8.04.1 server. I used apt-get install postfix to install. After the install is run I get a message saying Errors were encountered while processing:
 exim4-daemon-light
 exim4-base
E: Sub-process /usr/bin/dpkg returned an error code (1).

If I try to run apt-get install postfix, I get:
 You might want to run 'apt-get -f install' to correct these:
 The following packages have unmet dependencies:
  exim4-daemon-light: Depends: exim4-base (>= 4.69) but will not be installed
                   Conflicts: mail-transport-agent
   postfix: Depends: ssl-cert but it is not going to be installed
            Conflicts: mail-transport-agent
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I have tryed:
 apt-get -f install

and then tryed again. just makes a cycle and get same errors over again.






can somebody help with this please.

I am trying to intall clamav, mailx, mailscanner, postfix, postfix-doc, postgrey, and qpopper. all goes well exept for postfix.

tia....mike

---

### Post by djamu on 2008-11-16
[http://www.howtoforge.com/](http://www.howtoforge.com/)

---

### Post by meomike2000 on 2008-11-16
Thank you for your suggestion. I will use it as a reference. The problem has been with a corrupted dpkg file. I have fixed this and am now moving along with my setup.

---

