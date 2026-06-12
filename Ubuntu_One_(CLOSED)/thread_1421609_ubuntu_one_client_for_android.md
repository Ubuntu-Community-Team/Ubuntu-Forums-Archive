---
title: "ubuntu one client for android?"
date: 2010-03-04
forum: Ubuntu One (CLOSED)
---

### Post by ukripper on 2010-03-04
Are there any plans for ubuntu one client on android platform? Would love to sync my zoneminder events with my android phone on the go. Currently using dropbox command line daemon on my ubuntu server.

---

### Post by joshuahoover on 2010-03-04
> **ukripper said:**
> Are there any plans for ubuntu one client on android platform? Would love to sync my zoneminder events with my android phone on the go. Currently using dropbox command line daemon on my ubuntu server.

We don't have plans to create a client for Android currently but we'd love to help those interested in developing one.

Thank you,

Joshua

---

### Post by ukripper on 2010-03-05
> **joshuahoover said:**
> We don't have plans to create a client for Android currently but we'd love to help those interested in developing one.

Thank you,

Joshua

Thanks Joshua for coming back on this one.

Where can i find up to date documentation and source code for ubuntu one(if licensed under GPL)?

Thanks again.

Edit:

i was trying to find source code for ubuntuone on launchpad. it seems ubuntuone is not open sourced - see this bug report [https://bugs.launchpad.net/ubuntuone-servers/+bug/375272](https://bugs.launchpad.net/ubuntuone-servers/+bug/375272)

Is it true that ubuntuone is not open sourced?

---

### Post by cb951303 on 2010-03-05
true
the server part is proprietary and the worst part is they don't even plan to release the source in the future.

that's why I went for dropbox. it's *MUCH* more capable and as UbuntuOne, the client interface is open source (not the daemon).

---

### Post by ukripper on 2010-03-05
> **cb951303 said:**
> true
the server part is proprietary and the worst part is they don't even plan to release the source in the future.

that's why I went for dropbox. it's *MUCH* more capable and as UbuntuOne, the client interface is open source (not the daemon).

I am gutted to know that!

i guess in this situation i'd have to resort to dropbox which is cross platform and also running as a cli daemon on my ubuntu 9.10 server without any problem. iFolder requires mono which i won't even think about. 

However, for my future server needs i found a great solution using lsyncd and rsync in conjunction. Very interesting blog here - [http://fak3r.com/2009/09/14/howto-build-your-own-open-source-dropbox-clone/](http://fak3r.com/2009/09/14/howto-build-your-own-open-source-dropbox-clone/)

---

### Post by cb951303 on 2010-03-05
I tried rsync before but it doesn't allow renaming files. Everytime you rename a file it reuploads it and deletes the older one. I guess it's not much of a problem for home users, though not resource friendly for the bandwidth :)

/rant: Frankly, I don't see why would anyone prefer UbuntuOne over DropBox. I'm not saying this to disrespect the UbuntuOne team, it's just that they don't have any business advantage, or "underlying magic" that will make them appealing to the customer.
UbuntuOne team, take this as a constructive criticisim: Find something different and valuable to the customer if you really want to challenge DropBox.

---

### Post by ukripper on 2010-03-05
> **cb951303 said:**
> I tried rsync before but it doesn't allow renaming files. Everytime you rename a file it reuploads it and deletes the older one. I guess it's not much of a problem for home users, though not resource friendly for the bandwidth :)



Apparently dropbox does utilise rsync libraries. When used with lsyncd, rsync would give dropbox like functionality triggering when needed. using rsync alone without lsyncd is major overhead i agree.

> **cb951303 said:**
> 
/rant: Frankly, I don't see why would anyone prefer UbuntuOne over DropBox. I'm not saying this to disrespect the UbuntuOne team, it's just that they don't have any business advantage, or "underlying magic" that will make them appealing to the customer.
UbuntuOne team, take this as a constructive criticisim: Find something different and valuable to the customer if you really want to challenge DropBox.

+1 on that. ubuntuone, android client can give you advantage over dropbox for now but i read somewhere dropbox is already on developing client for android.

