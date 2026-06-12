---
title: "Don't Get Me Wrong About This. But..."
date: 2010-08-04
forum: Testimonials &amp; Experiences
---

### Post by oldefoxx on 2010-08-04
i still spend most my free time dealing with Ubuntu in terms of installs and trying to get certain aspects towork will with each other.  That is actually the light part of my day, even though progress is slow as I encounter unexpected issues.

For instance, did you know that an early release of 9.10 did not include support for the touchpad mouse?  Sort of makes it a bad choice for portables, like laptops and notebooks.  Apparently this was cause as a missing psmouse in the kernel, so they updated the kernel and put out a new release of 9.10.  Problem solved, right?

Not quite.  If you are following the Update Manager method of moving up to version 0.10, you inadvertantly will get the old 9.10 kernel instead, and the touchpad still does not work.  You are forced tp download 9.10 yourself, burn it to a CD, reboot to it, and elect to use the manual partitioning method with no formatting to try and preserve /home with all the user accounts and data.  Many people would rather avoid having tp go manual this way. No information found on getting a package with psmouse in it and then doing another make and install on the kernel.  You also need headers and other things to make that happen anyway. 

If you are trying to move up from 8.10, you may have another problem. The Brasero Disk Burner that shows up there lacks a means of burning an image directly to a CD or DVD.  You have to find, download and install another package to do this for you, or get it done on another PC.

Disk burning software is not always that great anyway.  There are differences, and the disks vary widely in terms of write speed and compatability with specific burners.  Expect to make several copies to be on the safe sode. Best choices in terms of software should include a buffer feature and manual override for the recording speed, and maybe a verify after write feature

Debian distros like Ubuntu offer what are called DEB files for installing or updating software.  Software sources for DEB files and such are maintained in what are called Repositories, which are approved online sites that the Update Manager will visit occasionally.  The Update Manager knows of these sites by settings you make or enable in /System/Administrative/Software Sources.  An alternative procedure is go into Terminal mode, enter sudo -s, then enter the command apt-get update, and when that completes, follow it with the command apt-get update,  You also have the options of using apt-get install <package name> and apt-ger remove <package name> to  by entries in /etc/apt/sources.list.

Knowing the full name of a package is not always required.  This is because you can tag the end of what you know or guess at with an asterick, and if the first part matches, that is good enough  For instance, if you want to install wine, you have several approaches.  Just go with apt-get install wine, and if that does not work, you can mext try apt-get install wine*  If there is a specific version of wine that you want, you might elect to try apt-get install wine1*, which might fetch wine 1.0, wine 1.1, or wine 1.2, whichever is currently flagged as being appropriate for your version of Ubuntu.

These are just things you pick up as you move along.  What can hinder you sometimes, in fact quite often, are matters involving assigned ownership and rights for accessing various files and folders, or even specific drives.  By using sudo -s in terminal mode, you also gain the reght to reassign ownership and specific rights to each of the files and folders individually or collectively.  To actially do this, you will likely make use of the chown and chmod commands.  Changing ownership is not really necessary in many cases, and best not be done if ownership needs to go back at some point.  That is becase there is no clear indication of whom owns what, so putting it back might be a bit difficult.  However, before doing a chmod, you might use something like a ls -al command, which reports flag status along with eacn file listed.  Use that list as a guide, and chmod will let you get the job done.

What I cannot decide is whether Ubuntu is targeted at the owner/user, or intended for some organization with assigned users per machine.  If the first, the emphasis on security and ownership are set too high in my opinion.  You will spend a lot of time having to enter enter your password time and time again just to get pass the hurdles.  If meant for organizations, there is concern that the user might be able to do too much, because he can easily get into terminal mode, grab root rights, make changes, then depart back to what he was doing before. Would an organiations's management be comfortable enough with that possbility, and hope ot might be used?  Too much might be put at risk if that wer to ever happen, which it easily could happen.

Let me add another concern as well.  Any LiveCD or USB drive becomes a possible means of breaching the safeguards of any PC to wich they can be attached and used to boot from.  The native system is dormant at that point and unable to enact or assist in its own defense.  If everything is fully encrpted, then there is no immediate consequence, but the whole of the machine's contents can be stored for later study, and a little software bug added to capture the encrption key the next time the PC is brought up.  The only real trick is get the key off the PC out to where the intruders want it to go so that they can get to it.  Then they are free to put all the encrypted contents on another PC and use the key to open it all up.

