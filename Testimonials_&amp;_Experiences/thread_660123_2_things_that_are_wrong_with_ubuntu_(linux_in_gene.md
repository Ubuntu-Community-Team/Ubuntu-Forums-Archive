---
title: "2 things that are wrong with ubuntu (linux in general)"
date: 2008-01-06
forum: Testimonials &amp; Experiences
---

### Post by LoneWolfJack on 2008-01-06
Ok, I have been using Ubuntu as my primary OS for several months now, and for the very most part, I'm very happy with it. However, there are (at least) two major things that I feel can drive people away from the entire linux thing, so I'd though I'd put them here and hear what others say...

First, why can't we have a way of installing apps the windows way? The typical end-user will never accept that he has to use the console and type cryptic commands to get their apps installed. They want to go to a website, download the respective file and install it by double-clicking it. 

Secondly, why on earth do we have this mess of a folder structure in linux? Why can't we have a single linux folder that holds all the core stuff, be it called var, etc or usr? I feel it extremely unpleasant to visually scan through a whole bunch of non-related folders every time I'm looking for something.

Perhaps I'm the only one who finds this irritating, but if not, there should be something done. Naturally, at least for the second issue this won't be easy as linux has always been like this.

Anyway, I'm curious what you think about this.

---

### Post by wolfen69 on 2008-01-06
> First, why can't we have a way of installing apps the windows way? 
because it's NOT windows. thank god.
> Secondly, why on earth do we have this mess of a folder structure in linux? Why can't we have a single linux folder that holds all the core stuff, be it called var, etc or usr? I feel it extremely unpleasant to visually scan through a whole bunch of non-related folders every time I'm looking for something.

perhaps you would like to add a registry also. and .exe files? after that, we could call it Winux.
> Perhaps I'm the only one who finds this irritating, but if not, there should be something done. 
perhaps you are not the only one. if you want something done, do it yourself. no one is stopping you from taking the linux source code and coming up with something better. talk is cheap. if you want things done the windows way, use windows.

---

### Post by LoneWolfJack on 2008-01-06
Aside of flaming away do you have anything constructive to say?

Discarding Windows features just because they are Windows features is childish at best and won't help Ubuntu/Linux at all.

---

### Post by lancest on 2008-01-06
To me Linux is a true secure internet workstation (unlike Windows). Software is ideally off the internet!
 You like you can also use AptonCD to install new packages and dependencies:  [http://aptoncd.sourceforge.net/index.html](http://aptoncd.sourceforge.net/index.html).  Its a removable repository which is very easy & useful. Unique to Ubuntu i think.

---

### Post by vanadium on 2008-01-06
Indeed curious remarks for someone who says having used Ubuntu as primary OS for several months now.

1) Many thousands of apps can be installed from one central location in a uniform way with a few mouse clicks in Ubuntu. 

2) A normal user doesn't have to know or deal with the folder structure. He doesn't even have to know about "drive letters". All his files and data are consistently found in one hierarchical folder structure in his private home directory.

---

### Post by jeffus_il on 2008-01-06
I think I am missing something, The are many graphical interface programs to install software on linux and ubuntu, Adept, Synaptic, there's a gui to install debs from debian, they all work much better and simpler than windows and there are thousands of free apps available ...

---

### Post by wolfen69 on 2008-01-06
if you want things to change, ***[COLOR="Red"]you[/COLOR]*** need to start the changes. create your own distro then. complaining on some backroom thread wont change anything.

wait, i just got off the phone with Linus Torvalds, and he said he will make the changes you mentioned in the next kernal release. Mark Shuttleworth is also hastily re-doing Hardy Heron to accommodate you.

---

### Post by jeffus_il on 2008-01-06
As for the directory system, you can find all you configuration stuff in the /etc directory, very neat and convenient, you have a /var where all you changeable stuff is kept, your applications in /usr, and your home directories in /home. You can dump all in one partition or you can split it up into partitions, a very useful feature. If for example your home directory starts filling up, you can purchase another disk, make a new partition on it, copy the contents of /home to it, free up space on the first disk, mount the new partition exactly where the old one was in the directory structure, and with no moving of the operating system, expand your whole system, How would you do that on windows?

---

### Post by LoneWolfJack on 2008-01-06
Well, you see, my company develops business software. Despite of being a techy myself, I learned to see programs like Joe Average does. I know I can add many things through the program manager or through synaptics. Some time ago I installed apache/php/mysql through the terminal with just a fist full of commands. Good enough for me, but maybe not good enough for Joe.

