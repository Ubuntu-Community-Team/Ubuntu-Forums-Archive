---
title: "Network Admin Job"
date: 2012-03-29
forum: The Cafe
---

### Post by darknoobie on 2012-03-29
Recently I was hired by this company to help build there website and clean up there network issues. We have Servers that are roughly 8 years old and router's, switches that are bout 6 years old. The equipment is in a closet. The servers were covered with 1/8 inch of dust. Right before I got there they had a server fail and data was completely gone. They hired data doctors to fix it. The second week I was there we lost power in the closet and mail server completely died. I was able to go into everyone's computers and export the ost to pst and rebuild on a new exchange server. I saved them a few hundred dollars and I was told if we lost data again while I worked here I would get fired. I found out that the backup power supply unit had been out of service for 2 years. I responded with. "We need funds to purchase new equipment or allow me to shutdown everything to clean/backup and restore everything using ubuntu. They told me they don't have the funds, just to work with what I got. Recently the closet lost power again and 3 scsi drives died. Now I'm being threatened that I will lose my job if I don't get that data back. They had asked me why I didn't do a backup. I responded with "I did but the 250gb backup drive you purchased me cant hold 2tb of information. :mad: Well I was hoping if anyone can give me advice weather I should hang in and deal with this or ditch the place and get a new job. I have A+ and Network+ certification and currently in queue for Cisco ccna training.

---

### Post by trivialpackets on 2012-03-29
I'm not one to give the advice to walk away from a job without having another in place, although I can say without a doubt, keep looking for something better.

---

### Post by CharlesA on 2012-03-29
> **eric.proctor said:**
> I'm not one to give the advice to walk away from a job without having another in place, although I can say without a doubt, keep looking for something better.

What he said. Sometimes you are given a shoe-string budget and asked to work miracles and it's not possible.

If they don't give you the tools to do your job, and expect you to get it done somehow, find a different job.

---

### Post by chamber on 2012-03-29
No matter how crappy the company are, if you quit and went for a new job it could end up making you look bad that you just quit.  Its easier to get a job when you are in a job.

---

### Post by winh8r on 2012-03-29
I would suggest sticking with it for the time being, but in the meantime

 maybe prepare a fully detailed report listing all that is wrong or not 

functioning as it should, and put in writing your judgement that the system 

is not fit for purpose the way it is and is in all likelihood going to fail 

again unless you are given the resources to do something about it.

Make sure this goes to someone in authority.

That way if it fails again through no fault of yours then they will not 

have a leg to stand on legally as you warned them of the dangers well in 

advance and they chose to ignore your warnings based on your experience 

and qualifications in the job.

By all means cover their back, but make sure yours is covered better!

Good Luck.

---

### Post by CharlesA on 2012-03-29
> **winh8r said:**
> I would suggest sticking with it for the time being, but in the meantime

 maybe prepare a fully detailed report listing all that is wrong or not 

functioning as it should, and put in writing your judgement that the system 

is not fit for purpose the way it is and is in all likelihood going to fail 

again unless you are given the resources to do something about it.

Make sure this goes to someone in authority.

That way if it fails again through no fault of yours then they will not 

have a leg to stand on legally as you warned them of the dangers well in 

advance and they chose to ignore your warnings based on your experience 

and qualifications in the job.

By all means cover their back, but make sure yours is covered better!

Good Luck.
Huge +1 to that. It also covers you if they push it and say that you aren't doing your job.

---

### Post by angryfirelord on 2012-03-29
Yeah, that can be hard when you're stuck in a situation like that. Unfortunately, incompetent upper management seems to be the norm in most businesses.

What I would do is break it down into terms they can understand. Don't say, "I have to convert your backup to Ubuntu and it's going to cost $2000." Try something like, 

