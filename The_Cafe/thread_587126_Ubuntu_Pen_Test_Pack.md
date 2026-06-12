---
title: "Ubuntu Pen Test Pack"
date: 2007-10-22
forum: The Cafe
---

### Post by fischer98 on 2007-10-22
I've been slowly delving into the world of Information Security, and aside from Ubuntu's obvious general appeal, there is a strong need for InfoSec professionals to be proficient in both Linux and Windows. Ubuntu was my first real in-depth exposure to Linux, back with 5.10, and it has grown and matured a lot since then. IMHO, it is the best distro out there for the Linux noob who is looking to learn, understand, and use Linux either as an occasional tool or as a primary desktop OS.

That being said, there are other distros out there that are specifically designed for InfoSec professionals. [http://www.securitydistro.com](http://www.securitydistro.com) is a wealth of information. Backtrack is probably one of the best, and there is also nUbuntu, which is obviously an offshoot of Ubuntu. And while these specialty distros will always have their place, they don't meet my two primary goals:

1. A distro that is easy enough to use that it "just works" as a primary, every day desktop OS.
2. A distro that has all the tools installed that I would need for an authorized penetration test.

Backtrack satisfies (for the most part) number 2, but is inadequate for number 1. The reverse can be said for Ubuntu. I am especially pleased with the 7.10 release as a primary OS.

Being mostly a windows monkey, I have neither the time nor desire to create my own distro. I can download and install the tools I need in Ubuntu, but if I ever have to reload my laptop, it would take a small act of Congress to get all the tools set up again just like I had them. So my thought is that I could create a "Penetration Testing Pack (PTP)" for Ubuntu that would automatically install all of the tools and documentation I would need. My initial goals for such a project:

1. Gear the layout of the tools and documentation towards the penetration testing process, grouping tools together that would be used in the same phase of a particular test.
2. Locate, gather, and/or create documentation geared towards those just getting started in the InfoSec world, with an emphasis on training sys admins who are wanting to make the transition from information technology to information security. 
3. Only install tools that are available as packages from the main, reserved, universe, and multiverse sources so that updates to the tools can managed via Synaptic.
4. For essential tools that do not meet the third criterion (i.e. Metasploit), either work with the tool developer to create packages that can be managed and updated via Synaptic or provide tools as part of the PTP that can easily update these tools.

My question to the Ubuntu community is this: would you use such a resource, and if so, would you want to contribute to it?

---

### Post by daynah on 2007-10-22
You've done a great job laying out 1) why you need this and 2) what you need to accomplish this...

But I don't know what this is. I know it involves the word penetration... and this sentence... "So my thought is that I could create a "Penetration Testing Pack (PTP)" for Ubuntu that would automatically install all of the tools and documentation I would need."

I just don't think I understand, to me, Ubuntu already does that. I'm obviously just not getting it. The Penetration must have distracted me. Elaborate more?

---

### Post by fischer98 on 2007-10-22
Penetration testing is essentially authorized hacking, either for your own organization or for third-party clients. The goal is to identify where and how attackers could compromise your network/systems/data and provide recommendations and remedies to mitigate the risks.

The point of the project would be to have a single program/script that would download, install, and configure all of the tools I would need for such work and integrate them into both the Gnome environment and the Ubuntu file system in a logical, organized manner. 

Yes, I could download and configure each of them one at a time, but if I ever need to either reload my system or set up a new one, I don't want to have to spend hours doing it all over again. I'm a big fan of automation. If I have to do it once and foresee needing to do it again, I generally try to provide an automated method so that it can be done the same way each time.

Think of the EasyUbuntu project, but for security/hacking/penetration testing tools. [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/). You could individually download and configure all of the components that tool installs, but that tool is one of the first things I run on a new Ubuntu installation because it is so, as the name implies, easy.

---

### Post by fischer98 on 2007-10-22
One more thing. If you answer the poll as "Yes, and I would want to work on the project as well", please post a quick reply to this thread or send me a PM. Thanks.

---

### Post by revolve on 2007-10-23
This sounds a bit like the nUbuntu project.

[http://nubuntu.org](http://nubuntu.org)

---

### Post by fischer98 on 2007-10-23
Kind of, but nUbuntu is only half of what I'm trying to do. From their website:

"The main goal of nUbuntu is to create a distribution which is derived from the Ubuntu distribution, and add packages related to security testing, and remove unneeded packages, such as Gnome, Openoffice.org, and Evolution."

To me, those listed apps, and others, are part of what satisfy my daily use, primary OS that just works requirement. I don't want to have to dual boot for daily use vs. pen testing, nor do I want to have to run one in a virtual machine on top of the other.

That, and the latest release of nUbuntu is only 6.10. If they are attempting to match the Ubuntu release cycle, they are two releases behind. This way, I let the Ubuntu guys do what they do best, releasing a great OS, and my program just adds the extra security tools layer that I need.

---

### Post by marco123 on 2007-10-23
I think this is an excellent idea.  Would save me a lot of time installing all the programs separately.:)

---

### Post by pixeldotz on 2007-10-23
ahhh i would love this.
(absolutely love whitehat)

i was thinking about this during the weekend whilst i was trying to get bluediving installed in ubuntustudio. (this goes to your everyday os use and pentest pack since i use ustudio every single day). i couldn't get it installed correctly because the libreadline the repos have are not the ones it needs.

i'd be willing to help with the wireless side of the distro. especially the broadcom issue so many have (i feel your pain people as i too have to manually install my 4311 wireless)

let me know what you need. i can do some eyecandy too if needed.

---

### Post by fischer98 on 2007-10-23
Thanks for the offer to help. Keep in mind this is not meant to be a separate distro, but rather an add-on to Ubuntu. I won't be trying to configure any hardware, wireless or otherwise. 

My goals for phase 1:
1. Be able to create menus in Gnome for all users from the command line. These will be used to organize the tools and documentation
2. Identify the tools to install.
3. Create a directory structure under /pentest to give a logical layout to the tools, house tool- or pen-test-phase-specific documentation, and provide symbolic links to the tool binaries
4. Download and install the tools

Would be nice for phase 1:
A graphical installer where I can choose not to install specific tools and/or configure other options. Perhaps read out of the apt-cache database for tool descriptions.

I can already do 3 and 4, and I am close on 1. One thing that would be of help would be to comb the main, restricted, universe and multiverse repositories for tools to install (goal 2). 

Since part of my vision for this project is for it to be a teaching tool for sys admins looking to make the jump to infosec, I will probably focus on tools that I can find detailed, tutorial-style documentation for, above and beyond the man pages. Nmap is a good example. There is an excellent tutorial at [http://www.nmap-tutorial.com](http://www.nmap-tutorial.com). It goes well beyond the man page. And obviously, there is a wealth of info at [http://www.insecure.org](http://www.insecure.org) on the program.

---

### Post by pixeldotz on 2007-10-24
i see where you're going with this.

i love the idea of a tutorial based section. much like backtrack2 but with lots more info.

i think with the information on most of the tools i could write decent html or pdf based tutorials we could toss in there. nmap is invaluable as an infosec tool and tutorials like that for all the tools would be heaven for script-kiddies (and a nightmare for the rest of us.)

back on topic :).

what do you think should be the main focus of the add-on? network/wireless/bluetooth? (bluetooth i pretty much got down flat and can write detailed tutorials for all the tools in backtrack)

---

### Post by fischer98 on 2007-10-24
Exactly. Backtrack is great, but even after going through the Backtrack 101 training, I really don't feel like I understand the Pen Test process any better. It seems more geared towards people who already understand Linux and infosec to a certain degree.

Script-kiddies will always be there, unfortunately. I tend to fall into the camp of they will find the info anyway, so lets make it easy for the rest of us who have to defend against them.

There are 5 general attack phases:
1. Reconnaissance (find out what info is out there in the public domain that can be used for an attack)
2. Scanning (network mapping and vulnerability scanning, looking for attack vectors)
3. Exploitation (get unauthorized access to the target's data/network/systems, electronically and/or via social engineering)
4. Maintaining access (trojans, backdoors, and the like)
5. Covering tracks (erasing logs, hiding attack files, etc.)

Most of my experience lies in 1&2, so that's where I'll focus my efforts for now. Most pen tests, as I understand it, would stop with step 3, but InfoSec professionals need to be aware of 4&5 tactics as well. As such, I would like to focus on steps 1-3, but also provide info on 4&5 as well. As for the attack vectors (wireless/bluetooth/network/web,etc), I'd like to cover as many as possible.

As for the tutorial arm of all this, I envision two types: individual tool tutorials and "putting it all together" tutorials that delve more into the thought processes that go into an attack/pen test and how to use the tools in conjunction with one another to achieve the objective. I want to include all the documentation as pdf, and I am a big fan of not reinventing the wheel. So unless you can't find well-written tutorials or just feel like writing, focus on gathering rather than creating. On the flip side, my wife says I'm a bit of a grammar nazi, especially in formal writting, so my bar for "well-written" will be pretty high.

---

### Post by pixeldotz on 2007-10-25
understandable.

a good tutorial for an example would run like...

"you would run say nmap after picking your target. once the info needed has been gathered you could run XXXX to try and gain access then start deleting logs to hide your tracks and use XXX to setup a hidden account to maintain access and future access"

of course 'picking your target' seems to malicious in nature. i'd word it differently of course.
"after obtaining proper authorization to test the network..."

sounds better.

but it'd be a way to go through the thought process and understanding of what tool to use for what job.

---

### Post by fischer98 on 2007-10-26
Right. And rather than those "putting it all together" tutorials going into deep detail of how to use all the ins and outs of a particular tool, we would probably just provide an example or two and rely on other tuts we either find or write to fill in the gaps.

Update for those interested: I've finally figured out the whole creating menus thing in Gnome. Alacarte is great for just yourself, but it doesn't support system-wide menus. It's a pain in the butt, if you ask me, as I have to create all manner of text files by hand to define the menus. But I digress...

I'll be setting up a simple website for the project soon, as the Pen Test Pack will be just one part of an overall Pen Test Project. Once I've got about 10 or so tools added, I'll turn my attention to the delivery system for actually downloading and running the tool. All of you who voted that you'd be interested in using the tool, I'd like to get some help testing out an alpha release. I'll probably be ready for that in a few weeks or so, as time permits.

---

### Post by pixeldotz on 2007-10-27
seeing as how we want a desktop workable release how will this be done?

will it be done likw ubuntustudio that even though is geared toward the creative side of linux still functions as full desktop?

i really like this idea as i have been installing lots of pen-test tools into my ubuntu studio install.

but starting from a fresh gnome (or flux) install is what i was thinking.
meta-package?

---

### Post by fischer98 on 2007-10-28
I hadn't even considered doing a meta-package. It's a good idea, but right now, I am just doing a simple bash script. The script would still be necessary after the fact, as there are a number of organizational things I want to do after a package is installed. 

For instance, like the BackTrack guys, I want to have a /pentest directory with everything organized in there. But one thing that irritates me about BackTrack is that some of the tools are already in your PATH, and some aren't. So for some, you actually have to call the exec absolutely, or browse to the appropriate dir under /pentest. My /pentest will show all the tools installed, but will only contain symbolic links to the actual binary. It will also contain the documentation for a given tool. So the links serve more to let you know what all is installed as you are browsing the directory, but you can call each binary from any path you like. 

My script will actually be two different scripts. One will contain separate install lines for each tool, arranged alphabetically inside the script. So you'd see something like this:

#Nmap - Install nmap and nmapfe
apt-get -y install nmap nmapfe
mkdir -p /pentest/scanning/nmap
ln -s `which nmap` /pentest/scanning/nmap/nmap
ln -s `which nmapfe` /pentest/scanning/nmap/nmapfe
rm /usr/share/applications/nmapfe.desktop

And that's one entry in the script. Removing the desktop file takes it out of the default menu placement (which goes under system tools fo r NmapFE). Then my second script copies all the files necessary to set up the menu in Gnome as well as copying all the documentation files to their appropriate location under /pentest. 

I know, it's not pretty, but again, I'm a windows monkey, so this is all still a little new. Eventually, I want to have a graphical installer that lets people choose which tools/options they want to install, as well as providing an uninstall option. 

Right now, I'm thinking I would just distribute everything in one tar.gz file along with a README for install instructions.

The installation of the packages is really not that big of a deal. Anyone could write that script if they wanted to take the time. I'm thinking (and hoping) that what will give this project value is the organization of things in the Gnome menu & /pentest dir and the tutorial-style documentation included.

---

### Post by pixeldotz on 2007-11-02
sounds good.

what about for the tools not in the repos?

like the blue diving sweet?

there are no debs that i know of for that one (spent a few days looking)

i had trouble installing it on ubuntu studio.

---

### Post by pixeldotz on 2007-11-03
ok last thing.

i started putting tools together in  xubuntu as a test under a virtual machine.

what release should be used? i think xubuntu since it's the least intensive of all the window managers.

[edit]

woops. i forgot you're doing everything as a script installer.
hehe.

---

### Post by n3tfury on 2007-11-03
if he went that route, fluxbuntu would be a good choice also.

---

### Post by samjh on 2007-11-03
This is a very interesting idea.

What is the scope of the tools and tutorials you're aiming for?  Information security is a very broad field, and thorough penetration testing can be much more than the usual sit-at-a-computer-and-type-away job.  For example, are you looking to cover the shifty area of social engineering, or just focus on the purely technical aspects of pen testing?  Will you be looking at internal attacks by employees, external attacks via the web, wireless attacks, email-based phishing or attachment attacks, phone taps, or keeping it limited to a few of the most obvious areas?

A lot of security-related documentation tend to be either to basic or too advanced, so there will probably need to be a lot of self-written materials for tutorials.  Most of the really good texts need to be purchased.

---

### Post by n3tfury on 2007-11-03
> **samjh said:**
> This is a very interesting idea.

What is the scope of the tools and tutorials you're aiming for?  Information security is a very broad field, and thorough penetration testing can be much more than the usual sit-at-a-computer-and-type-away job.  For example, are you looking to cover the shifty area of social engineering, or just focus on the purely technical aspects of pen testing?  Will you be looking at internal attacks by employees, external attacks via the web, wireless attacks, email-based phishing or attachment attacks, phone taps, or keeping it limited to a few of the most obvious areas?

A lot of security-related documentation tend to be either to basic or too advanced, so there will probably need to be a lot of self-written materials for tutorials.  Most of the really good texts need to be purchased.

although i'm always interested in social engineering (i've read The Art of Deception, among others) i don't see how this can be incorporated into what the OP wants?

---

### Post by samjh on 2007-11-03
That's why I asked.  There is nothing to stop that sort of material from being incorporated into the tutorials or documentation.  So the scope of the tutorials or documents need to be pinned down: does the OP want material that is only relevant to the software in the pack, or does he want wider scope?

---

### Post by pixeldotz on 2007-11-06
information security in general does not need to focus on digital information.

you guys are right. any kind of information that needs to be kept confidential would be at risk.

a simple fact of social engineering is that the person on the other end of the line is not getting paid big money to keep those secrets or really care who's asking them what. i could call up numerous department stores with just a birthdate/address and name and get all the information i need.

i think a section on social engineering needs to be added.

where i work we have a very tight-knit it group that knows who calls for what and who to direct to who in case they don't know the answer.

procedure training for the human factor of infosec is the hardest part :)

