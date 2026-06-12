---
title: "A worm in Ubuntu"
date: 2007-05-13
forum: The Cafe
---

### Post by slimdog360 on 2007-05-13
Something I wanted to bring to the attention of the masses [http://ubuntuforums.org/showthread.php?p=2645036#post2645036]("http://ubuntuforums.org/showthread.php?p=2645036#post2645036")

Barney here says that he had/has a worm on his dapper install and to me, from the sounds of it, I wouldn't disagree. Read the post for yourselves and tell me what you think.
For those who don't want to read it I'll give the summary
-bad email
-bad link from within email
-downloads (or partially downloads) a .bin file
-thunderbird dead

there was no root user involved so this could explain the isolation to thunderbird.

---

### Post by argie on 2007-05-13
Interesting. But I thought one of the protections was that one must explicitly chmod any downloaded file to executable before running it. How did it come with that permission already given?

Like:
Download file.bin
chmod +x file.bin

is what I mean.

---

### Post by samjh on 2007-05-13
The bin file might have been a dummy payload to divert attention to whatever was really causing the problem.

---

### Post by riven0 on 2007-05-13
Good point, argie. 
And I want to wwwfriendgreetings.com and nothing weird happened... so far:) . It's possible Barney's problem is not related to that email at all; it just appeared when he clicked on the link to open a new browser window. I'm not an expert on this, though, so I don't know.

---

### Post by jiminycricket on 2007-05-13
some unknown vuln in thunderbird or firefox?

---

### Post by jfinkels on 2007-05-13
I blame Bill Gates.

---

### Post by samjh on 2007-05-13
Quite likely that the problem was with the email.  He said "postcard", so I wonder if it was either a normal email, or something with embedded content.

Perhaps the downloaded bin file contained code that was a payload to exploit buffer overflows in Thunderbird or Firefox?  Who knows.

---

### Post by slimdog360 on 2007-05-13
> **riven0 said:**
> Good point, argie. 
And I want to wwwfriendgreetings.com and nothing weird happened... so far:) . It's possible Barney's problem is not related to that email at all; it just appeared when he clicked on the link to open a new browser window. I'm not an expert on this, though, so I don't know.

thats cause I left out the '.' after the www

also if you go to the trendmicro site that I gave you'll see that there is more to the url

---

### Post by heimo on 2007-05-13
It's easy to misdiagnose this kind of problems. If it's a real exploit using vulnerability in thunderbird, it's important to 1) diagnose the problem properly, 2) bring this to attention of thunderbird developers. And I'd like to add 3) not make too fast conclusions without investigating properly and 4) not spreading baseless FUD. I've seen GNU/Linux operating systems rooted and do know that security problems exist, not trying to deny that - but please, base your conclusions on facts and not quick conclusions. Capture network traffic, isolate the binaries, dissect, reverse-engineer, debug, report, fix and patch.

:)

---

### Post by riven0 on 2007-05-13
> **slimdog360 said:**
> thats cause I left out the '.' after the www

also if you go to the trendmicro site that I gave you'll see that there is more to the url

No, I put in the . after www. I just took it out in case someone clicked on it and something is hidden there. Although, everything is still working perfectly on my side.


I'm gonna check out the real link on trendmicro now...

---

### Post by heimo on 2007-05-13
> **slimdog360 said:**
> thats cause I left out the '.' after the www

also if you go to the trendmicro site that I gave you'll see that there is more to the url

On trendmicro page about worm.friendgrt.b I can't see anything about it running on Linux based operating systems or using Thunderbird vulnerability. What's your theory?

---

### Post by riven0 on 2007-05-13
Hey! Trendmicro blocked out part of the url! :mad: I wanted to see the page!

Anyway, it can't possibly be a Linux worm. Look at the [technical details]("http://www.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=WORM%5FFRIENDGRT%2EB&VSect=T") on Trendmicro's site. It asks the user to download a program; an .exe program. Not a Linux problem.

---

