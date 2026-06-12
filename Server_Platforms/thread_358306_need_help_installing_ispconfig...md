---
title: "need help installing ispconfig.."
date: 2007-02-10
forum: Server Platforms
---

### Post by hockey97 on 2007-02-10
Hi I I have ubuntu 6.10 server and I done all the right installations directions, but when I install ispconfig it fails at when looking at proftpd becuse I didn't install that but then decided to thinking that's the problem when I try installing it I get a error message stating that it cannot find the package I tried install so many way's I even downloaded the newest version of it in .rpm format and tried to intall it with rpm ivh and rpm -Uvh ect I tried alot of way's on installing it and got the same error cannot find package and also on certain commands I would get common not found. 

I am really frustrated becue I spent 2 month's on this and still can get it to work. I am somewhat a noob in linux base areas, I also have the same error with installing the php5 some packages and also apach2 and that websta. any ideas ???

Also if I do get this server up and running can I make my own domain name?? Like will I be able to run a pro looking websites??? thanks for your time

---

### Post by jtc on 2007-02-11
First of all, may I ask why you need ispconfig?

Secondly I'd say a big part of your problem is that you are using rpm-files. Ubuntu generally has its packages in deb-files, and to be on the safe side you should preferable using deb-files made specify for Ubuntu.

---

### Post by hockey97 on 2007-02-11
Hi I want to use ispconfig for a graphical interface, I  don't really like the console way of doing that, I see  I got to unpack the packages that are in rpm but when I try to install it it can't find it,  I also want to know if it's possible for me to be able to run this server on the same computer while I run windows like I have 2 partisions one for this server and the other is windows xp pro which I use for everyday stuff ect, I want to know if I am on and running windows can I still have the server running in the backround??

---

### Post by hockey97 on 2007-02-12
Hi I want to use ispconfig becuse it's graphical interface I don't really enjoy using console stuff interfaces to control my server.

---

### Post by jtc on 2007-02-13
[Webmin]("http://www.webmin.com/") is probably what you are looking for.

---

### Post by Brazen on 2007-02-13
webmin is not for managing websites, but it is pretty good for setting up your server (ie changing the IP address or firewall settings) but is sounds like you are past that part.

Also, FYI, I would suggest vhcs or zpanel over ispconfig in a heartbeat.

You don't want to install rpms on Ubuntu, or any Debian based system for that matter.  If you need to install ProFTP or anything else, use apt, or download a deb file.

If you want to go with ISPConfig, I would suggest starting over with Ubuntu 6.06 Dapper server and use this guide: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by hockey97 on 2007-02-13
Hi thanks alot I wanted to get ispconfig becuse it said in my instructions on installing the server to use this as a graphical interface to manage your websites and data bases, as you might can tell I am a newbie to linux so I don't know what programs are out their, but I might look into what you suggested. I want to know with ubuntu 6.10 can I make and host my own domain names?? and also how would I make a online game would I use a database like mysql or somthing?? Becuse I finished making a game but I nsed to make the scripts so people can connect to my server over the internet and play against each other. 
BUT THANKS FOR YOUR HELP I been trying to get my server up and running for 2 months and kinda frustrated.

---

### Post by hockey97 on 2007-02-14
I have some more questions, I want to use a mail server in which I cna make the interface like graphic wise so like my customers that use my mail servcies that when they log in I want to make my own graphic for the log in and the mail interface something in the order of like aol or so.

I also would like to know if I can downlaod zip files and unzip them with this server if so , iis their some command to do that remeber I am new to linux world so bear with me wth my newbie questions. lol I check those sites you gave me zpanel looks great at the download section I see zip files and a rar  files would I download zip??

and Is it possible for me to run windows xp and have the server running in the backround?? becuse I am mostly on windows xp most of the time and I don't want to have to shut down my ubuntu 6.10 server in order to run my xp.

Thanks for the help, I really apprieciate it.

---

