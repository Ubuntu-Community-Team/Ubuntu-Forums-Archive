---
title: "Tennessee Team Contributions"
date: 2009-08-26
forum: Tennessee Team - US
---

### Post by tbuss on 2009-08-26
[deleted]

---

### Post by binarymutant on 2009-08-26
Idea 1. Create "How-To's"
 good stuff, you should link your howtos in the wiki here:
 [https://wiki.ubuntu.com/TennesseeTeam/Reading](https://wiki.ubuntu.com/TennesseeTeam/Reading)

Idea 2. Create video tutorials
  awesome idea, idk how to create screencasts correctly though, the first 
  time I tried it was sooo slow :(

Idea 3. For those with personal sites, advertise *nix Ubuntu FOSS...
  How about a Tennessee Team Ubuntu button?

Great ideas we need more contributions :D

---

### Post by jfenn2199 on 2009-08-28
Actually I have been working on the starting phase (pretty much just brainstorming) of a Non-Profit similar to whats described above if anyone else is interested let me know and we can get the ball rolling a little further (or furthur if there are any fans of the pranksters out there lol).

---

### Post by binarymutant on 2009-08-29
I need screencast ideas, halp!

<EDIT>
Just wanted to let you all know that xvidcap is very lightweight and does screencasts very well
</EDIT>

---

### Post by AliTabuger7 on 2009-09-02
Can I suggest that you upload whatever materials you make (with source) to [http://spreadubuntu.neomenlo.org/](http://spreadubuntu.neomenlo.org/) so others can use it too?

---

### Post by netritious on 2009-09-06
**[FONT=&quot]Free VPS for Ubuntu TN Team[/FONT]**[FONT=&quot]

I would like to contribute a Virtual Private Server to host the new LoCo TN web site and any associated web services. The intention of this contribution is to give the LoCo TN Team a place to work on projects for Ubuntu in the name of the Team and provide more than a free web host might offer. 

**VPS Specs **
2.5 GHz CPU, 256MB RAM, 4GB HDD. Unmetered 16Mbps down/2Mbps Up Commercial Grade Comcast, Ubuntu jeOS (Hardy Server 32-bit) 

**Web Services **
Apache, MySQL, PHP, BIND (DNS), Dovecot/Postfix (POP/IMAP/SMTP), SSH/SFTP 

**Who has access? Who grants access?**[/FONT]
  [FONT=&quot]The LoCo TN Team has a chain of command. Decided by a unanimous vote in the August 2009 Team Meeting on freenode, the LoCo TN Team Trustee, Don Harper (w4ett), is the the team’s ranking officer. The Team Trustee, and/or a LoCo TN team member desiganted by the Team Trustee, would be the point of contact for new user accounts and permissions. Outside of needs for administration would be up to the LoCo TN team, but at the sole descetion of the Team Trustee and/or designated team admin(s) to provide the desired service on their time. [/FONT]
  
  [FONT=&quot]For instance, if an approved LoCo TN team member wanted ssh/sftp access it would be w4ett to approve the team member, and w4ett (or designated team admins) that would grant such access on the server. I voluteer to be an admin, but only if w4ett designates me to do so, and only if the team agrees this is an overall good procedure to secure rights to the server.[/FONT]
  
  [FONT=&quot]Netritious.com has Host and Guest root access on all hosted services. The LoCo TN Team Trustee (w4ett) would have root access to the VPS. Unless the LoCo TN Team or Team Trustee decides otherwise, Netritious.com will have root access for maintenance and emergencies. All other access is at the sole descretion of the Team Trustee or LoCo TN Team member(s) designated as VPS administrator.[/FONT]
  [FONT=&quot] 
**What can the LoCo TN Team expect from the VPS?** [/FONT]
  *[FONT=&quot]Performance[/FONT]*[FONT=&quot]. Since the intention of the contribution is to host a web site for [www.ubuntu-us-tn.com]("http://www.ubuntu-us-tn.com"), and if left at that capacity, the VPS will be /very/ robust.[/FONT]
  
  *[FONT=&quot]Control.[/FONT]*[FONT=&quot] It’s hosted By Us, For Us. As a team we can decide and cater to different projects and the required underlying technologies without having to choose among a handful of decent free web hosts.[/FONT]
  
  *[FONT=&quot]Reliability.[/FONT]*[FONT=&quot] It’s all based on Ubuntu baby! Need I say more?[/FONT]
  
  *[FONT=&quot]Redundancy.[/FONT]*[FONT=&quot] Netritious uses Heartbeat/DRBD clusters to provide redundnacy to VPS services and data.[/FONT]
  
  *[FONT=&quot]Scale.[/FONT]*[FONT=&quot] When Netritious.com grows finanicially so will our VPS platform. We’re a small outfit right now but don’t intend to stay that way long.[/FONT]
  
  **[FONT=&quot]What are the conidtions for this free service?[/FONT]**
  [FONT=&quot]The LoCoTN VPS would be but one of many VPS hosted at Netirtious.com. If the LoCoTN VPS interrupts business in a significant way then it has outgrown what I can provide. 

**What happens if the LoCoTN VPS interrupts normal business for Netritious? **
It really depends on what is causing the problem and on what scale the disruption takes place. I wouldn't blindly shutdown the server unless it was something critical, and if that were the case I would probably shut all the VPS down and run a read-only backup while the problem is investigated. This means the server shouldn't see downtime. If this ever happened I would of course report it in IRC. 

**What can the Loco TN Team host on the server?**
Anything the Team approves to host, but by default DNS,WWW(PHP),MySQL,POP/IMAP/SMTP will be hosted. 

**What about using the server for mirroring Ubuntu repositories and/or ISOs? **
I’ll leave this up to the Team. I closely monitor the cluster so if it gets out of control or degrades the paid VPS customers I’ll bring it to the Trustee’s attention and throttle the bandwidth to/from the VPS. [/FONT]
  
  [FONT=&quot]A better alternative to hosting ISO’s would be to seed existing Ubuntu iso torrents. This would allow us to leverage existing services in the name of the Team without overloading the VPS and the underlying resources. 

**What about hosting video tutorials and other multimedia?**
As with the ISO scenario why not leverage existing free services? For video I would suggest YouTube and just embed a link to the video from the server (usually placed in a web page). This is really up to the Team, but the server won't be 'snappy' with multiple large (>100MB) simultaneous downloads.

**Where is the VPS server now?**
The VPS server will be setup when the Team has decided it's to be used for hosting the ubuntu-us-tn.info web site. As much as I would like to get started right away, currently it is in discussion on the #ubuntu-us-tn channel on Freenode. When the team has reached some consensus to utilize this contribution I'll be glad to set it up at that time. 
 [/FONT]
  **[FONT=&quot]What does Netritious.com gurantee?[/FONT]**[FONT=&quot]
Currently I can’t gurantee anything other than a spot on my cluster, a static IP address, and a VPS with Ubuntu jeOS installed and patched with ssh access given to w4ett. [/FONT]
  
  **[FONT=&quot]What are Netritious.com’s limitations/capacities?[/FONT]**
  [FONT=&quot]The service is currently in an experimental state of development and there are some draw backs. Netritious.com has been live now for six months and already has had a couple of significant outages, both of which lasted for two-four hours. The service is netiher geographically redundant, nor is the power redundant. (Currently there is 30 minutes of backup power in the event of power outage.) Netritious is a small outfit that hopes to grow into a colocated envrioment which is truly redundant, but until that time Netritious.com cannot guarantee data, uptime, access, backups, etc. I have it covered as well as someone can with my budget constraints. Full system backups are currently sporadic and development driven.[/FONT]
  
  [FONT=&quot]I'm open to any questions, suggestions or feedback.[/FONT]

---

### Post by binarymutant on 2009-09-08
[CENTER]**Introduction**
*Hiya*
[/CENTER]
I'm pleased to announce that the Tennessee Team has a website :D
[[COLOR="Blue"]**http://www.ubuntu-us-tn.info**[/COLOR]]("http://www.ubuntu-us-tn.info")
The great [[COLOR="SeaGreen"]Don Harper (w4ett)[/COLOR]]("https://wiki.ubuntu.com/w4ett") has donated money to register this domain and should be swarmed with alcoholic gifts when ever you see him. :D In another thread the great [[COLOR="SeaGreen"]Rich Gray (netritious)[/COLOR]]("https://launchpad.net/~netritious") has offered to donate space to host the website, Seeing all this buzz is so awesome that I've decided to create a repository in the spirit of collaboration. In the Ubuntu fashion the code repository is hosted by Launchpad, found here: 
[[COLOR="Blue"]**https://launchpad.net/www-ubuntu-us-tn**[/COLOR]]("https://launchpad.net/www-ubuntu-us-tn")

[CENTER]**Bazaar Usage**
*Since not everyone uses version control systems as much as I do.*[/CENTER]

This is a quick intro to using Bazaar that should get anyone up and collaborating within minutes. :D

First some short requirements:
Log on to Launchpad and navigate to your profile. Click "Change details" and then click "SSH Keys" and add your [[COLOR="Blue"]**SSH key**[/COLOR]]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") to your Launchpad. If you already have a key it's normally found in *~/.ssh/id_rsa.pub* If you don't already have an SSH key then issue this command in a terminal:
```
ssh-keygen -t rsa -C "Your Name <your-email-address@wherever.com>"
```

Now it's time to install [[COLOR="Blue"]**Bazaar**[/COLOR]]("https://wiki.ubuntu.com/Bzr").
```
sudo apt-get install bzr
```
Once it's installed issue this command so that bzr knows about your Launchpad account:
```
bzr launchpad-login <username>
```
Excellent, it's obviously time to rock. Grab the source code for the website, study it, edit it, make something great, most importantly have fun:
```
bzr branch lp:www-ubuntu-us-tn
```
After doing something to the code commit it. A commit tells others what changed:
```
bzr commit -m "This is my commit message"
```
and then upload it to your branch on Launchpad:
```
bzr push lp:~<username>/www-ubuntu-us-tn/trunk
```
in order keep current with the changing main branch issue this command (always stay current with the main branch please):
```
bzr pull
```

When you want to get the code onto our website go into your Launchpad profile and under the Code tab navigate to your branch of the website. There will be a button that says "Propose for merging into another branch". Follow the instructions from there on and send it out. We'll do a code review together and more than likely merge it into the main branch. 

And that my friends is how Open Source Collaboration works :D
Of course bzr can do more than I can write in a thread, so please check out [[COLOR="Blue"]**https://help.launchpad.net/Code**[/COLOR]]("https://help.launchpad.net/Code") for a deeper understanding.

[CENTER]**We will rock**
*It's about collaboration*
[/CENTER]

Alright now that I've shown how collaboration works, you've probably seen my crappy code. I'm not really a dev (service industry for life) so please be gentle with me and any other collaborators :D  _This is the only definite rule._
I'm going to take the next section to write about why I did what I did and other _proposed_ restrictions.

[CENTER]_[COLOR="Red"]Flamewars start here[/COLOR]_
*Joking*
[/CENTER]

_Directory layout_: I started the original mockup for the site with one goal in mind: easy collaboration. Every section of the site is separated for this reason. Here's how it looks: 
 * *banners/* - anyone can add any number of banners into this directory and in the future we can have a banner script rotate them. This folder should say "drop some files in me".
 * *styles/* - this is for anyone that wants to include their own css themes for the site, hopefully in the future we can have the ability to switch themes. And this folder yells "drop some files in me"
 * *images/* - is for images that aren't banners, this promotes easy access to the team's misc. images and screams "drop some images in me".
 * *scripts/* - is for scripts of any sort, this promotes easy access to the team's scripts and screams "try some stuff in here"
 * *static/* - this folder is for the necessary pages for the team, I created it to keep people away from it pretty much. Pages like join.html and contact.html are necessary for our webpage and should be included on all pages, this folder is for that. These pages, once released, should not be changed often. This folder should say "Keep out"
 * *stuff/* - I didn't create it yet, but there needs to be a folder that's opposite of static/. This folder should be for any unnecessary stuff that shouldn't be on everypage, it should also promote easy additions to the website and should scream "drop a file in me". Lets name this soon to be real folder *stuff/* for now( I'm unsure of what to name it, so please help me out ).

_Scripting Languages_: I like to code and there are more people out there that do too, unfortunately though languages debates = flamewars which is why I want to have Rich Gray (netritious) host the site on his vps. I would like to be able to have any language supported so that we aren't turning down any potential collaborators, this would also keep us away from the flames.

_Merges vs pushes_: so that we don't step on toes please please please use the propose merge button in launchpad. This project is for collaboration only.

_Standards vs Fun_: HTML standards are great but sometimes contributors (like me :D ) don't want weed through references just to put up a page about their kitty. So I'm for fun on any page in *stuff/*. However. in order to keep certain parts of the website readable in all browsers though I propose we find a standard and apply it to everything under *static/* (I don't care which standard, just trying to open the doors for discussion).

_Content_: Everything should be open sourced, public domain, free to share, etc. etc. etc. I would follow the DSFG if in doubt or maybe OSI's thing (idk what it's called)

_Future Rules and Restrictions_ I'm open to any ideas but would like to say that this site should be about collaboration within the team and getting people involved in a fun project. Future rules and restrictions should not limit this fun, instead they should expand it.

> [COLOR="Red"]**Comments, suggestions, improvements are needed**[/COLOR]


---

### Post by binarymutant on 2009-09-08
> **netritious said:**
> **[FONT=&quot]Free VPS for Ubuntu TN Team[/FONT]**[FONT=&quot]

I would like to contribute a Virtual Private Server to host the new LoCo TN web site and any associated web services. The intention of this contribution is to give the LoCo TN Team a place to work on projects for Ubuntu in the name of the Team and provide more than a free web host might offer. 

Lets move further discussion over here [http://ubuntuforums.org/showthread.php?t=1260940]("http://ubuntuforums.org/showthread.php?t=1260940")

---

### Post by binarymutant on 2009-09-08
to help with brainstorming here's a definitive list of other LoCo sites out there: [[COLOR="Blue"]https://wiki.ubuntu.com/LoCoTeamList[/COLOR]]("https://wiki.ubuntu.com/LoCoTeamList")

---

### Post by mac9416 on 2009-09-08
I thought it might be useful to post links to a few Ubuntu LoCo sites. Maybe we can take some ideas from them.
[LIST]
[*]Chicago: 
[http://chi.ubuntu-us.org/](http://chi.ubuntu-us.org/)

[*]Washington D.C.: 
[http://dc.ubuntu-us.org/](http://dc.ubuntu-us.org/)

[*]Arizona - some great ideas for sidebar content here: 
[http://www.azloco.com/](http://www.azloco.com/)

[*]Colorado: 
[http://coloco.ubuntu-rocks.org/](http://coloco.ubuntu-rocks.org/)

[*]Florida: 
[http://www.ubuntu-fl.org/](http://www.ubuntu-fl.org/)

[*]Georgia: 
[http://ubuntu-georgia.org/](http://ubuntu-georgia.org/)

[*]Maryland: 
[http://ubuntu-maryland.org/](http://ubuntu-maryland.org/)

[*]Massachusetts: 
[http://www.ubuntu-massachusetts.com/](http://www.ubuntu-massachusetts.com/)

[*]Minnesota: 
[http://ubuntu-minnesota.org/](http://ubuntu-minnesota.org/)

[*]New Jersey: 
[http://nj.ubuntu-us.org/](http://nj.ubuntu-us.org/)

[*]New York: 
[http://main.newyork-ubuntu.com/](http://main.newyork-ubuntu.com/)

[*]Ohio: 
[http://ohio.ubuntu-us.org/](http://ohio.ubuntu-us.org/)

[*]Pennsylvania: 
[http://ubuntupennsylvania.org/](http://ubuntupennsylvania.org/)

[*]Utah: 
[http://utah.ubuntu-us.org/](http://utah.ubuntu-us.org/)
[/LIST]

If you know of any others, you can post them or PM me and I'll add them to the list.

I've noticed that on many LoCo sites, they have links to System76. Here are the details of what looks almost like a LUG/LoCo "affiliate program" for System76: [http://system76.com/article_info.php?articles_id=26](http://system76.com/article_info.php?articles_id=26)

---

### Post by binarymutant on 2009-09-08
woops, I forgot to tell everyone that in order to keep your branch updated with the changes happening in the main branch you need to issue this command:
```
bzr pull
``` :D

---

### Post by jhaitas on 2009-09-08
Please note that the "static" directory has been renamed to "inc"

---

### Post by jfenn2199 on 2009-09-09
As far as content goes I feel that this website needs to be our face to the world.  Ubuntu is billed as Linux for Human Beings so we need to cater any said site to their means.  For Example:

Lets say we're out at a street fair or any gathering and find an opertunity to promote Ubuntu.  We give them the address to the wiki and there's digging and scrolling etc.  Now this is great for us because most of us have been here through this pages evolution we have gotten used to using it (though not the whiteboard as this really should be going there).

Now say we directed that person to [www.ubuntu-us-tn.info](www.ubuntu-us-tn.info), they have the kind of web experience they are most familiar with there's not too much information on the front page, just enough to tell who we are, what we do, and how we're doing it (as stated on IRC last night the text to the main page can be changed I have no objections I just needed an idea of what it would look like and how the style interacted with everything).  Then our newbie to the world of linux and possible of open-source (well knowledgeable exposure anyway), can decide that yes these values match mine I want to join and click on the join link and follow through the steps.  

As far as the contacts page go I think we should include an email address for w4ett, binarymutant, pace_t_zulu, and ericG as they are the Trustee and regional PoC's respectively.  

From there on the side boxes we can expand I personally like the idea of having the events on the leftside where they can be expanded but this is a project of collaboration so what does everyone else think of that positioning.  As far as the right box goes it's kind of bland yes we need a spot to allow easy access to what we've done, but we also need things that link out from the main page to the other sections of our team.

Team Contributions would be a good place for us to add sites of our team members but we need official links from the main page to the wiki and forums etc so that way as our new members who very well may be the human beings the marketing slogan talks about become more familiar with how things are done we increase the activity of the team members.

---

### Post by binarymutant on 2009-09-09
> **jfenn2199 said:**
> 
(though not the whiteboard as this really should be going there).

I'm against the "whiteboard" being used for discussion around the team. Wiki syntax is hard to learn, I'd actually prefer if we used either the forum or the mailing list for real discussion. This way people not familiar with wiki's can have some input too. In fact next meeting I'm going to raise the question of removing the whiteboard from the wiki altogether.

> just enough to tell who we are, what we do, and how we're doing it 
I'm down for this, +1
I'd also like to add that this be all in inc/ so that other stuff won't affect this vital info.

> As far as the contacts page go I think we should include an email address for w4ett, binarymutant, pace_t_zulu, and ericG as they are the Trustee and regional PoC's respectively.
+1, we could even remove Contacts too, if wanted  

> From there on the side boxes we can expand I personally like the idea of having the events on the leftside 
+1, I'm down for this

> As far as the right box goes it's kind of bland yes we need a spot to allow easy access to what we've done, but we also need things that link out from the main page to the other sections of our team.
Do you propose that we have the right box for links to info in the wiki or lumping both contributions and wiki info together in the right box? I like the idea of lumping it all together.

> Team Contributions would be a good place for us to add sites of our team members
Are you proposing that Team Contributions be on the top menu? or included on the right box?

I would like to keep both boxes ( or columns, whichever) on the site so that different css styles can hide or show them. It would be a nice to gestures to future themers.

---

### Post by jfenn2199 on 2009-09-09
> **binarymutant said:**
> I'm against the "whiteboard" being used for discussion around the team. Wiki syntax is hard to learn, I'd actually prefer if we used either the forum or the mailing list for real discussion. This way people not familiar with wiki's can have some input too. In fact next meeting I'm going to raise the question of removing the whiteboard from the wiki altogether.

I'm down for it I guess the roadmap would have been a better reference and not for the discussion just the actual laid out plan

> +1, we could even remove Contacts too, if wanted
I'm in favor of keeping the contacts to have a quick point of reference for any newbies to get intouch with the area PoC, I know on campaigns I've worked on it's been a big help instead of digging deep then contacting one person who contacts another who contacts the PoC who then contacts you back.


> Do you propose that we have the right box for links to info in the wiki or lumping both contributions and wiki info together in the right box? I like the idea of lumping it all together.

I was thinking having it linked to info on the wiki to help cut down on redundancies but lumping it together works too


> Are you proposing that Team Contributions be on the top menu? or included on the right box?

Kinda like I set up now having Team contributions in the right box and underneath Projects, putting like binarymutant.com.  Something along those lines

> I would like to keep both boxes ( or columns, whichever) on the site so that different css styles can hide or show them. It would be a nice to gestures to future themers.

Definitely I like keeping the boxes it makes for quick reference points for our visitors

---

### Post by binarymutant on 2009-09-09
Another issue that is probably going to come up is: Code Reviews
How many reviewers should approve code changes before accept into main? If it's just me reviewing code changes then I'm just going to start pushing into main without asking :D
[CENTER]*and if you haven't figured it out yet, my webdev skills suck lol*[/CENTER]
The issue of maintainer-ship has also come up: I'm all for replacing myself with the Tennessee.Team on who maintains the info on LP, but I just have one issue, any member of Tennesee.Team can potentially hijack the project away from us and potentially do other mean stuff. Pace_t_zulu has a good idea about creating a maintainer team for the website. I'd don't mind being the sole maintainer (obviously), this cuts down on having one small team being divided into even smaller teams. <edit> Do I even need to worry about this ^? </edit>

---

### Post by binarymutant on 2009-09-09
Hey what happened to this thread??

---

### Post by w4ett on 2009-09-10
Threads merged

---

### Post by mac9416 on 2009-09-11
binarymutant and I have been talking about the advantages/disadvantages of using a content management system (such as Wordpress) versus hand-coding the website. Here are the emails that have gone back-and-forth between us:

Me:
> ...One question: why not do the entire site with WP, not just the blog? I have made WP sites that don't even have a blog, it's that much easier than hand-coding. It's a little bit of a learning curve, but it makes it much easier to post quick updates, add/edit pages in a hurry, etc. Of course, whatever the team says, I'm cool with. I'm just thinking Wordpress would be the better way to go, from what I know.

binarymutant:
> Personally, I think hand coding gives it more of a team project feeling. I'm sure other people prefer a finished project over a never-ending one though, so I was kind of waiting for someone to bring this up (Glad you did). I'd rather this be on the website thread though to get other opinions as well. Or the mailing list, whichever you prefer for discussions. 
So, my stance is to have the team code on the root of the website, and have a link that goes to WP, since it would be easier to see "the fruit of everyone's labor". It would encourage more activity within the team to have a never-ending project is what I'm thinking. But I can also see both sides to this coin and can completely understand the want for a finished software project. So this is just another one of those things where I'm waiting for a team decision.

Me:
> Well, it's not really a matter of having a finished product to me - I'd really like to see the website be a constantly evolving project that just keeps getting better, just like you. And I really think you can have that with Wordpress. It's the speed at which you can improve/evolve a website with Wordpress that appeals to me. But I can also see what you're saying, that hand-coding allows everyone to collaborate, not just those familiar with Wordpress. So there are advantages and disadvantages to both. I'm obviously quite biased because I've become accustomed to Wordpress and really like it a lot.

But, as you say, the forums is the best place to talk about it. I'll probably post something tomorrow as it's getting late today.

binarymutant:
> feel free to copy paste this conversation if you want, might be quicker :D

Like binarymutant, I can see both sides of the argument. Hand-coding and using bzr/Launchpad gives the website more of a collaborative feel. However, Wordpress speeds up the process and allows cool features such as a blog or a blog "planet" to be easily placed inside the same theme as the "static" pages, giving everything a unified look and feel.

One disadvantage of Wordpress is that changes to things such as themes and pages cannot be reviewed by admins before being published (though blog posts can). Reviewing features can be expanded with plugins, though, perhaps making this a non-issue.

So, what are your thoughts? :)

---

