---
title: "UBUNTU has shot itself in the foot"
date: 2010-02-07
forum: Testimonials &amp; Experiences
---

### Post by Al Fischer on 2010-02-07
The decision to move to GRUB2 may be the final blow for UBUNTU. Looking forward to all the imrovements that come with a new release just got washed down the drain when I spent about a week trying to get it working with Win7 and XP. There seems to be little hope for a reasonable solution and I see many others with problems. Interestingly enough it is UBUNTU I can't make boot dependably. Windows and DOS work fine. I had a fine boot strategy using Grub4dos and Grub2 apparently won't work with it. The tutorials are laden with cautions and warnings about it being a 'beta' and i looks like calling it a 'beta' is mild.

I am thoroughly disappointed and disgusted with the direction that has been taken.

---

### Post by eddier on 2010-02-07
I have it installed on 2 Laptops and my main PC with win.7,no problems!

Check your own foot for bleeding!\\:D/

eddie

---

### Post by SigmaSanti on 2010-02-07
Some information as to the technical details to your problem would be more useful than your opinion, this is a help section.
Many people have had no problem with it (i am one of them), so if you would like help please tell us where your difficulty is: boot-up?, random error messages?, a neodymium magnet?

---

### Post by Post Monkeh on 2010-02-07
the only issue i have with grub 2 is that i can't password protect my entries to stop the recovery mode being available.

other than that it's worked fine on my laptop and my desktop

---

### Post by rumbo on 2010-02-07
Works for me booting Ubuntu 9.10 and Windows 7 Ultimate with default settings, both on the same drive.  Ubuntu set it up automagically.   I didn't even know it was GRUB2 until I just read your post.

---

### Post by phredbull on 2010-02-07
Actually, Grub2 seems to be causing plenty of problems for Wubi installs. It screwed mine up, so I just decided to partition my drive and do a full install. Now Grub2 is fine for me.

But I do agree that it seems silly to include such a flimsy piece of code that's responsible for an essential component of an OS.
:confused:

---

### Post by thecliff on 2010-02-07
I am dual booting on a notebook with Windows 7 with no issues at all.

---

### Post by michy99 on 2010-02-07
> **phredbull said:**
> Actually, Grub2 seems to be causing plenty of problems for Wubi installs. It screwed mine up, so I just decided to partition my drive and do a full install. Now Grub2 is fine for me.

But I do agree that it seems silly to include such a flimsy piece of code that's responsible for an essential component of an OS.
:confused:

I don't think a Wubi install even uses Grub.

---

### Post by Morbius1 on 2010-02-07
I agree that if they want to call Grub 1.97 Beta, Grub2, it's fine with me. Although I'd feel better if the got rid of the "beta" suffix. 

There are alternatives to grub4dos that work with grub2 you know . I've been using a third party boot manger for many many years now and it works fine with grub2 ( so far :-\" ).

---

### Post by overdrank on 2010-02-07
Moved to Ubuntu Testimonials & Experiences

---

### Post by Sylslay on 2010-02-07
LOL Lads 

"Check your own foot for bleeding!":D

---

### Post by Al Fischer on 2010-02-07
My attempt to move to 9.1 has been a total mistake. The UBUNTU part was fine. Created a load on a single HD to try it. Looked good. Clone my multiboot image and placed 9.1 in the partition originally ocupied by 8.1. Results : Dos, Xp and Win7 boot fine. 9.1 fails. Also Memcheck fails to load. Booting by UUID which checks good. Posted a problem with a question a week ago- not a single answer. Pulled Info on GRUB2 from Ubuntu, the Grub team, and atutorial by Dedoimedo. Studied and my conclusion is use at your own risk. Expect upgrades to cause problems. Only Ubuntu has apparently bought into Grub2 and others continue the 'old' way. Removing Grub2 looks like deleting about 40 files. 

Yes, there is blood on my foot too. It's from the bullit in my back from  the overspray of what seems to be 'friendly fire'. I am not pleased with this  situation as you can see. Multibooting needs to be done in an understandable, and controllable way. Not 'run this procedure and see what happens'.

---

### Post by 1roxtar on 2010-02-08
> **Al Fischer said:**
> The decision to move to GRUB2 may be the final blow for UBUNTU. Looking forward to all the imrovements that come with a new release just got washed down the drain when I spent about a week trying to get it working with Win7 and XP. There seems to be little hope for a reasonable solution and I see many others with problems. Interestingly enough it is UBUNTU I can't make boot dependably. Windows and DOS work fine. I had a fine boot strategy using Grub4dos and Grub2 apparently won't work with it. The tutorials are laden with cautions and warnings about it being a 'beta' and i looks like calling it a 'beta' is mild.

I am thoroughly disappointed and disgusted with the direction that has been taken.

How ironic that the "final blow" came because YOU had trouble with GRUB2.  I've made many dual-boot installs on computers with far ranges in specs, from old computers to brand-new ones.  I have yet to encounter any problems with Ubuntu OR Grub2.  Unless you bought out Canonical, Ubuntu will still be around and popular for a long time.

---

### Post by running_rabbit07 on 2010-02-08
Probably caused by a bad ISO image. Run check disk selection in the LiveCD's boot list.

---

### Post by running_rabbit07 on 2010-02-08
> **michy99 said:**
> I don't think a Wubi install even uses Grub.

I don't think they did either, because you can delete Wubi and uninstall it without booting problems.

