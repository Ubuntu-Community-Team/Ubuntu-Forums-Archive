---
title: "Suggest Which Version of Ubuntu"
date: 2016-03-25
forum: Ubuntu, Linux and OS Chat
---

### Post by midhun4 on 2016-03-25
I need to install Ubuntu for my office ,mostly for call centre agents,as of now i have installed 11.10,bt the version is too old i guess,only software they intend to use is TWINKLE,So i want to install a newer version,bt which has to less problematic without updates,pls suggest me a version.

Tnx in advance

---

### Post by Bucky Ball on 2016-03-25
*Thread moved to **Ubuntu, Linux and OS Chat**.*

You want an LTS version and you should stop using 11.10 now. It is not secure, is ancient, and hasn't received updates of any kind for nearly four years. Unsafe and possibly unstable.

14.04 LTS is stable and supported until 2017 and upgradeable any time until then to 16.04 LTS which is released in about a month.

If they're only use one app, or a few, I personally would do a minimal install of 14.04 LTS and add a desktop and just those apps, clone the install and install on every machine. Xubuntu or Lubuntu are also options.

But hard to give a lot of help as there are few specifics about your setup, i.e. the machines you're using and their specs.

If those machines are online, it is good that your first priority is to get them up to date because a call centre full of machine running a four year dead OS is a problem you don't want. Get them offline asap.

Did you have 11.10 on an old disk or did you find it somewhere online?

PS: When you say 'without updates' do you mean 'without upgrades', i.e. to a newer version of Ubuntu? LTS releases have five years support and the rest nine months. If you actually mean updates, they are a required part of keeping a clean, safe working environment and should be done regularly.

---

### Post by v3.xx on 2016-03-25
15.10 is the latest release

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by Bucky Ball on 2016-03-25
> **v3.xx said:**
> 15.10 is the latest release

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Production environment? Might be a stop gap until 16.04 LTS, but I'd still opt for 14.04 LTS. 15.10 has been a little flakey for me, but that's me, but wouldn't go for an interim in a call centre environment personally. Upgrading X amount of machines every nine months? Nightmare. ;)

---

### Post by v3.xx on 2016-03-25
> **Bucky Ball said:**
> Production environment? Might be a stop gap until 16.04 LTS, but I'd still opt for 14.04 LTS. 15.10 has been a little flakey for me, but that's me, but wouldn't go for an interim in a call centre environment personally. Upgrading X amount of machines every nine months? Nightmare. ;)

Just upgrade to 16o4 next month, just like 14o4.

---

### Post by Bucky Ball on 2016-03-25
Yep, so a stop gap until 16.04 LTS ...

---

### Post by v3.xx on 2016-03-25
Its a operating system used by many.  Nothing to do with stop gap.

---

### Post by pauljw on 2016-03-25
I believe 14.04 is supported until 2019 and I would use it until such time as 16.04 has it's major bugs worked out.  If I recall correctly, there are some significant changes being made with 16.04 that some older systems might not play well with.

I agree with Bucky Ball that it's most important to get these systems upgraded to a supported version before serious problems show up.

---

### Post by Bucky Ball on 2016-03-25
> **v3.xx said:**
> Its a operating system used by many.  Nothing to do with stop gap.

The point I'm trying to make is that best to keep production machines on LTS releases. Full stop. 14.04, being supported until 2019, gives the OP plenty of time to swap over. 15.10? Yea, great, go for it, and then upgrade 25, 50, 100 machines in two or three months. Not the best plan for a busy call centre. That's my thinking. Pretty sure I understand yours: 15.10 is the latest version. Makes no diff if these machines are three years old except for the fact it needs to be upgraded in a few months.  

So, let's leave it there and get back on topic, ay? :)

---

### Post by QIII on 2016-03-25
In a production environment, upgrading to a new release costs money.  It has to be installed, tested and deployed.

Installing 15.10 would condemn an enterprise to at the very least yet another round of this in July.  Installing 14.04 would allow for use until 2019 or the opportunity to do it at 16.04 or 18.04.

Using 15.10 would be a costly mistake.

---

### Post by montag dp on 2016-03-25
Or he could install 15.10 and just leave it there for four years after it's EOL like he did with 11.10. Lol. (Just kidding, don't actually do that.)

---

### Post by Bucky Ball on 2016-03-25
> **montag dp said:**
> Or he ...

... or she. Why the presumption every user (and staff member) here is male? :-k

A common misconception.

Anyway, yea. Don't do that. :D

---

### Post by v3.xx on 2016-03-25
> **QIII said:**
> In a production environment, upgrading to a new release costs money.  It has to be installed, tested and deployed.

Installing 15.10 would condemn an enterprise to at the very least yet another round of this in July.  Installing 14.04 would allow for use until 2019 or the opportunity to do it at 16.04 or 18.04.

Using 15.10 would be a costly mistake.

So an upgrade from 14.04 to 16.04 is ok, but to upgrade from 15.10 to 16.04 would condemn an enterprise?  A costly mistake?  I'm not seeing the logic in that.

