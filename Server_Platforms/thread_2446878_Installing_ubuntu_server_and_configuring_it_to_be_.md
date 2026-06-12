---
title: "Installing ubuntu server and configuring it to be a home media and a web server"
date: 2020-07-08
forum: Server Platforms
---

### Post by 66gramms on 2020-07-08
Hello!

I've found my uncle's old computer (from around 2010) hanging around in our garage. I was thinking on cleaning it and making it into a home server for myself and the family, so it could host movies and stuff, also it could localhost websites.

I've never worked with any server before so I'm a bit afraid and that's why I came here for instructions. I know I should download and install ubuntu server but first of all which version would be compatible with this old PC?
Then I have no idea how to do the hosting, I guess I'll have to make it into a static IP, I could do that for my own computer from the router based on it's MAC adress, I gues it'll work the same with the server?

Then what software do I use and how do I set it up? ATM I use plex media server from my computer and I like it so far so I'd love to use the same on my linux server. For the webhosting I have no idea?

Also, how could I connect to it to see and use it's CLI so I don't have to plug a monitor to it every time I want to do something?

Thank you for your help in advance!

---

### Post by slickymaster on 2020-07-08
Thread moved to **Server Platforms** for a better fit

---

### Post by Doug S on 2020-07-08
You question is much to broad.

> **66gramms said:**
> I've never worked with any server before so I'm a bit afraid and that's why I came here for instructions. I know I should download and install ubuntu server but first of all which version would be compatible with this old PC? I suggest the [Ubuntu Serverguide]("https://ubuntu.com/server/docs") as your main reference. 

> **66gramms said:**
> Then what software do I use and how do I set it up? Beats me. You need to decide that.

> **66gramms said:**
> Also, how could I connect to it to see and use it's CLI so I don't have to plug a monitor to it every time I want to do something?I use puTTY, myself. Depending on the OS on your PC, you might be able to use SSH directly from a terminal window in your PC.

---

### Post by TheFu on 2020-07-08
There isn't 1 answer for each of your questions.
Each choice has pros and cons.  There are 20+ different web servers to choose.
For setting a static ip, there are multiple ways.  

As for managing the server - there isn't any GUi so the best answer is over ssh.  There are many different client programs, but most people just use ssh in a terminal from their Unix workstation.  ssh and ssh-based methods are how we transfer files and manage systems around the world efficiently.  There are ssh/sftp/scp clients for every OS made.

"old computer" isn't very descriptive.  Some exact specs would be good, otherwise we aren't even guessing good.

A raspberry pi v3 or newer can do what you seek (probably).  The only questionable part is storage capacity. Also if any media needs transcoding neither the Pi nor the 10 yr old PC will handle that well.

To learn what you'll want to know, start here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by SeijiSensei on 2020-07-08
First, I wouldn't install Ubuntu Server.  Pick a lightweight desktop version like Xubuntu or Lubuntu.  You can still connect remotely with SSH and use the command prompt if you wish, but getting things up and running at first might be easier with a GUI.

Second, you haven't told us much about this computer.  You might need a new disk drive or two.  Memory is less of an issue in my experience though I'd try to get to 2-4GB if you can.

You can run Plex on Linux if you want, or you can run other DLNA servers.  I use [minidlna]("https://help.ubuntu.com/community/MiniDLNA") myself.  It takes only a couple of minor changes to a configuration file and you're on your way.  I can see my minidlna installation from my Android phone and from my TVs all of which have built-in DLNA clients.

I also run an NFS server on this same machine.  Most of the time I watch videos on the server via a computer running Kubuntu over wifi that's connected to my TV.  I mount the video directories from the server using NFS and access them just as if they were on the local machine.

---

### Post by LHammonds on 2020-07-08
> **66gramms said:**
> I've never worked with any server before so I'm a bit afraid and that's why I came here for instructions.
#1 - Do not try to install an OS directly on that machine and mess around trying to learn on it.  Why?  Because you will want to re-install many times to try different software / configurations and it isn't always very clean to install one app, and remove...then install another, etc.

#2 - Use VirtualBox on your PC to install a server operating system and make sure you make good use of snapshots.  After installing the base operating system, take a snapshot and call it "base install" and then proceed to apply updates and whatnot to the OS...then take another snapshot and call it "base + patches."  Then install a web server such as Apache, then take another snapshot.  Then configure the web server, add modules, etc.  If at any point you want to go back to the way it was when you 1st installed Apache, use the snapshot manager to revert to that point.  Or if you want to go all the way back to a base install, you can do that too...VERY quickly which saves you a ton of time and avoids problems such as not knowing how to configure a service and having messed around with 20 different settings to finally make it work how you want it.  Revert all the changes you made and try it again after you know what you need to do to get the results you are looking for.

Use snapshots like this to refine your server and make your learning experience much better and faster.

Once you have documented how to install the server and the services you want, you can try it one more time in a virtual environment.  Once you have it exactly how you want it, THEN take it to the physical server and replicate the same process you have proven to work in a virtual environment.  Anything that is different with the physical server should just be the differences in the physical hardware but the process to set it up should be almost identical.

LHammonds

---