---

### Post by Al Fischer on 2010-02-08
Obviously, I am not planning on buying out Canoniacle!

However, he direction since I have been playing with Ubuntu has been progress towards a more user installable, more  powerful and easier to useexperience and more likely to be possible to use by the masses. Yes, I  am sure it is possile to istall a multiboot system withe the delivered distro. That is why there are so many questions about what to deo when it doesn't work. AN READ the tutorials and documentation and Then tell me you would feel comfortable installing it on YOUR system that containe your whole digital life and you did'nt have the ability to first clone it. I cloned mine before starting. After a week I am giving up. 

Please look at the documentation and then tell me what you think.

---

### Post by phredbull on 2010-02-08
> **running_rabbit07 said:**
> I don't think they did either, because you can delete Wubi and uninstall it without booting problems.

Maybe it's not supposed to use Grub, but after an update, I saw Grub1.97 beta for the first time, (with a grub:sh> prompt) and wasn't able to boot in anymore. Do a search for Wubi and Grub and you'll see that others have had this problem.

---

### Post by anaconda on 2010-02-08
I have similar problems with grub2.. 
And I only have ubuntu on my computer. Sometimes (maybe 1 out of 3 times) it wont boot It just hangs.

But I plan to install the old version of grub to correct this problem. Never had problems with it.

The thing is that old grub doesnt support ext4 ?? if I remember correctly? 

(luckily I use jfs !)

---

### Post by 3rdalbum on 2010-02-08
I agree with the OP, Ubuntu should never move forward and never support new filesystems and other new technologies.

---

### Post by Al Fischer on 2010-02-08
Please, don't misunderstand my concerns. Ubuntu should move forward but is being dependant on a boot loader that the developers call 'beta' and issue many warnings about using it moving forward or is it jumping off a cliff?

From what I see I am not the only user wanting to multiboot and having problems. Neither am I the only user that is not a Linux expert, just a learner willing to try. I would like to be able to use thia latest 'improvement' known as Karmic or  9.1 but Ubuntu has made it almost impossible. 

Yes, I have been using grub4dos, which probably puts me in the minority, but should boot  fine. 

If any of you have a reasonable solution other that removing a long list of grub2 files manually I am willing to listen and learn. 

I stand by my original opinion that Ubuntu has shot itself in the foot.

---

### Post by NFblaze on 2010-02-08
I really do think Grub2 sucks. I only have a problem with it on my laptop, where it screws up booting into Windows. I dont know why they decided to include it, if it's still Beta. They should give an option if I want to use Legacy or Beta until it's up to standards. Then again, by I suppose to really work out all the bugs the more users you have the better.

---

### Post by Post Monkeh on 2010-02-08
> **anaconda said:**
> I have similar problems with grub2.. 
And I only have ubuntu on my computer. Sometimes (maybe 1 out of 3 times) it wont boot It just hangs.

But I plan to install the old version of grub to correct this problem. Never had problems with it.

The thing is that old grub doesnt support ext4 ?? if I remember correctly? 

(luckily I use jfs !)
I'm fairly sure i started using ext4 when i installed 9.04 and grub booted my laptop ok. Plus you can use ext4 on various other distros that still use grub. I wouldn't go so far as to say ubuntu has shot itself in the foot, but i do think they should have stuck with grub as default until at the very least grub 2 can offer the same functionality as grub.

---

### Post by Al Fischer on 2010-02-08
The LEAST they should have done is WARN us before bothering to attempt using this mess. Moving forward with something that is troublesome is not generally a good plan.

Kind of reminds me of Vista....

---

### Post by Al Fischer on 2010-02-08
What is jfs? another multiboot solution?

---

### Post by Juan Largo on 2010-02-08
I agree with the OP.  Although only GRUB2 supports EXT4, it is not yet ready for prime time, and it's a great example of a solution in search of a problem.  I'm glad that GRUB2 works most of the time (yay).  But even a high success rate isn't much good when you can't fix it when it fails.  Unfortunately, that seems to be the case with GRUB2.  

Installing GRUB2 is like rolling dice:  Most of the time it works, which is great.  But once in a while you roll snake eyes and you're screwed.  And even if you're lucky enough to get it working the first time, some future software upgrade may hammer it later.  

With classic GRUB you can almost always fix any problem by editing menu.lst from a Live CD.  To change the configuration file with GRUB2, you have to run a script.  Huh?  Please explain exactly how to run a script when GRUB2 can't find the root partition and the computer won't boot.  Being asked to run scripts on a computer that won't boot is completely brain dead, and reminds me of the stupid BIOS message:  "Keyboard error or no keyboard present.  Press F1 to continue or DEL to enter Setup."  DUH!

I don't object if Ubuntu wants to experiment a little.  But please don't put alpha and beta software into a production environment with no options for installing stable versions.

---

### Post by HappyFeet on 2010-02-08
I have a simple solution: Don't like it? Don't use it. But ranting in this section accomplishes nothing. Ubuntu isn't going to change because of this thread.

---

### Post by chewearn on 2010-02-08
> **Juan Largo said:**
> I don't object if Ubuntu wants to experiment a little.  But please don't put alpha and beta software into a production environment with no options for installing stable versions.

^ Sorry, I have to call out this misleading statement.

1. Who exactly is the person who put alpha and beta software into a production environment?  Think about it.  (hint: who is in charge of the computer?)

