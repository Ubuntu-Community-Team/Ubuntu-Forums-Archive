---
title: "Secure Jailed Chrooted Hosting Server"
date: 2011-09-23
forum: Security
---

### Post by bundabrg on 2011-09-23
Hi All,

I'm busy playing around with a config that seems fairly easy to setup and was just looking at feedback. I havn't quite finished yet but I'm almost done.

[SIZE="3"]**The Scenario**[/SIZE]
I have a hosting server. It will provide web hosting for static, PHP and python scripts.

It will also allow limited shell access via SSH.

Access for files is via SFTP though it might also support FTP

[SIZE="3"]**Common Issue**[/SIZE]
The most common issue with providing shared hosting is the fact that if someone has access to your server they can often see more than they should. For example if you allow someone access to PHP, then they can script a php shell that can access anything else that is readable by apache. This can be mitigated somewhat through the use of suPHP and suexec.

Also if someone has ssh access, then they also have access to stuff that is outside their home directory. They may also be able to exploit suid scripts that are out dated.

All this is not new information, and indeed there are strategies to work around this. I do know however how difficult it sometimes is to manage a whole host of shared hosting servers, all at differing versions, and be able to keep up to date with all updates.

[SIZE="3"]**Idea**[/SIZE]
I had the idea that for shell access I'd like to jail the user into their own environment to such a degree that they would be unable to see any other users data.

Commonly this is down by creating jails for a user, or by using bind mounts to mount a jail around a users directory and chroot them into it.

However I wanted to extend this further and try get this jail idea to work with Apache as well, or indeed work with anything.

What I came up with is to make use of an automounter. What happens is when anything attempts to touch the users 'directory', the automounter will automatically create a jailed environment for them.

I performed the following: -
[LIST=1]
[*]Mounted a volume, with the -nosuid option, onto /mnt/data
[*]Created a JAIL base through the use of **debootstrap** to /mnt/data/jail/base. I use debootstrap as I want to be able to then add stuff in here as needed to support libraries etc.
[/LIST]

Because /mnt/data is mounted nosuid, the jail is about as harmless as one can get.

I store my users in the following structure: -
```

  /mnt/data
    /user
      /<username>
        /home
        /web
        /cow

```

I then create a /virtual dir at root. Making use of **autofs**, whenever someone attempts to access
```

  /virtual/<username>

```

autofs will perform the following: -
[LIST=1]
[*]Mount using **aufs** the jail base (/mnt/data/jail/base) and the user COW dir (/mnt/data/user/<username>/cow)
[*]Bind mount /mnt/data/user/<username>/home to /virtual/<username>/home/<username>
[*]Bind mount /mnt/data/user/<username>/web to /virtual/<username>/var/www
[*]Bind mount or mount dev,proc,sys to /virtual/<username>/dev|proc|sys though I may consider just adding static dev entries in the jail for security.
[*]Either mount /mnt/data/<username>/tmp to tmpfs or leave it writable within the COW provided in the AUFS mount. Haven't quite decided on which way I'm going yet.
[/LIST]

After a period of inactivity, it will unmount all this.

Then I can make use of a special shell for the user that will peform the following: -
[LIST=1]
[*]Chroot them into /virtual/<username>
[*]Execute a shell inside here, setting privileges to the user
[/LIST]

Whats good is that I can configure apache on the server to setup VirtualHost entries to point to the /virtual/<username>/var/www folder and make use of suPHP's chroot function to lock web hits in there. It would require a few symlinks added to the COW to get working.

It also means pretty much any other program can be configured to make use of the virtual dir and be jailed in as long as it has the capability of chrooting.

The special shell would be SUID root, and would basically perform the following: -
[LIST=1]
[*]Check if /virtual/<logged_in_USER> exists. If not, bail
[*]Chroot into /virtual/<logged_in_USER>, and set privs to <logged_in_USER>
[/LIST]

So if user fred executes it, it will chroot into /virtual/fred as the user fred.

