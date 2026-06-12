---
title: "Leased line advice"
date: 2006-03-23
forum: The Cafe
---

### Post by Swab on 2006-03-23
Hi,

Just wondering if anyone has any experience of purchasing a leased line in the UK.  

I am currently trying to convince my boss that we need a leased line, she is sold on the advantages it would bring but doesn't like the price (several quotes of around £1500 installation plus £7000 per year).

Is there anyone here who knows of a provider offering decent service at a lower price?  I'm sure these providers exist, but I just can't find them!

Any and all input appreciated.

---

### Post by mips on 2006-03-23
Who quoted that price ?

What speed/bandwidth are you looking at ?

Do you need symetrical bandwidth where your up/down speeds are the same. For normal internet usage asymetrical services like ADSL will suffice seeing it is suited to the nature of internet traffic. If you are gonna upload as much as you download then a symetrical service would be required. Leased lines also come with local/international ratios concerning your traffic. Usually also included is a SLA of some sorts.

I'm sure one of the ADSL2(+) services would suffice but then again I don't know your exact needs. Maybe elaborate a bit more on usage type/staff numbers/own mail&web servers etc. We need to know a bit more about your company, why this is required and what your plans are. A symmetrical leased line might not be an ideal solution and cost your company an arm and a leg. If you could still reach your goal and spend less your boss would be much more impressed :)

[http://www.google.co.za/search?client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial_s&hl=en&q=Leased+line+providers+in+Glasgow&meta=&btnG=Google+Search](http://www.google.co.za/search?client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial_s&hl=en&q=Leased+line+providers+in+Glasgow&meta=&btnG=Google+Search)

---

### Post by Swab on 2006-03-23
Quotes from BT, Biscit, and others.

The company comprises a small primary school and nursery, as well as a childcare training organisation.  We only have one site.   

Currently we are developing 2 web sites, 1 for the school, and the other for the training organisation.  We are also developing a web based system allowing teachers to edit reports from home, and allow parents to download those reports in pdf format.   In the future we would like something along the lines of schooltool or moodle to facilitate communication between staff, teachers, and parents. 

So, at the moment all of this is hosted by a third party, who are proving to be unreliable (lots of downtime, upgraded PHP version without bothering to tell us).  My proposed solution is a 2Mb symetrical leased line.

ADSL2 and SDSL are not available in our area at this time, and doesn't look like this will change any time soon.

---

### Post by Trel on 2006-03-23
Look into local (local to your country.. not city) colocation via companies in Telehouse or Redbus datacenters in the UK. Setting up your own connection can cost quite a bit (as you've found out) while colocating can provide you with a superior connection with better peering and redundancy not to mention redundant power and everything else.

The only cost then would be monthly fees associated with your colocation and the cost of the physical server hardware itself.

---

### Post by Swab on 2006-03-23
[QUOTE=Trel]Look into local (local to your country.. not city) colocation via companies in Telehouse or Redbus datacenters in the UK. Setting up your own connection can cost quite a bit (as you've found out) while colocating can provide you with a superior connection with better peering and redundancy not to mention redundant power and everything else.

The only cost then would be monthly fees associated with your colocation and the cost of the physical server hardware itself.[/QUOTE]

I have thought about colocation also, but there was not much difference in price to be honest.  Quotes for 1u with 2Mb were around £6,000, plus a trip to London to install.

---

### Post by Trel on 2006-03-23
Did you talk to someone that is colocating a large number of servers in the datacentre or directly with the datacentre?

---

### Post by mips on 2006-03-23
I honestly don't believe you will see much variation in price for a leased line as most companies probably make use of BT's infrastructure. The other thing is you will have to either invest in a proper router (Cisco) or lease/rent one which is going to add to the cost.

Try this maybe,
[http://www.bt.com/broadband/moreinfo/](http://www.bt.com/broadband/moreinfo/)
javascript:popUp('http://www.adslchecker.bt.com/pls/sdsl/sdslchecker.welcome?ms=E&version=2&URL=eco.btwholesale.com/broadband1/checker/sdsldecision.asp',530,480);

Or alternatively look into a new hosting provider that can provide you with a SLA.

---

### Post by Swab on 2006-03-23
[QUOTE=mips]I honestly don't believe you will see much variation in price for a leased line as most companies probably make use of BT's infrastructure. The other thing is you will have to either invest in a proper router (Cisco) or lease/rent one which is going to add to the cost.

Try this maybe,
[http://www.bt.com/broadband/moreinfo/](http://www.bt.com/broadband/moreinfo/)
javascript:popUp('http://www.adslchecker.bt.com/pls/sdsl/sdslchecker.welcome?ms=E&version=2&URL=eco.btwholesale.com/broadband1/checker/sdsldecision.asp',530,480);

Or alternatively look into a new hosting provider that can provide you with a SLA.[/QUOTE]

Do you think I might get by with a slower leased line?  Prices do fall sharply for 1Mb or 512Kb ... I would imagine the web sites would only have casual visitors, and tthe primary school only has 100 pupils, so it's not as if parents will be logging in all the time.

Thanks for the replies by the way.

---

### Post by shamrock_uk on 2006-03-23
Not an expert in this area, but really I can't imagine why 1Mb wouldn't be more than enough for your purposes. 

Hope you find a solution soon!

---

### Post by Trel on 2006-03-23
Talk to Adam at [http://www.iracks.com/](http://www.iracks.com/)

They operate servers all over Europe and can definitely help you with better pricing than £6000.

---

