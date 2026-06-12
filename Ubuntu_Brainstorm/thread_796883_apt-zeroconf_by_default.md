---
title: "apt-zeroconf by default"
date: 2008-05-16
forum: Ubuntu Brainstorm
---

### Post by CrazyGuy123 on 2008-05-16
It's time we installed apt-zeroconf by default.  It allows intelligent package location, and will significantly reduce update/download times on groups of PC's, as well as saving tons of bandwidth.  It's bloat free at just 13kb, already packaged and very compatible, and hopefully debian will follow our lead.

It's very self contained, only requiring one extra line to be added to a config file to fully integrate with apt.

What next is required for inclusion?

edit:  have a look at [http://trac.phidev.org/trac/wiki/AptZeroconf](http://trac.phidev.org/trac/wiki/AptZeroconf) for more info

---

### Post by smartboyathome on 2008-05-16
I don't think this would be needed for everyone. Only certain people who have groups of PCs.

---

### Post by CrazyGuy123 on 2008-05-16
Nope, but then lots of things included in Ubuntu arent of use for everyone (for example all those HP printing and imaging services that start on all computers on every boot), however since this only takes up an additional 13Kb of disk space and is probably useful for 50% of Ubuntu users it's a worthwhile tradeoff in my opinion.

---

### Post by smartboyathome on 2008-05-16
That percentage is a little high imo. I would say it be more useful for 25% at most of Ubuntu users. A lot only use Ubuntu on one machine.

---

### Post by CrazyGuy123 on 2008-05-16
well even if it's only 5%, I still believe a 13k package is worth the space investment.

The other issue of design and development time is already solved, and the project seems to have a maintainer.

---

### Post by smartboyathome on 2008-05-16
Ok, then, how would it be implimented? Surely it requires SOME setup after installing.

---

### Post by CrazyGuy123 on 2008-05-16
The clues in the name...  :-)  In all seriousness, there are config options you can tweak if you so wish, it comes with a default config that allow it to discover any other system in the network with packages available via avahi, and download packages over the local network rather than over the internet.  It doesn't pose a security risk since packages are digitally signed anyway.

