---
title: "iptables..."
date: 2007-08-29
forum: Server Platforms
---

### Post by Nevstah on 2007-08-29
hi guys

i have successfully set up a rule to only allow one remote IP address to gain access to a particular port, in this case 10000 - webmin. i now wish to allow two remote addresses to have access to this port, but i have no clue how to go about this :(

can anyone point me in the right direction? i tried to add a 2nd rule for the same port, but that just didnt work at all!!

many thanks

nev

---

### Post by yey365 on 2007-08-29
Did you specify the IP address in the rule? if so try extending it to an ip range.  E.G. 192.168.0.1 becomes 192.168.0.1-2

Hope this helps.

Jim

---

### Post by gombadi on 2007-08-29
Adding a second rule for the same port will work if you put it in the right place. What problem did you have adding the second rule?

Have a look at what is currently set up with this command.
```
iptables -vnL
```

How are you adding the rules - iptables commands of some sort of front end?

Remember that iptables starts with the first rule in a table and works its way down until it finds a match so this could be the problem -

```

iptables rule to allow the first ip address to connect
iptables rule to block access to port 10000
iptables added rule to allow second ip address to connect

```

The above rule to block access to port 10000 means packets never get to the second rule to allow packets from the sceond ip address.

---

### Post by Nevstah on 2007-08-29
i'll check the rule order!! that sounds like a daft enough mistake to make!! thanks

i'm sure i'll get back if that wasnt the problem:P

---

### Post by nowshining on 2007-08-29
you'll have to do

sudo iptables -vnL

---

