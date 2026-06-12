---
title: "How come no updates in Hardy yet?"
date: 2008-04-28
forum: The Cafe
---

### Post by HappyFeet on 2008-04-28
it's been a few days. shouldnt there be a few updates by now?

---

### Post by NightwishFan on 2008-04-28
They will come in a few days I assume.

---

### Post by kevin11951 on 2008-04-28
just got some updates here.

---

### Post by bobbocanfly on 2008-04-28
Because getting updates into a stable release takes a long exception process and a lot of testing. If you have the hardy-proposed repositories on there are a couple of updates that need some testing.

---

### Post by aaaantoine on 2008-04-28
Ah, so they're not just waiting for the server load to ease up?

---

### Post by HappyFeet on 2008-04-28
> **aaaantoine said:**
> Ah, so they're not just waiting for the server load to ease up?

the servers seem to be running fine right now.

---

### Post by Polygon on 2008-04-28
I just assumed they were taking a break or something from the stress of meeting the release schedule :)

---

### Post by geoken on 2008-04-28
Ragarding the server load; there should be some dialog which initiates synaptic's 'find fastest mirror' feature on synaptic's first run. My download speed went from 20-60k to full line saturation (1100k) after I discovered that feature a few days ago. It really aided me during that 're-install all my old apps' period.

---

### Post by jespdj on 2008-04-29
The final release of Hardy has passed. There will only be security updates from now on.

---

### Post by laney on 2008-04-29
> **jespdj said:**
> The final release of Hardy has passed. There will only be security updates from now on.

That's not strictly true. Regressions/other bugs can also cause new package versions to be uploaded. See [here](https://wiki.ubuntu.com/StableReleaseUpdates) for more info.

---

### Post by aaaantoine on 2008-04-29
Security and stability.

Hopefully the latter point means they'll continue to backport the fglrx drivers as they're released.

---

### Post by etlpkby on 2008-04-30
After being on Hardy since early March (Alpha6) on AMD64 bit version, it's strangely quiet on the updates. I'm used to downloading about 50Mb of updates per day :rolleyes:

After the official release of Hardy, we all should still get security updates and recommended updates (default in Synaptic).

