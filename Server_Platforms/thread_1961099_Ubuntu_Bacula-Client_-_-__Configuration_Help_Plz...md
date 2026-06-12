---
title: "Ubuntu Bacula-Client - -  Configuration Help Plz.."
date: 2012-04-18
forum: Server Platforms
---

### Post by SILLAT on 2012-04-18
I have Bacula 5.0.0-9 running on a CentOS x64 Box, I have configured Bacula to backup 2 Win2003 Server at present and all is well, I want it to backup my Ubuntu Desktop as well as 2 more Linux Server.
I'm running ubuntu 11.04  with bacula-client  5.0.3-0ubuntu2
I'm having problems configuring the Ubuntu bacula-client so it can run backups, **I'm not sure if I've installed all the right packages but this is what i did:**
I ran
*sudo apt-get install bacula-client bacula-common bacula-console bacula-fd*
I then edited bacula-fd.conf and bconsole.conf and started the service  */etc/init.d/bacula-fd start*
I also open port 9102 - 
root@ubuntu:~# netstat -tulpn | grep LISTEN
tcp        0      0 127.0.1.1:9102          0.0.0.0:*               LISTEN      3687/bacula-fd  
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      867/cupsd       

Bconsole works fine i can connect and run jobs,verify etc..but the bacula-client has errors when i try to run a backup -[I] Fatal error: bsock.c.135 unable to connect to client ERR=Connection refused
[/I]
**What am I Missing ??**

Here's my bacula-fd.conf

> #
# Default  Bacula File Daemon Configuration file
#
#  For Bacula release 5.0.3 (04 August 2010) -- ubuntu 11.04
#
# There is not much to change here except perhaps the
# File daemon Name to
#

#
# List Directors who are permitted to contact this File daemon
#
Director {
  Name = bacula-dir
  Password = "bacula-dir password"
}

#
# Restricted Director, used by tray-monitor to get the
#   status of the file daemon
#
#Director {
#  Name = buntu-mon
#  Password = "hKyy3ScGadhHOg2uMQvaTzwDXRiDWN5Sr"
#  Monitor = yes
#}

#
# "Global" File daemon configuration specifications
#
FileDaemon {                          # this is me
  Name = ubuntu-fd
  FDport = 9102                  # where we listen for the director
  WorkingDirectory = /var/lib/bacula
  Pid Directory = /var/run/bacula
  Maximum Concurrent Jobs = 20
  FDAddress = ubuntu.domain.local      #127.0.0.1
}


here's my bconsole.conf

> #
# Bacula User Agent (or Console) Configuration File
#

Director {
  Name = bacula-dir
  DIRport = 9101
  address = bacula.domain.local
  Password = "bacula-dir password"
}


---

### Post by Gyokuro on 2012-04-18
At a fast glance I think this is your problem:

FDAddress = ubuntu.domain.local #127.0.0.1

you have to set the FQDN and check your /etc/hosts file too. Should work afterwards. HTH

---

### Post by SILLAT on 2012-04-18
> **Gyokuro said:**
> At a fast glance I think this is your problem:

FDAddress = ubuntu.domain.local #127.0.0.1

you have to set the FQDN and check your /etc/hosts file too. Should work afterwards. HTH

the ubuntu.domain.local is just for reference
i actually have ubuntu.example.local

I will add it to my etc/hosts and see what happens
Thanks

---

### Post by Habitual on 2012-04-18
partial /etc/hosts{.template} on my CentOS release 5.5 (Final)/64 bacula server 


```

...
xx.xxx.224.35 bacula bacula
xx.xxx.224.35 bacula-fd bacula-fd
xx.xxx.224.35 bacula-sd bacula-sd
xx.xxx.224.35 bacula-mon bacula-mon
xx.xxx.224.35 bacula-dir bacula-dir
...

```

HTH

---

### Post by SILLAT on 2012-04-18
**@ Gyokuro  & Habitual**
Thanks Much for the /etc/hosts tip
Everything is working now :-)

I added the Bacula Server FQDN to the bacula client /etc/hosts on the Computer
Then added the ubuntu desktop FQDN to the Bacula Server /etc/hosts on the Server
I then used IP adress instead of FQDN for the FDName (i might change this back to see if it will work with the FQDN) 

Thanks Again

---

### Post by Habitual on 2012-04-18
Glad it all worked out.

---

