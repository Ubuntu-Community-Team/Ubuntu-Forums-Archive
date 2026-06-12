---
title: "Antyvirus or firewall"
date: 2010-10-03
forum: Security
---

### Post by Pat. on 2010-10-03
Hello,

I've recently installed Ubuntu 10 on my laptop and I'm not sure whether it's safe or not. My question is do I need any antyvirus or firewall to protect my pc against virus, spyware etc.?

---

### Post by rookcifer on 2010-10-03
> **Pat. said:**
> Hello,

I've recently installed Ubuntu 10 on my laptop and I'm not sure whether it's safe or not. My question is do I need any antyvirus or firewall to protect my pc against virus, spyware etc.?

AV not needed.  Firewall is only needed if you run a server of some sort (like SSH or VNC).  If you need a firewall look into gufw.

---

### Post by HermanAB on 2010-10-03
You don't really need anything extra.

See the Security sticky note above in the forum.

---

### Post by Pat. on 2010-10-03
Alright, but I frequently log in to my bank accounts through the internet, am I safe when I do it on Ubuntu?

---

### Post by krishnandu.sarkar on 2010-10-03
From your side : Yes..!!

---

### Post by adc100 on 2010-10-03
Along the same lines.my Router went bad.  What bad things could happen.  I am just a normal PC useer. I of course do online banking, investing and Credic Card purchases.

Thanks.
Al

---

### Post by Dex73 on 2010-10-03
There should be a fire wall that comes with ubuntu, but it's not active by default. I installed firestarter to easily turn it on.

NOTE: If you take this route, remember firestarter is for setting up a fire wall. You don't have to set firestarter it's self to start at dial up, just the fire wall.

P.S. It's extremely uncertain whether or not you even need it.

---

### Post by uRock on 2010-10-03
TO turn on the Firewall, simply open a terminal and enter **sudo ufw enable** For a GUI, install GUFW via the Ubuntu Software Center or **sudo apt-get install** gufw via a terminal.

Do not install Firestarter, as it has not been maintained for years.

Anti-virus is unnecessary unless you are sharing files with Windows systems.

For more info on security in ubuntu check out this link. [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by oregonbob on 2010-10-03
You may have heard that Windows is not recommended for online banking. Last spring the FBI advised people no longer use Windows PC's for online banking because fraud is so rampant. The best method is to use a Linux live CD, a Mac or Linux.

You can find lots of info about online banking and fraud on this security website: [http://krebsonsecurity.com/?s=online+banking&x=17&y=8](http://krebsonsecurity.com/?s=online+banking&x=17&y=8) read same author, Brian Krebs, on Washington Post: [http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html](http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html)

On Linux you are much safer but be sure to use good passwords and only install authenticated software. Don't underestimate the importance good passwords.

---

### Post by Ahava591 on 2010-10-03
You do not really need AV software; if you are sharing files with Windows users, (hopefully legally,) then I recommend you get some. Otherwise, there's no real need at this point in time. Also, the AV if you are sharing with Windows users is mostly for their benefit; it is all but impossible for malware written specifically for Windows to harm you. 

A software firewall is a good idea; I disagree that only server environments need it.
Ubuntu comes with one, however as has been stated, I don't think it's enabled, ("turned on,") by default. Somebody has already posted what you can do to turn the firewall on. A lot of people I know and I have seen it here recently recommend that you do not use Firestarter as a GUI.
-I do not know enough about it to talk about Firestarter; however, if you want a graphical user interface, GUFW is an option that is still maintained.

I believe the latest release of GUFW was in April or May of 2010.

There are stickied threads dealing with nothing but security in this sub-forum, they should be at the top. Please read these through first, if you then have questions feel free to ask. If you don't understand something you read, try searching for it in the forums using the search bar. If you still can't find it, or if you are still unsure about something, everybody here is here to help.

Good luck.

---

### Post by HermanAB on 2010-10-04
Yes, you can turn a firewall feature on in Ubuntu, but it won't really do anything beyond what the modern IP stack is already doing, so why bother?

---

### Post by Velnias on 2010-10-04
No need for antivirus on desktop. 
If Windows cannot defend against viruses you can catch by simple browsing or plugging in  a USB key, then, chances getting some from Ubuntu running boxes, is very tiny and makes no senses.

---

