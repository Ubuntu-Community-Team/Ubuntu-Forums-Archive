---
title: "Dell Precission 450 Dual Xeon 2.3ghz: suitability"
date: 2007-11-29
forum: Server Platforms
---

### Post by HWTMA on 2007-11-29
Hello,

**My question is this: is a Dell Precision 450 (2x 2.3ghz Xeon procesors), running Ubuntu Server 7.1, up to the job as a first server for small office?**

Note: this hardware is available at no cost.

_Some background:_
I'm working with a small but growing charity who are currently considering option for the consolodation and growth of their IT infrastucture. They currently have an assortment of Windows PCs (desktops and laptops, XP Pro and Home edition) and a few Mac Books. These are split between two locations. A single large exernal harddrive is used as back-up. They have decided that they have reached the point that investmnt in a server is now needed.

They have one person who maintains all the existing systems. She is not an IT pro, nor does she want to move down that route at the expence of her profession (underwater archaeologist). So her opiions are based on her perception of ease of maintenance; mine by the current and future GIS requirements and a background in using Macs with various UNIX/open source apps (I also use a dual boot PC with Ubuntu and XP).

I'm of the opinion that they should start simple, perhaps start with a file and print server. I feel investment should be in that which directly benefits those areas of their services they wish to expand, that being GIS and 3d visualisation. 

They are entrenched in ESRI GIS software and I think with current skills, a migration to open source alternatives would impact productivity too greatly. Therefore in the near future I'm going to be encouraging a step up to ArcGIS Server (basic ed.), which will (I'm told) run on Ubuntu server.

However, their IT person is keen to implement a email, web and ftp as well. She want to do this with a Windows Server 2003 + hardware package (c. £5000 plus support).

If the Dell hardware is up to it, what would be your recomendations for upgrading it? It currently has 1gb RAM and a single 120gb hard disk, so I feel these would be good places to start. It also has a Lacie eSATA PCi card, with RAID surrort, so we could make usee of that as well. Clearly there comes a point of diminishing returns with upgrades, but I think some cash and tlc would be worthwile.

I'd appreciate your comments on any aspect of what I've said (though doubt I've left something out!), 

Regards,

Lawrence

---

### Post by twistedtwig on 2007-11-29
not that I have had lots of experience but I would say she sounds powerful enough, another GB of ram might be good.

one thing to think of is how much storage do you need?  you say you have 120 gb drive in it atm is this easily enough or do you need more?

Raiding the drives would be sensible if affordable.

What sort of traffic do you expect the site, web, ftp, email etc would get?

If it is not a heavy site I would guess it would be up to it... I am sure others have far more knowledge on that than me.

2003 is a nice system, as long as you dont want / need AD and don't want ASP.NET then Ubuntu will do just as well.  There is the mono project to run asp.net on linux but I have no personal experience with it.

GL sure others will have more useful thoughts than me though

---

### Post by crouton on 2007-11-29
It sounds like you want the Linux equivalent of Windows2003 Small Business Server, which provides ActiveDirectory, Exchange, SharePoint, etc.  Unfortunately there is no all-in-one analagous package, but you can get pretty close.  You just need to spend some time determining what you need, and determine if various packages fulfill those needs.

The machine itself is fine.  More RAM wouldn't hurt considering how cheap it is currently.  

There are email/collaboration suites such as Scalix and Zimbra that will get you closer to your goal.  As far as backups go you'll need to determine the size of your backup set before you can purchase drives/equipment.  Look into rsync for remote replication, perhaps to an off-site server (home?)  FTP is fairly easy.  Apache2 will host your website fairly easily as well.  Samba for file/print sharing and possibly NT-style PDC if you're looking into user authentication.

RAID1 external enclosures are pretty cheap these days so you might want to consider that as the on-site backup medium, saving your primary HD space as a temporary staging area or what not.

---

### Post by HWTMA on 2007-11-30
Thanks for your comments!
With regard load on the server, the current web site received 432,000 hits last year, so relatively light in the grand scheme of things, but them the hardware we're talking about is at the lower end of server hardware. Email wise, there's about 15 full time staff, with fairly typical email use/habits. On the ftp side, it's likely to be mainly me using that to provide updated GIS data etc from off-site and possibly as was suggested, to facilitate back-ups. But I'd defer to others greater knowledge and experience to determine how this level of use/traffic matches up to the hardware we have. 

One of the offices in which I work is currently migrating to AD. From that experience of it I would definitely steer well clear of that!! 

There's definitely a gulf between what I think the organisation should start out with and what their IT girl wants to do! It's a small organsation with not pots of cash, though it is slowly expanding. She want to go down the mail server route for example, because their current service provider's server offers too little space to serve as a backup for their mail. I would sugggest that this could be solved with appropriate local solutions. Or, by telling the service provider that they'll loose their custom if they can't be given bigger mail boxes!! 

Their webite is small, fairly static and as far as I can remember, just plain old html. I don't see any justificaion at present to maintain a web server.

As for ftp, we can probably do without that as well. The data I deal with is all going into a database and I can manage replicated versions from within my GIS, assuming the server is appropriately configured to allow be to connect to the DB remotely.

So all we ned is shared file space with back up and printing, at this stage.

The charity is a maritime archaeology organisation so they not only produce quite a bit of data, but have obligations to archive it and store it for perpetuity! Their data includes photographs, video, raster map data of various sorts and soon, 3d visualisations/animations. So their needs are quite high for an organisation of their size. However, as with RAM, 
storage is relatively cheap, so should not be an issue. 

Thanks again for your comments, any more very welcome!

Regards,

Lawrence

---

