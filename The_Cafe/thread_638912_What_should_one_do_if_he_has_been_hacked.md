---
title: "What should one do if he has been hacked?"
date: 2007-12-12
forum: The Cafe
---

### Post by BertP on 2007-12-12
Ok this is embarrassing ... I am an Ubuntu noob  and for the last several days,  I  have been DLing porn clips using Azureus,  when not DLing I left Azureus active to seed....

Well today I tried to log-on to a non-porn website and I had to request a new password because my regular password would not work. (it's not a financial site so I need not work about losing my shirt,,, yet)

anyway I was able to request a new password and log on.  Some hours later I notice a new item on my desktop.  a file name "pervie.png" is now present.   This file shows a screenshot  of when I was trying to log on to the website with the password problem earlier today where I had to change my password.

So immediately  I close Azureus, next, I goto my router and close the port I had opened for Azureus,  then I loaded FireStarter and close access to the port there....   Then I restart my computer.

I do have  a version of FreeAVG on my computer.  I haven't used it since the upgrade to Ubuntu 7.10 but when I press the "update" button, I get a message that says I don't have permission to update
AVG.

I am able to scan my computer and I get a lot of error message in AVG which telling  directories that it doesn't have permission to access   (I have attached screenshots of errors to this message)
eventually AVG hangs...

what should I do next?

---

### Post by KiwiNZ on 2007-12-12
Get  a bandage:)

---

### Post by koenn on 2007-12-12
Forum admins are allowed to make fun of hapless community members and their problems ?

---

### Post by isecore on 2007-12-12
Provided you actually HAVE been cracked (I find it very difficult to imagine, but none the less it occasionally happens) there's really only one way to be sure: reinstall.

Unplug the machine from any networking, move whatever you want to keep to some other drive, then completely wipe it and start fresh.

If that's not an option, start looking in the world-writable directories such as /tmp and /var/tmp for weird directories and scripts. That's usually where crackers store their applications.

But again, I find it somewhat difficult to imagine that you've been cracked. Ubuntu in it's default configuration (even without firewall) is quite secure, and also since you're sitting behind a NAT (your router) meaning that whoever managed to tunnel in that way has some very impressive skills - far beyond the average script kiddie.

But if you want to be sure, save your stuff, format and reinstall.

---

### Post by popch on 2007-12-12
> **koenn said:**
> Forum admins are allowed to make fun of hapless community members and their problems ?

Only if they are humans (the forum admins). Judging from his contributions, KiwiNZ passes the Turing test with fanfares and cymbals.

Hence, yes, he should be. IMO.

---

### Post by fedex1993 on 2007-12-12
I dont think anything has ever happened like that form what i seen.
First stop downloading porn from torrents
Two i would start fresh with a clean install and dont move any programs over to a drive cause they can also be infected
three ...... good luck

---

### Post by popch on 2007-12-12
> **fedex1993 said:**
> 
three ...... good luck

four - use only appliances in virtual machines for downloading stuff and things, and use those appliances never, not ever, for other things or sites.

---

### Post by SomeGuyDude on 2007-12-12
> **popch said:**
> four - use only appliances in virtual machines for downloading stuff and things, and use those appliances never, not ever, for other things or sites.

Five: no need to tell us you were downloading porn. Really, you can just say you were downloading torrents via Azureus.

---

### Post by BertP on 2007-12-12
I have a wire-only network  Is there anyway to know whether I am allowing remote access?   Would a hacker have to have  root access to be able to place anything in my user's desktop directory if the user was currently logged in?

---

### Post by BertP on 2007-12-12
> **SomeGuyDude said:**
> Five: no need to tell us you were downloading porn. Really, you can just say you were downloading torrents via Azureus.

yeah, but because I was left with a "pervie.png" in my deskop,  I'm guessing that the attack might have come through my Azereus connection, so I explained the evidence in respect to my activities.

---

