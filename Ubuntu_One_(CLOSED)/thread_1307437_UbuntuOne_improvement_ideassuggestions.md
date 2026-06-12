---
title: "UbuntuOne improvement ideas/suggestions"
date: 2009-10-31
forum: Ubuntu One (CLOSED)
---

### Post by jondecker76 on 2009-10-31
I really like the concept of UbuntuOne and thought I would post some of the things that I would like to see added in the future to make this a really great service:

1) Firefox bookmarks syncing/sharing/backup
My wife could add a bookmark on her computer, and it will propegate over to mine as well..  Also, on a fresh install, these could be imported and make future setups a breeze!

2) Per folder syncing/sharing/backup (yes, I know this is in progress!)

3) Installed Applications syncing/sharing/backup
For example, I install gparted on my desktop..  Since my laptop is sync'd, it would also install gparted automatically..  Would be nice with an option to also sync the application's hidden folder. Also, on a fresh install, all your backed up applications automatically install for you once you set up your UbuntuOne client.. Again, installing and setup would be a breeze in the future!

Anyone else want to add to this list of suggestions?

---

### Post by SIXAXIS on 2009-10-31
For them to really compete with DropBox, they need to extend it to be integrated with Windows and Mac systems as well. DropBox integrates with Explorer, Finder, and I believe it also integrates with Nautilus.

---

### Post by eskar113 on 2009-10-31
Personally I'd love to see Thunderbird contact integration along side Evolution.

As far as integration with Windows, I just used Prisim to make it into a web application (if I'm using the right terminology ;) ) and it's been a semi-decent work around but if there is Win/OSX integration like with Ubuntu, that would be awesome :)

---

### Post by manoriax on 2009-11-01
Data should be saved encrypted on the server. And if this blocks the share-service, just decrypt the folders (would be better to be able to share single files, aswell) that the user wants to share with others.

---

### Post by donniezazen on 2009-11-01
Haha!! First U1 should have basic functions and bug-free to compete with other providers. Canonicals business plans are being forcibly imposed on free Ubuntu users.

---

### Post by joshuahoover on 2009-11-02
> **jondecker76 said:**
> I really like the concept of UbuntuOne and thought I would post some of the things that I would like to see added in the future to make this a really great service:

1) Firefox bookmarks syncing/sharing/backup
My wife could add a bookmark on her computer, and it will propegate over to mine as well..  Also, on a fresh install, these could be imported and make future setups a breeze!

2) Per folder syncing/sharing/backup (yes, I know this is in progress!)

3) Installed Applications syncing/sharing/backup
For example, I install gparted on my desktop..  Since my laptop is sync'd, it would also install gparted automatically..  Would be nice with an option to also sync the application's hidden folder. Also, on a fresh install, all your backed up applications automatically install for you once you set up your UbuntuOne client.. Again, installing and setup would be a breeze in the future!

Anyone else want to add to this list of suggestions?

All great suggestions! 

We do some of #1 already with our Bindwood Firefox plugin. For info on installing Bindwood, please see: [https://wiki.ubuntu.com/UbuntuOne/Tutorials/Bookmarks](https://wiki.ubuntu.com/UbuntuOne/Tutorials/Bookmarks) We're going to enhance the plugin in the future so you have more control over when it syncs and allow you to see bookmarks via a web UI.

#2 is on our roadmap for Lucid. It's a very popular request and one we look forward to providing users with. 

#3 is one we've discussed and it's a possibility for the future, but won't be done for Lucid. We think being able to ease system restore and setup is a good use case for Ubuntu One in the future.

Thank you,

Joshua

---

### Post by rectagonal on 2009-11-02
1) Evolution/Sunbird calendar syncing.
2) Letting my win32 tomboy at work sync with my U1 tomboy notes.
3) Epiphany support for synced bookmarks.
4) Let me browse my synced bookmarks from the web interface.
5) The ability to import data from other other clouds. ( Import contact's from google & etc ).
6) Let me edit the documents i've uploaded into u1 via the website. Integrate OpenGoo's document editor or something similar.

---

### Post by goseph on 2009-11-02
Ubuntu One needs the following to get the awesomeness seal of approval IMHO.

1) The server side software should be free to be consistent with the Ubuntu philosophy.

