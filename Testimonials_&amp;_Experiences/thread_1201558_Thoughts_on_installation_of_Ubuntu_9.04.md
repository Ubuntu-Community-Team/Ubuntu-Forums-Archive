---
title: "Thoughts on installation of Ubuntu 9.04"
date: 2009-07-01
forum: Testimonials &amp; Experiences
---

### Post by emp on 2009-07-01
OK.. here goes.

**Installation background**
I want to set up Ubuntu 9.04 on my home machine to use as a desktop OS. Vista was the straw that broke the camel's back, so to speak.

However, dual boot is in order, as I need some programs only available in Windows for work. 
[B]
The machine[/B]
Intel Dual core, no problem here. 2 internal HDs, 1 external.

**My IT background**
I have some experience with Linux, but a complete install / configuration is nothing I have done before. (use Linux on web servers, so Apache, vi, as well as basic commands are OK)

I am a programmer though, so I am not computer - illiterate.

**The installation**
The graphical installation works fine, up to the point where partitions have to be edited / chosen.

All I see is

a) Install Dual Boot automatically
b) Choose a HD and kill it completely
c) manual partitioning


After poking around in the manual partitioner, I decide it is not for me. Swap? Etx3? What the ....?

So, back to the automatic options.

I want dual boot, so go!

**The surprise:**
After installation, GRUB dies with error 21.

From all I can gather, Ubuntu has decided to install itself on the external USB harddisk. In the bootup, this causes GRUB to die.

I seriously expected Ubuntu to install itself on /hda1 

[B]
What could be done better:[/B]
OK, I am not here to bash Linux (far from it), but I think a middle ground in the installation would be nice.

Why can I not choose the harddisk I want the dual boot Ubuntu on?
The dialog does recognize all harddisks and even displays them in human-readable format (Samsung SCSI  instead of /hda1)

So this (to me) seems like a viable suggestion.

**My solution?**
Well fdisk -l from the live distro did not work (it literally did nothing).

So I am going to unplug my USB drive and reinstall Ubuntu, which will probably land on my 2nd hard disk. hoping it will write a viable GRUB.

::emp::

---

### Post by caravel on 2009-07-01
You should have used _manual partitioning_.  The other options are for a PC with no OS installed or for a PC that already has an OS and some free space.

Why was the external USB HDD even connected up while you were installing?  I assume you use that for storage and it has your important data on it?  There is no way I would leave that connected while installing any OS.

The most important thing is to read up before attempting the install.

The manual partitioning is not difficult.  All you need for a basic installation is one ext3 (ext3 is the file system) partition with a mount point of "/" and one swap partition of about 1GB and you're all set (The swap doesn't require a mount point).

fdisk -l just lists partition information.  It probably did what it was supposed to do.  If you want to get rid of the newly added ext3 and swap partitions from your USB HDD just use gparted to delete them and then resize the primary partition to fill the free space again.

```
sudo gparted
```

---

### Post by emp on 2009-07-01
Jesus H!

Sorry, but that is exactly the response I anticipated and actually hoped I wouldn't get.

Yes, what you said is correct, but please... think of normal user Joe Average.

I think the changes I propose are doable (the installer is almost there) and feasable.

As for "why was your USB connected": 

Of course the reason was
 
a) lazyness (as if I was the only one)
and 
b) I never had any problems leaving the device connected, not even when installing (urghs) Vista.

As for the partition, 

a) I had free space on the first HDD, just like in your post "... for a PC that already has an OS and some free space...."
b) Ubuntu was fine with repartitioning the external drive automagically, so why not the first HDD? (if there would not have been unpartitioned space)

I was actually very, very happy with the rest of the installation, this post was supposed to point in a direction to make Ubuntu more "user friendly" or "desktop ready" whatever you like to call it.

best,
::emp::

PS: fdisk -l literally did ntohing. No output, nothing. I know what it is supposed to do. Well, it did nothing.

---

### Post by caravel on 2009-07-01
> **emp said:**
> b) Ubuntu was fine with repartitioning the external drive automagically, so why not the first HDD? (if there would not have been unpartitioned space)

You opted for the automated option.  The installer probably went for the largest available contiguous space.  As I said use manual partitioning - it's not that hard and in all honesty "Joe Average" almost never installs his own OS anyway so they should definitely not be attemtpting to install Linux.

Do:

```
sudo fdisk -l
```

and post output.

---

### Post by emp on 2009-07-01
I think you are wrong here.

But honestly, I still

a) find this behaviour disturbing
b) think it can be improved (what is wrong with that, I fail to grasp)

and

c)Hope my plan will work and I get my dual boot.

The output of fdisk -l (as you fail to grasp it)

