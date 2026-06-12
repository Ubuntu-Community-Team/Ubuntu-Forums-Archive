---
title: "Sending email through command line/PHP"
date: 2005-08-30
forum: Server Platforms
---

### Post by dudinatrix on 2005-08-30
I have my system set up as a local web development server.  Apache2, PHP, MySQL.  One of my PHP pages for my site sends an email using the "mail" command.  It works fine (sends emails) when I upload it to our live, offsite server, but I can't test it on the development system (mail only works locally).

Do I have to set up a full mail server on my development system to be able to send mail externally this way, or is there a faster approach?

---

### Post by lao_V on 2005-09-08
To the best of my knowledge PHP's mail function uses sendmail to actually send it. In Ubuntu, you have posftix which comes with sendmail wrapper. So, as long as you have postfix working correctly you should be able to send emails. There might be a logfile in /var/log (mail.log?) which I believe you could check for any errors.

---

### Post by robert_pectol on 2005-09-08
Here's what I do.  First, I create an SSH tunnel to my remote SMTP server and forward local port 1225 to my remote SMTP server's port 25, through the tunnel.  Then, I specify a relay host within my Postfix config file that causes Postfix to use localhost's port 1225 for mail delivery like this:

relayhost = 127.0.0.1:1225  (located in my /etc/postfix/main.cf config file)

With things configured this way, Postfix delivers all mail for which it is NOT the final destination, to localhost on port 1225, which in turn, traverses the SSH tunnel to to the remote SMTP server to be forwarded to it's final destination!  As far as your local Postfix process is concerned, it merely delivers to another local SMTP server on 1225!  Sounds a little complicated but it's actually fairly easy to impliment.  An added advantage to doing it this way is that you don't need to adjust or lower any security settings on your remote SMTP server since mail arriving over the SSH tunnel will appear to be coming from it's own localhost (which is allowed by default)!

It is a little tricky to get up and running but once in place, it works like a charm (or at least it has for me thus far)!  In order to automate things, I wrote an SSH tunneling script that gets started on bootup.  If you are interested in my script, let me know.  I'd be glad to share it with you.

---

### Post by relix42 on 2005-09-08
[QUOTE=dudinatrix]Do I have to set up a full mail server on my development system to be able to send mail externally this way, or is there a faster approach?[/QUOTE]

Install the nullmailer package.  No messy MTA of any kind required.  It just hands off mails to a specified SMTP server(s) and let's them handle it.  I've done this will all my live and development servers - I don't want to have the muck of any MTA laying around if I don't need it.

---

### Post by LordHunter317 on 2005-09-08
robert_pectol's solution is entirely silly and excessive unless for some reason you cannot contact the remote SMTP server directly over port 25.

---

### Post by robert_pectol on 2005-09-09
[QUOTE=LordHunter317]robert_pectol's solution is entirely silly and excessive unless for some reason you cannot contact the remote SMTP server directly over port 25.[/QUOTE]

Ever heard of the term, "open relay?"

LordHunter317's post (along with about 95% of all his other posts) is condecending, narrow minded, and somewhat belligerent!  Why does he make it a point to go around the forums making shitty comments like that?  Just because he does things a little differently than someone else does NOT mean that he is right and they are wrong!!!  Normally I'd just let it go but I, along with many others, am getting sick of his pompus downtalk!

---

### Post by lao_V on 2005-09-09
[QUOTE=LordHunter317]robert_pectol's solution is entirely silly and excessive unless for some reason you cannot contact the remote SMTP server directly over port 25.[/QUOTE]

I have reported this as a bad post to the mods. The community doesn't need this kind of post IMHO. If you disagree with other peoples solution then I'm sure there are more polite ways of conveying it.

---

### Post by LordHunter317 on 2005-09-09
[QUOTE=robert_pectol]Ever heard of the term, "open relay?"[/quote]Modern day mailservers can be setup to only allow relaying from fixed hosts, to fixed places, and by fixed users (or any combination thereof you desire).

