---
title: "possible email virus in kubuntu 804"
date: 2008-07-01
forum: Security
---

### Post by athun on 2008-07-01
Not so very knowledgable so be kind.

Using Kubuntu 8.04,. firefox 2, and thunderbird 2.
Nutshell is that I appear to have been infected with a virus - probably through email.   My system worked fine before but now no longer recognizes USB devices,   Open Office Word will open but I can't get any documents.   If I try to open a flash drive I get the message, 'firefox doesn't know how to open this address because the system (media) isn't associated with any program'.   The OS does detect the USB flash drive but my media files do not show either on the desktop or on the console command line.   

Obviously now, I foolishly waited too long before installing clam av.   I can still install it but I am not sure if the presumed virus will insulate itself from an after-the-fact clam av install.   Checked syslog but frankly don't know what to look for.   On-line checking sites don't work for Kubuntu.

Appreciate any help.   How should I proceed?   Thanks

---

### Post by lukjad on 2008-07-01
> **athun said:**
> Not so very knowledgable so be kind.

Using Kubuntu 8.04,. firefox 2, and thunderbird 2.
Nutshell is that I appear to have been infected with a virus - probably through email.   My system worked fine before but now no longer recognizes USB devices,   Open Office Word will open but I can't get any documents.   If I try to open a flash drive I get the message, 'firefox doesn't know how to open this address because the system (media) isn't associated with any program'.   The OS does detect the USB flash drive but my media files do not show either on the desktop or on the console command line.   

Obviously now, I foolishly waited too long before installing clam av.   I can still install it but I am not sure if the presumed virus will insulate itself from an after-the-fact clam av install.   Checked syslog but frankly don't know what to look for.   On-line checking sites don't work for Kubuntu.

Appreciate any help.   How should I proceed?   Thanks

First off, relax. Sit back, take a deep breath. 
Point #1: 

> Original post:
[QUOTE]Linux does not get viruses.[/QUOTE]

> New and enlightened post after criticism and subsequent edit:
[QUOTE]It is ferociously unlikely that your particular Linux box will ever in its normal lifetime; if properly updated and not run as root for extended periods of time especially while surfing the Internet, installing dubious programs from shady third party repositories  based in The Republic of Elbonia, so long as you do not in any way shape or form insult anyone with more money, power, or tech savvy or works for the government, or is the government, or works for or is head of any organized crime right especially those that specialize in computer crime including my not limited to computer fraud, computer hacking, computer bashing, computer smashing, etc.; and normal being only a general time frame as defined by the tech community in general, get a virus, unless you do something really, really stupid. [/QUOTE]
______________________

Resuming original post
______________________

