---
title: "Age verification process"
date: 2007-11-01
forum: The Cafe
---

### Post by twistedtwig on 2007-11-01
Hi all,

this may not get any answers at all.  I have been googling it for a bit and still not found exactly the answer I am looking for (am still going naturally)..

I am a one man band and thinking of setting up am online poker site in the UK.  This will (at first at least) have NO real money transactions, will be all "fun" money.

But there are legal issues, least of all "Age Verification".  I am not really sure how to go about this.  There are sites I can pay to use, but I was hoping to find a way of maybe checking against UK passport, or National insurance numbers or Credit cards (without taking any money off of it).

I don't know if I will need a different process for different countries.  What I am getting at I guess is do people have any experience with this, any suggestions or hints and where to go or what to do?

Thanks

---

### Post by ddrichardson on 2007-11-01
Well, I'm sure there are solutions, of which we could debate all night. In all honesty though, given the time and effort this would require, would it not be as well just consulting a lawyer so you have piece of mind in the issue?

---

### Post by twistedtwig on 2007-11-02
You could be right (about finding out where the law stands)... I am also interested in the technical side if people have any knowledge on the implementation as well.

Thank you for your input :)

---

### Post by Superdelphinus on 2008-01-09
I can help you with the law bits if you like? what do you need to know? re age verification it's all about off setting your liability - i.e. getting the 3rd party to confirm that they are over the age limit using an 'autograph' which could amount to a simple check box

---

### Post by pjkoczan on 2008-01-09
> **twistedtwig said:**
> But there are legal issues, least of all "Age Verification".  I am not really sure how to go about this.  There are sites I can pay to use, but I was hoping to find a way of maybe checking against UK passport, or National insurance numbers or Credit cards (without taking any money off of it).

I don't know if I will need a different process for different countries.  What I am getting at I guess is do people have any experience with this, any suggestions or hints and where to go or what to do?

Those are certainly ideas, but good luck getting access to that information to check it, and good luck getting people to enter sensitive data such as that.

If you're really concerned about age verification, you might want to consider creating a login system on the web-app end and requiring a valid email address to sign up. This way you can track people and possibly vet against email providers information (they may be more willing to work with you if you have a problem). It's hard to actively suss this out, so you'll probably end up taking a more passive approach to this anyway (i.e. dealing with a problem after it happens).

I'm not a lawyer, though. As was previously mentioned, you should check with one if you're truly that concerned.

---

### Post by ~LoKe on 2008-01-09
All you need is one of those disclaimer pages.  "Over 18? Enter"  "Under 18?  Leave".

---

### Post by Fleece Flamingo on 2008-01-09
If it's not "Real money" I don't see why you would need to verify.
I guess you could have a Terms Of Service that says you must be 18. You could also tell users on sign up to send you an 0.00 amount over pay pal that way you will know if they are indeed 18. Then when the site gets a little more popular you can use an actual service.

---

### Post by ~LoKe on 2008-01-09
> **Fleece Flamingo said:**
> You could also tell users on sign up to send you an 0.00 amount over pay pal that way you will know if they are indeed 18. Then when the site gets a little more popular you can use an actual service.

I had a PayPal account before I was 18. ;)

---

### Post by el_ricardo on 2008-01-09
check against the electoral roll, that has everyone's birthdates on it, not sure how you'd automate it though

---

### Post by twistedtwig on 2008-01-10
Thank you for all your replies.

I think I will end up going with more of terms and conditions and a check box stating you agree that your are 18+.

I do like the idea of paypal 0.00 value, but as LoKe said it is "possible" to get an account before your 18.  but then again its just as easy to tick a box when your 14 as when your 18.  Maybe a combination of them both.

Now just need to figure out how I could possibly automate the recipt of 0.00 from a certain person to then run a script to enable that account :p

---

### Post by tigerplug on 2008-01-10
> **~LoKe said:**
> All you need is one of those disclaimer pages.  "Over 18? Enter"  "Under 18?  Leave".


Yup, I think thats a good idea.


Also maybe you could try some CC verification (Yoiu can't get a Credit Card unless you are at least 18)

What will the site run on? - what are you building it with?

---

### Post by twistedtwig on 2008-01-10
The hardware is abit modest.. at least atm.. if it takes off I hope to be able to afford better later.

it is going to be a C# set of applications (as I use it at work and want to improve my knowledge in that area).  I have a windows 2003 standard server to host it on.

The problem with Credit Cards is that who is going to give me those details for a game that has NO real money involved at all...  I wouldn't would feel a bit odd....

I may go to real money down the line.. but that involves casino license and well.. they are like £30K ish a year in the UK!!!!!

---

### Post by tigerplug on 2008-01-10
> **twistedtwig said:**
> The hardware is abit modest.. at least atm.. if it takes off I hope to be able to afford better later.

it is going to be a C# set of applications (as I use it at work and want to improve my knowledge in that area).  I have a windows 2003 standard server to host it on.

The problem with Credit Cards is that who is going to give me those details for a game that has NO real money involved at all...  I wouldn't would feel a bit odd....

I may go to real money down the line.. but that involves casino license and well.. they are like £30K ish a year in the UK!!!!!



Hmm... Windows Server :( 

yeah I know what you mean... don't give up though!

It is profitable! ... enjoyable too!

---

### Post by twistedtwig on 2008-01-11
hehe yer... I hope so.... I do enjoy my ubuntu box but want to keep a foot in both camps so to speak.

Thanks for all the help and advice everyone.

---

### Post by fatality_uk on 2008-01-11
I suggest Mono for c# and you can keep a Linux server running.

If you want any help on the poker side, let me know. I am a three time regional finalist for LPPL, UKOPL and a won a "fair" bit of cash in ring games. I also ran a "poker school" at my local rugby club

I specialise in TH, 5 card draw :)

---

### Post by twistedtwig on 2008-01-11
Hi fatality_uk,

I did think about Mono for a bit but wanted to use MS SQL server to have a good play with that and read that it does not play nicely in Linux at all.

As far as I am aware they ahve "nearly" all of .Net 2.0 up these days.  I think it is going to be a real challenge at any rate and the posisbly added difficulty of worying about any Mono issues might just be that bit too much.

I often do worry about the sercuirty of Windows server compared to my ubuntu box (windows sides inside the network atm protected (mostly) by the ubuntu box).

I am still umming and arrhhing which way to go about it all really.


You sound like you know your stuff with Poker.  I am ok, nothing special at all, just enjoy playing the game, love the fact that it has the random and skill factors involved.  

I am really looking forward to getting my teeth fully into the project but have a couple of smaller ones to finish off before I do.  This is going to be (by  long way) the biggest project I take on and don't want to have old projects lying around wanting attention..  They are also acting as a bit of a training ground so I don't F&^* things up so much later! ;)

I will be testing the client in Mono to see how that runs, but I did plan on learning C++ to do a client in there as well once I have a lot of the C# side of things done.... 

I like to think about them and plan them as much as I can before I get too deep into code and find I have missed something or got an idea too wrong... to that end it has taken me longer than I wanted but I will get there....


If anyone has used Mono to create apps that are running 24/7, use aspx as well as web services, and can deal with remoting I would be interested to hear if it is "just the same as windows"... I presume you can not make windows services in linux....

I know the box I have thats runing 2003 would do a lot better on linux (perfomance wise) but I am nervous as to how much it can handle.

Also (god this is turning into a bit of a long one!)... I don't know how other DB's compare to MS SQL Server 2005, I have MySQL on the ubuntu Box atm but don't use it to the same extend as I think this maybe used.

Right... better leave it there or I will be ranting all day :p

Thanks...

---

