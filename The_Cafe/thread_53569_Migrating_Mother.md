---
title: "Migrating Mother"
date: 2005-08-01
forum: The Cafe
---

### Post by Brunellus on 2005-08-01
So my mother has now inherited *nosferatu*, my old box, as an email-checking, web-browsing, calendar-maintaining, and occasional word-processing machine.  

She's tech-averse and computer-diffident, and any explanation of how things work brings a look somewhere between fear and panic on her face.

I had tried to migrate her to Linux before, with SuSE 9.1 and KDE, but that box was frustratingly unstable (because I kept breaking it, since I didn't really know how to make it all work right back then).  Also, KDE 3.2 was dog-slow on that machine.

I have encouraged her to sit back, play around with the system, send some emails, do some web browsing, and generally get comfortable. 

"Does it have a manual?" she asked me.

"uh...no, not really.  There's online help, but you should just go ahead and ask me.  For *urgent* problems, call me on my cellphone.  For less urgent ones, keep a pad next to the computer and we'll go over them when I get back from work."

Sharing this box will be my youngest brother, ten years old, and not yet set in his computer ways.  Mainly, he'll be using AbiWord, eboard (he's a keen chess player), and TuxType.  He thinks it's cool--he has his own user account and everything, and he can play chess with the kitchen computer.  

Needless to say, there are some administrative things to work out.  I am tempted to enable the root password and remove mom and my brother from the sudoers group, to minimize the chance of accidental breakage....that way they can do all the "preferences" settings (background, etc) without accidentally blundering into synaptic or something.  

Second, i have to find some way to keep ESD from starting up with GNOME...but that's fairly trivial.

I'll be uptdating the forum with the progress of this peculiar experiment.  I don't expect my mom to become 1337 or anything, just to get over her computerphobia for a bit.  The fact that I'll not have to worry about crapware on this box is a blessed relief, since my mother clicks on almost anything....

---

### Post by ubuntu_demon on 2005-08-01
nice!

