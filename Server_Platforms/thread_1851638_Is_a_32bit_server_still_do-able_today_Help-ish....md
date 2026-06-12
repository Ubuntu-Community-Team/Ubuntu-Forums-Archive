---
title: "Is a 32bit server still do-able today? Help-ish..."
date: 2011-09-28
forum: Server Platforms
---

### Post by hotmonkey on 2011-09-28
Hello Everyone,
 

 Another new Ubuntu Server user here looking to learn and has a question right from the start...
 

 I would like to set up a web and mail server to host my website. I suspect that 10.04 or 11.04 server editions may be the way to go, but I will start learning which soon enough.  
 

 My question is that both editions recommend the 64 bit version for download. Unfortunately all I have and can afford is my 32 bit oldish server. Can I still create a safe, reliable and secure collocated web/mail server using the 32 bit download. Or should I put this project off until I can afford a 64 bit system?  
 

 I really want to get started learning and applying. I just do not want to get so deep into the project if the knowledge, skills and work are not transferable to a 64 bit system when I can actually afford one next year that I should just give up now and wait.  
 

 Looking forward to some comments, suggestions and maybe even a few good links to some tutorials and resources by people that have already done just this sort of thing before.
 

 Thank you!

---

### Post by i.r.id10t on 2011-09-28
Yes, you can... just download the 32bit iso image.

The cliky wizzard for what to download is probably detecting that your browser is running in a 64 bit OS, so it figures you want a 64 bit ISO image.  Just head for the alternate download links...

---

### Post by Dangertux on 2011-09-28
As far as security goes the architecture while it does have some impact has little to do with the ability to make a secure server. Most major tasks can still be accomplished on 32 bit architecture (including virtualization via paravirtualization).

That being said, as your system becomes more robust, it will begin to feel the pressure, whereas a 64 bit system would give you a little more room to breathe.

Securing a 32 bit server and 64 bit server are essentially the same, you just have a few more options in terms of separation in a 64 bit environment (full hardware based virtualization being the most notable)


Hopefully that helps answer your question.

---

### Post by drdos2006 on 2011-09-28
Go with version 10.4 LTS ( Long Term Support ) which will give you upgrades until 2015. Use the 32 bit on older equipment.

I am still using Webmin 1.550 on Server 10.4.
I tried Webmin 1.560 on Server 11.04 but Webmin needed tweaking and I just did not want the hassle. ( I was not able to connect to the server).

Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by hotmonkey on 2011-09-28
Wow!

Thank you for such a great starting point and things to consider. I've downloaded all of the different server iso options available, just in case I needed “... the other one...” situation. 

If I may follow-up with a question that was going to be saved for sometime later, that seems to have been mentioned already. Virtual Hosts/Servers. I am use to the notion of one real box, one real server (so to speak) running a web/mail server. I keep hearing talk about “virtual this and virtual that...” 

Since this is all new to me at this point. Would it be a better option to set up an ubuntu server, and then create some sort of virtual web/mail server instance for what I want to do (the now old fashioned way) or stick to a more traditional approach? 

Again, Thank you.

P.S.
I wish I could share how exciting and fun I think this is going to be if I don't mess it up too much.

---

### Post by Dangertux on 2011-09-28
> **hotmonkey said:**
> Wow!

Thank you for such a great starting point and things to consider. I've downloaded all of the different server iso options available, just in case I needed “... the other one...” situation. 

If I may follow-up with a question that was going to be saved for sometime later, that seems to have been mentioned already. Virtual Hosts/Servers. I am use to the notion of one real box, one real server (so to speak) running a web/mail server. I keep hearing talk about “virtual this and virtual that...” 

Since this is all new to me at this point. Would it be a better option to set up an ubuntu server, and then create some sort of virtual web/mail server instance for what I want to do (the now old fashioned way) or stick to a more traditional approach? 

Again, Thank you.

P.S.
I wish I could share how exciting and fun I think this is going to be if I don't mess it up too much.

