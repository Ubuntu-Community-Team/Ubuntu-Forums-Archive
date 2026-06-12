---
title: "Wiping RAM at each shut down"
date: 2010-06-03
forum: Security
---

### Post by alphaamanitin on 2010-06-03
Ubuntu Forum:

Is there a handy program that wipes my RAM at each shut down to prevent RAM attacks and recovering passphrases?  Is this even possible?  I have a truecrypt volume and have read that it is vulnerable to these RAM attacks.

AlphaA

---

### Post by bodhi.zazen on 2010-06-03
It is may be possible, but I would imagine it would be difficult and IMO is not really necessary.

The ram wipes itself after it has been powered off for a short time, probably faster then it would take to wipe the RAM.

The kernel sits in RAM, so you would need to boot some kind of a live CD, which did not use RAM, and thus would be slow, and wipe the RAM from there.

Again, turning your computer off is going to be a faster way to "wipe" the ram.

---

### Post by JohnnyC35 on 2010-06-03
Now, it would have to be totally powered off right? I mean unplugged. With motherboards now they are, or are gearing towards more of an always on standby are they not. So as long as there is power there could still be information on the RAM unless it was unplugged from the power or PSU switched off.?

---

### Post by tgm4883 on 2010-06-03
> **JohnnyC35 said:**
> Now, it would have to be totally powered off right? I mean unplugged. With motherboards now they are, or are gearing towards more of an always on standby are they not. So as long as there is power there could still be information on the RAM unless it was unplugged from the power or PSU switched off.?

That would be a sleep state. Off or hibernation should still remove power to the RAM. I haven't looked at the specs of it, but I would imagine that there *may* be a motherboard that keeps power to ram

---

### Post by sgosnell on 2010-06-03
RAM has to be constantly refreshed, or it just returns to zeros.  Turning the computer off stops the refreshing, and the RAM will be wiped within a few seconds.  If you leave a laptop in suspend, or sleep, the RAM will retain its state, but shutting down will wipe it.  You don't need to unplug the power, just turn the computer off.  RAM attacks are only possible while the OS is running.

---

### Post by HermanAB on 2010-06-04
Assuming that your hard disk is encrypted (otherwise, you are wasting your time), simply ensure that the machine remains under your control for a few seconds after powering it off.

---

