---
title: "Is root in recovery mode a security risk?"
date: 2005-12-28
forum: The Cafe
---

### Post by Irony on 2005-12-28
I note that when I boot into recovery mode on my laptop or desktop pc that it goes into *root@ubuntu* if I type *startx* it then boots into root GUI - isn't this a security risk as I don't have to type in a password.

Also how do I set a root password - if I go to *System > Administration > Users and Groups*, root already has a password (presumably my irony password).

---

### Post by Ocxic on 2005-12-28
when using recovery mode you want to be root that way your sure every one of your changes is applied, it's for normal day to day computing that you want to just be a normal user and not root, that way you can't accidently do something to destroy/messup you system.

---

### Post by Irony on 2005-12-29
Its just that it seems that anyone could boot into the computer via recovery and mess with the files.

---

### Post by Zwack on 2005-12-29
[QUOTE=Irony]Its just that it seems that anyone could boot into the computer via recovery and mess with the files.[/QUOTE]

Yes, which is why physical security is as important as "remote" security.

You might be able to set a root password and have that checked in recovery mode.  I don't know if that works on Ubuntu, it does in other places.  If you want to stop people messing with boot options then set a bios boot password and a GRUB password.

They can still get around these but you're working your way up... 

If this still isn't good enough then buy Secure Solaris or Hp-UX or SCO CMW.  You'll hate it very quickly but you will be very secure.

Z.

---

### Post by schilcha on 2005-12-29
Zwack, you made the run... anyways, here's my thoughts in the same direction...

If you can't trust your users that far, there's a password option for grub reduce boot-options for non-admin users.
Even in this case, a LiveCD can give you full access to the installed data (there's no root-pwd on the LiveCD). So you would also need a bios-pwd to prevent booting from cdrom.
Also other operating systems on the same machine can make your linux-data accessible without honouring priveliges (I know that rfstool for win gives a damn about file owners and permissions -- how should it do that?)
I guess to secure your data from normal and dedicated users, you'd need something like an encrypted filesystem, but I've never coped with that and I don't really know about its possibilities. Everything else is just bits on a disk. The OS takes care of what a user can and can't. If the OS doesn't care, there's no protection.

---

### Post by psusi on 2005-12-29
Neither a root password, nor a grub password, nor a bios password will prevent someone from booting the system and getting root access.  If you can choose to boot grub into recovery mode, you can just as easily tell grub to add init=/bin/sh to the kernel command line, which will bypass a root password.  If you can boot the system, you can get around the grub password by inserting another bootable media, like a cdrom or a usb memory stick.  A bios password is the hardest one to get around, but even that can be done.  

If you really want your system to be safe when captured by the enemy, you need to encrypt the hard drive.

---

### Post by Zwack on 2005-12-29
[QUOTE=schilcha]I guess to secure your data from normal and dedicated users, you'd need something like an encrypted filesystem, but I've never coped with that and I don't really know about its possibilities.[/QUOTE]

Encrypted filesystems will protect your data from other users but won't stop them being able to hack up the OS... And given that they can get full access to the OS then they can put something in there to record all of your key strokes and...

(I'm not paranoid... really, I'm not) 

But something along the lines of a CMW system will only allow certain users to do certain things to certain files.  A quick search for Compartmentalised Mode Workstation shows up some information as does Compartmenred mode workstation.  I know that Sun, HP and SCO all had products, but I don't know what is currently available.  HP-UX 10.16 was a complete pain to work with.

Z.

---

### Post by Zwack on 2005-12-29
[QUOTE=psusi]Neither a root password, nor a grub password, nor a bios password will prevent someone from booting the system and getting root access. [/QUOTE]

I was assuming that a grub password is set to only allow them to boot into the normal mode.  A root password is set so that they can't login as root and that a bios password was set so they can't change the boot path... (and the boot path is set to only boot from the first hard drive)...

They can still reset the bios CMOS settings, boot from another media, change the root password and they're in...

An encrypted filesystem will help, but only when used with the above, and all of the users need to be trusted.

A CMW still requires physical security but reduces the need for trust on users.

The only truly secure machine has already been rendered completely inoperable.

Z.

---

### Post by 23meg on 2005-12-29
Local physical security is every bit (pardon the pun) as important as remote security. Keeping your laptop within your reach at all times and physically securing the space where your desktop / server resides should be your #1 priority, before passwords, encryption and firewalls.

---

### Post by psusi on 2005-12-29
[QUOTE=Zwack]Encrypted filesystems will protect your data from other users but won't stop them being able to hack up the OS... And given that they can get full access to the OS then they can put something in there to record all of your key strokes and...

(I'm not paranoid... really, I'm not) 

[/QUOTE]

That's why you encrypt the WHOLE disk ( including the OS ).

---

### Post by Zwack on 2005-12-29
[QUOTE=23meg]Local physical security is every bit (pardon the pun) as important as remote security. Keeping your laptop within your reach at all times and physically securing the space where your desktop / server resides should be your #1 priority, before passwords, encryption and firewalls.[/QUOTE]

Of course a physically secure machine that is wide open to the internet is useless too.  You need to balance this all...  

Practical security is a trade off between security, cost and usability.  

CMW is very secure, is fairly expensive and is really nasty to have to use.  The trade-off is not normally worth it.  

Like everything else you need to decide how much you trust your users, how much you can put up with in the way of extra effort, and how much you can afford to spend on this.  With a lot of money and a lot of extra effort you could put your computer in a vault with a security guard standing watch over your users... But is that reasonable.

Think of trade offs, decide what you want to accomplish (or legally have to with HIPAA and Sarbanes-Oxley) and then implement it.

Z.

---

### Post by Zwack on 2005-12-29
[QUOTE=psusi]That's why you encrypt the WHOLE disk ( including the OS ).[/QUOTE]

In which case you have to decrypt it so that they can access your machine (I am assuming other users on this machine and it seems reasonable given that he is worried about people rebooting it...)

If you don't have any other users then yes, encrypt the whole disk, and never leave it up when you leave it.

Z.

---

### Post by ramiro on 2006-03-02
I booted into recovery mode for the first time today (it was an accident). and when it finished booting it dropped me at a root prompt, without asking for a password or anything! Is this the standard behaviour? Because this seems to be very insecure...

---

### Post by meborc on 2006-03-02
this is very standard and highly necessary, when u have managed to damage your system or lost your password... i guess that is why it has a name of RECOVERY :rolleyes:

it is true, that it seems a bit insecure (a lot for that matter) but it is the only way to have a chance to fix your system when everything else fails

---

### Post by ramiro on 2006-03-02
I understand that, but couldn't they at least ask for a password?

I mean, it doesn't take much for someone to completely destroy my machine.

---

### Post by aamukahvi on 2006-03-02
It's just like Win95 where you could bypass the password prompt by pressing Esc :p

---

### Post by wien on 2006-03-02
[QUOTE=ramiro]I mean, it doesn't take much for someone to completely destroy my machine.[/QUOTE]But they would have to be *in front of* your computer though. If you trust someone enough to let them come that close to your computer, they usually wouldn't do anything like that anyway. And if someone actually does get into your house and do that, your computer is probably the least of your worries.

---

### Post by aamukahvi on 2006-03-02
[QUOTE=wien]And if someone actually does get into your house and do that, your computer is probably the least of your worries.[/QUOTE]
Some skinny hacker armed with a wireless mouse... :mrgreen: He'd be needing some serious recovery mode after that :twisted: :twisted: :twisted:

---

### Post by meborc on 2006-03-02
i guess if you'r really scared, then you can delete the recovery option lines from your grub menu :) ... but if you then mess up your comp, then you'r in trouble...

AND if you don't guard your BIOS settings with admin password, it is easy to get access to your comp by setting it boot from cd and using knoppix... just a thought :rolleyes:

---

### Post by erze on 2006-03-02
You can password protect grub if you want.

In a terminal:

Execute grub:
$ grub

Enter the md5crypt command:
grub> md5crypt

Enter the password you want to use:
Password: ********

Example of respond from grub:
Encrypted: $1$k823K1$2qUgkIIUD7p6YMRXRDTw3/

Remember the encrypted password. :-D 

Quit grub:
grub> quit

Open /boot/grub/menu.lst and add your encrypted password "password --md5 $1$k823K1$2qUgkIIUD7p6YMRXRDTw3/" to this section:

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
password --md5 $1$k823K1$2qUgkIIUD7p6YMRXRDTw3/

Locate this section:

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

Change it to:

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

Save and quit menu.lst.

Excute update-grub:
$ sudo update-grub

Reboot...

Recovery mode is now password protected.

[COLOR="Red"]**I take no responsibilities for anything that may go wrong and make your system unbootable !!!!!**[/COLOR]

---

### Post by meborc on 2006-03-02
[QUOTE=erze]Encrypted: $1$k823K1$2qUgkIIUD7p6YMRXRDTw3/

Remember the encrypted password. :-D[/QUOTE]
i would use paper and pen :mrgreen: > Change it to:

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

if you have # in front of a *thing* then it is a comment... and it doesn't matter if you change it or not... or have i had too much caffeine today? :confused:

---

### Post by ramiro on 2006-03-02
I'm on a laptop, so they don't necessarily need to be in my house =) I suppose I shall have to guard my machine extra carefully againsed tech-savvy people at uni (doing computer science... damn)

