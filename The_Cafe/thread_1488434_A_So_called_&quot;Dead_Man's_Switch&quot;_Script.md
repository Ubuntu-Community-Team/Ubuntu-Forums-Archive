---
title: "A So called &quot;Dead Man's Switch&quot; Script"
date: 2010-05-20
forum: The Cafe
---

### Post by Warpnow on 2010-05-20
I doubt I'm the first person to think about this. A script that requires updating every 14 days or 6 months, or whatever. If the file is updated, then the script remains inactive, but when you fail to update it in the time frame, it executes a series of commands, such as sending out emails, uploading files, ect, ect, ect.

Could be used to distribute last messages in the event you die, to email you the IP address periodically of your laptop in the event it is stolen, or to distribute that government conspiracy info Fox Moulder gave you in the event that the alien conspiracy manages to find you in your cave and kill you.

So, anyone experimented with this?

Easy to jerry rig with a cron and touching an obscure file, but wondering if anyone had toyed with configuration or a self-contained executable?

Just a thought I have been toying with over the last week.

---

### Post by Paqman on 2010-05-20
I quite like the idea of the stolen laptop scenario, not so much the unexpected death one. You'd have to design the thing expecting that it will go off by accident. 

I'm reminded of the Mark Twain quote: "The rumors of my death have been greatly exaggerated"...

---

### Post by lisati on 2010-05-20
Nice idea, but what if it gets hijacked by something undesirable?

---

### Post by NightwishFan on 2010-05-20
It would have a definite old school hacker flair ;)

---

### Post by Dayofswords on 2010-05-20
a message from beyond the game sounds awesome!

knowing me, it probably say i died 5 times before i actually do

another cool idea is a watch that checks your heart beat every 2 hours for 1 minute, if the beat isn't sensed twice in a row, it would attempt to join a wieless network every hour and ssh into a server to give a script to execute

the watch can be turned off and will have a loud beep if the heart isnt sensed twice in a row so if your off, you have a chance to turn it off.

there is issue with this idea though... like, losing the watch, bugs, etc.

---

### Post by Warpnow on 2010-05-20
> **Dayofswords said:**
> a message from beyond the game sounds awesome!

knowing me, it probably say i died 5 times before i actually do

another cool idea is a watch that checks your heart beat every 2 hours for 1 minute, if the beat isn't sensed twice in a row, it would attempt to join a wieless network every hour and ssh into a server to give a script to execute

the watch can be turned off and will have a loud beep if the heart isnt sensed twice in a row so if your off, you have a chance to turn it off.

there is issue with this idea though... like, losing the watch, bugs, etc.

Also...having the watch be custom designed would prolly be really damn expensive. :-p


[quote="lisati"]
Nice idea, but what if it gets hijacked by something undesirable?
[/quote]

If they can hijack the app, they could just run the commands manually themselves. I wouldn't have the app ran with super-user priveleges or anything.

---

### Post by murderslastcrow on 2010-05-20
As a programmer, this sounds very interesting. It makes me wanna' have 9 lives just to test it. Lol, next thing you know you'll read in the paper about a software-related serial killer who uses people as subjects in his 'experiments'! :O

But no, seriously, I want to make something to test this theory. So long as there's a program that can send an authorized email and upload a file to FTP, or perhaps tinypic, without authorization or intervention other than preset coding, I think it would work pleasantly.

I mean, at the very most, an email would suffice to provide one with the information needed to pry open the secret vault, or whatever. XD

However, I'd probably want more fireworks than a simple message.

---

### Post by ericmc783 on 2010-05-20
I once heard about a website that offered services similar to what the OP is describing. Where when you die they send a message that you composed in advance, to email recipients that you selected. I don't think this site is around anymore, but I thought it was a good idea.

---

### Post by Old_Grey_Wolf on 2010-05-20
Hello Warpnow,

You need to Patent that idea, ASAP. :lolflag:

You could become a rich patent troll! :guitar:

---

### Post by MaxIBoy on 2010-05-20
No, that already exists. There are services which exist which allow you to send out a set of specific emails if you don't check in every few months. Used for last instructions and stuff like that.

---

### Post by Ebere on 2010-05-20
I live alone, waaaaaay out in the sticks in the mountains.

It's a hermit thing.

A script that would automatically send out emails if I didn't update it once a week, would be GREAT, in my circumstance.

But I am thinking that something that is online, and accessesd like webmail, would be best. 

If I had a heart attack in the middle of the night, nothing would be sent out, because my computer would be turned off...

That idea about a site online that offers the service sounds about perfect.

I also like the idea of putting one on the laptop, in case it is stolen.

---

### Post by Ebere on 2010-05-20
> **MaxIBoy said:**
> No, that already exists. There are services which exist which allow you to send out a set of specific emails if you don't check in every few months. Used for last instructions and stuff like that.

You say the service already exists ?

Any idea how I would go about locating same ?

Also, in my situation, I'd probably need to have the ability to 'update' via the phone, in case the power and/or internet goes out. (Happens quite often. And I'd hate for my family to get a 'Deceased John' email or letter, just because I couldn't get online to update. LOL)

---

### Post by Kafubie on 2010-05-20
OP makes me depressed.
For some reason talking like that me think a lot.

---

### Post by murderslastcrow on 2010-05-20
Death, eh. I'll deal with it when it happens. XD I hear from near-death experiencers that it's actually an invigorating experience, like getting high, but it's an emotional kind of high, like when you think back to the best moment of your life, but you're there, and that feeling surrounds you.

Of course, this is only after facing the darkest and deepest feelings of fear you've ever felt, in most cases, but eh. It's like blacking out but being there while it's happening, or being conscious as you slip into sleep.

But ANYWAY, I think a smarter idea than having a script execute when the person who stole your laptop steals it would be to place a GPS tracker inside so you can retrieve it. Of course, it would also be a good idea to execute a script that locks up all your files as it backs them up to a server somewhere or something in the background, or scares the crap out of them by starting a video of a demon/ghost saying, "I know you stole my computer, you won't escape!!! D:"

I think it'd be even better to have a script that checks for a value online and if it's true, it does all this, so you can set it as soon as you notice your computer is gone.

---

### Post by jjackson1984 on 2010-11-24
On the subject of a dead man software switch
I have to admit the linux distros are very secure.  There is one area for improvement that is crucial in my opinion.  I recently lost my laptop to theft, while my personal information and that of my clients are kept on an encrypted containers it is reasonable to assume that someone could in the not too distant future, crack those encrypted file containers.  A dead man switch would perform a D.O.D. compliant wipe of user defined, files, directories, or partition when the required password isn't entered at a user specified time interval.  Include also a fail2ban feature.  The program should be hidden maybe as a portion of the kernel or like a root kit.  Just so it could not be easily identified or disabled without a root password.
Possible concerns for lost or forgotten passwords.  Well the first rule of computers is back-up, back-up, and back-up again.  The concern here is that the information we are trying to protect is privaledged and confidential.
In summary the G.U.I. would allow the user to define the target files, directory, or partition to be wiped.  The user could set the time interval hours, days, etc. at which time the software asks for the authentication code.  Failure to enter the correct code within a maximum number of tries in a user specified time limit would then wipe the specified files silently.  Thus my stolen laptop would not contain information that could someday prove injurious to my clients or myself.
Thank you for reading my post

---

### Post by czr114 on 2010-11-24
I use FDE on all my systems, and encrypt all my backups to my own OpenPGP key.

When my mind goes, all my systems go with it.

---

