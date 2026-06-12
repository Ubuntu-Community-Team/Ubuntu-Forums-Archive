---
title: "GUI - Graphic User Interface on Linux LAMP Ubuntu Server"
date: 2007-04-04
forum: Server Platforms
---

### Post by jorgerosa on 2007-04-04
Old theme this one: **Should Ubuntu Linux Server have GUIs (Graphic User Interface)?**
Just my opinion: Im pro in Windows and it wasn´t easy for me to set a linux server.
You will find lots of people saying GUI are a waste of resources and that command lines are easy, etc.

Why should i spent hours in commands lines, when i can do the same using GUIs, i don´t care about my PC resources, i just don´t want spend ALL my time in writing command lines.
Just an example: That´s why im a webmaster for 20 years and i know all commands from HTML, JAVA, ASP, SQL, ACCESS, FLASH, etc.. BUT i allways use a WYSIWYG software like Dreamweaver and others. (a success software piece)

"I just don´t want to spent all my time writing code or commands." - do you see now why the Windows is a best-seller? It has GUIs for everything, even for servers (IIS).

Even you are not familiar with windows you should be able to run IIS and mount a home server for about an hour or less. You can do the same on Linux, but only if you are already familiar with line commands, else... Could be hell

Of course i´ll go for Linux Ubuntu Server, never go back to Windows,
but why Ubuntu server doenst come with GUIs and option to uninstall by default?

Believe me, if you do so, then you can beat windows market!

---

### Post by gepatino on 2007-04-04
IMHO, the fact that in the windows world you have GUIs for everything is not an advantage, of course it's an absolutely subjetive statement.

My case is the oposite of yours, I've always installed web servers on Linux, maybe since 1998 or so. Maybe it's hard for you to believe this, but a couple of years ago I had to make some changes in a IIS and it was a nightmare. It took me about an hour to find how to add a virtual host, when in apache it's a matter of minutes.

This could lead to a flame war and nothing will change, the truth is that we like to use the tools we're used to use (confusing? sorry about that... english is not my first language)

Usually LInux (or Unix like) servers never have a graphical environment installed by default, I think the reason is because usually those servers are in a remote location and you use ssh to manage them. Even if the server are on your office, using ssh allows you to be conected to many servers at once, don't need to much bandwith, etc.

well... just my opinion

---

### Post by Zuph on 2007-04-04
For the Desktop users, GUIs are nice and guide you through things.

For the server market, though, a GUI takes up an unbelievably and unjustifiably large amount of a resources.  Additionally, once an admin learns how to use the CLI for many programs, it becomes faster and easier to manage.  Additionally, most servers don't have any sort of monitor hooked up to them permanently.  Some have a KVM switch, and others simply have a serial terminal connection.  Either way, it makes sense to primarily run a basic CLI for remote access and serial access.

Additionally, it's a fairly simple matter of installing the GUI onto a default install of the server.  I'd rather my server start out lean and secure, and allow me to install exactly what I want, rather than have it start out with gobs of crap-ware that I don't want.

---

### Post by esaym on 2007-04-04
I installed kde on my box and it is only 450mhz.  Mainly just so I could set the time right.  Spent hours trying to figure out how to set the time and zone right.  Kde does it fine:)   However since then, I haven't loaded the gui in months.


You do what you got to do to administer.  Eventually you will get used to the console because we are all humans and lazy, why walk over to a computer and have to load up a gui just to administer it when you can do it all through ssh from your main desktop.  Things will slowly work out.  It did for me.

---

### Post by huygens on 2007-04-04
If you want to have Ubuntu Server Edition with a GUI. Install it, log in and type something like 'sudo apt-get install gnome gdm' and that should be it (or almost).

The problem of the GUI is the security and safety issue as well as the resource consumption.
For security, it is obvious, the more you have on your system, the more there is a risk to find a security flaw. Should I recall the recent security flaw in Windows with the mouse cursor... No GUI ==> no mouse ==> no flaws ;-)
For safety, and this is my opinion, but I think that it is much easier to do a misconfiguration with a GUI than with the CLI.
Resources, of course you can run KDE or Gnome on a old hardware. But if you get many connections and your server is a busy environment, the resources consumed by the GUI will be too important.

