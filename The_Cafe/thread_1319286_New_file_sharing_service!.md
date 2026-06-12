---
title: "New file sharing service!"
date: 2009-11-08
forum: The Cafe
---

### Post by PorkyPie on 2009-11-08
Hi everyone. I'm a pretty new php developer. I've made a service called "uploadmyfile", which, well... allows you to upload your file :).

I thought you might want to try it out, so you can give it a test run here: http:/www.failtewexford.com/uploadmyfile

It doesn't have any restrictions to how many downloads it can have. It's file limit is 500MB. There's no "account", or anything like that, simply pick a file, and click the "Upload My File!" button.

You'll find your uploaded file at http://www.failtewexford.com/uploadmyfile/uploads/<YOURFILE>

It's a very basic script. What do you think?

Edit: Also, I won't be keeping this service up long, so I am not responsible for data loss.

---

### Post by The Funkbomb on 2009-11-08
You might run into problems when 50 people start uploading untitled.jpg

---

### Post by PorkyPie on 2009-11-08
> **The Funkbomb said:**
> You might run into problems when 50 people start uploading untitled.jpg

True, I might implement the creating of random numbered folders.

---

### Post by joshdudeha on 2009-11-08
How about you just give the filename a random number, or a suffix that increments, like 01, 02 etc.
then give them the link after :)
would be better than random folders

---

### Post by markp1989 on 2009-11-08
it works :) i just uploaded my bootchart. but i do agree that you need to start adding random numbers at the start of every file eg XXXfile.type so other people will be able to add there bootchart lol

---

### Post by v8YKxgHe on 2009-11-08
As a PHP developer who knows a lot about PHP security, and also one to tell people their security issues, I'll step forward and admit what I just did.

You should never ever ever let people upload anything and everything to your server, ever. I just ran any PHP code I liked on your server and I replaced your index.php file with a small bit of something that resembles HTML.

Why did I do this? To protect you against any other malicious user that would use it for their gain. I did it to stop those from uploading any more files which could potentially cause a lot of harm and grief to you. I do apologies, however I hope you can understand (I also hope you have a local backup of the file) why I had to do it.

---

### Post by YeOK on 2009-11-08
> **AlexC_ said:**
> As a PHP developer who knows a lot about PHP security, and also one to tell people their security issues, I'll step forward and admit what I just did.

You should never ever ever let people upload anything and everything to your server, ever. I just ran any PHP code I liked on your server and I replaced your index.php file with a small bit of something that resembles HTML.

Why did I do this? To protect you against any other malicious user that would use it for their gain. I did it to stop those from uploading any more files which could potentially cause a lot of harm and grief to you. I do apologies, however I hope you can understand (I also hope you have a local backup of the file) why I had to do it.

You bully. You saw a post from a guy who made it plain and clear he was new to PHP and decided to hack him? 

That's not cool, you could have just used the private messaging system here to help him. That wouldn't have made you look 'leet' though, would it.

---

### Post by Sporkman on 2009-11-08
> **YeOK said:**
> You bully. You saw a post from a guy who made it plain and clear he was new to PHP and decided to hack him? 

That's not cool, you could have just used the private messaging system here to help him. That wouldn't have made you look 'leet' though, would it.

