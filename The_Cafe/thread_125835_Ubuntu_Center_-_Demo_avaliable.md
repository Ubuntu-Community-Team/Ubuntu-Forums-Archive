---
title: "Ubuntu Center - Demo avaliable"
date: 2006-02-04
forum: The Cafe
---

### Post by TTT_travis on 2006-02-04
Hi guys incase you haven't noticed my project called [Ubuntu Center]("http://ubuntuforums.org/showthread.php?p=707249") its a web based control app that lets you view certain parts of your ubuntu computer on a different computer in a web based app. Anyway, I have finally got a demo up so you can kind of see how it works.

Please note, there is no video support yet.

[http://snoopy.ath.cx/centerdemo]("http://snoopy.ath.cx/centerdemo")
Username: demo
Password: demo

---

### Post by super on 2006-02-05
hey, now!
that is really awesome! :cool: 

so the idea is anybody could set one of these up on their computer and then access it from any other computer on the net?

would this be a package for an existing ubuntu box or would it be a different 'flavor' of ubuntu? (like edubuntu)

i love the idea!

---

### Post by TTT_travis on 2006-02-05
[QUOTE=super]hey, now!
that is really awesome! :cool: 

so the idea is anybody could set one of these up on their computer and then access it from any other computer on the net?
[/QUOTE]
Glad you like it, and Yes, that is exactly its purpose but it can also be used across your network if you wanted too.

[QUOTE=super]
would this be a package for an existing ubuntu box or would it be a different 'flavor' of ubuntu? (like edubuntu)

i love the idea!
[/QUOTE]

This will be distributed as a package, its just php files so you would just have to extract it to a directory on your apache webserver and it'll be good. This should actually run on any version of linux, but the only officially supported distros will be Ubuntu, Kubuntu, Xubuntu and edubuntu.

---

### Post by mstlyevil on 2006-02-05
This is great. I hope you have all the success in the world in getting it up and running. (I would pay for a subcription to something like this.)

---

### Post by TTT_travis on 2006-02-05
[QUOTE=mstlyevil]This is great. I hope you have all the success in the world in getting it up and running. (I would pay for a subcription to something like this.)[/QUOTE]

Thanks. Would never charge a subscriptions for this, besides it would probably violate the GPL on the included scripts.

---

### Post by TTT_travis on 2006-02-05
sorry about the downtime the demo should be back up now.

---

### Post by xequence on 2006-02-05
That is a wonderful idea! Good luck with it :)

Thats what we need. Programmers with good ideas =)

---

### Post by TTT_travis on 2006-02-05
Thanks. However I'm far from being a programmer ;)

---

### Post by raublekick on 2006-02-05
I was pretty sceptical and unintrested when I saw the other thread about this. But this demo is really keen. I'm still kinda sceptical about how safe this is security-wise, but it looks really awesome and useful. As someone who spends a lot of time in school labs, it will be nice not to have to email myself files or use my USB thumbdrive all the time.

---

### Post by TTT_travis on 2006-02-05
[QUOTE=raublekick]I was pretty sceptical and unintrested when I saw the other thread about this. But this demo is really keen. I'm still kinda sceptical about how safe this is security-wise, but it looks really awesome and useful. As someone who spends a lot of time in school labs, it will be nice not to have to email myself files or use my USB thumbdrive all the time.[/QUOTE]

I think it will be pretty secure, it will be using the Apache HTTP Auth inorder for you to get access to any files and as long as no one brute forces it, it should be fine.

---

### Post by majikstreet on 2006-02-05
awesome!! keep up the good work ;D

---

### Post by RaptorRaider on 2006-02-05
Awesome, especially from a 13-year old.
Keep up the good work! :-D 

This could certainly be an interesting addition to Ubuntu Server, right?

---

### Post by raublekick on 2006-02-05
uh derr... i wasn't even thinking that a login is required to access this. i was thinking that anyone could get the url and get right into your system. nevermind!

---

### Post by TTT_travis on 2006-02-05
[QUOTE=RaptorRaider]Awesome, especially from a 13-year old.
Keep up the good work! :-D 

This could certainly be an interesting addition to Ubuntu Server, right?[/QUOTE]
Thanks, and actually that is my main use for this, I have a file server running Ubuntu Server that stores all of my music, pictures, and videos, using ubuntu center I will beable to listen to music during study hall and upload my files so I can work on them at home too.

