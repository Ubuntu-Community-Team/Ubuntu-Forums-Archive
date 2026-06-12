---
title: "What happened to UHS? &amp; My experience with WHS and why we can do better."
date: 2008-06-19
forum: The Cafe
---

### Post by garethsimpsonuk on 2008-06-19
Hi I've been thinking about the Ubuntu Home Server project ( the name should be changed ) and I went and checked their website last week and it was gone! I checked again today and it's back up although the thread on here says 'closed'. So I'm wondering if it's still in development.

Some of you may have seen a post of mine 2 days ago where I totally got fed up with linux in general and particurlarly Samba. It was all my fault not anyone else but I gave up as it was all way over my head! After 2 months I still didn't have my server up and running the way I wanted it. 
I decided to burn off the .iso I had collected of windows home server. 
I actually had a hard time setting it up. The C drive has to be bigger than 60gb.. I had a 40,60,80,80 and an add in card with a SATA 200gb but because the 40 was primary master it wouldn't have it. So I opened him up and swapped them round a bit. 
Then I was receiving some 'UI subsystem error' which was a pain but I got that sorted. There was a few other driver issues ( ubuntu didn't even need these ) but 'eventually' it was installed.
I installed the 'connecter software' on my windows lappy ( considered trying it with WINE ) set up my shares, setup users, backup config etc. I must admit all the SMB / permission stuff was a lot easier in windows. The connecter console was pretty handy too. It's not as in depth as putty and not as slow as VNC although it shouldn't assume you're brain dead. 

The things that let it down are:

- WAMP is rubbish
- The 'website' is rubbish and not modifiable ( i suppose if your an ASP guru ((which I dont aspire to be)) you may be able to mess with it )
- There is a lot of the w2k3 stuff missing / hidden so you cant mess it up.
- Theres the obvious one about security
- Shares were soo sloooow! I tried editing a photoshop file directly on a share...no chance

Well there's a lot more such as restriction of configuration and the waste on resources and the little '28 day' timer in the system tray although that can be dealt with ;-).

Anyway a Ubuntu server setup can overcome all of the above but has it's own problems ( although some of these are a benefit to! )

- Ease of use - I have been using ubuntu server ( and now the desktop ) since my join date and although I've really enjoyed it, the learning curve is too steep for ppl not interested in linux / technology. This can be overcome with code!

....ummm thats it I think! I honestly thought I could think of more downsides but I cant. ( maybe commercial backing, but that's what sets open source apart! )

Anyway to cut a long post not so long I went back to Ubuntu ( with no GUI this time ). I'm in the process off getting back to where I was with my setup ( this time im not gonna mess up SAMBA ). 
When it's all done I will have functionality any home server will be proud of! Here's what I've looked at:

- Backup i.e. bacula / rsync
- LAMP
- Samba
- Torrentflux-b4rt - protected from dodgy torrents as it's linux, will scan b4 being used in windows
- AVG - I believe this can scan the whole network
- Jinzoora
- MythTV ( eventually linux MCE )
- Various handy php scripts like SMF, Wordpress, Wiki
- Skyping my house
- There's some php desktop thing, 4got the name.
- Monitoring my brothers usage as we get told off & capped for being in the top 5% of downloaders for the week ( virgin media )

There's more I've looked at but my point is that Ubuntu would make a safer, faster and generally better home server! If the project has sunk I can't believe it. 
I am a linux noob but I can setup sites / articles / advertising and I think I've got a good business head on me ( already setup a small business ). I will look into recruiting some devs if this isn't being done. 
The reaction I seem to see with a linux home server is like marmite ( love it or hate it if you haven't heard of marmite ). A lot of people will say ' all the tools are there already' which they are, they just need consolidating.

Hopefully I haven't bored anyone. What are everyone elses thoughts on this? I think this could be huge!

---

### Post by Lostincyberspace on 2008-06-19
I prefer Cent OS for my servers I like being able to type service (the name httpd, phpd ....) start/restart/stop to start and stop services I wish Ubuntu would integrate something like this.

---

### Post by garethsimpsonuk on 2008-06-19
I'm not sure what you mean? Being able to type commands to start and stop services? That's possible but I'm guessing this isn't what you mean. So do you think CentOS could be a good candidate for a home server project? I thought that distro was harder to use ( but more configurable ). 
I couldn't find any distros with a 'home server' project based on it. Which is surprising. 
People may say the OSC doesn't wanna copy microsoft, well it's not about that. With the advancement and availability of technology a need for this has emerged.

Thanks

edit: by the way I know this has been discussed a lot, this isn't a 'server gui' post. it's everything to bring the server into the home. 
the internet, mp3's dvd's digital TV, security, communications, voip, organisation, phones, games consoles... i could go on. your employer has a manager, a plane has a pilot, living things have brains. it's fact that for things to be run efficient ally they have to have a central control! Microsoft deserve some credit for realising this first!

---

### Post by garethsimpsonuk on 2008-06-19
I've been reading the uhs site and it seems that there is some great ideas there. I've just registered, we must be able to get this going again. who are the mods / owns the domain?

---

### Post by madjr on 2008-06-19
you could create a good media/file server with mythbuntu. It has some special config apps

---

### Post by garethsimpsonuk on 2008-06-19
yes exactly but my girlfriends familycouldn't set that up and they want a home network setup. mostofhe tools arealredy built.we just need a centralised console ( probably web ) and to integrate the tools / do most of the config b4 hand

---

### Post by klange on 2008-06-19
> **Lostincyberspace said:**
> I prefer Cent OS for my servers I like being able to type service (the name httpd, phpd ....) start/restart/stop to start and stop services I wish Ubuntu would integrate something like this.

Not sure what you're saying - that's exactly how I start my services on my Ubuntu server, just prepending an /etc/init.d/, only because I'm too lazy to write up any aliases.
/etc/init.d/apache2 restart
/etc/init.d/dovecot start
etc.

---

### Post by garethsimpsonuk on 2008-06-19
> **WindowsSucks said:**
> Not sure what you're saying - that's exactly how I start my services on my Ubuntu server, just prepending an /etc/init.d/, only because I'm too lazy to write up any aliases.
/etc/init.d/apache2 restart
/etc/init.d/dovecot start
etc.

yea it's a necessity for all distros surely

---

### Post by garethsimpsonuk on 2008-06-20
> **garethsimpsonuk said:**
> yea it's a necessity for all distros surely

Maybe this isn't as popular as I thought lol

---

### Post by garethsimpsonuk on 2008-06-20
If the devs for the project are still around I've posted on the forum

---

