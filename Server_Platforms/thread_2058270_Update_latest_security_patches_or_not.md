---
title: "Update latest security patches or not?"
date: 2012-09-15
forum: Server Platforms
---

### Post by ericmachine on 2012-09-15
Hi everyone,

I heard few people talking about this (vendors in specific). But I am not sure, better I ask ubuntu forum directly.

This is quite a noob question.

Logical wise, I should not simply update security patches (comes from Windows env) as it will break my applications running (alfresco). But if I don't patch security patches, there may be an hole on my server and be more vulnerable for attacks.

So if you are at my scenario, what will you do?

My concern here is that if I update a security patch, will it really break my application?

I noticed when i login into ubuntu, it will show me ...

XX updates
XX security updates

I just want to update the security updates and not the normal updates. 

I tried this:-

apt-get update
apt-get upgrade or apt-get dist-upgrade

but often i believe it will install both normal and security updates.

what should i do? Thanks.

---

### Post by Bachstelze on 2012-09-15
You should install all updates of the OS you use, period. If you want to have less frequent updates, then Ubuntu is not the right OS for you, and you should use something like Debian stable.

---

### Post by thnewguy on 2012-09-15
If you are concerned about your application breaking, I recommend setting up a virtual machine which has the exact same configuration, packages and application(s) installed. When updated packages ar eavailable, install them in your virtual machine. Then reboot the virtual machine and see if everything still works. If nothing broke, then download the same updates for the real server. However, if your virtual machine stops working then you know one of the updates broke something and you can look into finding a solution in your virtual environment ebfore applying updates to the main server.

Check out VirtualBox (available in the repositories) for an easy way to set up a virtual server.

---

### Post by SeijiSensei on 2012-09-15
I didn't see any obvious settings in the man page for apt-get or apt.conf, but a quick Google search brought me to [this page](http://serverfault.com/questions/270260/how-do-you-use-apt-get-to-only-install-critical-security-updates-on-ubuntu).  It makes the common sense suggestion of commenting out all the entries in /etc/apt/sources.list except the ones for the security repositories.  Then just run apt-get upgrade each night via cron.

You should always install security patches as soon as they are available.  Other updates are optional.

---

### Post by Bachstelze on 2012-09-16
> **SeijiSensei said:**
>  Other updates are optional.

No, they are not. A bug can be very severe without being a security bug.

---

### Post by vexorian on 2012-09-16
^ But unless the bug is actually affecting you in a noticeable way then there is no need to update.


> **ericmachine said:**
> Hi everyone,

I heard few people talking about this (vendors in specific). But I am not sure, better I ask ubuntu forum directly.

This is quite a noob question.

Logical wise, I should not simply update security patches (comes from Windows env) as it will break my applications running (alfresco). But if I don't patch security patches, there may be an hole on my server and be more vulnerable for attacks.

So if you are at my scenario, what will you do?

My concern here is that if I update a security patch, will it really break my application?

I noticed when i login into ubuntu, it will show me ...

XX updates
XX security updates

I just want to update the security updates and not the normal updates. 

I tried this:-

apt-get update
apt-get upgrade or apt-get dist-upgrade

but often i believe it will install both normal and security updates.

what should i do? Thanks.
In ubuntu, they make a very relevant effort not to include anything else besides the security/bug fixes in the packages they are releasing. New features and tweaks usually are not packaged in the updates (you would need an OS upgrade or PPA to get them). 

Also, we got a "proposed" repository which some users test before allowing an update into the wild for mainstream users.

Regressions are thus very rare. Of course, they are not impossible. In case of no confidence, set up a test version of your server (either in VM or in another computer) running the updated versions and whatever the server runs and test out if something failed before installing.

---

### Post by ericmachine on 2012-09-17
Noted and thanks.

It's good idea to have a vm setup for testing. Will let my guys know :)

---

