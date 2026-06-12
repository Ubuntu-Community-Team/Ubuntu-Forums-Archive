---
title: "Where to propose a new Ubuntu feature?"
date: 2014-11-11
forum: Ubuntu, Linux and OS Chat
---

### Post by marginal39 on 2014-11-11
Hi.

Sorry if this is not the right place to ask but I need to know where I may propose a feature concerning the update/upgrade of Ubuntu.

Regards. :-).

---

### Post by ian-weisser on 2014-11-11
What kind of new feature?

Some simple new features can be requested using a Wishlist bug.
Others may require discussion at an Ubuntu Online Summit, or on a developer mailing list.

Some requested features may be infeasable or dangerous. Or already implemented. Or already planned.
The *best* way to get a feature into Ubuntu is, of course, to contribute the code for it.

Ubuntuforums is an appropriate place to discuss new feature ideas.

---

### Post by marginal39 on 2014-11-11
> **marginal39 said:**
> Hi.

Sorry if this is not the right place to ask but I need to know where I may propose a feature concerning the update/upgrade of Ubuntu.

Regards. :-).

I would like to include an option in the settings of the software updater that allows it to launch automatically at startup or login after a suspend.
Could you tell me what would be the best place to post such a request?

Regards.

---

### Post by ian-weisser on 2014-11-11
If I recall correctly, Software Updater already launches automatically soon after user login (memory; I don't use S-U myself anymore).
The icon change should be triggered by the daily apt cron job, which runs a few minutes after boot (or resume) with the rest of the cron.daily jobs.

The apt cron job updates the dpkg database (equiv to sudo apt-get upgrade), and checks for available updates (equiv to sudo apt-get update). Various settings in apt.conf permit security updates (enabled) and other repository updates (disabled), so they can update entirely behind-the-scenes. It also triggers several other processes based upon what it discovers, including SU.

The developers put a lot of thought into how to notify the user when updates are available, and how to limit the number of infrequently-used options. They settled on an alert icon, and letting the user decide when to click on it. One of the goals of this design was to specifically eliminate 'nagging' windows (like Software Updater) opening when the user didn't expect, or didn't want, or interrupting the user's work, or stealing window focus from something more important.

One problem with running SU at login or resume is that the dpkg database hasn't been updated yet. Depending on your network state and available bandwidth, that update may take a few seconds...or minutes.

Are you not receiving updates?
Or not getting the alert icon when updates are available?
Or did the developer miss a use case?
Can you give us an example of how this feature would be used?

---

### Post by marginal39 on 2014-11-11
> **ian-weisser said:**
> If I recall correctly, Software Updater already launches automatically soon after user login (memory; I don't use S-U myself anymore).
The icon change should be triggered by the daily apt cron job, which runs a few minutes after boot (or resume) with the rest of the cron.daily jobs.

The apt cron job updates the dpkg database (equiv to sudo apt-get upgrade), and checks for available updates (equiv to sudo apt-get update). Various settings in apt.conf permit security updates (enabled) and other repository updates (disabled), so they can update entirely behind-the-scenes. It also triggers several other processes based upon what it discovers, including SU.

The developers put a lot of thought into how to notify the user when updates are available, and how to limit the number of infrequently-used options. They settled on an alert icon, and letting the user decide when to click on it. One of the goals of this design was to specifically eliminate 'nagging' windows (like Software Updater) opening when the user didn't expect, or didn't want, or interrupting the user's work, or stealing window focus from something more important.

One problem with running SU at login or resume is that the dpkg database hasn't been updated yet. Depending on your network state and available bandwidth, that update may take a few seconds...or minutes.

Are you not receiving updates?
Or not getting the alert icon when updates are available?
Or did the developer miss a use case?
Can you give us an example of how this feature would be used?

Thank you for the extensive reply ian-weisser, but after "Big Sista" started hacking my PC I am not as sure as I was before concerning what is happening, what not and who's controlling my PC :-).

I receive updates, but wanted to make sure the updater is running in the background right after I logon to my desktop.
The main reason for that is that I noticed "Big Sista" is doing stuff on my PC a short time before an update meaning they fool arounnd with my PC because it is vulnerable and it has to be done quickly before the upcoming security update.
I just want to shorten the time between the vulnerability moment and the update one.
Also as I am getting old and my hearing is getting less reliable than before, I was thinking of adding a small mike to the CPU's fan in order to be able to hear the louder noise of it during an intrusion ;-).

Otherwise I get updates and the icon pops-up every now and then, but all of my internet is under "Big Sista's" control before and after it reaches me.

I know I am not alone in that boat and I know we have to be very scared and not discuss such intrusions, but maybe one day there will be so many of us that there are no going to be enough funny money to pay the ones who are spying on us anymore :-).

Thanks for the help :-).

