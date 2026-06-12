---
title: "Switching From SBS 2003 to Ubuntu"
date: 2009-09-14
forum: Server Platforms
---

### Post by kladha on 2009-09-14
I am a System Administrator in a Company which runs Small Business Server 2003 (15 Users ) with all of its Features such as Active Directory, Exchange Server, Remote Work Space, VPN and  Fileserver

But since our organization in growing and now we are thinking of Switching to Full Server rather then Small Business server, but dont have budget to buy the Full Microsoft server so we are thinking  of Switching to UBUNTU SERVER 9.0  Which seems a very good and cost effective solution.

Just want to know is it possible to switch to Ubuntu 9.0 from Small Business Server 2003 and how do i get start doing it?

---

### Post by bogdan.veringioiu on 2009-09-14
Hi.

You can start evaluating these guides (they are not exactly for the latest ubuntu version, but they are compatible).

[http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-pop3-imap-on-ubuntu-8.10](http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-pop3-imap-on-ubuntu-8.10)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html)

Cheers

---

### Post by viktara on 2009-09-14
Hi,

The only problem you might face is a drop in replacement for exchange servers calendering / groupware support.

There seems to be something on it's way through the openchange project, but it's not quite there yet:
[http://www.openchange.org/](http://www.openchange.org/)

If you client does not use the calendering functions then you have no issue.

I moved from windows server to linux a few years back.

Regards



Vik

---

### Post by TwiceOver on 2009-09-14
Not trying to get you away from moving to Ubuntu Server, but there's still quite a bit of scaling left in your SBS 2003 box.  You can have 75 users and the exchange server database is limited to 80gb which should be plenty.  You can also have other server boxes on the network...

The problems for me moving our network from SBS 2003 to Ubuntu are:

Exchange - There's just no good Push Mail alternative.  Though it can be complicated to adminstrate, it really is a fine mail system.

Group Policy - AFAIK Ubuntu cannot distribute group policy settings to Windows workstations.

Sharepoint (WSS3 Specificaly) - A decent CMS, easy to understand.

Domain Groups/Credentials - I'm not positive, but I don't think Samba does this too well.

RWW/OWA - Remote Web Workplace and Outlook Web Access are some really nice features...  A little hard to give up.

Don't get me wrong, I love Ubuntu, and you are spending out the *** for those CALs, but SBS 2003 is an excellent server system for a small business.  Especially if you have any LOB Apps that require Windows Server.

---

### Post by kladha on 2009-09-16
Thank you guyz for your help...

I have decided to first install the test ubuntu server and see if it would work as I want ... if there is any problem will it be alright for me to give you guyz a Private msg

Cheers

Kam

---

### Post by jonallport on 2009-09-17
For your e-mail/groupware have a look at [Zimbra]("http://www.zimbra.com").

I use the FOSS release as the successor to a GroupWise 6 installation.  The web-interface is pretty slick and fully ajax, but there's a (reasonably priced) 'Network Edition' with appropriate connectors if you just can't dispense with Outlook or your Blackberry.

Also, I believe there's an extension to use the Zimbra admin interface to manage your Samba users/groups within the LDAP server.

---