"Your server here has been in use for a while. Generally, 5 years is the life expectancy of computers and unfortunately, this one isn't going to last. I have an idea of putting in a new system and if you give me a little time to work out the details, I can probably knock down the overall equipment cost with some bundling. This new system should also perform a lot better than your old one." 

No matter how crappy the situation is, you have to present your idea as a positive, cost-saving benefit.

Stuff like this though is hard. I agree that the job probably isn't going to be pleasant overall, but at the same time quitting too soon can make you look bad to other prospective employers. It's a horrible vicious cycle, but that's what a recession will do. Your best bet is to lay out a plan, show management exactly what's needed and give a reasonable deadline to execute on it.

---

### Post by CharlesA on 2012-03-29
One of the things the IT manager at my work does is price out something that will do an awesome job but is expensive and then price out something that will do a good job (and still get the job done) but costs a lot less. 

Makes the budget guys happy cuz they can pick the cheaper option and it still gets the job done. ;)

---

### Post by keithpeter on 2012-03-29
> **angryfirelord said:**
> No matter how crappy the situation is, you have to present your idea as a positive, cost-saving benefit.

+1 to the full report and +1 to making it sound positive.

Best of luck with all this.

---

### Post by PapaGary on 2012-03-29
> **chamber said:**
> ...if you quit and went for a new job it could end up making you look bad that you just quit.
Not near as bad as getting fired.
> **chamber said:**
>  Its easier to get a job when you are in a job.
Truth.

---

### Post by knight2000 on 2012-03-29
Stick at it. Learn to improvise. Sometimes in the IT world you don't have the budget you want, but there are usually low/no cost ways to resolve many problems. When you become aware of something that potentially may become an issue always put it in an email and CC a few people into it. That way if something goes wrong you can say you did warn them about it. I've worked for a few companies that failed to invest and was nearly always able to find workaround for most issues. Sometimes it also helps to exaggerate a hardware problem early to force them into investing. I had to do that a few times to get workstations upgraded in a company I worked for. If I hadn't done that then the consequences would have been alot more costly than a new workstation. Anyway, good luck. Move on in good terms if you can.

---

### Post by SeijiSensei on 2012-03-29
I'd concentrate on getting them to invest in a new UPS.  That's a relatively low-cost solution that will cure a major problem right away.  Make sure you install the monitoring software that comes with the UPS (or use apcupsd on any Linux servers if you buy an APC UPS) so that the servers will shut down gracefully when the power fails.

