---
title: "Ubuntu Server will never be used in a Real IT enivroment"
date: 2007-10-28
forum: Server Platforms
---

### Post by robinlennox on 2007-10-28
Hey all,

Before the Flaming begins... I love Ubuntu and try to get people to convert from Micro$oft every chance I get.

However, I have a massive problem trying to sell it to System Admins, you know the one's, they've had an MCSE since NT 4 and swear by Micro$oft. Not realizing that an MCSE Course is designed by Micro$oft to push there products... but that's another story.

Well, everything I even discuss Linux specially Ubuntu as a viable alternative to their Micro$oft.

They always try complain of a lack of easy roll out, such as 
[LIST]
[*]No Active Directory alternative (So they can Authenticate)
[*]No Group Policy to manage they Computer and User Objects (Even thou, M$ only sorted this out in W3K)[/LIST]Now I've been "dabbling" with Ubuntu since Version 4 and been waiting for the these Ubuntu / Linux "Killer applications" alternative to appear...

And nothing, we are on version 7.10 and still nothing...

If Ubuntu, wants to become a viable alternative to Windows and open Linux to the masses, why have they missed out Business sector.

Business sector will not adopt Linux without AD and GP alternative; purely because there lazy and don't have the time or wont learn anything new. 

As most users use computers while at work, is that not the best market to expose these users to Ubuntu. Hence we need to create an alternative to Windows Server... to encourage System Admins to roll-out Ubuntu.

Just my 2 Pennies worth... Maybe I've missed something or maybe I'm mad... who knows?

What do you think?

---

### Post by meatpan on 2007-10-28
> **robinlennox said:**
> 
They always try complain of a lack of easy roll out, such as 
[LIST]
[*]No Active Directory alternative (So they can Authenticate)
[*]No Group Policy to manage they Computer and User Objects [/LIST]

What do you tell them?  Just curious, because these two types of technologies have been core to unix for decades.

Check out LDAP and the many successful LDAP wrappers and derivatives.

---

### Post by koenn on 2007-10-28
yep, the authentication part of Active Directory is nothing more than ldap and kerberos, with a nice GUI painted over it. 

Microsoft added Computer and User management to it because they needed a way to manage networked computers. In Unix (and thus Linux), this problem was solved by confining users to their home directory (so no need for all these policy settings to rectrict access to system files, program directories, control panel, ...), and having all user-environment configuration inside that user home directory. That, with the ability to have those 'user profiles' on a server and mount them to the users' filesystem was all it took. From that perspective, AD is a horribly complex and error prone way of managing computers and users. 

But, granted, it's a completely different way of looking at things so sysadmins who only know the Microsoft way will have difficulty to grasp the fact that there are other ways. And just like some users will never stop complaining that Ubuntu is not 'desktop ready', some sysadmins will never be willing to look at anything other than what they know and are used to.


Besides that, I think your right that Ubuntu will have trouble finding a place in the server market. Other distros are well established there, and I don't see what Ubuntu has to offer to compete with them. Possibly the 'ease of use' factor will get them an opening in the small business sector, but that's it, I think.

---

### Post by HermanAB on 2007-10-28
Oh, goodness, I have had MCSEs complaining that Unix doesn't have a database backed mail server and then getting very angry when I point out that Citadel has had a database back-end since before Microsoft was founded, that Exchange still bogs down at around 100GB, while Citadel can handle up to 256TB...

Anyhoo, as others pointed out, LDAP and Kerberos are originally Unix applications.  While the origin of  Sun Yellow pages has been lost in the mists of time, the present incarnation called Network Information Service (NIS), is quite good thank you and yes, it runs on Ubuntu.