### Post by isecore on 2007-12-12
The reinstall would in all honesty require the least amount of work, most likely. There's no need to worry about applications being "infected" since a breach of security under Linux, like any UNIX-like system won't be about viruses. Scanning with AVG or Clamav or whatever will most likely be a waste of time.

If you really want to go through the machine with a fine-comb then be prepared to spend a lot of time on it, and you'll have to go through every process running as well as any directory that's world-writable - and this is providing that you haven't been exposed to a rootkit that hides them all.

What would be required to be able to place an image on your desktop is difficult to tell. Supposing a cracker has gotten access, he might have enabled the root account and that would've let him put that picture on your desktop.

---

### Post by hanzomon4 on 2007-12-12
Is that a hack people? By the way kudos for being so up front about it being porn, you have nothing to be embarrassed about.

Could the pervie.png been accidentally downloaded from firefox while you were surfing?

---

### Post by koenn on 2007-12-12
> **popch said:**
> Only if they are humans (the forum admins). Judging from his contributions, KiwiNZ passes the Turing test with fanfares and cymbals.

:)

---

### Post by steveneddy on 2007-12-12
Put that guy that you hate info in your /home folder.

---

### Post by khurrum1990 on 2007-12-12
Hi, that does sound suspicious, but as long as u have a firewall I doubt u have anything to worry about, u r safe and there is no need to reinstall. This isn't like Windows. By the way r u sure u just didn't press the print screen key by accident?

---

### Post by Steveway on 2007-12-12
Maybe someone has gotten remote-access through VNC or whatever came together with ubuntu and you accidently allowed him to access your desktop.
Then he would have looked what you did and made a screenshot etc...

---

### Post by p_quarles on 2007-12-12
I don't get this "nothing to worry about, Linux is safe" line that people are giving. That's just not true. Media players (particularly custom ones) are among the biggest security vulnerabilities out there, and that goes for all platforms. 

Plus, you don't need root access to get into the user's logged-in account. You don't even need a pre-existing way of remotely controlling the computer: if a media plugin of some kind were to contain malicious code, it could have easily taken control of the userspace. 

The only thing to do here is reinstall, and be more careful in the future.

---

### Post by rune0077 on 2007-12-12
> **SomeGuyDude said:**
> Five: no need to tell us you were downloading porn. Really, you can just say you were downloading torrents via Azureus.

And *now* you're telling him :)

No, seriously, that whole "Linux is so secure so don't worry" doesn't hold. Linux *is* secure, but it ain't bullet proof. People can, and do, hack it. It doesn't happen all the time like with Windows, but that's not the same as saying that it never happens. Basically I would start by using System Monitor or some such and look for suspicious processes running. If you find any, kill them, locate their source and delete files associated with them. I would also change all account passwords ASAP. If the problem persists, reinstall.

---

### Post by BertP on 2007-12-12
> **khurrum1990 said:**
> Hi, that does sound suspicious, but as long as u have a firewall I doubt u have anything to worry about, u r safe and there is no need to reinstall. This isn't like Windows. By the way r u sure u just didn't press the print screen key by accident?

I have hit the print screen before by accident but I could not explain the filename.   by default it would be "screenshot.png"  not "pervie.png"   I pretty sure that before this thread,  I have never typed the sequence  of letters, "pervie"

---

### Post by isecore on 2007-12-12
I personally think that this is rather some weird mistake or something, than an outright crack.

At least that's what I'd think without having more information, such as exactly what services are running on the machine that listens outwardly.

EDIT: I agree with everyone here who says that while Linux is fairly secure, it ain't bullet-proof. Security is more than just an operating system, it's a whole mindset. But none the less, without us having A LOT more information about the box in question it's impossible for us to say HOW he eventually was cracked, and instead do the admittedly incredibly generic advice of reinstallation and in the future using a heaftier password. The usual nonsense, really. But how this gentleman eventually was cracked, we will most likely never know.

---

### Post by koenn on 2007-12-12
I don't know much about torrents and Azareus, but here's what I think :
putting a file on the desktop doesn't require any elevated privileges. Any application can do it, eg you can download with firefox and say "save file to desktop". Any other app can do that. 

