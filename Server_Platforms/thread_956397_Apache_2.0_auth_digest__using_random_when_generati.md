---
title: "Apache 2.0 auth_digest  using random when generating secret for authentication"
date: 2008-10-23
forum: Server Platforms
---

### Post by Buntoholic on 2008-10-23
[COLOR="Navy"]Hi all,

I'm using Ubuntu 8.04 and running the included Apache 2.0

I'm hosting quite a few websites on this server so it's more than annoying when I'm restarting Apache and it just hangs for a minute or so with the following mesasge in error.log
[I]
[Thu Oct 23 11:07:58 2008] [notice] Digest: generating secret for digest authentication ...[/I]

And then after a while :
[I]
[Thu Oct 23 11:09:29 2008] [notice] Digest: done[/I]

and the server starts.


I suspect that "auth_digest" is using /dev/random instead of /dev/urandom and is waiting for the system to have enough entropy to continue.

But with a live production system, I realy can't justify any downtime when adding or modifying a site config file.

Can anyone please suggest a solution for this problem ?[/COLOR]

---

### Post by Nostalos on 2008-10-23
I wish I could give you a simple solution but I can't.  And its not a problem with Ubuntu itself as I have the same problem with Ubuntu, Gentoo and Centos.   I run a pair of HA servers running over 100 sites a couple of which run auth_digest.   The problem lies with Apache which by default uses /dev/random.  The solution I had to implement on my servers was to custom compile Apache to use /dev/urandom instead.

---

### Post by heywouter on 2009-09-02
I had the same problem running a Virtualbox headless server. 
I'm running ubuntu 8 , apache 2 and php5 with mod_auth_digest enabled
The problem is that apache uses /dev/random by default and with a headless server the entropy gets quite low, that is what causes the apache to "hang" up on the digest secret generation.

As /dev/random "builds" entropy by using HW interupts (I don't entirely understand the process) and halt when the pool is empty . /dev/urandom is able to do this even if  the pool is empty 

I found a post here : [http://www.chrissearle.org/blog/technical/increase_entropy_26_kernel_linux_box](http://www.chrissearle.org/blog/technical/increase_entropy_26_kernel_linux_box)  that explains it nicely.

The solution is a simple hack of rng-tools:


[LIST=1]
[*]apt-get install rng-tools
[*]Edit /etc/default/rng-tools
[*]Set HRNGDEVICE=/dev/urandom
[*]Run /etc/init.d/rng-tools start
[/LIST]
This should push up your entropy above 2000 and your digest issue should be a thing of the past.

---