First let's clarify what virtualization actually is -- since it's not the same thing as virtual hosts. Virtualization in the server world is a lot like trying a different operating system using something like Virtual Box or VMware fusion.  At the basic level, the same things are happening the reasoning behind it is a little bit different. So for the sake of example let's say you want to do the following. You want to run a Wordpress site (just an example), hosted on Apache. You also want a mail server for your domain. Obviously you will also need a database back end for your Wordpress site so you choose MySQL.  Keep this set up in mind we will revisit it in a moment.

Now in a traditional "physical machine" realm. You might have all the services running on one machine, Linux is definitely capable of doing this, and it's not necessarily a bad thing.  However, when it comes to virtualization it has a few appeals, the first being for large companies it lowers the cost of doing business. Instead of seperating their resources and buying seperate physical servers they can do it buy creating multiple virtual servers on one powerful machine.

Wait, I just said Linux could run all these services on one server, right? Yes -- however here comes the second selling point for virtualization. Security, while there are arguments made that virtual security is bogus, it has matured alot in the past 5 or so years. Yes, you can break out of a guest instance and make calls to the hypervisor, but local escalation has always been possible in any method for seperation. Anyway -- the basic concept is this, seperation of resources. So in a virtual arena you would have one physical machine running a hypervisor (Xen, VMware EXsi , KVM whatever) that hypervisor would be in charge of handling multiple guest instances, which are the virtual servers. Each one is it's own operating system contained from the others (and theoretically the hypervisor/host OS). So you would now have 3 virtual servers, one say for your database, one for your mail server and one for your apache server. The concept is, if one is compromised at say the root level, it only effects that virtual server, not the other 2. Now of course, depending on what was compromised you also may lose one or both of the other 2 anyway due to the fact that root will likely have access to credentials on those other systems. Anyway, the basic concept is containment.

Additionally, you have the added benefit of easy migration. It is extremely easy to migrate one virtual machine to new hardware, as opposed to doing a full reinstall on new hardware if you are to upgrade in the future.

So how does all of this nifty stuff tie in to your situation? Well -- as I said before, you have a problem, you're using 32 bit hardware. While some 32 bit hardware supports paravirtualization (not going to get into the difference at the moment, we can discuss it further in for simplicity sake) it does not have support for full hardware virtualization, meaning some of your options will be limited. You would likely be using Xen, or a VMware product. KVM which is what Ubuntu natively supports best is not possible due to it's need for hardware supported virtualization. (This is one reason I don't like Ubuntu Server as much as I used to). 

Also, due to the age of the hardware virtualization may not be practical, but that all depends on the load you are expecting on your server. For now with the lower end hardware and the types of services you're talking about running though, I would not recommend virtualization, unless you just want to learn about it in which case that's cool. However, I don't see much actual practical benefit behind it in this case.

Hope this is helpful.

---

### Post by hotmonkey on 2011-09-28
Helpful? Are you kidding?

I only wish I could convey these concepts and applications half as well. 

This is great to actually easily understand what all the talk is about. Thank you for taking the time and effort to clarify that for me, and hopefully others. I guess it will be something for round 2, when the budget and knowledge base get there. I see where it can be a useful way to do some things when you have the need, or desire to keep moving toward discrete segments of a larger project in my case.

I think I will look forward to giving it a try, after I get these (new to me) Ubuntu Server basics under my belt.

Thank you...

---

### Post by Dangertux on 2011-09-28
Any time glad I could be useful , good luck with your new server :-)

---

### Post by Jonathan L on 2011-09-29
> **hotmonkey said:**
> Hello Everyone,
 

 Another new Ubuntu Server user here looking to learn and has a question right from the start...
 

 I would like to set up a web and mail server to host my website. I suspect that 10.04 or 11.04 server editions may be the way to go, but I will start learning which soon enough.  
 

 My question is that both editions recommend the 64 bit version for download. Unfortunately all I have and can afford is my 32 bit oldish server. Can I still create a safe, reliable and secure collocated web/mail server using the 32 bit download. Or should I put this project off until I can afford a 64 bit system?  
 

 I really want to get started learning and applying. I just do not want to get so deep into the project if the knowledge, skills and work are not transferable to a 64 bit system when I can actually afford one next year that I should just give up now and wait.  
 

 Looking forward to some comments, suggestions and maybe even a few good links to some tutorials and resources by people that have already done just this sort of thing before.
 

 Thank you!