If Azareus was running and listening for incoming  requests, there's also no need for "some very impressive skills" to penetrate through a NAT router , if  the connection is already there.

My guess : a script kiddie with an Azareus exploit, and porn for bait. 

Suggestion : A reinstall is probably easiest (as epplained by others) - then review your the files in your home, and maybe run a virus scanner to see if it detects any suspicious scripts left in home.

---

### Post by rune0077 on 2007-12-12
> **p_quarles said:**
> I don't get this "nothing to worry about, Linux is safe" line that people are giving. That's just not true.

Ha! You beat me to it. I so wanted to be the first to point that out. Rats!

---

### Post by n3tfury on 2007-12-12
> **p_quarles said:**
> I don't get this "nothing to worry about, Linux is safe" line that people are giving. That's just not true. 

so true, but falls on deaf ears around here.

---

### Post by isecore on 2007-12-12
> **n3tfury said:**
> so true, but falls on deaf ears around here.

The problem is that too many people see it as either-or. Either something is a 100% safe, totally crack-proof, impossible to penetrate or it's like Windows, i.e. leaking like a sieve.

Linux is somewhere on the grayscale. Ubuntu is fairly secure out of the box, can be made quite secure with a little handiwork, but is far from bullet-proof. The only 100% secure computer is one that's turned off, unplugged and locked inside an underground bunker guarded by vicious dogs and armed guards - and even then I wouldn't be sure.

I don't subscribe to the "linux is safe" myth, but fact of the matter is that IT IS QUITE SAFE compared to most peoples needs and most peoples uses. I'd happily put any one of my family members on an Ubuntu machine with a default install, because I know they won't surf to dodgy websites giving questionable advice. So in that essence it's true that "linux is safe". Put a default Windows-machine and a default Ubuntu-machine and I guarantee the Windows-machine will be owned within minutes while the Ubuntu-box will ignore pretty much any malicious traffic. So again, "linux is safe".

But is it bulletproof? Is it even idiotproof? Nope, not in the longest run.

Ontopic: I say again that we will never know how/why/what happened to the threadstarters computer. Something went funky, either by accident or by some script-kiddie or some blackhat. Whatever happened, he's got issues with it and my advice is still to reinstall. It's the only way to be 100% sure that whatever happened is gone. Hopefully he's learned a bit about security and being healthily paranoid.

---

### Post by KiwiNZ on 2007-12-12
> **KiwiNZ said:**
> Get a bandage:)
 
I would seem that some did not recognise this post as one made in jest .
 
 
So ( with apologies to John Cleese)
 
I offer a complete and utter retraction. The imputation was totally without malice and was in no way fair comment and was motivated purely by a desire to lighten the situation, and I deeply regret any distress that my comments may have caused you or your family, and I hereby undertake not to repeat any such light  hearted comments at any time in the future.

---

### Post by blithen on 2007-12-12
> **SomeGuyDude said:**
> Five: no need to tell us you were downloading porn. Really, you can just say you were downloading torrents via Azureus.

EXACT thing I was thinking.

---

### Post by n3tfury on 2007-12-12
i'm surprised the word [SIZE="7"][COLOR="Red"]**PORN**[/COLOR][/SIZE] bothers so many people.

---

### Post by KiwiNZ on 2007-12-12
> **n3tfury said:**
> i'm surprised the word [SIZE=7][COLOR=red]**PORN**[/COLOR][/SIZE] bothers so many people.
 
 
eeeek

---

### Post by LaRoza on 2007-12-12
> **n3tfury said:**
> i'm surprised the word [SIZE="7"][COLOR="Red"]**PORN**[/COLOR][/SIZE] bothers so many people.

Now I am pissed off. (Whoops!)

---

### Post by blithen on 2007-12-12
> **n3tfury said:**
> i'm surprised the word [SIZE="7"][COLOR="Red"]**PORN**[/COLOR][/SIZE] bothers so many people.

