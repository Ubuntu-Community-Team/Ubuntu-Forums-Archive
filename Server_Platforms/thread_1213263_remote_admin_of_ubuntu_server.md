---
title: "remote admin of ubuntu server"
date: 2009-07-14
forum: Server Platforms
---

### Post by kennedy7 on 2009-07-14
Hy guys, I have a server hosted at the ip 65.5.187.201 and unfortunately my php has crashed or something and I am not able to admin my server because i am on a vacation right now. But what happens when i browse to a php document such as [http://tyspage.doesntexist.com/info.php](http://tyspage.doesntexist.com/info.php) it returns with an error 500 internal server error. php has been working because almost all the pages i host are php. I recently switched from apache2 to lighttpd webserver but php still worked, until now. What id like to know is if there is a way i can remotely get into my server with some kind of admin tool other than telnet or ssh. I do have telnet on my server but i dont have any ports forwarded so i can only access that at my house. I am not looking to hack into any servers so i dont need a password bypass or anything, just a way to remotely admin my server. Otherwise my websites will be down for a while. Thanks guys

---

### Post by Vegan on 2009-07-14
Sounds like you have a flaky setup. My own IBM has run 24/7 like a charm. Sometimes it wants to be rebooted as 9.04 has automatic updates available and I use them.

My machine reboots fast enough so its not a problem.

I use TELNET for remote access, while criticized for security it works fine for me.

Others prefer to use SSL which is also criticized as well.

---

### Post by kennedy7 on 2009-07-14
Thats exactly why i dont make my telnet port available to just anybody "its a security breach" thats what most people hack into.
IS there any way i can access my server some way else? I have no way of working with it other than remotely so i cant just login and install stuff. Is there any way i can get in to my telnet without having the ports forwarded? Thanks

---

### Post by jeffathehutt on 2009-07-14
I don't think there is much you can do at this point...  If your router is blocking the ports, you would need a way to log into the router and forward the proper ports.  As far as I know, there is no 'back-door' to use.

Obviously when you get home, you should forward the ssh port (maybe run it on a non-standard port?) so this doesn't happen again.

If anyone knows differently, I'd like to hear it because I have often wondered about this myself.

---

### Post by R.Bucky on 2009-07-15
assuming this is a server edition rather than GUI? otherwise RDP at 5900.

---

### Post by dragos2 on 2009-07-15
> **R.Bucky said:**
> assuming this is a server edition rather than GUI? otherwise RDP at 5900.

Its filtered.

---

### Post by spynappels on 2009-07-15
While this does not help you right now, Webmin is worth a look for similar situations in the future. Still need to forward a port, but it is not the standard 22 port and can be accessed from any webbrowser through a https address.

Sorry I can't be of more help now though, I think you are stuck unless remote admin is enabled on your router on port 7080 or 7090 or something and you can get in to forward a port this way.

---

### Post by kennedy7 on 2009-07-15
Ok, thanks man, ill take a look at webmin. And other person, my server is just the server edition no GUI, but thanks, and you gota have port 5900 forwarded just like any other port.

---

### Post by kennedy7 on 2009-07-15
I have had one of my friends get into my telnet connection even without my ports being forwarded on my router, maybe there is a way. Dont know though, LOL thanks guys

---

### Post by -=hazard=- on 2009-07-15
Tell me where you live and I go forward the ports :D 

Joking

Anyway if you dont have any port forwarded you better forget the remote login untill you get home.

---

### Post by kennedy7 on 2009-07-15
Oh well, thanks anyway. What could be wrong though with the lighttpd? I mean it opens xml, html and folders but give 500 error when opening php. It has worked before and i havent done anything new

---

### Post by -=hazard=- on 2009-07-15
Never used  lighttpd, I prefer apache. Dont know what could have hapend

---

### Post by kennedy7 on 2009-07-16
Yes, i prefer apache2 also. But apache2 was to heavy for the work i was wanting my server to do. I host a private video sharing page that is a copy of youtube called ostube. I was trying to convert lots of video files at one time but my server kept running out of ram so i switched to lighttpd to do that and then when it was done i was going to switch back. I only used lighttpd because youtube uses it for there media serving/converting but apache2 is much more supportive for what i do.

---

### Post by koenn on 2009-07-16
long shot:
if you can remote admin your router, you can set up the port forwarding ...

---

### Post by kennedy7 on 2009-07-29
Never mind i am home now

---

