---
title: "My First Server"
date: 2011-12-24
forum: Server Platforms
---

### Post by kamakazi20012 on 2011-12-24
Hi to all that view this post.  And to those who are fixing to celebrate it I want to wish a very Merry Christmas.  

For Christmas, my wife got me a real server.  Well, it's from her anyway even if I picked it out and ordered it :D  The server is a Sun V20z from Geeks.  The information can be found here:

[http://www.geeks.com/details.asp?invtid=V20Z-220X2-R&cat=SVR]("http://www.geeks.com/details.asp?invtid=V20Z-220X2-R&cat=SVR")

I am waiting for it to arrive which should be sometime next week.  I was wanting to know something...since I am new to servers and am wanting to use Ubuntu for servers if the kind people here would help walk me through installing and setting up the Operating System?  

And I've heard it before...it's too much for my needs but I've been wanting a real server for quite sometime now and finally getting one.  And since my college studies involve web designing and interactive media I felt the server could serve me well for my extended studies in HTML, CSS, Flash, Java, JavaScript...etc.  My wife and I are also trying to start our own online used gaming store and I thought that the server could eventually be used to handle the website, orders, and any messages.  

As a last note; I have tried converting my wife's old e-Machine desktop into a server using Windows 2003.  That was a mistake...while it did work for a while it was too picky to setup and I need something more flexible.  I also think it would be a good way to help Ubuntu developers out by confirming another server type that is supported.  I have used XAMPP for Windows and am familiar with it so I do have a small amount of knowledge on how to use it.  I have located and downloaded a PDF version of the server's instructions so I have that if I need it.

I hope to have an interface that is familiar to those who have used commercially-available web hosts but I am not sure how to go about getting something like that.  Anyway, that's the plan so far.  Can't wait until it gets here!  Thanks in advance to those who will offer help.  Cheers!

While I am waiting for the server to arrive, if there are any applications that I need to download please list those so I can have them ready, please.  I welcome any documentation or other learning materials that will help.  ;)  Thanks to all!

---

### Post by Lars Noodén on 2011-12-24
> **kamakazi20012 said:**
> I hope to have an interface that is familiar to those who have used commercially-available web hosts but I am not sure how to go about getting something like that. 

For that, there is the shell.  It's the most powerful and flexible way of managing any servers.  Once you know your way around, you can do anything and even automate it.

One tip: only ever install packages that you get from the Ubuntu repositories.  Don't download any tarballs or other things.  By sticking to the package manager, you will ensure that your machine is easy to maintain and up to date.  The package manager keeps track of versions automatically.

