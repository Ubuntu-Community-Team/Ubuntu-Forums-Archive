---
title: "disabling remote password authentication"
date: 2009-08-01
forum: Security
---

### Post by wolfv6 on 2009-08-01
[FONT=Times New Roman, serif][SIZE=3]I read the instructions on [https://help.ubuntu.com/community/StricterDefaults#Disable%20Password%20Authentication](https://help.ubuntu.com/community/StricterDefaults#Disable%20Password%20Authentication) and have a question about  disabling remote password authentication.[/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]

I am using Ubuntu 9.04 on a desktop PC connected to the Internet.  I will login via the connected keyboard and never log in remotely.  [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]So I want to disable remote password authentication to defeat brute-force attacks.  If I add the following code in the [/SIZE][/FONT][SIZE=3]/etc/ssh/sshd_config[/SIZE][FONT=Times New Roman, serif][SIZE=3] file, [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]will I still be able to login from the locally connected keyboard?[/SIZE][/FONT]```
PasswordAuthentication no
```[FONT=Times New Roman, serif][SIZE=3]The instructions say “it will lock you out of the machine”, but it is not clear if lockout refers to just the remote login or all logins.[/SIZE][/FONT]
   [FONT=Times New Roman, serif][SIZE=3]
Thank you
[/SIZE][/FONT]

---

### Post by wojox on 2009-08-01
You can do it. That only if you remote login via another computer through a secured shell.

---

### Post by wolfv6 on 2009-08-01
> **wojox said:**
> You can do it. That only if you remote login via another computer through a secured shell.
Do you mean I would still be able to log in from my locally connected keyboard and that the code would only disable secured-shell remote login?

Thank you for your reply wojox, I just want to make sure I understand this correctly.

---

### Post by igorzwx on 2009-08-01
consider this ancient technique:
[http://en.wikipedia.org/wiki/MAC_address](http://en.wikipedia.org/wiki/MAC_address)

---

### Post by wojox on 2009-08-01
Yes that's what it means.

---

### Post by igorzwx on 2009-08-01
MAC address can be falsified, of course.
But in any case...

---

### Post by wolfv6 on 2009-08-01
> **igorzwx said:**
> MAC address can be falsified, of course.
But in any case...I am not familiar with this technique.  Please give me a link or some key words to google so that I can read about it.  I am just starting to learn about security and UNIX, so I am still slow to comprehend.  Thank you for your patients.

---

### Post by igorzwx on 2009-08-01
this is the link:
[http://www.google.com/search?q=ubuntu%20howto%20change%20mac%20address&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=ubuntu%20howto%20change%20mac%20address&ie=UTF-8&oe=UTF-8)

 	Quote:
 	 	 		 			 				 					Originally Posted by **igorzwx** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7716253#post7716253") 				
 				[I]MAC address can be falsified, of course.
But in any case...[/I]
 			 		 	 	 
I am not familiar with this technique. Please give me a link or some key words to google so that I can read about it. I am just starting to learn about security and UNIX, so I am still slow to comprehend. Thank you for your patients.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7716410") 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=7716410")

---

### Post by Agent ME on 2009-08-01
> **wolfv6 said:**
> I am using Ubuntu 9.04 on a desktop PC connected to the Internet.  I will login via the connected keyboard and never log in remotely. So I want to disable remote password authentication to defeat brute-force attacks.  If I add the following code in the [SIZE=3]/etc/ssh/sshd_config[/SIZE] file, will I still be able to login from the locally connected keyboard?```
PasswordAuthentication no
```The instructions say “it will lock you out of the machine”, but it is not clear if lockout refers to just the remote login or all logins.
Thank you
Changing that option will not affect local logins. (/etc/ssh/sshd_config is a config file for sshd, the program allowing remote logins. SSH is no way involved with local logins.)

To the other person mentioning MAC addresses: That's not really relevant at all here. I guess on a local network you could try to limit login by MAC, but that's easily circumventable, and has little to do with interaction with the larger internet.

---

