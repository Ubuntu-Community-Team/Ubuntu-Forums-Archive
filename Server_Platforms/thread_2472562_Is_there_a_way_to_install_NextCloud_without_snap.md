---
title: "Is there a way to install NextCloud without snap?"
date: 2022-03-03
forum: Server Platforms
---

### Post by MakOwner on 2022-03-03
As the title says -- Is there a way to install without using the snap?
Ah, let me rephrase -- comparable installation from the non-snap repository or perhaps a NextCloud ppa?

Using DuckDuckGo I haven't found anything relevant so far.

---

### Post by #&amp;thj^% on 2022-03-03
> **MakOwner said:**
> As the title says -- Is there a way to install without using the snap?
Ah, let me rephrase -- comparable installation from the non-snap repository or perhaps a NextCloud ppa?

Using DuckDuckGo I haven't found anything relevant so far.

This is for 20.04 [https://askubuntu.com/questions/1256624/installing-nextcloud-19-without-snap-on-ubuntu-server-20-04-apache-2](https://askubuntu.com/questions/1256624/installing-nextcloud-19-without-snap-on-ubuntu-server-20-04-apache-2)
Same Instructions from the author [https://gist.github.com/MarGraz/3b15d318954acbaed0d61eb89c9d334d](https://gist.github.com/MarGraz/3b15d318954acbaed0d61eb89c9d334d)

---

### Post by MakOwner on 2022-03-03
Thank you.  

Shame to see Ubuntu spiral downhill like this :/

---

### Post by MakOwner on 2022-03-03
Thank you very much :)  
That actually led me to some even more useful information -- there is a Next Cloud OVA you can download to build a virtual machine.  
That should be an easy one to set up and compare to the build I do using that procedure.

Here is the link I stumbled upon: [https://nextcloud.com/install/#instructions-server](https://nextcloud.com/install/#instructions-server)
And another (small) version here: [https://www.hanssonit.se/nextcloud-vm/](https://www.hanssonit.se/nextcloud-vm/)

---

### Post by LHammonds on 2022-03-04
> **MakOwner said:**
> Shame to see Ubuntu spiral downhill like this :/What do you mean by this?  I'm confused.

This is [how I install NextCloud 19 on Ubuntu 20.04](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=282) but the MariaDB server is a separate dedicated machine which just means the DB setup is slightly adjusted for access from another machine and the permissions in the database will reference the application machine...unless you use the % access which is not recommended.

LHammonds

---

### Post by VMC on 2022-03-04
> **LHammonds said:**
> What do you mean by this?  I'm confused.

...

I'm guessing he means the increasing Snap usage.

---

### Post by LHammonds on 2022-03-04
> **VMC said:**
> I'm guessing he means the increasing Snap usage.
LoL, if that's the case then the person doesn't realize more options = better for us.   You can still install NextCloud manually, just as I have done...you can still "apt install" from repository if you want everything on one server including the database that comes with it (and usually out of date which is not good with PHP apps) and now you have the snap option.  More options is nice even if apt and snap are not options I'd ever use for NextCloud.  However, snap would be great for those apps that are so complicated that they require specific versions (read outdated) of specific libraries which makes even experienced installers pull their hair out.

But that was just a side question since I had no idea what was meant by it but was probably referring to existence of snap.

LHammonds

---

### Post by TheFu on 2022-03-04
I don't use snaps for servers and haven't used pre-built installs (like docker) for anything beyond a toy or extremely short-term trial to learn what some software was all about. 

My nextcloud install is manual.  I've been upgrading it for 3+ yrs, maybe a little longer. I made a mistake of putting other php webapps into the same virtual machine with nextcloud.  Last fall, I moved the other webapps into a dedicated LXD container for each and I plan to move nextcloud to an lxd container RSN - real soon now.  That means sometime in the next 2 yrs. ;)   If I were doing it again, I'd start out building nextcloud into a dedicated container, not necessarily lxd, but definitely never docker.  Don't use pre-built containers randomly gotten over the internet.  Just don't.

I should say that none of my php webapps are internet facing - at least not directly. To access them, a VPN must be used. I just don't believe I have the skills to secure those webapps and all the install instructions that I've seen are a bit lacking on security.  Adding a TLS web cert doesn't secure anything. It is amazing how often people post "Secure the install" and it is just adding a TLS cert so HTTPS works.  Beware if you see that claim on any instructions. All HTTPS does is provide a connection between the client and server that cannot be modified. It doesn't validate the server - not really and it doesn't prevent the server from being hacked.

---

### Post by kevdog on 2022-03-04
@TheFu -- I think your statement about "pre-built" containers randomly gotten over the internet is kind of farfetched.  Nextcloud releases official containers which would probably be a starting point. You can say the container isn't secure -- however after installing nextcloud on bsd within a jail -- I'm no more certain this installation is more secure than the container image.  I definitely don't have the skills to audit the code.  Usually the container image is updated quicker with more modern php versions than I can do it myself.  Containers might not be for everyone, however I can't say for nextcloud its a bad option.  For other projects where the containers have essentially been abandoned or not really updated, this argument might hold true.

---

### Post by TheFu on 2022-03-04
> **kevdog said:**
> @TheFu -- I think your statement about "pre-built" containers randomly gotten over the internet is kind of farfetched.  Nextcloud releases official containers which would probably be a starting point. You can say the container isn't secure -- however after installing nextcloud on bsd within a jail -- I'm no more certain this installation is more secure than the container image.  I definitely don't have the skills to audit the code.  Usually the container image is updated quicker with more modern php versions than I can do it myself.  Containers might not be for everyone, however I can't say for nextcloud its a bad option.  For other projects where the containers have essentially been abandoned or not really updated, this argument might hold true.

There are plenty of random places providing pre-built containers.  I wouldn't call the nextcloud project container "random", as we are already trusting their work just by using their php code already.  But that doesn't mean they are experts on container security either.  I don't think there is anything malicious in the core nextcloud code. They may be experts on container security too. I don't know and since I've decided not to use any pre-build containers, at least not for production, I don't need to know.

I certainly don't trust docker's container repo and have concerns over containers provided for NAS devices.  But each might be provided by the main project team. I don't need to know, since I don't have any commercial NAS devices.

Just like PPAs, I always say, use a "trusted PPA", but people have different ideas what "trusted" means. We all have a different idea. I suspect that applies to container repos too.  What I consider "random" might be the gold standard for someone else.  That's fine. We all have different needs and make different choices.

Being aware and cautious still makes sense, rather than assuming all is perfect without spending the 3 minutes to validate where the code/package/container came from.

---

