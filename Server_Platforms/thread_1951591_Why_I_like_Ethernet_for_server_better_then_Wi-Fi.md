---
title: "Why I like Ethernet for server better then Wi-Fi"
date: 2012-04-02
forum: Server Platforms
---

### Post by roffisserver on 2012-04-02
Reason 1: It is a direct connection and is faster. If there is a problem  with the Wi-Fi your server won't go down. If you are running some type  of server off you desktop you could use Wi-Fi, if you didn't need it to  be up all of the time.:razz:

Reason  2: When you get a server all you need to do is plug the Ethernet in and  go. You don't have to worry about collecting all of your network data.  Whatever kind of Server OS you are installing(Ubuntu server, Redhat,  Windows Server,CentOS)you can be sure that it will support Ethernet.

Reason  3: Cheap! If you have never had a server before and want it to be easy  to setup, Ethernet is the way to go. All you have to buy is a cheap  cable. You don't have to go through a Wi-Fi setup process and get a  router that you think will last. If your server doesn't have a wireless  card you wouldn't have to get that too! But you can be sure that it has  Ethernet.

Conclusion: If you want my opinion Ethernet is the way to go. It is easy, simple, and is compatible with everything!


Check me out other places::KS
Twitter: @Ultimate_Coder
Email: ~snip~

---

### Post by jerome1232 on 2012-04-02
Putting your email in a public forum that is regualarly scoured by bots for emails and other personal information is a great way to get lots and lots of spam.

At the very least write it like (I'm not sure if some bots are smart enough to grab an email out of that or not)

#Ihatespam-Myemail AT somedomain dot com

---

### Post by rubylaser on 2012-04-02
Ethernet is the way to go with a server, but it's not all magical fairy dust as you make it sound.  A user will still need to manually edit /etc/network/interfaces if they'd like to use a static ip and still have a general idea of networking and their subnet to set it up. 

Also, some ethernet cards are not supported or supported very well, so they don't "always" work.  

I'm also not sure about the links to stuff you talked about, or why you put your contact info right in your post.

---

### Post by CharlesA on 2012-04-02
> **rubylaser said:**
> Ethernet is the way to go with a server, but it's not all magical fairy dust as you make it sound.  A user will still need to manually edit /etc/network/interfaces if they'd like to use a static ip and still have a general idea of networking and their subnet to set it up. 

Also, some ethernet cards are not supported or supported very well, so they don't "always" work.  

I'm also not sure about the links to stuff you talked about, or why you put your contact info right in your post.

What he said. Manually editing conf files in order to get a simple static IP might be a pain, but getting wifi working is worse.

Granted you can set a static IP during install, but I recall having to go back a screen or two after the installer grabbed an IP from dhcp..

@OP: Contact info and unnecessary links removed, if someone wants to contact you, they can PM you here.

---

### Post by roffisserver on 2012-04-02
Well I think editing those files is pretty easy.

---

### Post by rubylaser on 2012-04-02
> **roffisserver said:**
> 
Reason  2: When you get a server all you need to do is plug the Ethernet in and  go. You don't have to worry about collecting all of your network data.  Whatever kind of Server OS you are installing(Ubuntu server, Redhat,  Windows Server,CentOS)you can be sure that it will support Ethernet.

It is easy :) But certainly, not as easy as just plugging in the cable and going if you want a static ip as you would likely want on a server.  As CharlesA and you said though, it is WAY easier than setting up wireless and much more reliable as well.

---

### Post by CharlesA on 2012-04-02
DHCP reservation *COUGH* is even easier. ;)

Even tho I can do that, I prefer having a static IP on my server. Easier to deal with that way.

---

### Post by hawkmage on 2012-04-02
I use DHCP with a static mapping on many of my servers.  The only time I stay away from DHCP is when I am using virtual interfaces.

---

### Post by zeljkojagust on 2012-04-03
I think WiFi in the same pot with server technology is not worth a discussion. Tablets, phones and notebooks (netbooks) for entertainment are OK with WiFi, everything else, especially workstations and servers should be on at least gigabit ethernet.

---

### Post by CharlesA on 2012-04-03
> **zeljkojagust said:**
> I think WiFi in the same pot with server technology is not worth a discussion. Tablets, phones and notebooks (netbooks) for entertainment are OK with WiFi, everything else, especially workstations and servers should be on at least gigabit ethernet.
I suppose it depends on what you are using the workstations for. At the place I work, we've got almost everyone running off wireless from laptops.

Of course some might not consider laptops "workstations" but we've got developers who just hook them up to external keyboard/mice/monitor and do their thing.

---

### Post by a2j on 2012-04-03
in my world, server = reliability/availability. wifi can provide none of those.

---