There are still updates needed, coz yesterday I upgraded googleearth to 4.3 (beta) version and found it wouldn't connect to googlearth's servers :(

It was fine with 4.2! Hardy Heron broke 32-bit support for DNS on 64-bit system - See here

[http://ubuntuforums.org/showthread.php?t=770046](http://ubuntuforums.org/showthread.php?t=770046)

..so updates are still essential - just won't be 50Mb and 120 packages per day hopefully :p

---

### Post by Wobedraggled on 2008-04-30
It is odd coming from the beta and it's gajillion updates. Don't worry stuff will roll in soon enough.

---

### Post by isaacj87 on 2008-04-30
If I open up the Hardy-proposed I get 54 updates...The updates are coming soon enough.

---

### Post by wpshooter on 2008-04-30
> **jespdj said:**
> The final release of Hardy has passed. There will only be security updates from now on.


I am will to bet you some good money, that there is going to be a POST final release of Hardy.  This thing has so many bugs in it that I can not even get it to install correctly (might less to run) from either the Live CD version or the Alternate CD version.

I would be looking for Hardy 8.04.**1**.

---

### Post by forrestcupp on 2008-04-30
> **isaacj87 said:**
> If I open up the Hardy-proposed I get 54 updates...The updates are coming soon enough.

Right.  Just enable your backports and proposed updates and you will get updates more regularly.  There is, of course, risk involved with being more cutting edge.

---

### Post by rajeev1204 on 2008-04-30
> **forrestcupp said:**
> Right.  Just enable your backports and proposed updates and you will get updates more regularly.  There is, of course, risk involved with being more cutting edge.



What exactly is a back port ? Iam still not sure .

---

### Post by spamzilla on 2008-04-30
I've had 20+ updates this week alone. 

What server are you getting your updates from? Maybe the server is not up-to-date with its updates.

---

### Post by SomeGuyDude on 2008-04-30
I had about 5MB of updates this morning. Plus quite a few yesterday.

---

### Post by jacksaff on 2008-05-03
> **rajeev1204 said:**
> What exactly is a back port ? Iam still not sure .

With major debian and ubuntu releases lots of under-the-hood changes get made to things like the compiling software. The result is that packages compiled for new versions might not run on old versions. You don't want to update the base software on the old version as this runs the risk of introducing bugs, so old versions of debian tend to get stuck with out-of-date software. 
Back porting means (roughly) compiling the latest version of a program using the older tools of previous releases. The latest firefox for example might get compiled using the tools from ubuntu dapper so that users of dapper can still run the newer software. As long as the new firefox doesn't depend on some new feature in the compiler then this should cause no problems ... except that somebody has to do the compiling and maintain these packages and make sure they get security updates and the like. With a 6 month release schedule back-porting isn't too high a priority for ubuntu. The LTS versions however risk getting very out of date if backports don't get made available.
Hope this made sense. :)

---

### Post by the yawner on 2008-05-03
> **jespdj said:**
> The final release of Hardy has passed. There will only be security updates from now on.
I wouldn't consider the final release of Firefox 3 as a security update. :lolflag:

---

### Post by Zdravko on 2008-05-03
Since 1 week I don't get any updates. Today there were 2 updates detected - libdap and lshw. But the update managers can't connect to download them :(

---

### Post by samjh on 2008-05-03
> **Zdravko said:**
> Since 1 week I don't get any updates. Today there were 2 updates detected - libdap and lshw. But the update managers can't connect to download them :(

Try a different source mirror (if using Gnome: System -> Administration -> Software Sources -> Download From).

I got those two updates today. :)

---

### Post by Dale61 on 2008-05-03
I also had the same two updates waiting for me this morning.  Took all of about 3 minutes to d/l and install.

---

### Post by Sukarn on 2008-05-03
Updates are being tested with hardy-proposed. After enough testing, these should roll over into hardy-updates.

---

### Post by isaacj87 on 2008-05-03
Just checked and I've got 68 updates with the hardy-proposed repo opened.

@anyone: Has anyone installed updates from proposed, and if so, have you had any problems?

---

### Post by wolfchri on 2008-05-03
Is there ANY mirror for the security.ubuntu.com repositories?

At least from here, Germany, the security repositories are no longer reachable, or when they can reached, with a ridiculous low throughput.

Obviously, too many Ubuntu systems now which poll the security repos once a day. Makes about 10-20 million polls a day (yes, there at least this amount of Ubuntu installations worldwide - my family alone has 6 of them now :-)  - what happens when there is a new package in this repos? Down for 6 weeks?

---

### Post by spamzilla on 2008-05-03
I've had 100's of updates to install and an updated kernel *.17 this morning.

---

### Post by amar on 2008-05-03
he he,whilst reading this thread, the first updates poped up in the top right.

spooky

---

### Post by bobbocanfly on 2008-05-03
I have -proposed enabled and its working fine. As a test user most of the time i find it weird when i wake up and there are no updates to install

---

### Post by BigSilly on 2008-05-03
So am I right in thinking you won't get any updates unless you have enabled the Hardy-proposed repo? Because I'm still getting nothing myself, and have had nothing since installing last week.

/is trying to keep up...

---

### Post by Sukarn on 2008-05-03
hardy is supposed to be a stable release, so no updates (unless maybe security updates) will get into hardy-updates without being tested for stability first in hardy-proposed.

If you're really dying for updates, then just enable hardy-proposed. Personally, I haven't had any problems so far, but then again, I haven't tried rebooting into the -17 kernel that was put up in the proposed updates a few hours ago.

---

### Post by BigSilly on 2008-05-03
Nah, I wasn't exactly dying for updates. I was just curious as whether I should have had any by now. I'm not having any issues with Hardy either, so no panic for me, but I was concerned there might be something I've done wrong with my setup which might affect the update manager. If there's nothing, then that's great.

---

### Post by freduardo on 2008-05-03
Not that it matters a great deal but I just had the first two updates since installing Hardy, being libldap and lshw.

Not using proposed btw.

---

### Post by Sukarn on 2008-05-03
> **freduardo said:**
> Not that it matters a great deal but I just had the first two updates since installing Hardy, being libldap and lshw.

Not using proposed btw.

Those two updates have already been mentioned in this thread.

---

### Post by freduardo on 2008-05-03
> **Sukarn said:**
> Those two updates have already been mentioned in this thread.
oops

---

### Post by hackmeister on 2008-05-03
> **samjh said:**
> Try a different source mirror (if using Gnome: System -> Administration -> Software Sources -> Download From).

I got those two updates today. :)

Got the new updates after to switching to the main server in the U.S.. I had it pointed to the MIT mirror during the initial scramble after the release.

---

### Post by rajeev1204 on 2008-05-03
hmm

Never knew about the proposed thing before .

Well, how long before these updates come to us in the regular cycle?

---

### Post by Crazysah on 2008-05-03
Is there any tree trunk for the releases or any schedule to look at?

---

### Post by DC@DR on 2008-05-03
I just wonder if they will upgrade Firefox when it reaches the final release? :-)