However, the programs I am talking about are those that DON'T come through those apps. You have to download them, perhaps convert them to deb and then run them through the terminal. If there are tools that have a GUI for doing all that, one of them should come installed with Ubuntu and linked to the respective files.

Personally, even though I'm not a Linux geek, I can use the terminal no problem, but I still appreciate a GUI. No question, sometimes editing a conf file is faster than working through a GUI but you can't do that to Joe Average.

---

### Post by kelbizzle on 2008-01-06
Question #1- We do have ways to just double click to install software. They're called .deb  Packages. **System -> Help and support ->Adding, Removing and Updating Applications** Since ubuntu is based on [Debian]("http://www.us.debian.org/") It's makes it super easy for us.

Question #2 - We do have one folder where we keep all of our stuff. It's call the root of the drive and it begins with a  " / " If your a newbie... The only folder you really need to be concerned with is your home folder. What is it that your looking for?...Music?...Movies?.... Pictures? Do you know the meaning behind the file structure?  Before you complain first LEARN about the os your using..([Learn the Linux file structure]("http://www.freeos.com/articles/3102/")) 

Being a windows power user for many years. I just like many new ubuntu users had to read, research, test, read some more, ask for help etc. because being a technical guy I know how much of a headache it is to switch to a new and totally different product. 
The difference between me and a frustrated new user. Is the thirst for knowledge. I want to know how to make my system do what I want. I want to learn how to fix something when it isn't working correctly. I want to understand my system inside and out. Others with so many years or Wizards holding their hand and idiot pop up messages. They have been led to believe you should just be able to pick up a computer and begin doing everything imaginable on it without reading a help file or reading the manual. Ubuntu does this to an extent. 

Let me be the first to tell you. If you wants Ubuntu's Distribution of Linux to work for you...You must READ...and LEARN..about what it is your using. After that and only then will you be able to truly enjoy or hate Linux. Since the beginning of computer I've never kept any distro of Linux on my system for more than a week. I'm going on 2 years with ubuntu it truly is better than windows. JUST LIKE A MAC.

---

### Post by jeffus_il on 2008-01-06
The Ubuntu repository today contains 100% of what the average "Joe" needs, Remember , it contains a full Office suite, programs for playing music, watching video, mail and internet browsers, and lots more, the average user does not need to go beyond the repository. Much easier than windows.

Also if you have software you want to market/distribute to Ubuntu users, there is a mechanism through the gui to add your repository to the default Ubuntu one, and have your software install and updated very easily, more so than windows, and totally gui.

---

### Post by LoneWolfJack on 2008-01-06
> **wolfen69 said:**
> if you want things to change, ***[COLOR="Red"]you[/COLOR]*** need to start the changes. create your own distro then. complaining on some backroom thread wont change anything.

wait, i just got off the phone with Linus Torvalds, and he said he will make the changes you mentioned in the next kernal release. Mark Shuttleworth is also hastily re-doing Hardy Heron to accommodate you.

Don't know where all your hatred is coming from, but it reminds me of all those self-declared usenet sheriffs back in the mid 90s everybody used to make fun about.

First off, I am not complaining. I am putting forward something I noticed and asked for input. Nothing more, nothing less. Secondly, especially for the folder structure thing, it actually makes me smile that you are naive enough to think someone would, as you would certainly say, "demand" such a drastic change in how Linux works. 

As for creating a new distro, I really think we have enough Linux distros and there should actually be less than more.

My C is a bit rusty, but I pay several programmers who regularly contribute to the Linux community, so don't start that leech thing with me.

---

### Post by abstractcoder on 2008-01-06
I think people should understand that Linux is **NOT** WIndows. People who are thinking about switching shouldn't expect it to be "just like windows". 

Further, people who know nothing about Linux shouldn't be using it. The last thing we need is a bunch of windows users switching to linux while knowing nothing about the security issues.  

The "average" user most likely doesn't know how to write a solid iptables firewall. As for the alternatives, sure they could install a firewall using Synaptic. There are still other security issues, services, default passwords, accounts, etc. I doubt an average user can secure the system. 

A person who wants to switch must like to learn, because that's what it takes. Research/Learning.

I find the Linux file structure to be a lot more organized than Windows. Windows is a MESS, and the Terminal isn't that hard to use/understand.

If the user has trouble doing basic things like installing programs, moving around the file system, etc after a few months, then they shouldn't be using that OS.

(I switched from Windows to Linux a few months ago)

---

### Post by bapoumba on 2008-01-06
Pfui.. That was quick.
24 hours cool off period.

---

