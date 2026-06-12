---
title: "How did I get attacked?"
date: 2011-04-24
forum: Security
---

### Post by narps on 2011-04-24
I'm running Ubuntu 10.10. I left my computer locked for a few hours in my dorm. When I came back, I was immediately suspicious because my computer was turned off, and I always leave it on. Also my roommate is known for messing with people's computers. I logged back in, and after a bit of searching found a keylogger on my system and a script that would record my password when I used sudo.  I'm just wondering if anyone has any idea how this could happen. I have a good password, and have a BIOS password, and I know that he doesn't know either of them.

---

### Post by msandoy on 2011-04-24
Physical access is almost as good as giving away the password. The BIOS password you mention, does it only prevent access to BIOS, or does it prevent startup of the computer?

If it was possible to switch it off and then on again, and enter the startup menu of Ubuntu, it would be possible to use recovery mode to change the password, and take full control.

---

### Post by mr-woof on 2011-04-24
out of interest, how did you find the script and keylogger?

---

### Post by realzippy on 2011-04-24
> **mr-woof said:**
> out of interest, how did you find the script and keylogger?

..can you post both?

---

### Post by HermanAB on 2011-04-24
Chances are that you played with VNC at some point and that you use a really kewl 4 to 8 character password, which is equivalent to leaving your machine unsecured.

---

### Post by narps on 2011-04-24
> **msandoy said:**
> Physical access is almost as good as giving away the password. The BIOS password you mention, does it only prevent access to BIOS, or does it prevent startup of the computer?

If it was possible to switch it off and then on again, and enter the startup menu of Ubuntu, it would be possible to use recovery mode to change the password, and take full control.

It prevents startup.

[QUOTE=mr-woof]out of interest, how did you find the script and keylogger?[/QUOTE]

I looked at the files modified during the time period I was gone. He told me the purpose of the script and keylogger was to obtain my password, but he wouldn't tell me how he got them on my hard drive because he said I still have a vulnerability that he will exploit again.

[QUOTE=HermanAB]Chances are that you played with VNC at some point and that you use a really kewl 4 to 8 character password, which is equivalent to leaving your machine unsecured.[/QUOTE]

No and no.

---

### Post by kostkon on 2011-04-24
> **narps said:**
> I looked at the files modified during the time period I was gone. He told me the purpose of the script and keylogger was to obtain my password, but he wouldn't tell me how he got them on my hard drive because he said I still have a vulnerability that he will exploit again.
Who? Your roommate??

---

### Post by Rubi1200 on 2011-04-24
> **kostkon said:**
> Who? Your roommate??
Very good question!

@narps; if you really expect us to help you, post the logs, script, and any other relevant hard information so we can take a look at it.

---

### Post by Rubi1200 on 2011-04-24
By the way, and I apologize in advance for being so suspicious but this doesn't make any sense to me:
> after a bit of searching found a keylogger on my system and a script that would record my password when I used sudo.

If he installed a keylogger, then he already knows or knows how to hack your password since to install it would require root privileges. 

Therefore, why would he need to have a script recording your usage of sudo?

---

### Post by Rasa1111 on 2011-04-24
> I looked at the files modified during the time period I was gone. He told me the purpose of the script and keylogger was to obtain my password, but he wouldn't tell me how he got them on my hard drive because he said I still have a vulnerability that he will exploit again.

and you just said "ok"? 

I am a non-violent person..
But if a "friend" or room-mate did that to me..
I would put them to sleep. 

Still,
This thread is kinda........ sketchy...

What's the real deal? 

 Can you not just backup all your files, and do a re-install, just to be safe? 

 "Known for messing with peoples computers"

and he is still getting away with it? 

Not in my world..  Touch my stuff like that without asking Ill eat your fingers off.. then spit them out at ya..   lol 

Strange.....

---

### Post by doas777 on 2011-04-24
> **Rubi1200 said:**
> By the way, and I apologize in advance for being so suspicious but this doesn't make any sense to me:


If he installed a keylogger, then he already knows or knows how to hack your password since to install it would require root privileges. 

Therefore, why would he need to have a script recording your usage of sudo?
this can be done with a liveCD. remember physical access is root access. 
if you boot into a livecd, and mount the drives, you are root. just add the scripts where you want then, and add the script launchers to the rc's. 

