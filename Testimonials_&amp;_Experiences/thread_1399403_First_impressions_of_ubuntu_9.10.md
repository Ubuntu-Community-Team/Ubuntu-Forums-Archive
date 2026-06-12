---
title: "First impressions of ubuntu 9.10"
date: 2010-02-05
forum: Testimonials &amp; Experiences
---

### Post by chadknackers on 2010-02-05
It stinks big time. Like the rear end of a dinosaur. Let me tell you why.

I've been using Unix and Linux for about 10 years. This was back in the good old days of recompiling the kernel to get a sound card working. Nowadays things are meant to be easy.

So, I have a laptop with Windows XP pre-installed, but without a CD ROM. But that's OK, because I know how to netboot things, and that's how I got FreeBSD and Solaris onto this laptop for a three way multiboot. I thought it would be nice to put Ubuntu onto it.

Rather than just go full steam ahead I decide to put Ubuntu into a Virtualbox on my desktop machine first. No problem there, it installs fine. It reboots but I can't log in at the graphical login. It's not a password problem because I set the password to 'a', and I know I'm not mistyping a one letter password.

So my very first impression of Ubuntu is that it doesn't work. But I want to know why. So, being familiar with Linux, I do Alt-F2, and log in that that. Same username, same password. So I tail /var/log/messages, then go back to the graphical login and try to get in again. Same failure, so I switch back to text console and have a look. ssh-agent is segfaulting.

So, it's not me. It's Ubuntu that is at fault. It is literally faulty. And why ssh-agent needs to automatically run the very first time I try to log in I do not know. How does Ubuntu know that I will ever use ssh?

The installation was fine, it looks very pretty and is easy to follow, but it boots up with an unusable system. Why is this? I'll tell you: poor testing. I could fix this, but why should I? What if I was not a dab hand at UNIX/Linux? What if I was a total newbie who was persuaded to use Ubuntu? I'll tell you now that I would spend about two minutes bothering to log in, then give up and go back to Windows land where I can log in without problems.

For crying out loud. This is just really poor. Needless to say that I won't bother re-partitioning my laptop hard drive to make space for Ubuntu. My life is too short to waste on things which don't work. Perhaps it would work differently on real rather than virtual hardware, but I'm not going to waste my time finding out. Other things work well in Virtualbox, but Ubuntu doesn't.

10/10 for ease of installation.
0/10 for functionality thereafter.

Boo.

---

### Post by markbuntu on 2010-02-06
Most likely your virtual box setup is kludged. There are some wikis around about installing ubuntu in virtual box which can require some special considerations.
Did you read them?

Anyway, nobody put a gun to your head and made you do this so you should just relax.

---

### Post by chadknackers on 2010-02-06
No, it's not my Virtualbox which is broken. It is Ubuntu. But your response is typical of people who don't read posts properly.

You are right that nobody forced me to use Ubuntu. And that is a good thing, because it is unusable.

---

### Post by wojox on 2010-02-06
I've been using Linux since April 2009 and no problems. Sounds like an operator error. ;)

---

### Post by craig10x on 2010-02-06
Wow...well all i can tell you is that i was using 9.04 for 6 months and everything worked perfectly...and compared to windows...it was the most trouble free time i have ever experience on a computer....I wouldn't go back to windows now if you paid me...

Then 3 days ago, i decided to to change over to 9.10...and did a clean install (Ubuntu is all i run on here)...it's a 1 year old Toshiba Laptop with AMD Turion X2 and Ati Radeon graphics....and 9.10 installed PERFECTLY and EVERYTHING WORKS...plus i got some very nice improvements...

So...in my book Ubuntu isn't a worthless operating system...it's a PRICELESS operating system...:D

---

### Post by dondiego2 on 2010-02-06
> **craig10x said:**
> wow...well all i can tell you is that i was using 9.04 for 6 months and everything worked perfectly...and compared to windows...it was the most trouble free time i have ever experience on a computer....i wouldn't go back to windows now if you paid me...

Then 3 days ago, i decided to to change over to 9.10...and did a clean install (ubuntu is all i run on here)...it's a 1 year old toshiba laptop with amd turion x2 and ati radeon graphics....and 9.10 installed perfectly and everything works...plus i got some very nice improvements...

So...in my book ubuntu isn't a worthless operating system...it's a priceless operating system...:d


x2

---

### Post by Tamlynmac on 2010-02-06
> chadknackers

Thank you for sharing your experience. Sorry you had problems. But good luck with what ever OS you choose. Since this is not a debating section of the forum, I will not comment on your opinions.

