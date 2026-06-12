---
title: "[SOLVED] Is Ubuntu secure enough for Online Banking?"
date: 2005-05-03
forum: Server Platforms
---

### Post by John H on 2005-05-03
I am currently a very happy (K)Ubuntu user.
As such, I have decided to convert 3 Window$ computers at work to Ubuntu.
However, one of them is used for all the Company's Banking via a browser interface.

Question 1. Is the default install of Ubuntu secure enough for Online Banking?
Question 2. Is Konqueror's web interface secure enough for Online Banking?

I installed Firestarter but it doesn't seem to be logging anything. I am considering using Shorewall. 

Any thoughts, suggestions, tips, comments etc are extremely welcome.
------------------------------------------------------------------------------------------------------------------
Current (hopefully former) shellshocked Windoze user.
Former Mandrake, Red Hat, Fedora, FreeBSD user

---

### Post by SamH on 2005-05-03
I'm pretty sure that Konqueror has the necessary security.

Besides, you can always apt-get Firefox.

---

### Post by nocturn on 2005-05-04
[QUOTE=John H]I am currently a very happy (K)Ubuntu user.
As such, I have decided to convert 3 Window$ computers at work to Ubuntu.
However, one of them is used for all the Company's Banking via a browser interface.

Question 1. Is the default install of Ubuntu secure enough for Online Banking?
Question 2. Is Konqueror's web interface secure enough for Online Banking?

I installed Firestarter but it doesn't seem to be logging anything. I am considering using Shorewall. 

Any thoughts, suggestions, tips, comments etc are extremely welcome.
------------------------------------------------------------------------------------------------------------------
Current (hopefully former) shellshocked Windoze user.
Former Mandrake, Red Hat, Fedora, FreeBSD user[/QUOTE]

Yes it is.

---

### Post by hashimoto on 2005-05-04
I would say it is at least as secure as Windows.

I would rather worry about the way that your bank has arranged the online banking. There have been phishing scams going on and I must say I'm a bit amazed that they are succesfull. The way that online banking seems to be made elsewhere is a mystery to me, but as I have understood it you have a user id and a password (not changing) and with the combination of these you can do anything. I might be wrong, though.

How does my bank do it: I have a user id that is not changing. I have password which is different every single time I log in (bank sends me a list by snailmail). And before I can make any payments or money transfers effective I must enter another changing password. Nothing happens if I don't enter it.

The thing is, any system can be breached (more or less easy). If you are using constant user id's & passwords for online bankin, then you are in danger. I've been wondering why the changing password scheme does not seem to be used elsewhere. It makes phishing so much more difficult, if not impossible.

---

### Post by dave9191 on 2005-05-04
When you connect to your banks site, an encrytped connection is established. So you dont have to worry about people intercepting your data, and you can assume that the banks computers will be secure. And there are no trojans that nick your bank details around for linux yet. So your safe from that angle. 

I use firefox and Im not worried one little bit. 

And you can always set up a firewall just in case there are any bugs that let people take control or peak into your computer. But you have numbers on your side now. People wont be trying to find linux machine and exploit them, they are too rare atm.

---

### Post by az on 2005-05-04
Many of these sites use browser detection to "enhance" their security.  Konqueror may give you a prblem here.  Mozilla and it's family are fine.  Firefox (Hoary) will identify istelf as firefox and everybody uses firefox...

Mozilla is also available...

You can always install the user ID switcher in Konqueror or firefox...

---

### Post by jdong on 2005-05-04
I recommend using Firefox for this purpose. Konqueror is a much less used browser, which would make it have less code review scrutiny, possibly meaning more bugs. Furthermore, Banking type sites typically do browser version checks, and would only work with IE/Netscape. Since Firefox is close enough to Netscape, you'll get by ;)

---

### Post by Psquared on 2005-05-04
I use Firefox to access my online banking and it works fine. I change my password about every month or two, and I've not had any problems.

---