2. Is there really "no options for installing stable versions"?  This is Linux.  There is always option.

---

### Post by Morbius1 on 2010-02-08
> 1. Who exactly is the person who put alpha and beta software into a production environment? Think about it. (hint: who is in charge of the computer?)The only problem with that statement is the user (especially if new to Ubuntu ) doesn't know that there's a difference in the different releases so he doesn't know that some releases are more stable by design than others.

It's been my experience that LTS and LTS+2 are more stable than the others. So 8.04, 9.04, and I'm guessing 10.04 are more stable than 8.10 and 9.10 releases. 9.10 should have been released with a suffix - TP - Technology Preview. That would let the user know what he's getting himself into.

---

### Post by Juan Largo on 2010-02-08
> **HappyFeet said:**
> I have a simple solution: Don't like it? Don't use it. But ranting in this section accomplishes nothing. Ubuntu isn't going to change because of this thread.
The name of this section of the forum is entitled "Ubuntu Testimonials & Experiences," not "The Fanboy Cheering Section."  

"Experiences" can be both good and bad.  The OP had a bad experience and posted about it.  It was entirely appropriate to do that here.  And I realize Ubuntu won't change because its users are having problems.  Ubuntu will never change because it's "perfect."

[QUOTE=chewearn]
1. Who exactly is the person who put alpha and beta software into a production environment? Think about it. (hint: who is in charge of the computer?)

2. Is there really "no options for installing stable versions"? This is Linux. There is always option. 
[/quote]
1.  Are you saying that 9.10 shouldn't be used in a production environment?  Where was the warning about not doing that?  The users didn't decide to include GRUB2 by default -- Unbuntu's developers did.

2.  I realize there are plenty of choices and other Linux distros out there that are better than Ubuntu.  Nobody is complaining about that. They're complaining about Ubuntu making bad choices.

---

### Post by gjoellee on 2010-02-08
> **eddier said:**
> I have it installed on 2 Laptops and my main PC with win.7,no problems!

Check your own foot for bleeding!\\:D/

eddie

Indeed...! I have no issues...did not have any with grub legacy either though...

---

### Post by chewearn on 2010-02-08
> **Juan Largo said:**
> 1.  Are you saying that 9.10 shouldn't be used in a production environment?  Where was the warning about not doing that?  The users didn't decide to include GRUB2 by default -- Unbuntu's developers did.

Please read precisely what I said, and not what could be perceived or implied.  I am not saying anything about Ubuntu 9.10 and production environment.  My opinion in this matter shall remain un-voiced in this thread.

> 2.  I realize there are plenty of choices and other Linux distros out there that are better than Ubuntu.  Nobody is complaining about that. They're complaining about Ubuntu making bad choices.

I re-quote your previous statement:[I]
"I don't object if Ubuntu wants to experiment a little. But please don't put alpha and beta software into a production environment with no options for installing stable versions."[/I]

In my reply, I am pointing out that owner of computer should take full responsibility what they put into their computer.  Ubuntu's developers are not responsible nor capable of forcing what get installed into the users computer.

In your reply, you brought up a different point: "users are complaining about Ubuntu making bad choices."

Okay, I have no problem with your new statement.  You or users are free to complain about this, in my opinion.

But take note: this is an entirely new statement compared to previous one you raised.  What I was debating about was your previous statement.

---

### Post by Al Fischer on 2010-02-09
Very interesting conversations here. Basically it appears to me that I probably should not have posted any type of concern with Ubuntu so as not to upset the fan-boys of the world. My apologies to anyone I may have offended.

Yes, we are responsible for what we put on our computers, but when we install what is expected to be an improvement and it proves otherwise, some dissatisfaction should be expressed. I just re-read the 'release notes' and did not understand from the notes what would be the result of installing. Yes, this release works well under certain circumstances, however, multiboot as we have done in the past is now a whole different story. More like an ongoing story with the next broadcast coming tomorrow. Probably with a surprise ending.

May I suggest that those who are so strongly supporting this mess called GRUB2 download and read the documents available and then put yourself in the shoes of one who does not have years of Linux experience. In my case I have experience with CPM, DOS, Assembler, Windows, AS400, some  SAS and a little IBM360/370
I hope someday to be able to say I have some Linux skills,too.

In the meantime there have been about 30 replies to this thread started out of frustration but not one reply to the request for help with the issue. Ahhh, the Spirit of Ubuntu...

---

### Post by Tamlynmac on 2010-02-09
> Al Fischer
In the meantime there have been about 30 replies to this thread started out of frustration but not one reply to the request for help with the issue.

Perhaps, it due to the fact that (as specified in the T&E header) this section of the forum is not a support section. For those individuals in need of assistance the "Help Sections" of this forum are available and IMHO the best on the net.

This section of the forum as defined by it's very name, is a section for individuals to share their experiences. Might I suggest a visit to the help sections - to all those in need of assistance. I believe you will find all the Ubuntu help spirit your looking for there.

---

### Post by chewearn on 2010-02-09
Preamble: my reply below reflects my "philosophy" in Ubuntuforums.  Maybe other members agree with me, maybe they don't.  I tried my best to adhere to these principles.

> **Al Fischer said:**
> Very interesting conversations here. Basically it appears to me that I probably should not have posted any type of concern with Ubuntu so as not to upset the fan-boys of the world. My apologies to anyone I may have offended.