Meh, I think he did him a favor. Between when he sent him the PM, and when he (the website's owner) actually gets around to securing it properly, a lot of damage could have been done.

---

### Post by ZankerH on 2009-11-08
> **YeOK said:**
> You bully. You saw a post from a guy who made it plain and clear he was new to PHP and decided to hack him? 

That's not cool, you could have just used the private messaging system here to help him. That wouldn't have made you look 'leet' though, would it.

He saw an obvious newbie mistake, fixed it, and made a public statement about it to remind other people. What's your problem?

---

### Post by Sporkman on 2009-11-08
So: his error was keeping the same filename as was uploaded, and moving it to a predictable place.

---

### Post by Frak on 2009-11-08
> **YeOK said:**
> You bully. You saw a post from a guy who made it plain and clear he was new to PHP and decided to hack him? 

That's not cool, you could have just used the private messaging system here to help him. That wouldn't have made you look 'leet' though, would it.
I would rather weld a bank door shut than leave it wide open for a suicide bomber to enter. The bank had good intentions, it just wasn't very well secured.

I just now saw the topic, but when I saw what the OP was doing, I thought about doing the same. Web servers are at the risk of remote code execution through the interpreters, which is even more dangerous than having an unpatched kernel. You could hide what OS your server runs on, but you can't hide the interpreter.

@OP
Limit the file types that can be uploaded, and put checks in to make sure that the extension matches the wanted filetype. The PHP interpreter won't execute code that doesn't end in a .php. Be sure to also check mime-types. Finally, in case you're using a database, make sure you sanitize all data being stored. SQL injections are a real problem nowadays.

---

### Post by Mehall on 2009-11-08
I would happily let a bomber go into a vault. Then I'd lock him in.

Those things are fairly blast proof, inside and out.

a ROBBER on the other hand, they don't get in.

---

### Post by YeOK on 2009-11-08
> **Frak said:**
> I would rather weld a bank door shut than leave it wide open for a suicide bomber to enter. The bank had good intentions, it just wasn't very well secured.

I just now saw the topic, but when I saw what the OP was doing, I thought about doing the same. Web servers are at the risk of remote code execution through the interpreters, which is even more dangerous than having an unpatched kernel. You could hide what OS your server runs on, but you can't hide the interpreter.

Fair enough, so if anyone finds a security hole in TangoCMS, they should hack the home page and leave a note in the forums.

---

### Post by v8YKxgHe on 2009-11-08
> **YeOK said:**
> You bully. You saw a post from a guy who made it plain and clear he was new to PHP and decided to hack him? 

That's not cool, you could have just used the private messaging system here to help him. That wouldn't have made you look 'leet' though, would it.
There was no hacking going on at all, I simply exploited a possibly very serious hole which protected his server from someone else doing malicious things, and told the user about it. There was no harm done, in fact the very opposite. I could have very easily read his database credentials for the main site, and executed a simply query to drop all the tables in there - destroying his main, public website. Would you rather someone do that?

Like said by another user, the OP has not yet been online or seen what has been done - which is a long time to leave such critical hole open.

> So: his error was keeping the same filename as was uploaded, and moving it to a predictable place. 
Not entirely, even if the file was given a random name the link would still need to have been given to the user, and so the code could still be executed (assuming same extension kept). For all file uploaders, always put the files *outside* of the document root if you can, and pass them through to the user using another method. Or more simply, restrict what can be uploaded (which is kinda hard).

> Fair enough, so if anyone finds a security hole in TangoCMS, they should hack the home page and leave a note in the forums. 
I would kindly accept the challenge, in fact after the release of the upcoming 2.4.0 I was thinking about doing a security challenge, where every security issue gets a small money reward. I'm not claiming that there are no security issues btw, or that I know everything about security, since I don't. I am just a very security conscious person when it comes to developing on the web, since I need to protect my users.

To the OP, in case you were wondering what the code was:

[PHP]<?php file_put_contents('../index.php', '<h2>Rule #1. New PHP developers should never code file uploaders. They are not simple, and they are not easy to secure. Enjoy.</h2>'); ?>[/PHP]

---

### Post by Frak on 2009-11-08
> **AlexC_ said:**
> There was no hacking going on at all, I simply exploited a possibly very serious hole which protected his server from someone else doing malicious things, and told the user about it. There was no harm done at all.

It was just a matter of time before somebody uploaded a PHP script by mistake to the server, only to have it executed when it was returned to the user. Could do anything as far as throw a "Database not found, error on line ###" to causing an infinite loop on the server.

> **AlexC_ said:**
> Like said by another user, the OP has not yet been online or seen what has been done - which is a long time to leave such critical hole open.

Agreed. The second you put something on the internet, you begin real-world security testing. There are no "Internet Police" to protect you from vandals.

> **AlexC_ said:**
> Or more simply, restrict what can be uploaded (which is kinda hard).

Not hard. Time consuming, yes. It's more of anticipation of what can be uploaded. It's more a problem of how much Regex you know than how difficult it is to block certain files. With a combination of client (Javascript) and server (PHP) side handling, you can stop the lazy ones at the gate, and the more forceful ones at the door.


> **AlexC_ said:**
> I would kindly accept the challenge, in fact after the release of the upcoming 2.4.0 I was thinking about doing a security challenge, where every security issue gets a small money reward. I'm not claiming that there are no security issues btw, or that I know everything about security, since I don't. I am just a very security conscious person when it comes to developing on the web, since I need to protect my users.

I'd take on your challenge. I too am very security conscious, and for that reason, PHP isn't usually my first language of choice.

> **Mehall said:**
> I would happily let a bomber go into a vault. Then I'd lock him in.

Those things are fairly blast proof, inside and out.

a ROBBER on the other hand, they don't get in.

Talking about the bank itself. There are usually a lot of people inside the bank.

---

### Post by v8YKxgHe on 2009-11-08
> Not hard. Time consuming, yes. It's more of anticipation of what can be uploaded. It's more a problem of how much Regex you know than how difficult it is to block certain files. With a combination of client (Javascript) and server (PHP) side handling, you can stop the lazy ones at the gate, and the more forceful ones at the door.
Assuming you have the right tools available. I guess the 'hard' part in my statement comes from having to deal with multiple environments that I don't know of (since my projects can all be installed by others). Even still, being sure 100% what a file is is quite hard. Lazy ones can be stopped yeah, and most others.

> I'd take on your challenge. I too am very security conscious, and for that reason, PHP isn't usually my first language of choice.
Awesome, it's not setup yet and would only be valid for 2.4.0 code. I'll PM you if you want when I set it up.

---

### Post by Frak on 2009-11-08
> **AlexC_ said:**
> Assuming you have the right tools available. I guess the 'hard' part in my statement comes from having to deal with multiple environments that I don't know of (since my projects can all be installed by others). Even still, being sure 100% what a file is is quite hard. Lazy ones can be stopped yeah, and most others.

True, I've never created anything where I haven't anticipated the environment. I'm a private freelancer for a business pool, so I readily know what the target audience and service platform are beforehand.

> **AlexC_ said:**
> Awesome, it's not setup yet and would only be valid for 2.4.0 code. I'll PM you if you want when I set it up.

That'd be great.

EDIT, PHP only, or Database sanitation too?

---

### Post by PorkyPie on 2009-11-10
Oh, hey. I was just going to my uploadmyfile folder, and noticed it had a weird message. Came here, and had a private message. I seen what I did wrong, I'm very glad that AlanC_ did what he did. Thank you.

And, to that person who said he was a bully, you're totally wrong. He did that to help me.

And, I'm sad to say that since I've dis-continued the service, your files have now been deleted. I may learn some more php, and improve, and decide to re-launch the service.

Regards,
PP

---

### Post by v8YKxgHe on 2009-11-10
> **PorkyPie said:**
> And, I'm sad to say that since I've dis-continued the service, your files have now been deleted. I may learn some more php, and improve, and decide to re-launch the service.

Regards,
PP

As said in the PM, I would be more than happy to help you out with re-launching it and making it nice and secure. It's the least I can do.

---

### Post by PorkyPie on 2009-11-10
> **AlexC_ said:**
> As said in the PM, I would be more than happy to help you out with re-launching it and making it nice and secure. It's the least I can do.

Nah.. It's fine. Thanks for your offer though.

---

### Post by Bucky Ball on 2009-11-10
> **AlexC_ said:**
> I had to do it.

? You didn't *have* to do anything. If you were going to do anything it would have been way more polite to let the OP know he might have a security issue by posting on the forum, explaining and helping them fix it up, *not* by hacking their system to prove a point.

---

### Post by PorkyPie on 2009-11-10
Ok... soo, I'm not sure what's happening now. Bucky Ball has a point, and AlexC_ did technicaly hack my uploadmyfile script. And, no, I don't have a local copy. But.. AlexC_ did also help out. It wasn't nice though to hack my server though.

---

### Post by PorkyPie on 2009-11-10
> **Bucky Ball said:**
> ? You didn't *have* to do anything. If you were going to do anything it would have been way more polite to let the OP know he might have a security issue by posting on the forum, explaining and helping them fix it up, *not* by hacking their system to prove a point.

I agree with you. I have taken appropriate actions. Thanks Bucky Ball.

---

### Post by catco_designs on 2009-11-10
That was actually a very nice thing he did ..
Many would just do an exploit and watch you squirm
or see where you were asking questions and confuse you even more by leading the the blind sheep:p

---

### Post by Sporkman on 2009-11-10
> **catco_designs said:**
> That was actually a very nice thing he did ..


Agreed.

---

### Post by PorkyPie on 2009-11-10
It might have been a nice thing to do, but he still technically modified my files without asking. If he had just notified me, I would have taken care of it myself. So really, in a way, it's hacking. Part of a PM he sent me today was:

> Yes, I uploaded a phpinfo.php file to start with, to see if the exploit would work - then uploaded the wrong foo.php file, so upload it as I think lolcake.php, or something similar.

Kind Regards,
Alex

So, he uploaded three files. The "lolcake" php file changed the content on the page. He also uploaded a phpinfo file, although, that wouldn't do damage. He also uploaded this weird "foo.php" file.

I understand how people agree that it was a nice thing he did for me, by ensuring that people couldn't upload dangerous files, or any files for this matter. But he was wrong in what he did; uploding a file to destroy the content of my other page. Whatsmore, I don't have a copy of the file the had been there previously. So, my glory of creating my first php script didn't last very long.

---

### Post by Frak on 2009-11-10
> **PorkyPie said:**
> It might have been a nice thing to do, but he still technically modified my files without asking. If he had just notified me, I would have taken care of it myself. So really, in a way, it's hacking. Part of a PM he sent me today was:

It took you quite a while to respond. Somebody could have set up a spamming system by now. That would have you in trouble by various authorities by not securing your own system. It could have went further than that. Your server could have been turned into a botnet of sorts.

> **PorkyPie said:**
> So, he uploaded three files. The "lolcake" php file changed the content on the page. He also uploaded a phpinfo file, although, that wouldn't do damage. He also uploaded this weird "foo.php" file.

lolcake - Replace the dangerous file with another one that is harmless.
phpinfo() - Test to see if your server can be exploited.
foo.php - Probably information to see if he could retrieve any more information than what phpinfo provides.

> **PorkyPie said:**
> I understand how people agree that it was a nice thing he did for me, by ensuring that people couldn't upload dangerous files, or any files for this matter.

More than dangerous, your server could have been transformed into a botnet to do the creators bidding. This sounds like fantasy, but this is very real and is extremely common.

> **PorkyPie said:**
> But he was wrong in what he did; uploding a file to destroy the content of my other page.

Read my first point.

> **PorkyPie said:**
> Whatsmore, I don't have a copy of the file the had been there previously.

That's **your **fault, nobody else. Nobody stopped you from creating a backup.

---

### Post by YeOK on 2009-11-10
> **PorkyPie said:**
> Ok... soo, I'm not sure what's happening now. Bucky Ball has a point, and AlexC_ did technicaly hack my uploadmyfile script. And, no, I don't have a local copy. But.. AlexC_ did also help out. It wasn't nice though to hack my server though.

I manage servers for a number of people and these kind of exploits happen now and again. When they do, I generally force an OS reinstall, new passwords and will upload all html and database files from clean backups, ie: backups not stored on the server. Its time consuming and very annoying. 

If AlexC_ had genuine concern for you and your server, he should have known to contact you via PM and give you time to respond. 

My advice to you now is, change your password, check logs for any unusual activity and if your renting space on a shared server, contact your host and let them know. You should also delete all html files and upload clean backups.

Yes, you made a silly mistake in your upload script but its not an excuse to illegally access your server. However honourable the intentions.

---

### Post by Frak on 2009-11-10
> **YeOK said:**
> My advice to you now is, change your password, check logs for any unusual activity and if your renting space on a shared server, contact your host and let them know. You should also delete all html files and upload clean backups.

Good way for your shared host to bar your account. If your host doesn't trust you, nothing stops them from removing your account with no warning.

---

### Post by Barrucadu on 2009-11-10
Well, the moral of the story is that upload scripts aren't as trivial as they would first seem :P

---

### Post by Sporkman on 2009-11-10
> **YeOK said:**
> Yes, you made a silly mistake in your upload script but its not an excuse to illegally access your server. However honourable the intentions.

How was it illegal? The website owner provided a mechanism for uploading files. That's what AlexC_ did.

---

### Post by MicrosoftFan on 2009-11-10
> **Sporkman said:**
> How was it illegal? The website owner provided a mechanism for uploading files. That's what AlexC_ did.

Not sure which jurisdiction it would fall under but for example, under the [(UK) Computer Misuse Act]("http://www.opsi.gov.uk/acts/acts1990/ukpga_19900018_en_1#pb1-l1g3"), the unauthorised modification of the index.php file was illegal (even though there were good intentions).

**3 Unauthorised modification of computer material **

(1) A person is guilty of an offence if&#8212;
[INDENT](a) he does any act which causes an unauthorised modification of the contents of any computer; and
(b) at the time when he does the act he has the requisite intent and the requisite knowledge.
[/INDENT]
(2) For the purposes of subsection (1)(b) above the requisite intent is an intent to cause a modification of the contents of any computer and by so doing&#8212; 
[INDENT](a) to impair the operation of any computer; 
(b) to prevent or hinder access to any program or data held in any computer; or 
(c) to impair the operation of any such program or the reliability of any such data.[/INDENT]
(3) The intent need not be directed at&#8212; 
[INDENT](a) any particular computer; 
(b) any particular program or data or a program or data of any particular kind; or 
(c) any particular modification or a modification of any particular kind. 
[/INDENT]
(4) For the purposes of subsection (1)(b) above the requisite knowledge is knowledge that any modification he intends to cause is unauthorised.

(5) It is immaterial for the purposes of this section whether an unauthorised modification or any intended effect of it of a kind mentioned in subsection (2) above is, or is intended to be, permanent or merely temporary.

(6) For the purposes of the [1971 c. 48.] Criminal Damage Act 1971  modification of the contents of a computer shall not be regarded as damaging any computer or computer storage medium unless its effect on that computer or computer storage medium impairs its physical condition. 

(7) A person guilty of an offence under this section shall be liable&#8212; 
[INDENT](a) on summary conviction, to imprisonment for a term not exceeding six months or to a fine not exceeding the statutory maximum or to both; and
(b) on conviction on indictment, to imprisonment for a term not exceeding five years or to a fine or to both.
[/INDENT]

---

### Post by The Funkbomb on 2009-11-10
Oh for the love of...

Why the back and forth?

No, he shouldn't have uploaded that but he had the best intentions in doing so.  The small headache he caused now could have been a much bigger headache with someone with malicious intent.

---

### Post by Bucky Ball on 2009-11-10
> **Frak said:**
> Somebody could have set up a spamming system by now. 

Not if you'd PMed the OP to help them prevent it instead of changing their files of your own violition; warned them of a security issue and helped them work out what to do about it.

Better to admit maybe you should've curbed your enthusiasm before meddling on a strangers server than start blaming others for your mistake and throwing mud to see if any sticks. 

First you thought you were being helpful by meddling with someone elses files, then apologetic and more helpful, now you're defensive because the OP doesn't appreciate having their work tampered with un-authorised. 

If you want to be helpful, in future PM the OP and help them work out their security issues in preference to and BEFORE barging their server like a CIA raid at dawn, thinking you have the authority to do a security fix on a stranger's machine and alter a stranger's work because you know something about security. :)

