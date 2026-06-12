---
title: "So this is irritating.."
date: 2007-12-11
forum: The Cafe
---

### Post by blithen on 2007-12-11
I saw someone today wearing a 'chown -R us ./base' shirt and I KNOW they do NOT know what that means. Does this irritate anyone else?

---

### Post by igknighted on 2007-12-11
> **blithen said:**
> I saw someone today wearing a 'chown -R us ./base' shirt and I KNOW they do NOT know what that means. Does this irritate anyone else?

I would think it would be *base*, after all, you need all possible "bases" ;)

---

### Post by blithen on 2007-12-11
> **igknighted said:**
> I would think it would be *base*, after all, you need all possible "bases" ;)
:lolflag::KS

---

### Post by akiratheoni on 2007-12-11
Yeah, it does... >.<

---

### Post by willie_wang on 2007-12-11
:( i don't get it

---

### Post by blithen on 2007-12-11
> **willie_wang said:**
> :( i don't get it

Do you not get the command or why I'm mad?

---

### Post by Lostincyberspace on 2007-12-11
> **blithen said:**
> Do you not get the command or why I'm mad?
Or both?

---

### Post by igknighted on 2007-12-11
> **Lostincyberspace said:**
> Or both?

In geek lore there is a poorly translated animated video, and the catch phrase from it was "all your base are belong to us".  So chown is the change ownership command, -R is recursive (for all), 'us' is the user who ownership is being changed to, and ./base is the file/folder that the ownership is being changed.  So it's a geekification of a geek phrase.  When I added the *'s they are wildcards, so any file or folder in that directory that had the string 'base' anywhere in it would have its ownership changed, just to tack on a little extra ;).  Hope that helps.

<completely kidding>
If you need more help, use 'man chown' and rtfm!
</completely kidding>

EDIT FOR LINKS:
[http://en.wikipedia.org/wiki/All_your_base_are_belong_to_us](http://en.wikipedia.org/wiki/All_your_base_are_belong_to_us)
[http://www.youtube.com/watch?v=qItugh-fFgg](http://www.youtube.com/watch?v=qItugh-fFgg)

---

### Post by LookTJ on 2007-12-11
Haha that's funny, but that's supposed to go to nix people?

---

### Post by hanzomon4 on 2007-12-11
Why would it be ./base? Is base being executed or is it part of a hidden root?

---

### Post by igknighted on 2007-12-11
> **hanzomon4 said:**
> Why would it be ./base? Is base being executed or is it part of a hidden root?

./ just means "in this folder".  It only executes if it is issued as the command, in this case it is an argument.  So it is saying "the file/folder called base, in the current directory".

Actually, a better example would be to open a terminal and type 'mkdir newdir' and then 'cd newdir', then run 'ls -al' to show all the files.  You will see a '.' and a '..'.  The '.' means this folder, while the '..' means one folder above.  So assuming I made newdir in my home folder, 'cd ../Desktop' would take me to my desktop.  If you were in your home folder, 'cd ./Desktop' would work.  The reason you don't normally need this is that it is assumed most of the time.  When executing a program, however, you need to explicitly state "this folder", or else it will look for the app in /usr/bin or /bin, or any of several folders.  You can add ./ to the list of directories that the system will try to execute to avoid needing the ./ if you desire.

(Note: I'm only rambling about this crap because I have an exam on it tomorrow, so this is studying in a way... just tell me to shut up if you want :))

---

### Post by Lostincyberspace on 2007-12-11
Because who ever did it didn't ever know what they were doing.

---

### Post by hanzomon4 on 2007-12-11
Well that's just extra work! If base is in the working directory "chown -R us base" would be fine...

---

### Post by igknighted on 2007-12-11
> **hanzomon4 said:**
> Well that's just extra work! If base is in the working directory "chown -R us base" would be fine...

Indeed.  Clearly the work of a n00b. :P

---

### Post by hanzomon4 on 2007-12-11
[This boo.. I mean noob](http://www.youtube.com/watch?v=kBVmfIUR1DA)

---

### Post by igknighted on 2007-12-11
> **hanzomon4 said:**
> [This boo.. I mean noob](http://www.youtube.com/watch?v=kBVmfIUR1DA)

Haha, I saw that for the first time the other day... classic.

---

### Post by dfreer on 2007-12-12
> **hanzomon4 said:**
> Well that's just extra work! If base is in the working directory "chown -R us base" would be fine...

But what if you have a program in your path called *base*? 0.o

---

### Post by chips24 on 2007-12-12
what the .... are you talking about, i dont understand, it dosent sound friendly.

---

### Post by hanzomon4 on 2007-12-12
> **dfreer said:**
> But what if you have a program in your path called *base*? 0.o

Nothing

Edit: path as in /usr/bin or in the same directory as base? In the latter I guess you'd end up owning both, but I don't think it's possible to have two files with the same name in the same directory.

---

### Post by jr.gotti on 2007-12-12
Lmao! This thread is fun...

---

### Post by Erdaron on 2007-12-12
> **blithen said:**
> I saw someone today wearing a 'chown -R us ./base' shirt and I KNOW they do NOT know what that means. Does this irritate anyone else?

I know it's probably elitist in some way, but I feel ya. You need to earn your geeky chops to wear something like this.

(Also, shouldn't it be 'sudo chown -R us ./base'?)

(Speaking of [sudo]("http://elliottback.com/wp/wp-content/uploads/2006/09/sandwich.png"). Tee-hee. I know it's old.)

---

### Post by dfreer on 2007-12-12
> **hanzomon4 said:**
> Nothing

Edit: path as in /usr/bin or in the same directory as base? In the latter I guess you'd end up owning both, but I don't think it's possible to have two files with the same name in the same directory.

Path as in /usr/bin. The reason for the *./base*, is because if there is a program called *base* in /usr/bin/, you'll end up changing it's permissions and not the permissions of the directory/file called *base* in your current directory. 

At least I think that is what will happen, and why they specify ./ Not that this really matters anyways :D

---

### Post by igknighted on 2007-12-12
> **dfreer said:**
> Path as in /usr/bin. The reason for the *./base*, is because if there is a program called *base* in /usr/bin/, you'll end up changing it's permissions and not the permissions of the directory/file called *base* in your current directory. 

At least I think that is what will happen, and why they specify ./ Not that this really matters anyways :D

No, since base is an argument, not a command, it wont look in the default path.  The ./ was unnecessary here.

---

### Post by willie_wang on 2007-12-15
> **Lostincyberspace said:**
> Or both?

both :)

---

### Post by aimran on 2007-12-15
> **chips24 said:**
> what the .... are you talking about, i dont understand, it dosent sound friendly.

It's from a video game. The english translation was poor and has since evolved into a meme.

---

### Post by psyopper on 2007-12-15
I need to find one of these t-shirts. It's too bad "all your base" went back out of fashion a few years ago...

---

### Post by Paqman on 2007-12-15
> **psyopper said:**
> I need to find one of these t-shirts. It's too bad "all your base" went back out of fashion a few years ago...

You can get them from jinx.com, along with some other splendidly geeky shirts.

---

### Post by gn2 on 2007-12-15
It's just like kids wearing Che Guevara T-shirts, they haven't a clue, they just want to feel *cool* and make a statement.

Even if they haven't a clue what the statement is.

Send them all off to Antarctica wearing their Che + CLI t-shirts.
Then they'll be cool! :D

---

### Post by lespaul_rentals on 2007-12-15
> **blithen said:**
> I saw someone today wearing a 'chown -R us ./base' shirt and I KNOW they do NOT know what that means. Does this irritate anyone else?

How do you know they don't know it?  Are you friends with him/her?  Do you know that person has never ever used Unix?

Grow up, mate.  Stop caring about what other people are wearing, even if they are complete noobs who have no idea what it means.  Sure, it's stupid, sure it's probably just an attempt to feel 1337 and nerdy, but come on.  Light up a grit, walk your dog, do whatever you do to calm down.

---

### Post by forrestcupp on 2007-12-15
> **gn2 said:**
> It's just like kids wearing Che Guevara T-shirts, they haven't a clue, they just want to feel *cool* and make a statement.

Even if they haven't a clue what the statement is.

Send them all off to Antarctica wearing their Che + CLI t-shirts.
Then they'll be cool! :D

Do you remember in the 80's when it was popular to wear a t-shirt with Japanese writing on it?  No one even knew what they said.

---

### Post by gn2 on 2007-12-15
> **forrestcupp said:**
> Do you remember in the 80's when it was popular to wear a t-shirt with Japanese writing on it?  No one even knew what they said.

I also remember a girlfriend I had in the 90's who had a Japanese symbol tattoed on the top of her right butt cheek.

I'm fairly certain it meant: down a bit, left a bit, FIRE! *

(*Reference to UK game show Golden Shot in the 70's)

---

### Post by djsroknrol on 2007-12-15
I like my sig better:

There's no place like ~/ :)

---

### Post by ticopelp on 2007-12-15
> **lespaul_rentals said:**
> How do you know they don't know it?  Are you friends with him/her?  Do you know that person has never ever used Unix?

Grow up, mate.  Stop caring about what other people are wearing, even if they are complete noobs who have no idea what it means.  Sure, it's stupid, sure it's probably just an attempt to feel 1337 and nerdy, but come on.  Light up a grit, walk your dog, do whatever you do to calm down.

+1

---

### Post by Palmyra on 2007-12-15
First of all, you mean annoying, not irritating.  There's a difference.

Second, so what?  Let's take the most popular phrase on the Internet, and turn into into a phrase on a T-shirt.  So?  Why is this a big deal?  My fashion choices have absolutely nothing to do with you, whether you claim I know what I am talking about or not.  Suppose I used "In Soviet Russia, ...." on a shirt.  Sure, this phrase is now widely used on the Internet, but I don't want some fashion experts (e.g. you) to give me their opinions on what is appropriate or not appropriate.  

It is people like you who find that their opinions are so valuable they must permeate the lives of other people.  Take, for example, me.  I like to pop my collars, but only in private.  I dare not do this in public for fear of having someone point out that this was something done long ago, and it is, nowadays, taboo to pop your collar.  Why do I care that it is no longer fashionable to pop one's collar?  Do I like doing it?  Yes.  Therefore, I shall do it.  But I don't do it, because, again, of people like you.

Oh, my post says that I am heated about this, and to a certain extent, I am, but don't worry, because my heart is not beating at a faster rate.  To the OP: don't worry too much about my rant.  It's not so much about you, but the overall society that dictates what can and cannot be done.  I am sure you are a nice and friendly person.

[img]http://i23.photobucket.com/albums/b360/Euxgnibs/Popped-Collar.jpg[/img]

---

### Post by blithen on 2007-12-15
> **lespaul_rentals said:**
> How do you know they don't know it?  Are you friends with him/her?  Do you know that person has never ever used Unix?

Grow up, mate.  Stop caring about what other people are wearing, even if they are complete noobs who have no idea what it means.  Sure, it's stupid, sure it's probably just an attempt to feel 1337 and nerdy, but come on.  Light up a grit, walk your dog, do whatever you do to calm down.
Yes I am friends with him. At least good enought to know he doesn't know anything about *Unix.

---

### Post by hanzomon4 on 2007-12-15
> **Paqman said:**
> You can get them from jinx.com, along with some other splendidly geeky shirts.

The got some nice stuff

---

### Post by herbster on 2007-12-15
If this actually irritates you, kiss the floor and thank the universe for the life you got.

---

### Post by blithen on 2007-12-15
Well I guess this turned out to be more of a bashing me thread, so mods if you read this can you please close the thread? All I simply asked was if it made anyone feel weird knowing that the person I know wears a shirt that he has no idea what it means. Guess it's to hard to stay on topic I guess. Again mods if you read this, please close it.

---

### Post by ticopelp on 2007-12-15
You didn't say "make anyone feel weird," you said it "irritated" you and that you were "mad." I mean, not to bash you or anything, but let's not pretend you asked some other question other than what you asked. 

And to specifically answer said question; no, I don't know why it would be worth getting upset about.

---

### Post by blithen on 2007-12-15
> **ticopelp said:**
> You didn't say "make anyone feel weird," you said it "irritated" you and that you were "mad." I mean, not to bash you or anything, but let's not pretend you asked some other question other than what you asked. 

And to specifically answer said question; no, I don't know why it would be worth getting upset about.
well none the less, people started bashing me for asking a question.

---

### Post by lespaul_rentals on 2007-12-15
We didn't bash you, a lot of us just stated that while we do agree it's stupid to wear that shirt when you really have no idea what it means, we just feel it's quite pointless to complain.

---

### Post by blithen on 2007-12-15
> **lespaul_rentals said:**
> We didn't bash you, a lot of us just stated that while we do agree it's stupid to wear that shirt when you really have no idea what it means, we just feel it's quite pointless to complain.

And I appreciate the reply, and thanks you for it, but a few did bash me.

---

### Post by Paqman on 2007-12-16
> **blithen said:**
> a few did bash me

Not really. Maybe a gentle lightweight kind of bashing. I wouldn't stress about it too much if I were you :)

---

### Post by herbster on 2007-12-16
Hey we got love for ya, perhaps just don't share in the level of irritation you found from the shirt...

---

### Post by forrestcupp on 2007-12-16
> **Palmyra said:**
> 
Second, so what?  Let's take the most popular phrase on the Internet, and turn into into a phrase on a T-shirt.  So?  Why is this a big deal?  My fashion choices have absolutely nothing to do with you, whether you claim I know what I am talking about or not.  Suppose I used "In Soviet Russia, ...." on a shirt.  Sure, this phrase is now widely used on the Internet, but I don't want some fashion experts (e.g. you) to give me their opinions on what is appropriate or not appropriate. 
I don't think you really understand.  I don't think it's a problem with fashion.  I don't think he has a problem with the shirt.  He just thinks it's dumb for someone to wear a shirt like that if they don't have any idea what it means.

> **blithen said:**
> Well I guess this turned out to be more of a bashing me thread, so mods if you read this can you please close the thread?
If you can't handle a few people that you've never seen and probably never will see disagreeing with you on a forum, you need to spend some time searching your soul.  It's not that big of a deal.  Everyone has their own opinion.

---

