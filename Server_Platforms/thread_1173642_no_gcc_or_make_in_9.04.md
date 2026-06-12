---
title: "no gcc or make in 9.04"
date: 2009-05-30
forum: Server Platforms
---

### Post by Vegan on 2009-05-30
I was disappointed that I had to manually install gcc and make to be able to build programs.

These tools were there with older versions but not with 9.04 :(

---

### Post by cariboo on 2009-05-30
Build-essential hasn't been included with the server version for quite a while, as most of use don't need it. The package is on the install cd if you need it.

---

### Post by windependence on 2009-05-31
This is only necessary if you are compiling applications yourself. Be aware you are not gaining much, if anything by doing this. In fact, you are making application management very very messy if not impossible. If you install using a package manager, each package is logged in a database so it can be uninstalled or upgraded. If you love compiling apps I would suggest Gentoo. :)

-Tim

---

### Post by Titan8990 on 2009-05-31
> **windependence said:**
> This is only necessary if you are compiling applications yourself. Be aware you are not gaining much, if anything by doing this. In fact, you are making application management very very messy if not impossible. If you install using a package manager, each package is logged in a database so it can be uninstalled or upgraded. If you love compiling apps I would suggest Gentoo. :)

-Tim


You can use the Debian package manager to install from source too. Looks something like this:

apt-get -b source PACKAGE


Not as easy or flexible as Portage but the tools are there.

---

### Post by Vegan on 2009-07-09
Well I was able to get gcc up and running along with a mountain of other languages.

so I now have ```
make
``` available which is what I needed.

---

### Post by caco on 2009-07-09
Lucky you ... default installation usually carry popular applications, it show not a reason number of users compile stuff, we depend on ubuntu's reps for applications


[[IMG]http://brainstorm.ubuntu.com/idea/20470/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/20470/)

---

### Post by Cheesemill on 2009-07-09
```
apt-get install build-essential
```Will install make, gcc  and all the other tools you need to compile programs.
If you are going to be compiling kernel modules then you will need to do:
```
apt-get install linux-headers-`uname -r`
```as well.

---

### Post by dragos2 on 2009-07-09
Also having gcc on a server is dangerous.

---

### Post by Vegan on 2009-07-09
How? I have a hardware firewall so how are they going to run it?

---

### Post by windependence on 2009-07-10
The point is if it's there, it's a risk. An installed compiler lets a hacker write malware right on your machine and run it. No firewall is perfect as well as any other security measure. No offense but I think you need a bit more experience with this stuff. You should be installing from packages. There is no significant advantage to compiling the package, and package management will be a nightmare this way. If you were using Gentoo or FreeBSD, you would install the package by compiling, but in Linux, with the generic kernel, you won't see much if any difference in efficiency by compiling every program. I doubt seriously if you are writing your own programs in C. It takes years to get proficient doing this and probably would be inefficient to do as a consultant, especially for web development.

-Tim

---

### Post by dragos2 on 2009-07-10
> **Vegan said:**
> How? I have a hardware firewall so how are they going to run it?

You will be surprised ;)

---

### Post by Vegan on 2009-07-10
Bla bla, bla! My crappy old Linksys has seem it all. I am still safe from malware.

---

### Post by windependence on 2009-07-10
> **dragos2 said:**
> You will be surprised ;)

I wonder if he would be willing to let me hack him? :-)

-Tim

---

### Post by Vegan on 2009-07-11
Be my guest, but you will have to wait your turn behind the spammers who constantly attempt to break into my forums to post their crap.

---

### Post by windependence on 2009-07-11
There's a big difference. Those aren't real people, they're bots. Automated scripts. It's easy to foil them, but not so easy to fool a human being. If you are OK with an insecure site that's your business, but since you are calling yourself a programmer/analyst, etc, you ought to take security a bit more seriously.

-Tim

---

### Post by dragos2 on 2009-07-11
> **windependence said:**
> I wonder if he would be willing to let me hack him? :-)

-Tim

If he does not see it it does not mean that it does not exist. A skilled attacker would not
need more than a few minutes :))

---

### Post by Vegan on 2009-07-12
Well the telnet access is firewalled to only work on the LAN so way to easily get at that prompt. Then you have to figure out a valid user/pass to log-in.

All of this is logged. So I know who is nibbling.

---

### Post by windependence on 2009-07-12
Unless they delete the logs on the way out which is commonly done. Seriously dude, you need to read more on security. You think you know but you don't. We're trying to help you here, but I guess until you get hacked (and you probably won't even know it) you won't get it.

-Tim

---

