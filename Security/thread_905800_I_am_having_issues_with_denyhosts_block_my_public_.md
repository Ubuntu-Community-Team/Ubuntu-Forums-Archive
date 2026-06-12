---
title: "I am having issues with denyhosts block my public ip"
date: 2008-08-30
forum: Security
---

### Post by Dave_Connor on 2008-08-30
I ran "sudo denyhosts" when I was testing if I could log in at root and failed the password to see if the blocking was working but now when I ssh to my machine I can't since denyhosts keep autologging my IP, I edited hosts.deny and restarted denyhosts but it still blocks me. Any help with this ?

---

### Post by cariboo on 2008-08-31
Are you sure you removesd your ip address from /etc/hosts.deny?

Jim

---

### Post by Traumadog on 2008-08-31
Hi!

Try the following suggestion from the DenyHosts author Phil Schwartz.  It worked for me when one of my friends was locked out by DenyHosts:

> To cleanse the IP address from DenyHosts do the following:

- Stop DenyHosts

- cd to your DenyHosts WORK_DIR

- edit each file containing the ip address (grep "THE_IP_ADDR" *)

- remove the ip address from each file, then re-save the file

- Start DenyHost

Hope this helps! :)

Traumadog.

---

### Post by tubezninja on 2008-08-31
The above procedure is the way to do it.  Simply deleting the IP address from hosts.deny will just prompt DenyHosts to add it back again the next time it runs and still sees the IP address having incorrectly logged in so many times.  You may also need to purge the Ip address entries from /var/log/auth.log.

And lastly, I've found it helps if you go into /etc/denyhosts.conf and set RESET_ON_SUCCESS to "yes."

---

### Post by Dave_Connor on 2008-09-01
I forgot to say thanks :) I stopped denyhosts like you said and edited the files I need and was able to purge my IP from denyhosts thanks once again, you guys are awesome :)

---

### Post by cariboo on 2008-10-11
I changed the password on my server and was playing with grsync and managed to lock myself out. Thanks for the easy fix.

Jim

---

### Post by amac777 on 2008-10-11
To avoid this happening in the future, you can add your own IP to the hosts.allow file so it will never be blocked.

---

### Post by kevdog on 2008-10-11
Seems like you could just avoid this confusion by using iptables or writing a custom rule for firestarter altogether.  There are many ways however to peel a potato.

---

### Post by cariboo on 2008-10-11
This was on my personal server that only faces the private side of my network except ssh, no firewall needed.

@amac777 that worked thanks. I mistyped my password 6 times and I could still access the sever :)

Jim

---