One the hardware, it is nice, but I was psyched that you were ordering a real Sun with [Sparc](http://www.sparc.org/) and all that.  That would have been too cool.

---

### Post by volkswagner on 2011-12-24
With 12gigs of RAM, and your grand future plans, I'd like to suggest running a hypervisor.  You can create individual virtual machines for WebServer, MailServer, DevelopmentServer, etc.

That looks like a sweet deal, I think the RAM alone is worth that price.  I have never seen a server come with that much RAM on Geeks.  I'd be very interested in knowing how load that unit is.  I have a couple 1U servers here that sound like a shopVac running.  Way too loud for home use :(

As mentioned, stick with package manger apps.  While you are waiting for the package to arrive I suggest doing your homework.

Things you can research are VirtualMachines and the different HyperVisors, Xen, VirtualBox, VMware, KVM, etc.  If you go with one of the first three you can easily use one of the many prebuilt VM appliances from TurnkeyLinux.

You will want to know your partition scheme before installing.

The sticky at the top of this thread has a lot of information for running a server.

There are nice how-to's on howtoforge.com.

You will also want to investigate you isp contract.  Are you allowed to run a webserver?  Also check to see if your isp blocks any ports such as port 80.  You will want to become familiar with forwarding such ports on your particular router.

---

### Post by kamakazi20012 on 2011-12-24
@ Lars Sorry to have disappointed you on the Sun server.  But I couldn't possible afford a new server.  I wish I could; no doubt about that.

@volkswagner Yea, I almost purchased an HP for $169 from there and double-checking everything again when the Sun popped up so I went with it.

I will view those sites and the owner's manual to the server has already been a big help.  I'm not too worried about the ISP has I plan on keeping this on a private home network for the time being for learning purposes.  As long as it can allow me to practice HTML, CSS, JavaScript, and Flash based web page designs it will be a huge benefit for me as those are what I am studying for a career.  All the server has to do is deliver to the computers within the home network.  I have also considered using it as a way to create back-ups of all home computers.

---

### Post by Lars Noodén on 2011-12-24
volkswagner mentioned [virtualization](http://www.oracle.com/technetwork/server-storage/solaris10/containers-169727.html).  The sparc servers running Solaris have a really good VM.  The x86-based ones probably do too.  That way when you want to try an experiment you can start with a clean snapshot and delete it when you are done.  The manual is about 2-3cm thick printed.

---

### Post by spynappels on 2011-12-24
Those SunFires will also run ESXi very nicely, it is what we use at work for our lab systems and run Solaris on top.

---

### Post by drdos2006 on 2011-12-24
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. Uses Webmin to allow your browser to connect and modify your server settings.

As you install your server you need to allow Apache to be installed for web development.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server after your operating system is loaded..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by memilanuk on 2011-12-24
kamakazi...

That sure looks like a sweet machine for a home network.  Possibly a bit overpowered for 'just' learning web development, but no doubt you'll find other ways to put it to work! 

A couple questions for you, if you don't mind.  I've been kind of thinking about something similar - getting some dedicated (albeit used, to keep costs down) server hardware to replace the old 're-purposed' desktop PCs I have downstairs in my basement.  Primarily I'm curious how/where you plan on storing this beastie... I was under the impression that rack mount servers tend to be somewhat on the hot/noisy end of the spectrum?  Are they okay just being laid flat on the table (or stood up on their side, etc.) or does that screw with their cooling air flows?  How noisy are they really - obnoxiously so, or tolerable?

TIA,

Monte

---

### Post by boast on 2011-12-24
> **volkswagner said:**
> I'd be very interested in knowing how load that unit is.  I have a couple 1U servers here that sound like a shopVac running.  Way too loud for home use :(


I'm curious as well. Would love to get some rack servers, but scared of how loud it might be. I don't have a garage/basement/location I can run some cat5 to and store them.



> **volkswagner said:**
> 
There are nice how-to's on howtoforge.com.




+1. But its also more fun to learn on your own than mindlessly following a tutorial.

---

### Post by kamakazi20012 on 2011-12-24
Wow...ask and you shall receive!  I am amazed at all the wonderful feedback and help I am getting...it is very much grateful!  So, thank you for that.

As far as how noisy this machine is; I really won't know until I receive it from FedEx, remove from box, and plug it in.  But out of about a dozen different models I looked over, the one that I picked has less cooling fans so that should help control the noise level.  And not all servers are noisy; an old family friend had one they found on Craigslist for about $50.  I can't remember the brand but I remember it being about half the size of all the 1U units I looked at.  It was quick and rather quiet for a server.  

As for where I plan to place it; a neighbor had moved and gave us his old computer desk.  The desk right now is holding 2 19" TVs and about 2 game consoles.  The bottom of the desk (where one TV currently is sitting) is a large opening.  There are no enclosed spaces on the desk; everything is open so the server will have plenty of air flow.  And since this is right next to my entertainment system where our AT&T 2Wire Modem/Router is located, the connections will be right at my fingertips.  I plan to place the server on the bottom shelf of the desk.  I don't have a rack mount enclosure ... yet.  

I do know that when a computer is placed in a small enclosure the sound level is increased a little (unless it has a door that can completely enclose the computer).  I figure the more open space a computer has, the less noisy it can be.  It also depends on the condition of the cooling fans as some can wear out and will make a weird vibrating noise from wore out bushings.  

What I liked about the internal setup of the Sun Fire was the placement of the cooling fans.  Other models had the cooling fans up front and the CPUs in the rear.  Those also had like 6 or more fans to keep the system cool.  The server I got looks like it has four fans with the CPUs right behind them.  So I expect the system will not be as loud and will hopefully run cooler.  As it is, I'd rather have AMD than Intel anyway.  And I have plenty of laptops in my possession so I can dedicate one for server maintenance (2 Acers one of which runs Ubuntu, One Compaq and one Toshiba Satellite...all run 64-bit AMD processors of either Athlon X2 or Sempron except one Acer which uses Intel).  And my wife just got a new Acer laptop with a Quad-Core AMD processor which has been very impressive (wish I would have kept it for myself :lolflag:).  Naa...that was her gift from me.   

The only real downfall I see with the Sun Server is that it comes with only one hard drive.  I was wanting to try and keep an OS on one drive and data on another...but I can always add that later.  The only thing I could not find is if the drives are hot-swap.  But, with 12 GB of RAM...even if it is of the slower DDR memory, I will have more RAM than I will know what to do with. 

The server will be used for school learnings, any outside development that I may try (I enjoy creating games and music) and will be used for storing back ups of my college work.

---

### Post by kamakazi20012 on 2011-12-25
> **memilanuk said:**
> kamakazi...

That sure looks like a sweet machine for a home network.  Possibly a bit overpowered for 'just' learning web development, but no doubt you'll find other ways to put it to work!

Thank you!  And thanks to my wife for getting it for me (even if I placed the order).  And I've heard from other forums that I have went a bit overboard with the power but if you are going to do something might as well do it right the first time. 

> A couple questions for you, if you don't mind.  I've been kind of thinking about something similar - getting some dedicated (albeit used, to keep costs down) server hardware to replace the old 're-purposed' desktop PCs I have downstairs in my basement.  Primarily I'm curious how/where you plan on storing this beastie... I was under the impression that rack mount servers tend to be somewhat on the hot/noisy end of the spectrum?  Are they okay just being laid flat on the table (or stood up on their side, etc.) or does that screw with their cooling air flows?  How noisy are they really - obnoxiously so, or tolerable?

TIA,

Monte

I think I already answered your question, but to make it a bit more personal I will answer it again.  First of all, I don't think you can go wrong ordering a used server like I did.  Just make sure you will get something that you will enjoy having or else what is the point?  I went through all the servers that Geeks had for two days and placed the ones to compare in a shopping cart.  I was about to pick an HP with dual Xeon processors and 8 GB RAM but thought I would check to make sure I 
didn't miss anything.  That's when a few Sun Fire server configurations popped up.  They must have been added after I had
placed a few in a cart because all the servers before that were either HP, Dell or IBM.  I went with the Sun because of the name and the RAM it had.  I can work with a single hard drive for a while...no big deal there.  I do recommend if you can get one with more than one hard drive to do so.  Most of the sites I've viewed to get reconditioned SCSI hard drives cost more than I paid for the server with shipping so get the most bang for your buck if you can.  I went with the AMD models because I am an AMD fan...that's all there is to that.

Before I place it in a permanent place, I will more than likely test it out first to get to know it.  This will involve physical contact with the server, popping the top to check it out (make sure it is clean on the inside...no dust bunnies) and to get a mental map of where everything is on the inside should I need to.  Once I am comfortable with using it and setting it up I will find it a permanent home.  I don't mind having to reinstall an OS over and over...and I expect to have to once it arrives until I "know" what I'm doing LOL.

I live in a one-bedroom apartment with my wife.  The apartment is considered an apartment for handicap people which my wife is disabled so I don't have a lot of options open to me.  I can buy some wood and make a custom server shelf if I have to.  But, like I said, I think I will know more after I have taken it out of the box and actually seen it.  

Noise?  I have heard laptops and desktops be very noisy depending on model and where they were located.  I remember a friend of mine setting up his desktop in a computer desk that had a completely enclosed space for a tower.  Big mistake!  No air flow and the enclosure only seemed to amplify the sounds the tower made (fan/hard drive spinning and any optical discs inserted).  Getting hot?  That is to be expected from any electronic device to be honest.  But I can see your point; double the processors should mean double the heat.  But I believe that if a location is properly planned out then the heat won't become a factor.  Yes, it might get warm to the touch but if it is allowed a lot of open space then I don't think it will pose a threat.  I've had laptops that literally left red spots on my lap from them getting hot.  If nothing else, I can rig up some 12" cooling fans on the outside of the server to help force more cool air into the system or place them on the back to pull the hot air out quicker.  

On a side note...the instructions to the server I am getting has to be the most detailed set of instructions I have ever seen, period!  Why don't they make instructions like that more often?  That don't mean Ubuntu documents...those are top notch in my book!

---

### Post by kamakazi20012 on 2011-12-26
After reading the instructions and user's manual I need to make a correction.  I had mentioned that this server has 4 cooling fans.  I was way wrong.  I didn't see them in the photo on Geeks but this system has 8 fans.  And I'm not sure how many are in the power supply.  So, as far as the noise level is concerned...I will let those who are curious know how noisy this server is when it arrives and I fire it up.  I just hope it doesn't get treated like the computer FedEx handled with care.

---

### Post by Lars Noodén on 2011-12-27
I'm also curious as to the noise level.  They tend to be comparable to regular house vacuum cleaners.  You may have to put it in a closet and run a long cable to it.

---

### Post by rubylaser on 2011-12-27
We had a bunch of Sunfire X2100's here are work (1U).  Those were among the loudest servers I've ever been around.  I had to take a couple home to set them up in the past, and even running in the basement, they could easily be heard in the main living area of the home. Ours were higher pitched than a vacuum and as result even more annoying.

I hope yours is MUCH less noisy :)

---

### Post by collisionystm on 2011-12-28
try out Zentyal

---

### Post by kamakazi20012 on 2011-12-28
Well, the server arrived today while my wife and I were out getting something for dinner.  The box was literally blocking our door when we returned.

As for the machine...it's bigger than I had expected.  I am not sure where exactly I am going to permanently place the server.  Right now, and I know it's not a good place for it, it's in our living room floor right in front of my desk.  I didn't get any extra cables and used the extras I had laying around.  I couldn't get logged in to the SP management.  Keeps coming back with Connection Denied.  Not sure what is going on there. 

Ubuntu Server 64 is installed and functioning.  Accessing the IP address using a Windows PC and Google Chrome returned a page that said "It Works!!"  So I assume that it is working.  Now I just need to figure out how to connect to it with FileZilla FTP (Need to find the FTP address) so I can start uploading some stuff to work with.  If the memory on this thing is only running at 400 MHz, it would fool me...it's rather fast so far.  

Noise?  Yea...it needs to be in a shielded room.  It won't fit in our closet but it will fit under the bed (already tried without it being on).  But it's good to know it is up and running and ready.  Ubuntu supports a Sun Fire V20Z server...it's official as far as I am concerned.  I do believe that most of the noise from the fans is from worn out bushings.  It is really noisy when first fired up but after a few seconds it seems to die down a little.    

I don't have a public-access connection yet so the server is on a private network at the moment.  And I am having to access it using the IP numbers for now.  

If anyone has any pointers (would like a graphic interface) I'm all ears (or eyes).  Thanks for the help and I am looking back over those after posting this.  So far, I am proud to have it.  I'll post pics of it soon.

---

### Post by memilanuk on 2012-01-23
Any updates, now that you've had it a little while?  Have the rose-tinted glasses faded yet? ;)

---

