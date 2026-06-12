---
title: "Minitab 16 and TIBCO Spotfire for Linux"
date: 2013-10-24
forum: Ubuntu, Linux and OS Chat
---

### Post by amjjawad on 2013-10-24
Hello Everyone,

I am trying to convert my neighbour to Linux but he asked me whether there are alternatives for:

** Minitab 16**

and

**TIBCO Spotfire**

Since I have never used nor heard of these software, I need help :)

The only reason he is using Windows 8 (and he admitted that he hates Windows 8) is because of these two software.

Help is highly appreciated :)

Thanks!

---

### Post by Erik1984 on 2013-10-24
I don't know those application either but can't you set him up with a dual boot? Then he can still fall back on Windows 8 if he can't find alternatives for those applications.

---

### Post by amjjawad on 2013-10-24
> **Euroman said:**
> but can't you set him up with a dual boot? Then he can still fall back on Windows 8 if he can't find alternatives for those applications.

Of course I can but obviously, he is having hard time with Windows and don't even want to Dual-Boot. He is interested to switch to Linux. He is actually having both Mac and so happy with it and Windows (not happy at all) and as I mentioned, the only reason as he said that forcing him to use Windows for now is these Programs :)

Thanks!

---

### Post by monkeybrain20122 on 2013-10-24
Do people still use Minitab? The statistical computation package of choice today is definitely R. It is FOSS, powerful and is expanding rapidly,. It is used by some industrial heavy weight like google. It is in the repository, or you can get up to date version from ppa. [https://launchpad.net/~marutter/+archive/rrutter](https://launchpad.net/~marutter/+archive/rrutter)

If R is overkill and your friend doesn't feel like programming s/he can try pspp (which is more of a learning tool than a production one IMO). Unfortunately you have to compile it if you use Ubuntu because the repo version is out of date and is missing some important new features from ver 8.1 (logistic regression is the biggie) But it is easy to compile and the website gives step by step instructions. Then of course SPSS and STATA run natively in Linux, but cost a lot $$$.

Don't know about the other software.


EDITED:

Just checked out the other one. Since R is also one of the best software for datamining and analytics I would definitely say go for R. Only catch is you need to learn to program. There is a  (several?) point and click interface, but I wouldn't recommend it as it is very primitive and you get the most out of R by programming. R has a nice IDE (also FOSS) called Rstudio, you can download the .deb from [http://www.rstudio.com/ide/download/](http://www.rstudio.com/ide/download/)
There are also some java-based data mining tools that are cross platform, but I can't remember their names at this point.

---

### Post by RichardET on 2013-10-25
I have used Spotfire;  There is no GNU/Linux equivalent.  My solution is to go with Ubuntu, then use a windows VM underneath it.  Spotfire is a very good graphical tool for data presentation & analysis.  No sense in trying to wean him off of it.

---

### Post by monkeybrain20122 on 2013-10-25
> **RichardET said:**
> I have used Spotfire;  There is no GNU/Linux equivalent. .

Maybe for your use case. I looked at its websites and it seems that there are many Linux equivalents that do the same kind of things. As mentioned R is probably the best for data mining and related tasks (it is rapidly gaining on SAS in terms of adoption, and SAS actually has an module to invoke R in its data miner) R also has powerful graphic tools for presentations. But with R you need to learn to program, point and click is too limiting (but see Rattle in the link below)

There are also others 
[http://www.siliconafrica.com/the-best-data-minning-tools-you-can-use-for-free-in-your-company/](http://www.siliconafrica.com/the-best-data-minning-tools-you-can-use-for-free-in-your-company/)
All of them are cross platform and most are open source.

---

### Post by amjjawad on 2013-11-03
> **monkeybrain20122 said:**
> Do people still use Minitab? The statistical computation package of choice today is definitely R. It is FOSS, powerful and is expanding rapidly,. It is used by some industrial heavy weight like google. It is in the repository, or you can get up to date version from ppa. [https://launchpad.net/~marutter/+archive/rrutter](https://launchpad.net/~marutter/+archive/rrutter)

If R is overkill and your friend doesn't feel like programming s/he can try pspp (which is more of a learning tool than a production one IMO). Unfortunately you have to compile it if you use Ubuntu because the repo version is out of date and is missing some important new features from ver 8.1 (logistic regression is the biggie) But it is easy to compile and the website gives step by step instructions. Then of course SPSS and STATA run natively in Linux, but cost a lot $$$.

Don't know about the other software.


EDITED:

Just checked out the other one. Since R is also one of the best software for datamining and analytics I would definitely say go for R. Only catch is you need to learn to program. There is a  (several?) point and click interface, but I wouldn't recommend it as it is very primitive and you get the most out of R by programming. R has a nice IDE (also FOSS) called Rstudio, you can download the .deb from [http://www.rstudio.com/ide/download/](http://www.rstudio.com/ide/download/)
There are also some java-based data mining tools that are cross platform, but I can't remember their names at this point.

Hello,

Thank you for your suggestion but what do you mean that he needs to learn how to program?

Also, please note that I have used nor heard of these programs, I am just trying to help him :)

Thank you!

---

### Post by amjjawad on 2013-11-03
> **RichardET said:**
> I have used Spotfire;  There is no GNU/Linux equivalent.  My solution is to go with Ubuntu, then use a windows VM underneath it.  Spotfire is a very good graphical tool for data presentation & analysis.  No sense in trying to wean him off of it.

Last time I talked to him, he said he is using a VM running Windows XP because his programs don't work with Windows 8 and it seems he has no Windows 7 Disc.

Thing is, he is very interested to switch to Linux.

---

### Post by monkeybrain20122 on 2013-11-03
> **amjjawad said:**
> Hello,

Thank you for your suggestion but what do you mean that he needs to learn how to program?

Also, please note that I have used nor heard of these programs, I am just trying to help him :)

Thank you!

Hi,

I mean R uses primarily the command line and  the user would need to be able write R functions and r scripts in order to take full advantage of R's advanced features. R is not just a statistical package, but a comprehensive  computing environment for data analysis and statistics.  [http://cran.r-project.org/](http://cran.r-project.org/)

However, it also has some point and click interfaces. For example [http://rforge.net/JGR/](http://rforge.net/JGR/) But last time I checked (a few years ago, granted) JGR was kind of rudimentary. There may be a few others too (e.g Rattle from the link in my previous post). Even though it is definitely not for the power user IMO,  your friend may find a point and click interface adequate for his purpose (I never use minitab, but I doubt that a purely point and click stat program would have a lot of advanced features, it seems that all serious stat programs require programming to get the most out of them, --e.g R, SAS, STATA, SPSS with syntax. P.S. STATA and SPSS also run natively in Linux, I think STATA costs less than $200, don't know how much Minitab costs)

---

### Post by RichardET on 2013-11-04
I do SAS in my professional life plus I use R, Spotfire, JMP, Enterprise Guide.   I also love Linux.  But unfortunately only R is on Linux.  Linux only :  use R.
Linux + VMware with a Windows guest:  R, Spotfire, JMP, Enterprise Guide.

---

### Post by monkeybrain20122 on 2013-11-05
I used SAS at work. It is good for data management and macro programming is quite fun, but its statistical capability is vastly inferior to R and even STATA, plus, who could afford  to rent a super expensive SAS license every year except for large organizations? (You can find an old release with license expiring in 3 months in the torrent sites of course but let's assume we are all legit here) Entreprise Guide is for amatures, it was installed at work but we never found it useful, if you want point and click SPSS can do more and  is cheaper (and run natively in Linux) 

SAS is one of the most inextendible and inflexible software in that every extra module costs you another license, R is completely opposite, you can do almost anything imaginable with it, you can always find an R pakage somewhere that does what you need even if requires a bit tweaking and modifications. For a while my employer paid for my copy of SAS (base only)  and I ran it in virtualbox, now I have switched completely to R and don't even bother anymore.

---

### Post by RichardET on 2013-11-09
I am quite expert in SAS, and I challenge you to manipulate large Teradata tables in R, the way it can be easily be handled in SAS.  Not sure what your level of stats background is, but SAS is the gold standard for GLM as well as mixed models.  I like R, but like other tools similar to R, all tables are processed in memory, and obviously this is a severe limitation.

---

### Post by monkeybrain20122 on 2013-11-10
There are many ways to work with big data in R, check out the R-bloggers for example to see the options,--and since R is open source it is infinitely extendible and can work with other tools such as Python, There are also some R packages to dump large datasets into hardndrive like SAS does. For enterprises there is also RevolutionR but it is proprietary and supports only Redhat Linux (would work in Fedora but not in Ubuntu)

SAS is "Gold standard" only in certain industry (e.g pharmaceutical) which do rather common stats (ie procedures that any competent package can do and perhaps better, like general linear models), I suppose the reason why it is "gold standard" has to do with history (entrenched proprietary formats and vendor lock in) as well as liability (if something goes wrong because of bugs you can sue SAS but not R) but for cutting edge statistical research R is now pretty much the standard. R is fast overtaking SAS as the favourite for data mining (SAS's data mining package actually has a "proc R" to invoke R in SAS, check it out if you don't believe me). For econometrics STATA is actually better than SAS according to experts in the field. I think the only place where SAS may still has an edge is data management, but may not be for long. 

But in any case it doesn't sound like OP's friend is a corporation that would spend thousands of dollars to rent a SAS license so your points are quite moot.

---

### Post by philinux on 2013-11-10
Moved to U L and OS chat.

---

### Post by RichardET on 2013-11-10
> **monkeybrain20122 said:**
> There are many ways to work with big data in R, check out the R-bloggers for example to see the options,--and since R is open source it is infinitely extendible and can work with other tools such as Python, There are also some R packages to dump large datasets into hardndrive like SAS does. For enterprises there is also RevolutionR but it is proprietary and supports only Redhat Linux (would work in Fedora but not in Ubuntu)

SAS is "Gold standard" only in certain industry (e.g pharmaceutical) which do rather common stats (ie procedures that any competent package can do and perhaps better, like general linear models), I suppose the reason why it is "gold standard" has to do with history (entrenched proprietary formats and vendor lock in) as well as liability (if something goes wrong because of bugs you can sue SAS but not R) but for cutting edge statistical research R is now pretty much the standard. R is fast overtaking SAS as the favourite for data mining (SAS's data mining package actually has a "proc R" to invoke R in SAS, check it out if you don't believe me). For econometrics STATA is actually better than SAS according to experts in the field. I think the only place where SAS may still has an edge is data management, but may not be for long. 

But in any case it doesn't sound like OP's friend is a corporation that would spend thousands of dollars to rent a SAS license so your points are quite moot.

If you want to discuss big data, how do you handle the missing values?  R is cutting edge, that's true, but not sure why every discussion here has to lean in favor of an open source version.  SAS does alot more than simply dump data to a disk.  You should follow Richard DeVeaux's work with SAS JMP.  There are many free lectures available.  He has much to say about big data.

---

### Post by monkeybrain20122 on 2013-11-10
OP asked for a Linux alternative for Minitab, there are plenty of options, free or non free, open or proprietary which all are available to Linux. Yet you come here to advertise for SAS, which is the most closed and most inflexible (Stata is proprietary but more open than SAS and allows more user participations), most inextendable, with the worst inter-portability,--Stata and SPSS data formats are much easier to import to other formats without having a copy of the software,-- , most expensive (~$1000 for a license just for SAS base and Enterprise Guide(?)  that expires in one year and extra licenses for additional modules). 

For the high cost and all its limitations  it is not even that good on many fronts: The programming language is clunky and inflexible,many options appear like ad hoc afterthoughts and lack coherence and logic, not object oriented, no advanced data types like matrices or vectors ... The way SAS handles data value formatting is retarded. Up to SAS9.3 it runs only on single core! (Maybe they fix it in 9.4, but I haven't used SAS since 9.3)

But most important for this thread,SAS runs only on Windows (there is a Linux/Unix version but it is different and only run in batch from what I  know, never used it) So why even suggesting it? How does it help OP?  Are you paid by the SAS institute or just trolling? :)

---

### Post by SeijiSensei on 2013-11-10
If all he wants to do is run crosstabulations, then I vote for [**PSPP**]("http://www.gnu.org/software/pspp/"), the GNU clone of SPSS.  Things like R or STATA are overkill for simple crosstabulations.  I used SPSS for years in my earlier life as a social scientist and pollster.  A couple years back I helped analyze a survey we conducted among my college classmates.  I was frankly thrilled to discover that PSPP existed so we could avoid paying for a statistical package we would be using only once every five or ten years.

I'm also a big fan of [**gretl**]("http://gretl.sourceforge.net/"), the GNU econometrics package.  Along with the basics like least squares it also has a wide array of maximum-likelihood methods for things like probit and logit and extensive support for time-series analysis like Box-Jenkins ARIMA modelling.  Most of the results I report in my blog linked below are based on gretl.

Both of these packages are in the Ubuntu repositories.

---

### Post by monkeybrain20122 on 2013-11-10
> **SeijiSensei said:**
> If all he wants to do is run crosstabulations, then I vote for [**PSPP**]("http://www.gnu.org/software/pspp/"), the GNU clone of SPSS.  Things like R or STATA are overkill for simple crosstabulations.  I used SPSS for years in my earlier life as a social scientist and pollster.  A couple years back I helped analyze a survey we conducted among my college classmates.  I was frankly thrilled to discover that PSPP existed so we could avoid paying for a statistical package we would be using only once every five or ten years.
.

I agree, but I am not able to compile PSPP in 13.10 so far. Seems that some library doesn't have the right version (forgot which one, would try again when I have the time) The version in the repository is old and missing some important features: Logit is very important for social scientists, it is in 0.8 but not earlier.If this works and graphic output is not mangled I think pspp would give spss the run of its money, as many social science applications don't really need anything beyond descriptive statistics and logit (it would also be nice if they implement layering in cross tabulation, I don't think this option is available at this point.)

Interesting link.

---

### Post by RichardET on 2013-11-11
> **monkeybrain20122 said:**
> OP asked for a Linux alternative for Minitab, there are plenty of options, free or non free, open or proprietary which all are available to Linux. Yet you come here to advertise for SAS, which is the most closed and most inflexible (Stata is proprietary but more open than SAS and allows more user participations), most inextendable, with the worst inter-portability,--Stata and SPSS data formats are much easier to import to other formats without having a copy of the software,-- , most expensive (~$1000 for a license just for SAS base and Enterprise Guide(?)  that expires in one year and extra licenses for additional modules). 

For the high cost and all its limitations  it is not even that good on many fronts: The programming language is clunky and inflexible,many options appear like ad hoc afterthoughts and lack coherence and logic, not object oriented, no advanced data types like matrices or vectors ... The way SAS handles data value formatting is retarded. Up to SAS9.3 it runs only on single core! (Maybe they fix it in 9.4, but I haven't used SAS since 9.3)

But most important for this thread,SAS runs only on Windows (there is a Linux/Unix version but it is different and only run in batch from what I  know, never used it) So why even suggesting it? How does it help OP?  Are you paid by the SAS institute or just trolling? :)

I am not advertising anything. I do not work for SAS, nor am I a "troll."  I actually resent that accusation. I use GNU/Linux, specifically Ubuntu these days in my spare time, but my day job centers around use of SAS and other less powerful data analytics tools.  And I have done it quite awhile, so I have some perspective.  My background in R is weaker, but it is growing.  I wish to point out that you have some misinformation - SAS works on RHEL in interactive mode, you simply need X running, and there are versions of JMP prior to version 9 which work fine on Linux.  Matrices are handled well in SAS/IML.  

SAS grew out of the mainframe era, obviously decades before languages like C++ were in vogue.  I don't think it is wise to claim one form of programming is superior to another form, since object-oriented vs. non object-oriented is well beyond the scope of this forum.  

But I do get why those from a more modern era might lean in towards R, for many obvious reasons, and where I work there is a growing group of R coders over SAS coders.  In the past I have followed the SAS-R blog on blogger, and the two who maintain it give many different examples of R code with its SAS equivalence for those trying to migrate from one platform to the other.  

The thing which I find most annoying with all the tools other than SAS, is when one wants to read, manipulate, analyze large tables which reside in environments such as oracle, or teradata.  The connection part is easy with ODBC, so one can use Spotfire, SPSS, SAS, JMP, whatever.  But I have found that only SAS allows paged views, so that one can look at the data tables without reading the whole table into memory first - I can assure you that this will max out any PC, and I dont care how many cores you have.  When I do data analysis, I like to view the original data as well as new tables I have created from it in a stream of consciousness fashion so I can think as I go along about what to do next.  There are certain pitfalls one needs to hammer out in any analysis, such as missing values, duplicate rows, many-to-many joins, and a host of others, and performing these data checks are easiest for me in SAS.  But show me the tool which can handle billions of rows as easily as it can handle thousands of rows, without maxing out local resources, and which is easy to use, and free, and I will go there.

---

### Post by monkeybrain20122 on 2013-11-11
> **RichardET said:**
> Matrices are handled well in SAS/IML.  
I know that, but how much does it cost in additional to SAS base? That is my point. SAS is unextendible and locked down and every additional module or feature costs $$$  (and SAS/IML is Windows only)

> But I have found that only SAS allows paged views, so that one can look at the data tables without reading the whole table into memory first - I can assure you that this will max out any PC, and I dont care how many cores you have.  When I do data analysis, I like to view the original data as well as new tables I have created from it in a stream of consciousness fashion so I can think as I go along about what to do next.  There are certain pitfalls one needs to hammer out in any analysis, such as missing values, duplicate rows, many-to-many joins, and a host of others, and performing these data checks are easiest for me in SAS.  But show me the tool which can handle billions of rows as easily as it can handle thousands of rows, without maxing out local resources, and which is easy to use, and free, and I will go there.

[http://www.bnosac.be/images/blog/user2013_presentation_ffbase.pdf](http://www.bnosac.be/images/blog/user2013_presentation_ffbase.pdf)

When I used SAS I wrote macros to detect missing values, duplicate rows and other anomalies to automate the process of cleanup, then only pick a few samples to inspect by eyes to  1) see that the macro works as intended  for anomalies anticipated and 2) catch if there were anomalies that the macro might not have anticipated . I didn't work with a billion rows, only a couple hundred thousands, but even then I wouldn't want to or need to see the whole dataset. We separated the data cleaning/preparation process and statistical analysis as much as possible so the statistician (also me, or may be other people who asked for certain data) shouldn't need to see the database at all.

---

### Post by RichardET on 2013-11-12
Thanks for the link!  I have *Peter* Dalgaard *Introductory Statistics* with *R* , and it has been helpful, but my problem is that most jobs which come my way in the pay scale I need are usually SAS related, and then I never really get a chance to push my envelope with R.

---

### Post by monkeybrain20122 on 2013-11-12
You may want to also check out "R for SAS and SPSS users" by Muenchen. It is probably not very advanced but a good orientation. 
[http://science.nature.nps.gov/im/datamgmt/statistics/R/documents/R_for_SAS_SPSS_users.pdf](http://science.nature.nps.gov/im/datamgmt/statistics/R/documents/R_for_SAS_SPSS_users.pdf)

I also started with SAS, worked with it for a few years. It has been fun but I eventually find it too restrictive. Since we are experimenting with new infrastructures that may eventually free us from SAS, I am lucky to have the opportunity and freedom to explore other stuffs. :)

There is always a trade off between getting paid and having fun. I know a SAS programmer who works in a bank for 20 years and makes 3x as much as I do (doing less work as he doesn't do statistics, only data management and their data are more standardized so easier to handle) I wouldn't want to be in his shoes. I would rather make much less but have fun. :)

---

