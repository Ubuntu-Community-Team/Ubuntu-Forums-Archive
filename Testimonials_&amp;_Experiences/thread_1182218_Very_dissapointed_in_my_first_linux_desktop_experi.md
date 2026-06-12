---
title: "Very dissapointed in my first linux desktop experience!"
date: 2009-06-08
forum: Testimonials &amp; Experiences
---

### Post by a$$core on 2009-06-08
Hello. 

I decided to finally try out ubuntu, after hearing so many good things about it.

The desktop and everything relating to the OS seems great.  

However my wireless card isnt working (dwl-g650).

I have been reading forum posts and other info on the web for 3 hours now, and am totally baffled.

Apparently I need madwifi,  ndiswrapper, all this other crap.  Even then it wont work with WPA?  Millions of commands entered into the prompt.    I CANT FIGURE THIS CRAP OUT!

If people are going to get on the linux bandwagon it is going to have to get ALOT simpler than this.  Like no command line simple.  

I've burnt out my memory on reefer a long time ago, there is no remembering hundreds of text commands, their order, etc.  It just needs to work.  

Even if I were to learn all of this crap, it would take several years of constant use, which I cant do IF I DONT HAVE INTERNET.  It's a catch 22.  I cant have internet because I cant install the shite to make it work.  I cant learn how to make the shite work because I cant use the laptop constantly, because I dont have internet!

Can anyone point me to a super simple method to install whatever I need to make this wireless card work?  If the directions include command line I need every single command in order to do it.  

Also, if this problem is so common, why the hell isnt the stuff to make it work included in the ubunto OS?

---

### Post by Locutus_of_Borg on 2009-06-08
the solution is incredibly simple and requires no command line whatsoever


use compatible hardware


would you call windows difficult to use if it doesnt immediately work perfectly when you install it on a playstation 3?




what does lspci|grep Network output?

from what i read, the dwl-g650 should work out of the box on the latest ubuntu

---

### Post by Iowan on 2009-06-08
> **a$$core said:**
> Also, if this problem is so common, why the hell isnt the stuff to make it work included in the ubunto OS?Not all wireless card manufacturers feel the need to develop drivers for Linux.  Some have dropped support for older versions, so what might have worked in previous version of Ubuntu lo longer does.  In general, Jaunty natively supports far more wireless cards than previous versions... but not ALL...(yet).

In case you need more reading material, [this]("http://ubuntuforums.org/showthread.php?t=1176117") sticky covers some of the Jaunty workarounds.It's also possible that the wireless card is working, but another problem is preventing internet connection.

---

### Post by MrFSL on 2009-06-08
You know, I usually don't respond to these kind of posts; yet seeing that this is your first post.... here goes.

First, I understand your frustration. I came to Linux many years ago, when dial-up internet was king, and configuring modems meant that you had to already understand Linux as well as the AT command set and other modem technology such as PAP and CHAP etc.

Now, what you have to understand is that you need the appropriate drivers (special software to interface with your hardware) in order to get your equipment working. The problem is that not all manufacturers write drivers for Linux. People that are on Mac have the same issue. In Linux though, there are a lot of friendly people who spend a good deal of time getting hardware, like your wireless card, working even though they have no vendor supplied Linux drivers.

Drivers are an extremely complicated bit of software regardless of what operating system you are using. What you are actually saying in your post is: "I am having a terrible time with Linux because my **_Windows only_** Wireless Network Card doesn't work without some effort. 

Now, when we state it like that it sounds kind of silly doesn't it? Also, understand that there is a difference between "ease of use" and what is "easy to you." If you have never used the command line interface before it might seem difficult. But most people I know that use Linux extensively start using this CLI more and more because they find it is fast and easy.

Lastly, Linux is not for everyone. If you don't want to buy new hardware and your existing hardware doesn't support Linux, perhaps now is not a good time to switch. For 90% of all people I know that have converted to Linux, everything "just works" right out of the box.

Sorry your experience was bad.

---

