---
title: "Lubuntu for my 12-year old nephew?"
date: 2019-08-27
forum: Ubuntu, Linux and OS Chat
---

### Post by ndesign4506 on 2019-08-27
I installed Lubuntu 18.04.03 LTS with GNOME shell and GDM, on an old Lenovo T60 (the most I could afford), to get a simple, flexible user interface for 12-year old David. I'm beginning to have second thoughts, based on my own inexperience.  He wants a laptop for school work, and of course for playing lighter games. His experience so far is limited to Android phones. I will not always be available to maintain his system, and his parents are not interested.

Any suggestions and recommendations for a user-friendly, simple configuration -- and pointers on configuring it -- will be greatly appreciated. 
Thanks, Don

---

### Post by Autodave on 2019-08-27
Do you know the specs on that particular machine?  I tried looking it up, but it was built in many different configurations.

I use Xubuntu, so I am not familiar with that version. But, you should have the option, in Settings, for it to update a lot of stuff on its own w/o user intervention.  Will he have internet available at home?  Wired or wireless?

You could always install something simple like TeamViewer to be able to access his machine from your own.  I do this for my mom and it saves me a lot of transportation time to and from her place. :-)

---

### Post by CatKiller on 2019-08-27
> **ndesign4506 said:**
> his parents are not interested.

Is *he* interested? Personal motivation is the main driver of success.

If he wants a laptop to get stuff done, and he'd enjoy making it do what he wants it to do, then that machine will be perfectly fine. If he just wants to play Fortnite without any hassle, then it's less so.

My three-year-old uses Linux machines well, and it's unlikely that I'll get him a Windows machine at any point, but we're a Linux household. If your nephew's parents aren't tech-savvy, and all his friends are on Windows, being the sole penguin is going to be a tough gig for him. Things like saving on the cost of a Windows licence are pretty abstract benefits when you don't have to pay for it yourself, but not being able to use Windows software is a concrete burden.

---

### Post by Artim on 2019-08-27
Many distros intended for kids use the Xfce desktop (found in Xubuntu) for it's sheer simplicity and speed.

---

### Post by mörgæs on 2019-08-28
I think you made a good choice. He has a virusfree environment which saves him from a lot of worries. 

As for configuration you just need to let the system do all updates automatically. Many elementary schools use web / cloud software so chances are that he is only going to use a browser.

---

### Post by Mark Phelps on 2019-08-28
Really depends a LOT on what the school will require in terms of apps, to do the assignments.  If, as some do, they require Microsoft Office products, even if they provide a really cheap student license, that will not help you, because it will most likely be Office 365 and that does not run in Wine.

---

### Post by GhX6GZMB on 2019-08-28
Well, you already have an installation, let's call it **uncle**, which I hope works and has root rights and a login password.
Make a new user called **nephew** with normal rights (= stay with default settings).
Open your file manager and go to **/home/uncle** and copy everything, including subdirectories.
Go to **/home/nephew** and paste everything.
Open a terminal and execute[B] sudo chown -R nephew:nephew /home/nephew
[/B]
Now your nephew has his own area to work in, and he can't do any damage to the system.

---

