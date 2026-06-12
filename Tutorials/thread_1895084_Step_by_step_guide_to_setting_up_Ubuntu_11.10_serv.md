---
title: "Step by step guide to setting up Ubuntu 11.10 server for Newbies!"
date: 2011-12-14
forum: Tutorials
---

### Post by bvz on 2011-12-14
**Update 1/7/2012:**
Updated the UFW section to add a new in/out rule for dhclient
Updated the NETATALK section to use a newer version of Netatalk and a different afpd.conf file
Updated the NETATALK section to have a better prompt when using ssh or the console



[B][SIZE="4"][COLOR="RoyalBlue"]Section #1 - Introduction
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]

Hello,

I have set up a small server at my home to handle some basic NAS-like functions for my network of Macs.  I knew that I would have a hard time repeating the steps should I ever have to do it again so I documented the process.  Well, that sort of snowballed and I wound up writing a fairly in-depth HOW TO on the process.  Partly because I felt there wasn't anyplace where there was a comprehensive guide to doing what I wanted to do, and party because the act of "teaching others" actually makes me learn the process more completely myself.  I am aiming this guide at relative newbies to the Linux world (though I expect a certain amount of technical savvy regarding computers in general).

I tried to document not only the steps needed to recreate what I did, but also the basic knowledge needed to understand what exactly each step does.  In this way, even if individual users need to stray from the exact path I have taken, they should be armed with enough knowledge to adapt the instructions to their particular needs.

I am going to break the process down into several sections so as not to overwhelm anyone with a single block of text.  Questions and comments and critiques are welcome.

A note to the moderators: If I am posting in the wrong forum or breaking any rules here, please let me know and I will gladly adjust accordingly.






[B][SIZE="4"][COLOR="RoyalBlue"]Section #2 - Who wrote this guide and who is it for?  DISCLAIMERS!!
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]



**_[SIZE="3"]Part 1:  Who wrote this guide?  (Disclaimers!)[/SIZE]_**

Well, I wrote it of course!  :)

More specifically, I am a complete newbie to setting up and administering a server.  Everything here is stuff I learned by searching the web over the past month or so.  Prior to that, I had never used ssh, firewalls, netatalk, or anything of the sort.  I *have* been using a Linux operating system as an end user at work for over 10 years now, so I am comfortable with navigating via the command line.  

But beyond that, I AM COMPLETELY NEW TO ALL OF THIS!

Knowing this, take everything I post here with a huge helping of salt.  I researched this as best as I could, but there are absolutely NO guarantees that I haven't done something completely wrong.  I have, however, implemented all of this at home and it appears to be working.  I am also (he buffs his nails on his shirt) a pretty smart guy.  That said, hopefully the many folks here who are even smarter will chime in and correct any mistakes I have made.  I will attempt to update and edit the guide based on these comments.

And, finally, the requisite: 

**[COLOR="Red"]I TAKE NO RESPONSIBILITY IF YOU MESS UP YOUR SYSTEM, DATA, SENSE OF BALANCE, MARRIAGE, WHAT HAVE YOU.  [/COLOR]**

Even if you follow my instructions to the word.  Seriously.  I did my best here, but I am only posting this as a courtesy.  Go in with your eyes open.



**_[SIZE="3"]Part 2:  Who is this guide for?[/SIZE]_**

This guide is intended for people like me.  You are reasonably computer savvy but you don't know the first thing about setting up a Linux server.  You can figure things out when they are more or less obvious (i.e. you won't need a tutorial to use the nano text editor - but using vi might be beyond your immediate comfort zone).  You have used the command line, but not much beyond changing directories and moving files.  You haven't spent any time thinking about computer security other than to complain when you are forced to use a capital letter AND a number in a password (oh, the unjustified indignity!)  You may have heard of ports and port forwarding, demilitarized zones, network address translation (NAT), routers, and the like but are pretty muddy on what this all means.

Of course, if you are more advanced, this guide might still be of some use.  Who knows.



**_[SIZE="3"]Part 3:  How hard is this going to be?  I see a lot of text here...[/SIZE]_**

This isn't that hard.  Now, you might get a little freaked out by the amount of text in this guide, but don't be!  I can be a wordy person, but I also do my best to be clear and concise when needed.  The large amount of text is intended to simplify the process by explaining what each step does and why I elected to do it.  

If you get past the amount of words and let yourself just read it one sentence at a time, it should be a fairly quick, easy, and painless process to follow.  I have made my best effort to format the text in a way that is consistent, clean, and easy on the eyes.  Personally, I usually do better when reading instructions that are printed on paper (vs. reading directly from the screen).  If you are like me, you might consider printing the guide out and reading it through a few times before you go to bed.  At the very least I expect it will be a fairly effective counter to any insomnia you may have.  Be forewarned though, it is a lot of paper!

Although this server build isn't too difficult a process (mostly thanks to all the hard work done by the Linux open source community, the many folks who kindly post their own tutorials, the folks at the Ubuntu and LinuxQuestions forums, as well as Canonical), it surely isn't a 10 minute install and go scenario.  For that, you might consider FreeNas ([http://www.freenas.org/](http://www.freenas.org/)).  Alternatively, if you prefer Linux, you might also consider OpenMediaVault ([http://blog.openmediavault.org/](http://blog.openmediavault.org/)) which is based on Debian Squeeze and looks like it is shaping up to be a really nice, easy to install and manage solution.

Personally, I prefer building my own server for the simple reason that it forces me to really understand how the system works.  It also offers me the ability to customize the features that I want (which, as you will see, are not standard).  I might switch to OpenMediaVault some day since it is also based on Debian.  But if I do, I will have had the experience of setting up this server and that will allow me to customize OMV for my needs.  On the other hand, I may go crazy and install arch linux.  Either way, this is a great way to start learning how to manage your own server.

Finally, if you just parrot what I do and blindly type in what you see me typing here you are pretty much guaranteed not to get a working server.  In most cases you will have to slightly bend and tweak what I have done to get it to work for you.  That is why there are so many words.  They are there so that you can understand *why* I am doing something and then let you adjust accordingly for your particular situation.

Ultimately though, just read it one sentence at a time and you will be fine.



**_[SIZE="3"]Part 4:  Miscellany.[/SIZE]_**

If you have any questions, comments, or critiques please post them!  I will do my best to respond (but also know that I work from 8-7 and have a bazillion projects on the weekend, so there may be a delay before I get back to you).

Finally, I really relied on a number of websites and forums to put this together.  To the extent that I remembered, I have included these links here.  But a lot of people spent a lot of time posting a lot of useful information and I am sure I am only crediting a tiny fraction of those who helped me.  I'm sorry if I missed mentioning them all, but there you go.





[B][SIZE="4"][COLOR="RoyalBlue"]Section #3 - What are my goals for the system?  What are the limitations?
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]

Here is a brief rundown of the goals of this system:


**_[SIZE="3"]Part 1:  This machine will be a file server, a Time Machine backup drive, and a media server in my home.  Nothing Else.[/SIZE]_**

This part is fairly self explanatory.  I intend to have this system be on (though sleeping most of the time) 24 hours a day.  It will serve files to a local network of Macs (3 genuine articles, and one Dell mini 10v hackintosh).  It will also be a network drive to which these Macs will back themselves up via time machine.  Finally, it will serve music and movies to any of the machines.  But that is it.  It will not be running bittorrent, MySQL, Apache, etc.  It will not serve web pages or crunch any data.  I have modest needs and I prefer the security of having as few services running as possible.

It will not be a high-performance server.  It can stream multiple musical tracks at once.  It can stream movies.  But it isn't intended to replace your primary drive on your Mac.  Instead think of it as a media and file repository that you use to stream media or access archived files.



**_[SIZE="3"]Part 2:  There are actually going to be TWO servers in two different locations.[/SIZE]_**

Eventually, there will actually be two identical machines.  One will be located in California.  The other in Washington DC.  They will be identical in both hardware and software.  They will differ only in the actual user accounts (though the administrative user will be identical on both).

Each of these servers will back themselves up to the other (i.e. mirror all of their data to their partner across the country).  That way, if my server gets crushed in an earthquake here in California, all of the data will be safe in the great District of Columbia.  And vice versa (I mean, hey.  They just had an earthquake there.  Freaky, right?)

But that portion of the tutorial is currently missing because I am totally broke and cannot afford a second machine right now.  Still, I will offer a basic outline how something like that would work.



**_[SIZE="3"]Part 3:  Thoughts on system security.[/SIZE]_**

Because these servers will be partially "naked" out on the internet (i.e. I will need to access them remotely) I have spent a fair bit of time trying to make sure that they are secure.  A lot of the steps I am going to take here may smack of overkill but I think multiple layers of security can only help.  Specifically, as I am new to all of this, layering security helps protect against the consequences should I accidentally mess up one of those layers.  But, this should serve as a reminder that I really don't have much of a clue as to what I am doing.  I am just synthesizing what I have been able to glean from google searches.  Real security experts, please chime in!



**_[SIZE="3"]Part 4:  A note about OSX vs. Windows.[/SIZE]_**

I only have Macs, so this guide is directed pretty much exclusively to them.  That said, much of what is described here should be easily translatable to a Windows network.  It's just that I'm not going to do that (for pragmatic reasons, not religious ones).  If someone reads this and manages to add Windows specific tips, I'll try to insert them here.  

Alternatively, you could just ditch the dark side and convert to OSX which is all sunshine and roses.   (I kid!  I kid!)



**_[SIZE="3"]Part 5:  The hardware.[/SIZE]_**

Here is the hardware I am using for the server:
[INDENT]
	Intel D510MO motherboard (dual atom cpu)
	OCZ ssd drive (to store the Server software)
	Rosewill 4 port SATA II card (rc-217)
	4 Western Digital Caviar Green 1TB drives in a RAID 5 configuration
	FSP AURUM SERIES Gold 400 power supply (80+ GOLD)
[/INDENT]
[COLOR="red"]Note: I cannot recommend this configuration.  I am currently having difficulty with the S.M.A.R.T. reporting with this combination.  Turning on regular S.M.A.R.T. monitoring seems to lock the server up with some consistency.  That said, all of the steps that I outline here that have to do with S.M.A.R.T. are solid and with luck, my problems should not be your problems (unless you also have funky hardware).  I will update this post once I have replaced some of the equipment with better specs.[/COLOR]





[B][SIZE="4"][COLOR="RoyalBlue"]Section #4 - Define your terms!
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]

Since this is a guide for us newbies, I think it would be appropriate to define some basic terms here.  Again, keep in mind that I am new to all of this as well, so if you have a better definition, please chime in.  Also, if I made a mistake, let me know.


**_[SIZE="3"]SSH: [/SIZE]_**

This is a protocol that will be used to remotely administer your server.  It basically lets you open a terminal on your local Mac (or PC)  and start typing in commands as though you were physically working on the server.  It has all sorts of security features to try and prevent evil people from hijacking your computer or listening in on the commands you are sending.  You may have multiple ssh connections to your server at once, making it easier to edit a config file in one, and run terminal commands in another.



**_[SIZE="3"]Public/Private Keys: [/SIZE]_**

Most of us are used to the security model that relies on a user login (name) plus password.  If you can supply both pieces of information, you are allowed into the system.  Of course, if your login is easy to guess (say, your first name) evil-doers already have half of the information they need to get in!  If your password is easy to guess (or crack because it is a regular word found in the dictionary) then the walls to your digital kingdom are little more than decoration.

Key based security changes this model, making it much more secure.  You can think of Public/Private keys as sort of being a Lock/Key system. (A note to experts:  I know this is not at all how it really works, but I think it is a useful analogy).  To use key-based security, you generate two keys using a program running on your local machine (my Mac in my instance).  You store the public key (acting as a lock) on any system you want to remotely log into.  You store the private key (acting as a key for this lock) on the computer you will be logging in from.  This private key is itself locked up with a passphrase (essentially a password that is a full sentence including punctuation). Think of the local key as being locked up inside a safe with a combination lock on it (where the combination lock is your passphrase). 

To log into a remote system, you first supply your passphrase which unlocks your locally stored private key (think of opening the safe).  This key is then used to "unlock" the public key that resides on the server.  If everything "matches up", you are authenticated and can start using the remote machine.

Now, don't mistake the passphrase that unlocks the private key for a password that unlocks the remote server.  The passphrase only unlocks the key that resides on the computer you are sitting in front of (again, the passphrase is analogous to the combination to the safe that holds your key).  If you were sitting at a different computer (one that did NOT have your private key stored on it) simply typing in the passphrase would not let you log into the server.  You must have this private key file physically residing on the computer you are logging in from.

Why is this more secure?  Well, there is a ton of complicated cryptographic stuff going on in the background, but on the surface consider what it takes to break into a machine that does not use key based security:  Once someone manages to get both your login and password (either by guessing, cracking, or social engineering) they have full access from anywhere in the world.  Compare that to what is needed to break into a machine that uses key based security:  They would still need to guess/crack/steal your login but without the actual key file that is stored on your (hopefully) non-remotely accessible computer, no access is possible.  Even should your key be stolen (say your laptop is stolen), assuming you selected a reasonably secure passphrase, it would be useless because the key would still be protected inside the "safe".  That would buy you enough time that you could then change the public key on your server long before any could ever hope to crack your passphrase (if, in fact, they ever could).



**_[SIZE="3"]cron/crontab: [/SIZE]_**

cron is a process that allows the user to run arbitrary commands on an arbitrary schedule.  For example, should you want the server to check the hard drive temperatures every five minutes, you would instruct cron to run the hddtemp command once every five minutes.  cron can be tasked with running any number of commands on any frequency as long as it is greater than one minute (i.e. it cannot execute commands any more frequently than one minute apart).  For example, you can have a command executed every minute, and a second one executed only every Sunday night at 11pm.  crontab (vs. cron) is simply the file that configures which commands should be executed at what time.  We will be relying on cron to control basic server maintenance.



**_[SIZE="3"]IP Address:[/SIZE]_**

This is like a telephone number or street address for your computer.  If you want to connect to the computer, you will have to "call" it at this number (or "visit" it at this address).  The IP Address of a computer is not always constant.  Often (usually for home computers) it will change from time to time.

Also, there is a concept of a local address and public address.  Typically, in a home user setting, your router (the device that is either connected directly to your modem or is actually integrated with your modem) will have a unique public IP address.  This address is completely unique among all the IP addresses in the world (although it may change from time to time and the address you had yesterday may belong to your neighbor today).  Behind your router, each of the computers on your home network will also have a unique IP address, though it is unique only with respect to the other computers on your local network.  This is a local IP address.  These local IP addresses are reused all over the world, but are sequestered behind their routers which keeps them from interfering with each other.  The best analogy I can think of is a business with a single public phone number and multiple internal phones, each with their own extension.  While the reception desk has a single phone number that is completely unique in the world, each extension (say 1454) is used over and over at different companies everywhere.  

Local IP addresses usually fall into one of several ranges:

172.16.1.* where * can be any number between 1 and 255
196.0.10.* where * can be any number between 1 and 255
10.0.0.* where * can be any number between 1 and 255

There are several methods commonly used to indicate a range of IP addresses.  

172.16.1.*
172.16.1.0-255
172.16.1.0/24

All of these mean the same thing:  The range of addresses from 0-255 on the subnet that starts with 172.16.1.  Some tools that deal with IP ranges will require one format.  Some require another.  



**_[SIZE="3"]NAT:[/SIZE]_**

Network Address Translation. Typically your router will have this built in.  Basically it masks the IP address of your home computer behind the public IP address of the router.  So, internally you might have a machine with an address of 172.16.1.11, but externally it shows up as 132.456.23.66.  To use the phone number analogy above, it is like calling the central switchboard of a company (the public IP address) but not knowing the internal extension of the person you are trying to reach (the local IP address).  Without the internal extension, undesired calls can be stopped at the switchboard (aka, your router).  Even when the router passes data on to the local machines, the outside world is never made privy to their actual IP addresses.



**_[SIZE="3"]Ports:[/SIZE]_**

Note: I read the following analogy somewhere on the web. Apologies for not being able to credit the originator, but I forgot to save the web address.

One way to think of your computer is that it is like an office building.  Its IP address is like the street address of the building.  Each suite in the building provides a different service, as long as you are able to get in the door.  Ports are like the suite numbers for these offices.  

If you want to get a new filling for your teeth, for example, you would go and knock on the door of your dentist (suite 22 for example).  If you wanted some law advice, you would knock on a different door (suite 80 for example).  Of course, many suites are vacant (suite 22,512 for example) and knocking on them produces no results.  

On your computer, once you have the IP address (comparable to the street address of the building), you can try to connect to any port number you want (just as you could knock on the door of any suite in the building if you so desired).  

SSH, for example, typically listens on port 22.  If you want to ssh into a computer, you would first obtain its IP address and then try to connect to (knock on) port 22.  Once the ssh server answers the knock, you can then start negotiating your admittance.  

Web servers typically run on port 80.  If you want to visit a web site, you would once again obtain its IP address and then connect to (knock on) port 80.  When you use a web browser, this is the process that is running behind the scenes.

Having lots of ports "open" (i.e. listening for knocks) is a security risk.  Even if the port is password protected, it is conceivable that someone could sneak past that and get into the "office".  In fact, there are automated tools that simply go around and try to connect to every port on every IP address they can find. The are looking for an unprotected (or poorly protected) opening.  For example, since port 22 is known to be the port typically used for ssh, this port is often targeted with tools designed to take advantage poorly managed ssh implementations.



**_[SIZE="3"]RAID:[/SIZE]_**

RAID stands for "Redundant Array of Inexpensive Disks".  Or at least it used to.  Apparently the word "Inexpensive" offended some folks, so now it stands for "Redundant Array of Independent Disks".  Way less fun name.

Regardless, RAID allows you to store your data across several disks in a way that either speeds up access, improves data integrity, or does both.  I would highly recommend reading the Wikipedia article on RAID.  It is comprehensible and offers a lot of useful information: [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

Most home server RAID configurations are focused more on fault tolerance than performance (i.e. RAID "levels" 1, 5, or 6).  By adopting one of these RAID levels, you can survive having one or more drives fail without losing any data.  All that is required is that you replace the faulty drive(s) and rebuild the array before an additional drive fails.  In fact, you won't even have to stop using the system as all your data will still be available even while the system is in a degraded state.

Of course, nothing comes for free.  The increased redundancy of a RAID system means you will have to sacrifice some of your storage capacity for this level of protection.

RAID 1 mirrors your data across an any number of drives. (each drive is an identical copy of all the others.).  This cuts your actual storage space by the number of drives you have.  For example, if you have two one-terabyte drives, you will only have one-terabyte of storage available.  If you have four one-terabyte drives, you will still only have one-terabyte of storage available (but four copies of your data).  RAID 1 can lose n-1 drives and still function where 'n' is the number of drives you have (i.e. as long as one drive continues to function, no data has been lost).  Typically RAID 1 is limited to two drive setups due to the amount of storage space lost in more than two drive arrays.

RAID 5 distributes your data plus parity information across a minimum of 3 drives.  This cuts your storage by 1-1/n where n is the number of drives you have.  In other words, if you have 3 drives, you will get a total of 2/3 (1 - 1/3) of your total drive space.  If you have 5 drives, you will get a total of 4/5 (1 - 1/5) of your total drive space.  For example, three one-terabyte drives will leave you with two-terabytes of storage space.  Five one-terabyte drives will leave you with four-terabytes of storage.  RAID 5 can only tolerate a single drive failure (no matter how many drives you actually have in the array) without losing data.

RAID 6 distributes your data plus double parity across a minimum of 4 drives.  This cuts your storage by 1-2/n where n is the number of drives you have.  In other words, if you have 4 drives, you will get a total of 1/2 (1 - 2/4) of your total drive space.  If you have 7 drives, you will get a total of 5/7 (1 - 2/7) of your total drive space.  For example, four one-terabyte drives will give you two-terabytes of storage space.  Seven one-terabyte drives will give you five-terabytes of storage space.  The benefit of RAID 6 versus RAID 5, however, is that you can suffer two failed drives before losing data.  This may seem like overkill until you consider the fact that after a single drive failure in RAID 5 (and RAID 1 if you are only running two drives), you are as vulnerable to data loss as though you did not have a RAID array at all.  Considering the fact that a typical home user will most likely not have a spare on hand, this means: ordering a replacement, having the time to install it, and rebuilding the array (a process which can take the computer several days to complete in itself).  Your data could be vulnerable for days if not weeks.  Also, if you purchased your drives at the same time there is a distinct possibility that they were manufactured together.  This increases the chance that they will tend to fail at about the same time.

For the purposes of this server build, however, RAID 5 seems to be the best combination of flexibility and data redundancy.  The entire data set will be backed up to another system across the country.  Losing data to two or more drives will be annoying but hopefully not catastrophic.



**_[SIZE="3"]Software RAID vs. hardware RAID:[/SIZE]_**

RAID arrays can be managed via the CPU on your server, or via dedicated hardware that (supposedly) handles all of the duplicating / parity / striping whatnot.  For most small home server applications, however, having a software RAID solution will most likely be the preferred solution for several reasons:

1) Often hardware RAID is not really hardware RAID.  Cheap RAID cards often do most of their work in software anyway, with only a mild assist from the hardware.  So you are paying for some functionality that doesn't really buy you anything.  In fact, you may be paying extra for a worse situation because...

2) mdadm might actually run faster than many cheaper hardware RAID cards according to some reports.

3) Finally - and in my mind most importantly - If a hardware RAID card fails, chances are you will have to buy the exact same card from the same vendor to ever get your data back.  By comparison, software RAID can run on most any Linux system.  If your hardware fails, any other Linux system running mdadm should be enough to allow you to recover your data.







[B][SIZE="4"][COLOR="RoyalBlue"]Section #5 - Lets get down to work…  Install Ubuntu Server 11.10
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.
- This HOW-TO assumes you are installing the 64-bit version of Ubuntu Server 11.10.  For the most part there should be no issues if you install the 32-bit server that I am aware of.  I just have never tried it and cannot guarantee that it will be exactly identical to what is described here.




**_[SIZE="3"]Step 1: Install a fresh copy of Ubuntu Server 11.10 64-bit and create an administrative user who isn't you.[/SIZE]_**

Install Ubuntu Server 11.10.  The actual step by step process involved is fairly self explanatory, and if you need help there are many many guides on the internet that can help you.  The only specifics that I would suggest are as follows:

--------------------
When asked to install packages, leave them all blank.  We will be installing everything we need by hand.
	
--------------------
If asked about using LVM, select "no".  LVM is an added layer of complexity that our tiny NAS does not need.
	
--------------------
When asked to create a new user, create one that is not your usual login.  I.e. if you usually log in as 'bob' on most of your systems, make this one something like 'admiral'.  Reserve 'bob' for your regular use on the machine, and then 'admiral' will be the login you use to manage the server. 

Note: Nearly all of the examples below assume you are logged in as this user (admiral in this example).  Also note, whenever you see me type "admiral" you should substitute whatever administrative user name you selected.  

Make sure you pick a really strong password!  Don't use a dictionary word, even if it is one of those fancy-schmancy SAT words.  Don't think a "foreign" word is more secure.  Don't use a proper name.  Seriously.  Dictionary words and names are frighteningly easy to crack. 

For example:
[INDENT][I][COLOR="Magenta"]
	shadowcat
[/COLOR][/I][/INDENT]
is an extremely weak password, while:
[INDENT]
	*[COLOR="Magenta"]squibtish1126?[/COLOR]*    <---  silly name + girlfriend's sister's birthday + a question mark
[/INDENT]
is pretty strong and not that hard to remember.  Also, remember this is not your usual login. It is only used when you manage the system.  So even if it is really annoying, you shouldn't be using it very often (only when administering the server).




**_[SIZE="3"]Step 2: Log in and write down the IP address and MAC address of the server.[/SIZE]_**

Log into the server.  You will be doing this directly from the keyboard connected to the machine.  Log in using the administrative user you set up above (admiral in my example) and the really hard to guess password you selected.

You will need to know what the IP address of your server is at the moment.  The IP address may (and most likely will) change later.  I will show you how to handle this as one of the later steps in the process (it involves reserving an IP address for this machine on your router). For now, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	ifconfig
[/COLOR][/FONT][/B][/INDENT]
Look for a line that starts with *[COLOR="Magenta"]inet addr:[/COLOR]* followed by a bunch of numbers.  Note: There may be more than one line like this.  If so, use the line in the group labeled "eth0" (this is assuming you are using an ethernet cable to connect to the network and there is only a single ethernet connector in your machine.  If this is not the case, you may have to do a bit of research.)  Write down the four numbers separated by periods that immediately follow this text.  For example:  *[COLOR="Magenta"]172.16.1.16[/COLOR]*  This is the IP address of your machine and is the address you will use to log into it via ssh later.  Write it down because you will NOT remember it.

Next, look for a line that contains the text: 
[INDENT][I][COLOR="Magenta"]
	Ethernet  HWaddr.  
[/COLOR][/I][/INDENT]
Copy down the six letter/number combinations separated by colons that follow.  This will looks something like: 
[INDENT][I][COLOR="Magenta"]
	a0:32:de:3b:02:2e
[/COLOR][/I][/INDENT]
This is the hardware MAC address of your ethernet card (Note: MAC does not have anything to do with Macintosh.  It stands for Media Access Control).  This is an identifier for your ethernet card and should be unique in all of the world.  You will need this information later when you want to assign a (local) static IP address to your server as well as when you want to wake the machine up remotely.  Write it down because if you think you will remember this, you are completely delusional.



**_[SIZE="3"]Step 3: Update the system to the latest software[/SIZE]_**

Update all the packages to their most up-to-date versions. To do this, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get update
	sudo apt-get upgrade
	sudo apt-get autoclean
[/COLOR][/FONT][/B][/INDENT]






[B][SIZE="4"][COLOR="RoyalBlue"]Section #6 - Give your server a static IP address on your local network
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Unfortunately this section is, by necessity, a bit vague.  I have no idea which router you are using, and every router has a slightly different way of reserving IP addresses.  I am using an Apple Airport Extreme which has a relatively simple user interface.  Most routers use a web-based interface.  In either case, this step shouldn't be too hard, but you will have to use Google to figure out the exact steps.

In general terms, what we want to do is "reserve" an IP address for your server.  Typically, a router runs a DHCP server which will randomly assign the next available IP address to whichever device (laptop, desktop, smartphone, etc.) next requests one.  Servers, however, should always have the same IP address to ensure that we can reliably find them on the network.  To make sure that the server always gets the same address, we "reserve" one with the DHCP server on your router.  The server will introduce itself to the DHCP server using its MAC address (you did write it down, didn't you?) and the DHCP server will respond by returning the reserved IP address.  Other machines without reservations will continue to get a randomly assigned address (but never the reserved address).  You may make multiple reservations for multiple different machines.

Again, I'm sorry if this section is a bit vague, but I will attempt to illustrate by going through the steps using an Apple Airport Extreme.  Between this and googling your actual router model, you should hopefully be able to follow along.



**_[SIZE="3"]Step 1: Open the Airport Utility app[/SIZE]_**

Open the AirPort Utility.app located in the /Applications/Utilities directory

Select your device and choose "Manual Setup"

Click on the "internet" tool bar button and then select the DHCP tab.  There you will see a field called "DHCP Ending Address".  Apparently other routers are smart enough not to hand out static ip addresses to dynamic hosts under any circumstances.  Apple's Airport Extreme, however, will actually hand out a reserved address to any client as long as that reserved address has not been removed from the pool of available addresses.  So, we need to tell it that any addresses 99 and below are dynamic.  Any addresses 100 and above will be reserved static addresses.  To do this, edit the field that is labeled "DHCP Ending Address" so that the last number in the string of dot-separated numbers is 99.  For example, on my system I am using the 172.16.1.* subnet.  Therefore the DHCP ending address is 172.16.1.99.  If you were using the 192.168.0.* format, yours could be set to 192.168.0.99.  Note, I am arbitrarily using 99 as the cutoff point.  You could set yours higher or lower.

Next, click on the + sign under DHCP reservations.  A new sheet will appear asking for a description of the reservation.  I am calling mine UbuntuServer.  Make sure "Reserve address by" is set to:
[INDENT][I][COLOR="Magenta"]
	MAC Address
[/COLOR][/I][/INDENT]
and click "continue".

You will now be asked for a MAC address.  Type in the address you wrote down in the previous section.  Below this, you will be asked to provide a reserved address.  Here is where you assign an address to your server.  I personally tend to set mine at 100 (i.e. 172.16.1.100) because that is a nice, easy to remember address for the server.

Click "done" when you are finished, and then click "udpate".  Your AirPort will restart itself.

After it has restarted, you should probably restart your server to make sure it has taken the correct IP address (remember, you can get that info by typing ifconfig).



**_[SIZE="3"]Step 2: Repeat for any other non-computer devices on your network[/SIZE]_**

For reasons I will get into later, I also like to make sure that any non-computer devices that hook up to the network also use reserved IP addresses.  My network printer, for example.  It gets a reserved IP address in exactly the same way.


Again, I'm sorry I can't be more specific here, but the above steps should be generalizable to your specific router (assuming Google is your friend).






[B][SIZE="4"][COLOR="RoyalBlue"]Section #7 - Prepare your hard drives to be combined into a RAID 5 array
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes: 

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.
- Much of the information in this section came from: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)



**_[SIZE="3"]A short primer on Linux and Hard Drives.[/SIZE]_**

Since you are a bit more technical than the average user, you already understand that you can't just install a hard dive in a computer and start using it directly "out of the box".  If you have used Macs or Windows, you know that you typically need to "format" the drive before use.  If you are an OSX user accustomed to using the Disk Utility application, then you are also familiar with the idea of partitioning your hard drive before formatting it.  Presumably whatever method Windows uses to manage its hard drives is similar.

Basically, in order to user a hard drive on a computer, you need to have:
[INDENT]
	1) The hard drive.
	2) One or more partitions on this hard drive.
	3) A file system on the partitions so that the operating system can store data (aka "formatting"). 
[/INDENT]
Getting drives ready for our Linux server has the same requirements.  The only significant differences between the process you are familiar with on the Mac and the one under Linux (Ubuntu) server is that:
[INDENT]
	a) It is all command line driven, naturally.
	b) Linux has a peculiar way of "listing" drives (to Mac and Windows users anyway).
[/INDENT]
Under Linux, devices connected to your computer are generally listed as what appear to be files in the /dev directory.  One "file" per device.  While there are many files in this directory, the ones that deal with hard drives generally start with either "hd" (for IDE drives) or "sd" (for SCSI and SATA drives).  For example, if you have a machine with four SATA hard drives, you will find the following "files" listed on your system:
[INDENT]
	*[COLOR="Magenta"]/dev/sda[/COLOR]*	<--- this is the first SATA (or SCSI) drive (a)
	*[COLOR="Magenta"]/dev/sdb[/COLOR]*	<--- this is the second SATA (or SCSI) drive (b)
	*[COLOR="Magenta"]/dev/sdc[/COLOR]*	<--- this is the third SATA (or SCSI) drive (c)
	*[COLOR="Magenta"]/dev/sdd[/COLOR]*	<--- this is the fourth SATA (or SCSI) drive (d)
[/INDENT]
The first drive is "sda", the second is "sdb", and the third is "sdc" etc.  You get the general idea (Though I have no idea what happens after you have more than 26 drives connected to your system).  Note that these are the physical drives you have installed in your machine.  The bare "metal" so to speak.

As a different example, if you had four IDE drives connected to your system, you would find the following "files" listed on your system:
[INDENT]
	*[COLOR="Magenta"]/dev/hda[/COLOR]*	<--- this is the master drive on the first IDE channel
	*[COLOR="Magenta"]/dev/hdb[/COLOR]*	<--- this is the slave drive on the first IDE channel
	*[COLOR="Magenta"]/dev/hdc[/COLOR]*	<--- this is the master drive on the second IDE channel
	*[COLOR="Magenta"]/dev/hdd[/COLOR]*	<--- this is the slave drive on the second IDE channel
[/INDENT]
Now, these are just the bare drives attached to the system.  Any partitions on these drives are listed as separate "files" with a similar name but adding a number to indicate the partition number.  So, if you had two SATA drives with two partitions on the first drive, and a single partition on the second, you would have the following "files" listed on your system:
[INDENT]
	*[COLOR="Magenta"]/dev/sda[/COLOR]*	<--- this is the first SATA drive (bare drive)
	*[COLOR="Magenta"]/dev/sda1[/COLOR]*	<--- this is the first partition on this drive
	*[COLOR="Magenta"]/dev/sda2[/COLOR]*	<--- this is the second partition on this drive
	*[COLOR="Magenta"]/dev/sdb[/COLOR]*	<--- this is the second SATA drive (bare drive)
	*[COLOR="Magenta"]/dev/sdb1[/COLOR]*	<--- this is the first partition on this drive
[/INDENT]
This is most of what you need to know in order to prepare your drives.  There is only one additional concept to go over, and this is regarding our RAID management software.  Remember, normally accessing a drive requires:
[INDENT]
	Hard drive  ->  Partitions  ->  File System
[/INDENT]
Well, when using the RAID management software we have to add one more layer:
[INDENT]
	Hard drive  ->  Partitions  ->  Raid Management Software  ->  File System
[/INDENT]
[COLOR="Red"]If you are using drives that already have data on them be aware that these drives will be wiped clean![/COLOR]



**_[SIZE="3"]Step 1: Figure out which drives will be included in the RAID array:[/SIZE]_**

