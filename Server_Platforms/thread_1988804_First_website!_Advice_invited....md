---
title: "First website! Advice invited..."
date: 2012-05-28
forum: Server Platforms
---

### Post by prshah on 2012-05-28
Hello,

I am planning to make my first website. I hope it to be a commercial (semi-)success, though my current motivation is simply to [s]learn[/s] experiment.

I have decided on using Joomla!, with LAMP, at least initially. I have played around with Joomla! but not done any serious work on it. As a result, I'm not sure if I can do all that I want with it.

So, I plan to have a "test" server, which at least initially, will not be open to the Internet.

I was planning to throw it onto some old hardware I have lying around, but then I was pulled into the fascinating world of cloud computing...

However, being new to both server and cloud, I thought I would ask advice here first.

There are a number of "free" Joomla! hosting sites. However, most of them seem to say that 3rd party extensions are not allowed. I do not know enough about Joomla! to know what extensions are third party. For example, there is an extention "simple file upload"; can I use this, or will it be counted as a 3rd party extension? This is an example, but I hope you can get the picture...

I don't mind paying a smallish amount for paid hosting, but I don't want to pay out too much for a learning experience which may or may not be converted to a commercial site.

My main concern is that if I choose a provider, I need one such that in about 2 months, if I decide not to go ahead, I can close the hosting and walk away without being billed further (ie, no contract, no small print, etc).

With me own hardware, this is not an issue. However, I do not have enough knowledge for securing a webserver. (Though I am not going to expose it initally, I would rather have a solid groundwork laid on now.)

Please advise and guide... preferably first person experiences, but all opinions welcome.

(Notes: Tech level: intermediate-high, understand how websites work, can setup (mostly blindly) one, but no practical experience in managing one).

---

### Post by na5h on 2012-05-28
Learning how to set up your own server is always good...but in this particular case, you should probably concentrate more on the website itself. If you need a server in order to test your website, I recommend [XAMPP]("http://www.apachefriends.org/en/xampp.html").

---

### Post by Jonathan L on 2012-05-28
Hi prshah

> current motivation is simply to learn ... new to both server and cloud... walk away without being billed 

Focus on content, then content, then content.

But it's always really worth understanding operational things, especially as the grounding for any (potentially) serious web project.

I'd recommend two things:
Get some old computer and try it, try it, and try it again.
Try something like Amazon's free tier for getting your feet wet in the cloud

The best thing about the per-hour cloud offers is you simply turn it off.

