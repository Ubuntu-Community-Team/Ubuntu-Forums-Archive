---
title: "testing daily current in UEFI mode/screenshot knocks bullet from ubiquity"
date: 2015-01-15
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-01-15
testing xubuntu-desktop-amd64.iso daily in UEFI mode I went to choose 'Upgrade Ubuntu 14.04.1 LTS to Xubuntu 15.04' and after the screenshot was taken it knocked the radio bullet to the <something else>. option.

Mouse action very hyper also.

---

### Post by ventrical on 2015-01-15
Oy.... gee..

---

### Post by slickymaster on 2015-01-15
?!
I must confess that I'm lost ventrical. What do you mean? :confused:

---

### Post by ventrical on 2015-01-15
Now when i choose to upgrade 14.04 to 15.04 I get a mountpoint error.

---

### Post by ventrical on 2015-01-15
when you click 'OK it goes to <something else> and then re-loops back to original Ubiquity screen automagically.

---

### Post by slickymaster on 2015-01-15
> **ventrical said:**
> when you click 'OK it goes to <something else> and then re-loops back to original Ubiquity screen automagically.

ubiquity bug, perhaps?

---

### Post by ventrical on 2015-01-15
so I am going to choose 'erase 14.04 and reinstall' and see what happens. 14.04.1 will not shut down correctly anyways and you can't get <efivar> from the trusty repos.

---

### Post by slickymaster on 2015-01-15
> **ventrical said:**
> so I am going to choose 'erase 14.04 and reinstall' and see what happens. 14.04.1 will not shut down correctly anyways and you can't get <efivar> from the trusty repos.

Just as a heads up, be aware of this as you might face it: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1408495](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1408495)

---

### Post by ventrical on 2015-01-15
> **slickymaster said:**
> ubiquity bug, perhaps?


That is my thinking also but i am working on a  UEFI system with win 8 and ubuntu on it (14.04) that got carfunkled when i installed 14.04 - so basically it was already busted so i can't in good conscience file a bug against ubiquity because i don't have any evidence to that yet. but i am going ahead with erase and reinstall anyways.

---

### Post by ventrical on 2015-01-15
seriously messed up .. but i am going to go ahead anyways . if it breaks I'll just reformat and start from scratch.

edit:  filed a bug anyways .. just in case..

edit;

The below is a non bug.

[URL="https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1411367"]https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1411367


[/URL]

---

### Post by slickymaster on 2015-01-15
> **ventrical said:**
> seriously messed up .. but i am going to go ahead anyways . if it breaks I'll just reformat and start from scratch.
:lolflag:
Have fun ventrical.

---

### Post by ventrical on 2015-01-15
I quit that install because it kept comming up with ubi-partman error with each step. so I'll start from scratch again..

---

### Post by grahammechanical on 2015-01-15
Last week I had 2 attempts to install Vivid daily images and both failed partway through with ubi-console failed. You could be seeing issues with the daily images and not necessarily related to what you are trying to do.

Regards.

---

### Post by ventrical on 2015-01-15
Actually I broke down and used gparted to create a ext4 primary partion on 140GBs of unallocated space. I marked it as root and the install has completed.  I first had to follow the suggestion put up by Ubiquity to unmount two partitions - and then the install went seamless - so it appears it is not Ubiquity problem/bug.

Ok .. so restart now.

---

### Post by ventrical on 2015-01-15
> **grahammechanical said:**
> Last week I had 2 attempts to install Vivid daily images and both failed partway through with ubi-console failed. You could be seeing issues with the daily images and not necessarily related to what you are trying to do.

Regards.


The install went beautifully.  It is all in how we (I) use  gparted.  From my last experiment I left 140GBs Unallocated on a seagate hdd and thought that Ubiquity from the 14.04.1 daily would be able to detect it as <free-space>. Did not happen. However .. the system is no longer borked. also on that seagate is windows 8 system. Then there is primary Hitachi 80GB hdd with ubuntu 14.04 and windows bootloader on there- all in UEFI mode.

 So the moral of this story is that noobs with *custom systems* and UEFI will have to learn how to use gparted and <something else> in Ubiquity.

 Just on a side note .. xubuntu desktop seems to be developing more smoothly as time goes along..

