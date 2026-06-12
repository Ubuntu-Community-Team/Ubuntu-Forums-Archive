---
title: "How did he log into my computer?"
date: 2009-06-02
forum: Security
---

### Post by dcollier on 2009-06-02
Here is what took place.  Before going to lunch i locked my screen.  After returning from lunch there was someone working on my computer.  I am the only user at my desktop.  After the second user logged out, i noticed that there was an extra user added.  wtf?  My question is, is there a log that I can check to see when and how this took place?  The user is my boss, and after he logged out he walked away with a smile.  Is there a way to prevent this from happening again?

---

### Post by cdenley on 2009-06-02
The log you would want to check is /var/log/auth.log. Anyone with physical access can do anything on your system, unless you use encryption. If he rebooted then selected recovery mode in the grub menu, he could have created a new user or even set a root password.

---

### Post by cariboo on 2009-06-02
I don't think you can stop your boss from accessing the computer especially if it belongs to the company. If it is your own computer there isn't much you can do to stop someone if they have physical access.

---

### Post by dcollier on 2009-06-02
I do show an open session by (uid=0) and did notice that the computer was rebooted.  So, using encription, how would that stop this from happing?

---

### Post by HermanAB on 2009-06-02
If most of the system on disk is encrypted, then another user cannot change the system after a reboot.  They can completely wipe and re-install it of course, but that is kind radical

---

### Post by uupreti on 2009-06-02
> **HermanAB said:**
> If most of the system on disk is encrypted, then another user cannot change the system after a reboot.  They can completely wipe and re-install it of course, but that is kind radical


Are you guys taking about LVM with encryption at this point? It seems a good point. How can I encrypt my whole file system after installing fresh copy of Ubuntu (installed not using LVM encrypted). It's a really good point.

---

### Post by jonobr on 2009-06-02
cariboo907

Respect and salutations to the forum staff.

I think most people in work, should not expect privacy on their work system,
however, I'm thinking that dcollier could talk to his boss and express concern over his machine being accessed and the possibility of vulnerability being used by him, which could be used by others.

I would recommend  having a conversation with your boss , and front end it by indicating that the company has every right to do this.
Normally this access is done by IT staff.

However, not all bosses are created equal.
Sounds to me in this case as if the boss was leaving a user to access through and working/playing around on someone elses computer which is wrong and sounds  a bit disrespectful, Boss or no...

Cheers

---

### Post by MartyBuntu on 2009-06-02
I don't think there is any reasonable expectation of privacy (from your boss) on a company computer on company time.

---

### Post by jonobr on 2009-06-02
Hi MartyBuntu


I agree,
but depending on the company, this may be a function of IT and not his boss.
In the company i am in, I would have no problem with my boss doing this to my pc as I have no expectation of privacy,
however, he has no reason to do it and I think it would be  couteos for him to mention to me that he wanted to look at my machine.

It really depends on the company enviroemnt and again as previously stated,
I dont see the harm, that if you think there may be a vulnerability on your machine to asking your boss how he did it.

If he sayd, none of your business, then fair enough, he may have that right. 
And lastly, again, as I mentioned, just becuase he is your boss, doesnt mean he cant be a bad person doing bad things,

Its up for everyone to assess for themselves I suppose

---

### Post by MartyBuntu on 2009-06-02
True.

The boss *is* the boss. Like you said, this doesn't stop the OP from inquiring what is going on.

I'm not sure I'd feel too comfortable working in a place where you would have to guard against even your employer's shenanigans.

---

### Post by lisati on 2009-06-02
It can be surprising to some people what the boss can learn about what you're up to. Part of my first job was to write short programs to analyze the accounting logs produced by the companies computers and report on certain kinds of activities. This included reports on who had accessed particular files. Another was a report showing who had logged on along with when they'd logged off, how long they were logged on, and to give some indication of whether the logoff was "normal" (initiated by the user) or their session being canceled or timing out due to inactivity (a potential security risk - the company processed commercially sensitive data).

---

### Post by jonobr on 2009-06-03
lisati thats very interesting....
Thanks for sharing.

I think an environment like that would be simply too stifling for me

I would understand a call center environment where people have to be at their desk or where the old time clock would have been employed.

I do0nt understand why my boss cant get it into his head that people need some "left for dead" time ;)

---

### Post by theozzlives on 2009-06-03
Just my 2 cents. I feel if it's a company computer, you shouldn't have anything to hide from your boss, so it shouldn't bother you. If it's your personal computer, it belongs at home and your boss should supply you with one for work.

---

### Post by bodhi.zazen on 2009-06-03
To encrypt your installation, use the alternate CD 