There is enough simularity between Unix and Linux that each is potentially a threat to the other.  There is even more simularity between different distos of Linux, meaning that each then acts as an inscured threat to all of the others. And there is essentially no way to change this, because this is part of what open source creates, an [e environment with essentially no real basis for providing security.

I was taught two approaches in the military for trying to protect myself from enemy fire.  The first is cover, like trying to put a rock or vehicle between me and the enemy.  This helps, but if the enemy knows I am there, they will repositon themselves to get a clearer shot at me.  Eventually they will get me.  So cover is not the best answer.  

The other method is concealment, like crouching down in a ditch, lying under a bunch of leaves, or if seen, not looking like the enemy to my enemies.  This is much better, because if I am not evident, or if I am seen as being one of them, then they won't know to shoot me.

Some terrorists in Iraq and other places take a different aproach to the second method.  They dress up as police or the military and move among the populnce and other troopa.  When they are ready, they begin the slaughter of those around them. Then they depart, not to repeat this act for some time.  By this means, they erode the people confidence in those that seem to be there to protect them, and no one really knows whom to trust any more.  That may seem totally unrelated, but if Linux comes across as offering real protection, but is actually quite open to Linux in general, then you can see how that can be made to work against you, or your company, or your country, or whatever.

The only real approach to security is total concealment. I mean hardware that cannot be found anywhere else, software specific to only this hardware, and data in a vernacular of its own.  If the government is saving money by just buying and using equipment off the shelf that anybody can buy and use, do you think they put us all at greater risk or not?

So in my considered opinion, it would be absolute foolishness to take a product like Ubuntu to the organizational level without establishing some real in-deph contol and monitoring features that cannot be evaded. But software alone is not sufficient for this purpose.

What I can conclude is that Ubuntu as it stands really needs to be directed to the individal owner/user, which you might say it is now, but again the safeguards in place really just serve to intefere wih actions of the owner/user, and I don't see that as a necessary or desireable thing.

---

### Post by Ocxic on 2010-08-04
Allowing physical access to any machine allows for a security breach. if you don't want people booting live CD's or live USB drives, disable CD and USB booting in the BIOS and protect the BIOS with a password(tho given access to a machine for enough time allows a user to clear the BIOS).

Also "sudo" access is limited to ADMINISTRATIVE users, you have the option of created a "limited" or "normal" user account that does not allow access to "sudo" thus removing the security risk of users running commands with root / superuser privileges.
TIP: Use "sudo -i" not "sudo -s"

File permissions and access controls are there to prevent unauthorized use/viewing/execution of files and folders that a specific user would not normally have access to. Thus increasing the security of the overall system. Generally you should never need to "chmod" or "chown" anything unless your doing something specific that requires it. (Like sharing a folder between users)

Asking for a password to perform administrative tasks insure that an authorized person it really at the computer. "sudo" has a password timeout that allows you to perform multiple commands within a certain time limit (15min I think, and is separated from GUI and TERMINAL commands) this allows for enough time to perform tasks without becoming cumbersome by consistently asking for a password.(this time limit can be customized)

The repositories are full of software the has been tested, and confirmed safe to use with the system, and allows for a trusted source of software. any software installed out if the official repositories are basically "use at your own risk"

Your premise:
"There is enough similarity between Unix and Linux that each is  potentially a threat to the other.  There is even more similarity  between different distros of Linux, meaning that each then acts as an insecure threat to all of the others. And there is essentially no way to  change this, because this is part of what open source creates, an [e  environment with essentially no real basis for providing security."

I believe to be incorrect, UNIX and LINUX are very different systems, though they share certain similarities, they are very different, and neither pose a security risk to the other. Although any operating system that has the ability to boot a computer system, and access it's current file system could be considered a threat, and thus accounts for almost all types of OS's out there.

> 
Some terrorists in Iraq and other places take a different aproach to the  second method.  They dress up as police or the military and move among  the populnce and other troopa.  When they are ready, they begin the  slaughter of those around them. Then they depart, not to repeat this act  for some time.  By this means, they erode the people confidence in  those that seem to be there to protect them, and no one really knows  whom to trust any more.  That may seem totally unrelated, but if Linux  comes across as offering real protection, but is actually quite open to  Linux in general, then you can see how that can be made to work against  you, or your company, or your country, or whatever.
In response to the above quote: "If I put a letter in a Safe and hide the safe, that is security by obscurity. However, if I give you the same safe, with 100 other safes and there combinations, and detailed specifications of how the safe works, and you still cannot open the original safe with the letter, that is true security. And the true meaning of open source"

Basically TOTAL system security is practically impossible. With enough  time, and access to the physical machine, anyone can compromise a  system.(I know, I've done it)
It's only how much you've hardened the system to prevent a breach that will allow you the time to detect it.

Remember "Security is a journey, not a destination"

---

### Post by Elfy on 2010-08-04
moved - possibly this was a testimonial

---

### Post by oldefoxx on 2010-08-05
I am familiar with the concepts and need for security.  The problem is, to begin with, the more security needed, the less friendly the system becoems.  This is a blocking mechanism to ensure that you do not exceed what is expected of you.

Unfprtunately, being able to boot a working version of Linux from a CD, DVD, or whatever, means you are not hindered by designed in blockage of the system where the boot takes place.  So the means to get around the system safeguards can come in the door at any time in the hands of anyone that has access to the system. Any blocks then have failed.

Don't forget that in preparation for the attacks on 9/11, the men involved had already been trained in the necessary skills to get the planes to the sites and aim them in,  The blockage mechanisms of no planes, no pilots, no training for the planes, and no will to die as well were thus all overcome with just a bit of pre-planning, organization and commitment.

And the LiveCD approach to a hands-on effort to penetrating a Linux system does not even require a password!  To compare, the 9/11 attacks would have been just as feasable if the people that got on those planes had just the most basic flying skills and no familiarity with the type aircraft, because aircraft tend to follow the same rules when it comes to flight maneuvers.  The pre-schooling just made it more certain, just as using someone well versed in Linux to break into a system would make the most sense.

Think of any bank vault, or any other secure place, and it is never a question of whether you can get in or not, it is a question of what tools are available how much time you have.  With the right tools, and sufficient time, the vault will be penetated.  A simple tool might be just to know the combination, and for this, people are sometimes taken prisoner and forced to open it for you.

People that focus on security issues are the wrong people for the job.  They only think in terms of how the systems in place are beyond penetration.  What they need to be doing is begin thinking like a thief, of how they would get into the system themselves. That should be their only focus and interest, and when they work out a way in, then that is when they should start thinking about how to stop it.  Then they go back to breaking in again.  Some successful penetrators that have been caught and punished were brought over because this is the way they think to start with, of how to break in or get pass all blocks.

Linux is just plain vulnerable, just as Windows and the MacOS are.  You really need security, then start over from scratch and do everything differently, Your weakness then is that you still have to document and train users and support staff, and people eventually leave the job, but still have both knowledge in their heads and all sorts of job souvenirs like books, charts, and diagrams.  How are you going to keep all those out of the wrong hands?  In other words, security is likely to decline in its effectiveness as time passes, especially as people depart, but the people within become ever more complacent as time passes as well.

Ideas like "don't make LiveCDs" or "rid the system of BIOSes that allow CD or USB device boots" may seem reasonable to you, but PCs themselves are significant points of vulnerability in many ways.  They can be opened up, modified and added to, and rendered unsecure in the process.  To prevent this, monitoring and logging of the workspace and PC access are sometimes employed.  Lock and Key are also rules of the day, with attention given to thumbprint readers, retna scanners, voice analyzers, and so on.  But if there is anything in the universe to put less trust in than another human being, I don't know what it is.  As long as people are in the equation, nothing is certain when it comes to what is truly secure. 

Yet then you need someone to be observant in the monitoring and very attentive to the details presented in the logs created, and these can be extensive in size and scope. Plus, logs are merely written records of something happening and can be modified themselves, and the details changed or eliminated.  Besides, what gets written is only a reflection of the fact that something happened, but does not really tell us what caused it. Thus, no easy task to interpret and understand, made harder by the fact that humans tire and lose interest quickly and easily, so monitoring and logging are no guarantees of heightened security.

Now if you want to discuss or argue over such matters, that is fine.  But attention to security was a significant part of my career, and I think it fair to say that I have a rather reasonable grasp on the subject.  I relate a bank vault as something akin to an attempt at a software block, firewall, or intercession involving a password.  This would be like hiding behind or inside something that protects it.  This equates to a form of cover in military terms.

Concealment or cmmoflage would then be similar to requiring some intimate knowledge what is in the system, what it does, how it does it, how it is used, whom makes use of it, the role it plays in things, the way or ways in, the passwords required, the commands available, what protection points to avoid, how to circumvent monitoring and logging, and a rift of other things.I may not have all that, but if the system software and hardware is not unlike my own, then I have a head start.  

Hackers have found that they can monitor connection points to see if someone logs in and get the userid and password used, and even what that person does while on the system.  Much of this looking on adds to our ability to do this yourselves after they leave.  But if we could not read the code and recognize what was happening and how, we would in effect only perceive noise, and our observations would be useless to
us at that point.

I mean this topic could be expounded on forever, like switch to a different human languge or employ encryption.  People have to be able to use this stuff, you know, so those options can be quite limited.

These are just points of discussion anyway.  People will do what they will do, or they won't.  I can point out what I see as some significant inhibitors, but that does not stop anyone from going their own way when the time comes.  Lots of businesses do not need any significant degree of security in the first place.

---

