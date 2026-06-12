---
title: "Willow"
date: 2006-10-04
forum: Server Platforms
---

### Post by snelo on 2006-10-04
Hi, 

Does anyone out there use Willow - content filter - found a link to it on the WIKI *sounds* fantastic.

However - I'm getting a *little* frustrated at getting it to work.
My first error was that I couldn't "import profile" at line 44.  I eventually found out that I needed a "non-free" package to get that and now it is having a spak:
ImportError: no module named exefilter.

Does anyone have an idea?  Has anyone gotten it going and remembers how and can give me some advice.

Thanks in advance.
Andrew

---

### Post by murraymints on 2006-10-04
I tried out this app a couple weeks ago, after intalling the non-free package (somthing like python-profiler right?) it then worked fine.

What command are you using to try and run it?
What does your config file look like?

I found it to be great at blocking adult websites but alittle tricky to set up to also block game websites so I'm going to look at dansguardian next.

---

### Post by snelo on 2006-10-04
YES!!!!!!!!!!!!!!!!!

](*,) 

I had gotten the python-profiler - and then the error message moved to a different part of the file.

For anyone else who is trying this ...
you need to get python-profiler from [http://packages.debian.org/testing/python/python-profiler](http://packages.debian.org/testing/python/python-profiler)
you also need python-central (there is a link on the profiler page)

Then change the default willow.conf file - you need to take out the filters you haven't defined - exefilter and flashfilter.  Then it works....
DOH... Now I have to work out how to get it to use my password so I can remotely administer it....

Thanks for your support murraymints

---

### Post by Macchi on 2006-10-05
I have installed Willow on my son's computer and had the same issue with the missing dependency. I can't remember how I solved the problem, maybe the workaround has been mentioned somewhere else on the web.

Soon I plan to have a look at DansGuardian. There is also a script called "parental-protection" but it did change a lot of things on my test system. I prefer call it simply content filtering since it can be used for homes and for professional environments. 

Willow seems to provide some basic filtering, and obviously it is better than no filtering att all. But I am still unconfortable with a few things:

a) The access lists are static, I would prefer to be able to synchronize blacklists dynamically with a good known source.

b) The domain names keywords are visible on the file system.

c) Installation, operation and maintenance are neither trivial nor transparent. 

d) There is no authorization barrier to deactivate the filter

e) The filter is centered on the English language and we also use two other languages at home. Thus I would have to customize lists for two other languages.

 As I understood the filtering lists are static, provided with the installation package and can be adjusted manually. The problem is

---

