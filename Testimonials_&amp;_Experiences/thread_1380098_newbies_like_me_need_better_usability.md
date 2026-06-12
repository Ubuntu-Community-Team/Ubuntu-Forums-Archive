---
title: "newbies like me need better usability"
date: 2010-01-13
forum: Testimonials &amp; Experiences
---

### Post by suggestions on 2010-01-13
Hello to everybody,
this is my very first message.. first of all thank you to exist.. I hope to contribute to ubuntu, because I love linux, but it is sometimes very difficult to use for an end-user like me.. what I'm about to say can be useful for making ubuntu more palatable to the general user..

I'm writing from my eeePC701 4g (the first netbook, made by Asus, running linux xandros).. I have also installed ubuntu 9.10 karmic koala in a SSD card, but I have to keep xandros in the original internal SSD hard disk, because..

..because xandros in the eeepc is still unsurpassed

a part the boot time (22 seconds against 105 seconds of ubuntu 9.10), and apart the symbolic names (the usb drives in the file manager appear as D, E, F, and so on, like windows.. very nice, certainly better than "1f34-g6h3" in ubuntu), the BIG problem in linux is still the installation process..

in xandros the problem is "solved" in the sense that I cannot update my eeePC.. but in the following example this is still BETTER than installing in linux

take for example clam antivirus:

in xandros:
- i have an icon to launch
- i can update it
- i have a configuration GUI
- it is integrated in the file manager

in ubuntu:
- i installed it from the repositories
- there is no icon to click on
- i tried to launch it from the terminal (clamscan) but i didn't find a way to configurate it
- i don't have a gui to configure it
- it doesn't appear in the list of installed software (in the software center.. so i had to use synaptic to remove it)

conclusion:
i use clamav in xandros, and i removed it in ubuntu.. i have no time to waste in programming my OS for doing a very basic operation like a virus scan!

- I recently left the wonderful and fastest puppy linux because to install new applications and their icons is too difficult for me.. same problem as ubuntu..

a final note:
in windows you have an icon, and you always know where the programs are..

I'm nevertheless very happy to see that ubuntu is improving more and more at each release..

thank you for your attention
best regards to all
freg

---

### Post by Cheesemill on 2010-01-13
ClamAV doesn't appear in the menus because it's a command line program.

Install clamtk as well, it's a graphical front-end for ClamAV.

PS - Unless you are running a mail or file server for Windows clients there is no need for AV in Ubuntu.

---

### Post by sisco311 on 2010-01-13
clamav is cli anti-virus utility.

If you need a GUI you have to install [clamtk]("apt://clamtk") (click the apturl link to install it).

But, why do you need an anti-virus anyway? Are you running a file or mail server with Windows clients?

Check out this guide: [thread=510812]Ubuntu Security[/thread].

---

### Post by dmillerct on 2010-01-13
> **sisco311 said:**
> clamav is cli anti-virus utility.

If you need a GUI you have to install [clamtk]("apt://clamtk") (click the apturl link to install it).

But, why do you need an anti-virus anyway? Are you running a file or mail server with Windows clients?

Check out this guide: [thread=510812]Ubuntu Security[/thread].

You guys just posted the exact same thing 1 min apart. :o

@OP: While there is a definite learning curve when using linux (even when going from a distro like Ubuntu to Kubuntu). It can be a steep curve depending on your background and patience level but once you have grasped the general concept as well as philosophy surrounding it, I guarantee you will never want to go back. 

Keep at it, the results are worth it.

(oh and if you think a vanilla Ubuntu install is bad, stay away from Arch. ;))

---

### Post by stoogiebuncho on 2010-01-13
A couple of things:

1) Letter drives.  Coming from a Windows background (I assume), it makes sense that you would prefer drives to have a letter assigned to them the way Windows does it.  But a lot of people don't like that, as a letter doesn't give you any information about what sort of media it is.  Ubuntu is set up this way because that's the way we are used to, and it's the way that makes sense to us.

2) Installation in Ubuntu is actually pretty easy.  Next time you want to install something, use the Ubuntu Software Center (in your applications menu).  It sets up menus, icons and everything else automatically.  I'm guessing you used Synaptic when you installed ClamAV - Synaptic is meant for more experienced users, which is why it has both the command line version and the gui version.  If you had installed through the software center it would have worked very much like it does in Xandros.

