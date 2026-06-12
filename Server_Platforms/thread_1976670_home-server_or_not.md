---
title: "home-server or not"
date: 2012-05-09
forum: Server Platforms
---

### Post by roffemuffe on 2012-05-09
I want to set up a personal mail-server, sharing-center and possibly a website too (IPv6, of course).

I do not have much experience in servers, so my question is basically if I should go for a Ubuntu server version or a desktop version? Does the system require any modifications to my home-network?
I will use a spare computer (rather old), that will only run this one system.

How much work/skill is it in setting up for access from Windows 7 machines (I know! I'm sorry for the bad language!) and does it require any special software on the Windows 7 machines? Can I set it up on my own?

---

### Post by darkod on 2012-05-09
Well, if you wanna learn, you're looking into some fun.

You never mentioned what is your other option, if you decide not to do it. Buy a hosting plan with a provider? That would give you website and email, but you still need your data center at home.

Whether to start with the desktop or server version is a valid question. You can install any type of server roles on the desktop too, and having a GUI it might be easier for a start.

But that would also mean it will eat up more resources, especially on an older machine. The command line is not too complicated, and you should be able to pick up the main parts fast.

I would say give the server version a shot.

Another thing you will need to investigate even before making this decision: Do you know if your provider allows running services at home? Some providers are blocking customers running webservers and mailservers at home. I think you need to check if ports 80, 443 (for SSL) and 25 are open.
I believe this website can help you investigate if the ports are open from your location: [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

If the ISP is blocking you there is no way to run them at home.

When you say access from win7 machines, I guess you mean to a data stored on the server. It's easy, and no software is needed on the workstations. The setup will depend on whether you want open access to all data, or users have access only to their folders and they can't peek into someones folder.

There will be no modifications to your home network, although you might wanna make some planning, like is your network 100% gigabit for faster access and transfer, etc. Buy a gigabit switch for example, etc. Don't forget to set up the server with fixed ip. If your router/dhcp server assigns the whole range from .1 to .254 you will probably want to make it smaller so that you can use some IPs as fixed.

---

### Post by 2F4U on 2012-05-09
+1 for the home server

Given that you enjoy learning new things this is a great opportunity.

---

### Post by Garinil on 2012-05-09
> **roffemuffe said:**
> I want to set up a personal mail-server, sharing-center and possibly a website too (IPv6, of course).

I do not have much experience in servers, so my question is basically if I should go for a Ubuntu server version or a desktop version? Does the system require any modifications to my home-network?
I will use a spare computer (rather old), that will only run this one system.

How much work/skill is it in setting up for access from Windows 7 machines (I know! I'm sorry for the bad language!) and does it require any special software on the Windows 7 machines? Can I set it up on my own?
I personally just started learning, and I have one machine running the server edition, and another running just the desktop. It is very easy to learn the basics of the command line, not to mention that when you install the SERVER edition, and install the following, packages, that it is very easy to manage your server from any computer. 

LAMP server
Open SSH

Now, I personally have done no work yet with the mail server, so for that someone else would have to advise. I am all for someone learning about the linux system as I am doing. 

Regards,
Garinil

---

### Post by SlugSlug on 2012-05-09
am all for home servers :)

I run web, email, and game server

---

### Post by CharlesA on 2012-05-09
> **2F4U said:**
> +1 for the home server

Given that you enjoy learning new things this is a great opportunity.
+1. I have mine set up as VM host among other things.

---

### Post by kgatan on 2012-05-09
Theres alot of guides out there so its not that difficult to do everything from command line in ubuntu.
There are however a bunch of options to make it easier.

* Install a basic ubuntu server and a web gui such as Webmin for configuration of services as mail, web, shares etc.

* There is also options as "Zentya"l which is based on ubuntu. its a package(?) that also uses a web gui for all configurations.

---

### Post by CharlesA on 2012-05-09
> **kgatan said:**
> Theres alot of guides out there so its not that difficult to do everything from command line in ubuntu.
There are however a bunch of options to make it easier.

* Install a basic ubuntu server and a web gui such as Webmin for configuration of services as mail, web, shares etc.

* There is also options as "Zentya"l which is based on ubuntu. its a package(?) that also uses a web gui for all configurations.
Yep.

I used to use Webmin, then I decided to just manage the server via CLI only.

---

### Post by Bushflyr on 2012-05-10
Do eeet mon! I'm having a bunch of fun with it. Just started from basically zero a couple months ago and am learning tons. Be prepared to deal with a lot of little bugs, and walk away when you feel the urge to put your head through the monitor. Then enjoy the feeling of satisfaction when you finally get them solved.

For a server I'd go CLI only. GUI is just another layer to potentially screw up and once you get into it it's almost easier to just type a command rather than try and chase through a bunch of menus.

---

### Post by lisati on 2012-05-10
> **2F4U said:**
> +1 for the home server

Given that you enjoy learning new things this is a great opportunity.

+1 from me too.

At various stages over the last couple of years, I've had a GUI on my own home server. Now that I'm a little bit more confident managing it, I have the "server" edition installed without a GUI, and sometimes find "webmin" a useful tool for browser-based management tasks.

---

