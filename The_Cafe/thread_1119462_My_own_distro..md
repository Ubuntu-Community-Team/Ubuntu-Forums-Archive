---
title: "My own distro."
date: 2009-04-08
forum: The Cafe
---

### Post by Isilion on 2009-04-08
hi. i was trying to do a backup of my system. looking for at google, i found an applicattion in gnewsense repos called 'remastersys'. its cool, simply makes an installable livecd from your system.

later i wanted to do the same, but this time a copy of ubuntu including al synaptic packets y use, like anjuta, amsn, amarok4, firefox, even the non-free-flash plugin.

the target of 'my distro' is that i havent got to install any program before a system reinstall, or minimize the programs that i must install, every time that system crashes.

so, i made a new partition on the hd, installed a fresh copy of ubuntu minimal, and spent my time looking for packages and packages from diverse repos (ubuntu, linuxmint, and gnewsense. also the repos where you can find the latest amarok and kde files). then i runned remastersys and made an iso of my system. works great, its less than 2gb and can run in livecd mode, almost in my pc wich have 4gb of RAM.

then i wondered if i could share it with my friends. i think that, even including non free software, it will be ethical to share with others. Googling is possible for everybody, anyone can make the same as me; (i've noticed that some packages found at the ubuntu repos not are present in debian ones. or am i wrong?)and, in the case that i want to do a new, profesional finished, linux distro, i dont know if i'll have the rights to ask money for my work. im so confused in these themes, so i ask you plz to resolve my doubts. it would be wonderful if I, as programmer, student, musician and music lover, developer, etc, could share the system i use with others, and also get paid (i mean to dedicate in linux in a profesional way) 

in example, i want to do a rpg game using fenix engine. my distro will include the latest dev files of the game, and i would share it with my classmates, who help me with the game. i am free to do it? and even to upload the distro to internet, in the case i need to extend my web of developers and testers? :S

in other case, im programmer. it would be wonderful, to make a distro and dedicate my live to, and orientate my job to free software projects, some with lucrative goals. that's another doubt.

in any case, i think that's not bad what is mentioned at ubuntu faq. canonical puts emphasys in tell you that you can make remixes of ubuntu and share it. but if you want money for it, you have to ask permission. and remove every ubuntu logo. and be explicit that you dont have anything to see with ubuntu or canonical. 

but if ubuntu is debian based, why not to base my distro in debian? i downloaded it and reinstalled every program. im now testing it and its perfectly stable.

in short, my doubts are:

can i share a ubuntu-based distro? and also ask for money for it?
can i share those two distros, with you, for example? i mean the ubuntu-based and the debian-based. im so confused with licenses, and i dont see the difference between having nonfree software installed in your machine, or awaiting you in a repo :S

i hope to not sound stupid :S and not to be saying barbarities. i wait your response.

---

### Post by dyous87 on 2009-04-08
I am interested in starting a new distro based on Ubuntu or Linux Mint for the purpose of packaging with some low powered affordable netbooks and mini desktops. I've been trying to start this off and have been looking for people to help out.

The goal is to make an extremely polished, easy to use yet powerful system with EVERYTHING a typical user would need out of the box.

If you are interested in working on a new distro perhaps this can be an opportunity for us to work together. Let me know :)

As far as the two distros you have already made, I believe you can share them with friends, you can also sell them for money if people are willing to pay you for it, so long as you keep all the code open and you make any changes you make public. Depending on which country you are in however, certain non free software, such as MS Fonts and Restricted Extras may be illegal to package by default. 

Thanks,
David

---

### Post by cariboo on 2009-04-08
> can i share a ubuntu-based distro? and also ask for money for it?

You can sell it, but you have to provide the source if people ask.

> can i share those two distros, with you, for example? i mean the ubuntu-based and the debian-based. im so confused with licenses, and i dont see the difference between having nonfree software installed in your machine, or awaiting you in a repo :S