:lolflag:

---

### Post by Wiebelhaus on 2007-12-12
> **isecore said:**
> The problem is that too many people see it as either-or. Either something is a 100% safe, totally crack-proof, impossible to penetrate or it's like Windows, i.e. leaking like a sieve.

Linux is somewhere on the grayscale. Ubuntu is fairly secure out of the box, can be made quite secure with a little handiwork, but is far from bullet-proof. The only 100% secure computer is one that's turned off, unplugged and locked inside an underground bunker guarded by vicious dogs and armed guards - and even then I wouldn't be sure.

I don't subscribe to the "linux is safe" myth, but fact of the matter is that IT IS QUITE SAFE compared to most peoples needs and most peoples uses. I'd happily put any one of my family members on an Ubuntu machine with a default install, because I know they won't surf to dodgy websites giving questionable advice. So in that essence it's true that "linux is safe". Put a default Windows-machine and a default Ubuntu-machine and I guarantee the Windows-machine will be owned within minutes while the Ubuntu-box will ignore pretty much any malicious traffic. So again, "linux is safe".

But is it bulletproof? Is it even idiotproof? Nope, not in the longest run.

Ontopic: I say again that we will never know how/why/what happened to the threadstarters computer. Something went funky, either by accident or by some script-kiddie or some blackhat. Whatever happened, he's got issues with it and my advice is still to reinstall. It's the only way to be 100% sure that whatever happened is gone. Hopefully he's learned a bit about security and being healthily paranoid.

I like you man , add me to your friends.

anyway , I agree with isecore 100%.

---

### Post by Wiebelhaus on 2007-12-12
> **KiwiNZ said:**
> I would seem that some did not recognise this post as one made in jest .
 
 
So ( with apologies to John Cleese)
 
I offer a complete and utter retraction. The imputation was totally without malice and was in no way fair comment and was motivated purely by a desire to lighten the situation, and I deeply regret any distress that my comments may have caused you or your family, and I hereby undertake not to repeat any such light  hearted comments at any time in the future.

I got the joke and thought it was funny , Last thing we need is a bunch of robotic posters.

---

### Post by jdong on 2007-12-12
> **n3tfury said:**
> i'm surprised the word [SIZE="7"][COLOR="Red"]**PORN**[/COLOR][/SIZE] bothers so many people.

WTF? How'd I end up here? *goes back to google results*

---

### Post by floke on 2007-12-12
Would checking the logs on the router help?
You could also check the /var/auth.log to see what privileges have been used and when and what for etc.

---

### Post by corney91 on 2007-12-12
> **jdong said:**
> WTF? How'd I end up here? *goes back to google results*

:lolflag:

---

### Post by Bruce M. on 2007-12-12
> **n3tfury said:**
> i'm surprised the word [SIZE="7"][COLOR="Red"]**PORN**[/COLOR][/SIZE] bothers so many people.

Me neither, after all most **[SIZE="7"][COLOR="Red"]P[/COLOR][/SIZE]eople [SIZE="7"][COLOR="Red"]O[/COLOR][/SIZE]bey [SIZE="7"][COLOR="Red"]R[/COLOR][/SIZE]ules [SIZE="7"][COLOR="Red"]N[/COLOR][/SIZE]ormally** don't they?

And if they don't maybe re-install isn't such a bad idea.

---

### Post by t0p on 2007-12-12
> **KiwiNZ said:**
> I would seem that some did not recognise this post as one made in jest .
 
 
So ( with apologies to John Cleese)
 
I offer a complete and utter retraction. The imputation was totally without malice and was in no way fair comment and was motivated purely by a desire to lighten the situation, and I deeply regret any distress that my comments may have caused you or your family, and I hereby undertake not to repeat any such light  hearted comments at any time in the future.

PAH!! You don't fool *me*! Your wicked comment about bandages was clearly meant to harm and distress.  In fact, it wouldn't surprise me if it was you who was going round cracking innocent porn-fans' machines and leaving malicious pervie.png screenshots for all to see. 

