---
title: "Change ubuntu directory structure like windows"
date: 2017-06-10
forum: Ubuntu, Linux and OS Chat
---

### Post by suman-paria on 2017-06-10
HI All,

I have a question regarding Ubuntu(linux) directory structure.
From the beginning, I felt its complex.

As we are putting effort to change Unity to Gnome in 17.04.

Why can't we simplify the directory structure. 
How much changes we have to do?
Is it a big change?
Is there any security reasons?

I am sure it will help normal users.

Thanks.

---

### Post by deadflowr on 2017-06-11
Moved to Ubuntu, Linux and OS Chat
Not a support thread

---

### Post by ajgreeny on 2017-06-11
> **suman-paria said:**
> HI All,

I have a question regarding Ubuntu(linux) directory structure.
From the beginning, I felt its complex.

As we are putting effort to change Unity to Gnome in 17.04.

Why can't we simplify the directory structure. 
How much changes we have to do?
Is it a big change?
Is there any security reasons?

I am sure it will help normal users.

Thanks.
As someone who now gets totally lost in the filesystem structure of Windows, I would suggest that this is firstly, a non-starter, with absolutely no good reason to change things from where they are at present, and, secondly, I personally do not find the filesystem structure of Linux complex in any way, or not more than such a hige system is bound to be complex.  Your comment "I am sure it will help normal users." would certainly be incorrect as far as I'm concerned


I suspect you are coming to this from the standpoint of what you believe is a normal user, ie, a Windows user who knows his way around that filesystem like the back of his hand; I meanwhile, having not used Windows now for about 12 years, but knowing my way around Linux fairly well, would find myself in the same situation you now find yourself in, ie baffled about where things sit in the system.

Just accept that they are completely different OSs; probably neither of them is perfect, and one may fit your needs better than the other, and its detailed file/directory structure be known by you better than the other, but please do not think simply because of those differences that the Linux filesystem structure is inferior to Windows so should therefore be changed to that of Windows.

It should not, and will not, happen!

---

### Post by monkeybrain20122 on 2017-06-11
> **suman-paria said:**
> HI All,

I have a question regarding Ubuntu(linux) directory structure.
From the beginning, I felt its complex.

As we are putting effort to change Unity to Gnome in 17.04.

Why can't we simplify the directory structure. 
How much changes we have to do?
Is it a big change?
Is there any security reasons?

I am sure it will help normal users.

Thanks.

I find the directory structure rather simple and systematic. Basically you have /bin /lib/ Include/shared and same structures in /usr,  /usr/local and you can create these folders in  $HOME if you do a lot of local compilations  Fedora gets rid of /usr/local but I don't think this is a good idea if you compile things yourself or install outside the packaging system (say use pip to install python stuffs). Maybe it is just OCD but I like to keep them separated. 

You can pretty much do anything in your $HOME except for the config files. So what do you want to do?

+ 1 to ajgreeny. Windows' file system structure makes no sense and it is much easier to edit .config files and a lot cleaner just delete .config folders  if you want a fresh start with software foo than to fool around with the registry and risk breaking the system.

---

### Post by LastDino on 2017-06-11
For "normal user", I assume you mean someone who is little less "tech savvy", it is actually far easier to understand Linux file system. 

I'm repeating this from words of couple of 50+ people at my home. Exact words of my father "Why can't windows be as simple as Ubuntu?" 

Yes, he thinks Ubuntu is synonymous to Linux, I've tried explaining but to no avail so I left it there. And, yes, Ubuntu is what he has been using majority of time, his work doesn't require computers and why buy windows when he doesn't need any windows specific paid stuff?

Then there is also argument that these "normal users", are not normal at all if they are tinkering with OS file systems beyond USER folders.

---

### Post by TheFu on 2017-06-12
There is a documented, [file system hierarchy standards]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") document which attempts to explain why things are the way they are.

Linux inherits from Unix. Unix deals with small and very, very, large scale systems.  I find the fact that my raspberry pi AND by cluster of hundreds of servers at work all have the same general structure to be a comfort.

Skim that link. You'll definitely learn something and it might start to make sense.  There are very few things that aren't done with good reasons in the Unix/Linux worlds --- except some GUI designs - which I've never understood after 25+ yrs trying. ;)

---