2) There ought to be clients for Windows/OSX/ other Gnu/Linux distros!

3) The backups should be incremental rather than absolute. Ie you point out what directories you want backing up and it automatically backs up only what is edited.

(I'm assured this is being worked on)

4) More than 2 GB for free would be nice but they have to actually make money from this thing so I'm easy. I guess they don't want to start a price war with dropbox.

The above implemented would make Ubuntu / Ubuntu one bad-***!

---

### Post by yaaarrrgg on 2009-11-03
I think Ubuntu One is great!

My only thought is it would be nice to be able to chose how/where the data is stored.  My personal preference (for the sake of not putting all my eggs in one basket) would be that cloud storage also be implemented with a point-to-point model like BitTorrect.

E.g. encrypt data,  chop up it up into tiny pieces, and spread it out redundantly across multiple machines that have Ubuntu One clients installed (and, which have opted to join a storage cloud).   If someone opts into a storage cloud, they essentially would share a slice of their drive, and store slices of their encrypted data on other people's computers.  Overall, it's equal give and take, but the advantage is that it's decentralized.  But it's a choice to opt in or out.

From a security standpoint, I don't see how it would be any less secure than SSL routed over anonymous machines/sniffers.  Same concept with encrypted packets.

A practical problem would be if people turn their machines off, it could degrade the cloud storage performance.  How would you guarantee machine up-time?  However, the machines up-time may be rated by other peers.  Perhaps the more a machine is up, the more choice of equally highly-rated peers they would have.  (IOW, if you want the most reliable cloud storage, always leave your machine on).  Otherwise, there may have to be an option on the level of redundancy the data would be stored at, assuming that some machines will turn off.

Just a few random thoughts.  :)

---

### Post by goseph on 2009-11-03
> **yaaarrrgg said:**
> I think Ubuntu One is great!

My only thought is it would be nice to be able to chose how/where the data is stored.  My personal preference (for the sake of not putting all my eggs in one basket) would be that cloud storage also be implemented with a point-to-point model like BitTorrect.

E.g. encrypt data,  chop up it up into tiny pieces, and spread it out redundantly across multiple machines that have Ubuntu One clients installed (and, which have opted to join a storage cloud).   If someone opts into a storage cloud, they essentially would share a slice of their drive, and store slices of their encrypted data on other people's computers.  Overall, it's equal give and take, but the advantage is that it's decentralized.  But it's a choice to opt in or out.

From a security standpoint, I don't see how it would be any less secure than SSL routed over anonymous machines/sniffers.  Same concept with encrypted packets.

A practical problem would be if people turn their machines off, it could degrade the cloud storage performance.  How would you guarantee machine up-time?  However, the machines up-time may be rated by other peers.  Perhaps the more a machine is up, the more choice of equally highly-rated peers they would have.  (IOW, if you want the most reliable cloud storage, always leave your machine on).  Otherwise, there may have to be an option on the level of redundancy the data would be stored at, assuming that some machines will turn off.

Just a few random thoughts.  :)

Very cool concept. If any one piece of data was copied 5 times and the average up time was 12 hours per day per user, anybody joining the scheme could have free cloud storage at one tenth of the disk space they dedicate to Ubuntu one at no running cost to any servers or back-up hosts.

Ok so you would have to give up 30GB of prescious disk space just to do better than the current system for free. Hmmm...... might be worth it if you splashed out on a one off terrabyte external hard drive to get 100GB cloud storage free?

---

### Post by yaaarrrgg on 2009-11-04
@goseph That might not be a bad deal with a dedicated drive.  Also, I suspect people would be inclined to pay a one time price for their own hardware rather than paying for a monthly service (since it gives people more sense of ownership).

Looks like there's a couple open source distributed files systems in development:

[http://en.wikipedia.org/wiki/List_of_file_systems#Distributed_parallel_fault-tolerant_file_systems](http://en.wikipedia.org/wiki/List_of_file_systems#Distributed_parallel_fault-tolerant_file_systems)  

I suppose the biggest downside, IMO, is that it might undercut Canonical's business model.  I actually want them to make money on their services. :)

---

### Post by GarrettFoster on 2009-11-05
[LIST]
[*]Clients for Windows, Mac, Xubuntu, Kubuntu, as well as other flavors of GNU/Linux
[*]Clients for mobile devices: Blackberry, Android :) , Windows Mobile, Symbian, Iphone
[*]The ability to choose what folders are synced, much like spideroak
[*]The ability to link with other online storage. For instance I could use the ubuntu one client to also keep my google docs and photobucket photos synced/backed up on my computers as well.  
[/LIST]

