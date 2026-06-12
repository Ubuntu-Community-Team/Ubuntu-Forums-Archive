---
title: "Examples of FOSS being equal/superior to commercial/proprietary software?"
date: 2022-04-27
forum: Ubuntu, Linux and OS Chat
---

### Post by ATSC on 2022-04-27
Hey,


as the title says: Can someone give examples for FOSS application software for daily use that are equal or even superior in its quality-in-use (usability, functionality etc.) compared to its commercial/proprietary counterpart? Excluded is niche/nerd/admin/highly specialized software, operating systems etc...

cheers

---

### Post by TheFu on 2022-04-27
It is all a matter of opinion.  For cost alone, all F/LOSS is "superior" to a commercial product for many people.
At this stage, the only commercial software I use is software where they don't make a F/LOSS version.  I was using a commercial video editor the last decade until the last 4 months or so.  That has been replaced by a F/LOSS editor, which is far from perfect and does some things that I'd do differently. I actually use an editing script that I created much of the time because I don't need frame accurate edits all the time.

If you'd like to do some research on the topic, I'd point at **alternativeTo.net**. Decide for yourself.

There are lots of f/loss tools that I use daily and cannot live without that have no parallel in commercial software. I suspect most people take them for granted.

X11
xterm
ssh
wget
libvirt, kvm, qemu, virt-viewer
keepassxc
gbiff
bash/perl/sed/awk

BTW, I consider all of those end-user tools, since using any Unix-like OS without them is like cutting off an arm and both legs.  Sure, lots of end-users choose that mode with the computers, but that wasn't the purpose for Unix.  Unix was designed to provide simple, power, to end-users.

---

### Post by him610 on 2022-04-27
> Excluded is niche/nerd/admin/highly specialized software, operating systems etc...

That could cover a lot of examples.
Does your exclusion mean that 500 of the world's super computers running some form of open source software can not be an example?

---

