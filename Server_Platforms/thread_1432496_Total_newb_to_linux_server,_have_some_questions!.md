---
title: "Total newb to linux server, have some questions!"
date: 2010-03-17
forum: Server Platforms
---

### Post by hxcobd on 2010-03-17
This applies especially to those of you actively working as system administrators and whatnot, but certainly anyones' input is appreciated and valued.

I've recently been given a job offer by a small web company running a social networking-ish site. I have quite extensive experience with linux as an end-user and audio composer/developer, but in terms of managing Apache/Tomcat and doing things like automated backup, I'm basically starting from scratch.

Now, I've used CLI fairly often and can navigate my way around a linux system using command line without a problem, but there are a LOT of things I'd really prefer to use a window-manager for, or in ADDITION to.

Will I get laughed at for saying I'd like to use one? Will my employer/coworkers throw rotten vegetables at me?

I'd love any and all tips about working in a position such as this, really. I've got my orientation this Friday and while I'm always comfortable talking about linux, I KNOW there are going to be tasks they ask me about completing or knowledge I don't currently possess and I'm going to be a deer in headlights!

I know they primarily use outside hosting for the majority of their web server needs, and only house 2 servers at the office. They're both running CentOS 64-bit. (I assume these servers are used for prototyping and pre-launch testing.)

---

### Post by KB1JWQ on 2010-03-18
You may not like this, but yeah-- I'd not hire a *nix admin who wasn't comfortable with the CLI.  Servers don't get GUIs, the overhead hit isn't worth it.

You get to learn FAST.  Take a look at freenode-- the response time there is generally far quicker than on forums due to the realtime nature of discussions.  

Good luck.

---

### Post by HermanAB on 2010-03-18
Simple - run the GUI on your *local* machine.  That is what SSH -X does.

If your local is Windoze, use Xmingw and Putty.

---

### Post by jrssystemsnet on 2010-03-18
> **KB1JWQ said:**
> You may not like this, but yeah-- I'd not hire a *nix admin who wasn't comfortable with the CLI.  Servers don't get GUIs, the overhead hit isn't worth it.
The security exposure also isn't worth it.  A full GUI is several orders of magnitude more complex than a headless server.  Which tends to also mean that many more potential vulnerabilities exposed.  Keeping the server headless vs installing a full desktop environment can be the difference between an unprivileged user-level exploit and a ROOT exploit... which is kinda like the difference between salt in your underwear vs. salt on a slug.

Keep the desktop on your workstation, that's where it belongs.

---

### Post by NullHead on 2010-03-18
Honestly I wouldn't worry about it. You'll learn as you need the knowledge, and you'll learn to "get things done", aka googling stuff, as you move along in what needs to be done. Simply imply you can get what they require done, and do some googling to find out how. As long as you're comfortable with learning and the CLI you'll do fine.

---

### Post by hxcobd on 2010-03-18
Thanks a lot for the tips, guys.

I hadn't even considered SSH from my workstation. That makes considerably more sense. (I already use SSH for a variety of uses including rsync, no idea why this didn't occur to me, heh!)

I had pretty much come to the conclusion that Google was going to be my best friend in my endeavors. The fact that I'm joining the team and everything's already in place, just needing to be maintained, makes me feel a little better.

---

### Post by KB1JWQ on 2010-03-18
If you don't mind my asking, what were you planning on doing, sitting in the datacenter with a crash cart, plugging in a keyboard, monitor, and mouse to every box as you need to admin it?

Look into ssh keys as well; more secure, and keeps you from having to type a password 800 times a day. :-)

---

### Post by hxcobd on 2010-03-18
> **KB1JWQ said:**
> If you don't mind my asking, what were you planning on doing, sitting in the datacenter with a crash cart, plugging in a keyboard, monitor, and mouse to every box as you need to admin it?

Look into ssh keys as well; more secure, and keeps you from having to type a password 800 times a day. :-)

Already using SSH keys! Good tip though, thanks.

:)

The office itself actually only runs 2 servers and both are outfitted with keyboards and mice.

---

### Post by sv87411 on 2010-03-19
> **hxcobd said:**
> 
The office itself actually only runs 2 servers and both are outfitted with keyboards and mice.

If they don't have monitors then you're gonna have to get used to SSH ;););)

If they do have monitors though you can impress them by asking why they have monitors/mice installed and why they aren't locked away in a secure cupboard somewhere. :D

---

### Post by jonabyte on 2010-03-19
Have you ever though of picking up a Linux admin book and actually trying to learn it ahead of time?

---