3) It sounds like Xandros is really working out great for you, which makes me curious as to why you want to use Ubuntu.  The great thing about having so many distributions is that everyone can find the one that works the best for them.  So if Xandros is doing it for you, more power to you!

4) As has been mentioned before, you don't need to use an Anti-Virus program on linux unless you are connected to Windows computers.  And even then, the anti-virus program doesn't protect linux, it's just there to protect the Windows computers!

5) Welcome to Ubuntu Forums and thank you for your feedback.

---

### Post by sisco311 on 2010-01-13
> **dmillerct said:**
> You guys just posted the exact same thing 1 min apart. :o


Great minds think alike. :)


@OP:

Labeled devices that automount will be mounted in the /media directory using their label as the mount point, /media/<label>. 

To change a partition's label go to System -> Administration -> Disk Utility.

---

### Post by oldos2er on 2010-01-13
"in windows you have an icon, and you always know where the programs are.."

How long have you been using Windows? 

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by suggestions on 2010-01-13
Hi to all,
I love you.. thanks to your kind help now I have clam-av working! :-)

the difficulty was again my ignorance!

I want to reply here to everybody, because feedback is always very important in a community..

1) I have just installed clamtk.. I wrongly thought that it were just a GUI of clam-av, so I used synaptic to install clam-av.. then, not finding clam-av nor its icon or launcher I tried the clamscan command in the terminal, then I surrended (windows-like mind, I know!).. THIS WAS THE DIFFICULTY

2) I use the antivirus because I don't want to unwittingly infect other people by sharing infected files (.exe downloaded files, for example).. I am "linuxed" (immunized), but my friends are not!

3) I'm in the learning curve since two years.. I don't want to go back.. you can bet on this.. some times I have to go back to windows (for my canon printer, for example, or for few old programs that wine doesn't like)..

4) ok friends, I will forget gradually the letter drives :-)

5) I use synaptic only as a desperate user, not as an experienced user!!

6) I want to use ubuntu because xandros is too limited.. but xandros is good for newbies, so I use it as a life-saver.. I use ubuntu because I want to leave windows completely and with xandros is impossible (but with ubuntu and with your help now it seems to be possible).. 

a final note:

about Ubuntu Software Center:
to see it in the menu has been a *wonderful* surprise, a thing desired since a long time.. A BIG THANK YOU TO THE COMMUNITY for this..


> Welcome to Ubuntu Forums and thank you for your feedback.
  
thank you to you to exist!

freg

---

### Post by mikewhatever on 2010-01-13
Why not install things with the Software Center? I am quite certain Klam is there too.;)

---

### Post by admiralspark on 2010-01-13
Out of curiosity, are you using the Ubuntu Netbook Remix? It's made specifically for netbooks....

---

### Post by lavinog on 2010-01-13
100+ seconds to boot is not normal...it should be more like 10.

---

### Post by suggestions on 2010-01-13
> **admiralspark said:**
> Out of curiosity, are you using the Ubuntu Netbook Remix? It's made specifically for netbooks....

I tried ubuntu NR, but on my eeePC (7 inches screen) also ubuntu NR suffers the problem that certain configuration windows with options must be moved up with alt-mousedrag, because they are too long in height.. that's why I preferred to use the normal ubuntu.. I have found a very little difference..

---

### Post by suggestions on 2010-01-13
> **lavinog said:**
> 100+ seconds to boot is not normal...it should be more like 10.

I agree, but unfortunately in my eeePC (701 4g) this last boot took 105 seconds.. xpud completed the boot from usb key in 38 seconds.. of course they are very different.. I prefer ubuntu

---

### Post by bodhi.zazen on 2010-01-13
> **suggestions said:**
> Hello to everybody,
this is my very first message.. first of all thank you to exist.. I hope to contribute to ubuntu, because I love linux, but it is sometimes very difficult to use for an end-user like me.. what I'm about to say can be useful for making ubuntu more palatable to the general user..

I'm writing from my eeePC701 4g (the first netbook, made by Asus, running linux xandros).. I have also installed ubuntu 9.10 karmic koala in a SSD card, but I have to keep xandros in the original internal SSD hard disk, because..

..because xandros in the eeepc is still unsurpassed

a part the boot time (22 seconds against 105 seconds of ubuntu 9.10), and apart the symbolic names (the usb drives in the file manager appear as D, E, F, and so on, like windows.. very nice, certainly better than "1f34-g6h3" in ubuntu), the BIG problem in linux is still the installation process..