### Post by John H on 2005-05-04
[QUOTE=jdong]I recommend using Firefox for this purpose. Konqueror is a much less used browser, which would make it have less code review scrutiny, possibly meaning more bugs. Furthermore, Banking type sites typically do browser version checks, and would only work with IE/Netscape. Since Firefox is close enough to Netscape, you'll get by ;)[/QUOTE]

I use Firefox & Moz on Windoze, however, the Bank's website doesn't display correctly,
i.e., not all banking fuctions are available.
I was hoping Konqueror would be suitable. 
What about Opera ? Any thoughts there?

---

### Post by John H on 2005-05-04
[QUOTE=John H]I use Firefox & Moz on Windoze, however, the Bank's website doesn't display correctly,
i.e., not all banking fuctions are available.
I was hoping Konqueror would be suitable. 
What about Opera ? Any thoughts there?[/QUOTE]

News Flash.
I had a look at the Banks's supported Browsers, only IE & Netscape
Doesn't seem to an Netscape in synaptic.
Question; Do I really want to run IE via wine ? Hmmmm.

---

### Post by jdong on 2005-05-04
Netscape = Mozilla = Firefox, more or less. It'll work. You may have to fudge User Agents a bit (Firefox has a plugin to do that!)

---

### Post by mohaham on 2005-05-04
Firefox is as much secure as IE.

---

### Post by maqi on 2005-05-05
[QUOTE=mohaham]Firefox is as much secure as IE.[/QUOTE]

Firefox is MORE secure than IE. No Active X for starters. 

Interestingly, I recall a thread in these forums somewhere about installing Active X for Firefox :eek: Kind of negates one of the main benefits of using a browser other than IE.

maqi

---

### Post by UbuWu on 2005-05-05
[QUOTE=hashimoto]I would say it is at least as secure as Windows.

I would rather worry about the way that your bank has arranged the online banking. There have been phishing scams going on and I must say I'm a bit amazed that they are succesfull. The way that online banking seems to be made elsewhere is a mystery to me, but as I have understood it you have a user id and a password (not changing) and with the combination of these you can do anything. I might be wrong, though.

How does my bank do it: I have a user id that is not changing. I have password which is different every single time I log in (bank sends me a list by snailmail). And before I can make any payments or money transfers effective I must enter another changing password. Nothing happens if I don't enter it.

The thing is, any system can be breached (more or less easy). If you are using constant user id's & passwords for online bankin, then you are in danger. I've been wondering why the changing password scheme does not seem to be used elsewhere. It makes phishing so much more difficult, if not impossible.[/QUOTE]

My bank gives out a little device with the size and looks of a small calculator, in which you have to put your bank card. Then the device asks for your pincode (which is the same number you use for atm's). Then it gives you a 8 digit number which is the password you have to use to get into the system.

When you want to make a transaction you have to do the same thing again, but then you also have to type on the device an other 8 digit number which is shown on the screen before it gives you the required code.

Seems to me that this is a lot more secure than sending passwords by snailmail...

---

### Post by kosmic on 2005-05-07
for extra security when acessing online banks use a virtual keyboard to avoid keyboard sniffers.

just search in synpatic, sorry but I don't remember the name of the aplication (virtualkeyboard).

---

### Post by Martin Witte on 2005-05-07
For the suspicious minds: do not store your bank account number, card number etc. when offered - then it is quite hard for a phising scam if it succeeds to find useful information on your machine in cookies. If you're really suspicious: take an old machine, install Ubuntu on it - and use it only for banking, use your new machine for other internet activities.

---

### Post by RastaMahata on 2005-05-07
I always install firefox when connecting to my bank account from another computer running Windows, as I've grown tired of IE security holes.

Before connecting from a 3rd party PC, I disable the saving of passwords, forms and history (lets say I disable everything except for cookies If I am in another PC). After I've done my things, I just clean the cookies :)

---

### Post by fishfork on 2005-05-08
If you're really really suspicious, or even paranoid, then boot from a live CD like Knoppix (is there a Ubuntu one?) before you do any online banking. This way even if your hard disk is teeming with viruses and rootkits, they won't affect it.

---

### Post by mohaham on 2005-05-09
[QUOTE=fishfork]If you're really really suspicious, or even paranoid, then boot from a live CD like Knoppix (is there a Ubuntu one?) before you do any online banking. This way even if your hard disk is teeming with viruses and rootkits, they won't affect it.[/QUOTE]

Yes, Ubuntu has a live CD too.. and Firefox is the default web-browser on it..
I agree this is a good idea for Online-Banking...

---

### Post by dave9191 on 2005-05-09
[QUOTE=mohaham]Yes, Ubuntu has a live CD too.. and Firefox is the default web-browser on it..
I agree this is a good idea for Online-Banking...[/QUOTE]

You might not want to use a live cd because the versions will be out of date and not patched on that. And you want to make sure you are using upto date software. 

Dave

---

### Post by TravisNewman on 2005-05-09
*"My bank gives out a little device with the size and looks of a small calculator, in which you have to put your bank card. Then the device asks for your pincode (which is the same number you use for atm's). Then it gives you a 8 digit number which is the password you have to use to get into the system."*

I imagine there are no Linux drivers for that device ;) Unfortunate-- that's a great idea.