Ubuntu is based on Debian, so the licensing is the same. The only problem with the non-free codecs is tha they may be illegal to use in your country, you would have to check the licensing in your country, plus you may have pay licensing fees to the copyright/patent holder. In most cases the non-free software is closed source, so you can't provide the source to those applications/drivers, so you would be in contravention of the GPL.

Jim

---

### Post by Isilion on 2009-04-08
> **dyous87 said:**
> I am interested in starting a new distro based on Ubuntu or Linux Mint for the purpose of packaging with some low powered affordable netbooks and mini desktops. I've been trying to start this off and have been looking for people to help out.

The goal is to make an extremely polished, easy to use yet powerful system with EVERYTHING a typical user would need out of the box.

If you are interested in working on a new distro perhaps this can be an opportunity for us to work together. Let me know :)

As far as the two distros you have already made, I believe you can share them with friends, you can also sell them for money if people are willing to pay you for it, so long as you keep all the code open and you make any changes you make public. Depending on which country you are in however, certain non free software, such as MS Fonts and Restricted Extras may be illegal to package by default. 

Thanks,
David

certainly i would like people to work with. my distros are completely finished and in beta testing. the ubuntu-based is the system i was using since i changed windaz for linux, but has been "remastersystered". that means almost every ubuntu logo have been removed, including bootsplash (i wonder how to make my own, plz suggest). the debian based works almost as well, but i dunno if it's problem of my pc, or the flash plugin for IceWeasel (I havent found Firefox in Debian repos)

what apps does my distros really have? i'll try to enum:

both desktops, KDE (Default) & Gnome.

Anjuta
Kdevelop
Openoffice
Gimp
Amarok4
aMSN
Ktorrent
Firefox(Iceweasel in the debian-based)
D3lphin for KDE; Nautilus for Gnome.
Compiz
Brasero
TuxGuitar
Ophcrack & ClamAv, and i'm looking for other rescue apps.
Wine
Tork

some games as freeciv and freecol, because y love' em
...
and so i remember at the moment. im open to suggestions, and feel free to ask more in deep what packages i collected. i remember that i included a mod of open-arena that i found on mint repos :P

the live cd works great if you got enogh RAM. the desktop is configured and with effects. i worked on a Matrix (the film) theme, 'cause i love it.

unnafortunately i dont know very well how to configure a server. the last i tryed was to config the ssh. if someone help me, i would try to enable other services in the livecd.

---

### Post by Isilion on 2009-04-08
thanks Jim, i will check now Spanish legislation.

DVD and mp3 codecs, java runtime environment, and the flash plugins arent free im right? should i remove them?

---

### Post by machinakias on 2009-04-13
hi folks! may i ask some questions?

i saw that you made a customized distro with remastersys.

well,i'm trying to make my own,and i'm really close!
The only thing is that i cant find a way to change the default boot screen
(you know,that one with the ubuntu logo and the moving bar....)

could you give me some advice?

thank you!

---

### Post by RATM_Owns on 2009-04-13
> **machinakias said:**
> hi folks! may i ask some questions?

i saw that you made a customized distro with remastersys.

well,i'm trying to make my own,and i'm really close!
The only thing is that i cant find a way to change the default boot screen
(you know,that one with the ubuntu logo and the moving bar....)

could you give me some advice?

thank you!
It's called the USplash theme.

---

### Post by wolfen69 on 2009-04-13
> **Isilion said:**
> thanks Jim, i will check now Spanish legislation.

DVD and mp3 codecs, java runtime environment, and the flash plugins arent free im right? should i remove them?

other distros like mint include them, so i would not worry about it.

---

### Post by glotz on 2009-04-13
[QUOTE=wolfen69]other distros like mint include them, so i would not worry about it.[/QUOTE]Sorry but that's not very good reasoning there.

---

### Post by Isilion on 2009-04-16
yeah, i think that people like richard stallman would be deeply unhappy if i share a distro wich includes software that dont respect the four freedoms.

by the way, i almost finished building the homesite of my new distro. i have based the distro finally in debian. 

