---
title: "[SOLVED] Noob Network to Server Questions!"
date: 2008-10-14
forum: Server Platforms
---

### Post by Kellemora on 2008-10-14
Hi Gang

Now that I have everything working perfectly, do I dare change over to setting up as a server instead.  That's a comment not a question!

Here is the Scenario:  I have three desks, each with it's own computer and user, now everything is Ubuntu, no more Doze here.
I also have 3 other headless computers within this Network, tied to  the computer in my desk using a KVM switch.

Each of the 3 headless computers are used primarily for data storage, each one for a particular type of data, just for convenience sake is the only reason.  And easier backups too.

I have read the Ubuntu Server Guide and several other informational sights as well.  That don't mean I understood what I read, and none really answered my questions.

OK, now for the questions only a Noob can come up with.

Question #1
I'm going on the premise that in Linux, namely Ubuntu, that the location of the physical hard drive is irrelevant as it appears as if it's on the computer viewing it.  Quite unlike simple file sharing?  All drives, no matter where they are located would be MOUNTED in the Server?

That being the case, my thoughts are leaning in this direction.
By setting up a Server, everyone can LOOK TO the Server for the files they need to work on.  They will no longer have to remember WHICH computer the hard drive is located as the Server will handle that for them.

In other words, I can have a Server as the HEART of my system!

Question #2
What about the actual programs themselves?
Does Open Office for example physically need to be installed on EACH computer, or could it be installed on the SERVER and each of the desks become a dumb workstation?  I know some programs are NOT multi-user, so would not apply to those.  Nor does having a separate program on each computer really hurt anything.  I'm just thinking of a reasonable purpose to use a server.

Question #3
If the person at desk one is using a file from the server that it actually drew from computer sevens hard drive, this drive would then be mounted on the server, BUT would only the FILE be mounted on the desk one computer or would the whole hard drive, and if so, would it still be accessible to other users not working on the same file?

I do know about the problems of two people working on the same file at the same time.  That would not happen in our situation as each person is assigned their own files to work on.

Question #4
I don't need things most servers are used for, such as Apache, or connection from the outside world.  Other than we do have Internet for mail and web browsing, that currently works through the router and LAN so that ALL computer can access the Internet at the present time.
But the more I think (which could be hazardous), it seems that using a Server would simplify a lot of the extra steps we have to do in order to accomplish many menial tasks.

Could you explain in your own words, so an old geezer and idiot can understand what a server can really do and what it can't do as far as a simple home/office type LAN setup.

We did at one time have a Print Server, an older computer used to drive several printers all at once and it saved us TONS of headaches and work.

In my head, I'm thinking of a Server as being the main computer everyone uses, and the existing computes as being just workstations.  I'm also thinking of placing the /home directory for each user on the server as well, or if not the /home directory, then the /home/users directory.

Everything I've read so far seems to dictate that a Server is the way to go.  But then they get into running web sites, POP3 accounts and all that stuff I don't need.

I know in the Doze machines, each Program must be on the machine itself!
But, in Ubuntu, if the hard drive appears to be on the machine from being Mounted (and there is no Registry), it seems that a Program should be able to reside ANYWHERE and still appear to be on the machine it is being used on.
If I'm wrong about this, don't hesitate to say so!  Because my understanding of what I'm reading may be totally wrong.

In less than 1-1/2 months, we've already gone from using Doze to only have one last Doze machine left, and that is for accessing things that we cannot yet do on Ubuntu until we convert those files over properly and fix them up.  It's not exactly connected to the LAN anymore directly.  It now has it's own cable to the router, but has the same workgroup name for easier access.

I guess I need some ideas, and pointers as to what else to read that might be geared more toward small office server instead of running and ISP or web presence.

Thank You

TTUL
Gary

---

### Post by volkswagner on 2008-10-14
Topics too advanced for me are users working on the same file at once, apps running on the server vs. workstation.

I think you can benefit from one server (basic file sever), providing storage for the three work stations.  Having workstations access mounts on the sever can be done with simple NFS.