Also, I was grown up with DOS, Windows 3.1 and later discover Linux at the end of the 90s'. When I purchase a new computer in 2001, I had Windows XP Home on it. For once, you could have user accounts on Windows! I tried to use the GUI to configure file permission so that I could see the files of the other accounts but not modify them and vice versa. And that all account should have only basic privileges.
I have tried and tried with almost no luck. First of all, the file permissions could only be set with the CLI in Windows XP Home Ed. (or by rebooting in safe mode!!! :-x) Then I had to give admin priviliges to everyone because most of the application would not work properly without it :mad:. Now it seems that Vista corrects these flaws... well seeing the price of the upgrade to get a GUI and the functionality, that is a lot.
Linux was a breeze to configure for such a scenario already back in 1997 (and I guess much earlier too, as these are basic UNIX features).

---

### Post by bullgr on 2007-04-04
hi...

i was (and be?) a winblows user many years...
in my workspace i setup the last year a ubuntu server installation to use for a file server, with software raid 1.

in the begining of that it was very difficult to me, all the stuff must be done from the command line. but after many googling and searching in the web, ubuntu forum etc, i finaly master the damn command line.

you must be patient for each issue problem you must clear... i remember that for a tiny command (sudo chmod -R 777 mount-point) to be able all winblows users to have full permission on the files i was searching about 5-6 hours until i find the sollution.

the most difficult is when you don't know what to search (like me for the chmod command).

i remember that i was frustated too, why not a gui? but now after i do the job, and now how i am comfortable with the command line, now i realise the power and simplicity of the command line.

only when you master the command line you can understand how powerfull and how easy you config your system with it... just be patient...

and one issue too for the command line vs gui is that the command line, now matter are happens anything on the mashine, it always worked... this you can't say for a gui environment.

