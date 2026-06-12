---
title: "The Register: WEP hacking is even faster now"
date: 2007-05-15
forum: The Cafe
---

### Post by PartisanEntity on 2007-05-15
According to [The Register]("http://www.theregister.co.uk/2007/05/15/wep_crack_interview/"):

> 
Last month, three researchers, Erik Tews, Andrei Pychkine and Ralf-Philipp Weinmann developed a faster attack (based on a cryptanalysis of RC4 by Andreas Klein), that works with ARP packets and just needs 85,000 packets to crack the key with a 95 per cent probablity. This means getting the key in less than two minutes.

---

### Post by starcraft.man on 2007-05-15
Yup, seen this before. Can't say its much of a surprise, WEP was crackable before in under 5-10 minutes. Now its just that much faster. The truth is with the ability to bypass WEP that easily for free, WEP is dead and anyone using it is doing the equivalent of an unprotected wireless point, especially since completely automatic programs can do it for any lamen.

If you want to be protected, you need WPA + TKIP (AES if you want increased protection, but its hardware intensive, TKIP is light). And make sure your passphrase for WPA is strong, since you input it only once, you never have to worry about it. I recommend [this]("https://www.grc.com/passwords.htm") place for WPA passwords.

Oh, and it can be even less than 2 minutes, I saw it done in front of me in just over a  minute >.>.

---

### Post by wieman01 on 2007-05-15
> **starcraft.man said:**
> If you want to be protected, you need WPA + TKIP (AES if you want increased protection, but its hardware intensive, TKIP is light).
Nah... not anymore. You should not worry about hardware performance nowadays. AES works on basically any computer these days without impacting its performance. It's a small price given its benefits.

---

### Post by starcraft.man on 2007-05-15
> **wieman01 said:**
> Nah... not anymore. You should not worry about hardware performance nowadays. AES works on basically any computer these days without impacting its performance. It's a small price given its benefits.

Its true, I was kinda referring to much older hardware... and there are some routers I believe that don't support AES at all. TKIP is good enough, AES is just better when it comes to security. Neither have been cracked when a good password is used though :)

---

### Post by wieman01 on 2007-05-15
> **starcraft.man said:**
> Its true, I was kinda referring to much older hardware... and there are some routers I believe that don't support AES at all. TKIP is good enough, AES is just better when it comes to security. Neither have been cracked when a good password is used though :)
Yeah... AES is an overkill indeed, but one that comes at a low cost. I have heard TKIP being susceptible to brute force dictionary attacks as well, but with a weak password any encryption/authentication method is I believe. So I guess my insisting on AES is a bit academic for ordinary users/home networks. ;-)

---

### Post by Jonne on 2007-05-15
> **starcraft.man said:**
> Oh, and it can be even less than 2 minutes, I saw it done in front of me in just over a  minute >.>.
What app is used for that? I tried cracking my own AP with airsnort once, and it didn't work, even after running it for days... And can I install it through apt ;) ?

---

### Post by wieman01 on 2007-05-15
> **Jonne said:**
> What app is used for that? I tried cracking my own AP with airsnort once, and it didn't work, even after running it for days... And can I install it through apt ;) ?
Aircrack-ng that is. There is also a modified version of it that implements the algorithm suggested by Erik Tews, Andrei Pychkine and Ralf-Philipp Weinmann. But Aircrack-ng will do.

---

### Post by PartisanEntity on 2007-05-15
I use WPA encryption as well as mac address filtering, ip number limitation and reservation. That way even if someone happens to manage to crack the password they will still have a hard time accessing the network; their mac address won't be accepted and they wont be leased an ip number since all are reserved and any excess one's are not assigned.

---

### Post by G Morgan on 2007-05-15
Yeap, registration on top of encryption is the way to go.

---

### Post by Polygon on 2007-05-15
i was very surprised that the program to crack WEP networks was in the ubuntu repos. 

I still use WEP, its my dads decision and he knows that it can be cracked really easily. But whatever...

---

### Post by B. Gates on 2007-05-15
When I was running Linux, the only encryption I could select from the Network Manager was WEP, but in Windows I get the whole gamut due to proper driver support. Figures. :(

---

### Post by wieman01 on 2007-05-16
> **PartisanEntity said:**
> I use WPA encryption as well as mac address filtering, ip number limitation and reservation. That way even if someone happens to manage to crack the password they will still have a hard time accessing the network; their mac address won't be accepted and they wont be leased an ip number since all are reserved and any excess one's are not assigned.
MAC filtering, hidden broadcast of ESSID, and static IP ranges do not offer any sort of protection at all. Those are false friends.

There are the tools to circumvent these alleged security measures:

[LIST]
[*]_**MAC filtering:**_ Use Airodump to determine valid client MAC address and simply clone MAC address (iwconfig, hwaddr).
[*]_**Static IP:**_ Kismet enables you to determine IP ranges of wireless networks around you.
[*]_**Hidden ESSID:**_ Again Airodump lets you find out about the real name of a network as soon as one of the clients try to associate.
[/LIST]
That said, the only measure you can take against serious/potential crackers is to use WPA (possibly WPA2 with AES) with a good, strong password. Apart from this, there is nothing that would add to overall network security. Amen. ;-)

---

