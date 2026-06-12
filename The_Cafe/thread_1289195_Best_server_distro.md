---
title: "Best server distro?"
date: 2009-10-12
forum: The Cafe
---

### Post by dragos240 on 2009-10-12
I need something that can be installed by a 1gb flash drive. Something that is powerful, reliable, and somewhat easy to manage. I've heard good things about CentOS.

---

### Post by jaxxstorm on 2009-10-12
> **dragos240 said:**
> I need something that can be installed by a 1gb flash drive. Something that is powerful, reliable, and somewhat easy to manage. I've heard good things about CentOS.

CentOs is ok, but its had a bit of a torrid time recently (developer problems) Its also quite a way behind with its repositories so if you want bleeding edge applications you'll have to compile from source.

I personaly use Debian as a server distro. Its never failed me.

---

### Post by -grubby on 2009-10-12
Pretty much any server distro will fit on your flash drive.

As for the best one, that's subjective. "powerful" is vague, and so is "easy." Be more specific.

---

### Post by WalmartSniperLX on 2009-10-12
I never thought bleeding edge and servers really went well together.

If you want less of a curve from Ubuntu then get Debian. It's one of the oldest living major distributions, Ubuntu is based on it, and is reliable and powerful. One alternative I may add is Slackware. You can do the base install using just the first iso which should fit on a 1GB flash w/ no problem.

---

### Post by mmix on 2009-10-12
ui and security for reason, astaro 7.5.

[http://distrowatch.com/?newsid=05694](http://distrowatch.com/?newsid=05694)

---

### Post by dragos240 on 2009-10-12
I'm trying debian stable. Disk 1. I've installed debian before.

---

### Post by synsterky on 2009-10-12
I used debian for server applications for quite some time before switching to FreeBSD. I wouldn't say the learning curve in regard to package management would be that great.

apt-get install vs pkg_add -r

---

### Post by Nozze on 2009-10-12
What's wrong with Ubuntu Server edition?
That's what I run on my server.

---

### Post by vinutux on 2009-10-12
Debian is perfect...but huge size (full installation)...Ubuntu server is best 4 u...itz..minimal and based on debian.

---

### Post by dragobr on 2009-10-12
> **vinutux said:**
> Debian is perfect...but huge size (full installation)...Ubuntu server is best 4 u...itz..minimal and based on debian.

A server wouldn't need a full installation.. a minimal install of debian is really, really small...

Personally, if it is something that would need to be reliable, I'd install debian.. if it is something from with I'll try to learn new things and that can break eventually, I'd go with FreeBSD and/or Open Solaris...

---

### Post by Eisenwinter on 2009-10-12
I also second the Debian minimal installation, but I also think Arch Linux would fit, you can choose not to enable the testing repository (which is disabled by default anyway).

I'd go for Arch without testing, but hey, I'm a bit biased, because I use Arch and love it so much.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-12
Debian/Arch

---

### Post by toupeiro on 2009-10-12
I like ubuntu server, but I would run CentOS because its basically RHEL and I simply have more administrative hours under my belt with RHEL so there is a comfort zone there for me.  For development and experimenting, I like ubuntu server and as I log more hours on it, I may transition, but if I need to rely on it, I'm all about RHEL.

Outside of linux, I am a fan of Solaris.

---

### Post by RiceMonster on 2009-10-12
> **jaxxstorm said:**
> CentOs is ok, but its had a bit of a torrid time recently (developer problems) Its also quite a way behind with its repositories so if you want bleeding edge applications you'll have to compile from source.

I personaly use Debian as a server distro. Its never failed me.

Who needs bleeding edge on a server?

Go with CentOS. It's more or less like getting RHEL for free (of course you don't get the support, though).

---

### Post by lukjad on 2009-10-12
> **dragos240 said:**
> I need something that can be installed by a 1gb flash drive. Something that is powerful, reliable, and somewhat easy to manage. I've heard good things about CentOS.
I just use Ubuntu, very stable. It hasn't crashed once, and I only need to reboot for updates.

