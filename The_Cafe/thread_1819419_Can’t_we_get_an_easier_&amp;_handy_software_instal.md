---
title: "Can’t we get an easier &amp; handy software installation process in Ubuntu?"
date: 2011-08-06
forum: The Cafe
---

### Post by maqtanim on 2011-08-06
[COLOR=DimGray]*I've written this article quite a long ago in [my blog]("http://adnan.quaium.com/blog/1900"). I got some wonderful comments there. If you like, you can also check those [comments in my blog]("http://adnan.quaium.com/blog/1900"). I think this topic should get enough attention. So I am posting the article in the cafe. Hope that, nobody will mind. :)*[/COLOR]
[CENTER][IMG]http://img855.imageshack.us/img855/6931/linen.png[/IMG] 
[/CENTER]

After eying the title of this post, you must be astonished -  why on earth I am saying that Ubuntu needs an ‘*easier*‘ and ‘*handy*‘ software installation process! Software Installation in Ubuntu is already a breeze. All one have to do is just heading to the *Ubuntu Software Center*, find/choose what software one needs and then hit the install button. Or one can download the *.deb*  package and double click it to install the program. The installed  program is ready for one in no time. Anyone have to admit that it is  really pretty easy, even easier than Windows (where you have to click  lots of ‘Next’ buttons during the installation process).


 This whole procedure is easy if the computer is connected to the  internet. What if the computer is in offline? You’re probably wondering  who doesn’t have internet now a days! Actually there are a lots of them.  Such as in my country Bangladesh, internet is not available to the  majority of the computer users. Even though the minority gets the  benefit of internet, they don’t have blazing fast speed. An average home  user gets 10 kbps to 15 kbps download speed. Which is quite a low speed  for downloading. And obviously majority users are using Windows. As  there is a scarcity of internet and proper download speed, people  download  necessary software installer from some online computers and  then use that downloaded installer to several other offline computers to  install the program.


 Now compare the scenario with an Ubuntu installed offline PC.  Probably the easiest way to install a software in an offline Ubuntu  computer is using the [Keryx]("http://keryxproject.org/").  It can keep track of the source ppa and dependencies, which is quite  awesome. But still not easy enough to handle for a newbie. How? Well…  firstly, using a third party software to install programs is a bit ‘*scary*‘.  Secondly, if any one wants to share the downloaded file with others  then it will be a problem. Suppose I have an offline Ubuntu computer and  I want to install some program. So I take my flash drive (which have [Keryx]("http://keryxproject.org/")  inside it) and connect it to a computer which has the internet  connection. Then I download the desired program with the Keryx, and  install it in my offline computer. It is easy. But what if I want to  install that same downloaded program to another offline Ubuntu PC? There  are sure chances that the dependencies in the second PC will be  conflicted. Because it downloads the dependencies according to the first  PC, so the second PC will suffer from dependency issues. And that is a  nightmare for an average computer user. So as a result, previously  mentioned “*download with one computer and install in several different computers*” theory does not work here smoothly.


 To be frankly, the average users don’t give a damn about the  dependencies. They don’t want to search the web to find out which  libraries (and which versions) are required to install a specific  program. They need the system to be ‘just worked’. I’ve seen many users  who are very much afraid to use Ubuntu as they don’t have internet  connection in there home. And they don’t want to jumble themselves with  the* dependency hell*.


 My point is to find out that whether it is possible to implement a  more easier and handy software installation process for the offline  computers (like MacOSX may be). All the dependencies will be packed in a  single package for a certain program. (Please don’t be confused with  the projects like [portable linux apps]("http://portablelinuxapps.org/").  I am talking about a complete software installation.) The user just  need to download that file and drag-n-drop that file (like MacOSX) to  some places (may be in the Application [lens]("https://wiki.ubuntu.com/Unity/Lenses"))  or double click the file (like the .deb files) for installation. Thus  it would be much more handy for the newbie users as well as the offline  users.


 I am not sure if I made my point clear. In recent days, Ubuntu  emphasis on the looks-n-feels for the users. I think it is also  important to simplify the software installation process for the  newcomers as well as for all the users. To my view it is one of the  important bottle neck. May be it is a dumb idea. Some of you may point  your finger to the security issues. But I didn’t find any simpler idea  than this for helping the offline users. Any thought on this? Any other  idea?

---

### Post by Bandit on 2011-08-06
There needs to be at least 2 DVDs of offline software available for download so that someone can A) order them, or B) have someone download them for you. This was common not to long ago, but yea people are forgeting about lack of internet for most the planet.

---

### Post by SeijiSensei on 2011-08-06
There are DVD releases at cdimage.ubuntu.com, though one DVD obviously cannot encompass the entire repository.  Here's the one for Lucid: [http://cdimage.ubuntu.com/releases/10.04.3/release/](http://cdimage.ubuntu.com/releases/10.04.3/release/)

