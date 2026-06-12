---
title: "preventing facebook from harvesting personal info"
date: 2013-01-19
forum: Security
---

### Post by goodbye-windows(tm) on 2013-01-19
Hi All,

I have no use for facebooks methods and practices regarding collection of private information via the browser.

I do however want to follow my daughters exploits, she uses facebook a bunch.

So, I've been wondering if there was anyway to totally prevent facebook from harvesting personal info that I do not want disclosed. I believe this requires a second install of xubuntu, in a separate partition...the second install would be used for facebook only and would have only firefox enabled. It would be very minimal without any frills regarding software installed and unnecessary linux services and linux processes would never be allowed to run.

On this special account, I would only use firefox for accessing my anonymous email account and my daughters facebook page(s). 

Since I don't use firefox for anything else, there would be no personal information to harvest-case dismissed::>

My regular (everyday) linux user account would NEVER be used to log into facebook or my anonymous web email account-so there's no way for facebook to harvest any personal information (I hope).

The only problem I can see is that the bios can be read via installed software. And, the bios contains a globally unique serial number, so downloading the bios can provide a means to identify my computer regardless of any stealth measures I utilize.

Are there other globally unique serial numbers that can be downloaded via the web browser?

Is this approach the best method of preventing facebooks harvesting of personal info via the browser?

Appreciate all info.

TY.

Art

---

### Post by mike acker on 2013-01-19
> **goodbye-windows(tm) said:**
> Hi All,

I have no use for facebooks methods and practices regarding collection of private information via the browser.


TY.

Art

a separate user log-in should be sufficient . consider using a proxy server . fb will make every effort to get the dox on you -- even if you don't have a fb account

---

### Post by goodbye-windows(tm) on 2013-01-19
Thanks Mike.

But, can it be that easy/simple??? 

I don't trust firefox to keep the users separate, which is why I was thinking I would need a partition and a separate (dedicated) facebook only account on the separate partition. 

Everything I read about facebook leads me to believe that they use all available means to collect personal info-so I'm not sure I can count on them to keep their harvesting limited to the logged in user only.

> **mike acker said:**
>  fb will make every effort to get the dox on you -- even if you don't have a fb account

I think you're talking about the linkage between google/yahoo/youtube (and others). To me this is very alarming-but others seem oblivious to the danger...... Flash cookies make cookies last forever, they're large files so can hold lots of data and they cannot be deleted...again, I'm not finding many who care about this.

**If I don't have a facebook account, how does facebook gather info about me??? **

I'm familiar with proxy accounts and VPN. But, they allow cookies and other stealth means to harvest personal info. They allow me to keep my ip address private, but I can change ip addresses at will by resetting my router. Cookies negate the ip address swapping advantage, and vpn doesn't offer protection against cookies.

Since a java based browser allows the loading and execution of active content without my approval, it seems to me that websites can do nearly anything they want to my system without my knowledge....including harvesting of personal information from other users on my system.

**If I go to a separate installation in its own partition, are there any globally unique id's/digital fingerprints that can be downloaded via a web connection???** The ability to remain anonymous is most significant privacy issue (I think).

Art

---

### Post by cariboo on 2013-01-19
To prevent data from being accessible from other accounts on your system, use Linux permissions. A default Ubuntu installation is setup up to fairly easily share files among users. To prevent other accounts from accessing your home directory open a terminal and type the following command:

```
sudo chmod 700 /home/user_name
```

where user_name = your user name. Then log into the other account. open Firefox and type in the url bar:

```
file://home/user_name
```

you should get a permission denied message, or not be able to access the directory

---

### Post by uRock on 2013-01-19
I thought all browsers had the Private Browsing option.

---

### Post by cariboo on 2013-01-19
> **uRock said:**
> I thought all browsers had the Private Browsing option.

They do, but changing permissions is just the belt and suspenders approach. :-D

---

### Post by MoebusNet on 2013-01-20
Just my opinion, but if the Facebook business model is to collect and sell its users' information, won't using Facebook at all always be a risk?

I'm just sayin'...

---

### Post by Soul-Sing on 2013-01-20
use iptables to block domains. google search is full of this.