In short: BOO!! You're NASTY!!

---

### Post by seventhc on 2007-12-12
It might be a good idea to change your passwords on your machine...for both your regular user and the root password.

---

### Post by KiwiNZ on 2007-12-12
> **t0p said:**
> PAH!! You don't fool *me*! Your wicked comment about bandages was clearly meant to harm and distress.  In fact, it wouldn't surprise me if it was you who was going round cracking innocent porn-fans' machines and leaving malicious pervie.png screenshots for all to see. 

In short: BOO!! You're NASTY!!

No don't have them they make you go blind

---

### Post by BertP on 2007-12-13
Just to let you guys know, I have been doing a lot of checking on my computer and router as well as doing a variety of tests such as port scans and have found nothing.

I now feel that this  was most likely an accidental screen capture and the fact that the fragment of the word captured as the filename  could be viewed as commentary on my use of Azureus was just a strange coincidence.   Of course,  when I first saw the filename on my desktop ,I just freaked out!   

And while I am now thinking that it is more likely that I was attacked by paranoia and not a hacker,  It's probably not a bad idea to do the reinstall, just in case! ;)

---

### Post by Lostincyberspace on 2007-12-13
And there might be some code somewhere in Ubuntu that can only trigger if you were doing what you were doing that caused it to make the screen shot. Possible and funny if true.

---

### Post by jdong on 2007-12-13
Well the Alt-Printscreen screenshots DO cause the image to take the name of the active window, like this window is currently screenshotting as "Ubuntu Forums - Reply To Topic - Mozilla Firefox.png" on my desktop. It could just be that, plus some paranoia.

I agree with the OP that this is likely a mind trick. Don't worry, I've done that too many times to be funny -- it's surprising how real this highway hypnosis / "tunnel mind" stuff is. Sometimes I look over some of my robotics related code (~25,000 lines), comments, and VCS changelogs and I do not recall ever writing any of that stuff at all. Yet it's all signed with my GPG key and I KNOW I was the one who wrote all of the stuff I was reading, but it just simply doesn't ring a bell. And this is all stuff I've done within the past few years, sometimes just a month after writing the code!

---

### Post by GrahamOtte on 2007-12-13
> **n3tfury said:**
> i'm surprised the word [SIZE="7"][COLOR="Red"]**PORN**[/COLOR][/SIZE] bothers so many people.

OMG did u jsust say wut i think u said  **shiver**

---

### Post by FuturePilot on 2007-12-13
Lol, this thread is funny

It very well could have been a strange coincidence. A few times I've wondered how a file got somewhere and then I remembered I put it there. :p

---

### Post by hanzomon4 on 2007-12-13
> **BertP said:**
> Just to let you guys know, I have been doing a lot of checking on my computer and router as well as doing a variety of tests such as port scans and have found nothing.

I now feel that this  was most likely an accidental screen capture and the fact that the fragment of the word captured as the filename  could be viewed as commentary on my use of Azureus was just a strange coincidence.   Of course,  when I first saw the filename on my desktop ,I just freaked out!   

And while I am now thinking that it is more likely that I was attacked by paranoia and not a hacker,  It's probably not a bad idea to do the reinstall, just in case! ;)

Porn makes you paranoid... and horny =)

---

### Post by SupaSonic on 2007-12-13
Was the porn worth it at least?

---

### Post by nutter78 on 2007-12-13
doesn't [SIZE="7"][COLOR="Red"]PORN[/COLOR][/SIZE] stand for [SIZE="7"][COLOR="Red"]P[/COLOR][/SIZE]olice [SIZE="7"][COLOR="Red"]O[/COLOR][/SIZE]bserving [SIZE="7"][COLOR="Red"]R[/COLOR][/SIZE]andy [SIZE="7"][COLOR="Red"]N[/COLOR][/SIZE]ewbies 

No wonder there is so much paranoia out there!

---

### Post by EdThaSlayer on 2007-12-13
One should back up his data to a portable hard drive and immediately reinstall and use a stronger password in the future.

