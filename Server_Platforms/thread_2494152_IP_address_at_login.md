---
title: "IP address at login"
date: 2024-01-07
forum: Server Platforms
---

### Post by johndid on 2024-01-07
Hi, 

My Ubuntu server 20.04 LTS machine used to show its IP address at the end of boot before login.
I don't know what is the problem with it now, but I only see:

[I]"Ubuntu 20.04.6 LTS server tty1
server login:"
[/I]
How can I make it show the IP again?
Thank you

---

### Post by TheFu on 2024-01-07
If it is a server, you should force it to have a static IP.

There are advertising scripts placed on systems by Canonical to be shown as part of the login process.  I always just create a ~/.hushlogin file (zero length) so I never need to see that crap.  It isn't like I didn't just login to the system, almost always using ssh, so I know the IP address.  From time to time, Canonical changes their advertising.  

[https://askubuntu.com/questions/217358/how-can-i-display-my-machines-ip-address-on-a-tty-login-screen](https://askubuntu.com/questions/217358/how-can-i-display-my-machines-ip-address-on-a-tty-login-screen) says that Debian supports showing the IP address from the /etc/issue file using \4 and \6 abbreviations. There's a little more to it since Debian 10, so you'll want to read that link.

---

### Post by johndid on 2024-01-07
> **TheFu said:**
> If it is a server, you should force it to have a static IP.

There are advertising scripts placed on systems by Canonical to be shown as part of the login process.  I always just create a ~/.hushlogin file (zero length) so I never need to see that crap.  It isn't like I didn't just login to the system, almost always using ssh, so I know the IP address.  From time to time, Canonical changes their advertising.  

[https://askubuntu.com/questions/217358/how-can-i-display-my-machines-ip-address-on-a-tty-login-screen](https://askubuntu.com/questions/217358/how-can-i-display-my-machines-ip-address-on-a-tty-login-screen) says that Debian supports showing the IP address from the /etc/issue file using \4 and \6 abbreviations. There's a little more to it since Debian 10, so you'll want to read that link.

It already has a static IP, but when the IP didn't show up at the boot I knew that there was something wrong with its Ethernet card or its connection in general (yes, my server machine behaves strangely from time to time). Without the IP showing at the boot, I don't get that information at once anymore.

Thanks

---

### Post by TheFu on 2024-01-07
You actually login on the console?  Wow.  After the install, I setup a static IP on my servers and never worry about it again.  From that point on, I always use ssh.  Perhaps in 30 yrs, there has been 3 problems with that.

---

### Post by johndid on 2024-01-07
> **TheFu said:**
> You actually login on the console?  Wow.  After the install, I setup a static IP on my servers and never worry about it again.  From that point on, I always use ssh.  Perhaps in 30 yrs, there has been 3 problems with that.

I always use ssh too, but it was not my point.

---

### Post by TheFu on 2024-01-07
Did the /etc/issue macro work?

---

### Post by johndid on 2024-01-07
> **TheFu said:**
> Did the /etc/issue macro work?

Yes, I just added:


[HTML]Ubuntu 20.04.6 LTS \n \l

enp6s0: \4{enp6s0}[/HTML]

to the  **/etc/issue** file and rebooted

Thank you.

---

### Post by TheFu on 2024-01-07
When an issue is solved, please use the Thread Tools button to mark it SOLVED.  This saves people time - both looking for answers and those wanting to help.

---

### Post by LHammonds on 2024-01-09
Here is a thread on how to add IP, weather and other info at login: [Ubunt Logo in color ASCII art](https://ubuntuforums.org/showthread.php?t=2385550)

---

### Post by MAFoElffen on 2024-01-12
LOL. I remember trying that when you posted it.

I added weather to my motd'd back o Server 10.04... I forgot about when I did that. I should do that again.

I had a post on Server VGA console theming: [https://ubuntuforums.org/showthread.php?t=1743535&p=11548061#post11548061](https://ubuntuforums.org/showthread.php?t=1743535&p=11548061#post11548061)

---

### Post by TheFu on 2024-01-12
There is a URL that generates ASCII art weather - use curl to pull it.
[https://wttr.in/Webster_TX?2FnT](https://wttr.in/Webster_TX?2FnT)

Sometimes the weather information from that URL is a little suspect.

I prefer to get the NOAA forecast for my location from the local airport and strip out all the extra junk from it.  It is far from elegant, just some fancy egrep filters after conversion from html to text.  [https://aviationweather.gov/](https://aviationweather.gov/) is the website for the US. Just provide your local airport's 4 letter code.
$ curl --silent --show-error 'https://aviationweather.gov/adds/metars/index?submit=1&station_ids=KEFD&chk_metars=on&hoursStr=1&std_trans=translated&chk_tafs=on'

Some of the airport codes get blocked to prevent abuse.  KEFD is one of those.

---

### Post by MAFoElffen on 2024-01-12
Dang you guys! Now you have me wanting to play with those again...

---

