---
title: "Should Ubuntu implement delta updates?"
date: 2007-04-13
forum: The Cafe
---

### Post by soliac on 2007-04-13
Delta updates - also called binary "patches", contain just the *difference* between an old package and a new package. Should Ubuntu implement this feature for** it's** updates?
As a dialup user, I think this feature is highly desirable, what with my 3 KB/s modem. Broadband users would not have to worry about exceeding their data caps, as most delta updates would be only a few Kilobytes. The only downside is that applying these updates uses processing power, and I'm not sure if current solutions allow updates to be applied to *installed files* rather than the original .deb package.
What do you think?

---

### Post by kragen on 2007-04-13
can you add an extra box to the poll:

"have it as an option for users with slower connections"

I'm just thinking that although smaller downloads sounds great, it's far more complicated - if you download the whole package from scratch each time you update, then its far less likely to go wrong.

---

### Post by banjobacon on 2007-04-13
I remember reading that Suse does this. Is that true or not?

---

### Post by macogw on 2007-04-13
Even if it had to apply it to the original .deb, that's kept in /var/cache/apt/archives so it could do it anyway.

---

### Post by Starchild on 2007-04-13
Yes, absolutely. This is one of my main pet peeves. I've been wanting this feature for a long time. The current mindset of most free software projects seems rather elitist to me, in that they seem not to care much for the users with slow/flaky internet connection. That comes off as very strange and ironic to me given that free software is supposed to be based on *respect *for the users and their freedom. I've always regarded a feature like this to be far FAR more essential that some stupid bling!

---

### Post by hanzomon4 on 2007-04-13
Any draw backs?

---

### Post by Mathiasdm on 2007-04-13
This would be a wonderful feature.
When it's possible to submit ideas for Gutsy, be sure to send this in!

---

### Post by maniacmusician on 2007-04-13
I voted yes as well. I  can't really think of any drawbacks. Faster downloads, less stuff to install. I wish there was a way to cut down on the package lists that are downloaded when you do an "apt-get update"...you end up downloading a few MBs of that sometimes, and that must really suck for dial-up users; I can hardly wait the 10 extra seconds it takes me, they must have to wait 5 minutes while it just updates the list of packages....

---

### Post by salsafyren on 2007-04-13
> **maniacmusician said:**
> I voted yes as well. I  can't really think of any drawbacks. Faster downloads, less stuff to install. I wish there was a way to cut down on the package lists that are downloaded when you do an "apt-get update"...you end up downloading a few MBs of that sometimes, and that must really suck for dial-up users; I can hardly wait the 10 extra seconds it takes me, they must have to wait 5 minutes while it just updates the list of packages....

Debian Etch does this already.

I wonder why Ubuntu doesn't do this.

It is funny, Mandriva had has delta updates for quite a while, but they don't get as much coverage in the news as Ubuntu.

Sometimes, I think Ubuntu deserves more criticism than it gets.

---

### Post by antenna on 2007-04-13
> **maniacmusician said:**
> I voted yes as well. I  can't really think of any drawbacks. Faster downloads, less stuff to install. I wish there was a way to cut down on the package lists that are downloaded when you do an "apt-get update"...you end up downloading a few MBs of that sometimes, and that must really suck for dial-up users; I can hardly wait the 10 extra seconds it takes me, they must have to wait 5 minutes while it just updates the list of packages....

Interestingly, Debian implemented diff updates for the package lists quite some time ago, I wonder why Ubuntu is not using this also.  Or perhaps it does and it's server dependant or something.  Or maybe in Feisty.

---

### Post by hardyn on 2007-04-13
it would be nice, but i have a fast connection so makes little difference to me... i would be concerned about file corruption though, if they get it wrong... at least if a file goes wrong in coping or installing its pretty easy to detect... if a file is patched improperly i could see headaches arrising.

it would not be worth it, if we have start using the windows catch phrase... "try reinstalling" i absolutely hate that!

cheers.

---

