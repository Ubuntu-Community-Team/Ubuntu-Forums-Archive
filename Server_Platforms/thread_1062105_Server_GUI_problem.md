---
title: "Server GUI problem"
date: 2009-02-06
forum: Server Platforms
---

### Post by wordmaster on 2009-02-06
Hello,

 I just set up ubuntu server on a brand new computer with nothing else on it. As I am still trying to figure this stuff out, I wanted to install a GUI so, following instructions I ran across, I typed 
sudo aptitude install x-window-system-core gnome-core

It worked for about an hour and everything seemed to be OK. Then, I typed /ect/init.d/gdm start to start the desktop and it said no such file.

I assumed it would come up on a restart but I assumed wrong. So, apparently I have the GUI set up now, but how do I access it? Any and all help appreciated.

---

### Post by unixeducation on 2009-02-06
What do you get when you type "startx" at the prompt? BTW, is gdm installed (sudo apt-get install gdm)?

---

### Post by wordmaster on 2009-02-06
Thank you. That did the trick, however, should the GUI not start on a restart?

---

### Post by cariboo on 2009-02-06
The only way to have the gui start automagically on reboot is to install a desktop manager -- gdm, kdm or xdm. The way you have it set up now is probably better, as you don't need the gui 90% of the time, and once you have the server setup, you shouldn't need it at all.

Jim

---

### Post by hyper_ch on 2009-02-06
why do you want to have a gui on a server anyway?

---

### Post by carbm1 on 2009-02-06
> **hyper_ch said:**
> why do you want to have a gui on a server anyway?

Hyper_CH... Mad props for the amount of time and effort you put into the Ubuntu Forums and helping others. I have read and appreciated many of your posts.  However, this is the second time I have seen this exact same statement from you in two different posts today pertaining to a GUI on Ubuntu Server in a negative and non supportive way.

The entire point of Linux is freedom.  The freedom to setup things the way you want.  Hell, even the programs that are included in Ubuntu server, without a GUI, have their own bugs.. and more are found everyday.  Granted those programs have Canonical support for the support term vs. the GUI programs.

I want to have a GUI because the box I have Ubuntu Server installed on also serves as a desktop when my desktop computer is tied up. All I need is Firefox most of the time. I choose to install xorg, gnome-core, gdm, ubuntu-gdm-themes.  This gives me a basic desktop, nothing special, just enough and I still get to keep my Ubuntu Linux instead of switching to another disto.

Ever wonder why the other Linux distro's include a GUI? Ever wonder why they are doing so well?  Its kinda nice to see something after you install instead of the command prompt. I use CentOS, OpenSUSE, Suse Linux Enterprise Server 9 & 10, all have a GUI.  I personally prefer Ubuntu Server. My choice... I like the repos and I like the community.  I think Canonical should include support for Gnome or Fluxbox on the server version, My opinion only.  I can work completly from the command line myself... but I want Ubuntu Server to thrive and a GUI would take it a long way with some of the newbies.

My soapbox is over...

---

### Post by R.Bucky on 2009-02-07
> **carbm1 said:**
> Hyper_CH... Mad props for the amount of time and effort you put into the Ubuntu Forums and helping others. I have read and appreciated many of your posts.  However, this is the second time I have seen this exact same statement from you in two different posts today pertaining to a GUI on Ubuntu Server in a negative and non supportive way.

The entire point of Linux is freedom.  The freedom to setup things the way you want.  Hell, even the programs that are included in Ubuntu server, without a GUI, have their own bugs.. and more are found everyday.  Granted those programs have Canonical support for the support term vs. the GUI programs.

I want to have a GUI because the box I have Ubuntu Server installed on also serves as a desktop when my desktop computer is tied up. All I need is Firefox most of the time. I choose to install xorg, gnome-core, gdm, ubuntu-gdm-themes.  This gives me a basic desktop, nothing special, just enough and I still get to keep my Ubuntu Linux instead of switching to another disto.

Ever wonder why the other Linux distro's include a GUI? Ever wonder why they are doing so well?  Its kinda nice to see something after you install instead of the command prompt. I use CentOS, OpenSUSE, Suse Linux Enterprise Server 9 & 10, all have a GUI.  I personally prefer Ubuntu Server. My choice... I like the repos and I like the community.  I think Canonical should include support for Gnome or Fluxbox on the server version, My opinion only.  I can work completly from the command line myself... but I want Ubuntu Server to thrive and a GUI would take it a long way with some of the newbies.

My soapbox is over...

x2

---

### Post by hyper_ch on 2009-02-07
> **carbm1 said:**
> However, this is the second time I have seen this exact same statement from you in two different posts today pertaining to a GUI on Ubuntu Server in a negative and non supportive way.
You assume it's negativ and non supportive ;) I question you to think as to why you need a gui ;) that's a different thing ;)

The entire point of Linux is freedom.  The freedom to setup things the way you want.[/QUOTE]
And also the freedom to ask others as to why they want things to be done a certain way ;)

> **carbm1 said:**
> Ever wonder why the other Linux distro's include a GUI? Ever wonder why they are doing so well?  Its kinda nice to see something after you install instead of the command prompt.
And you think this is a good enough reason for a server to have a gui?

---

### Post by carbm1 on 2009-02-07
Without getting in to a philosophical, no end, argument over this, The point is still that its the end users choice to have a GUI.  If people are going to start getting harassed every time they ask how to install a GUI then we should just start telling them that other Distro's have a GUI.  I think Canonical should support at least 1 Display Manager on the Server Edition. There is certainly enough people asking for it.

