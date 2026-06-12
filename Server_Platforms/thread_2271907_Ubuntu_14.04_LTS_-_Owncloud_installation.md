---
title: "Ubuntu 14.04 LTS - Owncloud installation"
date: 2015-04-02
forum: Server Platforms
---

### Post by aaron27 on 2015-04-02
I am running owncloud on a 14.04 LTS server. so far everything is working.

however we want to be able to access externally - which means we need to add a re-direct in Apache , which is probably fairly easy except I have never used Ubuntu in depth before - any advice on this would be greatly recieved. Please see this post for history of my install - [https://forum.owncloud.org/viewtopic.php?f=31&t=27514](https://forum.owncloud.org/viewtopic.php?f=31&t=27514)

---

### Post by nerdtron on 2015-04-02
> 
however we want to be able to access externally

Careful on the external part as we need to have security measure here. But first, is your server IP accessible externally?

---

### Post by TheFu on 2015-04-03
If security matters, only let Owncloud be accessible with a full VPN. Maintaining the security on a LAMP webapp is non-trivial over time. 

If you don't care much about security, use HTTPS. It might be good enough. Just depends on whether you can trust the DNS and CAs where clients connect from or not.

With a full VPN, you just open the VPN port and your remote systems get added to the internal LAN IP range, so no need to change anything related to owncloud if you go that way.  OpenVPN is the recommended VPN solution for Linux.

I see from the other link that you are completely new to Linux and probably haven't made the thought transition needed to be successful. [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) has some directed learning. Go in order to get the most relevant information and background to avoid 
too much frustration.  There are also Ubuntu Desktop and Server guides - along with some reputable websites with how-tos.  Be certain to learn file and directory permissions for users/groups. These are the cornerstone of all security for *nix systems.

Skimmed the OC posts ... you got some good advice over there and have made much more progress than I would have expected from someone new to *nix. Nice job.

What you want to [https://oc.domain.com](https://oc.domain.com) --> [https://oc.domain.com/owncloud](https://oc.domain.com/owncloud) ... correct?  
[https://www.digitalocean.com/community/tutorials/how-to-create-temporary-and-permanent-redirects-with-apache-and-nginx](https://www.digitalocean.com/community/tutorials/how-to-create-temporary-and-permanent-redirects-with-apache-and-nginx) seems to have directions.  Or the apache docs: [https://httpd.apache.org/docs/2.4/rewrite/remapping.html](https://httpd.apache.org/docs/2.4/rewrite/remapping.html)

We stopped using apache here in 2008, so I can't provide exact answers. I think you'll want mod-rewrite.  Don't forget that apache is designed to support hundreds of virtual hosts on a single system. It is unlikely you want to touch the pre-existing config files. Rather, you should create your own in the sites-available/ directory. Copy the "default" file and modify it for your new OC stuff. Then create a link from sites-available/ to sites-enabled/ ... either with the **ln -s** command or I think apache has a command that does it.  There is always more than 1 way to accomplish things. Or you can use a reverse proxy as the redirector (and perhaps the SSL termination point) - pound, nginx, apache can all do this job. In your current setup, apache is probably what I'd try.

Lastly - for apache stuff, you can ask here, but apache.org has extremely thorough documentation. Just be certain that you know the version of apache you are running and only look at that documentation. Things have changed in the last 18 months, so google may NOT be your friend for anything new in apache configs.

---

