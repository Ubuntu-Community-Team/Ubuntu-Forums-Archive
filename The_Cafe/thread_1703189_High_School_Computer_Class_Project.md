---
title: "High School Computer Class Project?"
date: 2011-03-08
forum: The Cafe
---

### Post by kevin11951 on 2011-03-08
I volunteer at a local high school, helping to teach some computer concepts to students (mostly networking)...

They have been doing pretty well so far, and I want to do a fun project to wrap up...

Does anyone have any ideas for a fun computer project for high school students to do?  Hopefully it has nothing to do with networking, because the kids want to pull their hair out from all the work we've been doing with it.

I had the idea of setting up a LAMP stack using Debian 6 and Webmin...  The kids were, um, less than enthusiastic about the idea.

Some of the kids also hate Linux/BSD for whatever reason (The first day I was there, one kid walked up to me when I had my Ubuntu laptop, and said "You have fun with your Linux, while I play games on my Windows," strange comment ;), but I digress.)

---

### Post by GWBouge on 2011-03-09
> **kevin11951 said:**
> (The first day I was there, one kid walked up to me when I had my Ubuntu laptop, and said "You have fun with your Linux, while I play games on my Windows," strange comment ;), but I digress.)

I don't have a clue what the class is all about, or what they've learned, but maybe something with [Panda3d]("http://www.panda3d.org/"), or a render cluster for [Blender3d]("http://www.blender.org/")?  Show'em there really is something fun/creative/marketable to be had in Linux  =o)

---

### Post by kevin11951 on 2011-03-09
> **GWBouge said:**
> I don't have a clue what the class is all about, or what they've learned, but maybe something with [Panda3d]("http://www.panda3d.org/"), or a render cluster for [Blender3d]("http://www.blender.org/")?  Show'em there really is something fun/creative/marketable to be had in Linux  =o)

The class has thus far generally dealt with the following topics:

* Fixing Windows XP and 7 Machines (AD/PDC, Registry Editing, etc...)
* Fixing Hardware
* Networking (IPv4)
* and a few other things

Also, they seem to hate Linux because its cool to do so (here)...  Not for any real reason.

---

### Post by earthpigg on 2011-03-09
build a home fileserver out of commodity (cheap) parts.

---

### Post by Windows Nerd on 2011-03-09
> **kevin11951 said:**
> Also, they seem to hate Linux because its cool to do so (here)...  Not for any real reason.

Show them just how much Linux is used in our daily lives - Stock exchanges, webservers, most of the internet, phones (ex. Anyone here have a Droid?),and so on. Also prove just how much more secure Linux is compared to Windows, if you are knowledgeable in Pentesting. They can have their overpriced games and gaming hardware, we can have real-life application and security, with many old-school games (as well as some newer ones) that run on Linux :D.

---

### Post by kevin11951 on 2011-03-09
> **earthpigg said:**
> build a home fileserver out of commodity (cheap) parts.

How do I do that?  From scratch, or using something like FreeNAS...

---

### Post by earthpigg on 2011-03-09
> **kevin11951 said:**
> How do I do that?  From scratch, or using something like FreeNAS...

that's one way, [this]("http://www.intac.net/build-your-own-server/") is another, there are also Free Software options that will [add server capabilities]("http://filezilla-project.org/") to vanilla windows, or maybe come up with a way to let the students choose.

If you chose windows, make sure you can also comply with the potentially troublesome Windows EULA and Licensing [terms]("http://www.microsoft.com/About/Legal/EN/US/IntellectualProperty/UseTerms/Default.aspx").

Skimming because I'm bored, and curious about the legality of using vanilla Windows as a server...

> 3e. Device Connections. You may allow *up to 20 other devices* to access software installed on the licensed computer *to use only File Services, Print Services, Internet Information Services and Internet Connection Sharing and Telephony Services.*

3g. Media Center Extender. You may have five Media Center Extender Sessions (*or other software or devices which provide similar functionality for a similar purpose*) running at the same time to display the software user interface or content on other displays or devices.

3e is interesting. It doesn't say at the same time, whereas the multimedia part does.

Based on that, my guess is that you are ok if your lab has 20 or fewer computers on the LAN, and if only 5 or fewer *at a time* access sound/video content from the server.