I've also considered an Ubuntu machine for my dad but since he didn't own a machine at all I did a bit of investigation. I came to the conclusion that an apple imac is better suited for him see : [http://www.ubuntuforums.org/showthread.php?t=19774](http://www.ubuntuforums.org/showthread.php?t=19774)

Why not creating a user for yourself and adding that one to the sudoers file and removing the other sudoers ? 

Also you should install openssh so you can acces it from anywhere (but make sure they use safe passwords)

---

### Post by Brunellus on 2005-08-01
[QUOTE=ubuntu_demon]nice!

I've also considered an Ubuntu machine for my dad but since he didn't own a machine at all I did a bit of investigation. I came to the conclusion that an apple imac is better suited for him see : [http://www.ubuntuforums.org/showthread.php?t=19774](http://www.ubuntuforums.org/showthread.php?t=19774)

Why not creating a user for yourself and adding that one to the sudoers file and removing the other sudoers ? 

Also you should install openssh so you can acces it from anywhere (but make sure they use safe passwords)[/QUOTE]
 well, since it used to be my old computer, I am still a user (and sudoer).  So I guess I could just remove them from sudoers.

openssh is already up and running.  It's a learning experience for me, too.  I can ssh to the machine from anywhere inside our home network, but I haven't yet managed to figure out how to do it from the wilds of the internet.  Most maintenance might actually end up being 'sneakernet' around the house.  If/when I see her working, I might ssh into the box to do some updates/upgrades with apt.  I welcome the opportunity to sharpen my command-line skills....they make my little brother think I'm uber1337, but I'm really not.

---

### Post by somuchfortheafter on 2005-08-01
ssh uses port 22 i believe so setting port forwarding to your router to the computer's ip address and leaving port 22 open should do the trick....

---

### Post by ubuntu_demon on 2005-08-01
[QUOTE=Brunellus]well, since it used to be my old computer, I am still a user (and sudoer).  So I guess I could just remove them from sudoers.

openssh is already up and running.  It's a learning experience for me, too.  I can ssh to the machine from anywhere inside our home network, but I haven't yet managed to figure out how to do it from the wilds of the internet.  
[/quote]

just forward port 22 on your router/gateway to the right machine

[QUOTE=Brunellus]
Most maintenance might actually end up being 'sneakernet' around the house.  If/when I see her working, I might ssh into the box to do some updates/upgrades with apt.  I welcome the opportunity to sharpen my command-line skills....they make my little brother think I'm uber1337, but I'm really not.[/QUOTE]

you'll become 1337 eventually :-P:-P:-P:-P:-P:-P:-P

---

### Post by BWF89 on 2005-08-01
[QUOTE=Brunellus]So my mother has now inherited ***nosferatu***, my old box, as an email-checking, web-browsing, calendar-maintaining, and occasional word-processing machine.[/QUOTE]
You named your old computer after a vampire :shock: .

---

### Post by varunus on 2005-08-01
You can disable esd in GNOME from "system->preferences->sound", just uncheck "sound server startup."

But why do you need to?  Doesn't [this](http://www.ubuntuguide.org/#configuresoundproperly)  howto let you hear sounds through both ESD and ALSA?  (I would advise leaving sounds for events checked, I've had no problems with both ESD and ALSA running after that howto).

---

### Post by Brunellus on 2005-08-01
[QUOTE=BWF89]You named your old computer after a vampire :shock: .[/QUOTE]
 naturally.  I called it 'nosferatu' because it wouldn't die.  It originally ran winME, until it was finally rendered unbootable by God only knows what.  It was reborn as a SuSE 9.1 box for the whole family.  That experiment lasted until they bought a new windows computer for my brother....so it became my computer. I ended up installing, then re-installing Warty on it.

My middle brother calls it the machine that won't die--hence, nosferatu.

---

### Post by Brunellus on 2005-08-02
So my mother is able to send and receive e-mails and do a bit of websurfing.  

My middle brother noted an interesting behaviour pattern--she checked her e-mail midday, and, finding that no-one had written her, immediately ran downstairs to the Windows computer to see if it wasn't linux's fault.  

She is also unusually timid about clicking anything.  I had to show her (again) how to sort messages in Evolution by sender, date, subject, etc.  Never mind that this is the same as it was in OE and in any other mail client I've shown her how to use.  *sigh*

The positive is that she's using the computer now, and actually checking her e-mail frequently, which is a good thing.  I even showed her how to use the calendar in Evolution....it remains to be seen if she'll pick up on how nifty that tool is.

I was able to fix the sound bug in gnome thanks to ubuntuguide.  Just for fun, I did it remotely from my computer, so I could check *my* e-mail at the same time.  Huzzah for ssh!

My father was very keen to get a username on that computer as well, so I set up an account for him, too.  He's a little less timid than my mother, and is quite possibly a better candidate for FOSS adoption.  He's already been impressed by OpenOffice and Firefox running on his new winXP laptop.  He has his doubts as to the sustainability of the FOSS model--"how do they make their money?"--but he's happy with the apps so far.  Now to hook him to the OS(es).....

Technical question:  "sudoers" doesn't seem to appear as a group in the regular 'groups and users' gui in gnome.  Can anyone point me to a CLI howto on this, so that I can remove everybody but me from the sudoers list?

---

### Post by varunus on 2005-08-02
The sudoers list isn't in GNOME.  To access it, type "sudo visudo" from a console.  This will let you edit the sudoers file.

---

### Post by poofyhairguy on 2005-08-02
[QUOTE=Brunellus] He has his doubts as to the sustainability of the FOSS model--"how do they make their money?"--but he's happy with the apps so far.  Now to hook him to the OS(es).....[/QUOTE]

Your mom might be a lost cause if she won't learn to trust. Marketing will do that to a person. You might hook your dad if you answr his question. Here is the answer older people like to here (its true like many others).

If you look at who actually develops Linux and the GNU desktop, you will see many hardware companies involved (Intel, IBM, Realtek, etc.). For example, most Intel hardware works great with Linux because Intel spent the time to make it freat. Why?

Linux is a way for hardware companies to decrease the cost of software for their customers. If billions of computing dollars every year are spent on MS, then that means that a lot of resources are tied up in software. If OSS wins, then software will cost nothing and therefore people would spend more money on hardware. OSS for these companies might not make a direct profit, but if it cuts out MS eventually some of that money will be spent on new hardware.

Thats a true answer older people seem to like. Its not the only answer (some do it to pump resumes and get jobs -Gentoo guy, some do it to sell service and support (Red Hat), some do it just to be nice- like Mark the leader of Ubuntu, but none of those answers sound as good to older people like the first does. 

Its like they have to hear about the support of big companies or they think its not worth anything.

---

### Post by Brunellus on 2005-08-02
[QUOTE=poofyhairguy]Your mom might be a lost cause if she won't learn to trust. Marketing will do that to a person.[/QUOTE]

This isn't marketing, I don't think....just ignorance.  

Part of this is my own fault.  The last migration attempt was with a horribly broken SuSE install (damn you, rpm -f !).  

I think a good bit of is general distrust of technology.  We had to work very hard to get her to carry a mobile phone.  We had to work *harder* to convince her to turn it on, or to remember to carry it when she left the house!  I don't want her to go all 1337 on me--that might freak me out--but I do at least want her to get into the information age.

---

### Post by Brunellus on 2005-08-05
[QUOTE=Brunellus]This isn't marketing, I don't think....just ignorance.  

Part of this is my own fault.  The last migration attempt was with a horribly broken SuSE install (damn you, rpm -f !).  

I think a good bit of is general distrust of technology.  We had to work very hard to get her to carry a mobile phone.  We had to work *harder* to convince her to turn it on, or to remember to carry it when she left the house!  I don't want her to go all 1337 on me--that might freak me out--but I do at least want her to get into the information age.[/QUOTE]
 bumpity-bump and an update:

Dad is turning out to be a keen user...even if he's not clear which password applies where.  He's gotten so used to webmail interfaces for non-business e-mail that I had to go over the whole process of logging into his POP account through Evolution again.  He saved his password, and now he's more comfortable with the whole deal.

On the whole, I find my father to be more adaptible, technically, than my mother, if no less timid in some respects.  He has been a computer user since DOS 3, though--my mother hardly touched anything electronic, so that enters into it.

Reviews seem to be good.  They're not pushing the machine too hard, so they're not complaining as badly as I did when I tried to use the GIMP, say, to edit big photos.  In fact they didn't even notice that I'd left Folding@Home running as a background process. 

Maintenance via SSH is great.  I highly recommend this method to anyone who has become the family ComputerGuy!

---

### Post by Brunellus on 2005-08-10
[QUOTE=Brunellus]bumpity-bump and an update:

Dad is turning out to be a keen user...even if he's not clear which password applies where.  He's gotten so used to webmail interfaces for non-business e-mail that I had to go over the whole process of logging into his POP account through Evolution again.  He saved his password, and now he's more comfortable with the whole deal.

On the whole, I find my father to be more adaptible, technically, than my mother, if no less timid in some respects.  He has been a computer user since DOS 3, though--my mother hardly touched anything electronic, so that enters into it.

Reviews seem to be good.  They're not pushing the machine too hard, so they're not complaining as badly as I did when I tried to use the GIMP, say, to edit big photos.  In fact they didn't even notice that I'd left Folding@Home running as a background process. 

Maintenance via SSH is great.  I highly recommend this method to anyone who has become the family ComputerGuy![/QUOTE]
 Bump and an update.

Mom *loves* the computer now!

Little things seem to do it for her--the fact that it's always ready for her is huge.  She now checks her e-mail compulsively.  She isn't the fastest typist ever, nor does she do more than e-mail and web browsing on the box, but for those limited uses, the computer has been a resounding success.

The middle-click paste command got a"cool!".

No frustrations yet.  I have to credit GNOME, which is different enough from Windows to force her to realize "hey, maybe I should think about doing things a little differently" but not so different as to scare her off.  (I'd hate to think of what she would have made of Fluxbox or IceWM)
Now to see if she starts playing with it....

---

### Post by bk452 on 2005-08-11
[QUOTE=Brunellus]This isn't marketing, I don't think....just ignorance.  

Part of this is my own fault.  The last migration attempt was with a horribly broken SuSE install (damn you, rpm -f !).  

I think a good bit of is general distrust of technology.  We had to work very hard to get her to carry a mobile phone.  We had to work *harder* to convince her to turn it on, or to remember to carry it when she left the house!  I don't want her to go all 1337 on me--that might freak me out--but I do at least want her to get into the information age.[/QUOTE]
 Part of this is my own fault. The last migration attempt was with a horribly broken SuSE install (damn you, rpm -f !).***

RPMs will put you so far down in dependency hell that you'll switch to Ubuntu.

---

### Post by Brunellus on 2005-08-11
[QUOTE=bk452]Part of this is my own fault. The last migration attempt was with a horribly broken SuSE install (damn you, rpm -f !).***

RPMs will put you so far down in dependency hell that you'll switch to Ubuntu.[/QUOTE]
 ...which is precisely what happened.

---

