---
title: "OSS ecosystem... How does it work?"
date: 2007-11-19
forum: The Cafe
---

### Post by mardawi on 2007-11-19
If it's a platform, an OS, or a huge product then it makes sense to give it away for free, share the source code, and give everyone rights to play around with it. Because when you do that, you will have a large user base that you could never get without opening the source. And then you can profit by selling things around the product; consulting, support, hardware, more software tools, books... etc

But how can you profit when you are selling some sort of "small/medium sized" software product if you went ahead and opened the source? your competitors will rip the software off next morning and your 100 orders/month average will probably drop to zero although you are getting 10,000 new users a week!

So, how do you make money from your open source product?

---

### Post by Jussi Kukkonen on 2007-11-19
> But how can you profit when you are selling some sort of "small/medium sized" software product if you went ahead and opened the source? your competitors will rip the software off next morning and your 100 orders/month average will probably drop to zero although you are getting 10,000 new users a week!

That doesn't seem to match with reality. First, "rip the source and profit" is just wrong, in reality competitor would probably spend some amount of money and time to realise that the product is just different enough to not fit their systems/production environment without costly changes... Second, if the competitor offers similar services/add-ons as the inventor, the inventor can always get a little better price: name recognition and trustworthiness are even more important in OSS development than in sw business in general, IMO (this has lot to do with your application type though (consumer, business, server, ...). 

Now, if it happens that the competitor can actually out-perform the inventor/main developer from the above-mentioned situation, then the problem is not the source license, it's being less efficient... In this situation you're right though: squeezing the last penny out of customers really becomes impossible at this point (but it should be noted that a more efficient competitor probably will push you out sooner or later, regardless of source license).

Open-sourcing is definitely not a good business move everywhere, but I have yet to see an example of the scenario you describe. Counter-examples can be found quite easily: See e.g. Slimdevices with slimserver (available from ubuntu repos). They may be relatively big now as part of logitech, but they certainly weren't in the beginning.

---

### Post by daengbo on 2007-11-19
The people who wrote the code tend to get more "cred" than forks unless the original project went bad somewhere.

OSS is not about making money off the software -- It's about creating value for the customer. The traditional software system is pretty bad at doing that, which is why there were so many software multi-millionaires in the 90s. Competitive businesses which provide real value just don't start making cash hand over fist. They've got to work at it and continually improve the product.

The OSS market can be imagined as a restaurant. There are very few super-rich. Most restaurants just get by, and many more fail. The ones that make it do so by giving the diner something he/she couldn't get somewhere else and need to give a reason not to just eat at home.

---

### Post by mardawi on 2007-11-19
> **daengbo said:**
> The people who wrote the code tend to get more "cred" than forks unless the original project went bad somewhere.
The question is how to make money directly from an open source project that isn't huge enough to provide services around it.

> **daengbo said:**
> 
The OSS market can be imagined as a restaurant. There are very few super-rich. Most restaurants just get by, and many more fail. The ones that make it do so by giving the diner something he/she couldn't get somewhere else and need to give a reason not to just eat at home.
This is not true, you completely skipped the fact that restaurants actually sell treatment... not food. So, this puts us back into the model of providing the main product for free and profiting from the services around it.

> 
Open-sourcing is definitely not a good business move everywhere, but I have yet to see an example of the scenario you describe. Counter-examples can be found quite easily: See e.g. Slimdevices with slimserver (available from ubuntu repos). They may be relatively big now as part of logitech, but they certainly weren't in the beginning.
slimdevices sell hardware, even if their software doesn't sell good, they still profit more from hardware on the long run.

---

### Post by daengbo on 2007-11-19
> This is not true, you completely skipped the fact that restaurants actually sell treatment... not food. 
Actually, that was exactly my point. In the FLOSS world, you don't make money off of the software. People that try that completely miss the boat and fail.

Smaller projects are generally something that was developed in-house or used to boost someone's resume. Having a great OSS project can prove your project-management skills better than any interview ever could.

If you want to start a business around it, you make money by bundling it with hardware or by offering services. There are methods whereby people add proprietary pieces to a mostly OSS core, but these companies rarely do well.

