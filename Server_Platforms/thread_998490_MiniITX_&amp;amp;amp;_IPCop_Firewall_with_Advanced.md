---
title: "MiniITX &amp;amp;amp; IPCop Firewall with Advanced Proxy add-on?"
date: 2008-11-30
forum: Server Platforms
---

### Post by handy on 2008-11-30
Hi, I want to set up IPCop with Advanced Proxy, to use the box as a firewall & caching web proxy server.  

My query here relates to meeting the minimum hardware requirements to run the Advanced Proxy - Squid, addition to IPCop on my very small home network.

There will rarely ever be more than 2 people online at a time, though there will be P2P, & utube/google video being used occasionally.  Most of the time I am the only user of the internet in our house, there is no business related server here, it is just a *standard(?)* home network that happens to include a distro hopper. :-)
 
So, would one of these [***_Via MiniITX boards_***]("http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=202") (which I know will handle the IPCop) be able to deal with the caching load that Squid will place on it in our small network?

I was thinking of booting IPCop from a flash card of some description, & a SATA WD 36Gb Raptor for the cache.

What do you think?

***[Edit:]** [**_This page_**]("http://ubuntuforums.org/showpost.php?p=6303994&postcount=29") has my current working settings on it, if you want to get past the getting there bit. :-)*

---

### Post by cariboo on 2008-12-01
If you've got an old PII sitting around it would work just as well as a mini itx board, and be way cheaper to boot. Network I/O really doesn't tax the cpu much so if IPCop still has a web interface you shouldn't have any problesm with an older/lower powered computer.

Jim

---

### Post by handy on 2008-12-01
> **cariboo907 said:**
> If you've got an old PII sitting around it would work just as well as a mini itx board, and be way cheaper to boot. Network I/O really doesn't tax the cpu much so if IPCop still has a web interface you shouldn't have any problesm with an older/lower powered computer.

Jim

Thanks for your reply Jim. :-)

I have been doing more reading since I made this post, & was starting to gather that processing power really isn't important for the firewall & the caching web proxy; your post thankfully confirms my slowly coalescing understanding.

If I may ask you another question or two; is choosing to use the same server as a NAS, counter productive?  & would a NAS box benefit from more processing power?

I'm thinking I'll go to the recyclers tomorrow & hopefully be able to pick up a suitable old box to setup with IPCop & the Advanced Proxy - Squid extras.  I'll evaluate it for a while & continue to investigate the NAS combination as it certainly would be convenient to not have to dedicate & power another box for the job.

Something that I like about the MiniITX solution, is the low power consumption, which over the years of running 24/7, adds up, & may pay for itself & some (I haven't done the maths).  

If the Firewall/Proxy is a NAS as well, I'd eventually be running raid 5 with 4 SATA-2 drives & a compact flash boot card, so the thing is going to be getting up near 200watts at its worst.  Certainly not 24hours a day though. :-)

I look forward to any additional input you may have Jim, as I have no experience in this area of computing & enjoy learning from those that know.

---

### Post by volkswagner on 2008-12-01
I measured the draw of several machines. All were at idle, one PATA hard drive and one PATA cdrom.

Pent II 400 Mhz ~ 35-40 Watts
Celeron 500Mhz passive cooled (no cpu fan) ~ 35-40 Watts

Pent 4 various 1.6 Ghz-2.4Ghz and and Athlon K6 700Mhz all were hovering 95-110 Watts.

Go with the Pent 2 for CPU power to electrical power advantage.

I just got an Intel Atom based board.  I was needing the cpu power to add a photo archive site (LINpha) on my web server (currently the pent 2 400).  I have to say I love the capability of the Pent2.  For basic web pages it works great.  I still may set it up as a firewall/Router.  I am just not happy with the limited options on my current router.  Gotta love all those PCI slots, and up to 4 PATA drives.

I really liked the idea of the passive Celeron (less noise and dust intrusion). It just seemed more sluggish than the Pent2.  I did not do any real world test to confirm it though.  It could have been the fact the Pent2 did not have onboard vid/sound as the celeron did.  Also the Celeron was a branded Compaq (locked down bios) vs. custom built Pent II.

I have one question which I hope fits this thread.

Can these old Pent 2 boxes push Gigabit lan?  Do their PCI bus speeds support it?  This would not be for disk usage, only as a Gigabit router.

---

### Post by handy on 2008-12-01
Well I found a Dell Optiplex GX150 at the recyclers for $5-, it is a Pentium III, clocked a bit under 731Mhz, with 256Mb of PC133 RAM a 10Gb Seagate drive, a working (non original) CDROM drive & a floppy.
I've added a 3Com 10/100 NIC.

It was booting very slow, but after playing around in the BIOS & the drive Jumpers it is as it should be now.  It boots up to login in XP Pro', which is a good sign.

So now I'll get about downloading, installing (hopefully I don't have any hardware ID problems with the NIC's) & setting up IPCop.

I'll report back any problems or hopefully just my success story. :)

---

### Post by handy on 2008-12-02
I have installed IPCop, it is showing a fast flashing light on my hub/switch but it won't let me access it via its IP address from another machine?

I think it is working, but I can't configure it beyond the setup.

Hmmmmm...

---

### Post by handy on 2008-12-02
My $5- recycled server has an intermittent freeze.

Which is probably why it was at the garbage dump to begin with I guess. :-)

---

### Post by carbm1 on 2008-12-02
I use IPCop here at home and at work.

At home I have an Asus Terminator 1, 800Mhz VIA C3 Processor, 512MB RAM, and a 80GB hard drive. I have most, if not all, of the addons installed. Never had a single problem.  I have approx 7 computers here on at any given time.  The real winner for me is the Update Accelerator addon.

At work we use a Dell OptiPlex GX270, 2.8Ghz P4, 2GB RAM, 500GB Hard Drive. The hard drive is overkill but it was the only larger one I had laying around. We have a little over 400 computers running with this.  Of course we only have a T1 so I'm not really sure what we could really push through this.  It does everything we need including VPN between a couple of offices and Road Warrior VPN's.

Just some helpful notes...
[http://www.carbm1.com/?cat=9]("http://www.carbm1.com/?cat=9")

---

### Post by gTinker on 2008-12-02
handy, just a point I'd like to mention. Unless a version newer than the one I run is able to do it, IPCop takes over the whole machine, you couldn't run a file server on it at the same time. And in my opinion, a hardware firewall should be just that and only that.

---

### Post by handy on 2008-12-02
Thanks for your post Carbm1.

I have had my Optiplex running Memtest86 for 2.5 hours so far, with out failure of any kind.  I'll let it go all night, if it makes it through the night without failing, I guess I'll look a little further into the machine, replace data cables maybe try different drives in the hope that I may salvage it.  First thing I did when I got it home was blow all of the dust out of the thing with compressed air.

Anyway, if its not this machine, I'll find another for the job.

If I can't get it reliable tomorrow, I'll temporarily setup a drive in my 2nd box & see how I go.

[I]**[Edit:]**

Thanks for the link, I just caught it, am going to read it now. :-)[/I]

---

### Post by handy on 2008-12-02
> **gTinker said:**
> handy, just a point I'd like to mention. Unless a version newer than the one I run is able to do it, IPCop takes over the whole machine, you couldn't run a file server on it at the same time. And in my opinion, a hardware firewall should be just that and only that.

Thanks, I was wondering if I would be able to get into the system with IPCop running, & today when logged in as root I really had access to to next to nothing on the system; ls displayed not a thing! :lolflag:

---

### Post by carbm1 on 2008-12-02
gTinker, I have to agree. You should not try to do any other moding to the IPCop setup for use as a NAS. It your first line of defense.  You should seriously consider using something else like FreeNAS or something similar to setup a NAS on your network. 

I run that IPCop firewall box on that low power consuming VIA c3 processor.  I run Ubuntu 8.04.1 Server on a Compaq Proliant ML-310 with a 500GB hard drive for my NAS.

---

### Post by gTinker on 2008-12-02
[QUOTE=handy]Thanks, I was wondering if I would be able to get into the system with IPCop running, & today when logged in as root I really had access to to next to nothing on the system; ls displayed not a thing![/QUOTE]

Yes, a firewall is supposed to be secure, eh? ;)

You will do all your configuration of the firewall through the browser interface. I note you only mentioned one NIC, you're going to need at least two to interface a broadband connection to your local network.

---

### Post by handy on 2008-12-02
> **gTinker said:**
> Yes, a firewall is supposed to be secure, eh? ;)

You will do all your configuration of the firewall through the browser interface. I note you only mentioned one NIC, you're going to need at least two to interface a broadband connection to your local network.

Yes, I have 2 NIC's in it, interestingly I had an old 3Com card which was the same as that onboard.

I could gain no access via a web browser, so perhaps I misunderstood the instructions somewhere?  I have a seimens speedstream 4200 modem/router, I read nothing about any settings for other machines/browsers or modem/routers, I guess that is the transparent part eh?

Anyway, I'm off to bed, I expect that tomorrow I may have a question or two, I hope you don't mind dealing with a first time user of IPCop? :-)

***@carbm1:***  I read your IPCop blog, it is great, I look forward to being capable of using some of your techniques myself in the future.  First I had better work out how to install it properly... ;-)

---

### Post by gTinker on 2008-12-02
[QUOTE=handy]Yes, I have 2 NIC's in it, interestingly I had an old 3Com card which was the same as that onboard.
[/QUOTE]

Sometimes it's easier if they are quite different, that makes it easier to know which is which. Should still be able to work with two the same though.

[QUOTE=handy]
I could gain no access via a web browser, so perhaps I misunderstood the instructions somewhere?  I have a seimens speedstream 4200 modem/router, I read nothing about any settings for other machines/browsers or modem/routers, I guess that is the transparent part eh?
[/QUOTE]

