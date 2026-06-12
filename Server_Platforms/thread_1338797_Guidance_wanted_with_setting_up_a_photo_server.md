---
title: "Guidance wanted with setting up a photo server"
date: 2009-11-26
forum: Server Platforms
---

### Post by Excedio on 2009-11-26
Hey guys, I've been wanting to setup a server in my home that can be accessed by my family, friends and myself from outside of my network. I have 12,000+ pictures that I would like to share.

What is the best way that I can achieve this? I prefer not to host my pictures on a location outside of my home. My brother mentioned using Picasa, but I don't really like the idea of Google having all my pictures on their servers. I much prefer hosting something myself, I definitely have the bandwidth for it. Also, I'd like to build my own server so that I can expand it to do other things in the future.

What software should I use?
How should I proceed with this?

I am pretty clueless about this, but I am willing to work at it. Thanks.

---

### Post by dragos240 on 2009-11-26
First this:

HOW DID YOU GET 12K+ PHOTOS!!

---

### Post by Cam42 on 2009-11-26
> **dragos240 said:**
> First this:

HOW DID YOU GET 12K+ PHOTOS!!
Easy, he took them with a camera. ;)

---

### Post by red_Marvin on 2009-11-26
You'd probably want to set up a web server of some sort, and then some cgi to manage the pages, but there are many routes to take, and it depends on what you want and what your skills are.
If you know perl or python it should be pretty easy to set up something basic, but on the other hand I think there are more or less ready setups too available. Don't know the names though...

---

### Post by BenAshton24 on 2009-11-26
Just install apache and put them all into different directories in /var/www

```
sudo apt-get install apache2
```

---

### Post by RabbitWho on 2009-11-26
I'd like to point out that whatever photo site you use, even if you make one yourself, google will index it, and therefore your photos will be stored on their computers.

---

### Post by dasunst3r on 2009-11-26
> **Cam42 said:**
> Easy, he took them with a camera. ;)12K photos is about right for my four years of college.  Now, let's get back on topic...

Starting out with a basic LAMP (Linux Apache Mysql Php) server, you can install a script like Gallery ([http://gallery.menalto.com](http://gallery.menalto.com)).  I have been using it for my collection over the past four years, and it is VERY powerful.  You can do basic edits (crop and rotate), set permissions (so that only select people can access your photos, and even set up a shop for people to buy your photos!

If those capabilities are a bit too much for you, there's ZenPhoto ([www.zenphoto.org](www.zenphoto.org)).  It is simpler in that you drag-and-drop your photos to a predetermined folder and it'll show up on the generated web page.

---

### Post by BenAshton24 on 2009-11-26
You could also set up a database containing information about all of your images, their location on your server and their creation date + a little description. You could then write a simple PHP photo viewing web page thing that displays descriptions, dates and allows you to browse through your photos.

I'd be happy to help and if you want I can do the PHP bit for you when I have some free time.

Ben.

---

### Post by red_Marvin on 2009-11-26
> **RabbitWho said:**
> I'd like to point out that whatever photo site you use, even if you make one yourself, google will index it, and therefore your photos will be stored on their computers.

That's what robots.txt is for, I think google adheres to it.

---

### Post by Excedio on 2009-11-26
Firstly, thanks for all of the quick replies. :-)

> **dragos240 said:**
> First this:

HOW DID YOU GET 12K+ PHOTOS!!

Camera + Time = 12,000+ Pictures :-)

> **red_Marvin said:**
> You'd probably want to set up a web server of some sort, and then some cgi to manage the pages, but there are many routes to take, and it depends on what you want and what your skills are.
If you know perl or python it should be pretty easy to set up something basic, but on the other hand I think there are more or less ready setups too available. Don't know the names though...

Unfortunately, I do not know how to write perl or python...yet ;-)

> **BenAshton24 said:**
> Just install apache and put them all into different directories in /var/www

```
sudo apt-get install apache2
```

Will look into this.

> **dasunst3r said:**
> 12K photos is about right for my four years of college.  Now, let's get back on topic...

