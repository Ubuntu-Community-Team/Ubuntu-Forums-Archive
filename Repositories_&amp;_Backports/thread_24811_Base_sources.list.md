---
title: "Base sources.list"
date: 2005-04-08
forum: Repositories &amp; Backports
---

### Post by Technoviking on 2005-04-08
After testing hoary, I have change my sources.list alot. Can someone post the base sources.list including with Hoary final, so I can make sure I'm not missing any offical repos.

Thanks
Mike

ps here is mine
```

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

# GnomeBaker
#deb http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/i386/ ./

```

---

### Post by lao_V on 2005-04-08
You can find the repos [here]("http://www.ubuntuguide.org/#extrarepositories")

---

### Post by riffic on 2005-04-08
[QUOTE=lao_V]You can find the repos [here]("http://www.ubuntuguide.org/#extrarepositories")[/QUOTE]
you didn't answer his question..

I'm also looking for this, can someone just do a quick copy and paste of the default sources.lst ? 

thanks

---

### Post by Glanz on 2005-04-08
[QUOTE=riffic]you didn't answer his question..

I'm also looking for this, can someone just do a quick copy and paste of the default sources.lst ? 

thanks[/QUOTE]
 Here's what I am using and it works perfectly for me.... I don't know if it is the default though:
=================================================
# Ubuntu Hoary
deb [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") hoary main restricted
#deb-src [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") hoary main restricted

deb [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") hoary universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") hoary universe multiverse

deb [http://security.ubuntu.com/ubuntu/]("http://security.ubuntu.com/ubuntu/") hoary-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu/]("http://security.ubuntu.com/ubuntu/") hoary-security main 
restricted

## Uncomment after release to continue getting updates:
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary-updates main restricted

---

### Post by lao_V on 2005-04-09
[QUOTE=riffic]you didn't answer his question..

I'm also looking for this, can someone just do a quick copy and paste of the default sources.lst ? 

thanks[/QUOTE]

If you **[color=black]care to read[/color]** the [UbuntuGuide ]("http://www.ubuntuguide.org")you will notice that it lists the default repositories that come with the system and also the extra repositories!!!!

---

### Post by fede on 2005-04-16
Here is the default sources.list. My locale is Argentina, so just change the prefix for whichever your locale is (ie "us" instead of "ar" for USA). The only difference from the version in the Hoary Guide is the first line, as you can see. 

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://ar.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ar.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://ar.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

```

---

### Post by az on 2005-04-16
sudo apt-setup

Be lazy, it works.

---

### Post by Buffalo Soldier on 2005-04-16
```
# deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)]/ hoary main restricted

deb [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) hoary universe

deb [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
```

---

### Post by Psquared on 2005-04-17
[QUOTE=lao_V]If you **[color=black]care to read[/color]** the [UbuntuGuide ]("http://www.ubuntuguide.org")you will notice that it lists the default repositories that come with the system and also the extra repositories!!!![/QUOTE]

Look, I don't care how many cups of Ubuntu your handles shows or where you live, "baby" but that was rude.

Let me take this opportunity to say that I have seen more rudeness on this forum than any other Linux forum. Its not from everyone -- just a few, but it is consistent. If you don't want to politely interact on the forum then why be on here at all? 

The guy is obviously new - sure you gave him a link but why does that mean you couldn't post the information he asked for? 

The whole point of this forum is to try and be helpful - to everyone. Sometimes that means going out of your way. We all learn as we participate, and there is a gentle and polite way to deal with folks who don't want to do a search.

I can say for myself that I have done search after search and sometimes sorting through several threads and hundreds of posts can be grueling - it is a lot easier for someone to simply post the answer again.

Come Ubuntu people. We have a good thing here but I fear we risk turning people off by treating new people this way.

---

### Post by jonny on 2005-04-18
[QUOTE=Psquared]Look, I don't care how many cups of Ubuntu your handles shows or where you live, "baby" but that was rude.[/QUOTE]Agreed.  If you can't be polite, be silent.

---

### Post by az on 2005-04-18
My Goodness!


"Look, I don't care how many cups of Ubuntu your handles shows or where you live, "baby" but that was rude."

To be fair, the original answer was adequate, and the response to it was less than nice.  The information is all there and easily accessible.


"Let me take this opportunity to say that I have seen more rudeness on this forum than any other Linux forum. Its not from everyone -- just a few, but it is consistent. If you don't want to politely interact on the forum then why be on here at all?"

Please report such posts when you see them.  We will moderate them appropriately.  I can say that there is much less offensive language here than in most other forums.  People tend to be nice.  When they violate the code of conduct, they are asked to abide by them or leave.


"The guy is obviously new - sure you gave him a link but why does that mean you couldn't post the information he asked for? 

The whole point of this forum is to try and be helpful - to everyone. Sometimes that means going out of your way. We all learn as we participate, and there is a gentle and polite way to deal with folks who don't want to do a search."

There is a lot of traffic so it becaomes difficult to be very detailed.  Sometimes, it is better to be shown the road to the answer as opposed to the actual answer.  In this case, the answer was right there.  I think it is unfair to complain about this.  


"Come Ubuntu people. We have a good thing here but I fear we risk turning people off by treating new people this way."

I agree that we have a good thing here.  Your contributions to the forms are appreciated.

Ubuntu attracts different users than the traditional linux distributions.  They tend to have high excpectations.  If the users of ubuntuforums have equality high excpectations, that it great!

I agree that it is difficult for the typical linux guru to reccommend the more freindly (GUI) solutions to problems when the comman line option can be so easy.  That may lead to some short answers to questions and may be taken as rude.
this is not the case here, though, but is that what you refer to in saying that people being rude?

---

### Post by dataw0lf on 2005-04-18
[QUOTE=Psquared]
Let me take this opportunity to say that I have seen more rudeness on this forum than any other Linux forum. Its not from everyone -- just a few, but it is consistent. If you don't want to politely interact on the forum then why be on here at all? 
[/QUOTE]


Wow.  What Linux forums have you been a part of?  I think that the Ubuntu Forums is exactly the opposite, personally.  Most everybody here (except for a very small minority, much smaller than other, similar, communities) is very polite, in my opinion.   If you've had problems with people in the past, please bring it to the moderator's attention, by reporting posts, and private messaging.  We will certainly look into any rude posts you point out.

---

### Post by Psquared on 2005-04-18
Linuxforums.org and fedoraforums.org are friendly. Very few unanswered posts and people don't mind answering the same questions over and over. 

Searching for the precise answer on this forum is laborious. Every now and then I get lucky, but most of the time the answer is either not detailed enough or is to a slightly different question.

I have to disagree about this particular post. It is rude, at least in these parts, if someone asks for directions, to hand them a map and say "here." Helpful is helpful and rude is rude. Maybe rude is a poor choice of words. Curt, short, abrupt and using bold to point out somebody's mistake is not being helpful. Is it rude? Well, I think it is.

---

### Post by riffic on 2005-04-18
[QUOTE=azz]My Goodness!


"Look, I don't care how many cups of Ubuntu your handles shows or where you live, "baby" but that was rude."

To be fair, the original answer was adequate, and the response to it was less than nice.  The information is all there and easily accessible.
[/quote]
I apologize if my response seemed less than nice, but the ubuntu guide did not have the text of the default sources.list file. It was what the original poster had asked for, and it was not what the replier provided.
> 
There is a lot of traffic so it becaomes difficult to be very detailed.  Sometimes, it is better to be shown the road to the answer as opposed to the actual answer.  In this case, the answer was right there.  I think it is unfair to complain about this.  
 While I generally agree, the answer provided was not what the OP asked for and could have been easily answered, as shown by others.

not trying to mod sass or anything, these forums are wonderful and I appreciate anyone who helps others out of their own free time. I just wanted to clarify what might be seen as rudeness.

---

### Post by Glanz on 2005-04-18
If I remember correctly, a user needed an example of a sources.list right away and asked for an example list to be posted.He did not ask for a map,or a lecture on how to read manuals or documentation. I am sure he will get to studying documentation later, once he gets a base, workable system up. He may even learn enough from that documentation to help other users directly with a short reply without telling to go home and study more. In any case, some info is just so essential that taking the time to give it directly from one's own system is less trouble than referring someone to docs.
Either way, two things were accomplished: the user got several good examples of sources lists, and he got referral to good documentation.

---

### Post by TravisNewman on 2005-04-18
I'm closing this thread before it gets out of hand.

Conflicts should not be resolved like this-- this is just causing a war. Any problems that you have with users should be taken up with the moderators, and we'll decide on a plan of action. Just click on the button to report the post-- it's the yellow caution sign with the exclamation point in it. Hashing things out like this is obviously not working, and it's conversations like these that lead to unfriendly forums.

---

