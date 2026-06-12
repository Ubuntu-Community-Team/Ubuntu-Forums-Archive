---
title: "newbie: Do I need Security?"
date: 2009-03-30
forum: Security
---

### Post by kernel89 on 2009-03-30
I've been switching on and off from Ubuntu to XP. The reason? I'm a graphic designer and frankly Photoshop is my right hand, and my wacom is my left.

But that's not the question, the following is:
My previous installation of windows was infested with spyware that could not be removed with your average spy removal tool, and even though I had a registry "fixer", my windows was filled with glitches, which I why I switched back to Ubuntu.

Now I haven't installed anything related to security on my Ubuntu however, do I need to? I've heard of Linux being SUPER safe, but should I still get an anti virus, spyware removal, firewall, etc...

If so, can you point me towards what I need exactly, for I am, as I might of mentioned on my Title; a newbie.

-Thanks in advance!

---

### Post by damis648 on 2009-03-30
In short: No. :popcorn: You shouldn't worry about viruses and spyware, it's not much of a concern in the linux world. For more information, see [this]("http://ubuntuforums.org/showthread.php?t=510812") thread.

---

### Post by Bakon Jarser on 2009-03-30
Also, Photoshop CS2 works fine in linux with wine.  I'll guess that since it's your right arm you're probably using something newer but I thought I'd mention it.

---

### Post by wsonar on 2009-03-30
you may want to at least install firestarter

---

### Post by bodhi.zazen on 2009-03-30
> **wsonar said:**
> you may want to at least install firestarter

Why would you advise that ? With a default installation of Ubuntu there are no significant open ports to firewall.

---

### Post by linuxuser21 on 2009-03-30
> **bodhi.zazen said:**
> Why would you advise that ? With a default installation of Ubuntu there are no significant open ports to firewall.

I use Firestarter.  I don't even need that?  How about for a precaution at least?

---

### Post by bodhi.zazen on 2009-03-30
Precaution against what exactly ?

I think education is best.

