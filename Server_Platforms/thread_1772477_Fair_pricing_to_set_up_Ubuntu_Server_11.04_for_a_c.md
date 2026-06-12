---
title: "Fair pricing to set up Ubuntu Server 11.04 for a client"
date: 2011-05-31
forum: Server Platforms
---

### Post by nerr on 2011-05-31
Hey everybody, I've had someone approach me recently about setting up an Ubuntu server for his small business.  Having never done this for a paying client before, I have absolutely no idea where to begin as far as pricing goes.  Here are some of the things I've been asked to put together:

Install and configure Ubuntu Server 11.04 with:
- Apache (LAMP)
- Samba
- SSH
- Subversion
- Webmin

As well as configuring mdadm RAID and setting the system up for multi-user access.

For an experienced Linux user like myself, I don't believe that it will take me very long to get things up and running, but again, I have no idea where to even begin as far as pricing goes.

Keep in mind that this client is a small business owner of a game development company with only 5 employees.  I am told that he only has a "modest" budget to work with.  Additionally, it is possible that I will be hired in to this company shortly, to help with game development and to maintain this system which I am setting up.

Advice would be much appreciated!  I would like to use this opportunity to make money, of course, but I also want to be reasonable with the client so that I may be hired in to his company in the coming months for a programming job.

Thanks for your help!

---

### Post by arrrghhh on 2011-05-31
Well it's really up to you... if you feel you can do those things fairly easily, then perhaps a higher hourly rate is in order - after all, he's paying for your knowledge.

If, however, you don't feel so comfortable and think you'll need to do some research... give him a flat price so you can do research and fumble a bit without feeling rushed or like you're ripping the guy off.

I usually ask for $25/hr, depending on what I'm doing.  I have flat rates for other stuff, again it depends on the task really.  I can't say I've ever had anyone offer to pay me to setup a server like this, so I'm probably not the best person to be responding :p.

---

### Post by Lars Noodén on 2011-06-01
I'd skip Webmin if at all possible.  It's just one more thing to break or go wrong, can be hard to set up, and duplicates a subset of the functionality that you have normally through SSH.  An important point to remember is that if the web server is down, then so is webmin, so you will have to know how to do things the right way, regardless of whether you have webmin or not.

That said, I'd second what arrrghhh  said about flat rate vs hourly.  If you need more latitude for learning and experimenting, offer the flat rate.  Prices for labor are usually rather variable and based on the geographical region of the employer and employee.  What are the rates for similar activities in your region?

---

### Post by nerr on 2011-06-01
> **Lars Noodén said:**
> I'd skip Webmin if at all possible.  It's just one more thing to break or go wrong, can be hard to set up, and duplicates a subset of the functionality that you have normally through SSH.  An important point to remember is that if the web server is down, then so is webmin, so you will have to know how to do things the right way, regardless of whether you have webmin or not.

The only issue I foresee with this plan of attack is that the client has expressed interest in being able to easily manage the server himself, and preferably with some form of GUI.  I figure Webmin is probably a better approach for him than a full X environment.  Myself, I am definitely a terminal guy, but I realize that it's not exactly a common mindset anymore.

> **Lars Noodén said:**
> 
That said, I'd second what arrrghhh  said about flat rate vs hourly.  If you need more latitude for learning and experimenting, offer the flat rate.  Prices for labor are usually rather variable and based on the geographical region of the employer and employee.  What are the rates for similar activities in your region?

As far as similar rates go, I am honestly not sure.  I know that a lot of small computer shops around here charge a great deal of money to setup even a basic computer.  I think I'm starting to like the idea of just charging a flat $100 USD, since I have never done server setup for a client before.  It's still 4 hours at $25/hr, but it gives me a little bit of flexibility in case the job takes less time, and my client will feel like his money is better spent this way if it takes me more time.

Any further advice?  Thanks for the help so far!  It is really appreciated!

---

### Post by Lars Noodén on 2011-06-01
Just be sure that he knows that webmin is just a crutch and while suitable for assistants, the real admin has to work in shell.  Shell also gives you all kinds of flexibility as to from where you can work. 

With the flat rate, be sure to define success criteria that you both agree on so that it will not become a moving target.  Then you can make a check list:

1a. web site visible from world
1b. one staff member has successfully made a change to a web page, and can show others

2a. all staff members have svn accounts
2b. one staff member has committed a change, (and can show others)

and so on...

Having clearly defined success criteria will help everyone stay friends.  Put off anything that is not on that check list and summarize it for the next contract.

---

### Post by Lars Noodén on 2011-06-01
Be sure to include time for documentation and/or at least training of one guinea pig.

---

### Post by satanselbow on 2011-06-01
> **nerr said:**
> 

Advice would be much appreciated!  I would like to use this opportunity to make money, of course, but I also want to be reasonable with the client so that I may be hired in to his company in the coming months for a programming job.

Thanks for your help!

As a small business owner he should expect to pay a fair price - if you are looking to keep him sweet with a view to working for him again I would go for a flatprice. Server setups - with the best will in the world - can and do go wrong and can take much longer than expected. By offering a flatprice you will showing that you know what the job is worth and - should things not go you way - you will not be putting in a bill for hours that he might get upset at paying.