now im sharing it out of internet, between my friends, for testing, but the copy will be uploaded soon. 

please visit [http://www.felix-project.bravehost.com/](http://www.felix-project.bravehost.com/) for further info. the chats, forums, and polls are created ;)

im looking now for people who can make me a bootsplash image or tell me how to do my own. mi distro is finished, but it not looks very "proffesional".

it hasn't got any logo. since i've thought call it "felix" i thought in felix the cat. it's old, almost 1920 or so; will his right may have expired? :S

---

### Post by cariboo on 2009-04-16
I do believe that you have to check with eu regualtions, but I don't think there is a problem with using the none-free codecs. It is more for the Americans, that the codecs are not part of the default installation.

Jim

---

### Post by Isilion on 2009-04-16
> **cariboo907 said:**
> I do believe that you have to check with eu regualtions, but I don't think there is a problem with using the none-free codecs. It is more for the Americans, that the codecs are not part of the default installation.

Jim

thanks again Jim, ill check it out.

but if i upload it to internet, the installation should avoid non-free code, or im wrong?

i've noticed that ubuntu comes withthe flash-plugin non free not installed. debian comes with gnash, but works nasty (sob).

---

### Post by Isilion on 2009-04-16
well, i terminated the web. ive made it to look simmilar to the theme i decorated gnome and kde, colors, etc.

i think lots of people love matrix. please tell me your opinion :)

could anyone try the chat? i cant install java; or its not working.
the forum is also open, i hope you enjoy it.

perhaps before this week ends, i would release the beta to the internet. i dunno very well what's the next step. what documentation should i create?

---

### Post by glotz on 2009-04-16
End-user and technical. The former deals with how to use your software and the latter e.g. what your software is built using and other such technical info. The more the merrier.

---

### Post by Isilion on 2009-04-18
Hi again.

this is the final list of programs i'll use in my distro:

-aMSN
-Anjuta
-Amarok
-Audacity
-Aide
-Brasero
-Blend
-Clamav
-Compiz
-D3lphin
-Freeciv
-Freecol
-Gnome
-Hydrogen
-IceWeasel
-IceDove
-KDE
-Ktorrent
-Kdevelop
-Konqueror
-Mplayer
-Medusa
-Nessus
-Nmap (Zenmap)
-Ophcrack
-Opera
-OpenOffice
-OpenArena
-Putty
-Quanta
-TuxGuitar
-Tork
-Totem
-VLC
-VirtualBox
-Wine
-XChat
-...and more
versions are the available in lenny debian/stable repos. 

the kernel image is 2.6.26-1.

---

### Post by DeadSuperHero on 2009-04-19
I'm sorry, I just fail to see the point in this. There are plenty of distros that already offer this software, codecs, and everything else for Free.

Why not try and pitch in and help an existing team? It'd do the Linux community a lot more help, as we won't have to deal with another distro that isn't technically binary-compatible with the other 12,000 or so.

---

### Post by namegame on 2009-04-19
> **Mr. Psychopath said:**
> I'm sorry, I just fail to see the point in this.

Maybe this is just a learning experience. There's nothing wrong with that.

It's similar to why people try Slackware/Gentoo/Arch/Lunar/(other DIY distributions). To both learn something more and to have complete control over the system.

---

### Post by Isilion on 2009-04-19
Ok i will try to explain myself. fEliX is my own debian distro. as said in the faq, it's a backup of my system, so if i have to reinstall the system, i minimize the programs i must install after.
it's a personal project too. as you said, it's a learning experience. as i have unsderstood earning money with software libre is not selling copyes; it's selling services, support, merchandise, or even publiciting others services. even you can make non free software for linux, and ask money for it (like cedega)
simply i would like to develop and mantain my own linux distro. im not really "alone"; i got family, classmates, friends, who will help me. in short i would like to create my own repos, and i want to program software for linux too.
in further versions, apps i design will be only in my distro at first, and in my repos then. 
it would be wonderful if i could dedicate all my life to it, because it's what i know to do and it's what i'd love to do.
perhaps if i work hard enough and the results are satisfactory i can ;)