ahh well, I don't have anything important on dapper anyway (I'm crazy but not THAT crazy)

---

### Post by stu on 2006-03-02
My Dapper asks for a password every time... I wonder what is different?

---

### Post by meborc on 2006-03-02
even if u are in recovery mode?

---

### Post by erze on 2006-03-02
[QUOTE=meborc]i would use paper and pen :mrgreen: 

if you have # in front of a *thing* then it is a comment... and it doesn't matter if you change it or not... or have i had too much caffeine today? :confused:[/QUOTE]

Just one (1) # in the "AUTOMAGIC KERNELS LIST" section means that update-grub shouldn't touch the line, two (2) # is a comment.

---

### Post by meborc on 2006-03-02
[QUOTE=erze]Just one (1) # in the "AUTOMAGIC KERNELS LIST" section means that update-grub shouldn't touch the line, two (2) # is a comment.[/QUOTE]
sorry... i mix'ed up the lines you suggested to change... /me needs more sleep... thank you for making me feel stupid :mrgreen:

---

### Post by az on 2006-03-02
Anyone with physical acces to the computer can become root.  This is a fact of life.

Either encrypt your whole filesystem or make sure no one is ever alone with your computer.  All it takes is a screwdriver.

---

### Post by Mick-Bungstead on 2006-03-27
I have used the last 3 releases of Ubuntu and thanks to the exellent work by the developers I have never had a problem with it until yesterday when i edited the wrong file and killed my install, all fixed now though :) 
But, when I booted into recovery mode I realised something that made me go 'hmmm'. You can log in as root to recovery mode without giving a password.
Logically this is insecure, for the obvious reasons. Though there must be a very good reason for it that someone could explain to me.

---

