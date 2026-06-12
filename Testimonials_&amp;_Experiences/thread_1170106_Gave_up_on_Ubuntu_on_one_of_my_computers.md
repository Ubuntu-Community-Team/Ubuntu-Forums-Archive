---
title: "Gave up on Ubuntu on one of my computers"
date: 2009-05-25
forum: Testimonials &amp; Experiences
---

### Post by Raygreen on 2009-05-25
After playing around for over 2 weeks trying to get Ubuntu to load onto the hard drive of a computer that I wiped Windows XP off of, I gave up. No one here had any responses to my inquires. I tried many of the ideas that I saw on this forum from other postings having similar problems. I tried alternate disk, I tried prepping the hard drive with terminal commands that were suggested. All to no avail. I tried other distros, like Fedora, Mandriva, Linux Mint, PCLinuxOS, and they all had errors one way or another. I did have success with openSUSE and Freespire. I currently run Ubuntu 9.04 on my laptop and desktop through Wubi. 

I was able to get Ubuntu to work from the Live Disk and from within Windows XP on that other computer. Some how it just could not get it to load by itself on to the hard drive. Seems there is some kind of conflict with that particular hard drive and many of the Linux distributions I tried. I have been able to get Ubuntu to work solely on this laptop before. So I know it does work. To Ubuntu's credit, its the only distro that lets you run it through Windows without having to use the Live CD/DVD.

---

### Post by 73ckn797 on 2009-05-25
I believe that I saw this was a Dell computer? Junk it and build your own.

---

### Post by spcwingo on 2009-05-26
I had one system that Ubuntu refused to install from the live CD and the alternate.  What I did to get Ubuntu installed is:

Downloaded the mini ISO from here:

[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

Burn, boot from, and install from the CD.  When it's done installing reboot, log in, and run this one command:

```
sudo apt-get install ubuntu-desktop && sudo apt-get clean && sudo reboot
```

This will install the X server along with all the other apps on the live CD, clean the apt cache, and reboot into your new Ubuntu desktop (hopefully).

---

### Post by TransitMan on 2009-05-26
> **73ckn797 said:**
> I believe that I saw this was a Dell computer? Junk it and build your own.

I'm using a DELL computer and have no problems with Ubuntu.
I believe you need to rethink your answer a bit before telling someone to junk an otherwise perfectly good and working computer. 
Not everyone can afford to build their own right now.

---

### Post by Ethelbert2 on 2009-05-26
The "junk it" answer above is irresponsible and stupid. Actually many people like me turn to Linux in order to get an old computer going and hopefully extend its life. 

The idea that you have to have a special computer tailor built to make Linux work is one of the major reasons people go back to Windows.  

Outrageous fatuous nonsense like the junk it answer is arrogant and unhelpful.

---

### Post by presence1960 on 2009-05-26
if one is offended by a post the best thing to do is use the report post button located at the very bottom under posters info on left. It is next to the one that shows if you are currently on line or not.

I learned from experience not to get in a war of words as I got a PM from a moderator suggesting the above. I did feel justified because I was responding to the way a newbie was treated, but in retrospect the ensuing posts going back & forth did more harm than good.

---

### Post by 73ckn797 on 2009-05-26
So that no one will be offended, it is my personal opinion.

---

### Post by armandh on 2009-05-26
try a spare HDD 
I have a dell with xp that the file sys is so corrupted/fragmented that no repartitioning is possible
just error messages.

some day when xp fails I will wipe the HDD with a partition editor and be good to go

if Ubuntu runs live you probably have a HDD problem

I had a vista partition that could only be reduced by vista's own utility.

---

### Post by HappyFeet on 2009-05-26
> **73ckn797 said:**
> I believe that I saw this was a Dell computer? Junk it and build your own.

Agreed. I build my own and *never* have any problems. And if I didn't know how, or did not want to build my own, I would get a PC with Linux preinstalled. Problem solved.

---

### Post by Tamlynmac on 2009-05-26
> 73ckn797
So that no one will be offended, it is my personal opinion. 	

Unless substantiated by data everything in this section is opinion and I for one believe in your right to express it. When all we do is patronize each other, how can one expect to find the truth?

Chastising you for expressing your opinion, mandates chastising those for expressing a different opinion. Unless of course that opinion is shared by the majority, in which case they must always be right???? I think many unpleasant groups in the history of mankind believed they were right.

Lets keep in mind that this is the testimonial & experience section of the forum. Hopefully, the OP did not come to this section for assistance, but to define their experience and all members should have the right to express their opinion. Unless it deliberately hurts or infringes on others. I doubt your statement regarding disposal of the PC could be construed as offensive. For I read it as a suggestion not a mandate.

Prior to pushing the button, my opinion is that one should ask themselves if the statement was truly offensive (deliberately) or simply someone else's opinion that differs from your own. Open rebuttal and communications are healthy and beneficial, let us not become that which we (for the most part) despise - closed source. 

Just my $0.02

---

### Post by evermooingcow on 2009-05-26
> **Ethelbert2 said:**
> The "junk it" answer above is irresponsible and stupid. Actually many people like me turn to Linux in order to get an old computer going and hopefully extend its life. 

The idea that you have to have a special computer tailor built to make Linux work is one of the major reasons people go back to Windows.  

Outrageous fatuous nonsense like the junk it answer is arrogant and unhelpful.
Just as many people see no value in old hardware that can't run the latest MS OSes some people see no value in any hardware new or old that is incompatible with Linux.

Its just a matter of whether the person considers Linux their primary or alternate OS.

---

### Post by presence1960 on 2009-05-26
I was not offended by 73ckn797's remarks. I posted what I did because of Ethelbert's categorizing 73ckn797's remarks as stupid and irresponsible. At that point it took a turn toward being personal. I think we all need to be a little less sensitive (myself included at the top of the list) and just accept the fact that everyone won't agree with us just as we don't agree with everyone else. There is a whole different approach that could have been used to address the remarks not liked. We will certainly catch more flies with honey rather than with vinegar. There is more than enough room in here for each of us to have our own opinion provided we keep the other guys and gals in mind when we express it. Situations such as this have the potential to develop into a flame war.

On a personal note I will never buy a prebuilt PC, but to each his own. I don't think the remark is stupid because on closer examination it has merit. Irresponsible? no! maybe it could have been worded a little better- but nothing to get upset about.

If it bothered me I would have checked the forum COC and Do's & Don'ts. If it was something to gripe about I would have no problem using the report button.

---

### Post by Tamlynmac on 2009-05-27
> presence1960
Situations such as this have the potential to develop into a flame war.

+1

And to what purpose? I personally found nothing offensive in your original post regarding disposal of a PC. I suspected, that you had previously experienced issues with a prefab PC or Dell or both. ;)

