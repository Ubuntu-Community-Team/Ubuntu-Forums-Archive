---
title: "What if Linux was the only OS in existence?"
date: 2014-03-31
forum: The Cafe
---

### Post by Kyle_Undercofler on 2014-03-31
That is the question. What if there was no Microsoft Windows, and no Mac OS? What if there was only Linux? I think it would be amazing because Linux gamers would never have to worry about OS incompatiblities! It would also kind of suck though, because it would get ALOT more viruses. After all, the reason Linux gets so few viruses is because more people use Windows and Mac OS.

---

### Post by buzzingrobot on 2014-03-31
A very few distributions would quickly dominate, as they do now, probably those with the best relationships with hardware makers and, hence, the best driver support.

That trend would be supported by the readiness of hardware and peripheral vendors to support only the dominant distributions.

We might see more proprietary vendors release open source. But, that might be coupled with fee- or subscription-only access to binaries and updates.

---

### Post by Allavona on 2014-03-31
Oh yes, you can bet everything you love that we would be paying for it.

---

### Post by forcecore on 2014-03-31
As sidenote: then we would have lot of portable software too like windows has currently.

---

### Post by Old_Grey_Wolf on 2014-03-31
Without Microsoft and Apple I question whether most people would have the option to have a home computer. They made home computers affordable and available for many non-tech people.

---

### Post by buzzingrobot on 2014-03-31
> **Allavona said:**
> Oh yes, you can bet everything you love that we would be paying for it.

"Paying for it" is fully in compliance with FOSS licenses and requirement.  FOSS is about providing source code, not about giving things away.

---

### Post by buzzingrobot on 2014-03-31
> **forcecore said:**
> As sidenote: then we would have lot of portable software too like windows has currently.

Windows software only runs on Windows.  How is that portable??

---

### Post by forcecore on 2014-03-31
> **buzzingrobot said:**
> Windows software only runs on Windows.  How is that portable??

I mean that we would have lot of native Linux software that requires no installation and saves settings in own folder. In this case dominant desktop and libraries are needed. Currently we have hope with Ubuntu to become major distro. Lot of people like portable software concept to easily test and use new software from usb stick or from another drive or do not want pollute system.

---

### Post by buzzingrobot on 2014-03-31
> **forcecore said:**
> I mean that we would have lot of native Linux software that requires no installation and saves settings in own folder. In this case dominant desktop and libraries are needed. Currently we have hope with Ubuntu to become major distro. Lot of people like portable software concept to easily test and use new software from usb stick or from another drive or do not want pollute system.

Software that is not installed cannot be used.

The Linux file system is based on shared libraries:  The first app that requires Library X pulls it in as a dependency.  Any other app installed subsequently that requires Library X uses the one that's already installed. 

 To move to a system that sees individual applications using libraries inside application-specific folder would require a wholesale redesign and rewrite of Linux, as well as inviting the maintenance and security faults this approach brings with it. (You become dependent on each app maintainer to update the libraries under its control, even if they are identical to libraries someone else has updated.)

Storing settings inside application-controlled directories seems to offer no advantage over the current approach of storing them in each user's home directory.  How would the OS distinguish between settings for User A and User B? I'm sure a way could be devised, but to what advantage?

Ubuntu, like every other Linux distribution, is primarily a packager of software developed elsewhere.  Any fundamental change in how Linux is structured and implemented requires concurrence by thousands of developers who are not exactly likely to take orders.

Binary portability between operating systems can't really work.

---

### Post by forcecore on 2014-04-01
I have seen lot of software that loads libraries from own folder and there have been some portable software too. I have seen so much simple people who wants to download software and just run it. I have saved some from abandoning Ubuntu(or any distro) that i show that there is still hope for extract and run software, i have a script that can save settings and load libraries from own folder. Sometimes i need run software from another drive too.

Portable software mus be, i know distro must be specific but still target a major distro like Ubuntu and ok.

---

### Post by 23dornot23d on 2014-04-01
@ forcecore ...... I totally agree with what you are getting at here and that would make Linux Number 1 ........... bye bye Windows.