I've written my views at length here: [http://ubuntuforums.org/showpost.php?p=11295541&postcount=15](http://ubuntuforums.org/showpost.php?p=11295541&postcount=15)
And some how-to here: [http://ubuntuforums.org/showpost.php?p=11464805&postcount=3](http://ubuntuforums.org/showpost.php?p=11464805&postcount=3)

For what it's worth, I'd recommend 10.04.4 LTS server as your starting point: very stable, no surprises, 3 years left in support.

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by Habitual on 2012-05-28
> **prshah said:**
> ...Please advise and guide... preferably first person experiences, but all opinions welcome...

I am here to tell you that I have just gone through such a "test" recently using my hippyspinach.com Geeklog install on a new public domain called bournetoraiseshell.com. 

It is my professional and technical opinion that Joomla is not a product I would choose to install ever again. I have been in the hosting business for a number of years and joomla installs have always been a Big Shiny Target on the net. 

There's a reason "most of them seem to say that 3rd party extensions are not allowed"... most of the hacks are aimed at weaknesses in poorly written code and most of the targets are extensions or add-ons to joomla itself.

[These Off-Site Resources]("http://www.bournetoraiseshell.com/article.php/20100721213521300?query=htaccess") on my DorkBlog can actually help you maintain a relatively safe environment for any Content Delivery Package.

These days, experience has taught me not to install or use joomla.
I rely on [GeekLog]("http://www.geeklog.net/") now. It may not have all the fancy "fluff" that another package may have, but it does the J.O.B. that I need it to do, keep my mind free for new things to learn!

Good Luck.

---

### Post by LHammonds on 2012-05-28
For a learning environment, you might want to go with a virtual machine.  This way you don't have to worry too much about the technical mumbo-jumbo of getting all the hardware to work with your OS.

I usually test all my servers out by first installing them inside a virtual machine on my PC (Windows 7) using VirtualBox (at home) or VMware ESXi server (at work).

Ubuntu Server 10.04 LTS is a solid OS to start learning on.  There are MANY articles on how to setup / tweak / fix it because it has been around a long time and enjoys a support contract for maintenance (meaning, you can buy support for it if you want to gain access to paid experts).  Ubuntu Server 12.04 LTS recently released so you might want to cut your teeth on that server but there are obviously less articles about it but you can buy support for it as well.

As others have said, focus on your content 1st.  Get a quicky server up-and-running so you can figure out if the product is what you really want rather than trying to spend untold hours tweaking an OS or figuring out how to ensure scalability with database clustering, replication, etc.  Worry about those details later (but make sure you are not pigeonholing yourself by at least "knowing" there is a way to scale your solution if successful.

LHammonds

---

### Post by prshah on 2012-05-28
> **Jonathan L said:**
> 
I've written my views at length here: [http://ubuntuforums.org/showpost.php?p=11295541&postcount=15](http://ubuntuforums.org/showpost.php?p=11295541&postcount=15)
And some how-to here: [http://ubuntuforums.org/showpost.php?p=11464805&postcount=3](http://ubuntuforums.org/showpost.php?p=11464805&postcount=3)


Thank you both, thank you and thank you again! These are the kind of real world info that I need like a parched man needs water in the desert.

I too am very much lured by both scaling and economy of Amazon's EC2. But, I am stumped as to initially what AMI I should select for Joomla; the AMI directory lists soooo many when searched with joomla. I'm currently leaning towards JoomlArt (or words to that effect), but I think it is a third party image... not sure. Can you suggest a suitable jump off point / AMI?

Though I can install and configure Joomla on a barebones install, I would *prefer* not to do so, as I *believe* a preconfigured image will be both more secure and faster to start off with.

Also, I have one more question about how Amazon charges; I've always been vary of Pay As You Go, because a simple mistake on my part (Eg forgetting the shutdown an instance) can run into rather heavy charges. Can you possibly tell me (in real world terms, not Amazon marketSpeak): Am I likely to run up large charges without my knowledge; ie, is there a kind of cut-off or limit which Amazon will warn me as I approach? Or a daily report of amount used, with breakup etc? (my "large" charge limit is, for example, $20-30 / month. Please don't laugh. I'm just starting out).

> **Habitual said:**
>  joomla installs have always been a Big Shiny Target on the net. 
I rely on [GeekLog]("http://www.geeklog.net/") now. 

Heh, you really know how to turn a phrase "Big Shiny Target". Yes, this is a problem that I am concerned about.

However, all things considered, I would rather start with this, then, as I get more familiar with the concepts, move on to Drupal (or GeekLog, which I hadn't heard of till now).

Once again, thank you both. I welcome any further suggestions from you as well as others too.

---

### Post by prshah on 2012-05-28
> **LHammonds said:**
> For a learning environment, you might want to go with a virtual machine.  

Yes, I had considered virtualization, but since I had spare hardware lying around, I decided to get "physical".

However, the cloud argument is hard to overlook. While I am perfectly capable of getting the hardware and software up and running, I find it hard to resist / ignore a ready-made, professionally setup solution.

Add to that the lure of being able to work on it from anywhere (and any "thing"). The only thing I am worried about are the pitfalls and expense traps; downtime, SLAs etc are not important to me at this stage.

I think I have over-emphasised learning; I would like to restate that I am looking at "experimentation" primarily, and what I glean from this experiment will be put down to learning / experience.
> __________________
How I install a MediaWiki web server
How I install a Zimbra mail server
How I install a MySQL database server
How I install a Nagios monitoring server

The links in your sig seem to be very attractive and very relevant to me: I'm off to read them now.

---

### Post by Lars Noodén on 2012-05-28
One way to use virtualization is to work on you changes locally in a VM and then synchronize to your server.  The server then functions as a mirror.  If you don't like the changes you made in the VM or make too big a mistake, just don't upload the changes and instead roll back to an earlier snapshot.  
 
If you really want to work directly on your production server, then you could do that too, but it's harder to roll back your changes.  On the technical side of things all you need is a hosting service (aka cloud) that provides SSH, PHP and MySQL.  Some will even offer pre-installed CMS like Drupal or Joomla.  Spend the time to shop around, though, if that is your intended direction.  LAMP is a standard offering.

---

### Post by Jonathan L on 2012-05-28
Hi again prshah

> what AMI... barebones install, I would *prefer* not to ... large charges without my knowledge

For what it's worth, actually I would _recommend_ starting with what you call a "barebones" and what I call a "stable" image.  Then your experience is completely portable, though you might struggle a little more in the beginning.  I'd recommend a 10.04 stock 32-bit Intel image; You're listed as being in Chennai, so the nearest AWS place is probable Singapore, so the AMI is ami-6e6f283c.  This recommendation is for the plainest of the plain, which I think is the simplest place to learn a bit about the practicalities of operations.  If what you want to do is run App X, then certainly, get an image which directly runs App X.   I'd recommend you try both.  If you kill everything when you finish for the day, you're only paying for your computers when you're awake.

Charging and surprises: you're charged for hours of uptime, plus Gbyte-months of EBS storage.  When you start an image, you create a (usually small, eg 8 Gbyte) storage for the root.  When you kill the instance (running, chargable, computer), you have to check you've killed the disk too.  With the (very good) web control panel, you have to remember that it keeps each country separate: if you launch an instance in Singapore that will not show if you're looking at the (default) US page.  I've taken a look at one of my development accounts and the bill for May is approx 500 hours of smallest computer ('t1'), which is $12.28 for computers, $5.41 for disk, $0.05 for traffic.  I am not on the free tier, which you would be eligible for, I think.

Yes, they have billing alerts where you get email when you hit a threshold you define, and yes, you can check your bill-so-far for the month.

The main benefit of course is the education and the scalability.  Even without doing anything clever you can really scale up easily: and down, just as easily.

Just to be clear: I have no connection with them, just a very satisfied customer.

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by d4m1r on 2012-05-28
Based on what you are interested in running, I'd recommend 2 ways to move forward:

1) Purchase cheap monthly hosting from a linux provider (such as 123systems.net) and you can access a linux box that is connect to the internet with its own dedicated IP over SSH and install anything you want on it.

2) If you have old hardware lying around, put together a small server box together (specs don't really matter as you shouldn't need an interface) and set it up only on your LOCAL network. This means you wouldn't have to worry about security but could do anything you wanted with it again....


On a separate note, any reason you are looking at Joomla? That is mainly used for commercial websites, if you are interested in just running a personal website, I'd recommend Wordpress instead which is a free blogging software that is really flexible.

---

### Post by prshah on 2012-05-28
> **Jonathan L said:**
> actually I would _recommend_ starting with what I call a "stable" image.  I'd recommend AMI is ami-6e6f283c. I am not on the free tier.

Hope that's helpful.


Yes,very helpful and detailed.

So thanks in no small part to your advice, i will start with the t1 and ami you have recommended. As i understand it, this gives me a [s]barebones[/s] stable readymade server, to which i install joomla, and start preparing my website.

I'm having a hard time believing the free tier is really free (for limited use). I have gone through their details, and it seems i am getting everything i want, free for a year.. what's the catch? However the part about fiscal controls is reassuring.

Do you happen to see any mistakes in my assumption or plans?

---

### Post by prshah on 2012-05-29
> **d4m1r said:**
> On a separate note, any reason you are looking at Joomla? That is mainly used for commercial websites,

Hello, thank you for your input. Yes, I am looking at a commercial website (in the long run), mainly shopping cart and paypal integration.

As mentioned, there are a number of choices besides Joomla, but from what I have read and understand, Joomla has ease of use and a wide library of extentions that I can use to accomplish my ends.

The purpose is rather nebulous as of now, and to crystallize it, I need to DO SOMETHING, rather than sit around continuing to research. If what I'm trying to do doesn't pan out, I can treat the whole thing as a learning experience and move on.

---

### Post by Habitual on 2012-05-29
> **prshah said:**
> ...The purpose is rather nebulous as of now, and to crystallize it, I need to DO SOMETHING, rather than sit around continuing to research. If what I'm trying to do doesn't pan out, I can treat the whole thing as a learning experience and move on.

Sounds like  a perfect candidate for an AWS instance.

---

### Post by prshah on 2012-06-01
Thank you all for your replies.

Based on your inputs, I have taken the leap, and created an amazon account, and have setup a unit in the free tier.

Currently, I feel that I have bitten off more than I can chew, but, with some choking, and a lot of swallowing, I have managed to setup a lamp-server and Joomla.

I'm no shrinking violet when it comes to grappling with technology, but given that EVERYTHING is unfamiliar to me (for example, given EBS capabilities, I don't see the point of S3...), I am beginning to feel like [Sisyphus]("http://en.wikipedia.org/wiki/Sisyphus").

To that end, I plan to document my efforts here, so that some other poor soul like me may benefit from my efforts.

Surprisingly, there is VERY little information on Joomla+AWS, though they seem to be made for each other.

Of course comments and suggestions are welcomed. I am especially interested in tips on hardening my setup (fail2ban, users, Joomla admin hardening).

---

### Post by clay7 on 2012-06-01
I use rosehosting.com and linode.com. At either place, you can get a 512 MB VPS for $19.99/month, and you can cancel at any time. 512 is plenty for just starting out, and if you need more space and/or memory, you can upgrade easily. Plus, if you mess up and want to reconfigure, you can re-image in about 30 seconds and start again with a fresh server. Service from both have been excellent.

---

### Post by spynappels on 2012-06-01
I used the Amazon AWS Free tier for a year and with a micro instance running 24/7, I think I was charged something like $0.02 per month for data transfer, and nothing else. 

Just be aware that with Amazon, or any cloud provider, your server is online to the world, and you definitely need to take some basic precautions to secure the server. This is not an issue for a development server you may have in-house, behind your own router/firewall. You could simulate this on a public cloud system by using a VPN tunnel to connect to the server, and firewalling any other traffic.

I now use Linode, as it works out slightly cheaper for me and I prefer their out-of-band access.

---

### Post by vazduxosbra4kania on 2012-06-01
> **d4m1r said:**
> Based on what you are interested in running, I'd recommend 2 ways to move forward:

1) Purchase cheap monthly hosting from a linux provider (such as 123systems.net) and you can access a linux box that is connect to the internet with its own dedicated IP over SSH and install anything you want on it.

