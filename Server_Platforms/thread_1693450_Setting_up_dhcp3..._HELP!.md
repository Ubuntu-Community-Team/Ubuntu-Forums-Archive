---
title: "Setting up dhcp3... HELP!"
date: 2011-02-22
forum: Server Platforms
---

### Post by auzzie2112 on 2011-02-22
So i have my server all set up on my machine and ran "sudo apt-get update"
Then installed dhcp3 using "sudo apt-get install dhcp3-server"

Now its time to configure it but all the instructions i can find either error out when i type in the commands they provide due to :Permissions denied. and i'm on the account that i created when i installed the server which to my understanding is put into the administrators group but still not working...

After i have installed dhcp3 on my machine what are the next steps to configuring it?

---

### Post by elico on 2011-02-23
you must use the sudo to run many commands.
try:
sudo "command"

---

### Post by auzzie2112 on 2011-02-23
ok i will try that and get back to you thanks.
 
also the instructions i have so to save and exit the .conf file... how is this done?

---

### Post by auzzie2112 on 2011-02-23
I figured out the editing process. you insert text with "i" and you use "esc" to get out of the editing process to save and quit with ":wq" or just quit with ":q"
 
although now i'm on the next step in the process and i need to edit /etc/dhcp3/dhcpd.conf to configure my address pool, etc. but it comes up a sample configuration file. anyone know where the actual .conf file is located?

---

### Post by headvampyre@hotmail.co.uk on 2011-02-23
The sample config file is the config file. Are you just configuring dhcp services for IP assignment or PXE booting, i could write you a sample config for dhcpd.

---

### Post by auzzie2112 on 2011-02-28
> **headvampyre@hotmail.co.uk said:**
> The sample config file is the config file. Are you just configuring dhcp services for IP assignment or PXE booting, i could write you a sample config for dhcpd.
for ip assignment. i'm creating a server for like 3 computers at my house. i want them all connected to a domain.

---

### Post by headvampyre@hotmail.co.uk on 2011-02-28
If your wanting to do this - it has nothing to do with DHCP. I basically run a network like your wishing for. Here's my servers setup:

DHCP - for address assignment.
DNS - For lan IP's and forwards to virgin media and google's DNS servers.
Samba4 - Not yet released(Still stable and very usable) to replicate Microsoft's Active Directory Domain Controller functions.

Basically, you want Samba4 for windows, or NIS for linux. 

Add me on MSN/Message me on ubuntu forums, itll be easier to track problems you encounter through there :)

[http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)

is a basic setup for samba4 (ive configured mine to work with enterprise level security, and that quite a lot to post on here)

---

