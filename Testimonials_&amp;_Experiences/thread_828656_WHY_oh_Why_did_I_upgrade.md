---
title: "WHY oh Why did I upgrade"
date: 2008-06-13
forum: Testimonials &amp; Experiences
---

### Post by macpointman on 2008-06-13
I had everything working perfectly in 6.10.  Why did I upgrade to 8.04.  Nothing works now.  Cant find answers and am just getting frustrated.  I thought this was supposed to work right out of the box.  It does to an extent but the upgrade process is like pulling teeth.  Thank god I have native resolution.  before it was an easy solution now it is like you need to reinstall.  HELLO it don't want to reinstall This is Linux remember.  Am I the only one frustrated.  though I can not complain about a free operating system but if I am going to recommend this over windows its just gotta work.

I am a Lonux lover believe that it better because I have used it.  There is alot of fixing that has to occur though.

Damn I just want my 3d Accelleration to work out of the box and Beryl/ compiz.  Now I can not mount my DVD/CD drive


MacPointMan

---

### Post by cdtech on 2008-06-14
Sorry to hear about your frustrations. What type of system do you have? 
Did you do an Upgrade via the terminal or did you do a complete install with the CD?

Be sure to check your Software Sources and maybe do a sudo apt-get autoremove to clear out the old repository.

---

### Post by Victormd on 2008-06-14
I upgraded from Gutsy and was just as frustrated as you... until I did a fresh install, and everything worked straight out of the box, only minor tweaking was necessary, and now I have a very stable ubuntu running...

My guess is that, even tough it's linux and an upgrade should be very simple (and if you remove the GUI, it is), a lot has changed and I believe that from now on, things will be much simpler to upgrade because more attention is being paid to the GUI and a broader band of hardware is being supported...

---

### Post by loell on 2008-06-14
why oh why did you skip two versions of the upgrade?

after 6.10, you have 7.04, then 7.10 before you can have 8.04.

---

### Post by armandh on 2008-06-14
I still have 7.04 running on 2 boxes
and as long as it is doing the job it stays.

---

### Post by dacorr on 2008-06-14
i had an issue with mounting DVDs after install of hardy. It was confined to Movies mostly.

i checked the /etc/fstab and for the dvd drive i noted it was entered as a UFS (File System) or something close to that, i removed just that bit and it worked fine.

would surmise it had to probe for file system from that point on.

Dac

---

### Post by wolfen69 on 2008-06-14
> **macpointman said:**
> I had everything working perfectly in 6.10.  Why did I upgrade to 8.04.  Nothing works now.  Cant find answers and am just getting frustrated.  I thought this was supposed to work right out of the box.  It does to an extent but the upgrade process is like pulling teeth.  Thank god I have native resolution.  before it was an easy solution now it is like you need to reinstall.  HELLO it don't want to reinstall This is Linux remember.  Am I the only one frustrated.  though I can not complain about a free operating system but [B]if I am going to recommend this over windows its just gotta work.
[/B]
I am a Lonux lover believe that it better because I have used it.  There is alot of fixing that has to occur though.

Damn I just want my 3d Accelleration to work out of the box and Beryl/ compiz.  Now I can not mount my DVD/CD drive


MacPointMan

i tried to install vista for 2 customers. and it was a no go. nothing works! it even said on the pc, "vista ready". am i the only one frustrated? [B]if I am going to recommend this over linux its just gotta work.
[/B]

different OS, same complaint.

---

### Post by stchman on 2008-06-15
> **macpointman said:**
> I had everything working perfectly in 6.10.  Why did I upgrade to 8.04.  Nothing works now.  Cant find answers and am just getting frustrated.  I thought this was supposed to work right out of the box.  It does to an extent but the upgrade process is like pulling teeth.  Thank god I have native resolution.  before it was an easy solution now it is like you need to reinstall.  HELLO it don't want to reinstall This is Linux remember.  Am I the only one frustrated.  though I can not complain about a free operating system but if I am going to recommend this over windows its just gotta work.

I am a Lonux lover believe that it better because I have used it.  There is alot of fixing that has to occur though.

Damn I just want my 3d Accelleration to work out of the box and Beryl/ compiz.  Now I can not mount my DVD/CD drive


MacPointMan

Do a clean install of Hardy.  I have never had any luck going the upgrade route.  After the OS is instlled enable the ATI restricted driver and Compiz should work fine.

---