---

### Post by deadflowr on 2016-03-25
> **v3.xx said:**
> So an upgrade from 14.04 to 16.04 is ok, but to upgrade from 15.10 to 16.04 would condemn an enterprise?  A costly mistake?  I'm not seeing the logic in that.

An upgrade from 14.04 to 16.04 can happen 2 years from now.
Giving the OP time.
An upgrade from 15.10 will need to be done by summer's end.

---

### Post by QIII on 2016-03-25
> **v3.xx said:**
> So an upgrade from 14.04 to 16.04 is ok, but to upgrade from 15.10 to 16.04 would condemn an enterprise?  A costly mistake?  I'm not seeing the logic in that.

Infrastructure in an enterprise is not quite like a computer in the living room or a home network.  You can't fart around for an hour some evening munching Doritos and thumbing through a gaming magazine while you wait for an upgrade to finish.  Changes to enterprise infrastructure can take months to plan and execute -- a company has to pay someone to do that.  There is often re-training that is required across the enterprise.  Someone has to be paid to do the training and every hour of training keeps the employees away from generating revenue.  

Please.  The OP is asking a serious question about critical business systems in the enterprise, not about updating his home computer.  15.10 a mistake for the enterprise?  Yes.  A very, very costly mistake.  Flippantly suggesting that the OP should install 15.10 across an enterprise represents terribly irresponsible advice.

14.04 is available now and supported until 2019.  That gives an enterprise enough time to decide how to approach its plans for future upgrades.  Neither I, nor anyone else, said the OP had to upgrade to 16.04 the day after it comes out.  As a matter of fact, they stay with a supported LTS even if they wait until 18.04 comes out.

---

### Post by mörgæs on 2016-03-26
We can't give advice before knowing the hardware. It't not a given fact that the hardware is well supported by both releases.
Midhun4, about which gear are we talking?

---

### Post by v3.xx on 2016-03-27
> **QIII said:**
> Infrastructure in an enterprise is not quite like a computer in the living room or a home network.  You can't fart around for an hour some evening munching Doritos and thumbing through a gaming magazine while you wait for an upgrade to finish.  Changes to enterprise infrastructure can take months to plan and execute -- a company has to pay someone to do that.  There is often re-training that is required across the enterprise.  Someone has to be paid to do the training and every hour of training keeps the employees away from generating revenue.  

Please.  The OP is asking a serious question about critical business systems in the enterprise, not about updating his home computer.  15.10 a mistake for the enterprise?  Yes.  A very, very costly mistake.  Flippantly suggesting that the OP should install 15.10 across an enterprise represents terribly irresponsible advice.

14.04 is available now and supported until 2019.  That gives an enterprise enough time to decide how to approach its plans for future upgrades.  Neither I, nor anyone else, said the OP had to upgrade to 16.04 the day after it comes out.  As a matter of fact, they stay with a supported LTS even if they wait until 18.04 comes out.

And I recommend 15.10

---

### Post by mörgæs on 2016-03-27
Generally speaking I do the same, but the hardware in question could require something else.

I would not recommend that people skip the bug-reducing iterations 14.10, 15.04 and 15.10. 14.04 is up to date regarding security, not regarding functionality. 

Though, in this case I don't think the difference is that big since we have only heard of Twinkle as a requirement, which probably also runs well in an old environment.

---

### Post by vasa1 on 2016-03-27
> **mörgæs said:**
> We can't give advice before knowing the hardware. It't not a given fact that the hardware is well supported by both releases.
Midhun4, about which gear are we talking?+1. No point going on without OP responding.

---

### Post by midhun4 on 2016-03-29
Thanks all,My hardware is also not much of updated ones,Intel dual core ,with 2 gb Ram ,But yea based on suggestions made by many ,i guess i should go by 14.04,I guess most of u suggested tht itself ,correct me if  I am wrong ,Tnx again mates .

---

### Post by midhun4 on 2016-03-29
> **Bucky Ball said:**
> ... or she. Why the presumption every user (and staff member) here is male? :-k

A common misconception.

Anyway, yea. Don't do that. :D


That might be correct ,But in my case,Its HE!!!!

---

### Post by v3.xx on 2016-03-29
Good show

You will have enough time (till 2019) to decide how to approach future upgrades to your infrastructure.

Don't forget to mark your thread solved.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

):P

---

### Post by deadflowr on 2016-03-29
> **v3.xx said:**
> Good show

You will have enough time (till 2019) to decide how to approach future upgrades to your infrastructure.

Don't forget to mark your thread solved.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

):P

I don't believe that is possible in this sub-forum.

---

### Post by v3.xx on 2016-03-29
> **deadflowr said:**
> I don't believe that is possible in this sub-forum.

oops

---

### Post by midhun4 on 2016-03-29
I have downloaded 14.04 LTS ,Tnx  a lot guys .

---

### Post by Bucky Ball on 2016-03-29
All good. Don't hesitate to post a new thread in a support sub-forum if you have any questions or problems with it or the install. Good luck. :)

---

