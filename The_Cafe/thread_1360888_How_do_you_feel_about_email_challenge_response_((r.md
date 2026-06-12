---
title: "How do you feel about email challenge response ((re)captcha)"
date: 2009-12-21
forum: The Cafe
---

### Post by hwttdz on 2009-12-21
I think many people agree that spam mail it out of hand.  And I believe it actually incurs pretty significant server costs.  Anyways, I was just wondering how you feel about using some sort of challenge response authentication? i.e. if someone you haven't corresponded with in the past sends you a message you don't receive the message until they complete some sort of simple question, essentially to prove they're not a spammer.

I'd be a bit worried here that people would find it annoying, as you're essentially asking them to eat the "cost" of sending you a message.  Whereas before it  was paid by your act of filtering your real mail from your spam.  

Anyways I think my ideal email setup would be to whitelist a few domains (probably all .edu, and possibly gmail) then submit all other addresses to a challenge system.  Then I'd manually whitelist any newsletters.

I'm just curious to know what you think of this?  And I do realize that something very similar to what I've described it probably possible using open source software immediately, but I don't have quite the motivation to set it up at the moment.

---

### Post by t0p on 2009-12-21
I don't have any great feelings either way about Captcha.  Speaking generally.  But if I get bugged with it too often, I get a bit impatient.  Then it would all depend on how badly I wanted to write to you.  Sometimes, when I lose my patience, I also lose a little of my capacity for rational thinking.  Then there's no saying what I might or might not do.

---

### Post by Skripka on 2009-12-21
Captcha needs to die quickly.

---

### Post by doas777 on 2009-12-21
I'd say you would have to have a really good reason to go that far. I have almost no spam issue, just from good identity management. I can't think of the last time I got an email from someone I don't know.

---

### Post by hwttdz on 2009-12-21
Skripka, why the violent response?

Also realize that if I whitelisted the top three domains only a small fraction of the mail would be subjected to this verification.

I'd be happy to do this, as it would only cost me an extra 30 seconds to write a new person, and it already takes at least that to add them to an address book.

---

### Post by aysiu on 2009-12-21
I liked captcha in the beginning, but now it's so ridiculous that I often cannot read what I'm supposed to type. I know it's supposed to be difficult for bots to figure out, but it should still be human-readable.

---

### Post by Skripka on 2009-12-21
> **hwttdz said:**
> Skripka, why the violent response?

Also realize that if I whitelisted the top three domains only a small fraction of the mail would be subjected to this verification.

I'd be happy to do this, as it would only cost me an extra 30 seconds to write a new person, and it already takes at least that to add them to an address book.

The infliction of Captcha upon the masses probably needs investigated by the court in The Hague as a crime against humanity.

All Captchas do is prevent EVERYONE, man or machine, from  getting  to their desired data.  In order to make them at all effective against bots, Captchas have to be basically unreadable 90% of the time to human beings.

Whoever invented Captchas should shoot themselves before they reproduce.

---

### Post by hwttdz on 2009-12-21
Well, if your complaint is just with captcha, then there are other alternatives.  Such as being presented with 3 sets of 5 photos and being told to select the radio button for the kitten in each set.  Something that's trivially easy, yet a computer won't get right.

---

### Post by lisati on 2009-12-21
I used to use challenge/response based spam filtering but abandoned it.For a number of reasons it required more amount of work on my part to keep it working properly. And there's always the possibility of being reported as a spammer when it sends out a challenge in response to an email with spoofed "from" addresses that belong to some innocent third party.

---

### Post by Grenage on 2009-12-21
I hate captchas; I really, really do.  What e-mail needs is a revised protocol, not hacked measures that just tick people odd.  It's bad enough on sites (some to the point where I just no longer use them), I would probably use e-mail a lot less.

---

### Post by hwttdz on 2009-12-21
Skripka, I contest your claim that captcha's prevent everyone from accessing data, and the fact that there are a whole bunch of gmail and yahoo addresses registered seems to support my point of view that they're not impossible.  

Not to get too far off topic, but the goal is to find a problem which is simple for a human but difficult for a computer.  The cat/dog recognition problem, linked to a pet adoption page, such that no image is used twice?

lisati, that's a good concern.  I wish gmail gave finer control over filtering, such as checking if the sender and from tags matched.

---

### Post by hwttdz on 2009-12-21
Grenage, what do you mean/suggest by a revised protocol?  And remember under the scenario I propose you'd only need to solve one per address you correspond with, and these folks would be auto whitelisted if you send them a message.  So assuming 1/2 of the people in my address book contacted me first, I'd have had to complete 30 or so over the last few months call it 30 challenges*30 seconds/100 days = 9 seconds a day.  The question is, is that more or less than what the average person spends dealing with spam, my claim would be that it is.

---

### Post by LowSky on 2009-12-21
My favorite is click-your-password-keyboad and photo id websites. 
For email, the provider of the addresses should have better checks in place so that spammers cannot get an address so easily. Most of them use free accounts form yahoo or hotmail. If signing up is harder to do then less spam would occur.

---

### Post by hwttdz on 2009-12-21
What do you mean by "My favorite is click-your-password-keyboad and photo id websites."?

---

### Post by Grenage on 2009-12-21
I can see what you are proposing, but a lot of us are constantly dealing with different people, rather than the same individuals or companies.  Regarding the protocol; I really feel that we're still using a very old protocol that was never designed to put up with the misuse it currently gets.

I also imagine that the reason we've stuck with it for so long, is that it would cost a fortune and inconvenience a lot of people during the transition.  Still, it's tricky to come up with a solution that's both easy to use but isn't a centrally/de-centrally managed system.

---

### Post by Mornedhel on 2009-12-21
> **doas777 said:**
> I'd say you would have to have a really good reason to go that far. I have almost no spam issue, just from good identity management. I can't think of the last time I got an email from someone I don't know.

I managed that until my father gave my uni-provided email address to a lottery that (promised to) raise his winning chances for each address he gave.

The lottery was legit (obviously we didn't win anything anyway) but they also gave out the addresses collected. Long story short, that address is now 80% spam. The uni's spam filter marks spam in the mail subject, but still.

Oh, and chain letters are really annoying too. Just as an experiment, last time I got one, I wrote a short Perl script to count all unique email addresses in the various levels of forwarding, and I got over two hundred. Of those, only ten or so were from people I knew, the rest were contacts of contacts and contacts of contacts of contacts.

---

### Post by Skripka on 2009-12-21
> **hwttdz said:**
> Skripka, I contest your claim that captcha's prevent everyone from accessing data, and the fact that there are a whole bunch of gmail and yahoo addresses registered seems to support my point of view that they're not impossible.  

My point is that they slow you down, often substantially, from getting where and what you want.  The last time I had to deal with Captchas, it took 5 times refreshing the image before I got anything remotely readable.

[QUOTE=]
Not to get too far off topic, but the goal is to find a problem which is simple for a human but difficult for a computer.  The cat/dog recognition problem, linked to a pet adoption page, such that no image is used twice?
[/QUOTE]

This is the kind of thing Google Image Search does every minute, of every day of the week.  It ain't that hard....and if it is sufficiently problematic for a computer/bot--a human wouldn't be able to tell either.

---

### Post by Mornedhel on 2009-12-21
> **Skripka said:**
> This is the kind of thing Google Image Search does every minute, of every day of the week.  It ain't that hard....and if it is sufficiently problematic for a computer/bot--a human wouldn't be able to tell either.

Since when can Google Image associate any image to the concepts being represented ?

The human brain is better at this than any modern algorithm, by several orders of magnitude. A computer can do it, but it won't be any good at it. Shape recognition algorithms exist, but they have trouble recognizing potatoes from eggs -- something most humans can do effortlessly.

---

### Post by hwttdz on 2009-12-21
> **Mornedhel said:**
> Since when can Google Image associate any image to the concepts being represented ?

The human brain is better at this than any modern algorithm, by several orders of magnitude. A computer can do it, but it won't be any good at it. Shape recognition algorithms exist, but they have trouble recognizing potatoes from eggs -- something most human can do effortlessly.

Yes, I think mornedhel is correct and that google image search employs the alt text of an image and other information on the page to label the image.  They of course also employ the image labeller, which recruits humans to do the labelling.  

Grenage, I'm still curious what you propose in a new protocol? 

True that if you are perpetually dealing with an entirely new set of people this solution is not for you.  If you're like me and almost everyone you deal with uses an edu address (and hence could be whitelisted in one fell swoop) it would be rare that it would ever come up.

---

### Post by Sporkman on 2009-12-21
[IMG]http://sporkforge.com/slush/captchx3Old7.png[/IMG]

---

### Post by NoaHall on 2009-12-21
> **Sporkman said:**
> [IMG]http://sporkforge.com/slush/captchx3Old7.png[/IMG]
 
It said "Frogs", right?

---

### Post by Skripka on 2009-12-21
> **NoaHall said:**
> It said "Frogs", right?

You got the old style down...ho about the new ones?

[IMG]http://3.media.tumblr.com/tumblr_krrydlcbrU1qa0hfzo1_400.jpg[/IMG]

---

### Post by NoaHall on 2009-12-21
> **Skripka said:**
> You got the old style down...ho about the new ones?

[IMG]http://3.media.tumblr.com/tumblr_krrydlcbrU1qa0hfzo1_400.jpg[/IMG]

Does it say "2798075"?

---

### Post by Frak on 2009-12-21
Captcha is flawed. Many get to a point where they are impossible to read (looking at you, CSS-Tricks). The ideal method would be to use something that could only be solved using human thought, like "Drag the yellow fruit to the box", with five icons being a wrench, banana, apple, computer, and CD. With varying (randomly generated) id's, no captcha cracker could solve them. They can only be interpreted through human thought. It would also be simple (wouldn't work for those without JS though, which is a very small number).

That doesn't solve the captcha mill problem, but it solves the bot-solvers problem.

---

### Post by lisati on 2009-12-21
> **NoaHall said:**
> Does it say "2798075"?

I thought it was "Ubuntu Rocks"

---

### Post by hwttdz on 2009-12-21
Skripka, it appears that you just fished for the hardest one you could find, and of course that's the point behind the refresh button.  

You can see an example [here]("http://phoenix2.ath.cx/~jbylund/recaptcha/form.html") (not connected to any sort of backend).  Note this is my personal server and it may disappear at any time.  And for some reason I need to refresh to get it to show up.

---

### Post by Exodist on 2009-12-21
> **hwttdz said:**
> I think many people agree that spam mail it out of hand.  And I believe it actually incurs pretty significant server costs.  Anyways, I was just wondering how you feel about using some sort of challenge response authentication? i.e. if someone you haven't corresponded with in the past sends you a message you don't receive the message until they complete some sort of simple question, essentially to prove they're not a spammer............


This may cause more server usage and time consumption.

---

### Post by hwttdz on 2009-12-21
But at least the additional load would be placed on those servers from which the spam is originating.  And those isp's which don't do anything about spam abuse will have to bear the cost of their inaction, which seems sort of ... fair.

---

### Post by Exodist on 2009-12-21
You know I recant my last statement.

I think used by itself it wouldnt be helpful, but used in conjunction with certificates as a temporary solution until someone can get a certificate established from the system admin. Then it would be useful.

I hope i didnt confuse anyone with that statement..

---

### Post by hwttdz on 2009-12-21
I'm sorry, I don't understand what you mean by a certificate?

---

### Post by dragos240 on 2009-12-21
I thunk captcha is a great idea. It needs to improve, but it's a good concept.

---

### Post by Sporkman on 2009-12-21
I heard of one project where captcha responses were used to transcript old, rare documents & books.

---

### Post by hwttdz on 2009-12-21
> **Sporkman said:**
> I heard of one project where captcha responses were used to transcript old, rare documents & books.

Well it's not quite as noble as you make it out to be, but the most common implementation, reCAPTCHA, uses responses to digitize books.  But it's really any books, it's part of google's attempt to digitize everything.

---

### Post by Exodist on 2009-12-21
> **hwttdz said:**
> I'm sorry, I don't understand what you mean by a certificate?
Its used with microsoft exchange servers to validate emails and also used in encryption stuff. Something we used when I was in the military.

---

### Post by Sporkman on 2009-12-27
[IMG]http://sporkforge.com/slush/g.png[/IMG]

---

### Post by Gizenshya on 2009-12-27
I've seen some where there is a question, and you have to read and understand it to give the correct one word response.  I've also seen math word problems.

sometimes I think the captcha people typed their "correct" response wrong.  Maybe they used a sucky screen reader.

---

### Post by lisati on 2009-12-27
> **Gizenshya said:**
> I've seen some where there is a question, and you have to read and understand it to give the correct one word response.  I've also seen math word problems.

sometimes I think the captcha people typed their "correct" response wrong.  Maybe they used a sucky screen reader.

I don't know if there's a Linux-friendly version, but the challenge-response system I used to use with XP provided a link to a web page. The idea was that the person filled out a form which asked them to identify themselves and why they were contacting me. There was also a simple numeric captcha box which was a lot easier to read than some of the examples in this thread. After they clicked on "submit", an email was sent to my email address which was then picked up and automatically recognized by the software. Simply replying to the challenge email wouldn't work - it would go to a "noreply@" style email address and get bounced.

---

### Post by Keyper7 on 2009-12-27
> **Sporkman said:**
> I heard of one project where captcha responses were used to transcript old, rare documents & books.

reCaptcha is a very good project. They use a source that is at the same time naturally
readable by humans and experimentally unreadable by OCRs. And the double word system
makes it even harder for bots to pass it.

In the worst case, that is when people are hired at minimum wage to keep bypassing the
captchas manually, it still contributes to digitze books. A win-win situation.

---

### Post by chewearn on 2009-12-27
A major problem with challenge-response scheme that has not been brought up here is this.  Most spam emails have spoofed return or send-from addresses.  Therefore:

1. While people sending legitimate emails to you got inconvenienced, the spammers are not.
2. The challenge-response scheme would reply email to an unknown sender, which went to the spoofed address.  If the spoofed address was actual directed to a real server, you might get a nasty response from the server admin/recipient.  You might be reported as spammer yourself and have your email added to a spammer blacklist.

---

### Post by hwttdz on 2009-12-27
> **chewearn said:**
> A major problem with challenge-response scheme that has not been brought up here is this.  Most spam emails have spoofed return or send-from addresses.  Therefore:

1. While people sending legitimate emails to you got inconvenienced, the spammers are not.
2. The challenge-response scheme would reply email to an unknown sender, which went to the spoofed address.  If the spoofed address was actual directed to a real server, you might get a nasty response from the server admin/recipient.  You might be reported as spammer yourself and have your email added to a spammer blacklist.

I think that's the problem I'm most worried about.  I think the best solution here would be to enforce some relationship between the sender, from and reply to fields.  As most spammers throw out real reply to fields (otherwise they'd never get responses), so if they forge the from field you just ignore the message.  

I think that these forged headers are the big problem because I don't believe the time cost is significant.  And if it's not worth it for someone to complete the challenge which takes maybe 10 seconds, it's probably also not worth my time to read their message.

Of course I don't think I could implement this myself currently.

---

### Post by lisati on 2009-12-27
> **chewearn said:**
> A major problem with challenge-response scheme that has not been brought up here is this.  Most spam emails have spoofed return or send-from addresses.  Therefore:

1. While people sending legitimate emails to you got inconvenienced, the spammers are not.
2. The challenge-response scheme would reply email to an unknown sender, which went to the spoofed address.  If the spoofed address was actual directed to a real server, you might get a nasty response from the server admin/recipient.  You might be reported as spammer yourself and have your email added to a spammer blacklist.

It was actually mentioned in the first page of the thread. [http://ubuntuforums.org/showpost.php?p=8537417&postcount=9](http://ubuntuforums.org/showpost.php?p=8537417&postcount=9)

---

### Post by chewearn on 2009-12-27
> **lisati said:**
> It was actually mentioned in the first page of the thread. [http://ubuntuforums.org/showpost.php?p=8537417&postcount=9](http://ubuntuforums.org/showpost.php?p=8537417&postcount=9)


Ah, ok.  My bad.

---

### Post by Keyper7 on 2009-12-27
Several mail providers in my country offer a challenge/response system. And when I receive a challenge from one of those systems, I promptly ignore it.

I'm not going to configure your filter for you. Period.

---

