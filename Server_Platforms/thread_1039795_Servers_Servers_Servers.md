---
title: "Servers? Servers? Servers?"
date: 2009-01-14
forum: Server Platforms
---

### Post by Mystic001 on 2009-01-14
Hi All,

Hope someone can give me a quick and simple solution to my request.

I am a Windows user, looking to migrate over to Linux.

I have just installed Ubuntu 8.1.0 and am playing around trying to get a feel for it.
I am looking at putting together a temporary P-4 server, that will eventually be upgraded to a dedicated server when I have the funds. Right now I have limited resources, and the main website will be a health and wellness website, with no income.
I would like to host 2 web servers and an email server.

After 2 days of searching web page after web page, as well as a few hours looking through this Forum.
So far, the only thing I have gathered is that I should use a host os instead of a Virtual host.

Trying to figure out how to put all these Servers together(Virtual vs software,)to work has been very confusing.

For my host, I read that it is best not to use a Virtual host.
Do I use Ubuntu Desktop or Server?

Since I want 2 web servers, I will create Virtual Machines.
Do I use a Virtual Machine or Virtual Server?
I can't afford to purchase esx Server.  
Which would be best: Xen, Ubuntu's own, esxi, or another?

For the host systems...
Apache is the predominantly favored.
If I use it, I need to add additional modules to handle Forums, Blogs, email, polls.
I was looking at Drupal, as I want Forums hosted on the site.
It includes Forums, Blogs, and email services, polls.

In short...
host system... Desktop or Server?
Create Virtual machines using Virtual or Virtual Server?
Which Virtual software?
Guest system... Desktop or Server?
Apache server and modules or Drupal?

Backing up the Virtual machine for the health site will be very important.  As well security must be very good.

What would be the easiest and most efficient way to go?

I will continue to search the Forums for info, and I have found some, but any feedback would be greatly appreciated.

---

### Post by Fireblazer on 2009-01-14
Hey,

I'm just curios but, what were you reasons for choosing Virtual OS as opposed to Virtual Host?

~ Fireblazer

---

### Post by HermanAB on 2009-01-15
Uhmmm... Note that Ubuntu is NOT the easiest Linux on the block.  It is kinda intermediate.  If you have no Linux experience and no time to waste learning the hard way, then I suggest that you start with Mandriva or Suse.  With either of those systems, you can set everything you need up with a few clicks of a mouse.  Ubuntu simply doesn't yet have the advanced wizards that the older Linux distros have.

Setting up a Mandriva server with Apache, Email and more, is easier than doing the same with Windows 2003 server.

Cheers,

Herman

---

### Post by Mystic001 on 2009-01-15
While going through the Forums, I came across a thread, where one knowledgeable person it was better not to use a virtual host.
If  a virtual machine crashes, you lose a virtual machine.
If  a virtual host crashes, you lose all your machines.

Mystic001

---

### Post by mbeach on 2009-01-15
My two cents:
I suspect you want to run two websites, not run two separate virtual machines each hosting a web site.

Apache allows you to have whats called "virtual hosts" in that you have apache running only once, but is able to serve up web sites to multiple domain names.  For example, the same server and apache service can respond to requests for [www.healthandwellnesssite.com](www.healthandwellnesssite.com) and [www.myotherpersonalsite.com](www.myotherpersonalsite.com).

If you are just starting out, I'd personally recommend you start with a basic install of the server version on your computer.  I'd suggest you stay off the whole virtual machine thing only until you understand and get a feeling for it all.  By all means having virtual machines is the way to go eventually, but it sounds like it might be a "walk before you run" type situation.

If you want to setup two websites, its really not that hard to configure.  Many people will suggest you use 'webmin', but I've never had the urge to try it.  I'd learn where the configuration files are, how to edit them and go from there.

As for hosting an email server, depending on the number of users you have, I'd seriously consider letting Google handle that for you.  Google hosted domains ([www.google.com/a](www.google.com/a)) has an email feature that allows you to brand Gmail for your particular domain name, providing you up to a 100 users for free (I think that's the number).  That way, you don't have to deal with many headaches, you get a decent administrative setup, and an interface that many people are already familar with.  Again, that's my opinion and there are others which may want to point out that you may as well host your website there as well, but when it comes to the websites, I think hosting Apache yourself is the better decision.

Once you have your Server running, and you are ready to setup your two websites, post back here for assistance in the server forums.  There are several guides out there, but bear in mind that many are not specifically for Ubuntu, and will suggest you edit files which the Ubuntu folks do not use, or have alternatives for.  

If I'm completely off base, and you really do need two complete virtual machines for your two websites for some reason, than feel free to disregard.

Search for posts from windependance on the whole VMWare setup.  And I had thought that the Esx server was free now?  I could be wrong.

---

### Post by linux_tech on 2009-01-15
Hardware resource consumption is different.  For example, if you are choosing between vmware server and vmware workstation, server requires much more RAM than workstation.  Server is really only worthwhile if you need to a higher #of virtual machines.

---

### Post by Cracauer on 2009-01-15
The OP is completely confused.

Even if he believes the almost certainly bogus advice not to use the name-based virtualhost feature in apache, he doesn't have to go to actual virtual machines with separate OS installs.

If he doesn't want to use name-bases virtualhosts he needs two IP addresses, and he needs two IP addresses whether he uses one Apache bound to two addresses and do address-based virtualhosts.

Even if you use VMware for whatever reason you'll need a second IP address.

Classic case of (lack of) RTFM.

---