### Post by FoolsGold on 2007-04-13
> **hardyn said:**
> it would be nice, but i have a fast connection so makes little difference to me... i would be concerned about file corruption though, if they get it wrong... at least if a file goes wrong in coping or installing its pretty easy to detect... if a file is patched improperly i could see headaches arrising.
They're just patching the existing packages to match the latest package version. A hash will have already been performed on the latest build of the package, and it will be sent along with the delta. If the patching was successful, the hash values will be the same - if they aren't, the updater can force a download of the latest package. At least that's how I'd do it.

I voted yes, it's a good idea. Living in Australia, we have typical broadband speeds that the rest of the world would point and laugh at. To get anything close to international standards costs a heck of a lot, so conserving bandwidth via delta updates would be useful, as well as quicker.

---

### Post by mediax on 2007-04-13
I tend to agree with the suggestion that it be included as an option for users slower connections and/or download limits.  Experience in past lifetimes makes me wary of incremental updates, but I fully understand they could be a godsend to others.

---

### Post by Hobbsee on 2007-04-13
> **FoolsGold said:**
> I voted yes, it's a good idea. Living in Australia, we have typical broadband speeds that the rest of the world would point and laugh at. To get anything close to international standards costs a heck of a lot, so conserving bandwidth via delta updates would be useful, as well as quicker.

Havent heard what etch is doing w.r.t that.  Will have to look into it, maybe raise it at the summit.  Someone else likely will.

