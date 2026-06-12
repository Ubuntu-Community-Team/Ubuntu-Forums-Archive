---
title: "How long did it take you to get used to Linux your first time?"
date: 2011-07-21
forum: The Cafe
---

### Post by mnwolftrack on 2011-07-21
Hello--I'm brand new to Linux as of yesterday, and my first experience is with Ubuntu 11.04 server.  

How long did it take you get comfortable with Linux in general, from a server-management point of view (meaning not just any distro)?  I'm quite used to managing a network of Windows desktops and servers, and had my Linux "humbling" experience yesterday when I attempted to install Ubuntu 11.04 server and realized that my previous Windows experience meant nothing--now that I have to unlearn everything I thought I knew and start over.  As an example, I had no idea Ubuntu server edition was GUI-less, for starters.  It's taken me a day and a half just to get 11.04 installed, Samba possibly installed, and I'm trying to connect with Webmin  so I can have some sort of GUI interface for now (but it's not working due to access denied messages in my browser).  All I want to do is set up this server as a file server, but I have to copy over 100,000+ files from the old Windows machine and have file permissions to deal with on all those files/folders for approximately 100 users.  

My intent was to be able to start building and using Linux machines because I'm sick and tired of being a slave to Micorosoft, dealing with viruses, 9000 patches, over complexity, and all the licensing nonsense that goes on.  Mind you, I wasn't expecting Linux to be a Windows clone (and yes I've read the "accidental troll post etc...), but this was such a 180 from what I am used to, I'm not even sure where to begin or verify if I am doing it right.  I've only posted one other question on this forum thus far and haven't had a response yet (I'm quite familiar with using forums in general, just not a Linux-based one).  

I don't know how long this (learning Linux) could take me to figure out, and I don't know if I can dedicate that much time just to get a file server set up.  Mind you, I'm not complaining about Linux at all--it's so very different from what I'm used to that I don't know what to do now.  It would almost seem easier to learn this had I knew very little (or nothing) about computers at all.  

Thus, I request to poll other users on what it took for you to jump from a Microsoft World to a Linux world (including if you still have to use a mixed environment which is what I will have to do anyway).  I hate to think I'm "too far down the other path" to be able to teach an old dog new tricks.

---

### Post by ruffEdgz on 2011-07-21
Depending on how much you are willing to learn and adjust to a GUI-less environment like Ubuntu XX.XX Server, I think months would be a good guess. 

I didn't really start using Linux until my first job in 2008. At first is was a bit hard but I caught on in a month or so (I used other Linux distros in the past but always GUI based). Understanding your environment, reading the materials that will help you and retaining that information is key (like most things in life).

Linux books I enjoyed reading:
----
[Linux in a Nutshell](http://books.google.com/books?id=gBG7z8smAcsC&printsec=frontcover&dq=linux&hl=en&ei=UH0oTo6YOKLCsQLkzaE7&sa=X&oi=book_result&ct=result&resnum=1&ved=0CCkQ6AEwAA#v=onepage&q&f=false)
[Pro Linux System Administration](http://books.google.com/books?id=BKn8mfYGfcAC&printsec=frontcover&dq=linux+administration&hl=en&ei=0n0oTtiPKa7DsQLKoZ07&sa=X&oi=book_result&ct=result&resnum=5&sqi=2&ved=0CE4Q6AEwBA#v=onepage&q&f=false)
[Essential system administration](http://books.google.com/books?id=uRW8V9QOL7YC&printsec=frontcover&dq=system+administration&hl=en&ei=L34oTsrQMu2EsALY46U7&sa=X&oi=book_result&ct=result&resnum=1&sqi=2&ved=0CDcQ6AEwAA#v=onepage&q&f=false)

Welcome to the forum and best of luck!

---

### Post by schnelle02 on 2011-07-21
Hello.  I am fairly new to Linux also, as I have experience with the ubuntu desktop but recently at my internship I have needed to install Ubuntu Server 10.04(long time support) as well as the LAMP framework, SSH, and webmin.  Therefore I would imagine I could help you get webmin up and running.  If you are getting access denied messages then I suspect you didn't install the SSH package to allow remote access.  Please give me some more details on your installation process so I can help.

---

### Post by mnwolftrack on 2011-07-21
[ruffEdgz]("http://ubuntuforums.org/member.php?u=147600")--thanks for the book links.  Two of them are over 800 pagea a piece--looks like I could be reading for a long time.  I think my hopes of getting a file server built in a week is a dead dream.  I'm sure it's completely do-able for someone in the know, but I'm at a hinderance being knowledgable with Windows.

Schnelle02--I'm not sure where to start.  I did have issues with SSH and finding out it wasn't installed, and then the service wasn't running (so I started it), but it still doesn't seem to be working.  I just barely learned how to search through available packages with "SSH" in the name that I'm not even sure I installed the right one (but it was called ssh).  I typed:
 
sudo apt-get install openssh-server

and a bunch of stuff zipped by on the screen.  I saw some error messages regarding things being missing, so I found some other article on teh internet about installing those missing things just by doing another sudo apt-get and naming the missing items, but it still didn't seem to work.  Then I noticed a message within the console notes itself something to the effecdt of running subo apt-get -f (or /f) I don't remember, but then SSH seemed to finish installing (along with those missing dependencies).  Then I had to learn about "PuTTY" and took me a while to figure out that PuTTY wasn't working because the SSH service wasn't running.  I didn't do the "windows" standard of restarting the server, but I googled and found some other command on how to query if ssh is installed, if the service is running, and another google search on how to turn the service on.  

Prior to this, I was able to go to a browser and successfully get a login screen at [https://my.ip.address:100000/](https://my.ip.address:100000/), but I was getting access denied messages, and I apparently tried too many times because I got new messages saying my own work station IP address has been blocked now.  But, I waited about 10 minutes, tried again, and it seems it will at least attempt to let me log in again.  That being said, I do not recall ever being asked to make any user names or passwords during any of this process (install of Ubuntu 11.04 server, Samba, Webmin, etc...) OTHER than the initial setup of Ubuntu when it asked for a user.  So, I have only 1 user name and password for this server.  It never asked me to create a ROOT login or password (it was my impression after more research that the ROOT is disabled by default in Ubuntu???).  

You mentioned LAMP, and I *think* I won't need that because I'm not trying to build a web server (didn't even know what LAMP was 2 days ago).  

I'm sorry, I have probably not taken very good "notes" of my entire installation process.  This is partially becuase I hit a stumbling block at every single little thing, from not getting how to type commands, the syntax of them, the meanings of them, etc.... to finding for every ONE new thing I have to learn in order to move foward actually requires learning 5 other things first (and so on....).   I could just as easily wipe out the drive and start over again.  As my only other post on this forum goes, I'm not even sure if I have RAID 10 set up right....  In order to get Webmin installed, I had been following another (lengthy) online tutorial, but I just didn't seem to have the same results as the author of the procedure.  That, and they seemed to install other things (apache etc..) that I just plain didn't seem to need given I am only building a file server, so I *skipped" a few seemingly unnecessary parts.  And I am only trying to use Webmin to help ease my pain of trying to get this server set up.  Perhaps Webmin is not even the right solution?  The harder I try to set this server up, the dumber I feel.  

As the saying goes: I'm fluent in every language but Greek, and this is Greek to me.....

---

### Post by schnelle02 on 2011-07-21
You are correct LAMP is for web servers, for some reason I thought I read that in the initial post.  Plus webmin is a tool for running a web server, which is why the tutorials probalby had you install apache, php, and mysql.  If you just want to use it as a fileserver and you have SSH running then I would suggest just using an FTP client like winscp and remotely accessing the server storage.  Ubuntu is set up to not have a root user and to prompt for a password everytime you install something.  I find that annoying and you can change this....type ```
<snip>
``` then type your current passwd 3 times unless you want to change it.  now type ```
exit
``` and sign in as root.  Now you are the root user.

---

### Post by cariboo on 2011-07-21
This isn't a support question moved to the Cafe.

---

### Post by mnwolftrack on 2011-07-21
So my post regarding getting up to speed with a Linux server OS (and possible ways to do it best when coming from a Windows environment) is not "support related" and fits in better in a water cooler sub forum with topics such as what's in your backpack, UFO's in London, and other worldly news?

---

### Post by GSF1200S on 2011-07-21
Probably about 2 weeks until I was comfortable in the desktop environment/filesystem structure, a few months before I didnt fear losing the X server, and about 6 months until I willingly would mess with things it probably wasnt a good idea to mess with..

---

### Post by Linuxratty on 2011-07-21
Three days. I ran it for three days,then asked myself why I was still using Windows and paved over Windows.

---

### Post by cariboo on 2011-07-21
> **mnwolftrack said:**
> So my post regarding getting up to speed with a Linux server OS (and possible ways to do it best when coming from a Windows environment) is not "support related" and fits in better in a water cooler sub forum with topics such as what's in your backpack, UFO's in London, and other worldly news?

You didn't ask any specific support questions, so it does fit better here then in the server platforms sub-forum.

I would suggest you put off your server migration for at least 6 months, to give yourself time to get used to the server version. 

It may be an idea to install the desktop version, then add the server components you need, if all you want is a file server, all you really need is samba and ssh, that way you can have the best of both worlds, until you are ready to deploy your server.

I'd suggest you have a look at the [server guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html"), although it is for 8.04, the only real changes in the past several years is the ability to create a cloud server, so the document is still relevant.

**Edit** Seeing as I edited the post above here instructing the op how to enable the root account, I'd suggest you read the [RootSudo ]("https://help.ubuntu.com/community/RootSudo")howto.

---

### Post by Irihapeti on 2011-07-21
> **mnwolftrack said:**
> I hate to think I'm "too far down the other path" to be able to teach an old dog new tricks.

No one is too old to learn, unless they decide they are. (says she who is old enough to be a grandmother)

But, like others say, take it slowly and carefully and make sure you have working choices. Good backups always help, too.

It probably took me a month before I felt comfortable with it. It took another month before I plucked up the courage to delete my Windows partition.

---

### Post by 3Miro on 2011-07-21
I took a class in system administration on Linux, so after a semester I didn't know everything, but I had all the skills needed to figure out anything that I needed to.

---

### Post by Dustin2128 on 2011-07-21
Took me less than a week to learn the ins and outs of the desktop edition GUI. Gradually learned CLI from fixing problems and curiosity over a few months, so that by the time I set up my first ubuntu server, I could navigate the command line with my eyes closed. But I'm sure if I had been dedicated, it would have taken less than a week.

---

### Post by kaldor on 2011-07-21
Adjusting to Ubuntu 7.10 was very easy for me. Within a short time of trying Linux, I switched entirely. That said, I was not computer savvy at all. After about a year of using Ubuntu, I started trying more advanced stuff with it. 

By the time I was on 8.10 I was using the terminal more than the GUI for most tasks. Thanks to learning that, I can easily remotely administer a FreeBSD server and a RHEL 4.x server and work with SSH and Samba on a local network. It took a bit of research, but overall it's easy if you want to do it. These days, after using Linux for more than 3 years, I am pretty competent with it. 

My newest computer is a Win7 dual boot (needed it for college course :( ) and I really took Linux for granted. I feel very out of place without being able to access a package manager and other similar things.

I've never used Windows server, so I have nothing to compare to.

Basically, it's not hard at all if you actually want to learn.

Edit: After re-reading the original post, I have a couple of comments/suggestions.
- Install Linux on one of your own computers and force yourself to use it for your day to day stuff, and use the Terminal (Ubuntu is very GUI driven) as much as you can. Instead of right-clicking to make a new folder, use *mkdir FolderName*

- For servers, try to stick to the "LTS" releases. Every 2 years a new Long Term Support release of Ubuntu comes out which gets 5 years of support. They also tend to be more stable than the usual releases. The current LTS is 10.04 "Lucid Lynx"

- Try CentOS. It's a free clone of Red Hat Enterprise Linux, and it (CentOS and Red Hat) are used in a very large number of web servers so it's a good skill to have.

---

### Post by BrokenKingpin on 2011-07-21
I found to get use to it I had to use it exclusively for about a month... now I wouldn't consider using anything else.

---

### Post by Rasa1111 on 2011-07-21
When I first got my Ubuntu disc in the mail, (Ubuntu 9.10)
I ran from the CD for almost a week, Just to get a feel for it.
About 5-6 days after running from the CD, I felt comfortable enough to wipe windows and do a full install.
 Using nothing but Ubuntu ever since.

---

### Post by Bandit on 2011-07-21
When I started using linux it was on Slackware 7.0.
Being that I was still on dial up at the time and couldnt download any other distros, I basically had to learn that distro on my own. But I had two separate systems luckly and was able to look up how to setup my Xserver XFree86 and program the mode lines to get my monitor showing like it should.
Although I had the basics down the first 3 months, if I did anything that totally messed booting up, I had to reinstall. That was back in 1998, 13 years later I still learn new things *almost* everyday ;-)

---

### Post by Old_Grey_Wolf on 2011-07-21
If all you need is a basic file server, that will not take very long to learn and set up. I have used Linux/UNIX for a long time so I can't give a time estimate for learning the Linux command line interface.

If you need to have user assess controls and authentication integrated with Windows Active Directory and that sort of thing; then, it could take months depending on the time you can devote to searching and trying solutions. For example, LDAP is not as straight forward to set up as Active Directory, and integrating LDAP and Active Directory using 389 is something you will probably not find help with on this forum. 

I would not use the 11.04 release for a company server because it is not a Long Term Support (LTS) release. It is only supported for 18 months. If you use 11.04 you will have to either attempt to upgrade to the next 6 month release 11.10 after 6 months, try to upgrade through every 6 month release until you get to the current release after 18 months (10.04 -> 10.10 -> 11.04 -> 12.04), or installing the current release and try to recreate your configuration. With the modifications you may have to make to the system for enterprise use, an upgrade without a reinstall is probably not going to work. For servers, most people use the LTS releases. You only need to reinstall the LTS releases every 3 years; however, there is an advantage for doing it every 2 years. The server releases are supported for 5 years; however, I really don't know what the upgrade policies are, and I can't imagine using 5 year old applications even when they get security patches. The documentation about the server 5 year support is not clear; therefore, I upgrade at each LTS release. The 10.04 (April 2010) release will be supported until the 13.04 (April 2013) release. You should upgrade/reinstall at 12.04 (April 2012), or 2 years after release of 10.04; because, 12.04 is an LTS and 13.04 is not. After 12.04 is installed and configured I would not reinstall and configure again until 14.04 (April 2014). You do have the option of trying to upgrade from an LTS to the next LTS without reinstalling or upgrading to every 6 month release in-between the two; however, with the modifications you will probably make, it is unlikely that an upgrade would work successfully. Note that odd-year April releases are not LTS releases and October releases are never LTS, only even-year April releases are LTS. 10.04, 12.04, and 14.04 will be LTS; however, 10.10, 11.04, 11.10, 12.10, 13.04, and 13.10 are not LTS. I hope I have not confused you with this explanation of releases versus LTS :)

I use 10.04; therefore, this paragraph applies to 10.04. You can install a GUI on the server version if you like. You can Google for the instructions. To install a GUI you need an Internet connection and type a command in the terminal; such as, "sudo apt-get install [*desktop_name*]". To install the GNOME desktop it is "sudo apt-get install ubuntu-desktop" and for XFCE it is "sudo apt-get install xubuntu-desktop". The server editions don't have a GUI in order to conserve resources that could be used by the server processes and security considerations. If your server has enough compute, memory, etc., resources and no security concerns then you can install a GUI if that helps you manage your server.

---

### Post by era86 on 2011-07-21
A day to get it installed (painful).  A week to get it configured (sound, wireless, and mouse).  A full year to get comfortable with the tools I use now (though this is ongoing as I explore new applications).

TBH, I've been getting used to Linux since 2005...:popcorn:

---

### Post by Gawains Green Knight on 2011-07-21
I agree with the earlier post - install the regular desktop and then add the bits you need. I've used unix/linux for a while, but I only recently set up my own server - took an afternoon - it was relatively easy and just involved lots of searching this forum!

---

### Post by Khakilang on 2011-07-21
For basic usage, it took me less than a week. It was 8.10 back than. The GUI is pretty friendly and easy to navigate.

---

### Post by Lupi on 2011-07-22
My "first" was 8.04. It took me about 2 days to get used to it and 6 months to stop dual-booting.

---

### Post by nothingspecial on 2011-07-22
My first computer came with linux on it so I didn't have a problem ......

.....well I had lots of them, but none as a result of being familiar to windows

What are you actually trying to do?

---

### Post by Brandel Valico on 2011-07-22
I'd say about a week for common day to day roughly 1-6 months for less common uses.

Also you can add a GUI to your server if you prefer and are willing to give up the space on the drive

sudo "apt-get install ubuntu-desktop" Without the " symbols of course. should still get it installed. Been a few years since I set up a server and added a GUI to it. They may have changed the command. If so someone will tell you. Either way always check any command you don't know before running it.

Heres a bit of info

> [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by nothingspecial on 2011-07-22
> **Brandel Valico said:**
> "apt-get install ubuntu-desktop"

That will give you a full blown ubuntu system, probably, I'd think not what you want.

Stick with the cli. Have a look at screen or byobu. They will allow you to open multiple "windows", split your screen, copy and paste etc

---

### Post by Thewhistlingwind on 2011-07-22
To be conservative, a month, but that was for the desktop. 

While I agree with "Install a GUI" I don't think you want the full blown ubuntu setup. "ubuntu-desktop" gives you that, and I'm pretty sure theres ones in repos that are just the barebones DE's.

Also, I have to echo "Use the LTS (Long term stable.)" if your running a home server constant upgrades are fine, this is not true when your server is going down on more than just your time.

---

### Post by YesWeCan on 2011-07-22
> **mnwolftrack said:**
> Thus, I request to poll other users on what it took for you to jump from a Microsoft World to a Linux world (including if you still have to use a mixed environment which is what I will have to do anyway).  I hate to think I'm &quot;too far down the other path&quot; to be able to teach an old dog new tricks.
Time, lots of time
Tolerance
Lots and lots of web searches

I started with 9.04. My first impressions of linux:
it's free 
it puts me back in control of my PC 
it's got lots of potential 
it's buggy 
it's incoherent (a patchwork quilt of applications of variable quality and usability) 
it's extremely poorly documented 
it's old-fashioned 
it is a pain in the butt to figure out how to do anything non-trivial 
Web forums are essential resources.  

It took me 2 months to transition from "I cannot afford this free OS" to "I may be able to use this OS for something serious" and I am a technical professional.   I am now a seasoned user so I am already forgetting how hard it is to learn. I imagine 11.04 is a little easier for a beginner than 9.04 but I think you should expect it to be heavy going at first. Allow lots of time. Try not to get too frustrated by its eccentricities. And do not be put off by respondents on forums who make you feel stupid by claiming linux is the easiest and most reliable OS on planet Earth - just ignore them.  Once you are a seasoned user you will appreciate its versatility and the control you have over it.

---

### Post by koenn on 2011-07-22
getting used to a CLI-based server ? I'd say a couple of weeks to a couple of months, depending on how you go about it (as in: if you spend just an afternoon of trial and error every weekend or so it's going to take longer than when you systematically learn and practice every day)

to confidently run a production server, count on ~6 months to 1 year, since you both need to learn how to set stuff up and  develop a feel for diagnosing and troubleshooting. (do you know where the log files are and how to search through them ?)

otoh, linux servers are pretty simple :  once you know how to install software and realize that configuration is done by editing text files in the /etc directory, you can admin a server. 

At that point, you might find that without the handholding of dialog boxes and wizards, you have no idea how to configure that software. That's an indication that you've learned (a Windows-specific way of) *how* to accomplish a given task, and that you lack understanding of *what* you're doing. Learning those underlying concepts is an important factor in how much time it'll take to "get used to linux". 
It will also make you a better sysadmin. 



Here's some stuff you can use to get your hands dirty :
[http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm)
[http://users.telenet.be/mydotcom/howto/linux/index.htm](http://users.telenet.be/mydotcom/howto/linux/index.htm)

some of it is a bit outdated and most of it refers to Debian rather than Ubuntu, but learning to deal with that and making abstraction of OS and version specific issues is part of the exercise :)

---

### Post by mnwolftrack on 2011-07-22
Wow--lots of excellent responses!  Overall, it appears I should back out of my original plans of expecting to get a Linux server in production mode in a business environment (as a file server, hopefully using Active Directory-like permissions) in a week or so.  Instead, I should probably put Windows on this server (ugh), but use the old server as my Linux test machine and work with that until I am ready to go into production with something.

Honestly, my initial expectations were--how bad can it be?  I run a business network of Windows and have a good knowledge base to work with.  Oops--just found out it meant nothing!  

While I can still say I know nothing of Linux, I do think I can see a shred of light about it being easier to use than Windows.  I haven't actually said I found Linux "hard."  It's just COMPLETELY DIFFERENT (not necessarily hard).  

Believe me, I'm wanting to make the switch for a reason (and I'm sure is the same reason many of you switched already).  Windows is simply a bloated, complicated, and expensive choice.  Windows is only "easy" because it's all I know and I'm used to it.

As for my project:

This is to a be a file server in a small business of slightly less than 100 desktops, approximately a dozen servers, with Active Directory managing everything at this point.  One of the existing servers is a file server with 100,000+ thousand shared Word, Excel, PDF, and other typical business docs.  All employees have a main mapped drive to see all directories, directories are split by department (along with employee type), and sub folders/files are split up underneath this.  File permissions is complicated and not "straight across the board."  There's just no good way to do it that I can figure out, as there are all kinds of docs that are shared between different depts. but not necessarily to all employees within the same dept. (meaning employee A and employee B in dept. ABC won't have access to all of the exact same files).  All employees also have a second mapped drive to their personal folder, though the personal folders are still saved under the same structure as previously mentioned (the mapped drive to the personal folder is basically just a short cut for them).  

It looks like I should start a new thread back in the server forum regarding getting help setting up a file server, though I will need to be a little careful how I do this because I don't think this project is something that can be answered in one single thread (so I will likely have to create more as I go on).  But, to at least get the wheels rolling, I should start the main thread.  Everything I've researched thus far says I should use Ubuntu Server edition with Samba, or Red Hat Enterprise Edition.  I picked Ubu because there were no paid commitments for me to start learning.  That, and it seems to have such a strong following anyway.  

Thanks for everyone's feedback!  I feel better about being ridiculously overwhelmed!

---

### Post by Old_Grey_Wolf on 2011-07-22
> **mnwolftrack said:**
> ...Instead, I should probably put Windows on this server (ugh), but use the old server as my Linux test machine and work with that until I am ready to go into production with something...

That looks like a good plan. This link to LDAP 389 may help with LDAP and Windows Active Directory integration [http://directory.fedoraproject.org/](http://directory.fedoraproject.org/). There is information in the site's documentation for Active Directory synchronization with LDAP.

You might want to consider using CentOS 6 (RHEL 6 with branding removed) for this as it will not require compiling 389 from source code and it is free [http://www.centos.org/](http://www.centos.org/). On that page scroll down to "CentOS 6 Releases" and click on "Download: i386 | x86_64" to download the version you need.

I hope this helps you.

---

### Post by Carterclan on 2011-07-22
I ran a live cd for about 30mins. I love learning new stuff so for me it was a no brainer. I backed up then installed wiping windows of the face of the earth. Have never looked back and would never want to.

---

### Post by koenn on 2011-07-22
> **Old_Gray_Wolf said:**
> That looks like a good plan. This link to LDAP 389 may help with LDAP and Windows Active Directory integration [http://directory.fedoraproject.org/](http://directory.fedoraproject.org/). There is information in the site's documentation for Active Directory synchronization with LDAP.

the OP probably doesn't need a (2nd) LDAP server.
SAMBA + POSIX ACL + letting samba get user accounts and groups from Active Directory should be sufficient.

---

### Post by Old_Grey_Wolf on 2011-07-22
> **koenn said:**
> the OP probably doesn't need a (2nd) LDAP server.
SAMBA + POSIX ACL + letting samba get user accounts and groups from Active Directory should be sufficient.

Yes, SAMBA may be all the OP needs. 

Here is the SAMBA and Active Directory integration web page [http://wiki.samba.org/index.php/Samba_&_Active_Directory](http://wiki.samba.org/index.php/Samba_&_Active_Directory). The OP can read it to determine if it satisfies the need.

Edit: OP, as I said in my first post, "If you need to have user assess controls and authentication integrated with Windows Active Directory and that sort of thing; then, it could take months depending on the time you can devote to searching and trying solutions." You are already getting alternate solutions suggested that you will have to research and test.

---

### Post by Old_Grey_Wolf on 2011-07-22
This thread doesn't really seem like it should be in the Community Cafe. It seems like it should be in one of the Support Forums where it can get more technical solutions offered. Maybe one of the mods will move it to a more appropriate place.

---

### Post by mnwolftrack on 2011-07-22
I agree, which is why I had posted it in the Server forum to begin with.  But apparently my thread has more in common with UFO's than it does with server support and was moved here.  What do I know?

---

### Post by silex89 on 2011-07-22
When I first started with Ubuntu Breezy, it took me like a month or two to learn how to use it, mostly because at the time the console orders were much more required to configure the OS than today. I remember this:

```
sudo dpkg --reconfigure xserver-xorg
```

I needed that command to adjust my screen resolution to 1024x768 :D

Regards :)

---

### Post by Old_Grey_Wolf on 2011-07-22
> **mnwolftrack said:**
> I agree, which is why I had posted it in the Server forum to begin with.  But apparently my thread has more in common with UFO's than it does with server support and was moved here.  What do I know?

It may get moved again :)

---

### Post by cariboo on 2011-07-22
I would suggest if the op has specific questions about servers, he start a new thread in [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339")

---

### Post by Lucradia on 2011-07-22
I did not have any linux background before I first started using my first linux distribution (SimplyMEPIS) and it was quicker to learn than Windows after I had switched to Windows from MacOS 9.

---

### Post by uRock on 2011-07-23
> **mnwolftrack said:**
> How long did it take you get comfortable with Linux in general, from a server-management point of view (meaning not just any distro)?

> **Old_Gray_Wolf said:**
> This thread doesn't really seem like it should be in the Community Cafe. It seems like it should be in one of the Support Forums where it can get more technical solutions offered. Maybe one of the mods will move it to a more appropriate place.

> **mnwolftrack said:**
> I agree, which is why I had posted it in the Server forum to begin with.  But apparently my thread has more in common with UFO's than it does with server support and was moved here.  What do I know?

The original post had one question within it, which was not a support question. :)

---

### Post by nothingspecial on 2011-07-23
> **cariboo907 said:**
> I would suggest if the op has specific questions about servers, he start a new thread in [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339")

Here it is 

[http://ubuntuforums.org/showthread.php?t=1808470](http://ubuntuforums.org/showthread.php?t=1808470)

if anyone feels like answering.

---

