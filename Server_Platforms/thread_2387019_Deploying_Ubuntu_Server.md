---
title: "Deploying Ubuntu Server"
date: 2018-03-13
forum: Server Platforms
---

### Post by computermichael on 2018-03-13
As a learning project, I want to deploy an enterprise-grade Ubuntu setup for three computers. One will ideally run Ubuntu Server and handle logons (I assume LDAP), DNS, DHCP, email server, LAMP server, etc. I want the other two computers to run Ubuntu Desktop and login using credentials received from the server, similar to how Windows Server 2016 works. I assume I need to install an LDAP software distribution to achieve this. My question is how would I go about deploying LDAP to work properly and connect all the computers through Ubuntu Server.

---

### Post by Frogs Hair on 2018-03-13
Moved to ***Server Platforms***.

---

### Post by LHammonds on 2018-03-13
So one Ubuntu Server 16.04 LTS server, and two Ubuntu Desktop 16.04 LTS workstations that will connect to and authenticate against the server?

Will there be any Windows machines that need to authenticate as well?

Just asking for clarification...not that I'm knowledgeable about it.  I have my own project to setup Samba DC for Windows clients.

LHammonds

---

### Post by TheFu on 2018-03-13
I've done Unix/Linux LDAP authentication.  Actually, that part is pretty easy thanks to PAM and LDAP on the clients, provided you don't need to support Windows.  LDAP can be used for many webapp logins too.

Please reconsider your system architecture from a security standpoint.  
Systems that must face the internet shouldn't run internal authentication or internal LAN services.  
I would keep email separate and internet web servers separate.  The attack vectors are different, but once they are compromised, losing both sets of systems would be bad.  You can use virtualization to separate these different services. I've considered using LXD for my new services and migrations for older systems that need to be moved to newer base-OSes.

Of course, you CAN run everything on a single OS install, but why?

LDAP isn't anything special. It is just a package.  [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) should explain.  Getting logins working is pretty bonehead with LDAP-pam.  Honestly, the worst part is managing accounts using LDIF files - there aren't any safe GUIs for LDAP account management that I know.  I cheat and use Zimbra for that on our network.  That method has flaws, but the GUI for admins and end users to manage their LDAP information is consistent, central, and works.

---

### Post by computermichael on 2018-03-14
Appreciate the excellent replies. It will only be Linux workstations and it will be in a demilitarized zone completely separated from the internet, so i'm not as concerned with security as of yet.

---