Regards..

---

### Post by sudodus on 2015-01-15
> **ventrical said:**
> ...
 So the moral of this story is that noobs with *custom systems* and UEFI will have to learn how to use gparted and <something else> in Ubiquity.
...
Regards..

I've been following this thread :-)

I think your result is supporting the conclusion that it is important to teach and learn how to use the partitioning option ***Something else*** in the installer :-)

---

### Post by ventrical on 2015-01-15
> **sudodus said:**
> I've been following this thread :-)

I think your result is supporting the conclusion that it is important to teach and learn how to use the partitioning option ***Something else*** in the installer :-)

Precisely .. and I take full responsibility for this fail as I took it upon myself to have some of this prepared (even during last cycle)  in an area of the testers/wiki titled Instructional Development and I have yet to contribute anything of any substance  that pertains to this topic specifically.

[https://wiki.ubuntu.com/devel-tester-wiki#Instructional_Development](https://wiki.ubuntu.com/devel-tester-wiki#Instructional_Development)

I think I need some nudging along .. :) lol ... or some links would help.   The thing is. is that the time I spend setting up and contributing content to Instructional Development is time I could be spending on testing UEFI scenarios.

@sudodus, graham..

 If you both know of any pertinent links or wikis on the subject so I could source mine from there - would be appreciated.

Regards..

---

### Post by ventrical on 2015-01-15
Here it is.

> 
The installer is one of the first experiences in Ubuntu that new users  have, and it's critical that we make it a compelling one. The  installation should be rock-solid. Every person who fails to install  Ubuntu is likely one less person who will use Ubuntu. 


