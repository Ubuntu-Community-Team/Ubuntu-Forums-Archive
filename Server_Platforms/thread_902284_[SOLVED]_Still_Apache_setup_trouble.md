---
title: "[SOLVED] Still Apache setup trouble"
date: 2008-08-27
forum: Server Platforms
---

### Post by ingeva on 2008-08-27
Well -- at least I'm getting closer.

I deleted most of the rubbish copied from the default VirtualHosts file, and finally there were sever VHs in action! :)

The amputated VH files now look like this:

```
<VirtualHost *>
    ServerAdmin webmaster@intertrafico
    ServerName skms
    DocumentRoot /home/WEB/public_html/skms
</VirtualHost>
```"intertrafico" is the "main" hosts; several common files are found under that domain. My scripts use ServerAdmin to find them.

Now there's only one minor problem left:

I also evidently need an IP-based Virtual Host, because I have hundreds of WEB addresses that are being mapped to it. I can't use wildcards there.

I tried using IP-address 127.0.0.99, but it seems like Apache doesn't want any double definitions (and it complains and won't start).

Let's call the new VH "dummy". Any ideas how to set up this one?
(All it contains is a small HTML file giving some information).

Is it at all possible to combine IP-based and name-based VHs?
If not, is there a better way to do this?

---

### Post by leg on 2008-08-27
Try replacing the start with the name of the server 

i.e. <VirtualHost dummy>

Thats how I do it and I also have to add the name to the localhost line in etc/hosts file and then it all works. Don't forget to restart apache to pick up your changes.

---

### Post by ingeva on 2008-08-27
> **leg said:**
> Try replacing the start with the name of the server 

i.e. <VirtualHost dummy>

Thats how I do it and I also have to add the name to the localhost line in etc/hosts file and then it all works. Don't forget to restart apache to pick up your changes.

Result:
[Wed Aug 27 14:36:37 2008] [error] (EAI 5)No address associated with hostname: Could not resolve host name dummy -- ignoring!

The hosts file contains:
```
127.0.0.99 dummy
 larryj.mpgproduct.com
 www.myworldplus.com
 profit_now.edcgold.com
 dsweasey.promoblackbox.com

```

Of course, all annoying sites should be mapped to "dummy".

Any better way to do this is appreciated.

---

### Post by ingeva on 2008-08-27
> **ingeva said:**
> Result:
[Wed Aug 27 14:36:37 2008] [error] (EAI 5)No address associated with hostname: Could not resolve host name dummy -- ignoring!

Back to the original:

Something (don't know if it's the browser or Apache) modifies the WEB address,
so when I write "http://dummy/" or "http://dummy/index.html" the website
"http://www.dummy.com/index.html" is displayed.

[SIZE=5]**I HATE IT**[/SIZE] when software does things that I haven't asked it to do.

Can someone help me find something that actually works?

I'm really tired of the Apache thing now, and of all the suggestions that only set me back to where I was before.

Could someone sit down and write a more user friendly httpd server?
It's been done before -- the one I used with Windows (omnisecure) was just beautiful. However, that's still not reason enough to return to Windows! :)

---

### Post by leg on 2008-08-27
I will look into when I get home. I have probably missed a step out. I use apache with virtual hosts but I do know that mine are mapped against the localhost rather than any ip address. I don't think that should make a difference though.

