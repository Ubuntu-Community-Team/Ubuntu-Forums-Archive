---
title: "password security"
date: 2007-10-24
forum: Server Platforms
---

### Post by InGunsWeTrust on 2007-10-24
I am a Linux fanatic, I like to tell people that security is much better with Linux but sometimes it just isn't true. My major nag about Linux security is password security.

Let us say I had a single desktop with a single local logon. ANYBODY could walk up to that computer and put a live CD in and boot to it and simply open the /etc/shadow file and copy a known password hash in after root and log in as root.

The reason I am posting this though is to see if anybody has any clue how to circumvent this giant security hole.

---

### Post by robert_pectol on 2007-10-24
> **InGunsWeTrust said:**
> I am a Linux fanatic, I like to tell people that security is much better with Linux but sometimes it just isn't true. My major nag about Linux security is password security.

Let us say I had a single desktop with a single local logon. ANYBODY could walk up to that computer and put a live CD in and boot to it and simply open the /etc/shadow file and copy a known password hash in after root and log in as root.

Yep!  And how is this concept unique to Linux?

> **InGunsWeTrust said:**
> The reason I am posting this though is to see if anybody has any clue how to circumvent this giant security hole.

Physical security of the box is not the OS's responsibility!  If you are worried about physical security, put the box behind a locked door.

---

### Post by aysiu on 2007-10-24
If you allow someone to boot a live CD on your computer, the computer's "security" has already been compromised.

---

### Post by InGunsWeTrust on 2007-10-29
Actually, the password file in Windows has apperently been secured in some way because it is at the very least not as easy to do. If users have physical access to a computer it should not automatically mean that security has been compromised.

---

### Post by aysiu on 2007-10-29
> **InGunsWeTrust said:**
> Actually, the password file in Windows has apperently been secured in some way because it is at the very least not as easy to do. If users have physical access to a computer it should not automatically mean that security has been compromised.
Why do you need the password? If you have physical access, you can boot a live CD and get all the files or just take the hard drive itself and get stuff off of it later. Besides, you can reset the Windows password using a Knoppix CD.

---

### Post by InGunsWeTrust on 2007-10-29
I already know the password. I am trying to prevent other people from cracking the password. I have this security specialist friend that I made a bet that I could give him physical access to my PC and he couldn't crack into my Linux partition. This is the only security hole that is still open because I have my single user mode locked out by taking passwd out of the list of programs that can run in single and adding a password to my grub loader now I just need to make sure he can't overwrite my shadow file and I'll win the bet. I could just rearrange the boot order but he can just pull my CMOS battery out and let it reset to default which unfortunately has the CD booting first. The point of securing the password is that with my username and pass he could log onto a network and access network resources. The contents of my harddrive are irrelivent as long as services on my network are still secure.

---

### Post by CSMatt on 2007-10-29
Yeah you're going to lose that bet.  You could encrypt your drive, but I can't think of anything else.

All your friend needs is the hash, John the Ripper, and a lot of time to wait for John to crack the password depending on how strong it is.

---

### Post by scorp123 on 2007-10-29
> **InGunsWeTrust said:**
>  Actually, the password file in Windows has apperently been secured The *content* ... yes. The file itself? NO. Takes admins like me something like 2 seconds and I will overwrite the "administrator" password with whatever I want. Taaadaaa! I'm in. :)

> **InGunsWeTrust said:**
>  it is at the very least not as easy to do. Nonsense. You don't even have to know the password. You can read out the hash. You can overwrite the 'SAM' file (where the administrator's password is stored) with a password of your own choice. Or just delete it altogether. And when you're done you can restore the original hash so everything will look fine and normal as if nothing had happened ....

> **InGunsWeTrust said:**
>   If users have physical access to a computer it should not automatically mean that security has been compromised.  **But it does!** And you should add the word "unauthorized" .... As soon as an unauthorised user gains physical access to a computer --no matter what OS runs there-- the security has been compromised.

That's the very reason why all companies serious about their security policies have strict access controls. Nobody walks into the offices without having proper clearance and at least a visitor's badge. And the number of people who are allowed to walk into the server rooms is even more restricted. 

Having physical access to a computer means you can break into it. That's why they came up with harddisk encryption in the first place, e.g. to defeat this weak point all operating systems have in common.

---

### Post by koenn on 2007-10-29
> **InGunsWeTrust said:**
>  IThe point of securing the password is that with my username and pass he could log onto a network and access network resources. The contents of my harddrive are irrelivent as long as services on my network are still secure.
the scenario you describe involves the passwd and shadow files, which are for local accounts. If those accounts give access to network resources, you're probably using the same username and password for those network resources as well. that's a security hole you've created.

 As you yourself pointed out, there are numerous ways to get a computer to boot an other operating system than the on installed, once there is physical access to the machine. If your friend is any good, you've already lost that bet. Physical access => no security.

---

### Post by az on 2007-10-29
> **InGunsWeTrust said:**
>  I have this security specialist friend that I made a bet that I could give him physical access to my PC and he couldn't crack into my Linux partition.