### Post by Tadaen_Sylvermane on 2022-04-27
Any shell in *nix stuff is light years ahead of the CMD prompt in Windows. I also find the Snap system better. Not a huge fan but at least it's somewhat sandboxed unlike Windows stuff which roams free around your system. KVM  is far easier to use and with more features than HyperV. The concept of shared libraries instead of a different one in memory for each program is simply perfect. LVM is a blessing from above. For the time being secure boot is optional and I see no forecast of it being required for Linux. I'm running an i7-3770 and I will be able to run it till it dies unlike Windows 11 which demands I buy / build a new machine despite this machine having a truckload more muscle than I actually need for my normal daily use. Oh, and Docker (pretty sure it's now open?). I don't even know what proprietary software that can compete with it.


About all I got at the moment. This thread made me realize I don't do much with my machine other than a bit of gaming and just googling around a ton, learning more about *nix stuff, and email.

---

### Post by DuckHook on 2022-04-27
LXD

It not only sandboxes pretty much every app that I run, it gives me instant peace of mind and real time redundancy/recovery through snapshots/rollbacks. It allows me to easily clone and port my entire working environment to any machine that has LXD installed. My base OS remains pristine, all monkeying around occurs within the LXD container—therefore, all breakage is fixable via a simple rollback. It allows me to routinely copy the most complex platforms onto clone servers for easy&#8209;peasy mirroring.

Windows/Apple cannot even begin to glimmer about fantasizing about dreaming of such power. Not only is LXD "superior" to any proprietary counterpart—there *is* no proprietary counterpart.

The only problem is its wickedly steep learning curve, but it qualifies under your conditions: I'm an end user and I put LXD to daily use. In fact, because it underlies every other app I use, it is by far the most used app/platform on my whole PC ecosystem.

Details in my sig.

---

### Post by DuckHook on 2022-04-28
> **him610 said:**
> [QUOTE=ATSC;14092746]Excluded is niche/nerd/admin/highly specialized software, operating systems etc...That could cover a lot of examples.
Does your exclusion mean that 500 of the world's super computers running some form of open source software can not be an example?[/QUOTE]
Very insightful. A bit like asking: "Tell me why a Ferrari is a better car than a Chevy, but exclude stuff like torque, power, stability, handling and other car fanboy criteria."

---

### Post by DuckHook on 2022-04-28
Here are a few others:

[LIST=1]
[*]Nextcloud alone is infinitely superior to *all of Google in its entirety* by virtue of the single fact that it defends our data sovereignty by not tracking us.
[*]XMPP is superior to all of Facebook, Instagram, Whatsapp and Twitter combined, and for the same reason as above.
[*]Freetube is vastly superior to Youtube for… ditto.
[*]In the Android space, FDroid and Aurora (both FOSS) are superior to Google's Play Store for… ditto.
[*]TOR Browser is so superior to Chrome/Safari/Edge when it comes to privacy and data sovereignty that they don't even occupy the same mindspace.
[/LIST]
FOSS isn't superior because it has more bells and whistles. Framing the question only in terms of bells and whistles is an act of surrendering to the proprietary space by voluntarily lobotomizing what's best about FOSS.

FOSS is superior because it gives control of our lives back to us. This requires some effort on our part to reach out and grab it, but, unlike the proprietary opiates, at least it is on offer.

---

### Post by TheFu on 2022-04-28
DuckHook nailed it on the privacy.

I self-host lots of things that most people don't.  Nextcloud, Wallabag, email, PBX, DNS (with ad/content filtering), VPN.  Some of these run in KVM VMs and some run in LXD containers.  My security-oriented mind won't use pre-created docker images. I find that crazy.  Why would people want to allow a docker image created by some rando on the internet to run inside their LAN?  Sure, we have to trust some packages, but that trust should really be limited.  Here, we've decided to trust Canonical on some level. After all, we run their OS and get updates for it (which could do anything - literally ANYTHING) to our system(s), our LAN, and our data.  There's a line for who to trust that each person has to draw. For me, it is about who has screwed me over previously, the severity of that screwing, and my belief whether they are likely to do it again.

**LXD** is pretty great, but it has a few things that I dislike too (snap-only releases, zfs), but the barrier to using it is crazy low. Not as low as some other linux containers, but we can treat it almost like a virtual machine, which I treat the same as a physical machine.  Of course, LXD uses 1/10th the resources, perhaps even less, than a VM does.  All Linux containers do have limitations, mainly for things that absolutely must run as root and interface directly with hardware, but that's life. Most stuff doesn't actually need that.

I'd add that Linux is superior to other OSes due to **package management**. Updating the entire system, including all apps from thousands of different teams world-wide is 2 commands - or 1-click (I'm guessing) if you use a GUI.  The OS, applications, custom programs can all be updated with a single script, easily.  I have a script that updates ~20 systems weekly, **WHEN I DECIDE**, not when some vendor 2000KM away decides and forces the updates.  No more setup.exe and having to hunt down updates for each program - or each program having to create their own auto-update module just for their program.

Linux is superior in so many ways that matter to end users.  There is a learning curve.  But that same learning curve applies to kids raised on Linux, then forced to use that other OS in school.  [https://lifehacker.com/i-raised-my-kids-on-the-command-line-and-they-love-it-5974087](https://lifehacker.com/i-raised-my-kids-on-the-command-line-and-they-love-it-5974087)
> It has not escaped my attention that children that used Commodores or TRS-80s or DOS knew a lot more about how their computers worked, on average, than those of the same age that use Windows or MacOS.
Do it for the children.

---

### Post by ATSC on 2022-04-29
> **him610 said:**
> That could cover a lot of examples.
Does your exclusion mean that 500 of the world's super computers running some form of open source software can not be an example?

I don't know - I've never used a super computer in my life. Perhaps you can enlighten us - what programs do they run other than the ones that I've excluded above and below?

> **DuckHook said:**
> Very insightful. 

Thanks. :-)

> **DuckHook said:**
> 

Framing the question only in terms of bells and whistles is an act of surrendering to the proprietary space by voluntarily lobotomizing what's best about FOSS.

FOSS is superior because it gives control of our lives back to us. This requires some effort on our part to reach out and grab it, but, unlike the proprietary opiates, at least it is on offer.

