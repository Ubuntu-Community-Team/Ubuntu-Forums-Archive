---
title: "Warning! Quickstart Potentially Malicious!"
date: 2008-04-21
forum: The Cafe
---

### Post by cegpope on 2008-04-21
There is a system backup and recovery tool floating around the forums called Quickstart, USE AT YOUR OWN RISK!


QUICKSTART IS CLOSED SOURCE, SO IT IS IMPOSSIBLE TO KNOW WHAT IT IS REALLY DOING!


The author will not answer questions about how Quickstart works or why it depends on the installation of certain files!


Quickstart requires the installation of specific mail transfer and mail user agents which should enable it to send information from your computer without permission and without knowing the content of it's transmissions. Additionally, failure to have these installed prevents the program from working.


Inquiring about the function of Quickstart results in being flamed for not trusting a stranger on the internet!


QUICKSTART **MAY OR MAY NOT** be malicious, but the author will not provide information that allows for trust assessment.


Avoid Quickstart to protect your computer from the potential danger which is hidden from the user.

---

### Post by Gen2ly on 2008-04-21
link available?

---

### Post by billgoldberg on 2008-04-21
I believe this is the program (script):

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=613462](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=613462)

---

### Post by Google Spider on 2008-04-21
I always stick to the repos.:) Never heard of Quick start before looking at this thread. Thanks for the info.


EDIT:

 Yeah, I saw those posts and how they replied to your question was ridiculous.:mad: But as you said, it "may or may not" be malicious. :redface:

---

### Post by FredB on 2008-04-21
First time I heard about it. Thanks for the info.

---

### Post by skymera on 2008-04-21
> **Google Spider said:**
> I always stick to the repos.:) Never heard of Quick start before looking at this thread. Thanks for the info.


EDIT:

 Yeah, I saw those posts and how they replied to your question was ridiculous.:mad: But as you said, it "may or may not" be malicious. :redface:

+1
If you stick to the repos you dont need to worry :)
Theres plenty of packages availible.

---

### Post by bryncoles on 2008-04-21
i recently came across 'testdisk' - its in the repo's (though you might need universe and medibuntu enabled, cause i dont know which repo its in). thats open source file recovery software, and its the one piece of software thats really, really impressed me! im telling everyone about it!

---

### Post by PartisanEntity on 2008-04-21
I have never heard of Quickstart, but am surprised that the developer doesn't want to answer your question **cegpope**, I have posted that I too am interested in the answer, strange behaviour on the developers part.

---

### Post by bigbrovar on 2008-04-21
hmm if it is closed like Bill act like Bill send anonymous infor like Bill .. What is it ?

---

### Post by Tomosaur on 2008-04-21
It is a little suspicious at least, but I'd keep the tin-foil hats in the cupboard for the time being. It's worth investigating, I guess, so if anyone with the relevant know-how cares to monitor who QuickStart connects to, I'm sure a lot of people would be grateful for the info.

Anyone else worried about it, either just don't use QuickStart, or disallow it from connecting to anything.

---

### Post by aeiah on 2008-04-21
you could use darkstat or wireshark to see what's being communicated with the outside world

---

### Post by eragon100 on 2008-04-21
Thanx for mentioning it, I had never heard of it, I just used it to install the dvd codecs :guitar:

---

### Post by fatality_uk on 2008-04-21
Having read 10 of the 107 pages, I feel a little less secure using this app. I had recommended it for a friend and they did make use of it, but I suggest they will remove it now. The reason being is that while the basic premise of the program is great, and eases the implimentation of some functionality within Ubuntu, mdpalow seems to have no idea why he needs to use MAILX.

He included it because some others apps installed it. Well that's fine but your releasing a potential open door for someone by publishing the fact that he uses it but doesn't monitor the contents of it's transactions is silly in the extreme.

Quote from mdpalow.
> Why does MAILX make Scheduled Back-ups work? I REALLY DON"T KNOW. I just know it does. In fact, there's no code in the program that even has 'MAILX' in it. I have it installed at the very beginning of the program and that's it; no more reference to it.

I realise this is a freeware application, it's not FOSS, but still, it doesn't sit that well having MAILX installed onto someones system without there being a good reason.