---

### Post by pixeldotz on 2007-11-07
removing the .desktop file from the menu is a good idea i think. however; i think those should be placed into a folder for later use. like maybe as an added entry to the menu after we sort all .desktop files.

i know you want the user to be able to use the term and just type 'nmap' or 'nmapfe' but a menu style should also be used for all the gui styled apps like 'nmapfe'


btw i'm working from inside a xubuntu vmmachine (i to am a windows monkey with ubuntu studio on my laptop).

since the majority of all this will be script based, this makes it simpler to script everything before rolling out something for an installed system.

imo anyways.

is there anything particular i could be working on aside from documentation? nmap has an excellent tutorial already from just searching for 'nmap tutorial'. i don't know if we can put that into a release as i haven't checked the license on that document.

---

### Post by iceportal on 2008-05-15
I would absolutely LOVE to see this distro created. I've tried a couple ubuntu-based security distros, namely:

Protech Ubuntu - [http://techm4sters.org/](http://techm4sters.org/)
nUbuntu - [http://www.nubuntu.org/](http://www.nubuntu.org/)

But I have found them both lacking.

I LOVE Protech, it's very very good. I especially like the out-of-the-box Opera with Tor+Privoxy, though I'd like Firefox with Tor+Privoxy better.

My only complaints about Protech are:
1. Not Gnome. I figure they want it to be fast on every computer, but I <3 Gnome, and really it isn't hard to set up custom menus in Gnome like you can in fluxbox.
2. Kismet doesn't work OOTB (out of the box) like it does in BackTrack 2. I love kismet, and wish i could get it working on my compy, but I'm not technically elite enough yet to do it, so OOTB is a must.

So maybe you could fork Protech (or work with them to devise this PenBuntu package) so that you can:

1. Install it for use with practically any window manager you currently use, and
2. Have kismet work OOTB

Good luck with the project, and I'd love to hear more as time goes on!

---

### Post by psysmic on 2008-08-11
I know this was an older post, but found it by accident, and think this idea has real merit.

Suggestion:  Make the distro/ pack a reflection of your experience.  Not everyone can drop the coin to get a cert/ go to class.  So you installed Metasploit?  What is DCOM? And why does the exploit work?  This could be the element that makes this project stand out from other sec distros.  BT is the stuff, without doubt, but if you don't know what those tools are doing or which one is applicable, how do you what you are trying to learn is even relevant?  I love the education premise of what I think is your idea.  There are plenty of people out there selling themselves as "experts" (shudder), how does that help us? or you? So their expensive commercial software says you have x number of super critical problems, how can you positively affect change or fix the problem if you have no idea of how the technology works, talks, or interacts with other technology?  You just know that you have some "reds."  Yeah, those "reds" may fit nicely in your super trippy risk matrices, but if you're responsible for the well being of a system, all you have now is a document that may or may not get you budget to hire some real help.  On the other side, should I be impressed if you take down a system because you pointed and clicked?
If you had just a few tools, thoroughly substantiated and with the technological dependencies well related on a system in front of someone everyday because they can use it everyday, and not another tool packed specialized distro, you wouldn't only be different, you'd be making a difference.

---

### Post by twofish on 2008-08-25
I'd absolutely love something along these lines.  

I, too, am just delving into the world of pen testing.  I've used Knoppix, TRK, and now BT3.  To have a nice clean ubuntu install that's usable as both a regular workstation and pen tester would be fantastic.  

Hopefully, this movement still has some legs under it?

---

### Post by soudaonca on 2008-11-10
I would love to see it happening. Please keep us posted about the project. If I can be of assistance, count me in.

---

### Post by detroit/zero on 2009-01-27
I ran across this post while doing some pre-install recon for my triple-boot Vista/Hardy/BT3 project.

I'm down with a script or something that would install a bunch of security-related tools in Ubuntu. A whole new distro seems a little overkill, since there are already so many others out there. But, hell, whatever we can come up with would probably be a winner.

---

### Post by suniyo on 2009-01-27
> **revolve said:**
> This sounds a bit like the nUbuntu project.

[http://nubuntu.org](http://nubuntu.org)

nUbuntu is a great idea but is it stable?

---

### Post by jackal_in_the_box on 2010-08-20
Hello to all,

While I am newly registered member, I am not a newbie to this thread, the concept of the Pen Test Pack, and I am an "Advanced-Beginner" when it comes to Ubuntu. :-)

I found this thread just today, and actually *registered *because of this thread. I absolutely love this Pen Test Pack idea. I am saddened to see that the last post on this thread was back in 2009! Now that it's 2010, I'm hoping that this idea is still a go?

So I ask the original creator of the thread... any updates for us? I think there are a lot of fans of your concept here.

Thx,
Jackal

---

### Post by phillips321 on 2010-10-23
Sorry to dig up an old thred but it's worth adding to this discussion.

GnackTrack is a security based penetration testing distribution design with all of the tools incorporated in backtrack but on a ubuntu 10.04 base.

Have a look if you get chance: [www.gnacktrack.co.uk]("http://www.gnacktrack.co.uk")

---

### Post by 98cwitr on 2010-10-23
a gnome version of backtrack with better GUI usability would be awesome...oh wait........

---

