---
title: "Dial Up basics"
date: 2006-12-16
forum: The Cafe
---

### Post by kirenpillay on 2006-12-16
Hi

I would like to see the dial-up set-up mechanisms be brought up to the level found in Windows, more especially for Bluetooth dial-up and via USB cable.

There's no quick, intuitive way I can set up bluetooth dialup out the box like on Windows. To set up a bluetooth dial-up on Linux always means referring to a How-To somewhere on the net.

On Windoze, the bluetooth modem is automatically detected once I switch the phone's bluetooth on and pair with it. The relevant drivers for the modem are automagically installed. Then, all I do is create a new connection using the connection wizard. Intuitive, simple, easy no fuss. Why doesn't Ubuntu/Kubuntu have this capability? 

Small things like this hamper Linux adoption in the general public. This is where Windows outstrips Linux on the desktop, surely this can be changed?

---

### Post by an.echte.trilingue on 2006-12-16
Linux is pretty easy to use once you get used to it, but it is not and should not be exactly like Windows.  If it were, there would be no reason to use linux.  I would be willing to bet that you spent a lot of time learning to use windows, probably more that you realize.  Give Linux a fair shake by learning it and I think you will find it it pretty "intuitive" for most things as well.  For example, now that I am used to linux I find it unacceptable that I have to update all of my windows programs (even office, which is made by MS!) seperately instead of having one single package manager that takes care of all that.

In the case of your bluetooth modem, the reason is that the manufacturer did not write all these nice things for Ubuntu as they probably did for windows.  You need to take it up with them.

Also, do not forget that this stuff is written largely by volunteers or for corporate environments and if bluetooth modems do not interest them personally or if it is not needed in a corporate environment, they ain't gonna do it.

You could do it, though.

Take care,
-mat

---

### Post by xyz on 2006-12-16
[Windows-to-Linux roadmap: Overview]("http://www-128.ibm.com/developerworks/linux/library/l-roadmap.html")

---

### Post by kirenpillay on 2007-03-04
Hi People,

I reinstalled my machine with Ubuntu 6.10, hoping this would solve my problem, but no luck. I get an error when trying to authenticate. I've attached logs.

Here's an extract from the log I've attached. 

<snip>
Mar  4 22:55:44 shiva hcid[4550]: link_key_request (sba=00:10:60:A6:93:59, dba=00:12:37:3C:15:DC)
Mar  4 22:55:44 shiva hcid[4550]: pin_code_request (sba=00:10:60:A6:93:59, dba=00:12:37:3C:15:DC)
Mar  4 22:55:44 shiva hcid[4550]: call_passkey_agent(): no agent registered
</snip>

Its strange that no one else on this forum is experiencing it. There is a debian workaround using the passkey-agent, but this leads to another error regarding DBus, with a method "Request" not found in CallPassKeyAgent.  I'm guessing I'm on the wrong route.

Anyway, does anyone out there know how to overcome this problem? I'm desperate to get my Linux box running. Without internet access, I'm forced to use Windows.


Regards
Kiren

P.S: By the way, in South Africa and most third world countries, we don't have unlimited cheap bandwidth, so GPRS dial-up is a commonly used way to connect to the internet. There is ADSL etc, but this is too expensive (for me, average Joe)  so when Bluetooth doesn't work, i'm  pretty much screwed. I don't that this is as important in developed nations, but to us third world countries, it is. It would be nice if BT DUN was given a higher priority by the development team than it currently has.

---

### Post by racerx8518 on 2007-03-05
I'm having the exact problem. 
 I've found a couple of help pages but it took me 3 hours just to be able to connect the phone and push files over let alone using the dial up.

 Most of the helps deal with GPRS and not CDMA evdo which is what I use.

this one got me fairly far [http://www.spiration.co.uk/post/1307](http://www.spiration.co.uk/post/1307) 

My problem is the dial in number is #777 which stops the read I belive

---