for example, i must oneday change the graphic card (don't ask why) in a few minutes without slowing much down the workplace.
i just remove the nvidia card and put a ati card (notice, the change was from nvidia card to ati) and restart the mashine... and the job was done!!! in a few seconds.
try this in a graphical gui...

this is why i like a command line server :mrgreen:

---

### Post by jorgerosa on 2007-04-04
[COLOR="Navy"]**gepatino:** *"using ssh allows you to be conected to many servers at once"*[/COLOR]
It´s a great feature like you said. But at least 2 PCs needed.

[COLOR="Navy"]**gepatino:** *"make some changes in a IIS and it was a nightmare"*[/COLOR]
Well... its easy for me, and hard for you in Win. But its hard for me and easy for you in Linux, because we have skills in different OS. But the idea, i guess, its get people to Ubuntu (like myself) and usually people come from Windows, and come along with this Windows vicious.

[COLOR="Navy"]**Zuph:** *"GUI (...) unjustifiably large amount of a resources"*[/COLOR]
I agree, but thats why we spend money in faster PCs, for them to work faster.
But i also know that´s why Linux runs great on old PCs, but i think Linux should be more effective to the new machines. (And new technologies like bluetooth, wireless, etc)
Now imagine this: This Ubuntu forum without avatars, without images with only texts.
Well, all knowledge will be here anyway, but should it be apelative for you to come here and learn? (Even your answer is "yes", think in a beginner...) And we both know that images are a great "waste" of space and resources on server.

[COLOR="Navy"]**esaym:** *"we are all humans and lazy"*[/COLOR]
My case :-P  That´s the spirit!... But also people doesnt have too much time to spend.

[COLOR="Navy"]**huygens:** *"I was grown up with DOS, Windows 3.1 and later discover Linux at the end of the 90s"*[/COLOR]
Almost like me (i started in 80s and discover Linux... now)

[COLOR="Navy"]**bullgr:** *"just be patient..."*[/COLOR]
Believe me, I am!
But almost its a question of our own time.
(The main idea is: - Stupid example - Put the keys and start the car. And not: Check or fix engine first, then start the car. people prefer an old car that just put keys, started and go, than a Mercedes that you must fix engine first and only after put keys and go, just because people have no time (and or knowledge) to do so. Thats why some Ubuntu Linux lovers still have affraid to leave Windows - this is my case)

If i try to explain to someone (beginner) how to create and set a server in windows, its really easy, because people are see what im doing.
In Linux is hard. Its not really apellative or convicent for beginners, because they only see commands lines, usually people quit.(Of course, not experienced users, because they already know all about Linux great advantages)

Resuming:
**Its easier for a experienced Linux user to uninstall the GUIs on a linux server distro, than a beginner to install there the GUIs. [COLOR="Red"]Thats why GUIs should come by default[/COLOR] - Happy beginners and happy expert users.** Dont you agree? (Please, send feedback)

---

### Post by az on 2007-04-04
> **jorgerosa said:**
> **gepatino:** 
If i try to explain to someone (beginner) how to create and set a server in windows, its really easy, because people are see what im doing.
In Linux is hard. Its not really apellative or convicent for beginners, because they only see commands lines, usually people quit.(Of course, not the professionals, because they already know Linux great advantages)

That depends on how you show them.

Anyway, I don't really see the point of this conversation.

There is no GUI for an Ubuntu server because there is no GUI for an Ubuntu server.  If you want to write one, go ahead.  No one is going to stop you.  It is not prohibited.  But why do you think no one has bothered to do it so far?

And I am not talking about installing a desktop (gnome, icewm, fluxbox, etc...)  A desktop is useless.  I am referring to a graphical tool for configuring your LAMP (and other kinds of) server.

---

### Post by jorgerosa on 2007-04-04
[COLOR="Navy"]**AZ:** *"There is no GUI for an Ubuntu server because there is no GUI for an Ubuntu server. If you want to write one, go ahead. No one is going to stop you. It is not prohibited. But why do you think no one has bothered to do it so far?"*[/COLOR]

Do you know **XAMPP for Linux**? ( Link: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html) )
Why so many people (Ubuntu users included) go there for server downloads, when they have a much more secure LAMP server in Ubuntu distro? - **Because XAMPP have web-based GUIs.** - Not secure, not recomended for production, but much more easier to install and learn. (And their comunity is hudge!)

- I may agree with your point of view. But how about have Gnome (or KDE) with Firefox and Webmin and PhpMyadmin pre-instaled? (Just an example)

About Windows, can you answer this:
"Windows servers are unsecure and slow and, most important, expensive like hell. Linux is much more stable, great viruses advantages, fast and its free!" - If so, why there are so many window servers? My answer is: Because the GUIs. Yours?

*[COLOR="Red"]**Please Note: Im not putting Ubuntu (Linux) down! - I thanks god there are good people working hard and for free for all of us. This is a great thing!!! Im just trying to get ideas to improve and help beginners (like myself) to Linux world. That´s why im here. And others like me, or else the "YES" on this pool should be at zero votes.**[/COLOR]*

---

### Post by Zuph on 2007-04-04
> [COLOR="Navy"]**Zuph:** *"GUI (...) unjustifiably large amount of a resources"*[/COLOR]
I agree, but thats why we spend money in faster PCs, for them to work faster.
But i also know that´s why Linux runs great on old PCs, but i think Linux should be more effective to the new machines. (And new technologies like bluetooth, wireless, etc)
Now imagine this: This Ubuntu forum without avatars, without images with only texts.
Well, all knowledge will be here anyway, but should it be apelative for you to come here and learn? (Even your answer is "yes", think in a beginner...) And we both know that images are a great "waste" of space and resources on server.

