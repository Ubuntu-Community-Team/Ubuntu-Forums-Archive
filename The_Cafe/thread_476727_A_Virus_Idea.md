---
title: "A Virus Idea"
date: 2007-06-17
forum: The Cafe
---

### Post by mthakur2006 on 2007-06-17
Right...tell me if that is not possible.

.deb files are like .exe files in windows aren't they? When you double-click on one, you surely do get asked for your root password. So, if someone made a malware .deb file which had a code to delete all your hard disk and sent it to you in email, when you install it, won't that damage your system?

tell me i am wrong, or i am already scared with this possibility, honestly.
please point out a fault in this.

---

### Post by floke on 2007-06-17
Of course it could. If you give it your root password it can do anything.
That's why you should only install software from sources you can trust.
If you give out the root password then anything can happen.

---

### Post by mthakur2006 on 2007-06-17
well then ubuntu is no better than windows is it? 
there is a way round it though, is it possible to allow the app access to parts of the system it needs and not the whole system. OR, is it possible to have two extra users - one which can read root files but cannot append them, but can create new files in the required folder and the second one is the superuser which can do anything.
a three-level security instead of the two level we have now?

---

### Post by Feba on 2007-06-17
Ubuntu is much better. Programs can run easily in windows without any user interaction. 

> there is a way round it though, is it possible to allow the app access to parts of the system it needs and not the whole system.This would basically be your user account. Just compile the source on your /home/ partition.

---

### Post by earobinson on 2007-06-17
> **mthakur2006 said:**
> Right...tell me if that is not possible.

.deb files are like .exe files in windows aren't they? When you double-click on one, you surely do get asked for your root password. So, if someone made a malware .deb file which had a code to delete all your hard disk and sent it to you in email, when you install it, won't that damage your system?

tell me i am wrong, or i am already scared with this possibility, honestly.
please point out a fault in this.
Yes this could be done, but all the programs that are in the repos (unless you added your own) are certified by the ubuntu MOTU (they compile all the programs so they could add any code they want) But yes installing unsigned debs from an untrusted source is a bad idea.

---

### Post by floke on 2007-06-17
> **mthakur2006 said:**
> well then ubuntu is no better than windows is it? 
there is a way round it though, is it possible to allow the app access to parts of the system it needs and not the whole system. OR, is it possible to have two extra users - one which can read root files but cannot append them, but can create new files in the required folder and the second one is the superuser which can do anything.
a three-level security instead of the two level we have now?

Its faaaaar better than Windows. Windows doesn't even ask you for, or need, a password. To claim that, if you run as root in Linux (which is effectively what you are doing if you install software with your password) then it is just as insecure as windows is insane. what if I download something or trawl the web etc. and don't use my password - the worst that can happen is my /home files get trashed - not the system. Really, Linux can't protect you from yourself. It's a bit like saying, 'Well if I get out this sledgehammer and whack my PC really hard it will break. Dammit! that makes it just as rubbish as Windows'. You have the choice whether to use your root password or not; so use it wisely - you administer for, and must take responsibility for, your own system. As long as you stick to the official repositories then you're all checked out and fine - about a zillion times better than Windows.

