---
title: "FTP from Ubuntu Server to Remote File Server"
date: 2010-07-06
forum: Server Platforms
---

### Post by damo12 on 2010-07-06
[FONT="Comic Sans MS"]I support a small business which runs a headless Ubuntu Server (10.04 32bit) as a file server which is accessed by Windows machines.

Although the company has it's own back-up procedure they have decided to back-up some (none sensitive) files online.  The have chosen FileFactory ([http://www.filefactory.com/](http://www.filefactory.com/)) as the host for this.  FileFactory allows files to be uploaded to their server by FTP however I do not know how to set this up on the server.

The idea, if it is possible, is to connect to FileFactory through FTP and then synchronise the data using an Rsync command.

I normally access the server through Webmin and it has vsFTP installed.  I can access the company's server by FTP from inside and outside of the network so I know that vsFTP is working for incomming connections however I cannot work out how to configure it to connect to the FileFactory server.

Any help you can offer is greatly appreciated.

Thanks[/FONT]

---

### Post by HermanAB on 2010-07-06
Howdy,

You cannot connect two servers together.  You need to run a client to hook to FileFactory.  For example wput, or just ordinary ftp.

[http://wput.sourceforge.net/](http://wput.sourceforge.net/)

---

### Post by damo12 on 2010-07-06
[FONT="Comic Sans MS"]Thanks.  That seems to be what I'm looking for but as I'm pretty much a newbie I need a few guidelines.

I did find a guide for curlftps at [http://hartvig.de/2009/howto-mount-a-ftp-drive-in-ubuntu/](http://hartvig.de/2009/howto-mount-a-ftp-drive-in-ubuntu/) which seemed to be perfect but I cannot get it to install correctly.  When I try to install it I get the following message:

> Installing package(s) with command apt-get -y --force-yes -f install curlftpfs ..

Setting up mediatomb-daemon (0.12.0~svn2018-6ubuntu2) ...
update-rc.d: /etc/init.d/mediatomb exists during rc.d purge (use -f to force)
dpkg: error processing mediatomb-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mediatomb:
 mediatomb depends on mediatomb-daemon (>= 0.12.0~svn2018-6ubuntu2); however:
  Package mediatomb-daemon is not configured yet.
dpkg: error processing mediatomb (--configure):
 dependency problems - leaving unconfigured
Setting up cupswrapperhl2030 (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperHL2030-2.0.1: 64: cannot create /usr/share/cups/model/HL2030.ppd: Directory nonexistent
cp: cannot stat `/usr/share/cups/model/HL2030.ppd': No such file or directory
dpkg: error processing cupswrapperhl2030 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libpango1.0-common (1.28.0-0ubuntu2) ...
lpinfo: Connection refused
lpinfo: Connection refused
lpadmin: Unable to connect to server: Connection refused
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
Failed to clean up for defoma: 256 at /usr/sbin/update-pangox-aliases line 48.
dpkg: error processing libpango1.0-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libpango1.0-common (>= 1.28.0-0ubuntu2); however:
  Package libpango1.0-common is not configured yet.
dpkg: error processing libpango1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwxgtk2.8-0:
 libwxgtk2.8-0 depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libwxgtk2.8-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of filezilla:
 filezilla depends on libwxgtk2.8-0 (>= 2.8.10.1); however:
  Package libwxgtk2.8-0 is not configured yet.
dpkg: error processing filezilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-0:
 libgtk2.0-0 depends on libpango1.0-0 (>= 1.20.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtk2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-bin:
 libgtk2.0-bin depends on libgtk2.0-0 (>= 2.20.1-0ubuntu2); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgtk2.0-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mediatomb-daemon
 mediatomb
 cupswrapperhl2030
 libpango1.0-common
 libpango1.0-0
 libwxgtk2.8-0
 filezilla
 libgtk2.0-0
 libgtk2.0-bin
Reading package lists...
Building dependency tree...
Reading state information...
curlftpfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 75 not upgraded.
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libpango1.0-common (1.28.0-0ubuntu2) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
Failed to clean up for defoma: 256 at /usr/sbin/update-pangox-aliases line 48.
dpkg: error processing libpango1.0-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libpango1.0-common (>= 1.28.0-0ubuntu2); however:
  Package libpango1.0-common is not configured yet.
dpkg: error processing libpango1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-0:
 libgtk2.0-0 depends on libpango1.0-0 (>= 1.20.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtk2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwxgtk2.8-0:
 libwxgtk2.8-0 depends on libgtk2.0-0 (>= 2.17.5); however:
  Package libgtk2.0-0 is not configured yet.
 libwxgtk2.8-0 depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libwxgtk2.8-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of filezilla:
 filezilla depends on libwxgtk2.8-0 (>= 2.8.10.1); however:
  Package libwxgtk2.8-0 is not configured yet.
dpkg: error processing filezilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-bin:
 libgtk2.0-bin depends on libgtk2.0-0 (>= 2.20.1-0ubuntu2); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgtk2.0-bin (--configure):
 dependency problems - leaving unconfigured
Setting up mediatomb-daemon (0.12.0~svn2018-6ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
update-rc.d: /etc/init.d/mediatomb exists during rc.d purge (use -f to force)
dpkg: error processing mediatomb-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of mediatomb:
 mediatomb depends on mediatomb-daemon (>= 0.12.0~svn2018-6ubuntu2); however:
  Package mediatomb-daemon is not configured yet.
dpkg: error processing mediatomb (--configure):
 dependency problems - leaving unconfigured
Setting up cupswrapperhl2030 (2.0.1-2) ...
No apport report written because MaxReports is reached already
/usr/local/Brother/cupswrapper/cupswrapperHL2030-2.0.1: 64: cannot create /usr/share/cups/model/HL2030.ppd: Directory nonexistent
cp: cannot stat `/usr/share/cups/model/HL2030.ppd': No such file or directory
dpkg: error processing cupswrapperhl2030 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
lpinfo: Connection refused
lpinfo: Connection refused
lpadmin: Unable to connect to server: Connection refused
Errors were encountered while processing:
 libpango1.0-common
 libpango1.0-0
 libgtk2.0-0
 libwxgtk2.8-0
 filezilla
 libgtk2.0-bin
 mediatomb-daemon
 mediatomb
 cupswrapperhl2030
E: Sub-process /usr/bin/dpkg returned an error code (1)

.. install failed!

Unfortunately that means nothing to me.  I hope someone can translate it for me into directions of where I am going wrong.[/FONT]

---

### Post by damo12 on 2010-07-06
[FONT="Comic Sans MS"]My bad, it turns out curlftpfs was already installed.  I managed to mount the ftp server using the command:

```
sudo curlftpfs -o allow_other ftp://myusername:mypassword@ftp.mydomain.com myftp /mount/location
```

In case anyone is wondering this can be unmounted using the command:

```
sudo umount /mount/location
```[/FONT]

---