Starting out with a basic LAMP (Linux Apache Mysql Php) server, you can install a script like Gallery ([http://gallery.menalto.com]("http://gallery.menalto.com/")). I have been using it for my collection over the past four years, and it is VERY powerful. You can do basic edits (crop and rotate), set permissions (so that only select people can access your photos, and even set up a shop for people to buy your photos!

If those capabilities are a bit too much for you, there's ZenPhoto ([www.zenphoto.org]("http://www.zenphoto.org/")). It is simpler in that you drag-and-drop your photos to a predetermined folder and it'll show up on the generated web page.

Thanks very much for the recommendations. I'm leaning towards Gallery at the moment.

> **BenAshton24 said:**
> You could also set up a database containing information about all of your images, their location on your server and their creation date + a little description. You could then write a simple PHP photo viewing web page thing that displays descriptions, dates and allows you to browse through your photos.

I'd be happy to help and if you want I can do the PHP bit for you when I have some free time.

Ben.

This definitely sounds like more of a challenge for me....which I would be up for. :-)

I might take you up on your offer. :-)

> **red_Marvin said:**
> That's what robots.txt is for, I think Google adheres to it.

Can you elaborate on this? I'd really prefer not to be indexed. Also, if I just lock down the site and require a Username & Password, can Google really index it?

---

### Post by BenAshton24 on 2009-11-27
> **Excedio said:**
> 
Can you elaborate on this? I'd really prefer not to be indexed. Also, if I just lock down the site and require a Username & Password, can Google really index it?

You're perfectly correct, if you set up passwords correctly then google will not be able to index any content. The robots.txt is a file that you have on your server that is read by webbots to determine what you want to be indexed amongst other things. For example, you could prevent all indexing with the following:
```
User-agent: *
Disallow: /
```

Ben.

---

### Post by Excedio on 2009-11-27
Thanks for the explination. I also did some reading up about this. Seems that all "legit" webbots will abide by the robots.txt file. As expected, webbots created for malicious reasons will just run right past the file like it's not even there.

I'll definitely do both steps. Passwords and robots.txt

---

### Post by dasunst3r on 2009-11-28
Also read up on ".htaccess" -- it'll stop any bot dead in its tracks from indexing your photos.

---

### Post by Excedio on 2010-03-08
Hey guys...finally started to seriously **plan** my new server. While i'm still a ways off from the actual build, I want to be sure that I have my ideas put down on paper.
 
I'd like for you all to take a look at my attachment, it's a simple .txt file outlining my ideas.
 
I'm having a hard time even trying to decide which case I want to use to house my server. What do you all use? I want something that will allow me to have a maximum of 5 HDDs installed.
 
 
 
OH and by the way...you'll see that it's expanded from just a Photo Server, to a Web Server, future Media Center Server, and possibly an Email Server.

---

### Post by Excedio on 2010-03-08
Well...I can see that some people have taken a look at the outline. Any thoughts?

I'd also really like some help with picking out the pieces of the server...I like these so far...

**[Athena Power CA-SWH01BH8 Black Steel Pedestal Server Case - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811192058")**

[B][Athena Power AP-P4ATX85FE EPS12V Ver. 2.92 SLI Ready CrossFire Ready Active PFC Supports Intel Core i7 & Skulltrail Platform ... - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817104126")

[/B]**[Sony Optiarc 24X DVD/CD Rewritable Drive Black SATA Model AD-7240S-0B - OEM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827118030")**

---

### Post by FiveSidedPoly on 2010-03-08
In my honest opinion that case is a little overboard, yes it is nice, but it is very big and very expensive for a simple "photo" or media server setup. Especially if you just put it in the closet, basement, or hidden corner somewhere. 
 
Also I don't see the need for a dvd/cd drive unless you expect to load photos or programs that way, possibly burn photo dvd/cds, but since it's a server I guess it wouldn't be happening either much.
 
 
I have a media server with five drives right now in this case, its a pretty tight fit, but not that bad. I recommend them to alot of friends who are looking for something small.
 
[Rosewill FE-M020-BU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811147152")
 
As you can see they are sold out, the black ones too, I bought some of these over the pricey Antec Sonata I was looking at. Shop around, I'm sure you can find some at a different location.
 
I highly recommend a AMD Athlon II X2 of any flavor, they are very cost effective performance and price wise, plus they are easy on electric bill too at 65W.
 
A basic "photo" or media server can be built at the cost of the tower you found. Add a lot of storage for a few hundred then.
 
Take your time, don't ever rush into a built.

---

### Post by Excedio on 2010-03-09
I do realize that the case can be a bit much, but that's why I'm glad that I'm posting my thoughts here. :-) I need people to tell me what's smart and what's not.

The reason for the cd/dvd burner is simply because they're cheap, not much more than a cd/dvd player. I have two spare cd drives lying around, but I'm afraid of not having a dvd drive for some reason or another.

I'll definitely look around more, and I do like the case you showed me (just wish it didn't have any blue in it).

As for rushing...not happening here. :-) Started this thread on Nov and still have not bought any parts yet. :-) Definitely still in the planning phases. :-)

