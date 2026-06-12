---
title: "Host your own website using Ubuntu and your DSL or cable line"
date: 2006-02-01
forum: The Cafe
---

### Post by matthew on 2006-02-01
I admit it...found this on Digg. Pretty interesting idea...of course, make sure your ISP will allow you to do it from a residential account before you try.

[Digg link]("http://digg.com/linux_unix/Host_Your_Own_Website_Using_Ubuntu_and_Your_DSL_or_Cable_Line")

[How To page]("http://howtoforge.com/perfect_setup_ubuntu_5.10")

---

### Post by WildTangent on 2006-02-02
I've been doing this for quite a while on my cable connection

[http://www.w1ldt4ng3nt.net](http://www.w1ldt4ng3nt.net)

-Wild

---

### Post by TechSonic on 2006-02-02
Too bad my ISP started blocking port 80.

---

### Post by WildTangent on 2006-02-02
[QUOTE=TechSonic]Too bad my ISP started blocking port 80.[/QUOTE]
Then use a different port :P

-Wild

---

### Post by galgoz on 2006-02-02
I am a website designer and was considering doing just this with my companies website, we are a reseller of hosting as well so we can provide the whole package to our clients. However, I decided not to do this for several reasons. One, the business account, which is required by my isp, cost so much more that alone made it unreasonable to create my own server for web hosting. So we stuck with our hosting through our reseller account instead.

---

### Post by Gandalf on 2006-02-02
Hey,

I've been hosting my own websites for more than a year and a half now, anyway to skip all the manual configurations in the above howto take a look to -> [Install VHCS on Ubuntu / Debian](http://wael.nasreddine.com/Articles/Articles/Install_VHCS_on_Ubuntu_%10_Debian.html)  ;)

---

### Post by raublekick on 2006-02-02
Very interesting, I might have to try this out sometime.

---

### Post by Metz on 2006-02-02
Yup....also been doing this for about a year. It's a mess, all needs tidying up.....but I currently run 4 websites hosted on a single old peice of junk machine sitting hidden away in a cupboard. It was mostly done as an exercise in learning, but it may turn out to be more worthwhile than that eventually.

My broadband connection is un-capped, 4mb down/400kb up, no port blocks (you can work around that anyway), and it's a dynamic-ip connection. Who needs to waste an extra £5 per month when ddclient works perfectly well, thankyou very much :):)

[www.codegibbon.com](www.codegibbon.com) , [www.abysium.com](www.abysium.com), [www.secs-online.co.uk](www.secs-online.co.uk) (secretarial services, eventually...so don't get excited ! ;)) and [www.fallenangelscrypt.co.uk](www.fallenangelscrypt.co.uk) (wife's blog site).

[size=1]A friend is downloading a huge file from the server at the moment....so it's not as fast as it should be ;)[/size]

---

### Post by xequence on 2006-02-02
Thats a great idea, except... Most ISPs (as far as I know) dont allow you to run a server through your normal connection.

And it would require really fast internet, as most servers have 10Mbit or 100Mbit upload. I have 800Kbit upload, which is 100KB, and most of it is always in use through seeding torrents.

---

### Post by raublekick on 2006-02-02
[QUOTE=xequence]Thats a great idea, except... Most ISPs (as far as I know) dont allow you to run a server through your normal connection.

And it would require really fast internet, as most servers have 10Mbit or 100Mbit upload. I have 800Kbit upload, which is 100KB, and most of it is always in use through seeding torrents.[/QUOTE]

You don't really need that fast of a connection unless you expect lots of traffic (which would probably be the case if your website is for a business or something, in which case you should probably pay for hosting anyways). I solid 80KB/s upload rate can provide enough to run a low traffic web or even FTP server.

---

### Post by Tichondrius on 2006-02-02
[QUOTE=WildTangent]I've been doing this for quite a while on my cable connection

[http://www.w1ldt4ng3nt.net](http://www.w1ldt4ng3nt.net)

-Wild[/QUOTE]

me too, and the howto is useless, anyone can install apache on their ubuntu machine very easily, so all that's need is to make sure your firewall settings allow the incoming HTTP request. That's all, it works like a charm, however the speed of sending data is limited by your upload bandwidth, and also the incoming http requests take away some of your download bandwidth, so I wouldn't attempt running a large multimedia website.

---

### Post by majikstreet on 2006-02-02
yawn.. I've been doing this for months...except now I switched to a real host.... well I knew it was against comcasts TOS to host a server anyway... but I suddenly aquired ~500usd and had no use... so why not host my three sites for 20usd a month? xD

---

### Post by imagine on 2006-02-02
That HowTo somehow reminds of another HowTo: [Write bad documentation](http://www.kuro5hin.org/story/2003/9/29/104212/112) : )

Screenshots of entering a username aren't that helpful and just help to obscure the important information.

---