---

### Post by JK3mp on 2009-04-19
Hmm..interesting enough. But that site is just a little much. sorry. lol

---

### Post by Isilion on 2009-04-19
i know i've done a little only, but im on it ;)

---

### Post by Wiebelhaus on 2009-04-19
What about updates , would this man be selling an OS that uses the same repos that Ubuntu does... is that ethical?

---

### Post by DeadSuperHero on 2009-04-19
> **sx66gns said:**
> What about updates , would this man be selling an OS that uses the same repos that Ubuntu does... is that ethical?

It is, but selling it just strikes me as utterly, utterly pointless.

One only need to look at such flops as iMagicOS.

---

### Post by Wiebelhaus on 2009-04-19
> **Mr. Psychopath said:**
> It is, but selling it just strikes me as utterly, utterly pointless.

One only need to look at such flops as iMagicOS.

the idea of easy money I guess , It's nonsensical at best.

---

### Post by Isilion on 2009-04-19
> **sx66gns said:**
> What about updates , would this man be selling an OS that uses the same repos that Ubuntu does... is that ethical?

> **Isilion said:**
> yeah, i think that people like richard stallman would be deeply unhappy if i share a distro wich includes software that dont respect the four freedoms.

by the way, i almost finished building the homesite of my new distro. i have based the distro finally in -->debian.<-- 

now im sharing it out of internet, between my friends, for testing, but the copy will be uploaded soon. 

please visit [http://www.felix-project.bravehost.com/](http://www.felix-project.bravehost.com/) for further info. the chats, forums, and polls are created ;)

im looking now for people who can make me a bootsplash image or tell me how to do my own. mi distro is finished, but it not looks very "proffesional".

it hasn't got any logo. since i've thought call it "felix" i thought in felix the cat. it's old, almost 1920 or so; will his right may have expired? :S

i think the only package of a debian external repos are remastersys and ubiquity (this last because i didn't found a more simple installer. if i could take time to examine a installer code, i could make my own too).

at the moment i use that repos because i cannot make my own repo (at this moment, i repeat). but i would offer all my bandwidth if youre happy that way :).

im just starting. surely ill have to invest more than my time if i would make a proffessional distro. in this same thread, someone offered to host my project, i don't know if in exchange of money; and i havent got money now LOL

im worryed about ethics. we can talk here of ethic if you like, i'll take note of what we speak and i'll do the more ethical at respect. don't worry, you haven't got to pay anything to use my distro. you can too choice use other free like ubuntu or pay for other commercial distro. youre free to do what you like :). 

but ubuntu has a logo too, and canonycal have profits, even offering good repos and support (and mentoring, teaching, etc). im here to discuss things like this, so don't worry to ask about.

certainly i don't think i will made myself rich simply that way. im just trying to do my own distro, with my own projects. i dont have in mind selling softare that can be found in other distros. certainly i think that people who makes distros oftenly spend their own time and money in that work, because they love it, or just because its their job.

---

### Post by Marco A on 2009-04-19
.

---

### Post by Ticketoride on 2009-04-19
> **Isilion said:**
> looking for at google, i found an applicattion in gnewsense repos called 'remastersys'. its cool, simply makes an installable livecd from your system.
Is there any Way to create this remastersys *.iso somewhere else other than on the same Drive Ubuntu is currently installed on, as I have only about 2 GBs left. I have another Linux ext3 Partition which I have already mounted, but I also can't figure out what the Path would be. All a Walk in the Park in DOS Systems where Hierachies lead off Partitions, The Linux ones just confuse me.

---

### Post by Isilion on 2009-04-19
> **Marco A said:**
> I don't understand why some people have the problem with creating your own distro.

Look at Linux Mint it's based on Ubuntu.

Linux Mint uses the Ubuntu repositories except for the Mint specific softwares.