2) If you have old hardware lying around, put together a small server box together (specs don't really matter as you shouldn't need an interface) and set it up only on your LOCAL network. This means you wouldn't have to worry about security but could do anything you wanted with it again....


On a separate note, any reason you are looking at Joomla? That is mainly used for commercial websites, if you are interested in just running a personal website, I'd recommend Wordpress instead which is a free blogging software that is really flexible.

Hi soon i started thinking about website so i bought a domain and hosting for personal site (2.5 Eur per month). But the reason i am actually writing you is because i agree that  you can use wordpress cause, i use it and it is extremily flexible. You can be new to the webdesign world and still build yourself a very slick and good looking site. You can use themes that are already working and change the code in the way to fit your need in the best possible way. Let me show you a subdomain of my site which is created with wordpress - [www.blog.turlakov.com](www.blog.turlakov.com) (keep in mind that this is may be the most simple page u could have, and there are a lot more developed and better looking themes.) ;)

---

### Post by prshah on 2012-06-01
> **spynappels said:**
> I used the Amazon AWS Free tier for a year.. charged something like $0.02 per month ..

you definitely need to take some basic precautions to secure the server. 

Thank you, that information is very useful. 

And yes, I agree with you about the "basic precautions".. in fact, with Joomla being a "big shiny target" (quoted), I definately would like to be over-cautious rather than under cautious.