For the ubuntu-based option i linked above:
-Lots of folks will tell you that XFCE or anything X11 on a server is silly or evil or heretical. Eh, to each his own. It may increase electricity consumption, but it isn't going to slow a simple fileserver down significantly or make it catch on fire.
-It also means that you can easily google for solutions to server problems *while on that computer* without being restricted to the text-only version of the internet.
-That guide has been around for a while. In 2011, I'd suggest Lubuntu or any of the 5,000 other lightweight ubuntu derivatives. Or, heck, just use plain old vanilla Ubuntu. Really, it's not going to make a huge difference unless we are talking about ancient hardware.... or modern hardware with staggering demands placed on it. -The only suggestion I would offer is not to pick any distro that tries hard to look like windows - as soon as it becomes apparent that it isn't windows, expectations and reality will have diverged, and that usually isn't a positive situation.

---

### Post by juancarlospaco on 2011-03-09
Make a game using Python!, from rurple to pygame you choose...

---

### Post by sixstorm on 2011-03-10
Kids love music, so why not make a jukebox?

EDIT:  Jinzora is what I was thinking about.

---

### Post by Old_Grey_Wolf on 2011-03-10
Possibly let them set up a game server?

Googling on Linux Game Server may give you an idea. I found HOWTOs for several games.

If you have a computer with a dual core processor and 4 GB of RAM, they could set up more than one game server on a single host computer using Virtualbox.

---

### Post by earthpigg on 2011-03-10
> **Old_Gray_Wolf said:**
> Possibly let them set up a game server?

Googling on Linux Game Server may give you an idea. I found HOWTOs for several games.

If you have a computer with a dual core processor and 4 GB of RAM, they could set up more than one game servers on a single host computer using Virtualbox.

nice idea. Urban Terror, if you can get some permission slips signed.

---

### Post by pi3.1415926535... on 2011-03-10
Definitely you should find something to show the potential of Linux. Maybe LiveCD customization using a custom compile kernel, see who can get the most functional/amazing Linux setup.

---

### Post by Old_Grey_Wolf on 2011-03-10
If he chooses VMware Player instead of Virtualbox, there are some virtual appliances that he or they could install. The virtual appliances are virtual machines that are pre-configured. You just import the appliance in order to use it. He could try searching for virtualized game appliances.

If the students insist, the Virtualbox and VMware hypervirors run on Microsoft Windows as well as GNU/Linux.

Some of the students may have thought about setting up their own server for Game Parties. I think they may have the motivation to figure out how to do it if they have someone that can help them a little along the way.

---

### Post by kevin11951 on 2011-03-10
I talked to them today, and we have decided...

...to learn Python.

We are going to use the book "A Byte of Python," and I am making a customized Linux install that has Python 3, Geany, and a few other tools pre-installed.  Nothing too fancy though, I am just going to use Clonezilla to clone the HDD to the student's workstations.

---

### Post by SaintDanBert on 2011-03-10
> **earthpigg said:**
> build a home fileserver out of commodity (cheap) parts.

I like this project for students.  It has real-world value. Is realistic in scope and difficulty -- file and print services with more time it could stream audio and video to the intra-net.

Bonne chance,
~~~ 0;-Dan

---

### Post by AllRadioisDead on 2011-03-10
OP, as a highschool student, let me offer my $0.02.

Your class clearly isn't very fond of Linux, so stop shoving it down their throats. Why don't you ask them what they'd like to do for their final, and see if it gives you something to work with.
[COLOR="Lime"]
>Class doesn't like Linux
>Hmm, What should I give them for their final?
>Goes on Linux forum for suggestions[/COLOR]
wat

---

### Post by kevin11951 on 2011-03-10
> **AllRadioisDead said:**
> OP, as a highschool student, let me offer my $0.02.

Your class clearly isn't very fond of Linux, so stop shoving it down their throats. Why don't you ask them what they'd like to do for their final, and see if it gives you something to work with.
[COLOR="Lime"]
>Class doesn't like Linux
>Hmm, What should I give them for their final?
>Goes on Linux forum for suggestions[/COLOR]
wat

Now you begin to see my plan **evil laugh** ;)

---