---

### Post by simeon87 on 2010-02-06
> **chadknackers said:**
> You are right that nobody forced me to use Ubuntu. And that is a good thing, because it is unusable.

Nobody forced you to post here either, but apparently you did. The far majority has no such problems that you've experienced and there's no need to complain here about the operating system itself, it's far more likely your particular configuration that's at fault. Or are you really saying that Ubuntu shipped with a password/logging in problem that nobody experienced except you?

---

### Post by 3rdalbum on 2010-02-07
Not being able to log in is a well-known symptom of a corrupted download, misburnt install CD or faulty hard disk. Obviously, your problem doesn't happen to all of us, and by its popularity Ubuntu is probably the most well-tested Linux distribution ever. It's not like this is a problem that could affect everybody and fly underneath the radar, either.

Re-download Ubuntu, this time from a torrent so its integrity is checked at each stage. And next time, check your man pages before complaining:

> The idea is that ssh-agent is started in the begin-
     ning of an X-session or a login session, and all other windows or pro-
     grams are started as clients to the ssh-agent program.

Source: man ssh-agent

---

### Post by Methuselah on 2010-02-07
Sorry it stinked for you.
Good thing it only cost you a little time and there are mannyy options.
):P

---

### Post by the8thstar on 2010-02-07
Another waste of reading and writing time for us posters. These threads are getting old and painful.

---

### Post by chadknackers on 2010-02-07
> **craig10x said:**
> .and 9.10 installed PERFECTLY and EVERYTHING WORKS...

Good for you. But it doesn't work for me. That is all that counts. I don't care if it works for the man on the moon.

---

### Post by chadknackers on 2010-02-07
> **simeon87 said:**
> there's no need to complain here about the operating system itself

But why shouldn't I complain here. This is an Ubuntu forum, and Ubuntu does not work for me.

---

### Post by chadknackers on 2010-02-07
> **wojox said:**
> I've been using Linux since April 2009 and no problems. Sounds like an operator error. ;)

I've been using Linux since Redhat 4.2. You have nothing on me as far as Linux experience goes. Read my post properly next time, noob.

---

### Post by automaton26 on 2010-02-07
Well, that's your experience - but did you try all the usual caveats like check the MD5SUMs for all downloaded .iso files, and verify any written CDs ?