Somehow, I don't think you're asking this out of true curiosity...

---

### Post by bonzodog on 2007-11-19
Guys see please my other thread above, and read the two essays.

Eric explains that project forking is extremely rare, and almost never happens, unless something major happens, or the developer loses interest. 

Anyway, anyone re-using your code would have to mention yourself as being it's originator and then pass their OWN code on as well - this kind of acts as a preventative for using others code unless you don't intend to make anything from it.

---

### Post by mardawi on 2007-11-19
The reason behind the question is that in my opinion commercial close-source software are more popular/successful (not necessarily better) because those small/medium sized projects (the majority) can do serious profits and their FOSS counter-parts can't! And I think this is an important issue in the OSS ecosystem. How do we expect OSS to grow (grow, as in real growth, not a 26 million, the highest number i found, Linux users) while the majority of projects can't make any serious profits? 

I hope the discussion doesn't go off topic. I believe this is an important issue that should be addressed.

---

### Post by bonzodog on 2007-11-19
I think you are entirely on the wrong track here.

FLOSS is not about money - it doesn't need it to survive due to the viral nature of the GPL.

Open Source is a moral and ethical code for programming and licensing software. There is nothing to stop you selling the program, but most people that program for Open Source do it because they *want* to. 
A lot of closed source programmers actually have no personal interest in what they are doing, whereas Open Source developers tend to write software because it fills a niche that they are interested in using personally.
Open Source development happens in an entirely different way to Closed source, it's best explained in my other thread through ESR's essays.

