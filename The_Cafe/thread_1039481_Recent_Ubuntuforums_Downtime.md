---
title: "Recent Ubuntuforums Downtime"
date: 2009-01-14
forum: The Cafe
---

### Post by ubuntu-geek on 2009-01-14
This was posted on my blog which will hit the [planet]("http://planet.ubuntu.com") soon, but wanted you all to know as well.

> 
I just wanted to take a few minutes and comment on some of the recent issues we’ve had over at the UbuntuForums. Last week Thursday around 4pm EST, our main database server went into a “crashed” state. The result of this state was over 2000 queries that were lingering without completion for over 8000 seconds which resulted in resource issues, this caused the mysqld process to go into an unresponsive state and would not shutdown effectively. After the crash it was realized we had some inconsistent data in the database and a check/repair was ran to potentially correct the issues.

On Sunday evening around 11:30pm EST the forums were down again but this time with table corruption on our largest tables which is our post table (it has around 6.5 million rows) and the thread table (over 1 million rows). I’m assuming everything “wasn’t” ok, after the crash on Thursday even though the checks said they were. Monday was spent cleaning up the tables, fixing corruption issues etc. Unfortunately, because of the massive size of our tables a check and repair takes upwards of 4-5 hours per check and repair until the issues were mostly resolved, this had to be completed a few times. We’ll be monitoring the data integrity over the next couple days to ensure everything stays consistent.

When the forums were ready to come online last night around 7pm EST, we ran into issues with the amount of traffic the site was getting (benefits of being popular eh?). To help ease the pressure on our main database server we have utilized the “slave” feature in vbulletin which will send queries to a slave server to help reduce load on the master. So far this has been working pretty well except for a few hiccups which were easily corrected by changing mySQL variables.

James Troup from Canonical was a great help making sure the proxies were stable last night and will be getting us additional hardware to help with our explosive growth as we have outgrown our current servers. James, thank you for your help, it is appreciated.

Until things stable out we have disabled a couple of popular features on the forums namely the “Thank you” and the “Solved Post” features. We hope to re-enable them again soon. I expect we’ll have a some rough patches ahead of us until the new hardware is in place and we look forward to getting things more stable in the near future. We’ll also be implementing a better method of communication to our users when the forums are offline, expect an announcement on the forums in the near future about that. We appreciate everyones patience during this time.


---

### Post by Elfy on 2009-01-14
thanks for letting us know - I for one appreciate what you do :)

---

### Post by notwen on 2009-01-14
Good to hear.  Certainly been missing the forums throughout my slower times at work. =]  Here's to hoping you get the needed hardware and get everything back up & running as should be soon.  *cheers*

---

### Post by drubin on 2009-01-14
Thanks again for your hard work on this regard.

---

### Post by Sealbhach on 2009-01-14
Yay new hardware. The forums have been generally slow and unresponsive for as long as I've been using them so more hardware is a great thing. Thanks!


.

---

### Post by Joeb454 on 2009-01-14
First off, thanks to U-G (and James over at Canonical), for managing to minimize the downtime :)

Secondly, as I think this is going to be popular for the next couple of days, I've stuck the thread

---

### Post by Favux on 2009-01-14
Hi Ubuntu-geek,

Thank you for your hard work.  And all the forum work you do.  Hopefully soon I'll be able to "thank you"

---

### Post by matthew on 2009-01-14
Thank you, ubuntu-geek, and thank you, James, Canonical, etc.

---

### Post by talsemgeest on 2009-01-14
Thank you so much ubuntu-geek and James for all the hard work you guys have put in.

---

### Post by chucky chuckaluck on 2009-01-14
whatever any of that means. get well soon. :guitar:

---

### Post by Rocket2DMn on 2009-01-14
Thanks u-g and Canonical folks!  Your efforts are appreciated by so many people.  Rock on!
:guitar:

---

### Post by Nano Geek on 2009-01-14
Thanks for all the hard work trying to keeps the forums together. :)

---

### Post by Tom Mann on 2009-01-14
> **talsemgeest said:**
> Thank you so much ubuntu-geek and James for all the hard work you guys have put in.

Seconded, Thirded and Forthed. You guys rock! Have a star :KS

---

### Post by sstusick on 2009-01-14
> **talsemgeest said:**
> thank you so much ubuntu-geek and james for all the hard work you guys have put in.
+1

---

### Post by cardinals_fan on 2009-01-14
Thank you for the info.  Keep us up to date!

---

### Post by Thelasko on 2009-01-14
Thanks for all of the hard work!

---

### Post by Dr Small on 2009-01-14
I just found this thread (I don't visit the Cafe often, nor do I look at Stickies!!). I just wanted to say a big THANK-YOU for getting the forums back up. This is my favorite and most helpful spot on the Internet, and I love helping out (even though that does mean I am hurting the database even worse :p).

Thanks for keeping us up, and sorting out the issues! :)

---

### Post by Vadi on 2009-01-14
Thanks for explaining what happened and letting us know the communication will be improved.