There are a lot of servers out there that can't afford to spare the CPU cycles and memory for a GUI.  Sure, Joe Blogg's web server can spare it, but maybe my virtualized server can't, or my rendering server, or whatever.  Fact is, we don't make faster computers so we can spare the resources for a GUI, we make faster computers so we can do more in less time.

Keeping in mind that we're talking about servers.  Servers rarely take advantage of bluetooth, wireless, etc.  Servers also don't have to worry about being as user friendly, like a web forum or desktop OS.

If you want to make the GUI an option for the server, go ahead, but the day I can't install Ubuntu server with the bare minimum is the day I switch to a different distro for server use.

---

### Post by dca on 2007-04-04
It's just as simple to do 'sudo apt-get install ubuntu-desktop' after the LAMP install...

---

### Post by jorgerosa on 2007-04-04
[COLOR="Navy"]Zuph: "If you want to make the GUI **an option** for the server"[/COLOR]
That is the main idea: Allways should be "**an option**" for you and the others.
So if it becomes by default, you could uninstall it. (This should be also in a easy way too for all users) - In this case you **allways** have your Ubuntu server in your fashion-way, practical and fast, like you want to, but for the others would be easier.

[COLOR="Navy"]Zuph: "Keeping in mind that we're talking about servers. [/COLOR]**[COLOR="Red"](1) [/COLOR]**[COLOR="Navy"]Servers rarely take advantage of bluetooth, wireless, etc. [/COLOR][COLOR="Red"]**(2) **[/COLOR][COLOR="Navy"]Servers also don't have to worry about being as user friendly, like a web forum or desktop OS."[/COLOR]
[COLOR="Red"]**1)**[/COLOR] - That is true! But even windows servers have support for it (just install, or not, the drivers - optional in Win Servers OS)
[COLOR="Red"]**2)**[/COLOR] - NOT user friendly? You dont need to because you have good skills, but its not the case of most people.

[COLOR="Navy"]dca: "It's just as simple to do 'sudo apt-get install ubuntu-desktop' after the LAMP install..."[/COLOR]
Agree (again), but dca, its allways be a command line needed. Not "Just click and your done".
remember, only after you know this simple line command, its easy.
Can a beginner know this comand line a second after he installed the server?
He only gets frustated, because he doesnt see an icon or something to click on it (just check how many posts in the forums about: "how to install GUI om my ubuntu server")

Im a pro in windows (more than 20 years experience in PCs, with many OS and machines, like ZX Spectrum, Atari ST, Atari 130XE, Amiga 500, Amiga 1200 (with Workbench) - I created games and software for all these machines) still, i loved that new graphical MS OS 95, *Yes! That one with GUIs! Something new that turned in a best-seller, and gived millions to Microsoft!* and now i intend to become a skilled user in linux, and im starting to love this new OS, **but i´ll never ever be a fan (FANATIC) neither for Windows neither for others OS**, i got my own life.

So even i could see that we all are not in opposite sides, something is going in a wrong way here... And i think its the fact we are looking only at us, and allways forget that strange thing that are called beginners... (Windows its for rich people (not for everyone) but Linux, in this way, is only for skilled people - If this is true, then Linux its NOT for everyone)

---

### Post by pppetter on 2007-04-04
2 years ago, I had never tried Linux for my self, then I installed Ubuntu, and later on, an ubuntu 6.06 LAMP server. Now, I just LOVE my server. I never installed a GUI, and I never ever would advise someone to install a GUI, 'cause IT'S A SERVER! It hogs up alot of resources, and it is a real security issue. 
It may take a couple of weeks to set everything up the first time. But then you got your server, and it will stay there for years :)

---

### Post by silurius on 2007-04-04
I think "should" is entirely subjective in this case, so I doubt there's an answer that'll satisfy everyone.  Certainly there will be a more or less equal split between administrators who want/need the GUI and those who don't.  "Best practice" might be a better question, in which case the answer is probably "no".

Of course, I'm still a total Linux/Ubuntu newbie, so I could easily be wrong on this.

