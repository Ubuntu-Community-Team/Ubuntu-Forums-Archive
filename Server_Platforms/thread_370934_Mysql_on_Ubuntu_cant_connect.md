---
title: "Mysql on Ubuntu cant connect"
date: 2007-02-26
forum: Server Platforms
---

### Post by christoforever on 2007-02-26
hey guys i just installed mysql 5 on ubuntu dapper. I can connect throught localhost at home. Yet when im elsewhere i cant connect i get: 

Mysql error number 2003

Cant connect to Mysql server on "33.333.33.333" (110) (not my actual ip address)

i read online im supposed to open up a port for mysql to listen from, or open ubuntu to listen on some port. I dont know, i couldent find anything that i could follow. I have same problem with my apache web server. i can connect on localhost but not anywhere else. If anyone has any suggestions that would be greatly appreciated.

sincerely,
Chris Dancy

---

### Post by jethro10 on 2007-02-26
> **christoforever said:**
> hey guys i just installed mysql 5 on ubuntu dapper. I can connect throught localhost at home. Yet when im elsewhere i cant connect i get: 

Mysql error number 2003

Cant connect to Mysql server on "33.333.33.333" (110) (not my actual ip address)

i read online im supposed to open up a port for mysql to listen from, or open ubuntu to listen on some port. I dont know, i couldent find anything that i could follow. I have same problem with my apache web server. i can connect on localhost but not anywhere else. If anyone has any suggestions that would be greatly appreciated.

sincerely,
Chris Dancy

I remember finding it hard as well if I remember. What are you trying to connect with? a program or the Mysql admin manager in the repo's

If its the manager, use localhost for the ip address, NOT your ip address.
default username is root, password is blank.

good luck

J

---

### Post by christoforever on 2007-02-26
i was using mysql admin. Its supposedly running at my house as i write this. Only im not at home at the moment and i would like to connect to it. I also need it for java programming. I can definetly conncet from home using localhost, its only when i leave that i cant connect. any solutions?

---

### Post by jethro10 on 2007-02-27
Wierd, I realise my reply was trash and changed it but its still the old answer!
Anyhow, I was going to say, install firestarter, the GUI to the firewall.

It apears in System-->somewhere or other.

run it, switch on the firewall, and get someone to try to connect to your database.
In the firestarter "events" tab, you'll see what is being blocked. You can open the ports here, or switch the firewall off temporarily to test it all.

J

---

### Post by christoforever on 2007-02-27
another interesting thing i noticed. The mysql server is connected hardwire to my cable modem. I have a laptop which gets the signal from my wireless router. I cant connect to mysql from my laptop , yet when im on my pc i can log in just fine. Another Thing i put firestarter in and when i tried to connect from the outside nothing showed up. Am i suposed to be enabling something or turning something on that i dont know about?

---

### Post by jethro10 on 2007-02-27
If firestarter is running it should show the port being blocked by your firewall.

That should show you what to unblock.

Can you ping the Pc from the laptop?

J

---

### Post by christoforever on 2007-02-27
it shows nothing absolutely nothing. Is there a file i need to modify to correct these settings?

---

### Post by jcostom on 2007-02-27
Check your bind-address value in your /etc/mysql/my.cnf.  I'll bet it's set to 127.0.0.1.

Translation?  You'll only ever be able to connect from the system itself.

So, if you'd like to connect from hosts other than the system itself, comment out that line and bounce mysql.

Do be careful though.  If you're exposing the system to the outside world and don't take care to secure things, you're in for a world of trouble (i.e. unwanted guests in your databases).

---

