---
title: "Help Me With Setting Up a Server (Many Questions)"
date: 2009-05-08
forum: Server Platforms
---

### Post by Linux_Noobie on 2009-05-08
Ok i set up a Ubuntu 8.04 Server Going Basically by the settings on the Perfect Web Server Tuturial For Ubuntu 8.04, Http,Sql, and the whatnot are all working fine ok? But i have a few questions.


(A) I have a domain name i want to have go to my Ubuntu Server and Have it all work out right. My IP works from the outside, and putting my name (cpe.blahblahblah.ne.rr.com) into proxy works fine.
But ,**[SIZE="4"]My Quetion is how can i get it to work with my GoDaddy Domain??? [/SIZE]**

(B) Im Used to having a Control Panel on Web Hosting and would muchy like to have a control panel on my Linux Box Thats Kinda Like cPanel. I already have webmin but thats not the right thing. [SIZE="4"]**Whats a web Panel that is Easy to set up and Compatible with my Server?**[/SIZE]

(C) Email, [SIZE="4"]**Will It be able to Work? Ie [email]admin@domain.com[/email]?**[/SIZE]

(D) **[SIZE="4"]How Can i set it up so that my Road runner IP is consistent? [/SIZE]**It is dynamic and is changing periodically so that would mess things up. *I have a Motorola SBG 900 Router by the Way.*

(E) **_How can i have it set up so my server always has 192.168.0.[B][U]*19*_** and not something else? [/U][/B] Thats the internal ip i have set up for forwarding,and whatnot

Ok ubuntu Community - Sorry for all the Questions but i was never able to get this all right. And figure this is the best way to get it all awnsered. 

:guitar:

---

### Post by TwiceOver on 2009-05-08
A.  You need to point your DNS information to your IP address

B.  Not sure what else you want.  Webmin does everything I have ever seen a control panel do.

C.  Yes.  Assuming you set up a mail server and questions A and D are resolved.

D.  You would need to contact your ISP to have them set up a static IP.  This isn't something you can do on your own.  If this is not possible, look into "Dynamic DNS" service like dyndns.org

E.  You need to remove the package dhcp3-client and set up a static IP for your internal address.  There are plenty of guides out there.

---

### Post by Linux_Noobie on 2009-05-08
A. What DNS info? (Should i just replace NS1.Nameserver With my IP?
B. Im talking more of a hosting control panel kinda thing. (You know like cpanel, im about to check out vhcs.
C. K Then.
D. It looks like dyndns wants me to have a subdomain. How can i use it for a real domain? 
E. Ie so Replace localhost or whatever with 2045.5303 Or whatever??

---

### Post by Pnuts on 2009-05-08
(A) You will have to point your domain name to your external IP address. This is done in the dns settings in your domains account with godaddy.

(B) no idea on this one, sorry

(C) As long as you setup email for your domain (either you or someone like godaddy hosting it) yes. If your hosting it, you will need to configure a web server also on your linux box.

(D) Either contact your ISP and ask them if you can have a static IP address or look into a service like dyndns.com if you have a dhcp address.

(E) look at your routers settings, normally your internal dhcp range is only 100 addresses and starts at 100, so 100-200 is dhcp. Set your server to use a static IP of 192.168.0.x that isnt in the dhcp range of the router. see here for setting a manual address: [http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

---

### Post by Linux_Noobie on 2009-05-08
Ok i got it working on my server (Kinda)5361web.info

How can i get it to work on email and whatnot?

---

### Post by cariboo on 2009-05-09
@v_frankenstein_osg

You woud be better off starting a new thread, instead of hijacking this one. I'll start a new thread for you.

---