I used to dual-boot, but recently reinstalled Vista and put Kubuntu within VirtualBox instead (mainly because I'm having to develop in Windows at the moment).

I had no problems whatsoever, and it works really simply and smoothly. I can fire Kubuntu up quickly, do some safe browsing or media editing, and then close it again.

Fantastic - I wish I'd found out about VirtualBox ages ago.

---

### Post by craig10x on 2010-02-07
> **chadknackers said:**
> Good for you. But it doesn't work for me. That is all that counts. I don't care if it works for the man on the moon.

My friend, who bought my old toshiba and hp laptop...and those are about 3 to 4 years old, and very basic models with 512 mb memory...maybe 60 gb hard drives and intel celeron processors, and had windows xp on them....he installed 9.10 on them recently also and everything also worked on them "out of the box"

So, i would hardly say it was just a fluke or because i happen to have a newer laptop now.....if your particular hardware isn't compatible...why not buy a new laptop ...and just wipe out the horrid windows system and install 9.10....

You could go to Best Buy and get a great toshiba laptop with 15 inch screen for about $400-$500 or a 17 inch one for about $500-$600....

Beats having to live with Windows...Ubuntu and Linux are a great OS system and far superior to Windows in every way...isn't it worth a bit of an extra effort so you can enjoy it too?  Or are you just a Windows fanboy who is "trolling" here?

---

### Post by chadknackers on 2010-02-07
> **craig10x said:**
> 
Beats having to live with Windows...Ubuntu and Linux are a great OS system and far superior to Windows in every way...isn't it worth a bit of an extra effort so you can enjoy it too?  Or are you just a Windows fanboy who is "trolling" here?

Actually, no it doesn't beat living with Windows. Because at least with Windows I can log in without any problems. Ubuntu has provided me with an unusable system. It shouldn't require any extra effort on my part, it should just work.

Nothing to do with being a fan boy. As mentioned, I've used Linux for about ten years. 

Let me tell you now that not being able to log in does not make Linux superior to Windows "in every way". It makes it infinitely worse.

---

### Post by chadknackers on 2010-02-07
> **automaton26 said:**
> Well, that's your experience - but did you try all the usual caveats like check the MD5SUMs for all downloaded .iso files, and verify any written CDs ?

I used to dual-boot, but recently reinstalled Vista and put Kubuntu within VirtualBox instead (mainly because I'm having to develop in Windows at the moment).

I had no problems whatsoever, and it works really simply and smoothly. I can fire Kubuntu up quickly, do some safe browsing or media editing, and then close it again.

Fantastic - I wish I'd found out about VirtualBox ages ago.

Zzzzzzzzzzzz.

---

### Post by chadknackers on 2010-02-07
> **the8thstar said:**
> Another waste of reading and writing time for us posters. These threads are getting old and painful.

If "these threads are getting old and painful" it means that people have problems running Linux. Had that ever occurred to you?

---

### Post by chadknackers on 2010-02-07
> **3rdalbum said:**
> Not being able to log in is a well-known symptom of a corrupted download, misburnt install CD or faulty hard disk. Obviously, your problem doesn't happen to all of us, and by its popularity Ubuntu is probably the most well-tested Linux distribution ever. It's not like this is a problem that could affect everybody and fly underneath the radar, either.

Re-download Ubuntu, this time from a torrent so its integrity is checked at each stage. And next time, check your man pages before complaining:

Source: man ssh-agent


I see you blame anything except Linux. No, it's not a faulty download, nothing like that. If you think this is an isolated problem you have absolutely no understanding of how software development works. Do you really think that testing removes all bugs? You are mad. It removes bugs that are found, that is all. And any such changes as a result probably introduce other bugs.

Jesus. Some people think that Linux has no bugs.

---

### Post by markbuntu on 2010-02-07
If you find bugs, you should report them at launchpad or one of the developer sites if you would care for them to get fixed. Do not think that someone else will report your bug, they won't either.

Just complaining in the forums will not get bugs fixed, devs do not hang out here.

It is impossible for the devs and the distribution packagers to test everything on every concievable combination of hardware so they depend on users to report bugs so they can get fixed.

Microsoft takes the easy way out, they just lop off entire generations of hardware and say "This is no longer supported by our new operating system." The linux community takes a broader view and seeks to support all hardware. 

Microsoft can make the manufacturers provide hardware drivers. This is very difficult for the linux community as the hardware manufacturers are not under such pressure when it comes to supporting linux. A few do, but many do not.

So, if you are having problems with your linux system and do not report bugs, how do you expect them to get fixed?
If you are having problems with your hardware you should berate the manufacturers for not providing linux drivers.

We are trying the best we can, if it is not good enough for you then you can either join the effort or go somewhere else.

---

### Post by sandkernel on 2010-02-07
I've been a Unix admin for 10 years. Have admined Sun, AIX, Redhat, FreeBSD, Sles, OpenSuSe - you name it. Setting up a test system on a Virtual Box and expected it to duplicate an actual system may not be the best testing ground. There could be a an issue between your hardware and Sun Virtual Box for all you know. To say that Ubuntu sucks based on that install is not fair to be honest.

My last 2 work laptops have been Linux laptops with Windows laptops before them. Currently I am running Ubuntu 9.10 on a T400 and it kicks ***, at least as far as I am concerned.

---

### Post by running_rabbit07 on 2010-02-07
> **chadknackers said:**
> I see you blame anything except Linux. No, it's not a faulty download, nothing like that. If you think this is an isolated problem you have absolutely no understanding of how software development works. Do you really think that testing removes all bugs? You are mad. It removes bugs that are found, that is all. And any such changes as a result probably introduce other bugs.

Allah. Some people think that Linux has no bugs.

Have you tested the download with the MD5?  Until you can say you actually checked everything, you can't pass blame. I give 3rdalbum's post some merit being he helps people often and chances are he's already helped people fix the exact issue you are having.

---

### Post by armandh on 2010-02-07
still chances are not being able to access the os could have been avoided by checking the automatic log on box during setup.

then one would not have to remember what was used as an ID or PW

Not trying again to set it up while using greater care when entering these important items 
but just complaining has the OP looking like a troll

---

### Post by running_rabbit07 on 2010-02-08
> **chadknackers said:**
> I've been using Linux since Redhat 4.2. You have nothing on me as far as Linux experience goes. Read my post properly next time, noob.

Arrogance and ignorance go hand-in-hand, don't they? I've been playing guitar for more than 20 years, but I have met people who picked it up for a few weeks and were playing better.

---

### Post by solwic on 2010-02-08
> **chadknackers said:**
> I see you blame anything except Linux. No, it's not a faulty download, nothing like that. If you think this is an isolated problem you have absolutely no understanding of how software development works. Do you really think that testing removes all bugs? You are mad. It removes bugs that are found, that is all. And any such changes as a result probably introduce other bugs.

Jesus. Some people think that Linux has no bugs.

OK.  You win.  Ubuntu sucks.  

You waiting around for a farewell party or something?

---

### Post by chadknackers on 2010-02-08
> **markbuntu said:**
> Microsoft takes the easy way out, they just lop off entire generations of hardware and say "This is no longer supported by our new operating system." 

Do they? XP was released in 2001. It is still supported.

---

### Post by chadknackers on 2010-02-08
> **sandkernel said:**
> I've been a Unix admin for 10 years. Have admined Sun, AIX, Redhat, FreeBSD, Sles, OpenSuSe - you name it. Setting up a test system on a Virtual Box and expected it to duplicate an actual system may not be the best testing ground. There could be a an issue between your hardware and Sun Virtual Box for all you know. To say that Ubuntu sucks based on that install is not fair to be honest.

My last 2 work laptops have been Linux laptops with Windows laptops before them. Currently I am running Ubuntu 9.10 on a T400 and it kicks ***, at least as far as I am concerned.

Likewise I have done UNIX admin for 10 years - Solaris, Linux (several distros), FreeBSD, NetBSD, etc.

I agree that VirtualBox does not perfectly replicate hardware. But this is the first installation of Linux that has not worked on it (for me). It installed fine (or seemed to), it boots up fine, but does not allow me to log in.

The whole purpose of testing Ubuntu on VirtualBox before putting it on real hardware is to see if there would be any problems. Unfortunately there were.

---

### Post by chadknackers on 2010-02-08
> **running_rabbit07 said:**
> Arrogance and ignorance go hand-in-hand, don't they? I've been playing guitar for more than 20 years, but I have met people who picked it up for a few weeks and were playing better.

What is arrogant or ignorant about my post? The fact that you can't play a guitar well after twenty years just means you are crap at playing a guitar. It doesn't have anything to do with Ubuntu delivering an unusable system.

---

### Post by chadknackers on 2010-02-08
> **armandh said:**
> still chances are not being able to access the os could have been avoided by checking the automatic log on box during setup.

then one would not have to remember what was used as an ID or PW

Not trying again to set it up while using greater care when entering these important items 
but just complaining has the OP looking like a troll

So now it's my fault for enabling automatic login? Suppose I didn't want automatic login so didn't select that on purpose?

Open your eyes and read the post. I have described what the problem is.

---

### Post by running_rabbit07 on 2010-02-08
> **chadknackers said:**
> What is arrogant or ignorant about my post? The fact that you can't play a guitar well after twenty years just means you are crap at playing a guitar. It doesn't have anything to do with Ubuntu delivering an unusable system.

Arrogance= Thinking you know more about something because you have been doing it longer. 

I guess your ignorance is bliss.

---

### Post by davec64 on 2010-02-08
> **running_rabbit07 said:**
> Arrogance= Thinking you know more about something because you have been doing it longer. 

I guess your ignorance is bliss.

X1

I was going to try to help, but as the OP hasn't really given any details of the virtualbox configuration or "specifics" relating to the "not being able to log in" problem, I see no reason to try and help. I note he's also not bothered to reply to those posts that have even offered help choosing just to have a go at anybody who has a working system, not very helpful and not very interesting really.

Ubuntu and a community forum clearly isn't for you, so I hope you're happy with what you choose in the future. I suggest leaving Linux well alone as the individual distro's are communities more than just an OS.

Please don't bother replying to my post as it will purely be wasted effort on your part as I won't be revisiting this thread. I have no desire to read anymore rubbish.

Best wishes in what you choose for the future.

---

### Post by chadknackers on 2010-02-09
> **running_rabbit07 said:**
> Arrogance= Thinking you know more about something because you have been doing it longer. 

I guess your ignorance is bliss.

I see, in your book experience = arrogance. I think I've heard enough from you.

---

### Post by chadknackers on 2010-02-09
> **davec64 said:**
> X1

I was going to try to help, but as the OP hasn't really given any details of the virtualbox configuration or "specifics" relating to the "not being able to log in" problem, I see no reason to try and help. I note he's also not bothered to reply to those posts that have even offered help choosing just to have a go at anybody who has a working system, not very helpful and not very interesting really.

Ubuntu and a community forum clearly isn't for you, so I hope you're happy with what you choose in the future. I suggest leaving Linux well alone as the individual distro's are communities more than just an OS.

Please don't bother replying to my post as it will purely be wasted effort on your part as I won't be revisiting this thread. I have no desire to read anymore rubbish.

Best wishes in what you choose for the future.


I could fix this if I wanted to. But the point is I shouldn't need to fix it. It is a from-scratch installation. How could it break before I have even logged in? I'll tell you how: crappy testing by whoever does the testing.

---

### Post by running_rabbit07 on 2010-02-09
> **chadknackers said:**
> I see, in your book experience = arrogance. I think I've heard enough from you.

And there is the proof of ignorance. Don't be broken hearted when you learn that there are people with less time of experience just happen to know more than you, which you're proving more and more with every post.

Good luck with Windows,
Bye-bye.

---

### Post by running_rabbit07 on 2010-02-09
> **chadknackers said:**
> I could fix this if I wanted to. But the point is I shouldn't need to fix it. It is a from-scratch installation. How could it break before I have even logged in? I'll tell you how: crappy testing by whoever does the testing.

You burnt and installed a bad image and now it is Ubuntu's fault? Wow, I learnt that in the first week. Judging by your bean count, I'd say you are new to this.

---

### Post by Methuselah on 2010-02-09
A faulty download is a real possibility...not to say it is the only possibility.
I once experienced a world of weirdness and it turned out that I had a bad memory (RAM) stick.
I suppose it could be a bug in Ubuntu but not being able to log would have likely attracted attention unless it is triggered by very specific conditions.
In which case, existence of an obscure bug is hardly proof of lack of testing.

I would check out that iso/disc.
Good luck!

---

### Post by cariboo on 2010-02-10
The op doesn't seem to want any help, as the only posts he's made are in this thread. This thread is going nowhere. Closed

---

### Post by HappyFeet on 2010-02-10
> **chadknackers said:**
> crappy testing by whoever does the testing.

Just because the devs didn't test ubuntu on every possible hardware configuration, and it doesn't work on yours, doesn't mean it's bad. Use some common sense.

---

### Post by running_rabbit07 on 2010-02-10
> **HappyFeet said:**
> Just because the devs didn't test ubuntu on every possible hardware configuration, and it doesn't work on yours, doesn't mean it's bad. Use some common sense.

Yeah, but he is a senior Linux operator. I think he will be happy with Ubuntu. After all, it is the best OS for your buck!:D

---

### Post by chadknackers on 2010-02-10
> **running_rabbit07 said:**
> And there is the proof of ignorance. Don't be broken hearted when you learn that there are people with less time of experience just happen to know more than you, which you're proving more and more with every post.

Good luck with Windows,
Bye-bye.

But why should I need to know how to fix a broken installation? Is that not an admission that the installation system is broken, and should therefore be fixed?

Windows works fine. Ubuntu does not.

---

### Post by chadknackers on 2010-02-10
> **running_rabbit07 said:**
> You burnt and installed a bad image and now it is Ubuntu's fault? Wow, I learnt that in the first week. Judging by your bean count, I'd say you are new to this.

How can you possibly tell from my original post (or follow ups) that I have burnt a bad CD? Your presumption tells me a lot about you.

I didn't even burn a CD. I tried to install Ubuntu in VirtualBox, using the checksummed iso image.

Next time, don't jump to conclusions.

---

### Post by chadknackers on 2010-02-10
> **HappyFeet said:**
> Just because the devs didn't test ubuntu on every possible hardware configuration, and it doesn't work on yours, doesn't mean it's bad. Use some common sense.

VirtualBox is not uncommon.

---

### Post by chadknackers on 2010-02-10
> **running_rabbit07 said:**
> Yeah, but he is a senior Linux operator. I think he will be happy with Ubuntu. After all, it is the best OS for your buck!:D

I tried to use Ubuntu. Alas it doesn't allow me to log in, which makes it useless.

---

### Post by running_rabbit07 on 2010-02-10
I have run every Ubuntu from Feisty to Lucid in the VBox and have had only problems when upgrading the Alphas and even with Lucid, those alpha upgrades haven't had any issues. I guess you and Ubuntu weren't meant to be.

Good luck with whatever you use.

---

### Post by alh on 2010-02-10
> **chadknackers said:**
> I tried to use Ubuntu. Alas it doesn't allow me to log in, which makes it useless.
Man....... you're turning into a real bore! :-{

---

### Post by darrenn on 2010-02-11
> I got FreeBSD and Solaris onto this laptop for a three way multiboot.

It was easier for you too install bsd and solaris? That's rich.

---

### Post by Sef on 2010-02-11
> The op doesn't  seem to want any help, as the only posts he's made are in this thread.  This thread is going nowhere. Closed

Closed Now.

---