---

### Post by mastablasta on 2014-11-12
> **marginal39 said:**
> 
The main reason for that is that I noticed "Big Sista" is doing stuff on my PC a short time before an update meaning they fool arounnd with my PC because it is vulnerable and it has to be done quickly before the upcoming security update..

> Also as I am getting old and my hearing is getting less reliable than before, I was thinking of adding a small mike to the CPU's fan in order to be able to hear the louder noise of it during an intrusion ;-).
What?

:-k

> 
I know I am not alone in that boat and I know we have to be very scared and not discuss such intrusions, but maybe one day there will be so many of us that there are no going to be enough funny money to pay the ones who are spying on us anymore :-).


seriously - there are logs, security logs and if you are really paranoid you can install monitoring software. you will know exactly what happens on your computer. you can have it forwarded to your email or mobile phone. 

you must be very intresting that someone you call big sista is spying on you from external network as in understand. if you need better protection buy a firewall, create VPN, use TOR. oh and if your "big sista" has physical access then manage users and groups better and use ecrypted file system:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by marginal39 on 2014-11-12
> **mastablasta said:**
> What?

:-k



seriously - there are logs, security logs and if you are really paranoid you can install monitoring software. you will know exactly what happens on your computer. you can have it forwarded to your email or mobile phone. 

you must be very intresting that someone you call big sista is spying on you from external network as in understand. if you need better protection buy a firewall, create VPN, use TOR. oh and if your "big sista" has physical access then manage users and groups better and use ecrypted file system:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Hwllo mastablasta.

What I believe in is that the ones that have access to my PC can brake through any firewall VPN and TOR.
Also I tried to run Freenet a moth ago to no avail.
It sems to be starting but it dies not load.

Talking about physical access I don't believe it happens, at least not every day as I live with my wife only.
The only way for them to access my PC physically would be during the time we're out, but that wouldnt happen every day.
Strange things are happening on my PC like I loose control of the pointer of my mouse for 10 seconds and during that period of time it becomes invisible no matter how gard I try to move the mouse.
Most of the times that happens is when I watch videos.
Another "feature" of my PC is that after I login to Ubuntu my internet connection is taking about 10 seconds to connect compared to a much faster time before as if someone was "allowing" me to connect but only after "they" are controlling my internet access.

All that happens after I was refused enrty to the USA after I was held at their customs during a period of four hours for no reason.
Knowledgeable people already tried helping by giving me commands to execute in the terminal to no avail.
If you or someone else believes can help me resolve my safety issues with commands I can run in my terminal you are welcome.

Also sometimes when I run my System Monitor I see an activity of 3% for Firefox, 2% for compiz and 1% for gnome-system-monitor only BUT my CPU fan is making noise as loud as a helicopter for long time event hough there's no appearent reason for that as I am not doing nothing on my PC.

My Facebook password gets hacked right after I change it and so does my email password but not right away ...

I read the security logs, but sometimes they don't make sense.

Thank you :-).

---

### Post by mastablasta on 2014-11-12
knowledge will be your biggest weapon and you will sleep better if you use it. I apologise if this may sound rude but I believe you do not grasp the basic concepts of how things work. I know I do not have advanced knowledge but I do know a little bit about them. so getting to now how things work at their core will help you relax a bit in your life.

> **marginal39 said:**
> 
What I believe in is that the ones that have access to my PC can brake through any firewall VPN and TOR.

not really no. check the Wikipedia for truecrypt enrty. you will find how they caught a drug lord with data on PC. they even had physical access to the hard drive and could not crack it. attempted and invested a lot of time. it is not as easy as it is in the movies.