---

### Post by Skripka on 2009-01-14
Great work, thank you, now kick back and have several nice beers. :)

---

### Post by samjh on 2009-01-14
Thank you all for your hard work, and for letting us lowly users know what's been going on. :)

---

### Post by sydbat on 2009-01-14
Thanks U-G!! I think alot of us were going through withdrawal...

---

### Post by snova on 2009-01-14
Many thanks for fixing it!

More for the (interesting) detailed explanation.

---

### Post by irishdunn on 2009-01-14
Thanks for your effort in this, didn't realise how much I use the site until it went down.

---

### Post by -grubby on 2009-01-14
The explanation and help is appreciated. I was wondering where thanks went, now I understand ;)

---

### Post by 5BallJuggler on 2009-01-14
Thanks very much from the UK

---

### Post by cprofitt on 2009-01-14
<humor>

I can not believe we need new hardware... heck I can't see why anyone would need more than 640K.

</humor>

Seriously U-G - thanks. Having had my shared of tech emergencies turned nightmare (three disks on a raid 5 scsi attached storage device going at the same time is painful) I can truly appreciate what you went through and what it took to get it all back.

---

### Post by phrostbyte on 2009-01-14
Well at least this is a sign that Ubuntu Forums is growing. :P

Oh and thank you ubuntu-geek for your nice pleasant looking avatar. Since so many other people were thanking you for other things I have to complement something different. I really like your avatar. (Not being sarcastic.)

---

### Post by ghindo on 2009-01-14
> **irishdunn said:**
> Thanks for your effort in this, didn't realise how much I use the site until it went down.Ditto for me.

---

### Post by BGFG on 2009-01-15
Echoing Thanks, many of us have spent a sleepless night or two in server rooms waiting on database checks and if we could, we'd 'tag in' for you. 
Sincere thanks for all your efforts. Hope the database stops screwing around :)

Reynaldo.

---

### Post by sharathpaps on 2009-01-15
Thank You ubuntugeek and James and everyone at Canonical who work so hard purely for their belief of what Ubuntu & FOSS stand for..

I salute your Ubuntu....

Ubuntu forums has become a staple in my day to day life...

---

### Post by Scruffynerf on 2009-01-15
Just another thanks for letting us know.

As an aside... MySQL for the  backend of a site this large? Heck, even one of the lead devs has blogged panning MySQL.  I'm a bit surprised that PostGreSQL isn't being used. It is supposed to be a lot more stable with larger data sets.

---

### Post by Partyboi2 on 2009-01-15
Thanks ubuntu-geek for all your hard work and dedication to the Ubuntu forums.

---

### Post by halovivek on 2009-01-15
Thank you so much.

---

### Post by darrenn on 2009-01-15
Why didn't that lady simply call a computer tech? He could have put windows back on her computer in less than a hour. But that article sounds like a total sham anyway.

---

### Post by Joeb454 on 2009-01-15
> **darrenn said:**
> Why didn't that lady simply call a computer tech? He could have put windows back on her computer in less than a hour. But that article sounds like a total sham anyway.

Wrong Thread? :p

---

### Post by smartboyathome on 2009-01-15
UG, you deserve a beer. :KS

---

### Post by perlluver on 2009-01-15
> **smartboyathome said:**
> UG, you deserve a beer. :KS

+1 to that, good work guys, keep it up.

---

### Post by Dragonbite on 2009-01-15
Thank you for all of your hard work and long hours!

The sheer number of members and the heavy load on the servers should tell you that this is a very popular forum and you can pride in that!

---

### Post by jbelmonte on 2009-01-15
Thanks U-G and James. These forums are invaluable.

---

### Post by Joeb454 on 2009-01-15
> **jbelmonte said:**
> Thanks U-G and James. These forums are invaluable.