If you specifically want a drop in Active Directory replacement, then have a look here: [http://news.samba.org/releases/4.0.0alpha1/](http://news.samba.org/releases/4.0.0alpha1/)

Cheers,

Herman

---

### Post by robinlennox on 2007-10-29
Thanks for the great feedback.

The comments you have given are really useful. koenn was right; that Unix/Linux deals with authentication is a completely to that of Microsoft.

Hence the reason why system admins won't use Linux. These guys, struggle using OpenOffice or Office 2007 because it "Look Different.".

I take on board about LDAP, which I have known of for years, but not been able to push for two reasons:

[LIST]
[*]There are no step by step guide on how to setup authentication.[LIST]
[*]I think, if there was a video Library, like there are for the MCSEs, we could get some system admins to "Attempt" an install of Linux"[/LIST]
[*]The second point is where is the Group Policy alternative???[LIST]
[*]Most System Admins, enjoy been able to undeploy software/ applying policy's by linking/unlinking objects by using a nice GUI interface[/LIST][/LIST]Samba4 looks very interesting but this only deals with half of the soultion, Authentication and Authorisation.

There needs to be some sort of group policy alternative which is as GUI friendly as Group Policy....

Maybe there is one out there but I haven't seen it....

Thanks again for all your feedback.

---

### Post by netlogic on 2007-10-29
>     * The second point is where is the Group Policy alternative???
          o Most System Admins, enjoy been able to undeploy software/ applying policy's by linking/unlinking objects by using a nice GUI interface

What you want to do can be achieved, but it is difficult to do it in Linux than Windows. When you are calculating and trying to make decisions, you have to weight in the pros and cons. Something in Linux are better. Something in Windows are much better. Like Remote management for Windows is painful, because only good option is RDP.

There are various group policy tool for Linux, but it isn't the same or feature full like Windows. Have you checked, Kiosk Admin Tool? Also, there are many others, but it isn't the same as Windows tools.  Only thing I discovered was migration to Linux in a large enterprise will be very difficult. There are so many missing pieces to make it a smooth migration that unless you have a huge team to get involved, it can't be done. If you can justify the cost of consultants from the cost of OS and MsOffice applications, it might be feasible to hire a team to help you out. If this is a small environment, I think using the basic Samba setup to mimic NT4 environment is the best and wait for Samba 4 to be mature. Also, aren't you a bit tired of Microsoft's way of innovation? 2008 and Vista are disaster. I rather pay for constant advancements for Xp and 2003 bug fixes than upgrade to new features of newer oses. Everything has pros and cons. I am sorry I can't give you a better answer.

---

### Post by HokeyFry on 2007-10-29
at my job one of the guys i work with asked one of the sysadmins when he first started working there if they had any windows servers. he just scoffed and said, "Haha! Wait you're.... no, no we don't."

---

### Post by robinlennox on 2007-10-29
Hi HokeyFry,

I'm a willing convert to Open-Source as are most of the people who I work with.

However, when we try to convince others, we always hit a brick wall.

Most System Admins, just wont leave the easy and comfortable world of M$.

As you said, to implement Linux is very difficult compared to Windows. With Windows you can have a domain with A/D & group policy in about 2 hours....

With Linux, it's taken a least a day to get a system setup with A/D never mind G/P.

OK... I've got an idea...

Does anyone have any knowledge on setting up a Linux version(Ubuntu) A/D Domain with Group Policy. Without using any M$ tools.

Then I'll document it, and hopefully then show these veterans of Micro$oft, there is a world beyond Windows! :lolflag:

---

### Post by netlogic on 2007-10-29
[http://www.linux.com/articles/113755](http://www.linux.com/articles/113755)

I am sure there are many howto if you searched google. Actually, documenting the process on the forum will take few hours to a day to come up with some thing substantial that can be very useful. However, I am sure someone already has documented the process if you carefully searched.

---

### Post by robinlennox on 2007-10-29
> **netlogic said:**
> [http://www.linux.com/articles/113755](http://www.linux.com/articles/113755)

I am sure there are many howto if you searched google. Actually, documenting the process on the forum will take few hours to a day to come up with some thing substantial that can be very useful. However, I am sure someone already has documented the process if you carefully searched.

The link you sent says, what you should consider; not how to implement.

I have looked and looked and looked and... Looked for a "how to setup a Linux version(Ubuntu) A/D Domain with Group Policy" and found nothing in all of my years of trawling various Linux forums and search engines.

All I find are post or sites saying it's a good idea. But I am looking for or would like help to actual create a document outlining how this is possible. Then i can someone who isn't very familiar with Linux the document so they can give it a try.

I.E[LIST]
[*]Once Ubuntu Server is installed, use XXXXXX, which will act as your Active Directory. You can.....
[*]In Linux we use XXXXXX instead of Group Policy, you can create policy's by.....
[*]Congratulations you have a Linux Active Directory / Group Policy Domain :)[/LIST]If I have missed a "How To Guide" on my travels please share it :)

---

### Post by netlogic on 2007-10-29
Check and search Suse Enterprise and RHEL forums. I have seen them before. Actually, the process like this will take 16hrs out of my time to document.I am sure others who have more free time have documented on other forums. RHEL is a very good commercial Linux. I am sure they have documented and created a wonderful White paper on howto.

---

### Post by robinlennox on 2007-10-29
I'd rather stay clear of Red Hat & Suse as I wouldn't feel right suggesting a Distro which has frequent legal issues or gets into Bed to Microsoft just to avoid a Lawsuit.

That's the beauty of Ubuntu, it's one of a very few distros which can run well and have great functionally without having to have lots of closed source apps. Also the Application Manager is second to none.

What I'm really looking for is a guide with Ubuntu.

---

### Post by netlogic on 2007-10-29
They are all Linux to me. :) Documents designed for RHEL and Suse Enterpise will work fine for other Linux distros. You have to try other forums if you can't find answers here.