---

### Post by espen77 on 2009-11-10
My wishlist for U1-Santa:
[s]-synchronisation with symbian so I don't need to worry about many different address lists on phone, and computers.[/s]
-calendar integration. sync between gnome/evolution, U1-web, phone
-sync tomboy/U1-web with phone.
-sync the pictures in my phone to U1.
-be able to look at documents and pictures on U1-web without downloading them.
-be able to view, edit and delete your bookmarks on U1-web.
[s]-possible to give a url to a friend to show them a picture or a document, even if they don't have ubuntu one [/s]

-Esp-

---

### Post by rodrigo_ on 2009-11-10
> **espen77 said:**
> My wishlist for U1-Santa:
-synchronisation with symbian so I don't need to worry about many different address lists on phone, and computers.
-contain my mail inbox
-be able to look at documents and pictures on the web
-possible to give a url to a friend to show them a picture or a document, even if they don't have ubuntu one

-Esp-
These sound like good improvements, so please make sure you file bugs for them in Launchpad if they are not already there

---

### Post by andrea000 on 2009-11-10
I would like to be able to login to the web
from the desktop app like you can do with
dropbox.A photo album would also be a big
plus.

---

### Post by cb951303 on 2009-11-10
server side encryption
public folder
as much as sync options possible
win/mac/iphone/android client

would be in my list oh and please release the server source already :mad:

---

### Post by kevstar31 on 2009-11-10
Can you make it possible to get backed up files from the server via sftp?
I think this would be helpful to allow third party clients to use this service.

---

### Post by espen77 on 2009-11-10
> **rodrigo_ said:**
> These sound like good improvements, so please make sure you file bugs for them in Launchpad if they are not already there

Baby-steps....I haven't figured how Launchpad work yet. I've been a "Happy-camper" for many years, and I just figured it is about time to get a little more involved in the things that matter. :p

---

### Post by spacesearcher on 2009-11-11
I would like a button to add a subscription to my Amazon universal wish list :D

I also would like to see more info on the files in a different window estimated time/ % complete/ lists of files that changed that haven't been synced yet. 

I also would like to see more about security so I know how safe files are.

lastly have options for a rolling backup of files so you can go to previous versions.

---

### Post by manoriax on 2009-11-11
Which of these given suggestions have a chance to be implemented?

---

### Post by vashman on 2009-11-14
Lol, not alot most of them would cause more problems then give feature.  What I would like is to manage the contacts/notes on the web interface more like on a actual computer. ie: like have the file separated and managed like a file rather than using the editor which has more trouble running on special systems (separation of files and JavaScript/xxx applications).  I would also not mind some ads in the web interface if it pays any amount of what it takes to run the service, as long as it does not turn into one of those mishmash websites kind of like  a collogue.

---

### Post by jaxån on 2009-11-15
Sync photos: Put photo applications data directory under the "~/Ubuntu One"-directory
Sync phones contacts: Sync with Evolution, and then sync Evolution with Ubuntu One?
Running Ubuntu One sync client on other OS and distributions: Use the source, luke, it's free :)
Other client stuff, use your imagination, as you can sync everything under the directory ~/Ubuntu\ One. You "just" need to put the application data there.

When Ubuntu One syncs, there is a message on the screen, but it "only" shows how many files has been synced.  You can also hover the pointer above the cloud in the panel.

Browsing data on the server, like bookmarks synced with Firefox, must be done by Cannonical though...

But still, put the ideas here, so it could be sugested if there is an easy to put it into an application, or if it's easier to configure the application instead.

---

### Post by osomphane on 2009-11-16
1) Slow
2) Can't sync outside ubuntuone folder
3) Unlike M$ Live Mesh, cannot disable cloud storage

---

### Post by kolmanp on 2010-01-13
I would prefer possibility to buy by half price for half capacity. I think that 25G is enough. I like Ubuntu and feel that can support this project. 120$ per year is more for this service when I need 10-15G.