---

### Post by hashimoto on 2005-05-09
Yeah, I would love a system like that.

When travelling in business, I have to connect to my office via VPN using RSA SecurID. That's a small keyring gadget with a display for a changing six digit code (changing every 60 seconds). So I got to give my four digit PIN and that six digit code to connect. I feel kinda safe with that kind of arrangement.

---

### Post by UbuWu on 2005-05-09
[QUOTE=panickedthumb]*"My bank gives out a little device with the size and looks of a small calculator, in which you have to put your bank card. Then the device asks for your pincode (which is the same number you use for atm's). Then it gives you a 8 digit number which is the password you have to use to get into the system."*

I imagine there are no Linux drivers for that device ;) Unfortunate-- that's a great idea.[/QUOTE]

No there are no drivers for it. It is not connected to your pc, so no need for drivers at all...  \\:D/

---

### Post by fishfork on 2005-05-09
[QUOTE=dave9191]You might not want to use a live cd because the versions will be out of date and not patched on that. And you want to make sure you are using upto date software. 

Dave[/QUOTE]

I don't think that's really a problem if you're **only** using it for online banking, because the only website you'll be visiting is the bank's website. If you don't trust your bank's website, then you really shouldn't bank with them!

---

### Post by dave9191 on 2005-05-09
[QUOTE=fishfork]I don't think that's really a problem if you're **only** using it for online banking, because the only website you'll be visiting is the bank's website. If you don't trust your bank's website, then you really shouldn't bank with them![/QUOTE]


Good point :)

---

### Post by jonny on 2005-05-27
The real question should be this: is Internet Explorer on Windows secure enough for online banking?  If your bank thinks it is, and if they're prepapared to accept liability for online fraud, then I find it hard to believe that ubuntu is less secure.

Reasons for preferring Linux for security reasons include:

 - Herd immunity.  Little malware is written specifically to attack Linux PCs because the Windows community offers much ricker pickings (more users that are, on average, less technically aware)

 - Proper user segregation (windows defaults to making all users system administrators).  You can be much more confident with Linux that you will be unaffected if some other idiot user has picked up a trojan whilst trawling through porn sites.  You can also be much more confident that no-one else will be able to view your browser history or cached passwords.

 - Sensible default settings.  Ubuntu installs a very small number of services by default.  That's why Canonical doesn't believe that a firewall is necessary in a standard installation.

---

### Post by robobomb#1 on 2008-03-08
Use opera the safest browser there is. A smaller target then firefox and over 95% of the time all security vulnerabilities are patched. Take a look at secunia.com for the most secure browser. It will be opera:)

---