[http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

---

### Post by apmcd47 on 2009-06-03
dcollier, things you didn't say in your original post:
[LIST]
[*]Was this person known to you?
[*]Did you challenge him?
[*]Have you spoken to your manager or IT Support about the incident?
[/LIST] 
Other posters to this thread have assumed the other user was your manager checking what was on your computer, or someone doing this at his request. Is this true? Or did he just want to log onto a computer and chose yours? If the latter he could be in breach of your company's code of conduct. It is also possible that, as he has apparently rebooted your computer, his actions could have lost you valuable work, such as a processing job that takes hours to complete. Regardless of company policy on computers and privacy I think this is unacceptable.

Another thing to think about: regardless of how it was done, your machine has been compromised. I'm guessing the encryption will need to be done on a newly installed machine anyway, but even if it doesn't, it may be prudent to do so anyway.

---

### Post by dcollier on 2009-06-03
ok, sorry that i didn't respond back as quickly, and i want to thank you all for your time.  I will try the encryption.  On a side note, i work in the IT department, and my boss....well.. we get the picture.  This was not something done out of a power strugle, its just that i am the only on in the office using [grub] ubuntu as a work station.  At the time my computer was the only computer available, due to the fact that [i] we were using his office for a meeting, and he needed to check his email...lol     So i was socked as how quickly he gained access and was eager to learn how it was done and how to prevent it from happing again [learning process]!....So once again, thanks for the answers that I so dearly needed!

---

### Post by Agent ME on 2009-06-03
It doesn't take long to root a machine if you have physical access with a LiveCD.

If you're using grub with the default settings, then he doesn't even need one, but just needs to edit the command string for booting linux when the grub loader appears.
Easiest way to guard against this is to password grub:
```
export EDITOR=nano
sudoedit /boot/grub/menu.lst
```
Enable a password by adding in a line:
```
password mypassword
```
Then change this line:
```
# lockalternative=false
```
to this:
```
# lockalternative=true
```
Now the system will require the password to be entered if someone tries to boot into recovery mode or edit the kernel argument string.

Then to stop LiveCDs, you could configure your BIOS to only allow booting from the hard drive, and put a password on the BIOS.

(Technically, these are only deterrents that should protect your computer in a non-complete-hostile environment. A dedicated attacker could reset your BIOS, or remove your hard drive and place it in his own machine, and edit it to have his own user account added. If you think your attackers are this motivated, try looking into full disk encryption.)

---

### Post by apmcd47 on 2009-06-04
[This link]("http://onlyubuntu.blogspot.com/2008/04/howto-disable-ctrl-alt-del-from.html") will take you to a page describing how to disable reboot using *Control-Alt-Delete*. I've implemented (but not tested) this on my machine.

Andrew

---

### Post by dcollier on 2009-06-04
I am going to try that!

---

### Post by bodhi.zazen on 2009-06-04
LOL why ?

ctrl-alt-delete => nothing happens.

hold power button for 5 seconds -> reboot

---

### Post by picopir8 on 2009-06-04
Disabling ctlalt-delete is pointless.  What you need to do is disable single user login (or at least password protect it by setting the root password) and prevent booting external media in bios.

---

### Post by Agent ME on 2009-06-04
As I said, the most important thing is to lock down Grub. Nothing else is really needed, as a LiveCD would be needed to log onto the computer as root.

And if this is the case, then you really need to have a talk with your boss. And *maybe* just give him a limited account yourself, so he doesn't take it upon himself to figure out how to hack himself one (and give himself root too). ;)

---

### Post by apmcd47 on 2009-06-05
> **picopir8 said:**
> Disabling ctlalt-delete is pointless.  What you need to do is disable single user login (or at least password protect it by setting the root password) and prevent booting external media in bios.

Ctrl-Alt-F1,Ctrl-Alt-Del is arguably the fasted way to reboot a machine you don't have login rights and somebody is already logged into. So disabling it could be done as part of the work to stop another person getting access - all you are doing is delaying the inevitable, but it might be enough to make them think again and move on to another machine. 

But personally I come from a background where Ctrl-Alt-Del **doesn't** reboot the system, and only does something harmless like bring up a login/logout prompt. I have logged into the virtual ttys before now then typed Ctrl-Alt-Del by accident and watched in horror as my Linux system went down.

---

### Post by picopir8 on 2009-06-05
Holding the power button down or reaching around and unplugging the power cable then reinserting it is much more effective as you do not need to wait for the computer to shut down.  So it would be better to do that if you want to get in quickly before someone sees you.

If you can prevent unauthorized access from the off state then a person will be unable to log into the computer when it is password locked as well.

Going into bios and disabling every boot media except the internal hdd will prevent someone from booting a live CD, usb drive with their own os etc.

Locking down grub is a good idea because someone can specify booting from external media there as well.

Most importantly, setting the root password will cause the computer to prompt you for a password if you boot into single user mode.  This is more important because most people dont carry bootable media around with them so in which case this is their only way into the system.

Lastly, encrypt your fs, or at least your homefs.  That way, even if the person removes the hdd and puts it in another computer, they wont have access to your files.

---

### Post by bodhi.zazen on 2009-06-05
It is important, IMO, to point out that the problem here is physical access.

The techniques listed here will deter only the most casual of intruders and are easily defeated.

That is not to say they are not sometimes helpful, but it is a disservice, IMO, if we do not at least warn people that these techniques are easily defeated.

In addition setting a root password has it's downside as well.

If you are wanting to deter casual intruders, and you feel these things increase your security, go for it.

But, be warned that if you have sensitive data on your computer you really need to look at encryption. There are several options for encryption in Ubuntu from LUKS to ecryptfs.

---