Framing (or lecturing, rather) an answer to a question that no one has asked is more to your liking, no? :roll:


> **TheFu said:**
> DuckHook nailed it on the privacy....

> **DuckHook said:**
> A bit like asking: "Tell me why a Ferrari is a  better car than a Chevy, but exclude stuff like torque, power,  stability, handling and other car fanboy criteria."

errrr...., no? Most of you are missing the point - deliberately, it  seems. :roll: Not unsurprising but still sad. I didn't include these aspects  because I explicitly know very well hat these are its strengths -  otherwise I would not have asked, right?  Please stick to the question -  if you don't like a question (or the answer, or both),  well...don't reply. 

Just in case that I may have been unclear. "End-user software" means "application software": Programs that are being used by a user to work or to support a useful or desired **non-systemtechnical functionality**. Areas of application software include image editing, desktop publishing, games, groupware and software for educational technology etc. etc..... What I'm **not** interested in is system software or system utilities - programs that are needed to operate a system or device, including all programs related to software development. And yes, I know that it can be difficult to draw a line. And yes, I explicitly want to exclude the free/open source aspects.

Addendum: If you happen to understand german: [This]("https://www.heise.de/hintergrund/IT-Leiter-der-Stadt-Schwaebisch-Hall-Unter-Linux-leidet-die-Produktivitaet-6678160.html") is the background to my question

---

### Post by CharlesA on 2022-04-30
> **ATSC said:**
> errrr...., no? Most of you are missing the point - deliberately, it  seems. :roll: Not unsurprising but still sad. I didn't include these aspects  because I explicitly know very well hat these are its strengths -  otherwise I would not have asked, right?  Please stick to the question -  if you don't like a question (or the answer, or both),  well...don't reply. 

Just in case that I may have been unclear. "End-user software" means "application software": Programs that are being used by a user to work or to support a useful or desired **non-systemtechnical functionality**. Areas of application software include image editing, desktop publishing, games, groupware and software for educational technology etc. etc..... What I'm **not** interested in is system software or system utilities - programs that are needed to operate a system or device, including all programs related to software development. And yes, I know that it can be difficult to draw a line. And yes, I explicitly want to exclude the free/open source aspects.

Addendum: If you happen to understand german: [This]("https://www.heise.de/hintergrund/IT-Leiter-der-Stadt-Schwaebisch-Hall-Unter-Linux-leidet-die-Produktivitaet-6678160.html") is the background to my question

Does git count? I'm sure there are paid git clients out there (and servers too - GitLab and GitHuib).

---

### Post by QIII on 2022-04-30
@ATSC

Do not attempt to dictate to the community the manner/content of any response or who may and may not respond.  This is a chat sub-forum and you will get what you get.

Your demeanor in this thread has been reported to the Admins as undesirable.

---

### Post by exploder on 2022-04-30
LibreOffice to me is equal or superior to MS Office. About 5 years ago I had to write a paper for a class I was taking and in a format that I really knew nothing about. The school said I had to use MS Office. MS Office did not seem to detect what I was doing and crashed several times causing me to loose all my work.... I got fed up and started doing the paper in LibreOffice. LibreOffice automatically knew the format I needed and all I really had to do was to save it as a word doc. Needless to say, I used LibreOffice from then on to do all my work. 

Recently, I purchased a new, pretty high end desktop with all the RGB and bling. The PC came with Windows 10 but the builder did not activate Windows, which left it fairly crippled... I installed Ubuntu 22.04, everything worked out of the box, not only that but most of the apps I use came stock with it. Both OS's have their pros and cons but Ubuntu at the least is equal depending on the user's needs.

VLC certainly makes the grade here. Windows and Linux user's alike know it just plays everything! 

These days commercial software seems to have more and more advertising and subscriptions attached... I do use some free, proprietary software in Windows systems to test them before I sell them. I am not against people earning a living selling software but it's been many years since I spent any of my hard earned money on software.

---