( Blender 2.69 is a great example - I can download their package into very old systems - unpack it and it just runs ) 

if only all packages were like this one - then Linux would take a hold of the market to such an extent - it may become the main one.

---

### Post by leivalabidas on 2014-04-01
> **buzzingrobot said:**
> Software that is not installed cannot be used.

The Linux file system is based on shared libraries:  The first app that requires Library X pulls it in as a dependency.  Any other app installed subsequently that requires Library X uses the one that's already installed. 

 To move to a system that sees individual applications using libraries inside application-specific folder would require a wholesale redesign and rewrite of Linux, as well as inviting the maintenance and security faults this approach brings with it. (You become dependent on each app maintainer to update the libraries under its control, even if they are identical to libraries someone else has updated.)

Storing settings inside application-controlled directories seems to offer no advantage over the current approach of storing them in each user's home directory.  How would the OS distinguish between settings for User A and User B? I'm sure a way could be devised, but to what advantage?

Ubuntu, like every other Linux distribution, is primarily a packager of software developed elsewhere.  Any fundamental change in how Linux is structured and implemented requires concurrence by thousands of developers who are not exactly likely to take orders.

Binary portability between operating systems can't really work.


If you want to install so badly, then buy a 2 terabyte harddisk and install every package from package manager ONE BY ONE.

---