### Post by CatKiller on 2019-08-28
[Here's](https://web.archive.org/web/20140111165707/https://joinup.ec.europa.eu/elibrary/case/british-school-switches-students-computers-linux-reducing-costs-and-improving-computin) some information on two British secondary schools that switched to Linux. FWIW, teenage students appear to generally favour KDE. The school that had the full support of the higher-ups was more successful than the one that didn't, which isn't terribly surprising.

The education side of it will likely be *better* with a Linux machine: there are all sorts of goodies just there. As I mentioned earlier, the goofing-off-with-friends may be harder: there are thousands of games that will run on Linux, but they aren't necessarily the ones that he would want to play. Of course, they could be using consoles instead, which makes the multiplayer gaming part moot. Only you could answer that.

Make sure that there's a robust backup system in place. That way, if it all goes pear-shaped from enthusiastic experimentation - we've all been there - the crucial data is safe. Doing a Linux installation is trivially straightforward for a 12-year-old, particularly if you've already established that all the hardware works with Linux.

---

### Post by ndesign4506 on 2019-08-29
It's a T60, Type 6369, 2Ghz Core 2 Duo cpu, 4 (3) GB ram, 80 gb hd, 667 Mhz bus, 15.4" screen -- all that for $50 used.

He has wireless Internet access at home. Thanks for the note about TeamViewer, which I'll check out. Remote, or auto, updating is a goal.

Is he *ever* interested! When I asked what he hoped for on his 12th birthday in a couple of weeks, he blurted, "a laptop"! Not a smartphone, nor a tablet -- laptop only. He went on to state emphatically that he needed it to write school reports & take notes. 
The Lenovo T60 is a heavy beast, but it's maybe more rugged than the new ones, which I can't afford anyway.

Agreed, Xfce seems decidely simpler and more intuitive for an active 12-year old.

That's a key factor, auto updates, thanks! I expect that he'll be on a browser most of the time, as well.

Many thanks for this very useful advice, especially your reference to the meaty, well-written article, [h=2][SIZE=3]"British school switches students' computers to Linux, reducing costs and improving computing knowledge"[/SIZE][/h]

---

### Post by CatKiller on 2019-08-29
The other thing that you're likely to need to check with a used laptop is the battery status: the more they're used, and the more aggressively they're used, the less able they are to hold a charge. You can often get replacements, and they're often not too difficult to change (iFixit sells inexpensive kits with all the odd screw shapes that manufacturers use), but the price of replacement batteries goes up as availability goes down.

---

### Post by Artim on 2019-08-29
[This article]("https://technophobeconfessions.wordpress.com/2015/02/27/converting-libreoffice-writer-documents-to-microsoft-format/") is kinda old now and may not be relevant, but it's how I use LibreOffice to create perfect "Microsoft Word" documents without bothering with Office or any of those online offerings.

---

### Post by ndesign4506 on 2019-08-29
1000 thanks for the excellent advice from so many knowledgeable sources, on my 1st post!

Ultimately, I chose from among your recommendations a distro based on Ubuntu 16.04.3 LTS, *Linux Lite* v3.8. 

It's Xfce 4.12 desktop is just what I had in mind for my overactive nephew. 

I simply burned an ISO image on a DVD on my Windows 10 Lenovo (T61P), booted up with it on the 32-bit Lenovo T60 running Lubuntu v18.04 and watched it run & install, painlessly replacing the Lubuntu version.

However, I'm still left with the occasional need to remove & reinsert the laptop's battery to recover from a stalled boot -- which also happened with Lubuntu. My guess is that David can cope with that annoyance, without damaging anything, hopefully.

Thanks again for your timely help, as David hopes for his first computer in a couple of weeks' time.

---

### Post by ndesign4506 on 2019-08-29
Great idea! Save in .odt format until the very last document version, then save in .doc for compatibility.
Many thanks for this article, which keeps it simple for my young nephew.

---

### Post by slickymaster on 2019-08-29
Thread moved to **Ubuntu, Linux and OS Chat** for a better fit

---

### Post by CatKiller on 2019-08-29
> **ndesign4506 said:**
> I simply burned an ISO image on a DVD on my Windows 10 Lenovo (T61P), booted up with it on the 32-bit Lenovo T60 running Lubuntu v18.04 and watched it run & install, painlessly replacing the Lubuntu version.
The [processor in that laptop](https://ark.intel.com/content/www/us/en/ark/products/27255/intel-core-2-duo-processor-t7200-4m-cache-2-00-ghz-667-mhz-fsb.html) is 64-bit. Support for 32-bit software is on the way out, and 32-bit install images have already stopped. The laptop likely came with a version of 32-bit Windows XP, but only because 64-bit Windows XP was terrible.

---

### Post by Autodave on 2019-08-29
That battery just slides out: no tools needed.  $26 US on Amazon.

---