### Post by grahammechanical on 2022-05-01
Here is the problem I have with replying to this question. I cannot compare apples with pears because I do not have any apples. The last version of a Microsoft OS that I used was Win98. I have no basis for making an appraisal. I am not in a position to compare Ubuntu with other Linux distributions because I only run Ubuntu.

There are some applications that work on both Windows and Linux but in the past the Linux versions were often several upgrades behind the Windows versions. Linux developers started later than Microsoft developers. For years Linux developers had to be content to replicate what was offered in the Microsoft universe. I am guessing that Linux developers are now moving beyond replicating what others offer and are now working towards their own ambitions.

Regards

---

### Post by DuckHook on 2022-05-04
> **grahammechanical said:**
> Here is the problem I have with replying to this question. I cannot compare apples with pears because I do not have any apples…
I find questions of these sorts problematic as well but for a different reason: we are asked to compare pears to apples, but prohibited from using the best qualities of pears.

Suppose we say that pears are superior to apples because they are more fragrant. The response will be to exclude fragrance. We then point out that pears have more interesting shapes. Response: can't discuss shapes either. Pears are more eco&#8209;friendly because they can grow with less water? Can't use that criteria because it's an extraneous consideration. Pears will continue ripening after they are picked whereas Apples won't? Can't discuss ripening because it's a biological process. Pears have more varieties of texture? Nope. Texture is off limits.

Ultimately, it turns out that the only acceptable criteria are apple properties. Pear properties don't count. The only pear that meets the criteria is one that looks and tastes like an apple. It's a rigged game that is impossible to win.

@exploder raises the MSOffice vs LibreOffice comparison. Let's run with that as an illustration of the skew that's at work here. MSOffice generates 4 CVEs to every 1 from LibreOffice. And this discrepancy is even more pronounced when it comes to severe CVEs. MSOffice was initially designed with innumerable gaping security holes and MS now fights a rearguard action trying to backfill those holes. In terms of security, the superiority of LO over MSO is no contest.

But LibreOffice cannot open every MSOffice document, especially those with macros and heavy MS customizations. If we are asked to compare LibreOffice to MSOffice, but can't point to LO's superiority in privacy or security or reliability or speed or coding efficiency, then how can we make a fair or even intelligible comparison? Judging LO by MS's rules means that we forfeit the game before it even starts. Yet I would choose LO over MSO anytime for its far superior security alone.

But security is yet another "system" property, presumably off limits as a comparison criteria. So, what proprietary apps are we supposed to compare? That malware&#8209;infested recipe app? The crypto&#8209;miner masquerading as a cute cat app? That phishing program disguised as a banking app? Or that TripAdvisor app that, at last count, contained 16 trackers? Or MSOffice with its horrific security history? Adobe Flash anyone? The security joke called MS .NET? Modern AV apps that are now aspiring to be cryptomining bot nodes? I subscribe to a number of security blogs and RSS feeds. By my rough estimate, VMWare suffers roughly one critical exploit, some of them zero day, every three months. I can't remember the last time KVM or Xen were compromised.

Security ought to be the most important consideration in any modern app. But the proprietary vendors have conditioned their followers to think of security as some vague property that can be ignored so long as they run some magic antibiotic on their system. This denigration of what's truly important is a ploy to get them off the hook and allow them to continue focusing on the only thing that they are any good at: bells and whistles.

I have no answer to the OP's question not because Linux has no superior apps but because the question, by its very nature, cannot be answered. Sort of an "are your still beating your spouse" type question—it assumes the very premise that is at issue.

---

