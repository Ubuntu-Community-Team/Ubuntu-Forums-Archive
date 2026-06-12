---
title: "Virtualbox LAMP?"
date: 2010-03-22
forum: Virtualisation
---

### Post by mech7 on 2010-03-22
I am on a windows machine.. but mostly do programming for linux in PHP.. now I would like to setup a virtualbox LAMP server.. and it works ok already except for multiple site setup.

Normally we would have a development server with a dns and a wildcard for subdomains to easily setup multiple sites... kinda similiar to this: [http://postpostmodern.com/instructional/a-smarter-mamp/](http://postpostmodern.com/instructional/a-smarter-mamp/)

But how can I get the same setup for ubuntu server in virtualbox? Is it possible to have a seperate dns only for the LAMP? and still be connected to the internet?

---

### Post by HermanAB on 2010-03-23
As far as networking issueas are converned, using virtual machines is exactly the same as using multiple physical machines.  

So you got to decide whether you want to use DHCP with addresses assigned from a pool, or static IP addresses with DNS.

This is not really a LAMP issue at all - it is simply a networking issue that you got to figure out.

---

### Post by mech7 on 2010-03-24
Yes you are right.. actually it is both.. I connect to more then one network cause I am on a laptop...

But if I use the vhost adapter the I cannot access the internet anymore from the guest..

And I still need to connect to the DNS from the other server where I have no control over whatsoever to go on inet :(

---

### Post by codfather on 2010-03-25
Having read that chaps post on his setup , it would appear perfectly possible for you to do this in one of two ways.

Firstly you could lose Windows as your base OS, and then you would be in exactly the same state as that post, and you could follow the instructions almost to the letter as Ubuntu has bind you can install.

Secondly, you could set your VM to include bind and configure it that way, but the windows networking will get in the way , and it would depend on which subnets you have the host and the guests configured on.

hth

Nick

---

### Post by mech7 on 2010-03-29
Hmmm i know switching OS would be the easy way out... but I only use Linux as server and windows as development enviroment.

But how to get it working in virtualbox without interfering too much with my host connection ? And not necessary to keep it always on?

> **codfather said:**
> Having read that chaps post on his setup , it would appear perfectly possible for you to do this in one of two ways.

Firstly you could lose Windows as your base OS, and then you would be in exactly the same state as that post, and you could follow the instructions almost to the letter as Ubuntu has bind you can install.

Secondly, you could set your VM to include bind and configure it that way, but the windows networking will get in the way , and it would depend on which subnets you have the host and the guests configured on.

hth

Nick

---