---

### Post by Sukarn on 2008-05-03
> **DC@DR said:**
> I just wonder if they will upgrade Firefox when it reaches the final release? :-)

Yes, because in all probability it will be considered a security update.

---

### Post by bobbocanfly on 2008-05-03
Updates every couple of hours in Intrepid now. Its getting exciting. I just pulled down a new gcc and libc6. Bit scared about the new libc6 after what happened last time, though everything seems to be fine so far.

---

### Post by Sukarn on 2008-05-03
> **bobbocanfly said:**
> Updates every couple of hours in Intrepid now. Its getting exciting. I just pulled down a new gcc and libc6. Bit scared about the new libc6 after what happened last time, though everything seems to be fine so far.

Wait, you're telling me that they've started working on Intreprid now? Man, I've been checking the [Development & Programming](http://ubuntuforums.org/forumdisplay.php?f=310) subforum to see when they put up the Itrepid Ibex subforum.

---

### Post by bobbocanfly on 2008-05-03
> **Sukarn said:**
> Wait, you're telling me that they've started working on Interprid now? Man, I've been checking the [Development & Programming](http://ubuntuforums.org/forumdisplay.php?f=310) subforum to see when they put up the Iterpid Ibex subforum.

Yeah Intrepid has been open for a couple of days now. Obviously not much has changed (no new kernel or anything yet) but there are some behind the scenes (thinking libc6, gcc etc) uploads been done.

The #ubuntu+1 channel on freenode is up for discussing it, the Forums staff seem to be a bit slower.

[Here is my sources.list]("http://ubuntu.pastebin.com/f289c4872") bear in mind its not my fault if your system gets pwned upgrading, its just what i used and its working (so far) for me.

---

### Post by Sukarn on 2008-05-03
> **bobbocanfly said:**
> Yeah Intrepid has been open for a couple of days now. Obviously not much has changed (no new kernel or anything yet) but there are some behind the scenes (thinking libc6, gcc etc) uploads been done.

The #ubuntu+1 channel on freenode is up for discussing it, the Forums staff seem to be a bit slower.

[Here is my sources.list]("http://ubuntu.pastebin.com/f289c4872") bear in mind its not my fault if your system gets pwned upgrading, its just what i used and its working (so far) for me.

Didn't need the sources, but thanks anyway.

I've always used the development versions of Ubuntu on my machine as my main OS (with a backup OS installed just in case) so I am quite used to seeing the random breakage and fixing it.

---

### Post by BigSilly on 2008-05-13
Sorry to bump up this old chestnut into the main page again, but is anyone else here still not seeing any updates? The last ones I got were the previously mentioned libdap and lshw over a week ago. 

Don't get me wrong, everything is running just fine, but you know how it is with Ubuntu. You get used to regular updates. The missus is still using Gutsy on her laptop, and that is still seeing updates all the time.

Just finding it a little odd. Could I have something incorrectly set somewhere, or have you noticed there's been no updates too?

Thanks all.

---

### Post by ghindo on 2008-05-13
> **BigSilly said:**
> Sorry to bump up this old chestnut into the main page again, but is anyone else here still not seeing any updates? The last ones I got were the previously mentioned libdap and lshw over a week ago. 

Don't get me wrong, everything is running just fine, but you know how it is with Ubuntu. You get used to regular updates. The missus is still using Gutsy on her laptop, and that is still seeing updates all the time.

Just finding it a little odd. Could I have something incorrectly set somewhere, or have you noticed there's been no updates too?

