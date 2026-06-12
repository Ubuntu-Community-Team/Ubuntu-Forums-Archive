---
title: "VPS simulation on LAN Ubuntu server"
date: 2014-01-16
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2014-01-16
Hi all

Would like to simulate setting up a VPS on a spare server on a LAN.

So assuming Ubuntu Server 12.04 LTS is the O/S, should there be a typical LAMP installation or should adding Apache, MySQL, PHP etc take place after the basic O/S is installed? 

TIA

---

### Post by ian-weisser on 2014-01-16
Since you are simulating...
Do it both ways, and see which you prefer.

---

### Post by CharlesA on 2014-01-16
What ian said. A LAMP install will install the same things installing Apache/PHP/MySQL separately will.


Now if you wanted to run something like Nginx or MariaDB, you would have to do everything manually.

---

### Post by ChrisRChamberlain on 2014-01-17
ian-weisser,  CharlesA

Thanks for your replies.

Would there have been installed Apache, MySQL and PHP in a typical VPS?

Also, assuming user to be 'root', password to be 'mypassword', server name to be IP address, how would GRUB be handled during the installation process from DVD or USB memory stick?

Finally, 'sudo reboot' would take you out of the current session only, leaving you at the command prompt?

---

### Post by CharlesA on 2014-01-17
> **ChrisRChamberlain said:**
> ian-weisser,  CharlesA

Thanks for your replies.

Would there have been installed Apache, MySQL and PHP in a typical VPS?

Also, assuming user to be 'root', password to be 'mypassword', server name to be IP address, how would GRUB be handled during the installation process from DVD or USB memory stick?

Finally, 'sudo reboot' would take you out of the current session only, leaving you at the command prompt?

If you get an unmanaged VPS, you would have to install all the services yourself.

On a clean VPS like one from RamNode or Linode, the only user will be root but it should have a strong password set (which you should change immediately to another strong password).

The machine will shutdown and reboot like a regular physical machine. Unless you install a GUI or web-based admin panel, you will have to manage it over SSH, so logging off of the SSH session would leave the rest of the machine running.

I don't think you really need to worry about GRUB because it's mostly automatic, so that should be fine.

Are you asking if the servername should be an IP address or what?

---

### Post by ChrisRChamberlain on 2014-01-18
> ...if the servername should be an IP address or what? 

The only experience so far has been an observer of [ Fasthosts]("http://www.fasthosts.co.uk/?gclid=CJf0oPnVh7wCFWTnwgodSyMALw") VPS offering and it seemed there were using an IP address as a servername.

So I wondered if this was the norm?

---

### Post by CharlesA on 2014-01-18
> **ChrisRChamberlain said:**
> The only experience so far has been an observer of [ Fasthosts]("http://www.fasthosts.co.uk/?gclid=CJf0oPnVh7wCFWTnwgodSyMALw") VPS offering and it seemed there were using an IP address as a servername.

So I wondered if this was the norm?

I don't understand what you mean. I looked at that page and that company looks to offer a managered VPS, but that shouldn't have any effect on the server name.

Are you asking about Apache virtualhosts or something else?

---

### Post by ChrisRChamberlain on 2014-01-18
On that occasion the credentials were:-

user = 'root'
password = 'abcd1234'
servername = '999.999.999.999' 

Hence the question

---

### Post by CharlesA on 2014-01-18
> **ChrisRChamberlain said:**
> On that occasion the credentials were:-

user = 'root'
password = 'abcd1234'
servername = '999.999.999.999' 

Hence the question

That just looks like the connection information. They give you an IP address instead of a hostname because you might not have DNS set up for that server yet.

---

### Post by ChrisRChamberlain on 2014-01-18
Understood - thank you.

---