---

### Post by FiveSidedPoly on 2010-03-10
They also make that case in all black, but that one sold out a long time ago on NewEgg, I didn't realize that the blue one sold out until I tried to find it again to link here.
 
I do understand the need for a cd/dvd drive, I have an external that I hook up to my home server and HTPCs quite a bit for random things, you could go that route and it might be worth more in the long run.  Having one internally hooked up can draw power and power consumption is important if you're running it all the time.
 
Don't go overboard when picking a power supply, but do get something reliable, and plan for the future.
 
[Power Supply Calculator]("http://www.thermaltake.outervision.com/")
 
You can use the link provided, it's for Thermaltake's site, but Antec uses the same one.  Put the parts you are looking at into it, even add some things you might want to have later, and see what is recommended.  Add things like USB devices, a TV card, etc.  I usually shoot for around 100-150W higher then what they recommend.
 
If you have any questions feel free to ask.  I usually do a new build for something once a week.

---

### Post by Excedio on 2010-03-10
I will definately be looking in to the all black version. :-)
 
I like your perspective on having an external CD/DVD drive. Doesn't lock me down to using it on only one machine, and helps save on power (definately a plus).
 
Do you have any suggestions on a good server mother board? 
 
EDIT: This is the only SERVER mother board ON NewEgg that was MicroATX (That's what the Rosewill case takes...as I'm sure you are well aware).
 
There are two, maybe three, things that I see as Cons to this MoBo:
 
1. Maximum Memory Supported: 2GB (I really feel that I need to go higher than this considering that it will be a future Media Server)
 