I am reading through topics on server hardening right now, and would welcome any comments and/or suggestions.

---

### Post by spynappels on 2012-06-01
My main advice would be to set up a VPN tunnel to the instance and only use that for any work you may want to do on the instance.

You can firewall everything incoming except SSH on the main interface, and secure SSH with key-based authentication. Then allow all traffic on the VPN interface and use that for remote access, SCP file transfer and browsing to web content hosted on it.

This will simulate a server on your LAN with no access from the general Internet, with SSH access as a backup.

---

### Post by prshah on 2012-06-02
> **spynappels said:**
> set up a VPN tunnel to the instance

firewall everything incoming except SSH on the main interface, and secure SSH with key-based authentication. 

Thank you, this is useful. I am using SSH with key-based authentication (with relevant entries for AllowUsers AllowGroups, etc).

However, I know nothing about VPN (except that it stands for Virtual Private Network); as far as I understand it, a VPN tunnel allows me to use a remote network as though it is part of my own local network (maybe grossly simplified). If this is the case, then I don't need this as I don't WANT the remote network to be a part of my local network. The more detached, the better :)

I don't plan on sharing any resources from my local network to remote network (yet). I'll keep VPN in mind for the future, though (if the scenrio changes).

If I'm wrong about VPNs, I welcome corrections. Please don't derail the thread by saying I'm correct about VPNs.

