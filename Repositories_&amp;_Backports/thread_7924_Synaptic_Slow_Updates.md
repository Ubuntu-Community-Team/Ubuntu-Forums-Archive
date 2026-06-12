---
title: "Synaptic Slow Updates?"
date: 2004-12-12
forum: Repositories &amp; Backports
---

### Post by ZephyrXero on 2004-12-12
Hi, I'm brand new to Ubuntu... just installed it for the first time.

I'm just wondering why the packages in synaptic are all so out of date? I installed Blender and it's saying that version 2.33 (about 6 months old or so) is the newest version. It also has Firefox using some sort of weird 9.3 and 1.0PR blend, why can't I just use 1.0?

I installed with the Warty 4.10 disc. I added all the listed repositories to my list as well. Are there just not enough people contributing to keep this stuff up to do date or have they not passed some sort of approval yet?

I was using Gentoo...but it's way too hard for a newb, so now I am trying Ubuntu b/c it is supposed to be user friendly...I hope the rumors are true :/

---

### Post by jdong on 2004-12-12
Once again, we've discussed this over and over in the context of Firefox 1.0: After ubuntu makes a stable release, package versions stay fixed; except for security-vulnerable package in main.

If you'd like to see new apps, try backports: [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net)

Feel free to file feature requests if you would like to see some other package backported.

I already have Firefox 1.0, GAIM 1.1.0, etc.

---

### Post by ZephyrXero on 2004-12-12
Ok, well... that's great, but how come it was not included with the install as an option? The "universe" and whatnot servers were...

---

### Post by jdong on 2004-12-12
because backports are unofficial -- built by me , after I got extremely tired of choosing between:

1. Using old desktop software with Warty
2. Constantly dealing with quirks and bugs in Hoary


They aren't supported by Ubuntu, aren't MADE by the Ubuntu team, well, you get the point! LOL.

---

### Post by LongTooth on 2004-12-13
jdong, I'm thinking about adding your repository to my source.list. How do I go about updating Firefox and Gaim? Could I use Synaptic? Since I've got Flash, Java and Mozplugger installed and working I'm worried this upgrade will screw-up my browser or system. If it does, how easy is it to get back to the original packages? I'm running Warty and before I would upgrade to Hoary I think I'll wait until the official release. But I'd still like to run the latest Firefox and Gaim. Thanks for any tips.

---

### Post by ZephyrXero on 2004-12-13
well, in that case... thanks for the hard work jdong :)

---

### Post by ZephyrXero on 2004-12-13
I followed the instructions on the backport site and it's not working I get the error messages:

"Could not download repository indexes:

[http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/source/Sources.gz:](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/source/Sources.gz:) 404 Not Found

[http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/source/Sources.gz:](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/source/Sources.gz:) 404 Not Found"

---

### Post by jdong on 2004-12-14
[QUOTE=ZephyrXero]I followed the instructions on the backport site and it's not working I get the error messages:

"Could not download repository indexes:

[http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/source/Sources.gz:](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/source/Sources.gz:) 404 Not Found

[http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/source/Sources.gz:](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/source/Sources.gz:) 404 Not Found"[/QUOTE]


Don't add deb-src entries -- only deb entries!

I have no source packages for the backports areas, since you can find them at Ubuntu's and Debian's repositories -- SF.net was already getting mad about me using PWS to serve an APT repository getting ~200 downloads / day! 



P.S. I will be moving the repository to some fancy new Sourceforge thingie ... I'll let you guys know the outcome.

---

### Post by jdong on 2004-12-14
[QUOTE=LongTooth]jdong, I'm thinking about adding your repository to my source.list. How do I go about updating Firefox and Gaim? Could I use Synaptic? Since I've got Flash, Java and Mozplugger installed and working I'm worried this upgrade will screw-up my browser or system. If it does, how easy is it to get back to the original packages? I'm running Warty and before I would upgrade to Hoary I think I'll wait until the official release. But I'd still like to run the latest Firefox and Gaim. Thanks for any tips.[/QUOTE]

After adding the entries into sources.list, use either Synaptic or apt-get dist-upgrade to upgrade. It really doesn't matter -- it's a repository, just like Ubuntu's.

Flash and Java are confirmed working in the latest backports (there was a Java bug a while back -- squashed in 12 hours, LOL). I'm not sure about MozPlugger, but it should also work fine.

If you want to revert to Warty versions, Synaptic has **force version** options, or do **apt-get install mozilla-firefox/warty** to force a Warty downgrade.

---

### Post by CowPie on 2004-12-15
> **jdong]Once again, we've discussed this over and over in the context of Firefox 1.0: After ubuntu makes a stable release, package versions stay fixed said:**
> http://ubuntu-bp.sourceforge.net[/url]

Feel free to file feature requests if you would like to see some other package backported.

I already have Firefox 1.0, GAIM 1.1.0, etc.
 Hi,
most do not know this, please place a sticky with such knowledge?

I was vry worried until red this.

---

### Post by jdong on 2004-12-15
Well, we plan to add some sort of link to Backports, or some sort of Howto. The Howto's definitely a possibility, but that forum is VERY cluttered.


Backports is an unofficial project started by me, not supported by Canonical, Ltd. If you read the thread in Community Forums ("Backports, Anyone Interested?"), you'll see that developers have a rather **negative** view on Backports. Since we are official support forums, we can't go against the view of Canonical!

We'll definitely try to put some sort of link on the front page.

---

### Post by CowPie on 2004-12-16
[QUOTE=jdong]Well, we plan to add some sort of link to Backports, or some sort of Howto. The Howto's definitely a possibility, but that forum is VERY cluttered.


Backports is an unofficial project started by me, not supported by Canonical, Ltd. If you read the thread in Community Forums ("Backports, Anyone Interested?"), you'll see that developers have a rather **negative** view on Backports. Since we are official support forums, we can't go against the view of Canonical!

We'll definitely try to put some sort of link on the front page.[/QUOTE]
 HI, jdong please help as none will reply to my help cries.

---

### Post by HiddenWolf on 2004-12-25
[QUOTE=jdong]

I already have Firefox 1.0, GAIM 1.1.0, etc.[/QUOTE]
MY HERO!

---

### Post by Zolotnik1242 on 2007-05-15
> **jdong said:**
> Don't add deb-src entries -- only deb entries!

I have no source packages for the backports areas, since you can find them at Ubuntu's and Debian's repositories -- SF.net was already getting mad about me using PWS to serve an APT repository getting ~200 downloads / day! 



P.S. I will be moving the repository to some fancy new Sourceforge thingie ... I'll let you guys know the outcome.


[Loans pollution Mortgages Yahoo Bankruptcy](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

