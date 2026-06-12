---
title: "How ubuntu is very good at messing up your HD and files"
date: 2014-03-12
forum: Ubuntu, Linux and OS Chat
---

### Post by arthur4 on 2014-03-12
I wanted to do a dual boot with my windows, had 2 partitions, one with windows 8.1(which had all my files from my work, unviersity,etc). I, stupidly, tried installing ubuntu from a live cd, well, what hapenned was, it asked if I want to install it on my disk, but did NOT ask me which partition It would install into, neither it warned me it would format the ENTIRE disk.
I just want to thank ubuntu for failing at something so simple. Now I`m in a quest to recover my partition and files.

---

### Post by Iowan on 2014-03-12
No, I won't say it... :-#

---

### Post by monkeybrain20122 on 2014-03-12
> **arthur4 said:**
> I wanted to do a dual boot with my windows, had 2 partitions, one with windows 8.1(which had all my files from my work, unviersity,etc). I, stupidly, tried installing ubuntu from a live cd, well, what hapenned was, it asked if I want to install it on my disk, but did NOT ask me which partition It would install into, neither it warned me it would format the ENTIRE disk.
I just want to thank ubuntu for failing at something so simple. Now I`m in a quest to recover my partition and files.

Well it says it will erase everything. You didn't pay attention so how is that Ubuntu's fault? You should have chosen "install alongside" or "something else" and do it manually. Anyway dualbooting with Win8 is problematic because of MicroSoft's attempt to lock down the hardware, again it is not Linux's fault.

---

### Post by xicarusx on 2014-03-12
Not reading prompts is a good way to mess up your HDD and lose your files. 

There are multiple install options and it says in all caps THIS WILL ERASE YOUR FILES.

---

### Post by 23dornot23d on 2014-03-12
[IMG]http://toddhalfpenny.com/wp-content/uploads/2012/11/Install.png[/IMG]

---

### Post by QIII on 2014-03-12
Admitting one's own oversight in following obvious instructions is a more civil way of asking for help and having any chance of such being returned.

We have all done it ourselves.

---

### Post by sammiev on 2014-03-12
> **QIII said:**
> We have all done it ourselves.

Guilty as charged. :(

Thanks to having backups. :)

---

### Post by monkeybrain20122 on 2014-03-12
> **sammiev said:**
> Guilty as charged. :(

Thanks to having backups. :)

Nah, not me. :)

---

### Post by 23dornot23d on 2014-03-12
The question is - has the user actually overwritten anything ......... or is it that the computer will not boot up.

Often the initial reaction to something going wrong and a machine not booting or going to a black screen is 

Oh no ......... its screwed everything up ........ when that is rarely the case.

People do follow instructions - and when they see a Warning saying this will write over all of your data
they do not choose it - and especially with important information on a disk - they keep a backup before
risking anything - just common sense.

Booting from a live CD and running something like bootinfoscript 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Would probably be the first thing to do then (if confirmed that the drive has been overwritten) - take a image of it with clonezilla or take the hard drive out and give it to a specialist company to see if anything can be retrieved.

There are options ......... but how successful they are depend on the steps taken after realizing something
has gone wrong.

First reaction is usually oh no what have I done - the next reaction is what steps can be taken to recover the
situation. ( who knows - over the years of using both windows and linux - things happen - I once decided to
install win 95 just for a laugh ...... about a year ago now ........ it changed everything on one drive to 16 bit
with no prior warning - but I still managed to recover it with testdisk )

---

### Post by arthur4 on 2014-03-12
I just don't understand who would want to wipe all of it partitions inside one disk  just to install ubuntu?

Second thing, it says it'll wipe the disk, it just wipes the main partition, which just make it more confusing, why just not let we choose which partition it's going to be wiped, or warn the user about the partition that will be wiped instead? Ubuntu should be more user(noob)-friendly. Also, imagine how confusing it could be for people which first lenguage isn't english to see any difference between Disk and Partition.. Just saying, be more humble, it could be you that will need to be understood one day.

Anyway, fortunately I just remembered that I did a wide backup 3 weeks ago

---

### Post by varunendra on 2014-03-13
> **arthur4 said:**
> I just don't understand who would want to wipe all of it partitions inside one disk  just to install ubuntu?
I would.

Disk = Disk
Partition = Partition on a Disk
Partition != Disk (not equal to 'Disk')

Calling a partition "drive" is confusing, and not in accordance with any other terminology or dictionary other than microsoft's.

---

### Post by monkeybrain20122 on 2014-03-13
> **arthur4 said:**
> I just don't understand who would want to wipe all of it partitions inside one disk  just to install ubuntu?


Why not? When you install Windows doesn't it wipe the whole disk? It doesn't even have other options as far as I can remember. Most of us here don't dual boot with Windows.

---

### Post by su:bhatta on 2014-03-13
> **arthur4 said:**
> I just don't understand who would want to wipe all of it partitions inside one disk  just to install ubuntu?



A lot of people would. 

Refer to Post #5 image 
The Last option is 'Something Else- You can create or Resize partitions yourself...."

---

### Post by 23dornot23d on 2014-03-13
I just looked through the 8.1 installation instructions for a comparison ........... 

