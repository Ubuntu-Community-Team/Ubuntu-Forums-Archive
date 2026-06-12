---
title: "zfs SHOULD be in the kernel"
date: 2009-09-27
forum: The Cafe
---

### Post by fela on 2009-09-27
The only problem that is preventing the ZFS filesystem in the Linux kernel is its license - until Sun Microsystems release the ZFS under the GPL it cannot legally be ported to Linux.

So to sun microsystems: **Release ZFS under the GPL for **** sake!**

And now repeat after me.

---

### Post by zekopeko on 2009-09-27
> **fela said:**
> The only problem that is preventing the ZFS filesystem in the Linux kernel is its license - until Sun Microsystems release the ZFS under the GPL it cannot legally be ported to Linux.

So to sun microsystems: **Release ZFS under the GPL for **** sake!**

And now repeat after me.

Why would we want ZFS when there is btrfs in development? And ZFS didn't get everything right.

---

### Post by Xbehave on 2009-09-27
ZFS is nice however it is an entire FS stack, its much better to integrate btfs+lvm to give the same feature set without having an entirely separate filesystem layer. For now ZFS is better however btfs+lvm will offer all the features without tying you to either, e.g you can use lvm with ext,etc or you can use btfs without lvm.

---

### Post by RiceMonster on 2009-09-27
If I want to use ZFS, I'll use Solaris.

---

### Post by jrusso2 on 2009-09-27
I am hoping BTRFS will be as good as the hype and be the savior of Linux file systems and end ext filesystems once and for all.

---

### Post by fela on 2009-09-27
> **jrusso2 said:**
> I am hoping BTRFS will be as good as the hype and be the savior of Linux file systems and end ext filesystems once and for all.

We'll see.

So btrfs has online filesystem checking? I didn't know that.

---

### Post by zekopeko on 2009-09-27
> **fela said:**
> We'll see.

So btrfs has online filesystem checking? I didn't know that.

ext4 has online filesystem checking. The work is currently being done in the kernel to support this.

---

### Post by bryncoles on 2009-09-27
Excuse my ignorance but whats wrong with EXT*, and why's ZFS 'better'?

---

### Post by t0p on 2009-09-27
> **bryncoles said:**
> Excuse my ignorance but whats wrong with EXT*, and why's ZFS 'better'?

Looks like the OP messed up the poll.  Should have included a "Don't know" option.  bryncoles might have gone for that.  Me too.

As it is, I shrugged and clicked "Don't care".  Cos I don't, honestly, even I though I don't know what zfs is either.

---

### Post by fela on 2009-09-27
> **bryncoles said:**
> Excuse my ignorance but whats wrong with EXT*, and why's ZFS 'better'?

It has way more features. Google's your friend though as the list is quite long I think :)

---

### Post by fela on 2009-09-27
> **t0p said:**
> Looks like the OP messed up the poll.  Should have included a "Don't know" option.  bryncoles might have gone for that.  Me too.

As it is, I shrugged and clicked "Don't care".  Cos I don't, honestly, even I though I don't know what zfs is either.

Not everyone has to vote. If you don't know, don't vote. It's like when people elected George Bush as president because they didn't know who he was/they were insane.

---

### Post by Regenweald on 2009-09-27
> **bryncoles said:**
> Excuse my ignorance but whats wrong with EXT*, and why's ZFS 'better'?

That would take some explaining :) better you google a 'comparison'. I've seen quite a few spreadsheets of zfs vs btrfs vs ext4 out there.

---

### Post by fela on 2009-09-27
> **zekopeko said:**
> ext4 has online filesystem checking. The work is currently being done in the kernel to support this.

Not for date ('last mount time in the future') errors though.

I know this because when I renamed /etc/hwclock.sh and /etc/hwclockfirst.sh with .bak extensions, the hardware clock wasn't recognized/set/whatever and I got the 'last mount time in the future' error on every startup. I had to give back the .sh extensions and run update-rc to fix it.

---

### Post by JDShu on 2009-09-27
> **jrusso2 said:**
> I am hoping BTRFS will be as good as the hype and be the savior of Linux file systems and end ext filesystems once and for all.

I was under the impression that this is a given eventually. Don't all the developers involved expect btrfs to replace ext?

---

### Post by RiceMonster on 2009-09-27
> **fela said:**
> Not for date ('last mount time in the future') errors though.

I don't think you actually read his post. "The work is currently being done in the kernel to support this" means it is not supported in the kernel yet.

---

### Post by hessiess on 2009-09-27
> **bryncoles said:**
> Excuse my ignorance but whats wrong with EXT*, and why's ZFS 'better'?