### Post by 23dornot23d on 2014-04-01
> 
                     [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **buzzingrobot**                     [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12973650#post12973650")                 
                 Software that is not installed cannot be used.



I am not so sure that statement is TRUE ............... 

I can point to a package - " Blender 2,69 " and just run it ........ but I did not install it in the current system as it sits in a folder on another drive.

The only thing that I usually need to be sure of - is whether I am running 32 bit or 64 bit .

Would really like to see a list of packages that will run without a proper install into the current running system .... that would be heading towards

a full cloud based system of running programs from anywhere - I guess ...........

---

### Post by buzzingrobot on 2014-04-01
One key strength of a Linux distribution like Ubuntu (and others) is that its repositories contain packages that have been audited. 

One key weakness of Windows is that its users are encouraged to download software of unknown quality and safety from unknown sources.

Windows' ".exe" installation packages are the rough, lesser, equivalent of ".deb" packages In Linux.  They contain necessary files, etc., and a script to place the files in the correct location in the filesystem. In Windows, that is often in the same directory as the one created to host the actual application binary.  In Linux, those supporting files are placed in standardized locations in the filesystem.  This prevents the repeated installation of identical files and dramatically reduces maintenance and security concerns.

As far as I recall, Windows has no automatic dependency resolution capability.  Unless a software vendor is sure *all* the dependencies required for a program will be on *all* Windows machines, that vendor has not choice but to include those dependencies in the installation package. Multiple copies of those dependencies might already exist on any given Windows machine. 

In Linux, the tar achive (????.tar.gz) is a direct analogy of zip files in Windows, in that both are simply compressed collections of files, and not intended as automated installation tools.

Many tens of thousands of packages are available as .debs for easy installation in Ubuntu.

---

### Post by buzzingrobot on 2014-04-01
> **23dornot23d said:**
> I am not so sure that statement is TRUE ............... 

I can point to a package - " Blender 2,69 " and just run it ........ but I did not install it in the current system as it sits in a folder on another drive.

..

Of course, you installed it.  Even if it's just one single binary, you had to copy it from someplace to storage accessible by your system.  That's installation.

You can run apps over the web or over a local network, but that's the same thing:  The app is installed on storage accessible by your system.

---

### Post by buzzingrobot on 2014-04-01
> **leivalabidas said:**
> If you want to install so badly, then buy a 2 terabyte harddisk and install every package from package manager ONE BY ONE.

I'm not sure what that means.

Are you arguing software can be used in Windows without installation?

I install software in Ubuntu with one click.  Is a zero-click method available in Windows?

---

### Post by 23dornot23d on 2014-04-01
> **buzzingrobot said:**
> Of course, you installed it.  Even if it's just one single binary, you had to copy it from someplace to storage accessible by your system.  That's installation.

You can run apps over the web or over a local network, but that's the same thing:  The app is installed on storage accessible by your system.


You also said this ......... but if you just unzip something into a folder are you saying that - its the same thing as a .deb that puts things in specific places over the drive 
structure .......


> 
In Linux, the tar achive (????.tar.gz) is a direct analogy of zip files  in Windows, in that both are simply compressed collections of files, and  not intended as automated installation tools.



What I was trying to get to was that you can run Blender by unzipping it into a folder .......... on a older system where it was not installed to ....... and the relative libraries and pointers do not exist. ( we could get into a discussion about zip tar and uncompressing files ....... but its only a complete installation if it affects the operating system
that it is going into - by incorporating itself in a maze or web of connections in that operating system )

Unzipping into a directory // is so much simpler and does not inflict any damage or problems into older systems through having to upgrade libraries or programs that
some of your other older software relies on as dependencies.

The thread is good as it raises the issue ........... if Linux had got the market of supplying software in packages on disk that did not destroy or alter the users OS in such a way that it makes it difficult to remove and add new programs without in some way taking a risk that it may in fact effect the older programs already installed on said system.

Un-zipping into a folder was not what I consider a installation as such ......... as I can easily remove said folder and the program is gone ..........

With a debian gdebi / package manager install ........ only the package manager can uninstall it safely .........

This is where Linux may have got a better hold on the market place ....... 

```


The fact that a TRUE / PROPER install ........ 

Could not be done without people having to keep upgrading perfectly good systems all the time to get the latest software to run.


```

That is probably the one thing that kills user systems off ...... leaving them wondering ...... why did I upgrade ..... or why when my graphics / network / sound worked
alright before the install ......... does it not work now.

Its because parts of the system get upgraded that affect other installed packages ...... in such a way that the install will ask you to remove things or lead you into a
dependency hell .........

Unzipping into one directory is not a full install and does not lead to those problems stated above.

My own thoughts are that Blender has done a great job ...... and if only Wings3d could do a similar one - then every 6 months I would not have to go through

similar convoluted methods of getting things working on my own systems that I know work perfectly well , that was before any upgrade or installation of new software

that often is tied back to older ways of running ........

That is why Cinepaint will not install ...... that is why Gnofract4d, K3dsurf etc will only install with lots of messing around ...... it is also why as Ubuntu constantly changes it will constantly lose more and more packages that were made to run on the older versions.

Not because the programs themselves are bad - its because they cannot install without a package of older libraries sitting below them.

I would like to see Linux take a step towards solving the problem of how to package programs - like Blender has done - 

So they the programs are not so dependent or interwoven - in such a way that they start to destroy your system when either installing or removing said software

using one of the many package managers available now ....... and all working in slightly different ways ....... (some work better than others in this task).

........ if just unzipped into a single folder ( this to me is not what I class as a full installation ) and can be easily removed without really affecting the OS.

---

### Post by buzzingrobot on 2014-04-01
If you prefer a system that lacks automated dependency resolution, lacks a package manager, and permits unknown software of untested safety from unknown sources to have full access to your system, and also leaves you responsible for locating and installing dependencies it fails to include, as well as making you dependent on multiple vendors for security updates to identical software strewn in multiple locations across your system, then Windows is for you.

Linux uses a different approach, which, among other advantages, greatly reduces the bloat and security risk inherent in the Windows approach to software installation.  This approach is reliable if the user takes the time to understand it.  If the user tries to subvert that approach by imposing hazardous Windows habits and techniques on it, then the user is doing it wrong and should expect things to break.

(Blender is in Ubuntu's repos.  Why get it from another source?)

---

### Post by forcecore on 2014-04-01
> **buzzingrobot said:**
> If you prefer a system that lacks automated dependency resolution, lacks a package manager, and permits unknown software of untested safety from unknown sources to have full access to your system, and also leaves you responsible for locating and installing dependencies it fails to include, as well as making you dependent on multiple vendors for security updates to identical software strewn in multiple locations across your system, then Windows is for you.

No i really like that system core is well controlled and safe, i just say that there should be more software by 3rd party if major upgrade comes then i can use or test new version without install or carry specific version with me including settings. Portable software do not need system password too for install and can be even used in guest account on someone computer.

---

### Post by QDR06VV9 on 2014-04-01
> **Old_Grey_Wolf said:**
> Without Microsoft and Apple I question whether most people would have the option to have a home computer. They made home computers affordable and available for many non-tech people.

+1 Sadly True;)

---

### Post by 23dornot23d on 2014-04-01
> 
(Blender is in Ubuntu's repos.  Why get it from another source?)                 


Blender 2.7 running when latest in repos is 2.68a

[IMG]http://i.minus.com/inOnizRTsduwk.jpg[/IMG]

I Download it from the Blender site because in 10.10 you cannot run the latest version of Blender from the repository also 11.04 also 11.10 and even just 2 year old distros 
the latest version of Blender that you can run is 2.63 * ( clarify here - talking about versions over 2 years old )  from the repository unless of course you add a ppa ....... which again defeats the object of security.

or as I said earlier - you can upgrade your systems and lose a lot of what you were brought up with and are familiar with ........... 

I do not see what is a worse security risk than having to add ppa's which can mean that you download something from some unknown sources.

___________________________________________________________

Adding a folder from the site of the people that produce it should not compromise the system as you can still keep control of that folder - also it can be better as only one copy sits on a drive ........

When you have a number of Ubuntu installs all at different versions ...........


You can just access the one setup of Blender - and it retains all the settings you need for each system ( 10.10 through to 14.04 ) you run ........

I think the advantage of doing it this way is better than having numerous installs and numerous setups on each version - which was how I used

to have to work.


If Linux was the only system on the Net ......... then I think it would charge for packages and they would work 99 % of the time on any of the versions

even Windows had a little backward compatibility .......... not that I know a lot about Windows as its main problems come from installing things without

even giving the user a clue as to what they are or what they might be doing.


To make it so Linux is the only good system - means a little change ......... but not to really compromise security - but to allow some easy backward compatibility

and also allow the running of one piece of software from many computers with different versions of Ubuntu on them ..........

The core system does not get compromised if the main things are protected ( Networks and Downloads are the greatest threat - so why download so many times

and so many different packages when the source of the problems to do with breakage and to do with possible intrusions will come from outside sources )

My older systems rarely ever touch the Net - but I can still run the Software that I need on them .......... just from a portable  USB drive.

The installation may have been done on another computer - but the package I know will still run on my older systems.

There are always better ways of doing things ....... but its not through not doing anything at all - but it is done by using methods that we already

have in place ........... its not a security risk . 

( It actually works out better for the users with multiple versions of Ubuntu - as only one version is used therefore only one download )

I believe Ubuntu could become the major player it wants to be .... but not by continuing along the same path with packages ....

If Linux was the only player in the market - it still has problems that need solving to make it better ......... one of them is getting a single program onto

a usb drive - that can be taken to another computer and run without having to do any more installing ............... 

( This is how I work between two of my systems ..... the other system does not see the Net - so less of a security risk ........ )



Think of Methods to become Number one ..... and reduce the number of un-needed downloads too ....... download once and use on many systems even different versions

of the same system.

Maybe that way the dinosaurs that do go out of existence - will leave Linux as the remaining OS in existence for Desktops and laptops ..........

---

### Post by monkeybrain20122 on 2014-04-01
There are many programs that don't require installing to work (unzip/untar and click binary, that's it)E.gs, blender, eclipse, sage, scilab.. they are statically linked to their own libraries.If you download Firefox from Mozilla, it doesn't require installation (that is what I did in Debian as I couldn't get rid of iceweasal)  

This approach has pros and cons. It offers a lot of flexibility to use newer software (or to have multiple versions of same software) without worrying about dependencies, and if something is working you don't have to worry about the next update messing it up (the flip side is you can't also expect bug fixes if it is not working) On the other hand, if every program is like that there will be a lot of duplication of libraries, that's why comparing to Linux, Windows install is huge. I install all kinds of stuffs in my system and my / partition comes to less than 10Gs. There is no way to do this with Windows. 

