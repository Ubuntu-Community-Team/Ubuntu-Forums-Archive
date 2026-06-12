---
title: "Integrating user login"
date: 2009-02-03
forum: Server Platforms
---

### Post by bluethundr on 2009-02-03
Hi guys,

 I have a website where all the individual components are working flawlessly. 

 The site consists of twiki, laconica, roundcube, mailman and phpBB3. Also with the brilliant help of you guys I was able to setup subdomains in apache and have postfix functioning with a mysql back end. The help I get from you guys is simply invaluable.
 
 So here's my question. All these elements to my site are great, and add a lot of power and functionality to it. But each element has a discrete login, and each page looks like you are going to a completely different site.

 Is there any way, to have the user login to, say, a landing page that would automatically log the user in to all elements of the site? That is, a login to the landing page would gain you access to the twiki, roundcube webmail, phpBB3 and whatever other element I might choose to add in the future?

 I have hired a web designer to integrate the user experience for me, in terms of how everything will _look_. I want everything to have more or less the same interface. She can do that for me. 

 Right now, the main interface is the twiki. But with the help of the web designer, I am going to move the focus of the website away from the twiki to a landing page to higlight the other elements to the site, which are just as good in my opinion.

 I _think_ the twiki can gain it's login information from ldap. I'm sure MySQl would have to come into play in some fashion. Not too sure about the other elements or how this might be achieved. Any advice for my ambitious goal?

 Also, one other thing. I notice that roundcube seems to lack some features that I consider really essential. It's a great web interface, but there is 1) no automatic user registration for new accounts 2) no change password and 3) no forgot password option. In my book, this is absolute FAIL! How could the developers of this otherwise great app forget these essential features? 

 Are there any other webmail interfaces that have these features? Maybe squirrelmail or horde or some other package I have yet to learn about?

[center]One login to rule them all, One login to find them,
One login to bring them all and in the darkness bind them
In the Land of Mordor where the Shadows lie.[/center]:popcorn:

---

