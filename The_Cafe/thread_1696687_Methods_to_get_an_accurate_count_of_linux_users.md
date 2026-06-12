---
title: "Methods to get an accurate count of linux users"
date: 2011-02-27
forum: The Cafe
---

### Post by DoubleClicker on 2011-02-27
Whenever there's a discussion of how many linux users are there, inevitably people start throwing out numbers based on different ways to estimate the hypothetical number of users.  That is a far cry from getting an actual count. 

Getting an accurate count would not be technically difficult. One method that would work:

Have a daemon, which is installed by default (and not removable with the package manager), in every major distro, which once  per day sends a unique identifier,  to a server (e.g. counter.kernel.org, or counter.x.org).  the server will only count one hit per day from each identifier. 

To balance the load on the server, the hit would be done at boot time, and intervals of 86400 seconds from boot time.  besides the identifier, possibly other configuration parameters could be sent. e.g. kernel version, distribution, xserver, apache, etc. 

The count server will created web based analytics of the counts; e.g. hits per day, average hits per day for a each month in a year, etc. 

However, the big hurdle to overcome is the objections, of the people who consider it an invasion of privacy.   The FOSS community, to a large degree, objects to tracking, and would have a hard time accepting such a method.  In reality there isn't really much cause for concern, because the unique identifier, does not have to be anything traceable, like an IP address, it could be a public key or any kind of hash. The only requirements being that it is unique, and persistent.  

Some people will argue, that these numbers won't be completly accurate, because some people will build there own kernal/xserver without the counter. However I would guess that the number of people, that remove it, won't be statisticly significant.

I'd like to see people use this thread to figure out how to overcome objections, or to suggest other methods that would be equally accurate, but not objectionable.  

Please avoid posting any user count estimates.  This is about how to count Linux users, not about how many you think there are.

---

### Post by Spice Weasel on 2011-02-27
The only way to get an accurate count is to steal every single device with a processor on the planet and test to see what their operating systems are. One by one.

---

### Post by tgm4883 on 2011-02-27
> **DoubleClicker said:**
> Whenever there's a discussion of how many linux users are there, inevitably people start throwing out numbers based on different ways to estimate the hypothetical number of users.  That is a far cry from getting an actual count. 

Getting an accurate count would not be technically difficult. One method that would work:

Have a daemon, which is installed by default (and not removable with the package manager), in every major distro, which once  per day sends a unique identifier,  to a server (e.g. counter.kernel.org, or counter.x.org).  the server will only count one hit per day from each identifier. 

To balance the load on the server, the hit would be done at boot time, and intervals of 86400 seconds from boot time.  besides the identifier, possibly other configuration parameters could be sent. e.g. kernel version, distribution, xserver, apache, etc. 

The count server will created web based analytics of the counts; e.g. hits per day, average hits per day for a each month in a year, etc. 

However, the big hurdle to overcome is the objections, of the people who consider it an invasion of privacy.   The FOSS community, to a large degree, objects to tracking, and would have a hard time accepting such a method.  In reality there isn't really much cause for concern, because the unique identifier, does not have to be anything traceable, like an IP address, it could be a public key or any kind of hash. The only requirements being that it is unique, and persistent.  

Some people will argue, that these numbers won't be completly accurate, because some people will build there own kernal/xserver without the counter. However I would guess that the number of people, that remove it, won't be statisticly significant.

I'd like to see people use this thread to figure out how to overcome objections, or to suggest other methods that would be equally accurate, but not objectionable.  

Please avoid posting any user count estimates.  This is about how to count Linux users, not about how many you think there are.

Personally, I don't object to counting Linux users, but when it comes to my system. I don't want anything running on my computer that I don't approve of or attempts to call home.

Once you start putting that sort of thing on a users system, it's a slippery slope to abuse.

---

### Post by DoubleClicker on 2011-02-27
> **tgm4883 said:**
> Personally, I don't object to counting Linux users, but when it comes to my system. I don't want anything running on my computer that I don't approve of or attempts to call home.

