---
title: "Setting up a Server"
date: 2008-08-26
forum: Server Platforms
---

### Post by hackerlife on 2008-08-26
Hey guys hope this is the right place for this question...

So my friend and i wanna make a computer and put a massive hdd on it, and set it up so we can access it and add to it anywhere.

I'm assuming a need a fileserver, but someone earlier mentioned this might piss off my isp???

All help and any tips with fileservers is much appreciated.

Oh and would Ubuntu server edition be good for this? I can only assume so...

OH and how good of a comp would i need?

Thanks again

---

### Post by jerome1232 on 2008-08-27
Well the tool you use would depend one a few things.

What kind of computers are you going to be serving files to (Linux, Windows, Mac, a combination?)

Do you plan on sharing files across the internet or just on the lan?

If you want this going over the internet you will probably want something secure like sftp.

If this over a lan and with mixed linux/windows/mac's you might want to use samba.

If it's just linux computers and just on the lan there's quite a few options, nfs,ftp,sftp,samba.

I haven't setup alot of fileservers but knowing exactly what you want to implement will help someone who knows more than I give you good recomendations, and some how-to links.

---

### Post by hackerlife on 2008-08-27
Ok, moar info.

So we're trying to set up a comp with a massive hdd so we can save music/vid/other to it and access/add to  it via teh internets. 

It will most likely be used by (D) all of the above, macs, pcs, and linux.

We also would like somekind of password thing, so only friends (or those we sell the pass to!!) can access/add.

thanks again!!

---

### Post by DGortze380 on 2008-08-27
> **hackerlife said:**
> Ok, moar info.

So we're trying to set up a comp with a massive hdd so we can save music/vid/other to it and access/add to  it via teh internets. 

It will most likely be used by (D) all of the above, macs, pcs, and linux.

We also would like somekind of password thing, so only friends (or those we sell the pass to!!) can access/add.

thanks again!!

This will violate most ISP terms and conditions, how you proceed is up to you. The being said: 

1) You need to have a static IP from your ISP or use a service like DynDNS to track your Dynamic IP and associate it with a host name.

2) I'll assume you're using a typical high speed ISP Cable or DSL. If not correct me. You'll need to set up port forwarding on a router to forward all traffic on a specific port to your server.

3) What port you forward will depend on how you decide to connect to the server. If you're looking at transferring files, SFTP is a good option, I forget the default port for this (21, 22, or 23, I think), but for security reasons you should choose a port other than default anyways.

4) If you just want to access the files and stream content, then you're probably looking at a web server or VPN.

We really need to know exactly what you want to do and specifics about your network set-up to help much more than that.

---

### Post by de0xyrib0se on 2008-08-27
You will more than likely be capped very quickly by your ISP and a letter will be sent to you "suggesting" you stop doing this, last time i tried something like this it took them less than 3 hours to shut down my whole line.

To clarify my ISP at the time was Optimum Online, but i've heard horror stories from users of other ISPs such as actual legal proceedings against them, keep in mind the companies that own the Music and Movie studios own the ISPs.

---

### Post by jerome1232 on 2008-08-27
Yeah your upload bandwidth would get murdered rather quickly, Doing it for personal use once in awhile is fine but they will notice if your serving files out to alot of people, better to rent a server in a data center, you can get them pretty cheap, I found one for 29.99 a month, 500 GB's of bandwidth, you could buy more if you needed, came with 500 GB hard disk space also upgradable.

From what I've read so far I think sftp would best suit your needs.

btw sftp is just ssh, but dealing with file sharing, default port of 22.
edit: I am assuming the files are legal... not copyright protected content

---

### Post by hackerlife on 2008-08-27
oh jeez i had no idea this would be such a problem.
i just figured a small server like me (with like 4 people max using) won't even make a blip on their radars.

anyway, lets proceed.

i will be used dsl most likely.

Q's: what do u guys mean buy "ports?"

whats a web server or VPn?

thanks agian guys

---

### Post by DGortze380 on 2008-08-27
> **hackerlife said:**
> oh jeez i had no idea this would be such a problem.

Q's: what do u guys mean buy "ports?"

whats a web server or VPn?

thanks agian guys

I think maybe you should do a little more research before you jump into this.
Perhaps try it locally first. Also remember, you're going to be very limited in bandwidth, any uploads and downloads over the internet from a home server will likely be excessively slow. Been there, done that, never again. I'd look into renting server space as jerome suggested, [www.godaddy.com](www.godaddy.com) has some good options.

