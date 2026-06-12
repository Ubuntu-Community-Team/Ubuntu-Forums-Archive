---
title: "Adobe AIR out of beta for Linux"
date: 2008-12-18
forum: The Cafe
---

### Post by Vadi on 2008-12-18
In case anyone missed it - Adobe AIR 1.5 [is out for Linux]("http://blogs.adobe.com/ashutosh/2008/12/adobe_air_15_for_linux_is_out_1.html"), and is out of beta. It's now able to use the 'install badge' feature properly, so you can just [click on an app]("http://blogs.adobe.com/ashutosh/2008/12/badge_installation_of_air_apps.html") to install it :popcorn:

This is good stuff because this means you have access to even more apps - natively, without wine. Adobe [has a list of them here]("http://www.adobe.com/cfusion/exchange/index.cfm?event=productHome&exc=24&loc=en_us") - but you might stumble upon them in various websites too. For developers, this is one of the easiest ways to make a cross-platform app also - Adobe AIR itself guarantees compatibility wherever it runs. 

(of course, linux/windows/mac have different capabilities - but [air cushions that]("http://www.adobe.com/devnet/air/articles/developing_crossplatform.html") by providing 'feature check' functions. So you don't code for #if linux, but for #if feature)

[SIZE="4"]Download[/SIZE]: [http://get.adobe.com/air/](http://get.adobe.com/air/)

Video of install - if you get stuck. ([http://blip.tv/file/1590875/](http://blip.tv/file/1590875/))

---

### Post by Giant Speck on 2008-12-18
This is good news.  I discovered this a while back and I wasn't sure the project was still active!

Their selection of applications is somewhat... limited, though.  A whole lot of useless Twitter apps in there, too.

---

### Post by Vadi on 2008-12-18
This is esp. good news since adobe laid off 600 people at the beginning of December.

---

### Post by Giant Speck on 2008-12-18
> **Vadi said:**
> This is esp. good news since adobe laid off 600 people at the beginning of December.

:shock:

---

### Post by Hark3n on 2008-12-18
OK, I've downloaded the bin file but "sudo ./AdobeAIRInstaller.bin" returns a command not found error.  What gives?

Update.  Apparently you have to make the bin file executable.  Just run the following command "chmod u+x AdobeAIRInstaller.bin"

---

### Post by jrusso2 on 2008-12-18
I can't even get to the webpage that has the download. It says its for Ubuntu 7.10 though.  Will it work with Hardy?

---

### Post by Soopa on 2008-12-18
I can't get to that page either.. it just times out for me. :-(

---

### Post by Therion on 2008-12-18
Here's the VERY direct DL link (Linux version, duh) if it helps anyone:

[http://get.adobe.com/air/thankyou/](http://get.adobe.com/air/thankyou/)

---

### Post by Soopa on 2008-12-18
That worked.  Thanks, Therion!

---

### Post by Therion on 2008-12-18
> **Soopa said:**
> That worked.  Thanks, Therion!
No prob. 

Helping... It's what I do.  When I'm not pushing elderly women into oncoming traffic of course.

---

### Post by billgoldberg on 2008-12-18
> **Hark3n said:**
> OK, I've downloaded the bin file but "sudo ./AdobeAIRInstaller.bin" returns a command not found error.  What gives?

Update.  Apparently you have to make the bin file executable.  Just run the following command "chmod u+x AdobeAIRInstaller.bin"

Why would you run the installer with root privilages?

That's not a smart thing to do.

--

Damn, it won't install in Arch.

I guess it's time to download Mint 6 and test AA in vbox.

---

### Post by jrusso2 on 2008-12-18
> **Therion said:**
> Here's the VERY direct DL link (Linux version, duh) if it helps anyone:

[http://get.adobe.com/air/thankyou/](http://get.adobe.com/air/thankyou/)

Yes thanks.

---

### Post by Vadi on 2008-12-18
It works for Ubuntu 7.10+

---

### Post by graeme3816 on 2008-12-19
There is a good guide here
[http://blog.wired.com/business/2008/12/adobe-air-for-l.html](http://blog.wired.com/business/2008/12/adobe-air-for-l.html)

Easiest to install Flash first, this is a deb file from the Adobe site.

---

### Post by crc on 2008-12-19
Not sure if there's something wrong with my system's privileges but running ./AdobeAIRInstaller.bin (without the sudo command) installs it in the /opt directory.  Shouldn't it prompt me for a password? Can anyone else confirm this?

---

### Post by Vadi on 2008-12-19
It should prompt you for a password - maybe you gave sudo the password earlier though, in which case it wouldn't.

---

### Post by oldos2er on 2008-12-19
Every time I try to download an app, it tells me to "please install the latest version of the free Adobe flash player." I already have flash 10 installed.

---

### Post by Vadi on 2008-12-19
Puzzling. Well, post here then please: [http://blogs.adobe.com/ashutosh/2008/12/installation_issues_with_air_1.html](http://blogs.adobe.com/ashutosh/2008/12/installation_issues_with_air_1.html)

---

### Post by oldos2er on 2008-12-19
> **Vadi said:**
> Puzzling. Well, post here then please: [http://blogs.adobe.com/ashutosh/2008/12/installation_issues_with_air_1.html](http://blogs.adobe.com/ashutosh/2008/12/installation_issues_with_air_1.html)

 Done.

 EDIT: Well, I take that back, it doesn't look like it's going to be "approved."

---

