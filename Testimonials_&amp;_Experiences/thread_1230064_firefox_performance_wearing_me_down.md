---
title: "firefox performance wearing me down"
date: 2009-08-02
forum: Testimonials &amp; Experiences
---

### Post by yelirekim on 2009-08-02
I'm an open source software supporter in principle, and in practice.  I've been using some linux flavor (fedora, slackware or ubuntu) for a few years now, and generally I've been happy.  There is one major sticking point that I've recently had to come to terms with that is making me think I may have to switch back to windows: firefox performance.

I don't know what it is about firefox on Linux, but my experience with it has just been dismally slow.  I've gone as far as building several versions from source recently (3.5, 3.5b4 and 3.51) in an attempt to make this better, but still no dice.

I'm a web developer, and when I'm in the front end development phase for any given project I probably spend a good 50% of my day refreshing pages within firefox.  Two things that just absolutely astound me about this whole thing is that I can pull up a windows virtual machine, run firefox there, and it's faster... The second thing is that DNS resolution or networking issues don't really seem to have anything to do with the slow performance, I usually develop locally.

I've been reading through the "100 papercuts" usability drive for the upcoming Karmic release, and I think all of that is just great.  But from my perspective, working with the mozilla team to hammer out some of the issues firefox has on linux might be a better use of time, since I imagine a slow web browser probably trumps any small usability tweaks you will encounter within an operating system.

Anyway, this is just my two cents, has anyone else had any similar experiences, any ideas as to how we could improve this issue?

---

### Post by lswb on 2009-08-03
You're certainly not alone in your observation, many have noted it in these forums and elsewhere. The most common explanation I have seen is that firefox for linux is not compiled with all the optimizations of the Windows version. I don't know much about that, but it if it was that simple you'd thing *someone* would have compiled a faster version and have it available *somewhere!*

---

### Post by nedkelly on 2009-08-03
I can also say this is an observation that I have made.

I do not know why this is, but seems stupid if firefox is not compiled with all the optimized options

---

### Post by TenPlus1 on 2009-08-03
You could always try SwiftFox, this is basically firefox that has been compiled and optimized for certain systems and is definately a LOT faster:

