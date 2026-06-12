---
title: "Special Dansguardian Password, etc, HELP!"
date: 2007-02-08
forum: Ubuntu Christian Edition
---

### Post by Cyclops_ on 2007-02-08
Hi all... I really need some help, and I am in an interesting situation.

Firstly, I am a developer, and I have and would like almost unrestricted access to my machine (at home).  I am also becoming conversant with linux (from an administrator / developer perspective).  So I understand how things work to an extent.  This is both fortunate and unfortunate.  Fortunate in that I know how to configure things and work with things... or can at least look it up.

Where it is unfortunate is my problem.  I am a recovering p0rn0graphy addict... and I am trying everything I can to get away from it.  So herein lies the problem: the internet.  I am almost like to get rid of it -- shut it off, but I need it for the consulting work that I am doing... and of course it is very nice for my wife or I to do bills, look stuff up, download updates to the computer, etc etc.

That is why I was soooo excited for Ubuntu CE.

And for a while, it has worked.  I don't know much if anything about iptables and fireHOL and very little about DansGuardian... (unfortunately I know where log files and configuration files are kept, since I spent some time trying to get it to work, myself).

However, I would really like to be a sudoer on my own machine without having to worry as much about the problem.  And that's where DansGuardian has been helping.

But there are 2 problems with it.

The first is that I can make modifications to DansGuardian.  Let's take the GUI first.  Is there a way that we can have a Special Password created (implemented) for just the GUI so that I as a super user cannot access it, but my wife can?  I need not to be able to get in without her.

Then there are the log files and config files.  How can I deny myself access to those while still being a super user?  How about encryption with a password?  Any ideas?

The other issue is that I have installed IEs4Linux.  Somehow it completely averts the parental controls altogether.  I can go anywhere I want by using it without accountability or restriction.  Arg!  I have already messed up with it. 

The same thing applies with QEMU.  Does it also go around the restrictions and guidelines?  The browser within the VM ignores the controls.  I thought that everything was forced to walk through the shadow proxy?

Please help, all ... cuz I don't know what to do.  I don't want to mess up and lose my family.

Thank you for all you have been doing with this OS.  It is a good work I believe in.

Sincerely,

Michael

---

### Post by Cyclops_ on 2007-02-08
Oh... and is there anything that I could possibly do about the root "fixer" login?  Anyone can log into my machine, not have to supply a password, and do anything they want to it using that login. (Meaning, mainly, myself.)

---

### Post by mhancoc7 on 2007-02-08
Hi Michael,
Thanks for your interest in Ubuntu CE.

Your ideas and suggestions are good ones and have been discussed a bit before. I have not been able to find a way to create a special password for the GUI and even if it did have a special password the superuser (you) could still edit the Dansguardian files manually.

Yes, running IEs4Linux will bypass the filter as well as running a browser in a virtual machine. There are other ways around, but I do not want to give them up for those who don't know.

The fact is that the filter is not a perfect solution.

I hope to be able to implement an "Accountabilty" feature in a future release. This would not be perfect either, but it would help. I have already successfully setup a system which would allow a superuser to setup the GUI to send an email every week to an accountability partner. Now this can easily be disabled, however it would send the accountability partner an email informing them that the feature had been turned off. Now this also can be worked around if you are the superuser.

In short, I can't see a way to keep a superuser from getting around the filter. The only way to truly lock it down is to create a user account for anyone that needs the filter enabled. You would also have to setup the computer to not boot from CD. Then setup a BIOS password. That way users can't use LiveCDs to get around the filter.

Anyway, I have probably just told you what you already know. 

God Bless, Jereme

---

### Post by Cyclops_ on 2007-02-08
What about a password Built_In to the GUI.  Managed by the GUI in a special, non-text file in an obfuscated location?

As far as accountability... what about having the URLS to ALL domains accessed from ANY program stored in a special encrypted file?  It wouldn't be able to be tampered with if you don't have or know the encryption (or file location for that matter) and if the file were deleted, it would know because there is certain stuff stored in the file that can't just be recreated... and then it would send an email.