Hi Monkey

... while I don't disagree with a word Dangertux has said, there's aboslutely nothing wrong with starting with a 32-bit system to learn things.

I'd recommend starting with 10.04 LTS server and learning about things in the following order:

[LIST=1]
[*] Servers in general, connecting via SSH, the networking, DNS, user rights and so on
[*] Apache to understand the web server process, including virtual hosting
[*] PHP for dynamic content
[*] MySQL for stored dynamic content
[*] Email (recommend postfix for starting)
[/LIST]
 You can just use a 10.04 LTS install and choose LAMP server, SSH server, configure the postfix ... and start experimenting.

If you want a good thing to install, mediawiki is a great way to see that you have everything running properly and find out how a fully-functional system works all together.

Then after that ... I'd start thinking about virtualisation, and then you'll care whether you have a 32-bit or 64-bit system.  But you'll have some experience then to understand, for example. the interactions between web, mail, and database servers to think about putting them on separate systems, real or virtual.

Just a brief explanation about why I'd recommend this order.  Server first, otherwise you have nothing to work on.  Apache next, otherwise you're not doing web work.  PHP as it's a good compromise between power, ease-of-learning, good structure, and lots of big platforms (eg mediawiki) are written in it.  MySQL is very hard to learn in practice without a decent programming language already covered.  Email last because it's a) optional, b) mostly about DNS and security.

Incidentially, one of the strongest things about Ubuntu is the fact that it has long-term support server versions, which means your things (and tutorials and so on) don't age so quickly.  Really, really, highly, recommend using this if you're learning.  Leave all the jazz until you've got the basics covered and actually need some super latest feature.

Just some thoughts which I hope help.

Kind regards,
Jonathan.

---

### Post by Entilza on 2011-09-29
32 bit is definitely still do-able.  The 64-bit recommendation must be new, just last month 32-bit was still recommended so it looks like things have finally stabalized and moving forward towards 64-bit standards.

---

### Post by kevinthecomputerguy on 2011-09-29
The 64bit recommendation was probably browser detection on the machine he downloaded the .iso from (mentioned above)

I agree, nothing wrong with 32bit (until your memory needs surpass 3.x GB)

Also would like to add \ contradict myself :- )  Virtualization has another great feature, its very nice for backups. You can make complete boot-able backups, even while the machine is on and in use (using snapshots) When you create a virtual machine, it is just a file inside a folder. So your backups become that simple too, complete, 100% ready to boot, moveable to another server if needed, contained in a single folder \ file.

But back to the question, I agree with Jonathan L, get some real 32bit Linux experience, get your feet wet, and if \ when that solution no longer meets your needs, then spend the money. 

-Kevinthecomputerguy

---

### Post by hotmonkey on 2011-09-29
p { margin-bottom: 0.08in; }  Again, Thank you,
 

 I've been following links and reading tutorials from everyone's comments for days now. This is wonderfully helpful and informative.   
 

 I'm currently confused about the proper combination of hardware CPU/MB/RAM for Ubuntu KVM virtualization (that Intel VT-x or AMD SVM and motherboard combination for hardware and kernel use). But looking at prices and my skill level, reality seems to suggest that I need some practical experience before getting too eager or envious of the cool tools available. Let alone starting to save up for some of the prices I've seen...  
 

 I feel much more comfortable now having heard that at the moment, using Ubuntu Server on a 32bit system is still a reliable option and not a poor choice for my modest needs and current budget.
 

 Finally, are there any comments or suggestions on the best or preferred sequence of learning and applying these (new to me) skills? Example; Install, Configure, Security (with Website, Mail and Internet access in mind), LAMP, DNS, MAIL, hopefully you get the idea...  
 

 Kinda like baking a cake. I have all the parts and an oven. But the order you do things really can make a big difference to someone doing it for the first time. Like me...
 

 Best Regards to you all, Thank you.

---