---

### Post by koenn on 2007-10-29
> **robinlennox said:**
> IWhat I'm really looking for is a guide with Ubuntu.
and that's your first mistake. 
Sysadmins should design and implement sollutions. You shouldn't let a pseudo-requirement like that stand in the way of soving the problem at hand. 
If I had to provide file sharing to a bunch of windows clients, I'd consider samba a suitable alternative. If I needed to add centralised authorisation and single-sign-on, samba, ldap and kerberos might still  be an alternative, if i could convince myself / my collegues / my boss / my customers that the extra work involved outweights the downsides of AD (eg costs of CAL's etc). If the situation required features that AD offers out of the box but that Linux only can offer through weird workarounds and complex contraptions, I'd go with Active Directory. Simple as that. 

Look at it this way : 
would anyone consider it a good idea  - technically, all anti-MS feelings and cost / license issues aside - 
to pile op a heap of tricks, workarounds and complex (thus fragile) contraptions to manage  a bunch of linux workstations through Windows Active Directory or some other MS-specific technology while there are simple and straightforward Linux solutions to do the same ? . I don't think so. So, then, why would managing a Windows environment with Linux tools be such a good idea ?

---

### Post by robinlennox on 2007-10-29
The reason why I have choosen Ubuntu, is due to the fact it has a large Community base. Also it doesn't have any legal issues at the moment which Red Hat or Suse have. Also most people who I show different Distros to prefer, Ubuntu for it's ease of use, anon, anon.....

However, Debian could naturally be a possible alternative as could many other Linux distro but none of them have a user community such as Ubuntu.

But to go back to my original post of "Ubuntu Server will never be used in a Real IT enivroment"

After numerous posting it's becoming clear that there is no competitor in the Linux world for a policy based management tool which doesn't involve more then 2 hours of work to get a basic system working with Authentication & Authorisation.

Which means "Unfortunately", No-one is going to seriously adopt an open-source IT System.  

The Microsoft Package is very good... it's just a shame there is no alternative. Which means system admins will continue to push M$ and Linux will always be the server designed for heavy work and that's it. :cry:

---

### Post by netlogic on 2007-10-29
Like I said before, it can be done. It is something someone cannot write within few pages. That is why. Have you checked Amazon for books? I searched Amazon