[https://wiki.ubuntu.com/Ubiquity](https://wiki.ubuntu.com/Ubiquity)

last updated May, 2013..

---

### Post by ventrical on 2015-01-15
This is where the 'manual partitioning' link from that page leads to:

[http://iso.qa.ubuntu.com/qatracker/testcases/1302/info](http://iso.qa.ubuntu.com/qatracker/testcases/1302/info)

For a noob it is rather forensic.

Regards..

---

### Post by ventrical on 2015-01-15
Found a gem here.  (Sorry for off topic) .

[http://manpages.ubuntu.com/manpages/natty/man8/oem-config.8.html](http://manpages.ubuntu.com/manpages/natty/man8/oem-config.8.html)

I think  that all of this may have to do with :

--no-migration-assistant and --only options from terminal. THEN I hypothesize that if --only option is being used and ubiquity is THEN a stand alone program that it will unmount  all drives/partitions , reset them and then detect possible <free/unallocated> partitions.

 The --no-migration-assistant option may be as equally as beneficial as it will not then pre-empt partitions as they will then be excluded (if what I think that the algorithm is arranged in the detect module of the start up script) or so I assume.. and then detecting <free/unallocated> and offer up graphical option to install to second hdd.



Regards..

---

### Post by sudodus on 2015-01-16
Installing Ubuntu into a whole drive should be and is straight-forward. But I'm afraid that ***dual booting is complicated by nature***, and except some standard cases, it will need special attention and manual partitioning alias 'Something else' in Ubiquity terminology. This is actually a rather unfortunate way that many people are introduced to Ubuntu (and similarly to other linux distros).

It might be better with a wiki page, where newcomers are instructed to

0. create an Ubuntu flavour boot DVD/USB drive

1. shrink the Windows partition with windows tools (while booted from Windows)

2. boot from the Ubuntu flavour boot DVD/USB drive

a. create partitions with gparted

b. start the installer and select Something else at the partitioning window

c. go ahead in a way similar to what Elfy describes in the testing tracker [http://iso.qa.ubuntu.com/qatracker/testcases/1302/info](http://iso.qa.ubuntu.com/qatracker/testcases/1302/info), but to use the partitions created with gparted.

---

### Post by ventrical on 2015-01-16
> **sudodus said:**
> Installing Ubuntu into a whole drive should be and is straight-forward. But I'm afraid that ***dual booting is complicated by nature***, and except some standard cases, it will need special attention and manual partitioning alias 'Something else' in Ubiquity terminology. This is actually a rather unfortunate way that many people are introduced to Ubuntu (and similarly to other linux distros).

It might be better with a wiki page, where newcomers are instructed to

c. go ahead in a way similar to what Elfy describes in the testing tracker [http://iso.qa.ubuntu.com/qatracker/testcases/1302/info](http://iso.qa.ubuntu.com/qatracker/testcases/1302/info), but to use the partitions created with gparted.


Thanks for your input. One thing right off where people get sidetracked. The use of the term FAMILY.  People are actually looking for that word or term, especially noobs. (I know I was at one time) but now I know it means , Ubuntu, Kubuntu, Lubuntu etc...  My point is that it cannot be assumed that everyone will know this terminology  right off the mark so it presents a confusion at the very beginning. No offense intended to no one.

Regards..

---

### Post by grahammechanical on 2015-01-16
I agree that there is an issue with potential new user ignorance but I can only see one way to improve things and that is to make the Live session a live session that only offers an install option at the live session desktop. And have links on the live session desktop to locally stored installation guides.

One of the things that depresses me when I browse the forums to see if I can help is the fact that some who come here with problems have clearly not done any research.

People who today buy new computer devices are more likely to be consumers than hobbyists. Those who need to replace XP and still want to keep the same machine are not likely to be someone who has an interest in how computers work. 

How would the consumer know that Windows 8 = UEFI = install Linux in EFI mode as well? How would the person who still thinks that their XP machine is leading edge know that it may not be compatible with Ubuntu? Unless they do research. Unless the research is available at the live session desktop.

By the way, I do not think that going straight to Install Ubuntu is any quicker than going to the live session desktop and clicking the Install Ubuntu icon.

Regards.

---

### Post by ventrical on 2015-01-16
@graham

 In contradistinction, Windows 8 and previous versions on MS products go straight into install. The newer versions will offer to upgrade or repair. There is no "live" session. People who have used Windows products for the past 20 years understand this. They come to expect it. There are no frills or thrills. People do *not* understand "live" session. It is beyond their understanding that they are actually running an operating system that can do all the things that their windows system does on bare metal from their tiny USB.!!

  As innovative as that is it presents a distraction and so they wait for the bottom to fall out because they are preoccupied with "How can this be?"

  You mentioned that some people come here asking for help and have clearly not done any research.  Just off the cuff, the two links I provided show that they are outdated by well over a year and a half with the exception of elfy's revision at qatracker which is 8 months. That goes for the wayland and the mir wikis (the mir wiki which I updated). So a new convert comes in, wants to research mir or wayland and find that the knowledge bases are over 2 years old then of course they will suspect that the information is deprecated and possibly even unreliable.

  As the first link I provided it stated the truth, that the Installer should be Rock solid!  .. and the information and man pages should also be rock solid also. The installer process should be given just as much priority as the kernel , unity8 or the unity desktop. It's not that the general function of the installer is fundamentally flawed , its' the english translation and how it is intergrated with the GUI that fails to educate in an informative manner.

  So , my point is , as a tester, I often find myself researching subjects and coming up with outdated wiki links and then oblige myself to try and make them more current.

---


  I think the one shot live option could clear up a lot of confusion and an installer helper link icon too.

Regards..

---

### Post by sudodus on 2015-01-16
I agree that the installer should be rock solid, and the information too. And the information should be very available (it should come with the iso file).

I think that one problem with a wiki system is that there are several people who are active for a limited period of time and then leave. Instead of updating their wiki pages, they are often amended (things are added) but out-dated information remains. There are also several wiki pages that 'compete' with the same or very similar subject, and it is hard to find relevant information, particularly for beginners. The personal guidance at our Ubuntu Forums helps people find what is relevant, but I think it is important to help people by providing help without searching (like when the information about the installer comes with the iso file).

I don't understand what you mean by 'I think the ***one shot live option*** could clear up a lot of confusion'.

Please explain :-)

---

### Post by grahammechanical on 2015-01-16
> [COLOR=#000000]I think the one shot live option could clear up a lot of confusion[/COLOR]

It would certainly remove Windows from a lot of machines! :) When someone posts that they have installed Ubuntu and can no longer load Windows, I am tempted to post, "That's the Plan." :)

Now, I know that you are not meaning for the installer to remove Windows. But I do not think that a Microsoft installer will offer an "Alongside" option unless it is to install alongside an existing Microsoft OS. But Ubuntu has to offer exactly that.

Let us not dispute about jargon used among ourselves. Perhaps we need to say Try Ubuntu session instead of Live session. OK. I have re-programmed my mental lexicon.

Regards.

---

### Post by ventrical on 2015-01-16
> **sudodus said:**
> I agree that the installer should be rock solid, and the information too. And the information should be very available (it should come with the iso file).

I think that one problem with a wiki system is that there are several people who are active for a limited period of time and then leave. Instead of updating their wiki pages, they are often amended (things are added) but out-dated information remains. There are also several wiki pages that 'compete' with the same or very similar subject, and it is hard to find relevant information, particularly for beginners. The personal guidance at our Ubuntu Forums helps people find what is relevant, but I think it is important to help people by providing help without searching (like when the information about the installer comes with the iso file).

I don't understand what you mean by 'I think the ***one shot live option*** could clear up a lot of confusion'.

Please explain :-)

Firstly, a big +1 to what you just wrote:). You hit the nail on the head.  Allow me to be a little personable (and even off topic) :)  I live on the northern bank of the Detroit River in Canada (look it up). The river is currently frozen solid (polar vortex) so maybe some of my Swedish and Norweigan  colleages can understand. :) lol   The main point ... I live at the Centre of the Automotive Capital of the world. Sergio Marchionne, CEO of FIAT Chrysler just pumped 2 Billion dollars Canadian into our mini-van plant here in Windsor. Currently we have the North American Auto Show, the single largest auto-show in the world going on , open to the public in Detroit MI. With all the industry and technology I am surrounded by I still have people looking at me like I am from Mars as soon as I mention the word 'Ubuntu'.

  The point being that Ubuntu has a marketing problem in North America. (I had discussed this with Cariboo in length a few years ago in another forum). Mark Shuttleworth had set a goal that he would have over 200 million Ubuntu users by a certain date - and it did not happen.

 Now , addressing your question about "one shot live option'. What I mean by that is that the daily/currents should load right into the live session (as graham suggested) and have the Installer Icon  'Install (n)buntu' and also have a link to an Installer Help Page.

  However.. as I am going along here I see that there would need to be some heavy lifting done by the maintainers of certain modules . Another option would be to offer up a "live-only" iso option from the daily cdimage.ubuntus links.

 Before UEFI Ubiquity , for the most part, could do no wrong. Now with the UEFI option and Windows 8 (and 9, 10 .. onwards) there are complexities that offer a plethora of downtime at the keyboard to try and configurate.

