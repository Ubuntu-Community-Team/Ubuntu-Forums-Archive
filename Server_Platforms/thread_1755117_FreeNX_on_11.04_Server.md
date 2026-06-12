---
title: "FreeNX on 11.04 Server?"
date: 2011-05-10
forum: Server Platforms
---

### Post by watterzz on 2011-05-10
I have an Acer AH340-U2T1H I recently setup with Ubuntu Server 11.04. The server came with WHS originally. I have Ubuntu up and running and log on remotely via SSH. I have installed the gnome desktop environment and would like to setup access to the desktop.

FreeNX seems like the way to go and I've got the NX Client setup on my other machine, but am not having any luck getting FreeNX installed on the server.

This is the method I've found:

```
sudo add-apt-repository ppa:freenx-team
sudo apt-get update
sudo aptitude install freenx
```

After the update, I get the following errors:

```
W: Failed to fetch [http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
```

Any ideas? This is the first time I've messed with a server so keep it simple.

---

### Post by arrrghhh on 2011-05-10
I'm confused, why did you put Gnome on a server?  SSH is all you should need.

If you want Gnome, install Ubuntu Desktop.  Server doesn't come with a DE because it's meant to be lean&mean - little to update, little for security holes.  Don't fit a square peg into a round hole, if you feel you *need* a full blown DE, install Ubuntu Desktop.

---

### Post by watterzz on 2011-05-10
I'm planning on using the server as a media hub. I'm going to set up Subsonic and some torrent stuff. Also, I would just like a graphical way to manage files.

Should I just install Ubuntu Desktop then? This system will only be accessed remotely. What "server" features would I lose from installing just the desktop version?

If I do go with the server version, though, is there a way to get FreeNX on there?

---

### Post by druhboruch on 2011-05-11
Try apt-get install freenx-server.

If it doesn't work, check check your apt sources under
/etc/apt/sources.list.d as there is no packages for natty in this repo yet.
Packages build from lucid worked with maverick.

[https://launchpad.net/~freenx-team/+archive/ppa](https://launchpad.net/~freenx-team/+archive/ppa)

---

### Post by arrrghhh on 2011-05-11
> **watterzz said:**
> I'm planning on using the server as a media hub. I'm going to set up Subsonic and some torrent stuff. Also, I would just like a graphical way to manage files.

Should I just install Ubuntu Desktop then? This system will only be accessed remotely. What "server" features would I lose from installing just the desktop version?

If I do go with the server version, though, is there a way to get FreeNX on there?

I would say if you want a DE, use Ubuntu Desktop.  It can run **all** the same apps the server distro can, at the same service level just like a server - user-less basically.

You wouldn't really lose any 'server' features - the point of the server is to be lean-and-mean like I said above, so no DE to update/no security holes that come with running a DE, etc.  So there's really no tangible difference, server has some packages removed compared to the desktop edition... but like I said you can install all the same services on the desktop version as you can on the server edition.  

Please, if you want a DE, don't use Ubuntu Server!!

---

### Post by fezzik on 2011-05-12
The Server edition is just a minimal install with a few daemons preloaded.  I would say that a server install is a good choice really.  It would be a bit more work because you would have to install pretty much everything but in the end it would only have what you want on it.  I don't remember much about nomachineNX but cygwin was one of the ones I used to access from work over SSH.  The thing is it has the gnome desktop you don't need it on your server.  For server you can install the Xserver (there are instructions elsewhere in here it's been a while since I have done it but when I was using a strictly remote server setup I did pretty much exactly what you are doing). You can configure SSH to forward X and then there are several options for running graphic programs.  

So far I haven't been able to get NX working on 11.04.  I was about to try again because I liked using the NoMachineNX for graphic access.  They don't have repositories for anything past Lucid.

I currently have a full desktop install with several server daemons on it.  Mostly because our electric bills have been pretty large.  I haven't been able to get rdp working either but those ports are blocked from going out at work so it doesn't matter anyway.  The main thing I would  want graphic access for is checking the performance monitor.  Also for school I need to be able to run my virtual machines on that computer because the ones at school aren't really powerful enough to run two virtual servers at the same time.


For What it is worth.  You can manually go in and edit the /etc/apt/sources.list.d/freenx-team-ppa-natty.list  file and just change natty to lucid.  It is an old build but it will install freenx-server after and update.  A more ideal approach would be to build it from source and install it.  If you are so inclined.

---

### Post by vanlindholm on 2011-05-13
This worked for me: [http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html](http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html)

---

### Post by Njall on 2011-06-02
> **vanlindholm said:**
> This worked for me: [http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html](http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html)

I second this!  Well written HOWTO.

---

### Post by deesto on 2011-06-21
> **Njall said:**
> I second this!  Well written HOWTO.Certainly a well-written how-to, and it works.  But what happens when the PPA team finally updates their code for Natty?  Users following that how-to would be stuck with the Lucid version.

---