### Post by Dangertux on 2011-09-29
> **hotmonkey said:**
> p { margin-bottom: 0.08in; }  Again, Thank you,
 

 I've been following links and reading tutorials from everyone's comments for days now. This is wonderfully helpful and informative.   
 

 I'm currently confused about the proper combination of hardware CPU/MB/RAM for Ubuntu KVM virtualization (that Intel VT-x or AMD SVM and motherboard combination for hardware and kernel use). But looking at prices and my skill level, reality seems to suggest that I need some practical experience before getting too eager or envious of the cool tools available. Let alone starting to save up for some of the prices I've seen...  
 

 I feel much more comfortable now having heard that at the moment, using Ubuntu Server on a 32bit system is still a reliable option and not a poor choice for my modest needs and current budget.
 

 Finally, are there any comments or suggestions on the best or preferred sequence of learning and applying these (new to me) skills? Example; Install, Configure, Security (with Website, Mail and Internet access in mind), LAMP, DNS, MAIL, hopefully you get the idea...  
 

 Kinda like baking a cake. I have all the parts and an oven. But the order you do things really can make a big difference to someone doing it for the first time. Like me...
 

 Best Regards to you all, Thank you.


For the virtualization aspect, for hardware you really need to have an in depth understanding of how much load your particular applications put on a regular system before being able to accurately purchase hardware with virtualization in mind (less you may end up wasting a lot of money or ending up not spending enough). That is the other reason I would say hold out, see how it performs on bare metal before virtualizing it.

As far as web services go, I recommend LAMP -- one it receives regular attention in terms of security updates , they are also very mature applications so there will be a lot of documentation. 

DNS is going to be bind any where you go with it so that's pretty universal as well (unless you get into things like LDAP domain controllers)

Mail -- sendmail is a very mature project, however very archaic , postfix essentially fills the bill the same but is slightly more user friendly.

As far as guides and tutorials go I would check out the following many of them cover the same territory but multiple perspectives may help you understand a little better.

