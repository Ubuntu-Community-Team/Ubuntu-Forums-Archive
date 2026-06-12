---
title: "running a software server service"
date: 2010-08-18
forum: Server Platforms
---

### Post by strm on 2010-08-18
Hi,
I've been doing some searching for a convenient way to run a service on one of our servers (currently serving NIS and some NFS shares) to also serve software installs by allowing any NIS client to run a network install of available software on their machine.
So, for example, if an NIS client logs into one of the stations, he/she should have an option for some network installs available from the server (say some spreadsheet application). Once he/she installs it locally using the network install, that machine will now have the application available for use by all NIS users (on that particular machine), and of course be running it locally. The key is to make the process simple and allow general installation to be system-wide but user settings to be stored in users' home directories (which are NFS mounted from elsewhere).

Any ideas? Any pointers to some further reading would be appreciated,
Thanks!

---

### Post by strm on 2010-08-20
nothing at all?
apologies for the bump...

---

### Post by Lars Noodén on 2010-08-23
Could you give a little more description about what machine the programs should be running on?

If you have NFS, AFS, SMB or other networked file system, then the clients can use local data with locally run applications that are fetched from the server's harddisk.

If you have Freenx or VNC, then the clients display locally applications that are running on the server and accessing data on the server.

---

### Post by strm on 2010-08-31
I have total freedom as to what to setup and how. Currently most servers only export NFS directories but setting up AFS or SMB is not an issue. Same goes for VNC, Freenx. All client machines are fully capable Linux installations (mostly Ubuntu and Fedora) with VNC clients and servers installed for off-campus access. However, remote desktop solution doesn't seem appropriate as I want _local_ client installations to be available to users as to not bog down the server with regular user menial tasks.

In other words, I would like to provide seamless installations via the network (I would imagine one of the above network fs protocols) that only have to be run once per client _machine_ (again, all already running linux).

I am seeking advice as to which avenue it would be best to take in order to provide this service.

---

### Post by scorp123 on 2010-08-31
> **strm said:**
> I am seeking advice as to which avenue it would be best to take in order to provide this service. Is it allowed to mention commercial solutions? I'd use this then:

Sun/Oracle Secure Global Desktop:

[http://www.oracle.com/us/technologies/virtualization/secure-global-desktop-ds-068717.pdf](http://www.oracle.com/us/technologies/virtualization/secure-global-desktop-ds-068717.pdf)


And yes, it can run on Linux too. And yes, it's possible to convert the RHEL/SLES *.rpm packages into Debian/Ubuntu *.deb packages. Been there, done that.

The point here would be that all applications are installed on the server(s). All client desktops need to do is to login ... and taaadaaa, those applications show up in the start menu. Works tip top with Windows and GNOME.

So "Joe User" clicks on his "OpenOffice" icon, OpenOffice starts, he uses it like he would use any other normal app. What "Joe User" doesn't know and doesn't need to know is that his OpenOffice application is in fact running off the server and not locally.

And when "Joe User" logs in on a different desktop, the application follows him. In Sun lingo this is called "hotdesking". Your apps follow you wherever you go.

Advantages:

+ You only install the applications 1 x time => on the server
+ you can move around in the office, login from different desktops, login from home ... no problem. Your apps follow you wherever you go
+ no need to move large amounts of data around, install 1000 apps on 1000 different desktops ... you only install apps 1 x
+ no need for dozens of shares everywhere ... a network-mounted user home directory so that users can save their files wherever they login from will totally suffice ...

And last but not least ... if you decide to upgrade an application you also just upgrade it 1 x ==> on the server. No need to chase all the old installations and then copy the same x-100 megs around again and again.

Sorry for the sales pitch ... but this product is ***good*** and it has saved my lazy admin a** many times :D :D :D

---

