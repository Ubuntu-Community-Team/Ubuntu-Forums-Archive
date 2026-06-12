---
title: "Any ISP techs/operators using Ubuntu Server?"
date: 2008-08-29
forum: Server Platforms
---

### Post by spottedhog on 2008-08-29
I was approached yesterday to possibly help start a Wireless ISP.  Since I have been using Kubuntu on my laptop for a long time, I would like to set up the servers using Ubuntu.

Anyway, as far as what we may need for basics is, LAMP, mail server...  We are not wanting to do web hosting... just host our own domain/website along with providing email service.

Any ISP operators who could throw out some basic requirements?

thanks in advance...

---

### Post by kustomjs on 2008-08-29
you also might want to look into setting a DNS server also because soon as I get more equipment I am going to start a small WISP soon

---

### Post by spottedhog on 2008-08-29
I know about the DNS server, but I guess that is one question.  Should there be 2 DNS servers?  Sounds like a stupid question I guess....   And what kind of server requirements for a DNS?  512mb enough?  hard disk size?

thanks,

ohhhh...  what kind of wireless equipment?

thanks again

---

### Post by kustomjs on 2008-08-29
from what I was understanding you only need one dns server and for dns computer specs I would go with 1GB memory and 120gb hard drive and on the equipment it depends how much you want to spend if you want good service your going to pay alot more then like say for 2.4ghz equipment like linksys etc...

see when I get my service going its only going to be like 10 to 15 people 

so look at: [http://www.wifi-link.com](http://www.wifi-link.com) for some equipment

---

### Post by jimv on 2008-08-29
We really need more information about what exactly you mean when you say you're starting a wireless ISP.  Is this just going to be one hotspot somewhere, or something bigger?  How many people are going to be using your service?  Any pertinent details that you can supply are helpful.

---

### Post by kustomjs on 2008-08-29
also check this site out:[http://www.startawisp.com/content/view/38/80/](http://www.startawisp.com/content/view/38/80/)
[http://www.startawisp.com/content/category/8/82/60/](http://www.startawisp.com/content/category/8/82/60/)

---

### Post by spottedhog on 2008-08-29
We will start with a rural community of 350 houses, lake property...  Then expand from there.  Sooo, 350 customers immediately.

I plan on using the Alvarion BreezeACCESS VL 900 there, since all are within 1/2 mile radius.  Then for other deployments using the BreezeMAX line provided we can get a licensed frequency.  We are looking into the USDA Rural Development Load funds, and will try to use Alvarion for all of that.

There is a telephone switchhouse, AT&T but they refuse to get broadband out there, which is 4 miles from there.  We plan on putting a tower close to the switchhouse, then sending the signal to the community.

Thanks for all your input thus far!!!  some good reading ahead ;)

###########
Not sure if I made this clear...  We are not wanting to be in the web hosting biz....  Just the one website for ourselves.  Places like HostGator do very well ....  :)

---

### Post by windependence on 2008-08-30
Unless you want 350 people barking at you when something goes down (and it will), you need to eliminate ALL single points of failure. The reason everyone and his brother doesn't do this kind of thing is that to do it CORRECTLY, you need quite a bit of equipment. What if your access point dies at 3 am? How fast can you get another one? Think about 350 people calling your cell because their connection is down. 

You will need at minimum:

2 UPS boxes
2 servers
2 firewall boxes commercial or home grown
2 load balancers (can be home grown also)
redundant hard wired line providers (preferably different carriers)T1 or more
rdundant data center grade switches and routers
a good backup strategy
probably A/C units
lots and lots of power
Subcriber agreements
insurance
a lot more knowledge than you think

I probably missed something too.

-Tim

---

### Post by spottedhog on 2008-08-30
Thanks for your reply!

We plan on using solar in the PTP towers, with a 15 day charge capacity in the deep cycle batteries.  Battery backup at the main tower, using trickle charge like the phone company uses... 10 day supply.


I am not sure if I have some items you list being fully "covered", but I have others doing the Cisco routers, switches load balancing/firewall... and someone else for insurance, etc.

I mainly came on here to get more info about basic servers needed, like how many for the applications I listed.

I welcome any more suggestions!  Thanks for those so far!

---

### Post by windependence on 2008-08-30
Well here I use two powerfull boxes, one production and one backup. Each of these runs several VMs for various servers, and then I just copy the VM to the backup box so I have an exact replica of the servers over there. On the front end we use two load balancers (home grown) and redundant firewalls (also home grown pfsense boxes). Most of what I run is FreeBSD, because that is what a good part of the ISP market runs and it is the most stable and secure OS out there for serving the web with a very small footprint and low resource consumption.

-Tim

---

### Post by spottedhog on 2008-08-30
OK....  getting curiouser...  :)

I had seen instances where others talked about using FreeBSD.  I and the others will check on this.

Thanks!

Are you running an ISP or WISP?

---

### Post by windependence on 2008-08-31
Well I am a Unix/Linux consultant. I host sites for my clients as well as several of my own sites. I have actually been doing more of this and I am trying to go more in that direction because there is less travel involved with hosting and running sites as opposed to going onsite at a client's business and setting up mailservers, network, web servers, etc.

If you go to [http://uptime.netcraft.com/up/today/top.avg.html](http://uptime.netcraft.com/up/today/top.avg.html) you can see the longest uptimes for hosting companies. The one's that say BSD OS are probably OpenBSD, the most secure OS on the planet. Either one is a great hosting and server OS. I use Ubuntu server as a base for my virtual machine boxes, but now that VMware ESXi is free, I may be moving away from that on new boxes.

If you have more questions fore away.

-Tim

---

### Post by spottedhog on 2008-08-31
:)  I see you use SMF/Tiny Portal for your sig link site.  I merged PHP Nuke and SMF.

Can you "consult" over the 'net?  I might be interested in your services later.

thanks,

---

### Post by david_lynch on 2008-08-31
> **spottedhog said:**
> OK....  getting curiouser...  :)

I had seen instances where others talked about using FreeBSD.  I and the others will check on this.
The BSDs have a long history of reliability and innovation. I used FreeBSD and netbsd a lot in the 90s, becasue the BSDs were solid and mature, and linux was new and buggy and had a lot of catching up to do. Now linux is at the top of the food chain, and while BSD is still solid, I just can't see any complelling reason to move back to it. I get 1100 day uptimes from my busy linux servers these days with no problem.

I do IT consulting and have worked for some fortune 100 firms, as well as some single server mom and pop shops. All the ISPs I'm familiar with are running linux, although I haven't done an exhaustive search, so there are natually other OSes in use. I'd been working mainly with suse enterprise in the big firms, but have recently switched my own servers to ubuntu, and was impressed at the ease of transition to ubuntu, and how lean and functional ubuntu server is.

In any case, the best way to answer the question is to try all the OSes you're curious about. Really try them on for size - do some common tasks, compare the package management and update process, use it long enough to  troubleshoot common problems, and look at the availability of commercial and other 3rd party software.

I'll be curious to see what you find.:popcorn:

---