I've done it.  Many times.

> LordHunter317's post (along with about 95% of all his other posts) is condecending,No, you're making an assumption that's not there.  The post isn't intended to be that way, but you're assuming because I'm pointing out your solution is excessive, that it must be.

> narrow minded,Nope.  Just because I haven't go into a multi-page response doesn't mean I haven't thought  the solution through.  Clearly my response to your "open relay" remark shows I did think the situation through before, with at least a resonable degree of throughness.

Your response however, demonstrates prejudment and narrow-mindedness.  You're assuming simply because I pointed out your solution was not perfect, I must assume you're wrong, stupid, and look down upon you.  None of those things are true.

No one knows everything (including myself) and I'm well aware of that.  I have no problem even helping the greenest of Linux users, provided they pay attention, and they're willing to learn for themselves.  Short of those two requirements, I pretty much have no end to how much I'm willing to help and the time investment I make helping people at *all* skill levels is simply huge.

And believe it or not, I'm not (generally) condescending to them, unless they violate rule 1 or 2 above, or they assume just because I tell them they're doing some wrong/badly/suboptimally/whatever that I have some sort of personal vendetta to grind against them and a zeal to convert everyone to the one true LH317 way.

Admittedly, it's understandable that people do that, becuase emotions are hard to convey on the Internet and especially hard on message boards (there is some emotional feedback with real time communications that just isn't present here).

Nevertheless, assuming that because I say, "don't do this," or, "this can be done better," and don't explain why it is, that I'm being condenscending.  The simply reality may be I just don't have the free time to elucidate about all the details.  If you had responded, "Why is my solution inefficent," instead of, "LH317 is a jerk," I would have been happy to give this post (minus this long tirade) when I had the time to do so.

And the reality is on this forum anyway, when I'm curt like that, it's quite likely because I lack the time to see all the threads I want to see, and reply to them.

> and somewhat belligerent!Nope.  You need to look up the definition of the word.

>  Why does he make it a point to go around the forums making shitty comments like that?Because your solution is overkill for most situations, and a simpler solution would better serve most people?

>  Just because he does things a little differently than someone else does NOT mean that he is right and they are wrong!!!Funny, but it's not a simple right or wrong thing: the issue is how optimal and easy to implement your solution is.  Your solution is more difficult to implement than simply configuring your mailer properly. in **most** (but not all) cases, especially when you have control over both ends (which your's requires, in part).

OTOH, if you cannot control both ends, or there's other factors involved (the clients are behind a NAT with untrusted as well as trusted clients), or the data is sensitive,  then your solution may be a very valid one.
But neither of those are the general case.

> am getting sick of his pompus downtalk!The only downtalk here is the kind you're assuming.  What else would have me say?  Your solution is too complicated for the general case.  That's a fact.  No matter how I dress it up, that's the reality of the matter.  So how would have me say it differently?

[quote=Iao_V]If you disagree with other peoples solution then I'm sure there are more polite ways of conveying it.[/quote]Not really.  No matter how you dress it up, I'm still saying, "You're doing something less than the best way,"  Every time I've asked someone to say, show me how to be more polite, they've been unable to do so.  So what?  Would you just have me ignore his solution?

---

### Post by robert_pectol on 2005-09-09
I don't care how right you THINK you are... You sir, lack the social skills to convey your opinions, without coming off offensive and, "better than thou!"  It's obvious to anyone who reads this thread.  WHY CAN'T YOU SEE IT?

---

### Post by LordHunter317 on 2005-09-09
[QUOTE=robert_pectol] WHY CAN'T YOU SEE IT?[/QUOTE]Why I can't is irrelvant. Instead of trying to troll me, you could show me a better way...

In fact, I even asked Iao_V to do so, and the invitation is also open to you, or anyone else.  How would you have had me phrased my post?

---