The way that Linux organizes application  files into bin, lib etc is vary efficient and makes a lot of sense (a point that new users from Windows often get confused about when they look for program folders for individual applications like in Windows), but this tight integration also comes at a cost of less flexibility. So the trade off would probably depends on factors like how tightly integrate a given application should be with the system and how up to date users would expect. For example, something like vlc should be kept up to date without having to upgrade the whole OS (and it likely will become old by the time ubuntu-next releases) The current version of vlc probably wouldn't even compile in 12.04 even if you don't mind the troubles.

---

### Post by 23dornot23d on 2014-04-02
> 
If you download Firefox from Mozilla, it doesn't require installation  (that is what I did in Debian as I couldn't get rid of iceweasal)  



This is something that I had to do as of late because people are more used to Firefox than Iceweasel ........

> 
This approach has pros and cons. It offers a lot of flexibility to use  newer software (or to have multiple versions of same software) without  worrying about dependencies, and if something is working you don't have  to worry about the next update messing it up (the flip side is you can't  also expect bug fixes if it is not working) On the other hand, if every  program is like that there will be a lot of duplication of libraries,  that's why comparing to Linux, Windows install is huge. I install all  kinds of stuffs in my system and my / partition comes to less than 10Gs.  There is no way to do this with Windows. 



Yes if space was a problem ..... but nowadays its not so much a problem on the large hard drives and USB drives ....... even the SSD camera cards 32 gig are easily
large enough for most Ubuntu installs with plenty of useful software on them.