2. Onboard Video Chipset: Intel GMA 950. I constantly hear horror stories on the forum about Intel Video Cards. (However, this may not be an issue. I plan to run this server headless with No Machine - [http://nomachine.com/](http://nomachine.com/) - server installed so that I can pull up a Desktop when needed)
 
On a positive note about this MoBo.. There is a positive review from a Linux user.
 
[QUOTE=Reviewed By: King Arthur | 12/9/2009 | 4/5 Eggs | Tech Level: high - Ownership: 1 month to 1 year | This user purchased this item from Newegg]
**Pros:** Server has been running Fedora 10 x86_64 for more than 10 months now and has been nothing but rock stable. I had a need for an mATX server board that I could use my ever ageing Pentium 805D processor with. Server has 4 250GB SATA drives in software RAID5 data volume as well as PATA/IDE HDD for the OS drive. In addition to this, there are 3 external HDDs connected via USB. The server has routine uptimes exceeding 100 days and is only brought down for drive replacement or to boot a new kernel. Server is multi-homed and provides DNS, DHCP, firewall, routing and file serving (including NFS, SAMBA and iSCSI). Board works great with crucial DDR2-667 RAM. I plan to re-use this board with a newer Core 2 Duo processor once I have upgraded my core infrastructure.
 
**Cons:** On-board NICs were unstable using the stock kernel drivers with Fedora 10 and did not work at all with CentOS 5.x. Under Fedora 10, the interfaces would come up and remain functional until heavy traffic was initiated (large file transfers etc). The kernel driver had to be removed and re-loaded before the interfaces would re-initialize. It would have been nice if the board had been outfitted with Intel NICs as they are universally supported and known to be best in class. -1 egg.
 
**Other Thoughts:** According to dmidecode, the bios seems to think it has four (4) dimm slots and is capable of supporting up to 16GB of RAM. This board would rock if the layout could have been adjusted to support 4 dimm slots. Aside from the NIC issue (which may be resolved by now) this is an excellent Linux server board. [/QUOTE]

---

### Post by FiveSidedPoly on 2010-03-10
You don't need a specific motherboard for your home server, yes micro ATX would be best because they are usually cheaper, use less power, and you don't need everything a full ATX board offers.
 
The mobo you referenced looks good other then the issue with the NIC, I would not want a board for a server that has these kinds of issues, because I don't want to trouble shoot a NIC on top of other things.  Other then that it looks fine I suppose, but posting a link to it on NewEgg would be nice too.  :)
 
I currently am using this board from Asus.
 
[M4A785-M]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131595")
 
I got a whole bunch of these for HTPC builds, so it made sense to just use it.  
 
If you choose to use an AMD CPU, I recommend this board, or one similar to it.  It takes the AM2/AM2+/AM3 CPUs, has a really good onboard GPU, and takes DDR2 1066mhz ram.  It has 6 Sata connections.  And worked straight out the box with both HTPC and my home server builds.
 
I have one home server running a Athlon II X2 240, 4GBs 1066mhz ram, two 1TB WesternDigtal Green HDs, one 2TB WesternDigital Green HD, and a 2TB Seagate drive.  I'm using a 380W Antec Earthpower PSU.  And using that case I showed you.  I can't complain about this build, no real issues at all, other then the WD Green drives having the soft park issue with Linux.  But I fixed that, going to do a write up soon to share with everyone on here.
 
Each component was well under $100 except for some of the HDs and the ram.
 
I can't really recommend Intel stuff, don't use them other then in pre-built stuff, others know them better when it comes to picking for a build.  But choose what is comfortable for you.

---

### Post by Sporkman on 2010-03-10
Intel Atom-based machines make for fine home servers, though they may be limited in the number of drives supported.

---

### Post by Excedio on 2010-03-10
> **FiveSidedPoly said:**
> *snip* but posting a link to it on NewEgg would be nice too.  :) *snip*

I like this MoBo that you suggested.. it's actually very similar to the one that I have in my current computer... [ASUS M3A78]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131325") ...I love m board so I think I would love this one as well. :-)

I'm definitely going to take a look at the pieces that you listed in your server. What do you use your server for...curious.

---

### Post by FiveSidedPoly on 2010-03-11
One note on that motherboard I recommended, I have not been able to figure out how to wake it on lan, but I can live with it for now.
 
I actually have a M3A78-EM, in a LAN Box build, it's just sitting there collecting dust right now.  (I took that LAN Box to Iraq and back)  I use a lot of Asus boards, a M4A785TD-M EVO replaced the M4A785-M in my main HTPC because it has 128MB of onboard video ram and I didn't want to put a full GPU card in.  I can also recommend Gigabyte motherboards, have had great experience in the past with them, I have one in a graphics workstation I built almost 6yrs ago that still runs like a champ.  
 
But be careful with Gigabyte and MSI micro ATX boards, a few have come out recently that require a 500W+ PSU just to be stable.  Some people talked about them on NewEgg, unfortunately I got one and didn't find out until I read the manual.  Why a micro ATX board requires 500+W is beyond me, but just giving you a heads up.
 
 
My "home" server is used for just file sharing/storage mostly, tinkering right now with a good backup solution.  I am trying to create an internal website or wiki, but I don't know much about that when it comes to Linux, so I'm checking out all the options.  I'm about to take out the 2TB Seagate drive, because it is ticking randomly, its quite depressing.  I have another server set up as my 3D render farm manager.
 
 
I have heard that the Atom CPUs are good for a basic home server or HTPC builds, Sporkman may be able to share more info out them.  I personally like to have more power and scalability with what I do.
 
A M3A78 generation board could probably get picked up cheap and will be about the same as a [COLOR=#000000]M4A785-M, just the onboard GPU won't be as advanced, which won't hurt you.[/COLOR]

---

### Post by Excedio on 2010-03-17
Added a page to my blog dedicated to tracking my Server build. Feel free to leave comments there. :-)

[http://opensourceexcedio.wordpress.com/server-build/](http://opensourceexcedio.wordpress.com/server-build/)

---