[SIZE="3"]**Conclusion**[/SIZE]
As far as I can tell this should be reasonably light on resources. If the autofs timeout is set high enough, then only the first person hitting a website will get a slight hiccup in speed as everything is mounted. Bind mounts are reasonably light on the system as well though I can't yet find documentation that gives its impact.

I wonder then how such a server with 10,000 users would go.

---

### Post by bodhi.zazen on 2011-09-23
Sounds as if you should take a look at LXC or Openvz or Xen or Vserver.

---

### Post by Dangertux on 2011-09-23
> **bundabrg said:**
> Hi All,

I'm busy playing around with a config that seems fairly easy to setup and was just looking at feedback. I havn't quite finished yet but I'm almost done.

[SIZE=3]**The Scenario**[/SIZE]
I have a hosting server. It will provide web hosting for static, PHP and python scripts.

It will also allow limited shell access via SSH.

Access for files is via SFTP though it might also support FTP

[SIZE=3]**Common Issue**[/SIZE]
The most common issue with providing shared hosting is the fact that if someone has access to your server they can often see more than they should. For example if you allow someone access to PHP, then they can script a php shell that can access anything else that is readable by apache. This can be mitigated somewhat through the use of suPHP and suexec.

Also if someone has ssh access, then they also have access to stuff that is outside their home directory. They may also be able to exploit suid scripts that are out dated.

All this is not new information, and indeed there are strategies to work around this. I do know however how difficult it sometimes is to manage a whole host of shared hosting servers, all at differing versions, and be able to keep up to date with all updates.

[SIZE=3]**Idea**[/SIZE]
I had the idea that for shell access I'd like to jail the user into their own environment to such a degree that they would be unable to see any other users data.

Commonly this is down by creating jails for a user, or by using bind mounts to mount a jail around a users directory and chroot them into it.

However I wanted to extend this further and try get this jail idea to work with Apache as well, or indeed work with anything.

What I came up with is to make use of an automounter. What happens is when anything attempts to touch the users 'directory', the automounter will automatically create a jailed environment for them.

I performed the following: -
[LIST=1]
[*]Mounted a volume, with the -nosuid option, onto /mnt/data
[*]Created a JAIL base through the use of **debootstrap** to /mnt/data/jail/base. I use debootstrap as I want to be able to then add stuff in here as needed to support libraries etc.
[/LIST]

Because /mnt/data is mounted nosuid, the jail is about as harmless as one can get.

I store my users in the following structure: -
```

  /mnt/data
    /user
      /<username>
        /home
        /web
        /cow

```I then create a /virtual dir at root. Making use of **autofs**, whenever someone attempts to access
```

  /virtual/<username>

```autofs will perform the following: -
[LIST=1]
[*]Mount using **aufs** the jail base (/mnt/data/jail/base) and the user COW dir (/mnt/data/user/<username>/cow)
[*]Bind mount /mnt/data/user/<username>/home to /virtual/<username>/home/<username>
[*]Bind mount /mnt/data/user/<username>/web to /virtual/<username>/var/www
[*]Bind mount or mount dev,proc,sys to /virtual/<username>/dev|proc|sys though I may consider just adding static dev entries in the jail for security.
[*]Either mount /mnt/data/<username>/tmp to tmpfs or leave it writable within the COW provided in the AUFS mount. Haven't quite decided on which way I'm going yet.
[/LIST]

After a period of inactivity, it will unmount all this.

Then I can make use of a special shell for the user that will peform the following: -
[LIST=1]
[*]Chroot them into /virtual/<username>
[*]Execute a shell inside here, setting privileges to the user
[/LIST]

Whats good is that I can configure apache on the server to setup VirtualHost entries to point to the /virtual/<username>/var/www folder and make use of suPHP's chroot function to lock web hits in there. It would require a few symlinks added to the COW to get working.

It also means pretty much any other program can be configured to make use of the virtual dir and be jailed in as long as it has the capability of chrooting.

The special shell would be SUID root, and would basically perform the following: -
[LIST=1]
[*]Check if /virtual/<logged_in_USER> exists. If not, bail
[*]Chroot into /virtual/<logged_in_USER>, and set privs to <logged_in_USER>
[/LIST]