### Post by aysiu on 2006-03-27
The reason--it's for recovery.
You boot into it when you have to save your computer.
Otherwise, you boot into the regular kernel.

---

### Post by stuporglue on 2006-03-27
It's impossible to secure a machine that people have physical access to, so there isn't as much concern about the root on boot option. If you're worried, I think grub can require a password, and many BIOSes can as well. Even those can be worked arround, the HD can be removed and accessed etc. 

What no root on a booted system does for you is:
1) It's harder for you to accidentally rm -rf /*.*
2) If it's a server, I think it's harder for someone to use an exploit and elevate privs up to super user privs. 
3) other?

---

### Post by az on 2006-03-27
Anyone anywhere standing next to their computer, holding a screwdriver, can be root.

Physical access to the hard disk == you can be root.  Nothing new here.

---

### Post by aysiu on 2006-03-27
Who needs a screwdriver? Just pop in a live CD...

---

### Post by LordHunter317 on 2006-03-27
[QUOTE=stuporglue]2) If it's a server, I think it's harder for someone to use an exploit and elevate privs up to super user privs. [/quote]Not especially, no.

---

### Post by aysiu on 2006-03-27
[QUOTE=LordHunter317]Not especially, no.[/QUOTE] *Harder* is a relative term. Of course, if you want to be absolutely safe, you never connect any computer to the internet...

---

### Post by lean on 2006-03-28
You need a screwdriver because booting from anything else than hda is disabled, and the bios is password protected.

One way to be completely sure that nobody can boot the system, would be to have system wide encryption (this is not supported by Ubuntu).

Then an attacker can only erease the files - but that what a backup is there for.

---

### Post by LordHunter317 on 2006-03-28
[QUOTE=aysiu]*Harder* is a relative term.[/quote]Not in this case it isn't.  The difficulty of getting root given a local account is equal.

---

### Post by Mick-Bungstead on 2006-03-29
Thanks for bringing the light of this subject to my mind.
It's funny how the most obvious thing escapes your thoughts, like the only way to secure data is take the hard drive home with you and sleep with it. I should have known that. :) 
Thanks again.

---

### Post by MJN on 2006-03-30
*Sleep?* Too dangerous - someone might've followed you in and could nab it.
 
Better to swallow it.
 
;)

---

### Post by az on 2006-03-30
[QUOTE=MJN][
Better to swallow it.
 
;)[/QUOTE]
One byte at a time....

---

### Post by ketsugi on 2006-05-12
When GRUB automatically generates menu.lst, it creates a recovery option for each kernel, which drops the user into a root console. Why doesn't Ubuntu ask for a password when it does this? Isn't it dangerous to give root access without authenticating first?

---

### Post by aysiu on 2006-05-12
Anyone who has physical access to your computer has access to your files. It's no different from letting someone boot a Knoppix CD on your computer.

---

### Post by cgjones on 2006-05-12
Yeah, that's pretty much a given in security. If someone has physical access to the machine, it's all over. There are steps you can take, but it just slows them down. If you are worried about it, you can set a password in the BIOS or I think you can set a password on GRUB itself.

---

### Post by aysiu on 2006-05-12
I think what you should worry about most is people *accidentally* screwing up your computer.

If someone has the intent of destroying or stealing your data, she will do it. Even if you set a BIOS password. Even if you set a root password. She will just take a screwdriver, open up your computer, and take your hard drive somewhere else.

