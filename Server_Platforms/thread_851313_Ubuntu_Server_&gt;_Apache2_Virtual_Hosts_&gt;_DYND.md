---
title: "Ubuntu Server &gt; Apache2 Virtual Hosts &gt; DYNDNS"
date: 2008-07-06
forum: Server Platforms
---

### Post by antilog on 2008-07-06
I've read quite a few tutorials of setting up named virtual hosts, but I am stumped.

Info:
- Ubuntu Server 8.04
- Apache2 running successfully
- want to host multiple sites w/ different domains
- /var/www/site1 , /var/www/site2, etc
- sitting behind a dynamic IP cable connection
- using a dyndns domain to address the external IP from outside

So I'd like if someone on web goes to [http://site1.com](http://site1.com), it goes to mysite.dyndns.org, which goes to my router, which forwards to the web server, which detects site1.com and serves that directory.

What I am having trouble figuring out is if I am using dyndns, how does Apache know which domain to serve up?  I am thinking the solution may lie with domain DNS - have a record to point site1.com to mysite.dyndns.org.  Would this be a CNAME? A record?

My ignorance is apparent...

Any ideas?

Thanks

---

### Post by antilog on 2008-07-06
Ah, I am thinking maybe the easiest solution is to cut out dyndns and use Custom DNS (which dynamically updates the actual domain name), which should pass the specific domain name, not mysite.dyndns.org

Thoughts?

---

### Post by antilog on 2008-07-06
Custom DNS won't be an option, too expensive for 3 domains...

---

### Post by osjak on 2008-07-06
I've never done it myself, but can you setup three domains with DynDNS and use each one of them for your site? All three would resolve to your home server:

site1.com -> site1.dyndns.net \
site2.com -> site2.dyndns.net - server
site3.com -> site3.dyndns.net /

Then you can separate the requests at your server.

---

### Post by antilog on 2008-07-07
That's an idea, probably tricky though, since I imagine it would require running 3 separate ddns clients.

And I guess this is all moot until I can get ONE domain working. Been wrestling with virtualhosts all day...

Thanks for the repsonse

---

### Post by osjak on 2008-07-07
I like Linux because in 99 cases out of 100, somebody already had the same probem, solved it and posted his solition online :)

Here's a script for you to update your DynDNS record:
[http://nick.borko.org/update-dyndns](http://nick.borko.org/update-dyndns)

Make three copies of the script, each with its own logins to match your domains. Then just create a cron job to run them, say once a day to be safe, and viola - your domain redirection system is up and running :) 

No other DynDNS clients are needed in this case, of course.

PS: I never used the script myself, I just googled for it. If it doesn't work, try finding another one.

---

### Post by windependence on 2008-07-07
IMHO this is like holding your car together with chicken wire and chewing gum. Static IPs are fairly easy to get these days and pretty cheap. I only pay $4.95 a month extra for mine and as an added bonus, I get no ports blocked. Unless you absolutely can't get one even by changing ISPs, I would not use dynamic dns, at least on production boxes for sure.

-Tim

---

### Post by skunkbad on 2008-07-07
That's why I didn't go with DynDNS. Go with zoneedit.com and you don't have the subdomain crap to deal with.

Name based virtual hosts is basic to set up (at least it was on my 8.04 server). Simply make a host file for each site in the sites-available directory, and then symlink to it. If you don't know what to put in the host file, take a look through the forum and you will see plenty of examples.

Here is an example of one I am running right now:

```

<VirtualHost *>
	ServerName www.bigdomain.com
        ServerAlias bigdomain.com	
	DocumentRoot /var/www/bigdomain
	<Directory /var/www/bigdomain>
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
	ErrorLog /var/log/apache2/bigdomain-error.log
</VirtualHost>

```

Make your symlink, add the /var/www/bigdomain directory, restart apache, and put your index.htm file in /var/www/bigdomain to test it out.

This is literally all I had to do to get name based virtual hosts working.

Side note: I made sure to use -Indexes in the /sites-available/default file so that the www directory was no longer indexed, but this isn't necessary to get name based virtual hosting working.

---

### Post by osjak on 2008-07-07
> **windependence said:**
> IMHO this is like holding your car together with chicken wire and chewing gum. Static IPs are fairly easy to get these days and pretty cheap. I only pay $4.95 a month extra for mine and as an added bonus, I get no ports blocked. Unless you absolutely can't get one even by changing ISPs, I would not use dynamic dns, at least on production boxes for sure.

-Tim
You are totally right, Tim. But hey, if a person wants to experiment, why not? If I'm understanding correctly, those are not going to be production sites. This is a hobby project. I am actually interested how well such system will work for the OP. 

On the other side, if a better reliability is desired, I would suggest buying some shared web hosting plan and setting up sites there. This way, you get your websites running independently of your home server experiments. You can get somewhat acceptable shared hosting for $3 - $8 per month. 

