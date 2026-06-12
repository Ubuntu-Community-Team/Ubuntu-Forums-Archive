---
title: "Simple Authentication"
date: 2010-07-05
forum: Server Platforms
---

### Post by inyoka on 2010-07-05
I am currently trying to setup central authentication from a network of primarily Ubuntu systems.  I would like shared folders as well and so far I am settling on TurnKey Linux running Samba.  

My main question is why is simple centralised network authentication so hard on Linux.  I don't even care about Windows compatibilty. [Has anyone read the OpenLDAP Server guide? ]("https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html")

I know M$'s AD is expensive, and Linux is free.  However we don't even have a half decent configuration tool without installing a web-server and using something like Webmin or eBox.  Novell had the LDAPCfgTool which hasn't seen an update since 2007, and even that was not user friendly.

Is it really that hard to have slapd installed with a default configuration that allows for basic authentication (at the login screen), and have the Ubuntu user-management tools use an LDAP backend instead?

I must admit I am not overly knowledgeable in this area.  But looking at the time and effect being put in to things like Landscape and Eucalyptus, it just annoyed me a little that we have made no headway in making this easier.  This issue is a constant thorn in my side and I am sure somebody else must thing this as well?  

If there is an easy way to do this please let me know.

---

### Post by HermanAB on 2010-07-05
It is only difficult if you are hell bent on using Ubuntu desktop as a server.

The Mandriva small business server, Suse and Redhat Enterprise can all do what you want at the click of a mouse. With Ubuntu, you are on your own.

---

### Post by inyoka on 2010-07-05
> **HermanAB said:**
> It is only difficult if you are hell bent on using Ubuntu desktop as a server.

The Mandriva small business server, Suse and Redhat Enterprise can all do what you want at the click of a mouse. With Ubuntu, you are on your own.

I gave up on SUSE and Fedora years ago as they kept 'shipping' with floors that either prevented installation, or updates.  The Enterprise versions you refer to have costs attached and I work for a charity with a very tight budget.

Also I have now discovered gadmin which help's a bit (but is far from being considered good).  Perhaps once I have the servers up and running I could great a simple python tool to do the jobs I want.

However I admit I was being a little narrow minded and will spend the evening checking out CentOS and other free distro's to see whats available.

---

### Post by HermanAB on 2010-07-05
Yup, Ubuntu is my favourite desktop system, but for work purposes I always use Scientific Linux, which is the same idea as CentOS, but with an even free-er license.  The corporate lawyers really like Scientific.  

Mandriva and Suse also have good server support and lots of little server wizards, but their licensing is similar to Red Hat, so these cost money, but if your time is also worth money, then it makes sense.

So, if you use the enterprise type distros, then you have many little server wizards that can configure anything without much effort.  While, if you shoehorn Ubuntu into that role, then you got to deal with the downside.

---

### Post by elvinatom on 2010-07-05
> **inyoka said:**
> I am currently trying to setup central authentication from a network of primarily Ubuntu systems.  I would like shared folders as well and so far I am settling on TurnKey Linux running Samba.  

My main question is why is simple centralised network authentication so hard on Linux.  I don't even care about Windows compatibilty. [Has anyone read the OpenLDAP Server guide? ]("https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html")

I know M$'s AD is expensive, and Linux is free.  However we don't even have a half decent configuration tool without installing a web-server and using something like Webmin or eBox.  Novell had the LDAPCfgTool which hasn't seen an update since 2007, and even that was not user friendly.

Is it really that hard to have slapd installed with a default configuration that allows for basic authentication (at the login screen), and have the Ubuntu user-management tools use an LDAP backend instead?

I must admit I am not overly knowledgeable in this area.  But looking at the time and effect being put in to things like Landscape and Eucalyptus, it just annoyed me a little that we have made no headway in making this easier.  This issue is a constant thorn in my side and I am sure somebody else must thing this as well?  

If there is an easy way to do this please let me know.

