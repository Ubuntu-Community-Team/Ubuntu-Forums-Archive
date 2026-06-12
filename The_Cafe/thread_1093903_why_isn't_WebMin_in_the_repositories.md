---
title: "why isn't WebMin in the repositories?"
date: 2009-03-12
forum: The Cafe
---

### Post by pbpersson on 2009-03-12
When I discovered WebMin it totally changed my view of Linux - suddenly a whole new world opened up to me and I could configure things I didn't even know existed before.

Why isn't it included in the repositories?  It isn't as though it was just released this year, I remember using it years ago on Mandrake.  What's up with that?  :o

---

### Post by v8YKxgHe on 2009-03-12
Due to packaging issues IIRC, their packages were quite insecure and badly built. This was quite a few years ago now, so I don't know if this reflects their quality of packages now, though. This was on a mailing list for Debian quite some time ago (and so Ubuntu doesn't have it now either)

Personally, I'd say stay away from any web-based GUI to do your server work, you'll get a much better understanding of how things work without it.

---

### Post by sonicb00m on 2009-03-12
> **AlexC_ said:**
> Due to packaging issues IIRC, their packages were quite insecure and badly built. This was quite a few years ago now, so I don't know if this reflects their quality of packages now, though. This was on a mailing list for Debian quite some time ago (and so Ubuntu doesn't have it now either)

Personally, I'd say stay away from any web-based GUI to do your server work, you'll get a much better understanding of how things work without it.

I agree and disagree with that.

I think they are fine in the start but it's best to move on from them. But they are also convenient. The good thing about GUIS is that you can discover things you never even thought of looking for. It's also possible to blindly configure things accidentally and get them working.

With good old command line and config files (particularly in the cases of having to add your own switches, small scripts etc) there's no hope in hell of learning much from then if you don't know what to look for the in the first place. I've set up lots of debian servers over the years with the help of the howtoforge pdfs but i couldn't configure postfix and what not without referencing them all the time !

---

### Post by sujoy on 2009-03-12
webmin just confused me so much back when i tried it ...

---

### Post by igknighted on 2009-03-12
I think it would be included if someone packaged it properly and submitted it.  There is an equivalent that does come with Ubuntu, I forget what it is called though.

---

### Post by jethro10 on 2009-03-12
> **sujoy said:**
> webmin just confused me so much back when i tried it ...

Quite off topic and pointless, can you help on the actual problem? I also would like to know.

Thanks

---

### Post by JohnFH on 2009-03-12
I have the same question as well.  However I just added the webmin repository to the sources list.  It would be better to have it in the Ubuntu repositories directly though.

---

### Post by pbpersson on 2009-03-12
> **AlexC_ said:**
> 

Personally, I'd say stay away from any web-based GUI to do your server work, you'll get a much better understanding of how things work without it.

I am unfortunately to some degree one of those people who expect to sit down at the computer and actually do work - in this case be able to share files in Samba.  I did not want to spend days learning about configuration files and how they worked, I wanted to set it and forget it.  Back in my Mandrake days I almost gave up on Linux as "too much work" until I discovered WebMin.

My philosophy is that life is too short to spend days configuring something that should only take a few minutes.  Yes, I might learn some things by using the config files......but once I get it working will I remember what I learned a year from now?  I am thinking no.  ;)

---

### Post by darksideforge on 2009-03-12
> **JohnFH said:**
> I have the same question as well.  However I just added the webmin repository to the sources list.  It would be better to have it in the Ubuntu repositories directly though.


How do I find / get to the webmin repository?

---

### Post by JohnFH on 2009-03-12
> **darksideforge said:**
> How do I find / get to the webmin repository?