(Neither  I, nor anyone to whom I have spoken (with the possible exception of ***|{urse***) have experienced any viruses.) There are, however, times when things go wonky all on there own. Or we, the user, helps it go wonky. I have done this so many times that it's now hilarious. You say that Firefox is is having trouble opening your USB. The question that pops to mind is Why would you want to? *Go to Places->Computer->[The USB Drive]* and right click it. If the first choice is not *Open* but *Open with Other Application*, select *Open with Other Application* and choose *File Browser*. Tell us what happens.

---

### Post by lukjad on 2008-07-01
*I'm posting in series so that you can read and do something while I type away.*

Point #2: You can install clam av if you want to. I have never used it (or for that matter, any anti-virus) on Linux so you had best wait for someone else to post some help on that subject.

---

### Post by hyper_ch on 2008-07-01
clam av won't help because clam av scans for windows viruses...

I doubt very much you got a virus by email.

---

### Post by lukjad on 2008-07-01
Point #3: Since this sounds like a new install, whatever the trouble is you most likely will not loose much in the way of files and settings. Sometimes a reinstall is all it takes to fix a problem.

---

### Post by lukjad on 2008-07-01
On the other hand, since you seem to be using Firefox 2 and Thunderbird 2 you may have just finished an upgrade. Is that the case? If so there are lots of problems doing upgrades that my be solved with a completely fresh install.

---

### Post by lukjad on 2008-07-01
Also doing a "backgrade" with Firefox and Thunderbird may be causing a lot of problems. Do you have Firefox 3 and Thunderbird 3 installed? in another thread someone had both installed and his system was reeeeeaaaaaaaaaallllllyyyy slow and buggy.

---

### Post by athun on 2008-07-01
> **lukjad007 said:**
> First off, relax. Sit back, take a deep breath. 
Point #1: Linux does not get viruses. (Neither  I, nor anyone to whom I have spoken have experienced any viruses.) There are however times when things go wonky all on there own. Or we, the user, helps it go wonky. I have done this so many times that it's now hilarious. You say that Firefox is is having trouble opening your USB. The question that pops to mind is Why would you want to? *Go to Places->Computer->[The USB Drive]* and right click it. If the first choice is not *Open* but *Open with Other Application*, select *Open with Other Application* and choose *File Browser*. Tell us what happens.

Thanks for the reply.   I should have been clearer that it is not that I want to open USB with firefox but, when I plug in the USB drive I get a pop-up window offering the choice of opening the drive in a new window.   It is when I click on that button that I get the error message I quoted.   I have gone to 'file associations' and the drive should open in a Konqueror window but it doesn't.   Others have suggested the problem might be due to  installation of both firefox 2 and 3 but only firefox 2 is installed.   I also don't understand why the installed flash drive does not show up in the console command line.   And I could just reinstall but there is some data I don't want to lose which I want the flash drive to backup.   I could I guess use the DVD or CD recorder to back up that data but that still leaves the possibility that the problem, if it is a bug, could reappear.   Any further suggestions would certainly be appreciated.   Thanks again.

---

### Post by athun on 2008-07-01
> **lukjad007 said:**
> On the other hand, since you seem to be using Firefox 2 and Thunderbird 2 you may have just finished an upgrade. Is that the case? If so there are lots of problems doing upgrades that my be solved with a completely fresh install.

I did an upgrade recently (with Adept) which did include Open Office and have installed all available upgrades for all my installed files except the latest kernel upgrade and the four most recent others.   I did have firefox 3 installed also but I removed it and the problem remained.   I know that linux is pretty clean when it comes to virus but what really makes me think it could be a virus is that the USB media does not show up in the console command line.

Worse comes to worse I will reinstall and just lose the data but I sure would hate to.   Again, thanks.   Appreciate the time and attention.

---

### Post by |{urse on 2008-07-01
Lol why do people keep saying linux is immune to viruses? Educate yourselves please.

The following is a partial list of known Linux malware:

[edit] Trojans

    * Kaiten - Linux.Backdoor.Kaiten trojan horse[5]
    * Rexob - Linux.Backdoor.Rexob trojan[6]

[edit] Viruses

    * Alaeda - Virus.Linux.Alaeda[7]
    * Bad Bunny - Perl.Badbunny[4][8]
    * Binom - Linux/Binom[9]
    * Bliss
    * Brundle[10]
    * Bukowski[11]
    * Diesel - Virus.Linux.Diesel.962[12]
    * Kagob a - Virus.Linux.Kagob.a[13]
    * Kagob b - Virus.Linux.Kagob.b[14]
    * MetaPHOR (also known as Simile)[15]
    * Nuxbee - Virus.Linux.Nuxbee.1403[16]
    * OSF.8759
    * Podloso - Linux.Podloso (The iPod virus)[17][18]
    * Rike - Virus.Linux.Rike.1627[19]
    * RST - Virus.Linux.RST.a[20]
    * Satyr - Virus.Linux.Satyr.a[21]
    * Staog
    * Vit - Virus.Linux.Vit.4096[22]
    * Winter - Virus.Linux.Winter.341[23]
    * Winux (also known as Lindose and PEElf[24]
    * ZipWorm - Virus.Linux.ZipWorm[25]

[edit] Worms

    * Adm - Net-Worm.Linux.Adm[26]
    * Adore[27]
    * Cheese - Net-Worm.Linux.Cheese[28]
    * Devnull
    * Kork[29]
    * Linux/Lion (also known as Ramen)
    * Mighty - Net-Worm.Linux.Mighty[30]
    * Millen - Linux.Millen.Worm[31]
    * Slapper[32]
    * SSH Bruteforce[33]

[edit] 

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

Most of these are a mere nuisance, some are much nastier. Compare that to the bajillion win virii out there and it's a very small list and very rarely encountered but they do exist.

---

### Post by athun on 2008-07-01
> **hyper_ch said:**
> clam av won't help because clam av scans for windows viruses...

I doubt very much you got a virus by email.

Thanks for the advice re clam av.    Perhaps you are right that I do not have a virus but rather some bug, but I just don't understand why, then, the USB media does not show up in the console command line.   In effect it seems my OS (1) detects an installed USB drive, (2) insists that it be opened by firefox which, in turn, doesn't recognize the drive and (3), in contradiction, doesn't show the drive on the command line implying that the drive is not there.   Worse comes to worse I will do a reinstall but that means a probable loss of data and, unless I understand what caused the problem, the possibility that the problem, if not a virus, will reappear in the new install.   Thanks, though.   I appreciate the time and attention.   Any further thoughts would also be appreciated.

---

### Post by athun on 2008-07-01
> **|{urse said:**
> Lol why do people keep saying linux is immune to viruses? Educate yourselves please.

The following is a partial list of known Linux malware:

[edit] Trojans

    * Kaiten - Linux.Backdoor.Kaiten trojan horse[5]
    * Rexob - Linux.Backdoor.Rexob trojan[6]

[edit] Viruses

    * Alaeda - Virus.Linux.Alaeda[7]
    * Bad Bunny - Perl.Badbunny[4][8]
    * Binom - Linux/Binom[9]
    * Bliss
    * Brundle[10]
    * Bukowski[11]
    * Diesel - Virus.Linux.Diesel.962[12]
    * Kagob a - Virus.Linux.Kagob.a[13]
    * Kagob b - Virus.Linux.Kagob.b[14]
    * MetaPHOR (also known as Simile)[15]
    * Nuxbee - Virus.Linux.Nuxbee.1403[16]
    * OSF.8759
    * Podloso - Linux.Podloso (The iPod virus)[17][18]
    * Rike - Virus.Linux.Rike.1627[19]
    * RST - Virus.Linux.RST.a[20]
    * Satyr - Virus.Linux.Satyr.a[21]
    * Staog
    * Vit - Virus.Linux.Vit.4096[22]
    * Winter - Virus.Linux.Winter.341[23]
    * Winux (also known as Lindose and PEElf[24]
    * ZipWorm - Virus.Linux.ZipWorm[25]

[edit] Worms

    * Adm - Net-Worm.Linux.Adm[26]
    * Adore[27]
    * Cheese - Net-Worm.Linux.Cheese[28]
    * Devnull
    * Kork[29]
    * Linux/Lion (also known as Ramen)
    * Mighty - Net-Worm.Linux.Mighty[30]
    * Millen - Linux.Millen.Worm[31]
    * Slapper[32]
    * SSH Bruteforce[33]

[edit] 

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

Most of these are a mere nuisance, some are much nastier. Compare that to the bajillion win virii out there and it's a very small list and very rarely encountered but they do exist.

Thanks for the list.   Assuming that the problem indeed is a virus, do you have any idea of which it might be and, especially, any suggestion as to how I should proceed to get rid of it?   Or is the best or even only way to do so a full reinstall, which I would very much prefer not to have to do but will, of course, if necessary?   Really appreciate any suggestions.

---

### Post by brian_p on 2008-07-02
> **|{urse said:**
> Lol why do people keep saying linux is immune to viruses?

Because its correct?

> Educate yourselves please.

I thought I had done. 

> The following is a partial list of known Linux malware:

[Snipped]

> Most of these are a mere nuisance, some are much nastier. Compare that to the bajillion win virii out there and it's a very small list and very rarely encountered but they do exist.

We'll concentrate on the list of viruses and commence with staog. Screen cleaner to hand? Yes, I know, it's a wind up but we may as well start with a good laugh.

Now for the rest of the the so-called viruses. What we are looking for is one which can spread from user space to system space **without root assistance** and spread to other systems. When you find one let us know.

---

### Post by athun on 2008-07-02
Well, despite the dispute re whether linux systems get infected with anything serious I still have a problem, and it looks more and more like a virus.

I installed clamav (after the fact unfortunately) and it will not scan for virus.   If I try it starts and then hangs.  Unless I can solve this pretty soon I will have no choice but to do a reinstall with probable loss of some data.   If there is anyone out there who can offer advice re how to proceed or, better, how to get rid of this thing - virus or not - please respond.

Thanks.

---

### Post by The Cog on 2008-07-02
I think it's very unlikely to be a virus. But your system is borked, and the fix is probably the same either way because a re-install is probably easier than diagnosis.

You should be able to copy your data to an external drive first though. What to you mean by **doesn't show the drive on the command line**?

You should be able to mount the drive with something like
**sudo mount /dev/sdb1 /mnt**
and then copy your files off. Failing that, use a live CD of some sort to copy the data off to the external drive.

---

### Post by lukjad on 2008-07-02
Also, the /home folder usually contains all your data.
If you can copy it off or an external HD, a CD or a DVD you can always get all your info and data. If this is what you need to do remember to copy all the hidden files too. They all begin look something like *.[filename]* "filename" being of course the file name. ;) Also a fresh install will do wonders for your system. This has all the signs of a botched upgrade.

__________________________________________________

The rest of this post is a flame. If you do not like the idea of two people slinging insults back and forth like three week old cod, please stop reading now. Otherwise enjoy my sense of humor.
__________________________________________________



And to *|{urse* I just wish to say give you these quotes to chew on.

> Never attribute to malice that which can be adequately explained by stupidity.

> *Entia non sunt multiplicanda praeter necessitatem.* One should not increase, beyond what is necessary, the number of entities required to explain anything.

I am not calling anyone names here but am trying to make a point. Before we can assume the worst we must look for the simplest most direct route. If you see a man that was crushed flat as a pancake and an elephant sitting next to him, will you assume that the man was hit by a meteorite? 

Another proposal that I will give comes from the great Sherlock Holmes:

> When water is near and a weight is missing it is not a very far-fetched supposition that something has been sunk in the water.

It was easier to know it than to explain why I know it. If you were asked to prove that two and two made four, you might find some difficulty, and yet you are quite sure of the fact. One drawback of an active mind is that one can always conceive alternate explanations which would make our scent a false one. Here we have a person who has just done an upgrade on a system that is not prone to viruses. The common result of an upgrade is buggy programs, crashes, and general illness of the computer.

It seems to me that the simplest, most realistic and useful course of action is to proceed on the assumption that there is no virus and work from there. If there is a virus, a complete reinstall would most likely remove it.

> **lukjad007 said:**
> First off, relax. Sit back, take a deep breath. 
Point #1: Linux does not get viruses. (Neither  I, nor anyone to whom I have spoken have experienced any viruses.)

And please note I was speaking in general or realistic terms. It is possible to install dangerous or compromising software if given the root password. As for your list, based on that list please read [http://librenix.com/?inode=21](http://librenix.com/?inode=21).
Most if not all of the viruses on that list are old. I saw one that had infected 0-49 machines. With those odds this poor user better beware of lightning. ;) 
I probably should not have said that Linux does not get viruses. I should have said this:

> It is ferociously unlikely that your particular Linux box will ever in its normal lifetime; if properly updated and not run as root for extended periods of time especially while surfing the Internet, installing dubious programs from shady third party repositories  based in The Republic of Elbonia, so long as you do not in any way shape or form insult anyone with more money, power, or tech savvy or works for the government, or is the government, or works for or is head of any organized crime right especially those that specialize in computer crime including my not limited to computer fraud, computer hacking, computer bashing, computer smashing, etc.; and normal being only a general time frame as defined by the tech community in general, get a virus, unless you do something really, really stupid. 

Now, which rolls of the tongue more easily? I'll let you decided but, to avoid confusion I shall edit my post to reflect my new, enlightened view.

---

### Post by athun on 2008-07-02
> **The Cog said:**
> I think it's very unlikely to be a virus. But your system is borked, and the fix is probably the same either way because a re-install is probably easier than diagnosis.

You should be able to copy your data to an external drive first though. What to you mean by **doesn't show the drive on the command line**?

You should be able to mount the drive with something like
**sudo mount /dev/sdb1 /mnt**
and then copy your files off. Failing that, use a live CD of some sort to copy the data off to the external drive.

Answering this before I try your advice in order to answer your question about what I mean that the drive does not show up on the command line.   When, in file associations, I have firefox as my preferred browser application and Konqueror as preferred USB unmounted removable drive application, then when the USB flash drive is installed if I open konsole and cd to the media directory, the USB drive does not appear.   Same thing happens if I open Konqueror and display the contents of the media directory.  If I set Konqueror as my preferred browser (which I do not want) I can go to the media directory in Konqueror and I do find and can open the USB drive, but it still does not show on the Konsole command line when I cd to the media directory there and if, in this later case, I first install the USB flash drive, get the pop-up window, and then click on the button to open the drive in a new window, I get the error message about firefox which I quoted in my original post.

Will try your advice and either back-up with the USB drive or with CD drive and    reinstall    Thanks.   Really appreciate your help.

---

### Post by The Cog on 2008-07-03
An experiment to see if your KDE settings are the problem:

Log out.
At the login page, press Ctrl-Alt-F1 for a text console
Log in and use this command:
**mv .kde .kdeX**
Press Ctrl-Alt-F7 to return the the GUI
Log in (All your KDE settings are lost)
See if the broken USB drive handling is working now

If that fixes your USB drive handling, then there was something in your KDE settings that was causing the issue. You can either start doing all the settings from scratch, or you can restore the original settings and try to debug them. To restore the original settings:
Log out
Ctrl-Alt-F1
rm -rf .kde
mv .kdeX .kde
Ctrl-Alt-F7

Another thing:
With the USB stick in, the command **mount** or **df** will show whereabouts in the filesystem the thing has been mounted.

---

### Post by athun on 2008-07-04
Luckily, whatever the problem is, I can still copy my data to an external CD, so I am going to throw in the towel and just reinstall.   I agree that seems the easiest.   Want to thank all of you who tried to and did help.

---

### Post by lisati on 2008-07-04
> **athun said:**
> Luckily, whatever the problem is, I can still copy my data to an external CD, so I am going to throw in the towel and just reinstall.   I agree that seems the easiest.   Want to thank all of you who tried to and did help.

Join the club! I'm partway through a reinstall on my laptop....though in my case, it wasn't anything that arrived by email that alerted me to a problem: the name of the malware responsible is A.Silly.User.Who.Plays.Around.With.A.Faulty.Backup.Thus.Messing.Things.Up - another muck-up to contribute to the learning experience: Lesson (for me): find your way around unfamiliar software with a fresh head, instead of staying up late.

Edit: Just an aside about the viruse discussions: It's dangerous to assume that mischief won't happen just because Linux is somewhat less vulnerable to malware than Windows.

---