[QUOTE=raublekick]uh derr... i wasn't even thinking that a login is required to access this. i was thinking that anyone could get the url and get right into your system. nevermind![/QUOTE]
;)

------------
In other news work continues, I am currently working on the initial configuration of Ubuntu Center because right now it is pretty hairy.

---

### Post by curtis on 2006-02-05
Sorry for the comparison but it sounds like it is going to be like Windows Media Centre, except web based :D
Keep up the good work though, that demo is a pretty good start.

---

### Post by TTT_travis on 2006-02-05
[QUOTE=curtis]Sorry for the comparison but it sounds like it is going to be like Windows Media Centre, except web based :D
Keep up the good work though, that demo is a pretty good start.[/QUOTE]

lol yeah thats exactly what I was kind of thinking in the beginning, only Windows Media Center = Mythtv ;)

---

### Post by TTT_travis on 2006-02-05
I have just added a Upload module, check it out let me know how it looks, its in AJAX.

---

### Post by UbuWu on 2006-02-05
Looks great! Upload/download is a bit confusing, maybe this could be combined in file transfers? And would it work with a light-weight webserver like lighttpd instead of apache as well?

---

### Post by TTT_travis on 2006-02-05
[QUOTE=UbuWu]Looks great! Upload/download is a bit confusing, maybe this could be combined in file transfers? [/QUOTE]
hmmm, I'm not sure if I would want to combine them into a single module, it might actually make it more confusing. Any opinions from anyone else?

[QUOTE=UbuWu]And would it work with a light-weight webserver like lighttpd instead of apache as well?[/QUOTE]
it should as long as you can install php modules which I assume you can.

---

### Post by majikstreet on 2006-02-05
[QUOTE=RaptorRaider]Awesome, especially from a 13-year old.
[/QUOTE]

You are an extremely ageist person. Please _do not_ keep this attitude. This type of talk highly offends me, as I am sure it does others..

I could do this type of work if I felt like it, and I'm 12.

---

### Post by TTT_travis on 2006-02-05
[QUOTE=majikstreet]You are an extremely ageist person. Please _do not_ keep this attitude. This type of talk highly offends me, as I am sure it does others..

I could do this type of work if I felt like it, and I'm 12.[/QUOTE]

lol, yeah he may have made a generalization, however he is partly right there aren't many people that are 12 or 13 that have intrest in computers :cool:

---

### Post by majikstreet on 2006-02-05
[QUOTE=TTT_travis]lol, yeah he may have made a generalization, however he is partly right there aren't many people that are 12 or 13 that have intrest in computers :cool:[/QUOTE]
Yes, but that is changing. Computers are being taught in school, and so is web design. Everybody I know at least knows something; how to use AIM, xanga, and myspace. Better than nothing.

I'm one of the few with a lot of knowledge and passion for computers.

EDIT: Just checked out the upload file capability.. COOL! If you really wanted to make it special, maybe you could integrate celerondude's uploader [http://celerondude.com/script_uploaderv6](http://celerondude.com/script_uploaderv6)  (WARNING: Parts are NSFW) - but you may have some issues; he's had copyright issues and has started charging for future versions... anyway, what you have is cool :)

---

### Post by xequence on 2006-02-05
> I could do this type of work if I felt like it, and I'm 12.

You are a cool 12 year old =O

---

### Post by TTT_travis on 2006-02-05
> **majikstreet]Yes, but that is changing. Computers are being taught in school, and so is web design. Everybody I know at least knows something said:**
> http://celerondude.com/script_uploaderv6[/url]  (WARNING: Parts are NSFW) - but you may have some issues; he's had copyright issues and has started charging for future versions... anyway, what you have is cool :)

that looks cool, however its more then I need, its user based, somebody could make it as a plugin later on, but for now I think I'll stick with the AJAX one.

---

### Post by majikstreet on 2006-02-05
[QUOTE=xequence]You are a cool 12 year old =O[/QUOTE]
Thanks... lol... I should be working on specto instead of spending my time here...

[QUOTE=TTT_travis]that looks cool, however its more then I need, its user based, somebody could make it as a plugin later on, but for now I think I'll stick with the AJAX one.[/QUOTE]

well, I think parts of it are AJAX.. But you're the developer! Yeah, I agree, most people don't really need it, so it'd be better as a plugin.