I'm just not a big fan of home based web servers. When I fire up my torrent client, there's no way my upstream connection is going to be enough for a half-sane person to browse my home-based website. I have a home server for experimenting purposes, but my hobbiest websites are on a shared plan with a hosting company. I also use that hosting for offsite backups of my desktop documents.

---

### Post by windependence on 2008-07-07
> **osjak said:**
> You are totally right, Tim. But hey, if a person wants to experiment, why not? If I'm understanding correctly, those are not going to be production sites. This is a hobby project. I am actually interested how well such system will work for the OP. 

On the other side, if a better reliability is desired, I would suggest buying some shared web hosting plan and setting up sites there. This way, you get your websites running independently of your home server experiments. You can get somewhat acceptable shared hosting for $3 - $8 per month. 

I'm just not a big fan of home based web servers. When I fire up my torrent client, there's no way my upstream connection is going to be enough for a half-sane person to browse my home-based website. I have a home server for experimenting purposes, but my hobbiest websites are on a shared plan with a hosting company. I also use that hosting for offsite backups of my desktop documents.

The problem is, when you are trying to do things like virtual hosting, a redirect is going to get in your way most of the time depending on how it is done. Many people are also not aware that they can get a static IP just by asking their ISP for it. There are also ISPs like SpeakEasy which do not block ports and offer static IP connections in most areas.

I serve a site from my home that gets 13,000 page views per day and over 5 million hits per month. I try to limit any downloading to the overnight hours but there have been times when I had to do it and I have had no issues with bandwidth, in fact, I am only using a small fraction of the bandwidth I have. Also, with the proper gateway box, you can limit certain traffic and certain connections to a predetermined amount of bandwidth, also a good learning experience BTW. I just see so many people deviling themselves with this dynamic crap when they really don't have to go through all that pain. :)

-Tim

---

### Post by osjak on 2008-07-07
> **windependence said:**
> The problem is, when you are trying to do things like virtual hosting, a redirect is going to get in your way most of the time depending on how it is done. Many people are also not aware that they can get a static IP just by asking their ISP for it. There are also ISPs like SpeakEasy which do not block ports and offer static IP connections in most areas.

I serve a site from my home that gets 13,000 page views per day and over 5 million hits per month. I try to limit any downloading to the overnight hours but there have been times when I had to do it and I have had no issues with bandwidth, in fact, I am only using a small fraction of the bandwidth I have. Also, with the proper gateway box, you can limit certain traffic and certain connections to a predetermined amount of bandwidth, also a good learning experience BTW. I just see so many people deviling themselves with this dynamic crap when they really don't have to go through all that pain. :)

-Tim

:o  13,000 page views a day on a home server?! I need to pick your brain a bit :)  Would you mind sharing some technical detail about your connection? Up speed, down speed, does your connection affects your site visitor's experience?

The reason I ask - I have a community website that gets about 2,000 page views a day. It is on a dedicated server with a hosting company - $80/month. I am working on adding a video streaming system on it, so I doubt my home line would suffice at that point anyway, but right now it's just a Joomla/SMF combination, and I was sure it cannot be hosted at home with 2,000 page views a day. But I see now from your stats, it's doable. Please share your experience.

---

### Post by windependence on 2008-07-07
Sure. The setup is a dual Opteron system (2.6 GHz) and 8 gigs of RAM with 1.1 Terabytes of storage NOT in RAID. :) I have another box that is going to be the main server soon, this is a dual quad core Opteron box running at 2.2 GHz with 12 gigs of RAM. Both machines have redundant nics and power supplies. I also run 2 UPS boxes. 

Each box runs Linux for the host OS BUT I run FreeBSD on all my VMs using Vmware Server 1.04. When the new box is up, it will replicate to the old one for failover. I don't want to say anything bad about Linux, but FreeBSD (and the other *BSDs for that matter) kick serious @ss. If you want something lean and mean that is the way to go. Look what is the most used OS for web servers on netcraft.com. It ain't Windoze and it ain't even Linux.

As for my connection, well I don't even have the speed I want yet but FYI the down is 3 mbs and the up is just 640K. My users have no complaints and I surf the site from outside every day for several hours. It works fine.

Oh and I do have a 12 drive RAID cabinet attached for storage but I never use the drive. That is run from a Dell Perc3 card in the main server.

Glad to help, if you have questions please ask. ;)

-Tim

---

### Post by osjak on 2008-07-07
That's a heck of a home server! :) Thank you for sharing. I will try experimenting with FreeBSD. I've read a lot of good reviews about it. I guess I should bite the bullet and get familiar with it. 
Thanks again.

---

### Post by windependence on 2008-07-07
Here is a good resource where I am a member:

