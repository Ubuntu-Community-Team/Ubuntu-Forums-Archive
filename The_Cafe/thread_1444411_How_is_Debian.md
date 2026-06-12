---
title: "How is Debian?"
date: 2010-04-01
forum: The Cafe
---

### Post by Laxman_prodigy on 2010-04-01
Yes, Debian.

I heard it is very stable. They call themselves, "Universal Operating System".

Is there anything Ubuntu can do and Debian cannot? Just wanted to gather practical experiences about Debian.

---

### Post by Grenage on 2010-04-01
Debian is designed to be stable, it's one of the most stable systems out there.

Ubuntu is based on Debian, but designed to be more 'cutting-edge'.  Therefore, Ubuntu has many features that Debian does not have by default.  I use Ubuntu on my Desktops, Debian/CentOS on my Servers.

---

### Post by detroit/zero on 2010-04-01
> **Laxman_prodigy said:**
> Is there anything Ubuntu can do and Debian cannot?
Break with every update.

---

### Post by pbpersson on 2010-04-01
Is Debian as easy to use?  Is it user friendly and is everything intuitively obvious?  When you install it, will all the movies and multimedia features work when you surf the web?  If not, can you install Debian_Restricted_Extras and THEN can you use it?

I want something that I can install and then start using - being productive with my OS.  People have suggested that Debian is not up to that challenge, that Ubuntu has added a layer of "easy" to Debian.

Is this true?

---

### Post by Psumi on 2010-04-01
> **pbpersson said:**
> Is Debian as easy to use?  Is it user friendly and is everything intuitively obvious?  When you install it, will all the movies and multimedia features work when you surf the web?  If not, can you install Debian_Restricted_Extras and THEN can you use it?

I want something that I can install and then start using - being productive with my OS.  People have suggested that Debian is not up to that challenge, that Ubuntu has added a layer of "easy" to Debian.

Is this true?