### Post by Sef on 2008-06-15
> I had everything working perfectly in 6.10. Why did I upgrade to 8.04. Nothing works now. Cant find answers and am just getting frustrated.

If you updated directly from 6.10 to 8.04, you would have broken your system. You need to do a clean install.

---

### Post by macpointman on 2008-07-20
This is supposed to be LINUX and better than windows.  If Windows can make an UPGRADE work and charge more than a hundred bucks for the basic upgrade. you'd think the Linux community could.  It is after all supposed to be FAR superior to Windows.

I am sorry I guess I am just frustrated.  I NEVER NEVER should have tried that upgrade option.

Now I cant even log in after the new updates.  I get nothing but a white screen when I boot into Gnome in Regular mode or Failsafe mode.  I am not well enough versed in command line to fix it.

SO what do I do.  I am keeping Microsucks as my primary on my desktop until I can get it all worked out on my notebook.  Which is effectively BRICKED. My notebook is my secondary unless I am traveling.  I don't like living without it but I can at the moment.

Doing a CLEAN install is completely out of the question at this moment.

MacPointMan

I can not effectively recommend this Operating system to my customers based upon this experience.

with 6.10 I was able to get everything running.  I am going on almost 6 months now with the same problem and no answer.  with 6.10 I could find an answer within minutes.  NOW after the newest updates NOTHING AT ALL just plain old whight screen.

Ubuntu Linux does not "Just work" right now.

MacPointMan

---

### Post by michael_1234 on 2008-07-20
> **macpointman said:**
> This is supposed to be LINUX and better than windows.  If Windows can make an UPGRADE work and charge more than a hundred bucks for the basic upgrade. you'd think the Linux community could.


Upgrading is a little different than updating. I had some people accidentally install SP3 on Windows -- presumably just a "service pack" -- and hose their system. But going from Windows 95 to Windows Vista (or... Ubuntu 6.10 to 8.04)....well, Good Luck. Backups would be part of any upgrade like that, on windows/mac/solaris/linux etc. But it's pretty obvious that telling you that now won't relieve your frustration (the most frustrating things in life are the stupid things we ourselves do).

Other linux distro's (I'm thinking of Fedora) pretty much presume a clean install. A "yum" upgrade from fedora 7 to 8 was a serious "at your own peril". I'm shocked / surprised that my ubuntu 7.10 went to easily to 8.04, personally.  And, yes, I backed up first (more on this, below).

>  I am sorry I guess I am just frustrated.  I NEVER NEVER should have tried that upgrade option. 

Not without backing up, first.


>  SO what do I do.  I am keeping Microsucks as my primary on my desktop until I can get it all worked out on my notebook.  Which is effectively BRICKED. My notebook is my secondary unless I am traveling.  I don't like living without it but I can at the moment.

Doing a CLEAN install is completely out of the question at this moment.


Ask yourself what, exactly, is out of the question? What is it that you can't afford to wipe clean? Your OS? Your applications? Or your files? In Linux, those are three different things. (In Windows, they are pretty tightly coupled).  

When I backup (before an upgrade.. ahem): I backup my paritions (for a complete restart if the system is totally hosed) and I backup my files (useless for a complete restore, but great for cherry-picking files to restore afterwards).

Your files are probably still fine. Use something like a bootable "gparted" CD, copy all your *files* to an external disk (it's not too late to back those up). Optionally, copy applications as well (though, you might just want to re-install these). 

Do a clean install. A good idea is to create a partition just for the OS, and a separate partition for files / custom applications.

After the install, copy your files back to your home directory from the external disk.



>  I can not effectively recommend this Operating system to my customers based upon this experience.

Ubuntu Linux does not "Just work" right now.

MacPointMan

Now you're just talking out of anger. Which, I understand, I've been there before, too. I'm happy that my laptop still works after throwing it across the room (when it had windows on it). But seriously (although, that was in all seriousness), I've personally had a lot better luck with linux on desktop systems than laptops. Laptops have sketchier support (eg, they are less standard...?) for linux when it comes to (eg) drivers, etc.  For example, trying to get beryl/compviz working on my laptop under fedora was a total waste of time (and probably hozed that system) ... since eventually I realized that my graphics card didn't support it...! Not all hardware is created equal.

Good luck, & hang in there,
-m

ps: you have to admit, linux "support" IS better than MS support. I assume you've tried to get support from MS before? (And, no, Dell support doesn't count.)