> 
Talking about physical access I don't believe it happens, at least not every day as I live with my wife only.
The only way for them to access my PC physically would be during the time we're out, but that wouldnt happen every day.
.
Good, because usually physical access is basically full access.

there are cheap measure to see if anyone entered the house while you are out. tough I very much doubt it. 

> 
Strange things are happening on my PC like I loose control of the pointer of my mouse for 10 seconds and during that period of time it becomes invisible no matter how gard I try to move the mouse.
Most of the times that happens is when I watch videos.

Could be a software or hardware issue. definitely does not indicate a break in attempt or control. in fact if they are in and if they are good you won't know they are in. ;-)
> 
Another "feature" of my PC is that after I login to Ubuntu my internet connection is taking about 10 seconds to connect compared to a much faster time before as if someone was "allowing" me to connect but only after "they" are controlling my internet access.

Again this does not indicate what you think it does. it could be that wrong drivers are loaded or there is a firmware issue. 
> 
All that happens after I was refused enrty to the USA after I was held at their customs during a period of four hours for no reason.
Knowledgeable people already tried helping by giving me commands to execute in the terminal to no avail.

ouch. did you bring a nail clipper on the plane? :)
> 
If you or someone else believes can help me resolve my safety issues with commands I can run in my terminal you are welcome. people over at security section are good at that. much better than I am. I managed to spam my own email box yesterday....

> Also sometimes when I run my System Monitor I see an activity of 3% for Firefox, 2% for compiz and 1% for gnome-system-monitor only BUT my CPU fan is making noise as loud as a helicopter for long time event hough there's no appearent reason for that as I am not doing nothing on my PC.
*chrip, chrip, chrip....* nothing...
this is nothing unusual. my old computer at work used to do that. it decided to cool off itself a bit more and it ran the fan :) also you could have a cron job running. top or better yet htop in terminal will let you know what process is doing it.
> 
My Facebook password gets hacked right after I change it and so does my email password but not right away ...


now that could be a problem. how do you know they get hacked? two factor authentication should prevent this.
> 
I read the security logs, but sometimes they don't make sense.
again security section of forums. post specific and good questions and post the logs if you need them interpreted.

now to remember - by default Ubuntu does not listen on any ports. if you installs server apps and then open ports on your router as well only then someone will see your PC and be able to access it (if oyu let them)

for starters check /var/log/auth0.log
this should show any logins from other IP's.

checking for rootkits and then installing fresh should remove any backdoors (if you think they are there) and then you can just do updates as they come. while security updates are important it is also goot to know that unless you are running a server you have all "doors" closed by default on your computer.

there was a good article about someone who let their computer be hacked (they opened server services to internet and then waited to see what will happen and how fast). they monitored the progress of the hack, how long it took etc. anyway such monitor tools can be used to find a hack. but I can't find the article right now.

---

### Post by marginal39 on 2014-11-18
Hello mastablasta and thank you for the extensive reply.

I am old and a little busy so I'll try your suggestions but it will take time.
First here's a link with an article to what I know they're doing to my internet connection: [http://gizmodo.com/the-nsa-uses-radio-waves-to-monitor-100-000-computers-w-1501722277](http://gizmodo.com/the-nsa-uses-radio-waves-to-monitor-100-000-computers-w-1501722277)

Also today I installed Gufw Firewall and guess what after I turned it's status from OFF to ON it turned OFF by itself right away, after what I turned it ON back again.
Here's a copy of that happening from the logs: 
[18.11.2014 10,52,57] Status: Enabled
[18.11.2014 10,52,52] Status: Disabled
[18.11.2014 10,52,49] Status: Enabled

I will be back after I follow the steps you gave me.

Thanks.

---

### Post by marginal39 on 2014-11-18
> **mastablasta said:**
> 
not really no. check the Wikipedia for _**truecrypt**_ enrty. you will find how they caught a drug lord with data on PC. they even had physical access to the hard drive and could not crack it. attempted and invested a lot of time. it is not as easy as it is in the movies.

I see what you mean, but given the fact that I am not a computer wiz and am more into the metaphysical than the computer sciences a competition on the physical level is not one I will win.

It is and have always been a constant competition between the ones creating the software and the ones crackng it.
Therefore nothing is a 100% safe because in the period between it is safe and the one it is cracked there's a security breach.

Thanks.

---