You might consider switching to Debian.  Here's the current Debian repository on eight (!) DVDs:  [http://cdimage.debian.org/debian-cd/6.0.2.1/i386/iso-dvd/](http://cdimage.debian.org/debian-cd/6.0.2.1/i386/iso-dvd/)

---

### Post by Furball588 on 2011-08-06
ya know....at what point do groups that supposedly build farms , build schools, educate people, and ultimately communities embrace technology as part of their mission?

Considering most models of building an infrastructure focus on providing industry their bandwidth first and letting the people benefit from the after effects, I wonder how much benefit there would be to simply setting up a couple of repositories in a place to get the ball rolling...

I know that probably doesn't directly solve anything.. but I guess at some point, you make the statement..burn your own disk :)

---

### Post by 3rdalbum on 2011-08-06
> **SeijiSensei said:**
> There are DVD releases at cdimage.ubuntu.com, though one DVD obviously cannot encompass the entire repository.

DVD images only hold the contents of the CD, plus extra language packs. They don't hold extra programs.

It would be perfectly possible to make self-contained programs that are installable by dragging them to your home directory or /usr/applications folder. It's perfectly possible to make Windows-style installers. It's perfectly possible to do these on Linux for most programs.

Nobody wants to do them, and almost nobody would want to install from them.

They are too big. They introduce security flaws by using old libraries. They are unsigned, so they can be modified at any point in their journey by a malicious party to contain malware. They create more work for developers and packagers. They don't allow for centralized updates, so each and every program has to have its own logic and system for handling its own update, which is frankly a nightmare for users. Or they force the user to do the updates themselves, which is another brand of hell.

Keryx is a stop-gap solution until everybody has internet access wherever they have their Ubuntu computer.

You're certainly not the first person to have suggested copying Mac OS and Windows-style installation methods, but the reason why these haven't been adopted on Linux is simply because our method is better suited for Linux and Linux users, and I'd go so far as to say it's better overall. Note that Windows and OS X are moving toward the Linux repository model (which annoyingly gets called "App Store model", even though the repositories predate the iOS App Store).

---

### Post by 3Miro on 2011-08-06
> **3rdalbum said:**
> DVD images only hold the contents of the CD, plus extra language packs. They don't hold extra programs.

It would be perfectly possible to make self-contained programs that are installable by dragging them to your home directory or /usr/applications folder. It's perfectly possible to make Windows-style installers. It's perfectly possible to do these on Linux for most programs.

Nobody wants to do them, and almost nobody would want to install from them.

They are too big. They introduce security flaws by using old libraries. They are unsigned, so they can be modified at any point in their journey by a malicious party to contain malware. They create more work for developers and packagers. They don't allow for centralized updates, so each and every program has to have its own logic and system for handling its own update, which is frankly a nightmare for users. Or they force the user to do the updates themselves, which is another brand of hell.

Keryx is a stop-gap solution until everybody has internet access wherever they have their Ubuntu computer.

You're certainly not the first person to have suggested copying Mac OS and Windows-style installation methods, but the reason why these haven't been adopted on Linux is simply because our method is better suited for Linux and Linux users, and I'd go so far as to say it's better overall. Note that Windows and OS X are moving toward the Linux repository model (which annoyingly gets called "App Store model", even though the repositories predate the iOS App Store).

+1. You can compile program with static libraries and produce a .deb file that is self contained. It can even be version independent, one deb for all versions of Ubuntu, however, this is very impractical. Static programs are big and maintaining them is a clumsy process. All the tools are in place to facilitate such form of distribution, but people are not doing this because too few people are interested enough to do the heavy work.

---

### Post by Warpnow on 2011-08-06
No offense, but I don't think this is necessary. For offline machines, you don't want to run Ubuntu anyway. The need for updates being even more important the lack of software.

If you are running linux on an offline computer, you realy should be using Debian.

---

### Post by Thewhistlingwind on 2011-08-06
> **Warpnow said:**
> 
If you are running linux on an offline computer, you realy should be using Debian.

This.

The problem with programs that bring their dependencies with them is that the author of the software must now take it upon themselves to maintain their dependencies versioning, if they don't do this, you as a user are screwed.

---

### Post by m4tic on 2011-08-06
I've brought up this topic lots of times and I've reached a reasoning that it's pointless to ask people from well-off countries about it, most don't seem to get it. For example, the DVD repository image point shouldn't even be mentioned, if bug #1 can be fixed, an easier way to install software like the others needs to be found, we can't just ignore this. Yes they're moving to app stores, but they still have offline installs, wasn't more choice better in the linux world?

---