Seems to me that if the security flaws related to running a GUI are addressed and documented well, the only remaining flaw with the server GUI idea is resource-related.  Beyond that, it boils down to personal preference.

---

### Post by brentoboy on 2007-04-04
I dont think that the need here is a ubuntu-desktop on top of a LAMP server.

What is really needed is a GUI that isnt all that extra crap (just a browser, no extra apps) that has real honest to goodness server gui setup options inside of System > Administration.   A GUI for managing and maintaining and tweaking your settings for your AMP.

It also needs a powerful samba domain server configuration tool.  It would be a SAMP GUI server.

It doesnt need to even have GDM installed.  It could sit at a text login until someone logged in and issued a startx command, then, it could offer a GUI that was compeltely devoted to making server admin really really easy.

It doesnt help to have a gui if all you do with the GUI is open up a gui terminal and sudo a bunch of commands.  you need a GUI that makes it easier to setup and manage your services.

---

### Post by silurius on 2007-04-04
> **brentoboy said:**
> I dont think that the need here is a ubuntu-desktop on top of a LAMP server.

What is really needed is a GUI that isnt all that extra crap (just a browser, no extra apps) that has real honest to goodness server gui setup options inside of System > Administration.   A GUI for managing and maintaining and tweaking your settings for your AMP.

It also needs a powerful samba domain server configuration tool.  It would be a SAMP GUI server.

It doesnt need to even have GDM installed.  It could sit at a text login until someone logged in and issued a startx command, then, it could offer a GUI that was compeltely devoted to making server admin really really easy.

It doesnt help to have a gui if all you do with the GUI is open up a gui terminal and sudo a bunch of commands.  you need a GUI that makes it easier to setup and manage your services.Here, here.  I might change one or two things there, but I mostly agree with this.

---

### Post by jorgerosa on 2007-04-04
**silurius**, maybe you are "a total Linux/Ubuntu newbie", but you have gone to the right point, and you argumented very well, with no bullsh*t talk. Its that kind of stuff Ubuntu forum needs to be really helpfull. (even i agree or not, doesnt matter)

---

### Post by taco2 on 2007-04-04
> **Zuph said:**
> For the Desktop users, GUIs are nice and guide you through things.

For the server market, though, a GUI takes up an unbelievably and unjustifiably large amount of a resources.  Additionally, once an admin learns how to use the CLI for many programs, it becomes faster and easier to manage.  Additionally, most servers don't have any sort of monitor hooked up to them permanently.  Some have a KVM switch, and others simply have a serial terminal connection.  Either way, it makes sense to primarily run a basic CLI for remote access and serial access.

Additionally, it's a fairly simple matter of installing the GUI onto a default install of the server.  I'd rather my server start out lean and secure, and allow me to install exactly what I want, rather than have it start out with gobs of crap-ware that I don't want.

I'm going through this right now, and it is not a simple matter of installing the GUI.  I've been working on it for about three weeks, and want to give up

---

### Post by brentoboy on 2007-04-04
taco, you need a good book

this book is an absolute necessity for every frustrated linux administrator.
[http://www.amazon.com/Linux-Quick-Notebook-Perens-Source/dp/0131861506/ref=pd_bbs_sr_1/002-5096421-1951242?ie=UTF8&s=books&qid=1175740658&sr=8-1](http://www.amazon.com/Linux-Quick-Notebook-Perens-Source/dp/0131861506/ref=pd_bbs_sr_1/002-5096421-1951242?ie=UTF8&s=books&qid=1175740658&sr=8-1)

---

### Post by taco2 on 2007-04-04
Resuming:
**Its easier for a experienced Linux user to uninstall the GUIs on a linux server distro, than a beginner to install there the GUIs. [COLOR="Red"]Thats why GUIs should come by default[/COLOR] - Happy beginners and happy expert users.** Dont you agree? (Please, send feedback)[/QUOTE]

Exactly.  Thank you.   I'm fustrated with not having the GUI,

---

### Post by az on 2007-04-05
> **jorgerosa said:**
> [COLOR="Navy"]**AZ:** *"There is no GUI for an Ubuntu server because there is no GUI for an Ubuntu server. If you want to write one, go ahead. No one is going to stop you. It is not prohibited. But why do you think no one has bothered to do it so far?"*[/COLOR]

Do you know **XAMPP for Linux**? ( Link: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html) )
Why so many people (Ubuntu users included) go there for server downloads, when they have a much more secure LAMP server in Ubuntu distro? - **Because XAMPP have web-based GUIs.** - Not secure, not recomended for production, but much more easier to install and learn. (And their comunity is hudge!)

