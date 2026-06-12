---
title: "Internet Restrictions on based on MAC"
date: 2013-03-18
forum: Server Platforms
---

### Post by Ally Media Group on 2013-03-18
I am wanting to create a ipv6 DHCP server that will create restrictions on internet access based on MAC addresses.

Basically,
When a user's computer first accesses the network the DHCP server see's the MAC and say's it is unknown, it redirects to the website for the service.  Then the user creates an account with their credentials (username, password, etc), the website creates a table with the account information in a mysql database.  The next step would require the device to be registered to the account table.  The entry in the table would have the information reverent to the device (Name, MAC address, etc)
Once that information is in the database, the server would use that information to allow access to the internet for that device.
The ip address would be dynamic, only the MAC would be used to authenticate on the network.

I know how to create the database and website, but I am lost on how I would get the server side of the things working.  If anyone could point me in the correct direction it would be appreciated.

---