[http://www.amazon.com/gp/product/1931836396/ref=s9_asin_title_1/002-8835386-0717615?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=1TP7ME989Z5JD5Q12572&pf_rd_t=101&pf_rd_p=320448701&pf_rd_i=507846](http://www.amazon.com/gp/product/1931836396/ref=s9_asin_title_1/002-8835386-0717615?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=1TP7ME989Z5JD5Q12572&pf_rd_t=101&pf_rd_p=320448701&pf_rd_i=507846)

I am sure one of these books will fit your need. Also, have you called Ubuntu for technical support? This topic is very complicated that cannot be easily explained in the forum. It isn't a task problem issue. You are asking for answers on complicated planning and integration of execution of it strategies. I think that's why  people have hard time explaining it to you.

---

### Post by DSK on 2007-10-29
Perhaps this will  be the answer some day.

[http://ebox-platform.com/features](http://ebox-platform.com/features)

gutsy now has this in the repos.

---

### Post by kentl on 2007-10-29
Also if you write MS and Microsoft instead of M$ and Micro$oft people tend to take you more seriously. The latter way of writing only works, and barely even there, in biased environments like here on these forums where most people love Linux.

---

### Post by koenn on 2007-10-29
> **robinlennox said:**
> The reason why I have choosen Ubuntu, is due to the fact it has a large Community base. Also it doesn't have any legal issues at the moment which Red Hat or Suse have. Also most people who I show different Distros to prefer, Ubuntu for it's ease of use, anon, anon.....

However, Debian could naturally be a possible alternative as could many other Linux distro but none of them have a user community such as Ubuntu.

But to go back to my original post of "Ubuntu Server will never be used in a Real IT enivroment"

After numerous posting it's becoming clear that there is no competitor in the Linux world for a policy based management tool which doesn't involve more then 2 hours of work to get a basic system working with Authentication & Authorisation.

Which means "Unfortunately", No-one is going to seriously adopt an open-source IT System. 

The Microsoft Package is very good... it's just a shame there is no alternative. Which means system admins  will continue to push M$ and Linux will always be the server designed for heavy work and that's it. :cry:

In the real life IT environments I know of, Service Level Agreements are valued over community support. OS communities matter in terms of development, not support. 
And if sysadmins choose microsoft because it does what they need, they're making the right choice. 
That doesn't mean that "No-one is going to seriously adopt an open-source IT System.  " - IBM, Oracle, Google ... that's not IT then ?
It all comes down to 
1/ chosing the right tools for the job
2/ keep een eye on the big picture (as in : you don't implement a partial sollution that doesn't fit in with the rest of your evnvironment)

---

### Post by robinlennox on 2007-10-29
> **koenn said:**
> In the real life IT environments I know of, Service Level Agreements are valued over community support. OS communities matter in terms of development, not support. 
And if sysadmins choose microsoft because it does what they need, they're making the right choice. 
That doesn't mean that "No-one is going to seriously adopt an open-source IT System.  " - IBM, Oracle, Google ... that's not IT then ?
It all comes down to 
1/ chosing the right tools for the job
2/ keep een eye on the big picture (as in : you don't implement a partial sollution that doesn't fit in with the rest of your evnvironment)

Koenn,

I don't know what you consider "Real" IT Departments... But most IT Managers who can't resolve issue with Microsoft products, tend to use the Largest Community base for any IT Product I know of: MSDN... :lolflag:. I use this all the time for a wide variety of issues so i keep to my SLA!

That's why, I think Ubuntu would be a good alternative to the MSDN :). The Ubuntu Community reminds me of the MSDN and I'm sure I'm not the only one to think that.

Who said I don't like SLA's! I love them, if i stick to them i get a pay rise :)

Google, IBM don't use Microsoft... Ummm.... I think most of there Database and other "heavy work" is done by linux.

But for Authentication / Authorisation and Policy Management, I bet you they'll be using a Microsoft Box somewhere :)

But Keep your eye on the "big picture". This Thread was about, me asking for advise on tools I could show System Admins. Then maybe they can see the possibles of Ubuntu / Linux in particular i was looking at A/D and G/P.

It wasn't me saying that Micro$oft are crap... or I hate Microsoft... Far from it... Microsoft have there place as Linux does...

Also this post wasn't about me say: "HELP: I want to get rid of all my Microsoft Products for Linux". Why would anyone do that after spending Hundreds of Thousands of Pounds on their Products!

So please stop preaching on about choosing the right tools.:popcorn:

kentl, what is the big deal about putting M$ or Micro$oft... What a way to hijack a post:guitar:.

Please start another thread saying "I hate people who put M$, Micro$soft"... and if you have nothing constrictive to say please don't waste your time writing a post....

DSK - Thanks for the Link... I found this very Useful... This looks very promising!

---

### Post by robinlennox on 2007-10-29
Please don't Hijack this thread by Flaming.

---

### Post by netlogic on 2007-10-29
There are few SV firms that went 100% Linux. Also, many small companies have gone all LINUX. Many Universities have gone Linux due to the cost factor. Also, I don't think people are flaming here. You are reading into it too much from your frustration. Also, this isn't a good way to get help, because Ubuntu offers free products, it doesn't mean the community has also help everyone out. It isn't necessary to flame in a technology forum.

---

### Post by koenn on 2007-10-29
> **robinlennox said:**
> Koenn, ...

robbinlennox, 
your OP sounded rather like you were looking for drop-in replacements, like you were trying to replace one (Windows) apllication with another (running on Linux). In my professional opinion, that's not the way to design sollutions for computer and users management, or any other IT infrastructure. Hence the preaching about the right tools. I'll stop preaching now. 

Some things you apparently misunderstood : 
- I mentioned IBM, Google and Oracle as IT providers who are notorious for using, selling, and promoting Linux - in response to your claim that "No-one is going to seriously adopt an open-source IT System.". Whether or not they use AD, I don't know. Given that e.g. Google employees use Linux desktops mostly, I'd be interested to see how those integrate with the Microsoft Box you think they have there for Authentication  :) .