- I may agree with your point of view. But how about have Gnome (or KDE) with Firefox and Webmin and PhpMyadmin pre-instaled? (Just an example)



Then the correct path would be for someone to install the desktop version of Ubuntu and install the LAMP stack on top of that.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

You end up with the exact same LAMP server as if you installed from the server cd.


As for phpmyadmin, it is just as easy to install as the LAMP stack.  As for webmin, it's a horrible, quirky - if not broken- piece of software.  That's why it was removed from the archive - it doesn't work.  Not for long, anyway;  it's too difficult to support.

If it worked, or if there was an alternative, of course it would be in the archive.


> **taco2 said:**
> Resuming:
**Its easier for a experienced Linux user to uninstall the GUIs on a linux server distro, than a beginner to install there the GUIs. [COLOR="Red"]Thats why GUIs should come by default[/COLOR] - Happy beginners and happy expert users.** Dont you agree? (Please, send feedback)

Exactly.  Thank you.   I'm fustrated with not having the GUI,

No one is denying you your GUI - there just isn't one!  Find one that works and is supported and it will be included.

---

### Post by jorgerosa on 2007-04-05
When i talk about GUI for server, i dont mean a GUI like Microsoft has, with all that stuff that you will never use. But a simple GUI.

For example an "naked" Gnome (no wallpapers, no audio, etc) with at least a file browser and a  shortcut in the desktop where people click and opens firefox in a Webmin (or other) and a phpMyAdmin (All these could be **WEB-BASED** GUIs). And **allways** with option for an easy and clean unistall for skilled users.

1 - Could this turn a server so unsecure? I think no. (But im not a Linux skilled person to answer this right)
2 - More resources?  (If you can uninstall, where is the difference??)

And 100% of the beginners (and people with lack of time) will be no affraid anymore of explore the new server world.
Its normal, today, when a beginner ask for a GUI in a server, lots of people are ready to call him stupid and so on, but no one search for fast solutions (the "easy" solution is allways just write 1000s of "simple" code lines in terminals)

NOTE: I work with Webmin (for FTP, EMAIL, WEB, RADIO, Etc Servers) with no problems until today (all in the same machine, only to learn, of course its not a production server - Never intend to be, but i learned a lot). And, like i said, Webmin have no problems until now, but im using it for only 2 months, maybe i had luck or even i never "pushed" my server far away. So i give all the credits to AZ, when he says: "it doesn't work. Not for long, anyway; it's too difficult to support"

ALSO NOTE: If i never intalled a GUI how many time should i spent in install all that servers? With GUIs it takes me almost 5 days.
If i havent how long should i be able to do all that? An year? Sorry, i had already quited. (Remember that are my firsts steps in Linux, i have no skills at all in this OS)

---

### Post by vanilla on 2007-04-05
I voted Yes, but with GUI I don't mean a complete desktop.

Sometimes a simple thing like aptitude is enough not a real GUI directly, sometimes web-GUI is enough so you can solve it from a remote computer.

---

### Post by Zuph on 2007-04-05
It's my firm belief that you'll never have as lean a system by installing something then removing it--  more than likely, something will be left behind.  If it isn't an unused dependency of the GUI, then it's the GUI portion of some application that still uses resources or something.  I want the leanest system possible.

Make it an option on install if you must, "Server WITH GUI, Server WITHOUT GUI,"  if you can't figure out which one you want to install, then Linux probably isn't for you.