There's the Argentinian Ututo Linux and Estrella Roja Linux both based on Ubuntu also.

There's also MoLinux from Castilla-La Mancha Spain they have their own repositories or I can switch it to the Ubuntu repositories.

I'm sure there are more also.

There's nothing wrong in creating a Ubuntu based distro if it is useful to someone and well done project.

yes. as i read in ubuntu documentation, canonycal agrees with making ubuntu remixes and so, but you may ask permission in some cases. that's why i finally decide to base fEliX on debian.
im not proposing to sell an OS. my purpose is maintain the os and support their users. Stallman and Linus made simmilar things. they didn't like the way the things were going and decided to do their own. :)
in any case i think it's not easy money. at last, it will take too much time to see any money. i don't think that i alone can support as well as in SuSe, in example. But it's my will.

are you spanish? you mentioned few castillian distro's. i am. message me if you want to talk in spanish about this, by msn or irc.

---

### Post by Isilion on 2009-04-19
> **Ticketoride said:**
> Is there any Way to create this remastersys *.iso somewhere else other than on the same Drive Ubuntu is currently installed on, as I have only about 2 GBs left. I have another Linux ext3 Partition which I have already mounted, but I also can't figure out what the Path would be. All a Walk in the Park in DOS Systems where Hierachies lead off Partitions, The Linux ones just confuse me.

i think you can modify settings in remastersys using the front end. mount a pendrive or any writable media in a directory, such as /home/user/slave, and put that address in the settings. 

i think that other partitions mount in /media/ by default in ubuntu, like /media/disk. im not sure, hope had been useful

---

### Post by Ticketoride on 2009-04-19
> **Isilion said:**
> i think you can modify settings in remastersys using the front end. mount a pendrive or any writable media in a directory, such as /home/user/slave, and put that address in the settings. 

i think that other partitions mount in /media/ by default in ubuntu, like /media/disk. im not sure, hope had been useful
Thanks so much for the Infos. I have the Front End.

I have another Ext3 Partition mounted in /<Partition Name>, so that would only amount to a minor Path change from /home to /StorageDrive.

Cheers :D

---

### Post by Isilion on 2009-04-21
hi again. i found a trouble creating the distro debian in that i want to put ubituity as installer.
i think it's a kind of dependances problem. when i add remastersys and ubuntu repositories and install remastersys (and ubiquity, casper and libs), updater starts going crazy. it begins to install only ubuntu packages uninstalling debian ones. i make sure that synaptic "prefers" lenny stable packages, but the problem still.
i didn't tryed, but i think it solves removing al foreign debian package and returning sources.list to original.
reading at remastersys site, it's explained why there are to versions of remastersys, one for ubuntu and one for debian. main differences are on using ubiquity or a remastersys installer, which is not very user friendly.
i am satisfied at 99% with my distro, it fits all purposes why i made it, but i'd like to use that installer (or some good installer), as i dont feel comfortable with remastersys intstall.
googling a bit i have not found any, lots of projects and old tryes, but no one functional.
does anyone know of any? or about the steps that a script must follow to install a livecd to a hard disk? it's anyone working on a ubiquity-debian port?

---

### Post by Isilion on 2009-05-01
hi again! i have were successfull attempting to add ubiquity to my distro. finally i based it in gNewSense, and i had not got any problem. the distro could be download from here: 


[http://www.felix-project.bravehost.com/](http://www.felix-project.bravehost.com/)


please post in that forum if you try fEliX and found any bug. thanks to all help.

---

### Post by wsonar on 2009-05-01
Making an image of your system is not the same as creating a distro

---

### Post by Isilion on 2009-05-01
that does not means i could not share with others my system. please dont report the torrent.


and im intended to do my own distro, with own repositories and made with builder. this is only a first approach.

---

### Post by wsonar on 2009-05-01
> **Isilion said:**
> that does not means i could not share with others my system. please dont report the torrent.


and im intended to do my own distro, with own repositories and made with builder. this is only a first approach.


no worries just terminology

---

