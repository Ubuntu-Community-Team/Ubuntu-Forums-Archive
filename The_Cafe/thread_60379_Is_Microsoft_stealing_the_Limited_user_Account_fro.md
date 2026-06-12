---
title: "Is Microsoft stealing the Limited user Account from Linux?"
date: 2005-08-27
forum: The Cafe
---

### Post by mstlyevil on 2005-08-27
I was readinfg an article at pc world.com and come across a quote about a new feature in windows vista.
> Conscious of the security and reliability concerns that have plagued previous Windows releases, Microsoft is trying hard to overcome people's resistance to upgrading by proving that with Vista, things have changed. Based on my experience with Beta 1, the results of that effort remain to be seen. The most striking security innovation is the new Limited User account: A Limited User cannot install applications, but can perform routine tasks such as installing a new printer driver. 

  Ubuntu alredy has this feature with the Root/User accounts already seperated for security reasons. Is Microsoft actually looking to Open source software for Ideas on how to bring more security to Windows? What is your opinion.

---

### Post by rattaro on 2005-08-27
This is interesting.  I wonder how installing drivers from a limited user account is possible.  It may be that this act is done automatically through Administrator, but I'm not sure if that makes any more of a secure system.  This may be more like The Hurd, where drivers are in user space, not kernel space.  Who knows until it arrives, but this sounds a little more advanced compared to GNU/Linux.  I really wish installing new drivers was easier.

---

### Post by DJ_Max on 2005-08-27
Microsoft isn't completely stupid, they know what UNIX in general has that can be benfical to them. If you read M$ website more you'll see more features Vista is supposed to have, some which are similar to what UNIX is based on.

---

### Post by jdong on 2005-08-27
Well, that seems to line up with the "Power Users" Window concept. It also relates to belonging to some system groups under UNIX (wheel, operator, staff, etc), as well as being given high access levels via finer-grained security (SELinux, Secure  BSD, etc).

I wouldn't necessarily say it's "stealing" this from Linux... The idea of reduced priviledge isn't that much of a surprise, it's just that Vista is providing a new preconfiguration of kernel rights.


I wouldn't call this "secure" by any means... I've broken into XP systems with specially crafted "printer drivers" and "USB flash drives" ;)... Installing drivers most certainly **IS** a dangerous action.

---

### Post by Galoot on 2005-08-27
Stealing from open source software. Heh. Good one.

---

### Post by rolfotto on 2005-08-27
More like borrow.  Remember that Linux was made as a Unix clone and this basic feature existed before Linux - let alone Ubuntu.