---

### Post by rax_m on 2007-12-13
LOL that was an entertaining 10min read :D

---

### Post by khurrum1990 on 2007-12-13
It can happen that sometimes pictures taken during screenshots of specific things have their own file name. The only thing that sounds suspicious to me still is the file name, otherwise I have noticed that sometimes in Ubuntu while dealing with pictures even when I am offline I see some .png file on the desktop.

---

### Post by n3tfury on 2007-12-13
> **nutter78 said:**
> doesn't [SIZE="7"][COLOR="Red"]PORN[/COLOR][/SIZE] stand for [SIZE="7"][COLOR="Red"]P[/COLOR][/SIZE]olice [SIZE="7"][COLOR="Red"]O[/COLOR][/SIZE]bserving [SIZE="7"][COLOR="Red"]R[/COLOR][/SIZE]andy [SIZE="7"][COLOR="Red"]N[/COLOR][/SIZE]ewbies 

No wonder there is so much paranoia out there!

who's Randy.

---

### Post by hanzomon4 on 2007-12-13
Randy - slang for hot and bothered

---

### Post by n3tfury on 2007-12-13
okaaaay.

i'd rather not associate a dude's name to when my hormones start kicking it into high gear.  have fun with that.

---

### Post by hanzomon4 on 2007-12-13
Austin Powers?

---

### Post by n3tfury on 2007-12-13
k, don't recall that bit.  must not have been that funny to me i guess.

---

### Post by aaaantoine on 2007-12-13
> **n3tfury said:**
> okaaaay.

i'd rather not associate a dude's name to when my hormones start kicking it into high gear.  have fun with that.

Brits must get a kick out of guys named Randy.

But then again, it's not like we find it funny when a guy is named Dick.

But then *again*... Yes, we do.

---

### Post by tech9 on 2007-12-13
> **p_quarles said:**
> I don't get this "nothing to worry about, Linux is safe" line that people are giving. That's just not true. Media players (particularly custom ones) are among the biggest security vulnerabilities out there, and that goes for all platforms. 

Plus, you don't need root access to get into the user's logged-in account. You don't even need a pre-existing way of remotely controlling the computer: if a media plugin of some kind were to contain malicious code, it could have easily taken control of the userspace. 

The only thing to do here is reinstall, and be more careful in the future.

well stated p_quarles :)

---

### Post by tech9 on 2007-12-13
> **KiwiNZ said:**
> I would seem that some did not recognise this post as one made in jest .
 
 
So ( with apologies to John Cleese)
 
I offer a complete and utter retraction. The imputation was totally without malice and was in no way fair comment and was motivated purely by a desire to lighten the situation, and I deeply regret any distress that my comments may have caused you or your family, and I hereby undertake not to repeat any such light  hearted comments at any time in the future.

nice apology... remember it is good - that you (admins) lead by example :)

---

### Post by seventhc on 2007-12-13
alt+prt sc will give it a title like 'ubuntu forums' or whatever page your on as said earlier by '[[COLOR=#980101]**jdong**[/COLOR]]("http://ubuntuforums.org/member.php?u=780")' and if you hit prt sc by itself then it would show up as 'Screenshot.png' and numbers would be added by default if you never change the name so it would go as follows Screenshot.png then Screenshot 1.png, etc.  useless info I know, but hitting the prt sc key by itself seems more likely than hitting a key combination such as Alt+Prt Sc.
just my thoughts.
I would double check everything just to be safe.
maybe I'm just paranoid though.

---

### Post by tech9 on 2007-12-13
> **rax_m said:**
> LOL that was an entertaining 10min read :D
+1

---

### Post by chameleonkid on 2007-12-13
I don't know if this has been suggested but maybe attempt to find out when this screenshot was taken, by right clicking->properties and hopefully under the modified part it will say when it was last modified, If you haven't touched it I am guessing it will be the time when it was taken. Just an idea.

---

