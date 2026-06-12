---
title: "Outdated server needs and upgrade"
date: 2015-09-30
forum: Server Platforms
---

### Post by kablizzo on 2015-09-30
Hello Ubuntu Community! It's been a long time since I've been here. Frustrated with windows, I tried Ubuntu back in 2005 and have never looked back. A huge thank you to the entire community, developers, and experts who take time to monitor these forms. You've helped me 10fold during my conversion from windows I am hoping you can help me again.

I am posting on behalf of my employer. I find myself working at in non-profit call center environment doing good work on a shoestring budget. We all log into terminals that PXE boot to our server running Ubuntu 8.04. Being that this version has not been supported for years, our outdated web browsers have been loosing functionality. First our ability to utilize youtube went (flash player outdated). Then Google Maps stopped working. Now we have to use a work-around for access to our credit card terminal (web based) which is really putting a damper on our productivity. Needless to say it is way past time for upgrading.

So the crew found out that I am an Ubuntu fanboy when I came to it's defense against a windows fanboy talkin' trash. Now I've been appointed the "expert" though I am far from it. However, I would like to help if I can.

My main question is: Can we log into one of the terminals with the root login and install a more current version of Ubuntu just like we would at a desktop? Our terminals are basically older PC's with their hard drives unplugged set up to boot from the network, but they do have working optical drives. I am thinking, if it *is* this simple, we could just install the most current version of Ubuntu on it's own partition and have a dual boot environment on the server so we can still access our old files if we need to? This is how I keep my home system up-to-date. I always have the most recent release installed on one drive and 2nd most recent release on the other. Every time there is a new release I just replace the oldest version with the newest and do some maintenance in GRUB to get old menu options out.

Something tells me it's not this simple, though. I'm certain what we log into from the terminals is Ubuntu 8.04. It looks like what I used to use on my home PC when I ran Hardy Heron Desktop Edition but when I look in system monitor it shows 4 processors and 3 gigs of memory so it must be Server Edition? I don't even know the difference really,  I feel like I am getting in way over my head. I have researched and read about PXE boot servers but a lot of the terminology is hard for me to wrap my head around. I'm just not a network guy.

So thank you for taking the time to read my plight. Apologies if I posted in the wrong area or did something wrong. I appreciate any insight or advise that can be given.

---

### Post by darkod on 2015-09-30
When you say the terminal PXE boot, is the PXE server setup on the ubuntu server I assume?

Also it depends which other functions the ubuntu server has.

Upgrading 8.04 in the real meaning of the word is not worth it. Not only that it's not supported any more, you would need to do three release upgrades to get to the current 14.04 (if that's your goal). With so many subsequent upgrades something is destined to go wrong.

In fact, rather than dual boot 8.04 with 14.04, it might be a better idea if you can spare/get some basic machine and do a clean install of 14.04 on separate machine. That will also allow you to migrate the functions bit by bit while the current server is still working and all of your network. During migrations of this kind you always have to think what will happen if the new server doesn't work as expected, and the impact the organization will have.

Imagine you decide to format the current server and install 14.04 thinking you will manage to configure it in an hour or two and the office is up and running again after that. Then it turns out you can't make it work for a week... :)

A second machine with 14.04 and step by step migration is definitely your best choice IMHO.

On a side note, flash issue might be related to the browser itself, not to the OS. Flash is terribly unsafe and many browsers have begun blocking it.

Also, are we talking here only about the server OS (the 8.04 server) or also the client OS for the PXE clients. Because that has nothing to do with each other. If the terminals support booting it, you can have a newer OS image in the PXE setup and the terminals can boot it even if the server OS still stays 8.04. I havne't worked much with PXE but the way I understand it the client OS images are not directly related to the underlying server OS.

---

### Post by kablizzo on 2015-09-30
Thank you for replying :p I appreciate it so much!

> **darkod said:**
> When you say the terminal PXE boot, is the PXE server setup on the ubuntu server I assume?

Absolutely. All of us (about 12) log into the same computer. We can all see each others profile under /home.

> **darkod said:**
> Also it depends which other functions the ubuntu server has.

I think it's only purpose is for us to log into it and use our web based tools (database, credit card, wiki, calendar...etc.) and some of us make documents and maintain spreadsheets in open office.

> **darkod said:**
> Upgrading 8.04 in the real meaning of the word is not worth it. Not only that it's not supported any more, you would need to do three release upgrades to get to the current 14.04 (if that's your goal). With so many subsequent upgrades something is destined to go wrong.

Ya, said windows fanboy I talked about in my previous post is totally gung ho on diving in and trying something out over a weekend. I am completely freaked out about loosing our server if it gets screwed up. But hey, he's in a management role, I am not, so w/e.

> **darkod said:**
>  In fact, rather than dual boot 8.04 with 14.04, it might be a better idea if you can spare/get some basic machine and do a clean install of 14.04 on separate machine. That will also allow you to migrate the functions bit by bit while the current server is still working and all of your network. During migrations of this kind you always have to think what will happen if the new server doesn't work as expected, and the impact the organization will have.

Imagine you decide to format the current server and install 14.04 thinking you will manage to configure it in an hour or two and the office is up and running again after that. Then it turns out you can't make it work for a week... :)

A second machine with 14.04 and step by step migration is definitely your best choice IMHO.

On a side note, flash issue might be related to the browser itself, not to the OS. Flash is terribly unsafe and many browsers have begun blocking it