Well, this is going to be a bit different from a normal configuration. Normally, the IPCop box (which also acts as NAT router and does the DHCP for the network) sits in the place of that speedstream. Often broadband gateways (modem/router) have their own NAT and DHCP functions as well as a built in firewall. I'm not familiar with the speedstream but are you sure you need to use the IPCop box on a two seat network? You are definitely not going to want two boxes act as DHCP servers on the same network, that might even have been the source of your no access issue. 

[QUOTE=handy]
Anyway, I'm off to bed, I expect that tomorrow I may have a question or two, I hope you don't mind dealing with a first time user of IPCop? :-)
[/QUOTE]

We were all first time users at some point, there is a time tested and proven cure for ignorance. You already seem to be using it, reading documentation and asking questions. :)

---

### Post by handy on 2008-12-02
> **gTinker said:**
> 
Sometimes it's easier if they are quite different, that makes it easier to know which is which. Should still be able to work with two the same though. 

I picked up another old(er) box from the recyclers this morning, it is a Cyrix 200Mhz CPU, it had 32Mb/72pin RAM which I upgraded to 128Mb PC100 (it takes both kinds or memory) I put a couple of NIC's in it this time a Digital Tulip & an Intel pro/100+, it also only has 2.75GB HDD.  Boy is this machine noticeably slower than the Optiplex.

> **gTinker said:**
> 
Well, this is going to be a bit different from a normal configuration. Normally, the IPCop box (which also acts as NAT router and does the DHCP for the network) sits in the place of that speedstream. Often broadband gateways (modem/router) have their own NAT and DHCP functions as well as a built in firewall. I'm not familiar with the speedstream but are you sure you need to use the IPCop box on a two seat network? You are definitely not going to want two boxes act as DHCP servers on the same network, that might even have been the source of your no access issue. 

Yes, the speedstream provides NAT & some firewall functions as well.  I wonder if it is possible to turn the conflicting parts off in the modem/router?

I would like to set up the IPCop box to its ability to be a caching web proxy, apart from the other things that it does so well.

Apart from the IPCop box, I have 3 machines permanently connected to the net, plus there are 2 notebooks & I would like to build a NAS box.

I have the time, & would like to learn about setting up these little servers.  My experience in years gone by never got me past setting up & maintaining other people's windows based office LAN's with a simple file/application server.

Which taught me that setting up a windows network crosses the line of what is called sane, as you quite often had to redo/undo/redo exactly the same thing, in exactly the same way, until the windows system populated LAN chose to give you the result you were being paid for!

> **gTinker said:**
> 
We were all first time users at some point, there is a time tested and proven cure for ignorance. You already seem to be using it, reading documentation and asking questions. :)

Thanks :-)

[I]**[Edit:]**  It's been an over an hour since I wrote the above, which I had to save on my machine; as I started playing with the speedstream which required the loss of my internet connection.

In the speedstream I turned off the NAT/Firewall/DNS routing, & then reinstalled  IPCop in its box, attempting to get my numbers right, but I ended up without connection to the internet & had to just plug the speedstream back into the hub/switch.

I'm starting to loose enthusiasm for this one, my brain is tired & there is something that I'm not seeing. :-|[/I]

---

### Post by carbm1 on 2008-12-02
Are you on cable or DSL internet?

If you are on cable...
At the console of the IPCop box you should have set it up as a RED + GREEN network.  You should have set a LAN number (10.x.x.x or 192.168.x.x).  The GREEN NIC should be plugged into your switch (make sure its only a switch not a router).  You should then be able to ping the IP you assigned to the GREEN NIC.  Once thats done you should be able to go to [http://X.X.X.X:81](http://X.X.X.X:81) (replace x.x.x.x with the IP address).

By default IPCop will automatically use DHCP on the RED. Which your ISP should provide.  The RED should be plugged into your (now in bridge mode) speedstream modem.

Hope this helps a little...  We need to make sure your able to ping the box from inside even if the internet isn't working.

IPCop is a great project.  I hope you don't give up on it too soon.

edit: To re-enter the setup just type 'setup' at the bash prompt.

---

### Post by handy on 2008-12-03
Thanks for your reply & encouragement carbm1 It really does go a long way. :-)

I'm on DSL.

I have been setting up RED + GREEN.

Have been using a 192.168.254.1 on the IPCop box.  The IP of the speedstream is 192.168.254.254. **[Edit:]** [I]I just pinged it from another machine on the LAN, then I tried to access it from the browser where I had to get past the invalid site certificate stuff & now I have access to the IPCop box via the browser. yahoo! 

I've not connected it to the speedstream yet, & I'm understandably told by IPCop that the profile has errors. :-) /edit[/I]

The cheap 8 port switch that I'm using calls itself a switch?  I do also have an HP Procurve 2124 which also calls itself a switch, (I tend to believe it on that one) so I'll plug the HP in then & have a go at pinging the box.  I will have to edit the settings in the speedstream again.

I just looked & there is a Bridge Mode switch in the speedstream's setup, so I will select that (I know I don't have to tell you that I don't know what I'm doing here :-))

Whilst I continue to get the great help like you & gTinker are offering me, I'll hang in there.

Thanks again.

I'll go & have another go at it, this time I will write down all of my settings, so that I can give an accurate report.  I suspect that you will be able to see what are my (obvious to you) :-) mistakes, which I reckon could cut this process's time down dramatically... :D

---

### Post by handy on 2008-12-03
Well I had my first look around the IPCop browser interface, it looks good, all that is yet to be learned.

I edited my speedstream again - disabling the DHCP server, turning of NAPT, Firewall & chose Bridge Mode, which had the dramatic effect of locking me out of the speedstream IP completely!  

Of course my IPCop config is still wrong, so I had to reset the speedstream back to defaults, which has taken me about 3 hours to recover from. :lolflag:

I can see that I really need to know what I am doing before I push the Bridge Mode button again.

I have taken notes of the speedstream's settings, so I should be able to recover somewhat quicker next time.  I really should have had a record of my ISP's settings for it anyway.  It is more complicated than some I have seen.

---

### Post by gTinker on 2008-12-03
[QUOTE=handy]Of course my IPCop config is still wrong, so I had to reset the speedstream back to defaults, which has taken me about 3 hours to recover from.[/quote]

As I mentioned, I don't know anything about the speedstream you have but these things usually have a reset switch (often it is recessed so it can't be operated accidently). If it's there it operates differently from a power cycle reset, the reset switch puts the box back at defaults, that could save you the three hours for more productive testing.

[QUOTE=handy]
I'll go & have another go at it, this time I will write down all of my settings, so that I can give an accurate report. I suspect that you will be able to see what are my (obvious to you)  mistakes, which I reckon could cut this process's time down dramatically...  [/quote]

Great idea, this discussion has become complicated enough with various hardware that a clear representation of your proposed network could be useful. Could you work up some sort of description of your network architecture? For example a list, in order of connection, of the hardware and the settings. Something like this could help us visualise the situation

Having a graphical representation of your network architecture could be useful for you in the future as it becomes more complex and after it has been a while since you set it up.

It looks like you are getting close if I understand your posts correctly, you've managed to establish connection from your Ubuntu through the switch to your IPCop box, hang in there. You've probably already learned a vast amount of new information.

@carbm1,
Do you think we could replace the speedstream with the IPCop box since he's having trouble with bridge mode?

---

### Post by handy on 2008-12-03
> **gTinker said:**
> 
As I mentioned, I don't know anything about the speedstream you have but these things usually have a reset switch (often it is recessed so it can't be operated accidently). If it's there it operates differently from a power cycle reset, the reset switch puts the box back at defaults, that could save you the three hours for more productive testing. 

Yes, I had to reset the speedstream to be able to access the setup via the browser again.

Due to the reset it took me a long time to be able to get the right settings in to make it work again, as it has a quite a complicated setup procedure (which I have made note of for future reference like I should have when I initially set it up a couple of years ago).

> **gTinker said:**
> 
Great idea, this discussion has become complicated enough with various hardware that a clear representation of your proposed network could be useful. Could you work up some sort of description of your network architecture? For example a list, in order of connection, of the hardware and the settings. Something like this could help us visualise the situation

Having a graphical representation of your network architecture could be useful for you in the future as it becomes more complex and after it has been a while since you set it up. 

I agree, things that I once new, have to be learned all over again after what seems to be a progressively decreasing amount of time, as I get older... :-)

Tomorrow I will put together all of the information that I can regarding the details of the topology of my home LAN, including my IPCop setup configuration, which may be in error, though the speedstream seems to be a major obstacle, whether that is the sole problem or not is yet to be revealed.

> **gTinker said:**
> 
It looks like you are getting close if I understand your posts correctly, you've managed to establish connection from your Ubuntu through the switch to your IPCop box, hang in there. You've probably already learned a vast amount of new information. 

Yes, it really gave me a lift to finally be able to access the IPCop box from the browser of my main machine.  Which is currently running Arch & Leopard, as it is a 24" alu' iMac.  As previously stated, I have started making a record of my settings, & will attempt to make a very clear, concise & complete record of all of my settings with regard to the IPCop setup, the speedstream setup (possibly in multiple modes) & all other settings for the LAN as it develops. 

> **gTinker said:**
> 
@carbm1,
Do you think we could replace the speedstream with the IPCop box since he's having trouble with bridge mode?

I didn't even know that was in the realm of possibilities, I certainly would like to be able to remove the speedstream from the LAN altogether if it is possible?  It is not a nice piece of hardware/firmware.