The reason [http://dummy](http://dummy) is finding [http://www.dummy](http://www.dummy) is because your server can't find [http://dummy](http://dummy) so searches for it elsewhere.

---

### Post by ingeva on 2008-08-27
> **leg said:**
> I will look into when I get home. I have probably missed a step out. I use apache with virtual hosts but I do know that mine are mapped against the localhost rather than any ip address. I don't think that should make a difference though.

The reason [http://dummy](http://dummy) is finding [http://www.dummy](http://www.dummy) is because your server can't find [http://dummy](http://dummy) so searches for it elsewhere.

How are they mapped against localhost?
My setup defined  <computer.domain> as 127.0.1.1
but the address I'm used to as localhost (from windows) is 127.0.0.1.

I've tried both of these as well as 127.0.0.99, which I set up as a "special" address to trap the sites that are not supposed to be shown for different reasons (Some of them carry various malware, others are just plain annoying).

Other ***good*** ideas for blocking sites is welcome. My "dummy" index.html file reports the referring site if there is one, because it's sometimes necessary to block that -- so I would prefer to keep that possibility. I use different browsers on a regular basis so the blocking should be on the server side, not with the client. Some kind of firewall might help but it would probably not report the referrer.

My dummy site looks like this: [http://intertrafico.com/test/](http://intertrafico.com/test/) just to give you an idea.

---

### Post by windependence on 2008-08-27
> **ingeva said:**
> Well -- at least I'm getting closer.

I deleted most of the rubbish copied from the default VirtualHosts file, and finally there were sever VHs in action! :)

The amputated VH files now look like this:

```
<VirtualHost *>
    ServerAdmin webmaster@intertrafico
    ServerName skms
    DocumentRoot /home/WEB/public_html/skms
</VirtualHost>
```"intertrafico" is the "main" hosts; several common files are found under that domain. My scripts use ServerAdmin to find them.

Now there's only one minor problem left:

I also evidently need an IP-based Virtual Host, because I have hundreds of WEB addresses that are being mapped to it. I can't use wildcards there.

I tried using IP-address 127.0.0.99, but it seems like Apache doesn't want any double definitions (and it complains and won't start).

Let's call the new VH "dummy". Any ideas how to set up this one?
(All it contains is a small HTML file giving some information).

Is it at all possible to combine IP-based and name-based VHs?
If not, is there a better way to do this?

OK you still don't understand how the new modular Apache2 works. The main configuration is under the apache2.conf file, NOT httpd.conf. The httpd.conf is ONLY there for compatibility with apache 1.3.

The Vhosts are stored in /etc/apache2/sites-available/your_vhost_name_1. Each Vhost has it's own config file under sites-available. You must disable the default site to access all your vhosts by doing 

```
sudo a2dissite default
```

The /etc/apache2/sites-available directory is  not parsed by Apache2. Symbolic links in /etc/apache2/sites-enabled point to "available" sites. Use the a2ensite (Apache2 Enable Site) utility to create those symbolic links, like so: sudo a2ensite mynewsite  where your site's configuration file is  /etc/apache2/sites-available/mynewsite. Similarly, the a2dissite utility should be used to disable sites. 

Here is a great thread explaining how to do all this:

[http://ubuntuforums.org/showpost.php?p=5645242&postcount=3](http://ubuntuforums.org/showpost.php?p=5645242&postcount=3)

And here is official Ubuntu documentation that may help you to be less confused about the Apache2 modular approach to configuration:

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

And a brief explanation of all the Apache2 modules, even though it's Debian, it's still the same:

[http://www.debian-administration.org/articles/207](http://www.debian-administration.org/articles/207)

That should get you started well on your way, but you may want to start with a clean install because you have tried so many things (some things I don't even understand) so a clean go may be your best bet.

-Tim

---

### Post by ingeva on 2008-08-28
> **windependence said:**
> OK you still don't understand how the new modular Apache2 works.

I think it might be a good idea to read my posts before you spend a lot of time confirming that what I've done was right.

The httpd.conf was empty. It's a very nice file to use as an extension of the apache2.conf file if you don't want to mess it up. If it's obsolete, why is it being referred?

Apache has some stupid limitations. For instance, it took me a long time to discover that "NameVirtualHost" could be used only once. I did not find mention of it in the documentation. On the contrary, I got the impression that it was needed for every VH file. The error message did not make this clear; in fact the error messages from apache are a disaster!

I'll set this thread as "solved" now.
There may be differences between distributions. I run Ubuntu 8.04.
Since you are running BCD, I wouldn't start telling you that MY solution would be perfect for YOU.

---

### Post by windependence on 2008-08-28
You sure are stubborn and a bit onery. If you noticed I was TRYING to help you fix this, and I'm pretty sure I did with what I just posted above. I have indeed read what you wrote and quite frankly, most of it didn't make much sense.

The httpd.conf file is there for compatibility reasons for such things as cold fusion, and to preserve backward compatibility with Apache 1.3 and below. Although it's read by default (unless you comment it out)it certainly isn't apache's intent for you to use it for configuration because you don't want to "mess up" the real file.

As to Apache's "limitations", don't you really mean you just don't like their way of doing things? It certainly isn't a "limitation", it's just the way Apache does it. I will give you that the NameVirtualHost thing is not really clearly marked, but there certainly are many posts and articles out there about it if you search google.

Yes, I do run most of my stuff on *BSD (not BCD) lately, but I cut my teeth on Linux for years before I started with BSD. That doesn't mean I am not capable of helping you. So far, 120 people seems to think I have assisted them with something useful. I will continue to help you too, if you will just listen. ;)

-Tim

---

### Post by ingeva on 2008-08-28
> **windependence said:**
> You sure are stubborn and a bit onery.


Yes I am! :)

> **windependence said:**
> if you noticed I was TRYING to help you fix this, 


Thank you for trying! But some of the problem is that you tried to help me fix things that were already fixed, and I don't want to change something that works.

> **windependence said:**
> The httpd.conf file is there for compatibility
...Although it's read by default (unless you comment it out)it certainly isn't apache's intent for you to use it for configuration because you don't want to "mess up" the real file.


I understand, but I still prefer to use it. For now anyway.

> **windependence said:**
> As to Apache's "limitations", don't you really mean you just don't like their way of doing things?

Certainly. My previous webserver took about 5 minutes to set up. Everything was clear. To compare: I've spent about one month with Apache. Not 24/7, but still a hell of a lot of trial and error, time and energy.

> **windependence said:**
> helping you. So far, 120 people seems to think I have assisted them with something useful. I will continue to help you too, if you will just listen. ;)

I will listen. That's why I ask. But if I ask for bread I don't want soup.

Thank you for doing what you do anyway. I was very frustrated by this whole process and let it fall upon you. I finally found my solution by searching the Net.
I have no solution to mixing IP-based and name-based VHs, but maybe you can tell me if it's at all possible?

---

### Post by windependence on 2008-08-28
Hey no hard feelings at all. I have had to apologize at least once here for getting a bit frustrated with something someone said when I was attempting to help them.

Apache can seem confusing and haphazard at first but once you get the idea of how and why it is designed that way, you'll begin to see the beauty of it.....really. ;)

yes, you certainly can do both IP based and name based VH, but I am not completely convinced you need to do this. If you can give me a clear idea of what the problem is you are trying to overcome, I may be able to suggest a solution.

-Tim

---

### Post by ingeva on 2008-08-28
> **windependence said:**
> Apache can seem confusing and haphazard at first but once you get the idea of how and why it is designed that way, you'll begin to see the beauty of it.....really. ;)

There are probably many reasons why it's used on most servers. The program itself is probably quite elegant, but for me trying to make it work was something like going through hell. I also received and found so many tips that didn't work, that I lost count.

Much of the problem must have been that when I corrected something one place, it didn't help because the error was somewhere else. Instead, I just created a new problem. But really: Why apache doesn't report that (for instance) "listen 80" is not accepted twice is beyond me. Of course, the second instance should just be ignored -- maybe with a little warning.

> **windependence said:**
> yes, you certainly can do both IP based and name based VH, but I am not completely convinced you need to do this. If you can give me a clear idea of what the problem is you are trying to overcome, I may be able to suggest a solution.

The point of an IP-based VH is to trap some (several hundred) unwanted websites from being displayed. I want to map them to a local HTML script that gives me some information; for instance the referrer so I can know who called an annoying site. Sometimes I might wish to block the calling site as well. Many of them are frame-breakers that disrupt the surfing.

Now these sites aren't half as annoying in Linux as they are in Windows, because Linux doesn't have ActiveX -- and it's far less receptive to malware.

I would welcome another solution, especially a better one. :) When I move the webserver to another computer in my network I might not be able to use the current solution anyway.

I should have marked this thread as solved since we're now discussing a different topic, but it's not "my" thread". I hope the original poster har solved HIS problem -- which was very similar to mine (making php work with Apache).

---

### Post by windependence on 2008-08-28
> **ingeva said:**
> I also received and found so many tips that didn't work, that I lost count.

And so it is with Linux and possibly Unix in general. there are so many ways of doing the same thing and some people will write tutorials without testing them. I have gotten used to this over the years <sigh>.

> **ingeva said:**
> Much of the problem must have been that when I corrected something one place, it didn't help because the error was somewhere else. Instead, I just created a new problem. But really: Why apache doesn't report that (for instance) "listen 80" is not accepted twice is beyond me. Of course, the second instance should just be ignored -- maybe with a little warning.

Actually there is a command to check your Apache syntax that works quite well. It checks all your config files ot make sure they are correct. I'll see if I can dig it up for you.



> **ingeva said:**
> The point of an IP-based VH is to trap some (several hundred) unwanted websites from being displayed. I want to map them to a local HTML script that gives me some information; for instance the referrer so I can know who called an annoying site. Sometimes I might wish to block the calling site as well. Many of them are frame-breakers that disrupt the surfing.

So, if you refer to these sites using a hard IP then they won't show any remotely called sites?

> **ingeva said:**
> Now these sites aren't half as annoying in Linux as they are in Windows, because Linux doesn't have ActiveX -- and it's far less receptive to malware.

Now THERE'S an understatement. Active X was one of the worst things Mickeysoft ever invented. Of course this makes their stuff even more proprietary also.

> **ingeva said:**
> I would welcome another solution, especially a better one. :) When I move the webserver to another computer in my network I might not be able to use the current solution anyway.

Well, I gotta think about that one. I'll post it in a new thread if I can think of a different way.

> **ingeva said:**
> I should have marked this thread as solved since we're now discussing a different topic, but it's not "my" thread". I hope the original poster har solved HIS problem -- which was very similar to mine (making php work with Apache).

Very true, we sure did hijack this one. Did you ever get your php working on your sites? I think I have a fair understanding of how they are loading the modules in Apache2 now. All my sites are running on 1.3 using one single httpd.conf and on *BSD I compile php support right into Apache at install time.

-Tim

---

### Post by ingeva on 2008-08-28
> **windependence said:**
> Well, I gotta think about that one. I'll post it in a new thread if I can think of a different way.

-Tim

Thank you very much!
The "IP-solution" is the one that I used with my Windows for several years.
Whenever I found a "bad" site I copied the domain name to the hosts file, mapped to 127.0.0.6 (random choice). This IP was mapped to the my dummy site, and when such a site was encountered its URL was reported, and if possible also the URL of the referrer.

I see that the thread is [Solved] anyway now. I hope the original poster is OK with it, but he's been silent. I hope he hasn't given up but it seemed as he knew what he was doing. Maybe my solution helped him also.

BTW, being stubborn and persistent has helped me many times. So has being humble when that was required. :)

---