I'm not against complaints, or concern addresses in the appropriate section.  [Ubuntu Testimonials & Experiences]("http://ubuntuforums.org/forumdisplay.php?f=103") is certainly the right place to rant about your frustrations.

However, I am against using derogatory words such as "fanboys".  You may debate views, but resorting to name calling is not cool.

Certainly, I cringed at the tone adopted by some people in this forum.  It's my impression that the atmosphere has been less friendly since I logged back in this forum from more than a year ago.

> Yes, we are responsible for what we put on our computers, but when we install what is expected to be an improvement and it proves otherwise, some dissatisfaction should be expressed. I just re-read the 'release notes' and did not understand from the notes what would be the result of installing. Yes, this release works well under certain circumstances, however, multiboot as we have done in the past is now a whole different story. More like an ongoing story with the next broadcast coming tomorrow. Probably with a surprise ending.

Now, this is a robust argument against what I said about users being responsible.  Here, we have a good debate, and maybe your strong argument might soften mine.

I see "my job" in this section (if I even bordered), is to debate what I think is misconception or misunderstanding.  Doesn't mean I am right.  I am still learning, just like everyone else.


> May I suggest that those who are so strongly supporting this mess called GRUB2 download and read the documents available and then put yourself in the shoes of one who does not have years of Linux experience. In my case I have experience with CPM, DOS, Assembler, Windows, AS400, some  SAS and a little IBM360/370
I hope someday to be able to say I have some Linux skills,too.

Actually, I have no experience with Grub2.  I have resisted upgrading to newer version than 8.10, for one simple reason.  8.10 works for me, and no need to mess with what works.

Incidentally, this tied in with my view that I am responsible to what get installed in my PC.  See how it works?

> In the meantime there have been about 30 replies to this thread started out of frustration but not one reply to the request for help with the issue. Ahhh, the Spirit of Ubuntu...

This, I disagree for two reasons:
1. this part of the forum is not for support request, but meant as a testimonial.  You have not actually posted a thread in "General Help" for it.

2. Long time ago, a wise member of this forum suggest that people refrained from providing support answers to thread in this section (i.e.  [Ubuntu Testimonials & Experiences]("http://ubuntuforums.org/forumdisplay.php?f=103")).  I agreed with his reasoning.

Basically, it's that supporting thread in this section could lead to a vicious cycle.  We jumps in to help whenever someone rants.  Therefore, when people failed to get satisfactory help/solution, their next move would be ranting.  Meanwhile we get flamewars started from all that rantings.  In the long run, this is unhealty in a support forum that Ubuntuforums supposed to be.

---

### Post by Al Fischer on 2010-02-09
1. I originally posted this in the 'GENERAL HELP' section. Actually, I was unaware of this section. The thread was moved here by the moderator, I assume. Now I am aware of this section.

2. Earlier, I posted a question about using GRUB4DOS that was the beginning of my adventure. After a week 95 views, no replies.

3. I do understand completely that THIS section is not for soliciting assistance. It is for discussion of experience (Good or Bad, I would hope) My experience, as stated has been les than satisfactory. I have given the reasons. It appears there are others experiencing similar problems. AND there are those who have used GRUB2 with no problems. It looks like a simple dual boot with Windows may go fine. However when (NOT IF) a failure occurs, it will prove almost impossible to correct.

4. I used the term 'Fanboys' not as a derogerative but rather a descriptive. Not calling anyone names. It is a commonly used phrase and IMO very accurate.

5. I really hope that when YOUR working multiboot fails due to an update of something that you are successful in fixing the faulty GRUB2 code. Remember the caveats expressed in the GRUB2 documents warned you.

---

### Post by Tamlynmac on 2010-02-09
> Al Fischer

Fanboy much like the term troll, is a definitive name often used IMHO to alienate the opinions of others that differ from one's own. It's been my experience the term fanboy is often used in a derogatory manner to define individuals that enthusiastically supported a product. Simply because a product may not work for one, does not equate to the fact that it doesn't work for others.

Often, it comes down to the learning curve and one's desire to participate in said curve. IMHO, the profiling or labeling of others to serve one's own interest, reveals volumes about the writer and should be discouraged.

The actions taken by the staff to move your post, should not be misinterpreted as the reason for not receiving support in this section. When posting in this section, members who have read the T&E header know the T&E is not a support section of the forum and in [this]("http://ubuntuforums.org/showthread.php?t=1343965") sticky - it's reaffirmed. Thus, I believe that accusation is unfounded and lacks substance.

Good Luck
* I will not debate in this section of the forum. Or, respond to any arguments in this thread and will unsubscribe.

---

### Post by aysiu on 2010-02-09
> **running_rabbit07 said:**
> I don't think they did either, because you can delete Wubi and uninstall it without booting problems. Wubi uses Grub. It just doesn't install Grub to the MBR. Windows boot loader is still on the Master Boot Record. Grub is just for managing the virtual Ubuntu partition. It doesn't manage the dual-boot between Windows and Ubuntu.

---

### Post by GodLikeCreature on 2010-02-09
> **Al Fischer said:**
> The decision to move to GRUB2 may be the final blow for UBUNTU. Looking forward to all the imrovements that come with a new release just got washed down the drain when I spent about a week trying to get it working with Win7 and XP. There seems to be little hope for a reasonable solution and I see many others with problems. Interestingly enough it is UBUNTU I can't make boot dependably. Windows and DOS work fine. I had a fine boot strategy using Grub4dos and Grub2 apparently won't work with it. The tutorials are laden with cautions and warnings about it being a 'beta' and i looks like calling it a 'beta' is mild.

