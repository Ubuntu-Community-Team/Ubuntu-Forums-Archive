---
title: "As an IT Professional....."
date: 2017-01-29
forum: Ubuntu, Linux and OS Chat
---

### Post by ClickXT on 2017-01-29
As an IT Professional that has always worked in a Windows Enterprise environment -- would it make sense for someone like me to install Ubuntu and work on getting good/more knowledgeable with it?

I guess what I mean is... I like open source software and the concept. I am familiar with some and use regularly Firefox, Thunderbird, VLC, CloneZilla, etc. I bought a new Dell XPS 13 laptop and was considering putting Ubuntu on it. Would working with this one the side help me whatsoever for IT Support (Level 2-3) in a Windows environment? Would there be any benefit for me from a professional standpoint in my current type of role? Or am I much better off spending my personal time on a platform we also use at work?

Thanks for your time and thoughts.

---

### Post by QIII on 2017-01-29
Hello!

It's really your call.  If you are interested in taking a hike down an unknown path once in a while, you can explore Linux.  If the practicalities of life make that impossible, don't fret.

But if you do decide to explore Linux, the first thing you must do is leave your Windows expectations at the door.  It's a different OS entirely.  So whether it would *directly* help you provide better support for Windows users is doubtful.  Broader general knowledge is always a good thing, though.

I'd suggest using virtualization to begin with.  That way you can do snapshots and then break things all you want without loss.

Sometimes people will use the term "switch", but there is no need to "switch" to Linux.  There is no law against using both Windows and Linux.  I do.

---

### Post by Geoffrey_Arndt on 2017-01-29
Another thing to consider . . . will you always be working in a Windows only environment?    Most large organizations (business, govt/military, education/science, etc.) run a combo of windows, unix and linux - - with linux being the fastest growing OS and the most likely to control mission critical systems.   If going back to university or college (since around 2008-2010), Linux is (by far) the predominant system taught because it really runs not only the server world but the mainframes also.   

Understanding Linux helps you to understand IT and Systems in general . . . . understanding windows and it's ecosphere "only" is like being in a tech bubble . . . . not a good thing.

---

### Post by The Cog on 2017-01-29
Agreed - it's up to you. Many companies use both OSs, so if you have the time and inclination to look at Linux, it won't do you any harm.

QII is right about it being different though. And in ways you won't expect. Some things you expect to be different will be spookily similar. Some things that you know are fundamental to computing and must therefore be the same in all OS types will turn out to be nothing of the sort.

---

### Post by SeijiSensei on 2017-01-29
Are you currently more involved with servers or with desktops?  If the former, you might want to start with Ubuntu Server first.  Install VirtualBox on your Windows machine, then create a virtual machine and install Ubuntu Server.  Probably the first application you might want to consider is [Samba]("https://help.ubuntu.com/community/Samba"), which provides Windows-style ("CIFS") file sharing. Installing the "[LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP")" stack of Apache, MySQL, and PHP will give you some experience with Linux-based web hosting.  Once you've gotten your feet wet with that, you might try installing WordPress.  If you choose to invest in server-side applications, you'll need to get used to using the terminal rather than a GUI interface.  Ubuntu Server doesn't even come with a GUI because in most cases people manage Linux servers via [SSH]("https://help.ubuntu.com/lts/serverguide/openssh-server.html").

I've left mail off the list because it is much more complex to administer in a world full of spam and malware.  It's also less common in a corporate environment where Exchange often holds sway.

In most corporate environments Linux is hidden in the server room far away from the desktops of ordinary users. You might try running a desktop flavor of Ubuntu to see how well LibreOffice, Firefox, Thunderbird, GIMP and other desktop applications might substitute for the software your company now runs.

---

### Post by T.J. on 2017-01-29
I've found that using Linux alongside Windows boosts problem solving. 

I have used a number of different operating systems (including Windows, Linux and others) during my 25 or so years in jobs ranging from tech support, to systems administrator, to software engineer. What I have learned, as one professional to another, is what I can offer you: there is no magic bullet.  There is no single answer, no one size fits all.  Don&#8217;t let others &#8220;convert&#8221; you from Windows or try to fill your head with visions of utopia.  That is a recipe for disappointment and disillusionment.  That said, I love Linux and would use it over Windows any day - far fewer headaches for me personally.