If you're worried about someone accidentally selecting **recovery mode** and typing ```
sudo rm -rf /*
``` for fun, then setting a password for root will at least prompt them for a password when they boot into recovery mode.

**Note to new users**: _Never_ type into your actual Ubuntu installation the command I just gave.

---

### Post by madchicken on 2006-06-30
Hi guys...I noticed that using recovery mode from grub menu let me login on my system as root WITHOUT using password.
Is this only a bug in my installation or is this a big security issue in Dapper?

Bye

---

### Post by jak on 2006-06-30
If you lost your root password (if you even set it) how would you recover that?

It's not a bug, and it's not a huge security risk as physical access to your machine would be needed.

If you're really concerned you can always remove the recovery line from GRUB.. but I'm not sure what you'd do if you wanted to recover it.. and even then you can edit the commands from GRUB to boot into recovery mode, so maybe you'd want a password on GRUB, but then again I'm sure there's a way around that too.. it never ends, as theres always a way to get around passwords, and most of them are legitimately put there.

If someone gains physical access, like maybe your laptop is stolen, then encryption of data would be the best step to take, but how sensitive is you data really?

---

### Post by madchicken on 2006-06-30
Sorry...but I don't think this is correct, because this is a default setting. I found it playing with my system configuration. I didn't know before. 
I think a login access (like console one) is the best way for a recovery mode.
And if I loose my root password, well It's my fault, so I can still access to my data using a live cd and backup my data.
Even WinXP asks you for administrator password in recovery mode.

Think this thing: you leave your laptop (locked) in the office during the launch. Someone can reset your pc and destroy all your data without any trick.
IMHO this is a security issue.

Bye

---

### Post by geco on 2006-07-14
I also noticed this regrettable behavior I know about live CDs and so on... anyway I wonder that no Ubuntu guy thought about protecting the single-mode boot with a password. I think it is possible to add someting to debian automagc kernel script to ask for a password...
Anyway I prefer protect my computer by editing my /boot/grub/menu.lst file and locking the single user mode.
```

 title           Ubuntu, kernel version (recovery mode)
lock
root            (hd0,5)
kernel          /vmlinuz-version root=/dev/hda9 ro single
initrd          /initrd.img-version
boot

```
But I have to edit it everytime I update my kernel image :(

---

### Post by az on 2006-07-14
> **geco said:**
> I also noticed this regrettable behavior I know about live CDs and so on... anyway I wonder that no Ubuntu guy thought about protecting the single-mode boot with a password. I think it is possible to add someting to debian automagc kernel script to ask for a password...

Just set a root password.  You are prompted for the root password when you enter recovery mode, if one is set.

It still does not make your computer any safer to someone with physical access to your box.

> **geco said:**
> 
Anyway I prefer protect my computer by editing my /boot/grub/menu.lst file and locking the single user mode.
[CODE]
 title           Ubuntu, kernel version (recovery mode)
lock
root            (hd0,5)
kernel          /vmlinuz-version root=/dev/hda9 ro single
initrd          /initrd.img-version
boot
[CODE]
But I have to edit it everytime I update my kernel image :(

Edit /boot/grub/menu.list

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

and change that line to 
# lockalternative=true

then 

sudo update-grub.

---

### Post by geco on 2006-07-14
> **azz said:**
> Just set a root password.  You are prompted for the root password when you enter recovery mode, if one is set.
I don't like that, I fear a remote attack more than a local one, if I have a root password set someone could guess and use it from a remote computer.

> **azz said:**
> 
It still does not make your computer any safer to someone with physical access to your box.


I agree with you, but I can at least protect my computer form any silly user who doesn't know what he's doing. :)


> **azz said:**
> 
Edit /boot/grub/menu.list

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

and change that line to 
# lockalternative=true

then 

sudo update-grub.

I didn't know that... thanks!

---

### Post by mms on 2006-07-30
I just booted in recovery mode to fix my xorg.conf file, and to my surprise I got directly to a root prompt without ever having been asked for a password!?

Is this usual?

---

### Post by mority on 2006-07-30
> **mms said:**
> I just booted in recovery mode to fix my xorg.conf file, and to my surprise I got directly to a root prompt without ever having been asked for a password!?

Is this usual?

Yes, this is the wanted behaviour. It gives you the opportunity to recover a lost root password. And it is not an security issue since the attacker must have physical access to the machine. You should take measures to prevent physical access to your machine if you are concerned about this.

---

### Post by taurus on 2006-07-30
That's how it is.  If you go into recovery mode, it means you need to be root to fix whatever problem you may have with your system.  However, you don't need to be in the recovery mode to fix the problem with X.  You can do that from a prompt with the sudo command...

---

### Post by mms on 2006-07-30
I see. Thanks.

---

### Post by soundguy24 on 2006-08-30
[SIZE="2"]I used recovery mode to change the root password and get into my system -- isn't this bad??! Can I completely disable recovery mode?[/SIZE]

---

### Post by Boris2 on 2006-08-30
Which recovery mode do you mean?

Booting from a CD and recovering the system?
-> You could disable booting from CD and set a BIOS-password. But beware: BIOS-passwords can be reseted easy.

Booting the failback-system from grub?
-> Set a grub-password and protect alternatives. But I'll still be possible to access you system with a boot-medium (see above)


The only way (known to me) to protect you against this is to secure your room ;-)

---

### Post by aysiu on 2006-08-30
Anyone who has physical access to your computer has root access anyway...

---

### Post by skymt on 2006-08-30
There's a rule in computer security. If a cracker has physical access to the machine, it's his. There is no way to keep him out of your data, barring encryption, and there is absolutely no way to keep him from installing and changing whatever he wants, given enough time alone with the machine. BIOS passwords can be overridden. Account and grub passwords can be circumvented with a live CD.

My advice is to leave it alone. Convenience is more important, since anything you can do to protect your computer from physical access can be circumvented by a reasonably knowledgeable cracker.

Wait, I take that back. If you want, you can put your computer in a safe with holes for the cables. (If you do that, make sure to install liquid cooling.) Then the techno-cracker also has to be a safe-cracker.

---

### Post by soundguy24 on 2006-08-30
> **Boris2 said:**
> Which recovery mode do you mean?

Booting from a CD and recovering the system?
-> You could disable booting from CD and set a BIOS-password. But beware: BIOS-passwords can be reseted easy.

Booting the failback-system from grub?
-> Set a grub-password and protect alternatives. But I'll still be possible to access you system with a boot-medium (see above)


The only way (known to me) to protect you against this is to secure your room ;-)

[SIZE="2"]ok, I know about BIOS passwords--can you tell me about grub passwords?[/SIZE]

---

### Post by soundguy24 on 2006-08-30
> **aysiu said:**
> Anyone who has physical access to your computer has root access anyway...

[SIZE="2"]I guess I understand. :???: [/SIZE]

---

### Post by soundguy24 on 2006-08-30
> **skymt said:**
> If you want, you can put your computer in a safe with holes for the cables. (If you do that, make sure to install liquid cooling.) Then the techno-cracker also has to be a safe-cracker.

[SIZE="2"]nice.[/SIZE]

---

### Post by yomimono on 2006-08-31
You can set up grub to only allow you to boot a kernel if you input a specific password.  Here's how:

From a command line, type grub-md5-crypt and feed it the password you'd like to require in order to boot a kernel.  It will spit out the salted md5 hash of that password.  Copy that, and then edit /boot/grub/menu.lst as superuser (with sudo).

In /boot/grub/menu.lst, you should see a section that looks like this:

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

Remove the "# password topsecret" line and replace it with:
password --md5 [the password that grub-md5-crypt gave you] .

Now find the kernels you would like to restrict, for example:

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

And insert between "title" and "root" lines the word "lock".  Now grub will require that password on boot.

Please note that this isn't completely secure - the caveats above about physical access still hold true, as well as [some others](http://www.linuxquestions.org/linux/answers/Security/Breaking_RESETTING_grub_password) .  If you want more grub info, the man pages are pretty good, as well as the [online security documentation](http://www.gnu.org/software/grub/manual/html_node/Security.html).

---

### Post by Klaidas on 2006-09-01
Ooor, you give root a password, and it is required to enter to boot in recovery mode ;)

---

### Post by yomimono on 2006-09-01
Are you sure about that?  Usually booting into single-user mode puts you straight at a root prompt, whether you have a password set or not.  I'll admit I've never done this in Ubuntu before, but that's how it's worked on other Linux distros.

-Mindy

---

### Post by amo-ej1 on 2006-09-01
it's possible to have grub prompt you for a password so you won't be able to boot into single user mode. This is described at the following location:([http://http://www.gentoo.org/doc/en/security/security-handbook.xml?part=1&chap=2#doc_chap2]("http://http://www.gentoo.org/doc/en/security/security-handbook.xml?part=1&chap=2#doc_chap2")

HOWEVER:
a) booting from a livecd will allow you to mount the disk and change the password
b) removing the hard disk and placing it in a different machine and mounting it there will also allow you to modify the password ...

The rule stays if you have physical access to the machine, you have root access by definition, altough it may require some 'effort' to get there.

---

### Post by galileon on 2006-09-01
encrypt the whole thing?

---

### Post by rainbow_will on 2006-09-04
hi folks,
 I discovered that you can go into recovery mode when you switch your computer on, and get root access without even entering a password. Where is the security in that then?

will.

---

### Post by monktbd on 2006-09-04
anybody who has physical access to your computer has already compromised it. a reboot could also happen into a live-cd. and then the user is root as well.

the recovery mode itself is not a security issue.

---

### Post by taurus on 2006-09-04
If you don't want anybody to boot your machine into recovery mode, then don't include it in /boot/grub/menu.lst!!!  It isn't too hard to do...

---

### Post by meborc on 2006-09-04
consider for a monemt that you forget your password... to change it, the recovery mode is essential... 

btw - it is possible to protect grub with password, or just make the recovery mode invisible in grub menu by commenting it out in the menu...

so it is possible to make your computer a fortress (in terms of your little sister)... just the default should be so that you can recover any catastrophy by booting into recovery mode...

---

### Post by catlett on 2006-09-04
The default is for the owner to have access to his/her own computer. If you feel your computer is "too" available to other people and they can boot your computer without your being there, you can do 2 things.
1.BIOS security. Do 2 things with your bios. First set your computer to boot to the hard drive first. This way noone can put a linux live cd or a windows recovery cd in and get access to your hard drive's data. Second set a bios password so noone can enter bios without the password and change that setting.
2.GRUB security. First uncomment the line for the recovery mode in your grub menu list with a # put in front. That way it will not appear in the grub menu. If you need the mode, you can uncomment the line and it will appear on next boot. Second set a grub password. Then noone can select an entry in the menu without the password.

A little research goes a long way. Reactionary sarcasm gets you nowhere.

---

### Post by monktbd on 2006-09-04
> **catlett said:**
> 
2.GRUB security. First uncomment the line for the recovery mode in your grub menu list with a # put in front. That way it will not appear in the grub menu. If you need the mode, you can uncomment the line and it will appear on next boot. Second set a grub password. Then noone can select an entry in the menu without the password.


while i agree with number two i am not sure how much sense it makes to disable recovery mode in combination with it.
of course there can be the option of allowing other people to use grub but not recovery mode.

usually recovery mode is needed when the normal boot fails.
if i disabled it then i need a live cd anyway to do my recovery administrative work.

---

### Post by anaconda on 2006-09-04
commenting recovery-mode out from menu.lst isn't enough, because then you still could press 'e' in grub and edit any entry.. and change it to be "recovery-mode", or just press 'c' to get to grub-console and enter the commands manually and again you would be in "recovery mode" with root rights.

But it is possible to password-protect grub too.. so that you would need a password if you want to edit or manually enter boot commands..

And  if the "intruder" has physical access to your machine, he could just remove the hd from your machine, put it to another machine, whose bios he can adjust to boot from CD and  then he would have access to your (unencrypted) files..

---

### Post by rainbow_will on 2006-09-08
ok thanks for the replies folks.

---

### Post by williamts99 on 2006-10-04
I was wondering why it gives me root access when I choose single user mode from grub?  This seems like something that should not be there by default.  I have tested it as far as going and deleting files from two different users.  Even if users don't have access to the box(just the keyboard and monitor) they can have root access.  Is this a planned issue or will it be removed before shipping the final version?

---

### Post by orb9220 on 2006-10-04
This is consider like recovery mode in dapper. If you mess up yer system.

---

### Post by tenn on 2006-10-04
I have posted about this before, I think it is stupid why bother having a password at boot for you user account if any body can just boot in rescue mode.

---

### Post by gnomeuser on 2006-10-04
a) That can be optionally disabled
b) Anyone with physical access to your machine can wreck it, it's that simple.. deal with it
c) It's mighty useful for fixing your box when it breaks
d) It doesn't represent any more of a security threat than having boot via USB/CDROM/net enabled since any kiddie with a Knoppix CD can own you in less than 30 secs

---

### Post by chrisccoulson on 2006-10-04
You can lock the entry in the Grub menu list so it requires a password to boot to single user mode can't you?

---

### Post by tenn on 2006-10-04
It should be pass protected from install other distros do this or at least give the option during install, the default way it is like having a button
saying login in here free access it makes it to simple.

---

### Post by Khaine on 2006-10-04
This has always been a part of linux since, well, forever.  As linux is mainly used in a server environment physical security was not a priority.

---

### Post by givré on 2006-10-04
Keybuck reply to that issue :
> If you have the physical access to the machine that this implies, you could smash it to pieces with a very large hammer. It's a kind of "delete without possibility of undelete".

If it were just access to the files you wanted, you could open the box, take the hard drive out, and mount it from another machine.

Or if it were just login access you wanted, you can power cycle the box and add "init=/bin/sh" to the kernel command-line.

---

### Post by dinxter on 2006-10-04
i tend to set up a root password, that requires to be entered on single user mode

---

### Post by Lord Illidan on 2006-10-04
> **gnomeuser said:**
> 
d) It doesn't represent any more of a security threat than having boot via USB/CDROM/net enabled since any kiddie with a Knoppix CD can own you in less than 30 secs

Unless you encrypt your system or else keep it in a safe physical location..

---

### Post by finalbeta on 2006-10-04
I don't like they way people here go about security. Yes, it's true , anyone with physical access can do anything. But you might NOT wanna accommodate them like this.
If you do think like this, why bother locking your desktop or having passworded accounts on a home PC. 

Some bug in edgy let's you log in to a tty as root by pressing cntr-win-del twice. I had the exact same reaction. "It's physical access..."
That's like saying windows should just set up a backdoor for hackers after install because it's insecure anyway.

---

### Post by moonbeam on 2006-10-04
The default behaviour is probably the best one.  

1) My thinking is that the single user mode is actually, potentially useful for anyone this way.  Default to a password on installation and you WILL be in situation where a large percentage of people will forget the password when they need it.

2) As has been pointed out repeatedly, since time immemorable, if someone has physical access then the strength or lack of password is really the least of your worries.  Seriously, the subset of people who know how to exploit single user mode but would be in any way hindered by it being password protected is, I suspect, very small.  

3) If you're seriously concerned about those who have physical access to the system then encrypt!

The security gain from passwording single user mode vs the the benefit probably isn't worth it.  

Blah... it has all been said before.

regards,

---

### Post by az on 2006-10-04
> **finalbeta said:**
> I don't like they way people here go about security. Yes, it's true , anyone with physical access can do anything. But you might NOT wanna accommodate them like this.
If you do think like this, why bother locking your desktop or having passworded accounts on a home PC. .

It has nothing with going about security - it is what it is.  Locking your desktop does nothing to protect your box, nor would setting a root password if someone can physically touch your computer.  Period.  You want to address that security issue?  Get a room with a big lock on it.

Also, having passworded accounts is to secure your box from remote attacks.

> **finalbeta said:**
> 

That's like saying windows should just set up a backdoor for hackers after install because it's insecure anyway.

Not at all.  It is just a realistic approach to the situation.  Security is about being secure, not giving you a false sense of security.

---

### Post by finalbeta on 2006-10-04
This is ridiculous. Why use flame retardant, in the end it all burns anyway right?...
Using flame retardants might give people a false sense of security!

---

### Post by Binary Jay on 2006-10-04
It poses a problem if your significant other is linux savvy and wants to go looking for your private porn directory.

---

### Post by williamts99 on 2006-10-04
I guess a lot of people missed the part where there is **only access to the keyboard and monitor, not the machine itself**.  I guess it just seems to me that something like this by default should be that if you don't have access to the machine, the defaults should be secure.  For example, no, you can't put in a knoppix CD, or take a hammer to the HD if you don't have access to the machine.  No you can't plug in a USB device if you don't have access to the machine, etc etc.  

As far as taking a ton of skill to cause damage?  Naa, that doesn't take a lot of skill at all, it's pretty easy to delete everything on the HD if given the chance, so encryption there doesn't do anything.  Nor does it help with using wget and installing anything as root.

It is almost like the issue where you can hit ctrl+alt+f1 and then ctrl+alt+del twice and get root.  [http://ubuntuforums.org/showthread.php?t=270620](http://ubuntuforums.org/showthread.php?t=270620) Though I am sure that this one will be fixed pretty quickly.

As far as recovery, that makes sense because it happens, but usually you would have access to the machine if you were going to do any kind of recovery, hence you could pop in a CD or whatever to continue recovery efforts.

It just seems to me that it shouldn't be something that is enabled by default.

---

### Post by Titan_Prometheus on 2006-10-28
Ok, So I'm having trouble with mt virtual terminals, so i boot in recovery mode when i discovered that recovery mode logged my into root, with no password or anything. I believe that this is a grave security breach, i know that there is no root password set, but shouldn't it at least ask for a user and password?

---

### Post by mark_g on 2006-10-28
Well... almost everyone who uses linux/unix knows that the main account's name is root, so there's really no point to asking the username. Best is to always set a password for root.

---

### Post by tonyr1988 on 2006-10-28
No, that's the point of recovery mode: under a worse case scenario (let's say: something corrupts the file that holds your username / password), it lets you get in and recover.

The only way someone could get into recovery mode on your computer is through physical access. If they've got physical access to your computer, then they would be able to just boot a LiveCD and get root access anyway, so it's useless to try and make recovery mode protected.

As long as you don't always boot into recovery mode (or, preferably, don't do it while online), then you'll be fine.

---

### Post by monkeydust on 2006-11-03
Hello all

Can someone clear something up for me?

When I choose "Recovery Mode" in GRUB, it presents me with
the prompt. Fine. Except I noticed that it's logged me in
as ROOT, without asking for any password, and I can delete/modify
files in my usual home folder and in system locations.

Can someone explain why this ISN'T a security hole?

Thank you!

David

---

### Post by Anonii on 2006-11-03
Been there. Discussed that.

[http://ubuntuforums.org/showthread.php?t=151338](http://ubuntuforums.org/showthread.php?t=151338)
[http://ubuntuforums.org/showthread.php?t=247403](http://ubuntuforums.org/showthread.php?t=247403)
[http://ubuntuforums.org/showthread.php?t=138497](http://ubuntuforums.org/showthread.php?t=138497)
[http://ubuntuforums.org/showthread.php?t=109464](http://ubuntuforums.org/showthread.php?t=109464)

Just the biggest threads I found about this. And there are many others, smaller.

---

### Post by monkeydust on 2006-11-03
d'oh - cheers.

Had my stupid hat on today.

---

### Post by emarkay on 2006-12-13
I searched "recovery Mode" and only found 21 'hits'.  So I'll ash a few Q's
I know this mode gives you root access, but what else can you do in that mode, that you can't do in the GUI?

I guessed that "exit" takes out out of it and reboots, but sometimes also puts me into the Ubuntu desktop.

I have also (once today)  found that I had booted into recovery mode, and hit exit, and got the GUI, and then forgot I was in that mode and was on the Internet.  Is that a security risk?

Why is there not "flag" on the GUI that you are in "recovery mode"?

Are there any text based "help" screens in that mode to show the options?

Thanks!

---

### Post by emarkay on 2006-12-14
Anyone?

---

### Post by darrenm on 2006-12-14
> **emarkay said:**
> I searched "recovery Mode" and only found 21 'hits'.  So I'll ash a few Q's
I know this mode gives you root access, but what else can you do in that mode, that you can't do in the GUI?

I guessed that "exit" takes out out of it and reboots, but sometimes also puts me into the Ubuntu desktop.

I have also (once today)  found that I had booted into recovery mode, and hit exit, and got the GUI, and then forgot I was in that mode and was on the Internet.  Is that a security risk?

Why is there not "flag" on the GUI that you are in "recovery mode"?

Are there any text based "help" screens in that mode to show the options?

Thanks!

It just gives you root access to the shell. Nothing more, nothing less. You can do the same in the GUI by opening a terminal, su - 'ing to root or by pressing CTRL-ALT-F1 in the GUI and logging in as root.

typing exit in recovery mode won't put you in the GUI. I imagine you are not actually in recovery mode when that happens.

BTW recovery mode isnt a mode, its just not loading some startup scripts like X

flag? whats flag?

Help is available by typing man <any prog you need to run>

---

### Post by mykalreborn on 2006-12-14
or type man -k <application or whatever you want to search> if you don't know for sure.

---

### Post by emarkay on 2006-12-14
> **darrenm said:**
> It just gives you root access to the shell. Nothing more, nothing less. You can do the same in the GUI by opening a terminal, su - 'ing to root or by pressing CTRL-ALT-F1 in the GUI and logging in as root.

typing exit in recovery mode won't put you in the GUI. I imagine you are not actually in recovery mode when that happens.

BTW recovery mode isnt a mode, its just not loading some startup scripts like X

flag? whats flag?

Help is available by typing man <any prog you need to run>

OK thanks.  Is there any additional security issues - is it less secure from hackers and malware in this mode - I mean is EVERYTHING now root (SU) enabled?

I know I was in Recovery mode because I had text based, not graphic based boot up messages!  I am sort of confused about this now.

Flag - like something onscreen to remind you that you have selected and are using the "Recovery Mode".  Windows uses "Safe Mode" and it places those words at the corners of the screen.

Thanks!

---

### Post by darrenm on 2006-12-14
> **emarkay said:**
> OK thanks.  Is there any additional security issues - is it less secure from hackers and malware in this mode - I mean is EVERYTHING now root (SU) enabled?

Yep. but lets face it. If someone has physical access to your computer and knows shell commands then not allowing them root as a boot option won't change much.

> **emarkay said:**
> I know I was in Recovery mode because I had text based, not graphic based boot up messages!  I am sort of confused about this now.

Recovery mode is not just the command line. The command line is there all the time, not just in recovery mode. Recovery mode is only there when you boot the PC and choose recovery mode as a boot option.

> **emarkay said:**
> Flag - like something onscreen to remind you that you have selected and are using the "Recovery Mode".  Windows uses "Safe Mode" and it places those words at the corners of the screen.

Hmm -see what you mean, the hash gives it away though - If you see # then think before pressing return.

---

### Post by igknighted on 2006-12-14
> **emarkay said:**
> OK thanks.  Is there any additional security issues - is it less secure from hackers and malware in this mode - I mean is EVERYTHING now root (SU) enabled?

I know I was in Recovery mode because I had text based, not graphic based boot up messages!  I am sort of confused about this now.

Flag - like something onscreen to remind you that you have selected and are using the "Recovery Mode".  Windows uses "Safe Mode" and it places those words at the corners of the screen.

Thanks!

If you *really* are logged in as root then your desktop should revert to the installed default, not your customized user desktop.  I would recommend using a desktop background for the root account if you have it enabled that warns you that you are root (like somethign red for exmple)

---

### Post by boilertech on 2007-02-01
I have found a security flaw here. When Grub starts. If you pick "recovery mode" You end up at the command line with root access. If you then type "startx" You will be given full root permission in KDE/Gnome.

---

### Post by p!=f on 2007-02-01
> **boilertech said:**
> I have found a security flaw here. When Grub starts. If you pick "recovery mode" You end up at the command line with root access. If you then type "startx" You will be given full root permission in KDE/Gnome.
You need physical access to the computer first... :)

You can protect GRUB with a password btw. :)

---

### Post by PilotJLR on 2007-02-01
Yep... even a BIOS password.

Software security systems assume the machine is secured physically, which is why servers should be in a secure room.
This is not a bug.

---

### Post by CSMatt on 2007-02-28
It is of course dangerous to your computer if anyone (including yourself) is running as root, as that person can intentionally or unintentionally sabotage the computer.  Well, when booting in recovery mode, I noticed that you are prompted with a root prompt.  Worse still, no password is even asked for.  This means that anyone with access to the computer could boot into recovery mode and get unquestioned root access.  I'm not as worried about this, as the most likely candidates to ever gain direct access to this computer don't have a clue about Linux, let alone commands to use at a root prompt.  But this is still a big security breach.  While a BIOS password could prevent this, I don't see why a text logon can't be initiated instead, or at the very least a password asked for before unrestricted root access is given.

Why is this allowed to happen?

---

### Post by aysiu on 2007-02-28
Anyone who has physical access to your computer has root access anyway--that's why.

Read more here:
[http://psychocats.net/ubuntu/security#recoveryrisk](http://psychocats.net/ubuntu/security#recoveryrisk)

---

### Post by 23meg on 2007-02-28
It's a feature, and not a flaw. Recovery mode is also known as "single user mode", and that single user is naturally root.

The reason no password is asked for is that the root account is disabled by default. If you enable it with ```
sudo passwd root
```the password you set will indeed be asked for. But that's a departure from Ubuntu's basic security model.

The rationale is that if someone has unrestricted physical access to your computer, they can bypass pretty much any software security measure anyway. No software security model can do something about flaws in physical security; the latter is your responsibility. Even if your recovery mode is password protected, they can bypass it by booting with a live CD. Even if you put in a BIOS password to disable CD booting, assuming physical access is unrestricted, they can reset it by removing the BIOS battery. Having gone that far, they can even just grab your HD and use another computer to access your data.

---

### Post by CSMatt on 2007-02-28
My computer only has unrestricted access in the sense that I don't permit anyone from using it without my permission.  Though in practice, considering that others have this same policy, this is unenforceable if you ever happen to be away from the computer.  That's pretty much the status of almost every publiclly accessible computer and every unsupervised private computer.  While it may be true that security is a pipe dream in these conditions, that doesn't mean that some sort of way to prevent the exploitation of known flaws shouldn't at least be attempted.  By your logic, we shouldn't even bother trying to protect against viruses since the virus will almost always mutate into some undocumented form.

You're suggesting that every unsupervised computer should be locked away.  But even then, you can still break a lock, no matter how "unbreakable" it may be.

---

### Post by bodhi.zazen on 2007-02-28
> **CSMatt said:**
> My computer only has unrestricted access in the sense that I don't permit anyone from using it without my permission.  Though in practice, considering that others have this same policy, this is unenforceable if you ever happen to be away from the computer.  That's pretty much the status of almost every publiclly accessible computer and every unsupervised private computer.  While it may be true that security is a pipe dream in these conditions, that doesn't mean that some sort of way to prevent the exploitation of known flaws shouldn't at least be attempted.  By your logic, we shouldn't even bother trying to protect against viruses since the virus will almost always mutate into some undocumented form.

You're suggesting that every unsupervised computer should be locked away.  But even then, you can still break a lock, no matter how "unbreakable" it may be.

LOL

You can remove or hide the (Grub) entry.

But yes, physical access if bad news.

You might like this book

[http://www.apress.com/book/bookDisplay.html?bID=395](http://www.apress.com/book/bookDisplay.html?bID=395)

---

### Post by 23meg on 2007-02-28
> **CSMatt]My computer only has unrestricted access in the sense that I don't permit anyone from using it without my permission. Though in practice, considering that others have this same policy, this is unenforceable if you ever happen to be away from the computer. That's pretty much the status of almost every publiclly accessible computer and every unsupervised private computer.[/QUOTE]

True. If you don't have the computer protected by a bodyguard and/or locked safely, that's a compromise of physical security. Nothing that any software security model can do something about.

[QUOTE=CSMatt]While it may be true that security is a pipe dream in these conditions, that doesn't mean that some sort of way to prevent the exploitation of known flaws shouldn't at least be attempted.[/QUOTE]You can't amend flaws of physical security with software security. If your potential attackers are going to be turned away with a BIOS password, set one said:**
> By your logic, we shouldn't even bother trying to protect against viruses since the virus will almost always mutate into some undocumented form.That's got nothing to do with what I'm saying. I'm talking about two independent areas of security that you have to care about if you want "absolute security". It's not *my* logic, by the way, but the logic behind pretty much every half decent software security paradigm.

[QUOTE=CSMatt]You're suggesting that every unsupervised computer should be locked away. But even then, you can still break a lock, no matter how "unbreakable" it may be.[/QUOTE]If there were such a thing as absolute security, you'd be right to infer that from what I said, but as is often said, there's no absolute security, but only varying levels of insecurity. Every precaution can be bypassed; good security is about employing the right methods for your given situation. And you shouldn't expect general purpose software to predict what's best for you; if its policies don't suit you, you should bend them to suit, not expect them to bend to suit you.

---

### Post by aysiu on 2007-02-28
I've merged in a couple of other similar threads so people can get some other perspectives on the issue.

---

### Post by aysiu on 2007-02-28
In case you want to hear some more opinions about this, I've created a little megathread on the issue:
[Is root in recovery mode a security risk?](http://ubuntuforums.org/showthread.php?t=372262)

---