---

### Post by mike acker on 2013-01-20
> **MoebusNet said:**
> Just my opinion, but if the Facebook business model is to collect and sell its users' information, won't using Facebook at all always be a risk?

I'm just sayin'...

yes

this is why i recommend creating another user logon -- for using fb .  this will isolate the one user from another completely .

 someplace around there is a highly regarded alternate DNS -- which you can re-configure yourself -- and control what your system can access ...

it is important to remember we all have a 'reverse DNS' also -- that every web page can use (many do use ) to identify the computer that they are talking to ... see Steve Gibson Research for more info 

i would not want to underestimate the ability of fb to data-mine a pc -- once they get into it -- and i understand this can be from a fb web page -- you don't even have to sign up for fb for them to start mining

all the more reason to think about that alternate dns  ( i have info on it around here someplace )   one thing isn't clear though and that is ..... if you use a numeric ip address such as (e.g.) 158.70.208.177 -- dns is not required so i'm not sure how much real protection that dns server change actually provides ... i think most of the so called 'dark net' is accessed using numeric ip's ...

but the custom dns server will control the casual user ...

---

### Post by goodbye-windows(tm) on 2013-01-20
WOW, this is all kinda scarey. I've always been concerned about privacy,  it's the primary reason I dumped the brand M operating system.

I  looked into proxy servers for masking my ip address-but it occurs to me  that they could turn around and covertly share info with any other web  sites that want to know the originating ip address. Additionally, if  they offer a free service, I don't understand how they keep their  service running. I don't think I'll use a proxy service.

Regarding  cookies and other similar privacy compromising technologies......rather  than trying to control cookies etc, wouldn't it be better to just feed  them false data??? During times when I am not using the internet, a  software package could direct my browser to go to websites at random,  click on a few links there and then move to another randomly generated  ip address and continue. This would create so much false data that the  websites that harvest the data wouldn't be able to tell the static from  the legitimate tracking data.

I have done some testing.......I  can change my ip address by resetting my modem and waiting for it to  issue a new ip address. I get a pretty wide variation in ip addresses  this way. 

My desire to be stealthy on facebook is not to partake  of their product. It is for the sole purpose of enabling me to read my  daughters posts to facebook. I have no interest in having facebook  'friends' or following other facebook users. My daughter is in a  boarding school, and she posts most of her exploits to facebook. SO,  it's easier for her if I can just follow facebook instead of calling her  constantly to figure out what's going on with her school activities.

I  read recently that Microsoft's Skype program has been caught red  handed....downloading the bois of the host computer. This gives them  access to a globally unique fingerprint (the serial number) that is 100  percent accurate. **Are there any other globally unique fingerprints in my computer that can thwart my effort to remain anonymous???**

TY.

Art

---

### Post by uRock on 2013-01-20
Is it me or is this being overly paranoid? Do you have Wireshark or TCP dumps that show evidence of Facebook retrieving data from the system? If you aren't posting private information on Facebook, then I see nothing to worry about.


If you want the ability to hide your IP address, then use the Tor browser bundle. [https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en) I use their browser in Windows and Ubuntu with ease.

---

### Post by Ms. Daisy on 2013-01-21
This makes no sense to me.  If you don't want Facebook to know anything about you then don't create an account.  (Or create a dummy account and invent the bare-minimum information).

If you allow your child to have a Facebook, then you should make them share the password with you.  Let them know you'll log in occasionally to see what's going on.  I can't understand why you'd want to observe your child secretly.

---

### Post by goodbye-windows(tm) on 2013-01-22
> **Ms. Daisy said:**
> This makes no sense to me.  If you don't want Facebook to know anything about you then don't create an account.  (Or create a dummy account and invent the bare-minimum information).

Hi Daisy,

I appreciate that it might seem odd to you. 

Basically, my daughter uses facebook, she's 16 years old and knows it all::> 

She uses linux, and avoids most of hte severe privacy issues associated with the Brand M operating systems. But, she uses facebook. 

I do not stalk her or spy on her. Her mom is one of her friends. I have chosen not to have a facebook account at all until such time as I can join facebook anonymously (easier said than done). 

