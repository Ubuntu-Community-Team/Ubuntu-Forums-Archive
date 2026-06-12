---
title: "Hosting/running a Personal Website with Ubuntu Server"
date: 2015-05-15
forum: Server Platforms
---

### Post by branau on 2015-05-15
Hey everyone, I've been doing some research about this, and I'm a little overwhelmed with all of the options that are available, so I'm looking for some advice. I want to take an old computer, replace its OS with Ubuntu Server, and use it to host and run my own personal website to use as a sort of interactive resume and portfolio of my work. I've been learning Python/Django to make it some sort of web app type thing and I'm also hoping to use the server to back-up and/or easily transfer important files, pictures, videos, etc between computers. From what I've read, I wouldn't necessarily need a database to store any information, since I don't plan on collecting any information with this website (or would I?), although I would like to play around with a database to get some experience with it. As for hosting the website and getting it onto the internet for the world to see, I'd just have to set up the server with the DNS settings and then link a domain name to my IP address right? And if so, does it take up a lot of bandwidth to host a website?

---

### Post by Lars Noodén on 2015-05-15
> **William_Brawner said:**
> Hey everyone, I've been doing some research about this, and I'm a little overwhelmed with all of the options that are available, so I'm looking for some advice. I want to take an old computer, replace its OS with Ubuntu Server, and use it to host and run my own personal website to use as a sort of interactive resume and portfolio of my work. I've been learning Python/Django to make it some sort of web app type thing and I'm also hoping to use the server to back-up and/or easily transfer important files, pictures, videos, etc between computers.

For file transfer and backup about all you need is SSH via the package openssh-server.  Then you can run rsync or SFTP. 

> **William_Brawner said:**
>  From what I've read, I wouldn't necessarily need a database to store any information, since I don't plan on collecting any information with this website (or would I?), 


