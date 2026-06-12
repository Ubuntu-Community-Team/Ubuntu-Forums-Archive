---
title: "I hate Linux"
date: 2008-04-04
forum: Testimonials &amp; Experiences
---

### Post by SteveHillier on 2008-04-04
No I don't really but I do dislike with a vengeance the way it does certain things.  My other posts have raised some of these issues.
I have spent the last 10 hours trying to install 2 packages and so far I have installed 1.
I have spoken to help desks on both occasions.  One HD in England and one in US (paid for phone call!).
The package I have got installed just now did so with no apparent problem after resolutely refusing to do anything earlier today.  I have now put it on a scheduled run and await the results.
The other is Plesk.  I wrote a post last night seeking help but I think I have suffered from wrong information.  Not from anyone on this forum so don't get aggrieved.
I was told that I needed to install qmail and courier-imap and BindDNS and spamassassin BEFORE trying to install Plesk.  
Their help desk now tells me that it should be installed on a clean server.  Not that their documentation says anything about it.  
Notes in one hand and keyboard in the other I ran the install process to the letter using defaults.  At the end I got this useful information
Some of the software packages have not been installed.  Your software may not run correctly.  Please call our contact centre.  Gee whiz, I can make a lot out from that.
I followed their advice and tried to reinstall make less progress than the first time.  I am now informed that any email server is likely to conflict with Plesk so in reality I should have done the install on a bland machine.
Now my criticism is not on Linux *per se*, nor even of Ubuntu, but if a program is trying to install and cannot do so because of missing files, conflicts, patches and packages not arriving then why don't we stop the install give a USEFUL message to the user.  That is something that those people at MS have got done better than ourselves.
At one point on the initial install of plesk progress stopped.  In the end I hit return to give it a nudge, and then got a message that it was expecting me to put the Gutsy CD in the drive.  No output telling me I had to do this.  No clue as to what it was trying to do.
If I as a user (and an experienced IT technician and user) have problems loading and sorting out an install what hope is there for the non-computer minded user who simply wants to load a new program.
Until we are able to make these sorts of processes more user friendly then this superior OS will never catch on.
Let's have installs that work.  Uninstalls that are intuitive.  Programs that appear in menus WHEN they load.  Downloads that complete and let you know where you have placed the file.  And sorry this is an Ubuntu issue - programs that when you install do not set up directories with ownership and permissions as "root" when "root" is not used.  For example the directory /tmp is set to "root" ownership, so I can't read an error log that is there unless I first change the access permissions but I can't do that until I change ownership of the directory, and I can't do that until I log on as root.  At the end of a day when nothing has gone right I don't feel like doing this.  I simply want to throw the whole lot out of the window (after first having smashed it with a 14lb hammer) and having a whinge on this forum.
Am I alone in wanting to see improvements in this area?
Good bye, and thanks but no fish today please.

---

### Post by pytheas22 on 2008-04-04
Installation and uninstallation in Ubuntu is very easy using the package management system.  I think that the "Add/Remove Software" utility that comes standard on Gnome is as intuitive as it can get, and the apt-get backend is really powerful if you're an administrator.

Of course, software like Plesk is a little harder to manage because it's not in the standard Ubuntu repositories.  But a quick search reveals that there are .deb packages built for it, so I don't think it should be that hard to install...just download the packages you need and double-click.  If Plesk offers all of them in a repository that you can add to your list, it makes things even easier.

I agree managing software in Linux for which no packages exist is a big hassle, since no one wants to compile stuff manually and remove it by hand.  But with popular distributions like Ubuntu, it's usually not hard to find pre-built packages for almost everything that can run on Linux.

The whole package management system also tends to make things safer.  Unlike in Windows, where you install software by downloading it from random places on the Internet, most of the packages in Ubuntu come from a centralized location that can be trusted (of course, this does not include Plesk, but it does include 95% of the software that any "non-technical" user would be dealing with).

And as far as file permissions go, there are important reasons that not everyone has access to /tmp, and it shouldn't be a problem to get the access you need by using sudo.

I can understand that Linux can be frustrating if you're approaching it from a Windows mindset--it was very obnoxious for me at first too,  But try to understand why things work the way they do and I think you'll appreciate it more.  And if you still have problems with your installation, ask about them in this forum, which in my experience is an excellent source of support, and better than most of the similar sites on the Internet filled with people who don't really know anything but think they're "technical" because they can point and click their way around the XP Control Panel.

---

### Post by utUtu on 2008-04-04
And you call yourself

**[COLOR="Red"]... (and an experienced IT technician and user)[/COLOR]**

:lolflag:

---

