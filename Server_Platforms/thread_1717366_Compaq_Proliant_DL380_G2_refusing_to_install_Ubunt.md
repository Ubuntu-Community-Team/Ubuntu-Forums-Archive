---
title: "Compaq Proliant DL380 G2 refusing to install Ubuntu Server 10.10"
date: 2011-03-29
forum: Server Platforms
---

### Post by twocvbloke on 2011-03-29
I guess that the other thread I tagged onto (See [HERE]("http://ubuntuforums.org/showthread.php?p=10593837")) wasn't working, so I'm making my own...

I have a Compaq server, as per the title, and I wish to install Ubuntu Server onto it but ran aground when I found it got to trying to run the installer after the CD Boot menu, it just stopped there, waited 180 seconds (as per the error's details) and then locked up with the Caps Lock & Scroll Lock lights on the keyboard flashing.

Now I know it's not the server, as I have installed other OSes onto it in the past, including an older version of Ubuntu server (9.04), I did try and re-install the 9.04 version but the CD I had was too scratched up and got to a point in the installer (copying files) where it just failed cos it couldn't read the disc. 

Any thoughts or fixes for this? It's annoying having my server sat there unable to do anything... :(

The specs of the thing are:

Dual PentiumIIIs 1.4GHz
512mb RAM (keep meaning to upgrade it)
3x 18.2GB 10k SCSI HDDs (Storage)
1x 18.2GB 15k SCSI HDD (OS)
Smart Array 5i Plus Controller
DVD-ROM/CD-RW
3.5" floppy

Not sure what else is in there, but the full specs are on the web... :)

---

### Post by R.Bucky on 2011-03-29
I have a ProReliant similar to yours. However, I removed the RAID controller and installed WD Caviar Black SATA drives in RAID1 via mdadm in Ubuntu. I suspect that your controller is looking for software to interface with and not getting it. Just a guess.

---

### Post by twocvbloke on 2011-03-30
Unfortunately, this server's Pre-SATA, being a Pentium III DL380 G2 (later models look identical externally, but the innards vary), it's only got SCSI for the HDDs and I think 1x IDE channel for the optical drive...