I just really need something that I can't currently get past and have no desire to find a way to work around.  The strength needs to lie in the strategy... (or algorithm, or encryption)...

What do you think?

---

### Post by mysticrider92 on 2007-02-08
There are ways to password protect files, so you could do that to all of the Dansguardian config files, in addition to needing to be root, but on Linux, it is usually encryption and may not be usable for configuration files. The problem with most of this is (as you pointed out) that the root account on Linux is truly the root account, it has access to *everything*. The problem with a password in the GUI would be the same as the configuration files, it needs to be stored somewhere, and that would be easily visible to the root user. 

Another possible way would be to find a way to block sites with hardware, so you can't get past it on the computer at all (maybe a router configuration).

---

### Post by Cyclops_ on 2007-02-09
Right... what I was kind of thinking for the GUI password storage was making it non-plain text... like use some sort of your own algorithm to encrypt / obfuscate it ... or even a one way hash, like an MD5 or a SHA1 (or higher)... maybe a combination of the two... and add a salt to the end of the user's password before encryption.

You would then simply take the user's input upon entry into the GUI, add the salt, encrypt it using MD5 or SHA1 and check it against what you have stored.  Then it wouldn't matter if anyone knew where the password were stored... it wouldn't be in plain text and a WHOLE LOT harder to decode.

Is there anything you can see wrong with that?

Adding a password in this manner which you could ask for any time would make it so that, even if the user had the root password, the ONLY way into the GUI would be through that encrypted password...

And then we would have to come up with some strategy for the config files.

I do like the idea of the hardware block.  My wife actually suggested it to me today... and I think that it is a very good and viable solution.  So I will at least implement that.

Thanks,

Michael

PS... let me know if there is anything that I can do to help in the development.

---

### Post by mhancoc7 on 2007-02-09
Those sound like great ideas, but a bit over my head I am afraid. :)

If anyone has any ideas of how to accomplish some of this I would love to give it a go.

God Bless, Jereme

---

### Post by mysticrider92 on 2007-02-09
The encrypted password is a good idea, but I have no idea how to do that at this point. I'm still fairly new to programming (learning is a bit slow), and have never done something like that.

I can't think of any way to hide the config files, unless you were to block access to the folder in the same way as the GUI.

---

### Post by montgoej on 2007-02-09
What about say something run by Cron that would encrypt, sign and email the log files somewhere say once an hour or so?  That may be feasible if GPG was setup correctly, but I dunno.
~Jordan Montgomery

---

### Post by Cyclops_ on 2007-02-11
So, is there something we can do for IEs4Linux or QEMU?  I would really like to keep them, since I do Web Development contracting, but would like to be protected.

Any ideas?

---

### Post by RyanGT on 2007-03-02
Cy,

I share your questions, concerns, and challenges.  I am new to parental controls in Ubuntu, so this may be off but I have two thoughts about the technical side of your question:

1.  Can you do your day-to-day job without being root or a sudoer?  Can you give yourself permission to do everything that you need as a regular user?

or

2.  Can you setup a server running dansguardian (possibly without a gui interface and eventually with the monitor disconnected) that runs a firewall/proxy/dansguardian/... where you don't have an account and don't know the root password?  I don't think this would have to be a fancy computer.

On the spiritual side, I am working through an internet Bible study called the Way of Purity from settingcaptivesfree.com.  I recommend it.  It is a 60 day course that includes a mentor/accountability partner over email.

Ryan

---

### Post by kingdomworker on 2007-03-04
I think we hit a good point here and that is all of us need to protect ourselves well we are doing what we love. One thing I found with the new version of Dansguardian is that fact that you can turn it off by clicking one button and enter the root password. I love all the work you have done to it Jeremy and it is really easy to set up now but being able to turn it off? Why bother installing it? We all need to protect our selves so I would ask that the next upgrade of Dansguardian would do away with this one button! I would keep the one for unlocking Firefox proxy for some of us can't even get Firefox to work unless we do so. I do under stand that by unlocking the proxy there is away around Dansguardian but most users would not be able to figure this out. So I urge you to take a look at this idea when you upgrade Dansguardian.:)

