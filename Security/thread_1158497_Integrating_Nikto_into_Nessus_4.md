---
title: "Integrating Nikto into Nessus 4"
date: 2009-05-13
forum: Security
---

### Post by kofkof_00 on 2009-05-13
Hello, Fellow Ubuntu-ers

I have successfully installed Nessus, added THC-Hydra support, Integrated Nmap support, and now I am trying to get Nikto to play nice.

When I invoke the Nessus 4 client, it isn't shown under the cgi abuses list of plug-ins.

I have read the blog posting that Brian Martin did on the subject, and I'm confused about one thing.

[http://blog.tenablesecurity.com/2008/09/using-nessus-to.html](http://blog.tenablesecurity.com/2008/09/using-nessus-to.html)

"# ensure the $PATH knows where to find Nikto. to help ensure this works, also edit your system profile to add this path
PATH=/opt/nikto-2.03:$PATH
export PATH" 

From his post, this needs to be a global PATH setting.

I found this while researching the subject.

[http://sahasranaman.com/2008/02/05/path-variable-in-ubuntu/](http://sahasranaman.com/2008/02/05/path-variable-in-ubuntu/)

"Unlike most other linux distros, the PATH environment variable cannot be set in Ubuntu by adding an assignment statement in the ~/.bash_profile script."

I edited /etc/environment and added /opt/nikto before /usr/local/bin in $PATH

as per [http://ma75.blogspot.com/2008/05/en-calling-nikto-from-nessus.html](http://ma75.blogspot.com/2008/05/en-calling-nikto-from-nessus.html)
 
How can I ensure that Nessus can invoke Nikto, when everything would seem to indicate that you cannot add a global path (read: not invoked from the bash shell manually, from that account)

Nikto is installed in /opt/nikto 
It is the latest version.
I have updated it via the /opt/nikto/nikto.pl -update command
Nessus is up to date. (version 4, the 8.10 specific deb package from Tenable)
I have a profesionnal feed, but I have updated the plug-ins the manual way, as this is still just me playing around in a lab. ;)
Nessus works and has been tested.
I can invoke Nikto & manually give it parameters & it works.
In fact I can just type nikto.pl in bash & it starts up.

I did my homework before praying to the forum gods.

Anyone has ideas as to what else I can try?

---

### Post by kofkof_00 on 2009-05-20
The $PATH variable in /etc/init.d/rc needs to be edited to reflect where you installed Nikto. :)

---