Once you start putting that sort of thing on a users system, it's a slippery slope to abuse.

That's the objection I was referring to.  What would be as effective, and less objectionable to you?

---

### Post by DoubleClicker on 2011-02-27
> **Spice Weasel said:**
> The only way to get an accurate count is to steal every single device with a processor on the planet and test to see what their operating systems are. One by one.

For statistical purposes that's not at all true.  we don't need accuracy to the exact number  +/-0, all we need is have it to the degree of accuracy that apple and Microsoft have.

---

### Post by tgm4883 on 2011-02-27
> **DoubleClicker said:**
> That's the objection I was referring to.  What would be as effective, and less objectionable to you?

Unfortunately this is where it gets difficult. 

A) You could count downloads of a particular package from the repos. Maybe count the downloads of ubuntu-desktop (and any other -desktop package). This would give you the Ubuntu machines in the wild, although you would have to have all of the repository mirrors do the same and add it up. Something that is going to be a pain to get set up to do so for very little benefit. (you would also have to do the same for other distros).

B) Possibly have a poll of how many machines you run Ubuntu on (or plan to) when you go to download it, but again, this requires people to go to the main site to download the ISO, which not many people do.

C) Of course you could just take stats from the top 500 web site, pull out just the unique information and count how many people are using Linux. This would A) require that the top 500 web sites wanted to give out this information and B) possibly be less accurate due to what the top 500 web sites actually are.

C is probably the best method, but I guess the question is what would all this work actually do for us? What do we gain from getting a more accurate number of Linux machines?

---

### Post by Paqman on 2011-02-27
> **DoubleClicker said:**
> Whenever there's a discussion of how many linux **users**

<snip>

Have a daemon, which is installed by default

That wouldn't count the number of users, it would count the number of installs. Most Linux installs are servers, which may be in huge farms, a lot of which are only going to be virtual machines anyway, and thus could be being created and destroyed willy-nilly. Even home users may have more than one machine each. My household has at least five desktop Linux installs on four machines used by two adults.

---

### Post by Paqman on 2011-02-27
> **tgm4883 said:**
> I guess the question is what would all this work actually do for us? What do we gain from getting a more accurate number of Linux machines?

I don't think the big number at the bottom line would be that exciting, but if you were able to break it down to geographical location and other such fine detail you could get some interesting analysis of trends.

---

### Post by tgm4883 on 2011-02-27
> **Paqman said:**
> I don't think the big number at the bottom line would be that exciting, but if you were able to break it down to geographical location and other such fine detail you could get some interesting analysis of trends.

Some interesting analysis I suppose but still. An awful lot of work for something that in the end is used as a toy.

---

### Post by cariboo on 2011-02-27
Canonical counts the number of unique ip address that connect to the repositories to count the number of users, Last I saw, there about 12,000,000 Ubuntu users. 

This really doesn't work very well though, I run Ubuntu on 7 computers, all with one external ip address.

---

### Post by DoubleClicker on 2011-02-27
> **tgm4883 said:**
> Unfortunately this is where it gets difficult. 

A) You could count downloads of a particular package from the repos. Maybe count the downloads of ubuntu-desktop (and any other -desktop package). This would give you the Ubuntu machines in the wild, although you would have to have all of the repository mirrors do the same and add it up. Something that is going to be a pain to get set up to do so for very little benefit. (you would also have to do the same for other distros).

B) Possibly have a poll of how many machines you run Ubuntu on (or plan to) when you go to download it, but again, this requires people to go to the main site to download the ISO, which not many people do.

C) Of course you could just take stats from the top 500 web site, pull out just the unique information and count how many people are using Linux. This would A) require that the top 500 web sites wanted to give out this information and B) possibly be less accurate due to what the top 500 web sites actually are.