[http://www.debian-multimedia.org](http://www.debian-multimedia.org) - For video codecs.

To have a stable flash: add contrib to all your sources.list entries and use the flashplugin-nonfree like in ubuntu.

There is no sudo, add yourself to the sudoers list if you need to, otherwise enjoy su - command in terminal.

You need to make a root password, gksu will require this password. If you lose your root password, time for a re-install, as it cannot be recovered (according to debian users that is.)

I suggest installing a base CLI system with their netboot, and installing metapackages.

---

### Post by detroit/zero on 2010-04-01
It's a little more "hands on" than Ubuntu. It's well documented, and they do have forums of their own.

---

### Post by malspa on 2010-04-01
In the past, I've enjoyed having both included in a multi-boot set-up.  Debian will take longer to configure and set up, but some of that time is offset by bugs you sometimes run into with Ubuntu that you don't have in Debian.

I liked that I could get a Ubuntu CD mailed to me for free.  That was important at the time because I was using dial-up for years.

Once you get Debian set up and configured, especially if it's Debian Stable, you're pretty much home free.  That system is just going to keep working.  And for me it turned out that it wasn't as difficult to install as I thought it would be.

But after using Debian Etch and then Debian Lenny, along with Ubuntu and other distros, when it came time to do new installations on a new (to me) computer, I went with Mepis and Linux Mint, just to save myself some time.

With Mepis, you get a distro that's based on Debian and is almost the same as Debian Stable.  Same repositories, but you have a few Mepis tools added, and Mepis repos, and the Mepis Community repos are available. 

Not saying that Mepis is any better than Debian, and not trying to push Mepis, but with Mepis it's like having a Debian system that I can install in 20-30 minutes. 

Anyway, I generally stick with Debian Stable and Ubuntu LTS, and overall, my experiences with both each of those were really not all that different.  I did feel more comfortable keeping Debian completely updated than Ubuntu.  More afraid that an update will break something in Ubuntu.

---

### Post by Psumi on 2010-04-01
> **malspa said:**
> Not saying that Mepis is any better than Debian, and not trying to push Mepis, but with Mepis it's like having a Debian system that I can install in 20-30 minutes.

Though the wait is long for downloading packages, it's not usually something I factor in when I talk about install times; though average users would probably disagree.

Not factoring in the download/install time of all the packages needed for your "ready" system, it would take less than 20-30 minutes; as the packages I install for my system are basically all that's needed to run the system.

I use conky, and I regularly back it up along with my openbox autostart.sh, so I can have a system already configured for use quickly.

I don't use any taskbar, systray, etc. just the notification-daemon.

---

### Post by jackiemcghee on 2010-04-01
It's funny to see this topic here as I was just about to ask the same question. I'm pretty comfortable using Ubuntu and will always be grateful to it for being the distro that made me able to live with and then go on to enjoy Linux.

Sadly, though, I am not at all pleased with the direction they are taking. The new GTK+ themes for example look terribly amateur - as if no-one had ever come across the word subtle being applied to gradients, for example. I also have a vague unease about how top-down Ubuntu (as a community) is becoming.

I used Linux for business and pleasure and the main thing I care about is having a machine I can be productive on as well as goof around with and so I've been looking around. I considered Arch because I love the approach they take, but it seems very focused on the edge of the bleeding edge and I have concerns that the whole system might go POP when I'm in the middle of something really important. Which would be Bad. In the end, I reckon I am safest if I stick with a distro that uses APT: it's something I know and I've never had any problems with it.

Taking all that together, and now reading this thread, I'll stick with 9.10 until my new laptop arrives and then switch to Debian.

---

### Post by Psumi on 2010-04-01
> **jackiemcghee said:**
> Taking all that together, and now reading this thread, I'll stick with 9.10 until my new laptop arrives and then switch to Debian.

Remember to make windows recovery cds, unless it doesn't come with windows. Manufacturers no longer provide recovery cds, and will force you to make them yourself if you aren't careful (You can't return a laptop that came with windows, without windows.)

---

### Post by snowpine on 2010-04-01
> **Grenage said:**
> Debian is designed to be stable, it's one of the most stable systems out there.

Ubuntu is based on Debian, but designed to be more 'cutting-edge'.  Therefore, Ubuntu has many features that Debian does not have by default.  I use Ubuntu on my Desktops, Debian/CentOS on my Servers.

Debian is simultaneously more stable AND more cutting edge than Ubuntu. How? Debian is divided into three "branches": Stable (like using a more stable version of Ubuntu LTS), Testing (roughly equal to using a current Ubuntu release), and Unstable (a preview of what Ubuntu might be like in six months). 

A lot of Debian users choose Stable for servers and Testing or Unstable for casual desktop use (so they can have newer applications). But if you want the ultimate "just like Ubuntu but much more stable" experience, you can't beat Debian Stable Gnome--it is pretty much the "flagship" of the Debian fleet.

Just as Ubuntu has its derivatives (Mint, Masonux, gOS, etc.), so too does Debian. Three of my favorites:

MEPIS is cool because it mixes a Stable core with newer versions of desktop applications (like Firefox, OpenOffice, and the latest KDE).

Sidux is cool too because it's based on the latest Unstable stuff, but with an extra repository to smooth some of the rough edges.

CrunchBang was my favorite Ubuntu derivative, now they are switching to Debian with the new "CrunchBang Statler" Alpha-testing release. A sleek, minimalist, productive experience.

---

### Post by malspa on 2010-04-01
> **snowpine said:**
> But if you want the ultimate "just like Ubuntu but much more stable" experience, you can't beat Debian Stable Gnome--it is pretty much the "flagship" of the Debian fleet.

Or folks might like a Debian KDE version or a Debian Xfce version instead of Kubuntu or Xubuntu.

---

### Post by Objekt on 2010-04-01
I've been meaning to try Debian Lenny for a few months.  When I tried to install it a couple of weeks ago, the installer quit about 1/3 of the way in.  Apparently I got a bad download of the install CD.  I am usually meticulous about checking MD5 sums on downloads, but I must have missed one.

My primary interest in Debian is graphics performance.  I don't know what the deal is, but some 3D apps just aren't as snappy under Ubuntu 9.10 as they are under Windows XP, using exactly the same hardware (listed in my sig).  Even with desktop effects and all other Gnome eye candy turned off, there's a slight sluggishness to, e.g. Urban Terror 4.1 under Ubuntu vs. Windows XP.  I'm thinking Debian might not have the same problem.  It could just be that Nvidia's Linux drivers are lousy.

---

### Post by bpalone on 2010-04-01
Everyone, please keep the feed back coming.  I had also thought about posting a similar question, as I am also thinking of maybe making a change.  I currently have it installed in a VB on my laptop, just to get a feel for it and the differences.  Haven't played with it enough to come to any conclusions.

So, again keep up the feed back.

Thanks.

---

### Post by gjoellee on 2010-04-01
> **Laxman_prodigy said:**
> Yes, Debian.

I heard it is very stable. They call themselves, "Universal Operating System".

Is there anything Ubuntu can do and Debian cannot? Just wanted to gather practical experiences about Debian.

Because Debian is so stable it is often put on servers, as Debian usually has much less downtime than Windows Server has. Debian is also free...

My school use Windows Server, and it crash like once a week. Someone I know who works with servers, has a own Debian server. It has not crashed in over a year, and has only been down due to maintenance.

Although when it comes to desktops, you will soon notice that Debian is far from up to date, which has an effect on:
-Supported hardware
-Boot experience
-How easy it is to use
-Preformance
-and much more

Although Debian is a good OS, you will rather use Ubuntu unless you need a computer that you don't shut down more than once every 10 years.

---

### Post by Grenage on 2010-04-01
Windows is easily as stable as Linux (generally), these days.  People just have a habit of mucking about with Windows servers more, the GUI makes that easy.

---

### Post by Bachstelze on 2010-04-01
> **Laxman_prodigy said:**
> 
Is there anything Ubuntu can do and Debian cannot? Just wanted to gather practical experiences about Debian.

No. Just like there's nothing Debian can do and Ubuntu cannot. The difference is not in the things you do but in how you do them. Same goes for any Linux distro.

---

### Post by NightwishFan on 2010-04-01
Debian is excellent. I plan on reinstalling it actually and I might adopt it as my main distro. Mainly because such an incredible project deserves satisfied users. As for my quick review, it will do what you want. It will involve a bit of manual set up to get it there and you will lack many GUI tools, but it is awesome. As for graphic performance I do not see any difference between Debian and Ubuntu on Nvidia (or Ubuntu and Windows for that matter on Nvidia) but my intel chip works great on Debian. I really am not wanting to change just because Ubuntu's setup is (by default) how I have to work to get my Debian like. I am just lazy.

---