> fdisk -l
>

Read as: nothing! (as I said 3 times in my last post)

So far,

::emp::

---

### Post by caravel on 2009-07-01
Ah so now you're being rude?  Perhaps you think I'm paid to sit here and read/reply to your posts?  If I was I'd be transferring you to my hypothetical call center in New Delhi right now...

Newsflash for you:  You posted in a thread in the testimonials forum.  Threads get replied to.  You may not like/agree with every reply you get - strangely no one else has replied - and I think that's what frustrates you.

The facts are that you registed here in 2005, you've now posted 8 times - three of which in this thread - and you've never asked for help or advice here on this current issue.  Instead you came straight in here posting the usual *"I can't get it to work so it must be no good"* type thread - *without* first seeking advice/assistance.

I gave you the solution at the beginning: Manually partition (it's not ******* rocket science!) and unplug the USB HDD while you're installing Ubuntu.  But you've made it clear that you've no intention of trying to get Ubuntu up and running - you're simply nothing more than a *troll* and your last post proves it.

---

### Post by Tamlynmac on 2009-07-01
> caravel
Ah so now you're being rude? Perhaps you think I'm paid to sit here and read/reply to your posts? If I was I'd be transferring you to my hypothetical call center in New Delhi right now...

Newsflash for you: You posted in a thread in the testimonials forum. Threads get replied to. You may not like/agree with every reply you get - strangely no one else has replied - and I think that's what frustrates you.

The facts are that you registed here in 2005, you've now posted 8 times - three of which in this thread - and you've never asked for help or advice here on this current issue. Instead you came straight in here posting the usual *"I can't get it to work so it must be no good"* type thread - *without* first seeking advice/assistance.

I gave you the solution at the beginning: Manually partition (it's not ******* rocket science!) and unplug the USB HDD while you're installing Ubuntu. But you've made it clear that you've no intention of trying to get Ubuntu up and running - you're simply nothing more than a *troll* and your last post proves it. 	

+1
Couldn't have said it better. Thank You caravel

---

### Post by emp on 2009-07-01
Actually..

I did not want to be rude.

If my post was, I apologize.

I am still wondering about the attitude I got for my initial post.

I gave my testimonial of a (failed) installation and calmly described what could be improved.

All I got was a "you should have" and a thinly disguised RTFM.

I did in no way blame anyone, nor did I bash Ubuntu, nor did I say it was crap. I simply stated what could be improved.

You and me also differ in the opinion about "Joe Average".

You seem to think that he never installs his own OS, and probably that he should not.

I think that he does, and that everything that can be done to ENABLE poor Joe to seize control of his own system is good.

But anyhow, I guess we should agree to disagree.
Your ad hominem attacks ("you think I am being paid") are not only rude, they also aim into the wrong direction. I am fully aware what open source is, and I am actively pushing it in the workplace and elsewhere. 

I have the feeling I am being dealt the generic "stupid windows user" card here.

BTW, my rescue plan worked and I am now running Ubuntu on the machine.

::emp::

---

### Post by OscarFoxtrot on 2009-07-01
[quote=caravel;7545579... in all honesty "Joe Average" almost never installs his own OS anyway so they should definitely not be attemtpting to install Linux. [/quote]

Very  few computers come with Linux on, almost all PCs "Joe Average" is going to buy or already have will have some version of Windows, so lots of people are going to have to try to install Linux when their only previous experience, if they have it, is using a manufacturer's restore disk.

---

### Post by caravel on 2009-07-01
> **emp said:**
> I am still wondering about the attitude I got for my initial post.
You didn't get any "attitude"... perhaps, just perhaps you were expecting "attitude" and thus "found" it?

> **emp said:**
> I gave my testimonial of a (failed) installation and calmly described what could be improved.
You see, the thing is, the installation probably didn't "fail".  Perhaps it was user error?  Had you thought of that?  Probably not and that is solely down to the fact that you had never asked for help nor were you willing to learn.  You simply turned up here playing the role of "Joe Average" and posted this before even trying to seek help to solve the problem.

> **emp said:**
> All I got was a "you should have" and a thinly disguised RTFM.
A RTFM would have involved a link and a dismissal - in truth you've probably never seen an RTFM response to a post or you wouldn't have assumed that mine was one.  Get yourself over to some other notable Linux forums and try posting this and prepare for an RTFM.  If you went out and bought Windows Vista - would you plunge into the install without knowing the basics of partitions or, disc drives etc?  Would Joe Average be ok installing it as a second OS?

> **emp said:**
> I did in no way blame anyone, nor did I bash Ubuntu, nor did I say it was crap. I simply stated what could be improved.
No, in fact you posted how it didn't work for you.  I then responded in a fitting fashion (assuming you to be a coder) I responded with simple advice as to how to remedy the problem.  Your response was "Jesus H!" etc, followed by sarcastic comments as to how this was the third time you said something, how I was "faling to grasp" it and how my behaviour was disturbing".

I feel that your response was due to the fact that you *didn't want a solution* - you wanted to come here in the role of Mr "Joe Average" telling us all that the installer somehow isn't user friendly.  In a word: Bollox.

> **emp said:**
> You and me also differ in the opinion about "Joe Average".

You seem to think that he never installs his own OS, and probably that he should not.
Another newsflash for you: He doesn't.  Most people have not heard of the terms "Linux", "OS", "bootloader", "partition" and the like.  It may come as another big surprise to you, but the average person doesn't use Linux and if they do it's because someone installed it and set it up for them.  The average person does not install Windows either, they buy a preloaded machine or take it down to their local PC shop to get the restore disc image restored or Windows reloaded.  A *lot* of people throw the restore discs away with the box the PC came in - because they don't know what they are.  *I have lost count of the number of times I've come across this.*  Those installing Linux are generally people with some PC knowledge, not "Average Joe" as you like to call him.

> **emp said:**
> Your ad hominem attacks ("you think I am being paid") are not only rude, they also aim into the wrong direction. I am fully aware what open source is, and I am actively pushing it in the workplace and elsewhere. 
So first you aplogise for being rude and now I'm rude... That was not an ad hominem attack.  Re read and re-analyze your own comments first to find ad hominem attacks galore.  Your whole argument and the entire reasoning behind this thread is inconsistent.  My only ad hominem attack on yourself was in my labelling you as a *troll*.  I don't take that back.

> **emp said:**
> I have the feeling I am being dealt the generic "stupid windows user" card here.
Well no - you had stated that you were a programmer?  This is why I did not mince words in advising you of the most expedient and common sense solution.  I tried to address *your immediate issue first* - before moving on to bitching about what's wrong with the installer.  This moved away from your main agenda - clearly.

> **emp said:**
> BTW, my rescue plan worked and I am now running Ubuntu on the machine.

::emp::
So thread over - have a great time.

---

### Post by Tamlynmac on 2009-07-01
> emp
You and me also differ in the opinion about "Joe Average".

You seem to think that he never installs his own OS, and probably that he should not.

I think that he does, and that everything that can be done to ENABLE poor Joe to seize control of his own system is good.
Not investigating, learning and/or asking questions - usually dooms a project to failure. Prior to committing resources to any project (including installation of an OS) one should always define and endeavor to understand said project. Preparations for any project should include a comprehensive review of the requirements of said project and the necessary resources to complete the project successfully.

By simply downloading a file and copying it to a disk one can install Ubuntu/Linux. However, without investigating and spending time learning about the OS prior to installation - the risk of failure is high - as with any project, if one fails to plan then one plans to fail.

Failure can be defined in many ways. Obviously, your definition of "Joe Average" assumes Joe average is shall we less than competent and would waste no time learning about the OS prior to attempting the installation. I would disagree with that assessment. I believe many could successfully make the transition to Ubuntu/Linux and would comprehend that the transition requires an investment in time and learning. It's my opinion that no OS installation should be attempted without some basic fundamental knowledge of the OS and the system it's to be installed on (not even Windows). Should someone decide to install an OS without any experience and they waste no time on learning, I suspect the odds are not in their favor. IMHO, logic suggests those individuals would benefit from requesting assistance or having it done for them.

Your correct in assuming our opinions regarding "Joe Average" differ. I personally don't see the (so-called) average person as you do. But rather believe that they are smart enough to know that such a commitment requires an investment in time (based in learning). Every individual I've assisted in installing Ubuntu on their systems, understood that completely.

Please, try and consider that other people may not make the same assumptions you did. They may actually invest time and energy in assuring that their efforts are not in vein. Targeting those efforts towards a successful Ubuntu/Linux installation by performing the necessary steps prior to starting the project. Obviously, this substantially increases the likelihood of a positive outcome.

Unfortunately, you don't seem to believe that Joe Average is capable of that. I find that - SAD. I suspect if you took the time to read the posting of many on this forum who have made the transition, you might find that these individuals are wiser than you believe.

One point of contention: I don't know "Joe Average" and find it impossible to profile anyone or assign them to a category. When using the term Joe Average in the above response, my intent is only to respond to your statements. Most everyone I know has a different level of computing capability, stigmatizing them by profiling them - is just wrong on so many levels.
 [http://en.wikipedia.org/wiki/Wikipedia:Categorization_of_people](http://en.wikipedia.org/wiki/Wikipedia:Categorization_of_people)

---

