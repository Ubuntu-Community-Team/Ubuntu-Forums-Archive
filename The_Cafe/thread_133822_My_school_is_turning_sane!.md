---
title: "My school is turning sane!"
date: 2006-02-20
forum: The Cafe
---

### Post by benplaut on 2006-02-20
I've finally broken my school's sysadmin. He's starting to see the light, and wants to transfer a bunch of the school's client computers over to linux (he likes all the various things you can lock down ;) ).

He's put me in charge of the new systems, and right nwo i have one 'prototype' up and working with Dapper Edubuntu, taking advantage of Sabayon and Pesselus to lock down themes, etc.  So far, most of the students have tried it out, and i haven't gotten a whole lot of negative comments.

There is one thing they don't like.  Logging into network shares is cumbersome, and some have a hard time remembering how.

I'm trying to write a script to replace logging in. First of all, he doesn't want people to be able to change themes - fair enough. Second, he wants each student to have their own folder on the server - also a good idea.

The server runs windows (he can't be convinced to switch that), and is currently working with 'roaming profiles'.  A student's My Documents is downloaded into the RAM when they log in, and the updated version sent back to the server when they log out.  The problem with this is that whith all account customization disabled, an account login is pointless.  Instead, you can log into your network share from a locked-down client, which provides for a much faster system, overall.

The script would need to be able to do the following:

1. Pop up a dialog asking for the student's username & pass.  Log them into their share.
2. Symlink their share to a set folder on the system, so that OpenOffice will, by default, save to the share. Symlink needs to be updated every time a student logs in.
3. Make a link on the desktop to their share.
4. Provide a way to logout of the share when they are done.  A timeout would be nice

Coding is not my forte, but i can probably figure out how to do up all but the ones directly involving Samba - i've read the relevent parts of the guide, but it's all french to me.

AFAIK, 1 can be done with a small python program, or just using Zenity. Getting the **** in place of password may be a bit more difficult, but stealing it from another program might work (it would seem that way... i'm not sure).

If you've read this far, rejoice. I'm getting to the point.  Pretty much, where should i start? What should i read? I've got plenty of time to work on this, but i'm just, for now, lacking that first step.

Thanks a million, :mrgreen:

---

### Post by Iandefor on 2006-02-20
[quote=benplaut]AFAIK, 1 can be done with a small python program, or just using Zenity. Getting the **** in place of password may be a bit more difficult, but stealing it from another program might work (it would seem that way... i'm not sure). [/quote] Zenity supports masking the text.

Good job! I'm starting to consider talking to my school's director to switch a few computers over to Ubuntu.

---

### Post by benplaut on 2006-02-20
[QUOTE=Iandefor]Zenity supports masking the text.

Good job! I'm starting to consider talking to my school's director to switch a few computers over to Ubuntu.[/QUOTE]

you're right... i hadn't noticed that.

everything just got a bit easier :)

OK, so now the problem is, simply, what's the syntax to connect to a samba share, and would nautilus recognize it (and be logged in)

---

### Post by somuchfortheafter on 2006-02-20
my school has an iron spike that has rusted shoved up my A** for no reason regarding me using computers at school.. the good news is only 3 months left and i will begin my parade of bird passing to everyone who works for their tech department. And before anyone tries to say o well try talking to them, I have they do not listen, and they are brainwashed by the fact that windows 98 is a great os and nobody needs to use flashdrives. Congrats though on a victory in one educational system.

---

### Post by Kvark on 2006-02-20
The easiest way to do simple scripts like that is to:
1. Write down command for command exactly how you would do it manually using a command terminal.
2. Replace the things that varies from case to case (username, password...) with variables and ask the user about those things with zenity.
3. Save it as a bash script.

---

### Post by bored2k on 2006-02-20
Great news benplaut! Bad news: Community chat, not Desktop support. Decide, let us move it to Desktop support, or stop asking about tech questions ;).

---

### Post by benplaut on 2006-02-20
[QUOTE=bored2k]Great news benplaut! Bad news: Community chat, not Desktop support. Decide, let us move it to Desktop support, or stop asking about tech questions ;).[/QUOTE]

decisions, decisions...

I'll double post :mrgreen: 

yah, move it to Desktop support, i guess. Thanks

---

### Post by TTT_travis on 2006-02-20
Ok, If your computer has roaming profiles then I'd assume they use Active Directory and you can auth pam against that, so when they get to the ubuntu login screen they just type in there password and you add some sort of login script that would mount the proper samba shares. To mount samba shares with a command you first make the mount point

mkdir /shared
mount -t smbfs -o username=usernamewouldgohere,password=passwordwouldgohere //server/mount /shared

you might want to mount them to the desktop, although I am not sure how your setup works.