---

### Post by Mia1990 on 2010-01-13
I would like to see full sync with evolution it sync's my email address book and phone numbers but not any more information like the street address or notes inside the address book

---

### Post by bastubis on 2010-01-19
I think the UbuntuOne idea is fabulous but two things prevent me from using it properly: 

1. One of my boxes (Karmic 9.10) has a static IP - because the network manager has been so buggy since 8.10 I uninstalled it and set up the static IP manually. I started Ubuntuone and it says it's updating which surprised me since I hadn't set it up - and it isn't actually connecting to anything. Wondered where it thought it was going so ran u1sync --authorise in the ubuntu-one-client-tools package and got this error:
ERROR:dbus.proxies:Introspect error on org.freedesktop.NetworkManager:/org/freedesktop/NetworkManager: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files

Looks like ubuntuone can't sync without the network manager - which doesn't work with static IPs. Even if it did work, I don't need the network manager with a static IP anyway so it'd be good if ubuntu one didn't rely on it. Also be good if Ubuntuone threw up an error message instead of looking like it's doing something useful?  

2. Also have an eeepc with a 4 GB fixed drive which is pretty much filled by Netbook Remix 9.10. If I use all the 2 GB I have available, it won't fit on the 4 GB drive but I can't move the folder and symlink to an SD card because they're different devices with different FS. I spose it's not practical but would be good to be able to define what gets downloaded where.

---

