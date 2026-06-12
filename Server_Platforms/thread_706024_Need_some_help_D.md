---
title: "Need some help :D"
date: 2008-02-24
forum: Server Platforms
---

### Post by DakoRakkun on 2008-02-24
Hi! I need some help setting up a school server :-\" . 

Some background info: there's a student society related to my major at my university called Enredatec. They promote linux and have done a few install fest and other stuff. Some years ago they raised money to buy a machine and use it as a server, and everything was fine but the machine was hacked and put offline. The society hasn't been as active as it was because its active/older students graduated or are busy working. So the server has been sitting for a while doing nothing.

So I took the task of getting it up and running again :), though I'm not an expert with linux (I'm more of a Windows user :???: ), but I have tried, used and installed linux and ubuntu on some machines and played with them. The desktop version though.

So I came here and downloaded the server version, and I've been kinda of following this guide: [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10), though I'm not sure if this is what I need.

What I was is to set it up so that I can take the machine back to school so they can just hook it up and be online, and be able to give user account to other students so they can upload their websites and try their applications from here. I think ISPConfig is what I should use, not sure. As for software, PHP, Apache, MySql, Ruby/Rails (not sure if there's anything else that I might need or use). I'm not really sure if I need the DNS (not sure what it would do), or the mailserver, though ISPConfig asked for it.

I followed the guide, but had some problems. I didn't install Postfix at first 'cause I thought I didn't need it, but ISPConfig asked for it, so I went back and followed that step, but when I checked for "ehlo localhost" I didn't get what the guide asked (page 5 by the way), but I was able to install ISPConfig after that.

I had two other problems. The first one I believe is kind of small. I couldn't install php5-json, said something about being included php5-common or something like that, and I was already installing that.

The other is that I don't really know how to configure ISPConfig. And how will I be able to check the installation here (my linksys gives it an IP which I can use), but after I take it to school will it update its IP. I don't know the IP the school gives it, though I know there's an [www.enredatec.com](www.enredatec.com) domain.

And that's about it. Sorry, it's a long post, hehe. But I'm willing to install ubuntu from scratch again to get it working and running again. Any help/ suggestions :)?

Thanks in advance :D

---

### Post by kaginken on 2008-02-24
I built my gutsy server using the same how-to you did.  I too, opted to install the ISP Config just to try it out as I wasn't familiar with it.  After trying to figure it out, I decided it wasn't very useful unless you're going to be trying to run a LOT of websites...are you?

For me, the solution was to remove the ISP Config and the good news is - that solved several problems I was having.  It did a clean uninstall.

Something else I found out is that the gui didn't install by default, but that was an easy apt-get install command and it was up and running X Windows...

I'd recommend just removing it as the time it will take you to learn the isp config, you could just put your website(s) in apache manually...

Hope that helps!

---

### Post by DakoRakkun on 2008-02-24
Thanks for your reply :D. I was thinking of ISPConfig 'cause it seemed like a good tool to give other students account and being somewhat in control. Is it easy to do that in apache?

Also, is it easier to do all these stuff using gnome/x windows? I actually did all this directly on the computer typing everything. Tried with putty at first but couldn't do it, so I started typing and everything was fine till later in the guide, when I kind of regretted it :P. Found out I was typing another IP in putty :D, hahaha.

---

### Post by kaginken on 2008-02-24
Thanks for the thanks!  :)

I didn't really need the X windows gui on the server, actually didn't learn about it until after I was done installing everything.  It's all much easier from the command line, and faster too.  PuTty is a really good ssh client for windows too, that's what I use a lot if I'm in windows.  OpenSSh is another good ssh client that comes with file transfer built in, so makes uploading/downloading your files very easy.

Apache is quite easy to learn.  I have several websites running on mine just fine, each one is in it's own directory and you just link to them.  ISP Config seems like it would be pretty time consuming to learn, it wasn't very intuitive and had very little documentation and support...may as well just learn a bit about apache and eliminate the middle man.  Think ISP Config is just for very large webservers hosting a lot of sites.

Good luck with you and yours, sounds like a noble cause and the skills you'll learn in the process are very marketable!  Apache is like 70% of all webservers now.  :D

---

### Post by DakoRakkun on 2008-02-24
Heheh, thanks again.

Yeah, ISPConfig seems like overkill, the documentation wasn't that helpful, and the guide was also a little confusing.  I'll look into how to create accounts for others students without ISPConfig :D.

Thanks :D

---