[http://en.wikipedia.org/wiki/Computer_network](http://en.wikipedia.org/wiki/Computer_network)
[http://en.wikipedia.org/wiki/Vpn](http://en.wikipedia.org/wiki/Vpn)
[http://en.wikipedia.org/wiki/TCP/IP](http://en.wikipedia.org/wiki/TCP/IP)
[http://en.wikipedia.org/wiki/Network_port](http://en.wikipedia.org/wiki/Network_port)

---

### Post by hackerlife on 2008-08-27
yah i don't really know that much about any of this, but i figured here was a better place to get the gist of this stuff than google.

thanks for the links

---

### Post by DGortze380 on 2008-08-27
> **hackerlife said:**
> yah i don't really know that much about any of this, but i figured here was a better place to get the gist of this stuff than google.

thanks for the links

You're welcome, we'd be happy to answer specific questions, but it's a very broad topic to cover. Some background research would serve you well.

---

### Post by hackerlife on 2008-08-27
yah i really had no idea it would be this complicated.
would it be tough for me to get a quick program right now and set it up so me and my friend can test it right now?

---

### Post by DGortze380 on 2008-08-27
> **hackerlife said:**
> yah i really had no idea it would be this complicated.
would it be tough for me to get a quick program right now and set it up so me and my friend can test it right now?

It's not really just a program. You'd have to set up Static IPs, choose a protocol... etc... etc...

What exactly do you want to do? Are you trying to stream off a server, run programs off the server, or just set up a file server that you can copy to / copy from.

---

### Post by hackerlife on 2008-08-27
copy to/ copy from
i just want this so my friends and i can share big files easier, and this way we could like pool all our music vids and apps together on one massive hdd

---

### Post by DGortze380 on 2008-08-27
> **hackerlife said:**
> copy to/ copy from
i just want this so my friends and i can share big files easier, and this way we could like pool all our music vids and apps together on one massive hdd

Ok, I tell you this will work fine locally. Once you put it out over the internet, I really don't think you'll get the speed you need. 

Do you have two computers set up connected to a router or switch? That's the most basic set-up you'll need to test this.

I also need to know what Operating System each of the machines is running.

---

### Post by hackerlife on 2008-08-27
oh no i dont have the supplies here to set up to computers together.

if i do it hear one will be ubuntu, the other xp.

with my friend, ubuntu-ubuntu or ubuntu-mac

---

### Post by DGortze380 on 2008-08-27
> **hackerlife said:**
> oh no i dont have the supplies here to set up to computers together.

if i do it hear one will be ubuntu, the other xp.

with my friend, ubuntu-ubuntu or ubuntu-mac

To test it locally you will need to do the following.

At least two computers connected to a router or switch.

Assign Static IPs to both machines. "man ifconfig" for ubuntu info, don't remember how to do it in Windows at the moment.

On the Ubuntu Machine install ssh-server using synaptic or apt-get

On the Windows box install winscp (google it)

To access the Ubuntu machine (which in this test is acting as the server) use WinSCP. Enter the static IP of the Ubuntu machine, a valid user name and password to connect.

---

### Post by hackerlife on 2008-08-27
hey man thanks for all the help.

i have to leave now but will be on later, but before i go quick question,
i can totally use my wifi router for this, right? it doesnt have to be a physical connection? (wow that sounds really noobish but i need to know)

thanks again!!!
-will

---

### Post by DGortze380 on 2008-08-27
> **hackerlife said:**
> hey man thanks for all the help.

i have to leave now but will be on later, but before i go quick question,
i can totally use my wifi router for this, right? it doesnt have to be a physical connection? (wow that sounds really noobish but i need to know)

thanks again!!!
-will

It can be connected in any way that you choose, wired or wireless. A word of warning though, use some type of encryption, and be sure you have a decent router, I fried my wireless doing this on my old D-Link.

---

### Post by flatline on 2008-08-27
Ok dude, I'm going to assume that you are young and living at home - apologies if I've missed the mark.

There are several flaws in your plan.  For one thing, DSL, unless you have a business-class account, limits your upload speed quite a lot.  That means that you might be able to download torrents at a pretty decent speed, but if someone is trying to connect to your server from outside (especially if there is more than 1 connection), they will get something more like a dial-up speed.  

Example: If you have the basic Verizon DSL package, you can download at 768kbps, but you can only upload at 128 kbps, in the best case.  Let's assume you have a video file, an episode of Doctor Who.  It is around 350MB.  Assuming you can sustain the highest possible connection speed the whole time, it would take you just about 50 minutes to transfer that - to 1 person.  If there were two people accessing the server at once, or for some reason you can't maintain the 128kbps upload speed, it would take even longer.  Also, as others have mentioned, just because the ISP says that they will give you that speed, does not mean that they will allow you to use it 24/7.  They will detect the spike in your use and at the very least ask you nicely to stop.  Or they might just cut you off/slow down your connection.

In addition, you have some other problems.  How would the person on the outside know how to 'find' your server?  You would need a static IP address, or at the very least something like DynDNS that fakes it.  At home, since you are most likely using a router with NAT, you would need to enable port-forwarding to ensure that your server gets all of the incoming connections.  No offense, but the fact that you have no idea what a port is does not bode well for this venture.  Unfortunately, there isn't a program you can download and run FTW.

There are a whole bunch of other technical and legal reasons why this probably isn't a good idea.  I mean, you are on a linux forum, so we're not exactly working for the RIAA here, but you have to be smart about things.  You can't just hook up a giant hard drive to the Internet and go.

---

### Post by hackerlife on 2008-08-27
ok wow thanks (and u read me like a book lol)

ok well right now i really just wanna know about the legal aspects of this.

if its just me and a few guys using this once in a while, will they even care?

---

### Post by jerome1232 on 2008-08-27
On the other side of things setting this up on a LAN is a great way to start learning about this stuff. This would have very practical use on a LAN with 3 or 4 computers and you wanted a central place to store files.

---

### Post by DGortze380 on 2008-08-27
> **hackerlife said:**
> ok wow thanks (and u read me like a book lol)

ok well right now i really just wanna know about the legal aspects of this.

if its just me and a few guys using this once in a while, will they even care?

There is no specific answer to that. If it violates your usage policy then yes, they will care. What will do about it? Who knows. You really may want to do some more research and look into having some else host this for you, check out godaddy.com

---

### Post by hackerlife on 2008-08-27
mmm, yah, i dont really wanna risk anything cuz i love my internet sooo much!!!

but i dont rly feel like spending money (call me cheap, i'm really just too poor!!)

so ima do more research on my isp and what they might do

thanks

---

### Post by flatline on 2008-08-27
> ok well right now i really just wanna know about the legal aspects of this.

if its just me and a few guys using this once in a while, will they even care?

Well I guess you would have to define "they" first.  The RIAA/MPAA are notorious for aggressively pursuing anyone they think may have at one time or another heard music.  They have sued people that don't even have computers ([http://www.afterdawn.com/news/archive/7495.cfm](http://www.afterdawn.com/news/archive/7495.cfm)) and dead people ([http://www.theregister.co.uk/2005/02/05/riaa_sues_the_dead/](http://www.theregister.co.uk/2005/02/05/riaa_sues_the_dead/)).  So if you make any type of copyrighted music/video available and your security isn't 100% airtight... well, I don't have the b@lls to try it.  A buddy of mine at college almost got expelled for downloading *part* of the movie *SuperTroopers.*  What they're doing is most likely an abuse of the law and will (hopefully) be thrown out, but I personally don't have the time or money to deal with that.  Also, you would probably be grounded until you are 36.

Your ISP - this I can't really say.  Aside from the extremely poor upload speeds, I can tell you that they will almost assuredly slow down/cut off your connection if you guys transfer more than 100GB, maybe even less.  It isn't like they have someone checking on you, but if you go over a certain imaginary line, their systems flag you.  Depending on the ISP, this will either lead to A) the nice letter telling you to stop, B) they slow down your connection, or C) they say you were violating the Terms of Service and pull the plug.  You (or in this case your parents) agreed when they signed up for the DSL account to not do exactly what you are attempting.

However, setting up a home file server is never a bad idea, and as **jerome1232** said, it would be good experience.  You could get something like the Western Digital MyBook World Edition, or you can build your own, using practically any old computer, even one that doesn't run windows well - an old Pentium III with 512MB would probably be fine.  Alternatively, you could build something yourself using:
[LIST]
[*]Computer Case + Power Supply
[*]Motherboard
[*]CPU
[*]RAM
[*]internal Hard drive (preferably SATA but IDE is ok)
[/LIST]

---

### Post by hackerlife on 2008-08-27
yeah we were planning on building/restoring a comp for this project.
but holy crap i never realized this would be such a problem with my isp.
so there is no way this is going to happen, and i dont really have any need for a lan type server, so i guess i might just know all i need to know.

thanks for all the help to everyone who contributed!

-Will

---