ZFS has snapshotting, a limited form of version control implemented at the file system level, which allows you to delete stuff without worrying about possibly needing it again and alows you to track changes to your files over time.

---

### Post by Xbehave on 2009-09-27
> **bryncoles said:**
> Excuse my ignorance but whats wrong with EXT*, and why's ZFS 'better'?
Many fans of ZFS don't just say its cool because it has [SIZE="2"]LVM features[/SIZE]:
snapshots (work better than lvm snapshots)
safe resizing (e.g you don't need to change the partition table to change disk sizes)
entire FS snapshots
Handles whole disk failure (if set-up correctly)
Multiple multiple disks as a single partition
[SIZE="3"]
It has a few nice nice filesystem level features too:[/SIZE]
Online reduction
Online filesystem checking
on disk compression (offered by resier4)
Checksum's all data (requires additional tool in Linux (i think this is good))
copy-on-write 
snapshots of filesystem subtrees (requires other tools)

personally i think it is much better for linux to take its time and implement the features at the correct levels (this is done in zfs as it isn't just a filesystem ) so that as little as possible depends on on any other part (with zfs you get all or nothing, you can't stick to a well tested filesystem layout and gain LVM features)

---

### Post by Bachstelze on 2009-09-27
You got it wrong. The GPL is the problem here, not the CDDL... The CDDL does not prohibit you from integrating code into a GPL'ed project, it is the GPL that forbids you to integrate CDDL code into a GPL project.

---

### Post by gnomeuser on 2009-09-27
[Val Aurora' LWN article](http://lwn.net/Articles/342892/) on the design differences between zfs and btrfs. She has worked on both filesystems and gives a nice clean cut view of what the differences are underneath (hint: outside of the feature set they are totally different implementations).

Now I would like for Linux to have support for zfs in some way or form, the design of btrfs might be better but there are a good many zfs setups out there and a requirement to migrate them is to be able to interact with them. I think everyone would win if we had this support.

For this purpose I believe the FUSE implementation will suffice to create some conversion tools. 

Btrfs is the future for Linux, that doesn't mean we should poopoo zfs, it is a standard and it is adopted in several OSes now. Having support would benefit a considerable group of if not users then potential users. Should it be in the kernel? That depends FUSE allows for this kind of thing to be done outside and that would be ample for conversion but not for use. Aside the problems with license incompatibility ZFS is heavily patented and SUN would have to give a full patent grant even if they switched to a compatible license (but one without a patent grant - say if they switched to the MIT license).

Does the fact that btrfs isn't available now mean our best hope is to throw it away and beg for a relicensing of the zfs code? Absolutely not, btrfs is in the late stages and aside that even if we magically got the license change tomorrow (a process that is likely to take years if ever) porting the code is not a simple matter. Btrfs will be a finished enterprise tested and ready filesystem by then, rolled out by default by every Linux vendor on earth. It runs well, is very feature complete and stable today, you can test it quite easily and the next major rev of Linux distros are likely to carry some preview support. E.g. the next major version of Moblin is likely going to be defaulting to btrfs that is how stable tests today show them the  code is (this is sometime after 2009 Q4). 

Btrfs is the direction we are going, there is very little that can happen to stop that this late in the game. We have several vendors committed to not just supporting it but working on the code. Application developers are aching to start enhancing userspace with it's features such as snapshotting.

---

### Post by Bachstelze on 2009-09-27
By the way, the fact that the CDDL is GPL-incompatible is why it was chosen in the first place, so it's unlikely they will change it to the GPL. :p

---

### Post by forrestcupp on 2009-09-27
There's always something new.  When btrfs is out, there will be something new in the works that will be the future of Linux.  I thought GNU was about diversity.

---

### Post by schauerlich on 2009-09-27
This just shows one of the big deficiencies of the GPL. Here is a great technology with an open source license, but  it can't be brought into Linux because of technical reasons. Because the FSF's definition of "free" puts limits on how code can be used, even when the code is kept open source, we're stuck with having to re-implement an already open source technology. I thought free software was supposed to eliminate duplication of effort.

---

### Post by dragos240 on 2009-09-27
Comparing zfs to ext. What's the difference?

---

### Post by fela on 2009-09-27
> **EDavidBurg said:**
> This just shows one of the big deficiencies of the GPL. Here is a great technology with an open source license, but  it can't be brought into Linux because of technical reasons. Because the FSF's definition of "free" puts limits on how code can be used, even when the code is kept open source, we're stuck with having to re-implement an already open source technology. I thought free software was supposed to eliminate duplication of effort.

What he said. The FSF might aswell be doing closed source software if they refuse to accept an open source program like ZFS.

Although, the kernel team could always boycott the GPL...things would get very nasty very quickly though.

---

### Post by RiceMonster on 2009-09-27
> **fela said:**
> What he said. The FSF might aswell be doing closed source software if they refuse to accept an open source program like ZFS.

Although, the kernel team could always boycott the GPL...things would get very nasty very quickly though.

Considering the amount of code and contributors to the kernel, it would be virtually impossible to switch to another license at this point.

---

### Post by gali98 on 2009-09-27
You would have to ask oracle, not sun... (Though the deal is not in stone quite yet.)
I'm not seeing them too keen on GPLing anything ;)
Kory

---

### Post by cmay on 2009-09-27
I had opensolaris installed for long time on a computer I upgraded from 1 gigabyte ram to 4 gigabytes to run opensolaris better. I think linux has its fileformats and open solaris has zfs and I would let it be at that. also as it has been pointed out the cddl and gpl are both open source but not compatible so its not likely something like this is going to happen anyway.

---

### Post by t0p on 2009-09-27
> **EDavidBurg said:**
> This just shows one of the big deficiencies of the GPL. Here is a great technology with an open source license, but  it can't be brought into Linux because of technical reasons. Because the FSF's definition of "free" puts limits on how code can be used, even when the code is kept open source, we're stuck with having to re-implement an already open source technology. I thought free software was supposed to eliminate duplication of effort.

Yet again folk moaning about the FSF being the FSF.  They're what they've always been, it's a bit odd how that keeps catching folk out.

The zfs devs could re-license it.  Just a thought.

---

### Post by schauerlich on 2009-09-27
> **t0p said:**
> Yet again folk moaning about the FSF being the FSF.  They're what they've always been, it's a bit odd how that keeps catching folk out.But when them being themselves continually causes problems, people keep bringing it up.
> The zfs devs could re-license it.  Just a thought.But they probably won't.

---

### Post by kk0sse54 on 2009-09-27
> **t0p said:**
> 
The zfs devs could re-license it.  Just a thought.

Why should they?

---

### Post by Xbehave on 2009-09-27
[/troll mode] Sorry guys everything regarding zfs has been coverd pretty well so far, as some of you can't read im going to explain why some of you are idiots!

> **dragos240 said:**
> Comparing zfs to ext. What's the difference?
see [my post]("http://ubuntuforums.org/showpost.php?p=8016654&postcount=17") or [Val Aurora' LWN article](http://lwn.net/Articles/342892/)

> **EDavidBurg said:**
> This just shows one of the big deficiencies of the GPL. Here is a great technology with an open source license, but  it can't be brought into Linux because of **technical** reasons. Because the FSF's definition of "free" puts limits on how code can be used, even when the code is kept open source, we're stuck with having to re-implement an already open source technology. I thought free software was supposed to eliminate duplication of effort.
I'm going to assume you meant legal and respond to you post along with the others, if you meant to say technical then I'm sorry for giving you the credit that your post might have been self-consistent.
> **fela said:**
> What he said. The FSF might aswell be doing closed source software if they refuse to accept an open source program like ZFS.
For starters ZFS is not a simple program and would require a lot of work to integrate into the kernel, not that you could have know that unless you read > even if we magically got the license change tomorrow (a process that is likely to take years if ever) porting the code is not a simple matter. or had a clue what you were talking about!


> **EDavidBurg said:**
> But when them being themselves continually causes problems, people keep bringing it up.p
> **C!oud said:**
> Why should they?
The linux kernel has been under GPL for much longer than opensolaris and zfs ever existed. A [list of GPL compatible licenses]("http://www.fsf.org/licensing/licenses/index_html#GPLCompatibleLicenses") has been around and well know to the legal department of sun (who have several GPL project's) for just as long. The choice of a GPL incompatible license was made by sun, why should Linus and all the kernel developers re-license all their work? Something that would require much re-writting because kernel devs don't hand over copyright to Linus so any code by a dev that disagrees / is dead / is contactable would need to be replaced. And this is ignoring the fact that sun has a pile of patents on zfs as mentioned:
> Aside the problems with license incompatibility ZFS is heavily patented and SUN would have to give a full patent grant even if they switched to a compatible license (but one without a patent grant - say if they switched to the MIT license).
And well known by anybody with a clue over why CDDL and GPL are incompatible!
[/troll mode]
Sorry guys but if you insist on asking retarded questions that have already been answered i will insist on insulting you[/rant off]
No offence and have a nice day! The best chance for zfs inclusion is oracle re-licensing it to GPL as they are involved in Linux development, however the amount of work required to get it into the kernel means it would take a long time of the core kernel devs and that time would be better spent on btrfs + lvm related improvements which would yield better results as there are some very nice log file systems that would benefit from the improvements.

---

### Post by RiceMonster on 2009-09-27
> **t0p said:**
> Yet again folk moaning about the FSF being the FSF.  They're what they've always been, it's a bit odd how that keeps catching folk out.

The zfs devs could re-license it.  Just a thought.

Yet again you arguing that anything the FSF does is justified simply because that's what they are.

---

### Post by Earl_Maroon on 2009-09-27
From what I've heard about ZFS it would be great to have it released under the GPL, but I'm happy to wait for BTRFS to be finished.

---

### Post by fela on 2009-09-27
@Xbehave:

about the porting the code thing me bob: how is it that porting the code to the kernel wouldn't be a simple matter when porting it to a fuse driver seemingly is? Excuse my ignorance.

---

### Post by toupeiro on 2009-09-27
The plain and simple truth is rarely plain and never simple. -Oscar Wilde.

btrfs is not out.  zfs is.  If you need the functionality zfs provides, there's basically nothing else out there unless you wanted to get proprietary and run something like WAFL, but then again not everyone has that kind of money either.

If you need ZFS, you're running solaris. I agree it would be nice to see it ported to linux, but I also have no reservations about running solaris either.  What are your reservations about running solaris to use ZFS?  On the systems you would need ZFS on (and I didn't say WANT, I said NEED) what is linux providing you that solaris can't?

---

### Post by schauerlich on 2009-09-27
> **Xbehave said:**
> I'm going to assume you meant legal and respond to you post along with the others, if you meant to say technical then I'm sorry for giving you the credit that your post might have been self-consistent.

I suppose given the context, it was a poor choice of words. I did mean "legal", but when something gets "hung up on a technicality", then that means some small detail that shouldn't be important causes more trouble than it should.

---

### Post by zekopeko on 2009-09-27
> **Earl_Maroon said:**
> From what I've heard about ZFS it would be great to have it released under the GPL, but I'm happy to wait for BTRFS to be finished.

Funny thing is that btrfs is developed primarily by Oracle, parent company of Sun.

---

### Post by fela on 2009-09-27
> **toupeiro said:**
> If you need ZFS, you're running solaris. I agree it would be nice to see it ported to linux, but I also have no reservations about running solaris either.  What are your reservations about running solaris to use ZFS?  On the systems you would need ZFS on (and I didn't say WANT, I said NEED) what is linux providing you that solaris can't?

I don't actually NEED ZFS at all - ext3 is fine for my server's purposes. Just that I think it would be GOOD if ZFS was ported to Linux as some enterprises actually NEED it for its features.

I don't want to run Solaris as I'm used to Linux :P

No, I really couldn't care less whether it was Linux or solaris on my server - I just like Linux that's all.

---

### Post by toupeiro on 2009-09-27
> **fela said:**
> I don't actually NEED ZFS at all - ext3 is fine for my server's purposes. Just that I think it would be GOOD if ZFS was ported to Linux as some enterprises actually NEED it for its features.

I don't want to run Solaris as I'm used to Linux :P

No, I really couldn't care less whether it was Linux or solaris on my server - I just like Linux that's all.

If you're used to linux, you can get used to solaris within a day and be able to administer it.  If ZFS has any real value to you, then less than one day of getting the feel for solaris should pay for itself rather quickly.  If you just want it for the sake of wanting it... :-({|=

Enterprises have plenty of other options available to them besides ZFS.  I administer terabytes apon terabytes of SATA and FC disk without ZFS and have all the same functionality.  Most "enterprises" do.  Most small-medium businesses don't.  For those businesses, Please see the first sentence in this response. :)

---

### Post by kk0sse54 on 2009-09-27
> **toupeiro said:**
> If you're used to linux, you can get used to solaris within a day and be able to administer it.  If ZFS has any real value to you, then less than one day of getting the feel for solaris should pay for itself rather quickly.  If you just want it for the sake of wanting it... :-({|=


Or you could use FreeBSD, it's had ZFS support for a while now. Either way HAMMER > ZFS & btrfs :D

---

### Post by toupeiro on 2009-09-27
> **C!oud said:**
> Or you could use FreeBSD, it's had ZFS support for a while now. Either way HAMMER > ZFS & btrfs :D

I could do that, but the likelyhood of it is pretty small. :lolflag: (I tease about BSD.  Its fine for the people who love it.)

---

