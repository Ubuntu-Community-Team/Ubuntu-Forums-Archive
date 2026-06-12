---
title: "Automatix2 now has Thunderbird 2.0."
date: 2007-05-16
forum: The Cafe
---

### Post by kittyhawk63 on 2007-05-16
I just installed Automatix2 and found it has now included Thunderbird 2.0. It will delete any former Thunderbird versions and keep your settings for the 2.0 version. Those who like Thunderbird and _don't mind using Automatix2_ will find this the easiest way to install.

Note: I appreciated the help from several who gave instructions on installing Thunderbird as a tar.gz file. However, it still remains true, Automatix2 is the simplest method.
kh

---

### Post by chamberlain2006 on 2007-05-16
It may be harder, but installing from the tar.gz file would be much more reliable.  Automatix2 is known to screw you sometimes.

---

### Post by taurus on 2007-05-16
> **kittyhawk63 said:**
> I just installed Automatix2 and found it has now included Thunderbird 2.0. It will delete any former Thunderbird versions and keep your settings for the 2.0 version. Those who like Thunderbird will find this the easiest way to install.

Note: I appreciated the help from several who gave instructions on installing Thunderbird as a tar.gz file. However, Automatix2 is the simplest method.
kh

Well, good luck with Automatix and if it breaks your system later on for whatever reason, you should post the problem on their support forum since they are better equipped to handle it.

---

### Post by kittyhawk63 on 2007-05-16
Thanks Taurus. I will take your advice. I couldn't get Thunderbird 2.0 to install using your instructions. There was something about not being able to make a link to any locations. I was going to install 1.5. via Automatix2. I have never had a problem with Automatix2 installing Thunderbird 1.5. I was surprised to see the 2.0 version. I tried it and it works. 
Thanks again.
kh

---

### Post by taurus on 2007-05-16
It's your system so you can install whatever you want.  Just want to let you know in case there is a problem with your machine later on, then you can't really blame Ubuntu.

---

### Post by oilchangeguy on 2007-05-16
> **taurus said:**
> It's your system so you can install whatever you want.  Just want to let you know in case there is a problem with your machine later on, then you can't really blame Ubuntu.