> 
I think that one problem with a wiki system is that there are several  people who are active for a limited period of time and then leave.  Instead of updating their wiki pages, they are often amended (things are  added) but out-dated information remains.


Mea culpa!  I just got done a big job  and hope to have time to update Instructional Development. I know that basically elfy , cariboo and few others are the only ones who seem to pick up all the slack. I think the solutioin is that we just have to MAKE the time to update/upgrade the wikis we have started. I know you are vigilant about the ones you maintain.

Hope I answered your question. Ubiquity needs an overhaul because it is basically the marketing face of Ubuntu and if it fails there, it will fail elsewhere. To me, Mark Shuttleworth is a saint of a man but he has to get it through his head that he just can't let Ubiquity sleep on the shelf and collect dust, especially if he wants those 200 million solid desktop users.. and IMHO .. with convergence ... it ain't going to happen unless they hallmark ubiquity, almost like sort of requesting permission to board a ship. 
Regards..

---

### Post by ventrical on 2015-01-16
> **grahammechanical said:**
> It would certainly remove Windows from a lot of machines! :) When someone posts that they have installed Ubuntu and can no longer load Windows, I am tempted to post, "That's the Plan." :)

Now, I know that you are not meaning for the installer to remove Windows. But I do not think that a Microsoft installer will offer an "Alongside" option unless it is to install alongside an existing Microsoft OS. But Ubuntu has to offer exactly that.

