---
title: "repositories via bittorrent"
date: 2006-01-11
forum: The Cafe
---

### Post by borisattva on 2006-01-11
so i'm sitting here redownloading all the updates after a clean reinstall for the 8th time (lost of playing aroudn with different configurations k/ubuntu, plus several dapper retries) and i'm wondering about all the traffic of downloads and those of other users create, and the load it puts on the hosting servers.

alright so they are 'sponsored' 'funded',. what ever...
still what a waste of resources considering that we've had bittorrent available for how many years, 2-3? previous technologies?

when is the repository aproach going to adapt with the evolution and incorporate bittorrent protocols (or whatever comparable)?

with each installer using the resources i believe its only fair to offer an option to upon download become a seeder (never mandatory of course, for a number of considerations) i would gladly return 2x the traffic i downloaded, and have all the mirrors be seeders as opposed to dedicated servers.

only negative i can think of is security of all that code being transmitted and potential for garbage, but even that has been addressed with recent bittorrent improvements.

or am i just not fully understanding what i'm talking about?
whats the hold up?

---

### Post by BoyOfDestiny on 2006-01-11
[QUOTE=borisattva]so i'm sitting here redownloading all the updates after a clean reinstall for the 8th time (lost of playing aroudn with different configurations k/ubuntu, plus several dapper retries) and i'm wondering about all the traffic of downloads and those of other users create, and the load it puts on the hosting servers.

alright so they are 'sponsored' 'funded',. what ever...
still what a waste of resources considering that we've had bittorrent available for how many years, 2-3? previous technologies?

when is the repository aproach going to adapt with the evolution and incorporate bittorrent protocols (or whatever comparable)?

with each installer using the resources i believe its only fair to offer an option to upon download become a seeder (never mandatory of course, for a number of considerations) i would gladly return 2x the traffic i downloaded, and have all the mirrors be seeders as opposed to dedicated servers.

only negative i can think of is security of all that code being transmitted and potential for garbage, but even that has been addressed with recent bittorrent improvements.

or am i just not fully understanding what i'm talking about?
whats the hold up?[/QUOTE]

The other issue is not everyone has a good connection, or has connection limits. I'm only allowed 10gig up a month, that sounds like lot, but when I was seeding knoppix live dvd, I ended up with a warning. 

For users with something like dial up... ugh... Not happening. As for now you have an alternative, DVD iso's with torrents of ubuntu repos are found online:

[http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)

---

### Post by gord on 2006-01-11
id also be wary of the fact that most repository downloads are small things, bittorrent only really works with larger files, if your only downloading a file for 20 seconds or so then thats not much uploading. it might be a nice idea for the big dist-upgrade times but you get the same effect by downloading the new .iso's from bittorrent sources

---

### Post by borisattva on 2006-01-12
[QUOTE=BoyOfDestiny]The other issue is not everyone has a good connection, or has connection limits. I'm only allowed 10gig up a month, that sounds like lot, but when I was seeding knoppix live dvd, I ended up with a warning. 

For users with something like dial up... ugh... Not happening. As for now you have an alternative, DVD iso's with torrents of ubuntu repos are found online:

[http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)[/QUOTE]

thats why i suggested giving an option to the downloader at the completion of the transfer something like ' now that youve downloaded all these pacakges, would you like to become a seeder so others can download it form you?" and then select the ratio that the user would like to contribute (1x, 2x. whatever) maybe even have some suggested choices preselcte based on the detected connection. and then having an automatig seeding when omputer is detected idle or whatever other choise the user makes.

as for the size of files making it pointless, that i did not anticipate as i said i only know the gist of technology not the neuances. perhaps insteda of brekaing up smaller files into multiple seeder having a threshold setting under which a file size is not broken up (or atleast not too much) and loaded from a user directly. even easier a single small file transfer will complete the contribution quicker and release the user from seeding privilegies.

how about that?

---

### Post by BoyOfDestiny on 2006-01-12
[QUOTE=borisattva]thats why i suggested giving an option to the downloader at the completion of the transfer something like ' now that youve downloaded all these pacakges, would you like to become a seeder so others can download it form you?" and then select the ratio that the user would like to contribute (1x, 2x. whatever) maybe even have some suggested choices preselcte based on the detected connection. and then having an automatig seeding when omputer is detected idle or whatever other choise the user makes.

as for the size of files making it pointless, that i did not anticipate as i said i only know the gist of technology not the neuances. perhaps insteda of brekaing up smaller files into multiple seeder having a threshold setting under which a file size is not broken up (or atleast not too much) and loaded from a user directly. even easier a single small file transfer will complete the contribution quicker and release the user from seeding privilegies.

how about that?[/QUOTE]

I dunno. I just can't see it as being necessary. If you are running a stable release, you should not have a huge amount of updates. For those really interested in saving same bandwith, there are torrents for dvd images etc. The other option is making your own apt-mirror, even if it's just the files you need.  This perhaps would have been applicable in the case you describe if you used apt-move. [http://packages.debian.org/stable/admin/apt-move](http://packages.debian.org/stable/admin/apt-move)

My main problem is low bandwith/restricted bandwith users, ISPs that are hostile to Bittorrent traffic, firewalls, and having users trying to configure ports to have access to updates... An example might be college students using peer 2 peer on the wifi network. They will cancel my account if I do that...

Bittorrent is already an option for savvy users. The easy (and I guess current solution) is to add more apt mirrors and servers. You have the option to make an unnofficial one. 

Anyway, for compressed files or poritions of (to update current files) Somthing similar to torrentzip might help cut down on the redling. 

[http://sourceforge.net/projects/trrntzip](http://sourceforge.net/projects/trrntzip)

I think updates should just work. The way it is now seems fine, and has so many options to prevent their servers from being overly taxed.

---

