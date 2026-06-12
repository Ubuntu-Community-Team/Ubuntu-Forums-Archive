---
title: "Torchat"
date: 2010-11-07
forum: Security
---

### Post by chrisbetts on 2010-11-07
Ive only recently ditched Windows so im still finding my feet with Ubuntu so id appreciate it if you speak slowly and try to explain things as simply as possible!

I read through the other Torchat related threads and guides but am still stumpped.

Ive got Tor and Polilo up and running but cant get torchat going. 

Using this as a guide: ([http://ubuntuexport.wordpress.com/20...hat-and-ubuntu](http://ubuntuexport.wordpress.com/20...hat-and-ubuntu)) ive done the following:

Made the 2 changes to the tor config file:

HiddenServiceDir /var/lib/tor/hidden_service/
HiddenServicePort 11009 127.0.0.1:11009

Created the hiddenservices folder and installed torchat via the terminal.

But when I try to fetch a TorID to use - sudo less /var/lib/tor/hidden_service/hostname, I get a "no such file or directory" error message even though as stated above ive uncommented the hidden service entry in the tor config file.

Torchat is the final thing I need to get working to be rid of Windows for good so if anyone can see were I'm going wrong id be greatfull for your assistance.

---

### Post by lisati on 2010-11-07
Please don't start duplicate threads.

---