So if user fred executes it, it will chroot into /virtual/fred as the user fred.

[SIZE=3]**Conclusion**[/SIZE]
As far as I can tell this should be reasonably light on resources. If the autofs timeout is set high enough, then only the first person hitting a website will get a slight hiccup in speed as everything is mounted. Bind mounts are reasonably light on the system as well though I can't yet find documentation that gives its impact.

I wonder then how such a server with 10,000 users would go.


I think you have a solid plan, however I agree with bodhi.zazen on this, I really think virtualization would give you exactly the separation you are looking for. It also gives you a much better platform for recovery if a user whom you are hosting hoses their system. You can simply restore from a saved-state. 

I personally recommend Xen, although the other solutions are good as well.

---

### Post by Lars Noodén on 2011-09-23
However, virtualization will be a big loss in performance, even on a good system.  The jail seems to be the way to go.  I'd explore AppArmor more than Chroot.

---

### Post by Dangertux on 2011-09-23
> **Lars Noodén said:**
> However, virtualization will be a big loss in performance, even on a good system.  The jail seems to be the way to go.  I'd explore AppArmor more than Chroot.


Also a very good point. It depends on the hardware, and what tradeoffs the OP is willing to make, there will never be a perfect solution. :-/

---

### Post by bodhi.zazen on 2011-09-23
> **Lars Noodén said:**
> However, virtualization will be a big loss in performance, even on a good system.  The jail seems to be the way to go.  I'd explore AppArmor more than Chroot.

The performance hit on OpenVZ is trivial at best, same with LXC.

The trade off is that you get much better isolation / security then a chroot. Not to mention ease of configuring / maintaining.

Other then something like BSD jails, chroot has fallen out of favor.

---

### Post by Lars Noodén on 2011-09-23
There were also some good discussions on one of the BSD lists a few years ago summing up that for whatever other conveniences there might be with virtualization, security is not one of them.  Theo deRaadt was quite outspoken about it and the discussion made a lot of the news sites.

I'm underwhelmed by the performance of virtualization.  On a 2 GHz Intel Core i7 with 4GB of RAM, it is slow enough to not be enjoyable to use, it is quite sluggish with very long pauses.  It also consumes power like anything.  Without virtualization, the battery lasts 4 - 5 hours.  With virtualization running, even if it's not doing much, it is down to 1-2 hours.  

1:1 or worse hardware (virtualized or bare metal) to service is the Windows way of doing things.  I like Systrace much better than AppArmor, but 1) AppArmor is what Ubuntu is stuck with and 2) it is starting to catch up in features.  The strength of Linux systems is that multiple services can co-exist, unlike on Windows systems, and not need virtualization or separate hardware.

---

### Post by Dangertux on 2011-09-23
> **Lars Noodén said:**
> There were also some good discussions on one of the BSD lists a few years ago summing up that for whatever other conveniences there might be with virtualization, security is not one of them.  Theo deRaadt was quite outspoken about it and the discussion made a lot of the news sites.

I'm underwhelmed by the performance of virtualization.  On a 2 GHz Intel Core i7 with 4GB of RAM, it is slow enough to not be enjoyable to use, it is quite sluggish with very long pauses.  It also consumes power like anything.  Without virtualization, the battery lasts 4 - 5 hours.  With virtualization running, even if it's not doing much, it is down to 1-2 hours.  

1:1 or worse hardware (virtualized or bare metal) to service is the Windows way of doing things.  I like Systrace much better than AppArmor, but 1) AppArmor is what Ubuntu is stuck with and 2) it is starting to catch up in features.  The strength of Linux systems is that multiple services can co-exist, unlike on Windows systems, and not need virtualization or separate hardware.

Again good points , but I don't really agree 100%. Virtualization security while it may not be as mature has improved over the past few years. Yes, you can escape a guest operating system and make calls directly to the hypervisor, this has been known for a while. That being said how is that any different  from breaking out of a chroot? The methodologies exist for escaping either.

I also don't necessarily think that Ubuntu is STUCK with apparmor, the kernel has support for SELinux as well. Which in this case might be a more suitable alternative than Apparmor. Either would be useful though.

