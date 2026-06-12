---
title: "Drupal? What does it do?"
date: 2009-07-29
forum: Server Platforms
---

### Post by SoftwareExplorer on 2009-07-29
I'm curious, what does drupal do? It says on its website that it is a content management system, but I don't really know means.

---

### Post by serenityit on 2009-07-29
Content Management is a piece of web code that allows you to update pages of a website without the need of an editor like Dreamweaver or Frontpage (Windows). It is all done within the browser with a WYSIWYG editor.

In short...

1. Design template and upload to CMS
2. Edit pages using CMS admin panel
3. Job done.

---

### Post by FerociousTwig on 2009-07-29
It's even more sophisticated than that too. It's a modular web development solution. Basically it allows you to create fairly advanced web sites / applications without having to do or know much coding. The best part about drupal is that it happens to be open source. Therefore everybody is contributing new plugins for varied purposes everyday. For example, you can get a shopping cart module for ecommerce, or a comment module for a blog. Also, if you do know code, you can write your own plugins and contribute to the project. 

For further info, check out Joomla as well.

---

### Post by SoftwareExplorer on 2009-07-30
Sounds pretty awesome. Thanks for the responses. Ill have to give it a try.

---

### Post by Thirtysixway on 2009-07-31
It also  makes it very easy to setup websites with multiple users, along with roles (groups) and permissions.  I use it for my sites and client sites.

---

### Post by go2dell on 2009-07-31
Just to let you know, I've set up a PPA with updated Drupal5 and Drupal6 packages so that you don't have to install Drupal in Ubuntu and immediately upgrade to a newer version.  I didn't do any of the awesome work to get everything into place for these; I merely updated them to include the very latest available Drupal versions.  They are otherwise exactly as initially published by Luigi Gangitano in Debian.

One interesting note:  the Drupal6 package in Ubuntu hadn't been updated to include Ubuntu MOTU as the maintainer.  I fixed that.  :D

If you're new to Drupal, and unless you have a specific reason for using Drupal 5, then start with Drupal 6.  Drupal 5 is still maintained and supported, but 6 is the current version.  Support for 5 will be dropped sometime shortly after 7 is released, but 6 should be around for a good, long time.

[My Drupal PPA is here]("https://launchpad.net/~scott-testerman/+archive/ppa").

---

### Post by Macchi on 2009-07-31
Drupal is really great! But for a less steep learning curve you should also consider Joomla!, another open source web content management system. 
Joomla has a large number of free templates and more than three thousand extensions. It is often considered to be the market leader for small and medium organizations. 

PS: Drupal supporters, please don't throw stones at me for mentioning this...

---

### Post by darksideforge on 2009-08-26
> **go2dell said:**
> Just to let you know, I've set up a PPA with updated Drupal5 and Drupal6 packages so that you don't have to install Drupal in Ubuntu and immediately upgrade to a newer version.  I didn't do any of the awesome work to get everything into place for these; I merely updated them to include the very latest available Drupal versions.  They are otherwise exactly as initially published by Luigi Gangitano in Debian.

One interesting note:  the Drupal6 package in Ubuntu hadn't been updated to include Ubuntu MOTU as the maintainer.  I fixed that.  :D

If you're new to Drupal, and unless you have a specific reason for using Drupal 5, then start with Drupal 6.  Drupal 5 is still maintained and supported, but 6 is the current version.  Support for 5 will be dropped sometime shortly after 7 is released, but 6 should be around for a good, long time.

[My Drupal PPA is here]("https://launchpad.net/~scott-testerman/+archive/ppa").

AWESOME PPA!!! I've been trying to find a src for the update because the Drupal6 secupdt didn't want to work from the .tar I downloaded!

I was in Mooresville two weeks ago (an hour and a half north of me in SC)...wish I'd known about you then...might've sought you out to buy you a frosty beverage to deal with this wonderful August humidity!
:lolflag:

---

### Post by go2dell on 2009-08-26
Glad you liked it!  I just discovered that Launchpad is slightly confusing because it lists everything as i386 architecture, but the actual PPA repository is correctly marked as architecture "all."  If you have problems because of this, just try downloading the .deb you need and installing with *dpkg -i*.

My main reason for bothering with the PPA is that I'm doing Drupal development at the moment and like the ability to blow away a whole server and create a new one with just one nice little *aptitude install*.  For production machines I typically hand install, but what's the point of including Drupal in Universe if nobody ever uses it?

I'm always love frosty beverages, though I find that Charlotte has a wider selection of them than Mooresville.  :-$

---

### Post by Thirtysixway on 2009-08-28
> **go2dell said:**
> Glad you liked it!  I just discovered that Launchpad is slightly confusing because it lists everything as i386 architecture, but the actual PPA repository is correctly marked as architecture "all."  If you have problems because of this, just try downloading the .deb you need and installing with *dpkg -i*.

My main reason for bothering with the PPA is that I'm doing Drupal development at the moment and like the ability to blow away a whole server and create a new one with just one nice little *aptitude install*.  For production machines I typically hand install, but what's the point of including Drupal in Universe if nobody ever uses it?

I'm always love frosty beverages, though I find that Charlotte has a wider selection of them than Mooresville.  :-$

What's the difference between using the PPA and just downloading it from Drupal.org?

---

### Post by darksideforge on 2009-08-29
> **Thirtysixway said:**
> What's the difference between using the PPA and just downloading it from Drupal.org?

Adding the repos from the PPA allows Synaptic to do the install and takes care of any dependencies as opposed to manually installing via the .tar.

Plus, there's some other good info on his PPA page.

---

### Post by go2dell on 2009-08-29
With the PPA you can use *apt-get install drupal6* (or drupal5) and have the complete dependencies for Drupal installed.  If you download from Drupal.org, you must install the database manually, edit the config files manually, and ensure you have all the necessary Drupal dependencies set up properly first.

In other words, exactly the same thing that will happen if you type *apt-get install drupal6* without the PPA, except that the PPA comes with all (officially) currently known security issues addressed.

---