That's not a bet you could ever win.  It's not linux' fault you didn't make a smart bet.

> **InGunsWeTrust said:**
> 
 This is the only security hole that is still open ...

Never, ever think that.  Never, ever say that if you want to retain any sort of credibility.

Regardless of anything you can think of, there is always somebody that has thought of something you havent.  Security is a road, not a destination.

Anyway, your compromised  the moment s/he pulls out a screwdriver.  You feel lucky?

---

### Post by az on 2007-10-29
> **scorp123 said:**
> The *content* ... yes. The file itself? NO. Takes admins like me something like 2 seconds and I will overwrite the "administrator" password with whatever I want. Taaadaaa! I'm in. :)


sudo apt-get install chntpw

[http://packages.ubuntu.com/gutsy/admin/chntpw](http://packages.ubuntu.com/gutsy/admin/chntpw)

---

### Post by WIGGMPk on 2007-10-29
> **InGunsWeTrust said:**
> Actually, the password file in Windows has apperently been secured in some way because it is at the very least not as easy to do. If users have physical access to a computer it should not automatically mean that security has been compromised.

Depending on the environment and the purpose of the machine... YES physical access SHOULD mean your computer is compromised.


EX: Large Corp. Server Room.... Cleaning Attendant... Clumsy... Power Cord... Death to Network!

---

### Post by Mk9 on 2007-10-30
> **InGunsWeTrust said:**
> 
Let us say I had a single desktop with a single local logon. ANYBODY could walk up to that computer and put a live CD in and boot to it and simply open the /etc/shadow file and copy a known password hash in after root and log in as root.

The reason I am posting this though is to see if anybody has any clue how to circumvent this giant security hole.

OK. My solution to this problem is:
1. Change the BIOS boot settings to boot from the HDD before CD, USB or a Network drive. HDD boot must be the first option.
2. Password protect the BIOS.

Is this not an adequate solution to prevent the scenario you present?

I would be very interested to hear anyone's thought on why this would or would not work in reality.

---

### Post by scorp123 on 2007-10-30
> **az said:**
> sudo apt-get install chntpw Yes nice stuff ... :cool: ... and works on a Live CD too :)

Another nice one:
[http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

---

### Post by scorp123 on 2007-10-30
> **Mk9 said:**
>  2. Password protect the BIOS.  No real security. BIOS passwords can be reset, you just need to have the specs for the motherboard and BIOS in question, but in 99% of the cases it's just a jumper that needs to be reset. There are very few boxes and especially business laptops that are tamper-proof in that regard. And even so: All it takes is a screwdriver: remove the harddisk and you have all the data.

---

### Post by podunk on 2007-10-30
You don't really even need the mother board specs. Just unplug and don't touch it for a few seconds so all the capacitors discharge. Then just close all the open jumpers close to the battery then return them to the original postion. If needed rinse and repeat. There are usually only 3 or 4 jumpers up next  to the battery though.

---

### Post by MJN on 2007-10-30
That's not always true - some BIOS passwords cannot be reset by keypresses/battery-removal/jumpers/shorts - e.g. the ATMEL-protected IBM Thinkpad is one of the classics that requires a bit more work with some components and a spare PC.

Not that I'm saying BIOS passwords are bullet-proof, but merely that it's not always 'easy' to get past them.

As has been said many times over though, if it's got to the stage where someone is sticking screwdrivers inside your machine...

Mathew

---

### Post by Mk9 on 2007-10-30
Thanks for the information on BIOS password resets. I wasn't aware of that.

I guess the solution then is pretty simple - **very strong** encryption of any data you don't want exposed.

---

### Post by dfreer on 2007-10-30
There is no "solution" that can instantly make your box invincible. Linux is not the virus, spyware, and haxXor proof OS that the kiddies think it is. Sure, it's not likely, and extremely doubtful, but at this point it's not impossible. Physical access to the machine is always a bad idea, and so making bets based on ignorance :p

> **podunk said:**
> Then just close all the open jumpers close to the battery then return them to the original postion. If needed rinse and repeat. There are usually only 3 or 4 jumpers up next  to the battery though.

8-O Mess with the wrong jumper, and you could find yourself looking for a new CPU. On my old PIII HP box (I think it was a PIII, may have been a PII, can't remember if the PIII's had the cartridge-like proc?), the jumpers that controlled the voltage to the CPU were located right next to the CMOS battery. If you don't have the motherboard specs, you could also just examine the mobo itself, the jumper may very well be marked. And AFAIK, there's nothing wrong with yanking the CMOS battery itself, should achieve the same goal.

---

### Post by InGunsWeTrust on 2007-11-01
Just glancing over all of the replies, and trying to quickly respond to all of them...

The BIOS password is blazingly easy to reset if you have physical access you don't even need to know anything about the BIOS. Just pull out the CMOS battery for 2 minutes and the password will be gone and all of the default settings will be reset into the BIOS.

Encryption would indeed solve the problem, but I don't know how to do that exactly. That kind of solution would be the kind I would want to hash out.

Also in correction of a previous statement I made. I know not all security holes will ever be filed, but that is the last blatantly obvious and ridiculously open hole. As another aspect of the bet he has only 2 hours to complete his endevour. If I can close the shadow file security hole it is quite possible I will win the bet. Also I know everything about the network resources and stuff but this is a theoretical bet that has nothing to do with real life.

Moving on though, does anybody have anything constructive to say or do you just want to over analyze every statement I make in order to avoid the problem?

---

### Post by MJN on 2007-11-01
No need for that attitude - I thought the conversation was quite friendly! There's nothing wrong with differences of opinion - that's how discussions thrive! :)
 