---

### Post by mhancoc7 on 2007-03-04
> **kingdomworker said:**
> I think we hit a good point here and that is all of us need to protect ourselves well we are doing what we love. One thing I found with the new version of Dansguardian is that fact that you can turn it off by clicking one button and enter the root password. I love all the work you have done to it Jeremy and it is really easy to set up now but being able to turn it off? Why bother installing it? We all need to protect our selves so I would ask that the next upgrade of Dansguardian would do away with this one button! I would keep the one for unlocking Firefox proxy for some of us can't even get Firefox to work unless we do so. I do under stand that by unlocking the proxy there is away around Dansguardian but most users would not be able to figure this out. So I urge you to take a look at this idea when you upgrade Dansguardian.:)

I completely understand your perspective. Believe me when I say that I have thought a lot about this. I wanted to find a balance between filtering and control. The intention of the web content filtering was mainly for parents to keep there kids safe. That is why I named them Parental Controls. I understand that we all need to keep ourselves pure on the web. However, no matter how much I lock it down the root user can always get around it. The current setup allows the root user to enable/disable. If a person feels that they need the extra help in protecting themselves then I always suggest that they let someone else (ie spouse) setup the root password and then give yourself a user account. This way you will not be able to get around the filtering. This , however, means that you will not be able to do a lot of the things that we all as Linux users are used to.

As you can see it is a complicated matter of trying to get the right arrangement for everyone. There will always be some that are not happy with the way it is setup, but I believe the current setup is the best that can be done currently for all.

God Bless, Jereme

---

### Post by kingdomworker on 2007-03-04
Yes, Jeremy I think your right we need to be able to use root as root and have full control of our systems under that user. Dansguardian dose a great job at what it was made for. I think what were talking about here is more about a 'Internet Accountability' program problem, i.e. not having one, then a problem with Dansguardian which is doing a great job at what it was meant to do. Since I already know that you have been trying to get a Internet Accountability program working I won't ask if anyone has tried to get one to work but ask what can I do to help with it? This is important for all of us for I have seen way to many friends and workers fight Internet pron problems. Thanks Jeremy for putting Dansgaurdian in Ubuntu CE for it is a big step to help these people and all of us with this plague, great job!:)

---

### Post by mhancoc7 on 2007-03-04
> **kingdomworker said:**
> Yes, Jeremy I think your right we need to be able to use root as root and have full control of our systems under that user. Dansguardian dose a great job at what it was made for. I think what were talking about here is more about a 'Internet Accountability' program problem, i.e. not having one, then a problem with Dansguardian which is doing a great job at what it was meant to do. Since I already know that you have been trying to get a Internet Accountability program working I won't ask if anyone has tried to get one to work but ask what can I do to help with it? This is important for all of us for I have seen way to many friends and workers fight Internet pron problems. Thanks Jeremy for putting Dansgaurdian in Ubuntu CE for it is a big step to help these people and all of us with this plague, great job!:)

Yes, I would really love to get an accountability program working. I already have an idea of how to implement it. The only problem is setting up the system to send emails via a script. They tend to get blocked as spam.
Jereme

---

### Post by kingdomworker on 2007-03-05
Well I think I have a couple ideas around the Spam thing Jereme. I was able to email out from Pine to my own email server. But I could not get it through to my Hotmail account? The first thing that came to mind was what if we and our accountability people all used email accounts from a server we new would work. What is we used whatwouldjesusdownload email accounts for this. I know that this is not the best answer but it maybe the easiest and fast way to get something up and running. That is if you can get the  whatwouldjesusdownload server to work with scrip emails? A lot of people would rather not have all the that stuff emailed to their POP account anyways. So having a place that they could just go check there accountability partners log with out filling up their everyday email would be a big plus! Just a simple idea , not sure if it would fly our not. For you would have to integrate a email sign up with the the installer?

---

### Post by xilix on 2007-03-06
Sounds very good. Good idea. Perhaps you could make it optional for those people who can not/don't want to use their own email-address.
icicle

---

### Post by jpuhalski on 2007-07-16
hi all,