IMO, only advantage Ubuntuone can have is when they make it fully open sourced.

---

### Post by cb951303 on 2010-03-05
I agree, open sourcing the server side should be the first step.
Other services that would make UbuntuOne valuable to the customer are (off the top of my head):

*Encrypted private storage
*Plugin interface / API for sync so that people can integrate it to their software. UbuntuOne team shouldn't be bothered with adding sync support for the software X. IMHO it's the software owner's job.
*Cross-platform support (At least Win, Mac and Android)
*Public folder and web interface (is it implemented yet?)

---

### Post by ukripper on 2010-03-05
> **cb951303 said:**
> I agree, open sourcing the server side should be the first step.
Other services that would make UbuntuOne valuable to the customer are (off the top of my head):

*Encrypted private storage
*Plugin interface / API for sync so that people can integrate it to their software. UbuntuOne team shouldn't be bothered with adding sync support for the software X. IMHO it's the software owner's job.
*Cross-platform support (At least Win, Mac and Android)
*Public folder and web interface (is it implemented yet?)

good points.

Funnily enough dropbox seems to be far ahead of ubuntuone project. Check the addons available - [http://wiki.dropbox.com/DropboxAddons](http://wiki.dropbox.com/DropboxAddons). i will be including the PHP dropbox uploader module at my work soon.

ubuntuone has to come with something unique and fast to gain popularity in the community itself.

---

### Post by DedMoroz on 2010-03-05
> **cb951303 said:**
> true
the server part is proprietary and the worst part is they don't even plan to release the source in the future.

that's why I went for dropbox. it's *MUCH* more capable and as UbuntuOne, the client interface is open source (not the daemon).

Yet I cannot even change the Dropbox logo in my system tray. So much for open source.

---

### Post by cb951303 on 2010-03-05
> **DedMoroz said:**
> Yet I cannot even change the Dropbox logo in my system tray. So much for open source.

no one claimed that dropbox is open source. only the client ui part is open source. which is also exactly the same amount of openness that UbuntuOne has. that's the part that I was emphasizing.

in case you missed it, I only stated that UbuntuOne is far behind competition and it lacks strategy to succeed in the future.
if ever UbuntuOne becomes what I need, I'll switch to it in a heartbeat.

please don't turn this into a flame war (which is clearly what you're after)

and BTW, I'm pretty sure the open source part will let you change the system tray icon: [https://www.dropbox.com/downloading?os=lnx](https://www.dropbox.com/downloading?os=lnx)
did you check it?

---

### Post by sanjaya on 2010-04-01
The following is a great alternative to Dropbox, and it is GPL

I have working scripts for Ubuntu 9.04 Simias server and Ubuntu 9.10 iFolder client working in an x86 environment. These are robust, Novell Suse developed that have recently been GPLv2ed and are needing developers from the Ubuntu community. I have been in touch with Ravi Kumar, one of the source code maintainers, and they seem pretty helpful.

Join this group, check out these scripts, maybe they can be the basis of something for Android. I would love to see these running in an ARM environment at least the client. Post any experiences to the group.

[http://groups.google.com/group/ifolder-ubuntu-debian-dev](http://groups.google.com/group/ifolder-ubuntu-debian-dev)

Let me know what you think. Email me if you need to:
sanjaya dot yogi at gmail dot com

---

### Post by cb951303 on 2010-04-02
I like iFolder but is there any service providers that gives at least 2GB space for free?

---

### Post by vibra on 2010-05-09
I use dropbox and recently i tried ubuntuone. Both look great services but I was sad to know that ubuntuone doesn't provide a client to the android platform. 

When I tried to browse through my internet mobile  on ubuntuone website and upload a file, it says "upload disabled"... The DropBox regular website says the same and its mobile website doesn't provide any option to try it. So it's explicit that upload files through regular websites/mobile websites is not possible (on mobile phones of course :P).

Ubuntu website:
[http://dl.dropbox.com/0/view/u5drxlzc5gjs655/snap20100509_181405.png]("http://dl.dropbox.com/0/view/u5drxlzc5gjs655/snap20100509_181405.png")

Dropbox website:
[http://dl.dropbox.com/0/view/4ng2ihz4nysujpf/snap20100509_183114.png]("http://dl.dropbox.com/0/view/4ng2ihz4nysujpf/snap20100509_183114.png")

I will be looking forward for a android client to ubuntuone :popcorn:

---

### Post by mkarnicki on 2010-05-09
I was accepted to Google Summer of Code 2010 with project: Android client for Ubuntu One. So you'll probably get it in ~3,5 months at most (unless you'll want to beta test ;) ). See ya then! :popcorn:

---

### Post by vibra on 2010-05-09
mkarnicki, great to know that. :) 

