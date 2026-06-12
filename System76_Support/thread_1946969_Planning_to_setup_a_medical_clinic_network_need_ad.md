---
title: "Planning to setup a medical clinic network need advice plan to use System 76 laptops"
date: 2012-03-25
forum: System76 Support
---

### Post by izquierdista on 2012-03-25
Hi Everyone, 

I am a soon to be physician and am planning to setup a very small medical clinic which will operate out of donated space at a high school in Phoenix Arizona, thus all my equipment needs to be as portable and compact as possible because I need to take to transport the equipment to and from the site during the days of operation.Anyways this is what I want to do: 

Use System 76 laptops because I know 100% they are ubuntu compatible from the ground up and also because I have used one of their laptops in the past for personal use and liked it alot. My electronic medical record program would be OpenEMR which is a HIPAA compliant program and best of all opensource and can be run off a server on site. 

I have already tried contacting some IT companies here in the Phoenix Arizona area and they try to tell me to use MS windows computers and get commercial software and they dont work with linux so thats why I decided to ask the forum. 

Here are my questions:

1) Can I use a laptop to act as the "server"? where OpenEMR would be installed all files stored etc. The other 2 laptops would access this server. Which system 76 laptop do you recommend for this role? 

2) I need a portable laptop printer compatible with ubuntu which one you recommend? 

3) I need a portable scanner and need one that works well with ubuntu, which one do you recommend? 

I welcome any and all suggestions thanks.

---

### Post by smarmytime on 2012-03-25
Technically, you CAN use a laptop as a server, but I don't know that it's really optimal. Is it possible you have an old tower lying around, that you could throw ubuntu on, and use as a dedicated server? If you don't, you could surely pick one up for $50 or so, used.

---

### Post by izquierdista on 2012-03-25
> **smarmytime said:**
> Technically, you CAN use a laptop as a server, but I don't know that it's really optimal. Is it possible you have an old tower lying around, that you could throw ubuntu on, and use as a dedicated server? If you don't, you could surely pick one up for $50 or so, used.

pardon me for being ignorant but are there any servers or towers that are portable and run off of battery power? If not, would it be safe for me to plug one into one of those large portable battery "generators" 

see the thing is that I only want to use the donated  space ( a classroom area) and not have to plug anything into the schools power grid because I will be providing services as an independent contractor so anything battery operated is a plus for me. the least amount of resources or dependence I have on the schools resources the better.

---

### Post by smarmytime on 2012-03-25
For a server, you generally want as stable a setup as possible. I'm guessing the load would be fairly low, would it not? Why not just set the server up at your home?

---

### Post by izquierdista on 2012-03-26
> **smarmytime said:**
> For a server, you generally want as stable a setup as possible. I'm guessing the load would be fairly low, would it not? Why not just set the server up at your home?

I want to have the server on-site because eventually I will go to different sites where I will see patients where I might not have internet access or if the internet goes down it wouldnt matter because if the server were on site I would only need my intra-net to operate and thats what attracted me to OpenEMR. Nevertheless I do plan to have a back-up server off-site, possibly even use one of those  cloud services?.

The load on the server would be low these are the main things I would need it to do: 

1) Act as the OpenEMR access server
2) Store business data such as spreadsheets for stocked items such as pharmaceuticals
3) Store general documents pertaining to the clinic ( libreoffice writer, spread sheet files, image files etc. etc.). 
4) allow access to the other 2 laptops that would be acting as workstations. 

