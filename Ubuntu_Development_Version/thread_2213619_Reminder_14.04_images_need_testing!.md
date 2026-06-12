---
title: "Reminder: 14.04 images need testing!"
date: 2014-03-27
forum: Ubuntu Development Version
---

### Post by balloons on 2014-03-27
Just a friendly reminder to everyone who's been enjoying breaking and reporting issues with trusty all cycle. For the final images to release we need testing done. Please do what you can during the final milestone which is a couple weeks away. Don't forget flavors as well who need help with testing.

I'd like point out mythbuntu specifically as needing some extra help this cycle. Of course, please don't forget about ubuntu! Let's make 14.04 an LTS to be proud of. Certainly we've come a long way since precise, let's put forth our best efforts on trusty.

So, how can you help? Simple, watch for the announcement for the the final milestone which happens about 5 days before the scheduled release. In the meantime, test and report against the daily milestone:

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

Thanks for your hard work and dedication this cycle. Remember, images can't release without results (the release team is kind of harsh like that :D); we need your help in verifying! As always happy testing!

---

### Post by Elfy on 2014-03-27
Stuck.

---

### Post by ventrical on 2014-03-27
> **balloons said:**
> Just a friendly reminder to everyone who's been enjoying breaking and reporting issues with trusty all cycle. For the final images to release we need testing done. Please do what you can during the final milestone which is a couple weeks away. Don't forget flavors as well who need help with testing.

I'd like point out mythbuntu specifically as needing some extra help this cycle. Of course, please don't forget about ubuntu! Let's make 14.04 an LTS to be proud of. Certainly we've come a long way since precise, let's put forth our best efforts on trusty.


  All of my spare time is spent on testing images, zsyncing .. etc... This cycle (as well as the several previous) are all to be proud of. At least I am.  Ubuntu, in general, does not understand failure. It does not project suffering upon  it's users. It is always dynamic, effervescent and an overall satisfying experience.  It engenders discovery and encourages exploration and study. It is not a bridge of sighs but rather a hi-way of experience. Unity forges a real bond between the engines under the hood and the needs of the  average end_user public and explicitly exposes user friendly techniques via the genius of it's design. The other Ubuntu flavours follow suit with their multiplicities of ambiance that those desktop experiences provide to the general masses and provide a cool ways and means for the 'linux for human beings' group to surf the net virtually and literally uninterrupted, a feat that cannot be boasted by any other OS on the market. Futhermore, with the new Ubiquity/Installer design with the Trusty release, the days of system recovery headaches are only phantoms of the past.

Regards..

---

### Post by ventrical on 2014-03-27
> **balloons said:**
> Just a friendly reminder to everyone who's been enjoying breaking and reporting issues with trusty all cycle. For the final images to release we need testing done. Please do what you can during the final milestone which is a couple weeks away. Don't forget flavors as well who need help with testing.

I'd like point out mythbuntu specifically as needing some extra help this cycle. 


k :)

edit:

Wow ... must be really busy bandwidth. Stopped dead in it's tracks during download. First time that happened.

---

### Post by ventrical on 2014-03-27
^fixed..

---

### Post by ventrical on 2014-03-28
Running the mythbuntu trusty .iso live.  Do I really have to install to disk it to get it to work? 

btw .. the live session is very snappy and works smoothly with other accessories.

---

### Post by balloons on 2014-03-28
> **ventrical said:**
> Running the mythbuntu trusty .iso live.  Do I really have to install to disk it to get it to work? 

btw .. the live session is very snappy and works smoothly with other accessories.

The live session is the first test. Did you check the tracker for the other two? One tests the frontend, the other the backend. The frontend test should be easier, though you aren't likely to have a remote. Just checking the live session is great; no one did that for beta 2! Thanks!

---

### Post by ventrical on 2014-03-28
> **balloons said:**
> The live session is the first test. Did you check the tracker for the other two? One tests the frontend, the other the backend. The frontend test should be easier, though you aren't likely to have a remote. Just checking the live session is great; no one did that for beta 2! Thanks!


 I didn't see any other tests there. I tested 'live session' and passed it. Are you saying that I can test the frontend and backends through the tracker while in 'live session' mode? or do I have to install?