I am thoroughly disappointed and disgusted with the direction that has been taken.

Hmmm...  It is a bit unreasonable to have such level of expectation when your setup is far from standard.  

Windows and Mac do charge you for their OS, and would also charge for support, yet I am sure they would not support you if you were trying to do something as out of the standard as what you are trying to do with Ubuntu.  

Even if it was a simple dual boot setup, do you really think you could phone MS support and express your frustration because Win7 does not allow you to dual boot, when WinXP did? (just a random example)  

In fact, I never had issues when trying to run Wubi installations under WinXP, but I have never been able to make it happen under Vista.  I am sure you understand I never phoned Microsoft, or went to a Windows forum and expressed my frustration.  I just assume they don't build their OS thinking of an Ubuntu Wubi installation.  Neither does Apple, and honestly, neither should Ubuntu.

I would understand your frustration if GRUB2 wouldn't work on a standard (clean) installation.  Your expectations are way beyond what's reasonable, IMHO.

---

### Post by running_rabbit07 on 2010-02-09
> **Al Fischer said:**
> In the meantime there have been about 30 replies to this thread started out of frustration but not one reply to the request for help with the issue. Ahhh, the Spirit of Ubuntu...

Probably because the fix is so easy that people felt that if you can't RTFM or do a simple Google for "ubuntu grub install," then, they shouldn't use the energy to re-explain that which was already at your finger tips.

If you take the time to do the Google, there is a thread that tells you how to use the LiveCD to add every needed entry for grub. Maybe there is a problem with the file used by grub for the memtest. 

[COLOR="Sienna"]I am not a grub pro and you didn't bump your help thread any. Have you noticed how quickly they move from page to page? Try bumping it so that one of those people who know a lot about grub can help you diagnose the problem. There are people who read those threads and not these threads and it is their attention you need to get, not the ones you find in this sub-forum.[/COLOR]

---

### Post by wsonar on 2010-02-09
Hap my trip boot before upgrade after upgrade no prob.