Let's get a list of all the drives on our system.  The easiest way to do this is to type the following (if you don't understand what sudo does, or don't understand what grep does, you should look them both up on Google.  Alternatively, you could just blindly type what I show here - though that is cheating):
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]sudo fdisk -l | grep -i "Disk "[/COLOR][/FONT]**   <--- note: that is a lowercase "L" just after "fdisk", followed by the pipe symbol.
[/INDENT]
You will get a list that looks something like this (yours may vary in detail, but generally it will look the same).  If you are using drives that already have data on them you may also get some warnings about unsupported partitions.  You can just ignore these (or you could use gdisk to clean them up - which is what I had to do when migrating some disks from FreeNAS. The website *[COLOR="MediumTurquoise"][http://www.rodsbooks.com/gdisk/wipegpt.html](http://www.rodsbooks.com/gdisk/wipegpt.html)[/COLOR]* was helpful in removing the GPT data):
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Disk /dev/sdb doesn't contain a valid partition table
	Disk /dev/sdc doesn't contain a valid partition table
	Disk /dev/sdd doesn't contain a valid partition table
	Disk /dev/sde doesn't contain a valid partition table
	Disk /dev/sda: 4294 MB, 4292967296 bytes
	Disk identifier: 0x00047a51
	Disk /dev/sdb: 8589 MB, 8589934592 bytes
	Disk identifier: 0x00000000
	Disk /dev/sdc: 8589 MB, 8589934592 bytes
	Disk identifier: 0x00000000
	Disk /dev/sdd: 8589 MB, 8589934592 bytes
	Disk identifier: 0x00000000
	Disk /dev/sde: 8589 MB, 8589934592 bytes
	Disk identifier: 0x00000000
[/COLOR][/FONT][/B][/INDENT]
Let's break this down.  The first four lines read:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Disk /dev/sdb doesn't contain a valid partition table
	Disk /dev/sdc doesn't contain a valid partition table
	Disk /dev/sdd doesn't contain a valid partition table
	Disk /dev/sde doesn't contain a valid partition table
[/COLOR][/FONT][/B][/INDENT]
These lines are fdisk complaining that it can't find a partition on the following four drives:
[INDENT][I][COLOR="Magenta"]
	/dev/sdb
	/dev/sdc
	/dev/sdd
	/dev/sde
[/COLOR][/I][/INDENT]
So, I know I have four "bare" drives in my system:  sdb, sdc, sdd, and sde.

The next two lines read:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Disk /dev/sda: 4294 MB, 4292967296 bytes
	Disk identifier: 0x00047a51
[/COLOR][/FONT][/B][/INDENT]
This shows that I have a 4GB drive with a valid partition on it called sda.  I know it has at least one valid partition on it because fdisk didn't complain about it in the first section.

The next eight lines read:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Disk /dev/sdb: 8589 MB, 8589934592 bytes
	Disk identifier: 0x00000000
	Disk /dev/sdc: 8589 MB, 8589934592 bytes
	Disk identifier: 0x00000000
	Disk /dev/sdd: 8589 MB, 8589934592 bytes
	Disk identifier: 0x00000000
	Disk /dev/sde: 8589 MB, 8589934592 bytes
	Disk identifier: 0x00000000
[/COLOR][/FONT][/B][/INDENT]
This shows me the same four bare drives as before (sdb, sdc, sdd, sde) along with their sizes (8 GB each).

So, in summary, I can deduce that sda holds my operating system, and that sdb-sde are bare drives that I will be adding to my RAID array.

Again, be aware that depending on the drives you have in your system, you may get slightly different outputs than what I have here (for example, when I built this server using two drives from an older FreeNAS device, I got some warnings regarding GPT Partition Tables).  Use what I explain here as a guide to understanding which drives are in your system, not as an absolute example of the outputs you will be seeing.




**_[SIZE="3"]Step 2: Partition each of the bare drives in preparation to be added to the array:[/SIZE]_**

[COLOR="Red"]NOTE: Partitioning a drive will delete ALL of the data on that drive. [/COLOR] 

Even if your drive has multiple partitions on it, all of your data on that drive will be wiped clean.  Be aware of this awesome power and responsibility when working with fdisk.  If you point it at the wrong disk, whammo!  You could be sorry.  That said, in the case of our server the absolute worst we could be doing is accidentally wiping out the freshly installed OS.  Just re-start the whole process if that happens (lord knows, the more times you do it, the faster you get - ask me how I know).



I am going to go through the steps for one drive.  Each subsequent drive is handled in exactly the same way.

Let's begin with drive:
[INDENT][I][COLOR="Magenta"]
	/dev/sdb
[/COLOR][/I][/INDENT]
We will be using the entire drive for the array, meaning just a single partition.  To begin, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo fdisk /dev/sdb
[/COLOR][/FONT][/B][/INDENT]
You will get a prompt that looks something like this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
	Building a new DOS disklabel with disk identifier 0x46623703.
	Changes will remain in memory only, until you decide to write them.
	After that, of course, the previous content won't be recoverable.

	Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

	WARNING: DOS-compatible mode is depreciated.  It's strongly recommended to
     		    switch off the mode (command 'c') and change display units to
		    sectors (command 'u').

	Command (m for help):
[/COLOR][/FONT][/B][/INDENT]
If you press 'm' for a list of possible commands you get the following list:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Command action
		a	toggle a bootable flag
		b	edit bsd disklabel
		c	toggle the dos compatibility flag
		d	delete a partition
		l	list known partition types
		m	print this menu
		n	add a new partition
		o	create a new empty DOS partition table
		p	print the partition table
		q	quit without saving changes
		s	create a new empty Sun disklabel
		t	change a partition's system id
		u	change display/entry units
		v	verify the partition table
		w	write table to disk and exit
		x	extra functionality (experts only)
[/COLOR][/FONT][/B][/INDENT]
In this case, we wish to create a brand new partition on this disk.  So press:
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]n[/COLOR][/FONT]**  <--- create new partition
[/INDENT]
We will then be asked:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Command action
[INDENT]		e	extended
		p	primary partition (1-4)[/INDENT]
[/COLOR][/FONT][/B][/INDENT]
We want to create a primary partition, so press:
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]p[/COLOR][/FONT]**  <--- create primary partition
[/INDENT]
We will then be asked which partition to create:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Partition number (1-4):
[/COLOR][/FONT][/B][/INDENT]
We want to create the first partition, so press:
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]1[/COLOR][/FONT]**  <--- we only want to create one partition, and it will be the first one.
[/INDENT]
We will be asked which cylinder to start with:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	First cylinder (1-1044, default 1):
[/COLOR][/FONT][/B][/INDENT]
This is just asking us where on the disk to start the partition.  We want the partition to take up the entire disk, so we will accept the default of 1.  Just hit enter.

We will then be asked which last cylinder to use:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Last cylinder, +cylinders or +size{K,M,G} (1-1044, default 1044):
[/COLOR][/FONT][/B][/INDENT]
Again, since we are going to use the full drive, accept the default.  Just hit enter.

At this point, we are dropped back to a prompt:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Command (m for help):
[/COLOR][/FONT][/B][/INDENT]
We have to tell fdiskt what kind of partition we want.  In our case, since this will be part of an array, we want to make the partition type be "Linux raid auto".  To set the partition type, type:
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]t[/COLOR][/FONT]**   <--- change a partition's system id
[/INDENT]
fdisk will let you know that it is working on partition 1, and then ask you for a hex code that describes what the partition type will be:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Selected partition 1
	Hex code (type L to list codes):
[/COLOR][/FONT][/B][/INDENT]
Go ahead and type:
[INDENT]	
	**[FONT="Courier New"][COLOR="RoyalBlue"]L[/COLOR][/FONT]**  <--- list partition codes
[/INDENT]
You will be presented with a long list of different partitions, and then prompted again:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Hex code (type L to list codes):
[/COLOR][/FONT][/B][/INDENT]
You will see that Linux raid auto is listed after the hexidecimal "number" fd.  So type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	fd
[/COLOR][/FONT][/B][/INDENT]
fdisk will let you know that it changed the system type of partition 1 to fd (Linux raid autodetect)

That is it!   To save the settings to the disk, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	w
[/COLOR][/FONT][/B][/INDENT]



**_[SIZE="3"]Step 3: Do it again for each of the other bare drives:[/SIZE]_**

Repeat this step once for each of your unpartitioned drives (sdc, sdd, sde).




**_[SIZE="3"]Step 4: Verify that your partitioning worked:[/SIZE]_**

This step is not absolutely necessary, but it would be good to make sure that your little trip through fdisk was productive.  Type this again:
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]sudo fdisk -l | grep -i Disk[/COLOR][/FONT]**   <--- note: that is a lowercase "L" just after "fdisk", followed by the pipe symbol.
[/INDENT]
You should get an output that looks a little like this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Disk /dev/sda: 4294 MB, 4292967296 bytes
	Disk identifier: 0x00047a51
	Disk /dev/sdb: 8589 MB, 8589934592 bytes
	Disk identifier: 0x4623703
	Disk /dev/sdc: 8589 MB, 8589934592 bytes
	Disk identifier: 0x9623d36f
	Disk /dev/sdd: 8589 MB, 8589934592 bytes
	Disk identifier: 0xc6b0c733
	Disk /dev/sde: 8589 MB, 8589934592 bytes
	Disk identifier: 0xd8b1c4a3
[/COLOR][/FONT][/B][/INDENT]
Notice that we didn't get fdisk barking about how it couldn't find partitions.

You may also type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo fdisk -l | grep -i "linux raid autodetect"
[/COLOR][/FONT][/B][/INDENT]
and it should give you one line for each of the drives you just partitioned:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	/dev/sdb1		1		1044	8385898+	fd	Linux raid autodetect
	/dev/sdc1		1		1044	8385898+	fd	Linux raid autodetect
	/dev/sdd1		1		1044	8385898+	fd	Linux raid autodetect
	/dev/sde1		1		1044	8385898+	fd	Linux raid autodetect
[/COLOR][/FONT][/B][/INDENT]
note that this is displaying the actual partitions you just created, not the bare drives themselves.  A subtle difference and not really one that makes a lot of difference for us right now.  Still, it is worth noting…  

And so I did.










[B][SIZE="4"][COLOR="RoyalBlue"]Section #8 - Install software raid and configure hard drives
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.
- Special thanks to the website: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)  from which I got most of the information in this section.
- [COLOR="Red"]Please be aware that this step may take anywhere from several hours to several days to complete![/COLOR]


**_[SIZE="3"]Step 1: Download and install mdadm.[/SIZE]_**

mdadm is a software RAID solution that seems quite robust and has a lot of support.  It will be the layer that sits between your partitioned hard drives and the file system.  Using this software will make your four drives appear to be one larger drive (with data redundancy).

Download and install mdadm:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get install mdadm
[/COLOR][/FONT][/B][/INDENT]
Unlike most other apt-get installations we will be doing in this setup, mdadm presents you with a big (text based) GUI.  It is asking about your Postfix Configuration (or in non-sysadmin terms: email).  This screen allows you to set up your mail configuration (this is to monitor your RAID array via email).  We will set this up manually later, so select:
[INDENT][I][COLOR="Magenta"]
	No Configuration
[/COLOR][/I][/INDENT]


**_[SIZE="3"]Step 2: Create the RAID array.[/SIZE]_**

