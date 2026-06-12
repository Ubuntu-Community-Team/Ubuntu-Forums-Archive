---
title: "Security discussion"
date: 2011-07-18
forum: Security
---

### Post by jtarin on 2011-07-18
> **jtarin**
Re: VLC Media Player vulnerable to heap overflow exploits
Quote:
Originally Posted by jtarin View Post
Has it been exploited? I dunno...let me take a poll.
It says "A vulernability to an exploit", which means the possibility exist at the time for it to be exploited.



Do you imagine everyone using VLC or some other affected application has implemented Apparmor or much less know what it is.I'm afraid most newbies do not......better to be on the safe side than not. I'm not some security nut-job crying wolf, but I deal with a lot of .avi's and I'm sure there are others. Which should come first...the accident or the warning?


> **bodhi.zazen **

With security you can not have your cake and eat it too.

Sounds as if:

_1. You do not know the difference between a vulnerability and an exploit._

'Au Contrare'

vul·ner·a·ble/&#712;v&#601;ln(&#601;)r&#601;b&#601;l/Adjective
1. Exposed to the possibility of being attacked or harmed, either physically or emotionally: "we were in a vulnerable position".

exploit
 &#8212; vb
2. 	to take advantage of (a person, situation, etc), esp unethically or unjustly for one's own ends

> **bodhi.zazen **
2. You can not complain about potential vulnerabilities and then refuse to learn to use the appropriate security tool.
Who was complaining? I posted a notice on a potential problem and left it at that. I never said anything about not knowing how to use Linux security tools......you assumed I did. 
I know how to use Apparmor, but possibly people new to Linux do not.


> **bodhi.zazen **I am closing this thread now as these vulnerabilities are listed, and managed elsewhere (Launchpad, bug reports -> mark as a security issue), not on the forums, not with polls on the forms, and not by an unwillingness to learn.

Feel free to start a new thread once you have done some reading and have some questions, otherwise relax and enjoy Ubuntu 
It's helpful for you to post links and most appreciative I would imagine by those reading these topics, but for you to make slighted comments about what I posted and to close the thread is not appropo.
This is the first time in 13 years on a forum one of my post have been closed due to disseminating information. Three Cheers!!!!:P

---

### Post by Dangertux on 2011-07-18
My 2 cents on that whole thing since I am not particularly sure which VLC exploit you are talking about. 

There have been MANY VLC exploits in the past. Its a popular application. As far as if someone has exploited it versus discovering the vulnerability. It really doesn't matter the vulnerability is known , writing an exploit based on a known vulnerability is an easy process. 

From what I read of your post it seems like the flaw is being tracked so why worry about it? Sure it's a vulnerability, all software has them. The scary ones are the ones that aren't discovered ;-)

I am sure it will be fixed in the future. Which leads to why the other poster mentioned apparmor. Apparmor is a great catch all for unpatched vulnerabilities. You can't expect developers to patch a 0 day instantly, that is why they are called 0 days. That is why things like apparmor and selinux exist. To mitigate the instapwn factor of a 0 day exploit. 

So to answer your initial question I am sure someone has exploited it and I am sure the metasploit module will be posted soon if not already lol.
 
Yes I think apparmor is a great idea in this case if youre worried about this vulnerability.  The other two alternatives are fix it yourself or stop using VLC until it's patched.

---

### Post by jtarin on 2011-07-18
> **Dangertux said:**
> My 2 cents on that whole thing since I am not particularly sure which VLC exploit you are talking about. 

There have been MANY VLC exploits in the past. Its a popular application. As far as if someone has exploited it versus discovering the vulnerability. It really doesn't matter the vulnerability is known , writing an exploit based on a known vulnerability is an easy process. 

From what I read of your post it seems like the flaw is being tracked so why worry about it? Sure it's a vulnerability, all software has them. The scary ones are the ones that aren't discovered ;-)