> **hyper_ch said:**
> And you think this is a good enough reason for a server to have a gui?
Do I think that most other distros supporting a GUI is good enough reason for Ubuntu to include a GUI?  Yes. I prefer Debian, I prefer the Philosophy of what Debian/Ubuntu is based off of.  If I wanted to learn for Career purposes I would instantly switch to CentOS and try to learn more towards RedHat. The latest CentOS comes with Gnome and you can download just about any RPM and it will work out of the box. Suse comes with a incredibly customized Gnome. 

Now, I also believe it should be an option to install or not to install the GUI. Guys like you and me don't need one to administer our servers.  I don't have gdm start on bootup so I'm not wasting resources. Last time I checked the basic Gnome didn't eat up more than 50MB...  RAM and HDD space is CHEAP!  There is no reason I can't spare 50MB when I need it.

As for me, the freedom to multitask in a GUI on my server. Including browsing the web and these forums.

---

### Post by darksideforge on 2009-02-07
> Hyper_CH... Mad props for the amount of time and effort you put into the Ubuntu Forums and helping others. I have read and appreciated many of your posts.  However, this is the second time I have seen this exact same statement from you in two different posts today pertaining to a GUI on Ubuntu Server in a negative and non supportive way.

hch,
I tend to agree with his assessment here; as a bona-fide newbie with Ubuntu Server, I'm really not sure that it's _your_ *responsibility* to ask why someone would or would not want a GUI with their server install, but for someone with 15,000+ posts, it would appear that you have a vast quantity of experience that could be put to better use than questioning someone's motives. You would be perfectly correct I should think in questioning what they want out of their system or what they expect in terms of performance, but questioning "why" they (I) want a GUI seems a little invasive. I've always been under the impression that the Swiss were supposed to be Neutral and impartial...  :-)

> I want to have a GUI because the box I have Ubuntu Server installed on also serves as a desktop when my desktop computer is tied up. All I need is Firefox most of the time. I choose to install xorg, gnome-core, gdm, ubuntu-gdm-themes.  This gives me a basic desktop, nothing special, just enough and I still get to keep my Ubuntu Linux instead of switching to another distro.

carbm1,
so far I've enjoyed reading your posts and gleaning advice from you. Regarding your posts on my questions in the other thread, the basic environment wasn't enough (no browser!) (no visual package manager!) and so I went back into sudo aptitude and downloaded all sorts of things. Now I'm not sure what I do and don't have...LoL!  My browser is working well and I'm navigating around on my desktop pretty well...kde is pretty new to me; the only other kde I've ever played with was Mandriva...for about 2 days before I trashed that stuff!! Back to Ubuntu desktop I went.  The one single kde application that I like seems to be the "Adept" package manager...MUCH MUCH better than the Synaptic that comes stock with Ubuntu Desktop 8.10!!

Is there any way for me to get rid of everything I have installed since the basic Ubuntu Server install was done...and get myself right back to the basic, command-prompt-only, barebones operation? (Without wiping the partition and doing another install of Ubuntu Server, of course...)  I'm thinking that I might go back and just do this:

```
sudo apt-get install xorg gnome-core gdm ubuntu-gdm-themes adept
```

and see what happens.

I know that there's a way to perform a sudo apt-get install (minus) and uninstall applications, but I haven't ever done it and I don't know much about it.  Suggestions?  As someone stated earlier, I would not be opposed to having to run startx every time I signed on...not that big of a deal, as long as I can figure out how to get back out to the Konsole or reboot and end up back at the command prompt. Is there an "endx" or "quitx" command I can run once I get to that point or would I simply need to reboot?

One last question: what do you think about the xfce environment vice Gnome or kde?

Thanks again for everyone's help!

---

### Post by hyper_ch on 2009-02-07
> **carbm1 said:**
> Without getting in to a philosophical, no end, argument over this, The point is still that its the end users choice to have a GUI.
It is their choice, however they should know what they do and if they just want to put on a gui to make them "feel" better then that's a bad thing to do. Informed choice is the key here.

> **carbm1 said:**
> If people are going to start getting harassed every time they ask how to install a GUI then we should just start telling them that other Distro's have a GUI.  I think Canonical should support at least 1 Display Manager on the Server Edition. There is certainly enough people asking for it.
What other distros? And they are not harassed ;) They just ask for a gui because most of them don't know any better. And just adding a gui because you don't know any better is just about one of the worst things to do. There's a reason for a "server" install. Linux servers generally run without gui and canonical has acknowledged that. That's why you get the desktop, alternate and server install.

> **carbm1 said:**
> Do I think that most other distros supporting a GUI is good enough reason for Ubuntu to include a GUI?  Yes. I prefer Debian, I prefer the Philosophy of what Debian/Ubuntu is based off of.  If I wanted to learn for Career purposes I would instantly switch to CentOS and try to learn more towards RedHat. The latest CentOS comes with Gnome and you can download just about any RPM and it will work out of the box. Suse comes with a incredibly customized Gnome.
Ubuntu comes with a gui also - on the Desktop and Live cd. Debian does not come by default with a gui, OpenSuse 11.1 does not have a gui selected either by default. CentOS - no clue, never tried - but then it seems not to be marketed as server os. And then I tend to think most distros do not install a gui on their own. You'll have to do/select that seperately (well, I have not tried all 400+ distros but the few I did, did not install a gui by default).