As far as Virtualization performance goes we're talking in a production environment with the right hardware. In this particular case a laptop with an i7 and 4GB of ram would not be on the table.

---

### Post by Lars Noodén on 2011-09-23
> **Dangertux said:**
> As far as Virtualization performance goes we're talking in a production environment with the right hardware. In this particular case a laptop with an i7 and 4GB of ram would not be on the table.

Don't try it on a P4 with 512 MB then, even as a proof of concept.  ;)

---

### Post by Dangertux on 2011-09-23
> **Lars Noodén said:**
> Don't try it on a P4 with 512 MB then, even as a proof of concept.  ;)

Well, yeah -- I think it's pretty obvious if the OP is talking about 10,000+ users that a P4 with 512 MB would be fairly out of the question. The resources consumed by the webserver alone at that point would make the whole point null and void. Even with the use of a reverse caching proxy to alleviate some of it.

On a side note I have used Xen in a test environment with  a P4 with 1024 MB of ram running Ubuntu 10.04 with the Xen hypervisor and paravirt guests  and it was useable, granted the only user was me, and there were only 2 guest OS'es. (centOS and debian stable). That being said, as stated above that is a sub-optimal configuration for what the OP is looking to do.

---

### Post by bodhi.zazen on 2011-09-23
> **Lars Noodén said:**
> There were also some good discussions on one of the BSD lists a few years ago summing up that for whatever other conveniences there might be with virtualization, security is not one of them.  Theo deRaadt was quite outspoken about it and the discussion made a lot of the news sites.

Depends on what you mean exactly by security. In this thread we are talking virtualization vs a chroot and isolating users and services from the host OS. With that in mind, virtualization is much more secure then a chroot.

> I'm underwhelmed by the performance of virtualization.  On a 2 GHz Intel Core i7 with 4GB of RAM, it is slow enough to not be enjoyable to use, it is quite sluggish with very long pauses.  It also consumes power like anything.  Without virtualization, the battery lasts 4 - 5 hours.  With virtualization running, even if it's not doing much, it is down to 1-2 hours.

1:1 or worse hardware (virtualized or bare metal) to service is the Windows way of doing things.  I like Systrace much better than AppArmor, but 1) AppArmor is what Ubuntu is stuck with and 2) it is starting to catch up in features.  The strength of Linux systems is that multiple services can co-exist, unlike on Windows systems, and not need virtualization or separate hardware.

"virtualization" is a broad category, and not all virtualization solutions are equal.

You really need to back up your broad claims with some benchmarks