Thank you both once again, I appreciate your help, as this is a rather demanding little project, & without you, I would have had to toss it in some time ago.

---

### Post by carbm1 on 2008-12-03
I believe the information your looking for is here:

[http://www.ipcop.org/1.4.0/en/admin/html/section-dialup.html]("http://www.ipcop.org/1.4.0/en/admin/html/section-dialup.html")

Your modem needs to be in bridge mode. Then you should pass your username/password for your ISP by selecting PPPoe and it should connect and show connected on the main page of your IPCop.

I used IPCop for nearly a year with DSL using the method above.  I'm now on Cable and still have no worries.

I hope this points you in the right direction.  Please let me know and if this doesn't get you... we'll look into it further.

Sorry it took you so long to get the modem out of bridge mode.  The IPCop takes over all the functions except for the DSL connection so it needs to be in bridge mode.

edit:  The above is a good read... but I think even reading that your going to leave out a step because I've been looking through my IPCop and I can't seem to find the settings for the PPPoe. I don't think if your on DSL that your a GREEN + RED... but i'm not sure. I'll look into it more to give you a better idea of what to do.

---

### Post by handy on 2008-12-03
Thanks for the info', the link looks extremely helpful.  I think from what I have read, that DSL is fine with RED + GREEN.

Could you please confirm my understanding of IPCop & Bridge Mode;- when I switch the speedstream to Bridge Mode, the modem router becomes very limited in its capacity, it is essentially just a modem & all of its configuration is handled via IPCop?  

Have I got the gist of it there?

Thanks.

---

### Post by gTinker on 2008-12-03
[QUOTE=handy]I agree, things that I once new, have to be learned all over again after what seems to be a progressively decreasing amount of time, as I get older... :-)
[/QUOTE]

I hear you on that! I retired two years ago and I have experienced the acceleration you mention.

On the other hand, you have exhibited, patience, logical thinking and approach to the problem and a desire to help others to help you. It is a good example to set in the forum and often the knowledge to do so comes from life experience.

---

### Post by carbm1 on 2008-12-03
ok, its funny how things come back to you. I was at work working on something completely different when it popped in my mind.

Yes your modem needs to be in bridge mode. Your IPCop takes over all the functions of NAT, DHCP, routing, etc. You do need to be on a GREEN + RED network.  

At the console type 'setup'. Select 'Networking'. Select 'Address settings'. Select 'RED'.  Then select 'PPPOE'. 

This should get you where in your web gui you can type in your PPPoe username/password for your ISP.  In order to enter that information on the DIALUP page you need to go to the main screen when you first sign-in and click on 'disconnect' first.  Then after you get your PPPoe information entered on the dialup page you can go back and 'connect'.

That should get you where you want to be.  I hope to add more stuff on my website about where to get the plugins and how to install them.  If your interested that is.

---

### Post by gTinker on 2008-12-03
andy,

I looked up the speedstream and now I understand why it is called a router, the key point for us is that it has one ethernet port. After seeing what is available I absolutely agree with carbm1 that the way to do what you want is set bridge mode, that makes the unit virtually transparent but will allow you to maintain a persistent connection with IPCop for whatever systems you plug in to the switch.

I'm guessing that the next thing you will want to do is add wireless. Might as well add another NIC to the IPCop box now and set it up with a blue net, then all you will have to add in future is a wireless access point to have a wireless network isolated from your local LAN. The wireless LAN can have Internet access but access to your local LAN only if expressly allowed. You mentioned a couple of laptops, probably at least one of them has some kind of wireless, eh?

---

### Post by handy on 2008-12-03
> **carbm1 said:**
> 
At the console type 'setup'. Select 'Networking'. Select 'Address settings'. Select 'RED'.  Then select 'PPPOE'. 

I checked that out & I had already selected PPPoE for RED.

> **carbm1 said:**
> 
This should get you where in your web gui you can type in your PPPoe username/password for your ISP.  In order to enter that information on the DIALUP page you need to go to the main screen when you first sign-in and click on 'disconnect' first.  Then after you get your PPPoe information entered on the dialup page you can go back and 'connect'. 

Thanks for that, it got me to that page where I could setup everything ***except*** VPI=8  &  VCI=35 ?  Interestingly *Figure 2.5. PPP Settings* on [***_this page_***]("http://www.ipcop.org/1.4.0/en/admin/html/section-dialup.html#section-ppp-settings") shows the settings that are not displayed on my IPCop installation? 

> **carbm1 said:**
> 
That should get you where you want to be.  I hope to add more stuff on my website about where to get the plugins and how to install them.  If your interested that is.

A great deal of thanks for the time you have contributed helping get there, I think I am really close at this point, there is just the above mentioned VPI/VCI unknown & I wouldn't be surprised if my DHCP settings are wrong, I'll post the details in the next post in the hope it aids viewing clarity. :-)

Also, I am very interested in the Advanced Proxy add-on & possibly others too, but if I may I'll ask you about that stuff after I'm up & running?

---

### Post by handy on 2008-12-03
> **gTinker said:**
> 
I'm guessing that the next thing you will want to do is add wireless. Might as well add another NIC to the IPCop box now and set it up with a blue net, then all you will have to add in future is a wireless access point to have a wireless network isolated from your local LAN. The wireless LAN can have Internet access but access to your local LAN only if expressly allowed. You mentioned a couple of laptops, probably at least one of them has some kind of wireless, eh?

So far I have managed to avoid the wireless technology. :-)  When I used to fix other people's computers, it was just starting to become popular, my extremely limited experience at that time indicated that the wireless networking technology was very much in its infancy & so I avoided it & where I could advised customers to wait a while so as to avoid the very real possibility of frustration & costs that may bear no positive result.

Anyway, that was well over 3 years ago now, & I'm sure the technology has improved dramatically.  I see the possibility for the use of wireless at our little house, & perhaps one day in the future I will do something about it, but really have no plans to at the present.

:lolflag: So all those words said maybe one day we will use wireless here for something.  My wife & daughter have Apple notebooks, we also have 2 iMacs, I perceive potential trouble due to Apple's desire to lock out most anything that they don't own!

I do like how IPCop handles the situation though, & that may diminish the time before I finally relent & give wireless a go.

---

### Post by handy on 2008-12-03
*I make minor modifications/updates to this page. Have done for the last couple of years. This page may also seem a little funny to anyone who has read the thread from the beginning. The reason that, that may be so is that this page is the one I link people to occasionally so it is a working summary.*
_____________________


**The following settings on this page are what is working for me now, thanks to the help I have received in this thread with one piece of info coming from the IPCop forum:**
 
A description of the home LAN follows:

There are 3 desktop machines; 2 x 24" alu' iMac & a box I built myself mostly used to test distro's these days, (aren't drive drawers a wonderful invention :-)) & a PS3. These 3 are constantly connected to the LAN, there is also 1 Apple notebooks that is rarely connected to the LAN.

Additionally there is the IPCop box, which is still running strong 2 years down the track (as of this update). When it dies I have another Athlon 700 already setup to take its place. 

Eventually I expect that IPCop will make an ARM compatible version which I certainly look forward to. I measured the energy usage of the PIII, & it costs ~$53/year here in Oz.

I used a FreeNAS box for a year or so, it has now been replaced by a Netgear ReadyNAS Duo, which uses 7W of power at idle.

Also I no longer use VoIP, so that device is disconnected from the LAN. 

All machines connect via cat-5/6 cable into an HP Procurve 2124 24-port switch, as previously mentioned I'm using a Siemens SpeedStream 4200, single port modem/router in bridge mode (bridge mode turns off the router, as is required by IPCop as it is a router too).

Apart from the modem/router, IPCop, LJ-5 Printer (not sure about the PS3?), all existing boxes have dynamic IP addresses.

The account my ISP provides has a dynamic IP address.
      
*Take note, the modem/router needs to be on a different subnet than the Green, as seen in the _underlined_ IP addresses below.*

|
DSL
|
Modem 192.168._254_.254
|
IPCop (named: *blackbox*) 192.168._1_.1 
|
Switch
|     
iMac..iMac..PC..Powermac..LJ-5 Printer..ReadyNAS..PS3

[B][U]My current IPCop settings follow:
[/U][/B]
**Host Name:** blackbox
**Domain Name:** domain.invalid
**Network Type:**  GREEN + RED
**Drivers & Card Assignments:-**
*GREEN:* Digital 21x4x Tulip PCI (eth0)
*RED:*  Intel i82557/i82558 PCI (eth1)
**Address Settings:-**
*GREEN interface:* 192.168.1.1 <- blackbox
*Network mask:*  255.255.255.0
*RED interface:*  PPPoE
**DNS & Gateway settings:** Blank
**DHCP server configuration:**
Start address:  192.168.1.2
End address:  192.168.1.24
Primary DNS:  192.168.1.1 <- blackbox
Secondary DNS: Blank
Default lease (mins): 2440
Max lease (mins):  4880
Domain name suffix:  domain.invalid


**_IPCop Dialup Settings:_**

**Profile:** internode-1
**Connection:-** PPPoE
Idle Timeout: 0
Connection on IPCop Restart: ticked
**Reconnection:-**
Persistent
Hold Off Time: 10
In case connection fails, switch to profile: internode-1 
Maximum retries: 5
**Additional PPPoE Settings:** unused
**Authentication:-**
User Name: my ISP account username
Method: PAP or CHAP
Password: my ISP account password
**DNS:- **
Manual: I have entered my ISP's primary & secondary DNS addresses
Profile Name: internode-1
__________________________

I have a set of (securely backed up) screenshots of the IPCop browser GUI settings for my future reference. As it will (& has, when I built a backup machine) save me from reinventing the wheel so long after the initial setup of my wonderfully reliable IPCop box.