### Post by zebra2 on 2022-05-05
There is quite a bit of proprietary software available that has both private and foss code included. Some of this software is very good and I don't mind paying to use it.  I think this thread goes to the immediate technical paradigm one enters upon trying to use linux and the struggle to replace MS based apps with appropriate FOSS based apps or even MS/FOSS proprietary apps that are available.  I have been using the Ubuntu default install since Karmic Koala and know this challenge very well.  So far I have been successful in finding appropriate both FOSS and proprietary solutions.  I just retired from a multi billion dollar company and used a Windows based computer every day. I have considerable college level training with spreadsheet. I kept my spreadsheets in compatibility mode and they always worked properly on my Linux system with Libre Office.  The problem for me was that Excel could not negotiate spreadsheets of the size necessary to accommodate my needs.   I would usually terminate with out of memory errors even though I had sixteen gig of ram, Even the company IT's said what I wanted to do wasn't possible and they wouldn't spend time on the problem. So we always settled for less than I believed was possible. It is entirely possible that the OP here has a limited knowledge of the capability of appications in a large application setting. Everything has limits and everything has bugs. 
The real question is how much frustration can the user of either paradigm tolerate. Life is difficult and leaving one's comfort-ability can be frustrating. My experience with Linux is that where Ubuntu has taken it is very desirable and functional and useful for all of my computing needs. It did take me a couple of years to get to the 100% linux experience.  I can identify with what I perceive to be the OP's frustration. I can only say that Ubuntu 22.04 can be a really great place for a new user to hard land.

---

### Post by TheFu on 2022-05-05
> MS/FOSS proprietary apps
Uh...  these don't exist.  Every license has to be reviewed and understood.  MS doesn't give code away for anything that is non-trivial, unless forced to do so - like for changes to KVM to make Windows-whatever run better in a VM ... or for kernel changes to make WSL or Linux work better under their hypervisor.  These are all self-serving, which makes perfect sense.

MSFT cannot under 40 yrs of damages to the F/LOSS world in 3 yrs of playing nice.  A leopard cannot change spots. I always assume the worst if there's MSFT involved and they need to prove their good intentions.  Whereas for F/LOSS companies, I assume good intentions, and it is my job to prove when they've lost trust.  Canonical has done that a few times.  It is hard to be 100% altruistic as a company. Very hard.

Look at what happened to the OpenOffice screw-ups by Oracle.

As for Excel abuse, that is very common.  It applied to LibreOffice-Calc abuse too.  Use the right tool for the right job.

I suspect what people think is 100% Linux, is really more like 20% Linux, especially if they avoid using the CLI and automation that is built-in to all Unix-like systems.  Trust me. _**If you only use the GUI, you are missing at least 80% of the power**_ that your humble Ubuntu can provide.

---

### Post by zebra2 on 2022-05-05
Actually I have better things to do with my life than concern myself with 100% of the power of linux.  If I only use a computer to send and receive my email and open a browser to log into my bank account and I do all of that in Ubuntu and not Windows OS then I am 100% Linux. In other words not using a Windows partition for part of my needs.due to lack of Linux software. As it is, I use Ubuntu OS for everything I do and have Linux compatible software that I am very satisfied to use in that endeavor.  That doesn't exclude the fact that I absolutely do use the command line for a great deal of what I need to accomplish outside of those software.  It also doesn't preclude the fact that some of that Linux compatible software is also ported to Windows. Much of the software available is ported to both Windows and Linux but I only access it via Ubuntu. The reason I only use Ubuntu is because of the 100% power and security of Linux.  On that point I agree 100%.

---

### Post by TheFu on 2022-05-05
> **zebra2 said:**
> Actually I have better things to do with my life than concern myself with 100% of the power of linux.  

Agreed.  I have better things to do as well.  

Everyone is different. If 10% works for a user, great.  Same for 20%, 40%, 60% ... if your $dayjob is Unix admin or programming, then perhaps higher efficiency makes sense?  These forums have all sorts of people helping others.

---

### Post by Tadaen_Sylvermane on 2022-05-16
Back to topic. I think backups are one way. With a pair of scripts I can do backups of my machine with no trouble and it is entirely automated. With any commercial backup software you are confined to the options they give you in the gui. If you want to go over ssh the app must support it else to bad so sad. With a full foss method you can customize and make it yours instead of trying to mold someone elses idea to fit yours. Case in point -

[https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/rdiffbackups](https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/rdiffbackups)

I've got both versioned (or whatever rdiff-backup is) and a straight rsync of other directories depending on content in one 78 line script. This sits in my cron.hourly and I don't think about it. I can't imagine any commercial gui that could do this easily that would be so small in total footprint.

---