mdadm takes several options when creating an array.  We will use the following command (which will be explained immediately following, so don't just type this in yet before you understand it):
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
[/COLOR][/FONT][/B][/INDENT] 
This can be broken down as follows:

-------------------------------------
*[COLOR="Magenta"]mdadm[/COLOR]* is the command that we are running:
	
-------------------------------------
The *[COLOR="Magenta"]--create[/COLOR]* flag tells mdadm that we want to create a new array.

-------------------------------------
The *[COLOR="Magenta"]--verbose[/COLOR]* flag tells mdadm that we want it to show us more information about what it is doing as it does it.

-------------------------------------
The *[COLOR="Magenta"]/dev/md0[/COLOR]* is the name of the device we want it to create.  Remember devices?  Anything beginning with "md" will be a RAID array on our system.  In our case, we will only have a single array.  But if we were to add a second array of disks in the future, that could be named: /dev/md1

-------------------------------------
The *[COLOR="Magenta"]--level[/COLOR]* flag tells mdadm what type of RAID array to create.  In this case, we want to create a RAID level 5 array.

-------------------------------------
The *[COLOR="Magenta"]--raid-devices[/COLOR]* flag tells mdadm how many drives will be made a part of this array.  In our case, we are adding four drives.

-------------------------------------
The last four arguments are the full path to each of the four partitions we want to add to the array.  Note, we are pointing to the partitions, and not the bare drives.  Notice the number 1 after each drive name.




Once you have run the above command, you should get an output that looks something like this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: size set to 976760320K
mdadm: Defaulting to version 1.2 metadata
[ 3832.268850] md/raid:md0: raid level 5 active with 3 out of 4 devices, algorithm 2
mdadm: array /dev/md0 started.
[/COLOR][/FONT][/B][/INDENT]
This indicates that your raid array has been successfully started.  But don't celebrate just yet because…



**_[SIZE="3"]Step 3: Don't turn off that machine!  Wait (and wait) for your raid to be initialized.[/SIZE]_**

Just because you started your array does not mean it has been fully initialized.  This process actually takes a moment.  To check on the status of the array type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	cat /proc/mdstat
[/COLOR][/FONT][/B][/INDENT]
You should get a result that looks something like this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sde1[4] sdd1[2] sdc[1] sdb[0]
      2930280960 blocks suoer 1.2 level 5, 512K chunk, algorithm 2 [4/3] [UUU_]
      [>……………………..]  recovery = 0.7% (7573036/976760320) finish=734.5min speed=21990K/sec

unused devices: <none>
[/COLOR][/FONT][/B][/INDENT]
Note that line about "recovery".  mdadm is actually building your array right now and it takes a LONG time.  In the example above, it is less than 1% complete and still has over 12 hours to go (734.5min)!  And that is with four 1TB drives.  A bigger system will take longer.



**_[SIZE="3"]Step 4: Get on with your life while you wait for mdadm to finish recovering your raid.[/SIZE]_**

Go outside.  Seriously.  You look terrible.



**_[SIZE="3"]Step 5: Come back the next day and verify that your raid was correctly initialized.[/SIZE]_**

Type: 
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	cat /proc/mdstat
[/COLOR][/FONT][/B][/INDENT]
You should see something like this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sde1[4] sdd1[2] sdc[1] sdb[0]
      2930280960 blocks suoer 1.2 level 5, 512K chunk, algorithm 2 [4/3] [UUU_]

unused devices: <none>
[/COLOR][/FONT][/B][/INDENT]
Note the lack of any lines that mention "recovery".  Your raid is now correctly initialized.



**_[SIZE="3"]Step 6: Format your new raid array.[/SIZE]_**

The next step is to format the array with a file system.  In my case (and most commonly) I will be using the ext4 file system.  To format this raid partition, you will use the mkfs command.

Type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mkfs.ext4 /dev/md0
[/COLOR][/FONT][/B][/INDENT]
You should get a result that looks something like this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
mke2fs 1.41.14 (22-Dec-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=128 blocks, Stripe width=384 blocks
183148544 inodes, 732570240 blocks
36628512 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4292967296
22357 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
        8193, 24577, 40961, 57345, 73729

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 29 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
[/COLOR][/FONT][/B][/INDENT]


**_[SIZE="3"]Step 7: configure mdadm by editing the mdadm.conf file.[/SIZE]_**

You need to tell mdadm all about the raid you just created.  Why do you have to do this manually when just a second ago you created an array using the very same computer?

I dunno.  It's just the Linux way I guess.  

Anyway, start by getting the information about the array that you will later have to add to the mdadm.conf file.  To do this, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mdadm --detail --scan
[/COLOR][/FONT][/B][/INDENT]
You should get back something that looks like this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	ARRAY /dev/md0 metadata=1.2 name=ubuntu:0 UUID=77b695c4:32e5dd46:63dd7d16:17696e09
[/COLOR][/FONT][/B][/INDENT]
Note that the name= portion (ubuntu in my case) will most likely be different for you (I think it matches the hostname you gave your machine when you first installed Linux, but I cannot be sure).  The UUID will most definitively be different.

We want to add the above line into the madadm.conf file.  The easiest way to do this is to append the line to the end of the file and then edit it afterwards.  Start by typing the following (note the pipe symbol after the word scan… it should be right above the enter key on your keyboard on U.S. keyboards):
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mdadm --detail --scan | sudo tee --append /etc/mdadm/mdadm.conf
[/COLOR][/FONT][/B][/INDENT]
Now, edit the /etc/mdadm/mdadm.conf file by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo nano /etc/mdadm/mdadm.conf
[/COLOR][/FONT][/B][/INDENT]
The line you appended should be at the end of the file.  While it is actually ok to just leave it there, the German in me wants it to live in the "correct" location.  I just use cut and paste to move it just under the portions that reads:
[INDENT][I][COLOR="Magenta"]
	# definitions of existing MD arrays
[/COLOR][/I][/INDENT]
It appears that newer versions of mdadm don't like the "name=XXXXXX" or "metadata=NN" portions of this line.  Remove both of those so that the line just reads (again, your UUID will be different):
[INDENT][I][COLOR="Magenta"]
	ARRAY /dev/md0 UUID=77b695c4:32e5dd46:63dd7d16:17696e09
[/COLOR][/I][/INDENT]
Save and close the file.

I had an issue where the array would get renamed to /dev/md127 every time I rebooted the server (my mdadm.conf file clearly says it should be /dev/md0).  Apparently this is new behavior for mdadm.  If it has difficulty assembling the array upon booting it will somehow rename it to /dev/md127.  If this is happening to you, try running the following command.  It appears to have fixed it for me (thanks to YesWeCan and this thread:  [http://ubuntuforums.org/showthread.php?t=1764861):](http://ubuntuforums.org/showthread.php?t=1764861):)
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo update-initramfs -u
[/COLOR][/FONT][/B][/INDENT]





**_[SIZE="3"]Step 8: Create a mount point for your RAID array.[/SIZE]_**

Linux "mounts" drives into what appear to be directories.  So, unlike a Windows machine in which each drive appears as a separate drive letter (C or D), a mounted drive in Linux appears to be just another directory that lives somewhere (anywhere) in the directory structure.  

For example, say you mounted your array at:
[INDENT][I][COLOR="Magenta"]
/home/admiral/mounts/raidarray/
[/COLOR][/I][/INDENT]
and you have the following file on your array:
[INDENT][I][COLOR="Magenta"]
music/classical/mozart/songs/deafguysong.mp3
[/COLOR][/I][/INDENT]
The full path to this file would be:
[INDENT][B][FONT="Courier New"]
[COLOR="DarkOrange"]/home/admiral/mounts/raidarray/[/COLOR][COLOR="DarkOrchid"]music/classical/mozart/songs/deafguysong.mp3[/COLOR]
|[COLOR="DarkOrange"]-----------------------------[/COLOR]|[COLOR="DarkOrchid"]-------------------------------------------[/COLOR]|
|[COLOR="DarkOrange"]-This is on your boot drive--[/COLOR]|[COLOR="DarkOrchid"]-This portion lives on your RAID array-----[/COLOR]|
[/FONT][/B][/INDENT]

It looks like a single, unified path.  But once you cd past .[COLOR="Magenta"]../raidarray/[/COLOR] you are actually navigating on your mounted RAID drives.

In order to mount the drive in a directory, the directory must already exist.  For our purposes, we will create a directory in *[COLOR="Magenta"]/mnt[/COLOR]* called *[COLOR="Magenta"]nas[/COLOR]*.  This means our raid array will exist in the following location: *[COLOR="Magenta"]/mnt/nas[/COLOR]*.  Note, you can select any location you want, but typically mounted drives are placed somewhere in *[COLOR="Magenta"]/mnt[/COLOR]*.  To do this, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mkdir /mnt/nas
[/COLOR][/FONT][/B][/INDENT]
Next, we need to edit the /etc/fstab file to make Ubuntu mount your raid at startup (otherwise this will just be an empty directory on your startup disk instead of a mounted raid array).
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo nano /etc/fstab
[/COLOR][/FONT][/B][/INDENT]
add the following to the end of the file (of course, replace *[COLOR="Magenta"]/mnt/nas[/COLOR]* with the directory you selected above):
[INDENT][I][COLOR="Magenta"]
	/dev/md0	/mnt/nas	ext4	defaults	1	2
[/COLOR][/I][/INDENT]
close and save the file.

Normally the /etc/fstab file is read at startup and your raid array will be mounted automatically.  But since we don't want to reboot just now, let's mount the raid manually.  To do this, we will simply tell Ubuntu to mount everything in the /etc/fstab file.  This is accomplished by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	mount -a
[/COLOR][/FONT][/B][/INDENT]
And that's it.  Let's verify that everything worked as planned.  Use the df command to list all of your drives and their mount points (and how much space is available on each drive).  Type the following (the -h option outputs data in a human readable format instead of blocks and bytes):
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	df -h
[/COLOR][/FONT][/B][/INDENT]
You should get an output that looks something like this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
Filesystem		Size		Used	Avail	Use%	Mounted on
/dev/sda1		28G		1.1G	25G	5%	/
udev			988M		8.0K	988M	1%	/dev
tmpfs			399M		296K  398M	1%	/run
none			5.0M		0	5.0M	0%	/run/lock
none			996M		0	996M	0%	/run/shm
/dev/md0		2.7T		201M	2.6T	1%	/mnt/nas
[/COLOR][/FONT][/B][/INDENT]
The key thing to look for here is *[COLOR="Magenta"]/dev/md0[/COLOR]*.  We can see that it is pretty big (2.7 Terabytes) and that it is properly mounted on *[COLOR="Magenta"]/mnt/nas[/COLOR]*.



**_[SIZE="3"]Step 9: Random note about mdadm and booting.[/SIZE]_**

mdadm will check the health of your array about once every thirty times you boot your system.  This takes a few moments (about five minutes in my case) and during the time your server may appear to have hung.  If you reboot your machine and it is not responsive, this may be what is causing the issue.  Just fyi.










[B][SIZE="4"][COLOR="RoyalBlue"]Section #9 - Install  and configure ssh
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.



SSH is going to let us log into the server from another machine.  This is going to make life easier for us in innumerable ways.  For example, we will be able to have multiple shell windows open at once.  We will be able to copy and paste from the internet (or even this tutorial).  We won't be huddled over the server keyboard in the corner of the closet behind the cat box.


**_[SIZE="3"]Step 1: Install ssh.[/SIZE]_**

Start by installing the latest version of openssh:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get install openssh-server
[/COLOR][/FONT][/B][/INDENT]



**_[SIZE="3"]Step 2: Find an unused port number and write it down (we will make ssh use this port instead of port 22).[/SIZE]_**
	
By default, ssh runs on port 22.  Apparently, lots of automated attacks directly target this port.  By changing your port number, you can cut down on the number of automated attempts to break into your system. While this isn't an actual security step by itself (you are merely hiding the entrance to ssh) it can at least mitigate some of the threat. 

A note on "security through obscurity" vs. "true security":  Many people suggest that changing the ssh port is not true security because you are merely obscuring the opening to your ssh process.  This is completely true.  And if this were the only thing we were doing to secure the server it would hardly be worth doing.  But changing the port in addition to using "real" security measures makes sense to me.  Even if I am wearing a full body kevlar suit, I am going to hide in the bushes when the knife wielding maniac comes by.  If I can cut down on the number of attacks somewhat by hiding IN ADDITION to properly locking down my server, I'm going to do it.

Even if you decide to leave ssh on port 22, make sure you make some of the other changes listed here (especially the ones labeled IMPORTANT SECURITY MEASURE).

To find an unused port number, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo netstat -anp --tcp --udp | grep -i LISTEN
[/COLOR][/FONT][/B][/INDENT]
You will get an output that looks something like this (you might have to hit ctrl-c to get control of your shell back):
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	tcp	0	0 0.0.0.0:22	0.0.0.0:*	LISTEN	704/sshd        
	tcp6	0	0 :::22		:::*		LISTEN	704/sshd        
[/COLOR][/FONT][/B][/INDENT]
From this you can deduce that only port 22 is currently open and in use (look for the number after the first colon).  That means *most* any of the other ports in the range 1-65000 (roughly) are available.  That said, ports below 1024 are reserved and should not be used.  I have also read that ports over 40,000 should be left alone (I have no idea why).  So I generally stay in the 15,000 - 30,000 range.  That's still a lot of ports!

Pick an unused port number and write it down.  Seriously, write it down.  If you forget it, you will have to physically log into the server and try and find the port number before you can remotely log in again.



**_[SIZE="3"]Step 3: Configure ssh.[/SIZE]_**
	
To configure ssh, edit the sshd_config file:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo nano /etc/ssh/sshd_config
[/COLOR][/FONT][/B][/INDENT]

-------------------------------------
Edit the line that starts with:
[INDENT][I][COLOR="Magenta"]
	Port 22
[/COLOR][/I][/INDENT]
And change it to read:
[INDENT]
	*[COLOR="Magenta"]Port 22512[/COLOR]*     <-- 22512 is just an example. Use the port number you wrote down from Step 5.
[/INDENT]
This will change the port that ssh uses when we restart it.


-------------------------------------
Edit the line that starts with:
[INDENT][I][COLOR="Magenta"]
	X11Forwarding
[/COLOR][/I][/INDENT]
And make sure it is set to "no" (we are not running X11 on this server)


-------------------------------------
Edit the line that starts with:
[INDENT][I][COLOR="Magenta"]
	AllowTcpForwarding
[/COLOR][/I][/INDENT]
And make sure it is set to "no" (it might already be set that way)


-------------------------------------
[COLOR="Red"](IMPORTANT SECURITY MEASURE!)[/COLOR]
Edit the line that starts with:
[INDENT][I][COLOR="Magenta"]
	PermitRootLogin
[/COLOR][/I][/INDENT]
And make sure it is set to "no" (Even though in Ubuntu Server the root user is, by default, not enabled)


-------------------------------------
[COLOR="Red"](IMPORTANT SECURITY MEASURE!)[/COLOR] 
Edit the line that starts with: 
[INDENT]
	*[COLOR="Magenta"]AllowUsers[/COLOR]*   <--- (this line may not exist, or it may be commented out. In that case either add it or uncomment it)
[/INDENT]
And make sure it reads:
[INDENT]
	*[COLOR="Magenta"]AllowUsers admiral[/COLOR]*  <--- substitute your administrative user's login for "admiral"
[/INDENT]		
This means only a single user (admiral in this example) will ever be able to remotely log in and administer your system.


-------------------------------------
Edit the line that starts with: (this line may be commented out. In that case uncomment it.)
[INDENT][I][COLOR="Magenta"]
	Protocol
[/COLOR][/I][/INDENT]
And make sure it reads:
[INDENT][I][COLOR="Magenta"]
	Protocol 2
[/COLOR][/I][/INDENT]
I have seen arguments that ssh1 is just as secure as ssh2 but, as ssh1 is being depreciated, it seems best to stick with the newer protocol exclusively.


-------------------------------------
Save and close the file.




**_[SIZE="3"]Step 4:  Restart ssh.[/SIZE]_**

Restart the ssh daemon by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo service ssh restart
[/COLOR][/FONT][/B][/INDENT]
Now if you were to type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo netstat -anp --tcp --udp | grep -i LISTEN
[/COLOR][/FONT][/B][/INDENT]
You should see something like this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	tcp	0	0 0.0.0.0:22512	0.0.0.0:*	LISTEN	704/sshd        
	tcp6	0	0 :::22512		:::*		LISTEN	704/sshd        
[/COLOR][/FONT][/B][/INDENT]
Which shows you that your ssh is now running on your new port (22512 in this example)




**_[SIZE="3"]Step 5: Get ssh ready to use public/private keys.[/SIZE]_**

Technically we have not yet turned off password based logins, but public/private keys are much more secure.  Here I will show you how to set up the server to let you log in from your Mac securely using keys.  Later, we will actually turn off passwords so that you will HAVE to use keys to log in remotely.

Create an .ssh directory in your home directory. This is where your public key will be stored.  If you don't know what a public key is, don't sweat it just now but you should take the time to learn about ssh eventually.  Prep the server by typing the following:
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]cd ~[/COLOR][/FONT]**
	**[FONT="Courier New"][COLOR="RoyalBlue"]mkdir .ssh[/COLOR][/FONT]**   <- don't miss the leading "dot" on .ssh
[/INDENT]
This just creates a hidden .ssh directory in your administrator's home directory.  

Next type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	chmod go-rwx .ssh
[/COLOR][/FONT][/B][/INDENT]
The chmod command changes the permissions so that only the administrator (admiral in this example) has permissions to read or write to this directory.  You may read the chmod command as: **[COLOR="Red"]chmod[/COLOR]** **[COLOR="Red"]g[/COLOR]**roup and **[COLOR="Red"]o[/COLOR]**ther **[COLOR="Red"]-[/COLOR]** (subtract) **[COLOR="Red"]r[/COLOR]**ead, **[COLOR="Red"]w[/COLOR]**rite, and e**[COLOR="Red"]x[/COLOR]**ecute privileges from **[COLOR="Red"].ssh[/COLOR]**).




**_[SIZE="3"]Step 6: Log out of your server.[/SIZE]_**

Log out of the server.  All further server configuration will be done via ssh from your Mac
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	exit
[/COLOR][/FONT][/B][/INDENT]
You should be returned to a screen that looks something like this (yours may vary depending on what you named your sever):
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Ubuntu 11.10 ubuntu tty1

	ubuntu login:
[/COLOR][/FONT][/B][/INDENT]	









[B][SIZE="4"][COLOR="RoyalBlue"]Section #10 - Get your ssh keys working and log in from the Mac
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.
- All of the following steps are performed from the terminal on your Mac!   You should be logged into your Mac as your regular user (you do NOT have to be logged in as the administrative user you created on the server - "admiral" in the examples provided here).





**_[SIZE="3"]Step 1: Set up your ssh keys.[/SIZE]_**

Open a terminal window (again, you are doing all of this from your Mac!) and type the following to create your private and public keys:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	ssh-keygen
[/COLOR][/FONT][/B][/INDENT]
The computer will ask you the following questions. Answer them as described:


-------------------------------------
[INDENT]
**[FONT="Courier New"][COLOR="SeaGreen"]Enter file in which to save the key (Users/bob/.ssh/id_rsa):[/COLOR][/FONT]**  <--- Note: your prompt will have YOUR Mac login name in it instead of 'bob'
[/INDENT]
Just hit enter to accept the default location of ~/.ssh/id_rsa


-------------------------------------
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
Enter passphrase:
[/COLOR][/FONT][/B][/INDENT]
Type in some sentence that you will remember. You can use letters, spaces, punctuation and numbers. The best passphrase has all four and is typically much longer than a normal password.  Also beneficial is something that does *not* follow normal grammatical structure.  Use something like:
[INDENT][I][COLOR="Magenta"]
	16 run blast_cast Peters jive with no nuts!?
[/COLOR][/I][/INDENT]
This may seem like it will be a pain to type over and over, but we will set it up so that you don't have to re-enter this passphrase all the time.  A long, complicated passphrase will not really be much of a hassle and will be much more secure.  That said, don't forget it!  The above example might be too hard to remember.  Pick a favorite line from a movie and alter it.  Just make sure it is not a simple sentence as they are much easier to crack.  Also, I've been told to never write this passphrase down.  That is absurd.  You should most definitely write it down.  Just keep it someplace far from the computer, safe, and in a format that makes it meaningless to anyone who may find it.


-------------------------------------
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
Enter same passphrase again:
[/COLOR][/FONT][/B][/INDENT]
Type it in again.


The computer will inform you that it has saved some files in your home directory.  It will give you some long gibberish key fingerprint and maybe even some random "image" made of characters.  Ignore these for now.

The next step is to copy your public key (one of the files it just saved) to the Ubuntu server.  This will be the "lock" on the administrative account on the server.  Nobody will be able to log into this account remotely unless they have the corresponding private key (and passphrase) on their computer.  In our case, the private key lives on our Mac.  To copy your public key to the sever type something ***similar to*** the following (I will show you an example here and then break it down so you will understand how to modify it for your particular situation - it isn't hard)
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]scp -P 22512 ~/.ssh/id_rsa.pub [noparse]admiral@172.16.1.16:.ssh[/noparse]/authorized_keys2[/COLOR][/FONT]**  <--- don't type this exactly. See below how to modify it.
[/INDENT]
Here is what it all means:  

-------------------------------------
The *[COLOR="Magenta"]scp[/COLOR]* means "secure copy". It will copy a file from one machine to another using ssh.  Literally type "scp".

-------------------------------------
The *[COLOR="Magenta"]-P 22512[/COLOR]* tells ssh which port to use. Remember where you changed the ssh port above?  Did you write it down?  Use "-P" followed by that number.

-------------------------------------
The *[COLOR="Magenta"]~/.ssh/id_rsa.pub[/COLOR]* is the public key file that you created just now. The output of ssh-keygen which you just ran will have displayed this file name for you.  But if you did as I suggested and just hit enter to accept the default, your file name will be identical to what I typed here. In this case you can literally type:  "~/.ssh/id_rsa.pub"

-------------------------------------
*[COLOR="Magenta"]admiral@[/COLOR]* is the user you will be logging into the server as. This is the administrative user you first set up when creating the server.  Substitute your administrative user name for "admiral" but keep the @ sign.

-------------------------------------
The *[COLOR="Magenta"]172.16.1.16:[/COLOR]* is the IP address of the ubuntu server.  Remember when you wrote that down before? Aren't you glad you did?  Don't forget the : at the end of this number.

-------------------------------------
The *[COLOR="Magenta"].ssh/authorized_keys2[/COLOR]* is the name of the file where the public key will be stored on the server. Just use this directly as I have it typed.  I.e. literally type ".ssh/authorized_keys2" (don't forget the leading dot!)



So, put together, it becomes:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	scp -P <your ssh port number> <path to your local public key file> <UbuntuServerAdministrator>@<Ubuntu IP>:.ssh/authorized_keys2
[/COLOR][/FONT][/B][/INDENT]
Once you have typed this, you will be prompted for your password (this should be the last time we log in using a password).  This is the password for the administrative user on the Ubuntu server (In the examples I have been providing here, it would be the password for the user 'admiral'). Once you enter your password you will get a line that looks something like this (don't worry if it isn't exactly identical):
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	id_rsa.pub                      100%  406     0.4KB/s   00:00
[/COLOR][/FONT][/B][/INDENT]
This means your public key is now stored on the ubuntu server for the user admiral (or whatever your administrative user is called).






**_[SIZE="3"]Step 2: Log into your ubuntu server from your mac using your private key.[/SIZE]_**

To manage the server from now on, you will use a command SIMILAR the following to log in from a command line:
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]ssh -p 22512 -l admiral 172.16.1.16[/COLOR][/FONT]**  <--- don't type this exactly. See below how to modify it.
[/INDENT]
Here is what it all means:  

-------------------------------------
The *[COLOR="Magenta"]ssh[/COLOR]* means "secure shell". It will allow you to open a shell on the server remotely so that every command you type into the terminal window on your Mac will actually be executed on the server.  Literally type "ssh".

-------------------------------------
The *[COLOR="Magenta"]-p 22512[/COLOR]* tells ssh which port to use. Again, remember changing the ssh port number?  This is why I had you write it down, because you will use it over and over.  Use "-p" followed by that number.  Note: ssh uses a lowercase "-p" to indicate the port number whereas the scp command above used an uppercase "-P".  Why is that you might ask?  Dunno.  Welcome to the vagaries of Linux.

-------------------------------------
*[COLOR="Magenta"]-l admira[/COLOR]*l is the user you will be using to log into the server (the -l stands for "login as" I suspect). This is the administrative user you first set up when creating the server.  Substitute your administrative user name for "admiral" but keep the "-l" before it.

-------------------------------------
The *[COLOR="Magenta"]172.16.1.16:[/COLOR]* is the IP address of the ubuntu server.  Again, remember when you wrote that down before? I wouldn't tell you to waste precious ink if I didn't have a good reason.

Once you type this in, you will be prompted for your passphrase.  I am running OSX Lion, and it actually popped up a dialog box asking for my "password" and offering to save it in my keychain.  Older versions of OSX may do it differently.  I don't know. In any case, you should be prompted for your passphrase.  Type it in and you should now be logged into your server via the command line.  

Feel free to open several terminal windows and log into the server multiple times (use the same command each time).  Having multiple windows makes managing your server more convenient.  These windows can be pointed to different directories at the same time, can be resized, etc.  You can have a command-line text editor open in one window, and a directory listing in another.  This is much more convenient than working directly on the server itself.

Note: your private key lives on your Mac that you are typing these commands on.  If you try to administer your server from a different computer, you will not be able to log in simply by using your passphrase.  Remember, the passphrase only unlocks your key.  It is the key (which, as mentioned, only lives on this computer) that unlocks the server.  If you think you will be administering the server from another machine, you will have to copy your key to that machine as well.  I won't tell you how to do that here, but Google can probably help.

Also Note: At the moment we have not disabled the ability to log into the system using the password you first set up for the administrative user.  If you don't feel comfortable using keys, or if you think you will be managing the server from multiple machines to which you cannot safely copy your key, you may leave passwords enabled.  I, however, will be turning this ability off in the next step.
		


**_[SIZE="3"]Step 3: Remove the ability to ssh into the server using only a username and password (I.e. Require key based authentication).[/SIZE]_**

As we have been saying all along, simple password based security is not going to be adequate for paranoid people like us.  Edit the ssh config file by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo nano /etc/ssh/sshd_config
[/COLOR][/FONT][/B][/INDENT]
Find the line that starts with 
[INDENT]
	*[COLOR="Magenta"]PasswordAuthentication[/COLOR]*  <--- This line may be commented out.  Just uncomment it.
[/INDENT]
And make sure it is set to "no"

Save and close the file.


Restart ssh by typing the following (you shouldn't be disconnected, but if you are, just re-log in):
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo service ssh restart
[/COLOR][/FONT][/B][/INDENT]







[B][SIZE="4"][COLOR="RoyalBlue"]Section #11: install msmtp so that your server can send emails
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype [/COLOR][/FONT]**is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.
- I used these guides a lot when working though this section:  [http://ubuntuforums.org/showthread.php?t=1185134](http://ubuntuforums.org/showthread.php?t=1185134)



There are a number of different methods that can be used to make your server do email.  Since I am only interested in having the machine send me emails when there are problems (i.e. the server won't ever be receiving emails) I have elected to just have it use my regular email service (aka, something like gmail or yahoo email).  This way I only have to install the most minimal software and will let the ISP handle all the complicated email stuff.


**_[SIZE="3"]Step 1: Install software that allows your server to send mail via your regular email account (msmtp).[/SIZE]_**

Note: User Bushflyr in the comments below set up a throwaway GMAIL account to receive these messages so that he would not have to have his actual email account password in the clear.  That is a pretty good idea and I think I will make similar changes to my system.  His comments (and setup guide) are here:  [http://ubuntuforums.org/showthread.php?p=11792720#post11792720](http://ubuntuforums.org/showthread.php?p=11792720#post11792720) (or just scroll down to page 3 of the comments).

In order for mdadm (or any other process) to send mail, I am simply going to set them up to use one of my regular email addresses.  To do this, we need to install msmtp.  This package will allow us to basically send email through an ISP smtp server (aka, use our regular email address).

Type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get install msmtp-mta
[/COLOR][/FONT][/B][/INDENT]
Once installed, we need to configure it.  This involves creating a configuration file.  The file does not already exist, so you you will have to create it by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo nano /etc/msmtprc
[/COLOR][/FONT][/B][/INDENT]
(Again, the file does not already exist so don't be alarmed when nano indicates that this is a new file at the bottom of your window).

Add the following information to the file:
[INDENT][I][COLOR="Magenta"]
defaults
tls off

account default
host smtp.youremailprovider.net
port 25
protocol smtp
auth login
user yourusername
password secretpassword
from [noparse]you@yourdomain.com[/noparse]
logfile /var/log/msmtp.log
[/COLOR][/I][/INDENT]
Of course, you will have to customize the actual settings to match those that your ISP requires to send an email.  The items you will want to customize are:
[INDENT]
	*[COLOR="Magenta"]host[/COLOR]*		<--- this is the smtp host name (smtp.domain.com) from your ISP
	*[COLOR="Magenta"]port[/COLOR]*			<--- this is the port that it receives mail on (usually 25, but my ISP - everyone.net - actually uses 2525)
	*[COLOR="Magenta"]auth[/COLOR]*		<--- this is the type of authorization your ISP uses.  Mine only worked with "login" which is problematic (discussed below)
	*[COLOR="Magenta"]user[/COLOR]*		<--- your user name
	*[COLOR="Magenta"]password[/COLOR]*	<--- password (this is problematic as discussed below)
	*[COLOR="Magenta"]from[/COLOR]*		<--- which email address is this being sent from.  Usually your own email address
[/INDENT]
The exact settings will depend on your ISP or email provider requirements.  The specifics of which are beyond the scope of this tutorial.  I will try to help if anyone has questions in the comments, but generally speaking the information you need should all be available from a google search.

[COLOR="Red"]Note:  there are some significant security issues with the sample I show above.  [/COLOR]

The first is that (for me) the only type of authorization that worked was to use "login".  This type of authorization sends all of your information in plain text, including your password.  Unfortunately, I can't seem to figure out how to fix that and my email provider (everyone.net) has the crappiest help of just about any service provider I have ever dealt with.  Eventually I will be switching, but no time now.

The second issue is that your email password is just sitting in this file waiting to be displayed to anyone who manages to work their way down to this directory on your server.  Now, ideally nobody ever would manage to get that far, but wishful thinking is no replacement for solid security measures.  Fortunately, msmtp allows you to use a different password storage system.  Unfortunately, I am too tired at the moment to figure it out.  So, for the time being, I am just going to leave it as is.  I will return to this post and edit it appropriately once I have figured out a better method.








[B][SIZE="4"][COLOR="RoyalBlue"]Section #12 - Write some system maintenance shell scripts
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.



There will be a number of scripts that we will want to have running in order to customize our server.  Some of these scripts will be called directly by cron.  Others will live in a custom scripts directory and be called on by yet other scripts.  In this section we will start to get these set up.  Later sections will deal with writing the actual scripts that manage the server.



**_[SIZE="3"]Step 1: Create a directory to hold a library of scripts.[/SIZE]_**

There are going to be a number of scripts that we want to run on a periodic basis, and we have several options as how to call these scripts.

One option is to roll them all into a single script and call this monolithic script from cron.  But this is less than ideal because it becomes harder to modify just one feature without affecting a second set.  Also, there is no granularity with regard to the frequency with which different functions may be called.

A second option is to write individual scripts, each with tightly focused functionality, and then install each of them into cron.  And in fact, this is the basis of the technique we will be using.  

The third option is to create directories to hold an arbitrary collection of scripts, and then create a master script (launched by cron) that will simply execute any script it finds in this directory.  In this scenario, adding functionality is simply a matter of writing a new script and dropping it into this directory, knowing it will be automatically executed alongside the rest of the scripts.  Disabling a script is simply a matter of moving that script back out of the directory.

We will be using a mixture of option 2 and option 3.

The first step is to create the directories that will hold the collections of scripts.  We will actually be making several directories.  We will make one set for scripts that run continuously (every five minutes).  We will make a second directory for scripts to be run once an hour.  We will make another set for scripts that should be run once a day.  And, finally, we will make another set for scripts that should run once a week.  Each of these sets will comprise of two directories: one for active scripts, and a second where you can move scripts if you wish to deactivate them (this second directory is simply a convenience and is not integral to the functionality of the system).  Start by creating the following directories:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mkdir /usr/local/sbin/continuous.active
	sudo mkdir /usr/local/sbin/continuous.inactive
	sudo mkdir /usr/local/sbin/hourly.active
	sudo mkdir /usr/local/sbin/hourly.inactive
	sudo mkdir /usr/local/sbin/daily.active
	sudo mkdir /usr/local/sbin/daily.inactive
	sudo mkdir /usr/local/sbin/weekly.active
	sudo mkdir /usr/local/sbin/weekly.inactive
[/COLOR][/FONT][/B][/INDENT]


**_[SIZE="3"]Step 2: Create a shell script to execute every script in one of these directories.[/SIZE]_**

We will want to create a set of scripts that, when executed by cron, will automatically invoke each script in one of these directories.  We will create one script per directory (i.e. one script for continuous use, one for hourly use, one for daily use, and one for weekly use).



-------------------------------------
Start by creating the continuous script.  Type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico /usr/local/sbin/continuous.sh
[/COLOR][/FONT][/B][/INDENT]
and paste or type in the following:

```
#!/bin/bash

ACTIVE_SCRIPTS_DIR=/usr/local/sbin/continuous.active

for module in `find "$ACTIVE_SCRIPTS_DIR" -maxdepth 1 -mindepth 1 -type f`; do
	if [ -x $module ]; then
		$module
	fi
done
```

save and close the file.

Change its permissions to make it executable:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo chmod u+x /usr/local/sbin/continuous.sh
[/COLOR][/FONT][/B][/INDENT]



-------------------------------------
Follow that by creating the hourly script (it is almost identical to the continuous script).  Type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico /usr/local/sbin/hourly.sh
[/COLOR][/FONT][/B][/INDENT]
and paste or type in the following:

```
#!/bin/bash

ACTIVE_SCRIPTS_DIR=/usr/local/sbin/hourly.active

for module in `find "$ACTIVE_SCRIPTS_DIR" -maxdepth 1 -mindepth 1 -type f`; do
	if [ -x $module ]; then
		$module
	fi
done
```

save and close the file.

Change its permissions to make it executable:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo chmod u+x /usr/local/sbin/hourly.sh
[/COLOR][/FONT][/B][/INDENT]



-------------------------------------
Next, let's create the daily script (it is very nearly identical to the other two scripts).  Type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico /usr/local/sbin/daily.sh
[/COLOR][/FONT][/B][/INDENT]
and paste or type in the following:

```
#!/bin/bash

ACTIVE_SCRIPTS_DIR=/usr/local/sbin/daily.active

for module in `find "$ACTIVE_SCRIPTS_DIR" -maxdepth 1 -mindepth 1 -type f`; do
	if [ -x $module ]; then
		$module
	fi
done
```

save and close the file.

Change its permissions to make it executable:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo chmod u+x /usr/local/sbin/daily.sh
[/COLOR][/FONT][/B][/INDENT]



-------------------------------------
Finally, let's create the weekly script (it is very nearly identical to the other three scripts).  Type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico /usr/local/sbin/weekly.sh
[/COLOR][/FONT][/B][/INDENT]
and paste or type in the following:

```
#!/bin/bash

ACTIVE_SCRIPTS_DIR=/usr/local/sbin/weekly.active

for module in `find "$ACTIVE_SCRIPTS_DIR" -maxdepth 1 -mindepth 1 -type f`; do
	if [ -x $module ]; then
		$module
	fi
done
```

save and close the file.

Change its permissions to make it executable:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo chmod u+x /usr/local/sbin/weekly.sh
[/COLOR][/FONT][/B][/INDENT]



**_[SIZE="3"]Step 3: Insert these scripts into cron.[/SIZE]_**

(Note: I used this website when putting together this section: [http://clickmojo.com/code/cron-tutorial.html](http://clickmojo.com/code/cron-tutorial.html))

Obviously, these scripts will do nothing unless they are called on a repeating basis.  That's where cron comes in.  cron is a daemon that runs other scripts on an arbitrary schedule (as long as that schedule is no more granular than one minute).  To insert items into cron, we need to edit the crontab file (for the root user).  To do this, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo crontab -e
[/COLOR][/FONT][/B][/INDENT]
This will bring up an editor that will allow you to edit the contents of the crontab file.  You may be asked which editor you wish to use.  I just stick to nano as it is the easiest.

Add the following lines:
```

MAILTO= yourusername@yourdomain.com
*/5 * * * * /usr/local/sbin/continuous.sh
6 */1 * * * /usr/local/sbin/hourly.sh
16 02 * * * /usr/local/sbin/daily.sh
26 03 * * sun /usr/local/sbin/weekly.sh

```
Obviously you will have to change the MAILTO line to point to your own email address.

Save and close the file.

Here is a quick breakdown of the different sections, but I would recommend you check the link I supplied ([http://clickmojo.com/code/cron-tutorial.html](http://clickmojo.com/code/cron-tutorial.html)) for more information.

-------------------------------------
*[COLOR="Magenta"]MAILTO=yourusername@yourdomain.com[/COLOR]* sets up an email address to which cron will send messages should any issues arise.

-------------------------------------
*[COLOR="Magenta"]*/5 * * * * /usr/local/sbin/continuous.sh[/COLOR]* this runs the continuous.sh script every five minutes.

-------------------------------------
*[COLOR="Magenta"]6 */1 * * * /usr/local/sbin/hourly.sh[/COLOR]* this runs the hourly.sh script six minutes after every hour.

-------------------------------------
*[COLOR="Magenta"]16 02 * * * /usr/local/sbin/daily.sh[/COLOR]* this runs the daily script every day at 2:16 am.

-------------------------------------
*[COLOR="Magenta"]26 03 * * sun /usr/local/sbin/weekly.sh[/COLOR]* this runs the weekly script every sunday at 3:26 am.



**_[SIZE="3"]Step 3: Test your scripts.[/SIZE]_**

I am a big fan of testing all of my automated scripts.  It is far too easy to accidentally make a typo and then any vital functionality that you depend on may simply fail silently.

To test our master scripts (and cron), we are going to create a simple script inside each of the script collection directories.  We will wait to see that they are actually called before removing them again and being satisfied that every thing is working.

Note: whenever creating new scripts that you intend to throw into one of these script collection directories, ALWAYS create it in your own home directory first, and test it there!  If you create it directly in one of these directories it is possible (especially with the continuous directory) that cron will come by and execute while you are in the middle of editing it.  That could lead to some disastrous results.



-------------------------------------
Test the continuous scripts:

Create a new script in your home directory called testContinuous.sh:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico ~/testContinuous.sh
[/COLOR][/FONT][/B][/INDENT]
and paste or type the following into it:
```

#!/bin/bash

echo "test of the continuous scripts" | mail -s "test of the continuous scripts" youremail@yourdomain.com

```
Note: you will want to change the email to actually point to your correct email address.

Save and close the file.

change its permissions so that it is executable:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo chmod u+x ~/testContinuous.sh
[/COLOR][/FONT][/B][/INDENT]
and test it by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	 sudo ~/testContinuous.sh
[/COLOR][/FONT][/B][/INDENT]
You should receive an email with the subject: *[COLOR="Magenta"]test of the continuous scripts[/COLOR]*

If that worked, move the script into your /usr/local/sbin/continuous.active directory:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mv ~/testContinuous.sh /usr/local/sbin/continuous.active/testContinuous.sh
[/COLOR][/FONT][/B][/INDENT]



-------------------------------------
Test the hourly scripts:

Create a new script in your home directory called testHourly.sh:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico ~/testHourly.sh
[/COLOR][/FONT][/B][/INDENT]
and paste or type the following into it:
```

#!/bin/bash

echo "test of the hourly scripts" | mail -s "test of the hourly scripts" youremail@yourdomain.com

```
Note: you will want to change the email to actually point to your correct email address.

Save and close the file.

change its permissions so that it is executable:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo chmod u+x ~/testHourly.sh
[/COLOR][/FONT][/B][/INDENT]
and test it by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	 sudo ~/testHourly.sh
[/COLOR][/FONT][/B][/INDENT]
You should receive an email with the subject: *[COLOR="Magenta"]test of the hourly scripts[/COLOR]*

If that worked, move the script into your /usr/local/sbin/hourly.active directory:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mv ~/testHourlys.sh /usr/local/sbin/hourly.active/testHourly.sh
[/COLOR][/FONT][/B][/INDENT]



-------------------------------------
Test the daily scripts:

Create a new script in your home directory called testDaily.sh:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico ~/testDaily.sh
[/COLOR][/FONT][/B][/INDENT]
and paste or type the following into it:
```

#!/bin/bash

echo "test of the daily scripts" | mail -s "test of the daily scripts" youremail@yourdomain.com

```
Note: you will want to change the email to actually point to your correct email address.

Save and close the file.

change its permissions so that it is executable:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo chmod u+x ~/testDaily.sh
[/COLOR][/FONT][/B][/INDENT]
and test it by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo ~/testDaily.sh
[/COLOR][/FONT][/B][/INDENT]
You should receive an email with the subject: *[COLOR="Magenta"]test of the daily scripts[/COLOR]*

If that worked, move the script into your /usr/local/sbin/daily.active directory:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mv ~/testDaily.sh /usr/local/sbin/daily.active/testDaily.sh
[/COLOR][/FONT][/B][/INDENT]



-------------------------------------
Test the weekly scripts:

Create a new script in your home directory called testWeekly.sh:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico ~/testWeekly.sh
[/COLOR][/FONT][/B][/INDENT]
and paste or type the following into it:
```

#!/bin/bash

echo "test of the weekly scripts" | mail -s "test of the weekly scripts" youremail@yourdomain.com

```
Note: you will want to change the email to actually point to your correct email address.

Save and close the file.

change its permissions so that it is executable:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo chmod u+x ~/testWeekly.sh
[/COLOR][/FONT][/B][/INDENT]
and test it by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo ~/testWeekly.sh
[/COLOR][/FONT][/B][/INDENT]
You should receive an email with the subject: *[COLOR="Magenta"]test of the weekly scripts[/COLOR]*

If that worked, move the script into your /usr/local/sbin/wekly.active directory:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mv ~/testWeekly.sh /usr/local/sbin/weekly.active/testWeekly.sh
[/COLOR][/FONT][/B][/INDENT]





Leave each of these scripts in their respective directories until you get the email message from each one.  This will tell you that your cron job and its associated scripts are working.  You should get your first email within 5 minutes.  The next one within an hour or so, the third one within a day, and the last one within a week.  Of course, once you have gotten each email, you should delete the appropriate script from the .active directory.  Or, as an example of how you will more commonly be manipulating these scripts, move it into the associated .inactive directory.  There it will sit ready to be used again if needed.  To do this for the testContinuous.sh script, type the following:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mv /usr/local/sbin/continuous.active/testContinuous.sh /usr/local/sbin/continuous.inactive/testContinuous.sh
[/COLOR][/FONT][/B][/INDENT]
Moving the other three scripts is done in the same way.









[B][SIZE="4"][COLOR="RoyalBlue"]Section #13 - Install system health monitoring tools
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.



This puppy is going to be sitting in the corner doing it's thing and we will forget to check on it.  It's just a given.  To that end, we will want to install a number of system monitoring tools that will notify us of any unhealthy situations.  Specifically, we will want to monitor the health of the individual hard drives by checking their S.M.A.R.T. status (google it if you don't know that that is), the temperature of the drives, the temperature of the processor, and the health of the mdadm RAID array.


[COLOR="Red"]BIG NOTE:  As it happens, my particular setup (intel d510mo motherboard with Rosewill RC-217 4-port SATA card and 4 Western Digital 1TB drives) gets flaky when using S.M.A.R.T.  Specifically, it would lock up the computer occasionally when accessing S.M.A.R.T. data either via a self test or from hddtemp.  It would also cause my system to freeze on boot.  It is inconsistent and seems to be related to when I move large amounts of data.  I am still trying to figure out what is causing the issue, but for now I have turned off any S.M.A.R.T. monitoring (which seems to fix the issue).  I still think you should go through the following steps and only disable S.M.A.R.T. if your system becomes unstable.[/COLOR]


**_[SIZE="3"]Step 1: Install smartmontools to monitor your hard drives.[/SIZE]_**

The smartmontools will allow us to check the S.M.A.R.T. status periodically as well as keep track of the drive temperatures.  To install these tools, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get install smartmontools
[/COLOR][/FONT][/B][/INDENT]


**_[SIZE="3"]Step 2: Use smartctl to interactively check the health of your drives.[/SIZE]_**

After smartmontools is installed, we should do a few manual tests to make sure that everything is ok with our drives before we bother setting up the automatic monitoring.  Note, nearly all of the information in this section is lifted from the following website: [http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/](http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/).  I highly recommend reading through that page as it gives an excellent primer on using smartmontools for new users.  I am summarizing what that page has to offer here:

First, lets make sure that our drives have S.M.A.R.T. monitoring turned on (Note, I am using /dev/sdb here as an example.  You will want to run the following tools once per drive in your system).
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo smartctl -s on -o on -S on /dev/sdb
[/COLOR][/FONT][/B][/INDENT]

To paraphrase the shadypixel blog, Here is what it all means:  

-------------------------------------
*[COLOR="Magenta"]-s on[/COLOR]* turns on S.M.A.R.T. support or does nothing if it’s already enabled.

-------------------------------------
*[COLOR="Magenta"]-o on[/COLOR]* turns on offline data collection. Offline data collection periodically updates certain S.M.A.R.T. attributes while the system is on. Theoretically this could have a performance impact. However, from the smartctl man page: "Normally, the disk will suspend offline testing while disk accesses are taking place, and then automatically resume it when the disk would otherwise be idle, so in practice it has little effect."

-------------------------------------
*[COLOR="Magenta"]-S on[/COLOR]* enables “autosave of device vendor-specific Attributes”.

-------------------------------------
*[COLOR="Magenta"]/dev/sdb[/COLOR]* is the device name that you want to enable S.M.A.R.T for.


Upon running this command, you should get a response along these lines:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, [noparse]http://smartmontools.sourceforge.net[/noparse]

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.
SMART Attribute Autosave Enabled.
SMART Automatic Offline Testing Enabled every four hours.
[/COLOR][/FONT][/B][/INDENT]

Next, we will run a short test of the drive.  The short test is less comprehensive than a full blown test, but it has the advantage of only taking about two minutes to run.  To run this test, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo smartctl -t short /dev/sdb
[/COLOR][/FONT][/B][/INDENT]
You should get something like this in response:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, [noparse]http://smartmontools.sourceforge.net[/noparse]

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Wed Nov  9 23:03:06 2011 
[/COLOR][/FONT][/B][/INDENT]
The key thing to take away from this output is that the test will take about two minutes to run.  It also gives you a time after which you may come back to see what the results are.  Note that the test is running in the background and does not block you from using either the ssh session or the computer in general.

To see the results of the test, wait two minutes and then type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo smartctl -l selftest /dev/sdb
[/COLOR][/FONT][/B][/INDENT]
Of course, if you run it too soon, you will not get the data you are interested in.  You must wait till the test is done to get the appropriate information.  Once the test is complete, and you run the above command, you should get an output something like this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, [noparse]http://smartmontools.sourceforge.net[/noparse]

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        41         -
[/COLOR][/FONT][/B][/INDENT]
As should be obvious, the key item in this output is the text that says *[COLOR="Magenta"]Completed without error[/COLOR]*.  If you get a different result, then it is time to start googling and, perhaps, exchange a drive.



**_[SIZE="3"]Step 3: Repeat the above steps for each of your drives.[/SIZE]_**

Repeat the above steps for each drive in your array.



**_[SIZE="3"]Step 4: Configure smartd to run these tests automatically.[/SIZE]_**

The above steps we ran manually, but ideally the system will automatically run these tests and notify us if there is a problem.  To do this we will rely on a tool called smartd.  To configure smartd, we need to edit the /etc/smartd.conf file.  Do this by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico /etc/smartd.conf
[/COLOR][/FONT][/B][/INDENT]
The very first step is to prevent smarted from automatically scanning for devices since we will be explicitly telling it which drives to scan.  To do this, find the line that begins with:
[INDENT]
	*[COLOR="Magenta"]DEVICESCAN[/COLOR]*  (there will be some text following it)
[/INDENT]
and prepend it with a pound sign so that it reads:
[INDENT]
	*[COLOR="Magenta"]#DEVICESCAN[/COLOR]*  (followed by its text)
[/INDENT]

Next we will explicitly add the drives we want smartd to monitor.  To do this, we will add a single line per device that is in the following pattern.  Note that in this first incarnation we are setting smartd up in a test mode until we can verify that it is properly working.  Once we are satisfied that it is properly monitoring the drives, we will return to this config file and edit it so that it will no longer be in test mode.  Start by adding one line per device that adheres to the following pattern:

```
	/dev/sdb -a -d sat -o on -S on -s (S/../.././02|L/../../6/03) -m myemail@myemailprovider.com -M test #exec /usr/share/smartmontools/smartd-runner

```

Again, to paraphrase the excellent shadypixel blog:

-------------------------------------
*[COLOR="Magenta"]/dev/sdb[/COLOR]*: Replace this with the device you wish to monitor. Note that this is the raw drive, not a partition on the drive (i.e. there is no number at the end of the device name).

-------------------------------------
*[COLOR="Magenta"]-a[/COLOR]*: This enables some common options. You almost certainly want to use it. (type **[FONT="Courier New"][COLOR="RoyalBlue"]man smartd[/COLOR][/FONT]** for more information on what, exactly, it does)

-------------------------------------
*[COLOR="Magenta"]-d sat[/COLOR]*: On my system, smartctl correctly guesses that I have a serial ata drive. smartd on the other hand does not. If you had to add a “-d TYPE” parameter to the smartctl commands, you’ll almost certainly have to do the same here. If you didn’t, try leaving it out initially. You can add it later if smartd fails to start.

-------------------------------------
*[COLOR="Magenta"]-o on[/COLOR]*, *[COLOR="Magenta"]-S on[/COLOR]*: These have the same meaning as the smartctl equivalents

-------------------------------------
*[COLOR="Magenta"]-s (S/../.././02|L/../../6/03)[/COLOR]*: This schedules the short and long self-tests. In this example, the short self-test will run daily at 2:00 A.M. The long test will run on Saturday’s at 3:00 A.M. For more information, type **[FONT="Courier New"][COLOR="RoyalBlue"]man smartd.conf[/COLOR][/FONT]**.  Be aware that the system will need to actually be powered up and awake at those times in order for the tests to be run (we will be configuring the server to use power management later).

-------------------------------------
*[COLOR="Magenta"]-m [noparse]myemail@myemailprovider.com[/noparse][/COLOR]*: This is the email address to send error reports to.

-------------------------------------
*[COLOR="Magenta"]-M[/COLOR]* test:  Normally this settings is not used.  Its only purpose, as you might guess, is to test the smartd reporting system.  -M test will force smarted to send a message to the email address you supplied whenever it is started.  I have added this setting here so that we can satisfy ourselves that smartd is, in fact, able to send us a report.  Once we are sure that is working, we will return to this config file and remove that setting.

-------------------------------------
*[COLOR="Magenta"]-M exec /usr/share/smartmontools/smartd-runner[/COLOR]*:  smartd-runner will execute each script in /etc/smartmontools/run.d/.   These scripts are then responsible for emailing the user specified by the “-m” option.  It just offers a bit of flexibility that allows custom actions based on different S.M.A.R.T. events.


save and close the file.



To get smartd running, you will need to edit the /etc/default/smartmontools.  To do this, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico /etc/default/smartmontools
[/COLOR][/FONT][/B][/INDENT]
 find the line that says:  
[INDENT][I][COLOR="Magenta"]
	#start_smartd=yes
[/COLOR][/I][/INDENT]
and uncomment it so that it reads:
[INDENT][I][COLOR="Magenta"]
	start_smartd=yes
[/COLOR][/I][/INDENT]
save and close this file.



**_[SIZE="3"]Step 5: Restart smartd and make sure it properly sends an email.[/SIZE]_**

Restart the smartd daemon by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo /etc/init.d/smartmontools restart
[/COLOR][/FONT][/B][/INDENT]
Now check your email.  You should hopefully have gotten a message whose subject is similar to the following:
[INDENT][I][COLOR="Magenta"]
	SMART error (EmailTest) detected on host: ubuntu
[/COLOR][/I][/INDENT]
Note, your host name is most likely something different.  Also, this is not an actual error message, but instead just a test (as you can see by looking at the body of the message).  Finally, you should have gotten one email message per line that you added into the smartd.conf file.

Assuming you properly received the emails, we will want to edit the smartd.conf file one more time to remove the test setting.  To do this, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico /etc/smartd.conf
[/COLOR][/FONT][/B][/INDENT]
Edit each of the lines you added in step 4 and remove the -M test # (Note: make sure you remove the # sign that comes right after the word test!).  Save and close the file.



**_[SIZE="3"]Step 6: Install hddtemp to monitor the temperature of your hard drives.[/SIZE]_**

(I referred to this website when working on this section: [http://www.cyberciti.biz/tips/howto-monitor-hard-drive-temperature.html](http://www.cyberciti.biz/tips/howto-monitor-hard-drive-temperature.html))

S.M.A.R.T. also allows you to monitor the temperature of your hard drives.  But we will use a package called hddtemp to actually manage this feature (it still relies on the S.M.A.R.T. monitoring hardware on your drives).

To install the package, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get install hddtemp
[/COLOR][/FONT][/B][/INDENT]
Upon installation, hddtemp will ask whether it should be run automatically as a daemon.  By default it suggests that you not do this and in fact we won't.  Select "no".

hddtemp has a very simple usage.  Simply type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo hddtemp /dev/sdb
[/COLOR][/FONT][/B][/INDENT]
you should get an output that looks something like this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	/dev/sdb: WDC WD10EARS-00MVWB0: 22°C
[/COLOR][/FONT][/B][/INDENT]


**_[SIZE="3"]Step 7: Create a shell script to monitor hard drive temps and shut down the server if necessary.[/SIZE]_**

Being able to interactively run hddtemp is fantastic, but we need it to actually monitor the drive temperatures on an ongoing basis and take action should the temperatures rise too high.  Running hddtemp in daemon mode is not the solution however.  As far as I can tell it merely listens to requests on TCP port 7634 and will report back the temperature when querried from a remote machine.  This is less than ideal for our situation for a number of reasons.  First, it requires that a second machine regularly check the temperature (or that we do it manually).  Second, it requires that we punch yet another hole through the firewall (which isn't a big deal if we actually gained something significant for it, but that isn't the case here).

Instead, we will create a shell script to monitor the drive temperatures and shut down the server if they go above 50 degrees C.  This shell script will be dropped into the hourly.active directory we created earlier and will therefore run every hour.

We will start by creating this script in our administrative user's home directory.  We never want to create a script directly in the hourly.active directory because it should be fully tested before being placed there.  To create this script, type the following:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico ~/hddtemp_monitor.sh
[/COLOR][/FONT][/B][/INDENT]
and then paste or type in the following:

```
#!/bin/bash
HDDS="/dev/sdb /dev/sdc /dev/sdd /dev/sde"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=50
for disk in $HDDS
do
  if [ -b $disk ]; then
	HDTEMP=$($HDT $disk | awk '{ print $4}' | awk -F '°' '{ print $1}')
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
           echo "The server ubuntu is shutting down due to excessive hard drive temp. Drive: $disk has reached a temperature of $HDTEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server ubuntu is shutting down due to excessive hard drive temperature" youremail@yourdomain.com
           $LOG "System going down as hard disk : $disk temperature $HDTEMP°C crossed its limit"
           sync;sync
           $DOWN -h 0
        fi
  fi
done
```

Note: you will want to change the message in the script to one that makes sense for you (mainly change the name of the server).  Also, make sure you change the email to your email address.  If you want to use a temperature threshold other than 50 degrees C, you should also alter the line that reads:
[INDENT][I][COLOR="Magenta"]
	ALERT_LEVEL=50
[/COLOR][/I][/INDENT]
Save and close the file when you are done.



Change the permissions on the file so that it becomes an executable script.  Do this by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo chmod ugo+rwx ~/hddtemp_monitor.sh
[/COLOR][/FONT][/B][/INDENT] 

Again, because I am a big believer in testing our scripts, we should set it up to see whether it actually works.  To do this, we will set the temperature threshold to 1 degree C.  To do that, edit the file by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico ~/hddtemp_monitor.sh
[/COLOR][/FONT][/B][/INDENT]
and change the line that reads:
[INDENT][I][COLOR="Magenta"]
	ALERT_LEVEL=50
[/COLOR][/I][/INDENT]
to something much lower (say, 1 degree).  For example:
[INDENT][I][COLOR="Magenta"]
	ALERT_LEVEL=1
[/COLOR][/I][/INDENT]
and save and close the file.

[COLOR="Red"]Note: testing this script will shut down your server immediately!  It will boot you off of your ssh session.  It will stop any running processes you may have.  So don't test this if there is any reason why you shouldn't shut down the computer right now.  That said, if you have been following this tutorial, there really isn't anything that should be running that would prevent you from shutting the machine down.[/COLOR]

To test the script, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	 sudo ~/hddtemp_monitor.sh
[/COLOR][/FONT][/B][/INDENT]
with any luck, your server will have shut down almost immediately and you will have received an alert email message.  If so, go ahead and restart the server, and re-log in via ssh.

Now, change the ALERT_LEVEL back up to 50 degrees C (or whatever value you want to use) To do that, edit the file by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico ~/hddtemp_monitor.sh
[/COLOR][/FONT][/B][/INDENT]
and change the line that reads:
[INDENT][I][COLOR="Magenta"]
	ALERT_LEVEL=1
[/COLOR][/I][/INDENT]
back to 50 degrees:
[INDENT][I][COLOR="Magenta"]
	ALERT_LEVEL=50
[/COLOR][/I][/INDENT]
and save and close the file.

Now move it into the hourly.active directory by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mv ~/hddtemp_monitor.sh /usr/local/sbin/hourly.active/hddtemp_monitor.sh
[/COLOR][/FONT][/B][/INDENT]




**_[SIZE="3"]Step 7: Get mdadm to send emails when it encounters errors.[/SIZE]_**

(I used the following website when working through this section: [http://blog.agdunn.net/?p=383](http://blog.agdunn.net/?p=383))

S.M.A.R.T. monitoring checks the physical health of your drives, as does hddtemp.  But we also want to keep tabs on the health of the actual RAID array.  Fortunately this is an exceptionally easy thing to set up.  We simply need to tell mdadm where to send its emails.  To do this, edit the mdadm.conf file.  To do this, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico /etc/mdadm/mdamd.conf
[/COLOR][/FONT][/B][/INDENT]
Find the line that starts with:
[INDENT][I][COLOR="Magenta"]
	MAILADDR
[/COLOR][/I][/INDENT]
and make sure it points to your email address (so it looks something like this):
[INDENT][I][COLOR="Magenta"]
	MAILADDR [noparse]youremail@yourdomain.com[/noparse]
[/COLOR][/I][/INDENT]
Save and close the file.

Now let's run a quick test to make sure it is all working.  Type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mdadm --monitor --scan --test
[/COLOR][/FONT][/B][/INDENT]
This will cause mdadm to send you a test email message.  Note, you will not be automatically returned to the command line.  Once you have verified that you have received the test email, you can press **[FONT="Courier New"][COLOR="RoyalBlue"]ctrl-c[/COLOR][/FONT]** to stop mdadm from running in monitor mode.




**_[SIZE="3"]Step 8: Install lm-sensors to monitor the temperature of your system.[/SIZE]_**

(I used this website as reference for this section: [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto))

We also want to monitor the temperature of our processor (and any other sensors our main board supports).  To do this, we need to install lm-sensors to track that information.  To install, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get install lm-sensors
[/COLOR][/FONT][/B][/INDENT]
Once it is installed, we want to run a utility called sensors-detect.  This will attempt to detect all the different sensors on your motherboard.  To run this app, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo sensors-detect
[/COLOR][/FONT][/B][/INDENT]
and answer "yes" to ALL of the questions (there are an awful lot of them!).   You especially want to answer YES when it asks:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Do you want to add these lines automatically to /etc/modules? (yes/NO)
[/COLOR][/FONT][/B][/INDENT]
as this will edit the /etc/modules file and append any sensors it found.

Next we need to insert the new modules into the kernel.  Do this by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo /etc/init.d/module-init-tools restart 
[/COLOR][/FONT][/B][/INDENT]
Now, when you type the command:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo sensors
[/COLOR][/FONT][/B][/INDENT]
you should get back a detailed set of voltages and temperatures from your system.  Note that some figures may be completely wrong.  This, apparently, is normal and you may need to edit your sensors.conf file to either adjust or ignore some of these bogus readings.  I would help you out with that, but as it happens my board (intel d510mo) refuses to report back ANY real information.  Apparently this is a known issue and updating the BIOS should have fixed it but I am still fighting with that.  

Just note that having lm-sensors installed is not enough to monitor your system.  You need to somehow check the sensors from time to time and act upon the information received.

We will again be using a script to keep track of the output of the sensors command.  We will start by creating this script in our administrative user's home directory.  We never want to create a script directly in the hourly.active directory because it should be fully tested before being placed there.  To create this script, type the following:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico ~/sensors_montior.sh
[/COLOR][/FONT][/B][/INDENT]
and then paste or type in the following (note, you may have to heavily edit this script depending on what kind of data you get back from the sensors command.  I can try to help you with this if you have issues.):

```
#!/bin/bash
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=80
SENSORSCMD=sensors

CORE0TEMP=$($SENSORSCMD | grep -i "Core 0" | awk '{print $3}' | awk -F '°' '{print $1}' | awk -F '+' '{print $2}' | awk -F '.' '{print $1}')
CORE1TEMP=$($SENSORSCMD | grep -i "Core 1" | awk '{print $3}' | awk -F '°' '{print $1}' | awk -F '+' '{print $2}' | awk -F '.' '{print $1}')

if [[ $CORE0TEMP =~ ^[0-9]+$ ]]; then
   if [ $CORE0TEMP -ge $ALERT_LEVEL ]; then
       echo "The server ubuntu is shutting down due to excessive Core 0 temp (it has reached a temperature of $CORE0TEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server ubuntu is shutting down due to excessive CPU temperature" youremail@yourdomain.com
       $LOG "System going down as Core 0 has crossed its limit (temp=$CORE0TEMP°C, limit=$ALERT_LEVEL°C"
       sync;sync
       $DOWN -h 0
   fi
fi

if [[ $CORE1TEMP =~ ^[0-9]+$ ]]; then
   if [ $CORE1TEMP -ge $ALERT_LEVEL ]; then
      echo "The server ubuntu is shutting down due to excessive Core 1 temp (it has reached a temperature of $CORE1TEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server ubuntu is shutting down due to excessive CPU temperature" youremail@yourdomain.com
      $LOG "System going down as Core 1 has crossed its limit (temp=$CORE1TEMP°C, limit=$ALERT_LEVEL°C"
      sync;sync
      $DOWN -h 0
   fi
fi
```

Note: you will want to change the message in the script to one that makes sense for you (mainly change the name of the server).  Also, make sure you change the email to your email address.  If you want to use a temperature threshold other than 80 degrees C, you should also alter the line that reads:
[INDENT][I][COLOR="Magenta"]
	ALERT_LEVEL=80
[/COLOR][/I][/INDENT]
Save and close the file when you are done.

Change the permissions on the file so that it becomes an executable script.  Do this by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
        sudo chmod ugo+rwx ~/sensors_monitor.sh
[/COLOR][/FONT][/B][/INDENT] 



Again, because I am a big believer in testing our scripts, we should set it up to see whether it actually works.  To do this, we will set the temperature threshold to 1 degree C.  To do that, edit the file by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico ~/sensors_montior.sh
[/COLOR][/FONT][/B][/INDENT]
and change the line that reads:
[INDENT][I][COLOR="Magenta"]
	ALERT_LEVEL=80
[/COLOR][/I][/INDENT]
to something much lower (say, 1 degree).  For example:
[INDENT][I][COLOR="Magenta"]
	ALERT_LEVEL=1
[/COLOR][/I][/INDENT]
and save and close the file.

[COLOR="Red"]Note: testing this script will shut down your server immediately!  It will boot you off of your ssh session.  It will stop any running processes you may have.  So don't test this if there is any reason why you shouldn't shut down the computer right now.  That said, if you have been following this tutorial, there really isn't anything that should be running that would prevent you from shutting the machine down.[/COLOR]

To test the script, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	 sudo ~/sensors_monitor.sh
[/COLOR][/FONT][/B][/INDENT]
with any luck, your server will have shut down almost immediately and you will have received an alert email message.  If so, go ahead and restart the server, and re-log in via ssh.

Now, change the ALERT_LEVEL back up to 80 degrees C (or whatever value you want to use).  To do that, edit the file by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico ~/sensors_montior.sh
[/COLOR][/FONT][/B][/INDENT]
and change the line that reads:
[INDENT][I][COLOR="Magenta"]
	ALERT_LEVEL=1
[/COLOR][/I][/INDENT]
back to 80 degrees:
[INDENT][I][COLOR="Magenta"]
	ALERT_LEVEL=80
[/COLOR][/I][/INDENT]
and save and close the file.

Now move it into the hourly.active directory by typing (this will make it run once every hour):
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mv ~/sensors_monitor.sh /usr/local/sbin/hourly.active/sensors_monitor.sh
[/COLOR][/FONT][/B][/INDENT]






[B][SIZE="4"][COLOR="RoyalBlue"]Section #14 - Power management
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.


This machine is going to be living a very lazy life.  90% of the time it will have absolutely nothing to do.  So why have it up and drives spinning this whole time?  Answer: we won't.  In this section we are going to set it up so that the machine spends most of its time trying to go to sleep.  It will only stay awake if:

1) there are other machines on the network that are awake
2) it is currently performing an important task (aka, backing itself up)
3) it is a scheduled "awake" time (aka during system maintenance)


**_[SIZE="3"]Step 1: Install pm-utils.[/SIZE]_**

Most of our power management will be handled by a package called pm-utils.  To install it, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get install pm-utils
[/COLOR][/FONT][/B][/INDENT]
Test to make sure the computer has the ability to go to sleep.  But before you do, here is a tiny tiny tutorial on the differences between hibernate and sleep:

**Suspend:**
Suspend shuts down as much of the computer as it can, but keeps the RAM powered so as not to lose your system's state.  In this state, your server is still drawing some power but much less than if it were fully awake.  If there were a power failure, however, the contents of your RAM will be lost and the next time the computer is started there may be the normal issues of a system that was not properly shut down.  The advantage of running in this "lighter sleep" is that the system wakes up fairly quickly.

**Hibernate:**
Hibernate copies the contents of the system's RAM to disk and then shuts the computer down to a nearly completely un-powered state (only the ethernet card should still be drawing power).  Upon waking up, the machine will boot back into the last saved state by reading the contents of the saved RAM into memory.  A power failure while the server is asleep does cause any issues as the memory is completely stored in a nonvolatile state.  So even after a power failure (while the server was asleep) your system will still boot back into the state it was in when it last went to sleep.  The disadvantage is that it takes the system much longer to wake up than when merely suspended.  On my system it takes about 45 seconds from dead sleep to fully awake.

**Hybrid:**
There is a third setting called pm-suspend-hybrid which acts as a combination of suspend and hibernate.  Using this, the contents of RAM are written to disk just as though the hibernate command had been issued.  But the computer itself only goes into a light sleep as though the suspend command had been issued.  If there is no power outage while the machine is asleep it will merely wake up as though it had only been suspended.  If, however, the system loses power while it is asleep, it will still manage to recover to its most recent state by booting from the hibernate image.  The advantages of this are all the speed of the Suspend method, with the robustness of the Hibernate method.  The disadvantage is that it takes more time to go to sleep (as it still has to write memory to disk) and it still uses more power than a fully hibernating system.

For a few reasons, I have settled on the hibernate strategy.  The first is that I am after as low power a system as possible.  The second is that I prefer the robustness of this technique over the speed of the Suspend technique (I have no intense need to access the server within 45 seconds of sitting down at my computer).  You should feel free to use whichever version your system supports and that makes sense to you.

Test hibernation by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pm-hibernate
[/COLOR][/FONT][/B][/INDENT]
Be aware that this will leave your ssh session hanging.  If you manage to wake the system up within a fairly short period of time (by pressing the power button on the server or sending it a magic packet) your ssh session will resume.  If you wait too long, however, you may have to re-log in.



**_[SIZE="3"]Step 2: Install fping.[/SIZE]_**

Our server will be the last machine on the network to go to sleep.  Specifically, it will periodically check the network to see if any other systems are on and awake.  If it finds that other machines are up and about, it will simply continue to run.  If, however, it finds that it is the last machine standing, it will put itself to sleep,  No need to serve files when nobody else is up, eh?  In order to accomplish this, it will need to be able to scan the network for other, non-sleeping machines.

Normally, the standard way of checking to see if a computer is on a network and listening for commands is to send it a "ping" command.  For example, if you wanted to see if your server were up and running, you could issue the following command from the command line on your Mac:
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]ping 172.16.1.100[/COLOR][/FONT]**   <-- of course, you would have to substitute the actual IP address of your server here.
[/INDENT]
If your server is active, you should get back the following response:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
PING 172.16.1.100 (172.16.1.10): 56 data bytes
64 bytes from 172.16.1.100: icmp_seq=0 ttl=64 time=1.708 ms
64 bytes from 172.16.1.100: icmp_seq=1 ttl=64 time=1.538 ms
64 bytes from 172.16.1.100: icmp_seq=2 ttl=64 time=1.527 ms
[/COLOR][/FONT][/B][/INDENT]
(you will have to hit **[FONT="Courier New"][COLOR="RoyalBlue"]ctrl-c[/COLOR][/FONT]** to stop it).

In our case, we will want to scan our network for multiple computers at the same time.  That is where fping comes in.  It is able to simultaneously "ping" multiple IP addresses at the same time.  To install it, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get install fping
[/COLOR][/FONT][/B][/INDENT]
Now, if we want to see what machines are up and about on our network, we would simply type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo fping -a -g 172.16.1.0/24
[/COLOR][/FONT][/B][/INDENT]
(translated, this means send a ping to every machine on the 172.16.1.* network).  You will get back something similar to this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
172.16.1.8
172.16.1.100
172.16.1.101
ICMP Host Unreachable from 172.16.1.100 for ICMP Echo sent to 172.16.1.2
ICMP Host Unreachable from 172.16.1.100 for ICMP Echo sent to 172.16.1.2
ICMP Host Unreachable from 172.16.1.100 for ICMP Echo sent to 172.16.1.3
etc...
[/COLOR][/FONT][/B][/INDENT]
This list will be very long and it will take a few moments before it stops spitting out those error messages.  fping has just let you know that there are three devices on the network that are currently responding to pings and a whole lot of addresses where nobody is listening.

For our purposes, we don't care about empty IP addresses, so let's modify the command we are issuing so that we only hear about active machines on the network.
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo fping -a -g 172.16.1.0/24 2> /dev/null
[/COLOR][/FONT][/B][/INDENT]
the section that reads 2> /dev/null effectively tells the shell to discard any error messages the command may generate (by throwing them into the Linux equivalent of a black hole: /dev/null).  Running this command will give you an output similar to this:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
172.16.1.8
172.16.1.100
172.16.1.101
[/COLOR][/FONT][/B][/INDENT]
That's great.   Now we know that there are three active devices on the network, and we are not besieged by millions of unnecessary error messages about unused addresses.

Now think back to when you first started setting up the server.  Remember the section where I told you to put your server on a static IP address (mine is set to 172.16.1.100)?  Remember also that I suggested that any other non-client devices be assigned static addresses as well (my HP printer is set to 172.16.1.101)?  Those actions are showing up here.  I have three machines on the network, but two of them (the server itself at 172.16.1.100 and the printer at 172.16.1.101) are never going to be clients of the server.  In fact, any IP address of 172.16.1.100 and above will never actually be a client of my server.  Also, due to the way the Apple Airport Extreme works, it will always assign itself to the address 172.16.1.1.  So instead of using fping to scan the entire network for listening devices, I am only going to scan the range of possible clients.  This range is 172.16.1.2 - 172.16.1.99.  So let's modify the fping command as follows:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo fping -a -g 172.16.1.2 172.16.1.99 2> /dev/null
[/COLOR][/FONT][/B][/INDENT]
We should now only get a list of IP addresses that are listening AND are not either my server, router, printer, etc…  For example:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	172.16.1.8
[/COLOR][/FONT][/B][/INDENT]
Ta da!  And that's it.  We now have a way of getting a list of active clients on our network.  



**_[SIZE="3"]Step 3: Write a script to have the server automatically go to sleep.[/SIZE]_**

Now let's convert this into a simple script that can periodically scan the network and put the server to sleep if there are no active clients listening.  We will start by creating this script in our administrative user's home directory.  We never want to create a script directly in the continuous.active directory because it should be fully tested before being placed there.  To create this script, type the following:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico ~/check_for_active_clients.sh
[/COLOR][/FONT][/B][/INDENT]
and then paste or type in the following (note, you will have to edit this script depending on your specific network configuration - aka IP addresses.  I can try to help you with this if you have issues.):

```
#! /bin/bash

#check to see if any other devices are responding to pings
#only check addresses 172.16.1.2 - 172.16.1.99 because
#the Airport is always on address 172.16.1.1 and all of my
#always on devices (that don't need server access) have
#reserved IP address of 172.16.1.100 and above

#if there are no responding clients in the ip range, go to sleep
if [ `/usr/bin/fping -a -g 172.16.1.2 172.16.1.99 2> /dev/null | wc -l` -eq 0 ]; then
	/usr/sbin/pm-hibernate
fi
```

Save and close the file when you are done.

Change the permissions on the file so that it becomes an executable script.  Do this by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo chmod ugo+rwx ~/check_for_active_clients.sh
[/COLOR][/FONT][/B][/INDENT] 
Again, because I am a big believer in testing our scripts, we should set it up to see whether it actually works.  Unfortunately, this one is difficult to test from another machine simply because the existence of this other machine on the network will cause the script to do nothing.  So, we will need to test it directly from the console connected to the server.

Start by making sure that every device on your network with a dynamically assigned IP address is turned off (or asleep).

Next, physically log into your server from the console.

Once you are logged in, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo ~/check_for_active_clients.sh
[/COLOR][/FONT][/B][/INDENT]
(you will be prompted for your password).

The server should process for a few moments and then go to sleep.  Once it has, hit the power button to wake it back up.  Confirm that it wakes up back to the point where you had left it.  If this works, log out of the console and return to your regular computer (which should still have ssh access.  If not, ssh back into the server to continue following this tutorial).

Now move this script into the continuous.active directory (this will make it run once every five minutes).  Do this by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo mv ~/check_for_active_clients.sh /usr/local/sbin/continuous.active/check_for_active_clients.sh
[/COLOR][/FONT][/B][/INDENT]
Test it again by putting your desktop computer (any any other devices using dynamically assigned IP addresses) to sleep.  Within five minutes you server should go to sleep.  If it does, wake it back up by hitting the power key.  Wake your desktop machine as well.  You should still be logged in via ssh as long as you did not let it sleep too long.



**_[SIZE="3"]Step 4: Get your client machines to automatically wake up the server.[/SIZE]_**

It is awesome that the server will automatically go to sleep when it is not needed, but we don't want to have to physically walk over to it and wake it up every time we wake up one of our client machines.  To remedy this, we will instruct our macs to automatically send a Wake-On-Lan magic packet to the server whenever they either start up or wake up.  To accomplish this, we will be using the excellent SleepWatcher tool running on our Macs and written by Bernhard Baehr (a man with an excellent first name by the way).  You can get his tool from: 

	[http://www.bernhard-baehr.de/](http://www.bernhard-baehr.de/)

Note to Windows users:  There must be similar tools available for your system.  Alas I don't know what they are and I am not interested in finding out.  I will update this post with any links if anyone has them to offer.

[COLOR="Red"]Note: much of the following is being done on our Macs!  Pay close attention to when you should be working on the command line on your Mac and when you should be working in the ssh session to your server![/COLOR]

**[COLOR="Red"]Mac:[/COLOR]** 		Download SleepWatcher 2.2 and install it as described in the associated ReadMe (I will leave it to you to properly install it.  The instructions included with the tool are clear and all I would be doing is repeating them here).

Next, we need a way of sending a magic packet from the command line on our Mac's.  The tool wol allows this (it is available for many different OS's as well).  Go to:

	[http://www.gknw.net/wol.html](http://www.gknw.net/wol.html)

and download the Mac OSX version of the tool.  Once downloaded, save the wol file (you don't ned the wol.c file) to /usr/local/sbin.  To do this, make sure you are in your downloads directory in the terminal and then type:

**[COLOR="Red"]Mac:[/COLOR]** 		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo mv ./wol /usr/local/sbin/[/COLOR][/FONT]**

make sure it is executably by typing:

**[COLOR="Red"]Mac:[/COLOR]** 		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo chmod ugo+rwx /usr/local/sbin/wol[/COLOR][/FONT]**

Now test the script to see if it works.  Put your server to sleep by typing:

**[COLOR="Red"]Ubuntu:[/COLOR]** 	**[FONT="Courier New"][COLOR="RoyalBlue"]sudo pm-suspend[/COLOR][/FONT]**

Your server should go to sleep in a few moments.  Once it has, let's try to wake it back up by typing (on your Mac):

**[COLOR="Red"]Mac:[/COLOR]** 		**[FONT="Courier New"][COLOR="RoyalBlue"]wol XX:XX:XX:XX:XX:XX[/COLOR][/FONT]**  <-- but replace the XX:XX:XX:XX:XX:XX with the MAC address of your server (you wrote it down ages ago when I told you to, right?)

Your server should wake back up.

So now lets write a script that will actually send this magic packet.  On your Mac, create a new script called wakeUbuntu.sh by typing:

**[COLOR="Red"]Mac:[/COLOR]** 		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo pico /usr/local/sbin/wakeUbuntu.sh[/COLOR][/FONT]**

and copy/type the following text into the file.

```
#! /bin/bash

sleep 10
/usr/local/sbin/wol XX:XX:XX:XX:XX:XX

```

Note, you will have to replace the XX:XX:XX:XX:XX:XX with the actual MAC address of your server.  Also, the sleep command near the top of the script merely tells the it to pause for 10 seconds before continuing.  I have added this because it can often take a little time before the Mac is fully connected to the wireless network.  Sending a magic packet before this time fails.

Save and close the file.

Make sure the script is executable by typing:

**[COLOR="Red"]Mac:[/COLOR]**	**[FONT="Courier New"][COLOR="RoyalBlue"]sudo chmod ugo+rwx /usr/local/sbin/wakeUbuntu.sh[/COLOR][/FONT]**

Test the script by putting your sever to sleep

**[COLOR="Red"]Ubuntu:[/COLOR]**	**[FONT="Courier New"][COLOR="RoyalBlue"]sudo pm-suspend[/COLOR][/FONT]**

and calling this script from the command line on your Mac:

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]/usr/local/sbin/wakeUbuntu.sh[/COLOR][/FONT]**

Your server should wake up.

Now, finally, we need to tell SleepWatcher to call this script whenever our Mac wakes up.  First run a test.  Start by putting your server back to sleep:

**[COLOR="Red"]Ubuntu:[/COLOR]**	**[FONT="Courier New"][COLOR="RoyalBlue"]sudo pm-suspend[/COLOR][/FONT]**

Next, type the following command on your Mac command line:

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]/usr/local/sbin/sleepwatcher --verbose --wakeup /usr/local/sbin/wakeUbuntu.sh[/COLOR][/FONT]**

Then put your Mac to sleep.  Wait a second or so to make sure it is fully sleeping, and then wake it up.  You should see that it wakes up and, in a few moments, executes the wakeUbuntu.sh script which then wakes up your server.  You should get an output similar to this on your Mac:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
/usr/local/sbin/wol: packet sent to EA60:FFFFFFFF-XX:XX:XX:XX:XX:XX 
sleepwatcher: wakeup: /usr/local/sbin/wakeUbuntu.sh: 0
[/COLOR][/FONT][/B][/INDENT]
Press **[FONT="Courier New"][COLOR="RoyalBlue"]ctrl-c[/COLOR][/FONT]** to cancel the sleepwatcher command.

Now we have to make sure that sleepwatcher is set up to run in the background.  To do this, we need to first edit the plist file that came with the tool.  Go to the directory where you downloaded sleepwatcher and then cd into the config directory:

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]cd ~/Downloads/sleepwatcher_2.2[/COLOR][/FONT]**
**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]cd config[/COLOR][/FONT]**

Next, edit the plist file by typing:

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo pico de.bernhard-baehr.sleepwatcher-20compatibility.plist[/COLOR][/FONT]**

find the line that says:
[INDENT][I][COLOR="Magenta"]
                <string>-s /etc/rc.sleep</string>
[/COLOR][/I][/INDENT]
and delete it (we are not interested in having anything run when our Mac goes to sleep).

Next, edit the line that says:
[INDENT][I][COLOR="Magenta"]
                <string>-w /etc/rc.wakeup</string>
[/COLOR][/I][/INDENT]
so that it now reads:

                <string>-w /usr/local/sbin/wakeUbuntu.sh</string>

(we want it to run our wake ubuntu script when the Mac wakes up).

Save and close the file.

Now move it to the LaunchDaemons directory.

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo mv de.bernhard-baehr.sleepwatcher-20compatibility.plist /Library/LaunchDaemons[/COLOR][/FONT]**

and change its permissions to be readable by all, writable only by root:

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo chmod ugo-rwx /Library/LaunchDaemons/de.bernhard-baehr.sleepwatcher-20compatibility.plist[/COLOR][/FONT]**
**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo chmod ugo+r /Library/LaunchDaemons/de.bernhard-baehr.sleepwatcher-20compatibility.plist[/COLOR][/FONT]**
**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo chmod u+w /Library/LaunchDaemons/de.bernhard-baehr.sleepwatcher-20compatibility.plist[/COLOR][/FONT]**

Note: as a shortcut, you could also just type:

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo chmod 644 /Library/LaunchDaemons/de.bernhard-baehr.sleepwatcher-20compatibility.plist[/COLOR][/FONT]**

which has the same effect as all three lines above.  It is just harder to remember (or derive) the exact numerical sequence for this pattern which is why I typically use the more verbose version above.

Now change its ownership so that it is owned by root:

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo chown root /Library/LaunchDaemons/de.bernhard-baehr.sleepwatcher-20compatibility.plist[/COLOR][/FONT]**

Finally, tell launchctl to load sleepwatcher automatcially:

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo launchctl load /Library/LaunchDaemons/de.bernhard-baehr.sleepwatcher-20compatibility.plist[/COLOR][/FONT]**

You should now be able to put your Mac to sleep, wait up to five minutes for the server to fall asleep, and then wake up your Mac (and have it wake your server within a few moments)!

Repeat this process for each Mac on your network that you want to automatically wake your server.







[B][SIZE="4"][COLOR="RoyalBlue"]Section #15 - Security: Install and configure DenyHosts
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.



Machines directly connected to the internet are the focus of an unbelievable number of attacks.  One such attack, I have read, is to try to brute force crack a system.  As far as I can tell, this involves repeatedly trying to log in on different ports with different user names and passwords.  Based on comments I have read, such attacks can occur hundreds of times per day - all of them simply random attempts to break into your system.

DenyHosts is a package which helps cut down on brute force attacks by watching your logs.  Any IP's that try to log into your system (and fail) a repeated number of times (between 5 and 10 times depending on the user name) are automatically blocked so they cannot make any further attempts.



**_[SIZE="3"]Step 1: Install and configure DenyHosts.[/SIZE]_**

Start by installing the package.
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get install denyhosts
[/COLOR][/FONT][/B][/INDENT]
Next we need configure it.  To do that, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo nano /etc/denyhosts.conf
[/COLOR][/FONT][/B][/INDENT]
Set:
[INDENT]
	[I][COLOR="Magenta"]PURGE_DENY = 5d
	PURGE_THRESHOLD = 2
	BLOCK_SERVICE = ALL[/COLOR][/I]  <--- you may also have to comment out the line that says BLOCK_SERVICE = sshd
[/INDENT]

Finally, find the line that starts with:
[INDENT][I][COLOR="Magenta"]
	WORK_DIR
[/COLOR][/I][/INDENT]
And make a note of the directory it lists (most likely it will be /var/lib/denyhosts).  Write it down.  Don't be lazy now, just write it down.

Save and close the file.



**_[SIZE="3"]Step 2: Build an exception for machines on your local network.[/SIZE]_**

DenyHosts, by default, will block ANY IP address if it fails to properly log in more than 10 times (5 times for non-valid user names).  This includes your Mac on your local network.  So, if you fat-finger your login attempt a bunch of times you could potentially lock yourself out of your own system.  Is this likely?  Not really, but it might be better if you set an exception to never block any of your local IP addresses.

I imagine this might be a slight security risk in case your Mac is compromised.  Of course, if that has happened then you have a whole host of other problems.  That said, I just don't know if this is a good idea or not.  If anyone has a particular opinion on this, I'd love to hear it.  For the time being, however, I am going to make an exception for local IP addresses.

To build a list of IP addresses that will never be blocked no matter what, we will create a file called allowed-hosts.  This file will live in the WORK_DIR you took note of above.  

Most likely, the IP address range you will be adding can be derived from the IP address of your server.  If it was, say: 
[INDENT][I][COLOR="Magenta"]
	172.16.1.16 
[/COLOR][/I][/INDENT]
then you would use:
[INDENT][I][COLOR="Magenta"]
	172.16.1.*
[/COLOR][/I][/INDENT]
(Just keep the first three numbers, and replace the last one with an asterisk.)

In the work directory that you wrote down in step 1 above, create a file named allowed-hosts:
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]sudo nano /var/lib/denyhosts/allowed-hosts[/COLOR][/FONT]**	<--- replace /var/lib/denyhosts with the directory you wrote down in step 1 above.	
Add the following (change the ip to match the pattern used for your subnet)
[/INDENT]
[INDENT]
	[I][COLOR="Magenta"]#always allow ssh from the local subnet
	172.16.1.*[/COLOR][/I]  <--- You should change this to match the pattern of your local subnet
[/INDENT]
Save and close the file.



**_[SIZE="3"]Step 3: Define some restricted user names.[/SIZE]_**

DenyHosts, by default, will lock out any IP address that tries to log in with a nonexistent user name after only 5 attempts.  If the user name is valid, however, it will allow a total of 10 login attempts before blocking the offending IP address.  However, there are a bunch of valid users on your system that have no business ever trying to log in remotely (or even locally).

We will add these users to a list of restricted user names.  By doing this, even though they are "valid" users on the system, they will be blocked after only a single failed attempt.

Get a list of all users by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	lastlog
[/COLOR][/FONT][/B][/INDENT]
You might want to open a TextEdit document so that you can copy the list of names into it.  In my case, the following users should not ever be logging in remotely:
[INDENT][I][COLOR="Magenta"]
	root
	daemon
	bin
	sys
	sync
	games
	man
	lp
	mail
	news
	uucp
	proxy
	www-data
	backup
	list
	irc
	gnats
	nobody
	libuuid
	syslog
	landscape
	sshd  
[/COLOR][/I][/INDENT]
Note that I include root in this list.  Root should never be logging in remotely and I suspect that it is one of the most common user names that automated break-in scripts try.  That said, there is already a setting in DenyHosts that limits root specifically.  Including root here is just overkill… but I am totally ok with that.   Depending on the packages you have installed on your system, you may have one or two additional users in this list.  The key is to include in this list all users who will never explicitly be logging into the system remotely (which is really all users except those you created specifically).  Also, note that if you add additional packages after this step (ftp, etc.) you may find that there are some additional users you would want to add to this list.  Feel free to do so, but also know that accidentally leaving a user off of this list isn't by itself a serious security threat.

You might note that the ONLY name NOT in this list is my original administrative user (admiral in the examples used thus far):



To mark these users as restricted, create a file named restricted-usernames in the work directory that you wrote down in step 1:
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]sudo nano /var/lib/denyhosts/restricted-usernames[/COLOR][/FONT]** <--- replace /var/lib/denyhosts with the directory you wrote down in step 1 above.
[/INDENT]		
Copy the names (just the names, not their last login time) into this file.

Save and close the file.


Restart DenyHosts
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo /etc/init.d/denyhosts restart
[/COLOR][/FONT][/B][/INDENT]







[B][SIZE="4"][COLOR="RoyalBlue"]Section #16 - Security: Configure various other settings to improve the default security
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.



There are a bunch of smaller things you can do to improve the security of your system.  They aren't the first line of defense, but they can certainly help.

I got much of this information from the following websites:

[http://www.upubuntu.com/2011/05/how-to-disable-ipv6-under-ubuntu.html](http://www.upubuntu.com/2011/05/how-to-disable-ipv6-under-ubuntu.html)
[https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults](https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults)


**_[SIZE="3"]Step 1: Turn off IPv6.[/SIZE]_**

Turn off IPv6 for now.  It is not really being used much yet and I have no idea what the security implications are for having it on.  We can turn it back on later if we need it and once we understand it better.  Start by editing /etc/sysctl.conf:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo nano /etc/sysctl.conf 
[/COLOR][/FONT][/B][/INDENT]
Add the following to the end of the file and then save:
[INDENT][I][COLOR="Magenta"]
	# IPv6
	net.ipv6.conf.all.disable_ipv6 = 1
	net.ipv6.conf.default.disable_ipv6 = 1
	net.ipv6.conf.lo.disable_ipv6 = 1
[/COLOR][/I][/INDENT]
Now, reload the configuration by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo sysctl -p
[/COLOR][/FONT][/B][/INDENT]
You can check to see if IPv6 is disabled by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	cat /proc/sys/net/ipv6/conf/all/disable_ipv6
[/COLOR][/FONT][/B][/INDENT]
If it returns a **[FONT="Courier New"][COLOR="SeaGreen"]1[/COLOR][/FONT]**, then IPv6 has been successfully disabled (I know this seems weird… I would have expected that returning 1 meant it was ON but… who knows?).











[B][SIZE="4"][COLOR="RoyalBlue"]Section #17: Security: Set up a firewall using ufw (Uncomplicated Firewall)
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.



Firewalls are a basic security tool, and most likely THE primary tool in your defense against intrusion.  Ubuntu 11.10 uses iptables to control your firewall rules (aka which ports are open to the outside world, and to whom they are open).  Unfortunately, iptables are notoriously difficult to work with.  Luckily Ubuntu ships with a tool called ufw (Uncomplicated Firewall) which is actually a tool that sits on top of iptables.  You instruct ufw with some fairly basic rules, and it translates those rules into actual iptables chains.  That said, ufw does not make a firewall stupidly simple, but it does bring it within range of the average person.

ufw is installed on your server by default, though it is turned off.  So there is no need to install it before use.  To find out the current status of ufw, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo ufw status
[/COLOR][/FONT][/B][/INDENT]
You should get back a result telling you that it is currently turned off:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Status: inactive
[/COLOR][/FONT][/B][/INDENT]
We will need to configure it, and turn it on.  Before we do, however, I want to warn you that if you make a mistake, you might lock yourself out of your server.  If this happens, don't panic.  You have only locked yourself out from remote access.  You can always work directly on the machine itself to take steps necessary to re-establish a connection.  That said, it is better to not lock yourself out, no?  So take some time to research ufw beyond what I am explaining here.

We are going to have an extremely restrictive set of rules.  I intend to specifically allow only those few things the server was built to do, and disallow everything else.  This only makes sense.  Why leave any ports or protocols open if you do not intend to use them?  So, to begin we will tell ufw to deny everything by default (i.e. block everything: both incoming and outcoming).
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo ufw default deny incoming
	sudo ufw default deny outgoing
[/COLOR][/FONT][/B][/INDENT]
Now, I am going to selectively allow those services that I want to have remote access for.

Start with ssh (remember you have it on a non-standard port):
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]sudo ufw allow in 22512/tcp[/COLOR][/FONT]**	<-- replace 22512 with the port number you selected for ssh
	**[FONT="Courier New"][COLOR="RoyalBlue"]sudo ufw allow out 22512/tcp[/COLOR][/FONT]**	<-- replace 22512 with the port number you selected for ssh
[/INDENT]
This tells ufw to allow anyone to connect to port 22512 (replace 22512 with the port you set up for ssh) using the tcp protocol.  Now remember that ssh is pretty locked down already, so allowing access to this port does not mean anyone can ssh into your computer.  It just means anyone has an opportunity to try to log in (but they would need to know the port number, have the key file, know your passphrase, and get all that within five tries before denyhosts kicks them out).  Also note that we have to specify a direction (in/out) otherwise only the incoming traffic will be allowed.

We also have to allow ping (or more specifically ICMP) to get through the firewall.  By default ufw blocks the ability of your server to run ping (or, again, ICMP upon which both ping and fping are built).  This is kind of esoteric, but important.  If you start up your firewall but have not allowed ICMP to function through it, your computer will put itself to sleep within five minutes or less (Why?  Remember the script we set up to check for active computers on the network?  Well, if ufw blocks ICMP and, by extension, fping, this script will think that there are no other machines on the network and then simply put itself to sleep.  Ask me how I know.)

So, to allow ICMP we have to edit the "before rules" of ufw.  This is different than the usual allow commands.  I think it has to do with the fact that ICMP seems to run at a lower level than TCP/IP.  In any event, I used this site as reference for the next section:

	[http://www.kelvinism.com/howtos/enable-icmp-through-ufw/](http://www.kelvinism.com/howtos/enable-icmp-through-ufw/)

We need to edit the "before rules" of ufw.  To do this, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo pico /etc/ufw/before.rules
[/COLOR][/FONT][/B][/INDENT]
Edit this file and add the following lines:
[INDENT][I][COLOR="Magenta"]
# allow outbound icmp
-A ufw-before-output -p icmp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
-A ufw-before-output -p icmp -m state --state ESTABLISHED,RELATED -j ACCEPT
[/COLOR][/I][/INDENT]
Save and close the file.

Once you have allowed ssh and outgoing ICMP, you can actually turn on ufw (had you turned it on prior to allowing ssh, you would have been booted off the system.  Had you turned it on before editing the before rules, your machine would have spontaneously gone to sleep within five minutes).  To turn on ufw, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo ufw enable
[/COLOR][/FONT][/B][/INDENT]

I am now going to open port 25 which is the port that most  smtp servers use to send emails, and port 53 which it needs to resolve dns requests (it uses dns to resolve smtp.whatever.com to an actual ip address).  In some cases, your email provider may use a different port than 25 (mine, for example, is 2525).  Just substitute this value for 25.  Also, note that we are only opening these ports in the out direction.
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo ufw allow out 25
	sudo ufw allow out 53
[/COLOR][/FONT][/B][/INDENT]

Next, I am going to allow certain ports to accept any connections from the local network.  Outside the local network, these services will not be accessible.  Note that I am using the address 172.16.1.0/24 to represent my local network.  This translates to an IP range of 172.16.1.0 through 172.16.1.254.  If your network uses a different set of IP addresses (The usual ones are: 192.168.1.0-254, 172.16.1.0-254, or 10.0.0.0-254) then substitute that.  For example, if your server's ip address is, say, 192.168.0.10 then you would want to use: 192.168.0.0/24

Start with allowing the dhcp client access.
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
sudo ufw allow in from 172.16.1.0/24 to any port 68
sudo ufw allow out from 172.16.1.0/24 to any port 68
[/COLOR][/FONT][/B][/INDENT]
Now, I am going to open the ports for Netatalk and Avahi (even though these have not yet been installed): 


Netatalk
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
sudo ufw allow in proto tcp from 172.16.1.0/24 to any port 548
sudo ufw allow out proto tcp from 172.16.1.0/24 to any port 548
sudo ufw allow in proto tcp from 172.16.1.0/24 to any port 427
sudo ufw allow out proto tcp from 172.16.1.0/24 to any port 427
sudo ufw allow in proto tcp from 172.16.1.0/24 to any port 4700
sudo ufw allow out proto tcp from 172.16.1.0/24 to any port 4700
sudo ufw allow in proto tcp from 127.0.0.1 to any port 4700
sudo ufw allow out proto tcp from 127.0.0.1 to any port 4700
[/COLOR][/FONT][/B][/INDENT]

Avahi
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
sudo ufw allow in proto udp from 172.16.1.0/24 to any port 5353
sudo ufw allow out proto udp from 172.16.1.0/24 to any port 5353
sudo ufw allow in proto udp from 172.16.1.0/24 to any port 56794
sudo ufw allow out proto udp from 172.16.1.0/24 to any port 56794
sudo ufw allow in proto udp from 172.16.1.0/24 to any port 42826
sudo ufw allow out proto udp from 172.16.1.0/24 to any port 42826
[/COLOR][/FONT][/B][/INDENT]

dhclient (needed for DHCP to work)
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
sudo ufw allow in from 172.16.1.0/24 to any port 67
sudo ufw allow out from 172.16.1.0/24 to any port 67
[/COLOR][/FONT][/B][/INDENT]

Finally, I am going to allow port 4040 which will be needed for our subsonic media server.  Again, it will only allowed from the local network.
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo ufw allow in proto tcp from 172.16.1.0/24 to any port 4040
[/COLOR][/FONT][/B][/INDENT]
Remember, by using the format from 172.16.1.0/24 we are limiting these ports to only accept connections from the local network.  Any attempts to connect from the wider world will be blocked.










[B][SIZE="4"][COLOR="RoyalBlue"]Section #18: Security: Install port knocking software
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.
- I referenced the following website for this section [https://help.ubuntu.com/community/PortKnocking](https://help.ubuntu.com/community/PortKnocking)



As you learned earlier, ports are like doors through which the server listens for requests and then allows authorized users through.  We have turned off most ports on our system except those that we specifically intend to use (particularly netatalk, avahi, and ssh for example).  That said, it would be even nicer if any of these ports that will eventually be open to the internet were turned off until a secret code was submitted that opened them up.  Currently, if you try to connect to our server on the port you set up for ssh (22512 in the example we have been using up till now) you will be challenged for your ssh private key.  Just this challenge would be enough for a malicious user to know that there was a locked door that they could focus their efforts against.

Port knocking is a mechanism where we actually camouflage the ports so that there is no response of any kind when you try to connect.  Instead, you need to "knock" on a pre-defined set of ports in a pre-defined order in a pre-defined amount of time before you can successfully try to connect to the port you want to connect to.  Once this secret pattern of knocks has been registered, the port you want to connect to is opened up and you may then try to connect to that port in the normal manner.  

For example, if you wanted to connect to ssh on port 22512, you would first "knock" on ports 1789, 20933, 12892, and 14999 in that order (this is just an example, you may set any pattern you wish) and do it within ten seconds (again, you may set any duration you want) before port 22512 is opened up.  At that point, you have a few moments to connect to this port.  Note that connecting still requires all of the ssh credentials you would have needed prior to installing the port knocking software.  The nice thing about this is that there is no easy way to determine that port knocking software is even running on your server.  If a malicious user knocks in the wrong order it will appear as though there are no open ports anywhere.  There is no "rejection" of the knocks.  Instead, nothing happens.  This is indistinguishable from a machine that actually doesn't have any open ports or is even physically not there.

We will be using the knockd tool to implement port knocking.  It isn't the most secure of the port knocking tools as it does not use encryption and some other more sophisticated techniques, but it is easy to set up and use.  Remember, we are not relying on port knocking for security, we are just adding a layer of camouflage to our system.  If someone sniffs out our port knocking sequence, they still need to get past our other security measures.  I think this compromise is sufficiently secure for the type of server we are protecting.

Port knocking does make it a bit more annoying to log in remotely, but the tradeoff appears to me to be worth it.  Again, we are talking about layered security here.




**_[SIZE="3"]Step 1: Install knockd on your server.[/SIZE]_**

To install port knocking software, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	 sudo apt-get install knockd
[/COLOR][/FONT][/B][/INDENT]
Once it is installed, edit the config file by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo nano /etc/knockd.conf
[/COLOR][/FONT][/B][/INDENT]
And modify it so that it reads as follows (of course, you will want to change the 7000,8000,9000 sequence to a custom, secret sequence of your own.  You don't have to limit yourself to just three ports, but I have not had any luck re-using ports so only use a port once.):

```
[options]
        logfile = /var/log/knockd.log

[openSSH]
        sequence      = 7000,8000,9000
        seq_timeout   = 30
        start_command = /usr/sbin/ufw allow proto tcp from %IP% to any port 22512
        tcpflags      = syn
        cmd_timeout   = 20
        stop_command  = /usr/sbin/ufw delete allow proto tcp from %IP% to any port 22512

```
Save and close the file.

Next, edit the start up file by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo nano /etc/default/knockd
[/COLOR][/FONT][/B][/INDENT]
Change the line that reads:
[INDENT][I][COLOR="Magenta"]
	START_KNOCKD=0
[/COLOR][/I][/INDENT]
to:
[INDENT][I][COLOR="Magenta"]
	START_KNOCKD=1
[/COLOR][/I][/INDENT]
And add the following line to the end of the file:
[INDENT][I][COLOR="Magenta"]
	KNOCKD_OPTS="--debug --verbose -i eth0"
[/COLOR][/I][/INDENT]
Save and close the file.




**_[SIZE="3"]Step 2: Tell ufw to deny the port we are using for ssh.[/SIZE]_**

Earlier we had set up ufw to allow ssh access via a non-standard port (22512).  But now that we have port knocking enabled, we have to make sure that any attempts to connect to our ssh port is denied by default (only after we have properly knocked will it be enabled).  

But before we close up this port, it will be handy to have some ssh shells open (they will not be terminated by changing the ufw rules, but any new attempts to connect will be blocked).

Once you have some extra shells connected to the server via ssh, delete the open port in ufw.  To do this, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo ufw delete allow in 22512/tcp
	sudo ufw delete allow out 22512/tcp
[/COLOR][/FONT][/B][/INDENT]
Of course, you will have to substitute the actual port number you set up for ssh.




**_[SIZE="3"]Step 3: Start knockd.[/SIZE]_**

Start knockd by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo service knockd restart 
[/COLOR][/FONT][/B][/INDENT]
you should be able to look at the log to see what it is doing.  To do so, type:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo cat /var/log/knockd.log
[/COLOR][/FONT][/B][/INDENT]
And it will tell you the status of the knockd process.  Of course, nothing is happening just yet because you still need to install a knocking client on your Mac.




**_[SIZE="3"]Step 4: Install the knocking software on your Mac.[/SIZE]_**

In order to get knockd to open up our ssh port, we will have to be able to send it a series of knock.  There are multiple ways of doing this (and I had considered writing a script that utilizes the nc command but had some difficulty with that) but the easiest way to go is to download a knocking client for your Mac.

On your Mac, go to the following website:

	[http://www.zeroflux.org/projects/knock](http://www.zeroflux.org/projects/knock)

and download the MacOS Client.  (Note, there are also clients for Windows and iOS)

Move the downloaded knock file (called knock) to your /usr/local/sbin directory.  (Note, if you can only find a file called knock-macos.tar it means you have not uncompressed it yet).  Move this file this by typing:

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo mv ~/Downloads/knock /usr/local/sbin/knock[/COLOR][/FONT]**

Make sure it is executable by typing:

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo chmod 777 /usr/local/sbin/knock[/COLOR][/FONT]** 

Now create a combined knock/ssh script so that you can connect to your server with a single command.  Create the script by typing:

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo nano /usr/local/sbin/ubs[/COLOR][/FONT]**

And copy or type the following into it:

```
#!/bin/bash

/usr/local/sbin/knock 172.16.1.100 7000
/usr/local/sbin/knock 172.16.1.100 8000
/usr/local/sbin/knock 172.16.1.100 9000
sleep 2
ssh -l admiral -p 22512 172.16.1.100

```
Note, you will have to customize the above script so that it: 

a) Uses your actual sequence of ports (not 7000 8000 9000) 
b) Uses your actual administrative user (not admiral) 
c) Uses your actual ssh port number (not 22512).

Also, normally you would simply have a single line which lists all of your ports in order, but I found that it would rarely work.  Instead I had a lot more luck by separating each knock out into a separate call to the knock script.

Save and close the file.

Make sure it is only accessible to the root user on your Mac because the proper sequence of ports is something like a combination… you want to keep it secret.  To do this, type:

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo chown root /usr/local/sbin/ubs[/COLOR][/FONT]**
**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo chmod go-rwx /usr/local/sbin/ubs[/COLOR][/FONT]**
**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo chmod u+rwx /usr/local/sbin/ubs[/COLOR][/FONT]**

Now test it to see if you can log into your server just by typing this one command (note: you have to have /usr/local/sbin in your PATH variable.  If it isn't look up on Google how to do that for the shell you are using - which is most likely bash.):

**[COLOR="Red"]Mac:[/COLOR]**		**[FONT="Courier New"][COLOR="RoyalBlue"]sudo ubs[/COLOR][/FONT]**

You will be prompted for your password and you may have to accept the server's RSA key fingerprint the first time.  

It works for me, but sometimes I need to run it more than once (that may simply be a case of some other process on the network hitting a port while the script is running and throwing off the sequence of knocks).







[B][SIZE="4"][COLOR="RoyalBlue"]Section #19 - Set up your users and the various directories on the RAID
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.



Now is the time to create all the regular users on the server.  These are the users who will be using the server to store files, back up their computers, stream music, etc.  You should include your regular login in this list.  You will also create directories where your data will be stored (all on the RAID array).




**_[SIZE="3"]Step 1: Create your first user.[/SIZE]_**

Creating a user is easy.  Assuming you want to add a user named 'bob' just type:
[INDENT]
	**[FONT="Courier New"][COLOR="RoyalBlue"]sudo adduser bob[/COLOR][/FONT]** <--- replace 'bob' with the name of the user you want to add
[/INDENT]
You will see the following:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Adding user `bob' ...
	Adding new group `bob' (1001) ...
	Adding new user `bob' (1001) with group `bob' ...
	Creating home directory `/home/bob' ...
	Copying files from `/etc/skel' ...
[/COLOR][/FONT][/B][/INDENT]
Then you will be prompted to enter a password for this user:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	New password:
[/COLOR][/FONT][/B][/INDENT]
Go ahead and assign a default password for the user (they can change it later).  Note, if you put in too basic a password you may get a warning that looks like:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	BAD PASSWORD: it is based on a dictionary word
[/COLOR][/FONT][/B][/INDENT]
Regardless, you will be asked to re-enter the password:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Retype new password:
[/COLOR][/FONT][/B][/INDENT]
Go ahead and re-enter the password.  You will be notified that the password was successfully set.
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	passwd: password updated successfully
[/COLOR][/FONT][/B][/INDENT]
After this, you will be guided through the process of entering some basic user information:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Changing the user information for bob
	Enter the new value, or press ENTER for the default[INDENT]
		Full Name []: Bob Smith
		Room Number []: 
		Work Phone []: 
		Home Phone []: 
		Other []: [/INDENT]
[/COLOR][/FONT][/B][/INDENT]
Just answer the questions.  Note that I elected to ignore some of the questions (Room Number for example) by just hitting enter when asked for information.  Finally you will be asked:
[INDENT][B][FONT="Courier New"][COLOR="SeaGreen"]
	Is the information correct? [Y/n] y
[/COLOR][/FONT][/B][/INDENT]
Assuming it is all correct, just hit:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	y 

[/COLOR][/FONT][/B][/INDENT]and press enter.

That's it.  You have just created a user named 'bob'




**_[SIZE="3"]Step 2: Lather, Rinse, Repeat.[/SIZE]_**

Repeat step 1 as many times as you have users that will be using the system.




**_[SIZE="3"]Step 3: Create the directory structure you want to use to organize data on your RAID array.[/SIZE]_**

I have my server set up in the following manner:

[INDENT]	1) A home directory on the RAID array for each user
	2) A media directory inside of which is my music, movies, etc...
	3) A shared directory called "Data" which is just open to anyone to store shared data
	4) A time machine directory for time machine backups
[/INDENT]
You, of course, may set your system up in any way you like.  To create these directories, do the following (substituting your own structure of course):

[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]sudo mkdir /mnt/nas/Users
sudo mkdir /mnt/nas/Users/george
sudo mkdir /mnt/nas/Users/ringo
sudo mkdir /mnt/nas/Users/paul
sudo mkdir /mnt/nas/users/yoko
sudo mkdir /mnt/nas/Data
sudo mkdir /mnt/nas/Media
sudo mkdir /mnt/nas/Media/Music
sudo mkdir /mnt/nas/Media/Movies
sudo mkdir /mnt/nas/TimeMachine[/COLOR][/FONT][/B][/INDENT]








[B][SIZE="4"][COLOR="RoyalBlue"]Section #20 - Set up Netatalk (open source Apple File Protocol) and Avahi (open source Bonjour implementation)
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]
Notes:

- Anything in **[FONT="Courier New"][COLOR="RoyalBlue"]bold blue monotype[/COLOR][/FONT]** is a command you type at the command prompt.  **[FONT="Courier New"][COLOR="SeaGreen"]bold green monotype[/COLOR][/FONT]** is used to show prompts from the computer.  *[COLOR="Magenta"]Pink italics[/COLOR]* are used to show either the contents of text files or miscellaneous prompts.
- The info in this section came from: [http://www.pronetworks.org/forums/configuring-ubuntu-to-store-time-machine-backups-t109371.html](http://www.pronetworks.org/forums/configuring-ubuntu-to-store-time-machine-backups-t109371.html)



This server will act as a file server and Time Machine backup drive for a group of Macs (and one Dell hackintosh). 

This will require that we install Netatalk (which supplies an open source implementation of the Apple File Protocol) and Avahi (which is an open source implementation of Bonjour).

Since I don't own any Windows machines, I am both unversed and uninterested in the details of making this server talk to them. That said, I am sure the process is equally simple. You should investigate Samba which is, as I understand it, an open source implementation of the Windows networking protocol.



**_[SIZE="3"]Step 1: Install Netatalk (open source implementation of Apple File Protocol).[/SIZE]_**

Netatalk is a service that will allow your Macs to talk natively to the server (vs. having to pretend they are Windows machines and communicate via Samba). [S]Ubuntu server 11.10 package repository contains a version of netatalk that is compatible with OSX Lion. Previous versions of Ubuntu do not (aka 11.04). 

Note: If you are following along with this tutorial but trying to install an older version of Ubuntu you might want to meander over to [http://andypeace.com/netatalk.html](http://andypeace.com/netatalk.html) where a very nice fellow by the name of Andy Peace has compiled a version of netatalk that might work for you (if you are installing a 64 bit system). You can download the file from the command line by using the wget command (wget [http://andypeace.com/netatalk_2.2.0-1_amd64.deb](http://andypeace.com/netatalk_2.2.0-1_amd64.deb)) and installing it using the dpkg command (sudo dpkg -i netatalk_2.2.0-1_amd64.deb)

Install netatalk by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get install netatalk
[/COLOR][/FONT][/B][/INDENT][/S]

**UPDATE 1/7/2012: The version of Netatalk currently available for install from the 11.10 repositories does not work with lion (may not work with previous versions of OSX either).  In order to install the latest version, do the following:**

I used this thread to help diagnose the issues:
[https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/810732]("https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/810732")

Start by setting up your server so that it can install packages outside of the official ones available for the 11.10 version of Ubuntu.  These outside packages are referred to as PPA's and are basically identical to a package you would install from the official repository, but are put together by members of the community and hosted elsewhere.  Of course you want to be careful not to install just any package from just any source, but as long as you are careful to use respected sources you should be fine.

To install the latest Netatalk ppa, we need to add the repository to our apt package management system sources list.  I used the following website as a reference as to how to accomplish this: [https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

Go ahead and read that previous link for a very good description of what we will be doing (as I am going to go light on the description here). Note: In theory you should be able to add a repository simply by issuing the [COLOR="Magenta"]add-apt-repository[/COLOR] command, but I was unable to get that to work (Perhaps I would have to install python software properties first, but the following method works and so I never bothered trying to go any further with this command).

Start by backing up your /etc/apt/source.list file and then editing it.  Do this by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
        sudo nano /etc/apt/sources.list
[/COLOR][/FONT][/B][/INDENT][/S]

Add the following line to the end of this file:
[INDENT][I][COLOR="Magenta"]
deb [http://ppa.launchpad.net/jstrunk-math/ppa/ubuntu/](http://ppa.launchpad.net/jstrunk-math/ppa/ubuntu/) oneiric main
deb-src [http://ppa.launchpad.net/jstrunk-math/ppa/ubuntu/](http://ppa.launchpad.net/jstrunk-math/ppa/ubuntu/) oneiric main
[/COLOR][/I][/INDENT]

Save and close the file.

Update your repositories list by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get update
[/COLOR][/FONT][/B][/INDENT]

Now you can install Netatalk by simply typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get install netatalk
[/COLOR][/FONT][/B][/INDENT]



**_[SIZE="3"]Step 2: Configure Netatalk.[/SIZE]_**

Now we need to configure Netatalk so that it will work with your OSX machines. 

Before we do, it might be useful to go into a little background on some of the terminology here as Netatalk is a fairly complicated beast. 

OSX uses the concept of file ID's to track files (vs. the actual name/path of the file). From the Netatalk documentation ([http://netatalk.sourceforge.net/2.2/htmldocs/configuration.html#id4164944):](http://netatalk.sourceforge.net/2.2/htmldocs/configuration.html#id4164944):)

*[COLOR="Magenta"]"Unlike other protocols like smb or nfs, the AFP protocol mostly refers to files and directories by ID and not by a path (the IDs are also called CNID, that means Catalog Node ID). A typical AFP request uses a directory ID and a filename, something like "server, please open the file named 'Test' in the directory with id 167". For example "Aliases" on the Mac basically work by ID (with a fallback to the absolute path in more recent AFP clients. But this applies only to Finder, not to applications)."[/COLOR]*

The thing you should take away from this is that Netatalk has to maintain a database of Catalog Node ID's for each file you are storing on the server. This database (and there are several options which kind to use but we will stick to the default of dbd) is responsible for tracking the CNID's for every file transaction that occurs. Having this database is required for our Netatalk installation to work. Incidentally, this database is also one reason why it is a bad idea to mess with the files being served by Netatalk outside of Netatalk. It becomes very easy for your CNID database to get out of sync with what is actually on disk. If you do find you need to manipulate these files from a command line on your server, use the ad tool that was installed along side Netatalk ([http://netatalk.sourceforge.net/2.2/htmldocs/ad.1.html](http://netatalk.sourceforge.net/2.2/htmldocs/ad.1.html)).  We will actually be creating a special login for doing exactly that in a moment.

Another thing to note is that the file protocol that we will be using is called AFP (Apple File Protocol). There is a rich history of different file services (serving files, print servers, time servers, etc.) that come with legacy Apple products (OS 9 and older primarily) and Netatalk seems capable of handling them all. But as we don't want any unnecessary complications, we will be disabling them all and limiting ourselves to just using AFP (via the afpd daemon).


-------------------------------------
Ok, now let's edit the Netatalk config file:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo nano /etc/default/netatalk
[/COLOR][/FONT][/B][/INDENT]
First, find the lines that start with:
[INDENT][I][COLOR="Magenta"]
	CNID_METAD_RUN
	AFPD_RUN
[/COLOR][/I][/INDENT]
And make sure they are both set to "yes". The first line turns on the default CNID database and has it run as a daemon. The second line turns on the Apple File Protocol and has it run as a daemon as well.


Next, find the lines that start with:

[INDENT][I][COLOR="Magenta"]	ATALKD_RUN
	PAPD_RUN
	TIMELORD_RUN
	A2BOOT_RUN
[/COLOR][/I][/INDENT]
And make sure they are all either set to "no" or commented out. These are all legacy protocols that we will not be using.

Save and close the file.


-------------------------------------
Next we want to configure the Apple File Protocol service (afpd). To do this we need to edit the afpd config file:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo nano /etc/netatalk/afpd.conf
[/COLOR][/FONT][/B][/INDENT]
And add the following line to the end of the file:

[S][INDENT][I][COLOR="Magenta"]	- -tcp -noddp -uamlist uams_dhx.so,uams_dhx2.so -nosavepassword
[/COLOR][/I][/INDENT][/S]

**UPDATE 1/7/2012: Apparently uams_dhx2.so does not play nice with OSX Lion, so we should update this line to use uams_dhx2_passwd.so**

[INDENT][I][COLOR="Magenta"]	- -tcp -noddp -uamlist uams_dhx.so,uams_dhx2_passwd.so -nosavepassword
[/COLOR][/I][/INDENT]

(Note that this lines starts with a dash, space, dash).  Save and close the file.

Here is a breakdown of the settings and what they mean:

*[COLOR="Magenta"]-tcp[/COLOR]* makes Netatalk run over the tcp protocol (vs. 
*[COLOR="Magenta"]-noddp[/COLOR]* disables AFP-over-Appletalk. Appletalk is a legacy protocol no longer needed for OSX clients so we turn it off.
*[COLOR="Magenta"]-uamlist[/COLOR]* provides a list of possible authentication methods (how the server authenticates the user). We are going to limit it to *[COLOR="Magenta"]uams_dhx.so[/COLOR]* and *[COLOR="Magenta"]uams_dhx2.so[/COLOR]* both of which are fairly modern and fairly secure.
-nosavepassword is fairly self explanatory. It will not store the user's password once authentication has been completed.

Note that all of the above settings are the default, so technically you could skip adding this line completely.


-------------------------------------
Finally, set up the shared volumes (the "drives" that your Mac will see when they log into the server).  In my case, I want one drive for each user (yoko, paul, ringo, and george), one drive for media, one drive for general data, and one drive to act as a time machine drive. In other words, the following remote drives will be visible by the Macs. They will look like separate drives even though they are merely separate directories on your RAID array (not all of these drives will actually be visible to each user though. I'll explain in a moment):

[INDENT][I][COLOR="Magenta"]	yoko
	paul
	ringo
	george
	Data
	Media
	TimeMachine[/COLOR][/I][/INDENT]


To set up these drives we will have to edit the the AppleVolumes.default file and add one line for each "drive" to the AppleVolumes.default file.

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo nano /etc/netatalk/AppleVolumes.default[/COLOR][/FONT]**[/INDENT]

Find the line that looks like:

[INDENT]*[COLOR="Magenta"]	~/				"Home Directory"[/COLOR]*[/INDENT]

And comment it out. We will not be allowing users to log into their Linux home directories on this server. Instead they will be using the specific directories we created per user on the RAID.

Next, add the following lines to the end (adjust change the usernames and paths to be appropriate, and add any additional directories as desired). We are explicitly defining which directories are allowed access by which users. The pattern is:

[INDENT]*[COLOR="Magenta"]	path to directory	name to display	list of allowed users		options[/COLOR]*[/INDENT]

To accomplish this, I have added the following lines:

[INDENT][I][COLOR="Magenta"]/mnt/nas/TimeMachine "TimeMachine" allow:geroge,ringo,paul,yoko cnidscheme:dbd options:tm
/mnt/nas/Data "Data" allow:geroge,ringo,paul,yoko cnidscheme:dbd
/mnt/nas/Media "Media" allow:geroge,ringo,paul,yoko cnidscheme:dbd
/mnt/nas/Users/george "george" allow:george cnidscheme:dbd
/mnt/nas/Users/ringo "ringo" allow:ringo cnidscheme:dbd
/mnt/nas/Users/paul "paul" allow[noparse]:p[/noparse]aul cnidscheme:dbd
/mnt/nas/Users/yoko "yoko" allow:yoko cnidscheme:dbd[/COLOR][/I][/INDENT]

Note the "allow" statements.  Any drive allowed for a user here will appear in the Finder on a Mac where that user is logged in.  Any drive that is not allowed for a user will not be visible.



**_[SIZE="3"]Step 3: Install Avahi (an open source Bonjour service).[/SIZE]_**

Install avahi by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo apt-get install avahi-daemon[/COLOR][/FONT]**[/INDENT]

Configure it by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo nano /etc/nsswitch.conf[/COLOR][/FONT]**[/INDENT]

Find the line that starts with *[COLOR="Magenta"]hosts[/COLOR]* and add

[INDENT]*[COLOR="Magenta"]	mdns[/COLOR]*[/INDENT]

to the end of the line,

Save and close the file.


Create a new file for Avahi so it knows what services to broadcast to the Macs. Do this by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo nano /etc/avahi/services/afpd.service[/COLOR][/FONT]**[/INDENT]

and paste in the following text

```
<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name replace-wildcards="yes">%h</name>
<service>
<type>_afpovertcp._tcp</type>
<port>548</port>
</service>
<service>
<type>_device-info._tcp</type>
<port>0</port>
<txt-record>model=Xserve</txt-record>
</service>
</service-group>
```

You may replace the text "Xserve" with any of the following to get a different icon:

[INDENT][I][COLOR="Magenta"]	&#9642;	iMac
	&#9642;	MacPro
	&#9642;	MacBook
	&#9642;	MacBookPro
	&#9642;	MacBookAir
	&#9642;	PowerBook
	&#9642;	PowerMac
	&#9642;	Macmini
	&#9642;	Xserve
	&#9642;	AirPort[/COLOR][/I][/INDENT]

Save and close the file and then restart avahi by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo service avahi-daemon restart[/COLOR][/FONT]**[/INDENT]




**_[SIZE="3"]Step 4: Set up a script to list, copy, move, and delete netatalk managed files from the command line.[/SIZE]_**

It is a bad idea to move files around from behind netatalk's back.  As mentioned before, netatalk maintains a database of file ID's that have to sync up with actual files on disk.  This CNID database can easily get out of sync if you use either an ssh session or the console to move files that netatalk is managing.  This is because netatalk will not be aware of the changes.  The best idea is to use either the Finder on your mac or the Terminal on your mac (not via ssh) to manipulate files.  However, there may be times when we want to use ssh or the console to manage our files.  In these cases we will need to use tools other than ls, cp, mv, and rm.  Instead we will use a netatalk supplied tool called "ad" which allows us to do many of the same file manipulations, but in a manner that keeps netatalk in the loop.

That said, it can be very easy to forget to use the correct tool at the correct time.  To solve that, we are going to write a small script that checks to see whether we are in a netatalk managed directory.  If we are, it will automatically use the ad tool to perform our requested operation.  If not, it will fall back to the standard shell commands.  It isn't a fool proof system, but it should cover nearly all of the situations we find ourselves in.

Again, please note that these tools are only necessary should you want to move files around when logged into the server via ssh or directly from the console.  If you are logged in from the Finder you may use the terminal (not via ssh) to move files around since all of those actions are being filtered through netatalk already.

Next, we will have to "wrap" the normal shell commands ls, mv, cp, and rm with our custom scripts to accomplish this.  Let's start with 'ls'.  




**_[SIZE="3"]Wrap 'ls'[/SIZE]_**

To create a new 'ls' command, type:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo nano /usr/local/sbin/lstemp[/COLOR][/FONT]**[/INDENT]

and copy or enter the following:

```
#!/bin/bash

WDIR=`pwd`

#if the .AppleDouble directory is present, it is save to assume it is a netatalk managed dir
if [ -d "$WDIR/.AppleDouble" ]; then

        newargs=""
        #check for valid args, discarding any that are not supported
        for arg in $@; do
                if [[ $arg != --* ]]; then
                        if [[ $arg == -* ]]; then
                                if [[ $arg == *l* ]]; then
                                        newargs="$newargs -l"
                                fi
                                if [[ $arg == *d* ]]; then
                                        newargs="$newargs -d"
                                fi
                                if [[ $arg == *R* ]]; then
                                        newargs="$newargs -R"
                                fi
                                if [[ $arg == *u* ]]; then
                                        newargs="$newargs -u"
                                fi
                        fi
                fi
        done

        #add any non-optional arguments (anything that does not start with a - )
        for arg in $@; do
                if [[ $arg != -* ]]; then
                        newargs="$newargs $arg"
                fi
        done

        #let the user know they are using a non-standard version of ls
        echo -e "\e[00;41mMAC MODE\e[00m"

        #execute it
        /usr/bin/ad ls $newargs 1>&1

        #let them know again that they are using a non-standard version of ls
        echo -e "\e[00;41mMAC MODE\e[00m"

else

        #just run ls in the normal manner
        /bin/ls $@ 1>&1

fi

```
Save and close the file.

Make it executable by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo chmod 777 /usr/local/sbin/lstemp[/COLOR][/FONT]**[/INDENT]

Test the script by changing directories to different locations on your server.  For example, type:

[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]	cd /usr/local/sbin
	lstemp -l[/COLOR][/FONT][/B][/INDENT]

You should get a regular listing of the contents of that directory.  

Next, switch to a directory being managed by netatalk.

[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]	cd /mnt/nas/
	lstemp -l[/COLOR][/FONT][/B][/INDENT]

You should get a slightly different output, one that is identified with red banners indicating that you are in the MAC MODE.

If this all works, rename your script to *[COLOR="Magenta"]ls[/COLOR]*.  This way, whenever you are in a directory being managed by netatalk, you will use the ad tools, and whenever you are in a normal directory you will use the standard Linux *[COLOR="Magenta"]ls[/COLOR]* tool.

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	mv /usr/local/sbin/lstemp /usr/local/sbin/ls[/COLOR][/FONT]**[/INDENT]

Note, you can always use the original ls command at any time (even if you are in a netatalk managed directory) by typing: 
	
[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	/bin/ls[/COLOR][/FONT]**[/INDENT]




**_[SIZE="3"]Wrap 'cp'[/SIZE]_**

Next, we will want to wrap the *[COLOR="Magenta"]cp[/COLOR]* command.  To create a new *[COLOR="Magenta"]cp[/COLOR]* command, type:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo nano /usr/local/sbin/cptemp[/COLOR][/FONT]**[/INDENT]

and copy or enter the following:

```
#!/bin/bash

WDIR=`pwd`

#if the .AppleDouble directory is present, it is save to assume it is a netatalk managed dir
if [ -d "$WDIR/.AppleDouble" ]; then

        newargs=""
        #check for valid args, discarding any that are not supported
        for arg in $@; do
                if [[ $arg != --* ]]; then
                        if [[ $arg == -* ]]; then
                                if [[ $arg == *a* ]]; then
                                        newargs="$newargs -a"
                                fi
                                if [[ $arg == *f* ]]; then
                                        newargs="$newargs -f"
                                fi
                                if [[ $arg == *i* ]]; then
                                        newargs="$newargs -i"
                                fi
                                if [[ $arg == *n* ]]; then
                                        newargs="$newargs -n"
                                fi
                                if [[ $arg == *p* ]]; then
                                        newargs="$newargs -p"
                                fi
                                if [[ $arg == *R* ]]; then
                                        newargs="$newargs -R"
                                fi
                                if [[ $arg == *v* ]]; then
                                        newargs="$newargs -v"
                                fi
                                if [[ $arg == *x* ]]; then
                                        newargs="$newargs -x"
                                fi
                        fi
                fi
        done

        #add any non-optional arguments (anything that does not start with a - )
        for arg in $@; do
                if [[ $arg != -* ]]; then
                        newargs="$newargs $arg"
                fi
        done

        #let the user know they are using a non-standard version of ls
        echo -e "\e[00;41mCOPYING IN MAC MODE\e[00m"

        #execute it
        /usr/bin/ad cp $newargs 1>&1

else

        #just run ls in the normal manner
        /bin/cp $@ 1>&1
fi

```
Save and close the file.

Make it executable by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo chmod 777 /usr/local/sbin/cptemp[/COLOR][/FONT]**[/INDENT]

Test the script by changing directories to different locations on your server.  For example, type:

[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]	cd /usr/local/sbin
	sudo cptemp cptemp deleteme[/COLOR][/FONT][/B][/INDENT]

If you now do a listing of this directory, you should see that you have successfully copied the *[COLOR="Magenta"]cptemp[/COLOR]* file into a file called *[COLOR="Magenta"]deleteme[/COLOR]*.  Don't delete this file just yet as it will prove to be a good test subject for our next script.

Next, switch to a directory being managed by netatalk (You may have to use your finder to drag a couple of files into this directory so that you have files to try copying).  Use cptest to copy a file here as well (name the destination something like deleteme).  You should be notified that you are doing a Mac Mode copy.  Check to see that the file does indeed exist by using the *[COLOR="Magenta"]ls[/COLOR]* command (note that it should be using the Mac Mode automatically as well).  Again, do not delete this file just yet as it will be useful for our next script.

If this all works, rename your script to *[COLOR="Magenta"]cp[/COLOR]*.  This way, whenever you are in a directory being managed by netatalk, you will use the *[COLOR="Magenta"]ad[/COLOR]* tools, and whenever you are in a normal directory you will use the standard Linux *[COLOR="Magenta"]cp[/COLOR]* tool.

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	mv /usr/local/sbin/cptemp /usr/local/sbin/cp[/COLOR][/FONT]**[/INDENT]

Note, you can always use the original cp command at any time (even if you are in a netatalk managed directory) by typing: 
	
[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	/bin/cp[/COLOR][/FONT]**[/INDENT]




**_[SIZE="3"]Wrap 'rm'[/SIZE]_**

Next, we will want to wrap the *[COLOR="Magenta"]rm[/COLOR]* command.  To create a new *[COLOR="Magenta"]rm[/COLOR]* command, type:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo nano /usr/local/sbin/rmtemp[/COLOR][/FONT]**[/INDENT]

and copy or enter the following:

```
#!/bin/bash

WDIR=`pwd`

#if the .AppleDouble directory is present, it is save to assume it is a netatalk managed dir
if [ -d "$WDIR/.AppleDouble" ]; then

        newargs=""
        #check for valid args, discarding any that are not supported
        for arg in $@; do
                if [[ $arg != --* ]]; then
                        if [[ $arg == -* ]]; then
                                if [[ $arg == *R* ]]; then
                                        newargs="$newargs -R"
                                fi
                                if [[ $arg == *v* ]]; then
                                        newargs="$newargs -v"
                                fi
                        fi
                fi
        done

        #add any non-optional arguments (anything that does not start with a - )
        for arg in $@; do
                if [[ $arg != -* ]]; then
                        newargs="$newargs $arg"
                fi
        done

        #let the user know they are using a non-standard version of ls
        echo -e "\e[00;41mDELETING IN MAC MODE\e[00m"

        #execute it
        /usr/bin/ad rm $newargs 1>&1

else

        #just run ls in the normal manner
        /bin/rm $@ 1>&1

fi

```
Save and close the file.

Make it executable by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo chmod 777 /usr/local/sbin/rmtemp[/COLOR][/FONT]**[/INDENT]

Test the script by returning to the directories where you had copied files in the previous example:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	cd /usr/local/sbin[/COLOR][/FONT]**[/INDENT]

and delete the *[COLOR="Magenta"]deleteme[/COLOR]* file you had created earlier by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo rmtemp deleteme[/COLOR][/FONT]**[/INDENT]

If you now do a listing of this directory, you should see that you have successfully deleted the file called *[COLOR="Magenta"]deleteme[/COLOR]*.

Next, switch to the same directory you had used to test netatalk copying before.  (This was the directory where you most likely had to copy some files into via the finder so that you could test the cp command).  You should have an extra file in here called something similar to *[COLOR="Magenta"]deleteme[/COLOR]*.  Use *[COLOR="Magenta"]rmtest[/COLOR]* to delete this file.  It should be successfully deleted, and you should have been notified that you were deleting in Mac Mode.

If this all works, rename your script to *[COLOR="Magenta"]rm[/COLOR]*.  This way, whenever you are in a directory being managed by netatalk, you will use the *[COLOR="Magenta"]ad[/COLOR]* tools, and whenever you are in a normal directory you will use the standard Linux *[COLOR="Magenta"]rm[/COLOR]* tool.

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	mv /usr/local/sbin/rmtemp /usr/local/sbin/rm[/COLOR][/FONT]**[/INDENT]

Note, you can always use the original rm command at any time (even if you are in a netatalk managed directory) by typing: 
	
[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	/bin/rm[/COLOR][/FONT]**[/INDENT]




**_[SIZE="3"]Wrap 'mv'[/SIZE]_**

Finally, we will want to wrap the *[COLOR="Magenta"]mv[/COLOR]* command.  To create a new *[COLOR="Magenta"]mv[/COLOR]* command, type:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo nano /usr/local/sbin/mvtemp[/COLOR][/FONT]**[/INDENT]

and copy or enter the following:

```
#!/bin/bash

WDIR=`pwd`

#if the .AppleDouble directory is present, it is save to assume it is a netatalk managed dir
if [ -d "$WDIR/.AppleDouble" ]; then

        newargs=""
        #check for valid args, discarding any that are not supported
        for arg in $@; do
                if [[ $arg != --* ]]; then
                        if [[ $arg == -* ]]; then
                                if [[ $arg == *f* ]]; then
                                        newargs="$newargs -f"
                                fi
                                if [[ $arg == *i* ]]; then
                                        newargs="$newargs -i"
                                fi
                                if [[ $arg == *n* ]]; then
                                        newargs="$newargs -n"
                                fi
                                if [[ $arg == *v* ]]; then
                                        newargs="$newargs -v"
                                fi
                        fi
                fi
        done

        #add any non-optional arguments (anything that does not start with a - )
        for arg in $@; do
                if [[ $arg != -* ]]; then
                        newargs="$newargs $arg"
                fi
        done

        #let the user know they are using a non-standard version of ls
        echo -e "\e[00;41mMOVING IN MAC MODE\e[00m"

        #execute it
        /usr/bin/ad mv $newargs 1>&1

else

        #just run ls in the normal manner
        /bin/mv $@ 1>&1

fi

```
Save and close the file.

Make it executable by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo chmod 777 /usr/local/sbin/mvtemp[/COLOR][/FONT]**[/INDENT]

Test the script by typing the following:

[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]	cd /usr/local/sbin
	sudo cp ls renameme[/COLOR][/FONT][/B][/INDENT]

If you now do a listing of this directory, you should see that you have successfully copied the file called *[COLOR="Magenta"]ls[/COLOR]* into a file called *[COLOR="Magenta"]renameme[/COLOR]*.   This isn't new, you have already done this exact same experiment above.  But now we will rename this file.  Type:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo mvtemp renameme deleteme[/COLOR][/FONT]**[/INDENT]

If you list the files in this directory, you should now see that the file *[COLOR="Magenta"]renameme[/COLOR]* has been renamed to *[COLOR="Magenta"]deleteme[/COLOR]*.  You should have been notified that you are listing in Mac Mode.  Go ahead and delete this file by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo rm deleteme[/COLOR][/FONT]**[/INDENT]

You should have been notified that you were deleting in Mac Mode.

Next, switch to the same directory you had used to test netatalk copying before.  (This was the directory where you most likely had to copy some files into via the finder so that you could test the cp command).  Go ahead and copy a file here as well.  Name the file you are copying *[COLOR="Magenta"]renameme[/COLOR]*.  You should have been notified that you were copying in Mac Mode.  Now move this file by using the **[FONT="Courier New"][COLOR="RoyalBlue"]mvtest[/COLOR][/FONT]** tool (move it to a file called *[COLOR="Magenta"]deleteme[/COLOR]*).  If you list the contents of the directory you should see that the file has been renamed from *[COLOR="Magenta"]renameme[/COLOR]* to *[COLOR="Magenta"]deleteme[/COLOR]*.  Go ahead and delete this new file using the *[COLOR="Magenta"]rm[/COLOR]* tool (again, you should be notified that you are deleting in Mac Mode).

If this all works, rename your script to *[COLOR="Magenta"]mv[/COLOR]*.  This way, whenever you are in a directory being managed by netatalk, you will use the *[COLOR="Magenta"]ad[/COLOR]* tools, and whenever you are in a normal directory you will use the standard Linux *[COLOR="Magenta"]mv[/COLOR]* tool.

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	mv /usr/local/sbin/mvtemp /usr/local/sbin/mv[/COLOR][/FONT]**[/INDENT]

Note, you can always use the original mv command at any time (even if you are in a netatalk managed directory) by typing: 
	
[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	/bin/mv[/COLOR][/FONT]**[/INDENT]


**UPDATE 1/7/2012: To better make sure we know when we are in a Netatalk managed directory or not, we will also update the prompt on our bash shell.**

To create a custom prompt for our bash shell, edit your .bashrc file (this is a script that is automatically run every time you create a new shell - either via ssh or the console.  So we put commands in here that we want to run every time we create a new shell).

To edit this file, type the following:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]	
nano ~/.bashrc
[/COLOR][/FONT][/B][/INDENT]

Once the file is open, add the following line to the end of it:

```
PS1='$(if [ -d "`pwd`/.AppleDouble" ]; then  echo "\e[00;41mMAC MODE\e[00m \033[01;32m\][\w]\033[00m\]: "; else echo "\033[01;32m\][\w]\033[00m\]: "; fi)'
```

Save and close the file.

Now, whenever you create a new shell, your prompt will intelligently change depending on which directory you are currently in (Showing the text "MAC MODE" in red whenever you are in a Netatalk managed directory).




[B][SIZE="4"][COLOR="RoyalBlue"]Section #21 - Set up time machine on your Mac
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]

There really isn't too much to this step.  On your Mac, turn on time-machine.  When it lists the possible drives you could use, select the one on your Ubuntu server.  Done.






[B][SIZE="4"][COLOR="RoyalBlue"]Section #22 - Install Subsonic - a web-based media server
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]

iTunes sucks hard (and this is coming from a total Mac-head).  That said, if you must use it you can serve music to iTunes devices by installing a daap server called forked-daapd.  On the plus side, it will act as though it were another iTunes machine on your network, sharing all of its music, including serving up DRM protected tracks that you may have purchased from the iTunes store when you were younger and much dumber (too dumb to realize that buying DRM encumbered music is completely nuts).  On the minus side, it will act as though it were another iTunes machine on your network, sharing all of its music.  This means you cannot use cover flow.  You cannot make playlists.  You cannot see your music in any format other than a giant list of every track on the server.  You cannot rate the music. 

So feel free to install forked-daapd if you want to use iTunes (I used it for a while back when I had FreeNAS installed, and I still have it installed on this Ubuntu server) but I am not going to bother walking you through it.  It is fairly self explanatory and I am not interested in using it myself.  That said, I do not wish to disparage forked-daapd itself.  It is an excellent package that does exactly what it is supposed to do.  It is just iTunes that sucks eggs.

Instead, I am going to suggest you install Subsonic ([http://subsonic.org/pages/index.jsp](http://subsonic.org/pages/index.jsp)) which is a Java based music server that will allow you to stream music to any machine in the house and to any device out on the internet.  The pluses are that you have much better control over your music from wherever you may be listening to it.  It is web-based so that you really only need a browser to connect (though we will not actually be using it that way).  It is much more flexible and much easier to use than iTunes.  The minuses are that you have to install Java on your server, you have to have a web server operating (though it is built into Subsonic and isn't a separate web server like Apache) which has unknown ramifications for security and, finally, the client side web view of your music is so ugly it will want to make you scratch your eyes out.  We are talking Android ugly here (and I am a HUGE Android fan by the way, but both it and Subsonic got hit with the ugly stick… hard).

Finally, Subsonic is somewhere between shareware and donationware.  You are free to use it on a fairly basic level without paying anything.  If you feel it is worth something (and I do) you are encouraged to kick a tiny amount of money back to the developer.  If you want to use any of the more advanced features, you are required to make a donation, but the amount is still flexible and up to you.  I personally have donated some money (more than the minimum amount) because I truly appreciate the effort that went into making a tool that blows iTunes out of the water.  Also, maybe if enough people donate the developer can hire a designer and make all of our lives better.  (I'm teasing!)

There may be more than one way to install Subsonic.  I noticed that you can simply type:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo apt-get install subsonic[/COLOR][/FONT]**[/INDENT]

And perhaps this will work.  I have no idea.  The actual subsonic website has different instructions for installation and that is what I followed.  Since then I have run the above command and all it does is tell me that my Subsonic package is up to date.  Feel free to try this first method though.  It may be all you need.

Otherwise, to install Subsonic from the instructions on the website (do the following.  First install Java by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo apt-get install openjdk-6-jre[/COLOR][/FONT]**[/INDENT]

This may take a while to install.

Next, we want to download the latest version of Subsonic to our home directory.  To do this we will use the wget command.  wget very simply will download any file you point it to on the internet.  In our case, we will want to go to Subsonic's download site (which is on SourceForge).  To begin, on our Mac, go to the following URL:

	[http://sourceforge.net/projects/subsonic/files/subsonic/](http://sourceforge.net/projects/subsonic/files/subsonic/)

There we will see a list of different versions.  Click on the latest version number that isn't a beta (4.6 in my case).  You will then be given a list of files that could be downloaded.  Don't click on any of them!  Instead, right click on the one that ends in .deb (a Debian package.  The Ubuntu software center and apt-get are based on Debian).  Copy the URL.

Now, in your ssh session type the following:

[INDENT]	[B][FONT="Courier New"][COLOR="RoyalBlue"]cd ~
	wget[/COLOR][/FONT][/B] <paste the URL here>[/INDENT]

You should get a notification that you are downloading the .deb package.

Once it has downloaded, we need to actually install it.  Do this by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo dpkg -i subsonic-4.6.deb[/COLOR][/FONT]**[/INDENT]

It will now install the Subsonic server for you.





By default, Subsonic runs Java as root.  This seems like it is a very bad idea and, luckily, it is changeable.  I used the following website to help me through this:  [http://forum.subsonic.org/forum/viewtopic.php?f=6&t=6146](http://forum.subsonic.org/forum/viewtopic.php?f=6&t=6146)

achoo5000's description is so good that I am simply going to copy the first bit verbatim with just a few tiny edits to make it fit in here (hope he or she does not mind).  I am going to deviate a bit when it comes to the last few steps.


------------ 

First step is to install everything as normal using the .deb package. 

Now make another user (called subsonic in this case): 

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo useradd subsonic[/COLOR][/FONT]**[/INDENT]

We now have to give this user ownership of all the subsonic data:

[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]	cd /var/subsonic/
	sudo chown -R subsonic:subsonic .[/COLOR][/FONT][/B][/INDENT]

I had a problem where mine would crash when trying to write to /tmp because there was already data there, you could just change the permissions as above, but I just deleted it.

[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]	cd /tmp
	sudo rm -rf subsonic/[/COLOR][/FONT][/B][/INDENT]

------------

From here I am deviating a bit from achoo's instructions (it may just be a case where I have a newer install of Subsonic which does things in a different way)


Edit the Subsonic startup script. To do this, type:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo nano /etc/default/subsonic[/COLOR][/FONT]**[/INDENT]

Near the end of the file, change the line that reads:

[INDENT]*[COLOR="Magenta"]	SUBSONIC_USER=root[/COLOR]*[/INDENT]

to

[INDENT]*[COLOR="Magenta"]	SUBSONIC_USER=subsonic[/COLOR]*[/INDENT]

Save and close the file.


Restart Subsonic by typing:

[INDENT]**[FONT="Courier New"][COLOR="RoyalBlue"]	sudo service subsonic restart[/COLOR][/FONT]**[/INDENT]





To listen to music on your Mac, point your browser to:

	[noparse]http://172.16.1.120:4040[/noparse]

(of course, you should substitute your server's actual IP address for 172.16.1.120)

You should be asked to log into Subsonic.  Go ahead and log in as instructed (you will be guided through the first time).  Make a new user in the Subsonic UI.  You can name this user anything you want.  I simply chose "music" because I want both my fiancee and myself to be able to log in as the same user and manage and share the same playlists.  But do whatever makes you happy.

With regard to the nasty UI.  I downloaded Submariner from the Apple Mac App Store.  It is a desktop client for the Submariner server and looks a lot better (plus you don't have to have a browser running).  There are other desktop clients as well.  At this point, just use whatever you like.







[B][SIZE="4"][COLOR="RoyalBlue"]Section #23 - Make your server visible to the outside world
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]

Generally, you want to keep your server locked up tight and hidden behind your router.  But if you want to connect to it from outside your local network, you will have to open up your router a bit and forward ports to the server.  I may go into more detail about this process in the future, but it has to be pretty generalized simply because the actual process varies from router to router.  The basic idea is that any ports you want externally accessible will need to be forwarded from the router to your server.

Here is a list of all the ports I think you will want to forward:

[INDENT]	ssh (in our example: 22512)
	Subsonic (port 4040) 
	All of the "knocking" ports (7000, 8000, 9000 in our example)[/INDENT]

Some things to consider:  If possible, forward a non-standard port to port 4040.  In other words, have port 2101 (for example) forwarded to port 4040 on the server.  This way you will connect to Subsonic on port 2101 (a non-standard port) when you are on an external network trying to listen to your music.

You will also need some way of knowing the IP address of your router when you are out and about.  There are services that allow you to set that up, but I intend to do it a bit differently.  Again, a bit of added security by obscurity.  But I do not have time to do that just now.  For the time being, you can sign up for a service like [http://www.no-ip.com/](http://www.no-ip.com/).  Note: I have never used this service and I have no idea if they are any good, if there are better services out there, or anything.  Again, I intend to roll my own but do not have time to do that just yet.








[B][SIZE="4"][COLOR="RoyalBlue"]Section #24 - Back your server up to a duplicate machine across the country
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]

Well, this part is simply going to have to wait.  I do not have the money to build a second machine right now.  When I do, I will post back here (editing this post actually).

If you want to take a stab at it, I expect I will be using the rsync utility (or Duplicity which builds on top of rsync).  I will also have to have a means by which each server will know the IP address of the other (these will change over time and cannot be predicted).  There are services which will translate a domain to a dynamic IP address and I may use one of those.  Alternatively, I may simply have each server periodically check its external IP address and post it somewhere public in an obfuscated format (like to dropbox or to my hosted web server).  I don't know.

But do know this:  [COLOR="Red"][B]RAID does not equal BACKED UP!
[/B][/COLOR]
Just because you have your data on a RAID set does not mean you have it backed up.  First off, what happens if you accidentally issue a command to delete a file?  Or a directory?  What if your server gets compromised or you drunkenly issue the wrong command and wipe out the entire file system?  What if there is a fire, or your house gets broken into?  RAID only protects you against disk failure (and RAID 5 only protects against a single disk failing.  If two fail, you are in trouble).

**[COLOR="Red"]YOU MUST BACK UP YOUR DATA SO THAT IT EXISTS IN MORE THAN ONE LOCATION.  PREFERABLY NOT IN THE SAME BUILDING.[/COLOR]**

Seriously.  Do it.  It is a little like my beautiful iMac.  I had thought about installing theft tracking software like prey ([http://preyproject.com/](http://preyproject.com/)) but always figured I had time to do it.  Then one day I came home to find stuff all over the floor and my 2 month old 27" iMac missing (the kensington lock didn't do squat).  All of a sudden it was too late.  Luckily I had backed my system up, but it was too late to do anything else.

Backups are like that.  You don't really see the need for them until suddenly you do and then you will really be sorry.  Back your data up now!  (I am currently doing that by copying the data from the server to my new iMac but I will come up with a better solution soon).  When I get it figured out, I will post here again.








[B][SIZE="4"][COLOR="RoyalBlue"]Section #25 - That's it!  Hope it was helpful
----------------------------------------------------------------
----------------------------------------------------------------[/COLOR][/SIZE][/B]

Let me know if you have any questions, comments, corrections, or suggestions.  I will attempt to adjust the posts here to reflect them.

Also, I would be very interested in any feedback including typos and formatting issues.  I want to have a quality product here :)

Finally, good luck!  I really hope it helps some folks and I really hope it helps us newbies learn a thing or two about the wonderful world of Linux server administration.  Once you have set up your own server, not only do you have total control over your own data, you can really start to understand what kinds of services you need and don't need - even if you eventually decide to switch away to a packaged NAS or even a cloud based system.

---

### Post by jdawgvh on 2011-12-31
great tutorial.  thank you!  I haven't made it all the way through it yet but I am setting up Ubuntu server w/ a Ubuntu client.  The only addition I've seen so far from your set up with the Mac is that for the Ubuntu client I had to issue the 'ssh-add' command to allow my private/public key pair to work properly.

---

### Post by bvz on 2011-12-31
> **jdawgvh said:**
> great tutorial.  thank you!  I haven't made it all the way through it yet but I am setting up Ubuntu server w/ a Ubuntu client.  The only addition I've seen so far from your set up with the Mac is that for the Ubuntu client I had to issue the 'ssh-add' command to allow my private/public key pair to work properly.

Glad the tutorial is of some help to you.

Just a clarification:  Did you have to issue the ssh-add command on your Ubuntu client or on the server?

---

### Post by jdawgvh on 2011-12-31
On my client I ran these steps:

ssh-keygen
scp -P 22512 ~/.ssh/id_rsa.pub [email]admiral@172.16.1.16:.ssh[/email]/authorized_keys2 (replacing your information for mine)
ssh-add
ssh -p 22512 -l admiral 172.16.1.16

---

### Post by AndesHelp on 2012-01-04
If this was a quick set-up guide for a simple file server set-up, I would hate to see the advanced version.  80% of this had nothing to do with setting up a small plain file server.

---

### Post by bvz on 2012-01-04
> **AndesHelp said:**
> If this was a quick set-up guide for a simple file server set-up, I would hate to see the advanced version.  80% of this had nothing to do with setting up a small plain file server.

Hey, I'm totally open to any criticisms, but they would have to be a bit more specific (and, given the amount of time I put into writing this, a bit higher quality than an unsubstantiated dismissal). 

Instead of taking the time to write something but then skimping out on offering anything constructive, why don't you help out by telling me what specifically would you cut from this tutorial (given that it is aimed at people new to setting up a server).

Edit:
Also, I am not sure where you got the idea that this was supposed to be a "quick set-up guide".

---

### Post by bvz on 2012-01-07
So I updated the original post to make the following changes (and I am including these as a separate post here for quick reference):



**[SIZE="3"]UFW[/SIZE]**
I added the following rules in UFW to make sure DHCP works:
[COLOR="DarkOrange"]----------------------------------------------------------------------------------------------------------------------------[/COLOR]

[INDENT][COLOR="RoyalBlue"][FONT="Courier New"]sudo ufw allow in from 172.16.1.0/24 to any port 67
sudo ufw allow out from 172.16.1.0/24 to any port 67[/FONT][/COLOR][/INDENT]




**[SIZE="3"]Section 20, Step 1: Install Netatalk[/SIZE]**
I Changed the way Netatalk is installed because the default version in oneiric does not play nicely with OSX Lion.
[COLOR="DarkOrange"]----------------------------------------------------------------------------------------------------------------------------[/COLOR]

The version of Netatalk currently available for install from the 11.10 repositories does not work with lion (may not work with previous versions of OSX either).  In order to install the latest version, do the following:

I used this thread to help diagnose the issues:
[https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/810732]("https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/810732")

Start by setting up your server so that it can install packages outside of the official ones available for the 11.10 version of Ubuntu.  These outside packages are referred to as PPA's and are basically identical to a package you would install from the official repository, but are put together by members of the community and hosted elsewhere.  Of course you want to be careful not to install just any package from just any source, but as long as you are careful to use respected sources you should be fine.

To install the latest Netatalk ppa, we need to add the repository to our apt package management system sources list.  I used the following website as a reference as to how to accomplish this: [https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

Go ahead and read that previous link for a very good description of what we will be doing (as I am going to go light on the description here). Note: In theory you should be able to add a repository simply by issuing the [COLOR="Magenta"]add-apt-repository[/COLOR] command, but I was unable to get that to work (Perhaps I would have to install python software properties first, but the following method works and so I never bothered trying to go any further with this command).

Start by backing up your /etc/apt/source.list file and then editing it.  Do this by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
        sudo nano /etc/apt/sources.list
[/COLOR][/FONT][/B][/INDENT]

Add the following line to the end of this file:
[INDENT][I][COLOR="Magenta"]
deb [http://ppa.launchpad.net/jstrunk-math/ppa/ubuntu/](http://ppa.launchpad.net/jstrunk-math/ppa/ubuntu/) oneiric main
deb-src [http://ppa.launchpad.net/jstrunk-math/ppa/ubuntu/](http://ppa.launchpad.net/jstrunk-math/ppa/ubuntu/) oneiric main
[/COLOR][/I][/INDENT]

Save and close the file.

Update your repositories list by typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get update
[/COLOR][/FONT][/B][/INDENT]

Now you can install Netatalk by simply typing:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]
	sudo apt-get install netatalk
[/COLOR][/FONT][/B][/INDENT]



**[SIZE="3"]Section 20, Step 4: Configure bash prompt for better interaction with Netatalk[/SIZE]**
Finally, I added a custom prompt to my .bashrc file to better inform me when I was in a netatalk managed directory when using ssh or the console.  
[COLOR="DarkOrange"]----------------------------------------------------------------------------------------------------------------------------[/COLOR]

To better make sure we know when we are in a Netatalk managed directory or not, we will also update the prompt on our bash shell.

To create a custom prompt for our bash shell, edit your .bashrc file (this is a script that is automatically run every time you create a new shell - either via ssh or the console.  So we put commands in here that we want to run every time we create a new shell).

To edit this file, type the following:
[INDENT][B][FONT="Courier New"][COLOR="RoyalBlue"]	
nano ~/.bashrc
[/COLOR][/FONT][/B][/INDENT]

Once the file is open, add the following line to the end of it:

```
PS1='$(if [ -d "`pwd`/.AppleDouble" ]; then  echo "\e[00;41mMAC MODE\e[00m \033[01;32m\][\w]\033[00m\]: "; else echo "\033[01;32m\][\w]\033[00m\]: "; fi)'
```

Save and close the file.

Now, whenever you create a new shell, your prompt will intelligently change depending on which directory you are currently in (Showing the text "MAC MODE" in red whenever you are in a Netatalk managed directory).






Those are the updates for now.  As always, let me know if you have any questions or comments!

---

### Post by her_meth on 2012-01-08
wonderful work, this is going to be useful. 
I'm planing to set some services and this is a great starting point.

Thanx for putting this together

---

### Post by mbuell on 2012-01-10
Wow. :popcorn:

Fantastic job. Great work - fantastically great production. 

Why? Plain English descriptions. Common sense strategic application. 

Yes, you have some extra verbiage - you bring this to us as a story - and you could trim that back by stating your goals at the top - then following up with the instruction sets. But hey, I don't mind the story - I like it. It makes it much more comfortable and friendly. So don't trim it. 

Inside that story you do a superior job of explaining security, key-based security, iptables, RAID, and more. 

I want to point this out by giving a negative example. A search on avahi gets me a link to this:
> The Avahi mDNS/DNS-SD daemon implements Apple's Zeroconf architecture (also known as "Rendezvous" or "Bonjour"). The daemon registers local IP addresses and static services using mDNS/DNS-SD and provides two IPC APIs for local programs to make use of the mDNS . .

I've been mucking about with computers for over 20 years, and linux for the past 4 or 5. I'm an intelligent, college-educated person. That description means nothing to me at all. I have to look up about every 3rd word just to feel like I have SOME grasp of what the author tried to say - and I still felt real shaky about answering "What does this mean to ME?". Compare that to what you wrote: "an open-source Bonjour alternative". There I go look up one thing - Bonjour, and say "Oh, ok."

You've done a good job, setting up some very good real-life parameters and goals. Not something written by network admins for network admins.

Here is another thank you - your examples of IP ranges. I can't tell you how many hours I have spent researching iptables and stuff trying to make the firewalls work the way I want them to work in linux. And, in all that time I have NEVER seen possible ways to write ranges of IP addresses stated so clearly or simply. I KNOW I have still had trouble getting various linux gui iptables tools to accept IP ranges properly. After all the research I did, I did not know you could use 0-250 as an equivalent to /24. If it does and it works, then you may have solved an unrelated problem. 

Massive amount of work you put in here. Excellent recording. 

Thanks.

---

### Post by mbuell on 2012-01-10
A minor correction, I think. When you get to the section managing the disks you state this command:

> sudo fdisk -l | grep -i "Disk /dev/"

But your results look like you actually used this command:
> sudo fdisk -l | grep -i "Disk "

Also - it would be easier to use this in a paged and linked format - with each section being a different page. That may be more work than you care to indulge in, but it would be easier to browse what you have. 

Still getting a giant thumbs up from me!

---

### Post by mbuell on 2012-01-14
Another thought - I agree with the poster who quibbled about the length of the article in ONE regard. Your title. It is not accurate. You compensate for this fairly quickly by stating your goals. It was because I read that section that I at first did not feel any issues with the title, but on reflection, your title should reflect your goals more accurately, and it should reflect that you spend a great deal of space on setting this up to talk outside the LAN, and talk to Macs.

---

### Post by drdos2006 on 2012-01-14
And for server newbies like me to get a better understanding of Raid, kevinthecomputerguy has just put a couple of very nice videos explaining the setting up and operation of Raid devices using Webmin as browser control of the Raid from here. [http://woodel.com/](http://woodel.com/)

regards

---

### Post by bvz on 2012-01-15
> Fantastic job. Great work - fantastically great production.

Thanks!  I am not much of a programmer, so this is one of the few ways I know to give back to the Linux community.


> **mbuell said:**
> Another thought - I agree with the poster who quibbled about the length of the article in ONE regard. Your title. It is not accurate. You compensate for this fairly quickly by stating your goals. It was because I read that section that I at first did not feel any issues with the title, but on reflection, your title should reflect your goals more accurately, and it should reflect that you spend a great deal of space on setting this up to talk outside the LAN, and talk to Macs.

Good point.  I don't know if I can edit my original Title, but if I can do you have a suggestion how I should change it?  Would it be more helpful if I called it an "in-depth guide to setting up Ubuntu 11.10 server for Newbies"?  I have a limited amount of text.  Maybe I should drop the "for Newbies" and put something else there?


> A minor correction, I think. When you get to the section managing the disks you state this command:
[QUOTE]sudo fdisk -l | grep -i "Disk /dev/"

But your results look like you actually used this command:
> sudo fdisk -l | grep -i "Disk " [/QUOTE]

You are absolutely correct.  I will make the change to the original text.  Thanks!

---

### Post by bvz on 2012-01-15
> **mbuell said:**
> 
Also - it would be easier to use this in a paged and linked format - with each section being a different page. That may be more work than you care to indulge in, but it would be easier to browse what you have. 

Yeah, that was my original plan in fact.  Each section was supposed to be a new post. But as it turns out, you have to get these tutorials approved before they get posted and they wouldn't have approved just the first section so I munged them all together into a single post (who knew it could handle that much text in a single posting? :p ).

I'd still like to figure out a way to split it up after the fact, but I don't know how something like that would be possible.  Maybe a repeat post of each section, and just edit the first post to be links?  But then there would be all of these intermediate posts between the "contents section" and the actual content.

Hmmm...

---

### Post by bvz on 2012-01-15
> **drdos2006 said:**
> And for server newbies like me to get a better understanding of Raid, kevinthecomputerguy has just put a couple of very nice videos explaining the setting up and operation of Raid devices using Webmin as browser control of the Raid from here. [http://woodel.com/](http://woodel.com/)

regards

Looks like an interesting link.  Thanks!  I will peruse it as I have a bit more time and maybe update my post to include links to his work.

---

### Post by jdawgvh on 2012-01-16
Just out of curiosity, why didn't you set up your server with DAAP?

---

### Post by bvz on 2012-01-16
> **jdawgvh said:**
> Just out of curiosity, why didn't you set up your server with DAAP?

Actually I started doing just that.  I had installed forked-daapd which is the most up to date version of DAAP available and it works quite well.  Unfortunately, the iTunes side of things is less than ideal.  iTunes and DAAP does not allow me to create playlists from the client computer as far as I can tell.  Nor does it appear to let me rate songs from the client, add music from the client, etc.  

(All of these issues are true for a "real" iTunes server as well as far as I can tell).

That is why I switched to setting up a subsonic server.  Even though it runs via Java which I don't love (though I can't really tell you why I find it problematic) the package is very nicely put together and is very flexible.  And as long as you stay away from the web interface, it can even be very pretty on the client side.  Submariner on the Mac works pretty well.  I suspect there are even more and better options on the pc.

Now I can create playlists from any connected machine, rate songs, etc.  I prefer how it organizes my music too (it just mimics the structure on the hard drive instead of using the tags embedded in the tracks).  Finally, though I have yet to take advantage of this, it allows me to stream music to anywhere in the world that I have a web connection (I would have to set up some sort of static IP address and change my firewall settings for that... something I intend to do eventually but not now).

---

### Post by asrock-z68 on 2012-01-26
Nice write up. I wish I had this when I was getting started. With Netatalk don't forget to add the "tm" option to the end of your AppleVolume.default for your shares. This will allow Apple Time Machine to recognize the share as Time Machine compatible. Also make sure your shares have read-write permissions.

---

### Post by castlecloud on 2012-02-09
Thank you for the great tutorial. :D

I followed along and when I tried to install the knockd software,
apt-get couldn't download anything anymore.

After a bit of searching I found that ufw needed another rule:

sudo ufw allow out http

which allows outgoing connections on port 80/tcp.

Can you confirm that, or did I miss something?

---

### Post by jdawgvh on 2012-02-11
I've got this all up and running (although I do have a Ubuntu client instead of a Mac).  I would like to make a small change.  I want my server to automatically update itself.  My concern is that I have the server checking every five minutes for activity on my network and it shuts itself down if it finds none.  So if I fire up my laptop to grab a file that I forgot or something and then shut it right back down my server might not have time to complete all the updates.  Is there a way to prevent the system from shutting down until updates are complete?

---

### Post by bvz on 2012-02-25
> **asrock-z68 said:**
> Nice write up. I wish I had this when I was getting started. With Netatalk don't forget to add the "tm" option to the end of your AppleVolume.default for your shares. This will allow Apple Time Machine to recognize the share as Time Machine compatible. Also make sure your shares have read-write permissions.

Sorry for the long absence everyone... things got busy at work, I'm, moving, and getting married in a couple of months.  Much. To. Do.


Anyway, thanks for the note.  You are absolutely correct regarding the "tm" option and changing the read-write permissions on the shares.  I will update the tutorial accordingly.

---

### Post by bvz on 2012-02-25
> **castlecloud said:**
> Thank you for the great tutorial. :D

I followed along and when I tried to install the knockd software,
apt-get couldn't download anything anymore.

After a bit of searching I found that ufw needed another rule:

sudo ufw allow out http

which allows outgoing connections on port 80/tcp.

Can you confirm that, or did I miss something?

I don't think you missed anything.  You may be right and we might need to add this rule.  I thought I had done something specifically to allow apt to run through the firewall but I may not have (there was so much back and forth when I was building the server that it is possible that I turned on ufw after I had done all of my apt-gets).

Most likely, if you got it to work using this rule then you should be ok.  Especially since you are only allowing the outbound on port 80.

Currently I am in the process of moving and the server is packed up and won't be unpacked for several weeks so I can't test this myself.  That said, you are most likely correct and I will update the tutorial accordingly.  Thanks for catching that.

---

### Post by bvz on 2012-02-25
> **jdawgvh said:**
> I've got this all up and running (although I do have a Ubuntu client instead of a Mac).  I would like to make a small change.  I want my server to automatically update itself.  My concern is that I have the server checking every five minutes for activity on my network and it shuts itself down if it finds none.  So if I fire up my laptop to grab a file that I forgot or something and then shut it right back down my server might not have time to complete all the updates.  Is there a way to prevent the system from shutting down until updates are complete?

As you noticed, the sleep script is incredibly stupid.  Its only criteria for staying awake is whether a client is also awake.

Ideally we would update the script so that it also looks for specific activities and as long as they are active, it will stay awake.

The original script looked like this:

```
#! /bin/bash

#check to see if any other devices are responding to pings
#only check addresses 172.16.1.2 - 172.16.1.99 because
#the Airport is always on address 172.16.1.1 and all of my
#always on devices (that don't need server access) have
#reserved IP address of 172.16.1.100 and above

#if there are no responding clients in the ip range, go to sleep
if [ `/usr/bin/fping -a -g 172.16.1.2 172.16.1.99 2> /dev/null | wc -l` -eq 0 ]; then
	/usr/sbin/pm-hibernate
fi
```


what we want to do is edit so that it also looks for specific tasks that are running.

Note, my server is currently packed away (I am moving) and won't be back up for a number of weeks.  I cannot test the following code and I am pretty sure it won't work out of the box.  But it is a start.  Once I have some time I will try to make the change official (and test it) and  post back here.

Still, for now we want to edit the script so that it reads something like this:
```

#! /bin/bash

#check to see if any other devices are responding to pings
#only check addresses 172.16.1.2 - 172.16.1.99 because
#the Airport is always on address 172.16.1.1 and all of my
#always on devices (that don't need server access) have
#reserved IP address of 172.16.1.100 and above

#also check for specific tasks that may be running that we do not
#want to interrupt

#by default the server wants to go to sleep
goToSleep=1

#if there are responding clients in the ip range, stay awake
if [ `/usr/bin/fping -a -g 172.16.1.2 172.16.1.99 2> /dev/null | wc -l` -gt 0 ]; then
        goToSleep=0
fi


#repeat the following block once for each process you want to keep the server awake for:

#check for a specific running process
if [ `/bin/ps aux | grep -i XXXXX | wc -l` -gt 1 ]; then
        goToSleep=0
fi 

#only go to sleep if all the tests above did not change the goToSleep variable.
if [ $goToSleep -eq 1 ]; then
	/usr/sbin/pm-hibernate
fi
```


Note: YOU WILL HAVE TO REPLACE THE XXXXX with some text that matches the text of the process you want to keep the server awake for.  Alas I don't know exactly what that is at the moment, but if anyone out there wants to chime in that would be great.  Otherwise, you might look into kicking off a download manually and using the:

ps aux

command to see if you can determine what the process name is that is running.

Again, once I have some more time I can come back to this and see how I can make it more robust.  Hope this helps.

---

### Post by Bushflyr on 2012-03-25
A HUGE thank you for the best setup guide I've been able to find! :guitar: It's well written and easy to follow for a complete n00b like me. 

You have a couple typos, in the hdd temp section, specifically **[FONT=Courier New][COLOR=RoyalBlue]sudo pico ~/hddtemp_mon[COLOR=Red]ti[/COLOR]or.sh [/COLOR][/FONT]**[FONT=Courier New][COLOR=RoyalBlue][FONT=Arial][COLOR=Black]It was kind of a WTF moment for me since I was cutting and pasting and the bugger is hard to see. It also occurs in the [/COLOR][/FONT][/COLOR][/FONT][FONT=Arial][COLOR=RoyalBlue][COLOR=Black]sensors monitor [/COLOR][/COLOR][/FONT][FONT=Arial][COLOR=RoyalBlue][COLOR=Black]section.[COLOR=RoyalBlue][FONT=Courier New][COLOR=Black][FONT=Arial]In the sensors monitor section you also have a line, [/FONT][/COLOR][/FONT][/COLOR][/COLOR][/COLOR][/FONT]**[FONT=Courier New][COLOR=RoyalBlue]sudo chmod ugo+rwx ~/hddtemp_monitor.sh, [/COLOR][/FONT]**[FONT=Courier New][COLOR=RoyalBlue][COLOR=Black][FONT=Arial]that should be [/FONT][/COLOR][/COLOR][/FONT]**[FONT=Courier New][COLOR=RoyalBlue]sudo chmod ugo+rwx ~/sensors_monitor.sh[/COLOR][/FONT]**[FONT=Courier New][COLOR=RoyalBlue].[COLOR=Black][FONT=Arial]

Regarding the msmtp setup section I didn't want to use my "real" email account for the concerns you expressed so I used [THESE INSTRUCTIONS]("http://www.okadadesign.no/blog/web-development/sending-email-from-localhost-using-msmtp-with-gmail/") and set it up to email my "real" email account through a throwaway Gmail account. That way nothing is compromised by having the password in the clear.

```
[/FONT][/COLOR][/COLOR][/FONT]
defaults
tls on
tls_starttls on
tls_trust_file /etc/ssl/certs/ca-certificates.crt
 
account default
host smtp.gmail.com
port 587
auth on
user username(at)gmail.com
password mypass
from username(at)gmail.com
logfile /var/log/msmtp.log

```

I'm still trying to get the sensors_monitor script working, it doesn't do anything at all for me. And that's as far as I've gotten now.

Again, thanks for a great howto.

---

### Post by bvz on 2012-03-25
> **Bushflyr said:**
> A HUGE thank you for the best setup guide I've been able to find! :guitar: It's well written and easy to follow for a complete n00b like me.


Thanks!  We n00bs gotta look out for each other :)



> **Bushflyr said:**
> You have a couple typos, in the hdd temp section, specifically **[FONT=Courier New][COLOR=RoyalBlue]sudo pico ~/hddtemp_mon[COLOR=Red]ti[/COLOR]or.sh [/COLOR][/FONT]**[FONT=Courier New][COLOR=RoyalBlue][FONT=Arial][COLOR=Black]It was kind of a WTF moment for me since I was cutting and pasting and the bugger is hard to see. It also occurs in the [/COLOR][/FONT][/COLOR][/FONT][FONT=Arial][COLOR=RoyalBlue][COLOR=Black]sensors monitor [/COLOR][/COLOR][/FONT][FONT=Arial][COLOR=RoyalBlue][COLOR=Black]section.[COLOR=RoyalBlue][FONT=Courier New][COLOR=Black][FONT=Arial]In the sensors monitor section you also have a line, [/FONT][/COLOR][/FONT][/COLOR][/COLOR][/COLOR][/FONT]**[FONT=Courier New][COLOR=RoyalBlue]sudo chmod ugo+rwx ~/hddtemp_monitor.sh, [/COLOR][/FONT]**[FONT=Courier New][COLOR=RoyalBlue][COLOR=Black][FONT=Arial]that should be [/FONT][/COLOR][/COLOR][/FONT]**[FONT=Courier New][COLOR=RoyalBlue]sudo chmod ugo+rwx ~/sensors_monitor.sh[/COLOR][/FONT]**[FONT=Courier New][COLOR=RoyalBlue].[COLOR=Black][FONT=Arial]

Thanks.  Great catch.  I've updated the post to fix those.

> **Bushflyr said:**
> Regarding the msmtp setup section I didn't want to use my "real" email account for the concerns you expressed so I used [THESE INSTRUCTIONS]("http://www.okadadesign.no/blog/web-development/sending-email-from-localhost-using-msmtp-with-gmail/") and set it up to email my "real" email account through a throwaway Gmail account. That way nothing is compromised by having the password in the clear.


Great idea.  I think I will do the same.  I added a link to your comment up in the original post so that others can profit your insight as well.


> **Bushflyr said:**
> I'm still trying to get the sensors_monitor script working, it doesn't do anything at all for me.

When you say it does not do anything, does it kick out an error?  If you set the temp to 1 degree, I am assuming it does not shut down the server, right?  Did the steps above that section work?  I.e. when you type:

[INDENT][COLOR="RoyalBlue"]sudo sensors[/COLOR][/INDENT]

does it spit out any information?

I'm trying to figure out if maybe lm-sensors is not working on your machine or if there is a problem with the script that I wrote that is calling it.

---

### Post by Bushflyr on 2012-03-25
The sensors package seems to be working fine. Here's the output:

```

****@****:~$ sudo sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +40.0°C  (crit = +65.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +41.0°C  (high = +80.0°C, crit = +99.0°C)
Core 0:         +40.0°C  (high = +80.0°C, crit = +99.0°C)
Core 1:         +39.0°C  (high = +80.0°C, crit = +99.0°C)
Core 2:         +37.0°C  (high = +80.0°C, crit = +99.0°C)
Core 3:         +39.0°C  (high = +80.0°C, crit = +99.0°C)

```And then I modified your script to be:

```

#!/bin/bash
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=80
SENSORSCMD=sensors

CORE0TEMP=$($SENSORSCMD | grep -i "Core 0" | awk '{print $3}' | awk -F '°' '{print $1}' | awk -F '+' '{print $2}' | awk -F '.' '{print $1}')
CORE1TEMP=$($SENSORSCMD | grep -i "Core 1" | awk '{print $3}' | awk -F '°' '{print $1}' | awk -F '+' '{print $2}' | awk -F '.' '{print $1}')
CORE2TEMP=$($SENSORSCMD | grep -i "Core 2" | awk '{print $3}' | awk -F '°' '{print $1}' | awk -F '+' '{print $2}' | awk -F '.' '{print $1}')
CORE3TEMP=$($SENSORSCMD | grep -i "Core 3" | awk '{print $3}' | awk -F '°' '{print $1}' | awk -F '+' '{print $2}' | awk -F '.' '{print $1}')

if [[ $CORE0TEMP =~ "^[0-9]+$" ]]; then
   if [ $CORE0TEMP -ge $ALERT_LEVEL ]; then
       echo "The server **** is shutting down due to excessive Core 0 temp (it has reached a temperature of $CORE0TEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server **** is shutting down due to excessive CPU temperature" ****@gmail.com
       $LOG "System going down as Core 0 has crossed its limit (temp=$CORE0TEMP°C, limit=$ALERT_LEVEL°C"
       sync;sync
       $DOWN -h 0
   fi
fi

if [[ $CORE1TEMP =~ "^[0-9]+$" ]]; then
   if [ $CORE1TEMP -ge $ALERT_LEVEL ]; then
      echo "The server **** is shutting down due to excessive Core 1 temp (it has reached a temperature of $CORE1TEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server **** is shutting down due to excessive CPU temperature" ****@gmail.com
      $LOG "System going down as Core 1 has crossed its limit (temp=$CORE1TEMP°C, limit=$ALERT_LEVEL°C"
      sync;sync
      $DOWN -h 0
   fi
fi

if [[ $CORE2TEMP =~ "^[0-9]+$" ]]; then
   if [ $CORE2TEMP -ge $ALERT_LEVEL ]; then
       echo "The server **** is shutting down due to excessive Core 2 temp (it has reached a temperature of $CORE2TEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server **** is shutting down due to excessive CPU temperature" ****@gmail.com
       $LOG "System going down as Core 2 has crossed its limit (temp=$CORE2TEMP°C, limit=$ALERT_LEVEL°C"
       sync;sync
       $DOWN -h 0
   fi
fi

if [[ $CORE3TEMP =~ "^[0-9]+$" ]]; then
   if [ $CORE3TEMP -ge $ALERT_LEVEL ]; then
       echo "The server **** is shutting down due to excessive Core 3 temp (it has reached a temperature of $CORE3TEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server **** is shutting down due to excessive CPU temperature" ****@gmail.com
       $LOG "System going down as Core 3 has crossed its limit (temp=$CORE3TEMP°C, limit=$ALERT_LEVEL°C"
       sync;sync
       $DOWN -h 0
   fi
fi

```Probably unnecessary to do all 4 cores since they're on the same chip, but I was a little fuzzy last night. If I get motivated and actually figure out how to write scripts I'll probably change to use just the Physical ID.

When I set the ALERT_LEVEL to 1 and run it just does nothing at all. No shut down, no email. Just another command line. All the previous scripts have generated the appropriate emails and shutdowns.

[COLOR=Red]***ETA: ****[COLOR=Black]I just noticed that there's no "do" and "done" in the sensors_monitor.sh script. I think there should be, but I'm not really sure.[/COLOR]*[/COLOR]

---

### Post by bvz on 2012-03-26
"do" and "done" are only needed if you have a for or while loop.  In our case we are using simple if-then-else commands.  

As it turns out, you found another error in my original post!

Sheesh.  

Took me a while to figure it out, but it turns out I have an error in my regular expression test.

In all of the lines where I had put something like:

```
if [[ $CORE0TEMP =~ "^[0-9]+$" ]]; then
```

I should have left the quotation marks off so it reads like this:

```
if [[ $CORE0TEMP =~ ^[0-9]+$ ]]; then
```

Clearly I need to go back and check my stuff a little more thoroughly.  :redface:  



So try the following code and let me know if it works:

```

#!/bin/bash
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=80
SENSORSCMD=sensors

CORE0TEMP=$($SENSORSCMD | grep -i "Core 0" | awk '{print $3}' | awk -F '°' '{print $1}' | awk -F '+' '{print $2}' | awk -F '.' '{print $1}')
CORE1TEMP=$($SENSORSCMD | grep -i "Core 1" | awk '{print $3}' | awk -F '°' '{print $1}' | awk -F '+' '{print $2}' | awk -F '.' '{print $1}')
CORE2TEMP=$($SENSORSCMD | grep -i "Core 2" | awk '{print $3}' | awk -F '°' '{print $1}' | awk -F '+' '{print $2}' | awk -F '.' '{print $1}')
CORE3TEMP=$($SENSORSCMD | grep -i "Core 3" | awk '{print $3}' | awk -F '°' '{print $1}' | awk -F '+' '{print $2}' | awk -F '.' '{print $1}')

if [[ $CORE0TEMP =~ ^[0-9]+$ ]]; then
   if [ $CORE0TEMP -ge $ALERT_LEVEL ]; then
       echo "The server **** is shutting down due to excessive Core 0 temp (it has reached a temperature of $CORE0TEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server **** is shutting down due to excessive CPU temperature" ****@gmail.com
       $LOG "System going down as Core 0 has crossed its limit (temp=$CORE0TEMP°C, limit=$ALERT_LEVEL°C"
       sync;sync
       $DOWN -h 0
   fi
fi

if [[ $CORE1TEMP =~ ^[0-9]+$ ]]; then
   if [ $CORE1TEMP -ge $ALERT_LEVEL ]; then
      echo "The server **** is shutting down due to excessive Core 1 temp (it has reached a temperature of $CORE1TEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server **** is shutting down due to excessive CPU temperature" ****@gmail.com
      $LOG "System going down as Core 1 has crossed its limit (temp=$CORE1TEMP°C, limit=$ALERT_LEVEL°C"
      sync;sync
      $DOWN -h 0
   fi
fi

if [[ $CORE2TEMP =~ ^[0-9]+$ ]]; then
   if [ $CORE2TEMP -ge $ALERT_LEVEL ]; then
       echo "The server **** is shutting down due to excessive Core 2 temp (it has reached a temperature of $CORE2TEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server **** is shutting down due to excessive CPU temperature" ****@gmail.com
       $LOG "System going down as Core 2 has crossed its limit (temp=$CORE2TEMP°C, limit=$ALERT_LEVEL°C"
       sync;sync
       $DOWN -h 0
   fi
fi

if [[ $CORE3TEMP =~ ^[0-9]+$ ]]; then
   if [ $CORE3TEMP -ge $ALERT_LEVEL ]; then
       echo "The server **** is shutting down due to excessive Core 3 temp (it has reached a temperature of $CORE3TEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server **** is shutting down due to excessive CPU temperature" ****@gmail.com
       $LOG "System going down as Core 3 has crossed its limit (temp=$CORE3TEMP°C, limit=$ALERT_LEVEL°C"
       sync;sync
       $DOWN -h 0
   fi
fi
```


I have updated the original post to fix this error.

---

### Post by Bushflyr on 2012-04-01
Tried that and it works well, thanks. 

I also found, not really an error, but depending (I think) on the model of HDD the $4 in your hddtemp_monitor script needs to be changed to $3. 

I have Seagate drives, hddtemp outputs:

```
/dev/sdb: ST2000DL003-9VT166: 35°C
```and running your script returned:

```

/home/****/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected
/home/****/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected
/home/****/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected
/home/****/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected

```Changing line 10 to read:

```

HDTEMP=$($HDT $disk | awk '{ print $3}' | awk -F '°' '{ print $1}')

```Fixed my issue.

***[COLOR=Red]EDIT[/COLOR]***[COLOR=Red][COLOR=Black]: Nope, guess it didn't. But it would have if I didn't have a mix of WD (/home) and Seagate (md0) drives. Trying to parse the different drive name formats is giving errors. 

Looking at [THIS PAGE]("http://www.cyberciti.biz/tips/howto-monitor-hard-drive-temperature.html") in the comments section gives what seems to be the solution, using the --numeric arg. Here's the script as I've got it running now and it hasn't kicked out any errors.

```
#!/bin/bash
HDDS="/dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=1
args="--numeric"
for disk in $HDDS
do
if [ -b $disk ]; then
    HDTEMP=$($HDT $disk $args)
    $LOG "HDTEMP for $disk is $HDTEMP"
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
            echo "The server **** is shutting down due to excessive hard drive temp. Drive: $disk has reached a temperature of $HDTEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server **** is shutting down due to excessive hard drive temperature" ****@gmail.com            
            $LOG "System going down as hard disk : $disk temperature $HDTEMP°C exceeded its limit"
            sync;sync
            $DOWN -h 0
        fi
fi
done
```[/COLOR][/COLOR] 

The next thing is that gknw.net and gknw.de seem to be permanently down. Is there another source for the WOL package? I've started in using the [Depicus page]("http://www.depicus.com/wake-on-lan/wake-on-lan-for-apple-mac.aspx"), but haven't gotten it working yet.

And, in no particular order, :p the pm-suspend command completely broke my install. After much gnashing of teeth and reinstaling the OS and breaking it again, I figured out that COMPLETELY powering down the system, not just turning it off, but physically unplugging it from the wall would allow it to boot again. Working on that issue today.

---

### Post by Bushflyr on 2012-04-01
And, I think there needs to be a section on setting the permissions after creating the various directories on the raid. I can see them on my Mac, but due to messed up permissions, I can't write to them.

---

### Post by stanbx on 2012-04-01
Thanks for posting this!

---

### Post by meanmoe32 on 2012-04-07
Thank you for this guide.

I modified the script hddtemp_monitor.sh for use with seagate and WD drives.  I have both and it seems that WD drives have an additional character which is recognized as a delimiter in awk:

From:
```

HDTEMP=$($HDT $disk | awk '{ print $4}' | awk -F '°' '{ print $1}')

```
To:
```

HDTEMP=$($HDT $disk | sed 's/\(.*\)://g' | awk -F '°' '{ print $1}')

```

I thought that others may find use for it.

Of course, if you had all seagate drives then you could just usethe following instead: 
```

HDTEMP=$($HDT $disk | awk '{ print $3}' | awk -F '°' '{ print $1}')

```
Again, thanks for the guide... very useful

EDIT: For the coretemp stuff, couldn't a default value be used instead of an additional conditional statement that checks for numbers?

---

### Post by jdawgvh on 2012-08-07
I found two utilities that might be useful.

Webmin automatically does a lot of the stuff that we did manually here:
[http://doxfer.webmin.com/Webmin]("http://doxfer.webmin.com/Webmin")

The other one had been bothering me for a little while.  Little did I know that it was there all along, I just needed to configure it.  My goal is to let Ubuntu update Windows style.  I like how Windows does all of it's updates with very little user intervention.  This can be done by configuring unattended updates
[https://help.ubuntu.com/10.04/serverguide/automatic-updates.html]("https://help.ubuntu.com/10.04/serverguide/automatic-updates.html")

---

### Post by Luke1991 on 2012-08-20
hey, I've been trying to follow this but the WOL script is down.

could anybody mirror the unix script at ```
http://www.gknw.net/wol.html 
``` for us?

---

### Post by ratcheer on 2012-08-24
Hi, bvz. Are you still around?

Did you know that this is one of the best threads on the whole internet?

Tim

---

### Post by bvz on 2012-09-28
Wow.  I had no idea anyone was even reading this.


I moved, got married, went on a long trip and then got back to my life about 2 months ago.  I must have my notification settings messed up because I never get any emails that anyone commented on this thread.  I just assumed nobody was interested in reading my ridiculously long tutorial.

I'll go through it over the next few days and see what's been happening (and fix up any errors in the original post if they have been pointed out).  I also am thinking of redoing the whole thing with the latest version of Ubuntu Server, just to keep things up to date.


> **ratcheer said:**
> Hi, bvz. Are you still around?

Did you know that this is one of the best threads on the whole internet?

Tim

---

### Post by jmc1024 on 2012-09-28
> **bvz said:**
> Wow.  I had no idea anyone was even reading this.


I moved, got married, went on a long trip and then got back to my life about 2 months ago.  I must have my notification settings messed up because I never get any emails that anyone commented on this thread.  I just assumed nobody was interested in reading my ridiculously long tutorial.

I'll go through it over the next few days and see what's been happening (and fix up any errors in the original post if they have been pointed out).  I also am thinking of redoing the whole thing with the latest version of Ubuntu Server, just to keep things up to date.

I've been following this as well! It is a great post and I refer to it often.  Thank you.

If you decide to spend some time on this, I'd like to suggest integrating squid into the mix. I installed squid and iptable rules to run a transparent proxy. Now the server can't resolve .local. addresses!?!

Mark

p.s. Congratulations on getting married! I hope you will be as happily married as I am to my beautiful bride.

---

### Post by bvz on 2012-09-30
> **jmc1024 said:**
> p.s. Congratulations on getting married! I hope you will be as happily married as I am to my beautiful bride.

Thanks!  I got one of the good ones myself.  Couldn't be happier.

---

### Post by bvz on 2012-09-30
> **jmc1024 said:**
> If you decide to spend some time on this, I'd like to suggest integrating squid into the mix. I installed squid and iptable rules to run a transparent proxy. Now the server can't resolve .local. addresses!?!.

I'll look into squid.  I never heard of it before now so it might take some time to figure it out (and time is one of those things I am perpetually short on).

My primary goal with this setup was to be "reasonably close" to a bare metal installation so that I would learn what everything does.  Now a real Linux guru would consider this install as not even close to bare metal, but for my purposes it is.

I'll check into squid, but if it just wraps some of what I am already doing I might skip it simply because I want a solid understanding of what works and why.  That is the same reason I skipped using any webmin type stuff as well.  Eventually I will switch to something like that, but when I do I hope that my time setting up this server like I did will help me really be able to troubleshoot and customize the system after one of these more automated interfaces has had its way.

Another thing I am considering is trying out openmediavault.  It seems like it is exactly the kind of thing I could use:  Automated but based on debian so that I can go in and customize it.

---

### Post by Zikofski on 2012-10-08
i tell you, you are a legend i have been following this for weeks now and slowly building up my server day by day, i am using 12.04 and so far it all works perfect with a few little things that i am posting so far :)

```
sudo chmod u+x /usr/local/sbin/continuous.sh
```

this code didnt work for me, it seemed to work on the test script, when running it mannualy but i got this email every 5 mins :( haha 

```
/bin/sh: 1: /usr/local/sbin/continuous.sh: Permission denied
```

busted my balls getting this ever 5 mins for 2 whole days haha,

it was fixed by using a different type of chmod code that you used after that,

instead of u+x i did ugo+rwx

and now i dont get any emails, but i know it worked as i got a error email from hdd temp :) which was fixed hopefully fixed the other guy who posted about that error :)

again many many thanks for this, its long but omg so good, all the info is in one place no sodding about in multiple threads and pages

P.S congrats on getting married too dude

---

### Post by incindre on 2012-10-24
Hiya BVZ,

Great post, I was completely lost without it!
I ran into some difficulties during the setup of the RAID Array. I'm trying to create RAID10 and simply substituted 'level 5' for 'level 10' during the setup. It wouldn't mount to any mount point I created. I installed Webmin, deleted the array and rebuilt (using webmin) and I'm all sweet now (or so I hope).
I'm now setting up the systems to monitor the health of the server and was wondering what the point of your 'Hourly' 'Daily' 'Weekly' scripts are, and if they are of any great importance. I've followed your instructions to the letter (and triple checked that my email address is spelled correctly) but when I test any of the scripts in the ~/ directory it sends no email and states "line 3: mail: command not found" (MDADM reporting to the same Gmail address is working fine however).
[ ]("http://i442.photobucket.com/albums/qq145/Incindre/MountingError1_zpsdc248db9.jpg")
I'm a Ubuntu novice using Server 12.04, could someone shed some light on this?

---

### Post by bvz on 2012-10-28
> **incindre said:**
> Hiya BVZ,

Great post, I was completely lost without it!
I ran into some difficulties during the setup of the RAID Array. I'm trying to create RAID10 and simply substituted 'level 5' for 'level 10' during the setup. It wouldn't mount to any mount point I created. I installed Webmin, deleted the array and rebuilt (using webmin) and I'm all sweet now (or so I hope).
I'm now setting up the systems to monitor the health of the server and was wondering what the point of your 'Hourly' 'Daily' 'Weekly' scripts are, and if they are of any great importance. I've followed your instructions to the letter (and triple checked that my email address is spelled correctly) but when I test any of the scripts in the ~/ directory it sends no email and states "line 3: mail: command not found" (MDADM reporting to the same Gmail address is working fine however).
[ ]("http://i442.photobucket.com/albums/qq145/Incindre/MountingError1_zpsdc248db9.jpg")
I'm a Ubuntu novice using Server 12.04, could someone shed some light on this?

Hey incindre,

Sorry for the delay in getting back to you.  I really only have time on the weekends now to look into this stuff (work and volunteering is getting out of hand).

I'm glad you managed to get your raid set up.  I haven't tried Webmin, but it sounds pretty cool.

The hourly etc. scripts are not super important.  They are simply scripts that get launched once an hour, day, or week (depending on the script) that launch other scripts.  The idea was as follows:

create four directories (continuous, hourly, daily, weekly).

create four scripts (continuous, hourly, daily, weekly).

These four scripts would be called by cron on an continuous, hourly, daily, weekly basis (respectively).  Each of these scripts does just one thing, it looks into its associated directory and runs any scripts it may find in that directory.  If there are no scripts in the directory, it does nothing and then goes back into hibernation till the next time it is called.

All the actual work is done by the scripts that you drop into each of these directories.  The idea was that makes it easier to just write a script (should you need a script to do something on a repetitive basis) and drop it into the directory to activate it (or move it out of the directory to deactivate it).



Could you post your script here?  I'll try to carve out a little time to look at it.  Make sure you remove or obscure any personal information (like your email and/or password).

Could you also post the results of the following command?  Type: "which mail" at the command prompt and then copy the results and include them in your post.

Finally, could you also post the results of the following command?  Type "dpkg --get-selections | grep msmtp" at the command prompt and then copy the results and include them in your post.

Based on the error you are reporting, though, it sounds like you don't have msmtp set up properly (or installed at all).  But you indicated that mdadm is properly sending emails so I am a little lost.



I'll try to look at it as quickly as possible.  I know how frustrating it can be to have the system not behave but not know where to turn to even get started debugging it.

---

### Post by bvz on 2012-10-28
> **Zikofski said:**
> i tell you, you are a legend i have been following this for weeks now and slowly building up my server day by day, i am using 12.04 and so far it all works perfect with a few little things that i am posting so far :)

```
sudo chmod u+x /usr/local/sbin/continuous.sh
```

this code didnt work for me, it seemed to work on the test script, when running it mannualy but i got this email every 5 mins :( haha 

```
/bin/sh: 1: /usr/local/sbin/continuous.sh: Permission denied
```

busted my balls getting this ever 5 mins for 2 whole days haha,

it was fixed by using a different type of chmod code that you used after that,

instead of u+x i did ugo+rwx

and now i dont get any emails, but i know it worked as i got a error email from hdd temp :) which was fixed hopefully fixed the other guy who posted about that error :)

again many many thanks for this, its long but omg so good, all the info is in one place no sodding about in multiple threads and pages

P.S congrats on getting married too dude

glad that worked for you.  I'll have to go back and check to see why the original version didn't work for you.  I suspect that your scripts were owned by you, but on my rig I must have had the scripts owned by root (or vice versa).  It should be fine the way you got it to work though.

---

### Post by Philliesfan251 on 2012-12-16
Thank you for posting such a great guide!
I am having a problem with hddtemp and shutting down at a certain temperature. When I try to run the script sudo ~/hddtemp_monitor.sh I get the following error ```
frank@Server:~$ sudo ~/hddtemp_monitor.sh
/home/frank/hddtemp_monitor.sh: line 11: [: 32Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 27Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 29Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 28Â: integer expression expected

```
Also when I tried to send a test email from mdadm, it didn't work and I got the following error ```
frank@Server:~$ sudo mdadm --monitor --scan --test
mdadm: Only one autorebuild process allowed in scan mode, aborting
```
I'm not to sure what to do from here, any help from anyone would be much appreciated.

---

### Post by CharlesA on 2012-12-16
> **Philliesfan251 said:**
> Thank you for posting such a great guide!
I am having a problem with hddtemp and shutting down at a certain temperature. When I try to run the script sudo ~/hddtemp_monitor.sh I get the following error ```
frank@Server:~$ sudo ~/hddtemp_monitor.sh
/home/frank/hddtemp_monitor.sh: line 11: [: 32Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 27Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 29Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 28Â: integer expression expected

```
Also when I tried to send a test email from mdadm, it didn't work and I got the following error ```
frank@Server:~$ sudo mdadm --monitor --scan --test
mdadm: Only one autorebuild process allowed in scan mode, aborting
```
I'm not to sure what to do from here, any help from anyone would be much appreciated.
Use UTF-8 encoding.

---

### Post by Philliesfan251 on 2012-12-16
How do I go about doing that?

---

### Post by bvz on 2012-12-16
> **Philliesfan251 said:**
> Thank you for posting such a great guide!
I am having a problem with hddtemp and shutting down at a certain temperature. When I try to run the script sudo ~/hddtemp_monitor.sh I get the following error ```
frank@Server:~$ sudo ~/hddtemp_monitor.sh
/home/frank/hddtemp_monitor.sh: line 11: [: 32Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 27Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 29Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 28Â: integer expression expected

```
Also when I tried to send a test email from mdadm, it didn't work and I got the following error ```
frank@Server:~$ sudo mdadm --monitor --scan --test
mdadm: Only one autorebuild process allowed in scan mode, aborting
```
I'm not to sure what to do from here, any help from anyone would be much appreciated.

CharlesA might have the answer there, though I don't know how that would happen.

Could you post your script here?

How are you creating it (for example, are you using a gui text editing app to create it)?

With regard to your second issue, it sounds to me like mdadm is already running and doing something (obviously I am no expert).  Type the following and paste the results back here:

```
ps -ax | grep -i mdadm
```

---

### Post by bvz on 2012-12-16
> **Philliesfan251 said:**
> Thank you for posting such a great guide!
I am having a problem with hddtemp and shutting down at a certain temperature. When I try to run the script sudo ~/hddtemp_monitor.sh I get the following error ```
frank@Server:~$ sudo ~/hddtemp_monitor.sh
/home/frank/hddtemp_monitor.sh: line 11: [: 32Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 27Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 29Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 28Â: integer expression expected

```
Also when I tried to send a test email from mdadm, it didn't work and I got the following error ```
frank@Server:~$ sudo mdadm --monitor --scan --test
mdadm: Only one autorebuild process allowed in scan mode, aborting
```
I'm not to sure what to do from here, any help from anyone would be much appreciated.


One other question, how many disks do you have in your array?  What are they named?  For example, in my case I have 4 (actually, five if you include the one that holds the OS).  The four that are being monitored are named: 

/dev/sdb 
/dev/sdc 
/dev/sdd 
/dev/sde

The script assumes that you have these drives named as such (line 2).

---

### Post by bvz on 2012-12-16
> **Philliesfan251 said:**
> 
Also when I tried to send a test email from mdadm, it didn't work and I got the following error ```
frank@Server:~$ sudo mdadm --monitor --scan --test
mdadm: Only one autorebuild process allowed in scan mode, aborting
```
I'm not to sure what to do from here, any help from anyone would be much appreciated.

Try modifying your command to add the following flag:

--no-sharing


So the command becomes:
sudo mdadm --monitor --scan --no-sharing

---

### Post by Philliesfan251 on 2012-12-16
```
frank@Server:~$ ps -ax | grep -i mdadm
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
 1079 ?        Ss     0:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog
10749 pts/2    R+     0:00 grep --color=auto -i mdadm
```

```
#!/bin/bash
HDDS="/dev/sd[a-d]"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=1
for disk in $HDDS
do
  if [ -b $disk ]; then
        HDTEMP=$($HDT $disk | sed 's/\(.*\)://g' | awk -F 'ï¿½' '{ print $1}')
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
           echo "Your server is shutting down due to excessive hard drive temp. Drive: $d$
           $LOG "System going down as hard disk : $disk temperature $HDTEMPï¿½crossed its$
           sync;sync
           $DOWN -h 0
        fi
  fi
done

```
I have 4 and I edited the script so it would be correct.
I'm editing it all from putty command line.
Not to sure how to copy all from putty.

---

### Post by bvz on 2012-12-16
> **Philliesfan251 said:**
> ```
frank@Server:~$ ps -ax | grep -i mdadm
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
 1079 ?        Ss     0:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog
10749 pts/2    R+     0:00 grep --color=auto -i mdadm
```

```
#!/bin/bash
HDDS="/dev/sd[a-d]"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=1
for disk in $HDDS
do
  if [ -b $disk ]; then
        HDTEMP=$($HDT $disk | sed 's/\(.*\)://g' | awk -F 'ï¿½' '{ print $1}')
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
           echo "Your server is shutting down due to excessive hard drive temp. Drive: $d$
           $LOG "System going down as hard disk : $disk temperature $HDTEMPï¿½crossed its$
           sync;sync
           $DOWN -h 0
        fi
  fi
done

```
I have 4 and I edited the script so it would be correct.
I'm editing it all from putty command line.
Not to sure how to copy all from putty.


Ok, well at least line 11 is short enough that we can see it all.

Do you see where your script differs from mine in the line above?  Line 10?  The awk statement has a different mix of characters than the degree symbol.

Try running the following on the command line directly:

```
/usr/sbin/hddtemp /dev/sda | sed 's/\(.*\)://g' | awk -F 'ï¿½' '{ print $1}')
```

This is just line 10 set up to run directly from the command line for disk sda.  Other than substituting in the actual hddtemp command for the variable, and substituting in the sda drive for the variable, it is identical to what you posted.  I suspect that the results of this command will not come back with an integer number.  I suspect that that is because the original script was supposed to split the returned text on the degree symbol and throw away anything other than the first part (the part before the degree symbol).  That is what awk does.  If your script is looking for something other than the degree symbol, it won't split the line properly and you will get some extra cruft in there that should have been cut away.

A second question I have is about your line 2

You concatenate all your drives by saying /dev/sd[a-d]

That's pretty fancy.  I've never done that before.  Does that actually give you the correct array?  Just wondering.

---

### Post by Philliesfan251 on 2012-12-16
> **bvz said:**
> Ok, well at least line 11 is short enough that we can see it all.

Do you see where your script differs from mine in the line above?  Line 10?  The awk statement has a different mix of characters than the degree symbol.

Try running the following on the command line directly:

```
/usr/sbin/hddtemp /dev/sda | sed 's/\(.*\)://g' | awk -F 'ï¿½' '{ print $1}')
```

This is just line 10 set up to run directly from the command line for disk sda.  Other than substituting in the actual hddtemp command for the variable, and substituting in the sda drive for the variable, it is identical to what you posted.  I suspect that the results of this command will not come back with an integer number.  I suspect that that is because the original script was supposed to split the returned text on the degree symbol and throw away anything other than the first part (the part before the degree symbol).  That is what awk does.  If your script is looking for something other than the degree symbol, it won't split the line properly and you will get some extra cruft in there that should have been cut away.

A second question I have is about your line 2

You concatenate all your drives by saying /dev/sd[a-d]

That's pretty fancy.  I've never done that before.  Does that actually give you the correct array?  Just wondering.

Line 10 was changed because of a previous comment somewhere in this thread that fixed another error I was getting.

```
frank@Server:~$ /usr/sbin/hddtemp /dev/sda | sed 's/\(.*\)://g' | awk -F 'ï¿½' '{ print )1}'
-bash: syntax error near unexpected token `)'
```

About line 2 I saw it somewhere when I was googling my errors. :D

---

### Post by bvz on 2012-12-16
> **Philliesfan251 said:**
> Line 10 was changed because of a previous comment somewhere in this thread that fixed another error I was getting.

```
frank@Server:~$ /usr/sbin/hddtemp /dev/sda | sed 's/\(.*\)://g' | awk -F 'ï¿½' '{ print )1}'
-bash: syntax error near unexpected token `)'
```

About line 2 I saw it somewhere when I was googling my errors. :D

re: Line 2
Cool trick


Did you try running the command by itself?

```
/usr/sbin/hddtemp /dev/sda | sed 's/\(.*\)://g' | awk -F 'ï¿½' '{ print $1}')
```

That will spit back exactly what line 10 in the script is doing. I suspect it will return something that is your hd temp plus some extra text.

---

### Post by CharlesA on 2012-12-16
> **Philliesfan251 said:**
> How do I go about doing that?
The only time I have run into that particular problem is if I am connecting to the box via Putty on Windows. It defaults to Latin-1, but you can change it from Windows > Translation

---

### Post by Philliesfan251 on 2012-12-17
> **bvz said:**
> re: Line 2
Cool trick
 
 
Did you try running the command by itself?
 
```
/usr/sbin/hddtemp /dev/sda | sed 's/\(.*\)://g' | awk -F 'ï¿½' '{ print $1}')
```
 
That will spit back exactly what line 10 in the script is doing. I suspect it will return something that is your hd temp plus some extra text.
 
Check the code you quoted :)

---

### Post by bvz on 2012-12-17
> **Philliesfan251 said:**
> Check the code you quoted :)

Whoops.  Total reading comprehension fail on my part.


Try running the following command (I had an extra parenthesis at the end):

```
/usr/sbin/hddtemp /dev/sda | sed 's/\(.*\)://g' | awk -F 'ï¿½' '{ print $1}'
```


I went ahead and ran a similar command here.  Note that I am traveling for work and don't have access to my server, but I am in front of a linux machine.  I literally ran the following command (I don't have hddtemp installed on this machine so I had to fake the output of hddtemp.  That's why I have that echo command in there. But this should be mostly identical to what your hddtemp is putting out.):

```
echo '/dev/sda: WDC WD2500YS-01SHB1:  25°C' | sed 's/\(.*\)://g' | awk -F 'ï¿½' '{ print $1}' 
``` 

and got back this:

```
 25°C
```


Note the degree symbol plus the letter 'C'.  That is what is messing up the next line which expects just an integer.

If I modify your command just the tiniest bit (replace the funky characters with a degree symbol) it gets closer:

```
echo '/dev/sda: WDC WD2500YS-01SHB1:  25°C' | sed 's/\(.*\)://g' | awk -F '°' '{ print $1}'
```

this gets me:

```
 25
```

This is just the temperature, but note that it still leaves me with some leading spaces.  I don't know if that is going to be an issue or not, but my original line in my script does not have any leading spaces.


I modified the line to remove any leading spaces (this might be the overkill way to do it, but it was the fastest way I could think of):

```
echo '/dev/sda: WDC WD2500YS-01SHB1:  25°C' | sed 's/\(.*\)://g' | sed 's/^[ \t]*//' | awk -F '°' '{ print $1}'
```

This returns just an integer.



So... after all of that, try putting the following line into your script:

```
HDTEMP=$($HDT $disk | sed 's/\(.*\)://g' | sed 's/^[ \t]*//' | awk -F '°' '{ print $1}')
```



Double check that line yourself to make sure it makes sense.  We have already established that my reading comprehension is a bit off :)


That should get your script functioning correctly.

I hope.

---

### Post by Philliesfan251 on 2012-12-18
Replaced that line
```
#!/bin/bash
HDDS="/dev/sd[a-d]"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=1
for disk in $HDDS
do
  if [ -b $disk ]; then
        HDTEMP=$($HDT $disk | sed 's/\(.*\)://g' | sed 's/^[ \t]*//' | awk -F 'ï¿½' '{ print $1}')
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
           echo "Your server is shutting down due to excessive hard drive temp. Drive: $disk has reached a temperature of $HDTEMPï¿½C and has crossed its limit of $ALERT_LEVELï¿½C" | mail -s "ALERT! The Your server is shutting down due to e$       $LOG "System going down as hard disk : $disk temperature $HDTEMPï¿½C crossed its limit"
           sync;sync
           $DOWN -h 0
        fi
  fi
done

```
 
Got this
```
frank@Server:~$ sudo ~/hddtemp_monitor.sh
/home/frank/hddtemp_monitor.sh: line 11: [: 28Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 26Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 26Â: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 27Â: integer expression expected

```
 
I'm running 12.04 if that makes any difference.

---

### Post by CharlesA on 2012-12-18
It looks like the problem is because of the way the script checks to see if the temp is higher than alert level.

I just checked the script you posted and it bombed out on me:

```
./test.sh: line 11: [: 32°C: integer expression expected

```

It looks like bvz fixed it by replacing the delimiter in awk with the degree symbol (which your code doesn't have). Your code also does not have the degree symbol at all and I can only think that is due to not using UFT-8 encoding, as I have run into similar problems in the past.

I went back to the original script and compared it with the current one and got this:

```
#!/bin/bash
HDDS="/dev/sd[a-d]"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=40
for disk in $HDDS
do
  if [ -b $disk ]; then
        HDTEMP=$($HDT $disk | sed 's/\(.*\)://g' | sed 's/^[ \t]*//' | awk -F '°' '{ print $1}')
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
echo $HDTEMP
           echo "The server ubuntu is shutting down due to excessive hard drive temp. Drive: $disk has reached a temperature of $HDTEMP°C and has crossed its limit of $ALERT_LEVEL°C" | mail -s "ALERT! The server ubuntu is shutting down due to excessive hard drive temperature" email@domain.com
          $LOG "System going down as hard disk : $disk temperature $HDTEMP°C crossed its limit"
           sync;sync
           $DOWN -P 0
        fi
  fi
done

```

Note: This script will bomb out if you have a drive that doesn't report a SMART temp:
```
./test.sh: line 12: [: too many arguments
```

@bvz: Outstanding job on that script. :)

---

### Post by Philliesfan251 on 2012-12-18
This is what it does UTF-8
```
frank@Server:~$ sudo ~/hddtemp_monitor.sh
[sudo] password for frank:
/home/frank/hddtemp_monitor.sh: line 11: [: 32&#9618;: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 29&#9618;: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 30&#9618;: integer expression expected
/home/frank/hddtemp_monitor.sh: line 11: [: 30&#9618;: integer expression expected

```

EDIT: Wow, just changed to UTF-8 and put the original script in and it worked! Should have listened to you from the beginning Charles. Thanks for the troubleshooting as well bvz, you have an awesome guide here.

---

### Post by Philliesfan251 on 2012-12-18
> **bvz said:**
> Try modifying your command to add the following flag:

--no-sharing


So the command becomes:
sudo mdadm --monitor --scan --no-sharing

Now for this problem :P I tried that and it kind of just hung, no emails or anything, had to Ctrl+C after like 5 minutes.

---

### Post by CharlesA on 2012-12-18
> **Philliesfan251 said:**
> 
EDIT: Wow, just changed to UTF-8 and put the original script in and it worked! Should have listened to you from the beginning Charles. Thanks for the troubleshooting as well bvz, you have an awesome guide here.

It has happened to everyone. I just know about it because I was trying to figure out why I was getting an odd character from cputemp and found out it was cuz of my encoding.

Glad you got it sorted. :)

---

### Post by bvz on 2012-12-20
> **Philliesfan251 said:**
> Now for this problem :P I tried that and it kind of just hung, no emails or anything, had to Ctrl+C after like 5 minutes.

Hey there, sorry for dropping off like that.

As far as I can tell, the original error you had is a new bug that was introduced in Ubuntu 12.04.  Since I am still on the older version, I can't replicated it (well... couldn't even if I tried since I am not at home).

Here is a quick description of it (in language that is hard to comprehend):

[http://osdir.com/ml/ubuntu-bugs/2012-02/msg11004.html](http://osdir.com/ml/ubuntu-bugs/2012-02/msg11004.html)

and here in language that is a little easier to follow:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641886](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641886)


Here is my interpretation (which could be wildly incorrect, it is only based on about 15 minutes of googling):

I think that the new version of mdadm only allows one monitoring process at a time.  We tell mdadm explicitly to scan the arrays when we followed the following part of my tutorial:

> We want to add the above line into the madadm.conf file. The easiest way to do this is to append the line to the end of the file and then edit it afterwards. Start by typing the following (note the pipe symbol after the word scan… it should be right above the enter key on your keyboard on U.S. keyboards):

sudo mdadm --detail --scan | sudo tee --append /etc/mdadm/mdadm.conf
Now, edit the /etc/mdadm/mdadm.conf file by typing:

sudo nano /etc/mdadm/mdadm.conf
The line you appended should be at the end of the file. While it is actually ok to just leave it there, the German in me wants it to live in the "correct" location. I just use cut and paste to move it just under the portions that reads:

# definitions of existing MD arrays
It appears that newer versions of mdadm don't like the "name=XXXXXX" or "metadata=NN" portions of this line. Remove both of those so that the line just reads (again, your UUID will be different):

ARRAY /dev/md0 UUID=77b695c4:32e5dd46:63dd7d16:17696e09
Save and close the file.

The new version of mdadm will not do any additional scanning without the --no-sharing option turned on.


There are a couple ways of fixing this.  The first, adding --no-sharing, should have done it for you (and I suspect it may have - more on this later).  The second is to install an updated version of mdadm.  You will have to use apt-get to download it (and you may have to use a different repository than the one built into Ubuntu - try googling on how to do that.  I can try to help you if you run into trouble)

Apparently the bug has been fixed, but it isn't in Ubuntu yet as far as I can tell.  If you can download and install the latest version of mdadm, that might solve it for you.

But according to what I have read, that > --no-sharing should have fixed it for you.




And it may have.


mdadm will not stop until you hit ctrl-c.  So that is normal.


It seems to me that the email portion is not working.  I.e. mdadm is doing what it should, but it isn't actually sending you an email (or for some reason you are not receiving it).  As far as I can tell, you have never received an email from mdadm, is that correct?  If so, I would suspect that that is your issue now.  Look to see whether you have properly set up that part of the tutorial (I forget exactly where it is and don't have time right now to look, but let me know if you still need help and I can do some research).




Here is one other thing you could try (add the --oneshot flag):

```
mdadm --monitor --scan --oneshot --no-sharing --test
```

But I'm not sure that this is going to help at all.  From the man page 

[http://linux.die.net/man/8/mdadm]("http://linux.die.net/man/8/mdadm")

we get this:

> -oneshot
Check arrays only once. This will generate NewArray events and more significantly DegradedArray and SparesMissing events. Running
mdadm --monitor --scan -1
from a cron script will ensure regular notification of any degraded arrays.

Which is a little cryptic.




But I suspect the issue is your email settings.




Oh, one more thing.  Once you get this working in test mode, I'm not sure whether you need to somehow propagete the --no-sharing into the config file or something.  That is another issue you may have to resolve.

Good luck.

---

### Post by bvz on 2012-12-20
> **CharlesA said:**
> @bvz: Outstanding job on that script. :)

Thanks!

---

### Post by Philliesfan251 on 2012-12-27
> **bvz said:**
> Hey there, sorry for dropping off like that.

As far as I can tell, the original error you had is a new bug that was introduced in Ubuntu 12.04.  Since I am still on the older version, I can't replicated it (well... couldn't even if I tried since I am not at home).

Here is a quick description of it (in language that is hard to comprehend):

[http://osdir.com/ml/ubuntu-bugs/2012-02/msg11004.html](http://osdir.com/ml/ubuntu-bugs/2012-02/msg11004.html)

and here in language that is a little easier to follow:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641886](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641886)


Here is my interpretation (which could be wildly incorrect, it is only based on about 15 minutes of googling):

I think that the new version of mdadm only allows one monitoring process at a time.  We tell mdadm explicitly to scan the arrays when we followed the following part of my tutorial:



The new version of mdadm will not do any additional scanning without the --no-sharing option turned on.


There are a couple ways of fixing this.  The first, adding --no-sharing, should have done it for you (and I suspect it may have - more on this later).  The second is to install an updated version of mdadm.  You will have to use apt-get to download it (and you may have to use a different repository than the one built into Ubuntu - try googling on how to do that.  I can try to help you if you run into trouble)

Apparently the bug has been fixed, but it isn't in Ubuntu yet as far as I can tell.  If you can download and install the latest version of mdadm, that might solve it for you.

But according to what I have read, that  should have fixed it for you.




And it may have.


mdadm will not stop until you hit ctrl-c.  So that is normal.


It seems to me that the email portion is not working.  I.e. mdadm is doing what it should, but it isn't actually sending you an email (or for some reason you are not receiving it).  As far as I can tell, you have never received an email from mdadm, is that correct?  If so, I would suspect that that is your issue now.  Look to see whether you have properly set up that part of the tutorial (I forget exactly where it is and don't have time right now to look, but let me know if you still need help and I can do some research).




Here is one other thing you could try (add the --oneshot flag):

```
mdadm --monitor --scan --oneshot --no-sharing --test
```

But I'm not sure that this is going to help at all.  From the man page 

[http://linux.die.net/man/8/mdadm]("http://linux.die.net/man/8/mdadm")

we get this:



Which is a little cryptic.




But I suspect the issue is your email settings.




Oh, one more thing.  Once you get this working in test mode, I'm not sure whether you need to somehow propagete the --no-sharing into the config file or something.  That is another issue you may have to resolve.

Good luck.

Thanks for the reply, I just tried it and got this message:

```
frank@Server:~$ mdadm --monitor --scan --oneshot --no-sharing --test
sendmail: cannot log to /var/log/msmtp.log: cannot open: Permission denied
sendmail: log info was: host=smtp.gmail.com tls=on auth=on user=myemail@gmail.com from=myemail@gmail.com recipients=myemail@gmail.com mailsize=534 smtpstatus=250 smtpmsg='250 2.0.0 OK 1356613608 t17sm49147429wiv.6' exitcode=EX_OK

```

...and this email:
```
This is an automatically generated mail message from mdadm
running on Server

A TestMessage event had been detected on md device /dev/md0.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid0 sdd1[2] sdb1[0] sdc1[1]
      1533528576 blocks super 1.2 512k chunks

unused devices: <none>
```

On a separate note, I started getting this hourly email:
```
/usr/local/sbin/hourly.active/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected
```

Not really in any rush to get it resolved because my server runs fine, but it would be nice to fix it :)

---

### Post by bvz on 2012-12-27
> **Philliesfan251 said:**
> Thanks for the reply, I just tried it and got this message:

```
frank@Server:~$ mdadm --monitor --scan --oneshot --no-sharing --test
sendmail: cannot log to /var/log/msmtp.log: cannot open: Permission denied
sendmail: log info was: host=smtp.gmail.com tls=on auth=on user=myemail@gmail.com from=myemail@gmail.com recipients=myemail@gmail.com mailsize=534 smtpstatus=250 smtpmsg='250 2.0.0 OK 1356613608 t17sm49147429wiv.6' exitcode=EX_OK

```

...and this email:
```
This is an automatically generated mail message from mdadm
running on Server

A TestMessage event had been detected on md device /dev/md0.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid0 sdd1[2] sdb1[0] sdc1[1]
      1533528576 blocks super 1.2 512k chunks

unused devices: <none>
```

On a separate note, I started getting this hourly email:
```
/usr/local/sbin/hourly.active/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected
```

Not really in any rush to get it resolved because my server runs fine, but it would be nice to fix it :)


Happy new year!

Glad things are starting to settle down.

The permission errors you are getting are, I think, because you are running mdadm directly (and not using the sudo command to run it as root).  The command appears to run (seeing as how you are getting the email), but you don't have permissions to write to the log.  If you try re-running it again but this time with the sudo command at the beginning of the line I suspect you would get the same email but without the error message at the beginning. But since you are getting the email, things appear to be working.


The second error you are getting because there appears to still be a typo in your script (and if the scrip errors out, cron automatically sends an email to that effect).  Could you post your hddtemp_monitor.sh script here again?  That particular line in the script compares the hard drive temperature (HDTEMP) against your predefined alert level (ALERT_LEVEL).  The error seems to indicate that one of those two variables does not contain a number.  I think we managed to get the HDTEMP variable worked out previously, right?  So it may be an error in the ALERT_LEVEL variable.

Anyway, repost your entire script here and I suspect we can work it out.

---

### Post by Philliesfan251 on 2012-12-28
> **bvz said:**
> Happy new year!

Glad things are starting to settle down.

The permission errors you are getting are, I think, because you are running mdadm directly (and not using the sudo command to run it as root).  The command appears to run (seeing as how you are getting the email), but you don't have permissions to write to the log.  If you try re-running it again but this time with the sudo command at the beginning of the line I suspect you would get the same email but without the error message at the beginning. But since you are getting the email, things appear to be working.


The second error you are getting because there appears to still be a typo in your script (and if the scrip errors out, cron automatically sends an email to that effect).  Could you post your hddtemp_monitor.sh script here again?  That particular line in the script compares the hard drive temperature (HDTEMP) against your predefined alert level (ALERT_LEVEL).  The error seems to indicate that one of those two variables does not contain a number.  I think we managed to get the HDTEMP variable worked out previously, right?  So it may be an error in the ALERT_LEVEL variable.

Anyway, repost your entire script here and I suspect we can work it out.

I wasnt thinking, I tried sudo right after I posted that and it worked fine, thanks!

Here's line 10 & 11:
```
 HDTEMP=$($HDT $disk | awk '{ print $4}' | awk -F '°' '{ print $1}')
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
```
All of this script stuff is completely foreign to me. Hopefully I'll have time to learn it one day.

---

### Post by bvz on 2012-12-29
> **Philliesfan251 said:**
> I wasnt thinking, I tried sudo right after I posted that and it worked fine, thanks!

Here's line 10 & 11:
```
 HDTEMP=$($HDT $disk | awk '{ print $4}' | awk -F '°' '{ print $1}')
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
```
All of this script stuff is completely foreign to me. Hopefully I'll have time to learn it one day.


No worries on the script stuff being foreign.  Eventually it will make sense if you keep hammering on it.  That said, there really isn't a need to learn it either.

Try the following code.  Save it as a completely different file (something like temp.sh) in your home directory.  Change its permissions to be executable:

chmod ugo+rwx ~/temp.sh  


Then run it by typing:

~/temp.sh


Post back the results here.  It will let me try to figure out where your code is going wrong.

All this is is your code from a previous posting, but modified so that it prints out a bunch of diagnostic information as it runs (that is what all the echo commands are for - they just print a value back to the command line when the code runs)  

```
#!/bin/bash
HDDS="/dev/sd[a-d]"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=1
echo "ALERT_LEVEL"
echo $ALERT_LEVEL
for disk in $HDDS
do
  if [ -b $disk ]; then
        HDTEMP=$($HDT $disk | sed 's/\(.*\)://g' | sed 's/^[ \t]*//' | awk -F '°' '{ print $1}')
        echo "HDTEMP"
        echo $HDTEMP
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
            echo "The server ubuntu is shutting down due to excessive hard drive temp. Drive: $disk has reached a temperature of $HDTEMP degrees Celsius and has crossed its limit of $ALERT_LEVEL degrees Celsius" | mail -s "ALERT! The server ubuntu is shutting down due to excessive hard drive temperature" youremail@yourdomain.com
            $LOG "System going down as hard disk : $disk temperature $HDTEMP degrees Celsius crossed its limit of $ALERT_LEVEL"
            sync;sync
            $DOWN -h 0
        fi
  fi
done
```


Note: I am visiting family at the moment and don't have a linux box in front of me to test this script.  I hope I haven't introduced any errors but it *should* be good to go.

---

### Post by Philliesfan251 on 2012-12-30
> **bvz said:**
> No worries on the script stuff being foreign.  Eventually it will make sense if you keep hammering on it.  That said, there really isn't a need to learn it either.

Try the following code.  Save it as a completely different file (something like temp.sh) in your home directory.  Change its permissions to be executable:

chmod ugo+rwx ~/temp.sh  


Then run it by typing:

~/temp.sh


Post back the results here.  It will let me try to figure out where your code is going wrong.

All this is is your code from a previous posting, but modified so that it prints out a bunch of diagnostic information as it runs (that is what all the echo commands are for - they just print a value back to the command line when the code runs)  

```
#!/bin/bash
HDDS="/dev/sd[a-d]"
HDT=/usr/sbin/hddtemp
LOG=/usr/bin/logger
DOWN=/sbin/shutdown
ALERT_LEVEL=1
echo "ALERT_LEVEL"
echo $ALERT_LEVEL
for disk in $HDDS
do
  if [ -b $disk ]; then
        HDTEMP=$($HDT $disk | sed 's/\(.*\)://g' | sed 's/^[ \t]*//' | awk -F '°' '{ print $1}')
        echo "HDTEMP"
        echo $HDTEMP
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
            echo "The server ubuntu is shutting down due to excessive hard drive temp. Drive: $disk has reached a temperature of $HDTEMP degrees Celsius and has crossed its limit of $ALERT_LEVEL degrees Celsius" | mail -s "ALERT! The server ubuntu is shutting down due to excessive hard drive temperature" youremail@yourdomain.com
            $LOG "System going down as hard disk : $disk temperature $HDTEMP degrees Celsius crossed its limit of $ALERT_LEVEL"
            sync;sync
            $DOWN -h 0
        fi
  fi
done
```


Note: I am visiting family at the moment and don't have a linux box in front of me to test this script.  I hope I haven't introduced any errors but it *should* be good to go.

No worries, I'm not really in any rush, like I said. Here's the results. I did receive an email and the server did shut down.

```
frank@Server:~$ sudo nano ~/temp.sh
[sudo] password for frank:
frank@Server:~$ chmod ugo+rwx ~/temp.sh
chmod: changing permissions of `/home/frank/temp.sh': Operation not permitted
frank@Server:~$ sudo chmod ugo+rwx ~/temp.sh
frank@Server:~$ ~/temp.sh
ALERT_LEVEL
1
/dev/sda: open: Permission denied

HDTEMP

/home/frank/temp.sh: line 15: [: -ge: unary operator expected
/dev/sdb: open: Permission denied

HDTEMP

/home/frank/temp.sh: line 15: [: -ge: unary operator expected
/dev/sdc: open: Permission denied

HDTEMP

/home/frank/temp.sh: line 15: [: -ge: unary operator expected
/dev/sdd: open: Permission denied

HDTEMP

/home/frank/temp.sh: line 15: [: -ge: unary operator expected
frank@Server:~$ sudo ~/temp.sh
ALERT_LEVEL
1
HDTEMP
33

Broadcast message from frank@Server
        (/dev/pts/0) at 16:25 ...

The system is going down for halt NOW!
HDTEMP
30

```

Email
```
The server ubuntu is shutting down due to excessive hard drive temp. Drive: /dev/sda has reached a temperature of 33 degrees Celsius and has crossed its limit of 1 degrees Celsius
```

---

### Post by Hawkway on 2012-12-31
This looks like a great guide especially for someone new to Ubuntu, like me.  Would the steps be similar for 12.04 server or is there a similar guide out there?

---

### Post by blaakfisk on 2013-01-04
I cannot say how grateful I am for this guide. I'm building a computer to do this on this weekend. I am wondering, though, would the security measures in this guide be incompatible with using Apache, MySQL and PHP to host a website? After completing this process I might search for a guide on how to do that.

---

### Post by incindre on 2013-01-04
Hi BVZ,

Thanks for getting back to me (all those months ago) but I pushed my problems to the back of my mind and got stuck in with sorting SAMBA out.
I've just bought a UPS for my server and can't get it to send me emails, so I've returned in the hope that you can suss me out!

Like you, I only need the server to warn me when there's been an error with my RAID Array or my UPS.

Here are the results of the commands you asked for:

> **which mail**
/usr/bin/mail> **dpkg --get-selections | grep msmtp**
msmtp                                           install
msmtp-mta                                     installMSMTP seems to be installed, it doesn't list in Webmin when I search for packages, but when I try to intall it from the terminal it says that it's already at the latest version.
Running a command to send a test email results in an email being successfuly sent.

MDADM's test emails worked when I last checked them (months ago) but not anymore, now I get:

> :~$ **sudo mdadm --monitor --scan --test**
mdadm: Only one autorebuild process allowed in scan mode, aborting
By adding --no-sharing to the end of that command it will actually send me a message; I won't pretend to know what that means, but I've put --no-sharing in the daily cron script for MDADM.
Should I also add --no-sharing to the MDADM script in the 'cron.d' folder? and does this guarantee that if bad stuff goes down with my RAID array that I'll get the appropriate alert?

Cheers!

---

### Post by rahvintalemon on 2013-01-09
As a Linux/Ubuntu novice I really appreciate the detail and effort put into this guide. Your guide doesn't gloss over the "easy" parts of the install and really drills down into the details when needed. I've bookmarked this as my goto file server setup guide at least until I get on my feet with Ubuntu.

Thanks!

---

### Post by wolfbuddy on 2013-01-19
Totally agree with the post above. Thank you for taking the time to create this. You're a :KS

---

### Post by tardyviking on 2013-01-21
Thanks.  Dude I love reading tutorials that are "narrative" .  Yours is very helpful and I will use it when I set up my server.  Thanks.  Your style is great for beginners.

---

### Post by MortenSJ on 2013-02-15
Thanks for a great tutorial. This really helped alot.

I'm trying to do the mail thing, and i went with the gmail thing and got it to work. 

I have a problem when i try to initiate the script.

```
sudo ~/testContinuous.sh
```

I get this error

```
/home/myUserName/testContinuous.sh: line 3: mail: command not found
```

BUT i think the script is working just fine. I keep getting mails every 5 minuttes from the server, but they are saying this.

```
/bin/sh: 1: /usr/local/sbin/continuous.sh: Permission denied
```

I also get an error when trying to run this

```
sudo ~/hddtemp_monitor.sh
```

Error

```
/home/myUserName/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected
```

I tried to google it, but i cant find anything useful.

---

### Post by bvz on 2013-02-16
Hey everybody, sorry for disappearing like that again.  Looks like this thread is in danger of disappearing sometime soon.  I guess the whole tips and tricks forum is going away.  Makes me sad, but then there is no point in fighting something you have no control over.

I am going to try to post this document somewhere else on the web (most likely a blog) so that if it does go away here, it will still be available.  I considered trying to convert it to the wiki but quickly ran out of steam trying to figure that out (which says something about my tenacity since wiki's are notoriously easy to deal with).  I think I gave up quickly because I am not sure how I would interact with folks like you all who have questions.

Anyway, hopefully the whole document will still be available somewhere on the internet for those who need it.  I might even, if I have time, update it to the latest version of Ubuntu Server.

Now some more disclaimers.  My server is no longer running.  It ran fine for quite a while, but then I got a bug up my butt to try something else and I have no money for new equipment.  So, I have dismantled it and now I am trying to build a couple different "mini servers" using a raspberry pi and the original drives from this machine (I'm hoping to make something similar to the new transporter device - google "transporter cloud" for more info).  Still, though, I should be able to help folks with questions.

Ok, let's dive into it...

---

### Post by bvz on 2013-02-16
> **Hawkway said:**
> This looks like a great guide especially for someone new to Ubuntu, like me.  Would the steps be similar for 12.04 server or is there a similar guide out there?

I'm not sure if there are any similar guides out there for 12.04.  But that said, I suspect nearly everything here would still apply to 12.04.  The only part that may be easier on the new system is netatalk.  I think they have a later version by default (one that works with Mountain Lion and Lion).

Outside of that I don't think you are looking at anything radically different.

Good luck.

---

### Post by QIII on 2013-02-16
You can help to maintain a wiki in the Community Wikis or create a new one if none exists.

That is where all the Tutorials & Tips have gone.

---

### Post by bvz on 2013-02-16
> **blaakfisk said:**
> I cannot say how grateful I am for this guide. I'm building a computer to do this on this weekend. I am wondering, though, would the security measures in this guide be incompatible with using Apache, MySQL and PHP to host a website? After completing this process I might search for a guide on how to do that.

My pleasure.

I think the security measures I indicated here would have to be expanded so that your different services (Apache, MySQL and PHP) can get through the firewall.  

I am not specifically sure what ports those services use (though I think Apache uses at least port 80).  You will need to modify the firewall section to allow those ports to be open and directed to the appropriate services (which really just means adding rules to the firewall).

Let me know if this makes sense to you.

---

### Post by bvz on 2013-02-16
> **incindre said:**
> Hi BVZ,

Thanks for getting back to me (all those months ago) but I pushed my problems to the back of my mind and got stuck in with sorting SAMBA out.
I've just bought a UPS for my server and can't get it to send me emails, so I've returned in the hope that you can suss me out!

Like you, I only need the server to warn me when there's been an error with my RAID Array or my UPS.

Here are the results of the commands you asked for:

MSMTP seems to be installed, it doesn't list in Webmin when I search for packages, but when I try to intall it from the terminal it says that it's already at the latest version.
Running a command to send a test email results in an email being successfuly sent.

MDADM's test emails worked when I last checked them (months ago) but not anymore, now I get:


By adding --no-sharing to the end of that command it will actually send me a message; I won't pretend to know what that means, but I've put --no-sharing in the daily cron script for MDADM.
Should I also add --no-sharing to the MDADM script in the 'cron.d' folder? and does this guarantee that if bad stuff goes down with my RAID array that I'll get the appropriate alert?

Cheers!


Sorry for the delay in getting back to you.

I *think* that what is happening is that you have mdadm running already as a daemon (i.e. it is running automatically when you start your server) and so that when you run it in test mode, it freaks out because there is already a version trying to manage your array.

The only way I think you could test that would be to somehow disable mdadm from running at startup.  I forget exactly how to do that but I suspect that if I waded through my original post, the information would be in there (can't believe I am too lazy to read my own guide! :)

Once you have mdamd disabled and you restart your server, you *should* be able to run your mdadm test command (without the -no-sharing flag) and still get the email.  Again, this is only a guess.  But if that works, then you will have confirmed that the issue is as I described it above.  (don't forget to re-enable mdadm when you are done).

If this is actually the case then I think the answer is that the "no-sharing" is not strictly necessary (since you normally will only have a single copy of mdadm active on your server).  That said, I don't think the no-sharing flag would hurt anything.

I can't guarantee that mdadm will email you if something goes wrong because I have to admit to being only a novice at this myself.  You might want to post your question elsewhere where someone with more experience might see it.  I'd hate for something to go wrong and you not get notified.

Another thing to check (it's getting too late to do the research myself just now and my wife is giving me evil looks even as I type this) is whether you can get mdadm to send you a "hey, I'm still here" message from time to time.  I suspect you are not the only one who sits and frets when you get no messages at all from your server.  "Is it still running?"  "Does no contact mean all is well, or does it mean my sentries are asleep at the gate?"

Frustrating :)

---

### Post by bvz on 2013-02-16
> **rahvintalemon said:**
> As a Linux/Ubuntu novice I really appreciate the detail and effort put into this guide. Your guide doesn't gloss over the "easy" parts of the install and really drills down into the details when needed. I've bookmarked this as my goto file server setup guide at least until I get on my feet with Ubuntu.

Thanks!

Thank you!  I'm glad I could help.  I get so much help from other people posting their guides on the internet it makes me glad I can give back a little.

That said, you should probably copy the guide to your local computer.  This whole forum is slated to be taken down in the near future and the guide will disappear.  I will try to put it back up somewhere  else, but as you can see by the frequency with which I reply here that my ability to spend time on this only comes in fits and starts.

---

### Post by bvz on 2013-02-16
> **wolfbuddy said:**
> Totally agree with the post above. Thank you for taking the time to create this. You're a :KS

Showed this to my wife.  She agrees :)

Thank you!

---

### Post by bvz on 2013-02-16
> **tardyviking said:**
> Thanks.  Dude I love reading tutorials that are "narrative" .  Yours is very helpful and I will use it when I set up my server.  Thanks.  Your style is great for beginners.

My pleasure.  I can get really wordy sometimes but I'm glad that that style works for you.

As I mentioned above, if you want to hang on to this tutorial you should consider copying it to your local machine as this forum is being taken down in the near future (no more tips and tricks unfortunately).

---

### Post by bvz on 2013-02-16
> **MortenSJ said:**
> Thanks for a great tutorial. This really helped alot.

Thanks!

> I'm trying to do the mail thing, and i went with the gmail thing and got it to work. 

I have a problem when i try to initiate the script.

```
sudo ~/testContinuous.sh
```

I get this error

```
/home/myUserName/testContinuous.sh: line 3: mail: command not found
```

What happens if you type the following on a command line?

```
which mail
```




> BUT i think the script is working just fine. I keep getting mails every 5 minuttes from the server, but they are saying this.

```
/bin/sh: 1: /usr/local/sbin/continuous.sh: Permission denied
```



I actually think the script is not working at all.  Those emails may be from cron itself.  If you set up your cron to email you whenever it encounters an error, that means that every time it tries to run the continuous.sh script it fails and then sends you an email.

The actual error you are getting is Permission denied which means that the permissions on your script are incorrect.  Type the following into your shell and post back the results here:

```
ls -l /usr/local/sbin/continuous.sh
```



> I also get an error when trying to run this

```
sudo ~/hddtemp_monitor.sh
```

Error

```
/home/myUserName/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected
```

I tried to google it, but i cant find anything useful.


This is similar (or maybe even identical) the issue that Philliesfan251 was having.  If you read through this entire thread, you will see what I am talking about.  Specifically it appears that the output of your hddtemp command is not actually outputting a pure number.   Check out what he was dealing with.  If you are still having issues after you read through the thread feel free to ask me more questions.

---

### Post by bvz on 2013-02-16
> **Philliesfan251 said:**
> No worries, I'm not really in any rush, like I said. Here's the results. I did receive an email and the server did shut down.

```
frank@Server:~$ sudo nano ~/temp.sh
[sudo] password for frank:
frank@Server:~$ chmod ugo+rwx ~/temp.sh
chmod: changing permissions of `/home/frank/temp.sh': Operation not permitted
frank@Server:~$ sudo chmod ugo+rwx ~/temp.sh
frank@Server:~$ ~/temp.sh
ALERT_LEVEL
1
/dev/sda: open: Permission denied

HDTEMP

/home/frank/temp.sh: line 15: [: -ge: unary operator expected
/dev/sdb: open: Permission denied

HDTEMP

/home/frank/temp.sh: line 15: [: -ge: unary operator expected
/dev/sdc: open: Permission denied

HDTEMP

/home/frank/temp.sh: line 15: [: -ge: unary operator expected
/dev/sdd: open: Permission denied

HDTEMP

/home/frank/temp.sh: line 15: [: -ge: unary operator expected
frank@Server:~$ sudo ~/temp.sh
ALERT_LEVEL
1
HDTEMP
33

Broadcast message from frank@Server
        (/dev/pts/0) at 16:25 ...

The system is going down for halt NOW!
HDTEMP
30

```

Email
```
The server ubuntu is shutting down due to excessive hard drive temp. Drive: /dev/sda has reached a temperature of 33 degrees Celsius and has crossed its limit of 1 degrees Celsius
```



Hey Philliesfan251,

So it looks like you got it working, right?

---

### Post by bvz on 2013-02-16
By the way to everyone who has questions.  If for some reason this forum does disappear and you still need questions answered, feel free to send me a pm.  You can even send me one if you post a message and I don't respond within a day or two.  If I get a notice that someone has posted here and I don't open it up right away I sometimes forget to return to the forum and then I don't get any additional notifications when there are new postings.

Picture someone with crazy hair who walks around muttering to themselves with strings tied to each finger.

That's me.

---

### Post by bvz on 2013-02-16
> **QIII said:**
> You can help to maintain a wiki in the Community Wikis or create a new one if none exists.

That is where all the Tutorials & Tips have gone.

I'll give it a try.  One thing I am not sure about is how people ask questions about the wiki.  For example if some of the folks here were having trouble with something I wrote (like they have) where would they go to ask questions.  And how would I know that they asked these questions so that I could either answer them (or fix the wiki)?

I know that others can update the wiki and that makes it a community project and I am ok with that.  I just wanted to know how I personally would still be able to connect with the people who are having trouble with a wiki I created.

Also, I suspect there is a tutorial on setting up/maintaining a wiki.  Could you point me to it?  Thanks!  People on this forum have been so helpful to me I do like the idea of giving back.

---

### Post by CharlesA on 2013-02-16
> **bvz said:**
> I'll give it a try.  One thing I am not sure about is how people ask questions about the wiki.  For example if some of the folks here were having trouble with something I wrote (like they have) where would they go to ask questions.  And how would I know that they asked these questions so that I could either answer them (or fix the wiki)?

I know that others can update the wiki and that makes it a community project and I am ok with that.  I just wanted to know how I personally would still be able to connect with the people who are having trouble with a wiki I created.

Also, I suspect there is a tutorial on setting up/maintaining a wiki.  Could you point me to it?  Thanks!  People on this forum have been so helpful to me I do like the idea of giving back.

What has normally occurred is the information in the OP or whatever gets moved to the wiki and a thread is created for questions/comments.

I believe there is a script out there that can help convert a forum post to wikicode, but I don't know where it is off the top of my head.

---

### Post by The Big Baddie on 2013-03-02
Hello,

I want to start by saying I really appreciate this thread. It has been very helpful in setting up my server. Now to my problem. I am trying to get the maintenance scripts up and working and everything works until I get to the part where I am writing test scripts. Everything is fine until I go to test the test scripts. I get this:

```
/home/dylan/testContinuous.sh: line 3: mail: command not found
```

I tried to google for some answers but I didnt find anything helpful. I do know that msmtp is working correctly because I did an echo test email and I received the test email. Thanks for your time and the guide again.

---

### Post by CharlesA on 2013-03-02
Are you sure you have the mailutils package installed?

Otherwise, check to make sure you are using the full path to mail.

---

### Post by The Big Baddie on 2013-03-02
That totally fixed it. I thought I had installed that package but I guess I didn't. Either way thanks for the tip :)

---

### Post by The Big Baddie on 2013-03-02
> **CharlesA said:**
> Use UTF-8 encoding.

Charles, can you post a link so I can learn how to do that. I understand the issue but I dont know how to fix it.

---

### Post by CharlesA on 2013-03-03
> **The Big Baddie said:**
> Charles, can you post a link so I can learn how to do that. I understand the issue but I dont know how to fix it.

Check this out:
[http://dag.wieers.com/blog/content/improving-putty-settings-on-windows](http://dag.wieers.com/blog/content/improving-putty-settings-on-windows)

---

### Post by The Big Baddie on 2013-03-03
Oh it is a setting. I thought it was in the coding itself. Thanks again.

---

### Post by The Big Baddie on 2013-03-03
Okay now I am getting this error:

```
/home/*****/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected
/home/*****/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected
/home/*****/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected
/home/*****/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected
/home/*****/hddtemp_monitor.sh: line 11: [: -ge: unary operator expected

```

Edit: Fixed it nevermind

---

### Post by undadawg on 2013-05-21
edit: fixed it

thanks, this is a great guide

---

### Post by TheFu on 2013-09-05
Sorry for the late response - didn't read anything after > 196.0.10.* where * can be any number between 1 and 255
line. You probably realize this incorrect now.
[https://www.arin.net/knowledge/address_filters.html](https://www.arin.net/knowledge/address_filters.html) or the RFC has the specifics.

    10.0.0.0/8 IP addresses: 10.0.0.0 -- 10.255.255.255
    172.16.0.0/12 IP addresses: 172.16.0.0 -- 172.31.255.255
    192.168.0.0/16 IP addresses: 192.168.0.0 – 192.168.255.255

Setting up a "server" can be as easy as during the install, choosing "LAMP" or "ssh" from the installation menu.  Adding all the RAID stuff is good, but might scare "noobs" away.

I like to add either fail2ban or denyhosts on any machine with internet access - good to quickly block unwanted ssh (and other) attempts, right?

---