Okay, you go out and accidentally leave the backdoor unlocked. Someone comes in and rearranges your furniture, replaces a few coffee cups, leaves and locks the door behind them. They haven't caused any damage as such and have done you a favour by locking the door behind them but a stranger rearranged your loungeroom (and left some biscuit crumbs on the coffee table). How do you feel about it?

---

### Post by Frak on 2009-11-10
> **Bucky Ball said:**
> First you were apologetic, now you're defensive.

I'm correcting everybody that doesn't know any better. Like, well, you for instance.

---

### Post by CJ Master on 2009-11-10
AlexC hacked the server, which was wrong, but since he had good intentions he's not likely to be sued.

That's this whole thing in a nutshell. Can we stop the back and forth debating now?

---

### Post by Bucky Ball on 2009-11-10
> **Frak said:**
> I'm correcting everybody that doesn't know any better. Like, well, you for instance.

And now you're getting aggressive and accusing people of not knowing any better. I take your personal comments to me as an insult, have reported it as abuse and am unsubscribing from this thread. Have a nice day. :)

**DON'T** PM me (I will consider that harrassment) or bother replying to this post. I won't be here to read it.

---

### Post by The Funkbomb on 2009-11-10
Everyone needs to calm down.

---

### Post by Sporkman on 2009-11-10
> **The Funkbomb said:**
> Everyone needs to calm down.

What they need is a ***Funkbomb***!

Personally, I think it would have been funnier if AlexC_ had uploaded a page displaying gay porn. :P Instead he had to be a do-gooder, and get flamed for it.

---

### Post by dmizer on 2009-11-10
Closed for review.

---

### Post by bapoumba on 2009-11-12
The thread will remain closed.

---