---

### Post by gTinker on 2008-12-04
No, the red interface will need to be recognised as eth1 before you can expect it to work.

Yes, you will want the IPCop box to act as DHCP server for the LAN.

You don't need to hand out so many IP addresses, you're only hanging a 24 port switch off of the green interface. And, no, you don't want the modem's IP in that group 

I found from the speedstream documentation that once you go into bridge mode you lose connection and hard reset is the only option to get connected again. That makes sense if you think about it, it's stepping out of the way and letting the connection to the Internet through transparently. No need to do this until the IPCop box is ready.

I don't know about that PPPoE page because I haven't used it but carbm1 does and will probably show up here later today to assist. While we're waiting go ahead and deal with the other issues.

You might consider changing the hostname for the IPCop box. It's going to be Internet exposed, no reason to advertise so easily that it is a firewall but probably no big risk if you do, so the choice is yours.

---

### Post by handy on 2008-12-04
Thanks for your post. It is certainly easier to give good help when you have a more detailed understanding of the problem, & you just gave me excellent help. :-D

How do I allocate eth1 to RED?

***[Edit:]** I'm editing the setup of IPCop now & noticed that RED has eth1 allocated, which is a pleasant surprise, /edit*

I'll go through & make the other modifications you suggested now.

---

### Post by handy on 2008-12-04
I have edited Post_29 to show my current settings.
[B]
*[Edit:][/B]  I'm sorry, it's midnightish & I really have to go to bed, I'm very tired.  I would like to continue live with you guys but I haven't got the horsepower at the mo', I look forward to reading any of your input first thing after a sleep. :-)*

---

### Post by gTinker on 2008-12-04
[QUOTE=handy]I have edited Post_29 to show my current settings.
[/quote]

Acknowledged.

[QUOTE=handy]
I'm sorry, it's midnightish & I really have to go to bed, I'm very tired.  I would like to continue live with you guys but I haven't got the horsepower at the mo', I look forward to reading any of your input first thing after a sleep. :-)[/QUOTE]

Yes, by all means get enough sleep, that will help with your troubleshooting and focus. It's early morning here, and just about normal workday start time for carbm1 in Arkansas. We're actually doing fairly good given the time differences, the Internet has made the world a more accessible place. I'll see if I can start earlier tomorrow but no promise. And I won't hold it against you that you're in Summer and I am cold in this hemisphere. 

[QUOTE=handy]
Thanks for that, it got me to that page where I could setup everything except VPI=8 & VCI=35 ? Interestingly Figure 2.5. PPP Settings on this page shows the settings that are not displayed on my IPCop installation? [/quote]

You aren't using the usb like shown in that dropdown list on the page are you? And, are you selecting PPPoE or PPPoE plugin? I don't know the difference but carbm1 probably will.

---

### Post by handy on 2008-12-04
> **gTinker said:**
> 
Acknowledged. 

Thanks.

> **gTinker said:**
> 
We're actually doing fairly good given the time differences, the Internet has made the world a more accessible place. 

I agree, the internet has made the world a much smaller place.

> **gTinker said:**
> 
I'll see if I can start earlier tomorrow but no promise. And I won't hold it against you that you're in Summer and I am cold in this hemisphere. 

Thank you, though please don't miss out on any sleep on my account, I am old enough not to be in a rush & I'm also quite confident of success in this venture.  As far as the weather is concerned we have had a remarkably kind year or so in my part of Oz, even the farmers aren't complaining about the weather!  We have had 5 perfect seasons (which may be a record in this land of drought). La Nina the trans Pacific rain shift has been on the Oz side of its pendulum. 

> **gTinker said:**
> 
You aren't using the usb like shown in that dropdown list on the page are you? 

No.

> **gTinker said:**
> 
And, are you selecting PPPoE or PPPoE plugin? I don't know the difference but carbm1 probably will.

No, & there is no need for me to fill in the fields in that section either.

I will add my settings from the Dialup page to post_29, it will become a long post, but it will have everything in it in the end, for my or anyone else's future reference.

***[Edit:]** I am having trouble reading & writing to Ubuntu at the moment, I can ping IPCop & the speedstream, I have done multiple network restarts, I will diconnect IPCop from the modem & network restart & see how I go.  Though it may very well be the Ubuntu server's they have not been behaving themselves under load lately.*
[B]
[Edit2:][/B] I have added the IPCop Dialup details to [***_post_29_***]("http://ubuntuforums.org/showpost.php?p=6303994&postcount=29")

---

### Post by handy on 2008-12-04
I just threw her into Bridge Mode did a network restart & I'm typing this through the blackbox. :-D

I'm sure I'll have some configuring to do, but this is a major milestone in the process, that's for sure.

I'm getting a lot of stalling on Ubuntu today, it is hard to tell what is comming from the Ubuntu servers & what is caused by me?
[I]
**[Edit:]** It must be me, I'm having to do network restart very often as I'm somehow loosing access via my browser to the internet? /edit[/I]

It seems that it will work without my inputting the VPI / VCI parameters, though I wonder what effect that is having?

---

### Post by handy on 2008-12-04
I had to reset the speedstream & set it up again.  It seemed that my internet was timing out very quickly causing me to have to do network restart VERY often to use it.

A setting to solve this is not obvious to me, so I await the help of someone with experience in these matters.

---

### Post by carbm1 on 2008-12-04
You should have "PPPoe Plugin" checked on your dialup page.  Its what actually makes it work.  Your username/password is passed to the DSL modem via the PPPoe Plugin.

Please try and see if that works. I'll be up pretty late tonight so maybe we can work on your time frame.

---

### Post by handy on 2008-12-04
Just spotted your welcome message, so I've fired up the blackbox & chosen PPPoE Plugin I'll go to Bridge Mode & see how it goes?

---

### Post by handy on 2008-12-04
Well I'm in, I'll give it a bit of a test & see what the story is, fingers crossed ;)

***[Edit:]** No, it still needs to have the network restart done very often, or it will time out on page loading?*

---

### Post by carbm1 on 2008-12-04
So it does work for a little bit then stops working?

On the main page, under System>Home.  Does it show Connected and your public IP address and hostname?

---

### Post by handy on 2008-12-04
Yes, it stops working until I use the following command:

/etc/rc.d/network restart

I am back in normal mode in the speedstream, I can tell you that when I select the Connect button in the IPCop Home page it successfully connects & starts counting the connected time.

Does that satisfy your question, or should I go back to Bridged Mode?  Which is not a real problem these days, I know how to set it up again pretty quickly now. :-)

Do any of the settings in the speedstream cary through to Bridge Mode? As the following are options in the setup:

[I]Select the Protocol:
RFC-2684 Bridged
RFC-2684 Bridged/IP
RFC-2684 Routed
**PPPoE**
PPPoA[/I]

The above is where I select PPPoE.

---

### Post by carbm1 on 2008-12-04
Honestly I cannot answer that question.  I don't know the exacts on those settings but I would think the PPPoe would be a safe setting. 

If it successfully connects, and you get internet traffic through the IPCop box, then after a short period of time it stops... I would start looking at replacing your RED interface network card.

IPCop is incredibly reliable, even when I was on DSL. With my cable here, and the T1's at the office its even more reliable.  At this point I think you have your settings on the IPCop correct, since its connecting and authorizing via the PPPoE plugin. I think we need to start looking at this recycled computer now.

---

### Post by handy on 2008-12-04
Ok, just to give you an idea of the time frame, I just went into Bridge Mode & opened the IPCop Home page & then found my way to this page it had timed out before I could start to type this reply, which of course is briefly remedied by the network restart command.

The 2 NICs in this box I have had here for some time, the intel I had bought new for a business customers system some maybe 7 years ago, the other one I would have salvaged out of a machine somewhere.

I'll replace them both & see what happens.  I'll get back to you shortly.

P.S. During the time it took to type this message it had timed out again.

---

### Post by handy on 2008-12-04
Replaced both NIC's, to no avail unfortunately.

Do you think that the VPI=8 & VCI=35 could be responsible?

---

### Post by carbm1 on 2008-12-04
Ok, nevermind on the staying up late. I hope getting the NIC's replaced works. You might have to rerun the setup program to assign the nics to red and green.  I'll check first thing in the morning.

Best of luck!

---

### Post by handy on 2008-12-04
Replaced both NIC's, to no avail unfortunately.

Do you think that the VPI=8 & VCI=35 could be responsible?

---

### Post by handy on 2008-12-05
With IPCop in Disconect mode, even accessing IPCop via the browser is timing out?

---

### Post by handy on 2008-12-05
Reinstalled on a different machine, with 2 different NIC's, still have the same problem fluctuating speed & timeout problem.

***[Edit:]** It may actually be a little different now, it is as though nothing happens for 10-15 sec's & then it moves as fast as it should, I'll investigate further.*

[I]**[Edit2:]** It is still messed up the same, it matters not which machine or NIC's are used, if IPCop is running, I'm in trouble.

I will contact my ISP & see what I can learn about the VPI & VCI settings.[/I]

---

### Post by handy on 2008-12-05
ISP educated me that the VPI & VCI settings stay in the modem/router & aren't required for Bridge Mode.  Which explains why there is nowhere to input them in my kind of IPCop setup.

I will see if I can get any help at the IPCop forum, I'll report back on anything that comes my way from there.

---

### Post by gTinker on 2008-12-05
Sorry, I not only wasn't able to get back early, I can't stay long.

If I followed what you did from your description it sounds like you are establishing the connection then trying to go into bridge mode and expecting it to function. I don't think that would be the correct way.