C is probably the best method, but I guess the question is what would all this work actually do for us? What do we gain from getting a more accurate number of Linux machines?
Those are the very inaccurate methods methods, which the the current widely variable estimates are made from.  The whole point of this exercise is to get meaningful numbers, that don't that don't have a a variance in orders of magnitude. 


> **Paqman said:**
> That wouldn't count the number of users, it would count the number of installs. 

True, but thats actually what Apple and Microsoft count too.   In calculating market share, and market potential, those are numbers that matter.

> **Paqman said:**
>  Most Linux installs are servers, which may be in huge farms, a lot of which are only going to be virtual machines anyway, and thus could be being created and destroyed willy-nilly. Even home users may have more than one machine each. My household has at least five desktop Linux installs on four machines used by two adults.  There are fairly simple ways to either make the counter only be part of desktop installs, or able to separate servers from desktops.  And remember, just like some people have multiple Linux boxes,spome linux boxes are used by multiple people.     

> **tgm4883 said:**
> Some interesting analysis I suppose but still. An awful lot of work for something that in the end is used as a toy.
 no it isn't just a toy, it's market research that determines how billions of dollars and man hours are spent.

> **cariboo907 said:**
> Canonical counts the number of unique ip address that connect to the repositories to count the number of users, Last I saw, there about 12,000,000 Ubuntu users. 

This really doesn't work very well though, I run Ubuntu on 7 computers, all with one external ip address.
That isn't a meaning full number because, several machines could be NATed to the same IP, and one IPs download from the official repositories can be mirrored for multiple machines.   So 12,000,00 unique IPs could account for  only a small fraction of the actual installs.  But pleas lets not get sidetracked into speculating about specific numbers.  When we have a deployed method to make actual counts, we will get meaningful numbers.

---

### Post by Khakilang on 2011-02-27
I believe it is easier for RedHat as they are selling their service and so is Microsoft and Apple. For other Distro its a bit difficult as some tends Distro hoping. Maybe you can organize a team to go door to door to check on the computer around the world.

---

### Post by tgalati4 on 2011-02-27
Just use 1%.  Everyone else does, so it must be correct.

A boot-time signal wouldn't work since I only reboot once every 6 months.

---

### Post by DoubleClicker on 2011-02-28
> **tgm4883 said:**
> A boot-time signal wouldn't work since I only reboot once every 6 months.It wouldn't be at boot time only, but every 24hrs:0mins:0secs  after the last time it ran.  So if your computer finished booting at 11:42:28, then every day at 11:42:28 it would execute.
> **tgm4883 said:**
> Just use 1%.  Everyone else does, so it must be correct.
Thats the problem, people use 1%, which is based on speculation not data,  developers, manufacturers, and content providers then think, "well linux only has 1%, it's not worth while to be linux compatible".  If using a credible counting mechanism discovers a 10%, or (lets dream a little) 50% share, believe me, they would bend over backward to make sure their products were linux compatible.

---

### Post by frup on 2011-02-28
If the information was really important to you, you could always campaign to your government that it form a part of a census question.

Once one countries population is counted, using the typical amalgamation of web stats that are often used would produce some interesting figures I suppose.

---

### Post by Paqman on 2011-02-28
> **DoubleClicker said:**
> 
And remember, just like some people have multiple Linux boxes,spome linux boxes are used by multiple people.     


That was sort of my point. Counting actual users is difficult. You could count the number of installs, but that's not quite the same thing.