---

### Post by Viva on 2009-10-12
I recommend centos too. Ubuntu isn't bad either, wikipedia switched to ubuntu a year ago I think.

---

### Post by Warpnow on 2009-10-12
Ran several severs using ubuntu. No complaints.

---

### Post by beercz on 2009-10-12
Debian - network install :-)

[http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)

Been using it for years on several servers - never had a serious issue with it - not once.

---

### Post by dragos240 on 2009-10-12
I have actually used arch on my servers for some time now, the only issue right now is the apache server. I'd rather not mess with it anymore. So, now I need to make a choice. I'm leaning towards Debian or Arch. Arch because of pacman, and the way all the configuration files are set up, but also debian because of everyone recommending it.

---

### Post by schauerlich on 2009-10-12
FreeBSD.

---

### Post by dragos240 on 2009-10-12
> **EDavidBurg said:**
> FreeBSD.

Is that hard to setup?

---

### Post by schauerlich on 2009-10-12
> **dragos240 said:**
> Is that hard to setup?

[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/)

You tell me. :)

---

### Post by vinutux on 2009-10-12
> **Viva said:**
> I recommend centos too. Ubuntu isn't bad either, wikipedia switched to ubuntu a year ago I think.

yeh....wikipedia switched to ubuntu from redhat 

*[COLOR="Sienna"]"We had a mix of things: some Red Hat 9, some Fedora -- several different versions. The group used a custom-scripted installation procedure, but found that having a multitude of versions was more difficult to maintain for its small five-person IT staff around the world. The move to all-Ubuntu was primarily done with the goal of "making our own administration and maintenance simpler. We decided that we want to standardize on something"[/COLOR]*