### Post by finferflu on 2008-04-04
I think you need to be aware that Linux applications are not Linux. Blame the application's developers rather than Linux. The messages you are looking for should have been provided by the application, and not by Linux. Linux is an OS, a base upon which people build stuff, which might or might not be very functional.

---

### Post by wolfen69 on 2008-04-04
> so I can't read an error log that is there unless I first change the access permissions but I can't do that until I change ownership of the directory,no need for that. just:
```
gksudo nautilus
```i havnt experienced any of the problems you have. ubuntu runs perfect for me. :guitar:

and this belongs in testimonials.

---

### Post by Lord Illidan on 2008-04-04
> **wolfen69 said:**
> no need for that. just:
```
gksudo nautilus
```i havnt experienced any of the problems you have. ubuntu runs perfect for me. :guitar:

I changed your command to gksudo, as it's safer for running GUI applications.

---

### Post by scarrabri on 2008-04-04
My Friend and i had a go at installing ubuntu ,will someone tell me that this is a joke,lol it has to be,we spent weeks getting nowhere,we got to the bit just after we put london in,and then it went looking for the hard drives ,now i know they are there and my friend knew his were there,then why the hell did ubuntu spend weeks looking for them,,my friend gave up after he  did get there in the end,which is a shame because i got mine going and i love it ,but ,what a difference it would make if it just worked,,best wishes scarrabri:lolflag::lolflag:

---

### Post by SteveHillier on 2008-04-04
> **pytheas22 said:**
> Installation and uninstallation in Ubuntu is very easy using the package management system.  I think that the "Add/Remove Software" utility that comes standard on Gnome is as intuitive as it can get, and the apt-get backend is really powerful if you're an administrator.

Of course, software like Plesk is a little harder to manage because it's not in the standard Ubuntu repositories.  But a quick search reveals that there are .deb packages built for it, so I don't think it should be that hard to install...just download the packages you need and double-click.  If Plesk offers all of them in a repository that you can add to your list, it makes things even easier.

I agree managing software in Linux for which no packages exist is a big hassle, since no one wants to compile stuff manually and remove it by hand.  But with popular distributions like Ubuntu, it's usually not hard to find pre-built packages for almost everything that can run on Linux.

The whole package management system also tends to make things safer.  Unlike in Windows, where you install software by downloading it from random places on the Internet, most of the packages in Ubuntu come from a centralized location that can be trusted (of course, this does not include Plesk, but it does include 95% of the software that any "non-technical" user would be dealing with).

And as far as file permissions go, there are important reasons that not everyone has access to /tmp, and it shouldn't be a problem to get the access you need by using sudo.

I can understand that Linux can be frustrating if you're approaching it from a Windows mindset--it was very obnoxious for me at first too,  But try to understand why things work the way they do and I think you'll appreciate it more.  And if you still have problems with your installation, ask about them in this forum, which in my experience is an excellent source of support, and better than most of the similar sites on the Internet filled with people who don't really know anything but think they're "technical" because they can point and click their way around the XP Control Panel.

I will grant the two packages I was loading today were not in repositories., therefore not available in the add / remove menu (unless I have missed it).
Yes I work with a Windows mind set, I spend 95% or more of my time fixing Windows problems.  I do make use of the forum but there was little on Plesk.
I agree with you Ubuntu is by far the best distro I have used in this respectand for most purposes works very well.
Thank you for your comments

---

### Post by SteveHillier on 2008-04-04
> **utUtu said:**
> And you call yourself

**[COLOR="Red"]... (and an experienced IT technician and user)[/COLOR]**

:lolflag:

'Fraid so.  Almost 30 years in the industry.  I have worked RSX11M, RT11, RSTS-E, MS-DOS in all variants except DOS 1.  I used CP/M.  I have used all Windows variants from Windows 2.1 (and not many people even new that existed.  I have worked Novell networks, Win NT, Win 2000 Server & Pro, Win 2003.
I ran SUSE 7 & 7.2, Redhat 9, Fedora 2, Dapper, Edgy, Fiesty, Gutsy.
I have programmed in Basic, Fortran, Dibol, Assembler, DOS command langauge and C.
I have not programmed in OOD/OOL and have difficulty getting my head round some of it.
I will own up, I probably don't know enough of the behind the scenes Linux activity, but these days I don't think I should need to.  I want to be able to load the programs I need to do the job I want thet machine to do with the minimum of fuss.
WHat I am trying to do is build my self a web server to host my and other websites as a service to my customers.  I sincerely hope no one is going to suggest I use an Bill Gates product for this purpose.
So, I have to claim to be experienced.  Maybe not in the area I am trying to work at the moment but you cannot deny my experience exists.
Thanks anyway.
addendum, I forgot my time on IBM VMS and MVS and JCL - sorry