As for things looking for software, I'd have thought that the current Ubuntu Server installer would know about industry standard controllers, as per it's predecessor, so I'm not sure what's changed between 9.04 and 10.10, but something's been changed and it's had an adverse effect... :(

As for removing the controller, well, if I did that, wouldn't that mean the drives will be inaccessible? 

I just want to use the server as a file store, although the storage in there is not exactly that big, but I do plan to buy some bigger hard drives to replace the 3x 10k drives...

I have to admit, it's been a long time since I dealt with configuring servers, and back when I was doing that (early to mid 2002), I think my server would have set me back about £2-3.5k, or something like that, way out of my price range, but I got it last year for £23, amazing how the price of technology falls over the years!!

---

### Post by twocvbloke on 2011-03-31
Seeing how nobody appears to be interested in offering a solution for 10.10, where can I download 9.04? I know that one works, but there's no "Previous versions" on the Ubuntu site that I can see... :confused:

Reading another thread on an older version, it's been recommended to "use the latest supported version", but, if people can't install it, then they cannot use it, either through hardware compatibilities or because the new versions just won't work... :roll:

I always saw linux as something to revive old hardware, but I think it's beginning to look like it's steering away from that into the domain of the big M$, only offering it for the latest stuff and leaving old hardware to gather dust, I'd love to be proven wrong though, but that is how I see it...

---

### Post by samosamo on 2011-03-31
> **twocvbloke said:**
> Seeing how nobody appears to be interested in offering a solution for 10.10, where can I download 9.04? I know that one works, but there's no "Previous versions" on the Ubuntu site that I can see... :confused:

Reading another thread on an older version, it's been recommended to "use the latest supported version", but, if people can't install it, then they cannot use it, either through hardware compatibilities or because the new versions just won't work... :roll:

I always saw linux as something to revive old hardware, but I think it's beginning to look like it's steering away from that into the domain of the big M$, only offering it for the latest stuff and leaving old hardware to gather dust, I'd love to be proven wrong though, but that is how I see it...

Ubuntu is just a distribution of the GNU/Linux operating system. Therefore, it's useless to make any assumptions when you've only tested one version of one distro.

If you aren't familiar with Ubuntu's regular releases, I suggest you read up on them as you may find Ubuntu 8.04 LTS is what you are actually looking for.

My last piece of advice is that you should check out virtualization solutions. Much like you, I used to do all my learning and development on old servers. A half dozen of them. I threw them away after I virtualized them on one single virtual host. You don't have to be wasting your time with Pentium3 hardware.

---

### Post by twocvbloke on 2011-03-31
> **samosamo said:**
> it's useless to make any assumptions

Yes, like assuming I have only ever used one version of linux, I have used Linux Mint, Ubuntu, Ubuntu Server & Kubuntu (many versions of all three since about 2005/6), Red Hat, OpenSuSE, Gentoo, and a few others I forget the name of...

I'm not learning or developing, I did all that years ago and decided I didn't like it, so went into building and repairing computers & laptops, I just have my server for file storage, and I want an OS that I know works and I know will operate the HP software needed to control the fans and power management, I know from past experience that Ubuntu is relatively easy to use, and has been recommended for my Compaq server, but, if I can't install it, I can't use it...

And I'm pretty sure it's 9.04 I want, as that is what I had, I'm not bothered about long term support or whatever, I just want my server to run an OS that can handle my files... :roll:

---

### Post by Pisnaz on 2011-04-20
Funny enough I just pulled my server up for a maintenance check and setup.  (circumstances at the moment preclude me using it) it is the same as yours.  I have Deb on it now and was mulling over Ubuntu server as I am getting lazier.  I will see what happens, if I get the same problems I may be able to figure it out and get you a solution.  I do know Deb works, as well as Centos.  
     
The main trick will be getting Hpasm I think for fan control and such to play nice.  It has been a few but it passed the serv check this am and is waiting for some writes and wipes to verify drives were not abused on the trip across the country.
     
I will try to let you know what happens tomorrow, know this is a tad old butat worst it may help somebody else.  Considering my old one I just retired was a quad proc PP200 proliant 5000 this is a walk in the park usually to deal with quirks.

Pisnaz

(edit as I got thinking) 
Not to sound like a smarmy **** but you did get the 32b right, not the default 64b version?

---

### Post by usatonycuba on 2011-04-20
**@Moderators, I think it is not very suitable reply to this thread this way, but I'll do so ..  it's really how I feel.. sorry if Im  mistaken**

[QUOTE=twocvbloke]Seeing how nobody interested in. Appears to Be Offering a solution for 10.10[/QUOTE]

That's why they call it Forum, free help, people willing to help others for free, but....  I think you should give some time, while someone tries to see how to grant a reasonable and good help.

At this very moment (this thread has 138 Views) ... ..how many ..of those 138 who have read this thread, do you think are advanced users ??.. I guess that you know that answer... So, If (as you say) That You Have Used ... > Linux Mint, Ubuntu, Ubuntu Server & Kubuntu (many versions of all three Since about 2005 / 6), Red Hat, OpenSuSE, Gentoo, and A Few Others I forget the name of ..... then I think... as an experienced user.. you must understand: What is a forum?, and how Forums support is provided .. and who are the people that offer such support.

Sorry, but it's like someone whant to blamed you, for having used so many Distributions **Since about 2005 / 6**, an just Join The Ubuntu Forums.. on Mar 2011...? ... would that be fair?

[QUOTE=twocvbloke]I always saw linux as something to revive old hardware[/QUOTE]
More than that.. but that too
[QUOTE=twocvbloke]but I think it's beginning to look like it's steering away from that into the domain of the big M$, only offering it for the latest stuff and leaving old hardware to gather dust[/QUOTE]
After 7 Distribution that you mention (and ...** A Few Others that you forget the name of..**)..?  ..you still dont know the differences?... For the simple reason that no one have answered the thread as expected?... 
[QUOTE=twocvbloke] I'd love to be proven wrong though...[/QUOTE]
R U ? ... I do hope so

**PD:**
Everything I have said, it is my own point of view, has nothing to do with the ubuntu forums members/users or its staff and moderatos, and always with the greatest respect for you .. No offense.. GL

(10 minutes after the last thing I wrote down) Just a thought: I have more than 7 years with Gentoo Linux (since code-line), and as a year more of it.. with Ubuntu (Desktop and Server) .. and still need (a lot) of the great community of Ubuntu and Gentoo, to solve many of my issues .. I imagine your frustration with more than 7  distributions in only 7 years.. that is almost a record .. my respect for you.

---

### Post by Pisnaz on 2011-04-20
Well I tried it on my DL380_G2 and had no issues at all.  Well to be fair I am formatting and building the encrypted disks so taking time now to write.  

I just started with no attempt to avoid issues and it has been running seamlessly.  I am going on a limb but did you do a MD5 sum of your ISO, and are you sure your ROM drive is up to snuff?  I know some of my early issues on this server were due to that, but I also modded in a DVD drive and such so it was expected till I got it fixed.  

Hope this helps and gives you some idea to try.  Personally I would run a MD5 sum on my ISO file, download as needed again and run a live cd of something to check the ROM is not the source of the issues.  Also sometimes as you probably know burning at lower speeds is helpful all depends on that drive.  

Luck, and need any help with it let me know.

Pisnaz

As usual sit back with a coffee and have a thought to follow, there may be a chance your ram is the issue, try pulling from 512 to 256 assuming like mine yours is in 128Mb sticks, if memory serves me these must be paired so think you can not go to 128.  Not common but it happens, depends if yours was sitting or such or was running and you just took it offline for a update.  

The controller is working with no issues, and I suspected as much as the Compaq/HP controllers have never been huge issues in the more, shall we say, mainstream distros.

---

