---
title: "Community Question"
date: 2006-04-20
forum: The Cafe
---

### Post by gymsmoke on 2006-04-20
When running apt-get install, do you actually go through and look up what the "suggested" and "recommended" packages are to see exactly "what" they are and try to determine "why" they are suggested or recommended?

---

### Post by mostwanted on 2006-04-20
I never use apt-get install, I use synaptic so that I can easily do things like that. I do sometimes look at the recommended packages when I'm installing programs I *know* can be extended.

Something else: personally I feel this community should move away from using apt-get for instructions because Synaptic is a lot better for many purposes - dependency-handling for instance! (ever got one of those "the following packages will be skipped" messages in Update Manager?)

But that's just my personal vendetta, you don't have to agree with me.

---

### Post by aysiu on 2006-04-20
[QUOTE=mostwanted]
Something else: personally I feel this community should move away from using apt-get for instructions because Synaptic is a lot better for many purposes - dependency-handling for instance! (ever got one of those "the following packages will be skipped" messages in Update Manager?)[/QUOTE]  I haven't had too many dependency issues with apt-get. If people are planning to install *ubuntu-desktop*, *kubuntu-desktop*, or *xubuntu-desktop*, I encourage them to use *aptitude* instead of *apt-get*, as it makes those packages easier to remove later on.

However, I have a little beef with your beef.