All our issues are related to the browser itself. We can't get it updated. It's more than just flash we are having problems with security seal. Our database needs to get updated and won't be compatible with the version of firefox we are using. It's a real bummer. When the repositories went away, I think a couple years ago, I was the one that figured out how to point the package manager to the "archive" repositories for all the no-longer-supported versions. The newer packages for firefox, chromium...etc. They just won't install with our version of synaptic.

> **darkod said:**
> Also, are we talking here only about the server OS (the 8.04 server) or also the client OS for the PXE clients. Because that has nothing to do with each other. If the terminals support booting it, you can have a newer OS image in the PXE setup and the terminals can boot it even if the server OS still stays 8.04. I havne't worked much with PXE but the way I understand it the client OS images are not directly related to the underlying server OS.

I think both the server and the OS we log into are 8.04. I suspected the environment we log into was a separate install of ubuntu based on what I've read about PXE, I just don't get how to put the image on the server and tell our terminals to boot from it. I know the first step is doing a fresh install of the desktop version we want to use and update/download all the stuff we want to have access too but then I get completely lost when it comes to putting it on the server and getting everyone to get to their new login screens on the terminals. That would be great news, IMHO, if we didn't need to upgrade the server because as far as serving us data, it's solid and hardly ever needs to be rebooted. I'm pretty sure nobody's maintaining it like they should though and that's pretty sad :(.

---

### Post by mastablasta on 2015-10-01
pretty silly setup in this day and age where you can get cheap PC hardware. even used 2nd hand hardware is very good these days. you could maybe even find a company that retires them after their 5 year lease expires and they might give it for free to charitable org. and then you can set up a proper server.

---

### Post by darkod on 2015-10-01
Here is one example how to prepare ubuntu ISO to be booted by PXE: [http://www.serenux.com/2010/05/howto-get-an-ubuntu-live-cd-to-boot-off-a-pxe-server/](http://www.serenux.com/2010/05/howto-get-an-ubuntu-live-cd-to-boot-off-a-pxe-server/)

You should be able to easily adapt this to your setup. It uses version 10.04 but you can use 12.04 or even 14.04 if you think your terminals support it. Also it uses NFS for the actual ISO file, I don't know if your setup has something similar, but if it doesn't I think you can do this without the NFS part. The ISO can be on the ubuntu server and because it is also acting as PXE server it should be able to use local file.

This is the part to update the client OS/ISO. If you decide to upgrade the server OS too, we can discuss it in more details. I already posted some ideas about that too.

---

### Post by kablizzo on 2015-10-01
Thank you so much for the link to that blog. I didn't find that one through my searches and it seems to be in a much simpler language than the one's I have come across. I don't really understand what you mean by NSF for the actual ISO file though. Google tells me NFS is Network File System (after offering a link to a bootleg ISO of Need For Speed ironically, lol).

So do you mean instead of an ISO file, like from a live CD, we move the entire file structure of the client OS to it's own directory? Like /srv/ubuntulivecd/i386 in the example? I think I understand, then it's just a matter of changing permissions and configuration files I guess...

So the game plan that has been proposed by my manager is to try to do a fresh install of Ubuntu Server on some new hard drives so we can preserve the old system on the current drives. He envisions us working on it after hours and being able to restore our current server by simply plugging in the new hard drives. I suggested buying a new or gently used system to play with instead because I am so nervous about changing something and not being able to change it back. He shot that idea down. I guess we'll see how this goes.

After we have a working server we will follow your example to put our client OS on it and try to boot to it from our terminals. I really hope this works :(.

@mastablasta I agree. Our setup may have even started out silly because our IT guy that set this up was quite an interesting character and we were begging him to update our system before he quit ad he wouldn't. I feel like maybe he didn't even have the knowledge to do it right which makes me super uber mega nervous about playing around with it. My manager (the guy I'm working with on this) thinks he outsourced someone else to set it up and was basically just a pretendo IT guy.  Also, my initial suggestion of getting new hardware and a new IT guy was shot down. "We can do this ourselves" says the manager windows fanboy I work for. I hope he is right :(.

---

### Post by darkod on 2015-10-01
I haven't worked much with PXE but the logic is that the clients can boot what you prepare for them. From that point of view maybe you will need to modify the original ubuntu ISO in some way, depending if you need any software not included by default in the ISO.

If the original ISO satisfies your needs, perfect. Otherwise you have to google around how to make changes to the original ISO and make a new ISO/image to use as client OS. From what I could see in that tutorial they export the files as read-only, so clients will not be able to make any permanent changes to the files on the server. Which is probably best because you don't want anyone playing around with the files that all clients are booting up. And since the terminals have no local storage, they have nowhere to guard any possible changes, they will depend only on the files from the server.

As soon as you get that planned, you're good to go. Setting it up shouldn't be complicated.

---

### Post by kablizzo on 2015-10-01
Found this in the Ubuntu wiki. Don't know how I missed it before I guess I was just scanning for "PXE Boot" and it's actually called diskless boot. it seems like a great how to though and it describes what we have (and want to continue). Just wanted to add that to the thread. I've stumbled across countless noob threads like this one with helpful links in it, maybe this is returning the favor to some other noob using the search engine.

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

Thanks for all the helpful advise I really appreciate it I think we have a good starting point. I feel a teeny bit more confident now ;)

---