> **carbm1 said:**
> Now, I also believe it should be an option to install or not to install the GUI.
You can install a gui ;)

> **carbm1 said:**
> Guys like you and me don't need one to administer our servers.
And a gui doesn't make it simpler to administer a server... and for those that never done administration in a terminal, have a look here: [http://www.endperform.org/2008/03/27/server-administration-gui-or-no/](http://www.endperform.org/2008/03/27/server-administration-gui-or-no/)

> **carbm1 said:**
> As for me, the freedom to multitask in a GUI on my server. Including browsing the web and these forums.
A server can multitask easily, no need for a gui...
A server can surf the net easily, no need for a gui there also... but then I also ask, why do you have a server if you want to use it as desktop?

> **darksideforge said:**
> hch,
I tend to agree with his assessment here; as a bona-fide newbie with Ubuntu Server, I'm really not sure that it's _your_ *responsibility* to ask why someone would or would not want a GUI with their server install, but for someone with 15,000+ posts, it would appear that you have a vast quantity of experience that could be put to better use than questioning someone's motives.
And my experience tells me that most people asking for a gui on a server have no clue what a server is and hence they think they need one. So asking as to why they need a gui I make them reflect and hence one can sort out if a gui is truly needed. The only time I ever needed X on a server was to run a diablo 2 server. The WoW server, the CS server, the ET server that I run don't need X at all. Neither does everything else I used a server this far.


> **darksideforge said:**
> You would be perfectly correct I should think in questioning what they want out of their system or what they expect in terms of performance, but questioning "why" they (I) want a GUI seems a little invasive.
What's invasive about that? I just about their motivation. You pointed out my experience before and in most cases people just have wrong ideas about servers and first you need to sort that out. So asking why they need a server is a first step towards that.


> **darksideforge said:**
> I've always been under the impression that the Swiss were supposed to be Neutral and impartial...  :-)
Yeah, and all Swedes are blonde, americans are stupid, nobody likes the Kiwis, the middle east is full of terrorists...
What does this stereotype has to do with a server?

> **darksideforge said:**
> Is there any way for me to get rid of everything I have installed since the basic Ubuntu Server install was done...and get myself right back to the basic, command-prompt-only, barebones operation? (Without wiping the partition and doing another install of Ubuntu Server, of course...)
There are ways to remove most of it easily. [http://www.psychocats.net](http://www.psychocats.net) has howtos for "pure gnome/kde/xfce" and there you get the list of installed packges that ubuntu-desktop, kubuntu-desktop, xubuntu-desktop does... so the majority can be removed easily but not everything.

---

### Post by darksideforge on 2009-02-07
Once again, Hyper_ch gives great opinions and no facts. He doesn't answer questions, only criticizes others' questions. At first I thought that his 10,700+ posts meant that he would be a significant source of knowledge; now, sadly, I see that those posts are simply a way for him to show that he is better than others and is singularly responsible for spreading The Word about non-GUI server operations.
> 
It is their choice, however they should know what they do and if they just want to put on a gui to make them "feel" better then that's a bad thing to do. Informed choice is the key here.

Yes, thank you once again, hyper_ch...if you'll keep your mouth shut long enough for someone reasonable to answer our questions instead of throwing out your vitriol against servers with GUI's, we might actually learn something.

> "What other distros? And they are not harassed  They just ask for a gui because most of them don't know any better. And just adding a gui because you don't know any better..."

Not harassed, huh? Not like someone from Switzerland would know anything about that....maybe we should have let the Germans blitzkrieg your butts in 1942 like they did everyone else. Neutrality my ar$e.  We don't know any better, huh? WoW....not only are you some great super-swami-Linux-guru now, but you're a mind-reader and an omniscient demi-God as well, huh? Wonderful...I never knew I'd meet a God on this message board.

> And a gui doesn't make it simpler to administer a server... 

Oh really? Well, I find it interesting that I can read the boxes, prompts, instructions in a GUI and follow along quite nicely. Oh wait, I'm sorry...I forgot that I was talking to God here....Hey God! Since you're concerned and on here, would you mind terribly just shifting every single Unix, Linux, Java, Perl, and Gt_ command over to my brain?? Sure would make it EASIER if I don't have a GUI to get around....I mean, everyone just automatically knows all those commands dating back to 1983 or so, right? I mean, there isn't any reason to have a GUI to perform any sort of server operations, right? That's cause you're God and you can just GIVE US all that knowledge we need for all those commands...I keep forgetting that part. Those of us that don't have the CLI knowledge that you have, well, we wouldn't want to screw up a server with GUI...heaven forbid.

Please. I think I'll go puke now...or at the very least gag.

---

### Post by hyper_ch on 2009-02-07
> **darksideforge said:**
> Once again, Hyper_ch gives great opinions and no facts. He doesn't answer questions, only criticizes others' questions. At first I thought that his 10,700+ posts meant that he would be a significant source of knowledge; now, sadly, I see that those posts are simply a way for him to show that he is better than others and is singularly responsible for spreading The Word about non-GUI server operations.
Where are your facts? All your postings seem to indicate you don't really know what you're doing... and I do answer if you would take your time to consider what I say... as for the rest, if it makes you happy to go on a personal level, then go for it ;)