PLEASE read this; [http://ubuntuforums.org/showthread.php?t=617338](http://ubuntuforums.org/showthread.php?t=617338)

You will understand an awful lot more about Linux and Open Source after that.

---

### Post by daengbo on 2007-11-19
Just recommend he keep an eye on Slashdot. He'll get all the information he can handle. ;)

---

### Post by az on 2007-11-19
> **mardawi said:**
> The reason behind the question is that in my opinion commercial close-source software are more popular/successful (not necessarily better) because those small/medium sized projects (the majority) can do serious profits and their FOSS counter-parts can't! And I think this is an important issue in the OSS ecosystem. How do we expect OSS to grow (grow, as in real growth, not a 26 million, the highest number i found, Linux users) while the majority of projects can't make any serious profits? 

I hope the discussion doesn't go off topic. I believe this is an important issue that should be addressed.


How can a restaurant make profits selling pizza if all the other restaurants around the neighborhood have the recipe to make the same pizza?

That is a more correct analogy of the question you are asking.  The value that the customers get (the pizza) is not the software itself.  It's the ability to make their computer do something.  In this analogy, the proprietary pizza vendor will charge you twice:  Once for the pizza and another time for the right to eat the pizza made from their recipe.  In other words, what the computer customer wants is to make the computer do something.  In the proprietary world, you have to pay for shelfware.  You have to pay again for support (any software in production use needs support).  In the FLOSS world, you simply pay for the services and support.

The value that computer users are willing to pay for is provided by FLOSS.  In fact, the great majority of software developers work (and get paid) to develop software that will never be sold (either free-libre or in-house)  Only a small percentage of software developers work for a project that makes money by being shrink-wrapped and sold in stores.

Edit:  Does Wolfgang Puck think that publishing a cookbook will mean less business for his restaurants?  No.  In fact it will make the restaurants more popular.

---

### Post by mardawi on 2007-11-19
> **daengbo said:**
> Just recommend he keep an eye on Slashdot. He'll get all the information he can handle. ;)

Do you always insult people before leaving discussions you can't handle?

---

### Post by mardawi on 2007-11-19
> **az said:**
> How can a restaurant make profits selling pizza if all the other restaurants around the neighborhood have the recipe to make the same pizza?

That is a more correct analogy of the question you are asking.  The value that the customers get (the pizza) is not the software itself.  It's the ability to make their computer do something.  In this analogy, the proprietary pizza vendor will charge you twice:  Once for the pizza and another time for the right to eat the pizza made from their recipe.  In other words, what the computer customer wants is to make the computer do something.  In the proprietary world, you have to pay for shelfware.  You have to pay again for support (any software in production use needs support).  In the FLOSS world, you simply pay for the services and support.

The value that computer users are willing to pay for is provided by FLOSS.  In fact, the great majority of software developers work (and get paid) to develop software that will never be sold (either free-libre or in-house)  Only a small percentage of software developers work for a project that makes money by being shrink-wrapped and sold in stores.

Edit:  Does Wolfgang Puck think that publishing a cookbook will mean less business for his restaurants?  No.  In fact it will make the restaurants more popular.

I understand that, and it's great, believe me i have nothing against it. I'm just trying to figure out how is it possible to make money out of "shelfware" when opening the source code. or is it as Jussi Kukkonen said >  Open-sourcing is definitely not a good business move everywhere...

---

### Post by az on 2007-11-19
> **mardawi said:**
> I understand that, and it's great, believe me i have nothing against it. I'm just trying to figure out how is it possible to make money out of "shelfware" when opening the source code. 

It's not.  Shelfware is not the correct business model.  It's not the business model that made millions for Google, Ebay, Amazon.com, Facebook, etc...  As for individual software projects, they make money by providing support.

The internet is digital;  suffice for one person to solve a problem and everyone can get it.  The cost of providing the code to one person is almost the same as providing it to everyone.  There will always be motivation for someone to pay a developer to write better software.

And if you want to make millions from shelfware, don't become a software engineer - become a lawyer.  These days, software companies don't pay software developers anything near what they spend on lawyer fees.

In regards to giving away the code, I wouldn't be concerned about FLOSS if I were you.  I suspect the shelfware companies are on their way out.  FLOSS is a disruptive technology and I don't think that many people are going to want to continue paying for someting they can get for free.

---

### Post by daengbo on 2007-11-20
How was that construed as an insult? It's the truth. This subject has been beaten to death in the 10 years I've been on Slashdot. You'll get every side of the story ten times if you head over there.

---

### Post by 23meg on 2007-11-20
Here's a relevant success story:

[http://www.linux.com/feature/121377](http://www.linux.com/feature/121377)

---

### Post by scorp123 on 2007-11-28
> **mardawi said:**
>  But how can you profit when you are selling some sort of "small/medium sized" software product if you went ahead and opened the source? your competitors will rip the software off next morning and your 100 orders/month average will probably drop to zero although you are getting 10,000 new users a week!  That highly depends on the license under which you published your code. For example: The BSD License. Read the Wikipedia article for the details:
[http://en.wikipedia.org/wiki/Bsd_license](http://en.wikipedia.org/wiki/Bsd_license)

Is the BSD License open source? Yes. Can others copy your code if you release your source code under this license? Yes. Can they sell their products? Yes. Are they forced to give back the changes they did? **NO.** Examples of this:

- Apple Mac OS X ... is based on BSD. And Apple is making big money from this. And because of the rules of the BSD License Apple don't have to publish their improvements or changes.

- Windows TCP/IP stack: ripped straight from BSD. Google around for this, there are lengthy discussions about this.

And now for contrast the GNU General Public License ("GPL"). Wikipedia explains all the details:
[http://en.wikipedia.org/wiki/GNU_General_Public_License](http://en.wikipedia.org/wiki/GNU_General_Public_License)

Is the GPL license open source? Yes. Can others copy your code if you release your source code under this license? Yes. Can they sell their products? Yes but read the license, there are certain conditions you should be aware of. Are they forced to give back the changes they did? **OH YES!**

So back to your scenario:

If you release your stuff under the GPL then any potential competitor is of course free to copy your product and "steal" customers from you. But because of the GPL any changes they make have to be published too, and by the same right you are able to incorporate their changes back into your original product and thus compete fair and square with anyone who copied your source code. That's for example how commercial Linux distributors (e.g. SUSE/Novell vs. Red Hat vs. Xandros, etc.) compete with each others. Huge parts in those distributions were and are released under the GPL. Any improvements or changes therefore have to be GPL too. And because of this anyone can copy those parts and incorporate them into their GPL products. And whoever the improvement got taken from can take the new changes back into their product ... and so on.

As I said ... it's all a matter of the license you choose, IMHO. :)

---