In my experience, the operating system seldom matters except as a preference.  What matters is the tools used in your particular job.  If you feel that you need to expand your skills, then by all means,  dive in &#8211; not just Ubuntu &#8211; but the entire community.  We welcome anyone, with or without skills. If you have the desire and energy to make a place for yourself, you can do that in FOSS (free opensource software).  Not everyone is a programmer.  There are writers, and tech support,translators, web-masters, and dozens of other areas where your skills(whatever they are) would be appreciated. Setting aside the egos and the usual politics of personality, everyone has access to the same open process and it is all offered under the same license to everyone equally. You can tailor a solution to meet your needs.  I think you will find that most of the community accepting and willing to help you achieve whatever goals you have, as long as you are willing to make an effort, and not give up.

I&#8217;ve been writing code since I was teenager, many years ago &#8211; and what Ihave discovered in the years since is that the  FOSS community (not just Linux) has some of the best and most creative IT people when it comes to solving problems.  It really shows when Linux runs on everything from supercomputers to your cell phone. I honestly believe that there is very little that FOSS can&#8217;t do.  Being a part of that, however great or humble, is a wonderful thing.  I encourage you to try it, but remember that FOSS is not just Linux. FOSS is on Windows too, and you can find a balance that fits your life and work needs without upending everything you already feel comfortable with.

Yes, I can believe it can help open new opportunities for work and life.  As with all things, you get out of it what you put into it.

---

### Post by 1clue on 2017-01-29
As an IT professional I manage lots of Linux images, mostly Ubuntu Server but also some other distros.

I suspect most people who dip a toe into the enterprise Linux pond do so with VM images of some sort of Linux and stay with Windows on the desktop.

With virtualization Linux makes huge sense, both because a tailored-for-VMs Linux image can be very small and because of the lack of license concerns with respect to the number of running copies of the OS. Of course if you're running proprietary fee-based software on the image then you need to worry about licensing that.

The Enterprise environments I've had contact with are very familiar with Linux on the server side, especially in VMs. Some of them have a few people who run it on the desktop, but usually I think it's an IT enthusiast rather than a mainstream user.

A lot depends on the corporate culture at your company though. Your company may be heavily biased away from Linux, and I know it's tough to fight that. It helps if you have something specific in mind as a project, to start off with.

---

### Post by Bucky Ball on 2017-01-29
> **clickster said:**
> Would there be any benefit for me from a professional standpoint in my current type of role?

I can see no benefit whatsoever to your current role working with Windows, nor is there any relationship between the two operating systems. It is highly unlikely anything you learn diddling with Ubuntu would be in any way applicable to a Windows environment, apart from perhaps the odd broader computer concept which is not OS specific.

So no, no benefit I can see to your current position. Some of the open-source programs you're used to are even slightly different in the Ubuntu incarnations.

Unsure how much you know about Ubuntu, but it is not a drop-in replacement for Windows. It will not natively run Windows programs, will only run some with a kludge called WINE and its cohorts and won't run .exe files. There will be a learning curve and you will be required to forget a lot of Windows conventions and adapt to Ubuntu/Linux conventions. Another reason I see no benefit to your current role. 

Good luck.

---

### Post by Habitual on 2017-01-30
> **clickster said:**
> As an IT Professional that has always worked in a Windows Enterprise environment -- would it make sense for someone like me to install Ubuntu and work on getting good/more knowledgeable with it?

I guess what I mean is... I like open source software and the concept. I am familiar with some and use regularly Firefox, Thunderbird, VLC, CloneZilla, etc. I bought a new Dell XPS 13 laptop and was considering putting Ubuntu on it. Would working with this one the side help me whatsoever for IT Support (Level 2-3) in a Windows environment? Would there be any benefit for me from a professional standpoint in my current type of role? Or am I much better off spending my personal time on a platform we also use at work?

Thanks for your time and thoughts.
Personal time = Linux
Work = Windows

How "under the hood" are you?

---

### Post by makitso on 2017-01-30
I had the same question about 8 years ago, worked in an exclusive Windows environment but felt bored technically.  So, I started looking at linux, starting with Debian and finally settling on Ubuntu 8.04. 
Looking back, it definitely the right decision -- for me.

---

### Post by bearlake on 2017-01-30
Been using Linux for more than 10 years now and just started with networking.

1st server had a GUI which for the most part was setup from the command line. That lasted 2 weeks. ( got bored )

2nd server is headless with no GUI and has been running for more than 6 weeks now with no issues or security issues to date.

Expected it to last about 15 min on the WWW.

Everything learned to date came from the Internet and people in this thread. ( Definitely one of the best sites for Ubuntu Server )

Good Luck from a nobody. :)

---

### Post by ClickXT on 2017-02-01
Thanks for the input all. I am still in "debate-mode" on this. I vaguely recall the last time I had this idea I couldn't even get Ubuntu to install my WiFi drivers and I became very frustrated and moved on. 

Thanks for all the input. It's all useful and noted.

---

