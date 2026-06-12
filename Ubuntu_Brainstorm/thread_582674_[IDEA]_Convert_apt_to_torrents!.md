---
title: "[IDEA] Convert apt to torrents!"
date: 2007-10-20
forum: Ubuntu Brainstorm
---

### Post by 1337455 10534 on 2007-10-20
There has been one (minor) post about this before, but we should seriously switch apt http downloads to torrents. It'll be faster, it'll save money (bandwith etc.), it'll be more reliable!
Ubuntu has an imbedded Bittorrent client, so the only hurdle would be to set up servers with a (libtorrent based, google it! :)) super seeding torrent clients, upload every UNIX program in existance into torrents, and tell apt where to get each!

In summation;
Get apt to convert from http to something more practical (over the course of 2 years, mebbe 3)

---

### Post by toby_1_kenobi on 2007-10-20
I've had this thought before as well, especially when doing a dist-upgrade at a time when the ubuntu servers are most overloaded.

---

### Post by m0eman on 2007-10-20
Although I think this is a great idea, it isn't going to work for everyone. Many people cannot use torrents for downloading. (students, people using an ISP the blocks or limits torrents...) This idea would be more practical if it were off by default but the user is able to select a mirror which uses the bittorrent protocol.

---

### Post by AlexenderReez on 2007-10-20
we have apt-torrent ...

> [http://sianka.free.fr/?lang=en](http://sianka.free.fr/?lang=en)

---

### Post by Choad on 2007-10-20
a great idea! three things tho: we should make sure it doesnt use the default bittorrent port (because isps will throttle this), we should encrypt the protocol (again, because of isps), and finally we would need to open the port in iptables by default.

---

### Post by screaminj3sus on 2007-10-20
and working upnp for people with gay routers

---

### Post by m0eman on 2007-10-20
Im all for encrypting and switching up the port, but i think that a hole in the iptables shouldnt be opened unitl the update is actually downloading/seeding

Which brings me to my question. When is the update being seeded and by who? Can you opt out of seeding but still use the bittorrent method? I think there will be some people who don't want to be seeding the updates because they just want to get the updates and be done.

---

### Post by Zdravko on 2007-10-20
Nice idea. BTW, what is a gay router?

---

### Post by DizzyTech on 2007-10-20
Sorry, accidental double post.

---

### Post by DizzyTech on 2007-10-20
Bad idea.  While the idea is great, the default torrent app does not work for me.

---

### Post by Zdravko on 2007-10-20
But for other users it may work!

---

### Post by 1337455 10534 on 2007-10-20
So the current apt system should not be replaced, just set to torrents by default.
Good.

---

### Post by m0eman on 2007-10-20
> **1337455 10534 said:**
> So the current apt system should not be replaced, just set to torrents by default.
Good.

NO, NOT DEFAULT!

---

### Post by snake444 on 2007-10-20
maybe it should download by torrent and http together 
some chunks with torrent and some with http

---

### Post by smartboyathome on 2007-10-20
> **snake444 said:**
> maybe it should download by torrent and http together 
some chunks with torrent and some with http

Or, maybe it should test to see which would offer the fastest speeds. I have set my server to a fast one, so I wouldn't necessarily want to download torrents which usually get 2-300 kb MAX in my experience.

---

### Post by 1337455 10534 on 2007-10-21
torrent + http?? Invent a new protocol??
Wow.

Anyways, why not by default? If made a secondary option, potential noobs with perfectly fine routers will be taxing servers...
How about put both options on a list, but torrents first (same size; bulleted one)

---

### Post by m0eman on 2007-10-21
> **1337455 10534 said:**
> Anyways, why not by default? If made a secondary option, potential noobs with perfectly fine routers will be taxing servers...
How about put both options on a list, but torrents first (same size; bulleted one)

If made a primary option, potential n00bs with bad routers will not be able to get updates...
Potential n00bs might not know what a torrent protocol is, and might leave it set to that...
This is a good idea, but it must be advanced users using it. Users that can open router ports, and firewall ports and know if thier isp supports the torrent protocol. So this option should be tucked away in the repositories dialogue.

---

### Post by 1337455 10534 on 2007-10-21
True. I remember me 4 months ago :lolflag:.
Hows about putting http download first on the list, torrent download second with a little "*" saying "Reccomended for advanced users..."

---

### Post by Zdravko on 2007-10-21
No, not default. Just an option.

---

### Post by Frak on 2007-10-21
Hey, if anybody gets done with this before I do, great job.

apt-torrent is a peice of work :D

Also, you can "Choose Best Mirror" to spread out the load.

---

### Post by Zdravko on 2007-10-21
Yes, that would be wise.

---

### Post by snake444 on 2007-10-21
when you enable the torrents download there will be an advanced button that you can set the upload speed and then an radio boxes with this option
Stop seeding after
(o) 5 Minutes
() 10 Minutes
() 30 Minutes
() Never
() Other ____ minutes

so every file you dwonload it it will continue seeding it

---

### Post by smartboyathome on 2007-10-21
> **snake444 said:**
> when you enable the torrents download there will be an advanced button that you can set the upload speed and then an radio boxes with this option
Stop seeding after
(o) 5 Minutes
() 10 Minutes
() 30 Minutes
() Never
() Other ____ minutes

so every file you dwonload it it will continue seeding it

Wow, since my computer can be on for days at a time, this might actually help the servers. :)

