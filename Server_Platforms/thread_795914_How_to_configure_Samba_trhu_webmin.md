---
title: "How to configure Samba trhu webmin"
date: 2008-05-15
forum: Server Platforms
---

### Post by rgotten on 2008-05-15
I am a complete new person on ubuntu server/linux. Following some threats, i just install WEbmin to configure SAMBA fpr my file server. Anybody has easy instruction to follow to configure SAMBA thru Webmin to conect my ubuntu server to my windows computers

Thanks

rgotten

---

### Post by ikonia on 2008-05-16
Webmin is not packaged or supported on ubuntu....for a very good reason, it's poor and dangerous.

It has multiple security holes and can cause breakage to you system.

I suggest you remove and forget about webmin, there are plenty of tools to help you that are supported and configured.

Ubuntu has Ebox in the repositories, which is the same sort of tool as webmin.

Samba can also launch "swat" which is a web interface for configuring samba.

Documentation can be found in the ubuntu community docs

For example

[https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)

---

### Post by sciurus on 2008-05-18
[https://help.ubuntu.com/community/eBox](https://help.ubuntu.com/community/eBox)

---

### Post by rgotten on 2008-05-25
> **ikonia said:**
> Webmin is not packaged or supported on ubuntu....for a very good reason, it's poor and dangerous.

It has multiple security holes and can cause breakage to you system.

I suggest you remove and forget about webmin, there are plenty of tools to help you that are supported and configured.

Ubuntu has Ebox in the repositories, which is the same sort of tool as webmin.

Samba can also launch "swat" which is a web interface for configuring samba.

Documentation can be found in the ubuntu community docs

For example

[https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)

Since i am newby and trying to do a file server, were can i get simple an d easy instructions on how to install Samba with ebox

rgotten

---

### Post by foolano on 2008-05-26
First of all, you have to keep in mind what ebox-samba offers you to check if it meets your needs:

ebox-samba uses an LDAP backed and is capable to work in file sharing mode or PDC mode. The latter is used in scenarios where you want your windows machines to authenticate against eBox.

The file sharing options and pretty simple:

Every user has a home directory that only he/she can access.

Every group can have an associated directory, and only users within the group can access the directory.


If you need more complicated stuff with samba I'm afraid eBox is not what you need. If that's enough feel free to request more help here or on the eBox forums, #ebox on the IRC channel...

Hope this helps :)

---

### Post by garethsimpsonuk on 2008-05-26
> **rgotten said:**
> Following some threats, i just install WEbmin



I don't think samba is a very good solution to threats. There may be another package in the repositories that can help.

---

### Post by windependence on 2008-05-26
> **ikonia said:**
> Webmin is not packaged or supported on ubuntu....for a very good reason, it's poor and dangerous.

It has multiple security holes and can cause breakage to you system.

I suggest you remove and forget about webmin, there are plenty of tools to help you that are supported and configured.

Ubuntu has Ebox in the repositories, which is the same sort of tool as webmin.

Samba can also launch "swat" which is a web interface for configuring samba.

Documentation can be found in the ubuntu community docs

For example

[https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)

Finally someone who agrees with me. 

The SAMBA configuration files are really not that hard to edit directly in a command line terminal. They are in plain text and well commented. You can use something like nano or pico if you don't like vi. All webmin does is edit these files for you anyway which can be bad if someone hacks your webmin install.

Also, SAMBA has great documentation, just check out their web page. Here is a good place to start:

[http://us3.samba.org/samba/docs/man/Samba-Guide/](http://us3.samba.org/samba/docs/man/Samba-Guide/)

-Tim

---

### Post by garethsimpsonuk on 2008-05-26
From what I know yes it loosens the security but for a home server it's fine...isn't it? lol
It can do a lot more than just samba and as I'm still in my second month of ever seeing a linux distro it's handy for headless admin without using ssh.
Of course my ultimate goal is to get rid of things like webmin and just use ssh but it helps with the learning curve but I agree if you know what your doing with a CLI there's no excuse!

---

