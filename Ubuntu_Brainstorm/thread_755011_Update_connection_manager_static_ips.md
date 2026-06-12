---
title: "Update connection manager static ips"
date: 2008-04-14
forum: Ubuntu Brainstorm
---

### Post by abrianb on 2008-04-14
When at work I tell friends about how much I like Ubuntu OS. I can't use it at work because I can't connect to the internet at work on my laptop unless I use windows. In windows I just set up a LAN connection . I filled in the blanks such as User Name, Password, Gateway, and the 5 static ips. The last is the problem with Ubuntu, no way to list more than one static ip address. Ubuntu works fine on this laptop at home using DSL from the same company as I use at work, With the only difference being that at home I have a dynamic address.
  If Ubuntu is to grow to be an acceptable OS for most people then connectivity needs to be very user friendly. 
  By the way, I made the connection in windows in about ten minutes having never done so before. The only information I had was an note scribbled out from the ATT tech saying " if you want to hook your laptop to the internet, there is an open cat 5 port on the back of the router" Then he listed User name, password, gateway and IPs.

---

### Post by Jussi Kukkonen on 2008-04-14
> I filled in the blanks such as User Name, Password, Gateway, and the 5 static ips. The last is the problem with Ubuntu, no way to list more than one static ip address. 

Abrianb, a computer can (normally) only have one IP address at a time... So that doesn't really make sense.

---

### Post by st4rdr1ft3r on 2008-04-14
it's done via eth0:0 (virtual interfaces) i believe. at least thats how i get additional ip addresses.

---

### Post by Jussi Kukkonen on 2008-04-15
st4rdr1ft3r, the point wasn't that it couldn't be done. The point was that it sounds like multiple IPs probably isn't what the OP actually wants -- they're definitely not a requirement to getting e network connection in the first place,

---

### Post by damoxc on 2008-04-15
Oh I totally agree it should be made far easier, I was just going by:
> I can't use it at work because I can't connect to the internet at work on my laptop unless I use windows
which implies that the OP was unable to give the interface additional IP addrsses.

(this is st4rdr1ft3r by the way, I made a new account)

---

### Post by abrianb on 2008-04-15
I have to enter all 5 ips on windows to establish the connection. I can't establish with Ubuntu. The set up is a wall socket with a phone line to a Netopia 4 port router model # 3346n-002. I just plug in  a cat 5 to one of the ports. The router gives me the first AVAILABLE IP. That is why I have to enter all 5. I have googled for a solution, posted on multiple forums, but still have not found an answer.

---

### Post by damoxc on 2008-04-15
if you edit /etc/network/interfaces to look something like:
[http://paste.ubuntu.com/7149/](http://paste.ubuntu.com/7149/)

that then you can setup multiple ip addresses on one interface. is that what you are looking for?

sorry if it's not.

---

### Post by abrianb on 2008-04-15
I think you have the correct answer on how it can be done. I thank you for the reply. I just have no idea as to how to get to where I can enter this information. I am very new to command line. As I said earlier, Ubuntu should Have an easier way of getting there. I am trying to learn more about using the terminal, and hope to become proficient. But I can tell you alot of folks will never open the Terminal.

---

### Post by Jussi Kukkonen on 2008-04-16
abrianb, I don't mean to irritate, but are you 100% sure you need multiple IPs? I cannot think of a single situation where a single IP would not give you an internet connection but five would...

> As I said earlier, Ubuntu should Have an easier way of getting there.
99.99% of users will never need this functionality. I'd be very surprised if Windows really does let you use several IPs from a GUI -- usually they hide obscure features like this as well...

Now that I start thinking about this... abrianb, are you by any chance referring to the five fields in this image when you talk about IP addresses: [http://portforward.com/networking/vista_static_ip_07.jpg](http://portforward.com/networking/vista_static_ip_07.jpg)? Again, I don't mean to get on your nerves, just making sure the problem's not something simple.

---

### Post by damoxc on 2008-04-16
Just incase you were wondering you add additional IPs in windows via the advanced button on that screen.

---

### Post by Jussi Kukkonen on 2008-04-17
> **damoxc said:**
> Just incase you were wondering you add additional IPs in windows via the advanced button on that screen.
ah, thanks for setting me straight (I shouldn't comment on Windows stuff, it's been a few years...)

---

### Post by abrianb on 2008-04-17
Jussi
 I really do need 5. One just will not work. I do hit the advanced Button as mentioned to list the additional 4. I looked on a windows 2000 pro machine and the set up was the same. So windows has had this for quite some time. I am guessing that the first available thing is to maximize resources. Lots of machines share this connection.

---

### Post by damoxc on 2008-04-23
Look at post #7, I posted an example /etc/network/interfaces file showing how to setup the multiple IP addresses.

---