---

### Post by SteveHillier on 2008-04-04
> **finferflu said:**
> I think you need to be aware that Linux applications are not Linux. Blame the application's developers rather than Linux. The messages you are looking for should have been provided by the application, and not by Linux. Linux is an OS, a base upon which people build stuff, which might or might not be very functional.

True.  
I am under no illusion that the Linux base is different to the applications that run on it.  I think in my initial post I indicated that the blame should be pointed to the application developers, and in both cases today these are paid for services and you might expect more because of that.
However I did use the title to get peoples gander up and it seems to have worked.  The general point I want to make is that I would like to see Linux in general become a more widespread acceptable product for general use, but as I have said in other posts, until the community can make it easier for the general user.  Some of that has to be done by the application developers, not only in the programs themselves but also in better documentation.  There is however a lot the Distros can do.  An application installer that gives the user more and standard control over what happens and what goes where and puts shortcuts in appropriate menu slots or at least doesn't complete the install and leaves you not knowing where anything has been put.
For Linux to become more mainstream we have to help the point and click brigade.  This will come at a cost of size and performance but is cannot be beyond the abilities of you young people who continue to enjoy the cutrting edge of software development.

---

### Post by SteveHillier on 2008-04-04
> **wolfen69 said:**
> no need for that. just:
```
gksudo nautilus
```i havnt experienced any of the problems you have. ubuntu runs perfect for me. :guitar:

and this belongs in testimonials.

I don't know about this gksudo thingy.  I will try it out and to connect it to nautilus, well I would never have though of that because I use the GUI file manager and to my simple mind that should do.

Ubuntu runs perfectly for me as a desktop machine.  What I am trying to do today is not what most users do and therefore my criticisms were not of Ubuntu *per se*.

That said, we do have however a mindset among Linux people that is geeky, techy and has a "this doesn't do what I want so I will write one myself that does".  Therein is both the strength and the weakness of the Linux Community.  **Not a criticism boys and girls but an acceptance of reality**.

---

### Post by SteveHillier on 2008-04-04
> **scarrabri said:**
> My Friend and i had a go at installing ubuntu ,will someone tell me that this is a joke,lol it has to be,we spent weeks getting nowhere,we got to the bit just after we put london in,and then it went looking for the hard drives ,now i know they are there and my friend knew his were there,then why the hell did ubuntu spend weeks looking for them,,my friend gave up after he  did get there in the end,which is a shame because i got mine going and i love it ,but ,what a difference it would make if it just worked,,best wishes scarrabri:lolflag::lolflag:

To this I will reply keep trying, it is worth it in the end, just don't go building a web server with Plesk on it at the moment.

---

### Post by finferflu on 2008-04-05
> **SteveHillier said:**
> True.  
I am under no illusion that the Linux base is different to the applications that run on it.  I think in my initial post I indicated that the blame should be pointed to the application developers, and in both cases today these are paid for services and you might expect more because of that.
However I did use the title to get peoples gander up and it seems to have worked.  The general point I want to make is that I would like to see Linux in general become a more widespread acceptable product for general use, but as I have said in other posts, until the community can make it easier for the general user.  Some of that has to be done by the application developers, not only in the programs themselves but also in better documentation.  There is however a lot the Distros can do.  An application installer that gives the user more and standard control over what happens and what goes where and puts shortcuts in appropriate menu slots or at least doesn't complete the install and leaves you not knowing where anything has been put.
For Linux to become more mainstream we have to help the point and click brigade.  This will come at a cost of size and performance but is cannot be beyond the abilities of you young people who continue to enjoy the cutrting edge of software development.