Take a look at this page : [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

If you can tell me what it is you want to use a firewall for, I can give you my advice on if firestarter is the tool for you.

But, assuming you are running a default installation of Ubuntu ad you have not installed any server(s) and you are behind a router, then no firestarter really does not do much for you. You are perfectly save without it.

---

### Post by linuxuser21 on 2009-03-30
Before 8.10, there was a lot of sites that Firestarter picked up though.

---

### Post by bodhi.zazen on 2009-03-30
> **linuxuser21 said:**
> Before 8.10, there was a lot of sites that Firestarter picked up though.

Umm ... what are you talking about ?

---

### Post by linuxuser21 on 2009-03-30
Whenever I went to certain sites, it would tell me IP addresses that it found.

---

### Post by binbash on 2009-03-30
Everyone needs security but default installation of ubuntu is secure enough for normal uses

---

### Post by bodhi.zazen on 2009-03-30
> **linuxuser21 said:**
> Whenever I went to certain sites, it would tell me IP addresses that it found.

I do not use firestarter so I have no idea what you are asking about here or why you feel you are in some way more secure because firestarter listed some ip addresses.

---

### Post by rage-against-windows on 2009-03-30
My wife uses XP along with a crap load of anti spyware, and anti virus programs and she still has to reformat about every 4-6 months. Out of habit and fear, I use Gfuw, and avast4linux. I scan my whole system, including the wine directories about once a week, and it always comes up squeaky clean. We both surf the same sites, and do about the same things online...download music, watch videos, ect, even use the same browser Firefox, yet she gets all this spyware and adware crap and I get nothing. So I would say Ubuntus about as safe as it gets for now.

---

### Post by Bakon Jarser on 2009-03-30
> Whenever I went to certain sites, it would tell me IP addresses that it found.

I think you are confused about what firestarter is.  It is just a GUI for interacting with IPTables which is the default firewall for Ubuntu.  If you just install it and don't change any of the configurations then really you haven't done anything to impact your security.

---

### Post by kernel89 on 2009-03-30
I somewhat knew that I didn't need any addtional software to protect my Ubuntu, but I'm glad I got great confirmation.

Thank You!

---

### Post by Woody70_06 on 2009-03-30
> **kernel89 said:**
> I somewhat knew that I didn't need any addtional software to protect my Ubuntu, but I'm glad I got great confirmation.

Thank You!

If you are really intrested in a firewall, Ubuntu 8.04 and 8.10 come with UFW(Uncomplicated Firewall) it is turned off by default but very easy to set up. I currently run it

It is Terminal only though, but VERY easy

To enable the firewall type:

    **sudo ufw enable**

To set the UFW default policy (Allow or Deny)
   
    **sudo ufw default deny**

You can replace deny with allow depending on your needs

**Deny**= means your firewall will "deny" all packets UNLESS your computer specifically requested them from the source...think NAT 

**Allow**= means it allows traffic though

To block or allow a specific port just type in the terminal

sudo ufw deny [insert port number]

for example, sudo ufw deny 22 would deny all traffic on port 22

sudo ufw allow [insert port number]

for example sudo ufw allow 22 would allow all traffic on port 22

more information on ufw here
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html")

ufw should be enough for most peoples needs I would think.

by the way i just recently converted over from Windows to Ubuntu full-time, Love the community here, and love the OS good job to all involved in both the forum and the OS itself.

I look forward to much learning on this forum. '

I hope that helps you out.

---

### Post by Bakon Jarser on 2009-03-30
> **Woody70_06 said:**
> If you are really intrested in a firewall, Ubuntu 8.04 and 8.10 come with UFW(Uncomplicated Firewall) it is turned off by default but very easy to set up. I currently run it



ufw is also not a firewall, just a frontend for IPTables.  IPTables comes installed by default and is setup to deny incoming connections by default so unless you need to change that or need additional rules there is no need to use it.  BTW I was very surprised to not have to add any rules in jaunty.  utorrent worked without me having to set up its port with ufw.

---

### Post by bodhi.zazen on 2009-03-30
> **Bakon Jarser said:**
> ufw is also not a firewall, just a frontend for IPTables.  IPTables comes installed by default and is setup to deny incoming connections by default so unless you need to change that or need additional rules there is no need to use it.  BTW I was very surprised to not have to add any rules in jaunty.  utorrent worked without me having to set up its port with ufw.

No, by default, UFW is disables and iptables allows all traffic.

As stated earlier, there are no open ports of significance so this is probably sufficient.

---

### Post by WatchingThePain on 2009-03-30
Relax mate,
You're not using windows now (and the nightmares are over!).
I came from windows too and I know it seems strange but viruses are not really a worry on Linux.

---

### Post by linuxuser21 on 2009-03-30
> **bodhi.zazen said:**
> I do not use firestarter so I have no idea what you are asking about here or why you feel you are in some way more secure because firestarter listed some ip addresses.

Wow, I apologize.  I was simply stating what has happened.

---

### Post by bodhi.zazen on 2009-03-30
> **linuxuser21 said:**
> Wow, I apologize.  I was simply stating what has happened.

No need to apologize and I did not intend to come across as harsh.

I was hoping to be able to teach you something is all.

---

### Post by Bakon Jarser on 2009-03-30
> **bodhi.zazen said:**
> No, by default, UFW is disables and iptables allows all traffic.

As stated earlier, there are no open ports of significance so this is probably sufficient.

Hmmmm....I guess I've always had ufw enabled before.  Good to know.

---

### Post by aysiu on 2009-03-30
In answer to the original question, yes you need security, but no you don't need antivirus or antispyware software.

Read bodhi.zazen's links.

---

### Post by jersoncito on 2009-03-31
[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

Its a nice Gui for ufw

---

### Post by bodhi.zazen on 2009-03-31
> **jersoncito said:**
> [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

Its a nice Gui for ufw

gufw is in the Ubuntu repositories as of 8.10.

---

### Post by kernel89 on 2009-03-31
I have another question as well. It's, well I guess you can say also related to security.

Anyway, you know how you would do some weekly maintenance with windows: (clean the drive, defragment, run the registry cleaner tool, so on so forth...)

Do I need to know anything about ubuntu maintenance? Although apparently ext3 file systems don't need defragmenting tools nor has it registries...so what can I so to keep it in tip top shape?

Oh and thanks for the previous support guys!

---

### Post by bodhi.zazen on 2009-03-31
You do not need to do anything like that with Linux.

If you like, look at these :

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

    [http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

    [http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

9.04 has a cleaning tool "janitor" under system -> administration

---

### Post by DarkReaper79 on 2009-03-31
> **WatchingThePain said:**
> Relax mate,
You're not using windows now (and the nightmares are over!).


I had to put that in my sig. Thats great. But back on topic, no need to worry. Just dont open ports that you dont need to be opened. I can go to those port scanning sites, and it cant see any.

---

### Post by WatchingThePain on 2009-03-31
Thank you..it is an honour;)

---

### Post by kernel89 on 2009-03-31
Yeah, the only port I have oppened is the Transmission's one, for I am port forwarding.

---

### Post by Peasantoid on 2009-03-31
While it isn't *necessary* to install any kind of security system (at least not yet), a popular argument for doing so is that it'll prevent you from unwittingly passing on malware to Windows users. I just run the occasional scan on my home directory with clamscan (part of ClamAV: sudo apt-get install clamav).

---

### Post by wsonar on 2009-04-09
> **bodhi.zazen said:**
> Why would you advise that ? With a default installation of Ubuntu there are no significant open ports to firewall.

I like to  see the ip's being blocked

just today I had 3 blocked connections they could have been snmp tring to push out an update thinking it was a window machine
but I like to see the attempted connections

---

### Post by wsonar on 2009-04-09
I use ufw on the server

---

### Post by connorh123 on 2009-04-09
As said earlier, it is actually impossible to get a virus onto Linux. So, to wrap this all up, you do not need security unless you feel you must.

---

### Post by wsonar on 2009-04-09
> **wsonar said:**
> I like to  see the ip's being blocked

just today I had 3 blocked connections they could have been snmp tring to push out an update thinking it was a window machine
but I like to see the attempted connections

all though it is not needed  I just like to see the attempts for curiosity sakes

---

### Post by lisati on 2009-04-09
There is no substitute for caution and good sense.

---