### Post by Yellow Pasque on 2009-06-08
Install the two ndiswrapper packages (they're on the Ubuntu CD). You also need some way to get the Windows drivers to your laptop (USB key, burn a CD).

---

### Post by LMZKJ on 2009-06-08
For MrFSL...

Very well said!  +1

---

### Post by jbruced on 2009-06-08
Sorry for your pain, and Sir, I firmly believe that if the tone of your post was more of a request than a rant about what you deserve, that you would find lots more fun and helpful people trying(and eventually succeeding) to bring you to a beautiful, stable, virus free, new operating system.

We ALL love Ubuntu here because it works. 

Please have some patience and be willing to learn.

GL
Bruce

---

### Post by Mirge on 2009-06-08
Please don't rant about Linux and then at the same time ask for support. I think the above posters summed it up quite nicely.

When you cool off, try using: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Polaris96 on 2009-06-08
LINUX and Ubuntu are FREE.  You pay your dues but take the knowledge with you.  Ever tried poking the windows registry??

Anyway, get a dlink adapter like this one from Tiger for 50bucks:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3321383&CatId=2704](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3321383&CatId=2704)

It's FASTER than what you have, and it will work with Ubuntu.  Move Forward!  you'll thank yourself when you're surfing faster.

After you're linked in, you'll start to complain about: flash, java, and playing DVDs.  We will be here.  Walk on, glasshoppah.

---

### Post by monkeyslayer56 on 2009-06-08
well if u can get it to work withouot WPA or use a wired conenction for me when i had a similar probablem i could only et wep so i lowered my wireless security to match that and then after a update or 2 i relized i was able to connect to a wpa network so if u can connect wired long enough to run updates that may or may not work 
sry i couldn't help more

---

### Post by cybergalvez on 2009-06-08
don't bitch, no one gets paid to do to this, you got ubuntu for free, when was the last time you got a free copy of OSX or Windows? Also if you're pissed that your hardware does not work, why don't you blame the guys who make the hardware for not making linux friendly drivers?  If you have a question ask nicely, otherwise one one will listen or help.

---

### Post by pricetech on 2009-06-08
> **a$$core said:**
> 
I've burnt out my memory on reefer a long time ago

And there's your problem.

---

### Post by Mirge on 2009-06-08
> **pricetech said:**
> And there's your problem.

Ha, I didn't even notice that... agreed, there's your problem.

---

### Post by rcayea on 2009-06-08
> **LMZKJ said:**
> For MrFSL...

Very well said!  +1




Ditto +2

---

### Post by Nythain on 2009-06-08
heh, with thsi many replies and not a single second response, one could only assume the user said his "ubuntu needs to be windows" peace and went back to windows

for anyone else reading this, i do so wish people would learn to stop blaming hardware/driver issues on an os and start blaming the hardware manufacturer like mentioned... its not linux or ubuntu's fault that some companies consider windows the only os

also, even xp doesnt know what your wireless card is without third party drivers, wich puts the up to date factor of linux miles above and beyond that of the most popular microsoft os

---

### Post by QIII on 2009-06-08
Sorry fellas.

The snarky responses are just what lead people to believe that our community is a bunch of snooty geeks that turn our noses up at noobs.

Remember that we were all noobs at one time.

The correct answer, even for someone who is ranting, is something like:

We're sorry you are having problems with a product that we all find to be extremely good.

But because Linux holds such a small market share, some hardware manufacturers do not bother to make their proprietary drivers compatible with Linux.  The issue you are having is not with Ubuntu, but with a hardware driver.

If you give us some time, we will try to see if we can find a solution to your issue.

---

### Post by Mirge on 2009-06-08
> **QIII said:**
> Sorry fellas.

The snarky responses are just what lead people to believe that our community is a bunch of snooty geeks that turn our noses up at noobs.

Remember that we were all noobs at one time.

The correct answer, even for someone who is ranting, is something like:

We're sorry you are having problems with a product that we all find to be extremely good.

But because Linux holds such a small market share, some hardware manufacturers do not bother to make their proprietary drivers compatible with Linux.  The issue you are having is not with Ubuntu, but with a hardware driver.

If you give us some time, we will try to see if we can find a solution to your issue.

Some ppl here (myself included) thoroughly enjoy using Ubuntu (or a variant) and hold it dear... so when someone comes ranting & raving about it, and explains away why he shouldn't be troubled to do some research and/or work at it because he smoked too much pot... well, my response to that is we are volunteering our time here, and certainly nobody is obligated to help. We do it because we want to contribute. But for someone to come in with the approach he took, it's bound to generate undesirable responses.

---

### Post by QIII on 2009-06-08
And those undesirable responses feed the stereotype.

