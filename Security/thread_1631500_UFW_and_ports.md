---
title: "UFW and ports"
date: 2010-11-26
forum: Security
---

### Post by Axolotl9250 on 2010-11-26
Hi all,

I'm going on a sort of security drive on my computer as so far with all my distro's I've never bothered to secure them more than the default, and I don't use any ssh or remote services.

I've just addded a lot more ad and script blocks to Firefox and I'm up to UFW and gufw, I had a look at [HTML]https://www.grc.com/x/ne.dll?rh1dkyd2[/HTML] which told me that every port up to 1055 is a stealth port, currently gufw says all incoming is denied and all outgoing is allowed, but nothings stopped working. Could anyone explain this port business to me (it's very very new to me) and what needs stopping or allowing, or as my systems probably a bit different, a way I can find out which ports are open and what ones I want allowed or blocked. Preconfigured rules available to me in gufw include services and programs, and theres a selection from ssh to FTP, to qTorrent. A lot of stuff I'm reading says to use a firewall and check ports, but doesn't really explain the significance and reasons behind it, and how to do it.

Thanks,
Ben.

---

### Post by spiky001 on 2010-11-26
Have you read the stickey at the top of this forum on security there will be a lot of info in there, as a rule unless you are running a service as ssh " you said you wern't then a firewall is not needed also if you are behind a router they have built in FW normally

---

### Post by OpSecShellshock on 2010-11-26
The reason everything still works is that under a default configuration, any connections that are initiated by you or that are related to connections initiated by you will be allowed. Connections initiated from external sources will not be allowed.

---

### Post by Axolotl9250 on 2010-11-26
Hi thanks, that's good to know, reading the security guides for Ubuntu, I don't believe I saw a way/command to view active ports and such. How would I do this? out of pure interest?

---

### Post by bodhi.zazen on 2010-11-27
> **Axolotl9250 said:**
> Hi thanks, that's good to know, reading the security guides for Ubuntu, I don't believe I saw a way/command to view active ports and such. How would I do this? out of pure interest?

There is more then one way to answer this

netstat -an | grep LISTEN | grep -v ^unix

netstat -ntulp

lsof -i -n -P

---

### Post by SeijiSensei on 2010-11-27
You can use **nmap** to scan for open ports.  If you run it from an external machine, you'll see what's open to the Internet.  (sudo apt-get install nmap)

---

### Post by halloween2311 on 2010-11-27
> **Axolotl9250 said:**
> Hi all,

Could anyone explain this port business to me (it's very very new to me) 


I'm not sure how basic you would like to go on learning about ports but I would suggest that for a basic understanding you check out Security Now Episode #43 (Open Ports) at GRC (the same site you used to test your firewall.)

Here is the URL:
[http://www.grc.com/securitynow.htm](http://www.grc.com/securitynow.htm)
With links to text and audio files.  This show is windows-centric but still covers a lot of great basic ideas that are cross platform.

Hopes this helps! :-)

---

### Post by bodhi.zazen on 2010-11-27
> **SeijiSensei said:**
> You can use **nmap** to scan for open ports.  If you run it from an external machine, you'll see what's open to the Internet.  (sudo apt-get install nmap)

If you want a graphical interface, use zenmap =)

---