---

### Post by UbuWu on 2006-02-05
[QUOTE=TTT_travis]hmmm, I'm not sure if I would want to combine them into a single module, it might actually make it more confusing. Any opinions from anyone else?[/QUOTE]

Maybe not combining them, but upload is actually both uploading and downloading to and from the computer. Maybe that could be renamed to file transfer and download to download torrents? (or can it do regular downloads as well?)

---

### Post by TTT_travis on 2006-02-05
[QUOTE=UbuWu]Maybe not combining them, but upload is actually both uploading and downloading to and from the computer. Maybe that could be renamed to file transfer and download to download torrents? (or can it do regular downloads as well?)[/QUOTE]

oh I get what your saying. I will have to think about that. and yes the download thing can do torrents and http download, although it probably doesn't work in the demo

---

### Post by WildTangent on 2006-02-05
Wow, that uploader is just the thing I need for times when I'm at school and can't upload via FTP.

-Wild

---

### Post by TTT_travis on 2006-02-05
I used ftp at my school a few times, but I think its blocked now :( , not that I can't get around that ;)

---

### Post by RaptorRaider on 2006-02-06
[QUOTE=majikstreet]You are an extremely ageist person. Please _do not_ keep this attitude. This type of talk highly offends me, as I am sure it does others..

I could do this type of work if I felt like it, and I'm 12.[/QUOTE]
While I can't find the word "ageist" in any online dictionary, it does not sound very positive. Positive however, my post was supposed to sound.
[QUOTE=xequence]You are a cool 12 year old =O[/QUOTE]
So why is a "Thanks... lol..." but not an "ageist"?

---

### Post by matid on 2006-02-06
So you're not really good at searching:
[http://dictionary.reference.com/search?q=ageist](http://dictionary.reference.com/search?q=ageist) ;)

---

### Post by majikstreet on 2006-02-06
[QUOTE=matid]So you're not really good at searching:
[http://dictionary.reference.com/search?q=ageist](http://dictionary.reference.com/search?q=ageist) ;)[/QUOTE]
:D yeah...

@ RaptorRaider

I dunno... just whatever... let's let this go..

---

### Post by lordbf1 on 2006-02-06
wow that is very cool!!!!!  keep up the good work!

\\lordbf1

---

### Post by Mathias-K on 2006-02-06
Impressive! This thing could be very useful, especially for Edubuntu users :)

---

### Post by TTT_travis on 2006-02-06
[QUOTE=Mathias-K]Impressive! This thing could be very useful, especially for Edubuntu users :)[/QUOTE]

Thanks, but just out of curiosity why is this useful for Edubuntu users? I am very intrested in education and computers.

---

### Post by Mathias-K on 2006-02-07
[QUOTE=TTT_travis]Thanks, but just out of curiosity why is this useful for Edubuntu users? I am very intrested in education and computers.[/QUOTE]

As it is now, it's very handy for students and teachers alike to be able to access school tasks and documents from home to school and the other way around. To my knowledge, Edubuntu lacks an efficient method of communications and document sharing between students and teachers.

My high school has bought a licence for Firstclass ([www.firstclass.com)](www.firstclass.com)), a program that is great for quickly spreading the word when a class is cancelled or sharing documents and assignments for homework, so that a lot of paper is spared. Unfortunately, it is not yet released for Linux.

Accessing such a "school/class-server" could really make things easier, i think. :)

---

### Post by TTT_travis on 2006-02-07
[QUOTE=Mathias-K]As it is now, it's very handy for students and teachers alike to be able to access school tasks and documents from home to school and the other way around. To my knowledge, Edubuntu lacks an efficient method of communications and document sharing between students and teachers.

My high school has bought a licence for Firstclass ([www.firstclass.com)](www.firstclass.com)), a program that is great for quickly spreading the word when a class is cancelled or sharing documents and assignments for homework, so that a lot of paper is spared. Unfortunately, it is not yet released for Linux.

Accessing such a "school/class-server" could really make things easier, i think. :)[/QUOTE]

Oh, I see.

Currently I have this installed so I can access my files at school. However, if your school runs Novell Netware they make software that allows access to your files stored on the fileserver at home. I forget what its called but its pretty decent, I should try to convince my school to get that. One of the most requested features for our schools network is a way to work on there files at home without using floppy disks to transfer the files.