Limit the UPS to the machines that must be kept up, probably the mail and file servers.  Most UPS manufacturers' websites have a calculator that will tell you how big a device you'll need.  Something like [this](http://www.newegg.com/Product/Product.aspx?Item=42-102-070) would probably support two or three servers for the amount of time required for them to shut down cleanly (five minutes or so).  

Don't worry about the servers themselves.  I've had servers of that vintage running 24/7 just fine.  Conquer the power problem for now.

If you can get them to spring for $150 or so for an external 1 TB drive to use for backups, I'd press for that as well.  Otherwise tell them that you'll need a backup drive soon, and that you're waiting for hard drive prices to come back down after the problems associated with the floods in Thailand.

The strategy here is to pick a couple of important devices that aren't very expensive.  Remind them that the time it takes you to fix problems from the power outages probably costs them more than the cost of a UPS.  Not to mention the actual cost to their business of data loss.

You can tell them that the person who recommended this strategy has been in the business for almost twenty years if you think that will help!

---

### Post by CharlesA on 2012-03-29
> **SeijiSensei said:**
> I'd concentrate on getting them to invest in a new UPS.  That's a relatively low-cost solution that will cure a major problem right away.  Make sure you install the monitoring software that comes with the UPS (or use apcupsd on any Linux servers if you buy an APC UPS) so that the servers will shut down gracefully when the power fails.

Limit the UPS to the machines that must be kept up, probably the mail and file servers.  Most UPS manufacturers' websites have a calculator that will tell you how big a device you'll need.  Something like [this](http://www.newegg.com/Product/Product.aspx?Item=42-102-070) would probably support two or three servers for the amount of time required for them to shut down cleanly (five minutes or so).  

Don't worry about the servers themselves.  I've had servers of that vintage running 24/7 just fine.  Conquer the power problem for now.

If you can get them to spring for $150 or so for an external 1 TB drive to use for backups, I'd press for that as well.
Agreed. That would be the main thing I would worry about too. If the data is being lost because of the hard poweroffs (is that a word?), then a UPS will help with that until you can get a decent backup strategy implemented.

It's not a complete solution to the data corruption problem, but it is part of it with backups (plus a UPS) being the ultimate solution.

---

### Post by MisterGaribaldi on 2012-03-29
The thing is that if your management is as stupid as they seem to be, I would strongly encourage you to get your affairs in order and get out of that company ASAP. It's not worth it.

---

### Post by HermanAB on 2012-03-30
Howdy,

Explain to your management that electronics usually fail when it is turned on.  An example being a light bulb - they almost never fail while already working and at normal temperature.   A mains power failure usually causes the electric supply to flicker rapidly on and off many times and therefore frequently causes data corruptions and failures.  That is why you need to buy a new UPS immediately - it is the most important way to protect your equipment.

The next thing to do, is fix the ventilation of the equipment closet and add fans with filters.  Point out to your management that in general, things that are kept clean, tend to last longer and you have to vacuum the inside of the machines and get the dust out of the CPU cooling fins and fans.

At the same time, make backups, even if you have to use a 12 inch stack of DVDs.

Maybe in a few weeks, you can all look back at your rough start at the company and chuckle about it, with happy users and no more failures.

---

### Post by rk0r on 2012-03-30
> **MisterGaribaldi said:**
> The thing is that if your management is as stupid as they seem to be, I would strongly encourage you to get your affairs in order and get out of that company ASAP. It's not worth it.


 +1 to this.

If your company does not understand that maintaining their IT infrastructure is just as important as the data they are keeping on their disks, they are most certainly heading downwards.

I would send out your CV to other places and jump ship when the offer arises.

I have never heard of sacking someone because their IT Infrastructure is unmaintained and outdated its absurd.

---

### Post by knight2000 on 2012-03-30
Never leave a job on bad terms. It will come back to haunt you if you ever apply for a decent company.

---

### Post by MisterGaribaldi on 2012-03-30
> **knight2000 said:**
> Never leave a job on bad terms. It will come back to haunt you if you ever apply for a decent company.

Companies in the U.S. are not allowed, under labor laws, to discuss employees with other companies, except to confirm status as an employee and dates of hire. This isn't to say that things aren't said on the sly, but I really wouldn't worry about it too much. In my experience, the next company is more interested in what you can do for them than what happened at the previous company. Obviously, you need to put a positive face on the situation in your next interview, but get the d*** interview! That's the most important thing.

---

### Post by Ms. Daisy on 2012-03-30
> **MisterGaribaldi said:**
> The thing is that if your management is as stupid as they seem to be, I would strongly encourage you to get your affairs in order and get out of that company ASAP. It's not worth it.
Or take it for the challenge that it is and rise to the occasion.  I'm willing to bet they're not stupid- they're just technologically ignorant & unwilling to take the time to learn.  You have to sell it to business people, so speak their language.  The right equipment will result in profits for them because productivity increases, blah blah blah.  Constantly losing data will result in losses in revenue, productivity, etc.

---

### Post by CharlesA on 2012-03-30
> **Ms. Daisy said:**
> Or take it for the challenge that it is and rise to the occasion.  I'm willing to bet they're not stupid- they're just technologically ignorant & unwilling to take the time to learn.  You have to sell it to business people, so speak their language.  The right equipment will result in profits for them because productivity increases, blah blah blah.  Constantly losing data will result in losses in revenue, productivity, etc.
+1. It makes a bit of an impression if you are able to do that.

---

### Post by SeijiSensei on 2012-03-31
That was the motivation behind my argument to focus first on the UPS.  Show that you can establish priorities and work within a limited budget.  Develop a plan to upgrade the facilities over the course of a year with each step clearly justified and costed.  In some cases doing nothing, and thus spending nothing, may be the correct way forward.

---

### Post by MisterGaribaldi on 2012-03-31
Ms. Daisy:

I'm sorry, and I hate to be critical, but your attitude on this is what gets people turned into little more than Foxconn-like slaves in a company run incompetently (or, in the OP's case, out-and-out irrationally, if he's to be believed). Why would any sane person want to continue on in that kind of situation?

---

### Post by CharlesA on 2012-03-31
> **SeijiSensei said:**
> That was the motivation behind my argument to focus first on the UPS.  Show that you can establish priorities and work within a limited budget.  Develop a plan to upgrade the facilities over the course of a year with each step clearly justified and costed.  In some cases doing nothing, and thus spending nothing, may be the correct way forward.
Yeah. The UPS would be the #1 thing to get if they are having data corruption after the servers dump due to power outages.

> **MisterGaribaldi said:**
> Ms. Daisy:

I'm sorry, and I hate to be critical, but your attitude on this is what gets people turned into little more than Foxconn-like slaves in a company run incompetently (or, in the OP's case, out-and-out irrationally, if he's to be believed). Why would any sane person want to continue on in that kind of situation?

Depends on the motivation/pay/whatever, I suppose.

But TBH, I don't think pay is the reason for staying if they cannot even afford to get their network infrastructure up to snuff.

---

### Post by MisterGaribaldi on 2012-03-31
> **CharlesA said:**
> Depends on the motivation/pay/whatever, I suppose.

But TBH, I don't think pay is the reason for staying if they cannot even afford to get their network infrastructure up to snuff.

To put a very fine point on it, the OP should have done a lot more investigating of the company before having accepted the position. I can't think of anyone worth a darn who would stay at a company like that one. Assuming the OP is worth a darn, then why would he want to remain, either? Again, how is putting up with "alpha hotels" (which is precisely what these folks would seem to be) good in any way, shape, or form? It doesn't prove one's abilities in IT or Net Admin. From where I sit, if he stays there, it either means he's utterly desperate for money to the point of being broke, or he has absolutely no self-esteem. I would pray neither of those describes him.

If it were me, I would have researched this company before ever stepping foot in their building. Then, if somehow they'd managed to pull the wool over my eyes, after the first scorcher of a meeting, I would tell them they could take the situation and shove it, and I'd walk out on them, even if I didn't have a job, because my own personal dignity and self respect would demand no less.

---

### Post by keithpeter on 2012-03-31
> **MisterGaribaldi said:**
> If it were me, I would have researched this company before ever stepping foot in their building.

Sounds like quite a small company. OP mentions being hired to "help build there website and clean up there network issues". Sounds like a younger person who may have taken the job to get a CV in 'web design'. For many small companies, there is enough money for just a 'computer guy' together with little understanding of the range of tasks that might be involved.

Basically the company management need a little education and some risk analysis, pretty sharpish.

Anyone heard from the OP?

---

### Post by Ms. Daisy on 2012-03-31
> **MisterGaribaldi said:**
> Ms. Daisy:

I'm sorry, and I hate to be critical, but your attitude on this is what gets people turned into little more than Foxconn-like slaves in a company run incompetently (or, in the OP's case, out-and-out irrationally, if he's to be believed). Why would any sane person want to continue on in that kind of situation?
What are you talking about? This would be the exact **opposite** of repetitive mindless assembly-line work. 

Why would anyone work at a place like this? Because they like a challenge?  Because they have to actually use their brain to solve a large problem? Because anyone could succeed in a company with gobs of money at their disposal, but only the best can shine in a place like this? Because if they can convince the management that IT is important then they have become indispensable?

If management is willfully ignorant, then that's a different thing entirely & I would run away screaming.  But if they can be educated, then the challenge would be fun.

---

### Post by MisterGaribaldi on 2012-03-31
> **keithpeter said:**
> Sounds like quite a small company. OP mentions being hired to "help build there website and clean up there network issues".

Size is no excuse for poor attitudes on the part of the ownership/management. It sounds like they have no idea what they're doing or what's going on, and they're willing to beat people up and/or fire them if the world doesn't follow the dictates of their limited, narrow view.

> Sounds like a younger person who may have taken the job to get a CV in 'web design'. For many small companies, there is enough money for just a 'computer guy' together with little understanding of the range of tasks that might be involved.

I've worked for companies of that basic type (not web development-related ones, though) and I speak from experience. They're run by ignorant prima-donnas who want things their way, with no expense and no inconvenience for them, no matter how utterly irrational their wants happen to be.


> **Ms. Daisy said:**
> What are you talking about? This would be the exact **opposite** of repetitive mindless assembly-line work.

I'm talking about being a slave to a company and then being stuck there because the OP (or any other such person) is dependent on them for a paycheck, and/or their own personal identity has become wrapped up in the job they do. That's a very dangerous combination.

> Why would anyone work at a place like this? Because they like a challenge?  Because they have to actually use their brain to solve a large problem?

And, based on the OP's description, this employer is _any_ of these things precisely *how* ?

> Because anyone could succeed in a company with gobs of money at their disposal, but only the best can shine in a place like this? Because if they can convince the management that IT is important then they have become indispensable?

Oh geez, gimmie a break. You can't shine in a company like this, you can only hope to avoid being shot in the back. And frankly, proving that IT is "indispensable" means what, exactly? Turning yourself into an empire builder as well?

> If management is willfully ignorant, then that's a different thing entirely & I would run away screaming.  But if they can be educated, then the challenge would be fun.

Good luck with that, and see how far it gets you in life.

---

### Post by Dangertux on 2012-03-31
I'm in agreement with those saying you should probably start looking around. Honestly, if you're not able to get the job done for what your employer wants the cost to be (free presumably?) then you had better believe they're looking around as well.

Some have mentioned that you should take the time to try to "shine", however realistically, hack jobs and "free solutions" don't always fix problems like this. Sure, if software was outdated etc, there would be some applicable free solutions, but it sounds like the infrastructure itself is degraded to the point of needing replacement. Some things do have a bottom line, and you can only do so much with failing hardware, if they are not willing to consider purchasing replacements it's only a matter of time before it completely fails, and it sounds like they are setting you up for failure by not being reasonable and expecting old hardware to last forever.

I would do the best you  can with what you have and make sure you're talking to as many recruiters/HR departments and whoever else will talk to you about your resume`.

Just my 2 cents.

---

### Post by Ms. Daisy on 2012-03-31
My point is that you're there, so do the best you can for as long as you're there.  I wouldn't sit there and take it while they set me up for failure.  You may as well quit & be unemployed if you're not going to fight.

Everyone with a family & obligations is a slave to the paycheck to a certain extent. It's good advice to always have a back-up plan and have your resume out there, but especially when you're in a doomed job.

---

### Post by knight2000 on 2012-03-31
In the real world you have to improvise. I have a strong suspicion that some of the people in this thread have alot less experience than they are letting on, especially in maintenance for small-medium sized companies. I wouldn't take opinions here too seriously, because you don't know if the people here have any real experience in the field. I have a feeling that at least one person here might still be a student. Knowing about computers or being able to make websites is one thing, but dealing with IT/office politics is something completely different, and every company is different.

---

### Post by Dangertux on 2012-03-31
Seriously? Small businesses can't cough up for a drive to do backups? Or an UPS? Is this business run in someone's garage? 

It's not like it's being suggested that the buy an $80,000+ compellent array here, some leway needs to be given by the employer in this situation. Unless of course OP wants to buy this stuff,  in which case more power to them and they can be the superstar standing in the unemployment line 3 months from now.

Personally I think this employer is being highly unrealistic with their expectations, perhaps a good idea would be to sit down with the management and say "This is what you realistically need." Let them define a budget, but you need to be clear that unless they put some money into it they will not be able to meet their goals. 

Nothing is free, not your man hours nor the parts they need to replace. 

Just my opinion.

---

### Post by MisterGaribaldi on 2012-03-31
> **knight2000 said:**
> In the real world you have to improvise.

Yes, that's absolutely true. Scotty's rule of trying to be a miracle worker is not that far from the truth.

> I have a strong suspicion that some of the people in this thread have alot less experience than they are letting on, especially in maintenance for small-medium sized companies. I wouldn't take opinions here too seriously, because you don't know if the people here have any real experience in the field. I have a feeling that at least one person here might still be a student.

As someone who has no post count yet outside of The Community Cafe, isn't that a bit presumptuous?

> Knowing about computers or being able to make websites is one thing, but dealing with IT/office politics is something completely different, and every company is different.

Office politics are something that exist everywhere. However, I would strongly agree with Dangertux's assessment above. Time, effort, and equipment cost money. Either you're a "for real" company, or you're not.

---

### Post by Dangertux on 2012-04-01
Here's the other thing , if you want to talk about "IT and office politics" we can do that too.

People love to spout off that "Ubuntu revitalized my aging piece of crap $EQUIPMENT" around here.

Now let's talk IT. That's a cute solution for your home file server or personal development web server. However OP is presumably talking about a production network. I use the term production loosely because if OP's management's opinion on productivity is anything like their opinion on asset management I don't think too much happens at this company. Which could be the reason that they don't want to spend money (they're about to tank).

Not to put down the OP, but -- most major/reputable companies don't hire a network engineer to "fix up computers and build websites." That sounds like a mishmosh of job titles and they really wanted "a geeky guy to make everything better and blame when it's not"

That's a farce. You need to get them to cut through the BS and come to a bottom line. If that bottom line is they can't afford it, then they may need to realize that they won't have the ability to have a fileserver/mailserver in the future. Thankfully Google's cloud service offer these at affordable rates on their rather stable infrastructure. 

That being said, there won't be much of a need for OP's position anymore :-/

---

### Post by knight2000 on 2012-04-02
Small companies usually have one 'computer guy' who does multiple roles, larger companies tend to split those roles. You fight with the army you can afford, not what you'd like to be able to afford. Many small companies simply can't afford to have a separate person for each IT role, and if they did have one person in each role there would probably be alot of people sitting around doing nothing. Outsourcing specific tasks is an option, but having things in-house allows a manager to have better control and sometimes stops IT companies from being able to (illegally) sell or pass on systems or data to competitors.

---

### Post by rk0r on 2012-04-02
> **knight2000 said:**
> Small companies usually have one 'computer guy' who does multiple roles, larger companies tend to split those roles. You fight with the army you can afford, not what you'd like to be able to afford. Many small companies simply can't afford to have a separate person for each IT role, and if they did have one person in each role there would probably be alot of people sitting around doing nothing. Outsourcing specific tasks is an option, but having things in-house allows a manager to have better control and sometimes stops IT companies from being able to (illegally) sell or pass on systems or data to competitors.


Not sure what your trying to say with this post ? 

Am i the only one of this thread that thinks the posts have gone way "ott"?!

---

### Post by madverb on 2012-04-02
Start applying for new jobs.
If the retards can't figure out that purchasing new hardware and having everything running efficiently is the way to go, then they aren't going to stay in business.
Seriously... how much money have they paid for recoveries? I bet way more than it would have cost to purchasing a beefy server and virtualise everything.

---