I think you need to put the modem into bridge mode, then turn it off for a while (to give time for the connection to time out), then establish the persistent connection from the IPCop box through the modem. Since I haven't actually done this myself, I'm just trying to figure it out from the documentation and might be mistaken.

---

### Post by handy on 2008-12-05
Thanks, I've also read on this [***_IPCop FAQ_***]("http://ipcops.com/faq/ipcop_faq.html#x1-1240003.5.3") that they recommend leaving the modem off for upto 4 - 8 hours or so, so that the ISP refreshes its cache & looses the MAC address of the modem/router.

I spoke to tech' support at my ISP today to query on VPI & VCI, & told him what I was up to, though I guess I would have had to have been lucky to be speaking to someone who understood what I was doing (I don't!) & could advise me on something such as the ISP's cache refresh timing.

As far as the order I have used when going into Bridge Mode & starting IPCop, I think I have probably covered all possibilities by now. :-)

---

### Post by gTinker on 2008-12-05
[QUOTE=handy]Thanks, I've also read on this [***_IPCop FAQ_***]("http://ipcops.com/faq/ipcop_faq.html#x1-1240003.5.3") that they recommend leaving the modem off for upto 4 - 8 hours or so, so that the ISP refreshes its cache & looses the MAC address of the modem/router.[/QUOTE]

That seems like a long time but it definitely would vary as the ISPs choice.

[QUOTE=handy]
I spoke to tech' support at my ISP today to query on VPI & VCI, & told him what I was up to, though I guess I would have had to have been lucky to be speaking to someone who understood what I was doing (I don't!) & could advise me on something such as the ISP's cache refresh timing.[/QUOTE]

You are correct, first tier support often can only work from scripts, probably wouldn't even know the answer to the question you asked.

[QUOTE=handy]
As far as the order I have used when going into Bridge Mode & starting IPCop, I think I have probably covered all possibilities by now. :-)[/QUOTE]

Are you sure you tried what I suggested after you had the bridged modem turned off for a while? However, it's late for you again, what I would do would be to sleep with the modem off and then get up and try again as long as no one at your site needs Internet while you sleep.

[edit] So trying to make sense of what we have seen from the data and what I have read from the documentation, I believe we can think of the speedstream as a combo unit, modem/router, by putting it in bridge mode you skip the router function and it acts as just a modem. At that point, we want the IPCop box to use the speedstream with PPPoE similar to the way it would use an analogue modem. I could be wrong.

---

### Post by handy on 2008-12-05
I have been advised from the IPCop support forum, to change the subnet of the Green so that it is not shared by the modem/router.

So my understanding of that says that I should move the Green into the IP range of say 192.168.1.*.  Which I will do shortly & see if that has any effect.

I will do as you advise regarding timing & the order of startup of the process as well.  I can't let the modem be off-line for very long at the moment, though perhaps in a week or more I will be able to leave it off line overnight.  I will give my ISP a call & try to find out the timing of their cache cleaning, under ideal circumstances I may only need to be off-line for a minimum amount of time to get past the cache problem.

[I]**[Edit:]** I have checked with my ISP, & they do not use MAC addresses in their authentication process.

I have also updated post_29 to my new settings.[/I]

---

### Post by handy on 2008-12-05
Well, I'm here after turning off IPCop, setting modem/router into Bridge Mode, rebooting modem/router, turning off modem/router & computer for 15 mins, then starting modem/router, booting my desktop machine to Xfce, then started the IPCop box, then did a network restart, opened Firefox then accessed the IPCop Main page, where I was told it was running (as it is set up to do), then navigated my way to here to write this.

In the past by this stage I would have lost net connection & would have to do a network restart to get another minute or so of net time, the big test (I think) is if I can now save this post without having to do another network restart.

Well I could preview it, it is looking good. :-)
[B]
[I][Edit:][/B]  I could save it! Which is a most wonderful thing.

I'll go do some more testing before I let my self get too excited. :lolflag:

**[Edit2:]** Yep she is good to go!  Thanks to you both gTinker & bmcar1, no way I would have hung in for 6 days without your assistance & encouragement.  It is an interesting phenomenon the various communities that the internet allows to spring up & grow.  Very nice indeed.  :KS

Now I can learn how to update IPCop to 1.4.21, install Advanced Proxy, & find out how to let torrents through the firewall. [/I]

---

### Post by handy on 2008-12-05
I've updated to the latest version of IPCop, & turned on the Web Proxy.

The two remaining problems are how do I install Advanced Proxy? I don't know what SCP is, though I'll do a search now which may be all I need.

The other question is how do I enable torrents in this new system?

---

### Post by handy on 2008-12-05
I'm having difficulty getting my Advanced Proxy file across to the IPCop HDD.

I am using the following:

*sudo scp -P 222 ipcop-advproxy-3.0.0.tar.gz [email]root@192.168.1.1:/ipcop-advproxy-3.0.0.tar.gz[/email]*

***[Edit:]** The above command works after SSH has been setup. /edit*

I have tried with port 22, port 222 & no port specified at all, but I still get the following error message with port 22, or 222 if it is specified:

[I]ssh: connect to host 192.168.1.1 port 222: Connection refused
lost connection[/I]

I'm sure this is another very easy problem to solve, once you know the answer.  I'll await input from someone who knows.  I'm getting lazier as I get older I think. ;-)

---

### Post by handy on 2008-12-06
I just booted into Leopard & quickly got it working on the internet.

Bailed out, & came back to Arch, I found that I had to do a network restart before I could use Firefox.

Any ideas?

---

### Post by handy on 2008-12-06
I have got Transmission downloading a torrent file.

The Transmission settings that I have used may not be as secure as they may be, for the reason that I don't know what I'm doing. :-) As usual.

Under the **Trackers** Tab:-
[B]
Connect to Tracker via a Proxy:[/B] (ticked)
**Proxy Server:** 192.168.1.1
**Proxy Port:** 80 <- I wonder about this?
**Proxy Type:** HTTP <- SOCKS4 & 5 are available

**Authentication is required:** (unticked)
**Username:** 
**Password:**

Under the **Network** Tab:-

**Use UPnP or NAT-PMP port forwarding from my router:** (unticked)

---

### Post by handy on 2008-12-06
IPCop has been running uninterrupted for 20 hours on the Dell Optiplex 150, it is acceptably quiet enough & will probably keep the job. I downloaded a torrent overnight; my wife has been in & out on her iMac, I have done a system update in Arch with the *yaourt -Syu --aur* command. It is going really well, very happy with the results thus far.

Though I do have a few unresolved questions which I'll summarise below:

**1.)** The exact method of using scp to install Advanced Proxy on the IPCop box?  I don't know how to use port 222, though I have searched on it.

**2.)** Could my Transmission proxy settings be more secure?  Please see the previous post for the details.

**3.)** I wonder why I have to use the following command after booting to the Xfce/Arch desktop before I can access the internet:

*/etc/rc.d/network restart*

If I always have to use the above command I can probably automate it, but I think that there should be a more appropriate method to prevent the need.

Further on this matter, my */etc/resolve.conf.head* has the following in it:

[I]# DHCP with user-specified DNS
nameserver 192.231.203.132
nameserver 192.231.203.3
nameserver 192.168.254.254[/I]

So the above is written to */etc/resolv.conf* every time the computer is booted up (or more accurately whenever the network is started or restarted).  In my IPCop Dialup settings I have got DNS: set to Automatic.  I would think that *nameserver 192.168.254.254* (the modem/router) is not appropriate in Bridge Mode, so I'll remove it & see?  Perhaps the entire *resolv.conf.head* file is no longer needed? So I will do away with it & see.

***[Edit:]** I have changed [I]resolv.conf.head* to just include 192.168.1.1 which is the IPCop box's address, if I don't do that Firefox won't work.[/I]

---

### Post by carbm1 on 2008-12-06
Handy, I will see if I can help you with some of your questions tonight when I have time to address some of your questions.

---

### Post by handy on 2008-12-06
Thanks carbm1, I'll keep an eye out for you.

---

### Post by carbm1 on 2008-12-07
> **handy said:**
> **1.)** The exact method of using scp to install Advanced Proxy on the IPCop box?  I don't know how to use port 222, though I have searched on it.

You have to enable SSH in IPCop first. Home > SSH Access. Check "SSH Access". You should then be able to use the command you used earlier.  I personally put everything in /root/addons. Your synatax earlier looks OK. 

Then SSH to the box and use: (adjust accordingly)
```

tar zxvf ipcop-advproxy.xxx.tar.gz
cd ipcop-advproxy
./install

```

> **2.)** Could my Transmission proxy settings be more secure?  Please see the previous post for the details.


I don't think you have anything to worry about or I don't completely understand your question.  All the proxy does is pass the request for you so it can cache it for the next person. However, this is really only true for static content not dynamic pages.  Of course now the web is comprised of mostly dynamic pages but the pictures are usually static. So thus the help.

> **3.)** I wonder why I have to use the following command after booting to the Xfce/Arch desktop before I can access the internet:

*/etc/rc.d/network restart*

I'm not familiar with Arch linux. I wonder if the problem is that you had a static IP instead of using DHCP that keeps using the old settings but when you run network restart it does the DHCP.  I had a similar issue with OpenSUSE once... I had a static IP entered but the GUI Network Manager would automatically kick it out. The two we're conflicting on startup.  You might check whatever GUI network manager vs. manually configured IP/DNS info.

---

### Post by handy on 2008-12-07
> **carbm1 said:**
> 
You have to enable SSH in IPCop first. Home > SSH Access. Check "SSH Access". You should then be able to use the command you used earlier.  I personally put everything in /root/addons. Your synatax earlier looks OK. 

Then SSH to the box and use: (adjust accordingly)
```

tar zxvf ipcop-advproxy.xxx.tar.gz
cd ipcop-advproxy
./install

``` 