[http://www.phoronix.com/scan.php?page=article&item=623&num=1](http://www.phoronix.com/scan.php?page=article&item=623&num=1)

With openvz it is rare to see more then a 3 % performance hit.

OpenVZ benchmarks are here:

[http://wiki.openvz.org/Performance](http://wiki.openvz.org/Performance)

As you can see, they are on par with Xen which in turn is very close to bare metal.

Sounds as if you have something grossly misconfigured.

---

### Post by bundabrg on 2011-09-23
Thanks for all your replies. Some of my comments are below: -

> 
Sounds as if you should take a look at LXC or Openvz or Xen or Vserver. 


Agreed and I've used Xen, OpenVZ and KVM to good success. However if you look at a standard hosting box running something like Plesk, Cpanel or Hsphere, there are a LOTS of domains hosted for reasonably simple websites.
It would overkill to implement a separate VM for each and every one of them. I'll do a bit more research with OpenVZ but I'm unsure if it will allow one to share a 'jail' amongst many users. I've always thought you have to maintain individual sets of files for every VM.

Xen/KVM or any other full virtualiszation method would never scale well to many users. Rather I'd use this if I were creating a VPS for a user where they can then host their own 10,000 users inside this VPS. It really depends on if I'm targetting the VPS market or the hosting market.

> 
That being said how is that any different from breaking out of a chroot?


With respect, I've never heard of any way of escaping a chroot unless someone is root inside that chroot, and then its trivial. If the entire jail is mounted nosuid and all calls into that chroot immediatly drop privlidges to that of the user, then that removes the ability to gain root through local exploits. The only way that may be possible is perhaps if /proc allowed access to the memory of another process outside the chroot.


I should mention the hardware. It would be standard server hosting. So something like a Dual Xeon with 32Gb of memory would be standard.

I should also mention that the whole reason I'm researching this is that I'm in the middle of developing a very pluggable multi-server clustered hosting control panel similar to cpanel/plesk and would like to use every trick in the book to make it as secure as I possibly can. Its quite likely that it would run within a VPS itself (IE, if someone buys one or more VPS from a one or more service providers and installs the control panel inside) so that eliminates all virtualization options as the hit to virtualize twice would be significant, though it will also be for real bare metal servers as well.

---

### Post by Dangertux on 2011-09-23
> **bundabrg said:**
> Thanks for all your replies. Some of my comments are below: -



Agreed and I've used Xen, OpenVZ and KVM to good success. However if you look at a standard hosting box running something like Plesk, Cpanel or Hsphere, there are a LOTS of domains hosted for reasonably simple websites.
It would overkill to implement a separate VM for each and every one of them. I'll do a bit more research with OpenVZ but I'm unsure if it will allow one to share a 'jail' amongst many users. I've always thought you have to maintain individual sets of files for every VM.

Xen/KVM or any other full virtualization method would never scale well to many users. Rather I'd use this if I were creating a VPS for a user where they can then host their own 10,000 users inside this VPS. It really depends on if I'm targetting the VPS market or the hosting market.



With respect, I've never heard of any way of escaping a chroot unless someone is root inside that chroot, and then its trivial. If the entire jail is mounted nosuid and all calls into that chroot immediatly drop privlidges to that of the user, then that removes the ability to gain root through local exploits. The only way that may be possible is perhaps if /proc allowed access to the memory of another process outside the chroot.


I should mention the hardware. It would be standard server hosting. So something like a Dual Xeon with 32Gb of memory would be standard.

I should also mention that the whole reason I'm researching this is that I'm in the middle of developing a very pluggable multi-server clustered hosting control panel similar to cpanel/plesk and would like to use every trick in the book to make it as secure as I possibly can. Its quite likely that it would run within a VPS itself (IE, if someone buys one or more VPS from a one or more service providers and installs the control panel inside) so that eliminates all virtualization options as the hit to virtualize twice would be significant, though it will also be for real bare metal servers as well.

In relation to breaking out of a chroot ; since this would be designed for a web hosting application the user would likely have access to SOME type of scripting or compiler (ruby, python, perl, c) So it's quite easy to inject code into running processes, some of them will not be running in the chroot (likely the webserver itself, probably the ftp server, and ssh) Thus you can leverage your way out of the chroot environment. Google if you'd like to understand more on breaking out of the chrooted environment, and various POC.

But since virtualization is pretty much out of the question what other option do you have?

---

### Post by bundabrg on 2011-09-23
> **Dangertux said:**
> In relation to breaking out of a chroot ; since this would be designed for a web hosting application the user would likely have access to SOME type of scripting or compiler (ruby, python, perl, c) So it's quite easy to inject code into running processes, some of them will not be running in the chroot (likely the webserver itself, probably the ftp server, and ssh) Thus you can leverage your way out of the chroot environment. Google if you'd like to understand more on breaking out of the chrooted environment, and various POC.

But since virtualization is pretty much out of the question what other option do you have?

With a chroot, apart from the webserver itself, everything runs in the chroot. 

For example, if you use suPHP with chroot enabled, then when someone browsers a vhost that hits a php file, suPHP will chroot into the directory, drop privs to the user, THEN execute the php5-cgi that resides in the chroot.

A trivial patch to suexec can do the same for all other CGI stuff. The idea is to give up using apache modules like modphp (especially since you lose the ability to use mpm-worker then and have to the prefork instead) and to make use of CGI or FastCGI which all can be chrooted and executed inside the chroot environment. This includes Ruby under FastCGI, Pythong under WSGI or FastCGI etc etc...

FTP server would also need to support chrooting and dropping privs to the jailed dir, but of course if its exploitable before that point you get the host system. 

But heres the niggle. If you wanted to go the virtualization route, you would need a dedicated IP per VM to get around this problem anyway (ie, an FTP server per VM, or apache server per VM to get around perhaps an apache exploit). A typical shared webhost will have a few IP's shared amongst many users. For example we have a /22 so that gives us 1024 IP addresses. One would be used for all shared web hosting, with dedicates ones used for SSL websites (one per certificate).


**Edit:** Oddly the email I got for your reply contained a subliminal URL embedded, inside your word 'running': [http://en.wikipedia.org/wiki/TUX_web_server](http://en.wikipedia.org/wiki/TUX_web_server), and yet I don't see the link in the post ;)

---

### Post by Dangertux on 2011-09-23
> **bundabrg said:**
> With a chroot, apart from the webserver itself, everything runs in the chroot. 

For example, if you use suPHP with chroot enabled, then when someone browsers a vhost that hits a php file, suPHP will chroot into the directory, drop privs to the user, THEN execute the php5-cgi that resides in the chroot.

A trivial patch to suexec can do the same for all other CGI stuff. The idea is to give up using apache modules like modphp (especially since you lose the ability to use mpm-worker then and have to the prefork instead) and to make use of CGI or FastCGI which all can be chrooted and executed inside the chroot environment. This includes Ruby under FastCGI, Pythong under WSGI or FastCGI etc etc...

FTP server would also need to support chrooting and dropping privs to the jailed dir, but of course if its exploitable before that point you get the host system. 

But heres the niggle. If you wanted to go the virtualization route, you would need a dedicated IP per VM to get around this problem anyway (ie, an FTP server per VM, or apache server per VM to get around perhaps an apache exploit). A typical shared webhost will have a few IP's shared amongst many users. For example we have a /22 so that gives us 1024 IP addresses. One would be used for all shared web hosting, with dedicates ones used for SSL websites (one per certificate).


**Edit:** Oddly the email I got for your reply contained a subliminal URL embedded, inside your word 'running': [http://en.wikipedia.org/wiki/TUX_web_server](http://en.wikipedia.org/wiki/TUX_web_server), and yet I don't see the link in the post ;)

LOL @ TUX web server, I had copy/pasted it to someone else and accidentally ctrl+v'ed it in this reply, and edited it out after I realized :-P

Now back OT : I understand the obvious issue with IP address limitations and virtualization, but as you stated above anyway that is not really an option.

Now back onto the topic of chroot since that is the path you are basically set on , or at least for lack of a better alternative seem to be. Ultimately your plan is pretty solid, not perfect but solid. For every day use , sure it's great. However,  the chroot model even in the method you described implemented is not impervious. For instance suphp has had multiple vulnerabilities over the past few years, usually stemming from code injection causing a race condition (in the very process you described above). suexec is right there with it. As far as chrooting services like ftp, so long as the service is running as the UID of the user in question (it would be or it would not be chrooted) then code is injectable, if a vulnerability exists it could be leveraged to escape the chroot. A perfect example of this can be seen in proftpd 1.3.2a. 

Now, how likely is any of this? Not really,  but the measures you take in building this system depend on your level of tolerance , how much of a risk can you take? Suffice it to say you have to determine that for yourself, nobody can do it for you. What is your level of risk? What is the company hosting? These are all questions that should be answered.

I hope that is helpful, there is no 100% solution as I stated before in this thread, however what you have is a very good start.

---

### Post by bundabrg on 2011-09-26
Thanks once again for your replies DangerTux. I appreciate your view on it. As a network security person myself its easy to get too close to an idea and its good to have more eyes on it. The main reason I post online is to see if I've completely missed the point or haven't considered another angle (I don't have time to test every possible software combination). Id much rather use a proven tested method than have to cover that groundwork myself.

I think for the case where if I run a site with thousands of web sites, or a dev site where I run something like Launchpad with thousands of users, having each user individually automatically jailed from each other using this method seems to be the best scaling method I can see. It would not be possible to give every user individual IP's or individual apache/ssh's and will still run within a virtual environment itself.

---