I am sure it will be fixed in the future. Which leads to why the other poster mentioned apparmor. Apparmor is a great catch all for unpatched vulnerabilities. You can't expect developers to patch a 0 day instantly, that is why they are called 0 days. That is why things like apparmor and selinux exist. To mitigate the instapwn factor of a 0 day exploit. 

So to answer your initial question I am sure someone has exploited it and I am sure the metasploit module will be posted soon if not already lol.
 
Yes I think apparmor is a great idea in this case if youre worried about this vulnerability.  The other two alternatives are fix it yourself or stop using VLC until it's patched.

Not my personal concern....the [original post]("http://ubuntuforums.org/showthread.php?t=1804795&goto=newpost") was merely and simply an announcement as to the vulnerability and with a link describing the fix in process, for those with an interest . Then it boiled over into something else.:P

---

### Post by uRock on 2011-07-18
I think the reasoning behind closing the other thread is due to the fact that there isn't much typical end users can do except not use avi files from untrusted sources.

Personally, I have not seen an .avi file since the days of Kazaa, so I am not sure how many people may be affected by such a vulnerability. Are there a lot of sites offering videos as .avi?

I am not sure there are any AppArmor profiles out there for VLC. I opened a movie within VLC and ran the **sudo apparmor status** command and do not see one in use.

---

### Post by Dangertux on 2011-07-18
On I see... I did read the original thread as well. 

And while the replies did seem rather, snippy if you will it wasn't that bad.  I think another factor is this, there are a lot of very new users on the forum, and this is a support forum primarily. So the concern might be something like screaming fire in a movie theater. I know that might sound silly but have you read some of the "I got hacked" posts. Honestly there really isn't too much to do if you're going to be watching a lot of AVI's other then to pony up and configure apparmor. Or take your chances.  

In any case I would just let it be for now and write it off.

---

### Post by jtarin on 2011-07-18
> **uRock said:**
> Personally, I have not seen an .avi file since the days of Kazaa, so I am not sure how many people may be affected by such a vulnerability. Are there a lot of sites offering videos as .avi?
My computer downloads .avi files 18 hours a day....7 days a week using jdownloader.:P

---

### Post by Dangertux on 2011-07-18
Well then you're in luck they patched it lol

[http://www.videolan.org/security/sa1106.html](http://www.videolan.org/security/sa1106.html)

It's actually been patched since the day the advisory was released. So I am really confused as to what the problem is now.

---

### Post by jtarin on 2011-07-18
> **Dangertux said:**
> On I see... I did read the original thread as well. 

And while the replies did seem rather, snippy if you will it wasn't that bad.  I think another factor is this, there are a lot of very new users on the forum, and this is a support forum primarily. So the concern might be something like screaming fire in a movie theater. I know that might sound silly but have you read some of the "I got hacked" posts. Honestly there really isn't too much to do if you're going to be watching a lot of AVI's other then to pony up and configure apparmor. Or take your chances.  

In any case I would just let it be for now and write it off.

I hear ya....point well taken...believe me. I just don't like hit and run tactics....or in this case snip and run....then close.:P
Rather than yell fire it was more like..."Hey is it getting warm in here or is it just me"?

---

### Post by uRock on 2011-07-18
> **Dangertux said:**
> It's actually been patched since the day the advisory was released. So I am really confused as to what the problem is now.

That is usually the case.

Lets keep the thread on topic. Post the other stuff in the RC or PM it, please. :)

---

### Post by jtarin on 2011-07-18
> **Dangertux said:**
> Well then you're in luck they patched it lol

