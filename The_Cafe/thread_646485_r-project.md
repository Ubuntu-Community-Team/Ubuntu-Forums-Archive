---
title: "r-project"
date: 2007-12-21
forum: The Cafe
---

### Post by satimis on 2007-12-21
Hi folks,


Any folk has experience on r-Project;
[http://www.r-project.org/](http://www.r-project.org/)

Please shed me some light on its main application with examples.

The package is availabl on Ubuntu repo;

$ apt-cache policy r-base-html```

r-base-html:
  Installed: (none)
  Candidate: 2.4.1-1
  Version table:
     2.4.1-1 0
        500 http://us.archive.ubuntu.com feisty/universe Packages

```

$ apt-cache policy r-doc-pdf```

r-doc-pdf:
  Installed: (none)
  Candidate: 2.4.1-1
  Version table:
     2.4.1-1 0
        500 http://us.archive.ubuntu.com feisty/universe Packages

```


I have been googling a while, Not much information discovered.


What is R?
Introduction to R
has some explanation there on the application of r-project.  


What is the difference in application amongst;

SPSS
[http://www.spss.com/](http://www.spss.com/)
The commercial statistic computing software

PSPP
[http://www.gnu.org/software/pspp/](http://www.gnu.org/software/pspp/)
The Open Source statistic computing software

and

R-Project
???


I know the former 2.  SPSS is very expensive.  PSPP is free to use.  I want to test PSPP if I have time.


TIA


B.R.
satimis

---

### Post by bruce89 on 2007-12-21
All I know is that Gnumeric uses a lot of code from them.

---

### Post by mali2297 on 2007-12-21
I have no experience with SPSS, but I would think that R is more advanced and less friendly to the casual user. 

R is popular among statisticians in the academia. Since the R project  is open source, they can make their new statistical methods available for everyone through extension packages.

To give a simple example on how to use R, here is a two sample t-test for simulated data.
```

> x<-rnorm(10,mean=2,sd=1)
> y<-rnorm(8,mean=1,sd=1)
> x
 [1] 2.6672517 2.9638705 0.8180030 3.8318896 1.0753156 2.8041727 1.2032993
 [8] 0.9976599 1.3971639 1.4489096
> y
[1]  1.62775562 -1.51850365  0.81710690  1.00699969  0.02306238 -1.46828786
[7]  2.16801164  2.87481070
> t.test(x,y,var.equal=1)

        Two Sample t-test

data:  x and y
t = 1.966, df = 16, p-value = 0.0669
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
 -0.0962559  2.5550242
sample estimates:
mean of x mean of y
1.9207536 0.6913694

```

---

### Post by satimis on 2007-12-22
Hi folks,



Thanks for your advice.


Are there projects applying R?  TIA


satimis

---

### Post by daynah on 2007-12-22
I tried all three while doing a psych project (which I made a very good grade on!) I had gotten SPSS for the class, but it was having problems in Vista and IT hadn't gotten back to me. It wasn't that I had waited to the last minute, I just needed to print what I had already done!

Anyway, I decided that I shouldn't just sit on my butt and wait for IT, that I'll at least try and see what R and PSPP can do, after emailing my teacher of my troubles and the lengths I was going to solve them.

I tried PSPP first and that quickly became a no go. PSPP has no gui front end, and I barely knew what I was doing. How was I to import my data? How do I even KNOW the names of the tests I had perfrmed in SPSS to tell PSPP? I quickly moved onto R.

R has a gui front end and it's very pretty. I was able to import my DATA from SPSS, but not my statistical analysises. I actually liked the way R presented the data better that the way SPSS presented the data, because in SPSS you have to switch back and forth like... "Okay was 0 female and 1 male or the other way around?"

So using the data in R, I started going through the tabs in find the basic statistical analysis and... I couldn't. I had NO idea what these tests were. I was looking for things like the mean and the standard deviation. The hardest test D wanted it to do was find the Pearson Correlation, I didn't even want a T Test (which I couldn't find either). In short, I had never heard of any of the tests it had. They all seemed to have a person's have it in, no basic stats.

OH and RKWard is the frontend to R that I used.

Both R and PSPP was way out of my league. PSPP because I don't have time to be screming around with commands when I'm having a hard enough problem with stats, and R because I'm just starting in research methods. I'm not even focusing on the stats. So chill out and gimmie the easy ones!

I don't know how good you are in stats. I recommend you install R and see for yourself (I mean, in linux if you uninstall you actuall uninstall so it's no biggie). But if you know you haven't learned a lot of stats, don't even think about it. :(

---

### Post by IanH on 2007-12-22
It would help to know what you are trying to do. R is one of the most powerful and versitile statistical packages out there, and can do almost anything you want with statistics. The official documentation is pretty much useless to a beginner, but there are a ton of tutorials out there that would be more help. I've found this one to be fairly useful: [http://zoonek2.free.fr/UNIX/48_R/all.html](http://zoonek2.free.fr/UNIX/48_R/all.html)

There are also a couple of gui frontends you might want to check out, but I haven't found them to be that useful. The main ones are Rkward, which currently lacks support for a lot of common tasks, and R-Commander, which is pretty basic.

Otherwise, you'll have to get familiar with the command language. I'm not sure what you are trying to do, but for a brief example:

#Load in a csv file, and save as a dataset named data
data<-read.csv('~/mycsv.csv')
#Get basic summary statistics on all variables
summary(data)
#Linear regression
model<-lm(y ~ x1 + x2, data=data)
summary(model)

Hope that helps.

---

### Post by satimis on 2007-12-24
Hi daynah,


Thanks for your advice.

> 
OH and RKWard is the frontend to R that I used.

What is OH?  Googling did not help me.  I found RKWard;

RKWard - front end of R
[http://rkward.sourceforge.net/wiki/index.php?title=General_FAQ](http://rkward.sourceforge.net/wiki/index.php?title=General_FAQ)

RKWard
[http://en.wikipedia.org/wiki/RKWard](http://en.wikipedia.org/wiki/RKWard)


> 
I don't know how good you are in stats. I recommend you install R and see for yourself (I mean, in linux if you uninstall you actuall uninstall so it's no biggie). But if you know you haven't learned a lot of stats, don't even think about it. :(

I never did stat computing.  I learned stat in school long time ago.  It is for curiosity to pursue the r-project.


satimis

---

### Post by satimis on 2007-12-24
> **IanH said:**
> It would help to know what you are trying to do. R is one of the most powerful and versitile statistical packages out there, and can do almost anything you want with statistics. The official documentation is pretty much useless to a beginner, but there are a ton of tutorials out there that would be more help. I've found this one to be fairly useful: [http://zoonek2.free.fr/UNIX/48_R/all.html](http://zoonek2.free.fr/UNIX/48_R/all.html)

There are also a couple of gui frontends you might want to check out, but I haven't found them to be that useful. The main ones are Rkward, which currently lacks support for a lot of common tasks, and R-Commander, which is pretty basic.

Otherwise, you'll have to get familiar with the command language. I'm not sure what you are trying to do, but for a brief example:

#Load in a csv file, and save as a dataset named data
data<-read.csv('~/mycsv.csv')
#Get basic summary statistics on all variables
summary(data)
#Linear regression
model<-lm(y ~ x1 + x2, data=data)
summary(model)

Hope that helps.
Thanks for your advice and URL.


I pursue the r-project mainly for curiosity and interest.  I think I have to find another PC to test R.  I'm now working on a VM built on Mail server running Ubuntu 7.04 as Host OS.  This is a fast machine, AMD Athlon64 X2 with 4G RAM.  But I can't test R on the server, I suppose.  CentOS 5 is running as Guest OS on the VM.  Would it be a good idea testing R on CentOS 5?


satimis

---

### Post by a3arar on 2010-08-28
R is a programing language and statistical package with many libraries.  It is free and heavily used in academia because they can write their own functions and share.  R thrives by is heavily object oriented programming approach.

R is very advanced in the areas of arrays, matrices, lattices, and graphics.  Vectors are the main ingredient to it's data structure.

R would be the best thing you'll learn for data analysis.  There are packages that integrates R with other programming languages like rcom and statConn.  A fact that makes R a lucrative statistical package for individuals, researchers, small businesses, and programmers.  It has a strong steep learning curve, but that is due to the Statistical Theories and practices embedded in its functions rather than difficulty of use.  But, that the nature of such packages whether Matlab, SPSS, and definitely SAS.

You can get R from ubuntu by typing:

sudo apt-get r-base-html 

and ubuntu will download all the packages that you need.
R is documented extensively on its website, the help package you download with it, or articles and books.  There are plenty of resources on the web.  Just google "R-stat objects", and you will get tons of information and links to resources.

Good luck.

---

### Post by beew on 2010-08-28
The R packages in the Ubuntu repo are very outdated. You should get them from one of the R mirrors instead. Add a PPA line to your source list by following the instructions here
[http://cran.r-project.org/bin/linux/ubuntu/README]("http://cran.r-project.org/bin/linux/ubuntu/README")

SPSS is mainly used in the social sciences. It is for intermediate users but R has a lot more advanced features and its development is quite cutting edge, it is one of the best  if not the best stat package around. Actually you don't really need a gui for R. It has a gui called Rcmdr but it is pretty much the same as running from the terminal itself. Never used Rkward but will look into it.

SPSS is easy to use with its point and click interface and you can also write codes ("Syntax" they call it)

As for PSPP, one word: garbage. It has a gui like SPSS but a look at the tool menus will show that it barely has any function. It may be good as a  spreadsheet and that's it and even gnumeric has more advanced statistical features than PSPP. These people should stop Saying that PSPP is meant to be a replacement for SPSS or they should be laughed off the stage. Maybe in a few years it will grow into something more serious, but right now it is a joke.

**P.S. Just realized this is a very old thread and I was fooled by a3arar who posted before me.** :)

---

