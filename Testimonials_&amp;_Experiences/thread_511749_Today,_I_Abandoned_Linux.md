---
title: "Today, I Abandoned Linux"
date: 2007-07-28
forum: Testimonials &amp; Experiences
---

### Post by eob on 2007-07-28
Don't get me wrong, I'm a huge fan of Open Source software (see here:[http://www.octane.ie/forum/showthread.php?t=6543&highlight=octane+server](http://www.octane.ie/forum/showthread.php?t=6543&highlight=octane+server)) and the Linux project, my one big enemy, however, is time.

I'm a web monkey by trade, I mess around with PHP & MySQL and get paid handsomely for it, so I decided it was time to bite the bullet and get a full-fat Linux server in the form of Ubuntu on one machine, and Puppy on the other.

I was super impressed, happy, and the end result looked uber-cool.. 

Then last week my webhost went t!ts up, and I had to spend an entire week moving websites from one place to another obnly to discover that my sites wouldn't work with suPHP, only full fat PHP. So I spent another week recoding them.

So you can imagine how exhausted I was sitting down last night at 1am and discovering Ubuntu needed to be updated. Easy, I thought, click the Ubuntu icon in the corner. It froze, something about SlapD backing itself up.

Sigh... I thought, reboot.

Ubuntu reboots. Sits there. MySQL and PHP now firmly dead. 

I spend until 2am trying to get Ubuntu to complete the update with no success. Googling, posting, sweating, crying. 

So in desperation, I swing my chair around and fire up my venerable Linux Puppy machine... only to discover that Apache (XAMPP) won't boot on that either. Something to do with MySQL not initialising. I do lots of forum reading and Googling... no answers to be found.

In frustration, I spin my chair back around to my old XP machine and in under 45 minutes I have IIS installed and running with PHP and MySQL. 

I now have one machine to back-up, not three.
I now have one machine running in my office, not three.
I now have everything I need on a single machine.

I really, really feel cheated. I've done so much talking to other nerds (some of whom work for Microsoft) about the benefits of Linux, about how it brings new life to old machines, about how it's sexy, about how it's free, about how it's climbing the corporate ladder and taking over the world.

And now, I'm about to drop my two Linux machines off at the recycling center.

I know most people will say 'It's just bad luck' but I'm not really convinced.

---

### Post by PriceChild on 2007-07-28
Ok... well at some point they were working... and then at the next point they weren't.

This doesn't happen without you doing something inbetween.

I think its a bit excessive to be trashing two machines just because you broke the operating system? Why not install good old windows xp on them and use them for something useful? :D

---

### Post by eob on 2007-07-28
The grand total of my involvement with Ubuntu was to click the 'You Have Updates' button in the top left :) Puppy is a bit more involved, and I'm far more forgiving of Puppy because I rather like it, and it hasn't got the resources to work with AND it was installed on an excessively elderly machine which shouldn't be entrusted to run MySQL/Apache anyway :)

My history with Linux is rather chequered. Everytime I try to make the leap, the software lets me down.

The first time I went with RedHat it was on an old P120, installed fine, but couldn't really do anything with it (I was about 16)

Second time round I installed Fedora on a Dell Latitude laptop, blithely unaware that the Latitude had a software controlled CPU fan which Fedora didn't support = I melted processor (only time I've ever had an OS actually physically harm a system).

My passion for open source was re-ignited by all the hype surrounding Ubuntu, but when you're short on time, and something as simple as an update thrashes your entire LAMP configuration, one which took a days work to figure out, then that passion tends to burn out and you can install IIS in under 45 minutes.

I have nothing against Linux, I'm all for it, but it's safe to say that the next time I go Linux, it will be as a toy, not as a serious OS.

---

### Post by toupeiro on 2007-07-28
I'm sorry to hear you had a bad experience, but coming from someone that has been an IIS admin since Micro$oft created it, let me tell you that you aren't doing yourself any service by abandoning linux/Apache.  Due to this incident, you would be choosing a web service/O.S. riddled with vulnerabilities, is completely bloated when it comes to code, and can crash for much less of a cause than what you experienced here.  While I think Server 2k3 was the best thing MS has done in years, it still can't maintain the uptimes linux can for the type of work you do.  Also be aware that system configurations are intended to be backed up before upgrades, because upgrades or patches do have the potential to reset configuration.  Microsoft products are not exempt from this in ANY way, shape, or form, trust me!  This isn't just with operating systems and apps though, if you have ever flashed a BIOS on your PC, then you should remember how all those factory settings come back into the spotlight. :-)  If you don't have a backup solution for ubuntu already, I recommend sbackup.  Its very easy to configure, has a nice crontab frontend if you are not comfortable with crontabs for scheduling,  has a good mechanism for purging old backups if desired,  and can dump backups via FTP or SSH if you do not have an external disk or tape drive. (sudo apt-get install sbackup)

 I used to maintain a online banking website and applications backend that on a low average would get 600,000 hits a month.  The Server 2003 boxes were being hammered, and most of it was internal windows churning.  More and more, it becomes more apparent to me that Windows is the toy.  A toy whose owners keep sewing the arms back on and changes its clothing every few years but at the core, its the same old thing.