Plus, the Linux architecture makes it far more secure than Win - lets say you do get a virus (there are only around 40 for Linux, and none in the wild, so you'd have to go out of your way) - this trashes /home - but can't touch system apps - thus protecting the system and making it far harder for the virus to propagate. since it can't propagate - it dies out. End of.

As for your suggestions, I don't think it would make any difference - eg I install a new app that can't change system files but can create new ones - so it just creates a new file instructing the OS to pass on your credit card details or whatever to a third party. How is that any more secure?

---

### Post by mthakur2006 on 2007-06-17
>  is it possible to have two extra users - one which can read root files but cannot append them, but can create new files in the required folder and the second one is the superuser which can do anything.
a three-level security instead of the two level we have now? 

what about this?

---

### Post by floke on 2007-06-17
Plus you can see exactly what is running on your system at any one time by opening up a terminal and typing 'top'. Now try doing *that* on Windows!

---

### Post by starcraft.man on 2007-06-17
> **mthakur2006 said:**
> well then ubuntu is no better than windows is it? 

The repositories (the main official ones) are maintained by a trusted team and everything put on them is vetted for both stability and quality (no viruses will make it). 

By your logic, I could write (if I knew the language, I don't) an installer and hand it to a Mac user and tell him to install it and then cripple his computer, that doesn't mean his system is insecure I actively targeted it and he gave it full power over modifying his system. You have to be careful with what you install, the repositories however provide a secure (secure enough at least to me) means for disseminating software to the masses, especially with the gpg authentication.

> there is a way round it though, is it possible to allow the app access to parts of the system it needs and not the whole system. OR, is it possible to have two extra users - one which can read root files but cannot append them, but can create new files in the required folder and the second one is the superuser which can do anything.
a three-level security instead of the two level we have now?

Completely unecessary, you the user have to be sure that repos you add/debs you download are from _**TRUSTED**_ sources. Getdeb for instance or the wine repos is a trusted source. Joe56.com is not a trusted source. There will always be a degree of onus on the end user, you have to be sure you know what your doing.

---

### Post by floke on 2007-06-17
> **mthakur2006 said:**
> what about this?

That's what I was on about - a malware app simply makes its malware in a new file. How is that any different?

---

### Post by Adamant1988 on 2007-06-17
> **Feba said:**
> **Ubuntu is much better. Programs can run easily in windows without any user interaction. **

This would basically be your user account. Just compile the source on your /home/ partition.

Thanks to UAC this is no longer true.   As acceptance arrives, so will malware.  I'm willing to bet that writing a virus for Windows Vista is no more difficult than writing a 'virus' for Ubuntu now.   Multi-user design can only do so much, the systems themselves are secure, it is the human element that introduces insecurity.   The only design difference that makes Linux more secure is the idea of repositories to house the software.   But yes, malicious software is definitely possible.

---

### Post by Feba on 2007-06-17
> Thanks to UAC this is no longer true.Only partially. For one, only 3-5% of windows desktops run Vista. Secondly, UAC only requires a user to press "YES" last I checked, and it is so over used that most users will approve it or even disable it due to the annoyance. Heck, a good number of programs won't run with UAC enabled, which forces users to turn it off. Thirdly, it's far more likely a virus writer will find a hole in windows than in linux, due to the nature of open source software. Fourthly, and it is somewhat becoming less true every day by a small degree, but linux users are , quite frankly, more likely to be knowledgeable about how to use their computers safely. They are less likely to open random emails, download random attachments, or run random executables.  This makes it that much harder to distribute a virus on linux. 

I'm not saying it's impossible to write a virus for linux, just that it's far more likely to happen to you on windows.

---

### Post by floke on 2007-06-17
You forgot to add the sheer variety of distros - many doing things slightly differently - makes it harder for viruses etc. to transmit through the distro population.

---

### Post by starcraft.man on 2007-06-17
> **Adamant1988 said:**
> Thanks to UAC this is no longer true.   As acceptance arrives, so will malware.  I'm willing to bet that writing a virus for Windows Vista is no more difficult than writing a 'virus' for Ubuntu now.   Multi-user design can only do so much, the systems themselves are secure, it is the human element that introduces insecurity.   The only design difference that makes Linux more secure is the idea of repositories to house the software.   But yes, malicious software is definitely possible.

Your right. The bottom line however from what I've seen is that Vista is still more insecure. Most users (I'd say its a nice sampling of average users) I know (at least 100 Vista folk, likely more) have turned off UAC entirely. That makes them maybe even less secure than XP, or more likely equally secure as XP. The reason they did this is because for more than a decade, Windows/Microsoft (the users picked up the belief/trait from them) has been about convenience _OVER_ security. It was always a second after thought to MS it seems to me looking back now (I've been with em since DOS). UAC is a really late patch to fix the glaring problem.

Su and sudo (from all I've read, I am admittedly new) were there all along, and their user base has learned (like me) to cope and use the system for security. Thusly they both have a secure platform, and make it secure through their behaviour.

Thats the difference, and in the end it doesn't matter how secure the actual platform is, if the majority of users turn off all the features (and ignore prompts) because their used to it being convenient then its an insecure and dangerous OS (likely be hijacked, like the rest of the spam bots). Thats the bottom line I think.

---

### Post by starcraft.man on 2007-06-17
> **Feba said:**
> Only partially. For one, only 3-5% of windows desktops run Vista. Secondly, UAC only requires a user to press "YES" last I checked, and it is so over used that most users will approve it or even disable it due to the annoyance. **Heck, a good number of programs won't run with UAC enabled, which forces users to turn it off.** Thirdly, it's far more likely a virus writer will find a hole in windows than in linux, due to the nature of open source software. Fourthly, and it is somewhat becoming less true every day by a small degree, but linux users are , quite frankly, more likely to be knowledgeable about how to use their computers safely. They are less likely to open random emails, download random attachments, or run random executables.  This makes it that much harder to distribute a virus on linux. 

I'm not saying it's impossible to write a virus for linux, just that it's far more likely to happen to you on windows.

I forgot about that one in bold, its true a LOT of programs have trouble without administrator access, and if they aren't gonna get new coded versions from their companies your stuck turning it off/giving them admin access. Where as of course, Linux programs have been designed to run with limited access for the most part (a few are root programs cuz they of course monitor and modify root systems).

One thing though, UAC requires your password if your logged in as a regular user. If your logged in as administrator you gave your password to log in (assuming you have one, some users I know don't even use a password...), thus it does just prompt for a yes or no.

---

### Post by Adamant1988 on 2007-06-17
> **Feba said:**
> Only partially. For one, only 3-5% of windows desktops run Vista. Secondly, UAC only requires a user to press "YES" last I checked, and it is so over used that most users will approve it or even disable it due to the annoyance. Heck, a good number of programs won't run with UAC enabled, which forces users to turn it off. Thirdly, it's far more likely a virus writer will find a hole in windows than in linux, due to the nature of open source software. Fourthly, and it is somewhat becoming less true every day by a small degree, but linux users are , quite frankly, more likely to be knowledgeable about how to use their computers safely. They are less likely to open random emails, download random attachments, or run random executables.  This makes it that much harder to distribute a virus on linux. 

I'm not saying it's impossible to write a virus for linux, just that it's far more likely to happen to you on windows.

Eh, I can type my password in so quickly that it would probably be slower for me to use a 'yes' key anyway.  Sudo is not any more security than UAC, really.   Once it's adopted completely in Windows and refined to be about as bothersome as sudo, it'll be a major security boon, right now it's just poorly implemented. 

Oh, absolutely, Linux users are a minority, and the majority of our minority are highly intelligent people.  Many users are coders because the free notion of software appeals to them and it's good to cut their teeth on, so really you get a more technically inclined demographic running on Linux anyway. 

Like I said though, you can develop the most secure operating system in the world and within days human error will have exposed several potential vulnerabilities.   But my point stands... UAC makes the system more secure, it's when the human using it bypasses the security without thinking that problems arise.

---

### Post by Adamant1988 on 2007-06-17
> **Steve.K said:**
> You forgot to add the sheer variety of distros - many doing things slightly differently - makes it harder for viruses etc. to transmit through the distro population.

This won't be a problem in the future.  There are already certain distributions that would make FAR more attractive targets than others.

---

### Post by floke on 2007-06-17
Yours would be one of them ;)

---

### Post by Feba on 2007-06-17
> Eh, I can type my password in so quickly that it would probably be slower for me to use a 'yes' key anyway. Sudo is not any more security than UAC, really.

Again, you're thinking from a purely system standpoint. The average user is FAR more likely to click yet another "Do you accept/approve/etc..." window "YES" without actually reading it than they are to type in their password, and a user is also far more likely to pay attention to sudo than UAC. It has been PROVEN that more dialog boxes, such as UAC has, are actually LESS secure, as the user starts to ignore them.

---

### Post by forrestcupp on 2007-06-17
> **Steve.K said:**
> Plus you can see exactly what is running on your system at any one time by opening up a terminal and typing 'top'. Now try doing *that* on Windows!

You haven't used Windows in a long time, have you?  If you press ctrl-alt-del in Windows it brings up the system resources where you can see everything that is currently running, and shut them each down if you want.

---

### Post by Adamant1988 on 2007-06-17
> **Steve.K said:**
> Yours would be one of them ;)

You mean Ubuntu?  That's what I use. 

> Again, you're thinking from a purely system standpoint. The average user is FAR more likely to click yet another "Do you accept/approve/etc..." window "YES" without actually reading it than they are to type in their password, and a user is also far more likely to pay attention to sudo than UAC. It has been PROVEN that more dialog boxes, such as UAC has, are actually LESS secure, as the user starts to ignore them.


Well of course I'm thinking from a system standpoint.  Yes, I understand that users will eventually just start clicking 'Yes', but as it's been said earlier unless you are an Admin it will ask for the password.

---

### Post by floke on 2007-06-17
> **forrestcupp said:**
> You haven't used Windows in a long time, have you?  If you press ctrl-alt-del in Windows it brings up the system resources where you can see everything that is currently running, and shut them each down if you want.

Nope :guitar::guitar:

And I thought ctrl-alt-del shut the system down :tongue:

Oh well, who cares what Windows does anyway?

(btw: it can't do acpi -t)

---

### Post by Feba on 2007-06-17
except that most viruses won't allow you to close their processes.

---

### Post by Adamant1988 on 2007-06-17
I'm actually waiting for 100% user-proof software to be built into Windows that just resets it to a certain configuration after restart.  Most businesses I know just set up their computers how they want them, if a problem arises, 'reboot' and any changed files are gone

---

### Post by butlershouse on 2007-06-17
The difference: 

okay hereis my experienced starter for 10 

1. It cannot propagate into another machines root accounts without user intervention.

2. there are far fewer API calls which link the operating system to core applications and as such its harder for a virus to locate and create a outbound call list for accessing emails and other machines.

3. Diversity of machine builds and requirements mean that one machine is very much unlike another in most server/desktop builds which means again that your not likely to be able to utilise the same libraries on each machine

4. Its going to be close to impossible for a virus to spread itself via email since the user will not likely have root access to the box or the domain.

5. Email and web clients in linux are not a integral part of the operating system and as a result do not have the same privileges and options as their windows counterparts which means the user cannot be infected just by reading the email.

6. Spreading as a worm or a trojan are far harder since all of the above


I commend you on your forward thinking, yes if the user chooses to be infected or run code they dont understand then they will be infected however its requires such a large user commitment that the enablement to deliver would be outpaced by the warnings and the updates the net result the virus would not be able to promulgate across a domain with any veracity. 



Bear in mind that there have been thousands upon thousand of linux machines available to attack every day for the last 10 years on the internet. If  a virus writer was seeking to make a name for themselves they would do no better than take on the real machines which run the net and drive commerce. They havent succeeded to date unlike Melissa which hit so many Windows servers it was a joke.  

If your belief is true then where are the viruses which match in number those for windows machines ?  Its a different architecture built on a predisposition for network access which defines its very security and as a result makes it hardier against viral contagions.

---

### Post by butlershouse on 2007-06-17
> **Adamant1988 said:**
> I'm actually waiting for 100% user-proof software to be built into Windows that just resets it to a certain configuration after restart.  Most businesses I know just set up their computers how they want them, if a problem arises, 'reboot' and any changed files are gone

Actually you can script windows system restore to do exactly this. 

Or you can use Terminal Services or Citrix to achieve the result metaphorically.

---

### Post by FuturePilot on 2007-06-17
No OS is safe if the user doesn't use common sense.

---

### Post by Afoot on 2007-06-17
If someone gets the key to your house, it's likely that it could be broken in to. But you don't give out your key now do you? Well, Windows doesn't even lock the house... that's a big difference.

---

### Post by nalmeth on 2007-06-17
>  a three-level security instead of the two level we have now?
Doesn't make much of a difference, because there is still a root user, and the malware needs only to trick the user into giving up the password.

Also, I disagree that the sheer amount of distros makes a huge difference. Kernel vulnerabilities have a sweeping effect over large numbers of distros. 

Nvidia's binary driver had a vulnerability that could be expoited through a website (running as normal user), to run arbitrary code as root.
[http://news.com.com/2100-1002_3-6126846.html](http://news.com.com/2100-1002_3-6126846.html)

That issue has more to do with Nvidia's Linux development issues, but an example  of a serious exploit opportunity.

---

### Post by forrestcupp on 2007-06-17
> **butlershouse said:**
> 
If your belief is true then where are the viruses which match in number those for windows machines ?  Its a different architecture built on a predisposition for network access which defines its very security and as a result makes it hardier against viral contagions.

If your response is to the OP, I think he was just saying it's possible.  I believe that the claim that "you can't get a virus in Linux" is over hyped.

> **FuturePilot said:**
> No OS is safe if the user doesn't use common sense.
While the original post is highly unlikely, it is a legitimate concern.  Say I download a deb package that I thought was a desktop publisher software, but it was actually malicious code that uses my administrative rights to erase my hard drive.  It wouldn't be a lack of common sense to try to install something that I think is a desktop publishing software.

Let's be honest with ourselves here.  There are so many software packages out there that it is impossible to know whether or not every one is from a reliable source.

---

### Post by Feba on 2007-06-17
> I believe that the claim that "you can't get a virus in Linux" is over hyped.Not really. As of right now, I'm only aware of one virus that is actively affecting linux, and that's due to a hole in OOo, not linux itself. And that STILL requires the user to allow OOo to run macros.

>   It wouldn't be a lack of common sense to try to install something that I think is a desktop publishing software.From an untrusted source, yes, it would.

> Well, Windows doesn't even lock the house... that's a big difference.
And with UAC, you have to pick between locking every room in the house, or not locking any.

I think a more appropriate analogy is a tool shed. With Linux, you use one key to open your tool shed and get to work. With Windows (-XP), the tool shed is either left unlocked, or you have to drive to your friend's house and use his toolshed every time you want to get at your stuff. With Vista, the tool shed is locked... but there's also a key to get to every appliance, get to the gas, and to turn the damned things on- to the point where you wouldn't notice if you're turning on the lawnmower with your foot under it. Or, you have to toss out all your keys anyway, and leave it for anyone around to get into. Oh, and some older tools force you to leave all the locks off anyway.

---

### Post by init1 on 2007-06-17
> **mthakur2006 said:**
> what about this?
Yes, you can have many users, each with different abilities. The sudo command gives users root like powers, as defined in the sudoers file. So if I make an other user, then I can do anything I want as long as I use sudo and the sudoers file says that sudo for me gives me root powers.

---

### Post by SoulinEther on 2007-06-17
Ideally, the package manager or package installer should present to you what it is going to do first, and then you give it consent to do so.

As far as I know, most command-line-driven programs like dpkg or apt-get have a "simulation" mode, where it just goes through the steps.... that's not bad, but I'm not sure if it is good enough.

Here's a thought: for managing emails and browsing the web, create another user with limited privileges. Allow your main account to access the files of the alt account, but not vice versa. To run your email client, go to your terminal, use su "subaccount name here" (is there a GUI for this? gksu isn't, right?) and log onto your sub account, and run your email client and internet browser.

---

### Post by Nekiruhs on 2007-06-17
> **SoulinEther said:**
> Ideally, the package manager or package installer should present to you what it is going to do first, and then you give it consent to do so.

As far as I know, most command-line-driven programs like dpkg or apt-get have a "simulation" mode, where it just goes through the steps.... that's not bad, but I'm not sure if it is good enough.

Here's a thought: for managing emails and browsing the web, create another user with limited privileges. Allow your main account to access the files of the alt account, but not vice versa. To run your email client, go to your terminal, use su "subaccount name here" (is there a GUI for this? gksu isn't, right?) and log onto your sub account, and run your email client and internet browser.
Yeah, 
```
gksudo subaccount evolution
```

---

### Post by init1 on 2007-06-17
> **mthakur2006 said:**
> Right...tell me if that is not possible.

.deb files are like .exe files in windows aren't they? When you double-click on one, you surely do get asked for your root password. So, if someone made a malware .deb file which had a code to delete all your hard disk and sent it to you in email, when you install it, won't that damage your system?

tell me i am wrong, or i am already scared with this possibility, honestly.
please point out a fault in this.
With a deb file, it installs files into your system. I don't think it could run a program, but I could still cause lots of trouble. If it replaced files like libc.so.6 or the sleep command, then you computer would crash. So yes, it is posible to get malware from debs, but it is rare.

---

### Post by SoulinEther on 2007-06-17
It's not the human element to blame at all. The automation of processes, however, is.

Arch Linux has something. While I might be oversimplifying and perhaps misunderstanding, you have to do everything yourself. You KNOW what you're doing. As long as you KNOW what your OS is doing, what your installing, what your program is doing, etc., you CAN'T let it do anything you don't want it to do, unless you overlook something.

Yes, overlooking is the human element, but... there's a difference between not paying attention and trusting in your package manager to do the work for you. One, you had the chance to stop it, the other, you had no chance whatsoever.

---