We all love Ubuntu, or we wouldn't be spending our time here.

The fact that we are volunteering is immaterial.

The ill behavior of others does not justify our own.

---

### Post by Mirge on 2009-06-08
Fair enough. Not going to start a fight. I'm out of this thread.

---

### Post by a$$core on 2009-06-08
I wasnt trying to start a flamewar, although I will admit I was ranting.  I work in a technical field, so I am very much used to finding my own solution to problems.  Not being able to do this made me quite aggrivated.  

I am a graphic designer / web designer / css and cms guy , and i have to use very basic linux in my job (not much more than knowing how to navigate directories / wget / unzip-tar / ftp / restart apache /msql etc.)

Now that I have had time to cool off, I realize that I was pretty much trying to be a dick.

However I still feel that some of my point is valid.  I know that the mfg doesnt supply drivers for linux in many instances.  However it was my understanding that the linux community was at the point where they have worked their way around these issues in almost all instances (hence all the talk that novices such as myself should give it a go).   

My complaint is mainly that the learning curve is so steep.  There isnt much effort put into usability, because it is assumed you are a linux guru right off the bat.

---

### Post by mark bower on 2009-06-08
@a$$core

after your forum drubbing, i hope you return and see this response.  i had trouble with any number of wireless PCI cards i own.  if you have USB available, i recommend you purchase a Belkin USB F5D7050.  it was recommended to me by two other parties, and works for me (out of the box - immediate connection to router) on multiple computers, all of them using ubuntu 8.10. it requires no other drivers (eg using ndiswrapper).

i share your frustration.  i requested help any number of times and with bumps to try and get help with my bluetooth dongle, and received no responses.  i am now looking to try and get support from a Linux Users Group (LUG).  the major problem i see with this site is that posts are made with such rapidity, that one's post quickly gets buried, much like craig's list.  thus, a post tends (certainly not always) to move rather quickly to the rear.

---

### Post by QIII on 2009-06-08
a$$core --

The Linux community has worked as fast and furiously as they can to come up with as many workarounds as possible.  There are people who do what they can to come up with open source solutions to a lot of these sorts of problems.  They do it on a volunteer basis.

Unfortunately, the Linux community does not have the Monopoly of Redmond to use as a way to twist arms into compliance.

---

### Post by sendblink23 on 2009-06-09
Here is a tiny suggestion, that I always do.. when installing any type of Live CD Linux OS ... 

*this suggestion is only for users who don't want to mess with complicated commands etc... to have running their wireless*

Well if by running the LIVE CD if it does not give you the possibility/ability to be able to connect to the internet by clicking the icon & choosing Wireless(having shown a near connection) ..  well simply forget about that *Flavor.. go for another one to test

Now I know it is not a good suggestion reply... but hey at least you would KNOW straight OUT.. BEFORE installing the OS to your machine.. if it works *out-Of-The-Box

The other would Install the OS through WUBI.. if you had Windows installed in the Machine.. its a perfect way to get everything working(and learning of using Linux)

As for my experiences.. I have done it with all command ways & sometimes gotten lucky out of the box working things also...  and the Best Solution for Wireless if yours doesn't work GET IT ON EBAY .. a USB Wireless (pretty sure you will see: Netgear WG111v2  around $10 - $15 on Ebay) its cheap and it works out of the box

---

### Post by LuvinLinux on 2009-06-09
Just thought I'd share a different experience.  Several months ago, I decided to quit stealing Windows software and try something different.  I had always been the guy my friends would come to with computer problems so I figured I shouldn't have too many problems figuring out this whole Linux thing.  I installed Ubuntu Hardy and had a pretty good experience (I did have to do a bit of work to figure out why I had no desktop after logging in: older Nvidia card, needed to disable desktop effects).  After getting this worked out things went pretty smoothly.  When Intrepid came out I decided to forego the whole dual-booting thing as I hadn't used Windows in quite a while.  Awesome decision, never going back.

I've just recently upgraded to Jaunty on my laptop (still running Intrepid on the desktop) and am having some issues (see below) but overall Jaunty seems pretty great.

I still have a crazy amount to learn about Linux but with the help of many knowledgeable and helpful Linux users I've been picking things up along the way and have been able to get things working the way I need them to.

