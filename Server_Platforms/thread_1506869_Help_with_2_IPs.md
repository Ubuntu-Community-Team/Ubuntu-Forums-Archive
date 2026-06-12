---
title: "Help with 2 IPs"
date: 2010-06-10
forum: Server Platforms
---

### Post by paryguy on 2010-06-10
Ok I'm pretty new at this admin stuff so bare with me....

I have one server from Media Temple and 2 IP address.

I need to have multiple domains and one in particular needs to be on XAMPP, the rest I'd like to have on a different version of Apache.  

So using two domains as an example, domain1 and domain2:

What steps would I take to get things setup?  
Do I setup XAMPP or LAMP first?  I have the XAMPP domain setup now but if I install LAMP, how will my server know what page to serve up?  They both use different conf files.  

Lost yet?  I am.

I just don't know what to do first.  I have XAMPP on there now but I'll wipe it clean and start over.  Any help is much appreciated.

---

### Post by clrg on 2010-06-11
Dude, seriously. Do you expect someone to write a tutorial for you? Do a little RTFM. Buy a book. Read manuals and tutorials. There's tons of material on the web.

I'm sorry if this sounds rude. Try to do it on your own. If you encounter a problem which google doesn't solve, I'd be delighted to help you.

---

### Post by paryguy on 2010-06-11
I should have been more specific.  I cant figure out which conf file takes precident or acts as the master file.   Xampp and Lamp both use different ones in different locations.  I dont need a tutorial or someone to hold my hand but quite frankly those out there on virtual host setup are pretty thin.

Does that narrorw it down?

---

### Post by clrg on 2010-06-11
A little. 

Check out the manpages of the daemons in question, then scroll to the very bottom (Shift+G), there should be references to the config files. If I remember correctly, Apache uses /etc/apache2/http(d).conf or something similiar as its main config file (but there could be a lot of includes...).

---

### Post by madverb on 2010-06-11
Umm.. make changes in one and see what happens.

---

### Post by paryguy on 2010-06-11
I installed both and couldn't run to instances of Apache as they were conflicting.  I'm beginning to think I might as well just wipe it clean, install LAMP and anything XAMPP has on top of it.

I've looked at the httpd.conf files but I couldn't figure out how to tell the server which ones to look at first.  I'm not too sure what you meant by man pages but will research a little more to see what I find.

---

### Post by koenn on 2010-06-11
You might first want to explain why you think you need both LAMP and XAMPP, as they're practiaclly the same thing, AFAIK

And why you think the 2 IPs are so important that they make up your thread title, while they're hardly mentioned in your post.

---

### Post by paryguy on 2010-06-11
> **koenn said:**
> You might first want to explain why you think you need both LAMP and XAMPP, as they're practiaclly the same thing, AFAIK

And why you think the 2 IPs are so important that they make up your thread title, while they're hardly mentioned in your post.

 Thanks for the response koenn.  First of all, I understand they're one in the same but I'm not that experienced in all of this.  My goal is to have a CDN server running Kaltura CE which I was able to do with an install of XAMPP.  The problem was I couldn't find an email setup for it or couldn't find a detailed enough explanation of how to set one up.  So I figured I could install EHCP which not only has a nice control panel for server stuff but also installs a mail server.

I posted a separate thread asking how to go about running the two and someoen mentioned you'd need 2 IP's so I got another one.  But they're on the same box and the two Apache's conflict.  I guess if I could just get a mail server up on XAMPP I'd be fine and wouldn't need the extra address.  

The control panel would be nice too but I'm not sure anymore it's worth a completely different setup.  I tried to install LAMP and then add all the components XAMPP had but that did something to my MySQL so now I'm back to square one.

---

### Post by koenn on 2010-06-11
Assuming all of that stuff just requires Apache, MySQl, PHP and maybe Perl, I think the way to handle this is to set up those (possibly as a LAMP task in Ubuntu Server), then add your applications, and any mail server. That shouldn't be too hard. Then, set up the apps. If they require separate sites, you configure virtual hosts in apache. You shouldn't need two IP addresses for that. 

I have zero experience with CDN or Kaltura so i don't know what they require exactly, but if they run on top of LAMP / XAMPP, it's usually just a case of creating a database and setting some default values. Most applications come with a setup script that helps you do that. 

If you need more help, you're probably gonna have to post concrete questions, with concrete info (the commands you ran, the modifications you made to files, the values you put in, the feedback you got from, e.g. the error messages, etc. 
And hope someone on these forums has done CDN and Kaltura before :)

---

### Post by paryguy on 2010-06-11
Thanks.  To be specific:

Kaltura CE is the community edition of Kaltura video platform.
[http://www.kaltura.org/](http://www.kaltura.org/)

CDN is just a content delivery network..I thinks that's what it stands for.  I guess the biggest problem was that Kaltura recommends installing it's server with XAMPP I guess because the more robust graphics and video libraries?  Who knows, anyways, I followed those instructions got it all running, then realized I needed to setup the rest of my site that relies on a mail server.  

I'm new to terminal so I was looking for the only way I knew what was using a control panel that doesnt' exist with XAMPP and I don't want to make one.

What I thought I could do was essentially split my server one running two separate web services.

I guess the solution is to sack-up and just throw XAMPP on there and learn how to setup a mailserver.  The last thing I wanted to do what become a server admin but the first thing I needed was a media server....a FREE one ;)

---

### Post by lisati on 2010-06-11
I haven't looked into doing it with 2 IPs on the same machine, but it is possible to tell apache to direct incoming requests for different domain names to different web sites sitting on the same machine. 

On my copy of apache, [http://spaminator.boldlygoingnowhere.org/](http://spaminator.boldlygoingnowhere.org/) shows one set of web pages, and [http://lisati.homelinux.com](http://lisati.homelinux.com) shows another. I control what goes where through apache's "sites-available" configuration.

---