EDIT: OH wait I see how you want to do it, I assume you want a icon on the desktop that says connect to servers and then they would enter there username and password, and that would mount the proper shares and provide a way for them to logout and just incase they forget to logout it would do it automatically. That sounds like a pretty good idea, however I think it would be better to just use the login system somehow.

Sorry for the horrible advice,
Travis

---

### Post by benplaut on 2006-02-21
thanks for the mount line... that's what i was looking for.

If i can keep gnome from being so damn bossy on the desktop, i can try to mount to ~/Desktop :)

Since this is no high-security matter, i'm thinking of maybe logout simple bringing up a fullscreen window that asks for your user/password, then the window closes once you're authenticated.

That shouldn't be very hard, just use 2 zenity windows and a blank fullscreen window (i think).

Cheers,

---

### Post by GreyFox503 on 2006-02-21
I can't help you much with the task at hand,, but I noticed that you said you were using Dapper Edubuntu above.  It would not be good if an update broke something important.  Why not use the stable version of Ubuntu?

---

### Post by bjweeks on 2006-02-21
Cause its a prototype?

---

### Post by GreyFox503 on 2006-02-21
[quote=bjweeks]Cause its a prototype?[/quote] 
If I was making a prototype or a test machine, I would want it to simulate the actual one I plan to build as closely as possible.  So either this means that benplaut is planning on deploying Dapper to his school's machines, or he's going to use Breezy.  And if he's going to use Breezy, what's the point of testing with Dapper?

I was curious why he made that choice.  I haven't used Dapper, but it's not supposed to be for production work (which school computers probably qualify for).  Maybe there is some cool application/feature only available in the Dapper version of Edubuntu.  In which case, just be very careful when updating the machines.  Heck, no matter what you're running, I would use caution when updating those machines.

---

### Post by benplaut on 2006-02-21
right now, it's using breezy edubutnu.  The reason to use dapper is because of the new Sabayon and Pessulus - two awesome apps to help 'lock down' the account.

You can prevent the student from changing theme, putting files on the disk, playing games, etc.

I haven't used the test machine in a few days, but i'm first going to see if i can backport the new versions of those two programs into breezy.

Also, by the time there are any decent number of these machines throughout the school, dapper will be stable, or at least at preview

---

### Post by majikstreet on 2006-02-21
That's ******* awesome!

I actually first read this from my school who of course uses windows..... I wish I could convince them, but I never even tried... Please tell how you got the guy to see the light :D

majikstreet

---

### Post by GreyFox503 on 2006-02-21
[quote=benplaut]Also, by the time there are any decent number of these machines throughout the school, dapper will be stable, or at least at preview[/quote]

Very true.  Time flies.  It's only a couple months away now before release.

---

### Post by shade11 on 2006-02-21
[QUOTE=majikstreet]That's ******* awesome!

I actually first read this from my school who of course uses windows..... I wish I could convince them, but I never even tried... Please tell how you got the guy to see the light :D

majikstreet[/QUOTE]

Easy, just keep telling him about Linux. When he has a problem on one of the Windows School Pc's just tell him how Linux can fix that or how that Linux doesn't get that error.

---

### Post by xequence on 2006-02-21
> When he has a problem on one of the Windows School Pc's just tell him how Linux can fix that or how that Linux doesn't get that error.

But then they will think linux is some uber great OS without any problems whatsoever, then when they find a problem they will be all "DOODZ, UBNTU NOT REDE 4 DA DAKSTOP".

What should you do? Tell them the pros and cons of windows, the pros and cons of linux, and let them choose the one that the think would best suit them.

---

### Post by TTT_travis on 2006-02-21
even though I am a mac guy I still think linux is great, I honestly think linux f'in rocks in schools, the only problem we face with linux in schools is the lack of the most uses programs like Adobe Creative Suite and AutoCAD if we can get the real actual products on linux (not opensource ones like gimp) I think linux could spread rapidly in schools, because windows is one of the most expensive things a school has to buy, if you use linux schools can buy hardware without and os already on it. Oh when you setup openoffice try to make the layout as much like word as possible and change the default icons to a different set, it makes people feel more comfortable, oh and set it to save to word .doc format by default.

I think what needs to be developed is a like Ubuntu Server :: School Edition which would include everything a school needs to get going from content blockers to firewalls, network virus protection, LDAP for centralized login, you can actually setup an entire network for $0 software costs, its pretty amazing. Now if adobe would just port their stuff the market would go up and schools would beable to afford more copies of Adobe CS and all of that because of how much they saved on server software, client software (windows and novell and stuff). Not having to pay client fees and punishing schools for the amount of hardware they have would definately be a good idea. I am wondering how much intrest there would be in a school server.

There is a project being build called Schooltool which looks pretty decent although the menu layout is horrible currently, it could edventually turn into a full fledged student information system like Skyward or whatever other overpriced products schools are buying now days.

---