---

### Post by spynappels on 2012-06-02
A VPN can also be used to provide secure access to a remote server. By accessing your Amazon instance through a VPN, you will have secure access to it and by denying all non-VPN access, you just make it so it cannot be accessed/exploited from the Internet at large. It means you need to worry less about hardening it as only you can access the apache/Joomla  on your server.

---

### Post by Jonathan L on 2012-06-02
Hi prshah

> taken the leap ...  free tier ... bitten off more than I can chew

Well done!  I promise you it's worth it when you get a grip on it.

> EBS capabilities, I don't see the point of S3
Use whichever is convenient.  EBS is basically a disk which you pick the size of.  S3 is more like a collection of files.  Nice explanations here [http://www.cloudiquity.com/2009/03/differences-between-s3-and-ebs/](http://www.cloudiquity.com/2009/03/differences-between-s3-and-ebs/)

> [Sisyphus]("http://en.wikipedia.org/wiki/Sisyphus")  
You said you wanted to "do something".  Otherwise you'd feel like Prometheus.

Per other people's observations: definitely take some precautions.  Setting up a tunnel into your machine is excellent, but isn't trivial.  I'd recommend starting with simply tightening up the access lists to only accept you own IP addresses (through the AWS control panel.)

Hope you're having fun.

Kind regards,
Jonathan.

---

### Post by prshah on 2012-06-03
> **Jonathan L said:**
> Setting up a tunnel into your machine is excellent, but isn't trivial.  I'd recommend starting with simply tightening up the access lists to only accept you own IP addresses (through the AWS control panel.)

Thank you for those tips and suggestions. These are the steps I have currently taken to harden up the server:

a) Enabled publickey ssh
b) Allowed only a single user ssh access
c) Tightened up ownership and permissions for Joomla files
d) Changed default admin username (for Joomla)
e) Opened ports (AWS) HTTP, HTTPS and a non-standard SSH port
f) Using HTTPS when logging into administrator (backend) on Joomla
g) FTP not enabled (sftp works)
h) Disabled root login for SSH
i) Enabled ufw (firewall), default deny, HTTP, HTTPS and custom SSH open
j) Stopping instance when not working on it (Temporary measure)

Unfortunately, since I am connecting from a dial-up ADSL account, I cannot restrict IP addresses. I can if last octet changes, but last 2 octets are changing (besides which, I am working from a different isp from work, home and mobile). If you can suggest how I can restrict in this scenario, please go ahead. Currently, I think I need something like 58/59.0.0.0 and 122.0.0.0 (last three octets should allow any numbers).

Thanks again for your experienced advice. I hope others can benefit from this information too.

---