But, yes, Microsoft is indeed looking in the OS world - and has hired OS developers as well.    One prominent example is Daniel Robbins from Gentoo:
[http://news.com.com/Gentoo+Linux+founder+to+educate+Microsoft/2100-7344_3-5749482.html](http://news.com.com/Gentoo+Linux+founder+to+educate+Microsoft/2100-7344_3-5749482.html)

They also operate an Open Source lab.

---

### Post by xequence on 2005-08-27
I do believe they had the limited user account in windows xp along with administrator but apparently it was a huge faliure and everyone used administrator instead...

---

### Post by arcanistherogue on 2005-08-27
Yeah, I saw a screenshot with something like this.  It had a popup saying "The requested action requires administrative privileges" and had a password box for hte admin.

---

### Post by mstlyevil on 2005-08-27
Limited user acct in XP would not let you use most of your apps and would most definately not let you install drivers. Furthermore it is not enabled by defalt. Vista on the other hand will have these features enabled by default. Steal is a strong term but I thought it was only fair to use terminology that Microsoft and Metallica are familiar with.

---

### Post by Brunellus on 2005-08-27
[QUOTE=mstlyevil]Limited user acct in XP would not let you use most of your apps and would most definately not let you install drivers. Furthermore it is not enabled by defalt. Vista on the other hand will have these features enabled by default. Steal is a strong term but I thought it was only fair to use terminology that Microsoft and Metallica are familiar with.[/QUOTE]
 surely we should be welcoming this as a large organization finally deciding to get *something* right?


I mean, really.  if you want to get upset about something, how about the lock stock and barrel appropriation of *BSD's TCP stack?  But since that was consistent with the terms of that license, that's not a big deal either.

What I would be concerned about is if Microsoft used something that was GPL, and subsequently tried to close it to outside development.

---

### Post by Lovechild on 2005-08-27
Windows XP actually has limited user account support as well, but every person I know uses the administrator setting because they hate having to switch users to perform sysadmin tasks. Windows's way of handling this isn't as elegant as just popping up a dialog asking for the correct password, I'm to understand you have to logout and login as the administrator account.

So if they continue this idiotic behavior, I bet you nobody will use this limited account stuff.

---

### Post by Kvark on 2005-08-27
All other OSes also has this basic security feature, Ubuntu wasn't first with it and it's only common sence to require special access for administrative tasks. To say that Micrsoft "steals" this from Ubuntu is like saying Fiat steals from Volvo by putting four wheels on their cars. Everyone else also puts four wheels on their cars, Volvo wasn't first with it and it's only common sence to put a wheel in each corner.

Besides, you can't steal an idea. If I take your car then you have to walk, thus I have wrongfully deprived you of your property, in other words stolen from you. But if I see that you have a car alarm, realize thats a good idea and install an alarm in my car too. Then you are not missing anything, you still have your security alarm, thus I have not stolen anything from you.



But there is one thing that is interesting here. And that is that Windows gets this very basic security feature many years after everyone else. Just like Internet Explorer was way after everyone else with tabbed browsing. And there are many other features that Microsoft are painfully slow to pick up. They need some competition biting 'em in the rear to make 'em pick up the pace.

---

### Post by mstlyevil on 2005-08-27
[QUOTE=Kvark]All other OSes also has this basic security feature, Ubuntu wasn't first with it and it's only common sence to require special access for administrative tasks. To say that Micrsoft "steals" this from Ubuntu is like saying Fiat steals from Volvo by putting four wheels on their cars. Everyone else also puts four wheels on their cars, Volvo wasn't first with it and it's only common sence to put a wheel in each corner.
.[/QUOTE]
 
  I was actually being sarcastic in using the word "stealing".  It is just funny that the one corporation that is so worried about any innovative Idea from thier software are more than willing to borrow from others.  Linus Torvaldis does not require us all to use a activation key to validate Linux nor does he require that we validate the authinticity of the software to recieve updates.  So stealing was a shot at good ol William Gates.

---

### Post by wmcbrine on 2005-08-27
I actually use a limited account under Windows XP. It works for almost everything. The difficulties are overrated -- it's only badly-written software that fails without frivilous access to administrator privileges. (Granted, that happens even less often in Linux. Never, in fact.) And when I do need to admin, often I can use the "Run as..." feature (from the context menu) rather than logging in and out. (Granted, this also works better in Linux, particularly Ubuntu.)

Limited Windows accounts are actually pretty commonly used in business environments. I'm the only person I know who uses one at home, though. :)

I started using it after I posted a message on DSLReports saying almost the same thing as others here: that it was too much of a hassle. As soon as I'd posted it, I thought "Wait, is that really true?". I'd had experience with limited accounts, but only on other people's computers. I hadn't really tried it out for myself. So I created a new admin account, demoted my regular account, and have been happy with it ever since.

---

### Post by mstlyevil on 2005-08-27
> Over the past 18 months, the company has set up an Open Source/Linux lab, run by Bill Hilf, Microsoft's director of platform technology strategy, on its Redmond, Washington, campus to test Linux and other open-source software. In the lab, proprietary Microsoft software is deployed alongside Linux and other open-source technologies to ensure better interoperability among them, Hilf said in an interview earlier this week.      Found this in an article at pc world .com

This is proof open source is being used by Microsoft to help taylor its offerings.

---