in xandros the problem is "solved" in the sense that I cannot update my eeePC.. but in the following example this is still BETTER than installing in linux

take for example clam antivirus:

in xandros:
- i have an icon to launch
- i can update it
- i have a configuration GUI
- it is integrated in the file manager

in ubuntu:
- i installed it from the repositories
- there is no icon to click on
- i tried to launch it from the terminal (clamscan) but i didn't find a way to configurate it
- i don't have a gui to configure it
- it doesn't appear in the list of installed software (in the software center.. so i had to use synaptic to remove it)

conclusion:
i use clamav in xandros, and i removed it in ubuntu.. i have no time to waste in programming my OS for doing a very basic operation like a virus scan!

- I recently left the wonderful and fastest puppy linux because to install new applications and their icons is too difficult for me.. same problem as ubuntu..

a final note:
in windows you have an icon, and you always know where the programs are..

I'm nevertheless very happy to see that ubuntu is improving more and more at each release..

thank you for your attention
best regards to all
freg

Moved to testimonials and experiences.

Use what OS you are comfortable with. Since there are no known active viruses for Linux you can simply stop scanning for viruses, problem solved.

---

### Post by HappyFeet on 2010-01-13
ClamAV stinks. I did a test on a heavily infected windows machine between clamav and avg.

ClamAv found 2 viruses and AVG found 12. Nuff said about *that*.

---

### Post by coffeecat on 2010-01-13
> **suggestions said:**
> I agree, but unfortunately in my eeePC (701 4g) this last boot took 105 seconds.. xpud completed the boot from usb key in 38 seconds.. of course they are very different.. I prefer ubuntu

I've just timed a bootup of Ubuntu Karmic NBR on my EeePC 701 4G. Including a POST of about 15 seconds, I got a usable desktop in 65 seconds from pressing the power button. That's an approx 50 second bootup from the time the BIOS screen disappears with autologin.

If you are getting >100 seconds on the same hardware with Karmic NBR, something is wrong. Were you booting from a USB flash drive, an SD card or from an installation to the internal drive?

---

### Post by lavinog on 2010-01-13
> **coffeecat said:**
> I've just timed a bootup of Ubuntu Karmic NBR on my EeePC 701 4G. Including a POST of about 15 seconds, I got a usable desktop in 65 seconds from pressing the power button. That's an approx 50 second bootup from the time the BIOS screen disappears with autologin.

If you are getting >100 seconds on the same hardware with Karmic NBR, something is wrong. Were you booting from a USB flash drive, an SD card or from an installation to the internal drive?

Wow, I don't have a netbook yet, but that still seems odd that it takes 50 secs.
Are you running bootchart?...if so, you might want to remove it when you don't need it, bootchart adds a significant amount of time to the boot up.
Is this with an SSD or mechanical drive?

---

### Post by Methuselah on 2010-01-14
I don't run AV in Ubuntu.
If my friends are running windows they should be running AV in the extremely unlikely event that I transmit a windows virus to them.

Also the lack of drive letters is a blessing when you realise what you gain by being free from that automatic policy.
Way back when I first used a Unix-like system 'mount points' were a mystery to me.
Eventually, I understood: your storage resource can appear as any folder not just a top level drive letter and once it is mounted you do not have to care whether it is physically a USB stick or network share.
Windows' way of doing things seems rather quaint and undesirable to me now.

---

### Post by longtom on 2010-01-14
> **suggestions said:**
> 
I'm writing from my eeePC701 4g (the first netbook, made by Asus, running linux xandros).. I have also installed ubuntu 9.10 karmic koala in a **SSD card**, but I have to keep xandros in the original **internal SSD hard disk**, because..


Wouldn't having Ubuntu on a SSD card slow down the bootup?...

---

### Post by suggestions on 2010-01-14
> **coffeecat said:**
> I've just timed a bootup of Ubuntu Karmic NBR on my EeePC 701 4G. Including a POST of about 15 seconds, I got a usable desktop in 65 seconds from pressing the power button. That's an approx 50 second bootup from the time the BIOS screen disappears with autologin.

If you are getting >100 seconds on the same hardware with Karmic NBR, something is wrong. Were you booting from a USB flash drive, an SD card or from an installation to the internal drive?

I boot from an SD card (8 GB).. by the way from the same SD card the puppy linux 4.31 desktop was ready in 48 seconds (half the time)..

---

