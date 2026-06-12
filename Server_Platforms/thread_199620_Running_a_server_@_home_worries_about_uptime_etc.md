---
title: "Running a server @ home worries about uptime etc"
date: 2006-06-19
forum: Server Platforms
---

### Post by ade234uk on 2006-06-19
I am paying £23.00 p/m for my resseller package. I have always wanted to run my own server from home at some stage, however what worries me about doing this is keeping it running 24/7 and also I worry about Fire which is not going to happen I know. 

Do any of you run a server from home?

What safety precautions do you take?

Is it a headache?

I was thinking of getting a shed come office which you can be for £300 - £400 for the garden and putting it in there. Am I overeacting. The only reason I want to do this is for safety just in case there was ever a fire. At least it would take the shed down and not the house.

---

### Post by Jason_25 on 2006-06-19
Your worried about the PC catching on fire?  There's nil chance in that, or it actually catching something else on fire.  Every computer I have built runs 24/7 for years without so much as a spark.  I run a server at my parents, but it's mainly for my own use and lightweight web hosting for ebay, etc.  If your still worried, maybe you can set it up to email/text you when the lm-sensors output for your hardware reads abnormally.

---

### Post by Soarer on 2006-06-19
Agree 100% with Jason_25. I run a server 24/7 in a cupboard in my spare bedroom/office. You want a reasonable amount of ventilation but PCs will shutdown from overheating before they catch fire. Electrical problems in your house wiring are much more likely to start a fire I would think.

---

### Post by LoclynGrey on 2006-06-19
I run a server in my garage, it's been up for 3 months now no problems. Unbuntu 5.10. It serves as a file and webserver.

On that note, my office pc in the house (Dapper) never gets turned off either.

---

### Post by Johnsie on 2006-06-19
I ran an HP Vectra as a server for a year and had no problems like that. If you're really worried then maybe you could consider installing a smoke alarm near the server. Like you I also worried about fire but haven't had any problems. I guess the smoke alarm idea is all you can do except maybe investing in some good fans to keep everything nice and cool.

Remember that you shouldn't throw water on electric fires.

Uptime should be good.... what I nromally do is have vnc to control it but if there's something I can't fix with vnc (like a crash) I amke a phone call and get them to reboot it. Havining auto-login enabled is a must for me as my  server doesn't have a monitor hooked up to it :-)

Good luck and have fun :-)

---

### Post by nihilocrat on 2006-06-19
The only annoying thing about running a server from home is that you're responsible for outages and might need to call home to get it rebooted if something seriously screws up. I ran one for about two years during high school and the only issues I had were because the box I was running it on wasn't taken care of very well, which gave rise to an occasional kernel panic. If the machine you're running it on is a stock machine and everything is working properly, it should have no problems running 24/7. If you built it yourself, make sure it has proper ventilation and fans, and that they're all in working order. I killed a graphics card from running my current desktop too hot without really knowing it.

One thing you will want to think about is backups. There are many, many ways of doing it but it would probably be smart to implement at least some form of backup.

Oh, and you'd probably be safer having it run indoors rather than in a shed outside: if it's warm enough ants might want to make a home in it. It's not humongously rare for people to have ants invade their laptops, so I'd guess desktops might be fair game too.

---

### Post by Randomskk on 2006-06-19
Yea, I certainly wouldn't worry. I have three or four servers running upstairs.

What I WOULD be worried about are power cuts, brownouts, and internet disconnections. For instance:
1) Power cuts. These will knock the server flat out, which not only can be bad but of course brings down your website etc. This can be avoided by using some variety of UPS

2) Brown outs. These can really damage hardware, drastically cutting down the life of your server. Again, a UPS will help out.

3) Internet connectivity. This should be your single biggest concern, I'll split it up:
a) Internet loss, ie if your connection drops. I'm assuming ADSL or cable, but in either case it's not uncommon for a modem to reset, or a connection to be lost for an hour odd. In these cases, the server is down, and there's pretty much nothing you can do about it.

b) Internet speed. You may have a fast download on your current ISP, but what about upload? This matters a lot more with servers, and as such you may find accessing it will be a lot slower, and it may slow down your own downloads etc etc. This can be resolved by upgrading your internet connection.

c) ISP restrictions. Many ISPs do NOT allow you to host a server, and even those that do may apply restrictions or may block ports such as port 80 (web servers) or port 25 (SMTP servers), blocking either of these will stop you ever getting a server online.

Of course, if you've already considered all of that, and fire is the only worry you have, then go ahead and set up a server - it's not going to catch fire any time soon.

---

### Post by ade234uk on 2006-06-19
Its interesting to hear your thoughts. I am a very paranoid person sometimes when I go away for the weekend I have to unplug everthing, I check the front and back door twenty times before I leave.

