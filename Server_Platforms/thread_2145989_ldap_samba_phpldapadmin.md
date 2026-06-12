---
title: "ldap samba phpldapadmin"
date: 2013-05-17
forum: Server Platforms
---

### Post by Rakeshvijayan on 2013-05-17
Hi friends 


Is there any howto is available to configure ldap samba with phpldapadmin I use [https://www.youtube.com/watch?v=FzpzQNU-Iuc](https://www.youtube.com/watch?v=FzpzQNU-Iuc) this viedo for set so ,but I am stuck while I tried to add samba user I got an error message ```
[TABLE="class: sysmsg"]
[TR]
[TD="class: icon"][/TD]
[TD="class: head"]Template Value Error
[/TD]
[/TR]
[TR]
[TD="class: body"]This template uses a selection list for attribute [**sambaSID**], however the selection list is empty.
You  may need to create some dependancy entries in your LDAP server so that  this attribute renders with values. Alternatively, you may be able to  define the appropriate selection values in the template file.[/TD]
[/TR]
[/TABLE]

``` I don't know how to go further .please share your knowledge I am new in the ldap configuration no body available to help me now

---

### Post by chrisguk on 2013-05-18
Have you tried this, ignore it says debian.

[http://www.howtoforge.com/debian-squeeze-ldap-server-with-openldap-and-phpldapadmin](http://www.howtoforge.com/debian-squeeze-ldap-server-with-openldap-and-phpldapadmin)

What do the errors logs say?

---

### Post by tommy smith on 2013-05-18
I also get same error like above and still don't know how to solve it :confused:  I'm using fresh ubuntu server 12.04 and setup follow that guide.

---

### Post by Rakeshvijayan on 2013-05-20
> **tommy smith said:**
> I also get same error like above and still don't know how to solve it :confused:  I'm using fresh ubuntu server 12.04 and setup follow that guide.


By the viedo he is not specify  how add samba ssid and group Id this is the problem for the configuration  ,I added it manualy by create samba domain .But it is not give me a solution .... 

> chrisguk 	 	 		[INDENT] 			 				Re: ldap samba phpldapadmin
 			 			Have you tried this, ignore it says debian.

[http://www.howtoforge.com/debian-squ...d-phpldapadmin]("http://www.howtoforge.com/debian-squeeze-ldap-server-with-openldap-and-phpldapadmin")

What do the errors logs say? 		
[/INDENT] 	


Thanks for the Replay .Above specified configuration is correct for me . error was lack of smbssid viedo uploader is not provide how he add such things , He take 5 day to complete the viedo he may forget to record some of configuration

---

### Post by tommy smith on 2013-05-23
I follow in this guide :

[http://www.unixmen.com/openldap-installation-and-configuration-in-ubuntu-12-10-server-debian-6/](http://www.unixmen.com/openldap-installation-and-configuration-in-ubuntu-12-10-server-debian-6/)

It's still same error, in both local and my vps :(

---

### Post by Rakeshvijayan on 2013-05-24
does any body know in this forum to configure  smbssid while installing samba.ldif

---

### Post by Rakeshvijayan on 2013-05-28
[http://www.unixmen.com/setup-samba-domain-controller-with-openldap-backend-in-ubuntu-13-04/](http://www.unixmen.com/setup-samba-domain-controller-with-openldap-backend-in-ubuntu-13-04/)


try this for samba-domain-controller

---