---

### Post by silurius on 2007-04-06
(Thanks for the book recommendation, brentoboy)

Not sure if I saw this idea brought up in this thread yet, but one huge advantage to offering a simple GUI in the "out of the box" server edition is user adoption rates.  Sure, you can get the same thing through other means, but I'm talking simple marketing and pr.  A secure, slick, streamlined administrator GUI would probably turn more heads amongst administrators who happen to be "linux-curious".  If they are worth their administrative salt, they will soon grow to appreciate how powerful the other main featuresets are on their own, and shelving the GUI altogether (after learning their way around) might be inevitable.

---

### Post by jorgerosa on 2007-04-09
I posted a new topic in Ubuntu Forum at: [http://ubuntuforums.org/showthread.php?t=405574](http://ubuntuforums.org/showthread.php?t=405574)
I´m looking for different solutions there (specific for web-based GUIs for servers). Maybe it can help someone, besides me.

By the way i found these comments here: [http://ubuntuforums.org/showthread.php?t=357600&highlight=guis+server](http://ubuntuforums.org/showthread.php?t=357600&highlight=guis+server) ...and i think they are not newbies!

**HW_Hack: **"At least with Fedora they give you a bare-bones Xwindow environment and a basic browser to use" (...)
**SuperMike:** "I'm a big fan of non-GUI servers, but at least with Suse I can go through Yast to accomplish things fast" (...)

---

### Post by damvcoool on 2007-04-30
instead of a gui, something like webmin would be a lot better.

---

### Post by briealeida on 2007-06-20
For security purposes (and less overhead). again NO. 

If you don't need it, get rid of it.  A golden rule, no? I know the GUI is more convenient but you'll really appreciate having learned to use the command line. It's rough going sometimes, I know, I was there.

---

### Post by netlogic on 2007-06-20
NO GUI for the default installation. If people want GUI, they can install it themselves. ***If people aren't ready to learn apt-get, they aren't ready to be running servers.*** GUI isn't a security risk, but it is a risk of stability on the server. I like to keep my server minimum and clutter free. It increases the uptime. If it gets to the point Ubuntu gets a tight GUI integration, I am moving back to Debian. If people want bloated Linux servers, they can try Suse.

---

### Post by Betelgeuse on 2007-06-20
> **jorgerosa said:**
> - NOT user friendly? You dont need to because you have good skills, but its not the case of most people.

[COLOR="Navy"]dca: "It's just as simple to do 'sudo apt-get install ubuntu-desktop' after the LAMP install..."[/COLOR]
Agree (again), but dca, its allways be a command line needed. Not "Just click and your done".
remember, only after you know this simple line command, its easy.
Can a beginner know this comand line a second after he installed the server?
He only gets frustated, because he doesnt see an icon or something to click on it (just check how many posts in the forums about: "how to install GUI om my ubuntu server")


Users should NOT be allowed to touch servers. There are lots of point and click server admins that knows nothing about what are they doing and I'll not allow any one of them near my servers...

Making an easy GUI for desktop computers is good for users but servers are another area, if someone wants to learn how to administer a server, it's not a good way with a gui. We're talking about servers, servers should be administrated by people who know what they are doing.

---

### Post by chris.zeman on 2007-06-20
Having installed ubuntu-desktop just today to try it out on my server, I don't see the usefullness in having a desktop environment on any Linux server. I voted YES on the poll, but I personally wouldn't use a desktop environment on any of my servers unless there were more administration utilities available. Perhaps I missed something, but I didn't see any sort of GUI to administer the DHCP Server. There isn't a GUI available for Shorewall either, which I already knew, and that's the case for many of the software packages you would use on a server.

The best GUI I have found to date for administering my servers is Webmin. I install the minimal version of Webmin and add the modules I need. Everything is simple to administer through the web interface. I know how to work with most of the packages through the command line as well, but sometimes it's quicker to do it through Webmin.

Chris

---