Overall, my Ubuntu experience has been quite good: Virtually all my posts have been responded to in a very timely fashion by knowledgable and helpful people.  It's quite refreshing actually, compared to forums for windows support.  I guess what I'm trying to say is thanks to all of those who have decided to put in a lot of time and effort to make my experience and that of those like me a positive one.  

  Now comes to the problem I'm having with Jaunty, ironically it is the same one which started out this thread: my DWL-G650 rev. B wireless card stopped working.  I remember somewhere along the way I had to do a bit of  work to get it up and running, but can't recall whether I was using ndiswrapper or what.  Any way, it was working for the first day I had Jaunty running but then decided it wasn't going to be able to connect to my network anymore.  I tried following some instructions for using ndiswrapper but it didn't seem to make any difference. Anyway, if anyone is interested/able to help me figure this out it would be greatly appreciated.  

Thanks in advance:)

---

### Post by QIII on 2009-06-09
Does the card work on another machine?

Might be a hardware problem if it stopped working suddenly.

Things break.  Give that a try, if just to rule out hardware.

---

### Post by keplerspeed on 2009-06-09
I dont think anyone's first experience would be flawless. I had to replace my lexmark printer with a HP since I couldnt get the lexmark to work.

---

### Post by a$$core on 2009-06-09
> **mark bower said:**
> @a$$core

after your forum drubbing, i hope you return and see this response.  i had trouble with any number of wireless PCI cards i own.  if you have USB available, i recommend you purchase a Belkin USB F5D7050.  it was recommended to me by two other parties, and works for me (out of the box - immediate connection to router) on multiple computers, all of them using ubuntu 8.10. it requires no other drivers (eg using ndiswrapper).

i share your frustration.  i requested help any number of times and with bumps to try and get help with my bluetooth dongle, and received no responses.  i am now looking to try and get support from a Linux Users Group (LUG).  the major problem i see with this site is that posts are made with such rapidity, that one's post quickly gets buried, much like craig's list.  thus, a post tends (certainly not always) to move rather quickly to the rear.

I posted again, last post on page 2.  Thank you for the recommendation.

> **QIII said:**
> Does the card work on another machine?

Might be a hardware problem if it stopped working suddenly.

Things break.  Give that a try, if just to rule out hardware.

Yes, the card works on the windows partition of the same laptop.

Also, QIII thanks for trying to be understanding of my frustration.

---

### Post by Nythain on 2009-06-09
> **keplerspeed said:**
> I dont think anyone's first experience would be flawless. I had to replace my lexmark printer with a HP since I couldnt get the lexmark to work.
my first experience was flawless, but i was runnin some ancient hardware, and im always hardwired :P

---

### Post by Russell_S on 2009-06-09
I just thought I'd add my thoughts as a Linux newbie.

I have been using Ubuntu now for about 3 days and am enjoying the experience. I do understand where a$$core is coming from but I definately do not agree with ranting on a forum, it just puts peoples backs up.

I think that most Linux newbies, like myself, will come from a Windows background and have a reasonably good technical knowledge of computer hardware and the Windows OS. When they have a problem with Windows that they are struggling with, they will ask a question on a Windows based forum and get an answer that they can understand and then, hopefully, fix the problem. I think the reason people get so frustrated with Linux is that you don't always understand the answers. For instance, with Windows if you are having a problem getting a new piece of hardware working, you may get a forum response like "You need to remove the old driver and then load the new 2.3.7 driver " and then you know what to do from there. The same problem with Linux however is completely different. The response "You need to load the newer driver" certainly tells you why the hardware isn't working but you still have absolutely no idea where to go from there. This is what is so frustrating when you are used to being in control and understanding what is needed and now finding yourself totally out of your depth and needing step-by-step instructions just to load a new driver.

I also think that newbies should maybe ease themselves in gently and start off dual booting so that they don't have to get it all up and running first go. You can take your time and probably find yourself gradually spending more time in Linux and gradually less time in Windows as you get the system running as you like it and also gradually find the Linux applications to replace the ones you use in Windows. This would avoid a lot of the stress involved in moving over to Linux.