It's far easier for me to say (in 20 words), > Go to Applications > Accessories > Terminal and type ```
sudo apt-get update && sudo apt-get install firefox libstdc++5
``` than it is for me to say (in 43 words) > Go to System > Administration > Synaptic Package Manager. Click the Reload button. Then search for the word *firefox*. Right-click it and mark it for installation. Search for the word *libstdc++5*. Right-click that and mark it for installation. Then click the Apply button.

---

### Post by mostwanted on 2006-04-20
[QUOTE=aysiu]I haven't had too many dependency issues with apt-get. If people are planning to install *ubuntu-desktop*, *kubuntu-desktop*, or *xubuntu-desktop*, I encourage them to use *aptitude* instead of *apt-get*, as it makes those packages easier to remove later on.

However, I have a little beef with your beef.

It's far easier for me to say,  than it is for me to say[/QUOTE]

Yes, of course it is. But in my experience some users don't understand what that actually means. Typing in a terminal is usually gibberish for them, however straight-forward it can seem for the rest of us. Forcing them to open up Synaptic and see - so to say - the whole picture: a big repository, when you install an app it automatically finds and selects dependencies. This will also serve as an eye-opener for many newbies.

I've seen several times, usually in threads where newbies have downloaded a tgz package or something, that people ask them to apt-get install instead. And it seems to me they don't actually get what is happening. Very often this leads to misunderstandings that apt-get is some magical command to install a package you've downloaded using a keyword. Using Synaptic gives a much more graphical and easy to understand image of how apt-get works.

---

### Post by aysiu on 2006-04-20
[QUOTE=mostwanted]Yes, of course it is. But in my experience some users don't understand what that actually means. Typing in a terminal is usually gibberish for them, however straight-forward it can seem for the rest of us.[/quote] That's why they should copy and paste, which makes it even easier--less chance for user error.

I'm making a note to myself to say *copy and paste this command* instead of saying *type this command*.

> I've seen several times, usually in threads where newbies have downloaded a tgz package or something, that people ask them to apt-get install instead. And it seems to me they don't actually get what is happening. Very often this leads to misunderstandings that apt-get is some magical command to install a package you've downloaded using a keyword. Using Synaptic gives a much more graphical and easy to understand image of how apt-get works. From what I've seen, they don't "get" how Synaptic works either. I've seen a lot of new users say they can't install (using Synaptic) the .tar.gz they downloaded. If they want an understanding, I link them here:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If they just want something installed, I give them the command to do it.

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=gymsmoke]When running apt-get install, do you actually go through and look up what the "suggested" and "recommended" packages are to see exactly "what" they are and try to determine "why" they are suggested or recommended?[/QUOTE]
I usually check out what is suggested and recomended (via synaptic) and just install them. 

I rarely checked why they're suggested or recommended.

---

### Post by nalmeth on 2006-04-20
I will always tell people to use apt-get over synaptic.
It's good to know a little bit about how your package manager works, and despite what a good application synaptic is, I still find it easier to find a package with apt-cache search.
Really, Synaptic is a really good app, but on my older computer and laptop, it's too slow, and the layout seems a little distracting to me.

Apt-get is a pretty easy concept once you understand the basics.
What gets me, is when some new guy, first time ever using linux, is told to tar -xyz and so on in the terminal to unzip files. This is where the GUI is supposed to be used. It's a simple right click, and it just looks really complicated via the terminal, especially for someone brand new.
Countless times I've seen someone struggle with this, and the simple solution is "right-click on the package, and click extract here"
>  That's why they should copy and paste, which makes it even easier--less chance for user error.

I'm making a note to myself to say *copy and paste this command* instead of saying *type this command*. Yes, this is good practice I think. It's really cool when you are given instructions, and you need only highlight to copy and click the scroll button to paste for all the steps. So long as the instructions are correct to the tee.
I've seen 
sudo apt-get install build-essential_*s*_ 
a hundred times.

---

### Post by gymsmoke on 2006-04-20
Ok... The reason I asked the question was not from a Synaptic point of view.

For desktop users, synaptic is fine (since we're assuming that these users are ex-M$) or some such OS...

But, in the case where the user is a little more advanced than that, or, in the case where you install Ubuntu as a server (NO GUI), apt-get is what you'll use (unless you are using dpkg/dselect) ... I asked the question because of this latter condition.
And, when I run apt-get install <pkg>, and get replies from apt like "Recommended Packages..." ,  and "Suggested Packages... " , I do look them up.

This all started with me personally because I wanted to install proftp, so i say 'apt-get install proftp' , and it recommends/suggest  readline-perl, and a few others...
so i abort the install and add those to the list .. apt-get install proftp readline ...
then it Recommends/Suggests a few more, so I abort and add those
then it Recommends/Suggests a list of about 20 additional packages, and I say "WTFO!!!" This could go on forever... so I start looking up the packages it Recommends/Suggests to see which of these may/may not be necessary...

I know it sounds like the long way round to get a simple package installed, but I'm finding it's also a great way to _only_ install what you'll need (which can definitely be a performance factor), and a way to learn about what's really going on in your distribution.

btw - I also noted that this is marked "Moved" ... But I don't know where it was "Moved" to, or why

---

### Post by aysiu on 2006-04-20
[QUOTE=nalmeth]What gets me, is when some new guy, first time ever using linux, is told to tar -xyz and so on in the terminal to unzip files. This is where the GUI is supposed to be used. It's a simple right click, and it just looks really complicated via the terminal, especially for someone brand new.
Countless times I've seen someone struggle with this, and the simple solution is "right-click on the package, and click extract here"[/QUOTE] On a similar note, why, when people say in the Absolute Beginner forum, "I'm trying to install *programintherepositories*, and I have a .tar.gz. What do I do with it?" do people immediately start giving instructions for how to untar the .tar.z and install from source?

I never encourage people to install from source unless they tell me that either

A. They are experienced users and want to know how to compile

or

B. They need the absolute bleeding-edge version of Gtkpod because the older version doesn't work with their iPod.

> btw - I also noted that this is marked "Moved" ... But I don't know where it was "Moved" to, or why Absolute Beginner is a support forum for beginners. This thread is really a "weigh in your opinion" thread, not a "please help me with my problem" thread. So it's now in the Ubuntu Cafe.

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=gymsmoke]
btw - I also noted that this is marked "Moved" ... But I don't know where it was "Moved" to, or why[/QUOTE]
moved to "ubuntu cafe", don't know why, don't know from where ;)

---

### Post by wolfee on 2006-04-20
Countless times I've seen someone struggle with this, and the simple solution is "right-click on the package, and click extract here"
 
Yes but how to install after "extract here" cannot easily be found out since the read me file won't open by clicking on it!! I still cant extract,compile,and install tar gz files. I went to a good web page that has video instructions and the sound is brocken up and the video is too blurry.

---