---

### Post by |{urse on 2008-07-20
Sorry man, that really sucks but you will fix these things sooner or later. Necessity is the mother of invention etc. etc. so get to work .lawl.

> Linux; If you installed it once, you're doing it wrong

---

### Post by solwic on 2008-07-20
> **macpointman said:**
> 

Ubuntu Linux does not "Just work" right now.

MacPointMan

Nope, it never has.  And it never will.  No OS will work for 100% of computers out of the box.  

I think you've got the answer to your dilemma:  use your desktop to burn a copy of the 8.04 disk and reinstall from scratch.  I know it sucks, and you shouldn't have to do that...but in this case it seems like you do, and being upset that it works that way doesn't stop it from working that way.  :(

Good luck, and know that you're not the only one with these problems with Hardy.  The trick is to fix what you can, using whatever help you can, and offering help to those having the same problems.  That's what'll make it better.  :)

Cheers!

---

### Post by hyper_ch on 2008-07-20
> **macpointman said:**
> This is supposed to be LINUX and better than windows.  If Windows can make an UPGRADE work and charge more than a hundred bucks for the basic upgrade. you'd think the Linux community could.  It is after all supposed to be FAR superior to Windows.

Have you tried to upgrade Win2000 to VISTA Business Professional? I don't think you can do that ;)

---

### Post by kevdog on 2008-07-20
Im going to sympathetic, and throw and idea out there -- it should be possible to upgrade from one LTS to another.  That's the entire LTS rationale -- LTS support should be continuous.  It shouldn't require all the intermediate upgrades.

---

### Post by hyper_ch on 2008-07-20
well, kevdog, he didn't upgrade from LTS to LTS ;)

> **macpointman said:**
> I had everything working perfectly in 6.10.  Why did I upgrade to 8.04.

Besides, LTS to LTS upgrade works.

---

### Post by Methuselah on 2008-07-20
Ubuntu moves a little faster than windows.
In the years between windows releases ubuntu has several.

However, I'm thinking the upgrade option should NOT be offered if its unlikely to work.

---

### Post by Sef on 2008-07-20
> However, I'm thinking the upgrade option should NOT be offered if its unlikely to work.

That depends on one's hardware.  It is impossible to test every conceivable configuration.

---

### Post by Canis familiaris on 2008-07-20
I hope there should be a way which does not technically upgrade the system but just installs the corresponding programs in the repos(i.e. corresponding programs installed by APT from old version to other) and migrate the /home directory. 
It would be more simpler and efficient.

---

### Post by silkstone on 2008-07-20
I have an old desktop which went Edgy > Feisty > Gutsy > Hardy by the upgrade route and everything worked each time. Also have a new desktop with a clean install of Hardy, and the same for a laptop - both worked with no glitches. I've been lucky I guess, and I can understand the OP's frustration, but there are bound to be problems for some people when running Linux (any flavour) on hardware designed for Windows.

I agree 100% with Anurag_panda that it should be possible for us to stick with a version of Ubuntu that works for us, but still be able to get the latest versions of the bundled software. This is a big drawback of the 6-month upgrade cycle as it is currently implemented - we don't have to upgrade the OS, but then we're left with outdated applications.

---

### Post by Canis familiaris on 2008-07-20
> **silkstone said:**
> I agree 100% with Anurag_panda that it should be possible for us to stick with a version of Ubuntu that works for us, but still be able to get the latest versions of the bundled software. This is a big drawback of the 6-month upgrade cycle as it is currently implemented - we don't have to upgrade the OS, but then we're left with outdated applications.
I actually meant to have the new version to be freshly installed and along with its corresponding applications of applications installed in the previous OS to be installed automatically not what you interpreted but I agree with you. Older versions of Ubuntu should also offer to install programs like Firefox 3 from the repos.
However do mind that the programs are updated in older releases as well till they are supported but there are no major increments.

---

### Post by nickdbliss on 2008-07-20
Ah yes upgrade sucks. I did it from 7.04 to 8.04 and no 3d acceleration now and a lot of other problems. Even fresh install of hardy didnt work. So i am stuck with it until i find a solution someday. Take care. For me no upgrades next time.

---

### Post by hyper_ch on 2008-07-20
well, if you upgraded from 7.04 to 8.04 you skipped a release in the middle ;) hence not really recommended.

---

