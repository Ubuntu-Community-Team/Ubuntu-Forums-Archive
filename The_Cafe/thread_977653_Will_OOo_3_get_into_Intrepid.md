---
title: "Will OOo 3 get into Intrepid?"
date: 2008-11-10
forum: The Cafe
---

### Post by shane2peru on 2008-11-10
Hey, I'm wondering if anyone knows   1.  If OpenOffice3 is going to be put into the Intrepid repos?  2.  Where I can find out this kind of info? (in an official statement or otherwise written) without having to post this on the community forums where opinions are not necessarily the views of the official release. 

It is more of a question of curiosity than anything.  Traditionally OO.o has not been released in the repos as an upgrade (correct me if I'm wrong here), but rather released in the next version.  Which would mean we will wait 6 months for it to come out in the 9.04 edition of Ubuntu.

Shane

---

### Post by snowpine on 2008-11-10
The current plan is that OO3 will be added to the "backports" repo sometime in December, which will give the Ubuntu team enough time to work through any bugs.

You'll need to enable the backports repository to get it using the Update Manager or sudo apt-get upgrade. Ubuntu's policy is to never make a major version change in the main repository after the official release, only minor changes for security/stability.

---

### Post by Skripka on 2008-11-10
OR....


1) You could go to their website, download the big tar.gz of packages

2) Completely remove all trace of OOO2 from your system

3) Open the tar.gz and extract

4) Open a terminal cd to the BIG folder of debian packages and:

[CODE]
dpkg -i *.deb
[/QUOTE]

[you'll need to install one deb that is hidden in a sub-folder by yourself, this particular package will not intstall if any leftovers of OOO2 are on your system....there is a specific terminal command to make this go easy....but I can't remember what I did right now]

And BAM.  You have OOO3 :popcorn:



OR, there is a still easier method for Ibexers:

http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml

---

### Post by Majorix on 2008-11-10
@OP:
1. Not exactly "Intrepid" repos, but it should show up in the backports, perhaps with an alpha of 9.04.
2. I too would like to know this :)

---

### Post by snowpine on 2008-11-10
2) Where to find this info: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

ps I used the same link as Skripka, it was very very easy: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by Majorix on 2008-11-10
> **snowpine said:**
> 2) Where to find this info: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

I know of that page, but have always thought it announced only the releases that have already made it into the repos. If I am not mistaken, the OP wants to know if he can "sniff the air" to see if the package is coming :)

---

### Post by snowpine on 2008-11-10
> **Majorix said:**
> I know of that page, but have always thought it announced only the releases that have already made it into the repos. If I am not mistaken, the OP wants to know if he can "sniff the air" to see if the package is coming :)

As I mentioned in my original post, there is no need to "sniff the air" when OO3 will to the main Hardy or Intrepid repositories, because the answer is "never." :)

This is a good introduction to how backports work: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

And the best source of information for future backports packages is: [https://bugs.launchpad.net/intrepid-backports](https://bugs.launchpad.net/intrepid-backports)

In other words, if you want something added to the backports, you file it as a "bug" so that the developers can consider it (and yes, they are aware people want OO3). :)

---

### Post by shane2peru on 2008-11-10
> **Skripka said:**
> OR....


1) You could go to their website, download the big tar.gz of packages

2) Completely remove all trace of OOO2 from your system

3) Open the tar.gz and extract

4) Open a terminal cd to the BIG folder of debian packages and:

```

dpkg -i *.deb

```

[you'll need to install one deb that is hidden in a sub-folder by yourself, this particular package will not intstall if any leftovers of OOO2 are on your system....there is a specific terminal command to make this go easy....but I can't remember what I did right now]

And BAM.  You have OOO3 :popcorn:



OR, there is a still easier method for Ibexers:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Thanks for this link!  Looks simple enough!  I did have it installed before I had to do a new installation.  I will give this link a try.


> **snowpine said:**
> 2) Where to find this info: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

ps I used the same link as Skripka, it was very very easy: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Cool, I didn't know about this site!

> **Majorix said:**
> I know of that page, but have always thought it announced only the releases that have already made it into the repos. If I am not mistaken, the OP wants to know if he can "sniff the air" to see if the package is coming :)

Yes, you are correct, I was looking to 'sniff the air'  and see what is coming down the trails.  I don't like to enable Backports, because I then forget to disable it.  Course using unknown repos too, is risky as well.  Thanks for the responses.

Shane

---

### Post by snowpine on 2008-11-10
> **shane2peru said:**
> Course using unknown repos too, is risky as well.  Thanks for the responses.


The 'deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main' repository (the one mentioned in the softpedia.com instructions) can be considered "safe and trusted". :)

---

### Post by andrewabc on 2008-11-10
I was about to install calcs ppa, and when the server thing refreshed it showed 100 updates and 195mb. I was a bit put off by all the updates and the size of it to get OOo3. So I'll have to wait for official version.

Also if ubuntu team is waiting until December to put in backports, hopefully they use 3.0.1 version which is supposed to be released in December and has many bug fixes.
[3.0.1 release date December 9th](http://wiki.services.openoffice.org/wiki/OOoRelease301)
Currently only 3 showstopper bugs need to be fixed

---

### Post by snowpine on 2008-11-10
> **andrewabc said:**
> I was about to install calcs ppa, and when the server thing refreshed it showed 100 updates and 195mb. I was a bit put off by all the updates and the size of it to get OOo3. So I'll have to wait for official version.

Also if ubuntu team is waiting until December to put in backports, hopefully they use 3.0.1 version which is supposed to be released in December and has many bug fixes.

195mb seems quite reasonable for an entire office suite. :)

You'll find that the "official" version from the OO.org website is 155mb, but it requires a more detailed installation process...

---

### Post by andrewabc on 2008-11-10
With Calcs PPA do I need to uninstall openoffice 2 first? Anywheres I've read it doesn't mention this. I'm guessing I don't since it just updates all the openoffice 2 stuff (not having OOo2 and OOo3 installed at same time)?

---