Just hope all can realize the value of being able to express our opinions and not start a flame war or push a button. For I truly believe that by sharing opinions we can learn from each other. IMHO it doesn't have to be a competition or a war, just an exchange of ideas and different points of view.

We also have the option of sitting back and reminding ourselves that opinions are like belly buttons - almost everyone has one. Including me. :)

Enjoy

---

### Post by majamba on 2009-05-27
try 8.10 works really good
also maybe you can give us your specs to see why ubuntu is not running
or 
maybe the computer so old that no linux runs on it

---

### Post by Ethelbert2 on 2009-06-01
[COLOR="DarkGreen"]Points accepted (with humility) about the right to express opinions. I see that no-one is offended, and the discussion has value. 

But I will try to explain why I made the comment.  One of the major selling points inducing me to take up Linux is how often I am told that 

a) it is piece of cake to install compared to Windows becasue of its plethora of drivers.

b) It is suitable for older computers because it hogs less resources, handles old hardware etc.

Having been convinced enough to try it and spend a lot of time on it, it is slightly contradictory to be told I should junk things (since the same advice would apply to the old P3 with a Radeon 7000 card I am trying to use).

In my case the solution appears to be to stick with an 8.10 version which is a bit disappointing (since I can't take advantage of other update things). There is enough frustrating satisfaction to persist for a while now and then, however. 

Junking the machine would defeat the object of the exercise in the first place, which is for practice and experiment and to not waste old resources. 

Another contradiction is the constant effort of Linux users to draw in the unconvinced and then, as soon as they hit problems, to blame them for **not** being convinced users or "willing to put in the time and learn the skills" etc. 

I am not a convinced Linux user (most of us are not) and although I am trying 32 and 64 versions on my main machine am unlikely to become so yet. Despite the promises there are just too many hassles finding drivers and getting everything to work. (Video issues, scanner has not driver, printer only works partially). Not the fault of many excellent volunteer contributors, I have slowly discovered, but the manufacturers - but it still is major obstacle if your main purpose is to use the tools on a machine (I have to earn a living and use the machine) rather than spend most of your time battling just to set it up.


Cheers[/COLOR]

---

### Post by lancest on 2009-06-01
You and only you, are responsible for buying Linux compatible hardware. Myself and many thousands of other desktop users around the world are completely sold out to desktop Linux. Many of us including myself  use Linux daily (on 5 machines no less) to earn a living and enjoy computing the way it should be. Yes Ubuntu is real and yes it does the job for business and pleasure on more hardware than any other OS. Good luck in the future, hope you aren't stuck with the virus magnet.

---

### Post by Jestersage on 2009-06-01
Wow. The community is still childish as ever. If it doesn't work, junk it? I thought we are suppose to be inclusive not excludign others?

OP, if your greatest issue is hardware, try openSuSE. It have better hardware compatibility.EDIT: And I look at his post again. Apparently he find it work better wth openSuSE and Freespire.

---