### Post by nickdbliss on 2008-07-20
> **hyper_ch said:**
> well, if you upgraded from 7.04 to 8.04 you skipped a release in the middle ;) hence not really recommended.

Yeah but i did fresh install as well. 7.04 didnt give me that much trouble as hardy gave. I ll wait till next release.

---

### Post by michael_1234 on 2008-07-20
> **silkstone said:**
>  ...I agree 100% with Anurag_panda that it should be possible for us to stick with a version of Ubuntu that works for us, but still be able to get the latest versions of the bundled software. This is a big drawback of the 6-month upgrade cycle as it is currently implemented - we don't have to upgrade the OS, but then we're left with outdated applications.

> **Anurag_panda said:**
> I actually meant to have the new version to be freshly installed and along with its corresponding applications of applications installed in the previous OS to be installed automatically not what you interpreted but I agree with you. Older versions of Ubuntu should also offer to install programs like Firefox 3 from the repos.
However do mind that the programs are updated in older releases as well till they are supported but there are no major increments.


Just to let the other casual readers of this thread know: you're not totally stuck if running an older distro.  The "Backports" repo does (somewhat) assist with this exact issue -- but not in all cases, of course.  So, you can have an older version of the OS and still get the newer software, IF it has been "backported" to the older version of the OS. 

[LIST]
[*][https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) - "The Backports team believes that the best update policy is a mix of Ubuntu's security-only policy AND providing new versions of some programs. Candidates for version updates are primarily desktop applications, such as your web browser, word processor, IRC client, or IM client. These programs can be updated without replacing a large part of the operating system that would affect stability of the whole system."
[/LIST]
I recently did this with a very non-essential command-line developer tool (cmake); so it's not as limited as it sounds. 

And, of course, there's always installing from the source. That usually works. I don't even make a package for some of these things: I stick them up in /opt or something (separate partition from the main OS and /home for backup and clean install purposes).

Also, on a personal note: I install SO MUCH crap (I'm a little too happy with package managers) that a "clean install" is really just like spring cleaning. Though, every other spring might suffice.

-michael

---

### Post by bmac on 2008-07-21
I've also used the upgraded route from FF to Gusty to HH on numerous machines (at least 15 now) and have never had an unsuccessful upgrade. Wonder why????

Of course I do spend time selecting Linux compatible hardware (when possible) and always backup the system prior to upgrade. Probably would fail if I didn't back it up....:lolflag:

---

### Post by macpointman on 2008-07-22
> **bmac said:**
> I've also used the upgraded route from FF to Gusty to HH on numerous machines (at least 15 now) and have never had an unsuccessful upgrade. Wonder why????

Of course I do spend time selecting Linux compatible hardware (when possible) and always backup the system prior to upgrade. Probably would fail if I didn't back it up....:lolflag:

It is me the Dumb Butt who decided to skip an iteration or two of upgrade cycles.  But Giving Linux Credit I had it working.  Until the most recent update came out several weeks ago.

While working on my system and reinstalling my drivers per the system manager Now I only get a White Screen of death.  This has been a problem in the past and has been able to be solved with logging into a Failsafe GNOME session and uninstalling the ATI drivers  and verifying my Xorg config file.

To be perfectly honest any real computer tech will tell you that a complete clean reinstall is completely out of the question unless of course he or she has reached it as the last option.  repairing the current installation should be possible in the grand majority of the cases.

Linux is one of those operating systems that well quite frankly is quite hard to completely hose and can be repaired quite easily if someone knows how to do so.  Unfortunately Joe Citizen is not one of those people and I am relatively new to the OS.

I completely dumped windows in a situation that many would never have even though of doing.  It gave me something to do, Kept me sane, and may have even kept me alive.  SO for that I have 6.10 to thank.

Lets get LInux where it needs to be.

MacPointMan

---

### Post by macpointman on 2008-08-03
first of all I want to appologize fr my frustrations.  I was pretty upset and frustrated at the time.  I do believe that Ubuntu works pretty well and with any OS there are going to be issues somewhere along the line.  Nothing or no one is perfect.

I just miss my sleek running Ubuntu Notebook.  Yes I will get it back online.  Yes i will get the newest latest and greatest stable version of Ubuntu on it running just the way I like it.  Yes others will be very impressed with my non widows Box and Notebook especially when they find out the OS is free and relatively easy to use.

SO please forgive me for being upset and seemingly trashing what is indeed a superior OS to windows.

MacPointMan

---