As for australia, the au.archive... mirror is horrid - try 
deb [http://mirror.pacific.net.au/ubuntu](http://mirror.pacific.net.au/ubuntu) feisty main restricted universe multiverse

(modify to taste).  It tends to stay up most of the time, with occasional md5sum mismatches.

---

### Post by koenn on 2007-04-13
I understood that Debian uses diff's to keep the Packages.gz up to date : the list of available packages/versions/... in a repo that apt uses to check if anything needs updating. The packages themselves would still have to be downloaded completely. That means it works for apt-get update, not for apt-get upgrade.

I also believe debian has been looking at rsync for package downloads - rsync does remote synchronisation of files by only transmitting the delta - but afaik it's experimental. 

Ubuntu is (or has been ?) looking at something similar : [https://lists.ubuntu.com/archives/ubuntu-devel/2006-May/018232.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-May/018232.html)

---

### Post by Hobbsee on 2007-04-13
> **koenn said:**
> I understood that Debian uses diff's to keep the Packages.gz up to date : the list of available packages/versions/... in a repo that apt uses to check if anything needs updating. The packages themselves would still have to be downloaded completely. That means it works for apt-get update, not for apt-get upgrade.

Would have thought ubuntu does this too.  It seems to.

Part of the problem is that the packages files are text - so can be diff'd.  Trying to diff a binary file isnt so easy.

---

### Post by koenn on 2007-04-13
but packages could be rsync'd. Although that would require some rethinking - eg the naming convention for packages includes versioning  while rsyncing a package to implement changes would keep the old filename.

Not as easy as it seems, i gather.

---

### Post by Mathiasdm on 2007-04-13
Well, I really hope they do implement it. I've been using Feisty for a little while now, and noticed today I can only download 1 GB for the next week, or I'll be over my limit :?

Of course, this is not solely due to Feisty, but if Ubuntu updates used diff, I might still have a bit more left to download ;)

---

### Post by Adamant1988 on 2007-04-13
> **Starchild said:**
> Yes, absolutely. This is one of my main pet peeves. I've been wanting this feature for a long time. The current mindset of most free software projects seems rather elitist to me, in that they seem not to care much for the users with slow/flaky internet connection. That comes off as very strange and ironic to me given that free software is supposed to be based on ***respect *for the users and their freedom. I've always regarded a feature like this to be far FAR more essential that some stupid bling!**

I'm sorry, let me stop you there. 

This "free software thing" AFAIK has nothing to do with respecting users bandwidth.  As far as I can tell this "free software thing" is based on the idea that users have certain rights and freedoms and that those are inalienable.  

Now, with that said, have you paid a dime to the Ubuntu developers? If not you are not in any position to judging the developers.  If Delta-updates are so important to you use SuSE, Foresight, etc. since those distributions offer that kind of updating (even RAV TUX's own Oz distro supports this if I recall correctly). 

If you would like to see this in Ubuntu, write a spec for it on the wiki/launchpad and if it's worth the developers time they'll do it.

---

### Post by macogw on 2007-04-13
> **Adamant1988 said:**
> I'm sorry, let me stop you there. 

This "free software thing" AFAIK has nothing to do with respecting users bandwidth.  As far as I can tell this "free software thing" is based on the idea that users have certain rights and freedoms and that those are inalienable.  

Now, with that said, have you paid a dime to the Ubuntu developers? If not you are not in any position to judging the developers.  If Delta-updates are so important to you use SuSE, Foresight, etc. since those distributions offer that kind of updating (even RAV TUX's own Oz distro supports this if I recall correctly). 

If you would like to see this in Ubuntu, write a spec for it on the wiki/launchpad and if it's worth the developers time they'll do it.

Oz probably does as it's Foresight-based.  Or is eighteen36 Foresight-based?  One of them is Foresight and one is rPath

---

### Post by Adamant1988 on 2007-04-13
> **macogw said:**
> Oz probably does as it's Foresight-based.  Or is eighteen36 Foresight-based?  One of them is Foresight and one is rPath

It's actually based more off of rPath than it is Foresight if I remember correctly.

---

### Post by happy-and-lost on 2007-04-13
Yes. There's nothing more annoying than downloading a 200MB OOo update when the only new feature is dual monitor support for Impress... I only have one monitor!

---

### Post by banjobacon on 2007-04-13
> **maniacmusician said:**
>  I wish there was a way to cut down on the package lists that are downloaded when you do an "apt-get update"...you end up downloading a few MBs of that sometimes, and that must really suck for dial-up users;

You can comment out the deb-src links in your apt sources list, or just go to System > Admin > Software Sources, and uncheck the box for 'Source code'.

---

### Post by 23meg on 2007-04-13
> **Starchild said:**
>  The current mindset of most free software projects seems rather elitist to me, in that they seem not to care much for the users with slow/flaky internet connection.

So you're pretty much sure that the reason this hasn't been implemented so far is that Ubuntu / Debian / the APT developers / whoever, are elitists, and not that there are technical obstacles or peculiarities that prevent it from being implemented, or not that nobody came up with a good implementation plan so far? I'd like to know how you can be so sure.

> **Starchild said:**
>  That comes off as very strange and ironic to me given that free software is supposed to be based on *respect *for the users and their freedom. I've always regarded a feature like this to be far FAR more essential that some stupid bling!

I'm afraid I'll have to come up with a derivative of [Godwin's Law]("http://en.wikipedia.org/wiki/Godwins_Law") which states that, as a feature wish or implementation discussion in the Ubuntu forums progresses, the likelihood of someone blaming "the developers" for focusing on "useless bling such as Compiz and Beryl" instead of "essential features" approaches one.

People who work on "some stupid bling" can't work on delta updates. If for some reason they were to, they'd make such a mess that you'd go screaming "Bring back the old update method! I just updated and everything is broken!". If for some reason they suddenly stopped working on "stupid bling", everything else (that they aren't working on) wouldn't suddenly start getting developed much faster. "The developers" isn't a homogeneous entity that's providing everything you're using; separate groups of developers are working on separate things, and distro developers put their work together.

Should Ubuntu implement delta updates? I don't know. I don't know a superficial bit about the internals of APT, I have no idea what possible obstacles and drawbacks may be, I'm not informed on whether it conflicts with anything already on Ubuntu's roadmap, so I'm not in a position to comment about it.

---

### Post by soliac on 2007-04-13
Is it possible to edit a poll to add another option? I couldn't figure out how to - sorry to people who wanted to vote "Yes, as an option for people with slow connections".

There are technical difficulties in implementing delta updates. The major one is that generating "deltas" is CPU intensive, and would kill a server. So, if server-side delta generation is out, how many uploaded delta's should a server hold? Should there be incremental deltas, or accumulative deltas? It seems to me that the "rsync" method looks really good from a server point of view. See proposed specification [rsync/zsync based synchronization tool for deb packages]("https://blueprints.launchpad.net/ubuntu/+spec/succinct"). Launchpad says that this spec supersedes [SmallerUpdates]("https://wiki.ubuntu.com/SmallerUpdates"). There is a wiki page on [APTPackageDeltas]("https://wiki.ubuntu.com/APTPackageDeltas") as well. There is also the [debdelta]("http://tonelli.sns.it/pub/mennucc1/debdelta/") tool, an earlier version of which is already in the edgy repos.

I don't blame the Ubuntu developers for not working on this feature, as it is experimental and some would say controversial. But it *is* necessary for the many dialup users, if they want to stay current with updates. I think this is a good goal for the next Ubuntu release, Gutsy Gibbon, or possibly the one after that. I would prefer it to happen sooner rather than later. There has already been lots of work put into several possibilities, so why can't the Ubuntu developers have a discussion on this and find a way forward?

---

### Post by rai4shu2 on 2007-04-13
Deltas should definitely be accumulative. That way, you don't have to download 10 different patches if you happen to reinstall from an old disc. That wouldn't really save much bandwidth, which is the whole point.

The only *real* downside is that the deltas would use a bit more server space.

---

### Post by Adamant1988 on 2007-04-13
It would be nice if we could actually get this feature, it would be nice to have shorter download times associated with packages, but I would need to see more information about the potential pitfalls associated with this method over the current one.

---

### Post by Nils Olav on 2007-04-13
> **Adamant1988 said:**
> It would be nice if we could actually get this feature, it would be nice to have shorter download times associated with packages, but I would need to see more information about the potential pitfalls associated with this method over the current one.

The only difference is that it is harder to maintain and so it may not work if a developer is careless. So it's not big deal for a big project like ubuntu.

---

### Post by sonny on 2007-04-13
> **soliac said:**
> But it *is* necessary for the many dialup users, if they want to stay current with updates. 
I don't think it IS necessary, I think you should digg more about delta updates, you haven't present any evidence of its liability. Haven't you thought that perhaps the current system is more "technically" correct than delta systems?. As I recall MS has delta updates and patches; I don't think that MS's way is the best way of doing it, but they surely have a lot of problems by patching and delta updating parts of the OS. And that is a "feature" a wouldn't want in Linux, eventhough it costs the project all dialup users to swhitch back to WinXP. I don't think GNU/Linux has defined itself as a project that does things like some group of people think, but as a project that does what's more "technically" correct to do.

---

### Post by rai4shu2 on 2007-04-13
Nonsense. Security is a total nonissue with respect to deltas. It's not even slightly risky.

---

### Post by soliac on 2007-04-13
> **sonny said:**
> I don't think it IS necessary, I think you should digg more about delta updates, you haven't present any evidence of its liability. Haven't you thought that perhaps the current system is more "technically" correct than delta systems?. As I recall MS has delta updates and patches; I don't think that MS's way is the best way of doing it, but they surely have a lot of problems by patching and delta updating parts of the OS. And that is a "feature" a wouldn't want in Linux, eventhough it costs the project all dialup users to swhitch back to WinXP. I don't think GNU/Linux has defined itself as a project that does things like some group of people think, but as a project that does what's more "technically" correct to do.

When I said "necessary" what I should have said was: Delta updates are necessary for dialup users that don't want to wait 10 hours just to update 3 packages, who would like their system up-to-date because they like system security, stability & new features. "Necessary", without such an explanation, was too big a generalisation. I apologise. (**I** feel it is neccessary. Have you ever tried staying up-to-date on Ubuntu over 6 months using 3 KB/s dialup access? Lots of patience needed).

I guess you mean "viability". If you read [this post on the project "debdelta"]("http://lists.debian.org/debian-devel/2006/05/msg02226.html"), you will see that it is currently possible to generate deltas and apply them to old .debs to generate new .debs. The the author of this project was working on a way to apply deltas to installed files. [See here for detailed information on debdelta]("http://tonelli.sns.it/pub/mennucc1/debdelta/INFO").
[Apt-sync]("https://wiki.ubuntu.com/apt-sync") was part of the Google Summer of Code 2006, and although seemingly frozen as of November 2006 it looks to be a likely contender, as it doesn't depend on server-side rsync but instead does it client-side & downloads relevant data using normal HTTP.

The current system is stable, and works. But "technically", it is **more *efficient*** to download only what data has changed. Otherwise you are downloading large amounts of redundant, unnecessary data that you already have installed on your computer! This may be safer - having the whole package in case something goes wrong - but still a waste! Waste of server bandwidth, waste of user bandwidth, waste of storage clientside and thus waste of money. OK, so Microsoft appears to use delta updates (and they do usually work, even if there are lots of them). So What? If the delta patched installation is MD5 Checksum proven to be the same as if you had installed the whole .deb then that **is** a feature we want in Linux. More efficiency for the same result is a GOOD thing. [SUSE can use delta rpm's]("http://www-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.3/suselinux-adminguide_en/sec.rpm.html#sec.rpm.delta") for it's updates. That doesn't mean Ubuntu shouldn't.

GNU/Linux is not one single project, but rather the collaboration of many projects. It definitely does things as decided by one big "group of people". Thus things may not be "technically correct", but they usually are because things happen through the collective work of many. Delta updates are very likely to happen eventually. Debian developers have already had [a meeting about it]("http://http://www.fosdem.org/2007/schedule/events/debian_delta_upgrades") in February.

Ubuntu not having delta update capabilities has NOT driven all dialup users away. There is such thing as downloading overnight, but this takes time & effort, to be repeated every few days. It is also a waste/impossibility for those on limited dialup plans, as this approach works best with quite a lot of the month's dialup hours being used. If anything, dialup users don't want to go back to Microsoft, as Windows doesn't give up the download links for it's updates. Synaptic provides a "Generate package download script" feature, enabling dialup users to download from somewhere with broadband or to schedule downloading overnight. Delta updates could enable them to do it straight away.

Technically, a "delta system" would exist *alongside* the current system, as new users would still have to download complete packages. If it were implemented, I'm sure it would be easy to continue using the current method.

---

### Post by The Noble on 2007-04-13
If the delta update system was as no frills to set up as the rest of the system, I would be stoked. Even though I use dsl, it's still a pain to beta test because of the huge amounts of downloads. If the devs can impliment this, I would be very happy.

---

### Post by Nils Olav on 2007-04-14
bump

---

### Post by Polygon on 2007-04-14
i voted yes

i mean, why not? almost all open source projects use patches that are submitted from the community to merge the changes from the patch into the main source tree, why cant we do this for binary packages?

not to mention it would save on server bandwidth costs as it would mean that after the initial download of a package, you would only have to download the difference, which means smaller files a majority of people each have to download.. and considering the userbase of ubuntu, each kb or mb that can be shaved off each download multiplied by how many users download it, = a LOT of saved space

and its also good for people who live in countries that dont have that good internet access, and people with slow internet.

also, did you think about putting this on the launchpad page for ideas for future releases? the developers rarely read the forums, but they do look at the ideas in launchpad

---

### Post by 23meg on 2007-04-14
[QUOTE=Polygon]
i mean, why not? almost all open source projects use patches that are submitted from the community to merge the changes from the patch into the main source tree, why cant we do this for binary packages?[/QUOTE]

Did you read the thread? Patching a binary is an entirely different affair than patching a text file. Sources are plain text, binaries are.. binary; source diffs work line by line, whereas to track differences in binaries you'd have to work at the byte level, and that introduces CPU usage and file integrity concerns, among others.

---

### Post by Polygon on 2007-04-14
i have read the thread, and yes i know that patching basically a text file and a binary are two seprate things, but the concept is the same

they use that patch system cause it would really be harder to manage a source tree if everyone who was adding stuff to the source just posted their whole modified source tree as an attachment and replaced the current source tree with their modified version. the patch makes it so its smaller and faster, as it just adds usually a few lines or something. but the concept between the regular source patching and binary patching is the same.

and ive also noticed that people have stated that debian etch and mandrivia have both implemented this, so it is possible and they have addressed or have solutions to stuff like file integrity and cpu usage...


and i also think that having the computer use a lot of cpu to calculate the differences between the binary packages is well worth it, as usually the binary packages arnt that huge (unless its maybe something like firefox... open office.. the kernel) and it might be possible that it would take less time then downloading the modified package itself?

---

### Post by Nils Olav on 2007-04-14
> **23meg said:**
> Did you read the thread? Patching a binary is an entirely different affair than patching a text file. Sources are plain text, binaries are.. binary; source diffs work line by line, whereas to track differences in binaries you'd have to work at the byte level, and that introduces CPU usage and file integrity concerns, among others.

Definitely not to a point where it's worth bitching about.

---

### Post by koenn on 2007-04-14
> **Polygon said:**
> and ive also noticed that people have stated that debian etch and mandrivia have both implemented this, so it is possible and they have addressed or have solutions to stuff like file integrity and cpu usage...
People have stated that, and they were wrong - as was pointed out in this thread. I know, 'cause I posted it : Debian uses diff's for the Package index, a text file, not for the packages (binaries) themselves. They have several attempts (apt-sync, rsync servers, ...) but if they'd gotten it working, Ubuntu would just have to copy it. But it isn't there.

---

### Post by Polygon on 2007-04-14
ah, ok.

---

### Post by yabbadabbadont on 2007-04-14
SuSE has had binary delta updates for a few years now.  The description in Yast explains about it being CPU intensive and the user has the option of turning them on or off.  If the update fails for any reason, the full rpm is downloaded and installed.

---

### Post by koenn on 2007-04-14
do you happen to have a link to a description of how that works / what's behind it ?

---

### Post by 23meg on 2007-04-14
> **Nils Olav said:**
> Definitely not to a point where it's worth bitching about.

I was merely pointing to the difference, which I thought the poster might have missed; I'm not making a case for delta updates being or not being implemented. See my first post for details. 

> **Polygon]and i also think that having the computer use a lot of cpu to calculate the differences between the binary packages is well worth it, as usually the binary packages arnt that huge (unless its maybe something like firefox... open office.. the kernel) and it might be possible that it would take less time then downloading the modified package itself?[/QUOTE]

We're talking about deploying this method as a default (aren't we?), which means it will affect everyone, all use cases. A computer doing CPU intensive work, such as a server or workstation, may suffer under the high CPU load, whereas it may not suffer as much from the extra bandwidth usage from non-delta updates. It's a tradeoff said:**
> also, did you think about putting this on the launchpad page for ideas for future releases? the developers rarely read the forums, but they do look at the ideas in launchpad

There's more than one blueprint in Launchpad on this already.

---

### Post by Nils Olav on 2007-04-14
> **23meg said:**
> I was merely pointing to the difference, which I thought the poster might have missed; I'm not making a case for delta updates being or not being implemented. See my first post for details. 

Oh, sorry my bad.

---

### Post by yabbadabbadont on 2007-04-14
> **koenn said:**
> do you happen to have a link to a description of how that works / what's behind it ?

Nope.  I just know that they have had it for a while now and that it works.  I loved it back in the day when I was using SuSE and only had a dial-up connection.

---

### Post by koenn on 2007-04-14
Too bad.
I've just been looking at some descriptions of yast at Novel and OpenSuse but there's not even a mention of incremental updates or anything related. 
I've had a go at building a few .deb's myself so i have a rough idea of how the debian packaging system works, and I can imagine there'd  be all sorts of pitfalls when they'd have to re-engineer all their tools and logistics to deal with delta updates. Just wondering how suse handles it ...

---

### Post by yabbadabbadont on 2007-04-14
> **koenn said:**
> Too bad.
I've just been looking at some descriptions of yast at Novel and OpenSuse but there's not even a mention of incremental updates or anything related. 
I've had a go at building a few .deb's myself so i have a rough idea of how the debian packaging system works, and I can imagine there'd  be all sorts of pitfalls when they'd have to re-engineer all their tools and logistics to deal with delta updates. Just wondering how suse handles it ...

I would imagine that they just use some tool like xdelta to generate the binary diffs between the previous version(s) rpm file(s) and the latest one.  Then they package these diffs and the rpm install script uses xdelta to generate the new rpm using the older rpm already on the client machine and the deltas contained within it (the patch rpm).  There of course would have to be checksums and such to validate everything.

---

### Post by Extreme Coder on 2007-04-14
It would be easier for the devs if they used DebDelta:
[http://packages.debian.org/unstable/devel/debdelta](http://packages.debian.org/unstable/devel/debdelta)

Extreme Coder

---

### Post by koenn on 2007-04-14
> I would imagine that they just use some tool like xdelta 
ha, ok, i see. didn't know about xdelta (but wikipedia does). 
still, there are issues. With todays updates it's just a matter of : if version number on server > installed version => candidate for upgrade => install newest version. Clear and simple. 
with delta updates, say I have installed version 3 and you have version 4  and the current version is 5, you'd need the delta from 4 to 5 and I'd need a diff  from 3 to 5. Or 3 to 4, then 4 to 5, in that order. Don't know how that would work out for large packages with multiple binaries (it's getting late here). It would require quite a bit of work, i think : apt, dpkg, packaging tools, repo setup, ... would have to be adapted,...
both Debian and Ubuntu have been looking at it (links earlier in this thread) but apparently without succes so far.

---

### Post by soliac on 2007-04-15
> **23meg said:**
> We're talking about deploying this method as a default (aren't we?), which means it will affect everyone, all use cases. A computer doing CPU intensive work, such as a server or workstation, may suffer under the high CPU load, whereas it may not suffer as much from the extra bandwidth usage from non-delta updates. It's a tradeoff; you trade in some CPU load to save some bandwidth, and the question is whether that's a good tradeoff for Ubuntu's user base in general.

I don't think that delta updates should _always_ be used if possible when updating, at least not for slow computers. Applying deltas does requires amounts of CPU usage, and this would likely crash old computers. That said, newer computers can handle the load required. Delta updates should be implemented to enhance the current system, not to replace it. Full updates and deltas could coexist. Perhaps the package manager could calculate if downloading+applying a delta/deltas would be faster/slower than downloading+installing the whole .deb and take the quicker action.


As for calculating deltas, wouldn't package maintainers do that? If they have a modern machine, it wouldn't take too much time. Servers could then carry on with their job of simply transferring the data instead of having to process it.
How many deltas should there be? I've drawn up a possible way of doing it:

[[IMG]http://img359.imageshack.us/img359/8712/deltaexampledy9.th.png[/IMG]](http://img359.imageshack.us/my.php?image=deltaexampledy9.png)
Should the accumulative delta period be more? Less?

---

### Post by 23meg on 2007-04-15
[QUOTE=soliac]Full updates and deltas could coexist.[/quote]How exactly would be the question.

[QUOTE=soliac]Perhaps the package manager could calculate if downloading+applying a delta/deltas would be faster/slower than downloading+installing the whole .deb and take the quicker action.[/QUOTE]

Faster/slower shouldn't be the only consideration, and leaving it to the machine to handle may not be optimal; the decision should probably be left to the system administrator.

---

### Post by TheMono on 2007-04-15
Why would you run a diff on a package already downloaded? After all, all a .deb is is a sort of archive that also allows you to run scripts when you extract (Yes, I know it is more complicated, but in short that is it).

So, say you have package.deb which installs files /usr/bin/package.sh and /usr/lib/package/package.ini

Then you download an incremental update. Instead of downloading a diff, running that diff on a deb file you already have then installing the new deb file, surely it makes a lot more sense to slightly extend APT so when it is writing out a new file, it can apply it as a delta.

So, to update the package above, you download a .deb containing /usr/bin/package.sh.diff, and /usr/lib/package/package.ini.diff, and any scripts which must be run to make the new version work. When this new deb is installed, it applies those deltas direct to the file instead of delta'ing another .deb package, checksums the new files, and runs any scripts required, just as when you install a normal .deb

CPU usage, and the actual work of extending APT, would be the only downside as far as I can tell.

---

### Post by vijaym on 2008-03-06
Is there any movement on the incremental upgrade idea.

I am in favour of smaller upgrades on an incremental manner. 

I know very little of coding but with bandwidth costs in south Africa and having to update regularly, I have been eating into my bandwidth. In SA outside of the costs, we are subject to DSL caps (1g, or 2 or 3g) which limit our internet use.

---

### Post by igknighted on 2008-03-06
I know fedora has implemented this, through a YUM plugin.  I haven't looked into how they added the functionality though.  I'm sure it is coming and will make it into apt sooner or later.  Right around the time broadband spreads worldwide :)

---