> **darksideforge said:**
> O
Yes, thank you once again, hyper_ch...if you'll keep your mouth shut long enough for someone reasonable to answer our questions instead of throwing out your vitriol against servers with GUI's, we might actually learn something.
See above ;)

> **darksideforge said:**
> Not harassed, huh? Not like someone from Switzerland would know anything about that....maybe we should have let the Germans blitzkrieg your butts in 1942 like they did everyone else. Neutrality my ar$e.  We don't know any better, huh? WoW....not only are you some great super-swami-Linux-guru now, but you're a mind-reader and an omniscient demi-God as well, huh? Wonderful...I never knew I'd meet a God on this message board.
See above ;)

> **darksideforge said:**
> Oh really? Well, I find it interesting that I can read the boxes, prompts, instructions in a GUI and follow along quite nicely.
What boxes? What prompts? The "benefit" you get is to use a fancy editor for the text files upon physical access... but then, well, fancy editors can also be used over nfs/sshfs/samba/... so, what makes it simpler to run a server with a gui?


> **darksideforge said:**
> Oh wait, I'm sorry...I forgot that I was talking to God here....Hey God! Since you're concerned and on here, would you mind terribly just shifting every single Unix, Linux, Java, Perl, and Gt_ command over to my brain?? Sure would make it EASIER if I don't have a GUI to get around....I mean, everyone just automatically knows all those commands dating back to 1983 or so, right? I mean, there isn't any reason to have a GUI to perform any sort of server operations, right? That's cause you're God and you can just GIVE US all that knowledge we need for all those commands...I keep forgetting that part. Those of us that don't have the CLI knowledge that you have, well, we wouldn't want to screw up a server with GUI...heaven forbid.
Getting personal again... if it makes you feel good, go ahead. Oh, by refusing to learn, well, why do you want to run a server then? Yeah, we all know all cli commands and all man pages by heart :)


> **darksideforge said:**
> Please. I think I'll go puke now...or at the very least gag.
Please go ahead...

Btw, how comes people always resort to a personal level if they run out of arguments or have none at all?

---

### Post by Ktykat on 2009-02-07
> **darksideforge said:**
> hch,
I tend to agree with his assessment here; as a bona-fide newbie with Ubuntu Server, I'm really not sure that it's _your_ *responsibility* to ask why someone would or would not want a GUI with their server install, but for someone with 15,000+ posts, it would appear that you have a vast quantity of experience that could be put to better use than questioning someone's motives. You would be perfectly correct I should think in questioning what they want out of their system or what they expect in terms of performance, but questioning "why" they (I) want a GUI seems a little invasive. I've always been under the impression that the Swiss were supposed to be Neutral and impartial...  :-)



carbm1,
so far I've enjoyed reading your posts and gleaning advice from you. Regarding your posts on my questions in the other thread, the basic environment wasn't enough (no browser!) (no visual package manager!) and so I went back into sudo aptitude and downloaded all sorts of things. Now I'm not sure what I do and don't have...LoL!  My browser is working well and I'm navigating around on my desktop pretty well...kde is pretty new to me; the only other kde I've ever played with was Mandriva...for about 2 days before I trashed that stuff!! Back to Ubuntu desktop I went.  The one single kde application that I like seems to be the "Adept" package manager...MUCH MUCH better than the Synaptic that comes stock with Ubuntu Desktop 8.10!!

Is there any way for me to get rid of everything I have installed since the basic Ubuntu Server install was done...and get myself right back to the basic, command-prompt-only, barebones operation? (Without wiping the partition and doing another install of Ubuntu Server, of course...)  I'm thinking that I might go back and just do this:

```
sudo apt-get install xorg gnome-core gdm ubuntu-gdm-themes adept
```

and see what happens.

I know that there's a way to perform a sudo apt-get install (minus) and uninstall applications, but I haven't ever done it and I don't know much about it.  Suggestions?  As someone stated earlier, I would not be opposed to having to run startx every time I signed on...not that big of a deal, as long as I can figure out how to get back out to the Konsole or reboot and end up back at the command prompt. Is there an "endx" or "quitx" command I can run once I get to that point or would I simply need to reboot?

One last question: what do you think about the xfce environment vice Gnome or kde?

Thanks again for everyone's help!

Since everyone else is arguing instead of trying to help you I will give it a try.

If you had installed gdm ( sudo apt-get install gdm ) you should be able to use the following in terminal to shutdown the GUI and return to the command line. 

sudo /etc/init.d/gdm stop

If you haven't installed gdm the command won't work. ( I know because I tried. ) The only other command I have been able to find that will shut down the GUI if gdm is not installed is...

Press Ctrl+Alt+Backspace

This will immediately kill the xorg server ( this is what was started when you typed the command startx to start the GUI. ) no questions asked. You will be left at the command line. Just be sure to have all of your files and folders closed prior to executing this. If I find a better way to do this I will add it here later.

---

### Post by carbm1 on 2009-02-07
The personal attacks need to stop now.  I don't care what color, race, religion, nationality... This is a support community on totally natural ground.

hyper_ch: you should seriously consider looking at CentOS, its fully binary compatible with RedHat.  Basically just the free version of RedHat Linux.

I like to have a GUI on my servers.  I only want a basic GUI not the full blown ubuntu-desktop package.  Yes its an option to install but it should be an option during installation.  Like it is in other distros.