[http://getswiftfox.com/deb.htm](http://getswiftfox.com/deb.htm)

Also, check out the Firefox tweaks guide for some help also:

[http://www.tweakguides.com/Firefox_1.html](http://www.tweakguides.com/Firefox_1.html)

---

### Post by tlutz on 2009-08-03
I run windows on one of my machines and have switched from Firefox to Google Chrome because I felt FF was too unresponsive, so I'm not sure switching back to windows would make you a happy camper.  It's a shame, because I really like using Firefox, but too often I found myself counting out loud to double-digits while Firefox loaded.

---

### Post by yelirekim on 2009-08-03
Using Chrome isn't an option because of firebug: [http://getfirebug.com/](http://getfirebug.com/)

It's far and away the most useful tool for front end web development.

Thanks for the swiftfox suggestion, I'll definitely give it a look, any idea why the version of firefox that comes with Ubuntu isn't compiled like that by default?

---

### Post by khelben1979 on 2009-08-03
I haven't experienced Firefox faster with Windows on my system, in fact it's often slower due to infections and trojans which keeps on coming in. I've got anti-virus and spyware which is supposed to take care of it, but because of this extra software my Windows system is actually way slower than any Linux distribution.

It's possible that Firefox might be faster on a Windows system if you're able to keep it clean for viruses and have 2 GB of RAM.

---

### Post by HappyFeet on 2009-08-03
Firefox for me has always run great. I don't have an answer why *you* are having a problem, but I myself love it, and think it is a great browser. Perhaps you should try Opera or Swiftfox. Going back to windows just because of a browser seems a little extreme, when there are good alternatives out there.

---

### Post by ngsupb on 2009-08-03
ye, FireFox sucks on Ubuntu. They should do something about it
Other things are ok

---

### Post by jocampo on 2009-08-03
Take a look on this article about browsers on Linux and memory footprint

[http://www.ibm.com/developerworks/linux/library/l-linux-memory.html]("http://www.ibm.com/developerworks/linux/library/l-linux-memory.html")

My personal experience is that my Firefox runs ok on Ubuntu but slower on Windows. I do not think Firefox sucks on Linux but it uses a some RAM because some included features and design. If your laptop or PC runs with 2gb of RAM you should not have problem.

That said, Firefox is cool but memory hungry. There are other options if you are looking for a good compromise between features and performance, like Dillo or Opera.

---

### Post by SecretCode on 2009-08-03
Firefox is definitely memory hungry - despite all the reports that it's "fixed" in Firefox 3 or each new version. The only time I've found Fx to be slow on Ubuntu is when it's using tons of memory - can get quite responsive again if I close most of the tabs (into Session Manager sessions for later work). 

And the same thing arises on Windows.

---

### Post by yelirekim on 2009-08-03
I have 3gb ram and a 2.0ghz core 2 duo processor, which should be more than enough to handle it.  But I'll just give you an example:

```

top - 12:28:41 up  2:44,  3 users,  load average: 4.14, 2.37, 1.73
Tasks: 172 total,   2 running, 170 sleeping,   0 stopped,   0 zombie
Cpu(s): 46.1%us, 40.0%sy,  0.0%ni,  6.1%id,  7.5%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   3017696k total,  3001236k used,    16460k free,    25448k buffers
Swap:  6385796k total,   175348k used,  6210448k free,  1996456k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                      
 8160 mike      20   0 1526m 698m 672m S   78 23.7  75:28.65 vmware-vmx                                                                                   
 6943 mike      20   0  932m 267m  26m S   64  9.1  23:00.19 firefox   

```

there is the first few lines of output from top, there is one item that takes up more resources than firefox: my windows virtual machine, but that virtual machine is running adobe photoshop cs4, adobe flash cs4, internet explorer, and firefox all at the same time.  This isn't during a particularly intense firefox session either, I have the ubuntu forums open, a google search, my basecamp account and the html5 spec, all pretty light things to have loaded, but firefox still sits there and eats the crap out of my CPU for whatever reason.

Furthermore, firefox is more responsive inside that virtual machine than it is from within ubuntu.  I know a lot of users would like to bury their heads in the sand and say that "firefox runs great on linux obviously you're doing something wrong", but I use Chrome, Opera, FF 2+3, IE 6+7+8, and Safari on a daily basis in order to do compatibility testing.  I'm WAY too aware of what it means when a browser is running slowly.  I've built firefox from source, built the chromium from source (oh god the pain) and generally spent more time using a variety of web browsers than I would have ever cared to, but it's part of my job.  It just saddens me that there isn't better native performance for FireFox inside ubuntu, because otherwise Ubuntu generally makes me much more efficient in all other aspects of my job.  But this one thing is just such a huge part of what I need to do, that it can't be overlooked.

Anyway, I did try out swiftfox and I have noticed a moderate performance increase, still not approaching what I see from windows though.  If anyone knows how to fix this, please let me know!

---

### Post by HavocXphere on 2009-08-03
Install 2 versions of FF: One for general surfing and one for actual work.

Switch off remembering history and clear the cache regularly.

Also maybe read up on the database backend of FF...lots of the problem seem to be coming from there. There is something about compacting the sql DB that is supposed to help.

And switch off ip6 in the about:config page of ff.

---

### Post by SecretCode on 2009-08-03
Hmm. Well my firefox performance was initially much faster in my ubuntu guest than on my windows xp host. 

The culprit may not be the overall capabilities of firefox on a given system, but the precise condition of the profile. To compare the two, you'd need to clear the cache* and have the same set of extensions installed.

* For good performance, keep the cache quite small, unless you have a particularly slow internet connection. Also reduce the 'keep my history for' setting to a much smaller setting, e.g. 20 days not 90. I've got the feeling that Fx can slow down quite a bit managing large cache and/or history.

** eta: and the other tips that HavocXsphere gave :)

---

### Post by yelirekim on 2009-08-03
I actually just stumbled upon that solution about ten minutes ago, I have a custom build of Shiretoko (FF 3.5.1) that I compiled having stripped out a bunch of unessential features from the browser, and adding some of the efficiency options, removing pretty fonts, debug etc from the build.  The resulting browser is much faster.

Additionally, I found that the previous custom builds I was making were hindered because I continued to use my existing firefox profile from the original ubuntu install, so this time when I rebuilt from source I used the profile manager to make a clean profile before starting the browser up, and now have my custom build, and the default ubuntu install running on two separate profiles.

This STILL isn't as fast as if it were on Windows, but it's manageable, enough that I can still hold on to Ubuntu as my primary operating system.  But I still stand by my statement that the default FireFox build on Ubuntu needs some serious performance tweaking.  All of these arcane commands, building from source, managing profiles, is just way outside the reach of most users.

---

### Post by moodle on 2010-05-03
Firefox remains painfully slow compared to Windows in Ubuntu 10.04.  I have 2GB RAM on my machine, and it's running Windows Vista and Ubuntu duel boot.

Something does need to be done about this, but it seems no matter how many times it is reported (I have seen the issue raised in 2007), nothing is done about it.

---

### Post by lancest on 2010-05-03
Not seeing any big slowness issues from Firefox (except maybe startup once in a while)

These day's I'm pretty picky about the speed of my Ubuntu OS. 

Google Chrome blazes on Ubuntu.
For general usage nothing to complain about there.

---