### Post by slimdog360 on 2007-05-13
> **heimo said:**
> On trendmicro page about worm.friendgrt.b I can't see anything about it running on Linux based operating systems or using Thunderbird vulnerability. What's your theory?
you will notice that I said it probably wasn't a Thunderbird problem. That trendmicro site was only one possibility as to what it could have been.
My theory, 
- it was a .bin file
- it (might) have been a worm, something which doesn't generally discriminate between operating systems
- the email was obviously dodgy
- Thunderbird was left screwed

hence there most probably was something wrong with that email, or the site, or something else. Of course Thunderbird could have just been corrupted making it a coincidence. This is why I asked the opinion of others.

---

### Post by macogw on 2007-05-13
He said he cancelled the download of the .bin.  If it didn't run, it couldn't have done anything.

I don't use mail clients (what's so hard about gmail.com? and then you don't even waste hard drive space) so I don't know if an email can affect the client, but you should *always* set your email to receive text only (no HTML).  You can be sure nothing's executing from the email then.  Do that even if it's just to cut down on repeat spammers.  They embed tranparent gifs and see if you load it.  If you do, they know you read spam, so they send you more, so just don't even let the images load by disabling HTML and you'll get less spam ;)

And no, you don't have to chmod +x everything.  If it was made executable before being uploaded, it would keep that setting.

---

### Post by heimo on 2007-05-13
>  Barney here says that he had/has a worm on his dapper install and to me, from the sounds of it, I wouldn't disagree.

...

> 
- it was a .bin file
- it (might) have been a worm, something which doesn't generally discriminate between operating systems
- the email was obviously dodgy
- Thunderbird was left screwed

Obviously something screwed thunderbird, and it'd be important to document what happened and report this, so that what-ever the bug is (if it's a bug) it will get fixed.

---

### Post by Barney on 2007-05-26
The "worm" has returned after 2 1/2 weeks, and replaces every inbound email message with either a message that I sent to my nephew on 1/14/2006 (which I cannot locate anywhere) or an old valid message from jacquielawson,com (cards).

ClamAv finds nothing; nor can I find any mysterious "program" files in my mail storage this time as I did before.

This thing acts like a WIndows worm.

Any help to eradicate will be much appreciated.

---

### Post by Barney on 2007-05-26
Why am I beginning to feel like the red-headed stepchild here, or even worse the mind-cripple who's kept in secret in the attic, so no one will know that there is any debility in the family?

Thirteen hours and no help from these Ubuntu forums is quite unusual, even though I fessed up to probably having brought this problem on myself...........maybe to test our invulnerability to such malcreant attacks; one might reasonably expect that our community would want to deal successfully with "worms," if that is what has befallen my Dapper installation.

