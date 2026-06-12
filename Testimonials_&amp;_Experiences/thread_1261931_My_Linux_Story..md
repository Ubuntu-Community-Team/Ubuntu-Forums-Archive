---
title: "My Linux Story."
date: 2009-09-09
forum: Testimonials &amp; Experiences
---

### Post by chinoy on 2009-09-09
Im returning to Linux after over 15 years.
This is my story.
Back in the early 90s.
I was working for Tata Steel and was a one man team called Skunk Works.

We had the countries first VSAT based network which cost the company big $$$$
When installed it didnt work.
I was sent in to see what could be done to get it to work.
We had 80,000 Staff and sales offices in 32 cities.

The problem was the speeds where so slow no TCP/IP stack would work.
Microsoft didnt even know what TCP/IP was. YOu had to buy a stack from another company.

This is when I heard of a kid called Linus who had writen his own os and the source code was avalible for free. Too bad there where no terms such as internet in our country back then. So off I went to the nearest IIT who where on ernet.

And came back with 42 flopies.
The next 3 years where spent seting up a country wide network runing on Linux.
I quit my Job when one of the mangement said Linux had no future no vendor support and was a dead OS all this was in the 90s

They striped my network and switched the complete system to Lotus Notes. That didnt last very long.

Fast forward 15 years and here I am with a Dell XPS M1530. Trying to load Linux.
I tried Ubuntu because a friend had a copy. The last version I installed was Slackware. 

Sad to say things are a lot more messy these days.
Ive spent 5 days trying to get my Express Card to work and cant even find one post of any help.

Linux with slackware was simple even a moron could install it.
This new version is just too complex.
First I installed the default desktop everything worked except my Express card so I was told to try a seprate Kernel. I downloaded that and everything crashed its taken me 10 hours just to get my Wifi up and runing.

Till you can get it to a point where it just works. Only then it can go main stream.
In a way Im sad to see the Linux comunity split up in so many directions.
If it had stayed with just one vendor say Slackware or something else we would have been rocking by now.

I will give it a few more days and if I cant get it to work will just go back to Windoze. And I hate windoze.

---

### Post by scouser73 on 2009-09-09
This post should be moved to Testimonials & Experiences.

---

### Post by shae on 2009-09-09
What type of express card are you trying to use?  Odds are that it is the express card that lacks drivers rather than the express card slot.

---

### Post by chinoy on 2009-09-10
Its the Lifeview DVB Fly-TV Express M5 MST-T2-A2
Its not a drivers issue.
The best answer I got was this card is designed to work with Windows XP MCE
I noticed across the net that as soon as MS came out with SP3 for XP a lot of hardware stoped working in particular TV Cards.
I have the driver CD that came with the card too bad they dont load.
THe vendor GDB in Auz even has updated Vista Compatible Drivers but when I try to install it says no hardware found.

The problem is to do with Dell Bios & Microsoft not being on the same page.
For Example under Win7 I see a whole lot of IRQ and Memory Conflicts.

---

### Post by Wim Sturkenboom on 2009-09-10
I don't get it. Are you using Windows drivers in Linux? Wine maybe?

And complain to GDB that there are no native Linux drivers.

---

### Post by Mighty_Joe on 2009-09-10
> **chinoy said:**
> 
Till you can get it to a point where it just works. Only then it can go main stream.
In a way Im sad to see the Linux comunity split up in so many directions.
If it had stayed with just one vendor say Slackware or something else we would have been rocking by now.

I will give it a few more days and if I cant get it to work will just go back to Windoze. And I hate windoze.

[Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by prem1er on 2009-09-10
Please tell us more.

---

### Post by chinoy on 2009-09-11
More about what the Setup I did back then or my existing problem. ?

About the last Linux install.
We had a Data/Voice/Fax/ Network.
When the system was sold to us we where told we would get  64Kbps thruput. They didnt tell us that this bandwidth was to be shared with all 32 sales offices.
So the On Net TCP/IP stack the only stack for windoz back then would time out. We tried every stack we could. OS2 / AS400 / IBM ES900 nothing worked.
Got the Linux code. Recompiled it with some absurd time  out values for the stack and it worked.
Each sales office got one Linux Box. The clients in each office interacted with this box so their work looked fast. The Linux server would then shug along transfering data to and from the main plant. 
What was amazing is that some of these servers where found runing 2-3 years non stop.
Who remebers Novell Netware another OS that ran for years without so much as a reboot.

I remember when I finished the project Slackware had just come out with their first version.
Quit my job when questions where raised about using Linux in a Corporate environment.
Points raised at the time where
a. No vendor support
b. If I quit nobody knew aything about the OS or how to support it.
c. That it was a free OS with no future.
At the time I was a big Linux Fan this was too much for me so I quit.

They then implemented Lotus Notes based system after I left. By the time they had improved the bandwidth. 

On my Existing problem.
I have a Dell XPS M1530 with an express card.
Dell Support forum shows over 500 people with Express Slot issues and nobody from Dell ever responds.

I suspect I have to enable raid in the Bios. For my express card to work.
No Im not stupid that I expect wine or Windows drivers to work.
Im expecting Linux s/w like Myth TV and Linux drivers to work with my card.

What I find frustrating is the lack of Info on Express cards.
The fact that drivers which worked on XP MCE wont work on XP or Vista.
The fact that Intell + Dell + the Bios guys didnt write a proper Bios. Or drivers for their chipsets.

In 15 years other than Linux being broken into so many distributions not much has changed.
We used X windows and KDE back then too.
I think Intell has kept everybody on their toes with new chipsets and CPUs.
Microsoft Driver Certification sucks.

---

### Post by Mighty_Joe on 2009-09-12
> **chinoy said:**
> What I find frustrating is the lack of Info on Express cards.


Don't blame the Linux community, take it up with the hardware vendors.  If they don't support Linux themselves or make their specifications open, someone has to reverse engineer the drivers in the dark. 
Also, you may notice that your wandering posts have gotten your post moved to the "testimonial and experiences" forum.  If you want help with your technical problem, I'd suggest posting again in one of the help forums and sticking to the relevant facts.

---

### Post by Tamlynmac on 2009-09-12
> Mighty_Joe
I'd suggest posting again in one of the help forums and sticking to the relevant facts. 	

I couldn't agree more. Just the facts, PLEASE.

While trying to assist in the "Help Sections" I'll often skip over assistance questions when they start off with statements similar to "It worked in Windows" or "I never had this problem in Windows". The motive for skipping is I really don't wish to waste time explaining or arguing over what Windows can or can not do or support.

It's been my experience, if one simply addresses the problem and forgoes the incessant Windows comparisons, assisting becomes only a question of solutions. Instead of wasting time dissecting a request for the actual problem.

KISS works and when asking for help - keep it simple and be specific. Drop the Windows comparisons and focus on the problem as it relates to Ubuntu/Linux. This will provider the assister with the required  information, instead of dealing with opinion or comparison.

I believe the forum would benefit from a fill in the blank / brief explanation form that would help requesters to identify their problems and all associated user information - without trying to completely explain it in their own words ( some issues may require more detail). This would eliminate the need for multiple posts requesting additional information from the requester (system specs, ect.). The results could be stored in a database and used to establish a listing of issues and potential solutions. Don't think it would take much space and eventually it might have a significantly reduction in the volume of help questions. Not to mention the frustrations of a new user trying to acquire support, while not being familiar enough with Ubuntu to use the appropriate terminology or understand the response.

Having done quite a bit of spreadsheet and some DB work, I believe this would truly be beneficial to new users. One section of the forum completely dedicated to a database of solutions, based entirely on information collected from the "Help Sections".  :-k

Just my $0.02

---

### Post by GodLikeCreature on 2009-09-14
> **chinoy said:**
> Till you can get it to a point where it just works. Only then it can go main stream.

Kinda surprising that someone could install Slackware in the early years (when something even as simple as mounting a drive was manual) has issues now with Ubuntu...

In my opinion, it is not realistic to expect the Linux community to close the whole gap.  Many manufacturers won´t collaborate, so it is a bit of a hit and miss.  In addition, the amount of devices nowadays has grown exponentially since 15 years ago.  When back in 94 it could be about mounting a CDROM drive (if at all), nowadays it is about the 3G modem, the wireless card, the photo camera, iPOD, video camera, memory cards, and a host of other USB devices...

It really makes no sense to compare how it was back then and how it is now...  

In addition, I am curious to know how you think Linux would have overcome the lack of manufacturing support if it remained a single distro community.  Although I see where you are coming from (a much stronger community support and experience), I very much think that problem would remain.

---

### Post by chinoy on 2009-09-14
well I got in touch with some of the kids who are into linux at the work place.
Nice to know that even top corporates and network service providers like Akamai have linux boxes in the office.
They all had only one thing to say. Ubuntu is the crappiest distro to go with.
They where talking about some other distor where the kernel is compiled for your specific machine and is downloaded dynamically.

Ive spent 10 days with Ubuntu and am washing my hands off it.
I cant load the modules I need. I cant re-compile my kernel. Without a bunch of error messages. And I dont even seem to have lilo installed.
All this worked without a flaw even in the first version of slackware.
Even pre slackware it worked.
This is just too much to expect 
Im now going to go with Fedora the kids say its much better and works.
Sorry Im just a grump old man. Ignore my views if you dont agree.
You have a valid point about the new hardware. I still say it would have been way better for the community if we had fewerr distro's Like Ive wasted close to a month playing with Ubuntu
I may not return here as Ive found little or no help to any of my issues.
But I will return to post feedback on my exp. with Fedora and how it differs from Ubuntu lets see if its half as frustrating.
Do a search for posts made by me on this forum you will find most of the stupid things I ran into which nobody has been able to respond to.

---

### Post by Gen2ly on 2009-09-14
Is this for real?  You may have read some good stories on Linux but this doesn't fly with me.  Building tun stacks on old ibm hardware... some points are very vague while others are very specific (seperate kernal ???).  If this story is real, I'd very much like to hear it.  I'd be absolutely fascinated, if you're gripe is with Ubuntu, just let it out.  But this mish-mash has got me a bit confused.

---

### Post by ukripper on 2009-09-14
> **chinoy said:**
> 

If it had stayed with just one vendor say Slackware or something else we would have been rocking by now.

I will give it a few more days and if I cant get it to work will just go back to Windoze. And I hate windoze.

I thought you quit your job because your ex-management didn't want Linux installed and now you are using windows yourself. Huh, bit confused about your story mate..sounds ambiguous to me...

---

### Post by GodLikeCreature on 2009-09-14
> **chinoy said:**
> well I got in touch with some of the kids who are into linux at the work place.
Nice to know that even top corporates and network service providers like Akamai have linux boxes in the office.
They all had only one thing to say. Ubuntu is the crappiest distro to go with.
They where talking about some other distor where the kernel is compiled for your specific machine and is downloaded dynamically.

Ive spent 10 days with Ubuntu and am washing my hands off it.
I cant load the modules I need. I cant re-compile my kernel. Without a bunch of error messages. And I dont even seem to have lilo installed.
All this worked without a flaw even in the first version of slackware.
Even pre slackware it worked.
This is just too much to expect 
Im now going to go with Fedora the kids say its much better and works.
Sorry Im just a grump old man. Ignore my views if you dont agree.
You have a valid point about the new hardware. I still say it would have been way better for the community if we had fewerr distro's Like Ive wasted close to a month playing with Ubuntu
I may not return here as Ive found little or no help to any of my issues.
But I will return to post feedback on my exp. with Fedora and how it differs from Ubuntu lets see if its half as frustrating.
Do a search for posts made by me on this forum you will find most of the stupid things I ran into which nobody has been able to respond to.

Hmmm...  I don't know, man, sounds to me a bit like you are trying to get things back to how they were years ago.  

I have tried a bunch of distros lately and none carry lilo anymore.  In fact many users are excited now that GRUB2 and Plymouth will take part of the start sections of our OS...  And you are concerned about lilo  missing?...

...And about Fedora...  Better than Ubuntu?  Well, not sure how, but when I tried it, I found it worse.  It usually incorporates the latest software apps, even if that means releases with beta versions.  As a result, it is kind of implied that consistency is not the ultimate goal, but being on the edge.  Plymouth and GRUB2 will also be part of Fedora if they are not already...

Anyways, I won't go on about it, but I found Fedora less mature than Ubuntu in many ways.  It seems to me like you are more interested in customising everything to the last detail, even if that takes a lot of manual tweaking...  

If that's the case, then Ubuntu is definitely not for you, and you would probably enjoy something like CentOS better...  Or even the current versions of Slackware!

Good luck

---

### Post by Maheriano on 2009-09-14
You installed a custom operating system from 3.5 inch floppy diskettes 15 years ago yet you don't know the difference between Linux and Ubuntu? They're 2 different things.

---

### Post by Invincible23 on 2009-09-15
> **chinoy said:**
> well I got in touch with some of the kids who are into linux at the work place.
Nice to know that even top corporates and network service providers like Akamai have linux boxes in the office.
Im now going to go with Fedora the kids say its much better and works.

chinoy sorry to hear Ubuntu didnt work for you.
As you have mentioned your friends can help you sort out some of your problems using some other Linux distro.
Good luck with that and enjoy your experience with Linux.

---