### Post by koenn on 2007-12-13
> **KiwiNZ said:**
>  ... and I hereby undertake not to repeat any such light  hearted comments at any time in the future.
I beg you to please reconsider. 
My narrow shoulders and feeble back could never carry the responsability and guilt of having caused such dreadful result.

---

### Post by lespaul_rentals on 2007-12-13
> **isecore said:**
> But again, I find it somewhat difficult to imagine that you've been cracked. Ubuntu in it's default configuration (even without firewall) is quite secure, and also since you're sitting behind a NAT (your router) meaning that whoever managed to tunnel in that way has some very impressive skills - far beyond the average script kiddie.

Oh, yeah, because there's no such thing as a backdoor Trojan horse that reverse connects. :rolleyes:

There are Linux backdoors out there.  All he had to do was download some pr0n that was bundled with a malicious file, and there you go -- who cares about NAT or a router then?

Also, Linux might be a thousand times more secure than Windows, but remember that there are many exploits still out there.  If you want a truly secure system, try BSD.

[quote=koenn]Forum admins are allowed to make fun of hapless community members and their problems ?[/quote]

Doesn't bother me that a mod made a little joke.  I hope this guy doesn't get his bank account/credit card owned but he was downloading pr0n.  He should know the risks.  Pr0n is like a grenade.  Sure, it might not blow up until you take the pin out, but who wants to play catch with one?  Same with warez.  You want to dig around the scum of the Interwebs, you should be ready to handle the consequences.

My advice to you would be to re-install your operating system.  A format will get rid of any malware that has infected you.

---

### Post by tech9 on 2007-12-13
> **koenn said:**
> I beg you to please reconsider. 
My narrow shoulders and feeble back could never carry the responsability and guilt of having caused such dreadful result.

wow, of all the sarcasm :roll:

---

### Post by koenn on 2007-12-13
> **lespaul_rentals said:**
> Doesn't bother me that a mod made a little joke.  I hope this guy doesn't get his bank account/credit card owned but he was downloading pr0n.  He should know the risks.  Pr0n is like a grenade.  Sure, it might not blow up until you take the pin out, but who wants to play catch with one?  Same with warez.  You want to dig around the scum of the Interwebs, you should be ready to handle the consequences..
and all of that is, of course, knowledge embedded in the human genoom so everyone 'just knows'.

---

### Post by Mr.Auer on 2007-12-13
The most likely way to get "hacked" using Ubuntu is if you run a SSH server (NOT installed by default!) and allow logins from the net. People tend to try and guess logins and passwords, automated or hand picked. Ive sometimes noticed Ive been specifically targeted for a dictionary attack, the attacker used usernames and passwords in my language. He had gone thru hundreds when I noticed this, I suppose I angered someone on irc etc. I could see his tries from /var/log/auth.log. You can easily prevent brute force logging tries by installing Fail2Ban (it bans ips after a certain amount of failed logins) or by allowing SSH logins only with a certain key or from certain IPs.

If youre really paranoid, you will want to put Conky etc to output your system and authentication logs to your desktop etc so you can always monitor logins and other activity like sudo commands etc continuosly.

A couple of quick tools that spot most KNOWN trojans and other assorted hacks are chkrootkit (Check rootkit) and rkhunter, Rootkit Hunter. They check for well known unix exploits and trojans, and check some more used system binaries for any changes. Theyre both in the repositories.

Hacking thru Azureus etc. doesnt sound too likely imho, unless you have allowed console access to Azureus from the internet.

The other easy way of getting hacked is running or installing programs or scripts from unverified sources...Some nasty person COULD possibly spread a malevolent script thru Ubuntu forums etc. You should always trust the people whose code you go ahead and run. You should always go thru a script etc.. and see what it does before running it. If you dont know, dont run it.

---

### Post by koenn on 2007-12-13
> **tech9 said:**
> wow, of all the sarcasm :roll:
There's no sarcasm there.

---

### Post by jdong on 2007-12-13
> **Mr.Auer said:**
> 