---

### Post by LaRoza on 2007-10-21
Why not? Because some ISP's severely restrict torrents, and not everybody would want such a service on their computer.

---

### Post by Arathorn on 2007-10-21
> **1337455 10534 said:**
> torrent + http?? Invent a new protocol??
Wow.
I know it's possible to simultaneously download from ed2k and http, isn't such a hybrid possible with torrent as well?

---

### Post by smartboyathome on 2007-10-21
> **Arathorn said:**
> I know it's possible to simultaneously download from ed2k and http, isn't such a hybrid possible with torrent as well?

It should be, but what I was talking about is it detects which would be fastest, and uses that (as some people wouldn't download a certain piece of software).

---

### Post by Frak on 2007-10-21
> **smartboyathome said:**
> It should be, but what I was talking about is it detects which would be fastest, and uses that (as some people wouldn't download a certain piece of software).
The only thing I was modifying apt-torrent for in the first place was for more experienced users to use apt-torrent instead as an option instead of bogging down the servers.

Give the user the choice, NOT DEFAULT.

---

### Post by snake444 on 2007-10-21
better that the menu will be like that
Download packages via
(o) http - default
() http + torrent - recomended
() torrent

and the http+torrent will be like in emule that can download ed2k+http
so that wont be a big problem

and if you enable the http+torrent and your isp shapes your torrent bandwidth it wont be a problem for you cause it will download all by http...

now you need to show this topic to developer:)

---

### Post by Perpetual on 2007-10-21
Good idea but I have to lean towards the NOT DEFAULT side and make it an option for users who understand it and know how to forward ports in their router.  Having a couple thousand unconnectable peers will do the torrent no good.

With that said, if it were an option, it would be my choice for upgrades.

---

### Post by Skerit on 2007-10-21
Well, we're clearly not getting the point, huh? Though users should be able to choose, that's a no-brainer, ubuntu should decide which protocol is best for the host computer on it's initial run. (So, if the downloads dont work because of some router-thing, it should fall back to the regular method - That IS the most logical step, if apt-torrent fails, automatically switch to apt-get, like how Gutsy tries to run compiz but fals back to regular metacity if it fails)

However, the seeding part should be an "opt in" choice, not everyone will be as pleased to know their computers are sharing files without them knowing it. 

Anyway, I do believe this is a wonderful idea, I don't know if this could be done before Hardy, however :(

Oh, and this forum is a bit more advanced to use the word "gay" for something bad. Please try to keep up with the 21st century.

---

### Post by Frak on 2007-10-21
> **snake444 said:**
> better that the menu will be like that
Download packages via
(o) http - default
() http + torrent - recomended
() torrent

and the http+torrent will be like in emule that can download ed2k+http
so that wont be a big problem

and if you enable the http+torrent and your isp shapes your torrent bandwidth it wont be a problem for you cause it will download all by http...

now you need to show this topic to developer:)
Also, another option for "Download via FTP/HTTP and seed via Torrent"

---

### Post by smartboyathome on 2007-10-21
> **Frak said:**
> Also, another option for "Download via FTP/HTTP and seed via Torrent"

I don't think that is possible at this point in time.

---

### Post by Frak on 2007-10-21
> **smartboyathome said:**
> I don't think that is possible at this point in time.
It's possible.

---

### Post by smartboyathome on 2007-10-21
> **Frak said:**
> It's possible.

I guess it IS possible, but you would have to set up a torrent, and then have that torrent tie into the seeding torrent. It is plain messy. >.<

---

### Post by 1337455 10534 on 2007-10-21
I just installed apt-torrent, and I have to say it is very pleasing! It barely diverges from apt-get (update: sudo apt-get update vs. sudo aptitude update) and retains all but "Super Cow" functionality. Mebbe apt-get and -torrent should have some coffee together and work something cool out :)!
My only complaints are;
> the package selection is extremely small. Perhaps a list of available packages would be nice (to apt-t devs out there).
> I have brain farts.. .'aptitude' is difficult to spell at the same speed and accuracy  as 'apt-get'... perhaps it should be changed to 'apt-t' :lolflag:! Wait, I'm serious...