Thanks all.I've been getting updates just fine for a while.  There were a bunch today, as a matter of fact.  What happens when you type in the terminal:```
sudo apt-get update;
sudo apt-get upgrade
```

---

### Post by BigSilly on 2008-05-13
> **ghindo said:**
> I've been getting updates just fine for a while.  There were a bunch today, as a matter of fact.  What happens when you type in the terminal:```
sudo apt-get update;
sudo apt-get upgrade
```

Shows nothing to be updated. Well it shows one package (sdlmame), but I've locked the older version in Synaptic. I don't want the newer one since it's less compatible with my romset. Other than that there's nothing.

I thought I might have accidentally set Software Sources to download in the background or without notifying me, but I haven't. Oh well, I'm sure it's all good...

---

### Post by FuturePilot on 2008-05-13
Over the past week probably I've received about 40 some updates.

---

### Post by gaffajoiner on 2008-05-13
I have had some, but it says that no updates for 10 days at the top of the box, i keep getting this message when i go for updates, it loads 35 of 36 

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


Can some one please help

---

### Post by FuturePilot on 2008-05-13
> **gaffajoiner said:**
> I have had some, but it says that no updates for 10 days at the top of the box, 
That just means you haven't reloaded the package information in 10 days. No big deal really.

> i keep getting this message when i go for updates, it loads 35 of 36 

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


Can some one please help

System&#8594;Administration&#8594;Software Sources
Uncheck the box for the CD-ROM

---

### Post by Sukarn on 2008-05-13
> **BigSilly said:**
> Shows nothing to be updated. Well it shows one package (sdlmame), but I've locked the older version in Synaptic. I don't want the newer one since it's less compatible with my romset. Other than that there's nothing.

I thought I might have accidentally set Software Sources to download in the background or without notifying me, but I haven't. Oh well, I'm sure it's all good...

Check which mirror you are using, and [how often it is updated](https://launchpad.net/ubuntu/+archivemirrors)
I got some security updates today from a German server. Although I live in India, that German server gives me faster ping and higher download speeds.

EDIT: The updates I got today were for openssl and related packages. You wouldn't get the updates if you don't have openssl installed.

---

### Post by BigSilly on 2008-05-13
> **Sukarn said:**
> Check which mirror you are using, and [how often it is updated](https://launchpad.net/ubuntu/+archivemirrors)
I got some security updates today from a German server. Although I live in India, that German server gives me faster ping and higher download speeds.

EDIT: The updates I got today were for openssl and related packages. You wouldn't get the updates if you don't have openssl installed.

Thanks for your replies, and the info. The server I am currently using is the server for the United Kingdom. I had switched over to the Virgin Media one, but was getting no updates there either. Once I'd switched back to the main UK server, I got those two updates I mentioned earlier, so I stayed put.

I do seem to have openssl installed according to Synaptic. The version I have (it says) is 0.9.8g-4ubuntu3. Does that look right to you? 

Thanks again.

---

### Post by inportb on 2008-05-13
Ah, indeed. I did a dist-upgrade and it installed a new package called openssl-blacklist. What's that?

---

### Post by Sukarn on 2008-05-13
> **BigSilly said:**
> Thanks for your replies, and the info. The server I am currently using is the server for the United Kingdom. I had switched over to the Virgin Media one, but was getting no updates there either. Once I'd switched back to the main UK server, I got those two updates I mentioned earlier, so I stayed put.

I do seem to have openssl installed according to Synaptic. The version I have (it says) is 0.9.8g-4ubuntu3. Does that look right to you? 

Thanks again.

That is the default version in hardy. The version in hardy-security is 0.9.8g-4ubuntu3.1

> **inportb said:**
> Ah, indeed. I did a dist-upgrade and it installed a new package called openssl-blacklist. What's that?

From the description of openssl-blacklist in synaptic,
> 
list of blacklisted OpenSSH RSA and DSA keys 
Contains the list of known-bad OpenSSH keys, for ssh-vulnkeys to use when
examining suspect keys.

---

### Post by BigSilly on 2008-05-13
> **Sukarn said:**
> That is the default version in hardy. The version in hardy-security is 0.9.8g-4ubuntu3.1


Right, so there should be an update on it's way then? I'll keep an eye on things over the next couple of days. There's nothing there according to both update manager and the terminal as it stands at the moment.

Thanks very much for your responses. Much appreciated.

---

### Post by Sukarn on 2008-05-13
> **BigSilly said:**
> Right, so there should be an update on it's way then? I'll keep an eye on things over the next couple of days. There's nothing there according to both update manager and the terminal as it stands at the moment.

Thanks very much for your responses. Much appreciated.

Are you sure that you have hardy-security enabled in your sources.list?

---

### Post by gaffajoiner on 2008-05-13
Thank you for the help, done as you say everything is now ok

---

### Post by BigSilly on 2008-05-14
Changed to the Main server from the UK server, and suddenly got 55 updates! Obviously something wrong with the UK server. I had tried different servers before, but got nothing any different. Still, sorted now.

Thanks for your replies everyone. Much appreciated. :)

---