The other easy way of getting hacked is running or installing programs or scripts from unverified sources...Some nasty person COULD possibly spread a malevolent script thru Ubuntu forums etc. You should always trust the people whose code you go ahead and run. You should always go thru a script etc.. and see what it does before running it. If you dont know, dont run it.

In all honesty  that's easier than brute forcing a 3-letter-long password on an open SSH server. Just post a "repository" of "<insert cool 3D desktop here>" packages.

I cannot stress the importance of verifying trust of the authors/distributors of what you install.

---

### Post by isecore on 2007-12-16
> **lespaul_rentals said:**
> Oh, yeah, because there's no such thing as a backdoor Trojan horse that reverse connects. :rolleyes:

There are Linux backdoors out there.  All he had to do was download some pr0n that was bundled with a malicious file, and there you go -- who cares about NAT or a router then?

Also, Linux might be a thousand times more secure than Windows, but remember that there are many exploits still out there.  If you want a truly secure system, try BSD.

Of course there are backdoors, but there's very few that execute themselves from a downloaded file a.la. Windows. Most backdoors in Linux rely on action of witless users to execute them, or a compromised service such as a webserver, SSH-server or the like. Of course there are exploits as well - there doesn't exist anything which is unexploitable.

Which leads me to your claim about BSD. It's hogwash. BSD is vulnerable to essentially the same things as Linux, and depends on the same things for security. If you're running a vulnerable service on a BSD system it will be susceptible to the same exploits. Your claim is essentially the same myth that "linux is safe" but applied to BSD instead. I agree that most BSD-systems are better out of the box, but if you run just ONE vulnerable service you'll be just as open to exploits as any Linux-box. BSD-systems are more conservative and rely more on thouroghly tested software, and differs in very little regard from less bleeding-edge distributions of Linux such as Debian which also thoroughly tests their packages before putting them into production.

---

### Post by Xbehave on 2007-12-16
wow this theread has gone oftopic
linux is designed with security in mind
but bsd is designed for secuirty
while neither is 100% safe bsd is more secure, nody can deny that

the way to make a 99% secure system has been around for years but as security = usability^-1 its rarely used
a system like hardend gentoo using SElinux and the sort would require alot of work to get an attack from azureus to affect firefox.
(other hardend setups are avalible)
ubuntu is looking to greatly improve its security with apparmor, which will prevent cross program attacks.

unforunatly if this was a trojan none of this would have helped once you got infected, any attempt to prevent trojans would require substantial work to xorg

---

### Post by seventhc on 2007-12-16
This thread should probably be marked as closed.

---

### Post by 20after4 on 2007-12-16
Bert - I really think this was a simple azerus exploit. I bet it's an automated script set to take a screenshot at some random time delay, I imagine it was intended to screenshot the actual viewing of p0rn rather than the website that you happened to be accessing at the time. It sounds to me like a practical joke more than anything - something that was intended to scare you and possibly expose your porn watching habbits to other users of your computer.

That's just my 2.7 cents.

---

### Post by jdong on 2007-12-16
> **Xbehave said:**
> wow this theread has gone oftopic
linux is designed with security in mind
but bsd is designed for secuirty
while neither is 100% safe bsd is more secure, nody can deny that


That assertion is a very difficult one to back up. In the end, most people use the same set of services under BSD or Linux (i.e. Firefox, the LAMP stack, OpenSSH, and so on), and if there were an exploitable aspect of any of those things, then both OS'es would be equally susceptible, and also of course not accountable for what happens beyond their control.

I've seen far far more intrusions happen due to poor sysadmin habits, misconfigured services, unpatched vulnerabilities, and even 0-days from popular services than from a kernel-based exploit on the types of services I've administered, though admittedly on a shell server where many untrusted users are granted access, this breakdown would be far different.


Based on what I see, there's really no difference between BSD and Linux in terms of security for what the average user or server admin does. The admin's habits and precautions taken would be a far bigger impact and should be focused on, not the internet-reputed fame of some operating system over another.

---

