---
title: "Firefox can't find the server at www.spyderwebs.selfip.com."
date: 2008-11-14
forum: Server Platforms
---

### Post by Lakeside5 on 2008-11-14
Over a week and still a blank page, instead of my website :( I will try to be simple/brief, so I don`t scare anyone off lol. I will supply more info as it is asked, and maybe I can solve this a step at a time.  server: Hardy Heron server edition LTD 8.0.4. Installed by: me, a noob. Router: linksys, settings: Port Randge Forwarding: (not sure I should do this either) www(application) start-end: 80-80, IP address: 192.168.1.100   UpnP Forwarding: FTP, 21, TCP
HTTP  80 TCP.  HostName/Domain Name (this is where I`m confused, may be the problem) Host: blank, not sure what to put. Domain: SpydrWebs.selfip.com. (From my accouont at DynDns, so I could have a name instead of an ip,with my Dynamic ip, I picked `selfip.com` from a list, and added `SpydrWebs` as name.  I also named my site `SpyderWebs` as the site name, on the Joomla install). I installed the Joomla CMS, unzipped packaged into a folder (`Joomla`) in www (var/www) My absoute path should be var/www/Joomla? At localhost in the webbrowser, I see the Joomla folder, and also a test.html file I put in there, to test the server. It works, I see the test file, AND the Joomla website, in fact I can sign in as admin, go into Joomla, do things, and see results on front end. So I ftp`d a test file with fireFtp called  test.html.  I did not create any directory or anythihg  `up there`, just uploaded the file.  But I can`t see it at www/SpydrWebs.selfip.com (which is what I figured to put there) I get: Firefox can't find the server at [www.sasswebs.selfip.com](www.sasswebs.selfip.com).
Can someone please help me sort this mystery? thanks :)

---

### Post by Philio on 2008-11-14
If everything works locally then it could be a couple of things:

1. Check your firewall allows connections to port 80.
2. Check you ISP allows port 80.
3. Check the dynamic DNS is setup correctly, the subdomains you've listed don't resolve currently which could be the issue.

---

### Post by Lakeside5 on 2008-11-14
Thanks so much for helping me unravel this! I started with your suggestion number two..which is where I should have started days ago, I mean, I did not check with my ISP about details, I just knew that they gave free space. Turns out they do not support running scripts (like php, etc.) it is just for a very basic page (hey, the mainpage is index.html :) ) and all that stuff I did with Dyndns and my router etc...In order to use their free space, I have to use THEIR info in the address bar (something like `myspace(sitename).greenbaytel.net(isp)boyscout***(my username for the isp).I decided to put Joomla on hold, and just see if my Ubuntu online server worked anyway.  I made a sample index.html file, and uploaded. I tried putting it in  var/www, and just at /,  but no matter where it was, even though it worked at localhost, I could not connect with my server, even though localhost displayed the page. I am not sure what to put in my router now, for `host` and `domain` on setup page. thanks again.

---