### Post by crazyfuturamanoob on 2010-06-04
Just wipe the parts of RAM that contain passwords. See which programs handle passwords, get their source code and add a memset(everything) at the end of main(). (maybe it's already like that)

---

### Post by noway2 on 2010-06-04
If you are really concerned about leaving recoverable data, you could also clear your swap space.  The secure delete tools package has a tool to do this, but it isn't the most convenient of processes, nor the fastest.  It isn't something that you would want necessarily want to do on a regular basis, but if you were concerned about someone getting physical access to the machine in a particular situation, it may be helpful.

---

### Post by alphaamanitin on 2010-07-14
Thanks Guys,

Sorry for the delay in the response.  I have read that it can be up to two minutes before the RAM degrades, any thoughts on the validity of this?

AlphaA

---

### Post by rookcifer on 2010-07-14
> **alphaamanitin said:**
> Ubuntu Forum:

Is there a handy program that wipes my RAM at each shut down to prevent RAM attacks and recovering passphrases?  Is this even possible?  I have a truecrypt volume and have read that it is vulnerable to these RAM attacks.

AlphaA

Unnecessary.  RAM is a dynamic medium; that is, once powered off, it loses everything it had "stored."  This is why the "cold boot attack" that has made so much news the last couple of years must be done within a couple minutes of the machine being turned off.  Typically an attacker will need to be waiting by the machine with canned air or some other tool to cool the RAM down after the machine is powered down.  If the RAM stays cold, it holds its memory longer after being turned off, thus allowing the attacker more time to do a RAM dump.

Unless you have people sneaking around the area where your computer is used, you have nothing to worry about.

---

### Post by yeleek on 2010-07-15
If the goal is protection of Truecrypt, then there are other things which are more pressing

[http://theinvisiblethings.blogspot.com/2009/10/evil-maid-goes-after-truecrypt.html](http://theinvisiblethings.blogspot.com/2009/10/evil-maid-goes-after-truecrypt.html)

---

### Post by alphaamanitin on 2010-07-15
I know that it is essential for a person doing a RAM recovery to do it in a brief window after the computer has been shut down.  I am not really worried about anything, I just like playing around with my computer and security.  I take it no one knows of such a program because it is a difficult task to do?'

AlphaA

---

### Post by supremedalek on 2010-07-15
Well, you may want not to have swap space defined in the hard drive and put /tmp in a ramdisk. Other than that, you want to make sure people will not boot up the machine for 30 minutes; I think that is the longest time a memory card was out of a computer and people were still able to retrieve some data off it.

---

### Post by sgosnell on 2010-07-15
Or reboot it immediately.  I would think booting the computer would wipe the RAM as the OS is reloaded.  I'm not sure of that, though.  Wiping the RAM seems difficult, because it can't be done while the RAM is in use, because that would remove the program, and it seems to be more trouble than it's worth.

---

### Post by endotherm on 2010-07-15
bleachbit has ram and swap shredding capabilities. perhaps there is a cli switch you could use to launch it non-interactively to do that one task. 

[http://bleachbit.sourceforge.net/documentation/command-line](http://bleachbit.sourceforge.net/documentation/command-line)


personally op, I think you are worried about nothing. short of defcon, you are not going to encounter too many EvilMaids.

my general recomendation on encryption, since that seems to be part of the topic at hand, is not to encrypt the whole hdd, but just your personal data. also don't have it automount at login. remember, if you are being stoped at the border or interrogated by a bad guy, and they see a password box pop up, most people have little recourse other than to give up the password. if you have a smaller volume archive sitting somewhere deep in your folder hierarchy, then there is a great likelihood that no one will notice it;s there unless they look for it.

[http://xkcd.com/538/](http://xkcd.com/538/)

---

### Post by alphaamanitin on 2010-07-15
> **sgosnell said:**
> Or reboot it immediately.  I would think booting the computer would wipe the RAM as the OS is reloaded.  I'm not sure of that, though.  Wiping the RAM seems difficult, because it can't be done while the RAM is in use, because that would remove the program, and it seems to be more trouble than it's worth.


I had not thought about that.  I am a grad student in biology who really enjoys playing with computers and learning more about them.  Things like that make me think more, thanks for pointing that out.  

As for swamp I don't think that is a real issue.  If I actually had *real* need to encrypt and info to keep private I would use True Crypts hidden operating system and encrypt the entire hard drive.  

So no wiping, but what about filling the RAM to near capacity with before shutting down?  Also, how long with my passphrase stay in RAM?  Will it really be there if I mount something like a True Crypt volume and and then unmount it, and use my computer for another hour before shutting down?  

AlphA

---

### Post by bodhi.zazen on 2010-07-15
> **alphaamanitin said:**
> I had not thought about that.  I am a grad student in biology who really enjoys playing with computers and learning more about them.  Things like that make me think more, thanks for pointing that out.  

As for swamp I don't think that is a real issue.  If I actually had *real* need to encrypt and info to keep private I would use True Crypts hidden operating system and encrypt the entire hard drive.  

So no wiping, but what about filling the RAM to near capacity with before shutting down?  Also, how long with my passphrase stay in RAM?  Will it really be there if I mount something like a True Crypt volume and and then unmount it, and use my computer for another hour before shutting down?  

AlphA

I think the "take home message" would be - If someone has access to your RAM (cold boot attack) that implies they have physical access.

If they have physical access, as indicated by this blog

[http://theinvisiblethings.blogspot.com/2009/10/evil-maid-goes-after-truecrypt.html](http://theinvisiblethings.blogspot.com/2009/10/evil-maid-goes-after-truecrypt.html)

And the comments ...

There are many problems you will have, from key loggers to custom kernels.

Your best (only ?) defense is to prevent physical access.

[color=darkred]This cartoon summarizes the entire conversation[/color] :

[IMG]http://imgs.xkcd.com/comics/security.png[/IMG]

---

### Post by alphaamanitin on 2010-07-15
Ha, that reminds me of an article I read on rubber hose decryption.  Basically, you beat the person with the passphrase witha rubber hose on the soles of their feet until they tell you the phrase.

Anyway, I was just thinking if there was a way to prevent the one very specific attack-the cold boot attack.  I take it that no one has really worked, or made public, a method for preventing this specific attack?  I mean obviously if a person has physical access and can prevent you from knowing (s)he accessed your computer a evil maid attack and the likes is very possible.  But I simply want to deal with only the cold boot attack in theoretical terms.  Which multiple posts have pointed out that running a program to wipe the RAM would be very difficult do to it needing to run in the RAM.

AlphaA

---

### Post by endotherm on 2010-07-15
> **alphaamanitin said:**
> Ha, that reminds me of an article I read on rubber hose decryption.  Basically, you beat the person with the passphrase witha rubber hose on the soles of their feet until they tell you the phrase.

Anyway, I was just thinking if there was a way to prevent the one very specific attack-the cold boot attack.  I take it that no one has really worked, or made public, a method for preventing this specific attack?  I mean obviously if a person has physical access and can prevent you from knowing (s)he accessed your computer a evil maid attack and the likes is very possible.  But I simply want to deal with only the cold boot attack in theoretical terms.  Which multiple posts have pointed out that running a program to wipe the RAM would be very difficult do to it needing to run in the RAM.

AlphaA

as bodhi said, Physical access is Root access. there are no exceptions to this rule.

but no, the best way to prevent a coldboot attack on your encryption keys, is only encrypt what you need to, and only decrypt it when needed.

---

### Post by alphaamanitin on 2010-07-15
So, still have one question unanswered I believe.  Does anyone know about how long the passphrase would stay in memory?  I understand that it would probably be highly variable and based on what you were doing at the time.  Obviously, if you ran a memory intensive program that used the near entirety of your RAM after mounting something like a true crypt volume the passphrase would probably be gone.  Does any one know of cases or proof of concept displays where a person was able to recover a passphrase an hour or more after the person mounted and unmounted an encrypted volume?  

AlphaA

---

### Post by endotherm on 2010-07-15
> **alphaamanitin said:**
> So, still have one question unanswered I believe.  Does anyone know how about how long the passphrase would stay in memory?  I understand that it would probably be highly variable and based on what you were doing at the time.  Obviously, if you ran a memory intensive program that used the near entirety of your RAM after mounting something like a true crypt volume the passphrase would probably be gone.  Does any one know of cases or proof of concept displays where a person was able to recover a passphrase an hour or more after the person mounted and unmounted an encrypted volume?  

AlphaA


well, truecrypt is on-the-fly encryption, so while you are working with the ciphered data or the container, you will need to have the key in ram. it isn't just used at mount, but is used for every IO operation (read or write) performed within that volumes namespace. as for how long it stays, that depends on many factors, so I don't think anyone can give you a perfect answer to that question. depends on your hardware, the amount of ram in the box, the amount used on average, etc.

---

### Post by cariboo on 2010-07-15
The information is only going to stay in ram until the capacitors on the motherboard leak down. You can't really predict reliably how long that's going to take. To delay leak down, you can freeze the capacitors, but again depending on how warm the capacitors are it is hard to predict how long leak down will take. 

All this depends on physical access, so unless the bad guy has time to prepare the system for fast access to the ram,before shutdown, this really should not be something to worry about.

---

### Post by Gurtz on 2010-07-15
Just out of interest, has anyone ever come up with some sort of physical-access trigger switch that could be mounted in the case. If the case were to be opened while the machine was on (to initiate a cold-boot attach on the RAM), the switch would trigger, which would then cause a script to be executed. The script could do "whatever", but possibly, in such a scenario, it could initiate an "unmount" of any open TrueCrypt volumes (which, I understand, would wipe the keys from memory). [This may not be practical for cases where the entire filesystem is encrypted, but could be of use on a smaller scale with individual TC files/partitions.]

Thoughts?

Gurtz

---

### Post by alphaamanitin on 2010-07-15
I thought it would be dependent on the amount of RAM you use after you are finished with something like True Crypt and umount it. However,  it seems to me that what cariboo907 is saying indicates that it will stay in memory until the capacitors drain and the magnetic memory degrades, but I still assume that using the near full memory would remove traces of the passphrase or am in mistaken?

AlphaA

---

### Post by endotherm on 2010-07-15
> **alphaamanitin said:**
> I thought it would be dependent on the amount of RAM you use after you are finished with something like True Crypt and umount it. However,  it seems to me that what cariboo907 is saying indicates that it will stay in memory until the capacitors drain and the magnetic memory degrades, but I still assume that using the near full memory would remove traces of the passphrase or am in mistaken?

AlphaA

you are correct that the info may be overwritten by another program while the computer is in use. Cariboo was speaking about the case that you shut it down. 

the problem with your approach is that it is unpredictable, there is little to no way to test it, and no way to confirm each run. 

I still have to recommend the memory shredder for bleachbit. it should overwrite all unused ram (your hash would reside in a block of recently unallocated ram if you had just exited truecrypt), and you don't have to reboot to do it.

---

### Post by yaaarrrgg on 2010-07-15
I think the bigger security risk would be someone reading the ram while the machine is on.  If you open an encrypted file, that's loaded into ram decrypted.   Passwords could too, depending on how an application is written.  Also some of that could be pushed to swap space and that would not necessarily be erased (completely).

---

### Post by alphaamanitin on 2010-07-15
> **endotherm said:**
> you are correct that the info may be overwritten by another program while the computer is in use. Cariboo was speaking about the case that you shut it down. 

the problem with your approach is that it is unpredictable, there is little to no way to test it, and no way to confirm each run. 

I still have to recommend the memory shredder for bleachbit. it should overwrite all unused ram (your hash would reside in a block of recently unallocated ram if you had just exited truecrypt), and you don't have to reboot to do it.


Did I miss one of your posts?  I do not recall the memory shredder for bleachbit-could you give me another short description?

Yes, yaaarrrgg that would be a bigger risk, and I would like to actually discuss theoretical solutions to that as well, but for now I think for my sake I need to only deal with the cold boot attack.  Too much info and not enough knowledge on my part:)

AlphaA

---

### Post by alphaamanitin on 2010-07-15
> **Gurtz said:**
> Just out of interest, has anyone ever come up with some sort of physical-access trigger switch that could be mounted in the case. If the case were to be opened while the machine was on (to initiate a cold-boot attach on the RAM), the switch would trigger, which would then cause a script to be executed. The script could do "whatever", but possibly, in such a scenario, it could initiate an "unmount" of any open TrueCrypt volumes (which, I understand, would wipe the keys from memory). [This may not be practical for cases where the entire filesystem is encrypted, but could be of use on a smaller scale with individual TC files/partitions.]

Thoughts?

Gurtz


I missed you post until now as I was typing my post.  This is a great idea I think.  Although a better script for dealing with that, in my limited understanding of True Crypt would to overwrite the first 100 or so blocks and the last 100 or so blocks on the true crypt volume-thus removing the headers. Unless back up headers are somewhere, this completely removes the possibility of decrypting the volume even if the passphrase is known.  At least this is what I have read on the True Crypt forums and in the manual.  Can you believe it I did actually RTFM.  Anyway, this would of course be a doomsday type program that one would only want to use if the data was not something that needed to be kept perminently but rather protected from getting in the wrong hands.  EG-a human rights group's computer being nabbed by a oppressive government to find collaborators and individuals who help the human rights group.  I know that this has actually been prevented because of PGP.

AlphaA

---

### Post by endotherm on 2010-07-15
here is some info about bleachbit cli options, but you will have to figure out how to call it to get your desired results. good luck

---