A quick search and I have found some links to it:

[https://wiki.ubuntu.com/specs/UbuntuOneForAndroid](https://wiki.ubuntu.com/specs/UbuntuOneForAndroid)

[https://wiki.ubuntu.com/GSoC/2010/MichalKarnicki/](https://wiki.ubuntu.com/GSoC/2010/MichalKarnicki/)

:P You are so lucky to work on this. Good luck!

---

### Post by mkarnicki on 2010-05-09
> **vibra said:**
> :P You are so lucky to work on this. Good luck!

Heheh, indeed I am :KS

---

### Post by duanedesign on 2010-05-09
> **cb951303 said:**
> no one claimed that dropbox is open source. only the client ui part is open source. which is also exactly the same amount of openness that UbuntuOne has. that's the part that I was emphasizing.

in case you missed it, I only stated that UbuntuOne is far behind competition and it lacks strategy to succeed in the future.
if ever UbuntuOne becomes what I need, I'll switch to it in a heartbeat.


The source for bindwood, ubuntuone-client, ubuntuone-storage-protocol, couchdb.one.ubuntu.com, desktopcouch, evolution-couchdb, funambol, tomboy web sync, and more are open source.They also recently split out the AWS S3 emulator that we use for testing and contribute it as a branch to the txAWS project.

I think Ubuntu One is a much more ambitious project than services like Dropbox. Ubuntu One's integration with Ubuntu Applications is something other services do not provide. With projects like [One Conf]("https://wiki.ubuntu.com/OneConf") and ZoHo integration on the horizon I believe Ubuntu One does have a long term strategy.

Considering what Ubuntu has given me over the years, for free, I am glad to have the opportunity to get a useful service and at the same time provide support for Ubuntu and employ open source developers.

---

### Post by ukripper on 2010-05-10
> **mkarnicki said:**
> I was accepted to Google Summer of Code 2010 with project: Android client for Ubuntu One. So you'll probably get it in ~3,5 months at most (unless you'll want to beta test ;) ). See ya then! :popcorn:

Congratulation, i look forward to beta test, please post the link.

Thanks.

---

### Post by mkarnicki on 2010-05-10
> **ukripper said:**
> Congratulation, i look forward to beta test, please post the link.

Thanks.

Thanks :) Will do!

---

### Post by Bavo on 2010-05-21
Looking forward to this!

I just added your blog to my Google reader, i will be following this project, and i'd be happy to beta test too.

---

### Post by mkarnicki on 2010-05-21
Cool, thanks Bavo ^ ^ !

---

