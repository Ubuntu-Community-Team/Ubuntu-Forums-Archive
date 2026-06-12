---
title: "Warning unable to determine ip address of 'Nagios'"
date: 2007-07-24
forum: Server Platforms
---

### Post by joeyoung25 on 2007-07-24
Hello all, first of all i have Ubuntu 7.04 with Nagios 2.9 installed i had tried to configure postfix to send the mail for Nagios but didnt work and never did figure out why but after a while I just set up a mail account on Evolution and then it started sending mail. My problem now is that I am unable to use synaptic or apt-get or anything else to install a package. I can manually download and install a package but that doesnt get me the updates and makes it more difficult to install certain things. here is the error i get when trying to install "any" package. It just sits there if i do an apt-get update or try to install from synaptic package manager also.
Hope someone knows how to fix this.Thanks for the help in advance.

root@Nagios:~# apt-get install proftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
proftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up proftpd (1.3.0-21ubuntu1) ...
 * Starting ftp server proftpd                                                  
 - IPv4 getaddrinfo 'Nagios' error: No address associated with hostname
 - warning: unable to determine IP address of 'Nagios'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                         [fail]
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: error processing proftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Nagios:~#

---

### Post by dotCOM41799 on 2007-09-18
I'm having the SAME problem..

anyone know how to fix this!? :(

---

### Post by mpslanker on 2007-09-19
Ok I am still pretty much a noob at this myself and I recieve the same error as well.  From what I can gather the FTP server still installed, it just couldn't start it.  I managed to work around this (anyone that has a better understand please correct me if this is a bad idea).  Here is what I did.

*$ hostname*

remember (or better yet write down) whatever that returns 

*$ gksudo gedit /etc/hosts*

here you will see neart the top of the page:
*127.0.0.1 localhost *

Underneath that add this line:
*127.0.0.1 **<whatever hostname returned goes here>***

Now save and exit and start proftpd. That should stop the error you were receiving (it did for me anyway).
Hope that helps and if there is a better solution or my solution causes any other problems please let me know.

Good Luck!

---

### Post by koenn on 2007-09-19
I'd say that fix is good enough. The problem is apparently that the post-install script of proftp can't find an ip address for the host, so adding an ip address and hostname in /etc./hosts would fix it. I suppose you could also use the real address, like
```
192.168.1.1  Nagios
```
(replace address and hostname with those of your computer)

Note that the installation did not complete (the post-install script broke of on the error), which may continue to produce errors and strange behaviour next time apt-get is used. 
You can fix that with 
```
apt-get install -f
```
(it fixes whatever loose ends are left dangling from incomplete installs)

---

### Post by dotCOM41799 on 2007-09-22
I have my hostname setup in there ... and after trying apt-get install -f, i got this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up proftpd (1.3.0-21ubuntu1) ...
 * Starting ftp server proftpd                                                   - Fatal: TLSRSACertificateFile: '/etc/gproftpd/gproftpd.pem' does not exist on line 53 of '/etc/proftpd/proftpd.conf'
                                                                         [fail]
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: error processing proftpd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gproftpd:
 gproftpd depends on proftpd (>= 1.2.10); however:
  Package proftpd is not configured yet.
dpkg: error processing gproftpd (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 proftpd
 gproftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by koenn on 2007-09-22
you could try reconfiguring proftpd :
```
dpkg-reconfigure proftpd
```
If that worked, you can also install and configure gproftpd - the reason that failed is that it needs proftpd to be setup first.

---

### Post by dotCOM41799 on 2007-09-22
Thanks Koenn ... I will try that when I get home, for SURE!!  I'll let you know how it goes.

Thanks again!!

---

### Post by datta on 2008-07-08
Hi,

I am totally new to ubuntu and squid 7.10 and your forum also. Firsly I am sorry to post my message here. I facing some related to proxy

We have configured proxy setting. We have facing some proxy related issue. We seem to be facing timeout issues on the proxy server. Over the last few days there are many times that a particular website has not opened (gives a proxy error) and on refreshing multiple times it sometimes opens up. This behaviour we are investigating. but I am clue less. for more detail.


The requested URL could not be retrieved

--------------------------------------------------------------------------------

While trying to retrieve the URL: [http://entertainment.in.msn.com/bollywood/article.aspx?](http://entertainment.in.msn.com/bollywood/article.aspx?) 

The following error was encountered: 

Unable to determine IP address from host name for entertainment.in.msn.com 
The dnsserver returned: 

Name Error: The domain name does not exist. 
This means that: 

 The cache was not able to resolve the hostname presented in the URL. 
 Check if the address is correct. 
Your cache administrator is webmaster. 



--------------------------------------------------------------------------------

Generated Tue, 08 Jul 2008 05:52:28 GMT by proxy (squid/2.6.STABLE14) 


Please give any idea so I can investigate the above problem

Thanks and Regards,
Datta

---