I think the bottom line is that we've covered everything, and your security concerns are nothing new hence why we have physically protected machines and/or encrypted drives.
 
Unless you've got anything more to add that hasn't been said I don't think there's much more for us to discuss without going round in circles!
 
Mathew

---

### Post by MianoSM on 2007-11-01
Physical access to a computer should always equal access to it with the right information.

On a systems administrator side it would be devastating if you couldn't recover from a forgotten password - especially if its on a system that you set up, forget about, and don't come back to until a year later and a new jump drive away.

I would accept the loss, because anything you do is just going to be overt and unnecessary that would never happen in the real world.

---

### Post by dfreer on 2007-11-01
> **InGunsWeTrust said:**
> I know not all security holes will ever be filed, but that is the last blatantly obvious and ridiculously open hole. As another aspect of the bet he has only 2 hours to complete his endevour. If I can close the shadow file security hole it is quite possible I will win the bet.

It is NOT a security hole. Can it be exploited by an attacker? Sure, very easily if you give them access to the machine. That's why you don't give them access. It's very useful for administrator's who need access. When you say it's a security hole, that's kinda like saying that the aluminimum computer cases are suspect to a DoS attack, because you can take a sledgehammer and smash the thing to bits.

You can try encrypting your hard drive, in which case google or a more aptly titled thread would be able to help you out. The very first hit looks like a decent guide, why not try that out?

[http://tldp.org/HOWTO/Encrypted-Root-Filesystem-HOWTO/](http://tldp.org/HOWTO/Encrypted-Root-Filesystem-HOWTO/)

---

### Post by InGunsWeTrust on 2007-11-12
I didn't mean to come off hostile, it just seemed that everybody was too quick to say it is totally impossible!

I did win the bet as it turns out. I did full disk encryption and he ended up trying to run a brute force on the 18 character passphrase that was the encryption key. Sadly given the 3 hour time limit that was pretty fruitless.

---

### Post by scorp123 on 2007-11-12
> **InGunsWeTrust said:**
>  I didn't mean to come off hostile, it just seemed that everybody was too quick to say it is totally impossible! Duh. Without harddisk encryption you would have lost in a couple of minutes. But then again that's precisely what we told you. :)

> **InGunsWeTrust said:**
>  I did win the bet as it turns out. I did full disk encryption and he ended up trying to run a brute force on the 18 character passphrase that was the encryption key. Sadly given the 3 hour time limit that was pretty fruitless.  Good for you :) ... and what did you win? I mean ... this was a bet of sorts between you and the other guy, right?

---

### Post by InGunsWeTrust on 2007-11-12
Well, it is true I would have lost without harddisk encryption but that is the kind of answer I was looking for! Instead of saying that everyone just said nope it's impossible! The wikki posted on full disk encryption was what I was looking for :-)

It was a hundred dollar bet :-)

---

### Post by MJN on 2007-11-12
I thought you said he was a security specialist? Did he not think you'd use encryption? :confused:
 
Do pass on his contact details - I'm a bit short of cash at thew moment... ;)
 
Mathew

---

### Post by dfreer on 2007-11-12
Glad you won though, $100 must be nice! :D

EDIT: Anything I was going to say has already been covered.

BTW, did you follow a guide to fully encrypt your hard drive? If so, can you tell us which link you used (for future followers of the thread)?

---

### Post by aysiu on 2007-11-12
> **InGunsWeTrust said:**
> I didn't mean to come off hostile, it just seemed that everybody was too quick to say it is totally impossible! I agree with dfreer. You may have a right to gloat over your friend, but you have no right to gloat over other forum members.

You did not come in and say > If I bet my friend $100 that he can't break the encryption on my hard drive within two hours, do you think I'd win? In fact, the word *encrypt* did not even show up until post #7, and it wasn't you who said it: [quote=CSMatt]Yeah you're going to lose that bet. You could encrypt your drive, but I can't think of anything else.[/quote] From post #8: [quote=scorp123]Having physical access to a computer means you can break into it. That's why they came up with harddisk encryption in the first place, e.g. to defeat this weak point all operating systems have in common.[/quote] Post #18: [quote=Mk9]I guess the solution then is pretty simple - very strong encryption of any data you don't want exposed.[/quote] The first time *you* mention encryption: [quote=InGunsWeTrust]Encryption would indeed solve the problem, but I don't know how to do that exactly. That kind of solution would be the kind I would want to hash out.[/quote] That's post #20.

So, no, you can't say "I told you so" to anyone except your friend.

---

