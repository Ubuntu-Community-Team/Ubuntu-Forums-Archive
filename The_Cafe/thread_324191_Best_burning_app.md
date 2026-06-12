---
title: "Best burning app??"
date: 2006-12-23
forum: The Cafe
---

### Post by patrickfromspain on 2006-12-23
Yeaaah,I know! Probably that has been discused lots of times... but I'm too lazy to search ;) Also, I want it to be actual...

So, in your opinion what the best cd/dvd burning app out there in linux?

---

### Post by rowanparker on 2006-12-23
K3b

---

### Post by wdo_will on 2006-12-23
I use k3b (and amarok, too), even on Gnome, although I sometimes use Gnomebaker.  They are both great (better than anything on Windows), but I personally think that k3b is better.

---

### Post by patrickfromspain on 2006-12-23
Wow.. seems k3b (which was also my choice) is winning by far...

I find k3b the most complete burning app. Brasero feels too simple to me, I don't like gnomebaker at all (I just don't feel comfortable with it) and nero linux is... not free (paying 20 bucks for it when you have k3b for free is... not for me).

I also use amarok and kaffeine. Three absolutely great kde apps I use in gnome... After downloading the gartoon kde theme, setting all the fonts and doing a "custom" colour scheme for kde all seems quite well integrated ^^

---

### Post by Klaidas on 2006-12-23
Nero Windows ;)
Ok, ok... I prefer Gnomebaker on Ubuntu.

---

### Post by BWF89 on 2006-12-23
K3b

I don't know if anyone heard but K3b is going to be the first (only?) burning app for Linux to have LightScribe support.