Coming from outside the Linux community there is an unfair perception that you are all geeks and don't tolerate people who can't re-compile a kernel from scratch while simultaneously editing a couple of pearl scripts (I havn't a clue what all that meant but it sounded good), however I have not found that at all. The few questions I have asked in these forums have been answered very helpfully and without patronising comments. Everyone seems very freindly and helpfull as long as you ask the questions in the correct way, but then that's the same for most forums.


Russell

---

### Post by Legace on 2009-06-09
> **Russell_S said:**
> -- while simultaneously editing a couple of **pearl** scripts --

It's perl, not pearl.

Anyway, I'm glad you understand. It's impossible to know everything when you first start to do something. You have to be patient and learn, and I'm glad you (and many others) acknowledge that :)

---

### Post by whitefort on 2009-06-09
> **QIII said:**
> 
The snarky responses are just what lead people to believe that our community is a bunch of snooty geeks that turn our noses up at noobs.


Yes.  Very well said.

In bygone years I tried, over and over, to switch to Linux.  What always sent me back to Windows was the sheer smugness and rudeness of people in Linux 'help' forums.

The reason I've been using Ubuntu on ALL my machines since the days of Dapper Drake was that this forum was different.

For me, the transition to Linux was a total nightmare - non-working internet connection, non-working printer, non-working ton of other things that I've forgotten.  When you're used to turning on your PC and everything 'just working', it's no fun to be told that to get something like an internet connection you'll need to follow some rocket-science instructions or buy a new modem.

If it hadn't been for THIS forum, I would have quit again, cursed Linux, and put the Microsoft handcuffs back on.

The helpfulness and politeness of this forum is Ubuntu's greatest treasure.  It would be a shame to see it lost.

---

### Post by Russell_S on 2009-06-09
> **Legace said:**
> It's perl, not pearl.

I did say that I havn't a clue what I was talking about ;). Actually, I think I did enter it correctly but the Firefox spell checker corrected it* incorrectly*.

I have to say though that I installed Ubuntu 3 days ago on my laptop (dual boot) and was so impressed that the same day I installed it on a second disk on my desktop (also dual boot), and since then the only reason I've booted back into Windows is to play a game of Call Of Duty with my son. I have now installed Virtualbox with Windows XP as guest just for the windows apps that I just CAN'T live without (at this stage) but they are few and far between.


Russell

---

### Post by TheLions on 2009-06-09
i found drivers for your card:

[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/) (if you have Texsas instruments chipset)
instructions here: [http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

[http://madwifi-project.org/](http://madwifi-project.org/) (if ayou have Atheros chipset)
install it clicking here [apt:madwifi-tools]("apt:madwifi-tools")

---

### Post by nothingspecial on 2009-06-09
The command line is not difficult it`s just different from what your used to. I use it all the time, not for everything, but for alot of things it`s just quicker and easier than pointing and clicking.

It just takes a bit of time to get used to. I recently got a desk at work with a pc on it running windows. I hated it because I didn`t have a clue what I was doing (I`m one of those rare species that started out with linux). So, I can understand how you feel. In the end they let me install linux on it but that`s not the point.

I`ve heard it said that learning linux isn`t hard - it`s unlearning windows that takes the time. And I suppose I`m not one to talk because I gave up with a new os. But the point is give it some time, this is completely different but no harder. 

> **a$$core said:**
> 
I've burnt out my memory on reefer a long time ago,

Me too, but I manage ;)

---

### Post by Polaris96 on 2009-06-09
Regarding a$$core's trial by moshpit.  I have little sympathy because he pretty much walked in and said, "your Mutha," to the nice people, here (and, looking back, we WERE nice).  

LINUX, like or not, DOES have some fraternal aspects, and one has to expect a spirited response if the first words he speaks are discourteous and belligerant.

That said, Kudos to a$$core for hanging in and admitting he was spun up.  I think that was a pretty good intro to the community.

Regarding Linux's craziness, it's the reality of open source life.  I came over after having had enough of expensive programs that didn't work right.  Now, I mostly use free programs that don't work right ... at first.  We trade a lot for transparency, but usually, if you stick with it long enough, you get things to work.  When you do it feels good.


...by the way, Lions,   does apt-get pizza really work?  if I use apt-get install can I still eat it manually?  maybe dpkg would be a more enjoyable way...  

By the way, the only things that have ever defeated me, so far, are finding a USA Sprint Chatscript that works for barry (pissed that I STILL can't tether my damned Blackberry Modem), and, as with a$$core, my linksys 802.11b PCMCIA card never yielded no matter what I tried.  

Upgrading to a dlink USB n wireless adapter worked gr8 - right out of the box.  Best way to go - improve hardware and get compliance in one fell swoop.

One of the mixed blessing of this OS is that you're going to learn 50ways to do anything, then forget 5 of them and shake your head trying to remember what you did when your stuff is dead after an upgrade.  It seems to be getting easier, or maybe I'm just getting used to things at last.

Hang in,  before you know it, you'll have a quake terminal for admin and a truckload of beans.

---

### Post by ManyBeers on 2009-06-10
> **a$$core said:**
> Hello. 

I decided to finally try out ubuntu, after hearing so many good things about it.

The desktop and everything relating to the OS seems great.  

However my wireless card isnt working (dwl-g650).

I have been reading forum posts and other info on the web for 3 hours now, and am totally baffled.

Apparently I need madwifi,  ndiswrapper, all this other crap.  Even then it wont work with WPA?  Millions of commands entered into the prompt.    I CANT FIGURE THIS CRAP OUT!

If people are going to get on the linux bandwagon it is going to have to get ALOT simpler than this.  Like no command line simple.  

I've burnt out my memory on reefer a long time ago, there is no remembering hundreds of text commands, their order, etc.  It just needs to work.  

Even if I were to learn all of this crap, it would take several years of constant use, which I cant do IF I DONT HAVE INTERNET.  It's a catch 22.  I cant have internet because I cant install the shite to make it work.  I cant learn how to make the shite work because I cant use the laptop constantly, because I dont have internet!

Can anyone point me to a super simple method to install whatever I need to make this wireless card work?  If the directions include command line I need every single command in order to do it.  

Also, if this problem is so common, why the hell isnt the stuff to make it work included in the ubunto OS?

I'll try

I run Ubuntu 8.04 on a Sony Vaio laptop. I have a Dlink DWL-g630 card with the Marvell chipset. There are no open source drivers for the card so I used the Ndiswrapper system. You need to download and install ndisgtk(enable Multiverse&Universe repositories)link  how-to add repositories [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu") using Synaptic Package Manager. When you have the repositories added just hit the search button and type in ndisgtk and it will find the package so you can MARK it for installation.
After you have installed ndisgtk you will need to get the Windows drivers for your card into 
Ubuntu. I have a dual-boot setup with XP/Ubuntu
on my laptop so i just copied the drivers from Windows to a NTFS shared partition and then booted into Ubuntu and copied them to my desktop. Where are the drivers for your card? 
Do you dual-boot? Can you get the drivers for your card into Ubuntu?

---

### Post by rft-hillview on 2009-06-17
I too am very disappointed as a Ubuntu newbie and the first reply to the original post was even more disappointing - unsympathetically suggesting the use of compatible hardware.

I have "moved up" from Puppy Linux where my 3Com 3CCFEM556 B 10/100 + 56K modem card loaded "out of the box". Similarly my D-link DWL-G650+ wifi card loaded " out of the box" - I was literally online within minutes fully connected to my router and the outside world. I even had my network printers up and running inside 1/2 hour from loading the software.

However there are limitations in Puppy Linux and I wanted something a bit more flexible.

I am not certain that in choosing Ubuntu Desktop 9.0.4 that I have chosen the right one.
It does not support either of my available network cards out of the box and instructions on how to use ndiswrapper and find the appropriate drivers for Ubuntu for this black box software to use is difficult to say the least when the computer you want them on is not on the net. What do you want me to do - go back to Windows and use it to solve Ubuntu's problems - sort of defeats to object of the exercise.

A large majority of new Linux users are using it on hardware which by virtue of its age is too old to support the current crop of bloated fatware released on an unsuspecting world by Microsoft. The drivers for virtually everything is available on one Linux platform or another. Reading the Ubuntu forum entries it seems that frequently you have to go back to a previous version of Ubuntu to get the solution to todays problem - at least in this you are not alone.

I know I will get round my coms problems in Ubuntu and because I am retired I will enjoy the battle ahead. However my sympathies are with the originator of this thread.

As a foot note my Toshiba MK5002MPL 5gb drive runs fine in Ubuntu 9.0.4 but NOT on Pupply Linux

---

### Post by MrFSL on 2009-07-04
hum... I'm really not trying to troll here... but... for the record...

My comments weren't meant to be "snarky." I re-read my post and I don't think it sounds "snarky." And I disagree with some of the etiquette suggestions. I think sometimes it is best to explain the issues to the user and NOT recommend Linux (or any other software) as a solution. A user has options. Some might be best served by staying on the O/S they are comfortable with, or have supporting drivers for.

I have educated many a user over the years on Linux, and helped them come to the decision that it really wasn't what they needed/wanted and they were very grateful. Other users picked Linux and have been happy ever since.

If Linux users have a bad reputation I think there is more than one way to remedy this. In my opinion offering solutions outside of the Linux or GNU or OSS arena; (as long as you stay objective) especially when trying to honestly educate the user; is by far a better approach.

In this particular situation, the fastest and cheapest (counting man hours) method to help the user is to recommend Linux compatible hardware (accompanied with an explanation of why). If the wireless was up and running quickly, the user could get a real taste of all the Ubuntu has to offer. I feel I have done this community proud. ;)

Lastly, it is cruel to 'dangle' a person who truly wants to use a Windows like O/S (but is only curious about Linux) with false hopes, wrong impressions, unrealistic expectations, etc. --- and this is why I don't usually (and never again will) reply to posts of this nature.

I apologize to the original poster if I came off as "snarky." AND thank you to those posters who had encouraging comments.

MrFSL

---

### Post by nothingspecial on 2009-07-04
I think very few people participating or reading this thread do think you were being snarky.

You were just telling it like it is.=D>

---

### Post by jflaker on 2009-07-04
Interesting note:
You buy a computer and it all works "out of the box" because the seller, like Dell, has made sure that all your hardware has the proper drivers.

HOWEVER, wipe that same system clean and install Windows from disk and you will find that you have a whole different story......I will guarantee that your video, network, sound, usb and many other important pieces of hardware will not work and you would be required to hunt down and download about 10 or more drivers, install them, reboot, install more, reboot....

Try this:
at the top of your screen...SYSTEM, ADMINISTRATION, HARDWARE DRIVERS....make sure that you have activated the proprietary drivers....those drivers could not be made available on install, but you are permitted to download them....

Once you have those drivers installed, give us an update.

---

### Post by Mirge on 2009-07-04
> **jflaker said:**
> Interesting note:
You buy a computer and it all works "out of the box" because the seller, like Dell, has made sure that all your hardware has the proper drivers.

HOWEVER, wipe that same system clean and install Windows from disk and you will find that you have a whole different story......I will guarantee that your video, network, sound, usb and many other important pieces of hardware will not work and you would be required to hunt down and download about 10 or more drivers, install them, reboot, install more, reboot....

Try this:
at the top of your screen...SYSTEM, ADMINISTRATION, HARDWARE DRIVERS....make sure that you have activated the proprietary drivers....those drivers could not be made available on install, but you are permitted to download them....

Once you have those drivers installed, give us an update.


He couldn't because his networking wasn't working due to drivers. As far as being too "snarky" or what have you, I call BS... I don't think anybody was out of line or rude regarding the OP.

---

### Post by Gizenshya on 2009-07-04
huh? only 5 pages?  but I'm not done with my popcorn :'(

I enjoyed this thread far more than I should have :)

but, anyway...

I fully agree with what QIII said in his posts.

MrFSL's first post didn't cross the line, IMO.  Although, it may not have been quite as helpful as it could have been.  Not being overly negative is not necessarily being overly positive...

In general, with exceptions noted, the repliers to the thread were less willing to help this person with his problem, because of his original post.  I think we can agree on that.

I understand everyone's position... but I think that people like this should be greeted with open arms and our utmost respect.  Now, yeah, that might be hard to swallow after essentially being insulted.. but ohh, well.  It does not help solve anything to be less than welcoming or less than helpful to people like this.  

I ask that if you don't have anything positive to say or add, please refrain from adding 'negative' (ie, not positive) comments in the thread.  Completely ignoring the ranting parts, and only addressing the issues brought up, IMO, is the best way to deal with it.

The last thing I would want would be for someone to go back into the world with a bad taste of Linux in their mouth, only to share their comments with whoever will listen.  Bad experiences get shared far more than positive ones, we all know this.  No matter how their attitude was coming in, it is all but guaranteed that the only thing that would make it into the original poster's future commentary on Linux is the douches on the forums that wouldn't help him.  Saving face on an internet forum is not worth giving GNU-Linux an enemy... no matter how 'right' it may feel at the time.  I say GNU-Linux because it would be generalized, and not limited to Ubuntu, in all likelihood.

Now, I must admit, I've been on both sides of the firing line at one point or another.  But I've (slowly) learned that that sort of thing is never really justified.

And, to be perfectly clear, no, I'm not saying what a$$core posted was in the right.

---

### Post by 3rdalbum on 2009-07-04
> **a$$core said:**
> 

However I still feel that some of my point is valid.  I know that the mfg doesnt supply drivers for linux in many instances.  However it was my understanding that the linux community was at the point where they have worked their way around these issues in almost all instances (hence all the talk that novices such as myself should give it a go).

"Almost all" is correct - most wireless cards do work out-of-the-box on a distribution like Ubuntu. In order to hit 100% compatibility, we need the hardware manufacturers to get together and create a specification for communicating with wireless cards. All flash drives and hard disks work out-of-the-box on all operating systems because they use the USB Mass Storage driver - there should be something similar for wireless networking devices.  

> My complaint is mainly that the learning curve is so steep.  There isnt much effort put into usability, because it is assumed you are a linux guru right off the bat.

It's sorta more assumed that if you're compiling drivers, that you know what you're doing. ATI and Nvidia make their own Linux drivers and they really do assume that you know what you're doing.

---

### Post by rft-hillview on 2009-07-06
Sadly "most" still means that 100% of my coms cards dont work (3Com 3CCFEM556 B 10/100 + 56K modem card and my D-link DWL-G650+ wifi card) which do as I said earlier "work out of the box" in some Linux offerings and if my research is up to the mark in some earlier releases of Ubuntu.

Being a newbie to Linux I am forced to ask the question as to why it is that something that works gets broken and why it is that something that works in one variety of Linux does not in another when it is all open source code so virtually no secrets.

Well having worked in the software industry for 40 years (but sadly not on Linux and or unix based systems and not having a C++ background) I actually do know why. Firstly there is the big resource and motivational problem in testing that all the historical code still works when giving birth to the latest and greatest and secondly there is a tendency to suffer from NIH when it comes to code - nicking abit from an open source system does not seem like a crime to me.

In case someone reads this and thinks I am bashing all those guy and dolls who spend their well earned leisure time grafting away - quite the contrary - I admire them and am deeply grateful that they are so successful in producing great systems - Ubuntu being one of them. Because of the coms problems on my particular hardware I choose to run on Puppy Linux because it handles both my coms cards - is it ideal - no but it is adequate. Will I keep testing Ubuntu as toime goes by - you bet I will.

many thanks to the people who keep open source alive

---

### Post by chriskin on 2009-07-06
> **a$$core said:**
> Hello. 

I decided to finally try out ubuntu, after hearing so many good things about it.

The desktop and everything relating to the OS seems great.  

However my wireless card isnt working (dwl-g650).

I have been reading forum posts and other info on the web for 3 hours now, and am totally baffled.

Apparently I need madwifi,  ndiswrapper, all this other crap.  Even then it wont work with WPA?  Millions of commands entered into the prompt.    I CANT FIGURE THIS CRAP OUT!

If people are going to get on the linux bandwagon it is going to have to get ALOT simpler than this.  Like no command line simple.  

I've burnt out my memory on reefer a long time ago, there is no remembering hundreds of text commands, their order, etc.  It just needs to work.  

Even if I were to learn all of this crap, it would take several years of constant use, which I cant do IF I DONT HAVE INTERNET.  It's a catch 22.  I cant have internet because I cant install the shite to make it work.  I cant learn how to make the shite work because I cant use the laptop constantly, because I dont have internet!

Can anyone point me to a super simple method to install whatever I need to make this wireless card work?  If the directions include command line I need every single command in order to do it.  

Also, if this problem is so common, why the hell isnt the stuff to make it work included in the ubunto OS?


man i LOVE those people who just scream about nothing working, yet they never ask the question to solve it on the forums :P

i can't say that my pc works perfectly, same way it doesn't work perfectly on windows, but i will not scream like a 5-year-old till someone notices :P

---

### Post by cariboo on 2009-07-06
The op hasn't been back to the forums since he created his username and this thread. Is there any need to keep the thread going?

---

### Post by chriskin on 2009-07-06
other than just having fun? no not really

but you can't say that making fun of a troll isn't fun right?

---

### Post by cariboo on 2009-07-07
You can't make fun of a troll that isn't here. This thread is closed.

---

