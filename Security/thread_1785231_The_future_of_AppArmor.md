---
title: "The future of AppArmor"
date: 2011-06-18
forum: Security
---

### Post by desire.linux on 2011-06-18
On Wikipedia it says:

> In September 2007, Novell laid off the AppArmor team.It makes me wonder what the future of AppArmor is. I really like this application.

---

### Post by tgm4883 on 2011-06-18
> **desire.linux said:**
> On Wikipedia it says:

It makes me wonder what the future of AppArmor is. I really like this application.

Being that was back in 2007 and that the developer [mailing list]("https://lists.ubuntu.com/archives/apparmor/2011-June/thread.html") seems to be active I would say it's future is bright.

---

### Post by crispy_420 on 2011-06-18
Read this:

[http://www.linuxplanet.com/linuxplanet/reports/7203/1/](http://www.linuxplanet.com/linuxplanet/reports/7203/1/)

Canonical is now a leading group behind it and there is kernel integration. To me that means it may be around a little bit longer.

---

### Post by bodhi.zazen on 2011-06-18
> **crispy_420 said:**
> Read this:

[http://www.linuxplanet.com/linuxplanet/reports/7203/1/](http://www.linuxplanet.com/linuxplanet/reports/7203/1/)

Canonical is now a leading group behind it and there is kernel integration. To me that means it may be around a little bit longer.

I recently suggested Canonical needs to improve the documentation of Apparmor.

Fedora and selinux are much more mature then Apparmor, both in terms of the rules, to the tools to manage those rules (there are graphical tools to manage selinux policy), debugging tools, and documentation.

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/)

Here is hoping Canonical steps up with apparmor, with documentation and with graphical tools.

---

### Post by wacky_sung on 2011-06-18
Compare using Apparmor, OpenSuse is much better equip than Ubuntu in term of apparmor tools. Whereas Ferdora is still leading use of SElinux.

---

### Post by uRock on 2011-06-18
> **wacky_sung said:**
> Compare using Apparmor, OpenSuse is much better equip than Ubuntu in term of apparmor tools. Whereas Ferdora is still leading use of SElinux.

What grounds are you basing your statement on? (Specifically the OpenSuSe vs Ubuntu apparmor.) I am interested to know the two distros handle AppArmor differently.

---

### Post by wacky_sung on 2011-06-18
> **uRock said:**
> What grounds are you basing your statement on? (Specifically the OpenSuSe vs Ubuntu apparmor.) I am interested to know the two distros handle AppArmor differently.

Probably first hand experience using OpenSuse on their Apparmor tools is better than a thousand words to explain.

---

### Post by cariboo on 2011-06-18
> **wacky_sung said:**
> Probably first hand experience using OpenSuse on their Apparmor tools is better than a thousand words to explain.

What's the name of the app? What's it look like? If you're going to make a claim like that, you have to back it up. :)

---

### Post by bodhi.zazen on 2011-06-18
SUSE had a graphical tool(s) to configure apparmor, but I have not looked at SUSE in years...

/me goes to DL latest suse ...

---

### Post by bodhi.zazen on 2011-06-18
Looking at the suse site:

[http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-security/](http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-security/)

[http://doc.opensuse.org/products/draft/SLES/SLE-apparmor-quick_draft/](http://doc.opensuse.org/products/draft/SLES/SLE-apparmor-quick_draft/)

[http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-security/part.apparmor.html](http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-security/part.apparmor.html)

This page shows the graphical interface for apparmor: [http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-security/cha.apparmor.yast.html](http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-security/cha.apparmor.yast.html)

Looks as if the graphical tool includes syntax checking ;)

---

### Post by wacky_sung on 2011-06-18
Thank Bodhi, you have answered it. 

> Just like people told me Linux is good and secure but i never know it till the day i try it. Then i digested it and explored it to know more just a single distro.

---

### Post by uRock on 2011-06-19
> **wacky_sung said:**
> Probably first hand experience using OpenSuse on their Apparmor tools is better than a thousand words to explain.

I was hoping for some points as to how it works differently, but I guess not.

---

### Post by bodhi.zazen on 2011-06-19
> **uRock said:**
> I was hoping for some points as to how it works differently, but I guess not.

I took it for a spin last night and there are some graphical tools available via YAST.

At an initial look , it appears it is easier to write a profile of an application as the defaults for a new application are more rational and it sort of walks you through the basics.

I do not have extensive experience with it mind you ;)

Also the SUSE documentation is a few notches better then the Ubuntu documentation. Apparently the wiki team and Canonical feels the Ubuntu documentation is adequate (from the feed back I got) ;)

The wiki team feels the problem is due to a lack of volunteers and apparently Canonical feels it is the community responsibility to document apparmor (as far as I can tell).

Judge for yourself :

SUSE: 

[http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-security/](http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-security/)

[http://doc.opensuse.org/products/draft/SLES/SLE-apparmor-quick_draft/](http://doc.opensuse.org/products/draft/SLES/SLE-apparmor-quick_draft/)

[http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-security/part.apparmor.html](http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-security/part.apparmor.html)

Ubuntu:

[https://help.ubuntu.com/11.04/serverguide/C/apparmor.html](https://help.ubuntu.com/11.04/serverguide/C/apparmor.html)

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

Edit: Still not enough form me to s/ubuntu/SUSE, but that is as specific as I can be. Take SUSE for a spin and judge for yourself, perhaps we can generate support for Canonical to consider adding some of these graphical tools to Ubuntu ? :lolflag:

---

### Post by uRock on 2011-06-19
Thanks bodhi.zazen, I shall soon look into it. It'll be really cool if such a application can be made for Ubuntu.

---

### Post by nrundy on 2011-06-19
I've looked at it but I'm still lost when it comes to trying to create/configure an apparmor profile.

But I was pleased to see that my 10.04 install has apparmor profiles on by default for things like Evince :)

This is cool.

---

### Post by bodhi.zazen on 2011-06-19
> **nrundy said:**
> I've looked at it but I'm still lost when it comes to trying to create/configure an apparmor profile.

This is the downside of apparmor, users have to individually learn to write and manage profiles.

You have the same problem with selinux, although selinux is more mature and so there is less a need for end users to have to maintain selinux policies.

When the need arises, there are better graphical tools that explain what to do (usually).

Apparmor is easier to learn then selinux policy , so pick your poison.

---

### Post by wacky_sung on 2011-06-20
> **bodhi.zazen said:**
>  **[SIZE="4"]so pick your poison.[/SIZE]**

I got good laugh over it :)

---

### Post by desire.linux on 2011-06-26
I can't understand why Debian refused to enable apparmor in 6.0. Apparmor is so great and easy to learn and use, and it can harden your system very well. I prefer Debian over Ubuntu, but without apparmor I won't use Debian.

---