You said it yourself, get more knowledge and then it won't be a problem anymore - no matter what distro you use.  IMO it's a good idea to keep all those "click and it works" style graphic tools out.  They make the OS unnecessarily large and slow and the user isn't really helped if he/she doesn't understand what's going on "under the hood".

---

### Post by inyoka on 2010-07-05
Getting more knowledge elvinatom is time consuming.  I am the only person who knows enough about linux and open-source in this company to do this.  It would be nice not to have to learn every facet of every service I setup on the server.  Especially as many of the configuration files are convoluted, and express a technical abstraction of the service, which is sometimes barely related to the reality of the application.  
Even with the daemons I do fully understand, sometimes it would be nice to know that someone intelligent has setup some sensible defaults just to get things off the ground (I think Ubuntu does a good job of this in general).  It is possible to spend your entire life learning about some of these programs.
I think in general it would be safe to say that Mr Shuttleworth if nobody else envisages a future which is a little simpler.  Perhaps thats why Canonical seems to be supporting Turnkey Linux

---

### Post by elvinatom on 2010-07-06
> **inyoka said:**
> Getting more knowledge elvinatom is time consuming.  I am the only person who knows enough about linux and open-source in this company to do this.  It would be nice not to have to learn every facet of every service I setup on the server.  Especially as many of the configuration files are convoluted, and express a technical abstraction of the service, which is sometimes barely related to the reality of the application.  
Even with the daemons I do fully understand, sometimes it would be nice to know that someone intelligent has setup some sensible defaults just to get things off the ground (I think Ubuntu does a good job of this in general).  It is possible to spend your entire life learning about some of these programs.
I think in general it would be safe to say that Mr Shuttleworth if nobody else envisages a future which is a little simpler.  Perhaps thats why Canonical seems to be supporting Turnkey Linux

I feel your pain, but that won't change the fact that there's no easy peasy directory service available - not reven under windows.  ldap is already greatly simplified (in contrast to it's predecessor), but it still is a nasty thing to deal with.  I was in pretty much the same position as you're in right now and finally got something to work with it, but later decited to not use it, because I would not have been able to maintain it.  My thought on it is: when you can handle all the tricky things (eg. directory, postfix) you become a powerful admin and that will effect your career.  Even though I gave up on it, I suggest you be smart, bite the bullet and learn it.

And also:  You will find that there's little help for you out there - the reason is that most admins or power users have no clue how to do it.  And the few that are familiar with it probably prefer to spend their time helping others with (forgive me) "real" problems.

---

### Post by inyoka on 2010-07-07
Actually M$ have Active Directory and its very easy.  (and only costs $5 from my local mall, if I had no principles).

LDAP being complicated to install actually is a "real" problem.  Abstruse software configuration leads to poorly configured servers.
----
For anyone who came to this thread looking for information which is a little more useful I would strongly suggest taking a look at [[COLOR="Blue"]_Turnkey Linux_[/COLOR]]("http://www.turnkeylinux.org/").  They provide Ubuntu based appliances which can be deployed on to bare metal or a cloud infrastructure.

They are still running 8.04 based systems, but have the base 10.04 system in testing, and appliances come pre-configured for basic operations.  They even allow you to access the command line through a browser (any browser, I used chrome and firefox), and have a webmin based configuration panel.  

Because each appliance is specialized for a specific task they also have sensible firewall settings by default, which are easy to change if you want to disable one of the many configuration options available.  They are the perfect headless army for getting services up and running quickly.

So far I have only used the Samba appliance for a week, but have been pleasantly surprised by the forethought given to the initial setups.  Also the staff seem very approachable, and in many respects they fill the gaps left by Ubuntu.  Because they are basically just pre-configured ubuntu installs the learning curve is minimal.

Sorry if that sounds a little like an advert, but they do seem to have everything I was looking for.  Also I have not heard anyone mention them before, perhaps because I didn't fully realise what I was looking for until I found it.  Hope this helps someone out.

---