this has been an issue of concern for me as well.  Looks like from what i've been reading here the separate password for Dansguardian is not going to be a good option.  I like the idea of an accountabiltiy partner that gets an email of sites visited.  Can you point me in the right direction for doing this?  I see the last post here was from March and i'm now running Ubuntu CE v3.2 which came out in June. 

thanks
john

---

### Post by Cryophallion on 2007-08-21
I am loathe to start a new thread on this topic, but I thought it might be a good idea to get a list of links in one place to see if we all can work together to get something working here.

Based on all these threads, and another site that I found about a week ago, I think there is a way to get something working for us. I just don't have the knowledge to put it all together. 

Here is my thought. First of all, replace tinyproxy with squid.

Then, configure dansguardian using the methods here:
[www.linux.com/articles/113733](www.linux.com/articles/113733)

I am sure you could set up firehol similar to the shoewall config listed, once agian I just don't know how.

Next. set up squid to report to accountability partners as shown here:
[http://www.internetsafety.com/faq/question.php?id=73](http://www.internetsafety.com/faq/question.php?id=73)

Finally, set up mstmp to do the mailing:
[http://msmtp.sourceforge.net/](http://msmtp.sourceforge.net/)

Either that, or we set up a relay server (that would still require a login, but at least that would be trusted), or people will just have to tell their partner to unblock the emails as spam.

This whole password thing for root is rough though, but if we give the option on installing the system without the gui (to make it harder to find and turn on, although invariably people will figure out how to get around it, it is a lot more difficult for new users than just clicking off on the dansguardian control panel)

I have also noticed dansguardian, as installed with the CE deb, tends to block out my LAN computers, and there should be an option to enable/disable that.

So, anyone with any ideas on how to put this all together?

UPDATE: As for this whole password or no password for dansguardian situation, how about an OPTIONAL password, that is needed to unlock the controls. It wouldn't affect the other sudo stuff that way. If you want to use it, can select that option. If not, then don't select the option. But at least that way it is an option.

---

### Post by mayliszt on 2009-06-17
Hi Cyclops_,
        I think before you find a solution, you can install a firefox addon ProCon Latte. It allow someone to set a pswd that you cannot see. I have installed it. It is not perfect, but it may help.

        By the way, if you find a solution for DansGuardian, please aslo tell me. I have the same problem as you do.

        May God bless you and protect you!
        Keep having a good fellowship with brothers and sisters. This also helps.

May Liszt

---

### Post by eric.duveau on 2009-06-17
[http://www.mobicip.com/](http://www.mobicip.com/) may bring a solution for you but it is still alpha stage.

So be patient. As for me I have given up to be root. I am just a sudoer user with some extra priviledges that I really need.

---

### Post by pac8612 on 2009-12-21
> **mhancoc7 said:**
> Hi Michael,
Thanks for your interest in Ubuntu CE.

Your ideas and suggestions are good ones and have been discussed a bit before. I have not been able to find a way to create a special password for the GUI and even if it did have a special password the superuser (you) could still edit the Dansguardian files manually.

Yes, running IEs4Linux will bypass the filter as well as running a browser in a virtual machine. There are other ways around, but I do not want to give them up for those who don't know.

The fact is that the filter is not a perfect solution.

I hope to be able to implement an "Accountabilty" feature in a future release. This would not be perfect either, but it would help. I have already successfully setup a system which would allow a superuser to setup the GUI to send an email every week to an accountability partner. Now this can easily be disabled, however it would send the accountability partner an email informing them that the feature had been turned off. Now this also can be worked around if you are the superuser.

In short, I can't see a way to keep a superuser from getting around the filter. The only way to truly lock it down is to create a user account for anyone that needs the filter enabled. You would also have to setup the computer to not boot from CD. Then setup a BIOS password. That way users can't use LiveCDs to get around the filter.

Anyway, I have probably just told you what you already know. 

God Bless, Jereme

You mention the email feature and setting it up. I would like to do this. I found instructions on how to do this with squid as the proxy, but not tinyproxy. Can you help me with these files? I'm still quite new to Linux.

Paul

---