> If you allow your child to have a Facebook, then you should make them share the password with you.  Let them know you'll log in occasionally to see what's going on.  I can't understand why you'd want to observe your child secretly.She's to old to have me babysit her by holding keys to her facebook page. I have told her I'll be joining her facebook, but anonymously. She's good with that, so I am in no way spying on her.

_**As you suggested, I have created a dummy account and will have joined facebook anonymously**_. This includes at least 2 anonymous web based email accounts, which have personal profiles that match the anonymous facebook profile. 

I have done this without relying on additional software and without involving additional persons or web "services". For example, I could use Tor to mask my IP address....but instead I change my ip address (manually) very often so that the ip address cannot be used for linking my everyday linux account with my stealth linux account.

Rather than trying to keep firefox from passing private data from one linux account to another, I have chosen to make a totally independent linux install on a separate partition. This separate linux install will be used exclusively for following my daughters facebook posts and for nothing else. 

So far, it's working great, I'm learning how to use facebook now.

At the present time, I'm stripping almost all the software from my stealth linux install. This keeps the stealth partition small, no need to tie up disk space. 

I'm going to go ahead and mark this one solved. I thank all for their input and contributions to this effort.

Art

PS:For Ms. Daisy......

You can google facebook privacy for more information on the methods facebook uses to track it's subscribers. 

If you really need proof, download a copy of 'collusion', an add on from firefox. Then log into your facebook account and watch as facebook distributes cookies. In less than 2 days, google has distributed cookies to about 80 other websites!!!! 'nuff said.

---

### Post by emiller12345 on 2013-01-22
.

---

### Post by uRock on 2013-01-22
> **goodbye-windows(tm) said:**
> If you really need proof, download a copy of 'collusion', an add on from firefox. Then log into your facebook account and watch as facebook distributes cookies. In less than 2 days, google has distributed cookies to about 80 other websites!!!! 'nuff said.

Adjusting browser settings will fix that. Using Private Browsing will prevent that. Installing a third party addon from an unknown source sounds more like a security issue than Facebook.

---

### Post by goodbye-windows(tm) on 2013-01-23
Interesting URock, 

Throughout the years, software has always  betrayed me in one way or another. So, you are correct, using third  party software that isn't opensourced is a risk.

Many of the Firefox add ons are opensourced however, which includes 'collusion'. 

There are many add ons I won't install because they are not open sourced.

The  most significant advantage of running linux (IMHO) is that it is  opensourced and the vast majority of the software used in linux is  opensourced too. 

Private browsing isn't very private....read the  fine print. Firefox's dirty little secret is that it still allows  websites to upload and execute active content on command. The user has  no idea what has been loaded into his system and what the active content  does within his system.

Firefox developers have openly admitted  that they can't program it to reject flash cookies. This is because  flash cookies are constantly changing how they hide. Wikipedia has an  outstanding article on flash cookies, including those types of flash  cookies that cannot be deleted by the user.

_**Rather than try  to patch firefox, I have chosen to install a complete linux system  inside an additional partition and to keep the stealth partition  biologically isolated from my primary (everyday) linux install. **_Seems much simpler to me-your mileage might vary.

I  am also considering doing a fresh install of linux on the stealth  partition and having Linux copy a clean firefox folder each time firefox  is opened. The clean copy would be saved from the new install, before  firefox has been allowed to access the internet. The entire firefox  folder would be deleted upon exiting firefox. This prevents any kind of  cookie, even forever cookies and various flash cookies from being saved  for later use by various websites. 

In the long run, I'd like to _**poison**_  my cookies and other personal info by intentionally creating stored  cookies and flash cookies that don't represent websites websites that  I've actually visited in the past.  Rather than making firefox immune to  cookies (flash and html), I think it would be much easier to create  'background noise' instead. This means I actually put google to work  preserving my privacy instead of having it take my privacy away.

I'm  still interested in any methods of fingerprinting that can make a link  between my everyday linux install and my stealth install. Such linking  could destroy the effectiveness of my entire stealth effort.

TY.

Art

---

