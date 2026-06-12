---
title: "Advanced file sharing server - Where to start"
date: 2009-08-21
forum: Server Platforms
---

### Post by cwaidelich on 2009-08-21
Hi there,

[As an intro:
I have done some simple filesharing with samba between Linux and WinXp and I have also done some filesharing between Linux and Linux with NFS. Actually 2 years ago.]

I will write the whole project, then I put the questions.

I want to create a advance file sharing server. It has to do the following:

1. Share Files from a Linux Server (1) to Linux Clients (about 15) and WinXP (3) machines all in a close LAN network protected with a Firewall.

2. There are some jerarquy between users / groups, that means that if:
```
Big Boss
|-- SalesDept Boss
|   |-- Salesman 1
|   |-- Salesman 2
|-- AccountDept Boss
|
... and so on

```
Bog Boss can see everything (admin control), SalesDept can see his and Salesman X files, AccountDept can only see his.

3. There are special folders can only be seen by certain people and modify by other people.

4. Users and passwd are defined in the server: 
4.1 That means that every person can access to his user account from every client computer. 
4.2 Passwd are reassigned from sistem admin in the server.

5. This should all be done from logon screen in the client.

== in other words, mostly like Windows Server 200X

That is basically it. Now the questions:

a) I would like to use only Samba to share files between Server and Clients, but I have read that it is not perfect. How would you configure this?
b) About question 4 and 5: Is this done with a Domain Server? Where do I start?

Pls notice: I don't want you to do this for me I just want a guide.

Thank you in advance.

Christian

---

### Post by jocampo on 2009-08-21
Because there is a Windows machine, you need Samba.

Here we go ;-) ...
[http://samba.netfirms.com/index.htm]("http://samba.netfirms.com/index.htm")

---

### Post by cwaidelich on 2009-08-21
Thx. I understand that with a Primary Domain Controller a WindowsNT can connect with his user and passwd to Samba. But how does it work for a Linux Client? Is is posible to connect with the user and passwd from the logon screen to samba?

---

### Post by Iowan on 2009-08-21
My home network uses Samba sharing - even from this Linux client. It may not be most simple, elegant,or efficient - but it works.  Access is controlled by Samba configuration.  It can be based on user and/or group depending on share options. I haven't done much with changing passwords after I set the system up. LDAP is an option for more AD-type control, but I can access my shares from whichever machine I log onto.

---

### Post by redmk2 on 2009-08-22
If you are looking for domain control (DC) ala WIN2000x, you will have to use Samba3.  The tutorial suggested by [COLOR="Blue"]jocampo  [/COLOR]is Samba2.  It is for NT style PDC control.

I would suggest reading [_[COLOR="DarkSlateGray"]Samba3 by Example[/COLOR]_]("http://us1.samba.org/samba/docs/man/Samba-Guide/").  This is an excellent guide with setups that range from simple to complex.

---