---

### Post by ticopelp on 2007-07-28
Sorry to hear it. I'm also a webmonkey by trade, and I've been using Apache / PHP / MySQL for months on Linux without any problem. I haven't used IIS in probably a decade, and man, did that piece of software suck. So my sympathies to you on that account. 

I don't use XAMPP, though, as I find it's not the most reliable piece of software in the world. This guide was a godsend: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server)

Frankly, setting up and maintaining Apache / Mysql / PHP on a LInux machine is ten times easier than doing so on Windows. Windows requires copying DLLs, editing the .conf files, and for me, using the most insecure options possible and pray you don't get pwned (I could only ever run PHP as a CGI process, which the readme explicility tells you is a bad idea). With Ubuntu it was:

> 
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart
sudo apt-get install mysql-server
sudo apt-get install phpmyadmin


Boom. Done. You're up and running. And in a lot less than 45 minutes.

I always find stories like this curious -- I feel like I ought to be having more problems than I do. I have a custom-built machine with hardware from every part of the world, I install new software and play around with settings constantly, and while I know my way around the command line, I'm no expert -- if Linux is so unstable and nutty I should be bricking my machine twice a week. Yet I manage to do all my work flawlessly on Linux, and have been doing so for months. 

Again, sorry to hear that it didn't work out for you, and I definitely understand your frustration, as I've felt the same frustration myself -- trying to use Apache etc. on Windows. :KS

---

### Post by wolfen69 on 2007-07-28
> **eob said:**
> The grand total of my involvement with Ubuntu was to click the 'You Have Updates' button in the top left :) Puppy is a bit more involved, and I'm far more forgiving of Puppy because I rather like it, and it hasn't got the resources to work with AND it was installed on an excessively elderly machine which shouldn't be entrusted to run MySQL/Apache anyway :)

My history with Linux is rather chequered. Everytime I try to make the leap, the software lets me down.

The first time I went with RedHat it was on an old P120, installed fine, but couldn't really do anything with it (I was about 16)

[B]Second time round I installed Fedora on a Dell Latitude laptop, blithely unaware that the Latitude had a software controlled CPU fan which Fedora didn't support = I melted processor (only time I've ever had an OS actually physically harm a system).
[/B]
My passion for open source was re-ignited by all the hype surrounding Ubuntu, but when you're short on time, and something as simple as an update thrashes your entire LAMP configuration, one which took a days work to figure out, then that passion tends to burn out and you can install IIS in under 45 minutes.

I have nothing against Linux, I'm all for it, but it's safe to say that the next time I go Linux, it will be as a toy, not as a serious OS.

i dont mean to burst your bubble, but fedora melting your CPU is impossible. the fan is either on or off. sure, you can have cool n quiet, etc. but as a PC tech, i assure you that an OS isnt going to be responsible for a meltdown. cpu fans dont need "OS support" to work.

---

### Post by Hairy_Palms on 2007-07-28
wolfen69 beat me to the punch, if that was true and your fan only ran when the OS told it too, then your cpu would fry each time the power was on before the OS booted.

---

### Post by MrHippocampus on 2007-07-28
> 
i dont mean to burst your bubble, but fedora melting your CPU is impossible. the fan is either on or off. sure, you can have cool n quiet, etc. but as a PC tech, i assure you that an OS isnt going to be responsible for a meltdown. cpu fans dont need "OS support" to work.

Actually, some do, I know it sounds stupid but ive read about people having to create new DSDT's or patch the kernel for their laptop's ACPI in order to get the fans working. Here is a [bug report]("https://lists.ubuntu.com/archives/kernel-bugs/2005-December/007622.html") for such a problem.

edit: [here]("http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nx6325#The_important_first") is a page from the gentoo wiki for another laptop which is known to suffer from this.

---

### Post by PriceChild on 2007-07-28
If your CPU temp gets too high then the machine will shut down. Unless you disable this in the BIOS...

---

### Post by MrHippocampus on 2007-07-28
It should throttle itself too, im pretty sure throttling is done on the chip by itself.

---

