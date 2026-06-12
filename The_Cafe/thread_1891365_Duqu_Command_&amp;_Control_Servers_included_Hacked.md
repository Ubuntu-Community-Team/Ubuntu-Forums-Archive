---
title: "Duqu Command &amp; Control Servers included Hacked Linux Systems by D. Dieterle"
date: 2011-12-05
forum: The Cafe
---

### Post by cap10Ibraim on 2011-12-05
Some very interesting information was released yesterday in a follow up [Duqu analysis report]("https://www.securelist.com/en/blog/625/The_Mystery_of_Duqu_Part_Six_The_Command_and_Control_servers") by Kapersky Labs. Highlights from the article include:
 
[LIST]
[*]*The Duqu C&C servers operated as early as November 2009.*
[*]*Many different servers were hacked all around the world, in  Vietnam, India, Germany, Singapore, Switzerland, the UK, the  Netherlands, Belgium, South Korea to name but a few locations. Most of  the hacked machines were running CentOS Linux. Both 32-bit and 64-bit  machines were hacked.*
[*]*The servers appear to have been hacked by bruteforcing the root  password. (We do not believe in the OpenSSH 4.3 0-day theory – that  would be too scary!)*
[*]*The attackers have a burning desire to update OpenSSH 4.3 to version 5 as soon as they get control of a hacked server.*
[*]*A global cleanup operation took place on 20 October 2011. The  attackers wiped every single server which was used even in the distant  past, e.g. 2009. Unfortunately, the most interesting server, the C&C  proxy in India, was cleaned only hours before the hosting company  agreed to make an image. If the image had been made earlier, it’s  possible that now we’d know a lot more about the inner workings of the  network.*
[*]*The “real” Duqu mothership C&C server remains a mystery just like the attackers’ identities.*
[/LIST]
 Wait just a minute, “*Most of the hacked machines were running CentOS Linux*“. Linux gets hacked? For those of you who think that Linux is invulnerable, this may be an eye opener.
 What is interesting though is how did they  do it? This leads to more questions. A recovered sshd log from a server  in Germany caught what might be evidence of a brute force password  attack:
[IMG]https://www.securelist.com/en/images/pictures/klblog/208193282.png[/IMG]
But what is odd too is that as soon as  they logged in, one of the first things done was to update OpenSSH (used  for remote access) from 4.3 to 5, as this snip from a recovered Bash  shell history shows :
 [IMG]https://www.securelist.com/en/images/pictures/klblog/208193276.png[/IMG]
 This has led to quite a debate, some  saying that the hackers got in using an OpenSSH Zero Day exploit, while  others claiming that they just needed the updated features of 5 to make  command and control more uniform across the board.
 Also interesting is to see how many times  help files and manuals are referenced in the above capture. Why would  the all powerful Stuxnet attackers who breached Iran’s secure nuclear  facilities and have created several 0-day attacks need to reference help  files so frequently?
 The simple solution is that they probably  were not as familiar with this distribution of Linux. Most likely they  were more familiar with Red Hat Linux Enterprise Linux which CentOS is  based on.
 Be it brute force password hacking or  another Stuxnet 0-Day, Duqu shows that Linux is vulnerable to hackers  too. And with it’s growing install base, supplanting Windows desktops in  many facilities, expect it to become even more of a target.

---

### Post by Dry Lips on 2011-12-05
Really interesting stuff. Thanks a lot for posting! I especially thought that the Kapersky blog post that was referred to was a good read.

[https://www.securelist.com/en/blog/625/The_Mystery_of_Duqu_Part_Six_The_Command_and_Control_servers](https://www.securelist.com/en/blog/625/The_Mystery_of_Duqu_Part_Six_The_Command_and_Control_servers)

---

### Post by Paqman on 2011-12-06
> **cap10Ibraim said:**
> 
 Wait just a minute, “*Most of the hacked machines were running CentOS Linux*“. Linux gets hacked? For those of you who think that Linux is invulnerable, this may be an eye opener.

This is actually pretty common. People get confused by the fact that there aren't any threatening Linux viruses in circulation. Hacking and viruses are completely different threats. Any OS can be hacked.

Linux is a primary target for hacking attempts of this type, because it's installed on so many servers. A powerful web-facing machine that's always on and can handle large amounts of traffic is a very attractive target for hackers.

---

### Post by F.G. on 2011-12-06
really interesting article. a nice look into how forensics and hacking actually work.

---

### Post by Dangertux on 2011-12-06
Funny how it's brute force SSH. I love that sysadmins let that happen so frequently.

BTW if you guys liked that you should check out the rest of his blog, Dan is a good friend of mine and has some really great posts about forensics.

[http://cyberarms.wordpress.com](http://cyberarms.wordpress.com) is his site.

---

### Post by Paqman on 2011-12-07
> **Dangertux said:**
> Funny how it's brute force SSH. I love that sysadmins let that happen so frequently.


Can't say that I'm surprised. When I opened up to SSH on my NAS my logs instantly filled up with brute force attempts from far and wide, it's a bit of an eye-opener how ubiquitous it is.

---