@op, if this is the case, put a padlock on your box, if you have a hasp. then diasble boot from anything but sata hdd, and set a bios power on and setup password (you implied that you had one). at least then you can make your roommate answer as to why he felt the need to physically break your property. won't stop a serious attempt, but most folks won't break your hardware for a prank. also, change your passwords, and use one a 4-factor one: [http://www.microsoft.com/security/online-privacy/passwords-create.aspx](http://www.microsoft.com/security/online-privacy/passwords-create.aspx) . these precautions will prevent him from booting from alternate media, altering bios settings, or clearing your existing bios configuration (to get past the passwords and boot media restrictions).  

I'll admit that I too am suspicious of your description, since the tech level to have identified the scripts seems out of synch with the nature of your question, so I wouldn't mind a description of your analysis process, and the contents of any scripts you found.

---

### Post by ChrisWells on 2011-04-24
I have been lurking these forums long before I joined, and noticed the large amount of people with 1 or 2 posts always posting saying they been hacked, or similar, on Ubuntu ofc.
Are these all just Windows trolls trying to make Ubuntu look bad or what?

Edit- you say about the Live CD (true) but he has BIOS password (which his room mate don't know) so not possible unless his room mate was to unplug his drive, put in another PC etc very unlikely in the space of a few hours

---

### Post by realzippy on 2011-04-24
Had an older acer laptop where the harddisc was unplugged in seconds,no screws,just beneath the battery;also -if op has a desktop- resetting CMOS
takes a minute.........but anyway,strange story. :P

---

### Post by Rasa1111 on 2011-04-24
> **ChrisWells said:**
> I have been lurking these forums long before I joined, and noticed the large amount of people with 1 or 2 posts always posting saying they been hacked, or similar, on Ubuntu ofc.
Are these all just Windows trolls trying to make Ubuntu look bad or what?

Edit- you say about the Live CD (true) but he has BIOS password (which his room mate don't know) so not possible unless his room mate was to unplug his drive, put in another PC etc very unlikely in the space of a few hours

I too have the same thoughts sometimes. lol

I'm always amazed when people who supposedly know what theyre doing.. (enough to know theyve been "hacked"), Claim they have been 'hacked'...
Yet I have family members and friends, ages 10 to 70, who know very, very little about computers.. Who have been running nothing but Ubuntu for almost a year... With no "virus protection" no active "firewall" , no knowledge (not much, other than what I tell them)) of how to keep themselves safe, Half of them don't even have the "Password to login" enabled.. 
and they have not been compromised in any way, nor do I foresee it happening. 

 Just regular ex-windows users.. 
Who ALWAYS had problems with their windows.. 
But theyre going on a year using Ubuntu, without a single problem.   lol
But these people who "know what theyre doing" seemingly get "hacked" so often?  lol ... :confused: 

 Just one more thing in this silly world I fail to understand.. :lol:  :rolleyes:

---

### Post by doas777 on 2011-04-24
> **ChrisWells said:**
> I have been lurking these forums long before I joined, and noticed the large amount of people with 1 or 2 posts always posting saying they been hacked, or similar, on Ubuntu ofc.
Are these all just Windows trolls trying to make Ubuntu look bad or what?

Edit- you say about the Live CD (true) but he has BIOS password (which his room mate don't know) so not possible unless his room mate was to unplug his drive, put in another PC etc very unlikely in the space of a few hours

well, most motherboards have a 'clear CMOS' feature somewhere, or you can just pull the watch battery. thats why locking the case is key. the bios passwords (for both poweron and setup) are important, but impossible to secure unless the case is physically locked. in the end, I can clear the cmos of most boxes in 20 minutes or less, and a hdd swap would take about the same amount of time. both indicate that an investment in physical security is essential.  

I agree with you guys, this is likely a non-event. I'm just trying to provide the correct advice for the problem, real or not. 

@op, fulldisk encryption is another answer to this issue, but can be a bit of a trial for a novice to set up:
[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

---

### Post by CandidMan on 2011-04-24
Reading the previous posts that give good practical advice, it's obvious your main concern is this so-called roommate with no respect for the property of others. 

Assuming this person a) is actually responsible and not bluffing b) has the capacity to respect boundaries, could you have a civil discussion with them about this.

I'd broach the point that it's all fun to him/her but they could inadvertently cause a major security breach in your PC with their shenanigans.

Failing that, you might consider asking for a change of roommate if you're in dorms or informing a relevant person of authority. This person might no be so flippant about other people's property when confronted.

---

### Post by Jive Turkey on 2011-04-25
With physical access his roommate probably physically removed the drive and mounted it in a different PC to bypass the BIOS password.  From there he could have done anything he wanted (apparently he didn't bother to change the last-modified times of the files he planted).

If it were me, I would tell him that I will call the police and press charges if he messes with my property again in front of a witness.  Privately, I would make some more serious threats.  Secretly, I would apply a skin staining substance to some key parts of my computer (i.e. methylene blue from an aquarium store).  From there you point to his blue hands and explain to the cops about the stain and the history of tampering.

---

### Post by debd on 2011-04-25
strange **_STORY_**  ;)

---

### Post by tgm4883 on 2011-04-25
If access was gained to the desktop, a script could be installed in the users directory to gain access. It wouldn't need root access at that point.

---

### Post by DodgeV83 on 2011-04-26
There is a simple solution to all of this:

1.  Backup and reinstall Ubuntu.  There is no telling what else he did and it's not difficult to hide the date/time of changed files.

2.  While reinstalling, check the "encrypt home" option.  To be safe you should also look into encrypting the whole drive, as home might not be enough.

---

### Post by hunterkasy on 2011-04-27
I am sorry for being a little of topic. but it ties into it.

Even with local access why is it so easy to gain access to the computer?  I have seen allot of threads on how to change the password without knowing the password

Also if you have your home directory encrypted can someone still easily get into the home dir?  or if someone changes the login password does that change the encryption password on home dir or is home dir still protected?

also if someone would install truecrypt or some other encryption and have it set for a whole (disk?) or a whole partition encryption would that solve the original problem in this thread?

---

### Post by tgm4883 on 2011-04-27
> **hunterkasy said:**
> I am sorry for being a little of topic. but it ties into it.

Even with local access why is it so easy to gain access to the computer?  I have seen allot of threads on how to change the password without knowing the password

Physical access is root access. This is true with any operating system.

> **hunterkasy said:**
> 
Also if you have your home directory encrypted can someone still easily get into the home dir?  or if someone changes the login password does that change the encryption password on home dir or is home dir still protected?

No, changing the user password that way does not change the encryption passkey. If you changed the password that way then you would still need to know the correct encryption passkey to gain access to the partition.

> **hunterkasy said:**
> 
also if someone would install truecrypt or some other encryption and have it set for a whole (disk?) or a whole partition encryption would that solve the original problem in this thread?

Probably. It's unknown how access was gained to the system, so I'd hate to speculate on something like that. For instance, if an exploit was in the lock screen code that could be exploited then the partition would already be decrypted.

---

### Post by 1clue on 2011-04-27
Most of this has already been said, but:
[LIST=1]
[*]There is absolutely no computer I've ever heard of that can keep you entirely out if you have physical access.
[*]An encrypted directory or partition only prevents access if your system is either shut down, or the device is not mounted.  Once you've got it going and the directory is readable, they have access if the system is still running.
[*]If you have an encrypted drive or directory and the key is stored on the drive somewhere, then you'd just as well not have encryption.
[*]There is a reset switch that clears the password on boot feature.  However, the only time I ever used that reset, I changed a couple settings and turned the bios lock back on without setting the password, just to see if it reset the password or just the setting to require its entry on boot.  My original password still worked.  I consider this a bug, but if yours does this that's probably the easiest route in.
[*]Pulling the drive, putting it into another system will also work.
[*]Booting off a livecd or similar is dirt simple, and there's a good chance your BIOS is set to boot off CD anyway.
[*]Most people don't guard their hands from view when they type their passwords absolutely every time, especially with a roommate.  He may have had dozens of times when he could have watched you type it.
[/LIST]

FWIW none of this is news, and none of it is any different than what can happen with absolutely any operating system.  I also find the topic and circumstances fishy, maybe more like fishing for ideas on how to prank a roommate than how they did it.  Doesn't matter, all this information will probably get a thousand hits on Google anyway.

---

### Post by realzippy on 2011-04-27
*I also find the topic and circumstances fishy, maybe more like fishing for ideas on how to prank a roommate than how they did it.*

...exactly.OP will never come back to the forum to show us the "script"
he "found"   :)

---

### Post by doas777 on 2011-04-27
> **hunterkasy said:**
> 
Even with local access why is it so easy to gain access to the computer?  I have seen allot of threads on how to change the password without knowing the password


Short answer: the company that made the device would have a support nightmare on their hands if there was no way to support a legitimate customer who had lost access to a machine for one reason or other. telling the customer to forget about their data and just "buy a new one" is an easy way to accrue bad will, and raise legitimate questions about the long term manageability of the device. in the long run, every device that supports a password requires a mechanism to bypass that password somehow.

---

### Post by tgm4883 on 2011-04-27
> **doas777 said:**
> Short answer: the company that made the device would have a support nightmare on their hands if there was no way to support a legitimate customer who had lost access to a machine for one reason or other. telling the customer to forget about their data and just "buy a new one" is an easy way to accrue bad will, and raise legitimate questions about the long term manageability of the device. in the long run, every device that supports a password requires a mechanism to bypass that password somehow.

This is partially true, but doesn't hold up for encryption. My company has an encryption product and if you forget your password there is no way to get your data back. This is by design and how it should be.

---

### Post by doas777 on 2011-04-27
> **tgm4883 said:**
> This is partially true, but doesn't hold up for encryption. My company has an encryption product and if you forget your password there is no way to get your data back. This is by design and how it should be.
I agree, to an extent. every encryption provider I've worked with has provided some means to ensure that you are not inappropriately locked out of data, but it usually requires some serious administration. for instance, here is the Truecrypt FAQ. [http://www.truecrypt.org/faq](http://www.truecrypt.org/faq)
check out the section entitiled "*We use TrueCrypt in a corporate/enterprise environment. Is there a  way for an administrator to reset a volume password or pre-boot  authentication password when a user forgets it (or loses a keyfile)?*"

Safeboot, a leading FDE provider provides several tools for ensuring access (warning, PDF)
[http://www.gatewaynintec.in/pdf/Safeboot%20Central%20Management.pdf]("http://www.gatewaynintec.in/pdf/Safeboot%20Central%20Management.pdf")

when properly administered, any real encryption provider can ensure that you are never locked out.

---

### Post by tgm4883 on 2011-04-27
> **doas777 said:**
> I agree, to an extent. every encryption provider I've worked with has provided some means to ensure that you are not inappropriately locked out of data, but it usually requires some serious administration. for instance, here is the Truecrypt FAQ. [http://www.truecrypt.org/faq](http://www.truecrypt.org/faq)
check out the section entitiled "*We use TrueCrypt in a corporate/enterprise environment. Is there a  way for an administrator to reset a volume password or pre-boot  authentication password when a user forgets it (or loses a keyfile)?*"

Safeboot, a leading FDE provider provides several tools for ensuring access (warning, PDF)
[http://www.gatewaynintec.in/pdf/Safeboot%20Central%20Management.pdf]("http://www.gatewaynintec.in/pdf/Safeboot%20Central%20Management.pdf")

when properly administered, any real encryption provider can ensure that you are never locked out.

True and False. Basically that is just restoring the original header and password to the encryption volume. There still isn't a backdoor into the system. You aren't bypassing the password, you still have to know the correct password, it's just the header that is restored so you have to know the original password.

---

### Post by doas777 on 2011-04-27
> **tgm4883 said:**
> True and False. Basically that is just restoring the original header and password to the encryption volume. There still isn't a backdoor into the system. You aren't bypassing the password, you still have to know the correct password, it's just the header that is restored so you have to know the original password.

quite right. but remember, we are discussing vendors and providers architecting their systems to provide administrators the ability to ensure that they are never locked out, via whatever mechanism; not the mathematical complexity of bruteforcing cipherdata. the header extraction feature in truecrypt is one of those mechanisms. granted some upfront work is required, but that is true of all admin bypasses. 

that said, look deeper at safeboot and read between the lines. theres something scarier in there that is much more in line with the backdoor you mentioned.

---

### Post by phz_swe on 2011-04-27
It sounds highly unlikely, and either it's pure trolling, a psychotic/extremely immature roommate or someone trying to find out ways to do this to other people.

Maybe you some time left a terminal with the sudo credentials provided and active, then one can do whatever, it's as good as a root shell.

With physical access, one could take out the drive, put it into another computer and install modified sudo binaries without problem. Encrypting your disk could save you against that, or using a sturdy lock on your case, but seriously? What is to hinder your roommate from stealing your pants when you are out? Or sell all your other belongings? Some sense of trust must be present. This is a people problem, not a computer problem.

EDIT: Meh, I'm tired, didn't look past the first page. What I said has already been said in other forms. I leave my version nonetheless.

---

### Post by CoffeeRain on 2011-04-27
I agree that he is probably trying to figure out how to do this to someone else.

---

### Post by amiacamal on 2011-07-08
I realise by now this is an old thread, but im bored at work and wanna throw in my 2Cents... Surely its a bad idea to leave the house for an extended period of time without **switching off the computer?** Just a thought, i realise it doesnt solve anything if the hard drive is just removed....

---

### Post by tgm4883 on 2011-07-08
> **amiacamal said:**
> I realise by now this is an old thread, but im bored at work and wanna throw in my 2Cents... Surely its a bad idea to leave the house for an extended period of time without **switching off the computer?** Just a thought, i realise it doesnt solve anything if the hard drive is just removed....

Why is it a bad idea again?

---

### Post by jmore9 on 2011-07-08
I once used a whole drive encrypter with wn2000 and forgot the login password.  Yea i did not write it down it believed my memory was really good !!!

Long story short i lost everything on the drive because no password no access.  so i don't do that anymore i just back everything up to cd or dvd and lock those up !!

I now do the same thing is linuix also.

---

