---
title: "Minimal hardware for server"
date: 2010-09-08
forum: Server Platforms
---

### Post by theDaveTheRave on 2010-09-08
Dear all,

I have been reading this [thread]("http://ubuntuforums.org/showthread.php?t=1561979&highlight=minimal+server+hardware") and it seems to be asking a similar, but subtly different question to the one I would like to know.


You may wonder why I am asking this question...

I am thinking of starting a business creating web pages and supplying a 'enterprise server' type solutions, whilst still being highly cost effective - eg recomend the client to use an 'old' pc for the majority of their server needs (LDAP, mail,  firewall, web server etc).

I plan on doing all of this on a linux platform, so as to pass the cost savings of related 'microsoft enterprise systems' to my clients ~ thereby making my proposition more interesting to clients.


However I'm not sure if the 'old' pc idea will 'cut the mustard' in terms of serving web pages.

So my real question is, at what point does the speed of the internet connection reach a bottle neck with the speed of my CPU?

as an 'example' in case I'm not being very clear (which I'm not sure I am).

My old pc has an AMD athlon chip in it, and equally old 30GB and 40GB HDD (SCSI ~ did I mention that they are old!).

My intention is to set up a system to the above type specification at home, to see how long it takes me to do, and to give me an idea of what I should charge clients.

I understand all the technology, but initially (to save on personal startup costs) I was intending to use my old pc as my personal gateway to the world, $40 for the web registration for 1 year is a considerable saving compared to the $20 per month for a hosted service ~ although as soon as things are going and being 'profitable' I would most likely either upgrade my server or get a hosted service.

Your oppinions also on the level of power consumption that the server will most likely use, any tools I can download onto the server to 'determine' the power consumption over any given period?

Thanks in advance.

David

ps, just found 'powertop' for an electrical equivalent of top - nice stuff, just love linux!

---

### Post by Naitsirhc Hsem on 2010-09-08
I have run ubuntu webserver on a 10gb hd pentium 4  machine.  I don't think you will run into any problems.  ubuntu can be pretty light

---

### Post by LightningCrash on 2010-09-08
It depends on the volume of traffic.
Something like a big ZenCart site is going to take a little bit of CPU power (and memory!), you could probably fit one or two on an older Athlon before you would experience any problems.

If you had more of a box, one thing I would recommend is that you use a VM, so you can just migrate the VM to the new box when you upgrade.
With slower hardware (I'm assuming Athlon under 1GHz), you're going to want all the performance you can get.

Your upload speed is probably abysmal so you're going to run out of upload bandwidth first anyway.
Definitely host any static content offsite in a CDN like Amazon AWS.

---

### Post by Calaway21 on 2010-09-08
I have been using Ubuntu Server 10.04 since June. We picked up an old Dell Poweredge 2400 with two pentium 3 600Mhz processors, 1GB memory, 6 SCSI HDDs. I decided to use it as a cheap office server for web development. It also has public access so that our clients can view progress on their websites and so that we can show our current projects to potential clients. I have six drupal sites currently running on it, all of which get several hits daily plus the collaboration of the my web development team, which is constantly uploading pictures, graphics, text, etc. 

This machine runs at an average load of 0.4 over the past month and uses approximately 47% of RAM and 0% of swap.

In my opinion, you should have no problems whatsoever especially if you are only serving static web pages. I think that you will overload your bandwidth before you have problems with your machine. Assuming that you will be using a residential connection.

As far as tools go, I use smartmontools to monitor my hard drives. You can set it up so that it will email you if you have a drive that is outside the tempeature threshold or if it is about to keel over. You can find more about it here:

[http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/]("http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/")

You should also look into systat. I haven't found a really good internet tutorial on this one.

---

### Post by theDaveTheRave on 2010-09-08
hi all,

Thanks for the input, seems like for an initial 'startup' this will work just fine.

One minor thing to add, I intend to use this particular machine as a 'home server' also - so mail, ldap login (on all the other devices), and also use it as a bit of a 'tv system' (using a myth backend, and then serving the tv out to the local network with vlc (probably).

Also will have it hooked into the stereo - so we can get all the online radio stations.

The only downside to all this is that I will need a 'GUI' of some form. I'm thinking that will mostly be for the TV experience ~ we recently acquired a really cool projector - for 1/3rd of the cost we get a screen that is over twice the size, the 2 year old twins are just totally mesmerised by it :D I must admit that the colour depth in the animated features is just awesome) can't wait to get the 3d glasses and the blu-ray player! - but I'm getting off topic... 

so where was I... ;)

I do intend to move up to a 'business' service for the phone / internet provision - so hopefully static IP will be included and I will get a higher incoming bandwidth.

---

### Post by gobbledigook on 2010-09-08
> **theDaveTheRave said:**
> The only downside to all this is that I will need a 'GUI' of some form. 

well that does change things somewhat ;) for serving a GUI in enough quality to serve your projector, you will need a half decent graphics card with at least a s-video out. as for getting the GUI i used to run xserv with fluxbox but i had a lot of issues running things on start... so i have now used the desktop 10.04 which is easy to start applications but does run slower. i have . 2.5ghz amd and 2gb ram. things like ssh'ing in takes a few seconds longer and boot takes almost 3mins as opposed to about 1min before but hopefully you won't need to do too many reboots :)

---

### Post by LightningCrash on 2010-09-08
> **theDaveTheRave said:**
> One minor thing to add, I intend to use this particular machine as a 'home server' also - so mail, ldap login (on all the other devices), and also use it as a bit of a 'tv system' (using a myth backend, and then serving the tv out to the local network with vlc (probably).

The MythTV backend might be a big load on the system, depending on how it's configured, transcoding, etc.

Just monitor your system stats (I use rstatd on the server and poll with xmeter, rsysinfo and rup) and make sure you're meeting your SLAs with your customers. Gkrellm also works on both.

---

### Post by Calaway21 on 2010-09-09
IMO your asking too much from a single old computer. If I understand correctly, you want to host public web pages, mail, use LDAP for home logins, and also be a full-fledged media center machine all on a sub-1GHz processor. 

Your machine would work fine for being a public web server (low-traffic), mail server, etc. When you start adding a GUI you are requiring much more RAM and CPU cycles. That's why you'll find retired desktops as office servers a lot of the time. They just don't have enough umph to run moder desktop applications but, they can share data no problem.

You should just build a media PC for your media purposes.

---

### Post by theDaveTheRave on 2010-10-25
@Calaway21

Yes I am aware of that, mostly the system will be a web server, and I'll upgrade to something with more 'oomph' when everything is working out - we still don't receive digi tv at my location for the moment, but once we do, I expect I will need to get a better system anyhow.

Thanks for everyone for adding in their comments, you have basically made me feel happier about the idea of what I am planning to offer.

Thanks again.

David

---