Let us not dispute about jargon used among ourselves. Perhaps we need to say Try Ubuntu session instead of Live session. OK. I have re-programmed my mental lexicon.

Regards.


 My apologies again for my  bad Canadian vernacular:)  I meant to say it would be good to be able to just boot into the live session with the Install Ubuntu icon and a couple of Installer help Links.

Regards..

---

### Post by sudodus on 2015-01-16
Thanks for the long post - quite interesting points. And yes, our Luleå River is also frozen.

> **ventrical said:**
> Now , addressing your question about "one shot live option'. What I mean by that is that the daily/currents should load right into the live session (as graham suggested) and have the Installer Icon  'Install (n)buntu' and also have a link to an Installer Help Page.

  However.. as I am going along here I see that there would need to be some heavy lifting done by the maintainers of certain modules . Another option would be to offer up a "live-only" iso option from the daily cdimage.ubuntus links.

 Before UEFI Ubiquity , for the most part, could do no wrong. Now with the UEFI option and Windows 8 (and 9, 10 .. onwards) there are complexities that offer a plethora of downtime at the keyboard to try and configurate.


I see, you want to put more focus on running Ubuntu live, maybe that people stay longer at the stages described at this link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

In that case I think we should change the terminology because ***try*** is not serious enough :-P

Ubuntu performs well with USB 3 (and improved flash hardware), and it will really make things much easier (than to fight with non-standard or even buggy UEFI, that makes it too complicated for average users to dual boot within the internal drive).

---

### Post by ventrical on 2015-01-16
> **sudodus said:**
> Thanks for the long post - quite interesting points. And yes, our Luleå River is also frozen.



I see, you want to put more focus on running Ubuntu live, maybe that people stay longer at the stages described at this link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

In that case I think we should change the terminology because ***try*** is not serious enough :-P

Ubuntu performs well with USB 3 (and improved flash hardware), and it will really make things much easier (than to fight with non-standard or even buggy UEFI, that makes it too complicated for average users to dual boot within the internal drive).

I'll use that as a hotlink at the tester wiki.

[https://wiki.ubuntu.com/U+1/tester-wiki#Instructional_Development](https://wiki.ubuntu.com/U+1/tester-wiki#Instructional_Development)

---

### Post by ventrical on 2015-01-16
> **sudodus said:**
> Thanks for the long post - quite interesting points. And yes, our Luleå River is also frozen.



I see, you want to put more focus on running Ubuntu live, maybe that people stay longer at the stages described at this link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

In that case I think we should change the terminology because ***try*** is not serious enough :-P


The common english PC venacular that most everyone understands is ***run !***

ie; ***Run Ubuntu live/Install Ubuntu  ***

That is way more sassy, effervescent and 'sexy' as Mark would say :) Even 6 year olds know how to ***run ***a program and what it means. The 'before installing it' thread is already inferred because of the second option. People are not stupid .. even noobs can figure that one out.

Regards..

Edit:

Just a side note: I am only meaning in the N/A english venacular. Those terms may not be immediately clear in another language or even in english slang dialects...

---

### Post by sudodus on 2015-01-16
You are right, ***run*** is better than ***try*** :-)

Do you mean that I should change the title of my tutorial thread?

---

### Post by sudodus on 2015-01-16
Its getting late here. Good night!

---

### Post by ventrical on 2015-01-16
> **sudodus said:**
> You are right, ***run*** is better than ***try*** :-)