As regards another machine what would go for 

1) A new machine from dell
[http://www1.euro.dell.com/content/products/compare.aspx/tower_servers?c=uk&cs=ukbsdt1&l=en&s=bsd](http://www1.euro.dell.com/content/products/compare.aspx/tower_servers?c=uk&cs=ukbsdt1&l=en&s=bsd)

2) A second hand dell server from ebay

3) Build your own

---

### Post by Randomskk on 2006-06-19
I'd build your own if you know roughly what you're doing; more bang for your buck generally speaking.
My second option would be buying a new one.

---

### Post by mrcowcow on 2006-06-19
I have run desktops as servers for a year and a half now, no problems. As long as you have a decent internet connection, you get execellent uptime. As for what you use, my current server is my parents old computer. It works just fine for small loads. If you nedd a server that can handle large loads, or needs to be up as much as possible, buy one from HP or Dell or somewhere. Sun now offers Ubuntu pre-installed on some of their servers too, but their servers are more expensive then ones from HP or Dell. And I would not reccomend putting your server out in the garden, just put it in the basement, or a closet somewhere where it is out of the way.

---

### Post by Shay Stephens on 2006-06-19
I have run a server (web, mail, ftp, database) for about 6 years.  The biggest problems I have run into is power failure (get a UPS), network outage, and hardware failure.

What get's irksome is when something fails when you are out and about.  Or when the network goes down because some turkey in a backhoe breaks a local cable.

I have opted to go with managed servers / web hosting.  For me, the static ip and bandwidth was about $100 a month.  A managed server is $99 a month, but much more reliable, and probably has better bandwidth / peak capabilities.

I am going to turn my server into an in-home entertainment / data server (DVR, music, file storage) once all the domains it hosts get transferred off.

For me it just wasn't worth it to do it in house, especially on mission critical stuff.  Now I can rest a little easier ;)

---

### Post by haircut on 2006-06-20
I run a PC from home with the Ubuntu Server on it. At the moment I  use it mainly to learn Linux via SSH, we don't have access to Linux machines where I work.

I hope to co-locate it eventually for running Game servers from. I've done this for some time now and I can agree with the rest of the comments here, no worries about doing it at all. The set-up is critical so I'm not worried about any outages I get. I have the connection (router reboot) completely fail on about 2 occasions.

Just give it ago and see.

---

### Post by Randomskk on 2006-06-20
[QUOTE=Shay Stephens]
I have opted to go with managed servers / web hosting.  For me, the static ip and bandwidth was about $100 a month.  A managed server is $99 a month, but much more reliable, and probably has better bandwidth / peak capabilities.[/QUOTE]

That's pretty costly; my server costs around $50/month for two static IPs plus as much bandwidth as I can use, at fairly good speeds.
Then again, I suspect electricity costs add a little on to that, and I do get the odd power cut or (more frequently) network failures.

Having the server local is much nicer for security though.

---

### Post by mumushi on 2006-06-22
Hello guys just came accross the thread because i was planning to have my own server at home my problem is im a newbie in ubuntu. Just wanted to ask help what do i need to do. How? Maybe a howto would be a great help. thanks!

---

### Post by ubuntu27 on 2006-06-22
[QUOTE=mumushi]Hello guys just came accross the thread because i was planning to have my own server at home my problem is im a newbie in ubuntu. Just wanted to ask help what do i need to do. How? Maybe a howto would be a great help. thanks![/QUOTE]

I never had my own server so I cannot help you. But, I can give you a link.

