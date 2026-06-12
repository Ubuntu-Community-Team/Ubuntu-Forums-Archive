---
title: "MythTV (master backend) 0.24.1 on Ubuntu server 10.04?"
date: 2011-08-12
forum: Server Platforms
---

### Post by rage_311 on 2011-08-12
Hi,

I had a dedicated HTPC box running Mythbuntu 11.04 (MythTV 0.24.1, I believe) that was both a master backend and frontend.  I was also running a separate box (server 10.04) as a file server, print server, etc.  Very recently I decided to try to migrate the backend duties and database from the HTPC box to the server so that I only need to have one machine running 24/7.  So, on the server, I installed mythtv-backend-master from the repository, which for 10.04 is version 0.23.0+fixes.  You might have seen this one coming... when I try to import the database from the Mythbuntu box into the server's MythTV installation, I get an error message saying the database schema (1264) is newer than expected (1254).

So, I'm wondering about my options at this point.  Is it reasonable to install the same version of MythTV on the server?  What would be the best way of going about that?

Is there a way to easily revert the database schema to the earlier version that's required?

Will I just need to start over with a new database?  (Hopefully not this one.)

Other options I haven't thought of?

Thanks in advance for any guidance.

---

### Post by tgm4883 on 2011-08-12
> **rage_311 said:**
> Hi,

I had a dedicated HTPC box running Mythbuntu 11.04 (MythTV 0.24.1, I believe) that was both a master backend and frontend.  I was also running a separate box (server 10.04) as a file server, print server, etc.  Very recently I decided to try to migrate the backend duties and database from the HTPC box to the server so that I only need to have one machine running 24/7.  So, on the server, I installed mythtv-backend-master from the repository, which for 10.04 is version 0.23.0+fixes.  You might have seen this one coming... when I try to import the database from the Mythbuntu box into the server's MythTV installation, I get an error message saying the database schema (1264) is newer than expected (1254).

So, I'm wondering about my options at this point.  Is it reasonable to install the same version of MythTV on the server?  What would be the best way of going about that?

Is there a way to easily revert the database schema to the earlier version that's required?

Will I just need to start over with a new database?  (Hopefully not this one.)

Other options I haven't thought of?

Thanks in advance for any guidance.

You cannot revert the database. I would activate the Mythbuntu team's PPA and use that to upgrade the MythTV backend to a version you can use. On 10.04 I believe you can get 0.23.0, 0.23.1, and 0.24 (and the development version 0.25) using [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

---

### Post by rage_311 on 2011-08-12
That's exactly what I needed.  Thank you.  So far, so good... still working on the rest of the setup, so I'll let you know how it goes.

I looked at the link that you gave me and it all appeared to be GUI-based -- I could be wrong.  That got me looking around a little bit more and I came across this page: 
[http://www.linuxnov.com/install-mythtv-0-24-1-in-ubuntu-11-04-natty-ppa/](http://www.linuxnov.com/install-mythtv-0-24-1-in-ubuntu-11-04-natty-ppa/)

It suggests a way to add the same repository via CLI (since I'm on Ubuntu server) then install the latest package.
Note: you must install python-software-properties before adding repositories via the add-apt-repository command.
Note2: there's a typo on that webpage... it says to apt-add-repository, but the real command is add-apt-repository.

```
sudo add-apt-repository ppa:mythbuntu/0.24
sudo apt-get update
sudo apt-get install mythtv
```
That's what did it.  After I removed my original 0.23.0+fixes installation and installed 0.24.1 from Mythbuntu's repository, I was able to import the database successfully.  Thanks again for the help!  I don't know if I ever would've gotten there without it.

---

### Post by tgm4883 on 2011-08-15
> **rage_311 said:**
> That's exactly what I needed.  Thank you.  So far, so good... still working on the rest of the setup, so I'll let you know how it goes.

I looked at the link that you gave me and it all appeared to be GUI-based -- I could be wrong.  That got me looking around a little bit more and I came across this page: 
[http://www.linuxnov.com/install-mythtv-0-24-1-in-ubuntu-11-04-natty-ppa/](http://www.linuxnov.com/install-mythtv-0-24-1-in-ubuntu-11-04-natty-ppa/)

It suggests a way to add the same repository via CLI (since I'm on Ubuntu server) then install the latest package.
Note: you must install python-software-properties before adding repositories via the add-apt-repository command.
Note2: there's a typo on that webpage... it says to apt-add-repository, but the real command is add-apt-repository.

```
sudo add-apt-repository ppa:mythbuntu/0.24
sudo apt-get update
sudo apt-get install mythtv
```
That's what did it.  After I removed my original 0.23.0+fixes installation and installed 0.24.1 from Mythbuntu's repository, I was able to import the database successfully.  Thanks again for the help!  I don't know if I ever would've gotten there without it.

Yep that's the correct way to do it. I didn't think about you not having a GUI available (although it would be setup via debconf as well, it might try to pull in a bunch of dependencies for you). How do you have the backend setup without a GUI?

---

### Post by rage_311 on 2011-08-25
> **tgm4883 said:**
> Yep that's the correct way to do it. I didn't think about you not having a GUI available (although it would be setup via debconf as well, it might try to pull in a bunch of dependencies for you). How do you have the backend setup without a GUI?

From a separate Ubuntu (desktop edition) machine on the network, I start an ssh session with "X11 forwarding" (using the -X option) to the server.  Then I run mythtv-setup and it runs it on my desktop and acts/appears just like it was running locally.

For anybody else that might want to do this, here's the syntax of that command:
```
ssh -X username@192.168.2.100
```
Of course, just replace "username" with the username for the machine that you're remoting into and the IP address with the actual address of the remote machine.

---

### Post by tgm4883 on 2011-08-25
> **rage_311 said:**
> From a separate Ubuntu (desktop edition) machine on the network, I start an ssh session with "X11 forwarding" (using the -X option) to the server.  Then I run mythtv-setup and it runs it on my desktop and acts/appears just like it was running locally.

For anybody else that might want to do this, here's the syntax of that command:
```
ssh -X username@192.168.2.100
```
Of course, just replace "username" with the username for the machine that you're remoting into and the IP address with the actual address of the remote machine.

Ah OK, so it does actually have a GUI available then.

---

