---
title: "Ubuntu 12.04 Server offline DHCP install"
date: 2012-08-30
forum: Server Platforms
---

### Post by WhtnySean on 2012-08-30
Hello, I am VERY new here so I hope I don't get slammed to much.. 

Goal: build a Ubuntu Server that will have DHCP enabled off our main network. Install FOG on it and run an imaging station seperate from any network/internet. 

I have the server software install (not FOG yet)and I need to install the DHCP software

sudo aptitude install isc-dhcp-server

Now, I do not want to plug this into our main network to try and pull this file. I am thinking that is my issue because this command error's out. 

Says can not find package. Is there any way to get this server up and running as a DHCP server without getting it on our main network?

---

### Post by kennethconn on 2012-08-30
What is the error message?
 
Updates are typically done online after server install - I'd imagine the server does not have any connection out to the internet. Now if you don't want one, you'll have to get the necessary packages and install on to the server locally (I have no experience of this).
 
Do you wish to keep seperate from your main network AND the internet, or just your main network?

---

### Post by WhtnySean on 2012-08-30
I wish to keep it off any Internet/Intranet, basically put a 24 port cisco switch (non DHCP switch) and this FOG Ubuntu server. So, it would be awesome to know where/how to download the files to a thumb drive to install onto the server. 

Sorry I created more questions with my question. 

Thank you for your time.

---

### Post by kennethconn on 2012-08-30
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
 
See the section - Installing packages without an Internet connection

---