> 
The way that Linux organizes application  files into bin, lib etc is  vary efficient and makes a lot of sense (a point that new users from  Windows often get confused about when they look for program folders for  individual applications like in Windows), but this tight integration  also comes at a cost of less flexibility. 


Totally agree ....... often see the same questions arise from Windows users ........ and its the first thing they tend to look for ........ where is the program folder.

I do like the idea of efficient and tightly integrated .......... but the cost of flexibility need not be a problem nowadays - as you say there are a few programs that
can be taken as complete units and unzipped rather than installed.

I wonder if it is what held back Linux from being the number 1 system though ...... or that it was for FREE and people tend not to trust people so much when they are given
things for FREE ........ thinking that there must be some catch or something.

When I first set about using Linux many moons ago it was to see / investigate what was available and at the time it opened up a whole realm of computing that I was looking for ...... think the chaos reigns 3d animations on a "Hot Sound and Vision CD" got me really interested back then ( plasma and 3d effects that we rarely see now ).

If there was only one ...... and it was Linux ........ do you think people would go buy CD's if say Blender / Firefox / Eclipse made them specifically to target rich people that
would rather just unzip something and get on with a task ........... rather than having to go through a install procedure that could render other things useless in the process.

Reason I ask is the old reason that the mouse and point and click was brought into play .......... because managers / people who think they are really clever - need to show
they can do things without appearing to make fools of themselves in process's that get awkward ........ like installing something and finding dependencies stop them in 
their tracks ........ as they have to know what they can and cannot upgrade or remove that will not kill their systems off.

Its really time for Linux to take hold of this market ...... especially now that Windows have stopped support for its main desktop / laptop system XP

This seems to have been done to grab more money from people that have already paid for a system they will never own and almost force them into going to the next version but at a cost  ....... where with Linux we can get into the code - still the same price - learn things from it ....... and then if we feel good enough .... start altering things to our own specifications to do tasks we think need adding .

I remember back to the first Linux system I bought - buying Linux Mandrake 7.1 a boxed set of floppies  with a proper manual .... something about doing that - which made it  seem at the time as if Linux had made it ..... changed its name to  Mandriva and now Mageia ....... nostalgia trip .

