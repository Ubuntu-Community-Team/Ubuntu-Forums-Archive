---
title: "Is there a list of Untrusted (High Risk) Repositories ?"
date: 2012-08-01
forum: Security
---

### Post by patriot56 on 2012-08-01
Greetings Forum. 
My question is, (and I hope this is posted in the right area) is there a known list of repositories, ppa.'s, etc. that are considered high risk? 
 I realize that Linux, by its very nature, is for the most part,  resilient to malicious code, (virus', spyware, malware, etc.).   That being said, are there even any security threats out there (as it relates to this subject) that a new Linux user should be aware of when adding Repositories?  And if so, what can be done to avoid these risks?
 I suspect education is your best friend as a new Linux user and that is exactly what I am alluding to.  As a new Linux convert I am always looking over my shoulder, as it were, anytime I download/install  anything.  
I realize that this is due entirely to years of exposure to an open 'Window' that allowed any and every virus riding on the wind to enter and infect.  
I have been a Linux user for about 2 years now but I generally don't venture outside of the parameters of the original install.  However, going back to what I said earlier, I believe that if I am going to learn Linux I am going to have to explore. I just want to do it as responsibly as possible.  That is the reason for my question.  
Are there Repositories that should be avoided...and if there are, is there a source somewhere that lists these Repositories?  
My search of the Internet has revealed some pretty alluring applications for Linux but with some of these applications, a little common sense tells me that they are offered by, umm?  Less than reputable sources? [-X 

Thank you for your help and advise.  
Any resources that can be provided will be enormously appreciated.   Thanks again.  

Respectfully,

 - Joe -

---

### Post by mikewhatever on 2012-08-01
I am having difficulties imagining, what exactly do you want to learn about Linux that needs adding repositories?

---

### Post by patriot56 on 2012-08-01
> **mikewhatever said:**
> I am having difficulties imagining, what exactly do you want to learn about Linux that needs adding repositories?
For example; there are repositories that are necessary to the ongoing use and updating of the OS and then there are repositories that are sources for "fluff", for example, UE Ultimate Edition has its own repository because of how much the OS is modified. (as I understand it. Correct me if I'm wrong).
This is what I meant by examining other repositories.  I just want to know if it is safe to do that?
There are some repositories that need to be added in order to obtain applications that are not part of the distribution's original release.
Again, I am new to Linux so if I am mistaken, please enlighten me. :???:

---

### Post by houseworkshy on 2012-08-01
I know what you mean, a "don't add this one folks, reports of malicious or very badly coded broken content" type thing.  One couldn't expect the team of any given distro to monitor everywhere else but there my be a user reports type site out there.  Wouldn't mind seeing something like that myself, especially as apt;urls can run repository adding scripts.  Someday a repository blocklist may even be a good idea as apt;urls can be hidden.
May have had trouble with one of those myself, or more probably didn't because it was prior to a reinstall anyway and I was even less informed then than I am now.  
As I recall it was some version of cinelerra which bunged in a sort of kde password protection popup in my gnome enviroment which I couldn't get past.  Far more likely it was a side effect of my learning by breaking phase but a quick check would have helped me to know.

---

### Post by Ms. Daisy on 2012-08-01
> **patriot56 said:**
> My question is, (and I hope this is posted in the right area) is there a known list of repositories, ppa.'s, etc. that are considered high risk? 
I realize that Linux, by its very nature, is for the most part, resilient to malicious code, (virus', spyware, malware, etc.). That being said, are there even any security threats out there (as it relates to this subject) that a new Linux user should be aware of when adding Repositories? And if so, what can be done to avoid these risks? 
Learn about the Ubuntu repositories & how to add/remove them here- this link directly answers a lot of your questions: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu). It's a matter of trust. AFAIK, the only way to be truly certain is to inspect the code for every app you want to install.
 
I suggest you also check out the [Basic Security Wiki]("https://wiki.ubuntu.com/BasicSecurity") to learn about security threats in Ubuntu. But I think you already understand that you should try to install software from the Ubuntu Software Center and avoid installing software from random web pages. 
 
And because I'm a masochist I'll address this bit: "I realize that Linux, by its very nature, is for the most part, resilient to malicious code, (virus', spyware, malware, etc.)." **Linux isn't any more resilient to malicious code than any other operating system.** It just hasn't been targeted by mass-market malware authors like Windows has. There are all kinds of proof-of-concept malware/viruses/spyware/etc. for Linux. Plus (so I'm not OT) if you download random software directly from the internet for Linux a lot, you're bound to find yourself owned by something malicious.

---

### Post by QIII on 2012-08-01
"Social Engineering" is as dangerous to Linux users as to Windows users.

"Hey, you just gotta install this!  Just sudo ..."

Ask here first.  It's a lot better than asking for help fixing something later.

---

### Post by patriot56 on 2012-08-01
> **houseworkshy said:**
> I know what you mean, a "don't add this one folks, reports of malicious or very badly coded broken content" type thing.  One couldn't expect the team of any given distro to monitor everywhere else but there my be a user reports type site out there.  Wouldn't mind seeing something like that myself, especially as apt;urls can run repository adding scripts.  Someday a repository blocklist may even be a good idea as apt;urls can be hidden.
May have had trouble with one of those myself, or more probably didn't because it was prior to a reinstall anyway and I was even less informed then than I am now.  
As I recall it was some version of cinelerra which bunged in a sort of kde password protection popup in my gnome enviroment which I couldn't get past.  Far more likely it was a side effect of my learning by breaking phase but a quick check would have helped me to know.
Thank you **houseworkshy** for your post.  This is *exactly* what I am talking about!  For anyone that is new to Linux (especially coming over from Windowz) are going to be wary of infecting their system, and most, I'm sure have heard that Unix/Linux systems "don't have to worry about virus' ", while this may be true in the conventional sense it is misleading in my opinion. I agree with you that it would be good to see a repository blocklist/blacklist especially if it were native to the distribution and added at the time of the install.

Thank you again for your response. :wink:

- Joe -

---

### Post by patriot56 on 2012-08-01
> **QIII said:**
> "Social Engineering" is as dangerous to Linux users as to Windows users.

"Hey, you just gotta install this!  Just sudo ..."

Ask here first.  It's a lot better than asking for help fixing something later.

[SIZE=3]**Ask here first.  It's a lot better than asking for help fixing something later**[/SIZE].
This has got to be one of the *single* most inelegant statements I've seen in this forum. :KS I sincerely mean that.
It is amazing just how far an ounce of prevention will go...
Thank you QIII for your reply.  It amazes me sometimes, how many people install things that they know nothing about, don't take the time to research, then complain when their actions result in a loss of data and complete re-install.
I've been there myself.
Thankfully, I learned, (at the expense of irreparable damage to data)  #-o  ](*,)

---

### Post by houseworkshy on 2012-08-01
Asking here is a good idea, I remember one newbie asking about installing a crippleware torrent client which wanted root access.  We talked him out of it.  It was obvious from the site that it was dodgey.  But he was a newbie who'd only put linux in a day or two ago and didn't know what the red flags were yet.
Another thing to do is to search for the name of whatever the thing is and see if others have had problem.  "+programx +forum"  is often a productive search.
All that sort of thing is for deliberately installing things.
Imagine a case where this is not the case and social engineering is involved.  Say a website has some apt;url in it.  The first one would be overt, wondergame or putting gnome2 on 12.04 for example ( a few hundred may have gone for that).  The user would click on it and enter the password just as expect to.  If a little further down the page another one was hidden, a link or image, any clickable object in fact.  Well the password box wouldn't appear if the second one was clicked, or even perhaps hovered over, within the 15 minets of the sudo timer.  If the user fell for it any old repository could be bunged in, any popup box could appear and anything could be installed and run, and wallop they've got a compromised system. They wouldn't even know it had happened, novice and expert alike.  
I'm not a fan of apt;urls and don't find the other methods of installing too difficult for me so would actually like to turn apt;url functionality off altogether.  The nearest I know to do is reduce the sudo timers default and sudo -k a lot but that is hardly good defence.  As apt;urls exist a repository blocklist is probably vital.  Even if one did exist it wouldn't be adequate anyway as malicious types could easily write new repositories by the sack load.
Meanwhile If anyone knows how to turn apt;url functionality off I'd like to know how it's done.

Sudden blast of belated logic.  Just had a quick ferrit,  and it has an unfinished man page, counts as a command eh?.  So does anyone know if a "sudo apt-get uninstall apt;url" or "sudo apt-get purge apt;url" would damage the rest of my system?

---

### Post by 1clue on 2012-08-01
Holy cow.

I strongly recommend you scroll up to what Ms. Daisy said, and go read for awhile from those links.  If they don't scare some sense into you, then you're asleep.

Linux is no more secure from malware than Windows overall.  The guys who insist it can't be compromised are either talking about the prevalence of Microsoft-oriented malware and the statistical chances of a Linux box being able to run one, or they're misinformed, or they're trying to convince you that you're safe so you don't pay attention when they install their malware on your system.

Think about this:  You're hooking up a software repository which is not only specific to Linux but specific to Ubuntu.  They can write absolutely anything they want, and if they put it into an Ubuntu-oriented repository then you're going to install it no questions asked?

I don't have any proof of this, but I'm guessing that network-based malware probably got started on UN*X before it got onto anything Microsoft.  UNIX was the first operating system to be networked, and was the most frequently used server because of it for a lot of years.  Networking software is super simple in UN*X, anything from a full blown spam-bot to something as innocuous as a script that opens all the DVD trays in the server room at the same time, while the IT guy is standing there.  (Guilty as charged on that last one, it was a hoot!)

---

### Post by houseworkshy on 2012-08-01
It comes down to trust.  One has to rely on experts checking the official repositories, so far they've done an amazing job ( hats off to them ) and kept the rubbish out  So rare that something bad makes it to a repository of any main distro it's a news story when it does.  If one sticks to those one should be ok, it's the shall we say "unofficial" repositories which pose the greatest risk. Cross platform things,  browsers and addons, virtual machines like java or wine, any sharing like p2p,  torrents or MUD games, social network sites plus wireless connections, also have damage potential.  Social engineering is a big one and not only for the daft.  For example if an institution you have dealings with,  such as your bank for example, accepts your identity based on questions like "date of birth" and "mothers maiden name" do you really want to bung those details in a discover your familly tree type site?   Thinking about things as a whole rather than focusing on what holds your interest in the moment is also a form of defense.

---

### Post by patriot56 on 2012-08-01
> **Ms. Daisy said:**
> Learn about the Ubuntu repositories & how to add/remove them here- this link directly answers a lot of your questions: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu). It's a matter of trust. AFAIK, the only way to be truly certain is to inspect the code for every app you want to install.
 
I suggest you also check out the [Basic Security Wiki]("https://wiki.ubuntu.com/BasicSecurity") to learn about security threats in Ubuntu. But I think you already understand that you should try to install software from the Ubuntu Software Center and avoid installing software from random web pages. 
 ......
Thank you for your reply.  Please note, as I said in my thread, I am a new Linux user and I don't know anything about Linux coding, so I wouldn't have a clue what to look for even if I knew how to display the code.  **I whole heartedly agree with you that it is a matter of trust**, but tragically there are those out there that don't. And because there are those that feed on trust and abuse it, we are forced to engage in this kind of discussion. If we could trust every repository out there, there would be no need for me to post this inquiry. ;-)

Thank you again Ms.Daisy for your input and for the valuable links you provided.
I promise you, I will read them and hopefully learn from them.
I would greatly desire to be one of the persons on this forum that is helping others instead of always looking for help.:(

Respectfully,

- Joe -

---

### Post by Lyfang on 2012-08-01
Canonical repositories should be safe, as well as Canonical Partners software repositories. See also: [Idea #27418: PPA can thret security risk - no way to find out which is trusted PPA]("http://brainstorm.ubuntu.com/idea/27418/")

---

### Post by patriot56 on 2012-08-01
> **houseworkshy said:**
> It comes down to trust.  One has to rely on experts checking the official repositories, so far they've done an amazing job ( hats off to them ) and kept the rubbish out  So rare that something bad makes it to a repository of any main distro it's a news story when it does.  If one sticks to those one should be ok, it's the shall we say "unofficial" repositories which pose the greatest risk. Cross platform things,  browsers and addons, virtual machines like java or wine, any sharing like p2p,  torrents or MUD games, social network sites plus wireless connections, also have damage potential.  Social engineering is a big one and not only for the daft.  For example if an institution you have dealings with,  such as your bank for example, accepts your identity based on questions like "date of birth" and "mothers maiden name" do you really want to bung those details in a discover your familly tree type site?   Thinking about things as a whole rather than focusing on what holds your interest in the moment is also a form of defense.
Well said houseworkshy. Well said.=D>
Those experts have done a better job with the official repositories than anyone could expect.  And as I understand it, most if not all of them are volunteers?  That's remarkable indeed.
With that said, you addressed the very nature of my original post.  It is the "unofficial repositories that I am inquiring about.  It is a list of these "unofficial repositories that I am addressing.  I just think that (at the very least, for new Linux users anyhow) it would be great to have a blacklist of these types of repositories.  Kind'a like, maybe the way "virus" databases are updated and distributed.
I'm just thinking out loud here.  The risk of doing this is that I am new to Linux and am probably making a fool of myself by suggesting solutions about something I no nothing about. 
Damn the torpedos, full steam ahead!!!:roll:

---

### Post by houseworkshy on 2012-08-01
I assume the official repositories to be safe.  Also adding a repository is a deliberate act so the best advice is always be leery of doing it, read around first at least.  Mediabuntu for example is generally trusted too.  It's not alway bad, most projects have a development repository for example.  Some people will add  one in the full knowlage that the program though the latest will have bugs, they are well aware of this in advance, often they've added the repository to help fix them.  So the rule may be only add what you trust or know about.
apt;urls could, in specific scenarios, be an exeption to this forknowlage, that is the only concern I have about them.  Other than the help on this site I tend not to trust them.  This distrust may only be my paranoia as I have not yet heard of hidden ones being used to add poison repositories when one is in sudo mode but in theory it could be done.  So I mostly avoid them but if I do use one I open a terminal and "sudo -k", this stops the timer and kills sudo.  Should I encounter another after that it won't just proceed but ask me first, so I have the choice and incidentially get a detailed view of what is going where, which I like anyway..  

They're not bad in themselves.  In fact as you are fairly new I strongly recomend [https://help.ubuntu.com/](https://help.ubuntu.com/) which gives a good overview.  Choose the appropriate version.  It is peppered with trustworthy apt;urls of things you may want.  You'll see what I mean if you use one quickly followed by another.  You'll also see what happens if you use sudo -k after using one.  It resets to asking the question again. Also I can see why they exist, brilliant the way they are used here, perfect for a newbie, learn the basics at the same time as setting up.  It's elsewhere I have a trust issue with the method.  The danger of adding a poison repository by accident is still remote.  sudo -k after each apt;url may be premature but it's never too early to aquire a good habit.

---

### Post by patriot56 on 2012-08-01
> **Lyfang said:**
> Canonical repositories should be safe, as well as Canonical Partners software repositories. See also: [Idea #27418: PPA can thret security risk - no way to find out which is trusted PPA]("http://brainstorm.ubuntu.com/idea/27418/")
Thank you Lyfang for your response. 
I will look at the link that you provided.
This is exactly what I was looking for, information.

---

### Post by vexorian on 2012-08-01
> **patriot56 said:**
> Greetings Forum. 
My question is, (and I hope this is posted in the right area) is there a known list of repositories, ppa.'s, etc. that are considered high risk? 
 I realize that Linux, by its very nature, is for the most part,  resilient to malicious code, (virus', spyware, malware, etc.).   That being said, are there even any security threats out there (as it relates to this subject) that a new Linux user should be aware of when adding Repositories?  And if so, what can be done to avoid these risks?
 I suspect education is your best friend as a new Linux user and that is exactly what I am alluding to.  As a new Linux convert I am always looking over my shoulder, as it were, anytime I download/install  anything.  
I realize that this is due entirely to years of exposure to an open 'Window' that allowed any and every virus riding on the wind to enter and infect.  
I have been a Linux user for about 2 years now but I generally don't venture outside of the parameters of the original install.  However, going back to what I said earlier, I believe that if I am going to learn Linux I am going to have to explore. I just want to do it as responsibly as possible.  That is the reason for my question.  
Are there Repositories that should be avoided...and if there are, is there a source somewhere that lists these Repositories?  
My search of the Internet has revealed some pretty alluring applications for Linux but with some of these applications, a little common sense tells me that they are offered by, umm?  Less than reputable sources? [-X 

Thank you for your help and advise.  
Any resources that can be provided will be enormously appreciated.   Thanks again.  

Respectfully,

 - Joe -
From a security stand point, white lists are better than black lists. You should instead ask for a list of reliable repositories.

---

### Post by patriot56 on 2012-08-01
> **vexorian said:**
> From a security stand point, white lists are better than black lists. You should instead ask for a list of reliable repositories.
Good point!  I was so focused on the bad that I didn't even consider that if one is familiar with the trusted repositories there is no reason to know about the bad ones.:-k
Thank you.  That's great advice.
Your point is well taken.

---

### Post by patriot56 on 2012-08-01
> **1clue said:**
> Holy cow.

I strongly recommend you scroll up to what Ms. Daisy said, and go read for awhile from those links.  If they don't scare some sense into you, then you're asleep.

Linux is no more secure from malware than Windows overall.  The guys who insist it can't be compromised are either talking about the prevalence of Microsoft-oriented malware and the statistical chances of a Linux box being able to run one, or they're misinformed, or they're trying to convince you that you're safe so you don't pay attention when they install their malware on your system.

Think about this:  You're hooking up a software repository which is not only specific to Linux but specific to Ubuntu.  They can write absolutely anything they want, and if they put it into an Ubuntu-oriented repository then you're going to install it no questions asked?

I don't have any proof of this, but I'm guessing that network-based malware probably got started on UN*X before it got onto anything Microsoft.  UNIX was the first operating system to be networked, and was the most frequently used server because of it for a lot of years.  Networking software is super simple in UN*X, anything from a full blown spam-bot to something as innocuous as a script that opens all the DVD trays in the server room at the same time, while the IT guy is standing there.  (Guilty as charged on that last one, it was a hoot!)
In response to your post 1clue, I am in the process of reading the invaluable information that Ms.Daisy provided but it is going to take some time to filter through all to the information/advice that has been offered.
After reading your post I couldn't help feel like you were under the impression that* I* was making the statement that Linux is more secure than Windows. In truth, I think it is, but I was in no way making a statement of *fact* that Linux cannot be compromised.  I was simply commenting on what I read somewhere and looking for help understanding it.
I believe that Ms.Daisy has offered some valuable information and I will read through it and apply it as with all of the links and information that everyone else has provided.

On a separate note, I'm not as naive as your post would indicate. I don't install anything on my computer unless I have thoroughly researched it and am convinced based on the **balance of probabilities** that it is the correct course of action.  Hence the reason for this thread.
I am simply trying to learn.

---

### Post by patriot56 on 2012-08-01
> **houseworkshy said:**
> I assume the official repositories to be safe.  Also adding a repository is a deliberate act so the best advice is always be leery of doing it, read around first at least.  Mediabuntu for example is generally trusted too.  It's not alway bad, most projects have a development repository for example.  Some people will add  one in the full knowlage that the program though the latest will have bugs, they are well aware of this in advance, often they've added the repository to help fix them.  So the rule may be only add what you trust or know about.
apt;urls could, in specific scenarios, be an exeption to this forknowlage, that is the only concern I have about them.  Other than the help on this site I tend not to trust them.  This distrust may only be my paranoia as I have not yet heard of hidden ones being used to add poison repositories when one is in sudo mode but in theory it could be done.  So I mostly avoid them but if I do use one I open a terminal and "sudo -k", this stops the timer and kills sudo.  Should I encounter another after that it won't just proceed but ask me first, so I have the choice and incidentially get a detailed view of what is going where, which I like anyway..  

They're not bad in themselves.  In fact as you are fairly new I strongly recomend [https://help.ubuntu.com/](https://help.ubuntu.com/) which gives a good overview.  Choose the appropriate version.  It is peppered with trustworthy apt;urls of things you may want.  You'll see what I mean if you use one quickly followed by another.  You'll also see what happens if you use sudo -k after using one.  It resets to asking the question again. Also I can see why they exist, brilliant the way they are used here, perfect for a newbie, learn the basics at the same time as setting up.  It's elsewhere I have a trust issue with the method.  The danger of adding a poison repository by accident is still remote.  sudo -k after each apt;url may be premature but it's never too early to aquire a good habit.
Based on my limited knowledge of apt:url's I would -- at least at first -- choose to error on the side of caution, so your suggestion to start early to acquire a good habit is good advice and advice that I have applied to my entire life as much as possible (most definitely as it applied to my career anyhow) and where applicable.
That said, I wanted to address your comment on the use of sudo -k when using apt:url's.
I am somewhat familiar with sudo -k. Meaning,  I have read a little about it and I don't think it's paranoid at all especially if you are a new Linux user trying to become familiar with apt:url's and non-mainstream repositories.  I see it as just being responsibly cautious.
According to the AptURL Documentation, (and I just skimmed the document) with Firefox 3.x, apturl works by default with Firefox and Epiphany if they are normally installed from the repositories.
If I discover that apturl is active in my version of Firefox, is there any disadvantage to disabling it?  Because I don't use my browser to install anything.
I always either use the Terminal or, the Ubuntu Software Center/Synaptic Package Manager.
If disabling apturl in the browser will remove any potential risk then it makes sense to me to do it.  Especially if I don't use it for anything.
i apologise if this post appears disjointed...I am reading through a mountain of information regarding this thread and my mind is numb.:confused:
Your comments on this are appreciated.

---

### Post by houseworkshy on 2012-08-02
I asked elsewhere about removing it and Mrs Daisy, who clearly knows more than I do, thought it should be ok to do so. I'm not on the Ubuntu side in this session so will try it out in the next. I don't see how it should damage browser funtionality, other than making apt;url links not function. I don't recomend that you do the same just yet, the ones in the help I linked to are safe and very handy indeed if you wish to go through that guide/tutorial. In an hour or so you could have a brief overview of the whole system and, if wished, have done some setting up too.

The man pages are extremly useful "man man" in the terminal for details on how to use them. The basics are just type "man" in front of whatever command you are interested in which takes you to it's manual page, then type "q" to return to the terminal. One can have several terminals open at the same time, and copy and paste between them. I often have one open for the manual page with another for doing things in. It's worth getting familliar with them as in some offline situation they are still there. Probably the safest things to play with first are the diagnostic but don't do anything commands, "ls", "grep", "locate", "find", "apropos", and so on. There is a standard format so getting to know it whilst it doesn't matter helps for times when it might.

That said command line is a little deep end for some, one can get by almost never using it at all, no more than a windows user using cmos or in the old days dos. So it may not be the best place to start learning.
 
This is a well written and free pdf [http://ubuntu-manual.org/](http://ubuntu-manual.org/) and definately worth a place on the drive. Working through that would put flesh on the bones you'd get from the help section.  If you were to go through those, in a day or two you would have a good overall understanding of your system. 

Linux is logical.  I found that in a few weeks I felt I knew more about what was running on my pc then I ever had before, and that was after decades starting with the spectrum, all the dos's and windows versions up to Vista.   Which I dumped in favour of Ubuntu,  when it wouldn't let me open my own writing,  on my own paid for machine, in the operating system which I'd also paid for just because I wasn't online (I'd moved and hadn't got a landline in yet).  Grrrr  made the phonecall to microsoft only once.  So when it was time for another the 7.04 disc had arrived and instead of using windows while I learned linux, I used linux and formated the other drive for another linux.  A few months later I was back online but totally won over by linux.

Don't let yourself get blinded with the advanced stuff you don't need yet.  I strongly recomend getting the over view first.  It really will take only a few hours to jump from novice to know your way around pretty well.  Getting that overview first is also important when it comes to the expert level things, one needs that overall context first in order to fully understand them.  
There are sticky threads with links to good command line resources here
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)  
but I'd get the basics of setting it up as you like, maybe installing a few programs you'd like or need from the default repositories, get the firewall going, etc and doing all the daily tasks first.

---

### Post by patriot56 on 2012-08-02
> **houseworkshy said:**
> I asked elsewhere about removing it and Mrs Daisy, who clearly knows more than I do, thought it should be ok to do so. I'm not on the Ubuntu side in this session so will try it out in the next. I don't see how it should damage browser funtionality, other than making apt;url links not function. I don't recomend that you do the same just yet, the ones in the help I linked to are safe and very handy indeed if you wish to go through that guide/tutorial. In an hour or so you could have a brief overview of the whole system and, if wished, have done some setting up too.

The man pages are extremly useful "man man" in the terminal for details on how to use them. The basics are just type "man" in front of whatever command you are interested in which takes you to it's manual page, then type "q" to return to the terminal. One can have several terminals open at the same time, and copy and paste between them. I often have one open for the manual page with another for doing things in. It's worth getting familliar with them as in some offline situation they are still there. Probably the safest things to play with first are the diagnostic but don't do anything commands, "ls", "grep", "locate", "find", "apropos", and so on. There is a standard format so getting to know it whilst it doesn't matter helps for times when it might.

That said command line is a little deep end for some, one can get by almost never using it at all, no more than a windows user using cmos or in the old days dos. So it may not be the best place to start learning.
 
This is a well written and free pdf [http://ubuntu-manual.org/](http://ubuntu-manual.org/) and definately worth a place on the drive. Working through that would put flesh on the bones you'd get from the help section.  If you were to go through those, in a day or two you would have a good overall understanding of your system. 

Linux is logical.  I found that in a few weeks I felt I knew more about what was running on my pc then I ever had before, and that was after decades starting with the spectrum, all the dos's and windows versions up to Vista.   Which I dumped in favour of Ubuntu,  when it wouldn't let me open my own writing,  on my own paid for machine, in the operating system which I'd also paid for just because I wasn't online (I'd moved and hadn't got a landline in yet).  Grrrr  made the phonecall to microsoft only once.  So when it was time for another the 7.04 disc had arrived and instead of using windows while I learned linux, I used linux and formated the other drive for another linux.  A few months later I was back online but totally won over by linux.

Don't let yourself get blinded with the advanced stuff you don't need yet.  I strongly recomend getting the over view first.  It really will take only a few hours to jump from novice to know your way around pretty well.  Getting that overview first is also important when it comes to the expert level things, one needs that overall context first in order to fully understand them.  
There are sticky threads with links to good command line resources here
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)  
but I'd get the basics of setting it up as you like, maybe installing a few programs you'd like or need from the default repositories, get the firewall going, etc and doing all the daily tasks first.
Once again my friend I applaud you for your assistance.  I have downloaded the document that you mentioned and have bookmarked the site that references the Command Line Resources.  I have been looking for a reference to the CLI and now it looks like I finally have a good one.
I used to work for an ISP and one of the people in the office was a devout Unix guru, (in his case, FreeBSD) and I was trying to learn it but circumstances prevented me from continuing. I remember him saying that if I would learn the CLI first, then learning the GUI would come without effort.  About a year later, and in a business of my own, I found myself wanting to try FreeBSD again.  I downloaded and installed the OS but ended up completely frustrated without his help.  That was 12 years ago. :icon_frown:
So I went back to the only thing I knew, Windows.  Now I don't care how long it takes, how many times I have to install it, or what I have to do to be successful, I will learn Linux because I will NEVER install another MS product on my computer again!!

Thank you again for your help, you've been awesome and your help has been very appreciated. 
It looks like I have some studying to do now and hopefully I can even learn something.:lolflag:
With the greatest admiration and respect,

- Joe -

P.S. I will leave the browser as it is for now and maybe address that subject after I have read some of the information that you've provided.

---

### Post by 1clue on 2012-08-02
> **patriot56 said:**
> ...I'm not as naive as your post would indicate....


Sorry if I overreacted.  This is one of my pet peeves.  This and every other Linux forum is full of threads where somebody naively insists that Linux is impervious to any sort of virus, and then assumes that means that Linux is impervious to all forms of malware.

I'm speaking from experience when I say that Linux can be hacked.  I've had several of my systems owned over the years, and all but the first were behind the best security I knew how to build at the time. 

When you look at system security, you can't just focus on one thing.  Windows is especially vulnerable to certain forms of attack while being pretty safe from others.  It just so happens that many of the forms of attack which are successful in attacking Windows are the sort of thing Linux defends against easily, but there are a lot of techniques and the windows-linux interaction is a tiny subset.

On the other hand, in this thread we're talking about a repository for debian-based Linux distributions, which is full of software that people will deliberately install as root.  The black-hat hacker is going to KNOW what your operating system is, and doesn't even need to worry about what sort of security you have because you're installing the package as root, deliberately.

In this case, black hats don't have to worry about what sort of intrusion works for Linux because you as the owner of the system are deliberately bypassing all security.  They can focus on "what can sort of application to I want to write?"  They need to spend a small amount of time bundling it in with some sort of legitimate software so people will want to install it.

As was mentioned earlier, before you add one of these repositories type in the full url into google, look for complaints.  Then type in a short name for the domain, and do it again.  If it has a human-readable name other than the domain, type that in too.

Another thing you can do is look at security advisories as Ms Daisy's wiki page suggests.

The best defense is education and an active skepticism of all things unknown combined with a curiosity to explore.  That can be applied to life in general IMO.

---

### Post by patriot56 on 2012-08-02
> **1clue said:**
> Sorry if I overreacted.  This is one of my pet peeves.  This and every other Linux forum is full of threads where somebody naively insists that Linux is impervious to any sort of virus, and then assumes that means that Linux is impervious to all forms of malware.
Please don't feel like you have to apologise.  I agree with you, especially *now* after reading through some of the information that has been provided. 
I came into Linux with a false impression, unfortunately I allowed myself to be influenced by others instead of researching it myself.  Believe me, that's not typical for me. 
I am retired from Law Enforcement and in my career it could be lethal to make a move without looking at all the options first.  I too have my pet peeves and I am just as passionate about them.  *Especially when it comes to security*. 
As you might have already guessed, I am suspicious about everything and cautious almost to the point of paranoid. (It was the job that made me that way, not the training).
I am interested in learning about "ethical hacking" but as I understand it, this requires an element of questionable ethics itself.  (Learning to do the same thing the unethical hackers do)
Thank you for taking the time to post your reply and explain your position on this matter.
As I said, I don't feel like you need to apologise. You are simply expressing your feelings about a subject you obviously care a great deal about.  And my guess is, a subject you *know* a great deal about. 

If you don't mind me asking (I know it is somewhat off the subject but) what do you know about FreeBSD? And is it the secure platform that I have heard about?
I am only slightly familiar with it and even that familiarity goes all the way back to 1996.
As I recall, I don't think FreeBSD even had a GUI back then, and if they did I don't remember it.

As always your thoughts are much appreciated.
Thanks 1clue

Respectfully,

 - Joe -

---

### Post by cariboo on 2012-08-02
One thing that everyone in this thread either doesn't know, or seems to have forgotten, is that if there is a problem with a ppa, repository, or even a .deb package, the community of linux distribution users will let everyone know, in no uncertain terms.

There was an incident several years back, where someone had uploaded a malicious package to gnome-look.org, within minutes of a forum community member downloading the package, there was a thread that went on for several pages detailing the problem with the package, and even naming the author. Needless to say the package was removed very quickly, and no one has seem or heard from the author since.

Personal awareness is always good, but don't forget there is also a community that is on the look out for the types of problems the op mentioned. If any distribution was known to have malicious packages in their repositories the fact would be published immediately, and they would either rectify the problem quickly, or they wouldn't continue to be distributed, as no one would it.

---

### Post by patriot56 on 2012-08-02
> **cariboo907 said:**
> One thing that everyone in this thread either doesn't know, or seems to have forgotten, is that if there is a problem with a ppa, repository, or even a .deb package, the community of linux distribution users will let everyone know, in no uncertain terms.....
Personal awareness is always good, but don't forget there is also a  community that is on the look out for the types of problems the op  mentioned. If any distribution was known to have malicious packages in  their repositories the fact would be published immediately, and they  would either rectify the problem quickly, or they wouldn't continue to  be distributed, as no one would it.

cariboo907....
As the OP to this thread I feel the need to clarify something.
In my original post I was looking for information that would provide a new Linux user with the tools to avoid being lured into installing an infected package through a repository that by all appearances looks innocuous.
I cannot offer an example however, I think I *can *offer an explanation of what I'm talking about and please try to read past my ignorance;
 (*though I realise this explanation is a poor one, as it does not offer the malicious source that I am referring to, it does demonstrate my confusion about what is safe and what is not*).

 This post started as a result of a search I did to find an answer to a problem I was having with VLC (VideoLAN media player). *I don't mean to be cryptic, I just don't think it is necessary to go into details about the problem here.* My search lead me to a utility/application called "Caffeine".  But to install it I was required to add the **ppa:caffeine-developers/ppa **to my Software Sources, (something that I am reluctant to do).  On the developers web page I saw this;
**Adding this PPA to your system**

                            You can update your system with **[COLOR=Red]*unsupported* [/COLOR]**[COLOR=Black]packages[/COLOR] from           this **[COLOR=Red]*untrusted* [/COLOR]**[COLOR=Red][COLOR=Black]PPA[/COLOR][/COLOR] by adding **ppa:caffeine-developers/ppa**           to your system's Software Sources. 
[I]That was what prompted this discussion.

[/I]  I understand *now* that this is benign and doesn't pose a threat (in the immediate sense).  But try to see how it appears for a new Linux user, especially to one coming over from Windows where the threat of infection lurks around the next click on a website, or the next email opened, or by no action of the user at all for that matter. The words unsupported and un-trusted immediately raises suspicion, or am I being overly paranoid?

I have nothing but the utmost respect and admiration for you and the rest of the Administrators of this Forum and for the knowledgeable volunteers that offer their help and experience.  It is a vast treasure of priceless knowledge.  IMHO.
The same respect and admiration goes for the entire Canonical team, the maintainers of the repositories, and the host of worldwide contributors to the Ubuntu product that makes it what it is.  Incredible! :KS
It is because of this level of support that I am so comfortable with the Ubuntu OS.  With so many eyes on the code I can't imagine how difficult it would be to get malicious code into the development chain?

One last thing before I mark this thread SOLVED, I think it is worth mentioning that earlier in the thread **vexorian** made, as far as I am concerned, a very valid point here is his response to my question:                                  [I]"From a security stand point, white  lists are better than black lists. You should instead ask for a list of  reliable repositories".[[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12145033#post12145033")
[/I]I have concluded that my question about a source for a list of un-trusted repositories/sources is not possible and therefore it makes little sense to leave this thread open.
I simply didn't understand how Linux uses repositories, how the repositories work or how easy it is to add a repositories to a sources.list.  I have a better understanding of it now (a little better) and I guess the old adage is true...."the best defence is a good offence".   
[I]
[COLOR=DarkGreen][I]In a bank, a teller never needs to study the counterfeit to be able to recognise it, because they are so familiar with the real thing that when a counterfeit is presented, they recognise it immediately.
I wish this could be said of computer resources as well.
[/I][/COLOR]
With all due respect [/I]cariboo907[I], thank you for addressing this thread and for bringing into focus why we are able to trust the Canonical Repositories and their partners.

- Joe -
[/I]

---

### Post by patriot56 on 2012-08-02
> **mikewhatever said:**
> I am having difficulties imagining, what exactly do you want to learn about Linux that needs adding repositories?
mikewhatever....
I apologise that I haven't responded to your question before this.
I simply meant to say that I am trying to learn as much as I can about Linux and, in fact, adding repositories has little to do with that education other than security.
I should have phrased that question better.  (I guess I do that a lot). :(sorry!
I was just looking for a way to prevent a computer meltdown. Understand, I came from Windows and while I understand the only secure computer is the one that is never powered up or given internet access, I still believe that Unix/Linux is a lot more secure "out of the box" and I am just trying to understand it.:confused:
 And this forum has been a valuable resource to that end.

So, again, accept my apology for not responding sooner.

Sincerely,

- Joe -

---

### Post by houseworkshy on 2012-08-03
You haven't come across as abrasive or accusative, on the contrary you've been courteous throughout, no worries.  
I like the idea of a white list of unofficial repositories too. Something like that would benefit all distributions.  White lists are definitely better than black because they are finite.  It would involve far more work than maintaining the repositories of any given distro, as there are stacks of them.  Sadly it would involve a team so large the idea is probably impractical.  However the official repositories of any given distro are that distro's white list anyway.  For the majority of users all the programs that they are likely to need can be found in it.

A blacklist is less work as it only takes a few bad things to tag it as bad whereas to be sure that it's good means checking every scrap of it.  So some web page ( it may exist already ) compiling bad reports is a viable idea.  But perhaps that would be second best anyway, it will never update as fast as hundreds of forums do.  The community do produce a sort of unofficial blacklist anyway, simply because if someone has a problem it gets mentioned.  If one is thinking of adding an unofficial repository searching for it's name will pull reports of any gremlins hiding in it out.  Searching forums is better for another reason too, some bit of code may be fine really but a novice has used it wrongly or it's not compatable with hardware etc etc.  On a forum, usually, an expert will have guided the mistaken out of their error or suggested a fix or mentioned that programA simply won't run with with hardwareB.  Searching can therefore be compared to consulting a blacklist first.  If people exercise caution and research before adding,  only the first few can be taken by surprise.  

So the official repositories are a white list and research pulls out the equivalent of blacklists for unofficial ones. Not something one can simply install to check unofficial repositories, true, but add research to the mix and it does the job.

---

### Post by vexorian on 2012-08-03
> **cariboo907 said:**
> One thing that everyone in this thread either doesn't know, or seems to have forgotten, is that if there is a problem with a ppa, repository, or even a .deb package, the community of linux distribution users will let everyone know, in no uncertain terms.

There was an incident several years back, where someone had uploaded a malicious package to gnome-look.org, within minutes of a forum community member downloading the package, there was a thread that went on for several pages detailing the problem with the package, and even naming the author. Needless to say the package was removed very quickly, and no one has seem or heard from the author since.

Personal awareness is always good, but don't forget there is also a community that is on the look out for the types of problems the op mentioned. If any distribution was known to have malicious packages in their repositories the fact would be published immediately, and they would either rectify the problem quickly, or they wouldn't continue to be distributed, as no one would it.
From a statistical perspective, that's right, there would be less users affected by an evil ppa or a ppa who gets taken by malicious hackers because we would find out soon and warn most users about it.

But it would still suck to be one of the guys who got affected by it. I think it is good to rely on the openness and enjoy the improved security thanks to the transparency. But it is also not a bad idea to be careful about what ppas you add. Specially if Ubuntu becomes bigger, this will need us to be careful. For example, Android is already pretty big, and there are already malicious alternate app repositories for it.

Enabling a PPA requires you to trust the source. And I think this is not something we highlight a lot. There are always tons of articles that mention "add this ppa" as if it was something that users are supposed to do without a question. But I'd like disclaimers there to remind users that it is not so simple. When you add a PPA, you are giving control of your installer (and thus root control) to a third party server. And you not only have to trust the good intentions of this third party server, but also that it is good at not getting hacked and that it is good at not having bugs that could render *at least* your package management ruined.

I think the default should be to wait for the community to validate a ppa that you find. As opposed to wait for the community to invalidate it. Because *at this moment*, there are no malicious ppas that we know of. But what if, maybe even tomorrow a malicious one appears? Black lists have proven not to be effective (e.g: Antivirus). White lists are turning out to be better (e.g: official app stores).

---

### Post by tubbygweilo on 2012-08-03
> I think the default should be to wait for the community to validate a ppa that you find. As opposed to wait for the community to invalidate it. Because at this moment, there are no malicious ppas that we know of. But what if, maybe even tomorrow a malicious one appears? Black lists have proven not to be effective (e.g: Antivirus). White lists are turning out to be better (e.g: official app stores).

Good, sound advice and I would always spend a little time at a search engine attempting to find something wrong.

---

### Post by cariboo on 2012-08-03
Setting up a ppa is fairly easy, all you have to do is sign the Ubuntu Code of Conduct, but that also leads to complications, as you have to have a valid email address and create opengpg key and confirm it, before being able to do anything on Launchpad. This leaves big footprints all over the internet, and I'm sure that if someone wants to create a malicious package and add it to a ppa, the last thing they want to be is traceable.

Here is an example of what I was talking about in my previous post

[http://ubuntuforums.org/showthread.php?t=1349801](http://ubuntuforums.org/showthread.php?t=1349801)

This incident was reported on all the major news sites.

---

### Post by 1clue on 2012-08-05
> **patriot56 said:**
> Please don't feel like you have to apologise.  I agree with you, especially *now* after reading through some of the information that has been provided. 
I came into Linux with a false impression, unfortunately I allowed myself to be influenced by others instead of researching it myself.  Believe me, that's not typical for me. 


My mission was accomplished.  Getting people to read documentation is my main goal.

> 
I am retired from Law Enforcement...
I am interested in learning about "ethical hacking" but as I understand it, this requires an element of questionable ethics itself.  (Learning to do the same thing the unethical hackers do)


OK having moved about a bit in the USA, I grew up in a place where law enforcement pretty much was guaranteed to be the good guys, but I hope you don't mind my comment that since then there have been times I've had to wonder.  Especially since I lived in Chicago.  I'm going to give you the benefit of the doubt with respect to this discussion, mostly because what I'm saying is common sense anyway and because I'd like to think only a few of the apples are bad.

Regarding ethical hacking, it goes along the same lines as ethical anything else.  What is your intent?  Are you following the laws as they exist for your locality and in the case of the Internet, any locality involved in your project?  Are you working in conjunction with an official agency which has some authority over your activities?  Do you have oversight by a respectable, independent third party who has no conflict of interest to act as a sanity check?

Don't tell me the answers to that, I'm just a guy on a forum.

Frankly I doubt that you'll find a person who claims to be an expert who really is, and also never find the real experts who will claim more than to "know a few things about networking."  As for my expertise I contributed to the discussion that Ms Daisy and others used to create the wiki, but I learned a lot too.  I consider myself able to follow the discussion and to use common sense, but I'm not in the league of a real professional security consultant.  I'm more the guy to slap the newbies silly and send them to the wiki page  :)

Truth is, you will spend quite some time learning about networking and security before you have to worry about the ethics of continuing.  I stopped playing way before that point.

> 
If you don't mind me asking (I know it is somewhat off the subject but) what do you know about FreeBSD? And is it the secure platform that I have heard about?
I am only slightly familiar with it and even that familiarity goes all the way back to 1996.
As I recall, I don't think FreeBSD even had a GUI back then, and if they did I don't remember it.

As always your thoughts are much appreciated.
Thanks 1clue

Respectfully,

 - Joe -

OK, about FreeBSD.

***Edit:***  Pardon the extreme brevity and possible inaccuracy of some of this.  This is all well-known history and you can google it if you want.  I'm saying enough to make my point, no more.

BSD is where the Internet was born.  DARPA used (mostly) that operating system when they invented the concept of networks of networks which turned into the Internet.  For years BSD had the most stable and most "compliant" network stack of anyone, mostly because it started out as a very stable OS, and that was where the smart guys were inventing it, and by that fact it was the "reference" network.  Everyone else was reading RFC's (requests for comment) and trying to implement their variant of that functionality, usually not very closely.

Now since then FreeBSD happened (split off from BSD), and if you look at history nearly every mainstream network stack is using FreeBSD code in a significant part or in its entirety.  Mac OS is a commercial BSD derivative.  Windows adopted the FreeBSD stack a few years ago.  Linux is heavily influenced by BSD with regards to networking.

In short, over and over it seems that operating system designers have looked at the cost and/or effort of rewriting or modifying their own networking stack to be better, or adopting FreeBSD's stack and usually come up on the side of the latter unless their networking was pretty good to begin with.

The FreeBSD license allows commercial use of the BSD code with proper attribution, but there is the complication of the "private" half of the license, which IMO I can't see how people could be bound by a contract they're not allowed to read.  But whatever.

Getting back to the point, BSD *can be* stable and secure.  So can a whole lot of other operating systems right now.  Frankly everything has changed since a few years ago, both in the BSD realm and in every other as well.  But no matter how secure your core OS is, if you stick something stupid (like a chat server) on it there's no way you're gonna claim security.

I'm not so much a FreeBSD guy because of two things:  It's BSD and I cut my teeth on System V, and because of that funky private half of the license that I'm not allowed to read.

However the security and capability of the operating system heavily depends on what you're putting on the box, and how your kernel is compiled.  I stopped messing with FreeBSD shortly after I discovered it has /etc/init instead of /etc/inittab, so I've never compiled kernels in BSD.  Linux, you can have an endless number of networking options compiled in and a good many of the combinations are not stable or entirely functional.

I hate to tell you this, but if you're looking at ethical hacking, you have to do it the hard way.  You're gonna have to start reading, and while you read you'll need a handy Linux box to experiment with.  And probably a couple other guys who are on the same trail, who are willing to be experimented on in return for your willingness to be experimented on by them.  First you're just gonna have to be a Linux nerd and figure out how to use things.  You need a certain amount of familiarity with the computing culture to even understand what these guys are talking about.

Back when I learned networking the Internet was still pretty much limited to schools and government, and modems (host to host) were still much more prevalent than real networking.  Computers were PC's with Windows 3.1, Commodore Amigas, Atari ST's and beige one-piece Macs.  In order to have my system at risk of being hacked, my phone had to be busy and only the rich guys had 1200 baud.  I used an acoustic coupler, which was a sort of cradle with rubber tubes on it that you stuck your handset into.  300 baud tops, usually less.  300 baud is 30 characters per second, and I can type faster than that.

Back then, "being hacked" had a lot of consent involved, if you didn't want to be a victim you just picked up the phone and talked into it.  Or disconnected the phone line.  You had plenty of time because it was somebody typing, there was no software for hacking.  Also the consequences were that you might have to reboot.

These days, you'll probably need a VPN between your network and your study buddies, because I think most major ISPs probably monitor the sort of activity you'll likely be trying.  It ain't the wild wild west anymore and the network admins are paying attention.

Good luck and have fun.

---

### Post by patriot56 on 2012-08-06
> **1clue said:**
> .....

OK having moved about a bit in the USA, I grew up in a place where law enforcement pretty much was guaranteed to be the good guys, but I hope you don't mind my comment that since then there have been times I've had to wonder.  Especially since I lived in Chicago.  I'm going to give you the benefit of the doubt with respect to this discussion, mostly because what I'm saying is common sense anyway and because I'd like to think only a few of the apples are bad.

.........Don't tell me the answers to that, I'm just a guy on a forum.


 I had a chance to apply to CPD but decided to stay on the west coast, from what I've heard, it was a wise decision.  Who knows?  But I do agree that there are some that shouldn't wear the badge. 
  
On the topic of "ethical hacking" my only real interest in it is the obvious education that goes with simply knowing how an"unethical hacker" accomplishes what they do. 
I believe that the more information you have the better you can respond to a given situation appropriately.  

Your comments on networking line up pretty closely with what I suspected was going to be necessary to get started. And just learning Linux at this time is going to keep me busy enough.
 

Thank you for your insight on BSD.  I, ahem....think I have a long journey ahead of me just trying to absorb the info. that you and everyone else has already provided and I am glad that I ask.
It's probably a good idea to leave BSD alone for the time being.
I just hope I can get my head around some of the technical jargon addressed in a lot of what I've already read. 
 [COLOR=Blue]*One could make a career of studying acronyms alone.*[/COLOR]
I still have a lot of questions, and I am sure that many of them will be answered in the material that this thread has produced but I don't want to test your patience or the patience of anyone else that may read this thread so, I will go over all of the documents, links and information that everyone has provided and if I still have questions I know where to find the answers.:)

As I said, I think at this point it's a good idea to become well acquainted with Linux before tackling anything else. 
I am looking into areas that quite frankly have intimidated me for a long time.
Networking and Programming for example have always been an area of contention for me.
The text says one thing but my brain interprets it differently.
I've always had a  hard time with networking because it just seemed to be so multifaceted. It has  so many layers that I have a hard time keeping everything in  perspective.

And programming?  Man I don't even know where to start there!  The point is, I may never understand it.

Being a Systems Security Consultant/Professional is my goal but I suspect that's a goal for another day.  And that's ok.
At this point I'll settle for becoming proficient with Linux.
At least now I have a starting place, a lot of good information and enough reading material to make me dizzy for months.

I know I keep saying this but thank you again, I really am grateful for everyone's help throughout this thread and sincerely appreciate the time you and all the others have given to this subject.
I had no idea that this thread would net so much valuable information.
To everyone that has contributed. =D>


Oh, and by the way 1clue,
 My first computer was a Tandy COCO with an external cassette tape drive, an internal 300 baud modem, a 5 1/4" floppy drive and a truck load of desire to learn everything I could about computers.
Of course "the Internet", as you said was pretty much limited to schools and government, however I do remember playing around on the BBS's, (Bulletin Board Systems) downloading and playing shareware games. Huh! Green text on a Black background. Man that was a *long* time ago.  Almost caused a divorce,-- until I got my wife interested in it too,-- then of course we had to get another computer because there wasn't enough room at the keyboard for both of us.:?
  
 
- Cheers -

---

### Post by 1clue on 2012-08-06
> **patriot56 said:**
> ...On the topic of "ethical hacking" my only real interest in it is the obvious education that goes with simply knowing how an"unethical hacker" accomplishes what they do. 
I believe that the more information you have the better you can respond to a given situation appropriately.  

Your comments on networking line up pretty closely with what I suspected was going to be necessary to get started. And just learning Linux at this time is going to keep me busy enough.


That's why I was suggesting a couple friends with similar interests.  You take turns creating a secure "network" and then the other guys try to break into it.  You definitely need more than one or two heads, you need a large enough group that people can learn something, build it and THEN get hacked.  Then you learn to clean up, fix the hole and try again.

Ideally, you have enough people that you don't figure out your opponent's head in a couple weeks.  The problem is that if you're going over a public network you need to hide the things you're doing from the ISP, because there are almost no circumstances when that sort of thing is legal.  The only exceptions I can think of is if you own both endpoints, or if you're hiring somebody to to do a security audit.  I think the idea that you and some other guys take turns trying to bust each other's networks is going to cut it.  It's in your terms of use in some fashion or another, and the lion's share of people who do that sort of thing are not benign.

Haven't done that sort of thing for decades, but I can tell you it was a whole lot of fun back in the days of the acoustic coupler, especially because I could literally watch it happen.  Spent more time doing that than studying for my degree.

> 
Thank you for your insight on BSD.  I, ahem....think I have a long journey ahead of me just trying to absorb the info. that you and everyone else has already provided and I am glad that I ask.
It's probably a good idea to leave BSD alone for the time being.
I just hope I can get my head around some of the technical jargon addressed in a lot of what I've already read. 


BSD is no worse than Linux, it's just I had already learned a lot about Linux when I finally tried FreeBSD.  The UNIX classes in college were all System V, I had simply had no exposure and didn't want to go there.

> 
As I said, I think at this point it's a good idea to become well acquainted with Linux before tackling anything else. 
I am looking into areas that quite frankly have intimidated me for a long time.
Networking and Programming for example have always been an area of contention for me.
The text says one thing but my brain interprets it differently.
I've always had a  hard time with networking because it just seemed to be so multifaceted. It has  so many layers that I have a hard time keeping everything in  perspective.



And programming?  Man I don't even know where to start there!  The point is, I may never understand it.


OK we have our first hiccough.  No coding, no hacking.

Networking, just keep all the layers separate.  Know what each layer does, what it's used for and how the interaction works between them.

The whole key to black-hat hacking is understanding how everything works when you don't follow the rules.  I don't know much but I know that.  I spent enough time getting bizarre, unexpected results when I didn't do it right to know that sometimes it does SOMETHING but not what you were hoping for.  Lots of security compromises come from a buffer overrun or some other thing that would be called a mistake in normal circumstances.

> 
Being a Systems Security Consultant/Professional is my goal but I suspect that's a goal for another day.  And that's ok.
At this point I'll settle for becoming proficient with Linux.
At least now I have a starting place, a lot of good information and enough reading material to make me dizzy for months.


Good.  :)

> 
I know I keep saying this but thank you again, I really am grateful for everyone's help throughout this thread and sincerely appreciate the time you and all the others have given to this subject.
I had no idea that this thread would net so much valuable information.
To everyone that has contributed. =D>


What comes around goes around.  If you read up on the history of Open Source you will find that the basic premise was that of sharing.  You pay for the right to use the software you were given by contributing something back to the system.  Back then it was all programmers so they swapped software, but now it can be documentation or money or helping out on a forum.

> 
Oh, and by the way 1clue,
 My first computer was a Tandy COCO with an external cassette tape drive, an internal 300 baud modem, a 5 1/4" floppy drive and a truck load of desire to learn everything I could about computers.
Of course "the Internet", as you said was pretty much limited to schools and government, however I do remember playing around on the BBS's, (Bulletin Board Systems) downloading and playing shareware games. Huh! Green text on a Black background. Man that was a *long* time ago.  Almost caused a divorce,-- until I got my wife interested in it too,-- then of course we had to get another computer because there wasn't enough room at the keyboard for both of us.:?
  
 
- Cheers -

One of my buddies had a coco in the early days.  A few of us had coding contests with a bunch of systems that all had approximately the same CPU.  I think you had a 6510, I had a 6502 and others had whatever.  Neal finally won by (he claimed) poking some memory location that turned off the memory refresh strobe.  He did that, went into the loop to calculate the result, printed the results and the computer abruptly crashed because, presumably, the only memory actually being refreshed was the loop of code.

I don't know exactly what he did but the evidence supported his claim.  I got interested in something else after that, I couldn't find anything comparable on my Atari 800XL.


Back on topic, If I were doing this now, I would suggest having an external vpn/firewall router from anywhere, just basic home stuff.  That router should be inviolate to your buddies.  Then you expose one box completely through the VPN, and that box is your "firewall."  Then get your workstation which is assumed to be non-expendable and you try to keep running steadily.  Then you have one or more other boxes that you can experiment with, and they don't have to be fancy at all.  Just give them a couple network cards and a decent developer setup and figure on wiping them off and starting with a clean format every so often.

Keep in mind though that when somebody hacks your network they're looking for a weakest link and so you need to pay attention to your whole network.  Those "rules" will still apply to your buddies.  If you got some guys who are doing this with you, the premise is that you VPN to the home router and then hack things from there.  That way it looks like peer-to-peer networking through a VPN which it is, and not like a security threat.

This could all be done with virtual machines at first because it would get you the basic training to set it all up, but after awhile you would want real hardware because the VM won't emulate everything.

Good luck and have fun.

PS.  I'm not dragging this discussion along deliberately, just yacking.

---

### Post by patriot56 on 2012-08-10
**1Clue**.  I could quote each of your posts to my questions and respond in a more articulate manner but I don't think that is necessary at this point.
I really like the ideas that you have presented here and I am looking forward to implementing most (or all) of them.
I believe that your education, training and experience are evident in the field that you are obviously very proficient in and I am thankful that I have had the opportunity to benefit from that background and I really hope to continue to do so in the future.  

Your Idea to set up a network of like minded students in the area of Network Security is a brilliant idea and it is something that I am going to attempt at my earliest convenience.

Your advice has been appreciated far beyond the ability to communicate.
Please accept my sincere appreciation for your advice and I hope to be able to draw on your knowledge in the future.

With sincerest appreciation,

- Joe -

---

