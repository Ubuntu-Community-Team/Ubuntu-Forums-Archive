---
title: "usb tools to detect restricted file access on windows 8"
date: 2014-06-24
forum: Security
---

### Post by g.wiebe84 on 2014-06-24
I'm the administrator at work. A Windows 8 laptop has had an unauthorized access after hours. Is there a back door to bypass the login screen? The question is this: are there some ubuntu/linux tools that I can put on a usb that I can run to check for a keystroke logger and unauthorized file access/deletion/copying?

This to be a secure Windows laptop with confidential accounting files on it. Installing Ubuntu on it is not an option, unfortunately. Are there any suggestions to make this laptop more secure?

---

### Post by HermanAB on 2014-06-25
Yes, unless you used bitlocker.

You really should use bitlocker.

If you are not using bitlocker and you are done punching yourself for not using it, then you could use any Live Linux disk to inspect the NTFS file system of the laptop machine.  I'd recommend Knoppix - it has all the tools.

---

### Post by jon43 on 2014-06-25
You really need to be encrypting your data. It wouldn't even take some exotic program to steal the files off the laptop if they are unencrypted. Someone could just boot a linux distro from a USB drive, mount the internal hard drive and copy all of the files.

---

### Post by g.wiebe84 on 2014-06-26
Thank you, gentlemen, for your responses and advise. Obviously, we've got a lot of work to do in our Data Security Dept.

---

### Post by SeijiSensei on 2014-06-27
First, if there are client files on the machine, they must be stored on an encrypted partition with the password known only to you and the computer's user. 

Next, I wouldn't try to fix this machine.  I'd reinstall everything from scratch.  If you have a lot of such laptops, you should build a standard Windows image file that you can install quickly on all of them.

Third, laptops with client information should not leave the office unless they are going with someone to a client's site.  They should definitely not go home with staff members.

You might consider consolidating all the clients' information on your office server and having the laptops download only what they need over a secure connection.  [OpenVPN]("http://openvpn.net/") is a good choice for that task.  

Accounting is a business with serious ethical and legal requirements to protect the privacy of your clients' information.  That should be the priority even if it means making the computers' users jump through some additional hoops.

---

### Post by bashiergui on 2014-06-29
> I'm the administrator at work. A Windows 8 laptop has had an unauthorized access after hours. Is there a back door to bypass the login screen? The question is this: are there some ubuntu/linux tools that I can put on a usb that I can run to check for a keystroke logger and unauthorized file access/deletion/copying?Do as others recommended and boot with a live CD. You'll want to inspect the time stamps on the files you suspect were accessed. I'd also look at internet history for recently accessed websites, perhaps your guy uploaded docs to Dropbox or to some free email service. I'd also look for all users on the computer and when they last logged in. Everything you need to know is probably still there, you just need to spend time figuring out how to find it or hire someone for a crapton of money to do that for you.

Then spend some time making a standard image like sejeisensei said. Obviously encrypt the user computers. How do you know the files were accessed after hours? Figure out how to prevent this case from occurring again by putting controls in place. Sell it to your reluctant boss by comparing the costs of the needed controls with the cost of data loss and resulting business losses and possible law suits. If they say no then at least your ass is covered when it happens again.

---

