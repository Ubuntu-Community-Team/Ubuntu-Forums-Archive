---
title: "User creation necessary"
date: 2014-02-10
forum: Server Platforms
---

### Post by Youri_van_Dijk on 2014-02-10
Hey Guys I'm following a guide by digitalocean to setup my own vps
([https://www.digitalocean.com/community/articles/initial-server-setup-with-ubuntu-12-04](https://www.digitalocean.com/community/articles/initial-server-setup-with-ubuntu-12-04))

The guide mentions the creation of a new user, is this necessary for my installation? Or does the account generated during the installation have the required privileges?

---

### Post by tfrue on 2014-02-10
I actually disabled root login through SSH on my server, for obvious security reasons, but you could SSH into your server as the user you created an use *sudo* to perform *root* task. So no, you don't have to create a new user nor login as root to set up VPS. Also, in that tutorial, you did not set up VPS and when you edit the SSH config file you are actually disabling *root* login which is good.

Now, are you wanting to create a VPS, or VPN?

OpenVPN for 12.04:
[https://help.ubuntu.com/12.04/serverguide/openvpn.html](https://help.ubuntu.com/12.04/serverguide/openvpn.html)

You would need to look at Apache for setting up a domain with a root directory for the / of your website, but Apache uses "virtual" servers.

Here is a link to setting up a VPS straight from the Ubuntu Server Guide:
[https://help.ubuntu.com/12.04/serverguide/httpd.html](https://help.ubuntu.com/12.04/serverguide/httpd.html)

Good luck,
Chris

---

### Post by Youri_van_Dijk on 2014-02-11
Thnx, I was hoping simply using the account created while installing would be sufficient. Security wise leaving the root account alone seems safer? 
I'm trying to use the VPS to host several small (mostly Wordpress) websites. Somehow I've got my mind on nginx as many mention that to be the fastest option, but first times are frustrating and I can't get it to work via those tutorials :D I'm using another vps provider than digitalocean which might be the issue.

---

### Post by tfrue on 2014-02-11
It depends on what the VPS is using on the back end whether that be Apache, or ngnx. It seems to me that most VPS have WoodPress or other blogging platforms, and many other tools, available without having to install them. For a long time, I was going to use domain.com to get a domain name and use their Linux Web Hosting services to host a blog platform, so you could check them out and decide if the services they offer will meet your standards.

[http://www.domain.com/domaincom/hosting/](http://www.domain.com/domaincom/hosting/)

 It's not safer to use root, as it's easier to make unwanted changes that are, well, unwanted. So it is always recommended to use the less privileged account rather than root, but either way will get the job done.

---

### Post by Youri_van_Dijk on 2014-02-11
Well I'd prefer my hosting in the Netherlands so I'm using a provider here. They supply an 'empty' vps (as far as I can tell as it's my first try ever) where you can install Ubuntu, centos etc for free, but require a €5 premium for plesk or control panel. I think that with those services it would be easy to install WordPress, but that's half the fun anyway right? 

I'll be using the generated account in Ubuntu then to install a Lemp stack as it seems it has root privileges. I will not be unlocking the root user as it will not be necessary, right?

Thanks for your help

---

### Post by tfrue on 2014-02-11
Yea, that's true! Ha!

When you install Ubuntu, it will create a non privileged user that can use *sudo*, so you don't have to unlock the root user. I actually read the last post incorrectly, I thought you said you wanted to use root but you said it's safer to leave it alone which is correct.

If you use Ubuntu Server, you can install many services like: LAMP, SSH, OpenVPN, TomCat, etc, during initial installation so I recommend trying that.

Good luck,
Chris

---