See the section half-way down this page titled "Using the Webmin APT repository":
[http://webmin.com/deb.html]("http://webmin.com/deb.html")

---

### Post by Dr Small on 2009-03-12
> **AlexC_ said:**
> Personally, I'd say stay away from any web-based GUI to do your server work, you'll get a much better understanding of how things work without it.

I agree. I have Webmin installed and never *ever* use it.

---

### Post by JohnFH on 2009-03-12
> **AlexC_ said:**
> Personally, I'd say stay away from any web-based GUI to do your server work, you'll get a much better understanding of how things work without it.

I definitely do not agree.  I was able to configure apache quickly to get it to do what I want without having to learn the syntax of .htaccess files (or whatever), and trawling throught the main configuration file.  The only situation where I would say you shouldn't use webmin is if you are learning linux system administration for your job or a course.

---

### Post by smartboyathome on 2009-03-12
I'd rather use SSH to configure my server. Unless you use HTTPS, how do you know that someone isn't listening in on what you send to webmin?

---

### Post by v8YKxgHe on 2009-03-12
removed

---

### Post by pbpersson on 2009-03-13
I was using WebMin to setup Samba server back in 2005

What is available now that is far better?

---

### Post by kwpowers on 2009-06-06
> **AlexC_ said:**
> You say you don't agree with, however my statement was that you'll learn more by not using Webmin, of which you agree with, and not with the speed at which tasks can be completed. ;) You'll also see that I started with 'Personally', which is an opinion. If you find that web-based server GUIs work for you and you learn from them, then great, go nuts.

Yes, there are certain tasks that a web-based server GUI can be quicker at, though you'll know nothing about what changed, why it was changed, or what it affects. It's a set and forget.

By using Webmin and Webmin only, you'll be 100% stuck when you get to a situation when you can't use it. 



Why are you wanting to use Webmin to setup Samba? There are far better tools to do that.


I discovered Linux back in the late 80s and started getting serious with it back when Red Hat went version 7.  Personally I do not advocate one tool over any other but there are good reasons to use whatever tool is a personal preference.  That is what makes Linux so great.  

For years I stuck with RH because it used gnome desktop but I preferred the KDE file browser because you could have tabs.  I changed to Ubuntu when Novel bought SuSe.  I got tired of RPM nightmares.
 
I still use SWAT to set up shares because it just plain works.  I use Webmin to edit my fstab file because it assures my syntax is correct and the machine does not break the next time I boot.  recovering a broken linux boot is a real nightmare.

You say there are better tools please when you make that kind of statement share the names of the tools for other's enrichment.

PS Webmin's default install seems pretty secure to me.  1 you need to give root a known password. 2 it uses https protocol. and 3 you need physical access since it will only respond to localhost unless you configure it to do otherwise.

---

### Post by kwpowers on 2009-06-06
> **pbpersson said:**
> When I discovered WebMin it totally changed my view of Linux - suddenly a whole new world opened up to me and I could configure things I didn't even know existed before.

Why isn't it included in the repositories?  It isn't as though it was just released this year, I remember using it years ago on Mandrake.  What's up with that?  :o

I was also disappointed to see Ubuntu abandon a project that has given so much to the Linux community.  Not all is lost you can go to to the Webmin site and download the debian installer.  after downloading accept the default program gdebi-gtk when you open it.  It will download and install the required dependencies and you will have Webmin on your computer up and running on the default port.

---

### Post by iponeverything on 2009-06-07
> **AlexC_ said:**
> 
Personally, I'd say stay away from any web-based GUI to do your server work, you'll get a much better understanding of how things work without it.

I also disagree with this somewhat -- I know and understand Linux server configuration, but I don't think that should be a requirement for someone that just wants to setup apache, DHCP, samba or some other basic service on their home server. 

If the server is going to be publicly accessible, then I believe there is a responsibility to know and understand how things work. Misconfiguration on publicly available server can affect a lot of other people. (open relay's etc.)

---

### Post by juancarlospaco on 2009-06-07
> **smartboyathome said:**
> Unless you use HTTPS, how do you know that someone isn't listening in on what you send to webmin?

Webmin IS http**S**  :D

---

### Post by 3rdalbum on 2009-06-07
> **smartboyathome said:**
> I'd rather use SSH to configure my server. Unless you use HTTPS, how do you know that someone isn't listening in on what you send to webmin?

Because you've tunneled the Webmin TCP port through your SSH connection to the server. That way you don't need to open any additional ports on your server for Webmin, too.

---

### Post by Mehall on 2009-06-07
> **juancarlospaco said:**
> Webmin IS http**S**  :D

+1

the address you're told to use is:

[https://localhost:10000](https://localhost:10000)

:P

---