### Post by Spr0k3t on 2007-05-16
WPA2 with a massive rot13(passphrase) is my primary line of defense.  However, I layer that with hidden ESSID, MAC filtering, and limiting static IPs to the devices in the house.  Granted WPA2 is effective, but it's good to have layers to keep everything locked down.  I do have a wide open low power AP which barely submits a signal so I can use a few wireless devices which don't work well with WPA2.

---

### Post by Tom Mann on 2007-05-16
> **B. Gates said:**
> When I was running Linux, the only encryption I could select from the Network Manager was WEP, but in Windows I get the whole gamut due to proper driver support. Figures. :(

I found that with Ubuntu too, but if you set your wireless connection to turn roaming on, it finds the WPA and asks for the key :)

---

### Post by stuman on 2007-05-16
Smith and Wesson security.  I have square piece of property approximately 1.5 acres.  If you're in range, you're in range.8) :twisted:

---

### Post by wieman01 on 2007-05-16
> **stuman said:**
> Smith and Wesson security.  I have square piece of property approximately 1.5 acres.  If you're in range, you're in range.8) :twisted:
Not sure what that's supposed to mean...

---

### Post by Jonne on 2007-05-16
A Smith and Wesson is a gun. I don't think it's legal to shoot someone for using your AP, though. (Except maybe in Texas).

---

### Post by wieman01 on 2007-05-16
> **Jonne said:**
> A Smith and Wesson is a gun. I don't think it's legal to shoot someone for using your AP, though. (Except maybe in Texas).
I know it is. That's exactly why I am asking.

---

### Post by koshatnik on 2007-05-16
I got rid of my wireless connection and went back to wired.  I don't care about accessing the internet in my kitchen or wherever. Rather have the security of wired.

---

### Post by imgsmall on 2007-05-16
Heh... pretty lucky around my way.  I've got 4 WPA networks within range, and a whooping 6 WEP :P

---

### Post by PartisanEntity on 2007-05-16
> **wieman01 said:**
> Not sure what that's supposed to mean...

It means in order for someone to access his wifi router they would have to trespass on his property, which is where the gun comes in.

---

### Post by wieman01 on 2007-05-16
> **PartisanEntity said:**
> It means in order for someone to access his wifi router they would have to trespass on his property, which is where the gun comes in.
Lovely... That's what I call (wireless) security. It's ironic. Anyway, back to the topic.

---

### Post by PartisanEntity on 2007-05-16
IMO the method I have set up, which I described in one of my earlier posts, is more than sufficient despite the existence of certain tools that can circumvent the barriers I have set up.

However, the more barriers we can place in the path of a hacker the more value a target needs to have in order to justify spending the time to hack it.

For example, I do not have any valuable data that anyone could steal, so there is no real incentive for someone to sit outside my house all day taking down one barrier after another.

This is especially heightened since my neighbour has a fully open and unprotected wifi network (which my laptop sometimes connects to without my input when it can't connect to my own wifi network).

---

### Post by wieman01 on 2007-05-16
Putting identity theft and data protection aside one should never give others access to his/her network for the simple reason that intruders might utilize the access point to do illegal stuff e.g. download videos, use someone's else credit card to purchase staff, etc. At the end of the day you might face a situation where you need to prove that you are innocent just because you have given somebody else a free ride. That's what I am most concerned about.

---

### Post by aysiu on 2007-05-16
> **starcraft.man said:**
> The truth is with the ability to bypass WEP that easily for free, WEP is dead and anyone using it is doing the equivalent of an unprotected wireless point, especially since completely automatic programs can do it for any lamen. It may be the equivalent for people who *care* to crack WEP, but for the average neighbor who's trying to steal some wireless bandwidth willy-nilly even researching and obtaining the "automatic program... for [laypeople]" is a bit too much effort--so, no they are not equivalent.

---

### Post by Sunnz on 2007-05-16
Vpn...

---

### Post by punkrokk on 2007-08-08
great stuff, can't wait for an attack on WPA better than rainbow tables (although they rock)

---

### Post by punkrokk on 2007-08-08
google church of wifi for more info

---

### Post by tanalyw on 2008-06-18
Hi, I was trying to figure out how does the cracking process works. Anyone knows how does the maths formula works?

All information is from [http://eprint.iacr.org/2007/471.pdf](http://eprint.iacr.org/2007/471.pdf) - page 76

E.g Key used = 12; 111; 28; 107; 226; 211; 232; 247

FKlein(12; 11; 28; 251) = S3^-1 [3 - X[2]] - (S3[3] + j3)
= S3^-1 [3 - 251] - (3 + 154)
= S3^-1 [8] - 157
= 8 - 157
= 107
= K[3]

I would like to ask the following questions if anyone of u can help. Thanks.
1. how S3^-1 [3 - 251] - (3 + 154) become S3^-1 [8] - 157 ??
as in how does S3^-1 [3 - 251] = S3^-1 [8] ??

2. And lastly, how do S3^-1 [8] become 8? and how come 8 - 157 gives 107??

Thanks.

---

### Post by Nessa on 2008-06-18
I work for a network devices manufacturer. We don't recommend WPA to our customers unless they have really old laptops or other hardware (printer, pda, etc) that can't handle Wifi Protected Access.

Just a thought, the customers I've worked with who use Linux - are in fact using Ubuntu. Makes me smile. :-D

---

### Post by ians1 on 2008-06-18
I tried using WPA in ubuntu but could not get it to work, hence WEP.

ian

---

### Post by PmDematagoda on 2008-06-18
Thread closed.

---