I had just finished setting up SSH when I discovered your post.

I used the following command:

***scp /home/handy/downloads/ipcop-advproxy-3.0.0.tar.gz [email]root@192.168.1.1:/ipcop-advproxy-3.0.0.tar.gz[/email]***

With the following results:

[I][B]root@192.168.1.1's password: 
ipcop-advproxy-3.0.0.tar.gz                                    100%  800KB 799.8KB/s   00:00 [/B][/I]   

So, after giving the IPCop box root password it looks like the file was copied across.

I had an open SSH in another shell window, when I go there & ls I get only a setup.log listed.  When I run the tar commands you posted I get the following errors:

[B][I]tar (child): ipcop-advproxy-3.0.0.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors[/I][/B]

Which would indicate that the file was not really copied?

Complicated stuff this SSH & scp.

> **carbm1 said:**
> 
I don't think you have anything to worry about ... 

Good, that's enough for me on Transmission. :-)

> **carbm1 said:**
> 
I'm not familiar with Arch linux. I wonder if the problem is that you had a static IP instead of using DHCP that keeps using the old settings but when you run network restart it does the DHCP. 

No, I have never had a static IP account, I have always used DHCP.

> **carbm1 said:**
> 
You might check whatever GUI network manager vs. manually configured IP/DNS info.

I have no GUI network manager, there are only files to edit.

I have posted a question on this one in the Arch forum, though it remains to be seen if it will attract an answer, due to having IPCop involved.  Anyway it is not really much of a problem, though I'm sure there is a solution.

---

### Post by gTinker on 2008-12-08
[QUOTE=handy]
I have posted a question on this one in the Arch forum, though it remains to be seen if it will attract an answer, due to having IPCop involved.  Anyway it is not really much of a problem, though I'm sure there is a solution.[/QUOTE]

There is really no need to even mention IPCop in your question in the Arch forum. You know the IPCop box is working well as a NAT router from the other distros on that machine and other computers on the network, thus the issue must be something about the Arch configuration. Just like carbm1, I don't know about Arch, have never used it but there isn't anything about your IPCop installation that would cause Arch to fail to get an IP address from the DHCP server. Are you sure you have Arch setup to "auto" the ethernet card when it boots?

---

### Post by handy on 2008-12-08
> **gTinker said:**
> There is really no need to even mention IPCop in your question in the Arch forum. You know the IPCop box is working well as a NAT router from the other distros on that machine and other computers on the network, thus the issue must be something about the Arch configuration. Just like carbm1, I don't know about Arch, have never used it but there isn't anything about your IPCop installation that would cause Arch to fail to get an IP address from the DHCP server. Are you sure you have Arch setup to "auto" the ethernet card when it boots?

I have changed nothing but the /etc/resolv.conf.head file.  The job of which is to write what you put into it into the head of the /etc/resolv.conf file every time your network starts up.  It used to mention my ISP's two DNS IP addresses & the speedstreams IP address, I have changed that so it just points at the IPCop box, as it doesn't need the ISP's DNS anymore, or the speedstreams IP.

Having said that, I had the problem of needing to use the network restart command ever since the IPCop box has been doing its job.  I experimented with the resolv.conf.head file & found that it needed the IPCop boxes IP or Firefox won't work.

So, for some reason the auto startup for the LAN, at least the part that points to the IPCop box is not doing its job the first time.  I can find no problems in log files on either IPCop or /var/logs/ on the Arch box.

I have had some response on the Arch forums, but nothing notable thus far.  My knowledge is somewhat lower than the person who has responded.  It can take a while to meet at a lever where two people can communicate on technical questions.

I just checked, & got another reply from the developer/moderator that has been replying to me, he too uses IPCop, he gave me a copy of the portion of his logs from both IPCop & Arch when they first talk to each other.  

He finished his post with the following:

> 
As the failure is only at boot-time, do a reboot before checking the logs. It may be that there is a delay initialising the driver for your network card, so your dmesg directly after reboot would also be useful. 

I will investigate this further later today after I have had some sleep. :-)

Thanks for your continued interest gTinker. :-)

---

### Post by handy on 2008-12-09
I have not been able to find any clues in  my Arch /var/logs/ as to why I need to network restart on the Arch box.  It will eventually show itself to me, & I'm not overly concerned about that one really.

I would like to be able to add Advanced Proxy to IPCop, I haven't been able to succeed (as previously posted), it looks as though the Advanced Proxy file copies using scp, but it does not appear on the root of IPCop?  When I give the tar command I get errors, because the file does not exist.

By the way, I picked up a Celeron 450 box today at the tip for the standard $5- fee, I'm educating myself to help decide whether to make it into a NAS or a torrent server.

---

### Post by gTinker on 2008-12-09
[QUOTE=handy]
Having said that, I had the problem of needing to use the network restart command ever since the IPCop box has been doing its job.  I experimented with the resolv.conf.head file & found that it needed the IPCop boxes IP or Firefox won't work.[/QUOTE]

Are you saying that still happens? It was my understanding of what you wrote that, that particular problem was happening before you correctly configured the connection between the IPCop box and the modem. If that was the case it makes sense, if it continued to happen after you established the correct connection, then it doesn't make sense.

[QUOTE=handy]
So, for some reason the auto startup for the LAN, at least the part that points to the IPCop box is not doing its job the first time.  I can find no problems in log files on either IPCop or /var/logs/ on the Arch box.[/QUOTE]

What are you calling "the auto startup for the LAN"? And what do you mean by "first time"? You wouldn't find anything in the IPCop logs, the problem seems to be (from data presented) that Arch isn't asking for an IP adress from the DHCP server on the IPCop box. Isn't the rest of your LAN able to access Internet while the Arch box is up? Is there a dhclient on your Arch install that you could force to ask for DHCP or the pump command or just bring the interface down and then back up? Trying one of those would test my suggestion. If issued in a terminal, we likely would even get more troubleshooting data from the error message.

---

### Post by handy on 2008-12-09
> **gTinker said:**
> 
Are you saying that still happens? It was my understanding of what you wrote that, that particular problem was happening before you correctly configured the connection between the IPCop box and the modem. If that was the case it makes sense, if it continued to happen after you established the correct connection, then it doesn't make sense. 

Yes, it doesn't make sense. :-)

I have always had this problem when IPCop is doing its job.  Sorry that previous post was not very clear, I had little sleep last night.

> **gTinker said:**
> 
What are you calling "the auto startup for the LAN"? 

The file /etc/rc.conf is where you tell the system that you are using DHCP with the use of the following line: eth0="dhcp"

> **gTinker said:**
> 
And what do you mean by "first time"? 

Bootup (as I said, very tired).

> **gTinker said:**
> 
You wouldn't find anything in the IPCop logs, the problem seems to be (from data presented) that Arch isn't asking for an IP adress from the DHCP server on the IPCop box. Isn't the rest of your LAN able to access Internet while the Arch box is up?  

Yes, the other machines boot to having internet access with no input required from me.

> **gTinker said:**
> 
Is there a dhclient on your Arch install that you could force to ask for DHCP or the pump command or just bring the interface down and then back up?  

Yes that is what */etc/rc.d/network restart* does.  Without that command I would not be able to use IPCop with Arch, at least not with my current level of knowledge.

> **gTinker said:**
> 
Trying one of those would test my suggestion. If issued in a terminal, we likely would even get more troubleshooting data from the error message.

The network restart is a terminal command it just takes the network lo & hi.

---

### Post by gTinker on 2008-12-09
[QUOTE=handy]Yes, it doesn't make sense. :-)

I have always had this problem when IPCop is doing its job.  Sorry that previous post was not very clear, I had little sleep last night.[/QUOTE]

Well, in that case you haven't setup IPCop box --> modem connection correctly. Since we told you to set it up as a persistent connection it should always present a WAN connection to the switch through the IPCop box. and, thus be available to your LAN.

I thought what you meant was that you always had to do that with the Arch boot of your multiboot and that the other boots of that system were not problematic and the other computers also booted and worked with no further commands.



[QUOTE=handy]
The file /etc/rc.conf is where you tell the system that you are using DHCP with the use of the following line: eth0="dhcp"[/QUOTE]

Yes, but it is apparently (from your results), not doing that "auto" (at boot) the way your other systems and distros are obtaining an IP address. 


[QUOTE=handy]
Bootup (as I said, very tired).[/QUOTE]

As above.


[QUOTE=handy]
Yes, the other machines boot to having internet access with no input required from me.[/QUOTE]

See, that's the point. Only the Arch system isn't obtaining an IP address at boot. Doesn't that lead you to believe that the network is OK but the Arch install isn't? 


[QUOTE=handy]
Yes that is what */etc/rc.d/network restart* does.  Without that command I would not be able to use IPCop with Arch, at least not with my current level of knowledge.[/QUOTE]

Naturally, as stated (for some reason) the Arch install isn't obtaining an IP address at boot. That's where you have to look for the answer.


[QUOTE=handy]
The network restart is a terminal command it just takes the network lo & hi.[/QUOTE]

Sure, I know that. But you didn't do what I asked. Somewhere, ARCH has some command to force the system to ask for an IP address from the IPCop DHCP server. Some command other than taking the network card down and then up. If you use that command (whichever one is available on Arch), the error message displayed will tell us if the Arch system is trying or capable or failing when it tries to get that DHCP address. The network card can come to the 'up' state without the IP address when you do a network restart so that doesn't test DHCP.

Once again, I suggest you get some sleep before working on this any more. You seem to always have more success that way, focus better and record things more clearly. That's pretty well true for all of us, frustration clouds our thinking, stresses us to make mistakes and not think logically. You have the patience to stick with this, it's taken a while but we have had some success.