### Post by mkarnicki on 2010-06-01
I have set up [https://launchpad.net/androidu1](https://launchpad.net/androidu1) recently, have a look :) I just managed to implement OAuth (authorization), more coming soon.

EDIT: Brand new team (+mailing list): [https://launchpad.net/~androidu1-users](https://launchpad.net/~androidu1-users)

---

### Post by fatality_uk on 2010-06-07
As I will hopefully soon be ditching my HTC HD2 for an HTC Evo4 I would be happy to throw my hat in the ring to help this project. C/PHP/JavaScript/testing just let me know!

---

### Post by ukripper on 2010-06-07
> **fatality_uk said:**
> As I will hopefully soon be ditching my HTC HD2 for an HTC Evo4 I would be happy to throw my hat in the ring to help this project. C/PHP/JavaScript/testing just let me know!

I thought EVO4 is just launching in US?

---

### Post by ukripper on 2010-06-07
> **mkarnicki said:**
> I have set up [https://launchpad.net/androidu1](https://launchpad.net/androidu1) recently, have a look :) I just managed to implement OAuth (authorization), more coming soon.

EDIT: Brand new team (+mailing list): [https://launchpad.net/~androidu1-users](https://launchpad.net/~androidu1-users)

Great work mate! thanks

---

### Post by mkarnicki on 2010-06-07
> **fatality_uk said:**
> As I will hopefully soon be ditching my HTC HD2 for an HTC Evo4 I would be happy to throw my hat in the ring to help this project. C/PHP/JavaScript/testing just let me know!

Thank you! I'll remember :)

> **ukripper said:**
> Great work mate! thanks

Thanks, doing my best!

---

### Post by mkarnicki on 2010-06-11
You can expect an update on the progress in the next few days. In the mean time, you can have a look here:
[https://wiki.ubuntu.com/mkarnicki/gsoc/AndroidU1/reports](https://wiki.ubuntu.com/mkarnicki/gsoc/AndroidU1/reports)
(updated weekly)

---

### Post by hartl_vienna on 2010-06-14
mkarnicki: You are my hero! Thanks for the great work!  :p

---

### Post by ukripper on 2010-06-14
> **mkarnicki said:**
> You can expect an update on the progress in the next few days. In the mean time, you can have a look here:
[https://wiki.ubuntu.com/mkarnicki/gsoc/AndroidU1/reports](https://wiki.ubuntu.com/mkarnicki/gsoc/AndroidU1/reports)
(updated weekly)

Thanks for the progress report. i am following it very closely.

Cheers.

---

### Post by mkarnicki on 2010-06-14
> **ukripper said:**
> Thanks for the progress report. i am following it very closely.

Cheers.
Cool! I'm happy GSoC admins and my mentor from Ubuntu One team aren't the only ones reading those reports :KS

I wanted already to deliver cloud browsing, but had a protocol issue - about to talk that over with the maintainer!


@hartl_vienna Thank you ^ ^ ! Glad you like my work, more coming soon!

---

### Post by mkarnicki on 2010-06-19
Update for you guys. The project has stalled for a week due to bugs on Android platform (SSLContext using SSL is not implemented, using TLS throws 'Bad family address'). We've been working hard together with verterok on downgrading the protocol client from NIO to OIO (Java Old I/O). Probably still a few days will be spent on that, then finally I'll go back on working on the application itself.

---

### Post by mainerror on 2010-06-19
mkarnicki if you require any help with Android just drop me a line. ;)

---

### Post by mkarnicki on 2010-06-19
Hey there mainerror :)

You could tell me a workaround for that bug
[http://code.google.com/p/android/issues/detail?id=4914](http://code.google.com/p/android/issues/detail?id=4914)
on Android versions less than 2.2 and then how to overcome second Android bug
[http://stackoverflow.com/questions/2879455/android-2-2-and-bad-address-family-on-socket-connect](http://stackoverflow.com/questions/2879455/android-2-2-and-bad-address-family-on-socket-connect) . Probably both are related to apache harmony implementation.

But now seriously ;) You can see that we have hit some serious Android issues. So we're adjusting the way we handle U1 protocol.

But thanks, I may use your help one day or another :)

---

### Post by mkarnicki on 2010-06-20
A bit more detailed update for you guys, [http://goo.gl/lQGW](http://goo.gl/lQGW)
As you will see from the report, we had some major platform bug related problems. But I hope the project will finally move on pretty soon.

---

### Post by ukripper on 2010-06-21
> **mkarnicki said:**
> A bit more detailed update for you guys, [http://goo.gl/lQGW](http://goo.gl/lQGW)
As you will see from the report, we had some major platform bug related problems. But I hope the project will finally move on pretty soon.

Thanks for the update on issues. Hope gets resolved soon.

---

### Post by mainerror on 2010-06-21
Nice mkarnicki looking forward for more updates.

---

### Post by mkarnicki on 2010-06-26
Here, guys, poke around ;)

And yes, it has bugs - it't bleeding edge development version :shock: This is just-for-fun non-official release.

Most visible issues:
:!: Android 2.1 (in some cases, the app may fail to connect and crash)
:!: closing the keyboard crashes the app(seems I didn't handle onConfigurationChange or something ;) )

Sorry, you can't up/download files, yet. I know you could have expected more, but please note the project was stalled for ~2 weeks (see reports: [http://goo.gl/VLz6](http://goo.gl/VLz6)), we had to work on the protocol as a workaround for Android bugs.

Have (a little) fun trying it out ;) (including laughing when you hit a bug!). Let me know how it worked + your Android version.

OAuth tokens are stored in the application preferences and occasionally can be exposed in the application logs (1. which I don't have access to anyway 2. I will fix this), so you may want to remove the device from one.ubuntu.com when you've finished.

Download androidu1.apk with QR code: [http://goo.gl/MfwG](http://goo.gl/MfwG)

---

### Post by duanedesign on 2010-06-27
Good work!

Glad to see the progress you have made.

---

### Post by mkarnicki on 2010-06-28
Hi guys, concluding last week I fixed few bugs. And for time being, we'll be running in portrait mode only, sorry. That's a temporary workaround we'll work on later.

Weekly report for those interested: [http://goo.gl/42LU](http://goo.gl/42LU)

QR code download (bleeding edge development version, still without up/download feature): [http://goo.gl/MfwG](http://goo.gl/MfwG)

---

### Post by ukripper on 2010-06-28
Great work mkarnicki:guitar: Will test it..

---

### Post by mkarnicki on 2010-07-09
I'm leaving a link to mailing list archive, if anyone's interested.

the mailing list: 
[https://launchpad.net/~androidu1-users](https://launchpad.net/~androidu1-users)

the mailing list archive:
[https://lists.launchpad.net/androidu1-users/](https://lists.launchpad.net/androidu1-users/)

Just posted the first mail ;) And.. back to work!

---

### Post by Excedio on 2010-07-15
Is the QR code to download gone or am I missing something? Id like to test this. :-)

---

### Post by mkarnicki on 2010-07-15
It's just few posts back, but today or in 1-2 days time there will be a milestone update.

Note, this is strictly development version, half-way implemented and likely to break when you least expect it ;)

---

### Post by Excedio on 2010-07-15
> **mkarnicki said:**
> Hi guys, concluding last week I fixed few bugs. And for time being, we'll be running in portrait mode only, sorry. That's a temporary workaround we'll work on later.
 
Weekly report for those interested: [http://goo.gl/42LU](http://goo.gl/42LU)
 
QR code download (bleeding edge development version, still without up/download feature): [http://goo.gl/MfwG](http://goo.gl/MfwG)
 
Wow....I clicked on EVERY link except this one. :-D
 
THANKS!
 
FYI: HTC Incredible 2.1 (Non-Rooted)

---

### Post by mkarnicki on 2010-07-15
Glad you found it Excedio :) Like I said, I'm working hard on it right now, so.. I'll get back to work ;)

---

### Post by Excedio on 2010-07-17
For those who are interested.. AndroidU1 has been updated and has new functionality.
 
QR Code for downloading..[[COLOR=#444444]http://goo.gl/MfwG[/COLOR]]("http://goo.gl/MfwG")

---

### Post by mkarnicki on 2010-07-17
As always, remember it's strictly development version, pre-alpha, far from beta. For example, you can download files to your phone, but not yet open them. First, I have to consult U1 developer about particular server response related to AndroidU1 sync, then I'll implement opening of files.

---

### Post by Excedio on 2010-07-17
I realize that this is still under pre-Alpha but, if I have an idea for a feature, where should I request them? Here? Launchpad? If launchpad, where in launchpad? Blurprints, or as a question?
 
EDIT: Got this answer for this on Launchpad. For anyone who has Ideas...[Click Here]("https://blueprints.launchpad.net/androidu1/+addspec").

---

### Post by mkarnicki on 2010-07-17
Excedio, you're a great beta tester :) Please file blueprints separately for each great idea you have:

[https://blueprints.launchpad.net/androidu1](https://blueprints.launchpad.net/androidu1)

I can see you already filed a one for the widget. I think your idea is pretty cool. We'll think about it in depth later :)

---

### Post by Excedio on 2010-07-17
I do what I can. :-D I don't know how to write code, so this is how I can contribute. :-)

---

### Post by mkarnicki on 2010-07-29
Hi guys,
You're welcome to have a look at an update on the blog:
[http://goo.gl/n2Dv](http://goo.gl/n2Dv)
Plus, let me announce the project official page ;)
[http://wiki.ubuntu.com/AndroidU1](http://wiki.ubuntu.com/AndroidU1) - you can check out the changelog

Cheers! :popcorn:

---

### Post by ehabh on 2010-07-29
On my nokia n900 I can sync tomboy to the n900 version called conboy, that is one of the few reasons I am still sticking with the n900.

---

### Post by ukripper on 2010-07-30
> **ehabh said:**
> On my nokia n900 I can sync tomboy to the n900 version called conboy, that is one of the few reasons I am still sticking with the n900.

C'mon man N900 vs Android is like apple and oranges. However, N900 is a good phone but what I want is android! Downloading torrents right now on it.

---

### Post by ukripper on 2010-07-30
> **mkarnicki said:**
> Hi guys,
You're welcome to have a look at an update on the blog:
[http://goo.gl/n2Dv](http://goo.gl/n2Dv)
Plus, let me announce the project official page ;)
[http://wiki.ubuntu.com/AndroidU1](http://wiki.ubuntu.com/AndroidU1) - you can check out the changelog

Cheers! :popcorn:

Sure will check it out. thanks again

---

### Post by jensk on 2010-10-10
This i great - just what I've been looking for. Together with apps like KeepassX-keepassDroid and others i can sync important information between my laptop and my HTC Desire.

Looking forward to have my Keepass files on my UbuntuOne account and using it on both devices.

Please let me know when I can contribute with translation.

---

### Post by edcompsci on 2011-03-14
Using the SKyfire browser on my Android Garminfone I have been able to login to ubuntu one and download my files.

---

### Post by mailman1175 on 2011-04-10
> **jensk said:**
> Together with apps like KeepassX-keepassDroid and others i can sync important information between my laptop and my HTC Desire.

THIS.

Has there been any progress made on this?

---

### Post by mkarnicki on 2011-04-10
Hi guys,

Yes indeed. I've been working on the official Android client since beginning of this year, and it is already functional. We've recently decided to change one core aspect of the app though, so you'll have to wait few more weeks for it to be released. I'm only giving vague info, as I'm not sure how much I can disclose ;d

Have a great day,
Micha&#322;

---

### Post by danpav2881 on 2011-11-08
Hi to all guys, I took a lot of knowledge in this forum but I'm just registered.

I'm working with keepass on more machines, OS are Ubuntu on PCs and Android on mobile. I'm using Ubuntu One to synchronize the Keepass's database. Do you think it will be possible in the future have an automatic file's sync on the Android version? Now by now the only automatic sync is about pictures if I understood right, isn't it? Adding the automatic sync for all of the file could be useful for a lot of people I think (maybe because I'm really lazy :D )

Thank you so much guys

Bye bye

---

### Post by mkarnicki on 2011-11-08
> **danpav2881 said:**
> Do you think it will be possible in the future have an automatic file's sync on the Android version?

Yes, most probably matter of few months though.

> Now by now the only automatic sync is about pictures if I understood right, isn't it?

We like to call it auto-upload (or backup) to avoid confusion around the sync/synchronization terms :) Yes, pictures can automatically upload to Ubuntu One.

Hope that answers your question :) Cheers!

---

### Post by danpav2881 on 2011-12-14
Yes you answered. :)

Thank you very much.

I hope that soon this software will be developed enough for my needs.

Ciao a tuttiiiii!!!!!!!!!!! :))))

---