You see, the devs are in charge of the application's behaviour, and of course, distro developers could patch or fix that, but it would take quite an amount of time to do that for every single application. You cannot really control how applications are being developed. 
My point is that Linux is an excellent OS, I love the philosophy behind it: one tool for one task, modularity and flexibility. You need to appreciate that. It's really a pity that people get stuck behind a GUI interface and don't see the potential of the machine they are using. On the other hand one could say that it's a pity the GUI apps don't take full advantage of the OS's capabilities, and seem to parrot other OSS. 
I think that the OS needs the user's feedback, especially Linux. It's been created by educated people and its primary aim is educated people. Knowledge is never bad, and of course it depends on what you are doing. If you use your machine for browsing the net and checking the mail, then you are ok with limited knowledge, but if you are doing things a bit more complicated, it's really recommended that you know what you are doing. 
If you really think that a GUI is what makes things simple, you should give [Arch Linux](http://archlinux.org) a go.

---

### Post by tubasoldier on 2008-04-05
I'm just curious as to your decision to use Plesk. Is it something you are familiar with or is it just that it is a graphical config tool?

If your just looking for a graphical config for your server needs have you looked into Webmin or cPanel? The reason I ask is that Plesk is a commercial software, while Webmin and cPanel are not. Therefore it is much easier for the community here to help you out with Webmin or cPanel, as we could download and install it ourselves and provide a better idea of what to do.. I doubt many of us are going to pay for Plesk. Not a criticism, just reality.

EDIT: By the way, I don't think Linux is all too far off from general use. My step-father is completely computer illiterate and he prefers Linux over Windows. Believe it or not, he says its easier to upgrade, easier to use, and easier to learn. So perhaps instead of trying to peak the interest of people who are already Windows literate we should be looking to people who don't know anything about computers and are willing to learn.

---

### Post by armandh on 2008-04-05
Ubuntu is just fine for general use as are the applications found in the add/remove drop-down. but when searching and adding I have found some apps that I feel are not quite ready for linux desktop noobs such as my self. while all have worked they seem to have a quirk or two. as an example; I just cut and pasted in to terminal that which would allow me to watch commercial DVDs. and when I put one in the regular viewer starts and plays the DVD, but a lot of the functions don't work. if I close the [totem?] viewer and open VLC and select open disk under file I get a viewer with all the functions working. but vlc doesn't seem to be integrated as well and I have no clue how to swap the auto run over or get the totem function buttons working or if either is even possible in this case.

---

### Post by SteveHillier on 2008-04-05
> **tubasoldier said:**
> I'm just curious as to your decision to use Plesk. Is it something you are familiar with or is it just that it is a graphical config tool?

If your just looking for a graphical config for your server needs have you looked into Webmin or cPanel? The reason I ask is that Plesk is a commercial software, while Webmin and cPanel are not. Therefore it is much easier for the community here to help you out with Webmin or cPanel, as we could download and install it ourselves and provide a better idea of what to do.. I doubt many of us are going to pay for Plesk. Not a criticism, just reality.

EDIT: By the way, I don't think Linux is all too far off from general use. My step-father is completely computer illiterate and he prefers Linux over Windows. Believe it or not, he says its easier to upgrade, easier to use, and easier to learn. So perhaps instead of trying to peak the interest of people who are already Windows literate we should be looking to people who don't know anything about computers and are willing to learn.

Plesk is running on our current server.  We are setting one up in the UK to take over so familiarity is a large part.  I am at the point of kicking it into touch as their support seems to comprise of someone who has difficulty in expressing their ideas clearly.  I will look at Webmin and cPanel so thanks for that.

Regards your second point - I think you are right and I think Ubuntu has gone a long way to making Linux acceptable to a wider audience and from the point of view of a new user it does make it easier, you do not have to overcome people previous experience and prejudice.  I just think that more needs to be done to improve the nuts and bolts of installation and configuration before more general acceptance is forthcoming.

---

### Post by SteveHillier on 2008-04-05
> **armandh said:**
> Ubuntu is just fine for general use as are the applications found in the add/remove drop-down. 

Maybe this is my problem.  I don't want general use.  I want web server use, I want domain server use, I want mixed domain workstation use.
Someone find a wodden box, put me in it and nail down the lid - I must be getting too old for this game!!!!

---

### Post by SteveHillier on 2008-04-05
> **finferflu said:**
> You see, the devs are in charge of the application's behaviour, 

Yes, you are right, maybe I should become a developer again - on second thoughts...

> **finferflu said:**
> My point is that Linux is an excellent OS, I love the philosophy behind it: one tool for one task, modularity and flexibility. You need to appreciate that. 

I do!  I do! but there is still that "AAAAGGGGHHHHH" factor when you spend all day trying to so something that doesn't work.

> **finferflu said:**
> I think that the OS needs the user's feedback, 

I hope the community can take my comments in this light.

---

### Post by armandh on 2008-04-05
> **SteveHillier said:**
> Maybe this is my problem.  I don't want general use.  I want web server use, I want domain server use, I want mixed domain workstation use.
Someone find a wodden box, put me in it and nail down the lid - I must be getting too old for this game!!!!

thats the nice part, it CAN be what ever you make it to be
with others you have no options.

---

### Post by linuxfan3 on 2008-04-06
> **SteveHillier said:**
> Maybe this is my problem.  I don't want general use.  I want web server use, I want domain server use, I want mixed domain workstation use.!

i don't know much but maybe the pure debian system is more suitable for you than ubuntu in case of server issues?

---