OpenSUSE installs a GUI by default. SUSE Linux Enterprise Server installs a GUI by default. CentOS installs a GUI by default.  All meant to be server OS's.  No bloat though, just your basic GUI.

Now, with a little clarification... My servers are not in a RACK half way around the world.  I have Desktop Servers on KVM's. I like to have a basic GUI on these. My Virtual Ubuntu Servers do not have a GUI installed and are administered through SSH and Webmin. 

I wouldn't ever consider using Ubuntu Desktop for running a server. There are just too many desktop programs that could pose a security risk. 

What I do now is...

```
sudo apt-get install xorg gnome-core gdm ubuntu-gdm-themes firefox synaptic
```

I get just what I need and no fluff.  Still running the Server Kernel.  Again, I do not feel this poses a severe enough security threat to my server.  At that point its exactly how I want it. More functional for me.

---

### Post by hyper_ch on 2009-02-07
why should I consider CentOS?

And well, OpenSuse 11.1 doesn't install a gui by default and RHEL Server is more a desktop isntall then a server install... and those three are just a tiny faction out of the 300+ distros in which most don't install a gui by default.

---

### Post by carbm1 on 2009-02-07
Forgot to add that if you want to disable the GUI from starting at bootup you could do this:

```
sudo update-rc.d -f gdm remove
```

If you want to start it after you boot up you could do:

```
sudo invoke-rc.d gdm start
```

Its all good. Enjoy a GUI on your Server!

---

