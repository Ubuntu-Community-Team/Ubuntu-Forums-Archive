---
title: "How much information can be leak out through a browser ?"
date: 2014-05-07
forum: Security
---

### Post by ubuserone on 2014-05-07
Browsing through some forum post , where I found some user signature able to determine our Ip address location and browser . I trace it and found it's from [http://www.danasoft.com]("http://www.danasoft.com/") . 
I am newly approach to Ubuntu OS and rookies on computer security.

How much more information can be leak out through a browser beside the location and how should we prevent from getting them leak out ? :(

---

### Post by lisati on 2014-05-07
The information about location that can be inferred based on IP address is, at best, only approximate, and has nothing to do with your browser. Contrary to what might be inferred from CSI-type TV shows, you're unlikely to be able to pinpoint someone's exact location based on IP address alone without some kind of subpoena or court order that lets you access an ISP's records. The Danasoft website identifies my location as Auckland, which is inaccurate by about 600km.

---

### Post by buzzingrobot on 2014-05-07
Users of IP addresses, like an ISP, acquire blocks of addresses.  Records of those assignments are open and available.  The typical user gets an IP address assigned (temporarily) via DHCP from an ISP.  It isn't difficult to do a quick lookup to identify the ISP that handed out an address. That can narrow down the location of the user, sometimes a great deal if more info about the ISP 's assignment patterns are available.

---

### Post by LastDino on 2014-05-07
People have already answered your IP question but as to how to avoid leaking info. You can try proxy or Tor browser.

---

### Post by tgalati4 on 2014-05-08
Use noscript to block javascript from running without permission.  Otherwise every website you go to will just start launching scripts--some of which can be malicious.  Use Adblock Edge to block the ads and clean up your browsing experience.

---

### Post by HermanAB on 2014-05-08
To stoke your fears some more, try this: [https://panopticlick.eff.org/](https://panopticlick.eff.org/)

---

### Post by buzzingrobot on 2014-05-08
Browsers relay a considerable amount of data back and forth.  It's how the internet works. (Remember, it was designed to be a publishing medium, not a communications tool.)

Googling something like "What does my browser say about me?" will generate many responses.

---

### Post by BBQdave on 2014-05-09
For the most part, the web is public space. With the expectation that you will be seen :)

---

### Post by thnewguy on 2014-05-09
A web brwoser will leak a lot of intformation, including (but not limited to) your approximate location, your browser name/version, your operating system name/version, a list of websites you have vsited recently, your IP address, possibly items purchased, plugins installed.... Plus anything you type into the browser, your mouse pointer movements. It helps to think of your web browser as a two-way portal. Remote sites can look at just abotu anything you do in the browser while you are looking at remote sites.

---

### Post by ant2ne on 2014-05-09
What makes you think the ISP will require a subpoena? "Your" IP actually blongs to the ISP and the records associated with it as well. They can cooperate with Law enforcement (or anyone) at will.

---

### Post by bashiergui on 2014-05-10
> **ubuserone said:**
> Browsing through some forum post , where I found some user signature able to determine our Ip address location and browser . I trace it and found it's from [http://www.danasoft.com]("http://www.danasoft.com/") . 
I am newly approach to Ubuntu OS and rookies on computer security.

How much more information can be leak out through a browser beside the location and how should we prevent from getting them leak out ? :(
Fundamental misunderstanding: an IP is not supposed to be secret. It can't be secret because that's how your computer talks to the rest of the world and how the rest of the world finds you to respond. If you make your IP secret then you will never get any web server to give you web pages you request.

Your IP could be used to track you personally, so as others suggested use Tor to hide your own IP behind another anonymous one.

Your browser announces to every web site details about the browser so that the server will give you pages that your browser can render. Again, that information has to be shared for the Internet to work. Read more about that here [http://en.m.wikipedia.org/wiki/User_agent](http://en.m.wikipedia.org/wiki/User_agent)

As others suggested you can use privacy extensions in your browser to minimize information leakage: block javascripts, adblocker, inprivate browsing, etc.

---

### Post by EnglishElectricAndy on 2014-05-10
Depends on what people might be afraid of 'leaking'.

The Internet is not like a phone network, where (theoretically at least) the law enforcement agencies are required to go through processes to obtain details of communications.

The legal ramifications of the Intenet are still developing, some might say faster than the legislators are able to keep up with .

---

### Post by alan26 on 2014-05-13
The case law with the internet is barely going to be able to keep up. By the time they get a prosecution and pass through criminal court it's going to be a year outdated or more. That means that just about every trial is on it's own to decide the fate of a defendant.

Also, the people making the laws don't know much more about a computer other than turning it on ... so laws are anecdotal at best.

---

### Post by WogBoy on 2014-05-14
Found this not long ago, Find out what your browser discloses.
> **System Scanner** is an web application that will show you  what information is available through a browser about your system,  including hardware and software, IP-address, broadband speed, security  problems (if any), geolocation and much, much more.      There are  desktop and mobile versions
[http://system-scanner.net/](http://system-scanner.net/)

---

### Post by ubuserone on 2014-05-21
> **lisati said:**
> The information about location that can be inferred based on IP address is, at best, only approximate, and has nothing to do with your browser. Contrary to what might be inferred from CSI-type TV shows, you're unlikely to be able to pinpoint someone's exact location based on IP address alone without some kind of subpoena or court order that lets you access an ISP's records. The Danasoft website identifies my location as Auckland, which is inaccurate by about 600km.
 Thanks for the details explanation lisati  :razz: .Sorry for being new to security section which took your time to help me out.Thanks again  :eek:
 
> **buzzingrobot said:**
> Users of IP addresses, like an ISP, acquire blocks of addresses. Records of those assignments are open and available. The typical user gets an IP address assigned (temporarily) via DHCP from an ISP. It isn't difficult to do a quick lookup to identify the ISP that handed out an address. That can narrow down the location of the user, sometimes a great deal if more info about the ISP 's assignment patterns are available.
 My actual reason is to avoid a few website detecting and identifies my location , but under a details of investigation through a browser information , will they able to detect the particular person ?
For an instant , 
[http://ubuntuforums.org](http://ubuntuforums.org) ? how much info does it request from our pc ?
 > **LastDino said:**
> People have already answered your IP question but as to how to avoid leaking info. You can try proxy or Tor browser.
Thanks for the suggestion :)

> **tgalati4 said:**
> Use noscript to block javascript from running without permission. Otherwise every website you go to will just start launching scripts--some of which can be malicious. Use Adblock Edge to block the ads and clean up your browsing experience.
Without noscript , I can't possible to access a certain forum features.

> **HermanAB said:**
> To stoke your fears some more, try this: [https://panopticlick.eff.org/](https://panopticlick.eff.org/)
[http://ubuntuforums.org](http://ubuntuforums.org) doesn't prompt installing any web browser plugin

> **buzzingrobot said:**
> Browsers relay a considerable amount of data back and forth. It's how the internet works. (Remember, it was designed to be a publishing medium, not a communications tool.)

Googling something like "What does my browser say about me?" will generate many responses.
Basically , it only detect browser information.

> **BBQdave said:**
> For the most part, the web is public space. With the expectation that you will be seen :smile:
How much can they see ? :(

> **thnewguy said:**
> A web brwoser will leak a lot of intformation, including (but not limited to) your approximate location, your browser name/version, your operating system name/version, a list of websites you have vsited recently, your IP address, possibly items purchased, plugins installed.... Plus anything you type into the browser, your mouse pointer movements. It helps to think of your web browser as a two-way portal. Remote sites can look at just abotu anything you do in the browser while you are looking at remote sites.
Do you have any exmaple on how they actually track our keywords , mouse pointer movements and website that had recently visited ?


> **bashiergui said:**
> Fundamental misunderstanding: an IP is not supposed to be secret. It can't be secret because that's how your computer talks to the rest of the world and how the rest of the world finds you to respond. If you make your IP secret then you will never get any web server to give you web pages you request.

Your IP could be used to track you personally, so as others suggested use Tor to hide your own IP behind another anonymous one.

Your browser announces to every web site details about the browser so that the server will give you pages that your browser can render. Again, that information has to be shared for the Internet to work. Read more about that here [http://en.m.wikipedia.org/wiki/User_agent](http://en.m.wikipedia.org/wiki/User_agent)

As others suggested you can use privacy extensions in your browser to minimize information leakage: block javascripts, adblocker, inprivate browsing, etc.
Would you suggest me an application to modified browser announced details ? such as user agent switch ?

> **EnglishElectricAndy said:**
> Depends on what people might be afraid of 'leaking'.

The Internet is not like a phone network, where (theoretically at least) the law enforcement agencies are required to go through processes to obtain details of communications.

The legal ramifications of the Intenet are still developing, some might say faster than the legislators are able to keep up with .
> **alan26 said:**
> The case law with the internet is barely going to be able to keep up. By the time they get a prosecution and pass through criminal court it's going to be a year outdated or more. That means that just about every trial is on it's own to decide the fate of a defendant.

Also, the people making the laws don't know much more about a computer other than turning it on ... so laws are anecdotal at best.
Putting aside,  internet law is still far ahead rather i'd concern more on security part to minimize the information announced by the browser.As blocking specific scripting to less down information passing out to a certain sites.

Back on track , how to determine what and which information was leak out through a browser in a script ? A non-script addon apparently only block a certain script but didn't specifically tells us what does the blocked script does.
Main concern , leaking out MAC address , pc component monitor model ,processor, driver version and other varies .

---

### Post by bashiergui on 2014-05-21
> My actual reason is to avoid a few website detecting and identifies my location , but under a details of investigation through a browser information , will they able to detect the particular person ?Yes, partly through browser information and partly as you're connected to a web server. If you need to be anonymous then use Tor. 
> Back on track , how to determine what and which information was leak out through a browser in a script ? A non-script addon apparently only block a certain script but didn't specifically tells us what does the blocked script does.For that you would have to review the javascript code. If you don't code then the best you can do is google each script and hope someone wrote an explanation. But the amount leaked depends also on what information is stored at any given moment in the browser. If you have been surfing all day and logging in to lots of sites then your browser contains a ton of information. If you just opened the browser after clearing the history, cookies, saved passwords, etc then there isn't much information in your browser.

But really, why do you care what it did if you blocked it.
> Would you suggest me an application to modified browser announced details ? such as user agent switch ?You don't need an app to change the user agent. It can be done directly in each browser. There are tutorials on the internet.

However, you still do not have a basic understanding of maximizing privacy. If you're going to use Tor then you don't want to change the user agent. When you look like every other Tor browser you're indistinguishable as an individual. 
> Main concern , leaking out MAC address , pc component monitor model ,processor, driver version and other varies .Your MAC address gets sent to the first hop between you and the server, which is probably your router. Then the router replaces your MAC with its own and sends it to the next hop. That continues so that the web server will see the mac address of the last router in front of it.

---

