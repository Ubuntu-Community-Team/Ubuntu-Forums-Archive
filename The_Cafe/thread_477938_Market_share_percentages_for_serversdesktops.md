---
title: "Market share percentages for servers/desktops?"
date: 2007-06-18
forum: The Cafe
---

### Post by Bluecircle on 2007-06-18
Hello, I'm trying to find up to date statistics on market share percentages for Linux, BSD, Novel Netware, OSX, and Windows. I want to know the market share (percent of total servers) held by each OS on servers. Does anyone know where I can find this? A quick Google search wasn't too productive.

---

### Post by tanelt on 2007-06-18
[Operating System Market Share for May, 2007](http://marketshare.hitslink.com/report.aspx?qprid=2&qptimeframe=M&qpsp=100)

**Windows XP            82.02% **
Windows 2000 	        4.31% 
Mac OS 	                      3.95% 
Windows Vista 	          3.74% 
MacIntel 	              2.51% 
Windows 98 	          1.24% 
**Linux 	                0.70% **
Windows NT 	           0.69% 
Windows ME 	          0.62% 
Unknown 	           0.05%

---

### Post by Bloch on 2007-06-18
What do the figures refer to? 
Usually market share means the percentage of total sales. This becomes problematic when we're talking about a free operating system (as some versions of linux are).

A more concrete figure, and easier to determine, would be the percentages of various OS's hitting a major website over a month.

---

### Post by Extreme Coder on 2007-06-18
> **tanelt said:**
> [Operating System Market Share for May, 2007](http://marketshare.hitslink.com/report.aspx?qprid=2&qptimeframe=M&qpsp=100)

**Windows XP            82.02% **
Windows 2000 	        4.31% 
Mac OS 	                      3.95% 
Windows Vista 	          3.74% 
MacIntel 	              2.51% 
Windows 98 	          1.24% 
**Linux 	                0.70% **
Windows NT 	           0.69% 
Windows ME 	          0.62% 
Unknown 	           0.05%
This is refering to how many are SOLD, right?
It isn't exactly accurate then :/

---

### Post by tanelt on 2007-06-18
This has nothing to do with sales. Read the "Help" page there.

> This data provides valuable insight into significant trends for internet usage. These statistics include monthly information on key statistics such as browser trends (e.g. Internet Explorer vs. Firefox market share), search engine referral data (e.g. Yahoo vs. MSN vs. Google traffic market share) and operating system share.

We use a unique methodology for collecting this data. We collect data from the browsers of site visitors to our exclusive on demand network of small to medium enterprise live stats customers. The sample size for these sites is more than 40,000 urls. The information published is an aggregate of the data from this network of hosted website statistics. The site unique visitor and referral information is summarized on a monthly basis.

In addition, we classify 300+ referral sources identified as a search engine. Aggregate traffic referrals from these engines are summarized and reported monthly. The statistics for search engines include both organic and sponsored referrals. The websites in our population represent dozens of countries in regions including North America, South America, Western Europe, Australia / Pacific Rim and Parts of Asia. Users should note that no double byte search engines are included in the search engine referral population.

The data is made available free of charge on a monthly basis that includes monthly browser market share trends, top search engine referrals, and operating systems trends.

---

### Post by Ultra Magnus on 2007-06-18
So there are more Mac servers than Linux servers - I really doubt that - seriously that just doesn't seem realistic - all the largest server farms use Linux - think google, DOD etc - This data is seriously flawed

edited - sorry just realised this is for desktop OS - although i've read in numerous places that linux has a greater desktop market share than mac so I'm still sceptical

---

### Post by tanelt on 2007-06-18
On the servers, however, Apache shows its power.

[http://news.netcraft.com/archives/web_server_survey.html](http://news.netcraft.com/archives/web_server_survey.html)

Apache   53.76%
Microsoft 31.83%

---

### Post by starcraft.man on 2007-06-18
Interesting. However like every other sampling survey/poll for anything else it isn't a completely accurate barometer of anything (there isn't any system with an acceptable accuracy for me, I ignore them all). For instance I'd like to know the actual sites they aggregate from, if their just a bunch of unimportant corporate/government sites it doesn't mean much if anything to me.

Oh and those numbers most certainly do not reflect servers, which would place linux over 60-70% (if not more) I believe out of the top 500 and general server use (don't remember site I read it off). In any case, I find it laughable that 2k beats Vista's install by enough of a margin :p.

In closing though, I couldn't care less what the rest of the desktop market uses. I use what I find to be best. I don't really see why what all those other users do is of any importance to me or anyone here (including OP, I don't know why he wants to know). If 100 people I knew jumped into the freezing st. Lawrence [(link)]("http://en.wikipedia.org/wiki/St._Lawrence_River") (a Canadian river), I wouldn't. Thats what I think of it anyway.

Edit: Bleh, another survey posted by tanelt...

---

### Post by Bluecircle on 2007-06-18
Ok, I guess I wasn't clear. I'm not referring to market share as sales, but as what percentage of all servers are running Linux, BSD, Windows etc. 

Tanelt: Thanks, but it specifies Apache vs. Windows, Apache doesn't neccesarily mean it's running Linux right?

Basically what I'm looking for is what percentage of servers run what OS. If possible, a study of ALL servers, and also one just of web servers.

---

### Post by tanelt on 2007-06-19
Well, remote users can't really tell the difference.

An Apache could mean that the box could be running basically any flavor of *nix or maybe on Windows inside a virtual machine or with Cygwin.
Microsoft IIS could mean it's a Windows box or a Linux box running a virtual honeypot that's identified as a Windows box to draw attention or it could be identified as BSD box or whatever the admin likes. So there's no way you can be sure what it's actually running.

---

### Post by Bloch on 2007-06-19
> I don't really see why what all those other users do is of any importance to me or anyone here (including OP, I don't know why he wants to know)

Gosh, that's a bit defensive!  Is it suspicious behaviour to ask?

I'm sure the figure is important to many commercial sites, hardware manufacturers (who don't bother to print "Linux compatible" even when it is, computer resellers, anyone interested in IT.

The most important statistic on consumer use - the one most relevant to e-commerce - is actually the easiest to determine. That is, the percentages online at any one moment.

It will vary from country to country and from website to website, but the figure e.g. for google.de or google.uk if they released it, would be a concrete figure that means something in itself.

On the site I am webmaster for the stats are:
	Windows		113580	80.2 %
	Macintosh	17641	 12.4 %
	Unknown		7664	  5.4 %
	Linux	           2721	       1.9 %


The "Unknown" is huge, but I'm sure that's the fault of the crappy stats software on my hosting service.

Any more webmasters who can give us stats?

---

### Post by Bluecircle on 2007-06-19
I'm looking for what the servers are running, not the end users.

---

### Post by karellen on 2007-06-19
> **Bluecircle said:**
> I'm looking for what the servers are running, not the end users.

Linux (the vast majority) and MS Windows Server 2003 (the rest of them)

---

### Post by cunawarit on 2007-06-19
> **Bloch said:**
> Any more webmasters who can give us stats?

Stat's for the 14th on one site:

Operating System 	Hits 	Visitors 	% of Total Visitors
1 	Windows XP 	211,699 	6,896 	**84.72%**
2 	Windows Vista 	15,438 	565 	**6.94%**
3 	Windows 2000 	15,561 	362 	**4.45%**
4 	Mac OS 	2,102 	94 	**1.15%**
5 	Windows ME 	2,096 	66 	**0.81%**
6 	Others 	152 	  59 	**0.72%**
7 	Windows 98 	 1,360 	48 	**0.59%**
8 	Windows Server 2003 	629 	21 	**0.26%**
9 	Windows NT 	320 	16 	**0.20%**
10 	Linux 	124 	7 	**0.09%**
11 	HP Unix 	7 	3 	**0.04%**
12 	Windows 95 	63 	3 	**0.04%**
	Total 	249,551 	8,140 	100.00%

I'd discount the Windows 2003 numbers, that's probably mostly us in the office... The numbers for non-Windows machines are low, probably largely to the advertising campaigns though, I guess we target sites mostly used by Windows people.

PS:

Last five days:

Operating System 	Hits 	Visitors 	% of Total Visitors
1 	Windows XP 	564,829 	20,322 	**82.44%**
2 	Windows Vista 	44,088 	1,653 	**6.71%**
3 	Windows 2000 	73,597 	1,203 	**4.88%**
4 	Mac OS 	11,765 	423 	**1.72%**
5 	Others 	1,438 	396 	**1.61%**
6 	Windows 98 	6,487 	274 	**1.11%**
7 	Windows ME 	4,751 	176 	**0.71%**
8 	Windows NT 	1,715 	76 	**0.31%**
9 	Windows Server 2003 	1,546 	54 	**0.22%**
10 	Linux 	1,019 	48 	**0.19%**
11 	Windows 95 	428 	18 	**0.07%**
12 	HP Unix 	372 	8 	**0.03%**
13 	Windows CE 	52 	1 	**0.00%**

---

### Post by Bluecircle on 2007-06-19
> **karellen said:**
> Linux (the vast majority) and MS Windows Server 2003 (the rest of them)

Yeah that's what I figured, but I can't find any good numbers. What about BSD (Or are you grouping that with Linux)?

---

### Post by ssam on 2007-06-19
there is not really any way of getting good stats from everybody in the world. you will have look at data from a range of sources. another source would be

[http://www.w3schools.com/browsers/browsers_os.asp](http://www.w3schools.com/browsers/browsers_os.asp) though it will mostly represent web programmers.

server marketshare is quite difficult to define. do you could one vote per domain name? in that case a personal website, or parked domain (domain registered, but no website) coulds as much as google.com.

between [http://www.alexa.com/](http://www.alexa.com/) and [http://news.netcraft.com/](http://news.netcraft.com/) you could work out what the top 10 (or top 100) site are using. this probably accounts for 90% of web traffic (or web page hits), and so may be good enough.

---

### Post by cunawarit on 2007-06-19
...

---

### Post by Atomic Dog on 2007-06-19
At our office we have 7 servers running linux based OS's and 8 server 2003 Virtual Machines. (4 on one and 4 on another)

There's a lot of servers running linux out there.  That's why I started using Ubuntu -just to get a feel for how linux works.  It saved my bacon when a VM wouldn't come up because of a VMware ESX partition entry in fstab.  Had I not had some familiatity I would have been screwed.

---

### Post by Bluecircle on 2007-06-19
> **ssam said:**
> 

server marketshare is quite difficult to define. do you could one vote per domain name? in that case a personal website, or parked domain (domain registered, but no website) coulds as much as google.com.



Obviously Google would have far more servers than just a parked domain name running on one server. If Google is running Linux then that would count as 100,000 servers running Linux (or however many they have), whereas a normal website would probably just count as one.

I want to know how many physical servers are using Linux as an OS, it has nothing to do with the domain name (it doesn't even have to be a webserver, it could be a game server, a NAS server at a business.... anything).

Of course it's hard to get a real estimate on this because there is no place that gathers this information, but I was wondering if there are any statistics or estimates.

---

### Post by samjh on 2007-06-19
For servers: [http://news.netcraft.com/archives/web_server_survey.html](http://news.netcraft.com/archives/web_server_survey.html)

---

### Post by cunawarit on 2007-06-21
Today I found a UK specific article talking about Web servers. 

According to the article 59% of UK company Web servers are Windows/IIS, Linux 17%, and Solaris 15%. 

I personally find that a bit hard to believe, it is not what I would have expected at all despite me having spent the last couple of years working with IIS. 

Anyway, also mentioned: "Even though the companies in our study seem to prefer Windows over Linux, our research shows they would be better off using Linux/Apache-based websites"

PS: The article would help, [http://management.silicon.com/itdirector/0,39024673,39167599,00.htm](http://management.silicon.com/itdirector/0,39024673,39167599,00.htm)

---

### Post by Zzl1xndd on 2007-06-21
As for desktop install base (as has been mentioned Market share refers to number sold) I normally she the estamates ranging Between 1 & 7 percent . Now I myself think it is in the 5-6 range based on the number of people I see that run linux in some way shape or form. but as it goes if Mac has 5% I know a lot more people using Linux then Mac so its a fair bet. The thing being is all of the polls are some what useless in Messuring this.

---

### Post by Ultra Magnus on 2007-06-21
> **tweakedenigma said:**
> The thing being is all of the polls are some what useless in Messuring this.

Thats true - It seems like every couple of weeks there is a new set of statistics stating something wildly different from the last - so unless allot of people are changing their OS all of the time and Businesses are constantly migrating their entire infrastrucure then I suggest taking these with a grain of salt.

One thing I've consistantly heard though is that Linux is preferred on web servers although Windows is preferred on business servers (I don't know the difference). As for Linux on the desktop - I think it probably has a userbase comparable to Mac but there are also allot of enterprise users who probably don't frequent the websites used in the study.

One thing I do know is that Linux is #1 for supercomputers by a very wide margin!

---

### Post by Bluecircle on 2007-06-21
> **cunawarit said:**
> Today I found a UK specific article talking about Web servers. 

According to the article 59% of UK company Web servers are Windows/IIS, Linux 17%, and Solaris 15%. 

I personally find that a bit hard to believe, it is not what I would have expected at all despite me having spent the last couple of years working with IIS. 

Anyway, also mentioned: "Even though the companies in our study seem to prefer Windows over Linux, our research shows they would be better off using Linux/Apache-based websites"

PS: The article would help, [http://management.silicon.com/itdirector/0,39024673,39167599,00.htm](http://management.silicon.com/itdirector/0,39024673,39167599,00.htm)

I read somewhere (I can't remember now) that the UK uses Windows/IIS more than anywhere else in the world. Other places like Germany and Denmark almost exclusively use Linux. For most of the world, Linux/Apache has a higher percentage than Windows/IIS

---

### Post by Bluecircle on 2007-06-21
> **tweakedenigma said:**
> As for desktop install base (as has been mentioned Market share refers to number sold) I normally she the estamates ranging Between 1 & 7 percent . Now I myself think it is in the 5-6 range based on the number of people I see that run linux in some way shape or form. but as it goes if Mac has 5% I know a lot more people using Linux then Mac so its a fair bet. The thing being is all of the polls are some what useless in Messuring this.

Not looking for desktop install, but I'm pretty sure Linux is closer to 1% for desktops. Macs around 4-6%

---

### Post by cabala on 2007-09-19
you need to know from where the statistician is getting money to generate such trends.

on the other hand, macs have been around for much longer than LINUX (the apple2 pre-dates windows1) so why be surprised that there are more of them around?

---

### Post by hessiess on 2007-09-19
what are the os statistics for this site? i would gess atlest 60% linux

---

### Post by karellen on 2007-09-19
what difference does it makes? if you run Linux, you use it for its own strength and because you like it, you don't think about market shares. so what the vast majority of people use windows? I don't really care, that just gives me a feeling of 'oneness' or not going with the whole stream, to say so...

---

