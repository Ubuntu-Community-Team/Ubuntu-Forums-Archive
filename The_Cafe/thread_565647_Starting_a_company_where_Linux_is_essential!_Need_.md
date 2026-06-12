---
title: "Starting a company where Linux is essential! Need advice and suggestions!"
date: 2007-10-02
forum: The Cafe
---

### Post by Spif on 2007-10-02
For easy readability, my post is divided in several sections. You can skip to the last section if you wish to only see my questions, the rest is only information that may help you more accurately.


**Introduction:**

I am currently working on a small project of mine: Starting a small company with me as the only employee. As I am a business/economics student at a university, it will only be a small spare-time project, but hopefully a very learning experience that will help me in my future career. 


**Company concept**

As for what my company will focus on, I simply cannot reveal yet. Too many things are still being researched thoroughly and I want to make sure all my ideas can be realized before I make any "public" statements.

However, this is unimportant. All you need to know is that I will be dealing with IT and that computer systems in general will play a vital role in my company concept. Free Open-Source software is everything to my company.


**Linux infrastructure**

A Linux-based infrastructure that is running smoothly and is easily maintainable is currently priority number one. Initially this will be the only thing that will lead to high expenses. As I am a poor student and because my time is limited, I cannot afford to make any mistakes regarding this. Making the right choice the first time is a must.

For that reason, I am seeking advice from other Linux users. Hopefully together we are able to make the best decision. 

My system will consist of the following:

[LIST]
[*]Laptop x1
[*]Stationary computer x1
[*]Server x1
[/LIST]

All machines will be running Linux.


**Questions**

*I need a good, reliable server. *
[LIST]
[*]It is very important that the server is energy efficient, as big electricity bills are unwanted.
[*]It will be used for multiple things, including mail, storage, system administration, etc.
[/LIST]

How powerful will it have to be to perform all this at once? Can you recommend me good, cheap server capable of this? 


*Operating system*
Requirements:
[LIST]
[*]Must be easily able to maintain a network of computers centrally.
[*]High security, including encryption, is a huge plus.
[/LIST]

Have looked at both Novell SLED 10 and Red Hat Enterprise Linux 5. Both seem to be very advanced and cover more than enough of my needs.RHEL is very expensive, but then I could always go with CentOS.
What would give me the best value for the least money?


*Software*

Meed suggestions for good FOSS software that will help me with management. ERP, CRM, etc. GTK+ applications are big pluses.


This is what I currently need advice with, more will likely come later. Thanks in advance for helping me!

---

### Post by maybeway36 on 2007-10-02
It would be worth checking out Fedora and Debian.

---

### Post by miggols99 on 2007-10-02
You don't want to have to pay for something like Red Hat or SLED. I recommend Debian stable because it is updated *really* slowly. Which is perfect for servers. Only security fixes.

---

### Post by Jussi Kukkonen on 2007-10-02
> **Spif said:**
> 
*I need a good, reliable server. *
[LIST]
[*]It is very important that the server is energy efficient, as big electricity bills are unwanted.
[*]It will be used for multiple things, including mail, storage, system administration, etc.
[/LIST]
How powerful will it have to be to perform all this at once? Can you recommend me good, cheap server capable of this? 

The electricity costs are not something you should worry about -- that won't make or break your business. You didn't actually list what you will be using the server for (except the mail/storage), so it's difficult   to estimate what kind of machine you'll need -- mail/storage can be handled with very low end HW. Some pointers:
[LIST]
 [*] if you're on a shoestring budget and do not have requirements for super high availability, you can use an ordinary low end desktop machine.
 [*] Most server duties can be accomplished with very low performance hardware (but if you want performance, expandability or fast service, be prepared to pay through the nose)
 [*] If mail and storage are the only thing you'll need the server for, I suggest you forget the server and use your ISPs email and a NAS box for storage/backups -- easier, faster, cheaper.
[/LIST]
> 
*Operating system*
Requirements:
[LIST]
[*]Must be easily able to maintain a network of computers centrally.
[*]High security, including encryption, is a huge plus.
[/LIST]

*"Security is process, not a product"* -- the most secure operating system will be the one your sys.admin is (or you are) most familiar with... Any major linux distribution can be made very secure.

It's good to plan ahead, but frankly I wouldn't worry about central software management when you're just trying to employ yourself... something like a local apt proxy will be "good enough" for a long time.

---

### Post by p_quarles on 2007-10-02
> **miggols99 said:**
> You don't want to have to pay for something like Red Hat or SLED. I recommend Debian stable because it is updated *really* slowly. Which is perfect for servers. Only security fixes.
You certainly don't have to pay for RHEL, because CentOS is a free clone :D

I use Debian stable on my home server, and second the recommendation. Just wanted to point out that CentOS exists and is good.

---

### Post by mohnkern on 2007-10-02
From a server standpoint, I agree, Debian is an excellent very stable choice.  I had several Debian boxes in a corporate environment, and they were extremely stable.  Uptime was measured in months on most boxes, and on a few a year or longer.

If you're talking about configuration management, I recommend Webmin, assuming it's still in development, it provides an excellent management interface, allows you to "match machine configurations" and can be done locally, or remotely.

---

### Post by blackhowling on 2007-10-02
CentOS would get my vote

---

### Post by KCPokes on 2007-10-02
> **blackhowling said:**
> CentOS would get my vote

Agreed.

---

### Post by DarkOx on 2007-10-02
If you're looking for CRM software, [SugarCRM]("http://www.sugarcrm.com/crm/") is good to look at. It's run through apache -- so you can use it locally or place it on your sever to have access to it anywhere with a web browser.

---

### Post by koenn on 2007-10-02
for the server OS, I'd recommand Debian, stable release (currently : Etch). runs forever, hardly changes. You can't get more stable than that. CentOS is Redhat minus the support, and is used as testing grounds for RH. I wouldn't recommend that for a production environment. 

for desktop and laptop, i'd say choose a distro that has the software you're going to need. Less install hasle. Or pick one in the same family as the server OS (eg Debian -> Ubuntu), so you're always on familiar ground. 

hardware requirements depend on what the server is going to be used for. If it's only for you, a desktop computer is good enough. I have a dns, dhcp, web, database, file and apt-proxy server running on a single pentium II machine without any performance trouble. 

Do get a decent backup sollution for your server (and the desktop and laptop pc if you plan to have data there as well)

Security is simple : decide what your server needs to be doing, and for whom (and possibly : when). Then take mesures to ensure it does only that, and only for those you intended (and only at the times you want it to). How ? That depends on the what and for whom.

---

### Post by samb0057 on 2007-10-03
Put an ad on craigslist to give out free copies of ubuntu. then put a sticker with your company name and number on the cd. you can get some customers this way. i've done it myself, it works

---

### Post by Spif on 2007-10-03
Thanks for the replies so far! Keep them coming :)

I've had a really rough day... statistics, math and two hours of football (my body is aching all over) followed by an hour on a bicycle, simply too tired to comment on the posted advice right now. Sorry.

---