**[http://www.cyberciti.biz/tips/wikipedia-moving-400-servers-to-ubuntulinux.html]("http://www.cyberciti.biz/tips/wikipedia-moving-400-servers-to-ubuntulinux.html")**

[http://arstechnica.com/open-source/news/2008/10/wikipedia-adopts-ubuntu-for-its-server-infrastructure.ars]("http://arstechnica.com/open-source/news/2008/10/wikipedia-adopts-ubuntu-for-its-server-infrastructure.ars")

---

### Post by lukjad on 2009-10-12
> **dragos240 said:**
> I have actually used arch on my servers for some time now, the only issue right now is the apache server. I'd rather not mess with it anymore. So, now I need to make a choice. I'm leaning towards Debian or Arch. Arch because of pacman, and the way all the configuration files are set up, but also debian because of everyone recommending it.
Debian/Ubuntu with apache. You don't want something that makes you reboot often for updates. :)

---

### Post by Warpnow on 2009-10-12
Like twenty posts and only a handful of suggestions for ubuntu on the friggin ubuntu forum. Shameful. :P

---

### Post by schauerlich on 2009-10-12
> **Warpnow said:**
> Like twenty posts and only a handful of suggestions for ubuntu on the friggin ubuntu forum. Shameful. :P

Maybe because it's not necessarily the best tool for the job?

---

### Post by Warpnow on 2009-10-12
> **EDavidBurg said:**
> Maybe because it's not necessarily the best tool for the job?

Ubuntu, however, is an excellent server distribution. It will use more space than a debian install, true, but it will still be rather small. Plus...its waaayyy easier to find guides/support for ubuntu than for any other distribution. 

Like I usually tell people new to linux: If you have a problem in ubuntu, then chances are you're the hundreth person to have it, and someone has probably documented a fix. You don't get that kind of support with any other distribution. It is almost as if google and ubuntu have a partnership, with how often google provides me excellent ubuntu support.

---

### Post by vinutux on 2009-10-12
> **Warpnow said:**
> Ubuntu, however, is an excellent server distribution. It will use more space than a debian install, true, but it will still be rather small. Plus...its waaayyy easier to find guides/support for ubuntu than for any other distribution. 

Like I usually tell people new to linux: If you have a problem in ubuntu, then chances are you're the hundreth person to have it, and someone has probably documented a fix. You don't get that kind of support with any other distribution.[COLOR="Red"] It is almost as if google and ubuntu have a partnership, with how often google provides me excellent ubuntu support[/COLOR].

nope........ 
it all right things about desktop but server is diff biz...server geeks prefer old/stable platforms...... but ubuntu is enough stable.....

---

### Post by Warpnow on 2009-10-12
> **vinutux said:**
> nope........ 
it all right things about desktop but server is diff biz...server geeks prefer old/stable platforms...... but ubuntu is enough stable.....

I've found -alot- of support for ubuntu server edition in things ranging from guides, blog posts, to forum posts here.

Not really sure what you're saying. 

Ubuntu + Webmin = Easiest server to setup ever.

---

### Post by dragos240 on 2009-10-12
What IS webmin exactly? How is it helpful? I've managed servers without it before. In fact, I have not tried it.

---

### Post by Warpnow on 2009-10-12
> **dragos240 said:**
> What IS webmin exactly? How is it helpful? I've managed servers without it before. In fact, I have not tried it.

:D

Its a web based GUI. Once installed, it will manage the installation of various servers. Mysql, apache, ssh, ect. It will install and configure them for you in a couple clicks.

It is truly brilliant.

Edit: On second, though, not sure if it will install for you. But after you've apt-get installed them, which is what I always did, it will start them for you and let you configure them in the gui. I think webmin includes these servers as plugins, but its been a while since I've used it so can't remember exactly.

---

### Post by dragos240 on 2009-10-12
Wow!

---

### Post by #11u-max on 2009-10-12
dragos, do you still have your server going?

---

### Post by lukjad on 2009-10-12
> **dragos240 said:**
> What IS webmin exactly? How is it helpful? I've managed servers without it before. In fact, I have not tried it.
I'm using webmin currently. It is basically a GUI way of managing your server. I can log in remotely via Firefox and see what's going on.

To login you just type the equivalent of this:

[http://myUbuntuSite.org:10000](http://myUbuntuSite.org:10000)

---

### Post by dragos240 on 2009-10-12
> **#11u-max said:**
> dragos, do you still have your server going?

Yes, but it's not up. It still works. Fine. I may get SSH up again, since I get chrooting to work (as I learned while installing gentoo.). But only if I get enough requests. It won't be up for too long though, maybe a few days, then some downtime. I am getting a new server for Christmas. That will run 24/7.

---

### Post by kk0sse54 on 2009-10-12
I love these subjective threads, as if the majority of our opinions are worth any sort of merit.
Anyways....

[bias]I'd go with FreeBSD. Depending on what you want to do with it it can take some time to set up but it's a server oriented OS with rock hard stability and fantastic performance. Nevertheless all the *BSDs are viable options as they all make fantastic servers. [/bias] Linux wise I like CentOS and would perhaps even consider using Slackware for a spin. When it comes to server use though, I wouldn't even touch Arch with a 10 foot stick.

---

### Post by dragos240 on 2009-10-12
> **C!oud said:**
>  I wouldn't even touch Arch with a 10 foot stick.

Why?

---

### Post by Sporkman on 2009-10-12
> **C!oud said:**
> I love these subjective threads, as if the majority of our opinions are worth any sort of merit.
Anyways....

[bias]I'd go with FreeBSD. Depending on what you want to do with it it can take some time to set up but it's a server oriented OS with rock hard stability and fantastic performance. Nevertheless all the *BSDs are viable options as they all make fantastic servers. [/bias] Linux wise I like CentOS and would perhaps even consider using Slackware for a spin. When it comes to server use though, I wouldn't even touch Arch with a 10 foot stick.

For performance & solid stability, I'd recommend Ubuntu Server.

---

### Post by dragos240 on 2009-10-12
Anyways, I chose arch. Love the distro for desktop use and server use.

---

### Post by RiceMonster on 2009-10-12
> **dragos240 said:**
> Why?

Why would you want rolling updates with a high chance of breakage on a server? I'd think you'd want something well tested that will be reliable and perform well. CentOS or FreeBSD will give you that.

---

### Post by dragos240 on 2009-10-12
> **RiceMonster said:**
> Why would you want rolling updates with a high chance of breakage on a server? I'd think you'd want something well tested that will be reliable and perform well. CentOS or FreeBSD will give you that.

I can't part with rc.conf and pacman. It's too awesome. It's light, and I had it running over a week (which is really good for a 14 year old), I would update it monthly.

---

### Post by -grubby on 2009-10-12
> **dragos240 said:**
> (which is really good for a 14 year old)

Is there an inherent quality with 14 year olds that causes 1 week of uptime to be impressive?

---

### Post by RiceMonster on 2009-10-12
> **dragos240 said:**
> I would update it monthly.

Good idea; take in all the breakage monthly rather than overtime.

---

### Post by dragos240 on 2009-10-12
Well, there's school. I can't monitor my server during the day. Whereas I could If I was at work. And the fact that my server isn't anything more than a netbook with arch, running under my mom's roof, as long as she's here, a day is glamorous.

---

### Post by dragos240 on 2009-10-12
> **RiceMonster said:**
> Good idea; take in all the breakage monthly rather than overtime.

Sarcasm is not currently installed, cannot detect sarcasm.

---

### Post by Sporkman on 2009-10-12
> **RiceMonster said:**
> Why would you want rolling updates with a high chance of breakage on a server? I'd think you'd want something well tested that will be reliable and perform well. CentOS or FreeBSD will give you that.

...as will Ubuntu Server.

---

### Post by RiceMonster on 2009-10-12
> **dragos240 said:**
> Well, there's school. I can't monitor my server during the day. Whereas I could If I was at work. And the fact that my server isn't anything more than a netbook with arch, running under my mom's roof, as long as she's here, a day is glamorous.

You could if you were at work? What?

---

### Post by #11u-max on 2009-10-12
> **RiceMonster said:**
> You could if you were at work? What?
[[color=blue]linky, enjoy :)[/color]](http://downforeveryoneorjustme.com/)

---

### Post by Regenweald on 2009-10-12
If you are serious about a dedicated server, then Solaris, *BSD, UbuntuServer etc. are your serious options. If you like the idea of having a server and having fun/learning (as you should) stick with arch. ( I get the feeling you were expecting a torrent of arch nominations :)) Servers are about stability/longevity/throughput and so on... I could be wrong, but I'm not aware of any rolling release server OS'es, for obvious reasons. Not many server admin want the freshest updates ( in most cases) unless said update brings considerable performance improvements or better administration. they want their servers to *work* for as long as possible.

---

### Post by dragos240 on 2009-10-12
> **RiceMonster said:**
> You could if you were at work? What?

I'm pretty busy at school and don't have too much time. I understand that a few people like to goof off in the cubical. More time.

---

### Post by dragos240 on 2009-10-12
Also, I have a question. What about kernel updates, and major vulnerabilities. Wouldn't that kill your uptime?

---

### Post by RiceMonster on 2009-10-12
> **dragos240 said:**
> I'm pretty busy at school and don't have too much time. I understand that a few people like to goof off in the cubical. More time.

I really think you should work in an office before you can make claims like that.

---

### Post by schauerlich on 2009-10-12
> **dragos240 said:**
> I can't part with rc.conf and pacman. It's too awesome. It's light, and I had it running over a week (which is really good for a 14 year old), I would update it monthly.

[Arch's init framework is based off of BSD's](http://wiki.archlinux.org/index.php/FAQ#Q.29_What_exactly_is_this_.27BSD-style.27_init_framework_I_keep_hearing_about.3F).

Also, ports/pkg_add are awesome too.

---

### Post by dragos240 on 2009-10-12
True. But from other people's experiences, like the people that my parents go to work with.

---

### Post by Frak on 2009-10-12
> **dragos240 said:**
> I'm pretty busy at school and don't have too much time. I understand that a few people like to goof off in the cubical. More time.

Yep. That's all I do all day; forget clients. They're useless.

---

### Post by dragos240 on 2009-10-12
> **dragos240 said:**
> Also, I have a question. What about kernel updates, and major vulnerabilities. Wouldn't that kill your uptime?
Also, I have a question. What about kernel updates, and major vulnerabilities. Wouldn't that kill your uptime?

---

### Post by Frak on 2009-10-12
[http://www.ksplice.com/](http://www.ksplice.com/)

Little research goes a long way.

---

### Post by CharlesA on 2009-10-12
> **Frak said:**
> [http://www.ksplice.com/](http://www.ksplice.com/)

Little research goes a long way.

That is schweet.

Thanks for the link!

---

### Post by Jekshadow on 2009-10-13
I go with OpenBSD (I know its not Linux) for my firewall/router, Debian on my Web/Database/File servers and then Ubuntu on my LTSP server.

It all depends on the purpose. For norm usage (aka LAMP/File/Print server) go with Debian. If you want something that will have a GUI, Ubuntu, and if you need something rock solid that is really secure, go with BSD.

---

### Post by Frak on 2009-10-13
I'd go with either FreeBSD or NetBSD for a firewall/web/database/file/etc server. Rock solid.

---

### Post by carnagex420x on 2009-10-13
It sounds like you should just have 1 install on your box of w/e distro you like and just lean some basic security, it is nothing to open a http server or pop something up in a terminal and have a server running while your out.
Also Ubuntu Server, has never failed me. But I hear Redhat has nice security features. -up 19 days. ksplice is good too.

---

### Post by dragos240 on 2009-10-13
> **Frak said:**
> [http://www.ksplice.com/](http://www.ksplice.com/)

Little research goes a long way.

It seems they ONLY support ubuntu, and no other distros. Why?
They SHOULD support other distros. Let me know when they support arch. :popcorn:

---

### Post by CharlesA on 2009-10-13
> **dragos240 said:**
> It seems they ONLY support ubuntu, and no other distros. Why?
They SHOULD support other distros. Let me know when they support arch. :popcorn:
It does say to "contact them" so.. they are probably still working on it.

---

### Post by Sporkman on 2009-10-13
> **Jekshadow said:**
> For norm usage (aka LAMP/File/Print server) go with Debian.

...or Ubuntu Server.

---

### Post by RiceMonster on 2009-10-13
> **Sporkman said:**
> ...or Ubuntu Server.

How many times are you going to post that? We get it, you like Ubuntu Server, and that's fine, just like it's fine for people to recommend other things.

---

### Post by Sporkman on 2009-10-13
> **RiceMonster said:**
> How many times are you going to post that? We get it, you like Ubuntu Server, and that's fine, just like it's fine for people to recommend other things.

Ubuntu Server - fast & stable.

---

### Post by Warpnow on 2009-10-13
> **Sporkman said:**
> Ubuntu Server - fast & stable.

But...have you tried the Server Edition of Ubuntu?

---

### Post by Sporkman on 2009-10-13
> **Warpnow said:**
> But...have you tried the Server Edition of Ubuntu?

Why, yes! Yes I have. To describe my findings, please allow me to invoke a quote from a well-respected community leader:

"Fast and stable, Server Edition of Ubuntu, is." --Yoda

---

### Post by ~sHyLoCk~ on 2009-10-13
My vote for CentOS and Debian. Never used ubuntu for server. I don't think server distro will go through a lot of upgrades which will increase the chance of breakage. The devs are not that stupid. You should always use specific tools for specific jobs. CentOS,Debian, Ubuntu server edition are meant for server use, why should you use something else? And why Arch of all things? There's a high risk of downtime due to misupgrades.

---

### Post by Simian Man on 2009-10-13
> **dragos240 said:**
> Also, I have a question. What about kernel updates, and major vulnerabilities. Wouldn't that kill your uptime?

Rebooting into a new kernel will take 2 minutes every month or so.  It's really not a big deal, and will certainly be better than your 1 week of uptime with your Arch server :).

---

### Post by dragos240 on 2009-10-13
> **Simian Man said:**
> Rebooting into a new kernel will take 2 minutes every month or so.  It's really not a big deal, and will certainly be better than your 1 week of uptime with your Arch server :).

It was only due to the fact that my archbox was "found" by my mom. Her electricity bill was about $10 more. Not really too much, but it wasn't because of the distro or anything.

---

### Post by carnagex420x on 2009-10-13
Debian is nice and small but you miss things like having sudo by default. Have never used Arch, but still Ubuntu Server. LTS hardly ever get a new kernel. Downtime = Almost 0

---

### Post by Warpnow on 2009-10-13
> **dragos240 said:**
> It was only due to the fact that my archbox was "found" by my mom. Her electricity bill was about $10 more. Not really too much, but it wasn't because of the distro or anything.

Didn't you say your server was a netbook?

A netbook is unlikely (try, impossible, since the power adapter is likely rated at a mere 35w capacity) to use $10 of power a month. Closer to a max of $3. Its an easy calculation. I just plugged my Acer Aspire One into a device that measures power usage.

It consumes between 25-30 watts. Companies charge per killowatt hour. Assuming there are 720 hours in a month (24x30), then 720 x 30 (maximum my laptop used under load) is is 21,600 watts. That's 21.6 killowatt hours.

Power companies charge various amounts per KwH. Mine is .089, or 8.9 cents per killowatt hour, and texas is known for high electric costs. 21.6 x .089 is 1.9224 or $1.92 per month. 

Here's a link to a guide: [http://michaelbluejay.com/electricity/computers.html](http://michaelbluejay.com/electricity/computers.html)

Considering a core 2 duo desktop and an LCD monitor will prolly pull 15 times that, the advantage of the atom in a netbook or nettop should become apparent.

---

### Post by thisllub on 2009-10-13
> **Jekshadow said:**
> I go with OpenBSD (I know its not Linux) for my firewall/router, Debian on my Web/Database/File servers and then Ubuntu on my LTSP server.

It all depends on the purpose. For norm usage (aka LAMP/File/Print server) go with Debian. If you want something that will have a GUI, Ubuntu, and if you need something rock solid that is really secure, go with BSD.

Lenny is a headache. 
Broken dependencies all over the place.
By far the worst Debian release ever.
You can't even install subversion without enabling testing or unstable repositories.

---

### Post by dragos240 on 2009-10-14
> **Warpnow said:**
> Didn't you say your server was a netbook?

A netbook is unlikely (try, impossible, since the power adapter is likely rated at a mere 35w capacity) to use $10 of power a month. Closer to a max of $3. Its an easy calculation. I just plugged my Acer Aspire One into a device that measures power usage.

It consumes between 25-30 watts. Companies charge per killowatt hour. Assuming there are 720 hours in a month (24x30), then 720 x 30 (maximum my laptop used under load) is is 21,600 watts. That's 21.6 killowatt hours.

Power companies charge various amounts per KwH. Mine is .089, or 8.9 cents per killowatt hour, and texas is known for high electric costs. 21.6 x .089 is 1.9224 or $1.92 per month. 

Here's a link to a guide: [http://michaelbluejay.com/electricity/computers.html](http://michaelbluejay.com/electricity/computers.html)

Considering a core 2 duo desktop and an LCD monitor will prolly pull 15 times that, the advantage of the atom in a netbook or nettop should become apparent.


It has a normal x86 intel processor. It's not ARM or atom. It uses power fast. Too fast.

36W is the adapter. It's an EEE 900HD

---

### Post by Warpnow on 2009-10-14
> **dragos240 said:**
> It has a normal x86 intel processor. It's not ARM or atom. It uses power fast. Too fast.

36W is the adapter. It's an EEE 900HD

The difference in power use is not too considerible.

The performance you get for pumping in that power is.

---