[http://www.videolan.org/security/sa1106.html](http://www.videolan.org/security/sa1106.html)

It's actually been patched since the day the advisory was released. So I am really confused as to what the problem is now.

> Solution

VLC media player 1.1.11 addresses this issue and introduces further stability fixes. A source code patch is also available _**as an alternative. **_
A source code patch is not exactly a fix in the strictest sense. How many people do you think are compiling their own VLC? Will the repos jump ahead to version 1.1.11? It's not just about VLC...but repos keeping current with the latest. They're already behind with this one.Last I looked it was sitting at 1.1.9

---

### Post by cariboo on 2011-07-18
Vlc version 1.1.11-ubuntu1 is in the Oneiric repositories, the update came through this morning.

---

### Post by jtarin on 2011-07-18
> **cariboo907 said:**
> Vlc version 1.1.11-ubuntu1 is in the Oneiric repositories, the update came through this morning.
Good news for all......thanks!:P
Us peasants at 10.10 could use some trickle down.:P

---

### Post by uRock on 2011-07-21
Patch implemented in Ubuntu 10.04. :D

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198016&stc=1&d=1311289692[/IMG]

---

### Post by jtarin on 2011-07-21
That's thatch, but why does it show ver-1.06 when the present from my pppa is at 1.09 and newest onsite is 1.10?

---

### Post by uRock on 2011-07-22
> **jtarin said:**
> That's thatch, but why does it show ver-1.06 when the present from my pppa is at 1.09 and newest onsite is 1.10?

That is the version used in 10.04.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198031&stc=1&d=1311307530[/IMG]

---

### Post by jtarin on 2011-07-22
So I have to downgrade to get the patch? That's hilarious.....downgrade to upgrade.:P

---

### Post by uRock on 2011-07-22
> **jtarin said:**
> So I have to downgrade to get the patch? That's hilarious.....downgrade to upgrade.:P

Lol, what? The update should be coming out for every release unless you are using a non-Ubuntu PPA. If you are using the VLC PPA, then you have them to thank for not forwarding the patch update.

Edit: Ubuntu 10.10 has received this update as well.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198081&stc=1&d=1311350462[/IMG]

---

### Post by uRock on 2011-07-22
11.04 has the update as well. Looks like Canonical has done their part in getting us the patch. :D

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198082&stc=1&d=1311351546[/IMG]

---

### Post by jtarin on 2011-07-22
> **uRock said:**
> If you are using the VLC PPA, then you have them to thank for not forwarding the patch update.Anyone I should thank in particular?:P

---

### Post by andrew.46 on 2011-07-23
> **jtarin said:**
> [...] newest onsite is 1.10?

That would be **[COLOR="Red"]*1.1.11*[/COLOR]** actually. This nitpicking post is courtesy of [xkcd]("http://xkcd.com/386/") :). BTW you can always build your own and apply whatever patches you want:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

There is a section there for the release version too.

---

### Post by jtarin on 2011-07-23
> **andrew.46 said:**
> That would be **[COLOR="Red"]*1.1.11*[/COLOR]** actually. This nitpicking post is courtesy of [xkcd]("http://xkcd.com/386/") :). BTW you can always build your own and apply whatever patches you want:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

There is a section there for the release version too.Check again...your in the wrong forum. That's for Windows pre-built. [URL="http://www.videolan.org/vlc/download-ubuntu.html"]For Ubuntu builds.

[/URL]I'm perfectly capable of building software, but if I wanted to do that I'd ditch Ubuntu and stick solely with Slackware.:P

---

### Post by andrew.46 on 2011-07-23
> **jtarin said:**
> Check again...your in the wrong forum. That's for Windows pre-built. [For Ubuntu builds.]("http://www.videolan.org/vlc/download-ubuntu.html")

Actually I think I *have* staggered into the wrong discussion and looking back through the thread I can see a little heat as well so I shall depart. However you will find that the latest stable source is in fact here:

[http://download.videolan.org/pub/videolan/vlc/1.1.11/](http://download.videolan.org/pub/videolan/vlc/1.1.11/)


> I'm perfectly capable of building software, but if I wanted to do that I'd ditch Ubuntu and stick solely with Slackware.:P

You may find that the Slackware camp will usually install vlc from alienBOB's script or packages:

[http://connie.slackware.com/~alien/slackbuilds/vlc/build/vlc.SlackBuild](http://connie.slackware.com/~alien/slackbuilds/vlc/build/vlc.SlackBuild)

so not a lot of independent building required usually. Mind you I see that even he has not upgraded to the very latest. Anyway my apologies for the interruption I shall go back to my normal business :).

---