would something like this do the trick: [http://www.stealth.com/portables_stealthbox_warrior_atx_17.htm](http://www.stealth.com/portables_stealthbox_warrior_atx_17.htm)

It looks like you can install ubuntu on it and I think its battery powered, correct me if Im wrong.

maybe the people at system 76 can make me something that does a similar job as the link I provided, I dont care if it looks pretty or not as long as it can remain charged for 4 hours at a time at a minimum would be great and I would just recharge the battery as needed.

---

### Post by perspectoff on 2012-03-26
I've been down that road already in every permutation.

You want your server in a stable location. Traveling is very hard on hardware, and clearly you haven't done it much or you'd know that. You want your core server in a stable, protected place.

The easiest thing to do is to set up OpenVPN. That way you can have your own "Intranet" at your permanent location (your garage, for example, as the other user suggested) and just connect to it from anywhere.

Then invest in 3G/4G access. As a traveling physician, it's worth the money. I lived off WISP connections for a year or two, and while free, it was frustrating not to have 100% connectivity from everywhere (since WISP connections require proximity to an antenna). 

If you are going to practice in really remote places, then get a satellite service.

I actually lugged a Brother 7820N printer/scanner/fax with me everywhere (which is 100% Ubuntu compatible) but ended up buying 4 or 5 of them and just left one at each location. There's a lot of wear-and-tear on printer/scanners with travel, too.

The very most important thing from the outset is to set up good backup of your records, and the easiest way to do that is with a RAID NAS (like the Synology DS-212). In 14 years I've never lost a record, but I've watched two hospitals have data crashes with lack of appropriate backup (to be fair, one was due to a flood -- so offsite redundant backup is a very good idea). 

The cost of running a server (especially if you only have a 150W power supply) is not that much, even if you have a 17.5 W Synology NAS attached. I'm sure if you're that conscientious, you could just give the school $75 or $100 for a year's worth of power.

I initially tried to do what you're talking about (and did it for all of 3 months), but as my mobile business grew (in the number of locations), it became more and more painful to lug equipment around. 

BTW, for most things I only use (Android) tablets now, which can act as either dumb terminals (using SSH/VNC) to the master server or can connect in other ways. I still use a laptop for OpenEMR (and other EMRs, since every facility seems to have their own), though, partially because I also use a variety of Telemedicine platforms and PACS access that an Android tablet is not sufficient to handle. 

I haven't looked into the OpenEMR Android capabilities...

Good luck.

---

### Post by izquierdista on 2012-03-26
> **perspectoff said:**
> I've been down that road already in every permutation.

You want your server in a stable location. Traveling is very hard on hardware, and clearly you haven't done it much or you'd know that. You want your core server in a stable, protected place.

The easiest thing to do is to set up OpenVPN. That way you can have your own "Intranet" at your permanent location (your garage, for example, as the other user suggested) and just connect to it from anywhere.

Then invest in 3G/4G access. As a traveling physician, it's worth the money. I lived off WISP connections for a year or two, and while free, it was frustrating not to have 100% connectivity from everywhere (since WISP connections require proximity to an antenna). 

If you are going to practice in really remote places, then get a satellite service.

I actually lugged a Brother 7820N printer/scanner/fax with me everywhere (which is 100% Ubuntu compatible) but ended up buying 4 or 5 of them and just left one at each location. There's a lot of wear-and-tear on printer/scanners with travel, too.

The very most important thing from the outset is to set up good backup of your records, and the easiest way to do that is with a RAID NAS (like the Synology DS-212). In 14 years I've never lost a record, but I've watched two hospitals have data crashes with lack of appropriate backup (to be fair, one was due to a flood -- so offsite redundant backup is a very good idea). 

The cost of running a server (especially if you only have a 150W power supply) is not that much, even if you have a 17.5 W Synology NAS attached. I'm sure if you're that conscientious, you could just give the school $75 or $100 for a year's worth of power.

I initially tried to do what you're talking about (and did it for all of 3 months), but as my mobile business grew (in the number of locations), it became more and more painful to lug equipment around. 

BTW, for most things I only use (Android) tablets now, which can act as either dumb terminals (using SSH/VNC) to the master server or can connect in other ways. I still use a laptop for OpenEMR (and other EMRs, since every facility seems to have their own), though, partially because I also use a variety of Telemedicine platforms and PACS access that an Android tablet is not sufficient to handle. 

I haven't looked into the OpenEMR Android capabilities...

Good luck.

Thank you very much for your extremely insightful input and recommendations I will go ahead and look more into the things you mentioned especially because you have faced the same logistics challenge I posed. 

I will update my post once I get everything figured out. 

Thanks everyone,

---

### Post by sanosuke.502 on 2012-04-17
im trying to develop/modify OEMR for dermatology, im a med student but don't know where to get started, i need to make it in spanish, and since there are several clinics i do need the server to be internet based so if a patien goes to a different clinic you can check his record anywere, i just need to know how to get on the road, making it web based does help since im planning it to be accesible from any OS,

---

### Post by SeijiSensei on 2012-04-18
> **sanosuke.502 said:**
> since there are several clinics i do need the server to be internet based so if a patien goes to a different clinic you can check his record anywere, i just need to know how to get on the road, making it web based does help since im planning it to be accesible from any OS,

I'd strongly consider renting a virtual server from a reliable provider like [Linode]("http://www.linode.com/").  Their prices start at $20/month, and for a few bucks more you get things like daily snapshot backups.  The most important thing to remember, if you're practicing in the US, is that you must encrypt any stored "patient health information" and use SSL for any web connections.  That means buying an SSL certificate for your domain once you've set things up.  If you want to be fully-compliant with Federal law, use AES256 for encryption.  Oh, and never communicate with patients via unencrypted email.  If you must communicate electronically with patients, you need to look into some type of patient "portal" software.

---

