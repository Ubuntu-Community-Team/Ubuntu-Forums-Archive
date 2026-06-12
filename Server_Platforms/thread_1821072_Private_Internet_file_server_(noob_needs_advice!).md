---
title: "Private Internet file server (noob needs advice!)"
date: 2011-08-08
forum: Server Platforms
---

### Post by Axxl Force on 2011-08-08
Hello Ubuntu community,

I'm a absolute "server- noob" but I've got some experienced with desktop linux and want to build my own file server to access my stuff over the internet.

I'm using dropbox for a while now like a cloud drive by simply mounting the "private" folder (which I encrypted with encfs/BoxCrypt) in order to cross-platform use important files.

The problem is that Dropbox only provides 2 GB for free and I don't know how secure my data is up there. Moreover I don't wanna always sync all files locally.

I got an intel atom machine standing around and so I want to build my own file server to provide the same or at least a similar service.

1. Which type of server application provides a "network drive" that computers (several users) from the internet can access?

2. What's the best way to encrypt my data and transmission in order to make the system absolutely unattackable/unreadable from outside?

3. Is there a service that can provide a dropbox-style sync mechanism?

4. Which distro should I use? I'd prefer a non-desktop enviroment solution but never had anything to do with it. Is that possible for an average linux user?

5. Any other tips?

I'm aware that this solution won't be very fast because of the limited upload of a standard internet connection but that would be ok! It's more that I want to have the possibiltiy to access all my data as a thin-client anywhere, anytime on any machine and still be on the safe side. I know that this is some kind of contradiction but what would be the best compromise?

I know some questions may sound stupid but I really never had anything to do with servers at all in the past...

thanks for your help!
Axxl

---

### Post by sloopveedub on 2011-08-10
> **Axxl Force said:**
> 
The problem is that Dropbox only provides 2 GB for free and I don't know how secure my data is up there. Moreover I don't wanna always sync all files locally.

Not sure if there's anyone offering more than 2GB for free generally speaking.  As for me, I went with [_[COLOR="Blue"]SpiderOak[/COLOR]_]("http://spideroak.com") because its security (uploads are encrypted and even they can't ever access my data).  Also, it can be setup to run on a headless (no monitor) Linux server.

> 1. Which type of server application provides a "network drive" that computers (several users) from the internet can access?

sFTP is a possibility.  If you have a dynamic IP address for your internet connection (typical), you'll need to use a dynamic DNS service to get from the internet into your box at home. 

> 2. What's the best way to encrypt my data and transmission in order to make the system absolutely unattackable/unreadable from outside?

Probably SSH/sFTP?  

> 3. Is there a service that can provide a dropbox-style sync mechanism?

SpiderOak does this.

> 4. Which distro should I use? I'd prefer a non-desktop enviroment solution but never had anything to do with it. Is that possible for an average linux user?

Ubuntu, of course!  I'm sure many, many distos out there could also accomplish this just as well as Ubuntu but this community is a good one for support!  You might want to start with this excellent little [_[COLOR="blue"]how-to[/COLOR]_]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1") which walks you through setting up a server with the Xubuntu GUI that you can VNC into until you get more comfortable with the command line.  There's also a [_[COLOR="blue"]part II[/COLOR]_]("http://www.bit-tech.net/bits/2007/07/24/build_your_own_better_server/1") which expands on the initial setup.

---

### Post by Cyked on 2011-08-11
I have an Ubuntu machine running Apache with with password encrypted protected directories and HTTPS and HTTP both running in one Apache instance..  

I also have an SFTP jail for whenever someone needs to upload something (which never happens), but its there.

I just host images of the kid so fam can see them, and other random crap so I can access securely from anywhere.

---

### Post by Lars Noodén on 2011-08-12
> **sloopveedub said:**
> Probably SSH/sFTP? 

+1 for SSH / SFTP.

You can run other things on top like SSHFS which uses SFTP but mounts the remote machine as a folder.

---