I have this book marked, it is an excellent NFS how to.

[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

If all work will be done in the directories on the server, one backup of just the server should suffice.

If you are interested in a work station/server environment than take a look at Edbuntu.  The apps may not apply but the theory/architecture does.  

[http://edubuntu.org/]("http://edubuntu.org/")

---

### Post by Kellemora on 2008-10-14
Hi VW

Actually, that first link is how I have my office set up right now!
Unless we have to reboot for some reason, the mounted files used by each person stay on their Ubuntu desktop.  Getting them back after a reboot requires me to go see if the IP number changed, normally it doesn't, but if it does, then I have to jump through hoops to get everybody up and running again, hi hi.........

I had read a little bit about edubuntu and just figured it was ubuntu with some kids programs added.  I DO KNOW it is set up as a main server with dumb workstations.

The main reason I am interested in this was because I have several older AMD K6 machines here.  I keep them off the LAN because they used to drag the whole LAN down to 10 from 100 before we got the new hubs.  It is to these old K6 hard drives that we save the archival backups to.

I picked up a 1.6gHz Pentium 4 machine with a blown OEM hard drive and stuck a 10gig and a 4gig into it, just to have a machine to learn and experiment with Ubuntu on.  In other words, I try it here first before implimenting it into my working system.  Ubuntu /root and some system files are on the 4gig drive.  But most application and program files plus their (dependencies) are on the 10 gig drive.  No user data is stored on this machine at all, although I do have a /home/user directory for temporary use while trying things on that machine.  It's fed to my KVM switch so I use it from my own desk.  

I talked to my brother since he runs a large server, but he knows very little about it.  A contracted IT service company maintains that part of his office equipment, the only thing he know is that is running under Red Hat Linux.  I sorta doubt that and would more than likely say its probably Mickey$oft net framework, because ALL of the desktops in his company, including his own are all windows XP machines.  He tried Vista and it cost him a week of shut down time to revert back to XP.  The only thing not on it is their primary accounting, which he maintains an a smaller networked system that only he touches.  I think he still uses Cougar Mountain's Accounting packages.

Using a KVM is great for MY machines.  But I can't see the other machines except through the shared folders on those machines.  Which means I have to get up and GO over to those desks everytime they need something done with them.

I'm 61 years old this month, not new to computers, but new to messing with OS's.  I did Basic programming eons ago and have had computers since the Heath/Zenith H8 Octal Entry and first Apple 1 Motherboards.  But then technology zipped right past me and I've just been a USER not a Doer ever since.

I was told the older machines, like my AMD Athlon 1.4mHZ machine would be better suited as a server and keep the newer machines as the working machines.  Makes sense in one way, since the server wouldn't be using GUI's.

But I truly know absolutely NOTHING about Servers at all.

And everytime I start reading something, within the first few paragraphs they are already way over my head with the terminology they are using to explain things.

I've read THREE massive TOMES written by Naba Barkakati covering Red Hat Linux 6, 7 and 9, BEFORE I found out it has nothing at all similar to Debian based Linux.  I only had Red Hat 6 from days of yore and thought Linux was Linux, didn't even know about Distro's until like 2 months ago.

So I HAVE come a long way in a short time, even if I do say so myself, hi hi........  I've gone from 8 Mickey$oft machines to 7 Ubuntu machines and one triple boot Doze XP (until we change the files over) that also now has Ubuntu and Debian on it.  I tried CentOS also when I was first studying Distro's, Knoppix too for that matter.  But after using Ubuntu for only 2 days, I was sold and began the process of converting all of our machines over to Ubuntu.

Hey, I'm beginning to ramble here, forgot it was a Forum!

Thanks for your suggestions!

TTUL
Gary

---

### Post by Kellemora on 2008-10-15
Hi VW

I came back to mark this thread solved, and to say thanks!

I did some more study on the edubuntu and learned a little more from the beginners forum as well, who sent me to some Thin Client documents.

It helps finding things when you finally learn the names of what they are called in Ubuntu, hi hi...........

TTUL
Gary

---

