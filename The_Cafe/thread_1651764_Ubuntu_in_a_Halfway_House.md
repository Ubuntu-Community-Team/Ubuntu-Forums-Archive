---
title: "Ubuntu in a Halfway House"
date: 2010-12-23
forum: The Cafe
---

### Post by earthpigg on 2010-12-23
Howdy,

I'll be setting up 10.04 on 4 or 5 virus-ridden XP systems in a [halfway house]("http://en.wikipedia.org/wiki/Halfway_house") that no one currently takes care of. The administration really has no incentive to take care of them, and the few nerds that are clients haven't had luck fighting the constant assault of new issues. I've received permission from the house's administration to do this.

I'm brainstorming how to make this a fire-and-forget setup - I don't want to come back every two weeks to fix things, and there is no reason these dudes ought not be technologically self-reliant.

No original system restore discs for those computers, so it's either miraculously clean up and fix the current XP installs, pirate windows (tsk tsk), or go with Ubuntu.

I don't know much about the system specs, but I was told that they are probably from the 2003-05 timeframe. I'm assuming 512mb of ram minimum, but plan to bring a command-line install disc in case I encounter one with 256mb - I'll do the openbox/gnome-panel thing, or maybe lxde.

The plan is to set them up with three administrator (sudoer) accounts and one user account (they will be encouraged to maintain user accounts for all their buddies).

I'll find two of clients that are interested in babysitting these things and hopefully have a nerdy disposition, and give them each a sudoer account, and show them how to install ubuntu. They will be taught to create and manage additional user accounts, install packages, introduced to ubuntuforums.org, and I'll probably plop that official PDF manual on the desktop. I'll teach them how to delete dotfiles as a catch-all method to fix whatever common things a normal user account can break. I know at least one client has been taking some form of Linux certification courses, but hasn't had much hands-on experience as i understand.

If I can get one of the staff interested in learning, then I will. If not, I'll insist that at least one accepts a post-it with a sudoer username/password and lets me show them how to boot from an Ubuntu CD that they will be left with. For better or worse, the clients aren't exactly free people just yet.

The reason that at least two clients need sudoer accounts is in case one is no longer available, there will still be one left that can train up a new second admin. I have no idea what the life story is of the one dude that's had Linux training, but I do know these guys rotate in and out from time to time for various reasons and it isn't always with advance notice.

Currently, every client that isn't otherwise restricted is allowed to use these internet-connected computers with an administrator account. This won't change that, except that only two clients will have an administrator account to begin with. Currently, there is nothing stopping the clients from encrypting data on these computers. The ability to check a box during account creation is not a departure from that.

The idea isn't to limit what the clients can/cannot do, but to make these things functional and prevent clients from *accidentally* breaking things for everyone else. I'm not going to attempt to make these things secure from being ***intentionally*** broken in any way.

So, yeah.

I'm thinking about fairly standard Ubuntu 10.04 LTS installs, and I've been thinking of additional software that may be beneficial. The users will be doing various things from just learning to type, working on resumes and job hunting, reading current events, playing casual games, etc. TuxType will definitely be installed, and I'll teach the two admins how to show the clients to "save as word doc" and similar things.

I think I need help compiling a checklist of things to do.


-Bring a 10.04 LTS disc, and a command-line install disc.
-Show the two admins their way around.
-Try to get a staff member to learn, as well.
-Give LTS disc to staff member.


Things to teach the two/three admins:
-package installing/uninstalling.
-creating/managing user accounts.
-introduce to ubuntuforums.org.
-the official user manual pdf.
-delete dotfiles as catch-all to fix 'broken' user accounts.
-set up/install dropbox or ubuntu one so users can have persistent and reliable data storage. these folks aren't in a position to be purchasing thumb drives and external hard drives, and there is no guarantee the admins won't break things and have to re-install from time to time. Anyone have any opinions on dropbox vs ubuntu one? I don't want to force anyone to be stuck with ubuntu in the future, so i'm skeptical of ubuntu one...
-reinstall Ubuntu in case they break things (they will be the ones doing the initial install).
-save as word document in openoffice. what other compatibility issues might they face?

Packages to install:
-tuxtype
-kolourpaint for simple image editing
-maybe hulu desktop? i don't know if these guys have cable.
-ubuntu restricted extras, etc.
-official adobe reader - i know there are web apps used by this institution that only work with this installed.
-what other package suggestions?

---

### Post by tgalati4 on 2010-12-23
Write a notify-osd script to remind clients:  "Have you checked-in with your Parole Officer this month?"

"Don't forget curfew at 11 pm."

---

### Post by Old_Grey_Wolf on 2010-12-23
> **earthpigg said:**
> I'm brainstorming how to make this a fire-and-forget setup - I don't want to come back every two weeks to fix things, and there is no reason these dudes ought not be technologically self-reliant.