[Server's FAQ]("https://help.ubuntu.com/community/ServerFaq")

[Wiki: Ubuntu Server]("https://help.ubuntu.com/community/Servers")

Hope that helps you.

---

### Post by mumushi on 2006-06-22
[QUOTE=ubuntu27]I never had my own server so I cannot help you. But, I can give you a link.

[Server's FAQ]("https://help.ubuntu.com/community/ServerFaq")

[Wiki: Ubuntu Server]("https://help.ubuntu.com/community/Servers")

Hope that helps you.[/QUOTE]

Thanks a lot for the help i'll be reading that now and maybe ask you for help later. :D Thank you so much...

---

### Post by mumushi on 2006-06-22
i already have finished reading the links you have given me and finally decided to use LAMP which is already in the ubuntu server installer and it autoconfigures everything mysql, apache, php. Actually i finished instaling it. now what's next? any guide? my main objective is to set up my own web server. thanks alot for any help, it is greatly appreciated.

---

### Post by ubuntu27 on 2006-06-22
[QUOTE=mumushi]i already have finished reading the links you have given me and finally decided to use LAMP which is already in the ubuntu server installer and it autoconfigures everything mysql, apache, php. Actually i finished instaling it. now what's next? any guide? my main objective is to set up my own web server. thanks alot for any help, it is greatly appreciated.[/QUOTE]


 [Here's a detailed guide]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06") to setting up am Ubuntu 6.06 LTS server that offers all services needed by ISPs and hosters (Apache web server, Postfix mail server (with SMTP-AUTH and TLS!), DNS server, FTP server, MySQL server, POP3/IMAP, Quota, Firewall, etc.). Screenshots included. 


[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)



***Start a new thread if you have some specific problemes. New thread are more likely to be seen than already replied threads.****  

That's just my tip :P



Good Luck!

---

### Post by mumushi on 2006-06-22
[QUOTE=ubuntu27][Here's a detailed guide]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06") to setting up am Ubuntu 6.06 LTS server that offers all services needed by ISPs and hosters (Apache web server, Postfix mail server (with SMTP-AUTH and TLS!), DNS server, FTP server, MySQL server, POP3/IMAP, Quota, Firewall, etc.). Screenshots included. 


[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)



***Start a new thread if you have some specific problemes. New thread are more likely to be seen the already replied threads.****  

That's just my tip :P



Good Luck![/QUOTE]

Thank you so much for the link it helped alot. About your tip in making a new thread i will be doing that soon. Thank you so much!

---

### Post by herald on 2006-06-23
I've run 2 separate Internet domains, each from my home.  This invovled anywhere from 4 servers and 2 desktops in the past to the current 6 servers and 3 desktops.  The biggest problem I've got is power.  I'm seriously considering having an electrician come in and drop in a 220 circuit (yes, I'm in the US) because when the air conditioner kicks on, I'm on the brink of a brownout that drops both of the domains I run.

I'm running a DMZ that provides full DNS, Web, Email, and VPN, not to mention the NIS infrastructure and Configuration Management for all the different things, both public and private.  My advice follows:
- Start small!!!  The Net is a big bad place these days, and it's horrifying to put out your shiny new internet site just to have it hacked to pieces and hijacked from beneath you.  If you start small, and learn what you're doing first, it will pay off in the end.

- Quality isn't cheap...If you want to have reliable stuff, spend the money in the right places.  Broadband, Routing, and storage are the big things in my book.  With all the horsepower even the older servers have, you can get a lot of bang for a little buck...Meanwhile, a Cisco router isn't cheap, but it's well worth it!

Running your own Internet Site is loads of fun and a wonderful way to learn.  Plus, it's great being able to VPN into my private file server from anywhere and stream in all my favorite music and videos :D  And as for starting a fire...Forget about it.  Worry about the electrical and ISP bills...they'll kill you before a fire does!

---

### Post by eldaria on 2006-06-23
I would not worry about Fire either, I was running a home server for 4 years, it was custom built into a Carton box, and was staying in the fuse and electric closet, it even overheated once due to a heat wave, and was beeping like crazy, but no fire.
The thing that killed that server was no fire or heat, but rather some mice who decided the server was a perfect place to build a nest.

[http://www.eldaria.net/album/v/eldaria/Old+Server/](http://www.eldaria.net/album/v/eldaria/Old+Server/)

Btw, the server hosting the pics is a home server, right now runnig Windows, but in process of getting migrated to a second server running Ubuntu 6.06.
Yes I know it is slow. ;-)


[COLOR="Red"]Update, I have updated the link to the pictures, since it is now runnig on new Hardware and on Ubuntu instead of Windows.[/COLOR]

---

### Post by Kurt` on 2006-06-23
[QUOTE=eldaria]I would not worry about Fire either, I was running a home server for 4 years, it was custom built into a Carton box, and was staying in the fuse and electric closet, it even overheated once due to a heat wave, and was beeping like crazy, but no fire.
The thing that killed that server was no fire or heat, but rather some mice who decided the server was a perfect place to build a nest.

[http://www.eldaria.net/album/listpics.asp?dir=Brian%5COld+Server](http://www.eldaria.net/album/listpics.asp?dir=Brian%5COld+Server)

Btw, the server hosting the pics is a home server, right now runnig Windows, but in process of getting migrated to a second server running Ubuntu 6.06.
Yes I know it is slow. ;-)[/QUOTE]
Nice cases. :)

@ade234uk: If you are **really** paranoid, you could install a halon-release system in the shed you were talking about ^^

---

### Post by Noahod on 2006-07-04
Why not just build a moat? \\:D/ 

Seriously, don't worry about it. Worst case scenario, your power supply goes bang once, and a spark goes 5cm out the back. Unless your server is built on dry grass or next to big smelly tank of petrol, I really can't see anything happening. 

I don't think the power bills are as bad as people make out, but just go down to the local markets and get something that's not overpowered, EG PIII 1ghz with a single harddrive and a fair bit of ram. If you want it to last a while surge protectors and UPSes go a long way.

---