[http://www.lacie.com/company/news/news.htm?id=10293](http://www.lacie.com/company/news/news.htm?id=10293)

---

### Post by dbbolton on 2006-12-23
baker

---

### Post by rowanparker on 2006-12-23
> **BWF89 said:**
> K3b

I don't know if anyone heard but K3b is going to be the first (only?) burning app for Linux to have LightScribe support.

[http://www.lacie.com/company/news/news.htm?id=10293](http://www.lacie.com/company/news/news.htm?id=10293)
Won't you need to buy new CD/DVD drives though? And how much wil they cost?

---

### Post by BWF89 on 2006-12-23
> **rowanparker said:**
> Won't you need to buy new CD/DVD drives though? And how much wil they cost?
Yes.

[http://amazon.com/s/ref=sr_nr_i_1/104-7691700-3218353?ie=UTF8&keywords=LightScribe&rh=i%3Aaps%2Ck%3ALightScribe%2Ci%3Acomputers&page=1](http://amazon.com/s/ref=sr_nr_i_1/104-7691700-3218353?ie=UTF8&keywords=LightScribe&rh=i%3Aaps%2Ck%3ALightScribe%2Ci%3Acomputers&page=1)

---

### Post by Artemis3 on 2006-12-23
After my quest for finding the best non k3b burning app, i came to the conclusion this must be Brasero, or growisofs (pretty easy to use directly). GnomeBaker is fine as long as you don't do multisession DVDs. Beware of programs using cdrecord instead of growisofs for this issue.

A word of advise: never ever share a burner with your hard disk on the same ide (pATA) cable, specially not the system/data hard disk. After getting many retry errors, (shared drives on the same pATA can not get commands at the same time) linux will reset the drive, causing the burning app to go nuts and produce a coaster. Also make sure you have DMA enabled with hdparm, Ubuntu does enable DMA by default if it doesn't sees errors at boottime (hint).

PD: For authoring VCD / DVDs, i'm using [tovid](http://tovid.wikia.com/) :)

---

### Post by rowanparker on 2006-12-23
> **BWF89 said:**
> Yes.

[http://amazon.com/s/ref=sr_nr_i_1/104-7691700-3218353?ie=UTF8&keywords=LightScribe&rh=i%3Aaps%2Ck%3ALightScribe%2Ci%3Acomputers&page=1](http://amazon.com/s/ref=sr_nr_i_1/104-7691700-3218353?ie=UTF8&keywords=LightScribe&rh=i%3Aaps%2Ck%3ALightScribe%2Ci%3Acomputers&page=1)
Ah right, that's not too expensive.

But special disks as well?

And how does it work, does it "print" it on or something?

---

### Post by BWF89 on 2006-12-23
> **rowanparker said:**
> And how does it work, does it "print" it on or something?
[http://en.wikipedia.org/wiki/LightScribe#Mode_of_operation](http://en.wikipedia.org/wiki/LightScribe#Mode_of_operation)

---

### Post by Artemis3 on 2006-12-23
Yes, lightscribe is for very lazy people who can't use a soft tip pen and don't mind paying more for the media... Worthless imo.

---

### Post by rowanparker on 2006-12-23
> **Artemis3 said:**
> Yes, lightscribe is for very lazy people who can't use a soft tip pen and don't mind paying more for the media... Worthless imo.

Yeah well, I am lazy :mrgreen:.

> **BWF89 said:**
> 
[http://en.wikipedia.org/wiki/LightSc...e_of_operation](http://en.wikipedia.org/wiki/LightSc...e_of_operation)


Thanks.


It looks alright actually.

---

### Post by mips on 2006-12-23
> **BWF89 said:**
> K3b

I don't know if anyone heard but K3b is going to be the first (only?) burning app for Linux to have LightScribe support.

[http://www.lacie.com/company/news/news.htm?id=10293](http://www.lacie.com/company/news/news.htm?id=10293)

lol, maybe the dev listened to me after all :mrgreen:

---

### Post by bonzodog on 2006-12-23
I'm sorry but you *cannot* beat the sheer raw power of cdrecord on the command line. A lot of these apps are just a front end to it, but, if you want the job done properly, learn the synatx, and do it from the CLI.

---

### Post by Artemis3 on 2006-12-24
You mean Ubuntu's unpatched cdrecord that can't handle multisession DVDs? No thanks.

---

### Post by patrickfromspain on 2006-12-24
well.. maybe you're right, but I prefer k3b. It works just fine for me.. why bother with the CLI then? ;)

Anyway... k3b is winning by far by now..

---

### Post by kuja on 2006-12-24
K3b is great, has anyone else checked out the release candidate? It's pretty nice.

---

### Post by kalikiana on 2006-12-24
I am using Graveman and I love it. :)

---

### Post by bastiegast on 2006-12-24
By no surprise K3B is winning. I love it too although almost always when I want to burn something I drag it to the cd in nautilus  or if its a ISO image I right click on in and select burn to disc. Gnome baker takes care of that, doesn't it?

---

### Post by spockrock on 2006-12-24
k3b wins hands down.

---

### Post by noteforself on 2006-12-24
i use gnome and k3b here.  hopefully, gnome and kde can be closer related in the future.

---

### Post by RAV TUX on 2006-12-24
K3B without a doubt.

(I'm using K3B 0.12.17)

---

### Post by slimdog360 on 2006-12-24
I prefer k3b but Ive heard xcdroast goes off.

---

### Post by mips on 2006-12-24
> **noteforself said:**
> i use gnome and k3b here.  hopefully, gnome and kde can be closer related in the future.

You'd better hope ComplexNumber does not read that :mrgreen:

---

### Post by hoagie on 2006-12-24
I use the default gnome burner that comes with ubuntu. What's its name though?

---

### Post by jdhore on 2006-12-24
i use k3b...it's simple, pretty powerful and pretty easy to use...

---

### Post by AndyCooll on 2006-12-24
I use GNOME and like Gnomebaker, however K3B is quite simply far better at the moment. When I've used Gnomebaker I've found it to be unreliable and trashed more CD's than I'd wish for. K3B seems to burn just about everything (and reliably).

:cool:

---

### Post by patrickfromspain on 2006-12-28
little bump!

---

### Post by shrimphead on 2006-12-28
personally I like Graveman, I would use K3B as it is arguably the most feature rich burning app ever but I don't like having to run kde libs and stuff in Gnome.

I want to like KDE, I really do, I just prefer everything else... but that's another story. maybe when KDE 4 arrives It'll change my mind

---

