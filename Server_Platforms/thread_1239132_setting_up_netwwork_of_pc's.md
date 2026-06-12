---
title: "setting up netwwork of pc's"
date: 2009-08-13
forum: Server Platforms
---

### Post by autroy on 2009-08-13
Hi I hope this is posted in the correct section.
Im looking for some reading material and suggestions as I havent used Linux before but so far it looks great on my laptop and im very impressed at how much fatser it runs as well!

My setup:
4 pc's and 2 laptops on a network with a network pc soley for backup and storage
I will be concerting all to Ubuntu with the exception of one pc used for gaming that will keep Vista.

What i want to acheive:
All pc's and laptops to save all personal data to the 'mainframe' pc, my thinking here is that the only pc that needs to run a backup will be the 'mainframe' pc.
Also i want the 4 users in the house to be able to use any pc with their own login and have their data come from the mainframe. Like we have at work where i can login to any pc and access my data / preferences etc from the mainframe and nothing that i do or save is on the pc im using.

Where should i go to read about this and is it possible / hard to set up

many thanks for any suggestions you have :)

---

### Post by mattm591 on 2009-08-13
To do what you're describing you'll need your server to be acting as a domain controller and then store all users home directories on this central server if you want them to be available whenever they login.

Take a look at this:
[https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html)
which describes how to use Samba as a domain controller.

As for whether it's hard depends on you're level of knowledge and how familiar you are with advanced configuration in Linux.

In my experience, any time you want to do something advanced with Samba you're going to be needing to manually edit the config files as no GUI will give you the options you need.

---

### Post by autroy on 2009-08-14
Thanks for that, it has helped a lot. it looks involved but im going to gve it ago

---

### Post by Iowan on 2009-08-15
[LDAP]("https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html") also comes to mind...

---

