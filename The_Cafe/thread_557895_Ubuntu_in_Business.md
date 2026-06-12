---
title: "Ubuntu in Business"
date: 2007-09-23
forum: The Cafe
---

### Post by Black Mage on 2007-09-23
I love Ubuntu and want to install it in my office at work, but my supervisors love windows and hate change. So I've been preparing a presentation to show them how well Ubuntu works and why they should invest in it. I currently have:

1. Cost
Ubuntu is a lot cheaper than windows because its free. Instead paying a license each computer I install it on, I could be installing a free and powerful. Btw, my supervisors love the word free. This so far is my biggest arguement

2. Windows Application Support
If a windows application is needed, it can be support by using Wine or VMware. Also the new release of Ubunutu JeOS should have support for apps in other OS.

3. Other Business have already switched
This is where I've done most my research and come up with the least results. Currently Amazon and The French National Assembly have both switched to using Linux, the French National Assembly is currently using Ubuntu.

4. Powerful and Secure Sever
Ubuntu can save money by putting it on almost any machine so the current business machines do not neet to be upgraded for Vista(saves mone). Also Ubuntu OS is more secure than Windows and much harder to get a virus.

5. Contains the Basics for Free
OpenOffice is just about as powerful as Microsft Office and for free. I'm planning to do my presentation in OpenOffice.

6. Easy to Manage
I can easily manage other users computer on a network just by using secure shell.

So these are the arguements in a nutshell of what I'm planning on presenting to my supervisors. But I still feel like I'm missing important key points so thats why I'm asking here, why would the switch to Ubuntu be a good idea? And to show as examples, what other business use Ubuntu? And that one is key, they like to see it be succesful with other business first before they try it. But finding other business that use Ubuntu is difficult so if anyone has any info on other business that use Ubuntu, that would be much appreciated.

---

### Post by n3tfury on 2007-09-23
take a look at elvis's post here:

[http://ubuntuforums.org/showthread.php?t=557812](http://ubuntuforums.org/showthread.php?t=557812)

he goes into great detail.  excellent post.

---

### Post by PilotJLR on 2007-09-23
-Since you've already bought Windows licenses, what is the business justification for trashing that and using Ubuntu?
-What about re-training people and/or loss due to a drop in productivity while people learn how to use everything?
-Why not just use OpenOffice on Windows?
-Wine is simply not a business solution... I use it too, but don't trust it for serious apps. VMware requires a whole new set of Windows licenses, which will increase costs!

So other than security and shell management, what is the business selling point???


btw, I prefer Linux (be it Ubuntu, fedora, rhel, etc) over Windows in most cases as well. Linux is an easy sell for servers, but more difficult for existing desktops. If the decision makers don't perceive a problem, then they won't see why they should change.

---

### Post by n3tfury on 2007-09-23
support would be an issue in a bigger environment.

---

### Post by Black Mage on 2007-09-23
> **PilotJLR said:**
> -Since you've already bought Windows licenses, what is the business justification for trashing that and using Ubuntu?
-What about re-training people and/or loss due to a drop in productivity while people learn how to use everything?
-Why not just use OpenOffice on Windows?
-Wine is simply not a business solution... I use it too, but don't trust it for serious apps. VMware requires a whole new set of Windows licenses, which will increase costs!


Right now the whole office uses XP, and Vista would be the next upgrade.I would have to buy a license for each computer I put vista on. Vista would also be costly because the company would either have to buy new computer or upgrade the RAM and graphic cards in the current ones.

And with the VMware, I was thinking of having a server completed dedicated to running VMware with a version of windows, with simultaneous user logins. So Windows won't have to be be bought for each computer in the office.

> **PilotJLR said:**
> -
support would be an issue in a bigger environment.
'

The company I work for has about 100 employees, 1/10 of the amount of the computer in which the French National Assembly had Ubuntu installed onto. So  I'm not worried about a huge enviroment, but a good question would be how large an enviroment Ubuntu can support.

---

### Post by JAPrufrock on 2007-09-23
Just found an interesting article called ["Can Ubuntu Linux really run my small business?"]("http://www.allbusiness.com/technology/4353657-1.html")

One of the authors conclusions is that the Ubuntu community saves him money because it provides IT support.  "What is so great about Ubuntu? 'It has the best user community built around it.'"

I also agree with the author that Ubuntu's biggest shortcoming is that it lacks a good accounting program like Quickbooks.

---

### Post by DarkOx on 2007-09-23
Honestly, I'd say the main problem with your presentation is a lack of specifics. You need to look at your own company first, and then at external ones to get an idea of how to implement Ubuntu. For example, the point "contains the basics for free" -- does your company need just the basics? Do you have finance guys that require more advanced features in Excel, or accountants with specialized software, or web designers who need Adobe (and so on)?

You need to think about the people in your company, and map out their specific computing needs. Then, think about whether or not Ubuntu can fill those needs. A survey might be useful here (but don't just ask "do you use a spreadsheet program?" OOo Calc is a great program, but if you're trying to do optimization with it, it can't substitute for an Excel spreadsheet).

Once you know Ubuntu (maybe combined with VMware for some windows-only programs) can match your needs at a reduced cost, both up front and from a maintenance perspective, then I'd look at other companies. Use their examples to further bolster your argument, and to get an idea of how an Ubuntu network can be set up at your company.

---

### Post by dasunst3r on 2007-09-23
If your computers are running just fine with Windows XP, then I see no reason to propose switching to Ubuntu unless you are on some lock-in scheme like Software Assurance, and that is about to expire.  In any case, I would ride it out until the year before support for Windows XP ends.  Here's how I would go about the transition to ease the employees into Linux and open-source:

[list]
[*]2 years before support ends: Start replacing programs with their open-source equivalents (e.g. IE with Firefox, Office XP with OpenOffice)
[*]1 year before support ends: Make the proposal.  Remark: Give your bosses two cases (getting Vista and upgrading where needed or getting Ubuntu and leveraging the current hardware you have now) and compare the costs associated with each one.
[/list]

I have attached an outline I did for a class in college called "Engineering Communications."  Hope you find that helpful.

---

### Post by PilotJLR on 2007-09-23
> **Black Mage said:**
> Right now the whole office uses XP, and Vista would be the next upgrade.I would have to buy a license for each computer I put vista on. Vista would also be costly because the company would either have to buy new computer or upgrade the RAM and graphic cards in the current ones.

And with the VMware, I was thinking of having a server completed dedicated to running VMware with a version of windows, with simultaneous user logins. So Windows won't have to be be bought for each computer in the office.


Why do you feel you MUST upgrade to Vista? XP will supported for several more years. This argument just doesn't hold water.

For simultaneous logins, you would need a license for Server 2003 + a Terminal Services CAL for each user. If you don't know about TS CAL's, then please research this, as it's a significant expense a lot of people don't plan for until their whole terminal services environment kills itself.


I'm not trying to shoot down your idea... but I've worked as a Sales Engineer before, so I know what the decision makers want to hear. You have not sold me on this one.

---

### Post by koenn on 2007-09-23
> **DarkOx said:**
> Honestly, I'd say the main problem with your presentation is a lack of specifics. 
I agree.
To give yet another exmple : "4. Powerfull and secure server" ) that may be all good and well but what your audience is (or should be) interested in is : can that Ubuntu server offer its clients the same functionality our current servers do. I can't be the judge of that as I don't know your office, but some hurdles might be : Active Directory features your current environment relies on ? File sharing with elaborate user and group permissions ? Printer serving/sharing for possibly linux-incompatible printers ? Microsoft Exchange ? MS-SQL database ? ...

If you have a plan for all that, the next thing they'll want to know is : what is that migration going to cost ? Ubuntu is free beer, but migrations cost money. Can you prove that the costs of the migration  are less than the costs of sticking with windows ? 


As for your sollution to use VMware ore some other virtualisation to offer Windows compatibility : Have a real good look at the Windows EULA's. While you might avoid the cost of a license for the OS on your desktop PC's, you'll still need  CAL's for any client accessing your server, and if that server needs to provide sessions for multiple users ("simultaneous user logins"), you might be looking at Terminal Services licenses as well - I'm not too sure you can pull this of with virtualisation alone.

---

### Post by Wharf Rat on 2007-09-23
Black Mage,
I admire your attempt at this. But, beware some of the items you noted can be incredibly difficult to overcome. DO NOT underestimate ANY of these obstacles.

> **Black Mage said:**
> I love Ubuntu and want to install it in my office at work, but my supervisors love windows and hate change. 

This is a very delicate dynamic. If your supervisor has to answer to an executive, be VERY careful here.  You could be looking for a new job.

> **Black Mage said:**
> 
1. Cost
Ubuntu is a lot cheaper than windows because its free. Instead paying a license each computer I install it on, I could be installing a free and powerful. Btw, my supervisors love the word free.

Always a good selling point. But, most companies are willing to pay for a product if it is perceived to fulfill their needs. In short "throw money at the problem."
  


> **Black Mage said:**
> 
2. Windows Application Support
If a windows application is needed, it can be support by using Wine or VMware. Also the new release of Ubunutu JeOS should have support for apps in other OS.

I think is is weak or bad selling point. Yes it is true, but the boss doesn't want  to hear " I have a better mouse trap, and you put the old mouse trap inside."  
I would only use this argument IF there is a particular legacy app that cannot be replaced by a Linux version.


> **Black Mage said:**
> 
3. Other Business have already switched
This is where I've done most my research and come up with the least results. Currently Amazon and The French National Assembly have both switched to using Linux, the French National Assembly is currently using Ubuntu.

Again, bad comparison. These are only two organizations.  I would not make a fundamental business change just because a couple of other people in the world are doing it.



> **Black Mage said:**
> 
4. Powerful and Secure Sever
Ubuntu can save money by putting it on almost any machine so the current business machines do not neet to be upgraded for Vista(saves mone). Also Ubuntu OS is more secure than Windows and much harder to get a virus.

OK, you have a strong selling point here.  Vista will cost on several levels: initial OS license, increased hardware needs, additional application software upgrades, employee retraining AND  **MAINTENANCE**.  Get some valid figures together and do a cost comparison to installing linux (Ubuntu or any distro you like).  Personally, I would use Ubuntu and the Gnome  interface. It isn't cute but it sure is easy to navigate.  You might choose another format depending on your user base.
Be sure to include the added life of existing hardware. And, if you needed a Windows app you might use VMware and one of your existing licenses (from previous point).

Additionally, you mentioned "server"  -- a whole different animal than desktop.  Look at implementing a linux server.  I very much support linux as a server platform.  I have used one since 1998 albeit a commercial package.  Here, I highly recommend a commercial product as opposed to "roll your own" unless you a skilled linux technician and reseller of PC's and computer services.  It is jut too easy to overlook something critical on a server.  Look at Nitix they offer a package that is great for any small business. To borrow from Ubuntu "It just works."


> **Black Mage said:**
> 
5. Contains the Basics for Free
OpenOffice is just about as powerful as Microsft Office and for free. I'm planning to do my presentation in OpenOffice.

Sounds good.

> **Black Mage said:**
> 
6. Easy to Manage
I can easily manage other users computer on a network just by using secure shell.

Ok. I have to ask. Are you part of the IT/support staff? If so, good.  If not, you need to be prepared to demonstrate your knowledge and skill in this area. And then, be prepared to take on a new job.



>  I'm asking here, why would the switch to Ubuntu be a good idea? And to show as examples, what other business use Ubuntu? And that one is key, they like to see it be succesful with other business first before they try it. But finding other business that use Ubuntu is difficult so if anyone has any info on other business that use Ubuntu, that would be much appreciated.

I hope you don't take any of my comments in  a negative tone. If there is such a thing as "constructive criticism" I am trying to offer it here.

I am a partner in a small/medium business. I AM the IT support along with ten other jobs.  I have the power to make a switch to Linux -- I personally don't think the time is right for my business.  But, I am strongly watching and learning. If tomorrow, I had to decide between - move to Vista, or something else.  That "something else" would likely be Ubuntu.

---

### Post by Black Mage on 2007-09-23
No, I appreciate the comments and do not take them in negative tone. I also take them as possible questions I will be asked when presenting a possible switch too Linux.

My main focus is to present how switching Linux can save money. What I really want this point is to find out which other companies have switched to Ubuntu and how it affected them, which results have been limited. I bring up topics such as 'Support for Windows' because issues like those are likely to come up. I'm trying to get all the loop holes before I decide to present it.

And remeber that this is a nutshell of what I'm going to say without being too specific. If I posted 10 pages on a forum, I doubt many people would read it fully.
But I really to appreciate the constructive critiscm though.

---

### Post by Swarms on 2007-09-23
Remember to post the outcome, very interesting!

---

### Post by Kingsley on 2007-09-23
You should probably check out a book titled The Business and Economics of Linux and Open Source.

---

### Post by Black Mage on 2007-09-23
Are there any known businesses today that use Ubuntu? Besides the French National and Assemby and Chris Dawson, founder of Box Populi.

---