Do you mean that I should change the title of my tutorial thread?


  I wasn't making that inference , but, now that you mention it... In ComSci 101 we were taught "a computer is a dumb terminal. It will only do what you tell it to do."   The term 'try' is somewhat ambiguous. There is no directive.. for example .. 'try to run ubuntu'.    One could also use the term 'attempt to run ubuntu'.. so there is some fuzzy logic here.

  As you know in programming language there is no such thing as ***try.*** It is ***do, get, pop, peek,poke. DIM,MAT,for,next, if, then,else...etc..***  we do not write 'try to do', try to get', 'try to pop'... etc.. Most end_users that I have worked with  prefer the direct method. 'Open the file'. Ok.. so it crashes. No what do I do? Try again? yes.. In that context 'try' is unambiguous because it referrs to a redundant attempt at a command that failed an argument.  I honestly think it is preferential , depends on conditions and is ultimately left up to the author.

Regards..

---

### Post by sudodus on 2015-01-17
Another and maybe better alternative:

- Leave the tutorial thread as it is, the terminology matches what you see in the installer: 'Try Ubuntu ...'

- Make a wiki page with the corresponding content and integrate it into the wiki structure, that you are working with. (I can volunteer to make that wiki page, and maybe ultimately replace the tutorial with a link to the wiki page instead of maintaining two similar help pages.)

---

### Post by grahammechanical on 2015-01-17
> [COLOR=#000000]Leave the tutorial thread as it is, the terminology matches what you see in the installer: 'Try Ubuntu ...'[/COLOR]

Ah. It is much easier to change the words we use and the words in a wiki page than to change the writing in the dialog boxes. The English language is overloaded with words but I am having difficulty coming up with a replacement for "Try Ubuntu without installing."

Practice Ubuntu, anyone? Experiment Ubuntu? Trial Ubuntu? Inspect Ubuntu? These also have other meanings in other contexts. That is it. I have reached the limits of my vocabulary. :)

Not, quite. One more. Examine Ubuntu.

Regards.

---

### Post by ventrical on 2015-01-17
> **sudodus said:**
> Another and maybe better alternative:

- Leave the tutorial thread as it is, the terminology matches what you see in the installer: 'Try Ubuntu ...'

- Make a wiki page with the corresponding content and integrate it into the wiki structure, that you are working with. (I can volunteer to make that wiki page, and maybe ultimately replace the tutorial with a link to the wiki page instead of maintaining two similar help pages.)


After thinking really hard on this I think you are right. If it is not broke don't fix it :)

Try Ubuntu is just perfect.

> 
- Make a wiki page with the corresponding content and integrate it into  the wiki structure, that you are working with. (I can volunteer to make  that wiki page, and maybe ultimately replace the tutorial with a link to  the wiki page instead of maintaining two similar help pages.)

Sounds good to me and I have seen from your wikis that they are very detailed and informative.  I am not sure how many people visit the testers' wiki or the alternate devel wiki.  But you know you are free to alter, amend or append what ever I have composed at those pages. In fact I encourage more of this. We should all get involved more.  Oh .. and as for your current tutorial, some users  are wired to check the ubuntuforums tutorials and even google sniffers pick them up a lot faster than wiki sites so it's not really a duplication .. just an alternate location to view the KB.

Regards..

---

### Post by ventrical on 2015-01-17
> **grahammechanical said:**
> Ah. It is much easier to change the words we use and the words in a wiki page than to change the writing in the dialog boxes. The English language is overloaded with words but I am having difficulty coming up with a replacement for "Try Ubuntu without installing."

Regards.

 It makes perfect sense. +1 .. no need to change it.  What was I thinking ?  :)

Regards..

---

### Post by sudodus on 2015-01-17
> **ventrical said:**
> [QUOTE=grahammechanical;13209503]Ah. [COLOR=#ff0000]It is much easier to change the  words we use and the words in a wiki page than to change the writing in  the dialog boxes[/COLOR]. The English language is overloaded with words but I am  having difficulty coming up with a replacement for "Try Ubuntu without  installing."

Regards.

 It makes perfect sense. +1 .. no need to change it.  What was I thinking ?  :smile:

Regards..[/QUOTE]

+1

---