my only complaint is that my grub theme is gone :(

---

### Post by ASHIE on 2010-02-09
I hav any problems with grub, yet. My experience with dual booting is that it's a pain in d but, cos i dont like rebooting to switch between OS's. I overcome it by ditching windows. ever since, life's been a breeze. i've reloaded windows recently, for one program (work related), but dont need it actually. I find virtual desktops, I use VirtualBox, a better solution cos u can use both desktops. what's the point in having to reboot if u need 2 use sumfin dat's specific 2 dat OS anyway.

---

### Post by darrenn on 2010-02-10
> My attempt to move to 9.1 has been a total mistake. The UBUNTU part was fine. Created a load on a single HD to try it. Looked good. Clone my multiboot image and placed 9.1 in the partition originally ocupied by 8.1. Results : Dos, Xp and Win7 boot fine. 9.1 fails. Also Memcheck fails to load. Booting by UUID which checks good. Posted a problem with a question a week ago- not a single answer. Pulled Info on GRUB2 from Ubuntu, the Grub team, and atutorial by Dedoimedo. Studied and my conclusion is use at your own risk. Expect upgrades to cause problems. Only Ubuntu has apparently bought into Grub2 and others continue the 'old' way. Removing Grub2 looks like deleting about 40 files.

Yes I agree with ASHIE I don't understand why you can't simplify your setup by running winxp and dos in a virtualbox. The whole reason for virtualbox is for setups like yours... I guess im missing something here. Doesn't win7 come with some sort of virtualbox xp built in?

---

### Post by running_rabbit07 on 2010-02-10
I doubt the OP wants to run them in VBox. If it is alright to dual boot, what is wrong with quad booting? He just needs to get grub tweaked.

---

### Post by Al Fischer on 2010-02-10
When I first tried Ubuntu I liked what I saw but felt I needed to use Windows for some things. I looked at what was available for multibooting and it looked like the GRUB4DOS method was about as simple and straight forward as anything else. Besides I could understand what it was doing and when I screwed up I could straighten it out. At the time I was totally unfamiliar with Linux and trying to learn the real basics. I had to start somewhere and this approach has worked fine. (until the 9.1 adventure)

The Virtual Box approach may be a very good way to run multiple systems but with my level of expertise it is probably not a good way to go.

I keep each O/S in it's own primary partition and hide or unhide them easily. I am not comfortable with any version of Windows playing well with any version of any other O/S. I think it is important to keep Windows locked up in it's own little place and kept on a leash!

Win 7 does come with a virtual thing, but I think it is only for using XP applications. There are times when good old DOS saves the day. and the DOS BOX in Windows is not the same.

I will probably continue my effort to use 9.1 in spite of the GRUB2 thing.

I am somewhat disappointed with some of the responses on this thread.  Some of them were offensive and insulting to me. Thats where my inappropriate use of the Fanboy label came from. Yes, I checked my own foot. It was bleeding. The bullet was from having tried a newer version of Ubuntu. Yes, I do Google for information so kindly refrain from trying to make others look totally incompetent. I am a LEARNER not an expert like some of you think you are.

What none of us know is how many others have heard great things about Ubuntu, downloaded it, installed it, and ended up with a non-functioning system. Some of those folks were willing to ask for help on the forum. Some of them got the help, some didn't or maybe couldn't ask. They simply went away in disgust thoroughly convinced that Ubuntu only destroys computers. 

I am still of the opinion that Ubuntu has shot itself in the foot by changeing to a highly complicated boot mechanism. Yes, in some circumstances it works but when it doesn't you got big problems.

---

### Post by m4tic on 2010-02-11
what's so difficult about ```
sudo update-grub2
```

---

### Post by Al Fischer on 2010-02-11
Nothing is difficult, if you understand it.
I am definitely not well versed in Linux. When I tried Ubuntu about a tear ago I struggled through the initial instal and actually got it working with some great help from this forum. Things like what is VI? My background is CPM (remember that?) DOS
Windows 3.1, 95, 98, 2000, XP, and now 7, but my foray into Linux is VERY recent. However, with a lot of fine quality help from here I am actually learning! I think it's the very basics I need to grasp.

I am not comfortable with the terminal yet and just issueing a command like update-something makes me cringe.

My approach to the GRUB2 thing was to go for the documentation and tutorials that were available. I read them and ended up VERY confused. (steep learning curve)  The authors are definitely NOT making GRUB2 sound useable. So for me, I am going to stick with something I understand and can manage to manipulate with some confidence.

As I manage to build some skills with Linux I will probably be more open to issueing commands. I spent about a week studying and trying before I posted what may have been an inappropriate statement. Total frustration.

I doubt I am the only inexperienced user in the world, and many would merely go away thinking this Ubuntu/Linux thing is garbage.
I at least admit it is my level of understanding and am DETERMINED to learn! Eventually GRUB2 will work as it should and will be adopted by everyone. I do not feel comfortable enough to help debug it.

---

### Post by running_rabbit07 on 2010-02-11
> **Al Fischer said:**
> When I first tried Ubuntu I liked what I saw but felt I needed to use Windows for some things. I looked at what was available for multibooting and it looked like the GRUB4DOS method was about as simple and straight forward as anything else. Besides I could understand what it was doing and when I screwed up I could straighten it out. At the time I was totally unfamiliar with Linux and trying to learn the real basics. I had to start somewhere and this approach has worked fine. (until the 9.1**0** adventure)

The Virtual Box approach may be a very good way to run multiple systems but with my level of expertise it is probably not a good way to go.

I keep each O/S in it's own primary partition and hide or unhide them easily. I am not comfortable with any version of Windows playing well with any version of any other O/S. I think it is important to keep Windows locked up in it's own little place and kept on a leash!

Win 7 does come with a virtual thing, but I think it is only for using XP applications. There are times when good old DOS saves the day. and the DOS BOX in Windows is not the same.

I will probably continue my effort to use 9.1**0** in spite of the GRUB2 thing.

I am somewhat disappointed with some of the responses on this thread.  Some of them were offensive and insulting to me. Thats where my inappropriate use of the Fanboy label came from. Yes, I checked my own foot. It was bleeding. The bullet was from having tried a newer version of Ubuntu. Yes, I do Google for information so kindly refrain from trying to make others look totally incompetent. I am a LEARNER not an expert like some of you think you are.

What none of us know is how many others have heard great things about Ubuntu, downloaded it, installed it, and ended up with a non-functioning system. Some of those folks were willing to ask for help on the forum. Some of them got the help, some didn't or maybe couldn't ask. They simply went away in disgust thoroughly convinced that Ubuntu only destroys computers. 

I am still of the opinion that Ubuntu has shot itself in the foot by changeing to a highly complicated boot mechanism. Yes, in some circumstances it works but when it doesn't you got big problems.

Being you copied the files from one system to another it is always possible that something doesn't match up on the new system. Probably something as simple as the UUID. 

The first fix I did for ya was easy though. Ubuntu Karmic was made in October(10) not January(1).

---

### Post by running_rabbit07 on 2010-02-11
> **m4tic said:**
> what's so difficult about ```
sudo update-grub2
```

This one commend works magic with grub2. It added and removed a few OSes as I tried them beside Ubuntu and Windows 7. Most recent addition is Back|Track 4.

---

### Post by Al Fischer on 2010-02-11
OK. I will try it. But I have been told to finish painting the living room first. GRRR...  Gotta live with this woman!

---

### Post by tdawgf on 2010-02-14
> **Al Fischer said:**
> When I first tried Ubuntu I liked what I saw but felt I needed to use Windows for some things. I looked at what was available for multibooting and it looked like the GRUB4DOS method was about as simple and straight forward as anything else. Besides I could understand what it was doing and when I screwed up I could straighten it out. At the time I was totally unfamiliar with Linux and trying to learn the real basics. I had to start somewhere and this approach has worked fine. (until the 9.1 adventure)

The Virtual Box approach may be a very good way to run multiple systems but with my level of expertise it is probably not a good way to go.

I keep each O/S in it's own primary partition and hide or unhide them easily. I am not comfortable with any version of Windows playing well with any version of any other O/S. I think it is important to keep Windows locked up in it's own little place and kept on a leash!

Win 7 does come with a virtual thing, but I think it is only for using XP applications. There are times when good old DOS saves the day. and the DOS BOX in Windows is not the same.

I will probably continue my effort to use 9.1 in spite of the GRUB2 thing.

I am somewhat disappointed with some of the responses on this thread.  Some of them were offensive and insulting to me. Thats where my inappropriate use of the Fanboy label came from. Yes, I checked my own foot. It was bleeding. The bullet was from having tried a newer version of Ubuntu. Yes, I do Google for information so kindly refrain from trying to make others look totally incompetent. I am a LEARNER not an expert like some of you think you are.

What none of us know is how many others have heard great things about Ubuntu, downloaded it, installed it, and ended up with a non-functioning system. Some of those folks were willing to ask for help on the forum. Some of them got the help, some didn't or maybe couldn't ask. They simply went away in disgust thoroughly convinced that Ubuntu only destroys computers. 

I am still of the opinion that Ubuntu has shot itself in the foot by changeing to a highly complicated boot mechanism. Yes, in some circumstances it works but when it doesn't you got big problems.

Sorry to hear about all your troubles. Maybe I am confused about something you are doing, but I have always found, for simple dual booting, that most problems come from trying to do something out of the ordinary. I respect your desire to do so, but I have never seen a default install anything pertaining to grub2, I know way back in the day I decided to see what not installing to the mbr to the first sector of my drive would do... Ahhh the wonderful memories. I sincerely hope you find a solution to this problem, and if you do, I hope that you share it with the community so that anyone else who might be having similar issues has a place to look.

Now as a closing you I am a little shocked at how a portion of the comments were down right disrespectful toward someone who was having a problem, and I understand why this was insulting to you. In the future, however, it might be best that instead of stooping to their level, you be the better person, Kindness is always returned in some way, however, so is rudeness.

---

### Post by kelvin spratt on 2010-02-14
I think A majority of users are missing the the point Ubuntu is based on Debian unstable,
This is why it uses Beta drivers etc, Grub2 is the next generation of boot loaders if you want stable releases you need to use Debian Lenny. or CentOS.
I think Ubuntu certainly Mint Linux gets as close to a stable Distro as possible.

---

### Post by running_rabbit07 on 2010-02-14
Debian is great if you are a pro and can compile everything your self. Otherwise, one is stuck with very out of date programs and no drivers for nVidia. At least Ubuntu offers up drivers in almost every situation. In the end, it takes much more work with Debian to get it running than it does to get Ubuntu working.

---

### Post by HappyFeet on 2010-02-14
> **kelvin spratt said:**
> I think A majority of users are missing the the point Ubuntu is based on Debian unstable,
But over time, with updates, becomes very stable.
> **kelvin spratt said:**
> This is why it uses Beta drivers etc, Grub2 is the next generation of boot loaders if you want stable releases you need to use Debian Lenny. or CentOS.
Not true for everyone. Every ubuntu release has been rock solid for me, even right after it's released.

---

### Post by HappyFeet on 2010-02-14
> **running_rabbit07 said:**
> Debian is great if you are a pro and can compile everything your self. Otherwise, one is stuck with very out of date programs and no drivers for nVidia. At least Ubuntu offers up drivers in almost every situation. In the end, it takes much more work with Debian to get it running than it does to get Ubuntu working.

I have to somewhat disagree with this. When I first used debian, (and used it for about a month) I had no problems getting everything setup and running. All you need to do is just get the proper repos added, and everything will show up in synaptic.

It only took slightly more time to set it up than ubuntu, because of the repos. No compiling for anything was needed. The only reason I use ubuntu instead, is because of the newer packages. But even in debian, it's not hard to get newer versions.

---

### Post by running_rabbit07 on 2010-02-14
> **HappyFeet said:**
> I have to somewhat disagree with this. When I first used debian, (and used it for about a month) I had no problems getting everything setup and running. All you need to do is just get the proper repos added, and everything will show up in synaptic.

It only took slightly more time to set it up than ubuntu, because of the repos. No compiling for anything was needed. The only reason I use ubuntu instead, is because of the newer packages. But even in debian, it's not hard to get newer versions.

Every install I did of Debian, Lenny and Squeeze, nVidia drivers were nowhere to be found to install them. The source.list were improperly configured and I could not run updates nor install anything.

---

### Post by kelvin spratt on 2010-02-14
> **HappyFeet said:**
> But over time, with updates, becomes very stable.

Not true for everyone. Every ubuntu release has been rock solid for me, even right after it's released.

Please when you quote Quote correctly not just the bits you can use to justify yourself.
this was the last paragraph you should of included this as well as it states that Ubuntu is Quite stable. 
[COLOR=Red]I think Ubuntu certainly Mint Linux gets as close to a stable Distro as  possible.[/COLOR]

---

### Post by tdawgf on 2010-02-14
> **running_rabbit07 said:**
> Every install I did of Debian, Lenny and Squeeze, nVidia drivers were nowhere to be found to install them. The source.list were improperly configured and I could not run updates nor install anything.

Well in all fairness ubuntu is kind of ahead of the game in terms of graphics drivers. Most distro's only provide open source drivers, and by default so does Ubuntu. They just have a much easier way to get your drivers. There are some pretty amazing guides out there for installing your drivers with out the nifty little app though.

---

### Post by HappyFeet on 2010-02-14
> **kelvin spratt said:**
> Please when you quote Quote correctly not just the bits you can use to justify yourself.
this was the last paragraph you should of included this as well as it states that Ubuntu is Quite stable. 
[COLOR=Red]I think Ubuntu certainly Mint Linux gets as close to a stable Distro as  possible.[/COLOR]

I wasn't trying to justify anything. I merely responded to a separate sentence. Besides, you are contradicting yourself, when you say if you want stable, use debian or centos, then say say ubuntu or mint is as stable as it gets. See? Make up your mind.

---

### Post by HappyFeet on 2010-02-14
> **running_rabbit07 said:**
> Every install I did of Debian, Lenny and Squeeze, nVidia drivers were nowhere to be found to install them. The source.list were improperly configured and I could not run updates nor install anything.

Hmmm, I had no such problems, and did not do anything special. I merely added a couple of repos, and BAM! everything I needed, from codecs to nvidia drivers were in synaptic. Even my wireless driver and tv tuner card worked. Was actually pretty easy.

If you want hard to set up, try Linux From Scratch, or even Slackware. Then talk to me about difficult. ;)

---

### Post by Hallvor on 2010-02-15
> **running_rabbit07 said:**
> Every install I did of Debian, Lenny and Squeeze, nVidia drivers were nowhere to be found to install them. The source.list were improperly configured and I could not run updates nor install anything.

It is not hard at all to install proprietary Nvidia drivers in Debian.

Fire-up your favorite terminal, if you don't know, hit the alt+F2 keys and type in xterm, then hit enter.

You'll need to become root in order to accomplish installing the drivers. Linux clearly seperates operational duties and liberties and that's a good thing. Becoming root is simple, in your terminal, 1issue: su , hit enter, input the password, enter again.

The first thing we do is to stop our graphical shell which is what the graphics drivers we are about to install would affect. This is easily accomplished by issuing the following command:

> /etc/init.d/gdm stop

Make sure you have contrib and non-free in your sources.list:

```
nano /etc/apt/sources.list
```

like this:

```
deb http://ftp.us.debian.org/debian/ lenny main contrib non-free
deb-src http://ftp.us.debian.org/debian/ lenny main contrib non-free

deb http://security.debian.org/ lenny/updates main contrib non-free
deb-src http://security.debian.org/ lenny/updates main contrib non-free
```

After that, just type:

```
aptitude update

aptitude install module-assistant

m-a prepare

m-a update
```


Select ONE of the following:

```
m-a a-i nvidia
```  

--OR--  

```
m-a a-i nvidia-legacy
```

Then continue with:

```
aptitude install nvidia-xconfig

nvidia-xconfig

modprobe nvidia

/etc/init.d/gdm start
```

[http://www.debiantutorials.org/module-assistant-nvidia-lenny](http://www.debiantutorials.org/module-assistant-nvidia-lenny)


All you need is the skill to replicate a few simple commands. That`s it.

---

### Post by mörgæs on 2010-02-15
Shooting oneself in the foot is a clever act done by a soldier in a hopeless situation. He will be brought to the infirmary where the foot may or may not be saved, but his life will. It does not indicate stupidity or giving oneself trouble, on the contrary it is a sign of judgement and will-to-survive.

---

### Post by Hallvor on 2010-02-15
> **mörgæs said:**
> It does not indicate stupidity or giving oneself trouble, on the contrary it is a sign of judgement and will-to-survive.

...and also cowardice.

---

### Post by XubuRoxMySox on 2010-02-15
A soldier who shoots himself in the foot - whether by accident or by design - is disgraced in the eyes of his fellow soldiers.

I dunno whether I'd call the inclusion of Beta software by default "shooting itself in the foot," but I do call it a bad idea. Really bad. Because:

**Beta software ** **has no place in a distro that is supposed to be "newbie friendly."**

And, a relatively new user like me who tries to share Linux with others and finds that Grub2 or PulseAudio messes up or freezes a *friend's* computer, with the result that both Ubuntu *and* the person who wants to share Linux look bad.

I can never recommend to a newbie any distro or version that has unproven, troublesome software by default. I prefer a rock-stable, tried-and-proven distro like Mepis to introduce new users to Linux from now on. Now that Ubuntu has shot itself in the foot, and I've caught a bunch of the grief it caused.

-Robin

---

### Post by scottuss on 2010-02-15
"Ubuntu has shot itself in the foot"

Ouch, I bet that hurt.

Anyway, I was under the impression that non-LTS releases were officially considered "testing / unstable"?

Doesn't this mean that all the arguments about whether unstable software should be included in each new release invalid, unless we're discussing an LTS release?

That's the way I see it, anyway.

---

### Post by mike264 on 2010-02-15
I wouldn't say they shot themselves in the foot, but I would like to have had the choice between Grub1 or 2.  I had 9.04 installed and then installed 9.10 on a second partition. Everything was alright until I had a kernel update in 9.04. Grub2 did not pick up the newer kernel version even after I updated Grub2. I was going to update manually but found it confusing compared to Grub1. Fortunately, I only installed 9.10 to experiment with it. I ended up formatting 9.10 and installing 9.04 and upgrading it to 9.10, keeping Grub1.
I don't think Grub2 is ready yet to be the prime boot loader.

Mike264

---

### Post by uRock on 2010-02-15
> **Hallvor said:**
> <snip>

Wow, I could have used all of that back when I tried Debian. I had the same problems as running_rabbit07 when it came to getting nVidia installed and with the not being able to get update manager and synaptic to connect to the repos. Thankx for posting and I will print this info to give it a try in the near future.

---