I wonder what would have made Linux the one that is 95 % used by people ....... maybe Mark Shuttleworth is showing us with the phones ...... 
[http://www.cnet.com/news/first-ubuntu-phones-go-on-sale-in-fall-mark-shuttleworth-reveals/](http://www.cnet.com/news/first-ubuntu-phones-go-on-sale-in-fall-mark-shuttleworth-reveals/)

you have to put a price on something and have to deliver what people really want ........ which is not necessarily what they need to do a job but if it costs a lot - then it must be good !!!

---

### Post by monkeybrain20122 on 2014-04-02
Tight integration offers a lot of flexibility at the system level. So there are trade offs. 

Personally I much prefer the Linux way, with a few exceptions when I want the flexibility for new features. I downloaded standalone blender and a few other applications. I also use ppas and compile my own. ppa is still 'the Linux way' in this discussion as the libraries are installed system wide and used by all applications, compiling would depends on whether the components are installed locally or in the file system, and whether compiled as static or shared ..

Speaking of Windows let's put things in perspective. It is not true that Windows users always get the latest and greatest,--or they even care about it. Many people I know on Windows are using very out of date software (starting with the OS--XP). It may come as a surprise but many Windows users don't know how to install software, so they keep whatever they had when the OS was set up for them. Not having the repository mechanism they never get updated (except may be AV, because there is enough nagging if they don't). It doesn't bother these users that their applications are outdated, as long as music plays, videos run and they can get on the internet they are happy. Then there are people who use expensive or pirated proprietary software, e.g Photoshop. It costs money to upgrade if they are paying customers, and if they download from torrent the latest versions are not always available. That means again they end up using old versions (all my brother's software is pirated and extremely out of date)

So in the end I don't think this is a deal breaker for linux gaining popularity. Many Windows users are not picky about software and computers, they use Windows because it is a packaged deal. let's not project out geek mindsets on them. :)

---

### Post by 23dornot23d on 2014-04-02
Its a lot of little things that all add up to making something the best ........

Price
Quality
Reliability

You would think Linux should win hands down any way here ....... 

Price Free ...... 
Quality - Good to Very good on programs like Blender and Firefox that are widely used
Reliability .......

Think that is where you have hit the nail on the head ......... reliability ......... people in Windows sometimes stick with initially installed software for main tasks
and only really update the nagging things like virus protection and firewalls ..... makes them feel as if they are taking part in something to make their systems
more reliable .......

The user to computer partnership ........ the user helping to save their system.

Defragging - virus protection - firewalls ........ all simple tasks users of Windows do and gives them a sense of taking part without doing anything too drastic to kill
it off ...... and if it does get killed off ...... then it was due to a virus or some outside force taking over.

Linux on the other hand ...... damn ..... my fault - should not have upgraded ......... or why did I try compiling that ....... when I know its integrated in such a way now
as to be difficult to upgrade or remove or why did I start linking things and cause problems - why did I try to add a different driver for my Nvidia card when the one I had
was working perfectly well .......... why did I even touch the network and try upgrading when the settings were working perfectly before ...... why did I mess with the sound 
as it used to work in every package and now it only works in a few ........

Think the user experience at adding value to their own system .... may be a point to bear in mind ........ upgrading or degrading a system .

How to tinker with things ...... and keep within a boundary that is safe for a particular user ............ 

or are we as Linux Users all taking things to the Limit to see when they will break and then wanting something to fix ...... ;)

What needs to change to make Linux the only one ........ and make others go extinct before it does.

---

### Post by buzzingrobot on 2014-04-02
> **monkeybrain20122 said:**
> ...unzip/untar and click binary, that's it...

That's an installation, at least as i define it. Putting software on a machine so it can be used, however it's done, is installing. Mostly semantics, though.  

Executables can be compiled with all needed support libraries linked into a single large binary. It's one way of coping with the filesystem differences and dependency issues across Linux distributions.  Presumably, that's why Mozilla does it.

Or, everything needed to run can be stashed in a simple tar acrchive and extracted into a single directory. That opens the gate to repetitive duplication and complicates updating and security.

Every so often, someone rolls out a distribution that tries to adopt a different approach. (Here's one that does away with /bin/ usr/bin, etc.:  [http://nixos.org/](http://nixos.org/)) They don't take off because of the inertia created by the fact that the the entire Linux software ecology is based on using shared libraries. Since no one is in charge here, and since there are plenty of developers who would resist the change simply because someone else wanted it, I think we'll be using shared libraries, with the little annoyances they bring, for a long time. One annoyance is that changes a user makes that aren't seen by the package manager/dependency resolver can cause problems down the road.

If *commercial* products ever really become common for Linux (I doubt they will), I suspect they will probably adopt Mozilla's approach of binding everything into one fat binary to avoid the hassle and expense of coping with distribution-specific differences. (Unless, of course, one distribution commands a large enough market that vendors can make money selling only into it.)

---

### Post by jamie-hamshere on 2014-04-02
> **Old_Grey_Wolf said:**
> Without Microsoft and Apple I question whether most people would have the option to have a home computer. They made home computers affordable and available for many non-tech people.
I thought that was down to Sinclair, Commdore, and Atari?

---

### Post by 23dornot23d on 2014-04-03
```

The hand-held [calculator]("http://en.wikipedia.org/wiki/Calculator") was introduced to the world by TI in 1967

Amstrad .... base 1968

Linux .... base 1969

The history of UNIX starts back in 1969, when Ken Thompson, Dennis Ritchie and others started working on the "little-used PDP-7 in a corner" at Bell Labs and what was to become UNIX.


Apple .... base 1969

[http://en.wikipedia.org/wiki/History_of_Apple_Inc.#1969.E2.80.931984:_Jobs_and_Wozniak](http://en.wikipedia.org/wiki/History_of_Apple_Inc.#1969.E2.80.931984:_Jobs_and_Wozniak)


Windows .... base 1975

[http://windows.microsoft.com/en-us/windows/history#T1=era0](http://windows.microsoft.com/en-us/windows/history#T1=era0)

```


And this guy [http://en.wikipedia.org/wiki/Alan_Sugar](http://en.wikipedia.org/wiki/Alan_Sugar)

Amstrad aimed at one application really - word processing ... but the computers were cheap and the guy did well out of it all.

Sugar founded Amstrad in [COLOR=#ff0000]**1968**[/COLOR], the name being an acronym of his initials &#8211; ***A**lan **M**ichael **S**ugar **Trad**ing*.

**Alan Michael Sugar, Baron Sugar** (born 24 March 1947) is an English[SUP][[4]]("http://en.wikipedia.org/wiki/Alan_Sugar#cite_note-4")[/SUP][SUP][[5]]("http://en.wikipedia.org/wiki/Alan_Sugar#cite_note-5")[/SUP] [business magnate]("http://en.wikipedia.org/wiki/Business_magnate"), media personality, and political advisor. From [East End of London]("http://en.wikipedia.org/wiki/East_End_of_London"), Sugar now has an estimated fortune of £770m (US$1.14 billion) and was ranked 89th in the [Sunday Times Rich List 2011]("http://en.wikipedia.org/wiki/Sunday_Times_Rich_List_2011")

Could anything ever top that ..... but what happened to Amstrad - Atari - Commodore - Sinclair ........... etc ....... 

What if Linux is the only one to continue when all the others fall by the wayside and what will be the application or applications that stand out in its thousands
upon thousands of a ever expanding library ..... is the library on the Net the reason Linux will always deliver - quickly uptodate answers to problems with the programs being altered in real time to address any issues that may arise.

I still wonder if Linux (unix) had not had so many branches from its core if it would have done better ... we will never know - and it still keeps branching off
instead of coming back together .... probably the A4 pdf shows the full extent better than anything - must print this off [http://www.levenez.com/unix/unix_a4.pdf](http://www.levenez.com/unix/unix_a4.pdf)

Source of above tree - of the Unix diversions since [COLOR=#ff0000]**1969**[/COLOR]
  [URL="http://www.levenez.com/unix/"]http://www.levenez.com/unix/
[/URL]

---

### Post by Eddie Wilson on 2014-04-03
> **Kyle_Undercofler said:**
> That is the question. What if there was no Microsoft Windows, and no Mac OS? What if there was only Linux? I think it would be amazing because Linux gamers would never have to worry about OS incompatiblities! It would also kind of suck though, because it would get A LOT more viruses. After all, the reason Linux gets so few viruses is because more people use Windows and Mac OS.
On the point of the viruses, that's not exactly correct. Most people say that Linux don't have viruses because there is no profit in it. There is not enough of Linux around. That is totally untrue. Chances are that there is more Linux around than Windows or Apple. Just look at Android, and all the other embedded systems that use Linux. Then you also have most of the servers in the world and most supercomputers running Linux. The list goes on and on. I'm not saying that Linux is unhackable but not with the kind of virus trouble we see in the Windows world. Most hackers, or computer criminals in the computing word today just simply do not have the skill sets in order to hack a Linux system. The thing about a question like this is that it's so hypothetical that there can really be no correct answer and no way of knowing what would really happen. But the virus thing...I don't think so.

---

### Post by Eddie Wilson on 2014-04-03
> **23dornot23d said:**
> Its a lot of little things that all add up to making something the best ........

Price
Quality
Reliability

You would think Linux should win hands down any way here ....... 

Price Free ...... 
Quality - Good to Very good on programs like Blender and Firefox that are widely used
Reliability .......

Think that is where you have hit the nail on the head ......... reliability ......... people in Windows sometimes stick with initially installed software for main tasks
and only really update the nagging things like virus protection and firewalls ..... makes them feel as if they are taking part in something to make their systems
more reliable .......

The user to computer partnership ........ the user helping to save their system.

Defragging - virus protection - firewalls ........ all simple tasks users of Windows do and gives them a sense of taking part without doing anything too drastic to kill
it off ...... and if it does get killed off ...... then it was due to a virus or some outside force taking over.

Linux on the other hand ...... damn ..... my fault - should not have upgraded ......... or why did I try compiling that ....... when I know its integrated in such a way now
as to be difficult to upgrade or remove or why did I start linking things and cause problems - why did I try to add a different driver for my Nvidia card when the one I had
was working perfectly well .......... why did I even touch the network and try upgrading when the settings were working perfectly before ...... why did I mess with the sound 
as it used to work in every package and now it only works in a few ........

Think the user experience at adding value to their own system .... may be a point to bear in mind ........ upgrading or degrading a system .

How to tinker with things ...... and keep within a boundary that is safe for a particular user ............ 

or are we as Linux Users all taking things to the Limit to see when they will break and then wanting something to fix ...... ;)

What needs to change to make Linux the only one ........ and make others go extinct before it does.
Most people that run Windows do not update, most don't even know what a firewall is, They know nothing about the inner works of their computer and most use Windows because it came on their computer. It is getting to a point where the operating system is irrelevant to the user of the system. How many tablets do you see running Windows? Very few, most run Android. Even the Apple OS takes a back seat to Android. People don't care. As long as they can get on Facebook, Amazon, twitter, Yahoo, and check their e-mail on whatever service, then they are happy. The days of MS Windows only software is slowly coming to an end. Companies that do not evolve will fail. Those are facts that cannot be denied.

---

### Post by buzzingrobot on 2014-04-03
> **Eddie Wilson said:**
>  Most people say that Linux don't have viruses because there is no profit in it.

Actually, it's because the return on investment is considerably larger with Windows, not because "there is no profit" in Linux. Malware is a business and businesses choose activities with the greatest return. 

 > Chances are that there is more Linux around than Windows or Apple. Just look at Android...

I don't think the numbers support that. Android attacks are far from unknown.

>  Most hackers, or computer criminals in the computing word today just simply do not have the skill sets in order to hack a Linux system.

They would learn.  Especially people in it for money. Criminals worry me considerably more than those folks you call "hackers". ("Hackers" is an honest and venerable label.) The former can wipe out your bank account.  The latter are typically annoying adolescents.

---

### Post by Kyle_Undercofler on 2014-04-10
> **Old_Grey_Wolf said:**
> Without Microsoft and Apple I question whether most people would have the option to have a home computer. They made home computers affordable and available for many non-tech people.

I never said if Microsoft and Apple never existed. They could still being making affordable computers, it's just that all of those computers would run on some form of Linux, as opposed to Windows and Mac OS. Heck, the two companys could have their own distros of Linux, but of course there'd still be the community made ones, like Ubuntu, or Linux Mint, etc.

---