I'll check it again..


Thanks in advance...

---

### Post by ventrical on 2014-03-28
> **balloons said:**
> The live session is the first test. Did you check the tracker for the other two? One tests the frontend, the other the backend. The frontend test should be easier, though you aren't likely to have a remote. Just checking the live session is great; no one did that for beta 2! Thanks!


Got it! :)lol  Have to hard install. Will do soon.

---

### Post by Elfy on 2014-03-28
> **ventrical said:**
> I didn't see any other tests there. I tested 'live session' and passed it. Are you saying that I can test the frontend and backends through the tracker while in 'live session' mode? or do I have to install?

I'll check it again..


Thanks in advance...

From the testcases it would look like they need the system to be installed
> 
Mythbuntu Backend & Frontend - Once installation is finished, remove the installation media and reboot.
Mythbuntu Frontend - Once installation is finished, remove the installation media and reboot.

Frontend would appear to require backend to be working - > Select "Watch TV". (this will only work if you have a backend already in the network)

---

### Post by ventrical on 2014-03-28
> **Elfy said:**
> From the testcases it would look like they need the system to be installed


Frontend would appear to require backend to be working -


Yep .. posted it above your's  :)  Just about to get on that now.  It uses a really slick xfce desktop almost like Xubuntu but the live session works right out of the box ..smooth and sleek.

---

### Post by Elfy on 2014-03-28
must have been posting at the same time :)

---

### Post by ventrical on 2014-03-28
Will not copy or move video file to /srv/ , even in root. So I cannot complete the test. Any hints??

> 
Download a demo file. I recommend a MP4 trailer (for example, the 480p MP4 trailer at[http://www.sintel.org/download](http://www.sintel.org/download) ).Once downloaded, move this file to the /srv/ directory (it must be outside your home directory)


edit:

fixed..

---

### Post by ventrical on 2014-03-29
Just a question. While setting up the mythubuntu they mention the 'machine ip'. Do they want the external ip or the internal ip?

In this step here. So I would assume we use the ip reported when using ifconfig from terminal ie; 192.168.2.29 or the Bcast 192.168.2.255  ???

'
 
[LIST]
[*]IP Address (Under Local Backend): [use the machine's IP address (not 127.0.0.1)] 
[*]Security PIN (required): 1234 
[*]IP Address (Under Master Backend): [use the machine's IP address (not 127.0.0.1)]' 
[/LIST]

---

### Post by d-cosner on 2014-04-05
I just did a clean install of 14.04 on an HP 655 laptop, everything is working great! No problems with the installation other than an error caused by Windows 8 partitions. I deleted the partitions and the install went fine after that.

---

### Post by ventrical on 2014-04-07
> **d-cosner said:**
> I just did a clean install of 14.04 on an HP 655 laptop, everything is working great! No problems with the installation other than an error caused by Windows 8 partitions. I deleted the partitions and the install went fine after that.

 I have run into this problem several times during this cycle and the best tool I have used is GRuB Rescue CD. Once the 'live' CD is  up just choose  the 'update grub' option and it will give you both partitions in GRuB menu. (Is this the type of problem you were refering to?)

Regards..

---

### Post by balloons on 2014-04-15
Final images are live on the tracker. Please test if you've not yet submitted a result to the tracker this week! Thanks everyone!

[http://iso.qa.ubuntu.com/qatracker/milestones/314/builds](http://iso.qa.ubuntu.com/qatracker/milestones/314/builds)

---

### Post by d-cosner on 2014-04-16
I installed 14.04 x64 on my kids computer, the install went great! Both my laptop and the boys desktop are running very well and I have not run into any problems. I even enabled secure boot on the laptop and tried out the signed kernel and there was no problems at all with it.

---

### Post by ventrical on 2014-04-16
The 64bit iso is really smooth in the live session so far.

---

### Post by fooman on 2014-04-17
Ubuntu Trusty Tahr 14.04 LTS = $0.00
brand new 240Gb SSD on sale a few weeks ago = $105.00

Ubuntu Trusty Tahr 14.04 LTS released on my day off from work = pricele$$! :D

...installing now!

---

### Post by Elfy on 2014-04-17
unsticking

---

