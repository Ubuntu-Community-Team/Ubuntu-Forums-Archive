---
title: "HELP!!! Spam Filter Using Ubuntu 8.04"
date: 2008-06-18
forum: Server Platforms
---

### Post by leartec on 2008-06-18
Hi,
   I am trying to build a spam filter for work using Ubuntu Server 8.04. Everything seems to be working fine expect I cant get Pyzor to install. The web site I'm using as instructional reference is: 

[http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu](http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu)


Now when I try to install this line:

apt-get install postfix postfix-pcre postfix-mysql postfix-ldap cabextract lha unrar razor pyzor spamassassin


I get this error:

[I]The following packages have unmet dependencies:
  pyzor: Depends: python (< 2.5) but 2.5.2-0ubuntu1 is to be installed
E: Broken packages[/I]


I even tried to break it down to this:

*apt-get install pyzor*


This is the entire output i get:

[I]Reading package lists... Done
Buing dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pyzor: Depends: python (< 2.5) but 2.5.2-0ubuntu1 is to be installed
E: Broken packages[/I]



From what I can tell it looks like Pyzor requires an older version of Python, or it is trying to install an older version of Pyzor. 


I did find Pyzor 04.0, the newest version. I have it downloaded and saved to my desktop, but dont know how to install it from my desktop. I am actually using putty to connect to the server I am working on.

Any ideas would be very helpful. Thanks!!!

---