- as for the community support : I was looking at it from the customers' point of view - i hadn't understood that you'd be selling SLA's to them, then use the community support forums to help you keep your promises.

---

### Post by koenn on 2007-10-29
> **netlogic said:**
> There are few SV firms that went 100% Linux. Also, many small companies have gone all LINUX. Many Universities have gone Linux due to the cost factor. 
yep, that's it. If it's all Linux, its manageable. If it's all Windows, too. 
It's the mixed environments and trying to solve Windows problems with Linux tools that are the hard part. 

Oops, preaching again  :)

---

### Post by Tlon on 2007-10-29
> **robinlennox said:**
> Hey all,

Before the Flaming begins... I love Ubuntu and try to get people to convert from Micro$oft every chance I get.

However, I have a massive problem trying to sell it to System Admins, you know the one's, they've had an MCSE since NT 4 and swear by Micro$oft. Not realizing that an MCSE Course is designed by Micro$oft to push there products... but that's another story.

Well, everything I even discuss Linux specially Ubuntu as a viable alternative to their Micro$oft.

They always try complain of a lack of easy roll out, such as 
[LIST]
[*]No Active Directory alternative (So they can Authenticate)
[*]No Group Policy to manage they Computer and User Objects (Even thou, M$ only sorted this out in W3K)[/LIST]Now I've been "dabbling" with Ubuntu since Version 4 and been waiting for the these Ubuntu / Linux "Killer applications" alternative to appear...

And nothing, we are on version 7.10 and still nothing...

If Ubuntu, wants to become a viable alternative to Windows and open Linux to the masses, why have they missed out Business sector.

Business sector will not adopt Linux without AD and GP alternative; purely because there lazy and don't have the time or wont learn anything new. 

As most users use computers while at work, is that not the best market to expose these users to Ubuntu. Hence we need to create an alternative to Windows Server... to encourage System Admins to roll-out Ubuntu.

Just my 2 Pennies worth... Maybe I've missed something or maybe I'm mad... who knows?

What do you think?

I'm sorry, but this whole post is just absurd.  Have you ever actually worked in a corporate IT environment?  In a position to make any decisions?

"Not realizing that an MCSE Course is designed by Micro$oft to push there products... but that's another story."

Everyone knows that MCSE is designed by MS.  It's an MS cert.  Nobody takes an MCSE to learn.  They take it to make more money.

"Business sector will not adopt Linux without AD and GP alternative; purely because there lazy and don't have the time or wont learn anything new."

Yeah... "too lazy" to axe their entire departments, hire a whole new department, and re-tool their operations around a nix-based infrastructure.  LOL.  In the Real World, it takes more than a certification class or two to make a techie trust-worthy in a given field.  Most employers want years of hands-on in-the-trenches experience, not a few certification classes.  Do you have any idea what it would take for an established MS-based enterprise environment to transition to *nix?

There are a lot of other reasons why pickup of Linux is bad.  Image is a biggie.  Free = cheap-in-the-pejorative-sense to non-IT people.  Another is, "if nobody pays them for it, what's to stop them from bailing out, and leaving us with unsupported and under-developed software?"  The FOSS philosophy is anathemic to the mainstream mode of thinking in Big Business, and it creates a tremendous amount of back-pressure against adoption.

"Killer apps" really don't have anything to do with it.  The reason is that the people in positions to make decisions aren't sysadmins.  To them, a "killer app" is defined as one you can make the strongest business case for in 30 seconds or less -- and sysadmins tend to be a bit under-skilled in that department.