---

### Post by handy on 2008-12-09
> **gTinker said:**
> 
Well, in that case you haven't setup IPCop box --> modem connection correctly. Since we told you to set it up as a persistent connection it should always present a WAN connection to the switch through the IPCop box. and, thus be available to your LAN. 

No, it is setup to be persistent, & as I have said previously the other machines have no problem, it is just something going on with my simple Arch configuration that will eventually come out in the wash.

I'm not going to worry about it at this stage, it is really not an inconvenience to bring the command up from the bash history & press enter, when I boot into Arch.  There are other far more interesting & satisfying things I would rather be doing at the moment.

Why waste time on that insignificant little problem when I could be creating much bigger & more complex ones?  :lolflag:

> **gTinker said:**
> 
See, that's the point. Only the Arch system isn't obtaining an IP address at boot. Doesn't that lead you to believe that the network is OK but the Arch install isn't? 

Yes, kind of; in that the Arch setup is how I built it, & there is obviously something that I don't know, & can get no clues from the logs about.  

Apart from this minor problem, my Arch system as it is currently set up is giving me by far the best computing experience that I have had in 23 years of computing life. :-) 

> **gTinker said:**
> 
Naturally, as stated (for some reason) the Arch install isn't obtaining an IP address at boot. That's where you have to look for the answer. 

I know, & I've looked, & I'm going to let this one go for the time being.

> **gTinker said:**
> 
Sure, I know that. But you didn't do what I asked. Somewhere, ARCH has some command to force the system to ask for an IP address from the IPCop DHCP server. 

If there is a bash command for that then I can do that.

> **gTinker said:**
> 
You have the patience to stick with this, it's taken a while but we have had some success.

We have had a great deal of success, if I get no further with IPCop I consider it a success as it stands.  Even if I can't get Advanced Proxy on to IPCop it doesn't matter, I may very well find on my tiny network that it would have a negligible effect on internet latency anyway. ***[Edit:]** Though I'd still like to try it.* :-)

---

### Post by handy on 2008-12-10
I just put the following line:

***/etc/rc.d/network restart***

***[Edit:]**  I've removed the **[I]re*** from the above command to make it ***start*** which is more appropriate under the circumstances I think.[/I]

in the ***/etc/rc.local*** on my Arch box, which has saved me having to type that line in the Terminal after any boot-up on this machine.

It is an easy workaround, the need for which remains unknown to me.

***[Edit:]** Upon request, I have posted my rc.conf to a thread in the Arch forums, so perhaps a mistake of mine may be picked up? *

---

### Post by handy on 2008-12-11
Something I have been noticing, is that even thought I have the IPCop web proxy turned on, I am not seeing anything at all happen in the Proxy Graphs?

I would expect to see some traffic if it was working, so I don't understand that one?

---

### Post by carbm1 on 2008-12-11
You use both of your computers to view the same content several times a day?

Then you should see something on the graphs.  If you use one computer for one thing, and the other for something totally different, you wouldn't see anything on the graphs because there isn't anything for it to cache. 

I attached a graph of ours here at work.  We are on a T1, 1.5Mbps u/d, and it makes a world of difference when 30 computers hit the same website at once.  It keeps our network from ceasing.

---

### Post by handy on 2008-12-11
So Advanced Proxy would basically be a waste of time on my home LAN then?

---

### Post by gTinker on 2008-12-12
Sorry handy, I was away for a couple of days.

[QUOTE=handy]
If there is a bash command for that then I can do that.
[/quote]

You might try dhclient, that's what I would use on a Debian system, but as I stated, I don't know anything about Arch. Maybe it has pump. What you need to do is find the command that triggers your interface to ask for DHCP. That would be a way to test the issue we were considering at the time. However, you seem satisfied with your workaround.

[QUOTE=handy]
I just put the following line:
 
 /etc/rc.d/network restart
 
 in the /etc/rc.local on my Arch box, which has saved me having to type that line in the Terminal after any boot-up on this machine.
 
 It is an easy workaround, the need for which remains unknown to me.[/quote]

Interesting, so on Arch the command is network not networking, there are probably other differences and I've not seen Arch.

One possibility that occurs to me is that on the Arch box networking is started before the module for the interface is active, thus requiring that restart you have added. Since you've posted to the Arch forum, they can best help you with that.

---

### Post by handy on 2008-12-12
> **gTinker said:**
> 
Sorry handy, I was away for a couple of days. 

No worries gTinker, I hope your trip was enjoyable.

> **gTinker said:**
> 
You might try dhclient, that's what I would use on a Debian system, but as I stated, I don't know anything about Arch. Maybe it has pump. What you need to do is find the command that triggers your interface to ask for DHCP. That would be a way to test the issue we were considering at the time. However, you seem satisfied with your workaround. 

Neither dhclient nor pump are on my machine, I'll see if they are available in the repo's.

dhclient is, so I have installed it, though I had better read about it to see what to do with it.

> **gTinker said:**
> 
One possibility that occurs to me is that on the Arch box networking is started before the module for the interface is active, thus requiring that restart you have added. Since you've posted to the Arch forum, they can best help you with that.

I'll post my rc.conf below, it is the main configuration file for Arch, you may understand more about Arch from this.  Also, you will notice that sky2 which is my network hardware is loaded first in the HARDWARE | MODULES section:

```
#
# /etc/rc.conf - Main Configuration for Arch Linux
#

#
# -----------------------------------------------------------------------
# LOCALIZATION
# -----------------------------------------------------------------------
#
# LOCALE: available languages can be listed with the 'locale -a' command
# HARDWARECLOCK: set to "UTC" or "localtime"
# TIMEZONE: timezones are found in /usr/share/zoneinfo
# KEYMAP: keymaps are found in /usr/share/kbd/keymaps
# CONSOLEFONT: found in /usr/share/kbd/consolefonts (only needed for non-US)
# CONSOLEMAP: found in /usr/share/kbd/consoletrans
# USECOLOR: use ANSI color sequences in startup messages
#
LOCALE="en_AU.utf8"
HARDWARECLOCK="UTC"
TIMEZONE="Australia/Sydney"
KEYMAP="us"
CONSOLEFONT=
CONSOLEMAP=
USECOLOR="yes"

#
# -----------------------------------------------------------------------
# HARDWARE
# -----------------------------------------------------------------------
#
# Scan hardware and load required modules at bootup
MOD_AUTOLOAD="yes"
# Module Blacklist - modules in this list will never be loaded by udev
MOD_BLACKLIST=(net-pf-10 pcspkr) ## turns off ipv6 & pc speaker
#
# Modules to load at boot-up (in this order)
#   - prefix a module with a ! to blacklist it
#
MODULES=(**sky2** snd-mixer-oss snd-pcm-oss snd-hwdep snd-page-alloc snd-pcm snd-timer snd snd-hda-intel soundcore fglrx)
# Scan for LVM volume groups at startup, required if you use LVM
USELVM="no"

#
# -----------------------------------------------------------------------
# NETWORKING
# -----------------------------------------------------------------------
#
HOSTNAME="archtypical"
#
# Use 'ifconfig -a' or 'ls /sys/class/net/' to see all available
# interfaces.
#
# Interfaces to start at boot-up (in this order)
# Declare each interface then list in INTERFACES
#   - prefix an entry in INTERFACES with a ! to disable it
#   - no hyphens in your interface names - Bash doesn't like it
#
# Note: to use DHCP, set your interface to be "dhcp" (eth0="dhcp")
#
###lo="lo 127.0.0.1"
# eth0="eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255"
**eth0="dhcp"**
###INTERFACES=(lo eth0)
INTERFACES=(eth0)
#
# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
# gateway="default gw 192.168.0.1"
ROUTES=(!gateway)
#
# Enable these network profiles at boot-up.  These are only useful
# if you happen to need multiple network configurations (ie, laptop users)
#   - set to 'menu' to present a menu during boot-up (dialog package required)
#   - prefix an entry with a ! to disable it
#
# Network profiles are found in /etc/network-profiles
#
#NET_PROFILES=(main)

#
# -----------------------------------------------------------------------
# DAEMONS
# -----------------------------------------------------------------------
#
# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#


DAEMONS=(syslog-ng @iptables network @netfs @crond @alsa @portmap @sshd @transmission-daemon @stb-admin @fam @gpm)# @tor @privoxy # @hal - hal's out on account of worker


# End of file 
```

***[Edit:]** I just read about dhclient & think that really it won't give me anything on Arch more than I have by running the [I]/etc/rc.d/network start* command as I am doing now.  For me the question remains as to why I have to, because really, there should be no need for input from me.  

If the Arch people do get back to me in my thread over there where my rc.conf is posted, I may find that there is an error there, though I doubt it, as it is such a simple file.  Hopefully I have made a mistake in it & that will put that problem to bed. :-)[/I]

---

### Post by handy on 2008-12-13
I have installed [***_Copfilter_***]("http://www.copfilter.org/") on my IPCop box.

I have set it up how I want it to be, & at this early stage it seems to be working ok with the exception of Privoxy.

When I go to the Privoxy Configuration link in IPCop, I get a the Privoxy web page that tells me that Privoxy is not running.

My Firefox is set to no proxy, & I have the web proxy running in transparent mode, I have cleared the cache in both Firefox & IPCop's web proxy & then restarted  Firefox to no avial (more than once)?

So I wonder if anyone has any experience with this particular IPCop add-on concerning Privoxy?

Thanks for your time.

[I]**[Edit:]** Of course after writing the preceding post I tried clearing caches once again & this time when tested with the Privoxy Configuration link it worked.