### Post by longtom on 2010-01-14
> **suggestions said:**
> I boot from an SD card (8 GB).. by the way from the same SD card the puppy linux 4.31 desktop was ready in 48 seconds (half the time)..

That is long as well - for Puppy Linux.  Puppy is a lot lighter than Ubuntu and since you run the standard Ubuntu on a netbook you should expect Ubuntu to take longer being a "normal" distro and not an especially light one (like Puppy, dsl, SliTaz etc...).

In other words, loading times of Puppy are not comparable with Ubuntu loading times.  You could take....Fedora or OpenSuse or one of those distros for a more accurate idea whether the distro or your hardware slows down the bootup.

---

### Post by suggestions on 2010-01-14
> **longtom said:**
> That is long as well - for Puppy Linux.  Puppy is a lot lighter than Ubuntu and since you run the standard Ubuntu on a netbook you should expect Ubuntu to take longer being a "normal" distro and not an especially light one (like Puppy, dsl, SliTaz etc...).

In other words, loading times of Puppy are not comparable with Ubuntu loading times.  You could take....Fedora or OpenSuse or one of those distros for a more accurate idea whether the distro or your hardware slows down the bootup.

I can already tell you something about this.. in fact on the sane SD card I had also fedora 10, and the boot time was about 120 seconds.. I used the bloated fedora because in the past ubuntu and puppy could not work well with my wireless.. 

I have read that other people have a noticeably shorter boot time.. do you think that I have some hardware problems? If so, do you have some opinion about the nature of the problem? Thank you in advance!

---

### Post by Tamlynmac on 2010-01-14
> suggestions
I have read that other people have a noticeably shorter boot time.. do you think that I have some hardware problems? If so, do you have some opinion about the nature of the problem? Thank you in advance!

Might I suggest you post help questions in the appropriate help section of the forum. The T&E is not a support section of the forum (see this [sticky]("http://ubuntuforums.org/showthread.php?t=1343965") and the T&E header).

Good Luck.

---

### Post by lavinog on 2010-01-14
> **longtom said:**
> Wouldn't having Ubuntu on a SSD card slow down the bootup?...