For the portfolio, you can get by with Apache2 and for standardized footers, headings and menus use server-side includes (noexec).  That way you can get by with the security and maintenance advantages of nearly static XHTML.  Though it's a hundred times more work to keep up, it's also popular to install [PHP](http://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design/) to achieve the same end result.  

> **William_Brawner said:**
> although I would like to play around with a database to get some experience with it. As for hosting the website and getting it onto the internet for the world to see, I'd just have to set up the server with the DNS settings and then link a domain name to my IP address right? And if so, does it take up a lot of bandwidth to host a website?

The site only takes up a lot of bandwidth if there are a lot of visitors or you are under heavy DDoS attack.  For the site, all you need is a static IP address and then point your DNS record for your host name to that address.  If you don't have a permanent address, then there are some tricks where you can subscribe to a dynamic DNS service and then point to their DNS record using a CNAME.

---

### Post by TheFu on 2015-05-15
Sounds like you have it all covered. Don't forget to run a firewall and that only specific ports (necessary) need to be opened to the "server."  The server must have a static IP inside your LAN.  Most residential ISPs are on DHCP addressed - those that change. You'll need a dynamic DNS service for this - many routers have built-in support for 5-15 providers, many are free.

How much bandwidth does a website use?  That depends.  If your internet is dialup - then YES it uses a lot of bandwidth.  If your ISP is "broadband" and you don't host anything but normal webpages (no audio, no video) AND the traffic is low (like a personal site would be), then it will probably be fine.

Don't under estimate that your system will be a target for hackers. They may not be out to go YOU, but they are out to get EVERYONE who is easily cracked. Attacks are completely automatic these days for websites like yours and mine.  Just because a website works, that doesn't mean it is secure. Be very careful, since 1 small mistake can be bad, very bad.  Multiple entities are scanning the entire internet every day checking every IP and every port for services. [https://krebsonsecurity.com/2015/05/whos-scanning-your-network-a-everyone/](https://krebsonsecurity.com/2015/05/whos-scanning-your-network-a-everyone/)  It is the wild-west out there.

---

### Post by branau on 2015-05-15
> **Lars Noodén said:**
> For file transfer and backup about all you  need is SSH via the package openssh-server.  Then you can run rsync or  SFTP. 

Would I need this package on the server only or on all computers that I wanted to connect to it?



> **Lars Noodén said:**
> For the portfolio, you can get by with Apache2 and for standardized  footers, headings and menus use server-side includes (noexec).  That way  you can get by with the security and maintenance advantages of nearly  static XHTML.  Though it's a hundred times more work to keep up, it's  also popular to install [PHP]("http://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design/") to achieve the same end result.  

Alright, I plan on using this as a learning experience so that I can broaden my opportunities when looking for work. Which method would you recommend? Or, in other words, which method is used more frequently by business websites or web apps today?


> **Lars Noodén said:**
> The site only takes up a lot of bandwidth if there are a lot of visitors  or you are under heavy DDoS attack.  For the site, all you need is a  static IP address and then point your DNS record for your host name to  that address.  If you don't have a permanent address, then there are  some tricks where you can subscribe to a dynamic DNS service and then  point to their DNS record using a CNAME.

I don't anticipate a ton of traffic to this site since it'll just be used for me to show off my work to potential employers, so hopefully it won't take up a lot of bandwidth. Unfortunately I do have a predisposition to moving a lot (I'm 20 years old and I've lived in 24 houses between 3 countries) so I may need to look into that dynamic DNS service.

Thank you for your help!

> **TheFu said:**
> Sounds like you have it all covered. Don't forget to run a firewall and that only specific ports (necessary) need to be opened to the "server."  The server must have a static IP inside your LAN.  Most residential ISPs are on DHCP addressed - those that change. You'll need a dynamic DNS service for this - many routers have built-in support for 5-15 providers, many are free.

I read that Ubuntu has a built-in firewall, would this be enough or do you know of another one that you would recommend?

> **TheFu said:**
> How much bandwidth does a website use?  That depends.  If your internet is dialup - then YES it uses a lot of bandwidth.  If your ISP is "broadband" and you don't host anything but normal webpages (no audio, no video) AND the traffic is low (like a personal site would be), then it will probably be fine.

Awesome, good to know.

> **TheFu said:**
> Don't under estimate that your system will be a target for hackers. They may not be out to go YOU, but they are out to get EVERYONE who is easily cracked. Attacks are completely automatic these days for websites like yours and mine.  Just because a website works, that doesn't mean it is secure. Be very careful, since 1 small mistake can be bad, very bad.  Multiple entities are scanning the entire internet every day checking every IP and every port for services. [https://krebsonsecurity.com/2015/05/whos-scanning-your-network-a-everyone/](https://krebsonsecurity.com/2015/05/whos-scanning-your-network-a-everyone/)  It is the wild-west out there.

If someone could get access to my website and the server, would that give them access to any other files stored on the server? Or to any other devices and computers connected to my home network? I'll look around for some good security practices and pay very close attention to the coding for the site/server.

Thanks again TheFu!

---

### Post by TheFu on 2015-05-15
> **William_Brawner said:**
> 

I don't anticipate a ton of traffic to this site since it'll just be used for me to show off my work to potential employers, so hopefully it won't take up a lot of bandwidth. Unfortunately I do have a predisposition to moving a lot (I'm 20 years old and I've lived in 24 houses between 3 countries) so I may need to look into that dynamic DNS service.

Thank you for your help!

I read that Ubuntu has a built-in firewall, would this be enough or do you know of another one that you would recommend?

Awesome, good to know.
If someone could get access to my website and the server, would that give them access to any other files stored on the server? Or to any other devices and computers connected to my home network? I'll look around for some good security practices and pay very close attention to the coding for the site/server.

Thanks again TheFu!

You should use ssh/sftp/scp for management and transferring files. Using anything is usually a mistake - for example, plain FTP should have died years ago, but it is still used. It is not secure. Once you setup ssh, many other things are possible.

There is only 1 firewall on Linux. Everything else is just an interface to that kernel function.

Dynamic DNS is probably required for your home website to work. Very few residential ISPs in the world provide a static, public IP to their users. It would be strange if yours did. However, maybe it does seem to work that way there. I dunno.

Security is never absolute.  We may believe we are safe, but 500 "zero day" flaws might be known by different "bad guys" around the world. Those zero-day flaws may allow someone remote to take over your server completely. The hardware, drivers, OS, applications and configuration can each be flawed allowing for hackers to break in. Security is hard. There isn't any checkbox for "Secure" or "No Security" - sorry. ;)  My profile has lots of links for linux security. There is no one way to do it.  I find that people who have never been hacked think security is easy.  I've had 2 servers hacked from the internet over the years. Last time was 2002 and I'm still paranoid.  I expect to be hacked and have a plan to resolve it after the fact. I do not believe my systems cannot be hacked. That would be crazy.

---

### Post by branau on 2015-05-15
> **TheFu said:**
> You should use ssh/sftp/scp for management and transferring files. Using anything is usually a mistake - for example, plain FTP should have died years ago, but it is still used. It is not secure. Once you setup ssh, many other things are possible.

Alright, I'll read up on those protocols then and figure out how to set them up.

> **TheFu said:**
> There is only 1 firewall on Linux. Everything else is just an interface to that kernel function.

I guess that makes it simple then, right? I'll start playing around with that on my Ubuntu Desktop so that I know the ins and outs by the time I get my server set up.

> **TheFu said:**
> Dynamic DNS is probably required for your home website to work. Very few residential ISPs in the world provide a static, public IP to their users. It would be strange if yours did. However, maybe it does seem to work that way there. I dunno.

I'll add this to my list of things to research then. Would this be something for which I'd require assistance from my internet provider? Or would I be able to do everything myself?

> **TheFu said:**
> Security is never absolute.  We may believe we are safe, but 500 "zero day" flaws might be known by different "bad guys" around the world. Those zero-day flaws may allow someone remote to take over your server completely. The hardware, drivers, OS, applications and configuration can each be flawed allowing for hackers to break in. Security is hard. There isn't any checkbox for "Secure" or "No Security" - sorry. ;)  My profile has lots of links for linux security. There is no one way to do it.  I find that people who have never been hacked think security is easy.  I've had 2 servers hacked from the internet over the years. Last time was 2002 and I'm still paranoid.  I expect to be hacked and have a plan to resolve it after the fact. I do not believe my systems cannot be hacked. That would be crazy.

So then, do you know of any good practices for damage containment? And recovering from an attack? I'll definitely read those links from your profile too. I don't understand why anyone would be interested in hacking my personal website but then again I don't understand why people do a lot of the things they do haha so I'll give that a bit more priority. I hadn't really considered security in all of this.

I only plan to use this to sort of teach myself how all of this stuff works, and then if it turns out to be a real hassle to manage it and keep it up and running, I'd probably just pay to have someone else host it like GoDaddy or one of those sites. If I were to do that and then keep the server only for back ups and file sharing over my LAN, would I still be at risk for attacks from outside sources? Or would it be possible to set up a LAN separate from my main connection to the internet to sort of shield it from outside connections?

---

### Post by TheFu on 2015-05-15
openssh-server provides ssh/scp/sftp. On the server-side, just secure that following best practices and call it done.  Do not use a password for authentication over the internet. Always, always, always use keys.

Learning the linux firewall takes time. It is a deceptively complex tool with features beyond open port X, close port Y. You can learn enough to be sufficient in a few hours. Becoming an expert can take years.

Standard security practices. Versioned backups and practicing restores to bare hardware are the start and end of security.  It is all the things we do in the middle that cause complexity.

Like I said before - they aren't out to get you (specifically). They are out to get everyone and use automatic tools. There are many reasons for this.  Learning to secure a server can take years. It depends on how many openings your software stack contains.  Hosting companies generally do a poor job at security.  Last week 100K wordpress sites where hacked.  That happens week after week.  You can review some posts and links on these forums for what hackers do with Linux servers after they gain control.  They can become spam servers, C&C for botnets, or soldiers in DoS attacks around world and on you LAN.  Computer security is a rabbit hole that you might never return from, if that is your calling.

You are asking good questions. Do some research to find answers.

---

### Post by branau on 2015-05-15
> **TheFu said:**
> openssh-server provides ssh/scp/sftp. On the server-side, just secure that following best practices and call it done.  Do not use a password for authentication over the internet. Always, always, always use keys.

Alright, I'll remember that. A quick Google search yielded [this tutorial](http://support.suso.com/supki/SSH_Tutorial_for_Linux) on how to use that. I skimmed it and it looks to me like it goes over the basics, at least enough to get me started. How does it look it to you?

[QUOTE=TheFu;13285988]Learning the linux firewall takes time. It is a deceptively complex tool with features beyond open port X, close port Y. You can learn enough to be sufficient in a few hours. Becoming an expert can take years.

So, is this something that should be high on my priority list? Or should I just go through the couple of hours or however long I take to become proficient in the firewall usage and then just keep myself up to date on current practices and new tools?

Also, I found [this documentation](https://help.ubuntu.com/community/UFW) about the Ubuntu firewall. Does this look good to you or should I keep looking?

> **TheFu said:**
> Standard security practices. Versioned backups and practicing restores to bare hardware are the start and end of security.  It is all the things we do in the middle that cause complexity.

Then I'd want to make periodic back-ups of my server and all the files on it, and then store that back-up on an external drive so that in case of an attack and loss of data, I'd be able to recover it or revert the server back to a previous state, right? And I'm a bit confused on your point about restoring to bare hardware. Would that be something I do in case of an attack? To completely remove any traces of said attack and then use a back-up to restore the server to a previously safe point?

> **TheFu said:**
> Like I said before - they aren't out to get you (specifically). They are out to get everyone and use automatic tools. There are many reasons for this.  Learning to secure a server can take years. It depends on how many openings your software stack contains.  Hosting companies generally do a poor job at security.  Last week 100K wordpress sites where hacked.  That happens week after week.  You can review some posts and links on these forums for what hackers do with Linux servers after they gain control.  They can become spam servers, C&C for botnets, or soldiers in DoS attacks around world and on you LAN.  Computer security is a rabbit hole that you might never return from, if that is your calling.

Hmmm, correct me if I'm wrong, but it would be safe, then, to manage my own website from the looks of things. And by hosting a website through a hosting company, I'd be at risk for having my work and projects stolen, unless they were all open-source.

> **TheFu said:**
> You are asking good questions. Do some research to find answers.

I appreciate your answers as well. I have a bad tendency to drop things that get boring but usually your answers end up giving me more questions, which gives me more to read and investigate. Thank you for that! I could really use a challenge to keep me going. 

In my research for questions about setting up a network for my home that doesn't use a connection to the internet, I've come across a couple of things. At first I thought an ad hoc network would be good for me but that would only work if I was the only one sending things to the server, which probably won't be the case. Ethernet cables wouldn't work either because they would be inefficient and wouldn't be able to connect to mobile devices like my phone or tablet. The only thing that really makes sense from what I've seen would be to have a second router that was only used for file transfer between my devices at home, and that way that connection would only be at risk from people within the given radius of the connection (like in my yard/house). That seems kind of pointless if I'm going to have a router connected to all of those devices and the internet though, unless I did decide to take my server to a local-only set up. 

As for the server, I came across something called Server Virtualization, which seems to be my answer about people gaining access to all of my other files not related to the web page. I still need to look into that but worst case scenario, I could always get a second server for the back-ups and run that on a local-only network using a second router to be absolutely safe. Having a second network that's within my own house only and is protected by SSH keys would be pretty much inaccessible from any outside attack on my internet-connected network, right?

---

### Post by TheFu on 2015-05-15
> absolutely safe

There is no such thing.  Computer security is about mitigating issues and limiting attack vectors.  If a computer is on a network, there are many attack vectors.

[http://blog.jdpfu.com/tag/security](http://blog.jdpfu.com/tag/security) has articles on my blog about "security", assuming I set the tag correctly. Probably more than you want.

---

### Post by branau on 2015-05-15
I think it's time I set a permanent bookmark to your blog, maybe even add it as one of my homepages haha. Or, better yet, I'll write a program to automatically retrieve and email myself the content of your newest posts. 

I'll read through all of those security articles and any questions I fail to answer on my own, I'll bring back here!

Thanks again, Fu

---

### Post by Lars Noodén on 2015-05-16
> **William_Brawner said:**
> Would I need this package on the server only or on all computers that I wanted to connect to it?


The package OpenSSH-server is only needed on the machine you connect to.  Everything else except that one, strange, other OS has the client support built in.  In Ubuntu, even the file manager has SFTP support, but unfortunately not with keys, though FileZilla has that.  I'd like to also emphasize what TheFu said about keys.  

> **William_Brawner said:**
> 
Alright, I plan on using this as a learning experience so that I can broaden my opportunities when looking for work. Which method would you recommend? Or, in other words, which method is used more frequently by business websites or web apps today?


My 2¢ is that if you only need standardized headings, footers and navigation menus, I would follow the KISS principle and stick with SSI instead (but noexec).  Most business don't need more but decide to increase their maintenance costs drastically by doing otherwise.  Many people smoke, many use [PHP](http://whydoesitsuck.com/why-does-php-suck/).  The sad part is that a lot of otherwise interesting web applications have been built on top of it.  But if you use them you have to have someone more or less available for the life of the site to deal with maintenance/security problems in both the web application and the scripting language itself.  I guess Perl worked too well there.  If you're looking for work then having[PHP](https://farm8.staticflickr.com/7226/7095238893_5000f6e57d_c.jpg) on your resume will help, but then you will risk getting a job where there may be exposure to or cleanup after PHP.  :****b  It's also possible to show off and do both by means of separate vhosts.  My guess, based on similar work in the distant past, is that they don't care as long as it looks good, and the easy way to do that would be CSS3 in external style sheets.

> **William_Brawner said:**
> 
I don't anticipate a ton of traffic to this site since it'll just be used for me to show off my work to potential employers, so hopefully it won't take up a lot of bandwidth. Unfortunately I do have a predisposition to moving a lot (I'm 20 years old and I've lived in 24 houses between 3 countries) so I may need to look into that dynamic DNS service.

Thank you for your help!

If you move a lot, it might be worth it to rent a cheap VPS and host your portfolio there.  That way when you move there won't be any down time during moves.  Some places can take days or weeks to actually connect.

---

### Post by TheFu on 2015-05-16
> **William_Brawner said:**
> I think it's time I set a permanent bookmark to your blog, maybe even add it as one of my homepages haha. Or, better yet, I'll write a program to automatically retrieve and email myself the content of your newest posts. 

I'll read through all of those security articles and any questions I fail to answer on my own, I'll bring back here!

Thanks again, Fu

Or just use an RSS feed reader.

---

### Post by SeijiSensei on 2015-05-16
I'm not sure what kind of "portfolio" you're talking about, but if they are images, there are some well-designed free packages to create a gallery like this: [http://galleryproject.org/](http://galleryproject.org/).  Most projects like that rely on PHP and the MySQL database, so I'd suggest you follow the instructions here to install the "LAMP" package in one fell swoop: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP).  That won't interfere with running scripts written in Python if you choose to continue down that route.

---