Bottom line, to make your stats meaningful you'd have to have the participation of every single distro. That's never going to happen, the distros are notoriously independent-minded, and will never agree 100% on anything (which is a large part of the reason desktop Linux isn't more widespread). Getting them all to install what many hardcore freetards would see as spyware just isn't going to happen.

IMO counting browser strings across a large number of websites (a la Statcounter) will probably give you the best data. Statcounter puts us at [about 0.75%]("http://gs.statcounter.com/#os-ww-monthly-200807-201101"), btw.

---

### Post by t0p on 2011-02-28
I think getting an "accurate count" is not possible without some kind of "phone home" system.  And I don't like my computer phoning home (even though that happens anyway, what with cookies and flash stuff reporting to third parties every time I visit a website).

Anyway, Microsoft and Apple don't have an "accurate count" of their users/machines.  They depend on estimation and extrapolation themselves.

---

### Post by cascade9 on 2011-02-28
> **DoubleClicker said:**
> However, the big hurdle to overcome is the objections, of the people who consider it an invasion of privacy. The FOSS community, to a large degree, objects to tracking, and would have a hard time accepting such a method. In reality there isn't really much cause for concern, because the unique identifier, does not have to be anything traceable, like an IP address, it could be a public key or any kind of hash. The only requirements being that it is unique, and persistent. 

As soon as you have an unremovable, unique and presistent ID tag it has the potential to be used to get more data on the user. 

I dont get this obsession with counting installs/users myself. 

> **Paqman said:**
> Bottom line, to make your stats meaningful you'd have to have the participation of every single distro. That's never going to happen, the distros are notoriously independent-minded, and will never agree 100% on anything (which is a large part of the reason desktop Linux isn't more widespread). Getting them all to install what many hardcore freetards would see as spyware just isn't going to happen.

I agree that you will never get all the distros to agree on something like that. Why you had to get into name calling ('freetards') is beyond me..... 

> **Paqman said:**
> IMO counting browser strings across a large number of websites (a la Statcounter) will probably give you the best data. Statcounter puts us at [about 0.75%]("http://gs.statcounter.com/#os-ww-monthly-200807-201101"), btw.

User agent switching could be throwing those stats out, a fair % of the people I know running a linux distro have it running all the time. Thats not the only problem with counting from websites though.

---

### Post by barbedsaber on 2011-02-28
you also have to consider that ubuntu is used A LOT in third world countries, and other situations where an internet connection is rare.
Just because we are fortunate enough to have an internet connection doesn't mean every computer user is, (afaik) in the situations where the internet connection is not present, ubuntu is much more common than it is in other situations.

0.02c

---

### Post by uljanow on 2011-02-28
Canonical is already doing that. The default ntp server is ntp.ubuntu.com. But you could only count users in an 24h interval because major ISPs use dynamic IP leases.

---

### Post by eriktheblu on 2011-02-28
Accurate data would be nearly impossible to acquire. A phone home system requires some type of communication system. Downloads/sales do not equate to installs.

The value of this data is questionable as well. From a business standpoint, the more important question is "what will be my net profit if I restructure to accommodate Linux?"

The number of Linux users does not directly correlate with that question, as Linux users are varied (desktop, server, smart phone, whatever). 

There is a difference between data and information. Since you will likely not get the data, focus on the information you need and seek alternatives.

---

### Post by tgm4883 on 2011-02-28
> **DoubleClicker said:**
> It wouldn't be at boot time only, but every 24hrs:0mins:0secs  after the last time it ran.  So if your computer finished booting at 11:42:28, then every day at 11:42:28 it would execute.
Thats the problem, people use 1%, which is based on speculation not data,  developers, manufacturers, and content providers then think, "well linux only has 1%, it's not worth while to be linux compatible".  If using a credible counting mechanism discovers a 10%, or (lets dream a little) 50% share, believe me, they would bend over backward to make sure their products were linux compatible.

Please learn how to quote correctly. I said neither of the things your responded to.

---

### Post by del_diablo on 2011-02-28
> **Paqman said:**
> IMO counting browser strings across a large number of websites (a la Statcounter) will probably give you the best data. Statcounter puts us at [about 0.75%]("http://gs.statcounter.com/#os-ww-monthly-200807-201101"), btw.

90% of the web only browses 10% of the web pages.
However, last time I checked Statcounter or any other form of "stastic miner" does not even cover 5% of the web. This makes them unsuitable for any form of datamining, unless you do it for a spesific group(Example: A country)
Nevermind that you also have a lot of computers that is never used online, never visiting the normal web, etc...

---

### Post by rg4w on 2011-02-28
> **del_diablo said:**
> However, last time I checked Statcounter or any other form of "stastic miner" does not even cover 5% of the web.
IIRC Statcounter relies on a certain set of member sites, most of which are in English-speaking countries with English-only web sites.  Is that correct?  If so, it's a problem for measuring Linux share since Linux is so much more popular outside the US/UK/AU/etc.

---

### Post by del_diablo on 2011-02-28
> **rg4w said:**
> IIRC Statcounter relies on a certain set of member sites, most of which are in English-speaking countries with English-only web sites.  Is that correct?  If so, it's a problem for measuring Linux share since Linux is so much more popular outside the US/UK/AU/etc.

Yes, that is the problem.

---

### Post by 3Miro on 2011-02-28
Putting a calling-home service inside a distribution that cannot be easily disable is a violation to the FOSS philosophy. I will never use a distribution that does that.

If you want to count the people using Linux, look for hits to the mirrors with updates i.e. how often and how many updates people download. This is not 100% accurate, but it is the best you can do.

In a semi-related matter, Microsoft knows the exact number of licenses that they sell, however, they have no clue how many illegal copies of windows are out there. Some countries run on almost 100% illegal windows, there is no way to keep track of that. Mac is better, since Hackintosh is less popular, but they don't know either. Even if you can count the exact number of machines running Linux, you still don't know what percentage that is, since there is no way to estimate the exact number of machines there are in the world; even if you can find the number of machines sold (disregarding custom builds), you don't know how many of those are still running today. Until we start licensing computers and requiring people to declare their OS, there is no way to keep track of this.

---

### Post by MisterGaribaldi on 2011-02-28
> **Spice Weasel said:**
> The only way to get an accurate count is to steal every single device with a processor on the planet and test to see what their operating systems are. One by one.
Yes, except that it doesn't represent a proper *user* head count. Sadly, brute-forcing the situation is probably the only way to get any kind of accurate count, though.

> **DoubleClicker said:**
> For statistical purposes that's not at all true.  we don't need accuracy to the exact number  +/-0, all we need is have it to the degree of accuracy that apple and Microsoft have.
See, I don't really care much for that sort of answer. No disrespect intended, of course, but what you're also trying to base this on is the law of large numbers thing. The issue with that is we don't really have any mechanisms in place to achieve this. Also, I don't really trust Microsoft's or Apple's counting mechanisms either, because they don't really eliminate things like virtualization, multi-booting, or piracy.

Of course, I would never agree to the sort of draconian "big brother"-type tactics I figure it would actually take to get an accurate number.

As third-world countries (especially ones like China and India) start using Linux more and more, that will turn the tables here. I mean, if 1/3 of China were using Linux, that would be greater than 100% of the U.S., Canada, the U.K., and most of Europe combined all using Linux. So, ultimately, it's a matter of scale.

---

### Post by Paqman on 2011-03-02
> **rg4w said:**
> If so, it's a problem for measuring Linux share since Linux is so much more popular outside the US/UK/AU/etc.

Source? I know there are *some* countries that have slightly higher usages such as Brazil and Germany, but i've never seen anything to suggest that goes for the whole world.

Anyway, we know how widespread Linux use is. Every different way of measuring that anybody ever tries comes back with roughly the same figure: 1%.

---

### Post by Simian Man on 2011-03-02
> **DoubleClicker said:**
> There are fairly simple ways to either make the counter only be part of desktop installs, or able to separate servers from desktops.  And remember, just like some people have multiple Linux boxes,spome linux boxes are used by multiple people.
Oh really, what are they?  I install Apache on my laptop to play with web programming.  How could you distinguish my laptop from a web server?  I also have many source control systems installed, how could you distinguish from a repository server?

If you want to do this to show how many Linux *desktop* users there are, the web-based sampling techniques are generally *more* accurate than what you are proposing because servers generally do not browse the internet :).

---

### Post by dh04000 on 2011-03-02
No method of counting users is prefect. Microsoft use licenses, but I have 2 licences myself. So don't go saying that their numbers are great. They are rough estimates.

The best way to get a rough estimate of online linux users would be to push an update (without telling anyone) in all major linux distros that creates an unique code for every computer and submits it for counting. It does this one time, and then uninstalls it self. This only can be applied to a system one time. Have this in the repo for about 1 month, and then remove. That would create a very "rough estimate" for all of the online linux users.

The non-online linux users would not be counted, but since they would not be the ones buying games, and other paid for services, they aren't really needed for a count anyway. All a count would be useful for is to push devs to make linux apps and games.

---

### Post by Paqman on 2011-03-02
> **dh04000 said:**
> All a count would be useful for is to push devs to make linux apps and games.

The current methods are perfectly adequate for this. I don't think refining a decimal point or two either way will make it suddenly commercially viable to do things that aren't currently.

We have about 1% of the desktop market. Maybe it's actually 0.5%, maybe it's 2%. It doesn't really matter, as it still puts us in the same ballpark.

Linux is awesome, but if you're looking for a platform that's heavily supported for commercial apps and games, Linux ain't it.

---

### Post by Bölvaður on 2011-03-02
I cannot believe no one has mentioned very simple method:

Pick a large group, like a country. Put everyone in that country in big list and have a computer randomly pick 2000 people from this list. Proceed to ask them if they use linux... might take some time but it should get accurate enough number, specially if you do this for few countries.

---

### Post by tgm4883 on 2011-03-02
> **Simian Man said:**
> Oh really, what are they?  I install Apache on my laptop to play with web programming.  How could you distinguish my laptop from a web server?  I also have many source control systems installed, how could you distinguish from a repository server?


Although this is a terrible technique, I thought I'd answer this question directly.

This is actually really easy to do. Just count the number of ubuntu-desktop (package) installs. If you wanted to filter out the people who install ubuntu-desktop on their server (which no self respecting admin would do on a production server), make a package that can only be installed from the live/alternate ISO, then count those installs. Again, no good admin is going to install a production server using the desktop ISO's. Any regular user that has a home server built from the desktop ISO is easily covered in the margin of error.

---

### Post by Dustin2128 on 2011-03-02
> **cariboo907 said:**
> Canonical counts the number of unique ip address that connect to the repositories to count the number of users, Last I saw, there about 12,000,000 Ubuntu users. 

This really doesn't work very well though, I run Ubuntu on 7 computers, all with one external ip address.
Those numbers would be more impressive if not for dynamic IP, but still, it's also counterbalanced by the widespread usage of NATs.

---

### Post by Primefalcon on 2011-03-03
I don't really think there is any accurate way tbh

---

### Post by Simian Man on 2011-03-03
> **tgm4883 said:**
> This is actually really easy to do. Just count the number of ubuntu-desktop (package) installs. If you wanted to filter out the people who install ubuntu-desktop on their server (which no self respecting admin would do on a production server), make a package that can only be installed from the live/alternate ISO, then count those installs. Again, no good admin is going to install a production server using the desktop ISO's. Any regular user that has a home server built from the desktop ISO is easily covered in the margin of error.

What about people who use anything besides Gnome?  What about people who use anything besides Ubuntu?  What about people who use the mini.iso disc for a server or for a desktop?  And I think you are discounting the number of people who will install a GUI on a server.  Just because one is installed doesn't mean it is running most of the time.  Heck a lot of people run Windows servers!

There really is no easy way to do this.

---

### Post by tgm4883 on 2011-03-03
> **Simian Man said:**
> What about people who use anything besides Gnome?  What about people who use anything besides Ubuntu?  What about people who use the mini.iso disc for a server or for a desktop?  And I think you are discounting the number of people who will install a GUI on a server.  Just because one is installed doesn't mean it is running most of the time.  Heck a lot of people run Windows servers!

There really is no easy way to do this.

No, it's really not that difficult from a technological point of view. The most difficult part of this is two things A) getting all linux distros to do it, and B) Not creating a huge uproar from Linux users. 

Create a package and count the number of installs. Make one of the packages for servers depend on it (for Ubuntu this could be the server kernel, other distos may have something similar). Similarly do the same for desktop installs (create a package, make ubuntu-desktop, kubuntu-desktop, xubuntu-desktop, etc depend on it)

For those edge cases where someone has installed Gnome (or KDE, insert your DE here), those can be counted as servers as well. Note that installing Gnome is not the same as installing ubuntu-desktop (true for KDE, XFCE, etc). Any of the -desktop packages would bring along things like OpenOffice, Evolution, games, etc. IMHO, if you install ubuntu-desktop on a server, you should be counted as a desktop. 

And no, I think you are overestimating the number of people that install a non-web-based GUI on a server in a production network. There is no reason to have a GUI running on a server that hardly ever gets accessed directly. Even for the ones that do, they likely aren't installing a -desktop package.

---

### Post by aysiu on 2011-03-03
To those people who say "There's no way to count Linux users, only installations," all I can say is that Windows and Mac platforms face *exactly* the same problem.

I have a Macbook Pro, which Apple counts as a Mac, but I also dual-boot it with Ubuntu. So am I a Mac user or a Ubuntu user? I'm neither. I'm a Mac installation and a Ubuntu installation. I also use Windows at work, so am I a Mac, Windows, or Ubuntu user?

You can't count users, only installations.

---

### Post by rg4w on 2011-03-05
> **Paqman said:**
> Source? I know there are some countries that have slightly higher usages such as Brazil and Germany, but i've never seen anything to suggest that goes for the whole world.
I didn't mean to suggest that Linux has a bigger share than Windows outside the US, just that it has a big enough share outside the US to warrant questioning the "1%" figure we find from so many US-centric stats.

I come across stories of Linux adoption outside the US so frequently that I don't really notice them anymore, so I don't have those URLs handy.  Moreover, getting solid statistics for non-US deployments is every bit as difficult for US-centric stats, so all numbers from all sources should be viewed with healthy skepticism.

That said, there are some encouraging signs I turned up in a quick Google search this morning:

> Look outside North America, he says, and the generally accepted figures are almost all too low, distorted by the Windows-dominated perspective of the United States and Canada.

At the end of his presentation, Seigo was reluctant to give a percentage, but, when I pressed him, he suggested that 8% was probably a bottom figure, and 10-12% the likeliest. Some of the audience seemed politely skeptical, but, even if you half his figures, his examples go a long way towards suggesting that North Americans consistently under-estimate GNU/Linux use because we live in a Windows-distorted environment. [http://itmanagement.earthweb.com/osrc/article.php/12068_3818696_2/Linux-Desktop-Market-Share-Greater-Than-One-Percent.htm](http://itmanagement.earthweb.com/osrc/article.php/12068_3818696_2/Linux-Desktop-Market-Share-Greater-Than-One-Percent.htm)

This article is a few years old, but the numbers noted for China are remarkable:
[http://www.linux.com/archive/feature/122473](http://www.linux.com/archive/feature/122473)

To the degree Open Office may be viewed as a canary in the coal mine for FOSS usage in general (perhaps dubious, perhaps relevant, I'll let the reader decide), their by-country stats show much stronger interest outside the US than within it:
[http://wiki.services.openoffice.org/wiki/Market_Share_Analysis](http://wiki.services.openoffice.org/wiki/Market_Share_Analysis)

While I don't agree with everything in this article and feel her conclusion should maybe be halved, the author has some points which I feel are worth considering in her argument that Linux market share may be as high as 10%:
[http://broadcast.oreilly.com/2010/09/debunking-the-1-myth.html](http://broadcast.oreilly.com/2010/09/debunking-the-1-myth.html)


So yes, the estimates are all over the place, and unfortunately there is no way to obtain solid data.  But looking at the broad range of data available, I feel it's safe to say that 1% represents the low end of the estimate range, and that non-US share is likely at least two to three times that.

---

### Post by mamamia88 on 2011-03-05
don't know if this has been suggested right now but if we could get distros to account for the number of distinct ips visiting a site it would give a decent representation.  sure isps change occasionally and it wouldn't be perfect but would be a good impression.  usually people download it once and keep a copy.

---

### Post by Bölvaður on 2011-03-06
so I guess no one here agrees with the most straight forward method of asking the people... which would count for any server/desktop installation problems and computers that are not connected to internet or do not go through updates.

it's a very simple method.. when you want to know something you do it via statistics, not bruteforce.

---

### Post by Paqman on 2011-03-06
> **Bölvaður said:**
> so I guess no one here agrees with the most straight forward method of asking the people... which would count for any server/desktop installation problems and computers that are not connected to internet or do not go through updates.


No, I think that's a perfectly sensible way to do it. Probably not the cheapest though, as distros would have to outsource the work.

---

### Post by DZ* on 2011-03-06
> **Bölvaður said:**
> I cannot believe no one has mentioned very simple method: Pick a large group, like a country. Put everyone in that country in big list and have a computer randomly pick 2000 people from this list. Proceed to ask them if they use linux... might take some time but it should get accurate enough number, specially if you do this for few countries.

It's a good method with the caveat that the response probability likely depends on the true proportion. A group that is in the minority may be more likely to respond. In the extreme case (most non-linux users ignore the survey) we'd have highly upward biased estimate.

Also, what is a good sample size, n? A confidence limit will look like p+z*sqrt(p(1-p)/n) and for z,n fixed it's the widest at p=0.5. To have a 99% interval as short as 0.01 we'd need to ask 66K people (in R notation)
```
> z <- qnorm(1 - 0.01/2); p <- 0.5; n <- p*z^2*(1 - p) / ((0.01/2)^2); n
[1] 66348.97
```

---

### Post by Bölvaður on 2011-03-07
> **DZ* said:**
> It's a good method with the caveat that the response probability likely depends on the true proportion. A group that is in the minority may be more likely to respond. In the extreme case (most non-linux users ignore the survey) we'd have highly upward biased estimate.

Also, what is a good sample size, n? A confidence limit will look like p+z*sqrt(p(1-p)/n) and for z,n fixed it's the widest at p=0.5. To have a 99% interval as short as 0.01 we'd need to ask 66K people (in R notation)
```
> z <- qnorm(1 - 0.01/2); p <- 0.5; n <- p*z^2*(1 - p) / ((0.01/2)^2); n
[1] 66348.97
```
that is doable as this would be the meta analysis.
Lets say we check 30 countries, that would mean for each country we'd ask 2200 people. It would be impossible to do it in every single country.. or is it no problem?
Then we'd have a geographical density of linux users per country.

---

### Post by matik on 2011-04-24
> **Bölvaður said:**
> that is doable as this would be the meta analysis.
Lets say we check 30 countries, that would mean for each country we'd ask 2200 people. It would be impossible to do it in every single country.. or is it no problem?
Then we'd have a geographical density of linux users per country.

Asking it from 66000 people costs alot of money. Think about the time, phone minutes etc. The results may be pretty biased, as noted above. And we do not get any realtime data. Never. Except when you are constanly phoning the same people every week and asking the same question again and again...

IMO easiest, cheapest way would be just to use the "home-phoning" system. I guess every installation in ubuntu afaik already generates some sort of UUID. If that UUID or it's hash is reported once per day using an encrypted UDP packet (maybe even the NTP sync could be reused) then it would be cheaper. Except, of course - cost of running the servers and bandwidth :(

If this system could be installed on every linux distro and FOSS people could overcome the "oh-my-god-big-brother-is-tracking-us" fear, then it'd be really nice way to see real user count. IN REALTIME. Maybe even see what distros are more popular - and not by download count, but real USE.

---