### Post by robert_pectol on 2005-09-09
You could start by leaving out phrases such as, "entirely silly."  How do you think that makes the person feel when they see you refer to their post with words like that?  If you are entirely honest with yourself, you'll have to agree that your choice of words is meant to be condecending!  Whether or not you think the solution presented is, "entirely silly", a cordial, gracious, and polite post would not have been what you posted!  Argue it 'til you're blue in the face but you know I speak the truth!

---

### Post by LordHunter317 on 2005-09-09
[QUOTE=robert_pectol]You could start by leaving out phrases such as, "entirely silly."[/quote]Perhaps.   

>  How do you think that makes the person feel when they see you refer to their post with words like that?I honsetly have no clue, as I don't percieve calling something silly as necessarily negative, and when I do, it's not being harshly so.

If I really wanted to trash your solution, there would be no question about in my wording.
 
>  If you are entirely honest with yourself, you'll have to agree that your choice of words is meant to be condecending!No, I really don't.  You can't assume that from my wording.  I'm entirely unaware of the fact that someone would find that offensive, because I call stuff "silly" all the time.  It doesn't even conciously enter my mind that it has a strong negative connotation, because I don't always use it that way.  And even when I do, as I said above, I don't use to have a **strong** negative connotation.

> a cordial, gracious, and polite post would not have been what you posted! I never argued that, in fact, I think I agreed, but you haven't really been much help in correcting my behavior.  One suggestion isn't enough, I think.

> Argue it 'til you're blue in the face but you know I speak the truth!
You might, but you haven't show me a **better way**, so what you say really doesn't matter one bit.  One suggestion isn't obviously going to fix things if I'm intentionally being condescending and belligerent, am I?

And thus, we're right back we're we started... these kinds of issues aren't as easy to resolve as one would think.  

And if that's really what you took offense at, instead of ranting, why didn't you just say, 'I didn't like it that you called my solution silly'?  I would have apolgozied to you on the spot.

Ranting the way you did just puts me on the defensive.  You didn't even initially try to make peace over what upset you, so are you really shocked by the replies you got back?

Seriously.  Even if you're right about my conduct (and you are, at least in part), your conduct was far from perfect here as well.  Believe it or not, I'm actually a pretty amiciable guy, and I don't generally like to offend people, though I don't care and am usually completely and totally unaware if I do so by accident.  However, if you say, "that offends me," 99/100 times I will apologize for it, and make a serious attempt at not doing it again.

---

### Post by robert_pectol on 2005-09-09
> 
You might, but you haven't show me a better way, so what you say really doesn't matter one bit. One suggestion isn't obviously going to fix things if I'm intentionally being condescending and belligerent, am I?

There you go again!  This is pointless!

> 
Ranting the way you did just puts me on the defensive. You didn't even initially try to make peace over what upset you, so are you really shocked by the replies you got back?

Perhaps I let my emotions influence my response to your initial post, a little too much!  But I stand by everything I've said relative to your condecending tone.

> 
I'm actually a pretty amiciable guy, and I don't generally like to offend people, though I don't care and am usually completely and totally unaware if I do so by accident. However, if you say, "that offends me," 99/100 times I will apologize for it, and make a serious attempt at not doing it again.

An amicable person **does care** if they offend people!  Otherwise they are ungenuine and considered two-faced by most!  Maybe you're ok with that.

Look, we obviously have distinctly different philosophies.  That's ok.  However, you should know that even though you claim you don't mean to come off offensive ,the way you do in your posts, there are those of us who have been offended by them.  Whether or not you care is up to you, but at least you know.  Also, I apologize for being sharp with you.

To dudinatrix,  I apologize for this thread going so far off topic!  I hope you found a solution to your query.

---

### Post by LordHunter317 on 2005-09-09
[QUOTE=robert_pectol]
There you go again! This is pointless![/quote]What was offensive about that?  Really, you may not like it, but just saying, "You're behaving rudely," **is not enough**.  I've repeated that in different ways three times now, please don't make me repeat it again.

---

### Post by robert_pectol on 2005-09-09
I'm finished here!  Good day to you, Sir!

---