---

### Post by Frak on 2007-10-21
> **smartboyathome said:**
> I guess it IS possible, but you would have to set up a torrent, and then have that torrent tie into the seeding torrent. It is plain messy. >.<
There is a way to have a torrent point to the main tracker to get the master torrent file information. Since that is universal (i.e. it all points to the tracker) everything can be routed through it.

---

### Post by 1337455 10534 on 2007-10-21
To Frak:
You seem very apt-torrent initiated. Tell me, if I install a program via apt-t, will it be seeding it? If so, can I mangae the seeding options anywhere? If not, why not?
If I just turn on my box, will apt-t start seeding?

---

### Post by Frak on 2007-10-21
> **1337455 10534 said:**
> To Frak:
You seem very apt-torrent initiated. Tell me, if I install a program via apt-t, will it be seeding it? If so, can I mangae the seeding options anywhere? If not, why not?
If I just turn on my box, will apt-t start seeding?
I believe the apt-torrent daemon is initiated when you start up. I haven't delved very far into it, but there should be a configuration file in /usr/lib/ that you can edit.

---

### Post by rudeboyskunk on 2007-10-21
The last time this idea was posted I voiced my support, and I do so again.  +1.

---

### Post by 1337455 10534 on 2007-10-21
I guess I never offically did, so +2 (for my friend, he doesn't have an account)!

---

### Post by Megatog615 on 2007-10-21
For router issues, wouldn't UPnP help?

---

### Post by amlucent23 on 2007-10-22
Although I see the value in this idea, really it could prove to be a most efficient method of application/update delivery. That being said, I will play the devils advocate.

What is to stop some anti ubuntu and foss hater from tampering with updates then seeding them out to non suspecting users? (hash files maybe)

And most importantly, this seems like it would take a lot of time=money to develop and implement. Why fix the current system if its not broken?

Dont hate, I'm just being realistic.

---

### Post by Sturmeh on 2007-10-22
For some of us, that is incredibly unconviencing...

Down here in Australia, we have superb HTTP download rates on the repos, as for torrent
s they are slow, because we get really bad upload speeds.

---

### Post by Shin_Gouki2501 on 2007-10-22
basically there should be soem "transparent" mechanism which LETs u decide wether u want to use torrent sources or NOT.
So if ur not able to use torrent soruce its redirects u automatically to HTTP but before it checks torrents, idea?

---

### Post by 1337455 10534 on 2007-10-22
OVerall, what are your impressions? Some say it isn't convenient, but it wouldn't hurt to just keep it available...

---

### Post by Skerit on 2007-10-22
> **Sturmeh said:**
> For some of us, that is incredibly unconviencing...

Down here in Australia, we have superb HTTP download rates on the repos, as for torrent
s they are slow, because we get really bad upload speeds.

But that's because those kinds of torrent *need* user-input! 
Those regular torrents (like those lesser-legal ones we all know and, maybe, love) aren't "super seeded" like regular downloads are.  How many servers host ubuntu? If, in theory, we make all the http-servers seed, the speed would only improve as regular users will also share with others ...

I might be blinded by this, but I'm only seeing the benefits :)

---

### Post by XioNoX on 2007-10-22
I thinks that it is a good idea to add torrents download. Fast for many people, no/less server overload, less bandwich to buy.
But there are negative aspects, not everybody CAN use it : corporates (firewall), restrictive ISP (bandwich limit, filtering,...), router not UPNP... or WANT use it : they think it is illegal, they are stupid,...
So a advance button in the end of the install guide where ther will be between many others option 
[ ] Use bittorrent if possible
 could be cool :)
so, +1

---

### Post by Frak on 2007-10-22
> **amlucent23 said:**
> Although I see the value in this idea, really it could prove to be a most efficient method of application/update delivery. That being said, I will play the devils advocate.

What is to stop some anti ubuntu and foss hater from tampering with updates then seeding them out to non suspecting users? (hash files maybe)

And most importantly, this seems like it would take a lot of time=money to develop and implement. Why fix the current system if its not broken?

Dont hate, I'm just being realistic.
One files md5sum is constant. Let's say they did change the file, the md5sum would change, but if you always downloaded a master torrent file from the official repo, then nobody could change the expected md5sum, so the tampered program would be tossed.

---

### Post by 1337455 10534 on 2007-10-22
Not unless it was efficiently done!!
Example of a torrent site with info on the downloads:

Name | Size | Files | Health | Speed | [COLOR="Red"]**md5sum**[/COLOR] | Last Updated

Would be the column headings, and i sort of have a table in mind.
Under each heading, there would be corresponding file info, and you could click the name of a file to download it...

---