I wish you well with your endeavor. 

I have never been able to set up a "fire-and-forget" system for people recovering from the problems the people at "halfway houses" have. There was always someone that would reinstall the OS, a pirated version, a different OS, etc., in order to get to whatever program or website they needed. If I tried password protecting the BIOS to prevent installing an OS, they reset the BIOS or re-flashed it. They are not idiots and they do have friends willing to help them circumvent anything you do. They have physical access to the computers; therefore, they can overcome just about anything you do.

I'm sorry to sound so pessimistic.

---

### Post by drawkcab on 2010-12-23
> **Old_Gray_Wolf said:**
> I wish you well with your endeavor. 

I have never been able to set up a "fire-and-forget" system for people recovering from the problems the people at "halfway houses" have. There was always someone that would reinstall the OS, a pirated version, a different OS, etc., in order to get to whatever program or website they needed. If I tried password protecting the BIOS to prevent installing an OS, they reset the BIOS or re-flashed it. They are not idiots and they do have friends willing to help them circumvent anything you do. They have physical access to the computers; therefore, they can overcome just about anything you do.

I'm sorry to sound so pessimistic.

Crazy!

---

### Post by dmizer on 2010-12-23
The only real way to do this would be to have them set up as thin clients with a central and isolated boot server. [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

Then you can simply remove the drives and the residents will not be able to tinker with the systems. This way, the residents don't have "physical access" as long as they can't physically access the boot server.

Edit:
I also just happened to think about another interesting possibility: Cafe con Leche which is an internet cafe management software. It could be set up with diskless clients (as illustrated above) but adds a nice GUI management interface: [http://ubuntuforums.org/showthread.php?t=777093](http://ubuntuforums.org/showthread.php?t=777093)

---

### Post by NightwishFan on 2010-12-23
Not sure if Ubuntu landscape works for desktop type machines or not, I think it is some form of central machine management or something.
[http://www.canonical.com/enterprise-services/ubuntu-advantage/landscape](http://www.canonical.com/enterprise-services/ubuntu-advantage/landscape)

---

### Post by judge jankum on 2010-12-23
The trojans, malware and viruses will be replaced with what they screw up on their own, welcome to the bull pen"

---

### Post by earthpigg on 2010-12-24
> **Old_Gray_Wolf said:**
> I wish you well with your endeavor. 

thank you.

> 
I have never been able to set up a "fire-and-forget" system for people recovering from the problems the people at "halfway houses" have. There was always someone that would reinstall the OS, a pirated version, a different OS, etc., in order to get to whatever program or website they needed. If I tried password protecting the BIOS to prevent installing an OS, they reset the BIOS or re-flashed it. They are not idiots and they do have friends willing to help them circumvent anything you do. They have physical access to the computers; therefore, they can overcome just about anything you do.

I'm sorry to sound so pessimistic.

I'm not setting the goal of attempting to prevent them from intentionally breaking anything. For whatever reason (maybe not all halfway houses are the same?), there doesn't seem to be a problem with folks intentionally breaking things.

The problem, as I understand it, is honest mistakes and errors that can cause breakage when everyone has an administrator account.

Personal data is far more valuable than any operating system install. I'm going to make sure to emphasize dropbox use, and encourage establishing accounts for all users.


Also, has it occurred to you that when you try to prevent an inquisitive person from doing something... it makes him ***want*** to do it? The two volunteers are going to watch me wipe and replace the installed OS, and help me do it. Others may be watching over their shoulders.

No bios password. No denying the two volunteers from having sudoer passwords, and no telling them they can't create as many admin accounts as they like. I'll ***suggest*** that they limit that as much as possible, but that is all.



> I also just happened to think about another interesting possibility: Cafe con Leche which is an internet cafe management software. It could be set up with diskless clients (as illustrated above) but adds a nice GUI management interface: [http://ubuntuforums.org/showthread.php?t=777093](http://ubuntuforums.org/showthread.php?t=777093)

I may have to give that a look-see :D

---

### Post by grahammechanical on 2010-12-24
I think that your attitude and approach is a good one and the correct one. After all, if the authorities (is that the right word? Supervisors? Living of the tax payers?) who run this halfway house don't care what these machines are used for, why should you do their job for them.

As for the clients (very Politically Correct term, that one), if they don't care that they are "breaking" something that they might find useful, then why try to stop them? They have to live with the situation or in this case, live at the halfway house without working computers.

Your approach might just help some of them accept responsibility and get satisfaction from doing so.

A thought has just occurred to me. Is there a computer in an office that the clients do not use and is necessary for the administration of the halfway house? If so, then create a PDF that explains everything that needs to be done to set up and maintain a working Ubuntu installation. Explain what can be done and how to do it. Put the PDF file on a CD and tell them to put it a cupboard until it is needed. Then all anyone needs to do is run the PDF on the office machine.

Regards

---

### Post by madjr on 2010-12-24
the only way to deploy and forget,

is using something like **Ofris** (is like deep freeze but for linux)

[http://www.webupd8.org/2010/08/ofris-deep-freeze-like-application-for.html](http://www.webupd8.org/2010/08/ofris-deep-freeze-like-application-for.html)

[http://www.webupd8.org/2010/09/ofris-gets-appindicator-gofris-deep.html](http://www.webupd8.org/2010/09/ofris-gets-appindicator-gofris-deep.html)

[http://www.youtube.com/watch?v=-79gQG-UGZo](http://www.youtube.com/watch?v=-79gQG-UGZo)

fsprotect is another option.
[http://admin.alfalinks.lv/en/content/how-install-fsprotect-ubuntu-1004-lucid](http://admin.alfalinks.lv/en/content/how-install-fsprotect-ubuntu-1004-lucid)


And / or **Plan B**.

[**Remaster**]("http://www.psychocats.net/ubuntu/remastersys") a special DVD version of Ubuntu with ALL the stuff they need. You can also apply Ofris to it.


And remember to lock down the UI. use gnome lockdown / ubuntu-tweak, hide some "preferences" , etc.

remove some applets like multidesktops. Usually people just get confused by it.

---

### Post by madjr on 2010-12-24
> Personal data is far more valuable than any operating system install. I'm going to make sure to emphasize dropbox use, and encourage establishing accounts for all users.

you may also want to try [jolicloud]("http://www.jolicloud.com/"), it comes with **dropbox** and is pretty hard for anyone to break the stuff. Just remember to lock the gnome panel at the top and you're good to go.

Install a few offline / online apps, open office, flash, etc.
Also everybody gets their own accounts.

---

### Post by earthpigg on 2011-01-02
Well, here's the After Action Report.

The systems had 256mb of RAM, could not boot from USB, had no CD burners or blank CD-Rs, and I didn't have the alternate install CD with me. I wasn't in touch with anyone savvy enough to know any of those technical details, so I didn't know any of that prior to my arrival. 

I'm also nervous about installing without being able to test it out first, so I don't like the idea of using the alternate install cd.

Call it a successful reconnosance, but not a successful installation.

I'm going to look at LXDE distributions that use Ubuntu's LTS repositories. I know there are many Debian and other options available, but I'm most familiar with Ubuntu.

So, we've got:

Lubuntu 10.04
Linux Mint's 10.04-based LXDE spin
What else?

Must be able to boot from the LiveCD on 256mb of ram for testing. A text-based installer is fine, but I'm not going to install without being able to test first.

---

### Post by sdowney717 on 2011-01-02
one thing to know is you can setup just one a single PC and if you clone the drives, the machines will all work as long as they are all intel pc's.
I setup ubuntu at home, took out the hard drive and put it in another pc, and it booted just fine. Must autodetect all hardware at boot, nice to have no registry to worry about.

---

### Post by sdowney717 on 2011-01-02
This situation makes me think a Chrome OS running off the cloud is a perfect system. No way for users to break the OS.

---

### Post by sdowney717 on 2011-01-02
[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

another thin client tutorial. 
I assume it runs off a lan?
How fast is thin client computing?

[http://www.ltsp.org/](http://www.ltsp.org/)
nice idea here
> The Linux Terminal Server Project adds thin-client support to Linux servers. LTSP is a flexible, cost effective solution that is empowering schools, businesses, and organizations all over the world to easily install and deploy desktop workstations. A growing number of Linux distributions include LTSP out-of-the-box.

Shiny new thin-clients and legacy PCs alike can be used to browse the Web, send e-mail, create documents, and run other desktop applications. LTSP not only improves Total Cost of Ownership (TCO), but more importantly, provides increased value over traditional computing solutions. LTSP workstations can run applications from Linux and Windows servers.

Linux thin-clients have proven to be extremely reliable because tampering and viruses are virtually non-existent. It's distributed under the GNU General Public License, meaning it's free and always will be.

You'll find that LTSP has comprehensive free and professional support, and it's developed by a very active global community. We invite you to participate too! 

---

### Post by tgalati4 on 2011-01-02
If you partition the drives by booting into terminal mode and using cfdisk, then you can create a small swap partition, then you can use the regular Ubuntu LiveCD with 256 MB.  It's a little slow but doable.

But for those specs, I would use Mint XFCE, or as others have suggested, setting up ChromeOS.

---

### Post by earthpigg on 2011-01-02
That looks like a very managable tutorial, sdowney. thanks.

But, a thin client or complex networked setup isn't the route I am going to go.

-These computers are over five years old. The hard drives are all on borrowed time, and it wouldn't be a good idea to put all the eggs in one basket. Any hard drive could fail at any moment.
-Anything more complex than the standard Ubuntu install process would result in the clients being reliant on me if one of the onsite administrators breaks something. With normal desktop installs, they will always have a viable option to undo any damage done.
-I don't have permission to do anything with the network beyond plug these machines into the router.
-The budget for additional hardware (switch, NAS for backup, etc) is $0.00.

---

### Post by ugm6hr on 2011-01-05
Given the changing clients, unreliable hardware (including HDs), I'd suggest against anything that requires setting up.
Do you know what the clients use computers for?
If they have wired internet access, consider just using Puppy Linux.
Benefits:
[LIST]
[*]It's designed to be run from the LiveCD (so no settings at all)
[*]It runs with 256MB RAM
[*]No administrator required
[*]No dependence on the HD at all - you could just format and leave for clients to save stuff anywhere on it (or leave them as they are)
[*]It has some basic off-line apps and will work fine with Google Apps
[/LIST]
Just set the computers to boot from CD as default, and you're good.

---

### Post by Thryn on 2011-01-05
> **ugm6hr said:**
> Given the changing clients, unreliable hardware (including HDs), I'd suggest against anything that requires setting up.
Do you know what the clients use computers for?
If they have wired internet access, consider just using Puppy Linux.
Benefits:
[LIST]
[*]It's designed to be run from the LiveCD (so no settings at all)
[*]It runs with 256MB RAM
[*]No administrator required
[*]No dependence on the HD at all - you could just format and leave for clients to save stuff anywhere on it (or leave them as they are)
[*]It has some basic off-line apps and will work fine with Google Apps
[/LIST]
Just set the computers to boot from CD as default, and you're good.
I was going to recommend Puppy as well, but an Ubuntu-based LXDE distro that hasn't been mentioned (I think) is [Peppermint]("http://peppermintos.com/"). It requires only 192 MB of RAM, but is cloud-based so it's probably only worth it if there's internet access. I haven't tried it though.

---

### Post by earthpigg on 2011-01-06
aha! that's right, i'd forgetten about peppermint. i tested it before, and it was very nice.

---

### Post by HermanAB on 2011-01-06
Hmm, I would remove the hard disks and give them Live CDs.  A fresh CD is only about 25c, so that is your best bet and with no hard disks, they cannot install anything on the machines.  If they are savvy and use their own USB disks or memory sticks, then it is not your problem.

---

### Post by ugm6hr on 2011-01-06
> **HermanAB said:**
> Hmm, I would remove the hard disks and give them Live CDs.

If the staff allow it, this is perhaps the simplest option for you.

Some distros (e.g. Puppy) are designed to be run like this - and copy to RAM at boot, so are faster than anything else once loaded. I've not used Puppy for a few years now, but I suspect it still boots in under 1 minute on old hardware from CD.

The other thing to consider with Live CDs is to ensure they don't give the option of install / run as LiveCD at boot each time - since this would just be frustrating. Again - Puppy works like this. In fact, I know a UK primary school had corporate PCs donated without HDs (for data security reasons) and used this method - [http://www.linux.com/archive/feature/50742](http://www.linux.com/archive/feature/50742) Since Puppy has always resembled a Win 95 desktop, it is always easily adapted to by non-Linux users.

Another option to try is Austrumi. I really liked it when I used it about a year ago (direct from LiveUSB). It uses the beautiful FVWM in a way I haven't seen done before for old hardware - so it may be a little confusing for those used to a Windows interface. Also - it used to default to Latvian language, although that may now be different.

Peppermint looks like a nice web-centric option, if it can do the same - although it does not boast a usable LiveCD experience.

An internet cafe type experience might be a good option - if such a distro exists. i.e. deletes all user files etc at logoff.

---

### Post by HermanAB on 2011-01-06
Yup, Puppy would be my choice too.

Run it, configure it, save the settings, keep a master disk and replicate.  Give the management a stack of disks and they can hand one to each new guest.

Guests can boot the disc, do what they want and save their work back onto the CD.  The CD should last till the guest leaves the house and then he can take it with him.  This preserves privacy for the users, and provides a zero maintenance system while the cost of the discs is near zero.

---

### Post by ugm6hr on 2011-01-06
A "trial" might be sensible... Perhaps consider putting LiveCDs in the drives of 2 of the computers and re-setting the boot options, after telling residents of the trial. Then ask for feedback after a couple of weeks.

If they prefer their existing virus/spyware-ridden experience on Windows - there is little value in pursuing this... Online risk is not something that most people know or care to know about.

If going down the LiveCD route, consider whether CD-R or CD-RW offers the best option for the residents / house with regard to "choice" vs cost.

Good luck! Let us know what you (and they) decide.

---