Sit down and work out how long each task should take - add a percentage to each task (timewise) for sorting out those little hiccups. Expect the list to get a little longer as you go along - we all L-O-V-E project creep :-# - and work your price out from there - you can also integrate getting paid for your lunch hour while you are there + travel expenses. 

An hourly rate for that sort of job can leave you disappointed (and poor) if you go overtime and don't get paid for the extra hours ;)

Do your homework - script some of the installation tasks in advance if you can and don't go too cheap or he'll expect you to be that cheap everytime :D

Good Luck ;)

***
If you are being expected to provide any hardware 20-30% markup is not unreasonable - justified by the fact that you spent time and effort researching it's suitability for the job - much more and you look greedy 
***

***
Don't forget to negotiate a maintenance contract while you are there ;)
***

---

### Post by satanselbow on 2011-06-01
> **nerr said:**
>   I think I'm starting to like the idea of just charging a flat $100 USD, since I have never done server setup for a client before.  It's still 4 hours at $25/hr, but it gives me a little bit of flexibility


I paid more than that to have my satellite dish bolted to the wall and plugged into the box... 4 hours to get a full server setup sounds a bit hopeful too.

You've got some good info from some experienced guys here - don't forget to let us all know how it goes ;)

---

### Post by ian dobson on 2011-06-01
Hi,

I've installed afew LAMP servers in my time, nothing too special/fancy and would recommend 8 hours for a simple install, abit of training and dealing with small problems.

The last box I setup ended up taking alot longer than expected as the customer requested that I do a data transfer from their old box (which I calculated with 8hours approx.), but they didn't tell me that no one had the admin password for it.

Avoid dealing/supplying the hardware if you can. Just tell them to get a Dell box with the required specs. and lett Dell deal with the hardware problems in the years to come.

Regards
Ian Dobson

---

### Post by spynappels on 2011-06-01
Hi nerr,

Is there a specific reason you are using 11.04? For production servers, I tend to use LTS releases, I'm currently running 10.04.02 LTS on all my production servers, and I only upgraded to that when 10.04.02 became available.

As a general rule, the more users and the more mission critical processes and data, the more stability you should aim for, and normally that means using an LTS release (after it has been out for a few months and has had updates applied to it!).

---

### Post by volkswagner on 2011-06-01
+1 for 10.04 LTS, unless there is something you just can't get without using 11.04.

---

### Post by SeijiSensei on 2011-06-01
Eight hours sounds like a more realistic amount of time, but $25/hour is pretty cheap, at least here in the US.  Remember that you should be including "overhead" in the price you charge your customers.  Most consulting businesses charge something like 4-8X hourly wages when taxes, benefits, and other overhead expenses are factored in.

I don't think you should be charging anything less than $100/hour myself.

Another approach to pricing advocated by an economist friend is to start with your desired annual income, then divide it by 1,000.  On a 2,000 hour annual basis (40 hr/wk X 50 weeks), that gives you a lot of time to devote to uncompensated tasks like marketing, management, and some time off as well.

---

### Post by Lars Noodén on 2011-06-01
> **volkswagner said:**
> +1 for 10.04 LTS, unless there is something you just can't get without using 11.04.

The backports repository should even have many of those things, too.

---

### Post by nerr on 2011-06-01
Wow!  Lots of great advice all-around!  Thank you all so much for your input.  Addressing some various discussions:

The client has already purchased hardware that he wishes to use for this machine.  I tried to steer him toward a decent Dell PowerEdge server that was very affordable, but he ended up buying an old Dimension PC with a dual-core AMD Athlon processor, 2GB of RAM, and two 1TB HDDs.  I should be able to get by, but it's not exactly what he described to me when he first told me what he was going to want.

For those who recommend that I set a clear 'checklist' of goals: I believe this is a great idea.  I will definitely be drafting a list up and speaking to the client before I see him, just to be sure I have my bases covered.  I definitely know what it is like to walk into a project expecting a single task, and then having many others piled on top due to requests.  This should definitely help prevent that.

As far as the version of Ubuntu Server goes, I guess I really have no good reason to run 11.04.  It is what I use on my home server, but I suppose 10.04 LTS is not a bad idea either, especially considering all of the stability fixes and updates which have been released for it by now.  I will likely go with 10.04 LTS to be safe.

Finally, for pricing: Again, I just don't really want to overprice my services with a client who may become a future employer.  I think that a strategy I might push for is a $100 flat-rate fee, and then just ask if he will compensate me for gas and any additional features which he requests once I am actually on-site.

Thanks for all the great advice so far!  Keep it coming!

---

### Post by wlraider70 on 2011-06-01
I don't have any professional bases, but for $100 flat I would have paid you to come set my home server up. At a price that low some people might question if you really know what you are doing.

On the other hand if you are SOOOO good at this that you think $100 is acquitted pay for tiny amount of time you will work on this, you must type REALLY fast.

What happens if you hit a snag you aren't prepared for and it takes twice as long? I think you are selling yourself really short. Would you be happy with $25 an hour 40 hours a week?

---

