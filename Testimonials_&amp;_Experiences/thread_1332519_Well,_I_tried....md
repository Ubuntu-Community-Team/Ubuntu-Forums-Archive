---
title: "Well, I tried..."
date: 2009-11-20
forum: Testimonials &amp; Experiences
---

### Post by salar on 2009-11-20
Hi all,
After a failed installation of Ubuntu on my XP-powered PC and on my other half's XP laptop, I have decided to forego the Ubuntu experience and get Windows 7. My experience went something like this, and is meant in no way to be a troll post, rather one users experience from coming to Ubuntu cold.

I followed the instructions for creating an ISO disc and found that no matter which burning software I used, I couldn't get a single working disc. All had errors on them.

I then went to plan B and used wubi to install dual-bootable Ubuntu on both computers.

The installation went very smoothly on both and worked perfectly on the laptop. The PC however refused to recognise my SB Live! soundcard and within just 1 week had refused to boot at all. 

The laptop started to fail soon after and would hang for a very long period of time before loading. There was also real issues with the wireless internet connection, as in there was none.

Reading the help files and posting to the forum lead to answers that assumed a level of PC competence that I am lacking. This is by no means a criticism of the forum members as there were some genuine attempts to get this sorted, however, when the help files start talking about altering code, I got very nervous and unsure. 

I tried. Really I did, but I'm afraid I just don't have the technical expertise to get it off the ground, and this is the real shame because when it worked it worked very very well. I loved the ease of adding and removing new applications, the clean desktop, the sheer speed compared to XP and the great open source programs that came with it. 

Who knows, perhaps in another couple of versions, when a few things have been ironed out and the help files are written with a bit more of a slant towards us stupid noobs, I would like to think that I'll be back.

Peace and it was a worthwhile exercise in the end.

John

---

### Post by hwttdz on 2009-11-20
A few things.  First this is usually a support forum, there's also a user experiences forum to share stories such as this.  

Second, when burning an ubuntu cd/dvd or really any cd/dvd setting the burn speed lower increases fidelity, also it's possible you aren't using the best quality media or that your media has a maximum burn speed which you were exceeding.  

Editing config files is easier to code/implement than gui's and once you get a little bit of a working knowledge it becomes simple to back up the config file in question, then edit it.  If the system breaks, you restore it to the previous state by dropping in the backup.  And really to do this you need only know a few commmands
sudo - superpowers
cp - copy
mv - move
cd - change directory
then a text editor.  

I recommend possibly trying using a LTS release, these are hopefully less buggy.  And possibly also waiting a few months after the release to allow bugs to be worked out.  Beta testers are a very small population, and it is not reasonable to expect them to test on every possible hardware configuration before release.  The next version is an LTS I believe, it's due out in april, so maybe June 2010 give it another go, if you have a machine that you can play around with.

---

### Post by Giblet5 on 2009-11-20
At least you tried. You'll always get respect for that alone.

+1 on the previous post. Especially the part about trying again next June with the LTS release.

---

### Post by snowpine on 2009-11-20
Sorry to hear about your negative experience. It sounds like the .iso file was corrupted. If the download was bad, you could burn 100 CDs and none of them will work.

If you decide to give it another try, use torrent software, [check the md5sum of the file]("https://help.ubuntu.com/community/HowToMD5SUM"), burn at the lowest possible speed, and then check the integrity of the burned disk. Or if you prefer, Canonical will even mail you an Ubuntu CD for free!

---

### Post by confused_user on 2009-11-20
I'm going to hazard a guess and say that you probably tried Ubuntu 9.10 - which is a pain in the *** to say the least.  I've been using Ubuntu since Hoary Hedgehog (4.something) and i have had a horrible experience with 9.10, i finally got rid of it on all 3 of my machines at home a few weeks ago.

For the most pain free Ubuntu experience - stick with the x.04 releases, 9.04 is the current.  If you bleeding edge applications and features then go for the x.10 releases, 9.10 is the current.

Beware of the x.10 releases though.

It's a shame that 9.10 has been marketed in the way it has, too much hype surrounding what is essentially a bug ridden version of 9.04.

I am sorry to hear that you have given up, i'm sure if you had got the right help we could have at least got you off the ground.  Ubuntu, GNU/Linux is not for everyone though, despite what some people would have you believe.

Windows 7 by Microsoft's standards is a good OS.  It is not without it's problems and i have to say after using both Ubuntu 9x and Windows 7 that they are closely matched.  What swung it for me was the applications available for Ubuntu, so much more variety and nobody has tried to install a tool bar or some other add related crap on my machine.

Nobody has asked me for money for the most basic of features.

ultimately i feel that Ubuntu offers infinitely better value for money and a far higher quality operating system than windows 7. 

I do agree that more effort should be put into making it viable for people with not much experience with linux though.

---

### Post by P4man on 2009-11-20
That it failed to boot after a week is probably the same issue a lot of wubi users reported. Looks like an update borked grub in some way. I dont know the solution, other than recommend you do a full install, not a wubi

That the cd failed to even write indeed points to a corrupted download. Should you want to try again, download the iso using bittorrent or at least check the md5 checksum after downloading. Making the cd is nothing ubunutu or linux specific.

As for the soundcard, I bet that would have been trivial to fix as its such  a common card. Not much point giving instructions now I guess.

The wifi could have been more tricky. It depends, most wifi cards work fine, some require a bit of console tinkering, and in some cases not even that will work. But even those rare cases there is a way to use windows drivers in ubuntu (ndiswrapper), and we could easily talk you through that. But only if you decide to give it another go :)

If not, then indeed, thanks for trying I guess. And win 7 isnt too bad if you dont mind the price (and virii)

---

### Post by jdrodrig on 2009-11-20
> **salar said:**
> 

Reading the help files and posting to the forum lead to answers that assumed a level of PC competence that I am lacking.

 and the great open source programs that came with it. 



Two minor things:

1) I wonder if anyone offers remote assistance paid support for ubuntu, in that way someone could take over your computer perform the suggested steps without you having to know all the details...

2) don't forget, that you can use most open source programs within Windows, in that way you can keep contributing by pointing out bugs or suggesting new features...

---

### Post by P4man on 2009-11-20
> **jdrodrig said:**
> Two minor things:

1) I wonder if anyone offers remote assistance paid support for ubuntu, in that way someone could take over your computer perform the suggested steps without you having to know all the details...

Of course:
[http://shop.canonical.com/index.php?cPath=31?osCsid=da75918a3b0f9df5d76bf9e9fd2451b2](http://shop.canonical.com/index.php?cPath=31?osCsid=da75918a3b0f9df5d76bf9e9fd2451b2)

Its not even that expensive TBH...

---

