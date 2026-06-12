---
title: "What's with Rackspace's Pro-RedHat Policy?"
date: 2009-02-09
forum: Server Platforms
---

### Post by SuperMike on 2009-02-09
I'm a PHP developer in the USA and my partner is in the UK. When he went shopping for a dedicated server in the UK, RackSpace was who could give him the best deal for the money and who was a major player in the dedicated space. But guess what they told him when I asked for Ubuntu Server 8.04 as the OS?!??

"We can't get good support for that like we can with RH. We'll have to charge you extra."

I tell you, guys, that's got me hopping mad. Sure, I know RH and Suse, I did plenty of sysop work on those, but they're always like two critical package versions behind than Ubuntu Server 8.04. If I am forced to have to install stuff on RH by source and scratch in order to at least get PHP5.2.1 or higher, or PostgreSQL 8.3 or higher, I literally will throw a radiator through a plate glass window. I cannot describe a more error-prone, voo doo process than doing custom compiles, and especially for PHP and PostgreSQL and the chain of dependencies with that.

Canonical -- are you guys on this? Can you get on this please?

---

### Post by SuperMike on 2009-02-09
I'm waiting on their callback. Hopefully Rackspace has left virtualization turned on that ships with RHEL5. If so, then I can install Ubuntu Server 8.04 and hopefully I won't have a performance penalty that is too great.

Check out this very short video from RH. It's 1 minute. It shows how to fire up a VM super easy.

[http://www.redhat.com/promo/streamline/Virtualization/?intcmp=70160000000HbewAAC#demo](http://www.redhat.com/promo/streamline/Virtualization/?intcmp=70160000000HbewAAC#demo)

If that link won't go through, then keep refreshing the redhat.com home page (at least in the month of Feb 2009) until it says "virtualize without vmware". Then click it.

But all I really need is to ensure I'm working with PHP 5.2.4 or better and PostgreSQL 8.3 or better.

We do plan to run with virtualization later, but I guess if I'm backed into a corner of having to do a custom compile, I'll run with VM stuff early. The reason we were considering virtualization was because it makes it easier for me to expand and use multiple web nodes on multiple physical servers. I can configure one VM, clone it multiple times, deploy it quickly on 4 physical servers, and even have a standby VM that I can engage in case the main one dies.

---

### Post by SuperMike on 2009-02-09
Okay, they contacted me back. There was some confusion. Basically they told my partner that RH is what everyone is trained on, and that Ubuntu is supported and free, but we would be on our own as far as tech support. I'll post more details as I can get straight to the heart of this matter. I'm trying to see from rackspace what exactly they mean here.

---