[http://windows.microsoft.com/en-us/windows-8/clean-install](http://windows.microsoft.com/en-us/windows-8/clean-install)

Very vague as to how it protects the users data .......... it just does the simple task of deleting everything on a partition
but does it give any indication as to what is on each partition ......

____________________________________________________________________

How many boot options would I have left at start up - say I was going to put that system (8.1) onto my drive.

Which of the operating systems would still work - Arch Linux - Mint Linux - Ubuntu Linux

or JUST 8.1

How would I get to my data on ext4 partitions ? ( what does Windows supply so that I can see and use all of my partitions ) ?
[IMG]http://i.minus.com/iJxuKQd5SvYew.png[/IMG]

I guess the real question is - if Linux can organize and layout many partitions and also keep track of everything it has on there as well as respecting
all other operating systems ........... it cannot be all that bad.

Try booting Arch linux or Mint linux or any other OS after installing WIndows just using Windows software to set up a boot loader ..........

I might be wrong here - because its not something I would risk - I have far more confidence in setting my partitions up with Linux than I ever would with
any other systems software ...... but that comes down to personal choice and having seen over the years how one company respects others or does not
as the case may be ..........

_________________________________________________________________________________________________

Glad you had a backup though ........ ( USB drives are cheap nowadays - its always good to have more than one copy of important things that you may need )

---

### Post by 3rdalbum on 2014-03-13
> **monkeybrain20122 said:**
> Why not? When you install Windows doesn't it wipe the whole disk?

Actually, no it doesn't. It has a manual partitioner. You can delete the existing partitions and create one partition, effectively wiping the whole disk.

> Also, imagine how confusing it could be for people which first language isn't English to see any difference between Disk and Partition

The first screen in the installer asks you to choose your language. If people purposely choose the language they are not best in... well, it's hardly Ubuntu's fault if they misunderstand is it?

---

### Post by stalkingwolf on 2014-03-13
pandora is a good windows based tool for drive recovery. there are also a few on the heirens disk.

"Linux expects you to know what you are doing."  not just click next.

---

### Post by JayKay3OOO on 2014-03-13
Re: How I am very good at messing up my HD and files.

P.S Re: How we were very good at messing up our HD and files using ubuntu.

---

### Post by arthur4 on 2014-03-13
Linux Ubuntu copied some GUI features from Mac OS X, by that I assume that they're trying to make the OS more user-friendly, so why not make things more clear? Like give a final warning, or on the following screen confirm if the user want to select a specific partition or just delete the whole disk. Wouldn't hurt, and yes there were many ways I could've avoided that, but I'm new to ubuntu, and I am human, I make mistakes, everyone does.. Just try to prevent the first experience of many adventurers to be as bad as mine.

---

### Post by SeijiSensei on 2014-03-13
One bad habit people coming from Windows have is the tendency to click "Next" during installations without actually reading the information on screen very carefully.  The options presented are pretty clear: replace Windows, install alongside Windows, and "something else" which lets you specify precisely what you want to happen.  I don't see how it could be made a whole lot clearer.

---

### Post by QIII on 2014-03-13
This sort of mistake happens.  I would *not* say it happens more often than not, but it does happen.  Those coming from Windows and for whom the notion of multi-booting is entirely new and foreign may step into pitfalls they have no idea to watch for.

Nobody who distributes Linux can protect against all types of failures -- and they wouldn't try. Part of the entire idea of Linux is that you should be able to do what you want.  That opens the door for mistakes among novices, but provides open opportunities for the experienced.  Nobody is born a Poet Laureate in the language spoken by their parents.  They have to learn.  Nobody in his very first class in a foreign language stands up in class to deliver a profound and moving extemporaneous speech in that language.  They have to learn.  Windows users have to learn Linux.

Take a look at some of the posts asking for help with the issue you have encountered.  You will find that the "Help!  I've managed to mess up my partitions trying to dual boot" threads generate dozens of helpful responses whereas the "Ubuntu is stupid and messed up my partitions" threads are not well received -- somewhat like this one.

To be brutally honest, the best way to improve your experience with Linux thus far would be for your attitude to become slightly less abrasive.  We're here to help.  But as volunteers we're not paid nor required to help.  We can walk away from those who demonstrate hostility.  We frequently do.

Addendum:

*If *you will moderate your attitude and *if *you will be willing to accept this community's tuition respectfully, then *you *will learn to *yourself* be one who helps another avoid what you have just encountered.  **That **is how the Linux community works and how the Linux community improves.

---

### Post by monkeybrain20122 on 2014-03-13
Maybe you should set up a dual boot between Windows8 and Windows7 and then tell us how much more novice friendly and idiot proof it is. I can't wait. :)

P.S. Dual booting is not an elementary operation for the absolute novice, I would think that anyone who attempts that would be a bit experienced, or at least willing to read the instructions and the prompts. Can't think of what more Ubuntu can do if you can't even read the prompts staring at your face.

---

### Post by QIII on 2014-03-13
OK.  I think the idea has been conveyed.  Let's not let this spiral into a cat fight.

arthur4, if you want some polite help sorting this out, I suggest starting a new thread with the details of what happened and asking politely for help.  There are plenty who would be happy to provide it.

---

### Post by cariboo on 2014-03-13
With QIII's post, I think this thread has run it's course. Thread Closed.

---