### Post by mistypotato on 2009-02-07
I'm about to install my very first Ubuntu server....and I was _[COLOR="Red"]very[/COLOR]_ disappointed to learn it didn't have a GUI.  :(

It would indeed be wonderful if it at least had an "option" to install one.  If I cannot install a GUI, I will stick with Winblows* for my server(s).

I've set up Winblows* servers but never Ubuntu servers.  In fact, I'm a Linux novice so I need all the graphical help I can get  :D

Carbm1...thanks for that...I will try it.


*[SIZE="2"]reference to that other OS by MS[/SIZE]

---

### Post by darksideforge on 2009-02-08
> **mistypotato said:**
> I'm about to install my very first Ubuntu server....and I was _[COLOR="Red"]very[/COLOR]_ disappointed to learn it didn't have a GUI.  :(

It would indeed be wonderful if it at least had an "option" to install one.  If I cannot install a GUI, I will stick with Winblows* for my server(s).

I've set up Winblows* servers but never Ubuntu servers.  In fact, I'm a Linux novice so I need all the graphical help I can get  :D

Carbm1...thanks for that...I will try it.


*[SIZE="2"]reference to that other OS by MS[/SIZE]



Misty,
Here are two other links to threads that I've participated in regarding putting a GUI on Ubuntu Server:

[http://ubuntuforums.org/showthread.php?t=1061629]("http://ubuntuforums.org/showthread.php?t=1061629")

and 

[http://ubuntuforums.org/showthread.php?t=1062261]("http://ubuntuforums.org/showthread.php?t=1062261")

Keep us informed in terms of what you decide to do or not to do and/or how it works out for you.

I'm going to try the X.org GUI next and see if I like that any better.

Just for argument's sake, some of the folks on here were great and managed to talk me through using the command line interface of the Ubuntu Server to install various portions of both the Gnome and Kde GUI's.  I didn't like the Kde at all, and I've yet to try the Xorg as I said, but several things (such as the browser) worked very well on Ubuntu Server for me.  I'll let you know how my experiments with xorg go.

---

### Post by torque154 on 2009-02-08
wow, this thread is heating up.  Lets add some more wood :P
> **mistypotato said:**
> I'm about to install my very first Ubuntu server....and I was _[COLOR="Red"]very[/COLOR]_ disappointed to learn it didn't have a GUI.  :(

It would indeed be wonderful if it at least had an "option" to install one.  If I cannot install a GUI, I will stick with Winblows* for my server(s).

I've set up Winblows* servers but never Ubuntu servers.  In fact, I'm a Linux novice so I need all the graphical help I can get  :D

Carbm1...thanks for that...I will try it.


*[SIZE="2"]reference to that other OS by MS[/SIZE]
I feel like I'm a linux noob, I don't know a lot about the interworkins, but you got to walk before you can run.  you probly shouldn't be using linux server if you havn't ever used linux.  In windows, if something breaks, how do you fix it? a configuration is not set right on the piece of software.  In linux you deal with the same problem, but in a different way.  instead of a fancy window that says yes or no, you have a text file that say 
```
Configure=YES
```
and you change to NO.  it's a different way of doing things, but why does everyone complain about it not being like windows?  it's different, don't throw it away b/c it works differently. 

Sure, GUI is nice but it's not necessary when your on a server. It not only slows the computer down, but I find it faster to just type in the command.  just learning the basic navigation such as changing directories, copying, moving, etc), adding users and groups and file permissions are pretty much 90% of what your going to need to know.  
I have yet to install the GUI on the server editions, but don't you have to configure your server from the config files anyway? so instead of using Vi or nano your using gedit (text editor).

someone said something about firefox and they wanted to use it. durring the install of ubuntu, you should also install OpenSSH.  then open up your SSH client and remotely connect to your server with your SSH client.  that way you can test, lookup things, and do whatever you need to do. 

I love GUI, but I don't see the need for a server application. I however think it would be a good idea to at least include the option on the cd. (like the alternative CD's)

---

### Post by andrea000 on 2009-02-08
here is my problem i run a linux terminal server and can't seem to get a desktop on the other linux pc's but to install a gui on the server any help. Please

XOXOXO

---

### Post by hyper_ch on 2009-02-08
what do you want to do on the server?

---

### Post by jimv on 2009-02-08
No one cares, but I agree with hyper_ch.  After doing technical support for years, I have discovered that many times users want to do something because they don't understand exactly why they want to do it, they don't know the alternatives, or they don't know why it might be better not to do it.

---

### Post by windependence on 2009-02-08
> **jimv said:**
> No one cares, but I agree with hyper_ch.  After doing technical support for years, I have discovered that many times users want to do something because they don't understand exactly why they want to do it, they don't know the alternatives, or they don't know why it might be better not to do it.

Ditto that. Most people new to Linux or any other Unices, want to run a server because it's "cool". The same reasons they want to run RAID on every box, set up a full blown DNS server for two local boxes, and use IPV6 because it's "there". 

This product is aimed at the rack server market. Here is what Canonical says about there being no GUI:

> **No X server by design**

  By design, Ubuntu Server Edition does not include an X server or any graphical desktop applications. This is a deliberate choice as we believe that most servers should be serviced remotely, are safer without the addition of code that needs direct communication from user space to hardware, and should not be used as a desktop by their administrator. 
 [INDENT] 	 	"*So I applaud the Ubuntu team’s common sense (and courage) in keeping the X Window System out of the default installation of Ubuntu Server.*"
	--Mick Bauer in April 2008 Linux Journal - "Security Features in Ubuntu Server"   	
[/INDENT]

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

THIS is why they didn't put a GUI in the SERVER version of the OS. Not to pi$$ people off, but to make it a better performing product on what it was intended to run on, yep, SERVERS. You can run a torrent server just fine on the desktop edition. In fact, to get your feet wet most server packages will run just fine on that kernel, and you aren't using server class hardware anyway. 

Look at these pages and read them: [http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition) 

Note the pictures on the pages. They are of data centers, not Billy Jo Jimbob's torrent box in the bedroom. Look at the text, it mentions BUSINESS servers lots of times, and uses words like "Ubuntu Server Edition is an energy efficient, low memory and disk footprint operating system that helps build server functions that respect our environment with no compromise on agility and versatility". Does that sound like they want a GUI on it? They have a product for that.

Don't get me wrong, for desktop use I love a good GUI to keep things organized. That's why I run a Mac for my desktop, BUT.......I run BSD on most all of my servers. Definitely no GUI there, but rock solid, scalable, and very small. It's an easy concept. Use the right tool for the job at hand.

-Tim

---

### Post by bigbearomaha on 2009-02-08
Just as a side note, If you do install a GUI on a server, it is easy to minimize the risks and resource usage of having the GUI running when no one is using it by switching the runlevel .

most Linux start in runlevel 5, which will start the X server.  However, if you are actually sitting down at the machine and finish the work you are doing, you can switch to runlevel 3 which shuts down X server and all GUI apps. 

Most people who are not comfortable with command line only usually comes from years of working in a forced GUI environment provided by other OS's.  it's the nature of the beast I guess.

If after you have used the GUi to get it all set up comfortably, you can switch to runlevel3 and then if you still want to use a GUI environment for admin, you can use an app like webmin or similar.

Just tossing in two cent, now I'm broke.

Big Bear

---

### Post by darksideforge on 2009-02-08
> **bigbearomaha said:**
> Just as a side note, If you do install a GUI on a server, it is easy to minimize the risks and resource usage of having the GUI running when no one is using it by switching the runlevel .

most Linux start in runlevel 5, which will start the X server.  However, if you are actually sitting down at the machine and finish the work you are doing, you can switch to runlevel 3 which shuts down X server and all GUI apps. 

Most people who are not comfortable with command line only usually comes from years of working in a forced GUI environment provided by other OS's.  it's the nature of the beast I guess.

If after you have used the GUi to get it all set up comfortably, you can switch to runlevel3 and then if you still want to use a GUI environment for admin, you can use an app like webmin or similar.

Just tossing in two cent, now I'm broke.

Big Bear

EXCELLENT INFO! How do I switch from RunLevel 5 to RunLevel 3?

Thanks for this great input!

---

### Post by HermanAB on 2009-02-08
Note that especially on a server, there is usually no shortage of disk space and the Linux system usually has its own partition separate from the data partitions. So, uninstalling the GUI stuff doesn't gain you anything - it simply frees up disk space where it isn't used anyway.

So, if you wish to run the server without a GUI, simply change the runlevel to 3:
# sudo init 3

and when you want to start the GUI up again:
# sudo init 5

There is no need to reboot or uninstall anything, this is what the runlevels are for.

Cheers,

Herman

---

### Post by bigbearomaha on 2009-02-08
Herman got it.

if you are sitting at the desktop, at c/l just type in "sudo init 3" ( make sure you are done doing all the stuff you needed to do.

Also, if you plan to use GUI remote admin, I like webmin myself and it's an easy install, then you can log in from any machine on the lan at [https://IPADDY:10000](https://IPADDY:10000)

and you never have to start up the GUI on that machine again if you don't need/want to.

Now, if you do decide to keep the GUI on the machine running in runlevel 5, you can access your GUI apps remotely as well using ssh -Y

Big Bear

---

### Post by redroad55 on 2009-02-08
I've certainly enjoyed reading this thread although I had to cringe at some of things said and at times I heard The "Dire Straits" playing "I want my GUI" "my bandwidth for nothing and My code for free " ..Or you know your a geek when you have more computers than furniture . I crack myself up..

  On a more serious note I tend to agree with hyper_ch ..
>  why do you want to have a gui on a server anyway?
This is why..When I was confined to microsoft's blatantly poor choices made in my behalf I had to do something .. Linux and the contributor's of these forums have been my saving grace , pushing me to learn and take responsibility for my unwillingness to leave my plug and play computing life style .. It is increasingly clear that microsoft has no intention whatsoever to put the end user in any other posistion than to be eternally dependent on them , spoon feeding software with only there bottom line as their guide..That being said when I first read that question  "why do you want to have a gui on a server anyway?" It made me feel the same way I did when I first thought about leaving windows behind .. It is a challenge to learn and to contribute what you learn to those that need help to get to the next step and have them learn something besides copying and pasting code in a terminal..

   Why is this important ? Looking at was said here by Windependence
> Note the pictures on the pages. They are of data centers, not Billy Jo Jimbob's torrent box in the bedroom. Look at the text, it mentions BUSINESS servers lots of times, and uses words like "Ubuntu Server Edition is an energy efficient, low memory and disk footprint operating system that helps build server functions that respect our environment with no compromise on agility and versatility". Does that sound like they want a GUI on it? They have a product for that.

 Energy efficiency is the key here .. every keystroke , every line of code translates to cpu usage which = electricity consumed. My point more specifically is the more people that become capable of writing code the chances of us writing more efficient code goes up . code efficiency = less power consumed ..What do you think for example it costs the world in terms of electricity for a poorly written line of code in a major os distribution like windows xp ? 

Try this example .. I live in the land of my ancestors it had some of the best freshwater fisheries in the world and in a matter of 150 years of the industrial revolution there is not a single body of water that I can go fish to feed my family. All , I repeat All the tributaries here, the governments recommendation is "Pregnant women and children should not eat any fish taken from these tributaries" .. Not to mention the 2 super fund sites ..How did this happen? inefficient use of natural resources fueled by the bottom line..

So for me "why do you want to have a gui on a server anyway?" that's at the very least a question worth asking .. 

Best to you all

---

### Post by bigbearomaha on 2009-02-08
I couldn't care less how he or anyone else runs their computer.   I run mine the way I want, he can run his the way he wants.

It's his server, not mine.  He came, asked a question as to how, I told him how.

Don't care why, It's none of my business. Not my server.

Big Bear

---

### Post by hyper_ch on 2009-02-08
> **bigbearomaha said:**
> I couldn't care less how he or anyone else runs their computer.   I run mine the way I want, he can run his the way he wants.

It's his server, not mine.  He came, asked a question as to how, I told him how.

Don't care why, It's none of my business. Not my server.

Big Bear

Give a man a fish and you feed him for a day. Teach a man to fish and you feed him for a lifetime.

---

### Post by redroad55 on 2009-02-08
> Linux and the contributor's of these forums have been my saving grace , pushing me to learn and take responsibility for my unwillingness to leave my plug and play computing life style

that includes you bigbear..Best to you

---

### Post by bigbearomaha on 2009-02-08
> **hyper_ch said:**
> Give a man a fish and you feed him for a day. Teach a man to fish and you feed him for a lifetime.


This isn't school.  if he wanted a class, he would have went to school and paid for the privilege like I did.

if he only wants to eat for one day, that's up to him, he didn't ask me to teach him how to fish, he just asked how to get there. he still has to do the work.

Now as I feel this is leaning toward me coming off argumentative wen I hadn't meant to,  I will let it be.  you folks have a fine day.

Big Bear

---

### Post by hyper_ch on 2009-02-08
The more he learns the less he'll ask for support here... if the server is properly setup then he will manage on his own... if it's not, then questions on questions and frustration upon frustration will arise ;)

---

### Post by redroad55 on 2009-02-08
I can only speak for myself but for me its the only way I have of learning what I need to..and you bigbear are the teacher whether you want to accept that or not .. As far as a formal education this is as good as it gets for me ... google and the forums ..Peace out

---

### Post by andrea000 on 2009-02-08
I am new to linux i use my server for a file server.I am only  experimenting with terminal server.I am sorry i should not be asking here.I think i am making some people mad i am sorry i should post my own question but every body here seems real 
smart.I am so sorry if i made anyone mad.

---

### Post by redroad55 on 2009-02-08
This is a good of a place as any for your question> here is my problem i run a linux terminal server and can't seem to get a desktop on the other linux pc's but to install a gui on the server any help. Please
but more than anything you need to be more specific of where you are and where you would like to go short term as well as long term with your project ...

I can only speak for myself but I rather enjoy a spirited debate ..
Post back any thoughts or questions..Best to you

---

### Post by cariboo on 2009-02-08
@andrea000

This debate has been ongoing for years, and will never be resolved. I personlly don't use a gui on my server, but I say use what serves you best. 

Have a look at these guides:

[UbuntuLTSP]("http://help.ubuntu.com/community/UbuntuLTSP?highlight=(LTSP)")

[UbuntuLTSPQuickInstall]("http://help.ubuntu.com/community/UbuntuLTSP?highlight=(LTSP)")

[Edubuntu Guide]("http://www.edubuntu.org/Documentation")

Jim

---

### Post by wordmaster on 2009-02-09
After all the Gui comments, I almost hate to ask, but now that y'all have helped me get my gui working, how do I set up Firefox? I tried going to the install section and installing mozilla, but there are a whole bunch of mozilla related items there and it tells me I have to install another browser suite first, etc., etc.

For a rank novice like me, it gets a little confusing. My prior little tad of experience was with the desktop version which automatically had Firefox installed. Any and all help appreciated.

BTW, I started out with RS-DOS and OS-9 (not from Mac) and worked my way up through MS-DOS so I am not command line phobic, I simply have not learned all the commands and structure in linux yet and and trying to ease into it.

---

### Post by Coreigh on 2009-02-09
Even when you have a GUI the command line is still the easiest option sometimes.
```
sudo apt-get install firefox
```

Adding the -s switch to apt-get will do a "dry run" to tell you what packages would be included if you install a package. For example:
> sudo apt-get [COLOR="Red"]-s[/COLOR] install firefox
Would show the steps without making changes. You can then decide if you want to go ahead with the installation.

My 2cents on the GUI argument:
  A) Its your server do what you want
  B) Some people are simply more comfortable with visual cues. A GUI may not add *ANY* functionality (and in some cases my remove some) but most people grew up with a graphical interface and converting your habits from that to a text based way of operating can be challenging. Personally The longer I use linux the more I do with the command line. In Hyper_ch's defense many many how-to's and tutorials are written for using the command line and thus it is very useful to be comfortable with it.

... But you have to start somewhere and you may as weel start with what you know. Just don't try to stay there or you'll never learn anything new.

---

### Post by redroad55 on 2009-02-09
here are a couple of links to help with command line ed. 
[http://linuxcommand.org/learning_the_shell.php]("http://linuxcommand.org/learning_the_shell.php")
[http://linuxcommand.org/index.php]("http://linuxcommand.org/index.php")
Best to you

---

### Post by andrea000 on 2009-02-09
I guess what i was saying is i am like a lot new to linux i set up LTS
and have been learning linux for a while now but still like a lot do not know a lot about it.so how do i get a desktop on my thin client's without installing a desktop on the sever?Thank you all so much

XOXOXOXO

---

### Post by redroad55 on 2009-02-09
There are still unanswered questions like do the thin clients require internet access ? Is it just a local area network where no internet access is required at all ? what does your network do, office? classroom? home network? the more specific you can be the easier it will be to help you , so take your time right down what your goals are and describe them back here and I or someone else will help you get there but more information is needed..Post back..
Best to you

---

### Post by andrea000 on 2009-02-10
> **redroad55 said:**
> There are still unanswered questions like do the thin clients require internet access ? Is it just a local area network where no internet access is required at all ? what does your network do, office? classroom? home network? the more specific you can be the easier it will be to help you , so take your time right down what your goals are and describe them back here and I or someone else will help you get there but more information is needed..Post back..
Best to you

Thank you internet access is not required but i would like to have it.What i am doing is experimenting right now i am running a few open office programs but i would like to use more google earth etc.also i would like to use it as a email and file server
but i am more interested in running some software off it so the three pc's in my house can run the same thing and my files are always the same.anyone that has any suggestions please add them 
i need a lot of help learning this.Thank you all

XOXOXOXO

Thank you all sooo much

---

### Post by wordmaster on 2009-02-11
Thank all of you very much for your help. My GUI is up and running and I am now ready to start figuring out how this OS works and get ready to actually use it as a server.

All the conversations and viewpoints are appreciated and are helpful as well as the background helps me to gain a better understanding of the whole thing.

---

### Post by TheFuturian on 2009-02-11
Hi All,

Am new to the forum, however was perplexed by the same challenge on my first build of Ubuntu Server (8.04.2)... He's the magic line I pulled together to get [Gnome]("http://en.wikipedia.org/wiki/GNOME") up and running smoothly:-

```
sudo apt-get install xorg xserver-xorg gnome-core gdm fast-user-switch-applet ubuntu-artwork synaptic update-notifier policykit-gnome gnome-system-monitor gnome-media gnome-screensaver
```

Some other nice optional 'apt-get' options IMHO (which I just throw on the end if desired) are:-
[LIST]
[*]gnome-netstatus-applet
[*]firefox (Much loved internet browser)
[*]file-roller (Archive Manager)
[*]vino (VNC Server for Gnome)
[*]filezilla (Schweet FTP Client)
[/LIST]

I prefer the GUI as a choice, rather then having it come up at boot... Get the best of both worlds that way ;-)

Have had difficulty trying to configure any sound, gave up. No biggie, in fact it's probably a blessing in disguise.

---

### Post by darksideforge on 2009-02-12
Now that I've been up on a minimal install of Xubuntu for almost a week, I'm ready to wipe the system and start with some new stuff. If I reinstall ubuntu server, will fluxbox work okay as a minimal desktop GUI as I continue to learn CLI (much easier with all those links posted by everyone to the MAN pages and the CLI tutorials!)?  I know I could do a

sudo apt-get install ubuntu-desktop

but I just thought I might be better off switching up and using a different "crutch" this go-round. Any suggestions on the fluxbox?  Also, after (IF you guys recommend it) I install the fluxbox, will Firefox work okay with the fluxbox in sudo init 5 if I install it from the command line?

Thanks again.

---