### Post by desnaike on 2011-08-06
This site will prepare and sell you the entire repository [http://www.linuxcd.org/view_distro.php?id_distro=452](http://www.linuxcd.org/view_distro.php?id_distro=452). You and a number of friends can pool your resources and purchase the entire up to date repository 9 dvd's that looks like the best option in your position.

---

### Post by ninjaaron on 2011-08-06
If the OP is concerned about the issue, he could easily start a community project to bring together a dvd or three with extra debs.  This is not difficult.


Or you could just use Debian, which already has this, and comes with way more software than Ubuntu by default.  Debian 6 has a pretty easy installer built in, and it isn't very different from Ubuntu.

---

### Post by maqtanim on 2011-08-07
Downloading and burning  large repository is not a good idea. Infact it is a very lame idea. Why? Let me explain. Suppose I (somehow with my crappy internet connection) downloaded all the repository and burned them in disks. Then I can distribute them among my friends. But how a person, who read about Ubuntu and decided to give it a try but doesn't know me and doesn't have any internet connection, can possibly install the necessary softwares in his freshly installed ubuntu? But in case of Windows, he can just download a single setup.exe file of the desired application from other computers (which have internet connection) and easily install that file into his computer. No internet, no dependencies, simple installation method.

We are living in a third world country. We do not have mass internet coverage all over the country. Very few people are lucky enough to use Internet. And the average net speed is less then 30 KBps. So offline installation is very much important for us. And if a person need to be a geek to install offline softwares in Ubuntu, then why they'll go for Ubuntu instead of Windows? 

After working for the Ubuntu Bangladesh LoCo team for a long time, I realized that general computer users don't like any hassle. They want to switch to an alternative OS other than Windows to avoid viruses, malfunction, system crash, system hang, BSOD etc. But the offline software installation in Ubuntu is so much hassle that in the end they choose to stick with Windows. When we talk with general people, the first thing they ask is - "I've heard that without a proper internet connection Ubuntu is cripple? Is that true?". So I've to tell them the bitter truth. This is really a bottleneck for spreading Ubuntu in the third world counttry.

---

### Post by Bapun007 on 2011-08-07
what about the pbi packages of pcbsd ! Is it similar to windows .exe programs .

---

### Post by LowSky on 2011-08-07
I'm confused. Ubuntu is an internet reliant distribution of Linux. Why not use a lighter version much like Puppy or DSL.

---

### Post by Elfy on 2011-08-07
> **LowSky said:**
> I'm confused. Ubuntu is an internet reliant distribution of Linux. Why not use a lighter version much like Puppy or DSL.

Because there'd be nothing to complain about then.

---

### Post by NightwishFan on 2011-08-07
I think all the bases have been covered already.

Solutions?
1. Put the repository on DVDs available for purchase at a low price similar to Debian. (Also for download but purchase is probably better in places with poor internet). Downsides: Have to purchase/download which takes time. Not very flexible to adding more software in the future, probably best to mainly distribute these with LTS releases.

2. Create monolithic debs for specific programs. Downsides: Harder to build and maintain, messy. Perhaps install them to /opt or /usr/local so they do no conflict with normal debs?

---

### Post by Bandit on 2011-08-07
It boils down to this, the well off and kids that dont pay for their internet connection here will give you BS answers all day as they cant see past their on nose. Those of us who have to look at the internet from financial perspective for schools and such who are having their budget cut or/and dont have internet access or is limited to dial up or low end DSL would really benefit from a on site (on campus) disc repository. 

Who ever mentioned, go with another distro. That is a lame answer and bad attitude to have and is over all counter productive to ever getting linux and Ubuntu to excel. Linux has always been about options, those who think we dont need more options shouldnt be allowed to even look at a linux distro as you act more like a diseases bringing it down, other then being helpful.

---

### Post by m4tic on 2011-08-07
> **Bandit said:**
> It boils down to this, the well off and kids that dont pay for their internet connection here will give you BS answers all day as they cant see past their on nose. Those of us who have to look at the internet from financial perspective for schools and such who are having their budget cut or/and dont have internet access or is limited to dial up or low end DSL would really benefit from a on site (on campus) disc repository. 

Who ever mentioned, go with another distro. That is a lame answer and bad attitude to have and is over all counter productive to ever getting linux and Ubuntu to excel. Linux has always been about options, those who think we dont need more options shouldnt be allowed to even look at a linux distro as you act more like a diseases bringing it down, other then being helpful.

+1, what you just said sums it up. I'm living with friends at a flat, before we moved together I was on ubuntu, tried converting them but it was hopeless, we don't have an internet connection besides our phones. We now have only windows on the computer, there are lots of internet cafes around us so getting software's easy for it. 

I want to put ubuntu on but what's the point. I'll be using it though when I get a laptop, 3g prices are getting cheaper now that I'll use my phone as a modem.

---

### Post by hakermania on 2011-08-07
I think the initial post is wrong. It correctly stated : "Who doesn't have internet nowadays?"
Well, even in Bangladesh I guess that in one or two years all people around will have internet connection with quite high speeds. So, why to spend so much time and effort for only two years?

---

### Post by aysiu on 2011-08-07
I proposed this 3.5 years ago on Brainstorm:
[Idea #142: Optional add-on CDs (not advertised heavily, but still available)](http://brainstorm.ubuntu.com/idea/142/) and it got voted down then. Eventually it got to positive votes, but only about 129 net positive ones.

This is the rationale I wrote up: > Not everyone has a broadband internet connection or any internet connection on Ubuntu. Sometimes they can download in Windows or get friends to burn CDs for them, but they don't have a direct connection to the repositories in Ubuntu. If Ubuntu is Linux for Human Beings, there should be a recognition of the lack of broadband internet in many places.

Yes, too many download options can confuse new users, but you don't have to advertise these add-on CDs. You just have to have them available somewhere. People will find them if they need them.

The DVDs contain Main and Restricted repositories, but not everyone has access to a DVD burner, and a lot of popular packages are in Universe. It's true a lot of popular packages are also in Multiverse, too, but I'm not sure if there are legal issues involved with distributing those on a CD. 

---

### Post by Bandit on 2011-08-07
> **aysiu said:**
> I proposed this 3.5 years ago on Brainstorm:
[Idea #142: Optional add-on CDs (not advertised heavily, but still available)](http://brainstorm.ubuntu.com/idea/142/) and it got voted down then. Eventually it got to positive votes, but only about 129 net positive ones.

This is the rationale I wrote up:

I think I remember that. 

Most distros still do this with box sets and I dont see why so many are against it. It doesnt take away from anyone and wouldnt make Ubuntu any less great. If anything, if some colleges or Universities ordered the CD/DVD set of the repositories, it would save Canonical money in bandwidth charges.. If I didnt have broadband, I would jump at the idea of getting 5 or 6 DVDs of the repositories for around $25-$30USD.

---

### Post by Thewhistlingwind on 2011-08-07
> **Bandit said:**
> It boils down to this, the well off and kids that dont pay for their internet connection here will give you BS answers all day as they cant see past their on nose. Those of us who have to look at the internet from financial perspective for schools and such who are having their budget cut or/and dont have internet access or is limited to dial up or low end DSL would really benefit from a on site (on campus) disc repository. 

Who ever mentioned, go with another distro. That is a lame answer and bad attitude to have and is over all counter productive to ever getting linux and Ubuntu to excel. Linux has always been about options, those who think we dont need more options shouldnt be allowed to even look at a linux distro as you act more like a diseases bringing it down, other then being helpful.

So, you just indirectly accused me of quite a bit. Including but not limited to: Snobbery, Rigidity, Incompetence, being poisonous, short sightedness, inexperience, AND said I am unworthy of using a Linux distro. I believe my answer was well within the bounds of reason, Debian has a system for this, Ubuntu does not, thus a valid solution is to use Debian. (Though not necessarily the ideal one.)

Ignoring all that:

> **NightwishFan said:**
> I think all the bases have been covered already.

Solutions?
1. Put the repository on DVDs available for purchase at a low price  similar to Debian. (Also for download but purchase is probably better in  places with poor internet). Downsides: Have to purchase/download which  takes time. Not very flexible to adding more software in the future,  probably best to mainly distribute these with LTS releases.

2. Create monolithic debs for specific programs. Downsides: Harder to  build and maintain, messy. Perhaps install them to /opt or /usr/local so  they do no conflict with normal debs?

These are the only options I see as well. Unless we have a format for distributing groups of .debs that are all installed as separate packages but from one installer.

And trust me, I've tried using Linux without internet, the effort required to install software is incredible.

---

### Post by Bandit on 2011-08-07
> **Thewhistlingwind said:**
> So, you just indirectly accused me of quite a bit. Including but not limited to: Snobbery, Rigidity, Incompetence, being poisonous, short sightedness, inexperience, AND said I am unworthy of using a Linux distro.

I..............


Just wanted to point out I didnt call any names or say anything like you posted..

---

### Post by Thewhistlingwind on 2011-08-07
> **Bandit said:**
> Just wanted to point out I didnt call any names or say anything like you posted..

Indirectly is a key word there.

---

### Post by Bandit on 2011-08-07
> **Thewhistlingwind said:**
> Indirectly is a key word there.

Indirectly can assume a plethora of misleading points or assumptions. Please dont put words in peoples mouths per se. ;-)

EDIT:
I would like to point out that everyone on this forum that uses Ubuntu is even if you dont want to be, is an ambassador of this fine distro. Also if we were salesmen at a GM car lot and someone came up to you and said they are looking for a car with ___ options. You wouldn't say, you need to look at a Ford then. That would get you fired as it is counter productive to send business away. Being that we are all ambassadors we should all be selling Ubuntu, not sending people to Debian, nothing wrong with Debian as its one of the best also, but the point remains.

---

### Post by Drenriza on 2011-08-07
So i read the majority of #1 and several posts. And i think the question should be "how can the inhabitants of a country get internet to their home" instead of "how can we get online material onto a portable deice to offline users"

It is very possible to get internet out to VERY remote parts of the world, with very primitive tools, by using old hardware. I read somewhere that people in some countries used barb wire to carry an electrical signal. And they reached speeds above 100KBps, above 10miles. And then the signal needed to be repeated, to prevent data loss. Along with other means of signal transfer of course. But one WAN sending unit is below 400$ along with a guide to create one if i am not mistaken.

The article is here, it is in danish, but i would believe google translate can translate a lot of it to make sense. unfortunately i don't have time right here right now to translate it. If i get the time i do so ,) Since its brilliant!
[http://ing.dk/artikel/120702-hjemmestrikket-traadloest-internet-breder-sig-i-fattige-lande](http://ing.dk/artikel/120702-hjemmestrikket-traadloest-internet-breder-sig-i-fattige-lande)

Think about it :D

---

### Post by forrestcupp on 2011-08-07
Every time you install something from the repositories, it downloads the debs and saves them on your hard drive, right? I wonder how hard it would be to set up a USB Ubuntu install where you could take the memory stick to a computer with broadband, boot to USB, install something from the repos, then just copy all the debs to your real Ubuntu install and run the deb file to install it. If that could work, then surely it wouldn't be hard to come up with an easy to use GUI that would copy the debs from your memory stick to the correct location and even let you run one to install it.

---

### Post by aysiu on 2011-08-07
> **forrestcupp said:**
> Every time you install something from the repositories, it downloads the debs and saves them on your hard drive, right? I wonder how hard it would be to set up a USB Ubuntu install where you could take the memory stick to a computer with broadband, boot to USB, install something from the repos, then just copy all the debs to your real Ubuntu install and run the deb file to install it. If that could work, then surely it wouldn't be hard to come up with an easy to use GUI that would copy the debs from your memory stick to the correct location and even let you run one to install it.
What you're describing is not that hard, but it's also not as simple as apps for Mac OS X and Windows.

The method you're describing involves these steps: [list=1]
[*]Find a Ubuntu computer that doesn't already have installed **both** the to-be-installed software *and* its needs-to-be-installed-on-a-fresh-installation dependencies.

[*]Clear out the cache of other installed software, so you aren't copying over extraneous .deb files.

[*]Actually install the to-be-installed software.

[*]Go to an obscure directory (/var/cache/apt/archives) and copy the .deb files to a USB stick or burn them to CD.[/list]

The method for Windows and Mac OS X:
[list=1]
[*] Go to the site that hosts the software to be installed and download the .exe or .dmg file.

[*]Copy the file to USB or burn it to CD.[/list]

See the difference?

---

### Post by beew on 2011-08-07
Maybe something like this would help? [http://portablelinuxapps.org/](http://portablelinuxapps.org/)

Unfortunately it seems to have discontinued as I haven't seen any update for quite a long time. But when it worked (it said tested for 10.04 but everything works in 10.10 and most are broken in 11.04) it was quite easy. No installation, just download to a usb and copy to your main Ubuntu install (which has no internet ) and click and it would work.

---

### Post by NightwishFan on 2011-08-07
The 'find a computer with broadband' route is made simple if you use aptoncd. I think you could also use this to make upgrade cds.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Package is in Ubuntu and Debian, so it is probably in Mint/Mepis/Zenix as well.

---

### Post by NightwishFan on 2011-08-07
Here are some utilities that also seem useful offline:

[LIST]
[*]apt-mirror: A small and efficient tool that lets you mirror a part of or the whole Debian GNU/Linux distribution or any other apt sources.
[*]apt-move: apt-move is used to move a collection of Debian package files into a proper archive hierarchy as is used in the official Debian archive.
[*]apt-cacher: Apt-cacher performs caching of .deb and source packages which have been downloaded by local users. It is most useful for local area networks with slow internet uplink.
[*]apt-offline: apt-offline can fully update and upgrade an APT based distribution without connecting to the network, all of it transparent to apt.
[*]apt-p2p: Apt-P2P is a helper for downloading Debian packages files with APT. It will download any needed files from other Apt-P2P peers in a peer-to-peer manner, and so reduce the strain on the Debian mirrors.
[*]debtorrent: Another bittorrent proxy for downloading Debian packages.
[*]aptlinex: (not so useful offline but interesting) This addon allows installing Debian packages from iceweasel, firefox, galeon or konqueror just clicking on a web link.
[/LIST]

**Edit, More about apt-offline:**
apt-offline can be used to generate a signature on a machine (with no network). This signature contains all download information required for the apt database system. This signature file can be used on another machine connected to the internet (which need not be a Debian box and can even be running windows) to download the updates. The downloaded data will contain all updates in a format understood by apt and this data can be used by apt-offline to update the non-networked machine.

apt-offline can also fetch bug reports and make them available offline

---

### Post by jwbrase on 2011-08-07
> **3rdalbum said:**
> It would be perfectly possible to make self-contained programs that are installable by dragging them to your home directory or /usr/applications folder. It's perfectly possible to make Windows-style installers. It's perfectly possible to do these on Linux for most programs.

Nobody wants to do them, and almost nobody would want to install from them.

They are too big. They introduce security flaws by using old libraries.

Exploitable from where, and to what end? A machine that's not connected to the network may not have the latest security updates, but it's also much less of a target: it's both less visible and less useful to anybody that might want to break into it.

---

### Post by beew on 2011-08-07
> **jwbrase said:**
> Exploitable from where, and to what end? A machine that's not connected to the network may not have the latest security updates, but it's also much less of a target: it's both less visible and less useful to anybody that might want to break into it.

That is true. It is the ultimate secure machine if you can't get online in the first place. :)

---

### Post by Thewhistlingwind on 2011-08-07
> **forrestcupp said:**
> Every time you install something from the repositories, it downloads the debs and saves them on your hard drive, right? I wonder how hard it would be to set up a USB Ubuntu install where you could take the memory stick to a computer with broadband, boot to USB, install something from the repos, then just copy all the debs to your real Ubuntu install and run the deb file to install it. If that could work, then surely it wouldn't be hard to come up with an easy to use GUI that would copy the debs from your memory stick to the correct location and even let you run one to install it.

Actually, that reminds me. While I'm using fedora and can't confirm it exactly right now.

I'm 99% sure theres an option you can give apt-get to not install packages pulled from the repos.

The problem, as I remember it, was that the packages were version specific and that you couldn't pull packages you'd already installed.

Maybe theres some sort of --force option?

What would really make that useful is a script that writes a script that installs all of the .debs in the right order.

So it'd be like a makeshift windows .exe

---

### Post by elliotn on 2011-08-07
to be honest I too was once pulled off by the dependancy hell, it still haunts me even today, compiling from source is worse....I think yes ubuntu/Linux as whole needs to stop this dependency thing....

---

### Post by del_diablo on 2011-08-07
Image it if Ubuntu package repos removed the entire "you need version X of lib" ********. Or added a "ignore and install" button.
Still remember having fun in a Debian using pinning combining stable, sid and experimental.

---

### Post by forrestcupp on 2011-08-07
> **aysiu said:**
> What you're describing is not that hard, but it's also not as simple as apps for Mac OS X and Windows.

The method you're describing involves these steps: [list=1]
[*]Find a Ubuntu computer that doesn't already have installed **both** the to-be-installed software *and* its needs-to-be-installed-on-a-fresh-installation dependencies.

[*]Clear out the cache of other installed software, so you aren't copying over extraneous .deb files.

[*]Actually install the to-be-installed software.

[*]Go to an obscure directory (/var/cache/apt/archives) and copy the .deb files to a USB stick or burn them to CD.[/list]

The method for Windows and Mac OS X:
[list=1]
[*] Go to the site that hosts the software to be installed and download the .exe or .dmg file.

[*]Copy the file to USB or burn it to CD.[/list]

See the difference?
I see the difference, but making things like Windows or Mac OS X is never going to happen in Linux.

But I think it would be a little bit easier than you're describing. Can't you set it up like a LiveCD, only on a USB stick so that everything is run from the USB stick that you boot from, with all the partitions being on the memory stick? If so, then the cache would be on the memory stick, and you could just sync whatever is installed on the memory stick with your own installation. If it's your personal memory stick that you are using only to install software to your computer, then you should never have an issue of whether something has already been installed or not.

If it's possible to set up a memory stick like that, then it shouldn't be too hard to create a GUI that could automate transferring debs and clearing the cache.

---

### Post by Timmer1240 on 2011-08-07
I thought it was easy?

---

### Post by Timmer1240 on 2011-08-07
Im using Mint Debian its a little harder here!

---

### Post by Thewhistlingwind on 2011-08-07
> **forrestcupp said:**
> 
If it's possible to set up a memory stick like that, then it shouldn't be too hard to create a GUI that could automate transferring debs and clearing the cache.

I thought the whole point here was to make a way to install one downloaded package onto a bunch of different computers.

Another option. (If you have the repos on disk.) for installs that are networked but not online. You can set up a local repository if memory serves and maintain software over LAN.

I still think the best option however; is something that emulates windows .exe's but still installs separate .debs.

@timmer, were talking about offline installs.

---

### Post by Bandit on 2011-08-07
I may be missing something. But you guys realize you should be able to use 
"dpkg --recursive -G -i *" to install all files from a USB, the -G option will prevent installing packages that are older or are the same version. You can get all your installed debs from var/cache/apt/archives. 
"apt-cache pkgnames" will list them for you.
Also "apt-get --download-only upgrade" will download updates for you to place on a separate disc for updating multiple machines. 
And of course this can all also be done over the lan from a file server as long as you have an accessible IP address..

---

### Post by maqtanim on 2011-08-08
Guys ... I think we've derailed the topic a bit. The original message was - "*Not every country has good internet facilities like the developed western world. Not every computer is not connected to the internet. And not every Ubuntu user is a geek. So a simple way to install softwares in offline computer is really a burning question for the offline-people.* *How can we help them by providing a simple and easy installation method like Windows and MacOSX?*"

Using aptoncd, apt-mirror, apt-move, apt-cacher, apt-offline, apt-p2p, debtorrent, aptlinex; Copying /var/cache/apt/archives to the offline computer; Setting up a local repository to serve softwares through LAN - but are those really 'easy' and 'simple' for a general computer user? No, not at all. They are not geek. Those are real hassle for them, and believe me they do not wish to do the hassle (everybody hates hassle ;) ). They need a 'simple' and 'easy' way. Not necessary that we need to follow Windows or MacOSX in every single steps. May be we could figure out a 'simpler' and 'easier' way. But we need to focus on the matter. When you are spreading Ubuntu in a third world under-developed country to fix the Bug#1, you will realize how much big bottleneck the 'offline software installation'!

---

### Post by Bandit on 2011-08-08
> **maqtanim said:**
> Guys ... I think we've derailed the topic a bit. The original message was .....................................

Yea true that. Not sure what else to do, Aysiu has had this posted in brainstorm for a long while. Prob best best is to keep voting it up and trying to get more people to vote on it. I did, but its a unfair vote many times because advanced users will be more prone to register while none advanced users get confused just trying to register.

Here is the link Aysiu posted. [http://brainstorm.ubuntu.com/ideatorrent/idea/142](http://brainstorm.ubuntu.com/ideatorrent/idea/142)

[I]
**Now need to add a brainstorm idea that it and forum logins need to share same login to get better feedback for brainstorm.**[/I]

---

### Post by forrestcupp on 2011-08-08
> **maqtanim said:**
> Guys ... I think we've derailed the topic a bit. The original message was - "*Not every country has good internet facilities like the developed western world. Not every computer is not connected to the internet. And not every Ubuntu user is a geek. So a simple way to install softwares in offline computer is really a burning question for the offline-people.* *How can we help them by providing a simple and easy installation method like Windows and MacOSX?*"

Using aptoncd, apt-mirror, apt-move, apt-cacher, apt-offline, apt-p2p, debtorrent, aptlinex; Copying /var/cache/apt/archives to the offline computer; Setting up a local repository to serve softwares through LAN - but are those really 'easy' and 'simple' for a general computer user? No, not at all. They are not geek. Those are real hassle for them, and believe me they do not wish to do the hassle (everybody hates hassle ;) ). They need a 'simple' and 'easy' way. Not necessary that we need to follow Windows or MacOSX in every single steps. May be we could figure out a 'simpler' and 'easier' way. But we need to focus on the matter. When you are spreading Ubuntu in a third world under-developed country to fix the Bug#1, you will realize how much big bottleneck the 'offline software installation'!

That's why I was trying to think of a way it can be done and then suggest a GUI to automate it all so that it *would* be easy. The problem with my solution was that it would be hard to install things on multiple computers.

The honest truth is that it will never be as easy as Windows to install things offline. The Linux world works differently, and they are set in their ways. Creating all-in-one installer files has been suggested for many years, and all along, everyone has said "we don't want to be like Windows." The problem is with how dependencies are handled. With Windows, every program is either going to use dll's that are already installed in the system, or they will include all of the dll's necessary in the installation. It's very rare that a Windows program will depend on other software that needs to be installed. The main times you see that are with software that was originally created for Linux and ported, or with .Net stuff. Since .Net is installed by default on the latest versions of Windows, you don't even really have to worry about that. Linux, on the other hand, has thousands of different non-default libraries that can be depended on. It's just a mess. Everyone cares more about choice than standards.

So, if you don't have the internet, I'm afraid your best bet is always going to be either using Windows, or trying to make what we have available as easy as possible, which will always require more tech effort than Windows or Mac.

---

### Post by 3rdalbum on 2011-08-08
> **maqtanim said:**
> Guys ... I think we've derailed the topic a bit. The original message was - "*Not every country has good internet facilities like the developed western world. Not every computer is not connected to the internet. And not every Ubuntu user is a geek. So a simple way to install softwares in offline computer is really a burning question for the offline-people.* *How can we help them by providing a simple and easy installation method like Windows and MacOSX?*"

Maybe the actual answer should be "Let's help people in these countries to get internet access, which will bring them more benefits than merely being able to install software on Ubuntu".

---

### Post by 3rdalbum on 2011-08-08
> **jwbrase said:**
> Exploitable from where, and to what end? A machine that's not connected to the network may not have the latest security updates, but it's also much less of a target: it's both less visible and less useful to anybody that might want to break into it.

Yes, but online users would get roped into using these offline installers too. Who wants to package things twice?

---

### Post by 3rdalbum on 2011-08-08
> **Bapun007 said:**
> what about the pbi packages of pcbsd ! Is it similar to windows .exe programs .

Windows ".exe programs" are programs. PBI packages are packages.

PBIs can only install software. EXEs are executable code that gets run. Some of them have code that installs other programs. But all EXEs are programs in their own right.

You probably mean that PBIs are like MSIs.

---

### Post by NightwishFan on 2011-08-08
There are all in one installers. I have used them for planeshift, google earth etc.

---

### Post by Thewhistlingwind on 2011-08-08
> **3rdalbum said:**
> Windows ".exe programs" are programs. PBI packages are packages.

PBIs can only install software. EXEs are executable code that gets run. Some of them have code that installs other programs. But all EXEs are programs in their own right.

You probably mean that PBIs are like MSIs.

Thank you for this correction.

.pbi actually, was just what I was looking for.

It appears to be a system that satisfies my requirements:

1. It automates and makes the task of installing software *easy *even offline.

2. It installs programs as separate packages, stopping issues with outdated libraries that the user can't maintain.

3. It doesn't require too much effort to obtain. 

Does any similar system exist for a Linux distribution?

---

### Post by forrestcupp on 2011-08-08
> **NightwishFan said:**
> There are all in one installers. I have used them for planeshift, google earth etc.

Those are great, but the only downside is that they install everything in your /home directory instead of making use of your file hierarchy. Since there are a hundred different file hierarchies out there and no one is willing to make a real standard, that can't really happen.

They're still good for some things, though.

---

### Post by NightwishFan on 2011-08-08
> **forrestcupp said:**
> Those are great, but the only downside is that they install everything in your /home directory instead of making use of your file hierarchy. Since there are a hundred different file hierarchies out there and no one is willing to make a real standard, that can't really happen.

They're still good for some things, though.

Well there is the LSB and LFH.

[https://secure.wikimedia.org/wikipedia/en/wiki/Linux_Standard_Base](https://secure.wikimedia.org/wikipedia/en/wiki/Linux_Standard_Base)
[https://secure.wikimedia.org/wikipedia/en/wiki/Filesystem_Hierarchy_Standard](https://secure.wikimedia.org/wikipedia/en/wiki/Filesystem_Hierarchy_Standard)
[http://wiki.debian.org/DebianLsb](http://wiki.debian.org/DebianLsb)

---

### Post by forrestcupp on 2011-08-08
> **NightwishFan said:**
> Well there is the LSB and LFH.

[https://secure.wikimedia.org/wikipedia/en/wiki/Linux_Standard_Base](https://secure.wikimedia.org/wikipedia/en/wiki/Linux_Standard_Base)
[https://secure.wikimedia.org/wikipedia/en/wiki/Filesystem_Hierarchy_Standard](https://secure.wikimedia.org/wikipedia/en/wiki/Filesystem_Hierarchy_Standard)
[http://wiki.debian.org/DebianLsb](http://wiki.debian.org/DebianLsb)

When I typed my post, I was actually thinking that it's a shame the the LSB and LFH doesn't change the fact that every distro out there implements its own file hierarchy.

---

### Post by NightwishFan on 2011-08-08
Yeah. I know the distro I use tries to be (mostly) compatible with it. For me that is good enough but you are quite correct.

---

### Post by Bandit on 2011-08-08
> **forrestcupp said:**
> When I typed my post, I was actually thinking that it's a shame the the LSB and LFH doesn't change the fact that every distro out there implements its own file hierarchy.

You made me think of SuSE devs, being they are one of the worse..
They put all installed applications into /opt and still put all the desktop gui stuff in /usr/local/(bin,lib,share). Which drives me nutz because I like to use the Standard Base for /opt being for optional 3rd party stuff like Firefox and /usr/local/(bin,lib,share) being for user compiled applications and /usr/(bin,lib,share) being for packaged files. Thank you Ubuntu for sticking close to this.

---

### Post by NightwishFan on 2011-08-08
Yes from what I know in Debian opt/ is always empty and /usr/local contains a basic root like folder structure.

I think /opt was used for the Kubuntu KDE4 remix back in the day. Not sure if Debian just upgraded into it while it was in Sid or not.

---

### Post by Bandit on 2011-08-08
> **NightwishFan said:**
> Yes from what I know in Debian opt/ is always empty and /usr/local contains a basic root like folder structure.

I think /opt was used for the Kubuntu KDE4 remix back in the day. Not sure if Debian just upgraded into it while it was in Sid or not.

Since I got the latest firefox and google earth. They are installed to those directories. /opt is more like Windows /programs folders were programs that contain a mix of binary and library files, which is common in linux 3rd party programs.

---

