---
title: "When I installed server, they never asked for the FQDN"
date: 2010-11-14
forum: Server Platforms
---

### Post by fmuise on 2010-11-14
Where do I go about setting this up?

---

### Post by James78 on 2010-11-14
```
sudo -s
echo "fully.qualified.domain" > /etc/hostname
/etc/init.d/hostname restart
nano /etc/hosts

*Add entry at top of file like...*
192.168.1.135 fully fully.qualified.domain

exit
```

I'm not completely sure, but I think Ubuntu sets it up a different way, where you have:
192.168.1.125 fully fully.qualified.domain

In your /etc/hosts, and:
fully

In your /etc/hostname. This way caused the hostname to be fully, and when called with the --fqdn option, it was fully.qualified.domain, however this caused problems for my system as certain scripts didn't expect "fully" when they called gethostname(), so I believe the other method I showed you is better because it caused the hostname to be the qualified one no matter what.

---

### Post by redmk2 on 2010-11-14
> **James78 said:**
> 
```
sudo -s
echo "fully.qualified.domain" > /etc/hostname
/etc/init.d/hostname restart

```
Pardon me for just jumping in here, but:  The hostnamee  is NOT the FQDN.  The hostname is the name of the host.  The FQDN is a DNS construct of hostname.domain_name.top_level_domain ie: Myhost.MyDomain.com> 

```

nano /etc/hosts

*Add entry at top of file like...*
192.168.1.135 fully fully.qualified.domain
exit
```
This the place to define the FQND if no DNS is used in a LAN.  But if one is only using a LAN then a FQDN is not needed. :-)> 


I'm not completely sure, but I think Ubuntu sets it up a different way, where you have:
192.168.1.125 fully fully.qualified.domain

In your /etc/hosts, and:
fully

In your /etc/hostname. This way caused the hostname to be fully, and when called with the --fqdn option, it was fully.qualified.domain, however this caused problems for my system as certain scripts didn't expect "fully" when they called gethostname(), so I believe the other method I showed you is better because it caused the hostname to be the qualified one no matter what.

This is why you do not add a FQDN to a hostname definition.

To the OP:  The use of Fully Qualified Domain Names is only used if you are defining a host that is accessible over the Internet.  If this is what you want then you need a registered domain name and a DNS entry defining this and the host in a DNS server somewhere facing the public internet.

---

### Post by James78 on 2010-11-15
> **redmk2 said:**
> Pardon me for just jumping in here, but:  The hostnamee  is NOT the FQDN.  The hostname is the name of the host.  The FQDN is a DNS construct of hostname.domain_name.top_level_domain ie: Myhost.MyDomain.com
I know. But how will you identify what machine it is without a proper name? It's easy and a good solution to just use the full fqdn as the hostname, as it's easy to identify which server it is. Either that or you can shorten it down to fully. If I have a server that's ns1, and I leave it named "Ubuntu", that's not very specific is it! The default hostname is "Ubuntu", so I'll have a bunch of servers, ns1, ns2, with no real way of identifying them. I put that there because it was a good idea, not because that's how to add a FQDN. ;)

> **redmk2 said:**
> This is why you do not add a FQDN to a hostname definition.
.. I was arguing TO add one to the hostname definition.

To the OP: You can add a FQDN to the hostname if you want to or not, mostly it's just for system identification, so it's up to you. There's NO negative problems or drawbacks to putting the FQDN there. So you can just ignore all the useless arguing. ;)

---