My initial post is at:  [http://ubuntuforums.org/showthread.php?t=440387](http://ubuntuforums.org/showthread.php?t=440387).

Since posting last, I have deleted my profile in Thunderbird and created a new one, but the problem persists.

---

### Post by FuturePilot on 2007-05-26
Maybe try recreating the problem on the live CD and see what happens. If you do everything the same and it starts happening then it could be a worm.

---

### Post by hanzomon4 on 2007-05-27
What sucks in linux is that there are almost no tools you can use to know whether or not it's a virus/worm whatever. I have clamav scan all of my emails but... it doesn't give me much peace of mind because I really don't understand it.

---

### Post by slimdog360 on 2007-05-27
maybe get remove thunderbird and reinstall it? If that doesn't work maybe installing it via the official package from the mozilla site rather then the repos.

---

### Post by riven0 on 2007-05-27
> **Barney said:**
> Why am I beginning to feel like the red-headed stepchild here, or even worse the mind-cripple who's kept in secret in the attic, so no one will know that there is any debility in the family?

Thirteen hours and no help from these Ubuntu forums is quite unusual, even though I fessed up to probably having brought this problem on myself...........maybe to test our invulnerability to such malcreant attacks; one might reasonably expect that our community would want to deal successfully with "worms," if that is what has befallen my Dapper installation.

It's not that everyone is ignoring you on purpose, Barney. It's just that most Ubuntu users have never come across something like this, so everyone is at a loss of what to do. I agree with whoever said to try to recreate the problem through LiveCD. That way you can pinpoint it down to being a worm or not and maybe get to the heart of the problem here.

---

### Post by DoktorSeven on 2007-05-27
I'm curious about this message; I'd want to see the actual mail message source to see if there is anything odd inside it that might trigger some sort of vulnerability.

---

### Post by ButteBlues on 2007-05-27
If you can, for now, move "~/.mozilla-thunderbird"  to another location and then start up thunderbird and re-add your email account.

---

### Post by tgbrowning on 2007-05-27
I came into this thread late, but I'm curious about one thing. 

This "greeting card" URL thing. 

At the present time I'm not up and running Ubuntu (just getting started) but I do definitely recall getting an email a day or two ago that was some screwy "card" from an unidentified friend. 

I read the text body (my mail is set for plain text only - no HTM) figured it was some sort of malware/worm/virus/whatever and deleted it. I wonder if it was the same bloody thing.

Browning>>>

---

### Post by Barney on 2007-05-27
This morning, I completely removed (via Synaptic) Thunderbird 1.5; downloaded and installed Thunderbird 2.0.   I'm running Dapper, always kept up to date.

My mail has been stored in Documents/Email/T-Bird/Barney.  

The same problem still exists!!  ...therefore, the "worm" (as yet unidentified) *may* reside in my mail storage; or may not, and may have taken up residence someplace else.

---

### Post by Barney on 2007-05-27
I again uninstalled everything T-Bird; and re-installed T-Bird 2.0.

I did not select my normal mail storage, and used the standard profile storage in /home/barney.

I tried several test messages, and all were delivered as sent.  I, again, suspect that there may be something in my mail storage, different from standard profile storage, (WAG) that is corrupting things.  I will review all mail stored there for anything other than .txt files before transferring storage to that location.

It is strange that one of two email address in the original T-Bird 1.5 was unaffected by this problem, while my main address was.

As I have no more hair to pull out, I must goto my therapist (see icon) to clear my thoughts.

Any help to find this goober - much appreciated.

---

### Post by Barney on 2007-05-27
Early this evening, I tried several more email test messages to the standard T-Bird profile and all went well.

I then switched my mail storage to the one that I have been using for months in Documents.  Ka-POW!  The incoming messages were all corrupted with the same type bogus messages as earlier reported.  There were no suspicious files in my mail storage folder.  I then deleted my inbox .msf file and tried again.  All was normal for three messages and then BAM right back to corrupting all incoming mail.  Sometimes worms take up residence in address books.  I did  not import my address book. so it wasn't there.

I used file manager to rename my old inbox "sinbox" thinking that there was something in the inbox corrupting itself.  T-Bird created a new inbox and inbox.msf and everything was fine for a couple emails and then all incoming messages were corrupted again.  So, it's not in my stored mails, it's not in my address book as I have none, but something, somewhere continues to corrupt my incoming messages.

I am not a computer geek, however, this now resembles everything I've ever heard about a "worm" taking up residence in some unknown corner of the file structure, and continuing to cause havoc.

---

### Post by Barney on 2007-05-27
Boy, do I ever feel dumb, no, stupid!!

Help from the Mozillazine forums provided the answer - my folders needed compacting!!

Daifne
Moderator
Joined: 31 Jul 2005
Where the Waters Meet, Wisconsin 	New postPosted: 27 May 2007 08:30 pm     
How recently have you compacted your folders? Compacting is something that needs to be done regularly in any email program and finalizes the delete process. We recommend weekly, but many of us do it daily. When done often enough, it can be an extremely fast process. Not doing so can lead to problems like those you are experiencing. See this about how to and why it's so important: [http://kb.mozillazine.org/Compacting_folders](http://kb.mozillazine.org/Compacting_folders)

To avoid this happening again, see the tips in these articles:
[http://kb.mozillazine.org/Keep_it_working_%28Thunderbird%29](http://kb.mozillazine.org/Keep_it_working_%28Thunderbird%29)
[http://kb.mozillazine.org/Performance_%28Thunderbird%29](http://kb.mozillazine.org/Performance_%28Thunderbird%29)

I expressed my thanks to Daifne; and regret that I have thrown up a RED FLAG herein that could have been avoided.  However, I'd rather feel like a dumb ****, than to have had a real worm invasion.

Best to all who tried to help,
Barney

---