why not post a survey. which has caused more system damage/problems. improper command line use. or using automatix. i'd bet hands down it's improper command line usage. when will the command line junkies admit that not everybody wants to be like them? most computer users of any operating system want the simplest ways to do something. how many windows users actually take the time to do routine maintenance (defrag, etc.) probably less than 10%. ubuntu may not support automatix (i don't know for sure) but during regular ubuntu updates, updates to automatix are included. why not acknowledge there are simpler ways to install programs than using the command line for everything? how many users in this forum get incorrect commands from other users? yes the command line has it's place. just not for everything. there are other ways. i've used automatix on both of my computers that run 6.06, and never had a problem.

---

### Post by kittyhawk63 on 2007-05-16
> **taurus said:**
> It's your system so you can install whatever you want.  Just want to let you know in case there is a problem with your machine later on, then you can't really blame Ubuntu.

Your right, and I won't.  I will say that I agree with oilchangeguy. I have never had a problem, yet, using Automatix2. I have used it on four different Linux versions. Could it be just a problem with system incompatibilities? I would not be the one to know this. I am too much of a noob to answer that. I only know what I know. I know that Automatix2 has done me a good job so far. However, saying that, I also like the command line. I like knowing something of what it takes to get a program installed and working properly.
kh

---

### Post by compiledkernel on 2007-05-16
> I've used automatix on both of my computers that run 6.06, and never had a problem. 

You might at upgrade though, there has been talk about blocking 6.06 systems with automatix installed on them at UDS. While a bit extreme it does exemplify the unsupported nature of Automatix with respect to Ubuntu. 

Moving thread to cafe, this isnt a support thread.

---

### Post by oilchangeguy on 2007-05-16
> **compiledkernel said:**
> You might at upgrade though, there has been talk about blocking 6.06 systems with automatix installed on them at UDS. While a bit extreme it does exemplify the unsupported nature of Automatix with respect to Ubuntu. 

Moving thread to cafe, this isnt a support thread.
i'd never go thru the hassle of upgrading, clean installs on any os, is the best way to go. so when the next lts version is released i'll do a clean install of that.

---

### Post by Saphira on 2007-05-16
Actually the way I've heard it is that update-manager will look for instances of automatix and other related **helper scripts** that could possibly cause system breakage and then just say no if you attempt to use upgrade-manager to upgrade your system.

---

### Post by maniacmusician on 2007-05-16
> **compiledkernel said:**
> You might at upgrade though, there has been talk about blocking 6.06 systems with automatix installed on them at UDS. While a bit extreme it does exemplify the unsupported nature of Automatix with respect to Ubuntu. 

Moving thread to cafe, this isnt a support thread.
The upgrade caused a lot of problems for people who didn't use Automatix as well. Take Edgy > Feisty. That was much smoother for most people, including those that used Automatix. 

The problem really is just having 3rd party libs in your system. When you upgrade, those don't get updated properly, since they're still linked to older libraries. That causes all kinds of conflict and that's why all hell breaks loose during updates.

---

### Post by Xanatos Craven on 2007-05-16
[http://www.getautomatix.com/forum/index.php?showtopic=902&pid=3717&st=0&#entry3717](http://www.getautomatix.com/forum/index.php?showtopic=902&pid=3717&st=0&#entry3717)

I don't know enough about the subject to personally comment on it, but you might find that thread an interesting read as far as Automatix FUD is concerned, and I'd like to say that I've used Automatix for a long time now and it hasn't broken my system at all or caused update issues.

[quote=Saphira]Actually the way I've heard it is that update-manager will look for instances of automatix and other related helper scripts that could possibly cause system breakage and then just say no if you attempt to use upgrade-manager to upgrade your system.[/quote]
What you described sounds quite unrealistic. You'd be more believable if you just said update-manager would fail. To actively detect helper scripts and refuse to upgrade because of them is against the spirit of Ubuntu, I'd think.

---

### Post by compiledkernel on 2007-05-16
I wasnt speaking of actual upgrade breakages maniac, merely that there has been talk of stopping Dapper systems with automatix installed on them (or other such programs) from upgrading in the future. ie. Upgrade-manager detects an installed a-x/e-u/envy/etc bit and says, no.

---

### Post by aysiu on 2007-05-16
> **oilchangeguy said:**
> why not post a survey. which has caused more system damage/problems. improper command line use. or using automatix. i'd bet hands down it's improper command line usage. I don't see why it has to be a competition. Anything that is likely to break your system should be discouraged. That is why I always chastise people who say > Oh, just type ```
sudo rm -r /media/sda1
``` If you do *sudo rm -r* and hit the *Enter* key a little too early (say, before the word *media*), your system will be screwed. Deleting through *gksudo nautilus* is a lot safer, especially since you can move things to the trash first instead of deleting things outright.

But I've seen very few instances of people asking others to copy and paste commands into the terminal without offering some caveat in bold letters if the command could break that person's system. When I have seen people offering up *sudo kate* as a command, I correct them right away (it should be *kdesu kate*).

Again, though, it isn't a competition, where Automatix is perfect and the command-line loses; or the command-line is perfect and Automatix loses. The two operate independently. Automatix could work perfectly... or break your system. The command-line could also work perfectly... or break your system.

> most computer users of any operating system want the simplest ways to do something. No they don't. Otherwise, they wouldn't complain so much about copying and pasting in a command or two. Most users don't mind if a task is complex as long as it requires very little learning. > ubuntu may not support automatix (i don't know for sure) but during regular ubuntu updates, updates to automatix are included. That's for two reasons: 1) Automatix often uses legitimate ways to install software and for many things is really just another way of using Synaptic, rendering Automatix redundant for many programs 2) Automatix adds its own repositories to your /etc/apt/sources.list, so it's not Ubuntu that's updating Automatix--it's Automatix itself that is updating Automatix > why not acknowledge there are simpler ways to install programs than using the command line for everything? They're not simpler, but they may require less learning. That's why I highly recommend Add/Remove Programs and Synaptic Package Manager. They are actually simpler in the vast majority of cases than Automatix is. > how many users in this forum get incorrect commands from other users? Very few. And, as I said before, in the rare cases they do, others jump in and correct the commands. > i've used automatix on both of my computers that run 6.06, and never had a problem. And only your experience matters?

---

### Post by compiledkernel on 2007-05-16
> 
What you described sounds quite unrealistic. You'd be more believable if you said update-manager would fail. To actively detect helper scripts and refuse to upgrade because of them is against the spirit of Ubuntu, I'd think.

Actually I dont think it would be too hard to do that, just search through the dpkg logs. Im sure there are remanents of automatix contained there in if you actually had it installed on your system. Update-manager could feasibly just do nothing in that case, or would opt to do nothing, I suppose.

---

### Post by oilchangeguy on 2007-05-16
"And only your experience matters?"

yes it matters. just as does every users. how many people who've said autamatix, or anything else for that matter will damage your computer are simply playing follow the leader, and have no clue what they are talking about? you've said that improper command line usage, and problems caused by automatix have caused system problems. so why don't we just stick with the facts, and not single out one thing. and yes most computer users just want things to work out of the box without having to jump thru hoops to get it done. when's the last time you used a command line in windows to get anything done? i fully understand that linux does not have the ease of installing some software via cd or easy web download. the software readily available in linux thru such apps like add/remove, etc. are great. but getting a program you downloaded from some web site to work can be a major hassle. getting some hardware to work in linux can be a major hassle. so to imply all of linux's ills can be solved by using the command line is just not realistic. i can't wait for shell shocked dell owners with ubuntu pre-loaded (this is a great day for ubuntu, and linux in general) start showing up in here. i know i'm not the only ubuntu user whose been mostly problem free with their ubuntu install. and hope that those that have, don't give up. ubuntu is a very good os (not perfect, but what os is?)

---

### Post by paparucino on 2007-05-16
Did someone  tried to do a distro-upgrade while automatix is active?
I tried it under Edgy. What I can say is that after 5 minutes of dirty words I had to   uninstall automatix and rewrite sources.lst.
It has to be noted that automatix was installed but never worked.

I think that in *buntu there are tools that do their job better than autoamtix.

It's no possibible to install thirdy parts? Saint Google is there to help everybody, the forums too.
Avoiding to be the usual point&click user is safe for the health
M$ and reality shows are for those users.

---

### Post by kittyhawk63 on 2007-05-16
This seems to have hit a nerve of difference of opinions. I was just intending to notify any who were interested that Automatix2 has Thunderbird 2.0 ready to install. I never intended to get a discussion started between GUI and the command line fans. The thing I like about Linux, you can have your cake and eat it too. Like what you see, then use it. Don't like what you have, then change it. There is...choke, choke...Windows. One way, like it or not. Before that starts another run, I still use Windows XP. I greatly dislike the fact that every time I install it, I have to call MS to get an activation key. I am being constantly nagged that my fresh install has not yet been activated and I have x amount of days to do so. Nag, nag, nag. :-\"I'll take my time, thank you. lol
kh

---

### Post by crane on 2007-05-16
> What you described sounds quite unrealistic. You'd be more believable if you just said update-manager would fail. To actively detect helper scripts and refuse to upgrade because of them is against the spirit of Ubuntu, I'd think.

So the Spirit of Ubuntu would be to let people upgrade a system Knowing they will have trouble because of a program. Sounds wrong, and I don't believe the Spirit of Ubuntu even pertains to this conversation.
This bugs me as much as "Windows is...." if you hide behind this then you do not know what you are doing. Windows is windows, this is Linux. If your going to set someone up to use linux they need to know what they are working with. I'm not saying they need to learn command line, but they have to realize that things are done different in linux than windows. What's next, we should change the file system to have a "C" drive so windows users will get it?
 Lets teach truths, not lies. Automatix is cool, not practical. OK so it may work to help keep people dumbed down on the working of Linux but that is not what we need. Seems the resources that went into Automatix (I mean the time and Work) could really help Ubuntu really prosper, unless the Automatix clan plans to start charging for the service, then that is another discussion altogether.

 Just my Thoughts

Crane

---

### Post by Saphira on 2007-05-16
Oilchangeguy, if you want to improve your experience and improve the experience of others then get involved. If you are as passionate about your OS as you come across, then jump in. Join a dev team, file a bug report on launchpad, file a bug report here. Join a mailing list and communicate with the developers. You don't have to be a developer or an uber geek to give back to the community, or help ubuntu , even as the software grows and develops. I think anyone here would probably say Ubuntu came along way by allowing mp3 playback to be installed from add/remove applications. 

Even the smallest of users, that has the simplest request can and does get heard. Supporting 3rd party applications that make your life easier doesn't do anything to help anyone elses experiences. Get your voice heard, rather than taking the easy way out.

---

### Post by aysiu on 2007-05-16
> **oilchangeguy said:**
> "And only your experience matters?"

yes it matters. just as does every users. Maybe you missed the word *only* in my sentence. > you've said that improper command line usage, and problems caused by automatix have caused system problems. so why don't we just stick with the facts, and not single out one thing. I agree fully with this statement. Why are you being argumentative about it? I haven't singled out Automatix. > and yes most computer users just want things to work out of the box without having to jump thru hoops to get it done. Then they should use Synaptic instead of jumping through the hoop of installing Automatix. > when's the last time you used a command line in windows to get anything done? Here's a better question: when was the last time I was forced to use the command-line in Ubuntu v. the last time I *chose* to use the command-line in Ubuntu? In case you're curious, though, I was forced to use the command-line in Mac OS X just a few days ago to troubleshoot a problem my wife was having with her Powerbook. Are you going to go on a rant about Mac OS X's dependence on the terminal now? 

The truth is that when Windows is screwed, it's screwed, and most users either reinstall Windows themselves, have someone else reinstall Windows for them, or buy a new computer. If the Windows command-line were more useful for recovery purposes, people would use the terminal in Windows more. > the software readily available in linux thru such apps like add/remove, etc. are great. but getting a program you downloaded from some web site to work can be a major hassle.  I don't see how Automatix makes this better, with the exception of Google Earth and a few other apps. But the problem still remains--if Automatix doesn't take care of it for you, then you're left jumping through other hoops. So the criticism you level at Synaptic applies to Automatix as well. Automatix is not a cure-all for software installation woes. > getting some hardware to work in linux can be a major hassle. What does that have to do with the discussion of Automatix? > so to imply all of linux's ills can be solved by using the command line is just not realistic.  And who implied that? Nobody. You're arguing with a straw man you've created, and it's quite entertaining to read. The command-line is the red herring some Automatix advocates resort to in order to make Automatix seem more special than it is. For the vast majority of tasks Automatix does, it's simpler to do those same tasks via Synaptic Package Manager or Add/Remove Programs than to go out of your way to install an extra helper program.

---

### Post by Saphira on 2007-05-16
Ive got a wicked idea - Automatix Team contributes its processes and packages (debs, source, whatever) back into Ubuntu and the MOTU's. Why hasnt this been done yet? I mean if they as a team care about Ubuntu as an OS, maybe they could contribute back to help improve Ubuntu as a whole.

---

### Post by Saphira on 2007-05-16
This is one person's really simple view about Automatix!

[http://youtube.com/watch?v=OioUeNYdCx0](http://youtube.com/watch?v=OioUeNYdCx0)

---

### Post by frodon on 2007-05-16
I think that automated scripts (not only automatix) and the persons who advice them without any explanation, warning or drawback explanation damage the ubuntu reputation creating troubles in the upgrade process when a new ubuntu release comes and this don't help ubuntu at all.

New users who perform an upgrade to a new ubuntu version will just say that ubuntu upgrade process is not reliable or stable whatever the tweaks they performed. I'm one of those against the idea to make easily available and without explanation advanced tweaks that bypath apt and dpkg, making this available in one click without any warning or drawback explanation don't help the user neither ubuntu reputation in the long run.

This is just my opinion an not a thruth by itself, some may have different experience which lead to a different view and i respect that, the goal at the end is not to know who is right but just to think about what is the best for ubuntu and its growth.

---

### Post by oilchangeguy on 2007-05-16
the bottom line is, not every computer user who elects to switch to any linux distro has the desire to learn the command line. don't slam those people, or discourge them by telling them that an automated installer will break their system, because that statement is not correct. because problems caused by improper command line use, or any other installer may damage the os, but not the entire computer. scare tactics should not be employed to promote the use of the command line. rather than being helpful, these statements can cause some users to return to windows. and spread untruths about linux. those that answer questions in the forum should be helpful and point out the possible ill effects of both methods, if they are not done correctly. but in the end assist new users in the way they want to be helped. that will do more to promote the spirit of linux, and the open source movement.

---

### Post by PriceChild on 2007-05-16
> **aysiu said:**
> Then they should use Synaptic instead of jumping through the hoop of installing Automatix.Have you seen Add/Remove lately? Lovely! :)

---

### Post by aysiu on 2007-05-16
> **oilchangeguy said:**
> the bottom line is, not every computer user who elects to switch to any linux distro has the desire to learn the command line. No, the bottom line is that the command-line and Automatix are not the only ways to install software. Synaptic and Add/Remove are great point-and-click ways to install programs (Java, Flash, MP3 playback, etc.) and do not require you to visit a website and install an extra piece of software.

---

### Post by kittyhawk63 on 2007-05-16
Please, last person...turn out the lights.

---

### Post by John.Michael.Kane on 2007-05-16
> **kittyhawk63 said:**
> Please, last person...turn out the lights.

As requested lights out.

---