### Post by Agent ME on 2010-03-19
> **HermanAB said:**
> Simple - run the GUI on your *local* machine.  That is what SSH -X does.
The server still has to have GUI programs installed to do that, which is likely not the case.

---

### Post by guessswh0 on 2010-03-19
Sorry, but if I had a linux admin, who i hired, come in and ask why there is no gui (or try to install a gui) on a linux server, I would immediately become very on edge with that person.

Definitely look into learning from the command line, and honestly, I would never ask on the job about a gui on servers.

---

### Post by hxcobd on 2010-03-19
> **jonabyte said:**
> Have you ever though of picking up a Linux admin book and actually trying to learn it ahead of time?

Exactly what I've been doing, but books don't generally cover questions like the one I posed.

The answer was sort of implied, which is why I didn't actually ask it at the interview. I know the vast majority of admins don't use GUIs. It was a question primarily drawn from curiosity.

Also, isn't it sort of incongruous to get mad at a linux user for being interested in possibly using a GUI for administration while Windows Server naturally runs a GUI? I mean, if command line was the universal standard across ALL systems and ALL operating systems, my question would clearly have been stupid; however, that's not the case...

---

### Post by jrssystemsnet on 2010-03-19
> **hxcobd said:**
> Also, isn't it sort of incongruous to get mad at a linux user for being interested in possibly using a GUI for administrationAin' nobody mad at'cha...

> while Windows Server naturally runs a GUI?Windows Server running a GUI is bloody *stupid*.  Believe me, there are *plenty* of things that Microsoft does that nobody with any sense would emulate.

The major reason that Windows Server runs a GUI is because the original *raison d'etre* for Windows as a platform was that it would appeal to non-professionals.  Having appealed to the non-professionals in the beginning, Windows then worked its way *up* as the non-professionals who were familiar with it began asking for it in the workplace.  Unfortunately, this means that the Windows environment tends to be EXTREMELY late to the party in implementing the sort of tools and infrastructure that are most useful to dedicated professionals, because it's a stretch away from the roots of the platform and an awful lot of legacy cruft.  (There are some exceptions to this rule - for example, Active Directory is currently the most complete system of its type... not that I have a lot of love for the way you have to *maintain* AD; but I digress.)

Linux tends to be the other way around - Linux was originally a clone of Unix, which has a *long* history of being designed strictly for professional IT types with a deep investment of knowledge; and it's been a long long road getting the safety wheels on to make it appealing to folks who aren't and don't want to be IT professionals with a deep investment of knowledge.

At this point, it's arguable which is doing a better job at leaving the limitations of its roots behind - is Windows growing to serve the professionals better, or is Linux growing to serve more casual users better?  Frankly, I think Linux is doing a much better job at whittling away its legacy limitations than Microsoft is, and by a long stretch - but it *is* arguable.

Either way, though, "but that's the way Windows Server does it" isn't necessarily a good rule of thumb for defending a particular way of doing things.  Just because Windows Server does it that way doesn't necessarily make it bad... but it REALLLY doesn't necessarily make it good, either. :)

Anyway, as said before... for most servers, the GUI is several orders of magnitude more code than the actual job the server is there to do.  This means it's usually more WORK for the server to run the GUI than to actually do its job, and it also means it's several orders of magnitude more exposure to possible security risks (and possible general malfunctions that get in the way of getting work done) than a simple console.

So, for most purposes... GUIs don't belong on servers.  GUIs absolutely *do* on workstations, and the people who administer the servers in many cases absolutely *do* need GUIs to do some of the things they do to administer the servers... but the GUIs in question, again, almost invariably belong on the workstation the admin sits at, not on the server the admin is admin'ing.