It does require a single line to be added to the apt config file, although I believe thats done automaticly on installation. (although I can't find the bit of code that does that right now)

---

### Post by Brean on 2008-05-18
Hi,

First of all I think the number of Ubuntu/Debian users who benefit from azc is very huge. Ubuntu is used in many Universities and firms and it saves a lot traffic by using azc on all that machines by default.
And just think of all the mobile users who will profit from azc (Students with their Notebooks at the university for example).
And also for modem and isdn users with more than one Computer the benefit would be very huge and it would save money.

Beside that there is no backdraw for the user when azc is installed. Their packages will still be downloaded via Internet if there is no other computer in the local network.

> **CrazyGuy123 said:**
> 
It does require a single line to be added to the apt config file, although I believe thats done automaticly on installation. (although I can't find the bit of code that does that right now)
The deb-package that has been build by the azc developers does all the work automatically (see [http://trac.phidev.org/trac/wiki/AptZeroconf#Configuration](http://trac.phidev.org/trac/wiki/AptZeroconf#Configuration)).

---

### Post by FuturePilot on 2008-05-18
I say a huge +1 to this. I have 4 Ubuntu computers on my network. Even though I don't have a bandwidth limit or anything like that, I think it's a waste to have to download updates again on each computer. Not only that, it just puts more load on the Ubuntu repos ;). It would be very nice if I only had to do it once. Then the other computers would pull the packages from someone else on the network. I've looked into apt-cacher but it's somewhat confusing to set up. I think apt-zeroconf would be much better.

Someone put on idea on brainstorm
[http://brainstorm.ubuntu.com/idea/3085/]("http://brainstorm.ubuntu.com/idea/3085/")

---

### Post by CrazyGuy123 on 2008-05-19
kk  it looks like there is at least some support for this idea, and considering the downsides are very small I'd like to go ahead and contact the people who decide what goes in.  I understand it will require a huge amount of testing before being considered, and probably bugfixes to work in the huge range of situations Ubuntu supports.  Who is it best to ask?

---

### Post by Master Chief on 2008-07-01
> **smartboyathome said:**
> I don't think this would be needed for everyone. Only certain people who have groups of PCs.

Remember Bill Gates's statement: "The Personal Computer only needs 64MB of RAM." so please be careful with such statements!

Say, how much RAM do you have installed?  I have 4 x 2GB Corsair modules installed. That's whopping multiplier isn't it?

Now back to the reason of my visit to this forum; which is that I just received another 48 updates.  Everything cool, but I hate to install everything on all PC's over and over again.  Don't you?

Seems like we have three options here:

1 - Be stupid and keep updating all PC's over and over again.
2 - Be smart and use something to make life easy.
3 - Or be even more stupid and don't update at all.

Now the question is: What do we use? For me that is simple. I pick option 2. Problem is that I don't know what to use, yet. That's the whole discusion for me. Period!  

Here are three solutions:
1 - [http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher)
2 - [http://trac.phidev.org/trac/wiki/AptZeroconf](http://trac.phidev.org/trac/wiki/AptZeroconf)
3 - [https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo](https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo)
    [http://www.linux.com/feature/139213](http://www.linux.com/feature/139213)

Possible problems:
1 - Mixed versions of 32bit and 64bit in LAN

---

### Post by rockin_goliath on 2008-07-01
I don't even know why is is up for debate, since it perfectly fits with Intrepid's stated goals of focusing on pervasive netowork connectivity.

[SIZE="7"]YES![/SIZE]

---

### Post by steeleyuk on 2008-07-01
How does it deal with different versions of Ubuntu? For example, my desktop machine is running Hardy but the laptop is still on Gutsy.

If I'm updating the Gutsy machine, does it simply ignore what is on the Hardy computer?

---

### Post by smartboyathome on 2008-07-01
> **Master Chief said:**
> Remember Bill Gates's statement: "The Personal Computer only needs 64MB of RAM." so please be careful with such statements!

It was actually said to be "The Personal Computer only needs 64**KB** of RAM.", and this was shown that he never actually said that. I just thought I would correct you.

I just meant that not everyone has more than one PC (in fact, I don't think many people do have more than one PC, especially those in the lower middle class).

---

### Post by Master Chief on 2008-07-01
> **smartboyathome said:**
> It was actually said to be "The Personal Computer only needs 64**KB** of RAM.", and this was shown that he never actually said that. I just thought I would correct you.

Bill Gates said literally "Look, the Personal Computer only need[COLOR="Red"]ed[/COLOR] 64KB of RAM." in a 1985 speech, but not as a prediction what most people seem to think. Darn, even I was one of them.

> I just meant that not everyone has more than one PC (in fact, I don't think many people do have more than one PC, especially those in the lower middle class).

But isn't that pure speculation? Driven by your own personal believes? 
I for one only know people who have at least two, or even more computers at home. Why? Well simple.. they have kids (just like me) who need computer/Internet access for school!

Packard Bell did research in The Netherlands and 50% of the households in this little country have three computers!
Just Google for: "Helft huishoudens heeft minimaal drie computers" to backup this claim!

---

### Post by Brean on 2008-07-05
> **Master Chief said:**
> 
Possible problems:
1 - Mixed versions of 32bit and 64bit in LAN
If you worry about a mixture of packages for different architecutres on one machine, that is impossible because azc checks the package file name (that includes the architecutre). 
There are also a lot of big packages that are platform independent like openarena-data and that can be shared between different architecutres with azc.

[QUOTE=steeleyuk]
How does it deal with different versions of Ubuntu?[/QUOTE]
If you have different versions the machines will not interfere each other (in such an environment azc is not that useful unless you want to do an dist-upgrade or if the machine with the newer version still has the old .debs)

---

### Post by Nullack on 2008-07-06
I would imagine this needs a blueprint, the blueprint to be approved for implementation and it to be scheduled for implementation. I think this is usually done at the developer summit.

---

### Post by Master Chief on 2008-07-15
> **Brean said:**
> If you worry about a mixture of packages for different architecutres on one machine, that is impossible because azc checks the package file name (that includes the architecutre). 
There are also a lot of big packages that are platform independent like openarena-data and that can be shared between different architecutres with azc....

Not exactly.  It was more about using 32 bits source code to compile drivers on/for your 64 bit Ubuntu version since there is no guarantee, really, that it'll work.

---

### Post by Rhubarb on 2008-07-31
> **Nullack said:**
> I would imagine this needs a blueprint, the blueprint to be approved for implementation and it to be scheduled for implementation. I think this is usually done at the developer summit.
Here's the blueprint for it:
[https://blueprints.launchpad.net/ubuntu/+spec/apt-zeroconf](https://blueprints.launchpad.net/ubuntu/+spec/apt-zeroconf)

It doesn't seem that there's a lot of activity going on for it.

I'd just installed an apt-cacher server today, it wasn't too hard to do.
But, I'd definitely like apt-zeroconf to be in the repos, installed by default in intreped ibex would be great too.

---

### Post by my_key on 2008-08-22
This would fit the bill perfectly, but I use apt-cacher now, because I have some small Debian (some Freelink) running NAS devices to act as small home servers. Since they're always on apt-cacher is great. Certainly because I've got 7 ubuntu-machines in the house :)

But for the laptops I would _love_ to use apt-zeroconf. I don't know how well it plays with apt-cacher but I'll definitely give it a look. My understanding is that apt-zeroconf is still pretty new, but I'll hope the devs consider to include it soon.

BTW: No need to compare these wonderful features to windows's. Win. doesn't have any repo's, so it's only for the OS's security updates. And come on, windows and security? :)

Cheers,
Michael

---

### Post by Megatog615 on 2008-10-22
Just bumping the topic. I have installed apt-zerconf on 4 machines and one just had Ubuntu installed today and it updated to the latest packages 100 times as fast as regular downloading. apt-zeroconf is amazing!

---

### Post by gnomeuser on 2008-10-22
> **CrazyGuy123 said:**
> The clues in the name...  :-)  In all seriousness, there are config options you can tweak if you so wish, it comes with a default config that allow it to discover any other system in the network with packages available via avahi, and download packages over the local network rather than over the internet.  It doesn't pose a security risk since packages are digitally signed anyway.

It does require a single line to be added to the apt config file, although I believe thats done automaticly on installation. (although I can't find the bit of code that does that right now)

If by doesn't pose a security risk you mean - doesn't require firewall to be disabled or having random ports opened.. then yes.. no security risk at all.. oh wait..

Could this be remotely exploited if enabled by default.

Add to this, we use PPAs for many things, these packages are not generally signed so people learn to just ignore signing messages - this granted is not a zeroconf problem, but still we should consider that the package manager frontends (with the exception of PackageKit) doesn't really refuse to install such unsigned packages. If we changed it to a consent form "I agree to potentially trade off security for the ability to install from this PPA repo" then at least there would be a proper default.

---

### Post by steeleyuk on 2008-10-22
> "I agree to potentially trade off security for the ability to install from this PPA repo"

Surely you're (unintentionally?) agreeing to that anyway by adding the PPA. Other than the default Ubuntu repositories, everything is unofficial and has a risk...

---

### Post by gnomeuser on 2008-10-22
> **steeleyuk said:**
> Surely you're (unintentionally?) agreeing to that anyway by adding the PPA. Other than the default Ubuntu repositories, everything is unofficial and has a risk...

kinda true, but then not so.

You get the ppa from Launchpad which is considered by most users an entry point for interaction with Ubuntu. Other users or application release notes will recommend it for getting the newest Banshee, OpenOffice e.g. yet users are not aware of the difference between Ubuntu and an active PPA community, nor about the risks.

As adding PPAs becomes easier (and trust me it will - in fact I believe it will become a single click operation soon). We could add the warning there but still a warning when you actually partake in the dangerous operation seems like the right thing to do, namely installing packages. This would also give us a uniform warning, say in case some clever hacker sneaks an unsigned packages into the distribution channel, the user needs to see the same warning as he does when taking action to violate the gauranteed level of authentication provided by signed packages.

We could also find a away to get ppas signed somehow and display a trust metric for the repo. Probably impossible without eroding security and trust in the first place and it would basically create a series of "certified by Ubuntu PPAs" which we likely don't want for support reasons.

A third way to do would be to dispense with all of this entirely and jail applications as they are installed to ensure they run but can't interact. The OLPC XO does something similar to this, kids can send each other programs, modify the source code and run it. There is no way to keep this safe by means of signing, so they do security in a whole different way compared to what we do now.

I like option 3, but it seems like a lot of work.. never the less, it also seems like the approach we would really want to not let the signature be the weak point. Just look at what happened to Red Hat few weeks ago, someone compromised their signing key and got signed packages pushed to the update channels.. bad stuff indeed

---

### Post by candrewswpi on 2008-10-29
The first step is probably to get Debian to include apt-zeronconf in their archives. Here's the ITP: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456815](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456815)

Also, I've upgraded the blueprint to link there as well. I think apt-zeroconf would be a really great addition to Ubuntu/Debian.

---

### Post by ssam on 2008-11-08
this would be great.

i have 3 i386 and 1 amd64 on my home network. it would not help the amd64 much (apart from the platform independent packages), but the i386s would see a big gain.

the is a brainstorm entry [http://brainstorm.ubuntu.com/item/3085/](http://brainstorm.ubuntu.com/item/3085/)

---

### Post by gabba on 2008-11-11
> **gnomeuser said:**
> kinda true, but then not so.

You get the ppa from Launchpad which is considered by most users an entry point for interaction with Ubuntu. Other users or application release notes will recommend it for getting the newest Banshee, OpenOffice e.g. yet users are not aware of the difference between Ubuntu and an active PPA community, nor about the risks.

As adding PPAs becomes easier (and trust me it will - in fact I believe it will become a single click operation soon). We could add the warning there but still a warning when you actually partake in the dangerous operation seems like the right thing to do, namely installing packages. This would also give us a uniform warning, say in case some clever hacker sneaks an unsigned packages into the distribution channel, the user needs to see the same warning as he does when taking action to violate the gauranteed level of authentication provided by signed packages.

A simple solution to this problem would be to have apt-zeroconf install only signed packages by default. Advanced users can always edit the config file and allow sharing of unsigned ones at their own risk. *This takes care of the package security risk.*
Apt-zeroconf should also be disabled by default (just as advertising/detecting of network printers is), but easy to find and activate and deactivate with a System->Administration entry. *This takes care of the "open port" security risk.* Default firewall options that open that port only to a local network (198.168.*.* and the like) and close it to the internet would be very smart too.

It'd already help immensely for users who have several ubuntu computers. A very interesting use case would be to network my laptop to a friend's computers, and quickly upgrade his default install to my custom ubuntu configuration by using dpkg --get-selections and --set-selections together with apt-zeroconf. This would be especially useful for those friends that are on dial-up, and much easier than all the other options like saving the packages cache on a CD or setting up a proxy.

---

### Post by gnomeuser on 2008-11-11
> **gabba said:**
> A simple solution to this problem would be to have apt-zeroconf install only signed packages by default. Advanced users can always edit the config file and allow sharing of unsigned ones at their own risk. *This takes care of the package security risk.*
Apt-zeroconf should also be disabled by default (just as advertising/detecting of network printers is), but easy to find and activate and deactivate with a System->Administration entry. *This takes care of the "open port" security risk.* Default firewall options that open that port only to a local network (198.168.*.* and the like) and close it to the internet would be very smart too.

It'd already help immensely for users who have several ubuntu computers. A very interesting use case would be to network my laptop to a friend's computers, and quickly upgrade his default install to my custom ubuntu configuration by using dpkg --get-selections and --set-selections together with apt-zeroconf. This would be especially useful for those friends that are on dial-up, and much easier than all the other options like saving the packages cache on a CD or setting up a proxy.

apt-zeroconf does not install packages, dpkg does and that we can easily control to just fail (or warn with big flaming letters) on unsigned packages. If the firewall was only opened to a local network that would work. For this case I like your solution, any enterprise might want to turn it off by default though, but they are likely to keep their own local proxy of packages they will allow installed anyways (this though is more PolicyKit+PackageKit territory to define).

I do still see a problem, as more PPAs are encouraged (e.g. I can hardly get a decent version of Banshee without the PPA), I will need to ignore signing messages more often. We risk breeding a culture of Windows like behavior (where it has been shown that most users will just click OK without even reading the message). We really do need a long term solution that does not rely on signing for security, it's not meant as a security tool. How to best solve this remains unknown.

---

### Post by gabba on 2008-11-11
> **gnomeuser said:**
> 

I do still see a problem, as more PPAs are encouraged (e.g. I can hardly get a decent version of Banshee without the PPA), I will need to ignore signing messages more often. We risk breeding a culture of Windows like behavior (where it has been shown that most users will just click OK without even reading the message). We really do need a long term solution that does not rely on signing for security, it's not meant as a security tool. How to best solve this remains unknown.

Lol, I suspect Ubuntu-like behavior is already worse: just copy from a random blog these lines of script that begin by sudo in your console, type your password and hit enter. Don't worry, it will fix all your problems. Also, enter your password every 5 min in random dialog boxes whose origin you don't understand.*

But to come back to apt-zeroconf: as long as you download the md5/sha1 hashes for packages from the repositories, you're sure that you have the right package. This is similar to bittorrent where you don't have to trust your sources. So in the end the signed/unsigned question is irrelevent to this particular discussion.

I think the focus should be to get this great software in Ubuntu while taking care of the open port security risk. So as I was saying:
- disabled by default
- local network only by default
- and probably: returns to disable status on each boot
All this of course could be overriden by advanced users so they don't go crazy.

*Edit (before anybody gets offended): this is a joke of course, even though it holds some truth. We human beings always like to take the easy shortcuts, often at our own risk...

---

### Post by mat1t on 2009-02-10
I can't get on to the trac and I'm interested in trying apt-zeroconf on a network. I've installed it but can't find any docs on how to configure it. (I know the name is zeroconf, but that refers to avahi... does it need a proxy setting up?)

---

### Post by lckarssen on 2009-03-17
I have the same problem when I try to access the apt-zeroconf site. It always suggests to save a file. This even happens when I simply go to [http://trac.phidev.org](http://trac.phidev.org).

I've downloaded and installed the debian package from the launchpad bug report, but apt-zeroconf doesn't want to start. It crashes with the following message in /var/log/apt-zeroconf.log:
```
Traceback (most recent call last):
  File "/usr/bin/apt-zeroconf", line 83, in <module>
    from aptzeroconf import main
ImportError: No module named aptzeroconf
2009-03-17 23:16:13 [MainThread] [DEBUG  ] apt-zeroconf 0.3~svn
2009-03-17 23:16:13 [MainThread] [DEBUG  ] Starting httpd on port 1618.
Traceback (most recent call last):
  File "/usr/bin/apt-zeroconf", line 86, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/aptzeroconf/__init__.py", line 51, in main
    httpd = HttpServer()
  File "/usr/lib/python2.5/site-packages/aptzeroconf/http.py", line 43, in __init__
    self.socket = socket.socket(socket.AF_INET6, self.socket_type)
  File "/usr/lib/python2.5/socket.py", line 159, in __init__
    _sock = _realsocket(family, type, proto)
socket.error: (97, 'Address family not supported by protocol')
```

Any suggestions?


Edit: Looking at the AF_INET6, socket option, I guess this is because I disabled IPV6 support...
Edit2: Indeed, after replacing AF_INET6 with AF_INET apt-zeroconf starts and is detecte by the service-discovery-applet.

---

### Post by SoftwareExplorer on 2009-04-07
I found where you can download this from the phidev.org site. If you go to [http://phidev.org/azc/](http://phidev.org/azc/) then you can download the package. Hope that helps someone, it sure took me awhile to find. 

I think that this is a great idea. I installed it, and it worked like a charm. It stayed true to its name asking only if I wanted to turn it on. This is why I love Ubuntu. I think, 'wouldn't it be nice to have a program that does this?", and then I go googling and someone has already done it.

---

### Post by daengbo on 2009-04-14
The apt-zeroconf website is permanently down.

---

### Post by Mr Tim on 2009-04-15
I stumbled upon talk of it a while ago, while I haven't yet installed it I'm planning on using it for the Intrepid to Jaunty update with my desktop and my sister's laptop (seeing as I live in Australia and suffer a ridiculous bandwidth cap). I'm not sure that it should be installed by default, but it should at least be in Universe, and someone should ensure that it is kept up to date.

---

### Post by Jonne on 2009-04-15
I just found out about apt-zeroconf after reading about apt-p2p and thinking about how it would rock to have something that for my LAN without having to set up a dedicated server. I just tested it on my boxes, and it seems to work great (downloading packages is now near-instant :) ).

I would also love to have this in the repo's. 

some notes if you try it yourself:
-install the packages python-pyinotify and python-avahi. dpkg wouldn't install those automatically for some reason. Maybe the gui deb install thing does this for you.
-right after you install it, either reboot or start apt-zeroconf manually (the command is apt-zeroconf, and you don't need to run it as root)

Too bad the project's website died

---

### Post by manishmahabir on 2009-04-16
@zonne

i plan to use apt-zeroconf.
i hope you have already used it.
i have installed from the deb file...0.4.1
do i also need to do something with my sources file?
i would be highly grateful if you could just illustrate stepwise how to set it up.
thanks in advance!

---

### Post by Jonne on 2009-04-16
apt-zeroconf will make the changes automatically when you install it, so no need to change the sources.list file. Just make sure you reboot after you install it to make sure apt-zeroconf is started (it won't start automagically right after installing for some reason, alternatively you could just start it manually).

If you find it to be buggy or something, you'll need to uninstall it and reboot again before your update manager starts working again. (on one of my boxes it does act a bit weirdly, but apt was already kinda screwed up there).

Keep in mind that apt-zeroconf registers itself as a proxy, so if it crashes for any reason, you will not be able to update or install new software until the process is started again. If you find apt failing, check in your system monitor to see if it's actually running.

Also note that the project website seems to be gone, so you're really on your own as far as support goes (apparently the original developer lost interest or something).

If you're new to Ubuntu, I wouldn't recommend it, tbh. There's just too much that can go wrong since this thing messes directly with how apt works.

---

### Post by manishmahabir on 2009-04-16
Thanks Jonne!
i have installed and rebooted as you said.it is working fine.
actually i also have apt p2p set up for which i had to insert localhost:9977/ in each source line.
on it i have again installed apt-zeroconf and it is working fine.
i was actually testing some method to share the downloaded packages zeroconf. i first came about apt p2p then apt-zeroconf.

apt-cacher did not appeal as i had to set up a server.

do you have any idea about apt cacher ng?

---

### Post by Jonne on 2009-04-17
I think apt cacher ng is a dedicated server thing too, which i don't want to use. My home network consists of mostly laptops, and I don't want to need to reconfigure my sources.list every time i go somewhere else with any of my boxen.

If your boxes are desktops and you have a server, apt-cacher-ng is for you, otherwise apt-zeroconf is a better option (unless you have 100s of computers, in which case the zeroconf traffic might cause issues on your network, i don't know how well that scales).

If only it was supported...

And it's nice to know that apt-p2p and apt-zeroconf work on the same box, i wasn't sure if that was possible.

---