### Post by redmk2 on 2010-11-15
> **James78 said:**
> I know. But how will you identify what machine it is without a proper name? 
The servers proper name is its hostname. This can be as a simple name such as: Bill or Bob or Jane.  This is all that is needed on a LAN.  If you need the services of DNS then you add the domain name suffix such as: Jones or Smith.  For DNS to work properly you need a [**_TLD _**]("http://en.wikipedia.org/wiki/Top-level_domain")such as .com or .uk or .org.  Using this we could have the DNS construct of bill.jones.org or  jane.smith.com.  The hostname is just part of the FQDN, but the /etc/hostname is only the hostname.> 
It's easy and a good solution to just use the full fqdn as the hostname, as it's easy to identify which server it is. Either that or you can shorten it down to fully. 
If I have a server that's ns1, and I leave it named "Ubuntu", that's not very specific is it!
I think you are confusing the need for a hostname with the need for a FQDN.  The OS needs to know the correct hostname hostname.  It uses /etc/hostname for the function [**_gethostname()_**]("http://opengroup.org/onlinepubs/007908775/xns/gethostname.html"). The FQDN is used to find a host on the internet  via DNS. > 
The default hostname is "Ubuntu", so I'll have a bunch of servers, ns1, ns2, with no real way of identifying them. 
The hostname does not have to be "Ubuntu".  It can be any name you  wish.  I have have a test domain and the hosts are: **malibu **and **rincon **and **newport**.  They are in a domain called **california **.  This is a test domain so the TLD is **test**.  All of these hosts are in my DNS server and can be pinged by either hostname (i.e. ping malibu) or by FQDN (i.e. ping malibu.california.test).> 

I put that there because it was a good idea, not because that's how to add a FQDN. ;)
It's not a good idea, as evidenced by your troubles noted at the bottom of your original post.> 

.. I was arguing TO add one to the hostname definition.

To the OP: You can add a FQDN to the hostname if you want to or not, mostly it's just for system identification, so it's up to you. There's NO negative problems or drawbacks to putting the FQDN there. So you can just ignore all the useless arguing. ;)
I'll leave it up to the OP to make his or her own decision.  I'm sorry you feel it is useless arguing.  There are correct ways to administer Linux.  I prefer to pass these methods on to those that ask. I'm not, however, telling you how to setup your machines.

---

### Post by redmk2 on 2010-11-15
> **fmuise said:**
> Where do I go about setting this up?

Why do you feel you need a FQDN?  Do you want to rename your server?  Or do you want to identify it via DNS over the Internet?

If you just want to rename your server you can edit (as root) the /etc/hostname file or invoke the command **hostname** as in the example below  ```
sudo hostname <yourhostname>
```