### Post by eob on 2007-07-28
The dell I mentioned uses a passive heat duct with a fan as back-up. The fan is software activated, as HippoCampus pointed out. I was curious to the cause, as I couldn't believe an OS could actually kill a processor, so I brought it to a Linux genius who sleeps in a room with servers running on either size of his bed and he diagnosed the problem. 

I thought it was an interesting one.

I'm currently choosing between IIS and Apache on Windows? Any recommendations?

You have to remember I have nothing against Linux, I'm just someone with very limited time. I'm emphatically not one of those people who live to sit in on a Friday night messing with config files. I just want it to work, and if it doesn't work, I just want to be able to fix it in a few minutes. What I definitely don't want to do is spend a few hours I don't have to spare Googling to see what SlapD means.

I intend giving Ubuntu another shot for fun at some stage on a secondary hard drive in my main box to see if it works any better on a higher spec'd machine, and I certainly wouldn't mind installing Puppy for that odd time when you want to boot & surf at the speed of light.

I wish you all all the best in your Linux adventures! 

PS. Before you all go, it'd be nice to know what slapD is and why it's broken, for curiousity sake! :)

---

### Post by leftcase on 2007-07-28
eob,

Whilst I'm sorry to hear that you've decided to migrate away from Linux, I wonder if you've done it for the wrong reasons. Although I understand that you're a skilled web programmer, it doesn't sound like you're a experienced systems administrator.

Configuring a secure and functional apache, mysql and php environment on any operating system requires skill and knowledge. Installing a pre-built WAMP environment certainly won't give you a secure and functional environment out of the box on your Windows XP OS.

 I can only suggest that if you're hosting websites that are important to you, or charging people for that service, that you employ the services of an experienced Windows or Linux systems administrator to configure your hosting environment so that you can ensure security and uptime.

From the xampp FAQ:
[I]
"As mentioned before, XAMPP is not meant for production use but only for developers in a development environment. XAMPP is configured is to be as open as possible and to allow the web developer anything he/she wants. For development environments this is great but in a production environment it could be fatal."[/I]

Changing to IIS from Apache is also pretty fatal. Having administered IIS and apache servers (Win & Linux) myself, I can only suggest youv'e probably chosen the more difficult option of the two ;-) 

Cheers

Chris

---

### Post by eob on 2007-07-28
> Configuring a secure and functional apache, mysql and php environment on any operating system requires skill and knowledge. Installing a pre-built WAMP environment certainly won't give you a secure and functional environment out of the box on your Windows XP OS.

Because I come from a background of coding one site in particular which is built from the ground up by a whole bunch of volunteers, I was lucky enough to have two tech support guys with a combined experience of 30 years in Linux/Windows/Solaris/Sparc etc. The server we were running:

[http://www.octane.ie/about/thanks.php](http://www.octane.ie/about/thanks.php)

Was an absolute legend in our own little world because with such a blocky 80's laptop stacked on-end, some tech guys could be convinced that it was this new type of mad Linux blade server :D 

Hey, well, I thought it was funny!

I wrote long and lengthy pieces on Ubuntu and how great it was, now I feel like I've misled so many fupping people, that I've spent nights in posh blokes houses with who drive Ferrari's and work for MS, talking up something that's, at best, average.

I want Linuxs time to be now, and instead, I have to compose a guilty email tomorrow morning to the lot of them asking for IIS advice...

---

### Post by bonzodog on 2007-07-29
> **vwbeamer said:**
> Later, don't let the door hit ya, where the good lord split ya,

Linux is only for those who are cool, trendy and intelligent, so you're to big a dumbass to figure it out, later dude.

/me applies the LART

---

### Post by eob on 2007-07-29
Thanks BonzoDog, and apologies to any Linux fans I've offended with this thread.

Due to the fact that anyone who knows anything throws up their hands and says 'Jebus prist, noooo' when I mention anything to do with IIS, I just removed it and installed WAMP instead. Much better.

It also means avoiding asking MS employees for advice and, as a result, having to listen to a lot of 'I told you so'.

I've got a second SATA HDD en-route, so, I'm going to reinstall Ubuntu and Puppy with GRUB on that in my main dev machine which has a bit more power than the Compaq. I'm hoping this will mean a return to Linux, sadly, as a toy so I can show off what Beryl can do :( :( :(

---

### Post by leftcase on 2007-07-29
> **eob said:**
> Thanks BonzoDog, and apologies to any Linux fans I've offended with this thread.

Due to the fact that anyone who knows anything throws up their hands and says 'Jebus prist, noooo' when I mention anything to do with IIS, I just removed it and installed WAMP instead. Much better.

You'll save yourself headache in the long run, and hey - if you ever decide to come back to linux, the skills you'll  learn administering Apache on Windows are transferable :popcorn:

Good Luck.

---