[http://daemonforums.org/index.php](http://daemonforums.org/index.php)

-Tim

---

### Post by antilog on 2008-07-07
> **windependence said:**
> IMHO this is like holding your car together with chicken wire and chewing gum. Static IPs are fairly easy to get these days and pretty cheap. I only pay $4.95 a month extra for mine and as an added bonus, I get no ports blocked. Unless you absolutely can't get one even by changing ISPs, I would not use dynamic dns, at least on production boxes for sure.

-Tim

Yeah, I live in a city, so no fiber, phone lines in the building look rough, DSL providers here are terrible (I am IT consultant, deal with them all the time), and my cable provider does not offer static IP's with their consumer service, and their min business package is out of my price range.

The sites I will be running are personal sites, not critical, and I really wanted total access to them, thus hosting them at home.  

Thanks for the idea!

---

### Post by antilog on 2008-07-07
> **skunkbad said:**
> That's why I didn't go with DynDNS. Go with zoneedit.com and you don't have the subdomain crap to deal with.

Name based virtual hosts is basic to set up (at least it was on my 8.04 server). Simply make a host file for each site in the sites-available directory, and then symlink to it. If you don't know what to put in the host file, take a look through the forum and you will see plenty of examples.

Here is an example of one I am running right now:

```

<VirtualHost *>
	ServerName www.bigdomain.com
        ServerAlias bigdomain.com	
	DocumentRoot /var/www/bigdomain
	<Directory /var/www/bigdomain>
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
	ErrorLog /var/log/apache2/bigdomain-error.log
</VirtualHost>

```

Make your symlink, add the /var/www/bigdomain directory, restart apache, and put your index.htm file in /var/www/bigdomain to test it out.

This is literally all I had to do to get name based virtual hosts working.

Side note: I made sure to use -Indexes in the /sites-available/default file so that the www directory was no longer indexed, but this isn't necessary to get name based virtual hosting working.

It's strange, most of the tutorials made it look this easy, but it's not working for me.  I think my next step is to reset the apache2 conf's to defaults and start over.

---

### Post by windependence on 2008-07-07
> **antilog said:**
> Yeah, I live in a city, so no fiber, phone lines in the building look rough, DSL providers here are terrible (I am IT consultant, deal with them all the time), and my cable provider does not offer static IP's with their consumer service, and their min business package is out of my price range.

The sites I will be running are personal sites, not critical, and I really wanted total access to them, thus hosting them at home.  

Thanks for the idea!

Are you in the US? If so, check out SpeakEasy and see if they offer service in your city.

-Tim

---

### Post by antilog on 2008-07-08
> **windependence said:**
> Are you in the US? If so, check out SpeakEasy and see if they offer service in your city.

-Tim

They offer T1 and various DSL.  Unfortunately the RJ11 wiring in this building is a mess, and T1 is out of price range.

Now that I am looking into this, it is ridiculous being in a major US city, being an IT guy, and not having an affordable static IP...

---

### Post by windependence on 2008-07-08
You may be surprised at how good the DSL may be. The only way you would know is to try it. The wiring in my building is also nasty but I have had no issues for 4 years.

-Tim

---

### Post by antilog on 2008-07-08
> **windependence said:**
> You may be surprised at how good the DSL may be. The only way you would know is to try it. The wiring in my building is also nasty but I have had no issues for 4 years.

-Tim 

I'll contact Speakeasy to work it out, maybe they can test the line.  It's a long shot, I also don't have telephone service...

---

### Post by windependence on 2008-07-08
There's always VOIP if you can get the DSL. :)

-Tim

---

### Post by antilog on 2008-07-08
> **windependence said:**
> There's always VOIP if you can get the DSL. :)

-Tim

What I meant was, the phone lines in my home are not active - I don't want voice service.  So it just adds another layer of complication - frayed lines, no existing service...

---

### Post by antilog on 2008-07-08
> **antilog said:**
> I'll contact Speakeasy to work it out, maybe they can test the line.  It's a long shot, I also don't have telephone service...

So I heard back from Speakeasy - over twice the price ($116) for roughly half the throughput (of what I have now).

Comcast Business got back to me saying they will do a site survey, their Consumer services don't offer static IP.

Still surprised that having a static IP in Baltimore City is so expensive...

---

### Post by antilog on 2008-07-08
Sorry for the play by play off topic tangent, but a little effort always helps:  contacting Comcast Business has been fruitful, immediate response, and for $15 more a month I can have a static IP and priority Business bandwidth over my Consumer-level neighbors.... I signed up for it, and will see how it pans out.

After that I'll proceed with the virtual hosts, and for now, just try to get 1 working...

Thanks for all the awesome help.

---

### Post by windependence on 2008-07-08
Fantastic! When they know they have a little competition, they get right on it. You will appreciate having all your prts open too.

Glad to help out.

-Tim

---

### Post by osjak on 2008-07-09
antilog, I'm glad it's working out for you! I'm wondering if Comcast's business package has the same down/up speed ratio as residential, or did they up the upload speed for you?

---