### Post by suniyo on 2010-01-20
First of all there are lot of bugs in U1 client and needs immediate attention after that there are any chances of any functionality changes. Client is very poor and with almost no options to set but bandwidth. There are few improvements needed for the client like changing password, information about out of sync files, total free space available, notes and contact access directly from client and most of all need to get rid of those frequent connectivity problems like this bug: [https://bugs.launchpad.net/ubuntuone-client/+bug/455544](https://bugs.launchpad.net/ubuntuone-client/+bug/455544)

---

### Post by matchett808 on 2010-01-22
knowing that the source for the Server side is coming out I would like the option (not that i am greedy) but to have 2 ubuntu one's running one to connect to my server and one to connect to the cannonical server (this is really just so i can store important stuff outside the house and chuck my media files onto a server! lol)

Personally after the initial release (after the beta) I have had little or no problems with u1, tomboy has refused to sync for a couple of days but thats it!

So good work u1 team and keep it up!

---

### Post by the.scarecrow on 2010-01-26
Its early days for me on U-1 but its already a great help switching between Karmic on my HD and Lucid on a USB.

Its easy to transfer bookmarks to firefox by sharing the backup/restore feature in organize bookmarks. The Tomboy notes sharing is a superb feature.

One thing I want to suggest is more information is needed during synchronization progress. It can be quite slow to upload and a small progress bar would be very helpful.

---

### Post by 311005901 on 2010-01-26
I can't say it enough: cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support. Cross OS support.

---

### Post by joshuahoover on 2010-02-01
> **bastubis said:**
> I think the UbuntuOne idea is fabulous but two things prevent me from using it properly: 

1. One of my boxes (Karmic 9.10) has a static IP - because the network manager has been so buggy since 8.10 I uninstalled it and set up the static IP manually. I started Ubuntuone and it says it's updating which surprised me since I hadn't set it up - and it isn't actually connecting to anything. Wondered where it thought it was going so ran u1sync --authorise in the ubuntu-one-client-tools package and got this error:
ERROR:dbus.proxies:Introspect error on org.freedesktop.NetworkManager:/org/freedesktop/NetworkManager: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files

Looks like ubuntuone can't sync without the network manager - which doesn't work with static IPs. Even if it did work, I don't need the network manager with a static IP anyway so it'd be good if ubuntu one didn't rely on it. Also be good if Ubuntuone threw up an error message instead of looking like it's doing something useful?  

We actually have a fix waiting to get into Karmic main. You can try installing it by following this FAQ: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/930](https://answers.edge.launchpad.net/ubuntuone-client/+faq/930)

Thanks!

Joshua

---

### Post by markinmadison on 2010-02-02
I also have a new idea as well. I just bought a new HD TV 22" for my computer. I use this as a monitor. There is no way to configure Ubuntu into a widescreen config. That would also be nice in the new Ubuntu or upgrade.

---

### Post by Marran77 on 2010-02-03
I guess this has been mentioned already, but support for Gnote. It's  faster and lighter than Tomboy. On my system Gnote uses 4.5 mb, and Tomboy about 10, even more sometimes. Maybe it's possible to reduce the memory usage of U1 too? The sync-daemon uses around 23mb and the applet around 13. Dropbox just uses around 27. It's also faster in my opinion. It syncs faster, the server seems faster.

---

### Post by Marran77 on 2010-02-08
Just came to think of another one. The choice to remove multiple files at once in the U1-website. Now one can only remove one file at the time. And then the website reloads, . . . . and reloads . . . . and then you can remove another one . . . . and so on . . . .

---

### Post by zeta on 2010-03-17
Hi,
I would really like to see a better integration/accessibility with mobile phones. To easily access my Tomboy notes on my Nokia E72 would be fantastic, an option to sync contacts or the calendar even better. Even a Ubuntu One webpage optimized for phones (smaller screen, less data) would be a huge step. 

So far, I managed to log in into the website from my phone, but the containing files don't show up, just the folders (after some waiting). Access to the notes worked one time (not great though), but now I only get errors.

---

### Post by GrfyGrumpyBear on 2010-03-22
The most important UbuntuOne improvement is to make it easy and obvious to **not** use. 

There is a sizable percentage of Ubuntu users who cannot or will not use the Cloud but still love the rest of Ubuntu. Please don't forget about us. [-o<

Thank you.

---

### Post by Ellipsis on 2010-03-22
I have had two big ideas for Ubuntu One (probably require a bit of development work and may not work in the real world).

Add a public or "web" sub-folder to automatically upload and display pictures and video online. In my idea I suggest creating a new site for it but it might be possible to seek partnership from Yahoo (for Flickr). 
[http://brainstorm.ubuntu.com/idea/24101/](http://brainstorm.ubuntu.com/idea/24101/)

Integrate games into Ubuntu One with shared highscores, save files and possibly achievements. 
[http://brainstorm.ubuntu.com/idea/24000/](http://brainstorm.ubuntu.com/idea/24000/)

---

### Post by Linuxnall on 2010-05-09
I would quite like for their to be a movie and tv store as well as the Music store so it is more like iTunes.

---

### Post by tricomp on 2010-05-10
> **Marran77 said:**
> Just came to think of another one. The choice to remove multiple files at once in the U1-website. Now one can only remove one file at the time. And then the website reloads, . . . . and reloads . . . . and then you can remove another one . . . . and so on . . . .

+1 - I think this is very important also

> **GrfyGrumpyBear said:**
> The most important UbuntuOne improvement is to make it easy and obvious to **not** use. 

There is a sizable percentage of Ubuntu users who cannot or will not use the Cloud but still love the rest of Ubuntu. Please don't forget about us. [-o<

Thank you.

+1 - I too think this is essential

> **Linuxnall said:**
> I would quite like for their to be a movie and tv store as well as the Music store so it is more like iTunes.

-1 - Please please don't even consider this right now. Take the time and energy to make the music store the best possible first. (Actually, at this point just make it work period.) This is what killed Songbird on Linux.- adding features instead of focusing on making the best possible Music Player. Instead of working out the many music player bugs they went for feature bloat and as a result - not enough resources for everything and bye bye Songbird for Linux. Resources only go so far. Way down the line I agree this would be nice but before then make Rhythmbox and the Music Store the best possible music experience first. Please. Don't mean to be negative, but losing Songbird on Linux was very annoying and this would be a huge undertaking for Ubuntu and they already seem to have their hands full with music store/U1 problems.

---

### Post by MHmedia on 2010-08-10
I'm getting to grips with U1 and have now started using it usefully, so kudos to the developers for getting it working nicely.

What I'd really like to see though is the option to add a short message to people I share a folder with - maybe up to 255 characters, just to add that personal touch. It would look a lot more professional!

---

### Post by b1ackcr0w on 2010-08-13
The ability to choose to choose either to backup a file or directory to U1 without syncing it down to other machines would be cool.

---