If we think we have found some bad data in the forums, how should we report it? I believe there is a problem with [http://ubuntuforums.org/showthread.php?t=1033697](http://ubuntuforums.org/showthread.php?t=1033697)

Thanks, I've informed the admins :)

---

### Post by sanderella on 2009-01-15
Thank you for all your hard work. Much appreciated.:KS

---

### Post by eragon100 on 2009-01-15
Thanx for all the volunteer effort you have put in ! :popcorn:

---

### Post by Slug71 on 2009-01-15
I'm still getting, '502 Proxy Error and Service Temporarily Unavailable' pages a lot.

---

### Post by jbelmonte on 2009-01-15
Are you accepting donations to help defray the cost of the new hardware?

---

### Post by solitaire on 2009-01-15
> **Slug71 said:**
> I'm still getting, '502 Proxy Error and Service Temporarily Unavailable' pages a lot.
  I'm getting a lot of 503 errors
> 
**Proxy Error**

 The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request *[GET /search.php]("http://ubuntuforums.org/search.php")*.
 Reason: **Error reading from remote server**
  Apache/2.2.8 (Ubuntu) Server at ubuntuforums.org Port 80


---

### Post by Sunspore on 2009-01-15
Thank you for making all this possible and making this one the best online forum I have ever visited.

Keep up the good work.

Cheerz!!!

---

### Post by ubuntu-freak on 2009-01-15
Thanks for the very detailed explaination ubuntu-geek, and thanks for all the hard work you put in - I don't envy you. I'm betting this forum has grown bigger than you ever thought it would.

---

### Post by deepclutch on 2009-01-16
for a second ,I dreamt your servers were hacked :P

---

### Post by FuturePilot on 2009-01-17
Thanks to all who put their hard work into fixing the forums up. :KS

---

### Post by billgoldberg on 2009-01-17
I hope you guys sort things out, because the errors and downtime isn't good for the reputation of Ubuntu.

---

### Post by Kaneda187 on 2009-01-17
Keep it up! good job! missed it when it was down though!

---

### Post by Old_Grey_Wolf on 2009-01-17
> **jbelmonte said:**
> are you accepting donations to help defray the cost of the new hardware?

+1

---

### Post by handy on 2009-01-17
> **jbelmonte said:**
> Are you accepting donations to help defray the cost of the new hardware?

I believe that donations & advertising revenue is most definitely accepted:

*_[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)_*

---

### Post by Joeb454 on 2009-01-17
> **handy said:**
> I believe that donations & advertising revenue is most definitely accepted:

*_[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)_*

You are aware that isn't actually ubuntu-geek's website? :)

---

### Post by handy on 2009-01-17
> **Joeb454 said:**
> You are aware that isn't actually ubuntu-geek's website? :)

Oops, I got his twin! :lolflag:

What is the URL for his site?

---

### Post by talsemgeest on 2009-01-17
> **handy said:**
> Oops, I got his twin! :lolflag:

What is the URL for his site?
I believe [this](http://moxiefoxtrot.com/) is it.

---

### Post by matthew on 2009-01-17
> **talsemgeest said:**
> I believe [this]("http://moxiefoxtrot.com/") is it.
Yeah, that's the real one. The other guy just has the same name.

---

### Post by handy on 2009-01-18
> **talsemgeest said:**
> I believe [this](http://moxiefoxtrot.com/) is it.

> **matthew said:**
> Yeah, that's the real one. The other guy just has the same name.

Thanks for setting me straight on that one. :-)

---

### Post by ShirishAg75 on 2009-01-18
Any idea when the new hardware would be put into service?

Also it would be good to know about the comment about postgreSQL vs MySQL which somebody made, commenting that PostgreSQL fairing better with larger data sets. 

IIRC PostgreSQL also is better with open-source forum software, although dunno about their scalability.

---

### Post by -kg- on 2009-01-18
I will add my thanks to UG and everyone involved.  I most certainly missed the Forums while they were down and it's great to see them back up.

Great job!

---

### Post by smilingfrog on 2009-01-19
I miss the thanks feature! So I'm going to post here instead. Thanks.

---

### Post by aceinthenight on 2009-01-19
Ubuntu is so stable lol...

---

### Post by jenkinbr on 2009-01-20
At least the forums are running smoothly again.

---

### Post by night_fox on 2009-01-20
Thankyou ubuntu-geek for sortin out the forums from their downtime. Much appreciated by everyone on the forums.

---

### Post by Benic on 2009-01-21
Thank you guys! Ubuntu forums rock! I just wouldn't make it without a little help from my fellow Ubuntu users.

Keep up the good work!

---

### Post by deadmnky on 2009-01-21
thank you for all your hard work everyone. always much appreciated.

---

### Post by Joeb454 on 2009-01-25
With the original post of this thread over 1 week old, and the last activity 3 days prior to this post, I'm unsticking this thread (as I mentioned in a recent thread in Forum Feedback & Help

---

### Post by sancho panza on 2009-01-27
I'd like to thank the poster for this thread...where is the button for that? Oops nevermind :P

---

### Post by namdung on 2009-02-05
Hopefully the forum will be back to 100% functionality soon. I was lost for a while with the forums.

The Ubuntu version mentioned below the avatar was much needed. When was this feature added?

Really appreciate all the hard work that goes behind keeping this great forum running.

Edit: My signature makes no sense for now ;-)

---

### Post by dunomous on 2009-02-11
I can't wait until this is brought back up, either. Although, I must say, I really do appreciate all the hard work that goes on to keep these forums operable!!

---

### Post by Vince4Amy on 2009-02-11
> The Ubuntu version mentioned below the avatar was much needed. When was this feature added?


It was readded, it used to be on here when the mini profiles of the users were at the top of each post, I preferred that.

---

### Post by FuturePilot on 2009-02-11
> **Vince4Amy said:**
> It was readded, it used to be on here when the mini profiles of the users were at the top of each post, I preferred that.

That option has also been readded.

---

### Post by expelledboy on 2009-06-27
You mentioned that you **werent** going to bring back the "*thank you*" feature.. and I was about to go and start a thread that basically said I would write more howtos here, instead of elsewhere, if this feature was added. I had no idea it had been removed! :P

---

