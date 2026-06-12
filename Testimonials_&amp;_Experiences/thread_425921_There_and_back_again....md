---
title: "There and back again..."
date: 2007-04-28
forum: Testimonials &amp; Experiences
---

### Post by seetho on 2007-04-28
I started off with Edgy in early February (before that it was Debian, NetBSD and Windows). I wiped Windows off completely from my work notebook.  There were moments of uncertainties that I will suffer from Windows withdrawal symptoms, but as the days went by I found that life was much much much better with Ubuntu.

There's no looking back now.  I can do everything (worth doing) with Ubuntu.  My notebook runs faster and everything just works.

When Feisty came along I upgraded and found it even better, except that one thing very critical to me stop working, i.e. suspend and hibernate.  I use an old IBM Thinkpad X31 and all was working fine under Edgy.  I tried to fix it by following some of the threads in this forum but I just couldn't get it to work.  My notebook would go into suspend and hibernate but I'm not able to bring it back to life.

Suspend and Hibernate features are critical to me.  I normally travel and have to work on batteries so shuting down all the time is not an option.

Yesterday I did a clean reinstall of Dapper on my notebook and I'm glad to report that everything is working again.  It's an LTS with updates until 2009, so I think I'll stick to this one until the next LTS comes along.

Thank you to the open source community for such a great piece of work.

---

### Post by seetho on 2007-07-03
I'm back again!  It's been 5 months exactly since I dumped Windows XP from my work notebook and installed Ubuntu.  I'm currently using 6.06 LTS on it.  I must say that it is not as stable as you would expect it to be.  It does crash on me occasionally.  I found that Firefox and OO can cause the whole system to lockup sometimes.  Nevertheless I still find Ubuntu much more satisfying and easier to use (now that I'm used to it) than Windows XP.

In the mean time I had another notebook at home which I installed Feisty for testing purposes.  It was very flaky during the first weeks of its release but it seems to have become a lot more stable - even more that my 6.06 LTS!

So where to now?...

I actually quit my previous job this January (after almost a decade with them) and joined two other friends as a partner in a new (1 year old) startup dealing in industrial instruments.  Company administration now falls under my care.  This also includes IT infrastructure!  So now I have the perfect opportunity to make use of Linux (Ubuntu) and OSS for a complete small business environment, and at the same time be able to document it here for the benefit of others should they decide to adopt the same path as I am about to embark on.  I officially join the company fulltime this month (July), so it is only just begining.

So far I have placed our e-mail and web hosting services in a hosting company that runs Linux servers.  In fact I did this sometime last year.  Only this year did I have time to start working on our website.  I used the simple [PmWiki]("http://www.pmwiki.org") tools to build our website.  Nothing fancy but the nice things it that I or anyone else in the company can update the site from anywhere.

Others in the company are die-hard Windows user so it will take a while to get them to change.  I do not want to force anyone since it will have a negative impact on productivity.  What I plan to do is to implement Ubuntu in the background.  The first being the file server.

So far I have only made test on having an SSH server on my home PC and then using SSH to connect back from anywhere using my notebook to access files on my home PC and also to backup my notebook using rsync.  I found SSH and rsync to be very useful indeed to this purpose.  I learned most of it from this [site]("http://www.suso.org/docs/shell/ssh.sdf").

My plan now is to put a Samba server in my office.  I will then configure SSH and rsync to periodically backup this server to my home PC (perhaps at night).  We will then have automatic off-site backup every single day.    I'll probably do this over the next couple of weeks in between my other responsibilities in the company.

I'll write back here with the results.

---

### Post by freebeer on 2007-07-03
Cool.  I look forward to your future posts.

I'm in a similar boat as yourself.  (Running the IT side of a small business.)  I've turned to the Ubuntu world partly to learn a bit about it, but mostly to investigate what it can offer a small business.  I really haven't implemented the "big migration" stuff (such as a Samba Server, running as a domain controller, etc.) but I've been playing with it on a test machine.  So far so good.  I've also set up an FTP server which is working well.  It allows my geographically dispersed people to collaborate on documents a lot easier that one can do through email (sometimes email file limit sizes can bite you).

---

### Post by seetho on 2007-07-03
Feel free to post your experiences too.  I'm sure there are many more others out there trying to use Ubuntu in a small business environment, and we can certainly learn from each other.  I'm no Linux guru by any stretch of the imagination, but I do believe that you can only achieve something if you dare to try new things.

---

### Post by freebeer on 2007-07-03
Yup... agreed.  I had always planned on posting a kind of "Executive Summary" of what I was (eventually) able to achieve.  I just haven't had as much time to work on it as I'd like (and I'm still dealing with the learning curve.)

Why doesn't somebody just give me a million dollars, so I can put RL aside for a while so I can get some work done!  :D

---