It shouldn't.  SSD drives are supposed to be faster than conventional hard drives.
([http://arstechnica.com/gadgets/news/2010/01/old-computers-get-young-with-ssd-upgrades.ars](http://arstechnica.com/gadgets/news/2010/01/old-computers-get-young-with-ssd-upgrades.ars))

I have even installed ubuntu on a compact flash card and got boot times <20 secs.

I am suspecting the problem might be hardware related, but not due to the drive, but something else like the wireless device.

Maybe you can install bootchart and see what part of the boot process is taking so long.  The charts will be located in /var/log/bootchart
Once the problem is fixed, you should remove bootchart so it isn't making a chart on every boot.

---

### Post by coffeecat on 2010-01-14
> **suggestions said:**
> I have read that other people have a noticeably shorter boot time.. do you think that I have some hardware problems? If so, do you have some opinion about the nature of the problem? Thank you in advance!

Yes, I have an opinion about the nature of the problem! :wink: You're booting from an SD card which is slower that an internal SSD, and slower than a USB flash drive. My 50 seconds was from the 4G internal SSD. As someone else has explained, Puppy Linux is extremely lightweight - no wonder it boots faster than Ubuntu.

It's misleading measuring boot-times with an SD card. Consider Linux on an SD card as a convenience. It can't be fast.

---

### Post by lavinog on 2010-01-14
Now I am not sure if everyone is talking about ssd or sd cards, but I have found many users complaining about slow boots on netbooks with SSDs...bug: [https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852?comments=all](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852?comments=all)
Basically, it looks like you shouldn't be using Karmic if you have a SSD.

---

### Post by suggestions on 2010-01-15
> **lavinog said:**
> Now I am not sure if everyone is talking about ssd or sd cards, but I have found many users complaining about slow boots on netbooks with SSDs...bug: [https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852?comments=all](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852?comments=all)
Basically, it looks like you shouldn't be using Karmic if you have a SSD.

in my opinion the bug can be in the grub loader.. 

because of the fact that it is a beta, I didn't give value to the fact that it actually stays frozen there for about a minute.. I thought: "it's a beta".. but having read the SDD problem in the link that you suggested to me ([https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852?comments=all](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852?comments=all)) I now understand that what is happening can destroy my SD card.. this is why I certainly will keep xandros in my eeepc SSD

details below:

I suspect that most time is wasted in some useless repetitive write/read operations..

the bug can be in the new grub boot loader.. in my eeepc 701 4g I select the option to boot ubuntu, and then the text menu stays there for about 45 seconds, then is replaced by ubuntu logo (monochrome white, center of the screen), and then with the brown wallpaper where a cursor goes from left to right and viceversa.. then I'm ready (100-110 seconds)..

now I have installed bootchart, and then I will tell you more..

in the meantime, thank you for your message

---

### Post by bobbins on 2010-01-16
I think one of the common mistakes from Windows users switching to Ubuntu is the obsession with anti-virus. Not sure about your boot up issues but there is no need to worry about the anti-virus aspect of your install.

---

### Post by stoogiebuncho on 2010-01-16
> **Tamlynmac said:**
> Might I suggest you post help questions in the appropriate help section of the forum. The T&E is not a support section of the forum (see this [sticky]("http://ubuntuforums.org/showthread.php?t=1343965") and the T&E header).

Good Luck.


The OP actually posted this in the Absolute Beginners area, but the mods moved it to T&E.  Not really sure why.

---

### Post by Tamlynmac on 2010-01-16
> stoogiebuncho
The OP actually posted this in the Absolute Beginners area, but the mods moved it to T&E.  Not really sure why. 	

I don't either, since this isn't a support or debating section of the forum. I find it baffling. :-k

Help provided here will not show up in a query of the help sections. Which basically necessitates a search of the entire forum (open forums) or at the least adding the T&E to the query. I've often wondered how many individuals have queried the help sections and missed responses in the T&E or even the Cafe. Since the T&E is not a support section, I doubt that many would include it in a search. Especially, if they've read the T&E header and/or the sticky. :confused:

Perhaps, narrowing down the search function would help minimize the work load on the servers. If all the support questions stayed in the help sections, than one would only need to query the help sections to find answers. idk?

---

### Post by lavinog on 2010-01-17
I think it was moved because the OP did not explicitly ask for help, but instead described differences between the OSes

---

### Post by bodhi.zazen on 2010-01-17
> **stoogiebuncho said:**
> The OP actually posted this in the Absolute Beginners area, but the mods moved it to T&E.  Not really sure why.

> **Tamlynmac said:**
> I don't either, since this isn't a support or debating section of the forum. I find it baffling.

> **lavinog said:**
> I think it was moved because the OP did not explicitly ask for help, but instead described differences between the OSes

As lavinog correctly stated, if you read the first post it is not a request for support.

I am not sure I see the discussion of SSD drives as "support" either.

I suggest you keep support discussions in the support sections of the forums and if you see a support question in T&E, please either report it so it can be moved or, rather then providing support here, suggest to the person requesting support that T&E is not for support.

The staff does not review each and every thread, let alone each and every post. This discussion has unfolded naturally as the participants meandered from one topic to another. Nothing wrong with that, but concluding that the staff somehow orchestrated it is a reach.

---

### Post by stoogiebuncho on 2010-01-17
> **bodhi.zazen said:**
> As lavinog correctly stated, if you read the first post it is not a request for support.

I am not sure I see the discussion of SSD drives as "support" either.

I suggest you keep support discussions in the support sections of the forums and if you see a support question in T&E, please either report it so it can be moved or, rather then providing support here, suggest to the person requesting support that T&E is not for support.

The staff does not review each and every thread, let alone each and every post. This discussion has unfolded naturally as the participants meandered from one topic to another. Nothing wrong with that, but concluding that the staff somehow orchestrated it is a reach.

Sorry, I didn't mean to imply that staff had orchestrated anything.  We all greatly appreciate the time and work you guys put into this thing.

I would argue that there was an implied question in the first post.  Namely: "How do I make ClamAV work in Ubuntu the way it works in Xandros."  And I responded to Tamlynmac's comment that this thread should not be in T&E  because I wanted to make sure that the OP didn't catch any flack since it was not the OP who put it here.

At this point, however, this thread has moved through so many topics that it doesn't really fit under any label.  :)

Maybe my clarifying only muddies the waters further, but I do want to reiterate my gratitude for ubuntuforums.org staff.  And in the end, it doesn't really matter that much where threads end up anyway. :)

---

### Post by bodhi.zazen on 2010-01-17
Thank you, it was not my intention to sound terse, just clarify why I moved this thread.

---