---

### Post by robinlennox on 2007-10-29
How did I know when I started this thread, I'd get some "Die Hard Linux Users" typing things that aren't productive and anything to do with the post.

Well I am thankful to the people who actual give me a hand. :popcorn: I mean that sincerely, I have something to work on; Thank you.

You've all been a great help!

But as with all communities there are always some people who need to spoil it for others. Shy...

I'm going to unsubscribe to this thread so please waste your time write what every you want.. whine saying I'm not what you think I am and so on... and whatever the rest of the drivel Tlon wrote about.... I didn't even waste my time reading it all.

What a way to crash a post Tlon, koenn & netlogic and added nothing productive to it apart from whining and bitching.

Thankful, the Linux world seems to be lacking more of users like you. You don't happen to come from the MSDN do you?

The unhelpful responses to post users get to there questions about Windows seem to get a similar response to what you gave to me.

Hey maybe Tlon, koenn & netlogic; just have alot of time on their hands, writing rubbish in post because they have nothing else to fill their day... I wonder why they have all this free time: They seem like a WOOT! :lolflag:

---

### Post by netlogic on 2007-10-29
One thing I discovered over many years on tech forums is a response like this will hurt you. That is all. If you want help from others, there are better ways to ask. Most likely, three of us will now avoid your posts. Also, I used to be an IT manager, and I remembered a tone like this almost got me fired. Anyway, good luck with your finding. Also, pickup the book that I suggested.  I hope you understand what Koenn and me are trying to tell you. Some times, there aren't magic commands someone can make it for you. Once, you discovered a good way by your research, you might come up with own magic command scripts for your deployments.  Also, if you want others to do your homework, most people tend to beg and ask in a nicer fashion. It is very important to know, books are still required to learn a new technology. The maturity also helps.

Good luck

---

### Post by koenn on 2007-10-29
> **robinlennox said:**
> 
Hey maybe Tlon, koenn & netlogic; just have alot of time on their hands, writing rubbish in post because they have nothing else to fill their day... I wonder why they have all this free time: They seem like a WOOT! :lolflag:
... and robinlennox apparently has to resort to insults and personal attacks when people  tell him something he doesn't want to hear.

But I'll take your advice and not waste any  more time on you.

---

### Post by netlogic on 2007-10-29
He seems like a college student who is trying to learn a real life IT scenario. We all know in forums, many people aren't what they seem.  No harm done. He doesn't sound like a IT professional to me. I hope he does more reading and gets what he wants to accomplish.   I guess he doesn't understand Microsoft's MSDN is for developers not for administrators. He doesn't seem like a person who was trying to  research and write an Active Directory clone. No harm done. People should just avoid this thread.

---

### Post by DraK on 2007-10-30
Check up on Ebox, I hear it coming to Ubuntu..

[http://www.ebox-platform.com/](http://www.ebox-platform.com/)

---

### Post by jaakan on 2007-10-30
> **robinlennox said:**
> Business sector will not adopt Linux without AD and GP alternative;

I have been a Systems Administrator for both Windows and Linux servers.
I come from a mixed 24/7 production environment background where all of the Linux boxes where running as a database server or a web server. And guess what not one used AD or GP. 18 redhat 3 Ubuntu all on DELL hardware.

Larger and Smaller companies do this as well. 

Here is an FYI 

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

[http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication](http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication)

---

### Post by rbprogrammer on 2007-10-30
> **jaakan said:**
> 
...
I come from a mixed 24/7 production environment background where all of the Linux boxes where running as a database server or a web server. And guess what not one used AD or GP. 18 redhat 3 Ubuntu all on DELL hardware.
...

speaking of Dell, the company is now starting to sell computes wil ubuntu already pre-installed.  which i think is a huge jump into the business market.  the only thing that needs to happen now is some more marketing.  not too many people know that dell just started doing this.

[URL="http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs"]
http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs
[/URL]

---

### Post by dasunst3r on 2007-10-30
If Windows-based authentication is what you're looking for, then you might want to look at Red Hat Enterprise Linux or SUSE Linux Enterprise series.  In the course of convincing people to at least give Linux a shot, offer the prospect of extending hardware lifecycles and/or server consolidation.

---