Prior to clearing the caches I looked in the privoxy.log on the IPCop box, & it looked as though it was working to the uninitiated me.[/I]

---

### Post by handy on 2008-12-13
I got a valuable reply in the Arch forums today, it solved my network startup problem, it is really obvious now that I see it. :lolflag:

[Quote=tomk]
    *Try un-backgrounding iptables. At the moment you are effectively starting them in parallel - maybe iptables needs to be fully up and running before you start your network.* [/quote]

To do what he said, all I had to do was remove the ***@*** from in front of *iptables* in the DAEMONS= line of my /etc/rc.conf . :-)

So, that is that one put to bed.  It caused me to learn a few things on the way, which seems to be what problems are for...

---

### Post by gTinker on 2008-12-13
[edit] ah! I see you got an answer while I was typing. Glad you got that sorted.

[QUOTE=handy]
I'll post my rc.conf below, it is the main configuration file for Arch, you may understand more about Arch from this.  Also, you will notice that sky2 which is my network hardware is loaded first in the HARDWARE | MODULES section:[/quote]

Yes I do notice that it is listed first in the modules section but because I haven't studied Arch I don't know anything about how it parses the file or in what order it executes what it sees. But no matter, this thread is not about me learning Arch.

It appears that you don't start the lo interface but I suppose you have a reason for that.

The following looked interesting to me:

[QUOTE=handy]```
#
...

# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
# gateway="default gw 192.168.0.1"
ROUTES=(!gateway)
#
... 
```[/quote]


That almost looks like you have it set to disable the gateway at boot but you may have a reason for that too. Without a gateway I do imagine a difficulty connecting to the net.

[QUOTE=handy]***[Edit:]** I just read about dhclient & think that really it won't give me anything on Arch more than I have by running the [I]/etc/rc.d/network start* command as I am doing now.  For me the question remains as to why I have to, because really, there should be no need for input from me. [/quote] 

It wasn't to give you anything more, it was a way to test by just making a DHCP request without a whole networking restart as a means to narrow down the troubleshooting of the issues we were following. As I mentioned before, you seem happy with your workaround, that's good enough for me. I just got involved to help you get IPCop working for your LAN, the Arch experts can help better with Arch configuration.

---

### Post by handy on 2008-12-13
> **gTinker said:**
> 
[edit] ah! I see you got an answer while I was typing. Glad you got that sorted.


Yes, so simple, one character can bring down an entire system, thankfully that @ wasn't having devastating effects. :-)

> **gTinker said:**
> 
That almost looks like you have it set to disable the gateway at boot but you may have a reason for that too. Without a gateway I do imagine a difficulty connecting to the net.

 
It seems that IPCop handles the situation so well that there is no need for me to change anything else in the rc.conf, thankfully.

> **gTinker said:**
> 
It wasn't to give you anything more, it was a way to test by just making a DHCP request without a whole networking restart as a means to narrow down the troubleshooting of the issues we were following. As I mentioned before, you seem happy with your workaround, that's good enough for me. I just got involved to help you get IPCop working for your LAN, the Arch experts can help better with Arch configuration.

Yes, I see what you mean re, dhcp.

As you already know the workaround is gone now & the network startup problem is truly solved.

Now with the addition of Copfilter I can see no need to add anything more to the wonderful IPCop, unless future additions to my LAN require something.

Thank you once again for all of your help throughout this looong thread.  

Due to both you ***glTinker*** & ***carbm1*** I have now got a very well functioning IPCop. =D>

---

### Post by handy on 2008-12-14
This morning the internet stopped working, I looked about in logs but did not understand, tried *network restart* on my Arch Linux client, which did not help, after I rebooted the IPCop box all was as it should be again.

This evening the internet stopped working again.  I again tried shutting down & restarting my clients network to no avail.  I then gave the IPCop box the reboot command, it took a good 15 minutes or so with lots of disk activity before it eventually did do a reboot?

If anyone has any familiarity with the IPCop add-on Copfilter, could you please tell me any parts of which logs you would like me to post?  I have only added Copfilter about 30 hours ago as I write this.


Copfilter Version - 0.84beta3a
New installation, about 30 hours old when this was posted.
PIII 731Mhz  256Mb PC133 RAM 10Gb HDD
Currently only using 2 machines on LAN.
Monitor = on
P3Scan = off
ProxSMTP = off for both green & red
HAVP, Privoxy = on, all settings 
frox = on
Antispam = off for all
ClamAV = on for all, update 4 hourly

Thank you for your time.

---

### Post by handy on 2008-12-14
Another 12 hours has gone by without any interference to my net connection.

I have posted my problem in the Copfilter forum, which has a hell of a check built in to prevent URL's being posted in an anti-SPAM measure, which has the side effect of making it very difficult to post technical details unless you have been a member for a certain period of time!? :lolflag:  

Most people would only need the that forum when they have just joined it.

***[Edit:]** It is 5 days or 5 posts before the posting limitations are removed.*

---

### Post by handy on 2008-12-15
Another 20hrs have gone by with no problem?

---

### Post by handy on 2008-12-15
I received advise on the Copfilter forum to increase the size of my swapfile to 1Gb & test the results.

I used the following to do the job:

swapoff /swapfile
rm -f /swapfile
dd if=/dev/zero of=/swapfile bs=1048576 count=1024
mkswap /swapfile
swapon /swapfile 

Apparently some of the add-ons incorporated into Copfilter use a lot of RAM, I don't use the worst of them, so hopefully increasing the swapfile size will do the trick for me.  For those that do use the really hungry services you apparently need at least 1Gb of RAM on your IPCop machine.

---

### Post by handy on 2008-12-15
From looking at the memory graph in IPCop, I can see that I will be able to release most of the recently expanded 1Gb+ Swapfile space back to the IPCop system.

Instead of 32Mb sized Swapfile which was the default setup for IPCop, it looks like if I allocate 256Mb to the job, I will be very safe as far as memory spikes are concerned.

When I find some more suitable memory at the tip in a $5- box, I'll upgrade to the motherboards max' which is 512Mb.

---

### Post by handy on 2008-12-19
3 more days have gone by without any problems whatsoever.  I will give it another week or more & post what I expect to be a perfect report on the behaviour of IPCop/Copfilter, everything is running as smooth as glass now. 

I am so impressed with the absence of any noticeable speed reduction & the total transparency of the following components that have come to IPCop via the addition of Copfilter:

[***_HAVP_***]("http://havp.sourceforge.net/"), [***_Privoxy_***]("http://www.privoxy.org/"), [***_Frox_***]("http://frox.sourceforge.net/"), [***_ClamAV_***]("http://www.clamav.net/").

---

### Post by handy on 2008-12-27
Just an update for anyone that is interested:

The IPCop/Copfilter headless box is running like a dream, its been up non-stop for 7 days; CPU rarely does more than idle; the HDD rarely spins up; /swap is usually 97% free; the 256Mb of RAM consistently runs at 97% full; the Optiplex GX150 is so quiet I can barely tell it is running, my internet speed has not slowed even though ClamAV & Privoxy are constantly doing their thing.

So the bottom line is that I can find no fault. :-D

---

### Post by cariboo on 2008-12-27
Glad to hear that everything worked out for you.

Jim

---

### Post by handy on 2009-02-17
Just an update to say that the IPCop box just keeps doing its thing faultlessly, 24 hours a day, everyday.

---

### Post by handy on 2010-03-03
Roughly a year since the last post, I thought that I would drop in to say that the IPCop/Copfilter combination have only ever stopped from their 24/7 task, when there has been a power black out. :)

The box has recovered from every one of those interruptions without complaint.

I also tested the power consumption @ my current billing rate of 19cents (AUS)/kw, & the PIII 7**Mhz/256MB RAM/2GBHDD headless box costs $54-/year.

This should give some of you an idea of what these 24/7 things can cost us.

I'm quite happy with that price/reliability ratio, though when the PIII does die, I should be able to cut the price in half.  Though the reliability of these little things still has to be proven to me?

---

### Post by handy on 2010-08-11
I inherited an old box running an Athlon 700Mhz, 512Mb RAM & a 20GB HDD. Fortunately IPCop was happy with the hardware so I have it set up identically to the old Optiplex PIII, ready to go to work when the Optiplex does eventually fail.

It's great how old hardware can be put to such good use. :)

[I]**[Edit:]** By the way, long ago now, I made screen captures of all of the browser GUI interface pages of IPCop, just to make my life easier if I ever have to set it up again as my memory is all but defunct. 

Those screen captures plus post_29 in this thread made it so easy. Without them I would have had to reinvent the wheel as my memory would have let me down after all that time. :)[/I]

---

### Post by markp1989 on 2011-03-20
just read all of this thread, and I am thinking of setting up a IPCop firewall for my house.

currently network looks like:
```

1. Cable modem
     |
     |
2. Dir-615 router running dd-wrt 
     |           |            |
3. Sisters pc    |            |
                 |            |
                 |    5. Buffalo WHR-G54S running dd-wrt **
                 |                            |
                 |                   6. other Sisters PC 
   4. 24port switch in my room
        |     |    |   |    
  7. printer  |    |   |
              |    |   |
    8.torrentslave |   10.XBOX 
                   |
                9. my Desktop 

```
the 24port switch is under used, but my 4port switch was full and I got a good deal on the 24port, £10 including shipping. 

on top of the 10 devices listed , we have 3 laptops, and 3 smart phones that regularly connect to the wifi 

                  
 ** used as a switch and to provide wifi to the 3rd floor of the house, as the steel supports were causing coverage problems 


internet is a 50mbs down and 5mbs up cable connection 

do you think I would see any benefits my replacing the dir 615 router with an IPCop  system?

Thanks, Mark

---