Official documentation : [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)
Guide I wrote discussing basic LAMP / OpenSSH / FTP set up as well as some details in regards to security : [http://dangertux.wordpress.com/tutorials/reasonably-secure-ubuntu-homesmall-business-server-tutorial/](http://dangertux.wordpress.com/tutorials/reasonably-secure-ubuntu-homesmall-business-server-tutorial/)
Detailed guide on how to forge , goes all the way through and installs pretty much every service up to and including ISPCONFIG 3 (note this guide does some things a little silly when it comes to security) : [http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3)

Hopefully that helps.

---

### Post by Jonathan L on 2011-09-29
> **hotmonkey said:**
> p { margin-bottom: 0.08in; }
 Finally, are there any comments or suggestions on the best or preferred sequence of learning and applying these (new to me) skills? Example; Install, Configure, Security (with Website, Mail and Internet access in mind), LAMP, DNS, MAIL, hopefully you get the idea...  
 

Hi Again Monkey ... I did actually mean my suggestions about what to learn should be done in that order.  I've edited my post to make that clearer.  Hope that's helpful.  Kind regards.  Jonathan.

---

### Post by kevinthecomputerguy on 2011-09-29
@Hotmonkey
 
Your getting great advice from these other guys.
 
There is my website [http://woodel.com](http://woodel.com)  (mentioned above) that is geared for begin'rs who are wise enough to know GUI is not the way. But its a little old school debian, where these guys are pointing you to new school Ubuntu.
 
Either way, read all of our guides. I see many questions like yours, and they read to me like this...
 
"I want to fix cars, but fixing them is confusing, where is the easy button" Well... if it was easy then... everybody would do it. Your not going to achieve your goals without many sleepless nights digging thru our tutorials.
 
good luck, read, try, start over. read, try, start over. Us people in I.T. dont make good money because we got it right the first time.

---

### Post by Dangertux on 2011-09-29
> **kevinthecomputerguy said:**
> @Hotmonkey
 
Your getting great advice from these other guys.
 
There is my website [http://woodel.com](http://woodel.com)  (mentioned above) that is geared for begin'rs who are wise enough to know GUI is not the way. But its a little old school debian, where these guys are pointing you to new school Ubuntu.
 
Either way, read all of our guides. I see many questions like yours, and they read to me like this...
 
"I want to fix cars, but fixing them is confusing, where is the easy button" Well... if it was easy then... everybody would do it. Your not going to achieve your goals without many sleepless nights digging thru our tutorials.
 
good luck, read, try, start over. read, try, start over. Us people in I.T. dont make good money because we got it right the first time.

You make good money? Lucky... I guess I missed the boat :-P

Honestly, though don't rule out debian tutorials they (most of the time) will work in Ubuntu. Maybe not with everything, but as far as basic things (installing packages, compiling, iptables, starting stopping services, editing config files) most of it will transfer over. So if you find a good debian tutorial don't knock it just realize there may be some minor differences.

Also I can't emphasize enough , alot of guides are written so you can copy and paste through them, try to actually understand what they are doing it will help you in the long run.

---

### Post by kevinthecomputerguy on 2011-09-29
I would marry Debian :- )

*Both are great

---

### Post by hotmonkey on 2011-09-30
Truth be told, as soon as any of you had mentioned a website or reference, I have visited them. Right off,  (kevinthecomputerguy's and Dangertux's) these websites have been very helpful and full of great ways of doing some of the things I didn't know I needed to do. 

If anyone who is reading this and has not visited them and looked around, you may possibly be missing what seems to be some good knowledge. At least from my point of view. 

As for Debian, I was not sure if it was ok to really mention it here in the Ubuntu forum so to speak. Personally, from what little experience I have, I like them both so far. Ubuntu seems a bit easier and friendlier for me to grasp at the moment.  Debian seems to be moving a little fast for me to feel really comfortable (with all the updates and such, I feel I am always falling behind). Once I get better, I am looking forward to trying out several options for the best fit for my needs. For now, Ubuntu feels like a safe place to start. Especially since everyone has been so helpful.

Also a “Thank you” (Jonathan L) for offering an order or sequence in which to learn all of this. I know I am in for a bit of struggle. However, just having a rough outline is making it easier for me to move in the proper direction.

My goal at the moment is not to be any sort of server expert. I just want a website to work as expected and to not get too frustrated by my ignorance and inexperience in the process.

Time to follow some more of the suggested links and keep reading...

Again, Best Regards.

---

### Post by spynappels on 2011-09-30
It might be very helpful in your learning journey to keep the server behind a router and not forward any ports to it from the internet, you can do all your testing and tweaking from inside the LAN  without having to worry too much about attacks from the Net at large. You can then concentrate on getting everything working and understanding how it works, and worry about hardening the system before it goes online properly.

This allows you to learn about such things as key authentication for SSH and turning password authentication off, as well as getting your head around things like apparmor without leaving gaping holes in your security through a configuration mistake while you are learning!

---

### Post by Jonathan L on 2011-09-30
> **hotmonkey said:**
> 
My goal at the moment is not to be any sort of server expert. I just want a website to work as expected and to not get too frustrated by my ignorance and inexperience in the process.


Hi Again Monkey

Glad suggestions are well received.  I edited my previous post to explain the order, and just want to comment about choice of platform.  From your comment ("X moves too fast") I'll just repeat my suggestion that 10.04 LTS server would be a great place for you to start.  Well documented, few remaining important bugs, lots of tutorials etc, and supported until 2015.  From your stated goals, install 10.04 and choose LAMP server (and SSH server) from the install menu and start making web sites!  It's how everybody else learned: wet feet.

Nobody mentioned it here, but a test web server needs practically no resources.  It won't matter at all what you run it on.  If you need dedicated hardware for any reason, I'd recommend something like an old Dell desktop (perhaps a GX150 at £1 on Ebay or if you're feeling rich a GX620 at £50).  I use an Asus nettop because I wanted something quiet and low power as it has to stay on (it's inaudible).  I do think it's a good idea to have a separate computer from your main email/web browsing/whatever computer, and a piece of old junk makes a perfectly good server.  You'll find that the only tricky part with these can be getting it to boot from a USB stick (recommended) or CD-ROM.

I'd also recommend getting good and fast at installing things and not being too precious about your installation.  That way you can make good big mistakes and just wipe them and continue.

So: time to stop reading, turn some old computer into a server and start practising.

Kind regards
Jonathan.

---