### Post by Aberrix on 2007-02-14
have you tried looking at this guide? [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

I had my server from base install to 100% running in less than a day with all the functions it seems you seek.

I've been using it for a month now and am very happy with it. no problems.

---

### Post by Brazen on 2007-02-14
> **hockey97 said:**
> I have some more questions, I want to use a mail server in which I cna make the interface like graphic wise so like my customers that use my mail servcies that when they log in I want to make my own graphic for the log in and the mail interface something in the order of like aol or so.

I also would like to know if I can downlaod zip files and unzip them with this server if so , iis their some command to do that remeber I am new to linux world so bear with me wth my newbie questions. lol I check those sites you gave me zpanel looks great at the download section I see zip files and a rar  files would I download zip??

and Is it possible for me to run windows xp and have the server running in the backround?? becuse I am mostly on windows xp most of the time and I don't want to have to shut down my ubuntu 6.10 server in order to run my xp.

Thanks for the help, I really apprieciate it.

You can use your Ubuntu server as a DNS server, but in order for your domain name to be accessible out on the internet, you must have your domain name registered with an ISP.

You can download zip files directly to your server using wget.  The syntax is "wget http://www.server.com/path/to/file.zip".  And you can unzip it with the "unzip" command (not sure on the syntax, try "man unzip" for help).

As for the email, I believe ISPConfig and those other hosting control panels I listed have built-in graphical email utilities.

Yes you can run Windows XP and install VMWare Server on it which will allow you run an Ubuntu virtual machine on that same box.

---

### Post by hockey97 on 2007-02-14
What I mean about the e-mail thing was that I want to have a service to people to have an e-mail account  on my mail server ect but when they log in and when the go to their account and see their e-maill that area I want to make my own custom art like what aol has like have my own buttons and custom art.

So their is no way on getting passed by the isp on having my own domain name??? Is their anyway I can get access to the barebone internet? 
becuse I don't really want to pay money on this.

So if I install VMWare Server  I can run ubuntu 6.10 server while I am on windows xp??

Don't worry about the command I have some idea on doing that and I know how to download stuff from the internet using commands. 

no I didn't see that tutorial. I followed a tutorial from here  [http://www.howtoforge.com/perfect_setup_ubuntu_6.10]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10")
I followed that and faild at the proftpd and the the webserver but got everything else done.


Thanks for your help

---

### Post by Brazen on 2007-02-14
> **hockey97 said:**
> What I mean about the e-mail thing was that I want to have a service to people to have an e-mail account  on my mail server ect but when they log in and when the go to their account and see their e-maill that area I want to make my own custom art like what aol has like have my own buttons and custom art.

So their is no way on getting passed by the isp on having my own domain name??? Is their anyway I can get access to the barebone internet? 
becuse I don't really want to pay money on this.

So if I install VMWare Server  I can run ubuntu 6.10 server while I am on windows xp??

Don't worry about the command I have some idea on doing that and I know how to download stuff from the internet using commands. 

no I didn't see that tutorial. I followed a tutorial from here  [http://www.howtoforge.com/perfect_setup_ubuntu_6.10]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10")
I followed that and faild at the proftpd and the the webserver but got everything else done.


Thanks for your help

If you want your own artwork on the email page, you will have to learn PHP, HTML, and CSS to design your own template for the ISPConfig interface.  Sometimes, if you just want to change a single graphic, you can just find the existing graphic on your server and replace it with your own.  This all just depends on what kind of artwork and layout you want.  I believe you can also pay the ISPConfig developers if you want them to design a layout for you (same for VHCS or zPanel).

If you don't want your very own domain name, you could sign up for a dyndns free account.  That would let you use a subdomain such as yourdomain.dyndns.org for free.

And yes, VMWare Server will let you run Ubuntu and Windows at the same time.  Keep in mind though, this will slow down your Windows computer, and probably make it impossible to play games will the Ubuntu server is running unless you have a high-end dual-core system.  Plus, just so you realize, Windows will have to be running in order to run the VMWare software which runs the Ubuntu virtual server.

Also, I would strongly suggest using Ubuntu 6.06 Server for this, not 6.10.

---

### Post by hockey97 on 2007-02-15
Hi Thanks for the replies, I am a programmer and I knew html for a long time so that's not really new to me I tried learning php but faild becuse I really had not time to learn it but I know sites to teache me  ect so it's not a problem so basily they would give me a default layout ect but in order I have tro change the image sorce ect?? 

So their is no way on getting a domain name like [www.smonthing.com](www.smonthing.com) for free , I seen domain names ect which High prices a month, I am making computer games ect and the site is a gaming site so for all the software I used ect It cost me an I don't have money at this moment to pay for a domain service, is the reason you need to register to the isp for your domain name is it becuse they have the access to the backbone of the internet??
and if you think their might be way's around getting to the barbone of the internet?? I have heard and seen some people having a dns server at their home and they got their own free domain name like [www.somthing.com](www.somthing.com) without registering to isp and I ask them about it but wont tell but they go to my school and I have seen with my own eye's the website up on the internet and I check if he really dosne't pay a thing and I found out he didn't, so I know their is some way of doing this but don't know how it's done and mostly it's not wellknown.

Well thank's alot I will have time this weekend to work on this wish me luck.

---

### Post by hockey97 on 2007-02-17
well I downloaded zpanel and tried unzip it said cannot find command and then I put in man unzip and same thing happen do I have to install a zip program?? need help with this.

---

### Post by PWRseth on 2007-02-17
Does zpanel support Ubuntu? I didn't see it listed on their site.

---

### Post by hockey97 on 2007-02-18
Hi on the site I didn't see it either, but people here used it on their ubuntu server and say's it works great, however I downloaded the zip files to my server and that's where I am at I don't know the commands to unzip the files I know thier is a way becuse the instructions I followed 2 month's ago with setting the server up had 2 packages in .zip formate and I unziped them, but I don't remeber using unzip as the command.
I Don't know if I have to download a package that handles .zip files or any type of software that will enable the .zip files. So I am stuck here.

What do you recommend for me to use for a panel, I have ubuntu 6.10???

Thanks for your help.

---

### Post by XplOzIOn on 2007-04-11
> **hockey97 said:**
> well I downloaded zpanel and tried unzip it said cannot find command and then I put in man unzip and same thing happen do I have to install a zip program?? need help with this.

to be able to unzip file you need the app on your system. Try:

```
sudo apt-get install unzip
```

If for some reason it cant be found add the extra repos to your system.

to Unzip simple do:
```
unzip /path/filename.zip
```

You can use zPanel, i started testing it today. so far it looks good.
Remember you can always buy a domain. the price is around 14USD per year just for the domain name. You can always use FREE DNS like [**CDMON**]("http://www.cdmon.com/")

Hope this helps you a bit more

---