(I know I'm longwinded and kinda forceful... but remember, I ain't mad at'cha. :))

---

### Post by jrssystemsnet on 2010-03-19
Regarding the burden of code...

```
me@server:~$ sudo du -hs /usr
364M     /usr
```

That is a pretty capable Ubuntu server; it runs MySQL, Postfix, Apache2 with PHP5, and has quite a lot of web application code, monitoring tools, analysis tools, and various other "this is the job I actually do" stuff that lives in /usr.

```
me@workstation:~$ sudo du -hs /usr
3.1G     /usr
```

That is a pretty basic Ubuntu workstation - no games on it, no applications outside the default loadout other than Thunderbird as a mail client, avidemux as a video editor, and the generic ubuntu-restricted-applications suite (codecs to view videos, the Flash plugin, etc).  And yet it's STILL nearly 10 times as fat as the server.

See what I mean?  Even discounting performance issues, 10 times as much code is 10 times as much stuff to break, 10 times as many opportunities for a security exploit to hurt you, 10 times as much stuff to maintain and update (and 10 times as much stuff to potentially break *when* you maintain and update it).  It's not a trivial issue.

---

### Post by Donny Bahama on 2010-03-19
> **jrssystemsnet said:**
> which is kinda like the difference between salt in your underwear vs. salt on a slug.LMAO!!! That belongs in the Analogy Hall of Fame!

---

### Post by Donny Bahama on 2010-03-19
> **HermanAB said:**
> Simple - run the GUI on your *local* machine.  That is what SSH -X does.I just learned something new. Thank you!

---

### Post by KinKiac on 2010-03-19
You may find that they will provide a lot of training on the job.  That is unless you're going to be the head guy.  I started almost 2 years ago working in a small IT dept(well somewhat small).  I monitor a couple of mirrored as400 servers, 2 mirrored rs6000's running AIX and about 30 or 40 intel servers running server 2003.  I was worried as well when I first started that I didnt know enough going into the job to be able to satisfactorily perform my duties.  When I actually started there was a lot of info thrown at me but I managed to get by just fine.  

My bosses basically told me they didnt expect me to know a whole lot about the servers and stuff coming into the job because unless I had worked in a similar job previously, I just would have nowhere to have gained experience on these types of machines.  I had 6 weeks of working side by side with other operators before they would let me work alone.  It all worked out, and Ive never even taken any formal computer courses.  

I dont know what your position entails exactly or what kind of experience they are looking for but Im assuming they know enough about your experience from your resume to be able to tell if you will be competent or not, unless you lied on your resume.  When i talked to my boss a little after being fully trained i admitted to him that i wasnt sure if i would be qualified for the position.  He kinda laughed and said to me "if we didnt think you were qualified, we wouldnt have hired you."  And that was that, 2 years later and im quite comfortable performing my duties, which include running backups, performing routine maintenance and repairs to various types of terminals and PC's and of course monitoring the servers.  one of my co-workers just got a job working for a data centre and it was the same thing, he felt like on the first day he knew nothing, but his supervisor assured him that they normally assume that of most new hires, and just train from within.  There's no better training than working on the front lines.

---

### Post by geoffmcc on 2010-03-20
Do you have ubuntu server installed on a home machine? If not, i would say do it. I am not the answer man you are looking for - I cant provide you with real world advice or opinions on the matter in terms of a job, but i can tell you that when I started working with Ubuntu server having very little linux experience- but do well with windows OS (but thats like playing a game on easy and then being impressed with yourself when you beat it)I couldn't help but to learn something new every time i connected into it and I couldn't help connecting into it to change or add something new.

So my advice is if you havent installed ubuntu server do it - maybe get wordpress and drupal or phpbb or something up then try writing scripts to back them up or look into other ways of doing it.

I recently started using my ubuntu server as a gateway/router to supply internet to 2 other pc's using a hub rather then me going out and buying a router using the clonezilla and drbl package 

[http://ubuntuforums.org/showthread.php?p=8986246#post8986246](http://ubuntuforums.org/showthread.php?p=8986246#post8986246)

---

### Post by hxcobd on 2010-03-20
> **KinKiac said:**
> You may find that they will provide a lot of training on the job.  That is unless you're going to be the head guy.  I started almost 2 years ago working in a small IT dept(well somewhat small).  I monitor a couple of mirrored as400 servers, 2 mirrored rs6000's running AIX and about 30 or 40 intel servers running server 2003.  I was worried as well when I first started that I didnt know enough going into the job to be able to satisfactorily perform my duties.  When I actually started there was a lot of info thrown at me but I managed to get by just fine.  

My bosses basically told me they didnt expect me to know a whole lot about the servers and stuff coming into the job because unless I had worked in a similar job previously, I just would have nowhere to have gained experience on these types of machines.  I had 6 weeks of working side by side with other operators before they would let me work alone.  It all worked out, and Ive never even taken any formal computer courses.  

I dont know what your position entails exactly or what kind of experience they are looking for but Im assuming they know enough about your experience from your resume to be able to tell if you will be competent or not, unless you lied on your resume.  When i talked to my boss a little after being fully trained i admitted to him that i wasnt sure if i would be qualified for the position.  He kinda laughed and said to me "if we didnt think you were qualified, we wouldnt have hired you."  And that was that, 2 years later and im quite comfortable performing my duties, which include running backups, performing routine maintenance and repairs to various types of terminals and PC's and of course monitoring the servers.  one of my co-workers just got a job working for a data centre and it was the same thing, he felt like on the first day he knew nothing, but his supervisor assured him that they normally assume that of most new hires, and just train from within.  There's no better training than working on the front lines.

This post was extremely helpful to me. Thanks a lot for writing.

I'm in the exact same position, actually. Well, mostly. I WILL be head of the IT/administration, though.

Like I said, it's a VERY small company with a VERY simplistic network, so on the networking/IT/maintenence side of things, I'm really not concerned at all. I've managed networks of roughly this size before. It's much smaller than the one you mentioned; only 2 network/backup servers, 2 database servers, and then about 12 workstations on the network.

But as far as administration stuff goes, it's basically all new to me. I've never used Apache or Tomcat before, or used tape backups at all, or done any significant shell scripting. I've managed to teach myself a lot of things (especially terminal commands, RSYNC/IOSTAT/IFCONFIG etc) and I'm not even hired yet.

I have been using linux for almost a decade now, just almost always as an end-user/tinkerer, and never as a server admin.

I know that when I actually get on the job, I'll be perfectly capable of performing the tasks needed. It's just kind of nerve-racking to step into a role, ALONE, knowing relatively little about the software being used. I'm also not expecting much training on-the-job, because as I said, the old admin will literally be gone when I move into the role.

That means a LOT of Googling and reading for me, but that's how I've always used linux, so nothing new, I guess!

Oh, and thanks for the SSH -X tip, that's brilliant! Should help a lot.

I plan on installing Ubuntu Server on my other laptop tonight to do some small-scale testing/tinkering. Really good tip, so thanks a lot for that idea. (I HAVE been using both laptops on vanilla Ubuntu to do testing and learning, but I've been running GNOME, so it's not entirely realistic.)

---

### Post by drdos2006 on 2010-03-20
Install webmin on your server and ssh from your browser on your desktop machine into your server.
For testing, that is what i am doing with virtual box on my desktop.
I used this HOW-TO from [http://woodel.com](http://woodel.com) and just changed some of the Debian commands to reflect Ubuntu commands.

regards

---

### Post by hxcobd on 2010-03-20
> **drdos2006 said:**
> Install webmin on your server and ssh from your browser on your desktop machine into your server.
For testing, that is what i am doing with virtual box on my desktop.
I used this HOW-TO from [http://woodel.com](http://woodel.com) and just changed some of the Debian commands to reflect Ubuntu commands.

regards

I don't really understand the point of Webmin. Why bother if you can already SSH or SSH -X in?

Also, all the servers are already set up and configured, and have been for 2-3 years now. This makes the 579-page setup guide a rather lengthy read for something I'm not really sure I need.

What's the advantage of using Webmin?

---

### Post by drdos2006 on 2010-03-20
This can answer your question more fully than I can. 
[http://webmin.com/demo.html](http://webmin.com/demo.html)
Webmin is a GUI run from the desktop.

regards
[edit]
The demos are not working but the screenshots are.
[/edit]

---

### Post by hxcobd on 2010-03-20
Yeah, checked out the screenshots. I guess it looks kinda handy. 

I think my willingness to use such a thing would depend largely on how long it takes to install and set up. If it took more than an hour or two tops, I can't imagine straying from SSH and CLI.

Do you think it's worth it, drdos? How do you like it?

---

### Post by drdos2006 on 2010-03-20
Yes, I certainly like it. It appears quite a few others like it as well.
I seem to remember it only took about three or four minutes with access from the server CLI to set it up.
You may need to open your firewall port to allow acces from your desktop. For me that is not an issue as I am running the server through virtualbox on my desktop.
The commands were to make a temporary directory.
sudo mkdir /options
cd /options
sudo wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.500_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.500_all.deb)
sudo dpkg –i webmin_1.500_all.deb
Webmin will complain of missing libraries and list them.
sudo apt-get install "the libraries that are missing"

To login to Webmin, open your browser, type your server IP address, followed by :10000 proceeded by https://
[https://the-ipaddress-of](https://the-ipaddress-of) your-linux-box:10000
The manual is very convoluted but thorough.
regards

---

### Post by hxcobd on 2010-03-20
Always appreciate any tips, drdos. Will certainly take a look at it and any other utilities that can make my conversion to this position easier! Thanks again.

---

### Post by Bryantos on 2010-03-20
> **jonabyte said:**
> Have you ever though of picking up a Linux admin book and actually trying to learn it ahead of time?

QFT. Documentation is your friend.

---