I seem to remember this was a script initially!! Perhaps if it had stayed that way a lot of people would be happier.

---

### Post by smartboyathome on 2008-04-21
I think it used to be called uBackup, maybe I can dig around and see if I can find that script again. It could probably be reverse engineered if absolutely necessary. :(

EDIT: I couldn't find the script. I did find the reason why it is closed source, though. The reason is because mdpalows has spent a lot of time on it, and doesn't want the code taken away by someone.

---

### Post by the_darkside_986 on 2008-04-21
Crap... tell me it isn't so... One of the main reasons why I use free/libre systems such as Ubuntu is to avoid being ***-raped by "free"ware malicious programs that have infested the Windows platform. Well as long as this crap doesn't start appearing in the repositories, I guess it's not a concern but new users should be informed about the purpose of FLOSS and the dangers of using untrusted proprietary applications (regardless of their monetary price). But this seems very curious so I am setting up a "sandbox" user account so I can download and look at the binary contents of the file and perhaps try to see what exactly it is trying to do. And I'll be examining this with a Free/libre hex editor and Free/libre software tools.

---

### Post by Het Irv on 2008-04-21
I have helped with the Developing of QuickStart from the near the beginning, ( I haven't done much but I have helped test).

To the OP:  You just happened to post at a bad time,  every now and then someone will come on and ask why QS is not open source.  mdplow has never really given a clear answer other than personal reasons when asked this and many of the regular posters in the thread are tired of this discussion.  Right before you posted someone else had just asked the same question, and it was just bad timing.

As to MAILX, something in the code for MAILX and it dependencies allows for the scheduled backups to occur, and for a while it was not in QuickStart.  mdplow put in the installer after it was determined that it was causing problems by not being installed.  

QuickStart has been and continues to be mainly for mdplow's personal use, but he allows others to download and use it, it has come a long way from its orgins, (it was uBackup previously),  and I have never had any problems.  If you don't trust it, then don't use it, but I have no reason not to trust the developer or his code so I will continue to use it.

---

### Post by Bruce M. on 2008-04-21
If you look at [Post #1050]("http://ubuntuforums.org/showpost.php?p=4758780&postcount=1050") you'll see it is a good explanation as to why MAILX is in QS.

---

### Post by fatality_uk on 2008-04-21
It's not that I don't trust him, I am sure that he no real mal intent. However, the problem lies in the fact that A) QuickStart installs a powerful application without my explict consent B) There is no source

And to make the point again. MAILX is installed without knowing why!!
Quote from mdpalow.> 
Why does MAILX make Scheduled Back-ups work? I REALLY DON"T KNOW. I just know it does. In fact, there's no code in the program that even has 'MAILX' in it. I have it installed at the very beginning of the program and that's it; no more reference to it.

[http://www.scit.wlv.ac.uk/cgi-bin/mansec?1+mailx](http://www.scit.wlv.ac.uk/cgi-bin/mansec?1+mailx)

---

### Post by KiwiNZ on 2008-04-21
I posted this in th ethread in question 
 
"...If you dont want to answer a question multiple times over a period of time put up a FAQ , dont chastise members for asking a question they really need an answer for."
 
I stand by that and urge the Dev to put up a FAQ.
 
If members continue to be chastised for asking questions several times then the continuation of that thread would be reviewed.

---

### Post by the_darkside_986 on 2008-04-21
Indeed, the developer may have no malicious intent, but it is difficult to find out what software does without its source--but not impossible. If anyone is interested, I made a [network capture]("http://sauer.endoftheinternet.org/qscapture.tar.gz") with Wireshark while attempting to run some of the program's features. It probably doesn't tell anything but anyone with more network knowledge can look at it. I did this in a non-admin account that does not have sudo privileges. The qs program asked for my password during the "Download updates" routine but I didn't bother typing anything in since it would be pointless to try, as my sandbox user doesn't have admin rights.

---

### Post by SuperSon!c on 2008-04-21
> **KiwiNZ said:**
> I posted this in th ethread in question 
 
"...If you dont want to answer a question multiple times over a period of time put up a FAQ , dont chastise members for asking a question they really need an answer for."
 
I stand by that and urge the Dev to put up a FAQ.
 
If members continue to be chastised for asking questions several times then the continuation of that thread would be reviewed.

a faq is a great idea and hopefully one the dev will consider.

---

### Post by the_darkside_986 on 2008-04-21
I keep getting weird ICMP's from random IP's regardless of whether or not I'm running QS so I guess QS itself is not doing anything on the network (except downloading a tarball in the Download update routine). I don't have torrents or anything running.

I noticed that when I entered my non-sudo-able password of the sandbox account, I get an error message like 
```


./QuickStart: line 2011: break: only meaningful in a `for', `while', or `until' loop

```

Not sure what that is all about but it might help the developer fix it.

---

### Post by Tomosaur on 2008-04-21
> **the_darkside_986 said:**
> I keep getting weird ICMP's from random IP's regardless of whether or not I'm running QS so I guess QS itself is not doing anything on the network (except downloading a tarball in the Download update routine). I don't have torrents or anything running.

I noticed that when I entered my non-sudo-able password of the sandbox account, I get an error message like 
```


./QuickStart: line 2011: break: only meaningful in a `for', `while', or `until' loop

```Not sure what that is all about but it might help the developer fix it.

It means he's got bad syntax in his code. It's usually only a warning for the developer, but it's worth fixing anyway.

---

### Post by Alasdair on 2008-04-21
I'm no expert on bash, but if this program really was using mailx for some nefarious purposes couldn't you just catch it red-handed by aliasing the mailx command with a program that logs its arguments to a file? Or wouldn't that work for some reason?

---

### Post by Tomosaur on 2008-04-21
> **Alasdair said:**
> I'm no expert on bash, but if this program really was using mailx for some nefarious purposes couldn't you just catch it red-handed by aliasing the mailx command with a program that logs its arguments to a file? Or wouldn't that work for some reason?

I don't think the actual program is written in Bash, it just uses Bash scripts for some purposes. The installer script is a bash script, for exaple.

---

### Post by smartboyathome on 2008-04-21
The program is in some kind of "bin" type format like a lot of proprietary program installers. I don't think it is using bash really, but external programs.

---

### Post by Alasdair on 2008-04-21
Assuming that quickstart just installs [_this_]("http://packages.ubuntu.com/hardy/mailx") package, I would guess that if quickstart does anything with mailx, it would just call it as an external program with whatever parameters it uses. Even if aliasing via bash wouldn't work you could possibly just replace /usr/bin/mailx with a different program (with the same name) that would log any arguments, and then possibly call the original mailx program with the supplied arguments - encase quickstart expects any output from mailx. I don't see any reason why that wouldn't work.

Judging from the author's comments in the quickstart thread, either he doesn't know how his program works, or he's not letting on the full truth. I'm not sure which is more worrying, given that users are trusting this program to handle sensitive and important data.

---

### Post by talsemgeest on 2008-04-21
I'm sorry, but I have to disagree with the lot of you. Quickstart is a brilliant and useful program. I have been using it for a while now with no adverse effects, and even though it is closed source the great usefullness of the program far outweigh the risks. I would certainly reccomend this program for anyone who has just done a clean reinstall, as this helps you get back on you feet a lot faster.

---

### Post by smartboyathome on 2008-04-21
I am looking into making an open source alternative to this program. Anyone else interested?

---

### Post by Google Spider on 2008-04-21
> **smartboyathome said:**
> I am looking into making an open source alternative to this program. Anyone else interested?

I'm not a programmer but yeah, looking forward to use it:)

---

### Post by ubuntu-freak on 2008-04-21
Not trying to blow my own trumpet here, but my [how-to](http://ubuntuforums.org/showthread.php?t=661833) is what I consider a "quick start". Wrote it for my own benifit, not just to help others. Doesn't take long to cut n' paste myself back to my perfect setup from a completely fresh install.
 
Long live the Terminal.
 
Nathan

---

### Post by K.Mandla on 2008-04-22
I've looked over both this and the other thread, and I'm not particularly enthused by this response to someone's contribution to the community. I don't see where it was ever proven to be malicious; in fact, it seems the author has withdrawn it over similar comments. To me that's a shame, since someone's efforts, for good or bad, were scuttled for no apparent reason.

If someone has something infinitely pressing that needs to be added to this thread, please contact a staff member and ask that it be reopened. Be prepared to make your case.

---