You should also edit the /etc/hosts file to reflect the name change.  if this step is not done, some things do not work (i.e. sudo).  The file looks something like this ```

127.0.0.1       localhost
192.168.1.2     <yourhostname> <yourhostname.domain.tld>

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

This part: *<yourhostname.domain.tld>* is the DNS alias.  This will allow you to use it on a LAN (locally only).  There is an example of this  [**_here_**]("http://www.faqs.org/docs/securing/chap9sec95.html").

---

### Post by James78 on 2010-11-15
> **redmk2 said:**
> I think you are confusing the need for a hostname with the need for a FQDN. The OS needs to know the correct hostname hostname. It uses /etc/hostname for the function gethostname(). The FQDN is used to find a host on the internet via DNS.
I'm not confusing anything. I said that using a proper system identification is key to knowing which server is which server. A proper hostname is needed to understand what server is which server! Name it what you will, a fqdn, or a short name, or anything else, but at the end of the day, you need to name it something useful so you can understand which server it is. I was merely saying that a fqdn in a server hostname is an excellent way to identify the server by.

"I know. **But how will you identify what machine it is without a proper name?** **It's easy and a good solution to just use the full fqdn as the hostname, as it's easy to identify which server it is.** **Either that or you can shorten it down to fully.** If I have a server that's ns1, and I leave it named "Ubuntu", that's not very specific is it! **The default hostname is "Ubuntu"**, so I'll have a bunch of servers, ns1, ns2, with no real way of identifying them. I put that there because it was a good idea, not because that's how to add a FQDN."

Here I stated that leaving the hostname at the default "ubuntu" is obviously a bad idea, and setting up a proper system identification, so you know what system is which system is a good idea. If I'm using one server as nameserver1, it's generally a good idea to either name it ns1 in the hostname, or ns1.domain.com, as I'll know what the server's providing services for.

> **redmk2 said:**
> It's not a good idea, as evidenced by your troubles noted at the bottom of your original post.
You're grossly misinterpreting what I said.

"In your /etc/hostname. This way caused the hostname to be fully, and when called with the --fqdn option, it was fully.qualified.domain, however this caused problems for my system as certain scripts didn't expect "fully" when they called gethostname(), so I believe the other method I showed you is better because it caused the hostname to be the qualified one no matter what."

Here, I say that when certain scripts got the systems hostname, they didn't expect a shortname, and expected a fqdn, so by making the regular hostname a fqdn, the scripts got what they needed and expected, thus supporting that sometimes adding a fqdn to the hostname is a good idea, even if it's just for system identification. Read it closely!

> **redmk2 said:**
> I'm sorry you feel it is useless arguing. There are correct ways to administer Linux. I prefer to pass these methods on to those that ask. I'm not, however, telling you how to setup your machines.
Please, feel free to tell them the correct ways, I have nothing against that. However, I did not ask for you to assume certain things that I did not say in my post. For example, read here:
> **redmk2 said:**
> Pardon me for just jumping in here, but: The hostnamee is NOT the FQDN. The hostname is the name of the host. The FQDN is a DNS construct of hostname.domain_name.top_level_domain ie: Myhost.MyDomain.com
I never said the hostname was a fqdn. Read the post, it clearly never says I assumed that, told them that, or said it was.
And also here:
> **redmk2 said:**
> This is why you do not add a FQDN to a hostname definition.
As stated before, you were grossly misinterpreting what I said.

> **redmk2 said:**
> If you just want to rename your server you can edit (as root) the /etc/hostname file or invoke the command hostname as in the example below
```
sudo hostname <yourhostname>
```
And remember that using the hostname command will only set the hostname temporarily, not permanently (reboot the machine and you'll be back to the regular hostname). To set it permanently, just edit /etc/hostname as he stated right before.

---

### Post by CharlesA on 2010-11-15
I've always set the FQDN in /etc/hosts and the hostname in /etc/hostname

Change what it refects in /etc/hosts and do this:

```
hostname -f
```

Shows you the FQDN.

---

### Post by James78 on 2010-11-15
> **CharlesA said:**
> I've always set the FQDN in /etc/hosts and the hostname in /etc/hostname

Change what it refects in /etc/hosts and do this:

```
hostname -f
```

Shows you the FQDN.
Ya. The only reason I was forced to add the fqdn as a hostname was because the Virtualmin installer script assumes the hostname is a fqdn. Either way though, it hasn't ever hurt me, and even if it was a shortname such as "ns1", it's definitely still good enough for identification. :)

---

### Post by redmk2 on 2010-11-15
> **CharlesA said:**
> I've always set the FQDN in /etc/hosts and the hostname in /etc/hostname

Change what it refects in /etc/hosts and do this:

```
hostname -f
```

Shows you the FQDN.

The **hostname -f (or hostname --long or hostname --fqdn) **invocation is returned by the resolver (DNS or /etc/hosts file), Not from the /etc/hostname file.  See the man pages on this.

The point I was trying to make is that you do NOT use a FQDN in the /etc/hostname file.

Edit:  I would not compound an error on one program with another in the OS.  Fix the problem in Virtual min or better yet; Learn to do without Virtualmin.

---

### Post by CharlesA on 2010-11-15
> **redmk2 said:**
> The **hostname -f (or hostname --long or hostname --fqdn) **invocation is returned by the resolver (DNS or /etc/hosts file), Not from the /etc/hostname file.  See the man pages on this.

I didn't say that it returned the FQD from /etc/hostname. Where did you get that from?

---

### Post by redmk2 on 2010-11-15
> **CharlesA said:**
> I didn't say that it returned the FQD from /etc/hostname. Where did you get that from?

I never said you stated that.  I added it.  Touchy touchy there CharlesA.

The issue is it appears that James78 feels this is so, as evidenced by ```
sudo -s
echo "fully.qualified.domain" > /etc/hostname
/etc/init.d/hostname restart
```

Subsequently he has described it as a hack. The hack is wrong.  The root problem should be cured with Virtualmin.

---