---

### Post by WildTangent on 2006-02-07
[QUOTE=Mathias-K]
My high school has bought a licence for Firstclass ([www.firstclass.com)](www.firstclass.com)), a program that is great for quickly spreading the word when a class is cancelled or sharing documents and assignments for homework, so that a lot of paper is spared. Unfortunately, it is not yet released for Linux.

Accessing such a "school/class-server" could really make things easier, i think. :)[/QUOTE]
My school uses Firstclass too, and it's really not that useful. Our accounts are limited to 10MB, so you can't use it to transfer many documents, most teachers don't let you use the chat either. It's generally just a waste of money to be honest.

-Wild

---

### Post by Mathias-K on 2006-02-07
[QUOTE=TTT_travis]Oh, I see.

Currently I have this installed so I can access my files at school. However, if your school runs Novell Netware they make software that allows access to your files stored on the fileserver at home. I forget what its called but its pretty decent, I should try to convince my school to get that. One of the most requested features for our schools network is a way to work on there files at home without using floppy disks to transfer the files.[/QUOTE]

Yeah, that's why it would be so cool if Edubuntu developed a nice program for Home<>School communications and transfering :)

---

### Post by Mathias-K on 2006-02-07
[QUOTE=WildTangent]My school uses Firstclass too, and it's really not that useful. Our accounts are limited to 10MB, so you can't use it to transfer many documents, most teachers don't let you use the chat either. It's generally just a waste of money to be honest.

-Wild[/QUOTE]

As with all software, the usefulness depends on it's use.

How many of your documents are over a couple of megabytes? We are limited to something like 15-20MB, but that's just fine.

As for the usefulness; when every student logs on about one time a day, it becomes the fastest method of reaching the whole class. Also, for those who often get their documents lost, a copy on Firstclass can be very useful :)

---

### Post by TTT_travis on 2006-02-07
My space is got pretty full when I was in art from saving large photoshop documents so I had uploaded them to home and deleted them.

---

### Post by raublekick on 2006-02-07
TTT_travis, most of my stuff is not stored in my home directory. Will the control center allow me to view anything that I have permission to read/write?

---

### Post by TTT_travis on 2006-02-07
ok, this will probably depend on which user apache is ran by, otherwise you might have to chmod it., I am considering including a miniserver with ubuntu center to ease configuration, but still release it as a standalone script for people that want it....maybe. And you can set the folders to where you want, by default they will be set in the /home/Shared/Music /home/Shared/Photos etc. format.  

I plan on releasing a beta of ubuntu center whenever I can figure out a way to configure it all. Currently you would have to enter MySQL info and a bunch of other stuff in like 3 different files. I tried using PHP variables and includes but it didn't work because the config files are not actually being formatted in php, so whatever I guess.

---

### Post by marcos89 on 2006-04-16
THIS SOFTWARE IS REALLY COOOOL when will there be a 0.2 releasE?? i  cant wait! it would be cool if it had options to start vnc server and stuff like that, CANT WAIT!:mrgreen:

---

### Post by jbmalone on 2006-04-16
My friend has this with his Windows box and I was just wondering if it would come to Ubuntu.  Nice work.

---

### Post by _linux_ on 2006-04-17
Ubuntu Center reminds me of Workspot. But Workspot uses VNC and a Red Hat desktop.

---

### Post by jono.carnie on 2006-04-20
Hi,

Does, [this]("http://snoopy.ath.cx/centerdemo")? Still work?
I've tried the demo/demo access details and it's not letting me on.


JC

---

### Post by nocturn on 2006-04-20
[QUOTE=jono.carnie]Hi,

Does, [this]("http://snoopy.ath.cx/centerdemo")? Still work?
I've tried the demo/demo access details and it's not letting me on.


JC[/QUOTE]

Same here

---

### Post by unkemptwolf on 2006-04-20
Yea, I cant do anything with it either.

---

### Post by basketcase on 2006-05-09
I just logged in..I love it.  I see a few issues with the styling in IE 6.0..Over all I LOVE the idea!! 

Keep up the good work!!

---

### Post by nalmeth on 2006-05-09
I really dig the idea. Good thinking.
I will definatly be using this soon.

---

### Post by PrimoTurbo on 2006-05-10
Very nice work :)

---

